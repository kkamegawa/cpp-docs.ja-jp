---
title: ユーザー定義リテラル (C++)
ms.date: 12/10/2019
ms.assetid: ff4a5bec-f795-4705-a2c0-53788fd57609
ms.openlocfilehash: 31b8f1dfb261839c04a6829132975ada9c09d619
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301302"
---
# <a name="user-defined-literals"></a>ユーザー定義リテラル

のリテラルにC++は、整数、文字、浮動小数点、文字列、ブール値、およびポインターの5つの主なカテゴリがあります。  C++ 11 以降、これらのカテゴリに基づいて独自のリテラルを定義して、一般的な表現形式に構文のショートカットを提供したり、タイプ セーフを向上させたりすることができます。 たとえば、Distance クラスがあるとします。 キロメートルのリテラルとマイルのリテラルを定義して、auto d = 42.0_km or auto d = 42.0_mi と記述するだけで、ユーザーに測定単位を明示するよう求めることができます。 ユーザー定義リテラルには、パフォーマンス上の利点または欠点はありません。主に利便性やコンパイル時の型推論のためです。 標準ライブラリには、std: string 用のユーザー定義リテラル、std:: complex、\<chrono > ヘッダーの時間単位および期間操作の単位があります。

```cpp
Distance d = 36.0_mi + 42.0_km;         // Custom UDL (see below)
std::string str = "hello"s + "World"s;  // Standard Library <string> UDL
complex<double> num =
   (2.0 + 3.01i) * (5.0 + 4.3i);        // Standard Library <complex> UDL
auto duration = 15ms + 42h;             // Standard Library <chrono> UDLs
```

## <a name="user-defined-literal-operator-signatures"></a>ユーザー定義リテラル演算子のシグネチャ

ユーザー定義リテラルを実装するには、次のいずれかの形式の名前空間スコープで**演算子 ""** を定義します。

```cpp
ReturnType operator "" _a(unsigned long long int);   // Literal operator for user-defined INTEGRAL literal
ReturnType operator "" _b(long double);              // Literal operator for user-defined FLOATING literal
ReturnType operator "" _c(char);                     // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _d(wchar_t);                  // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _e(char16_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _f(char32_t);                 // Literal operator for user-defined CHARACTER literal
ReturnType operator "" _g(const char*, size_t);      // Literal operator for user-defined STRING literal
ReturnType operator "" _h(const wchar_t*, size_t);   // Literal operator for user-defined STRING literal
ReturnType operator "" _i(const char16_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _g(const char32_t*, size_t);  // Literal operator for user-defined STRING literal
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

前の例では、演算子の名前は任意の名前を指定できるプレース ホルダーです。ただし、先頭にアンダー スコアが必要です。 (標準ライブラリでのみ、アンダースコアなしでリテラルを定義できます)。戻り値の型は、リテラルによって実行される変換またはその他の操作をカスタマイズする場所です。 また、これらの演算子のいずれも、`constexpr` として定義できます。

## <a name="cooked-literals"></a>cooked リテラル

ソースコードでは、リテラルは、ユーザー定義であるかどうかに関わりなく、基本的に `101`、`54.7`、`"hello"`、`true` など、英数字のシーケンスです。 コンパイラは、シーケンスを整数、float、const char\* 文字列などとして解釈します。 リテラル値に割り当てられている型を入力として受け入れるユーザー定義リテラルは、"調理済み"*リテラル*として非公式に知られています。 上記の `_r` と `_t` を除く演算子は、すべて cooked リテラルです。 たとえば、リテラル `42.0_km` は _b に似たシグネチャを持つ _km という名前の演算子にバインドされ、リテラル `42_km` は _a に似たシグネチャを持つ演算子にバインドされます。

次の例では、ユーザー定義リテラルが呼び出し元に入力を明記するよう求める方法を示しています。 `Distance` を構築するために、ユーザーは適切なユーザー定義リテラルを使用して、キロメートルまたはマイルを明示的に指定する必要があります。 言うまでもなく、他の方法でも同じ結果を実現できますが、ユーザー定義リテラルは、その他の方法よりも簡潔です。

```cpp
struct Distance
{
private:
    explicit Distance(long double val) : kilometers(val)
    {}

    friend Distance operator"" _km(long double  val);
    friend Distance operator"" _mi(long double val);
    long double kilometers{ 0 };
public:
    long double get_kilometers() { return kilometers; }
    Distance operator+(Distance& other)
    {
        return Distance(get_kilometers() + other.get_kilometers());
    }
};

Distance operator"" _km(long double  val)
{
    return Distance(val);
}

Distance operator"" _mi(long double val)
{
    return Distance(val * 1.6);
}
int main(int argc, char* argv[])
{
    // Must have a decimal point to bind to the operator we defined!
    Distance d{ 402.0_km }; // construct using kilometers
    cout << "Kilometers in d: " << d.get_kilometers() << endl; // 402

    Distance d2{ 402.0_mi }; // construct using miles
    cout << "Kilometers in d2: " << d2.get_kilometers() << endl;  //643.2

    // add distances constructed with different units
    Distance d3 = 36.0_mi + 42.0_km;
    cout << "d3 value = " << d3.get_kilometers() << endl; // 99.6

    // Distance d4(90.0); // error constructor not accessible

    string s;
    getline(cin, s);
    return 0;
}
```

リテラルの数値は 10 進数を使用する必要があります。そうでないと、数値が整数として解釈され、型が演算子と互換性がなくなります。 また、浮動小数点の入力では、型は**long double**である必要があり、整数型の場合は**長すぎる必要**があることに注意してください。

## <a name="raw-literals"></a>未加工リテラル

未加工のユーザー定義リテラルでは、ユーザーが定義する演算子は、リテラルを char 値のシーケンスとして受け取り、そのシーケンスを数値や文字列などの型として解釈することはユーザーの責任です。 このページで前述した演算子の一覧では、`_r` と `_t` を使用して未加工リテラルを定義することができます。

```cpp
ReturnType operator "" _r(const char*);              // Raw literal operator
template<char...> ReturnType operator "" _t();       // Literal operator template
```

未加工リテラルを使用して、入力シーケンスについて、コンパイラが実行するものとは異なるカスタムの解釈を提供できます。 たとえば、シーケンス `4.75987` を、IEEE 754 浮動小数点型ではなく、カスタム 10 進数型に変換するリテラルを定義できます。 また、cooked リテラルと同様、未加工リテラルは、入力シーケンスのコンパイル時の検証を実行するために使用することもできます。

### <a name="example-limitations-of-raw-literals"></a>例: 未加工リテラルの制限事項

未加工リテラルの演算子とリテラルの演算子のテンプレートは、次の例に示すように、整数および浮動小数点のユーザー定義リテラルに対してのみ動作します。

```cpp
#include <cstddef>
#include <cstdio>

// Literal operator for user-defined INTEGRAL literal
void operator "" _dump(unsigned long long int lit)
{
    printf("operator \"\" _dump(unsigned long long int) : ===>%llu<===\n", lit);
};

// Literal operator for user-defined FLOATING literal
void operator "" _dump(long double lit)
{
    printf("operator \"\" _dump(long double)            : ===>%Lf<===\n",  lit);
};

// Literal operator for user-defined CHARACTER literal
void operator "" _dump(char lit)
{
    printf("operator \"\" _dump(char)                   : ===>%c<===\n",   lit);
};

void operator "" _dump(wchar_t lit)
{
    printf("operator \"\" _dump(wchar_t)                : ===>%d<===\n",   lit);
};

void operator "" _dump(char16_t lit)
{
    printf("operator \"\" _dump(char16_t)               : ===>%d<===\n",   lit);
};

void operator "" _dump(char32_t lit)
{
    printf("operator \"\" _dump(char32_t)               : ===>%d<===\n",   lit);
};

// Literal operator for user-defined STRING literal
void operator "" _dump(const     char* lit, size_t)
{
    printf("operator \"\" _dump(const     char*, size_t): ===>%s<===\n",   lit);
};

void operator "" _dump(const  wchar_t* lit, size_t)
{
    printf("operator \"\" _dump(const  wchar_t*, size_t): ===>%ls<===\n",  lit);
};

void operator "" _dump(const char16_t* lit, size_t)
{
    printf("operator \"\" _dump(const char16_t*, size_t):\n"                  );
};

void operator "" _dump(const char32_t* lit, size_t)
{
    printf("operator \"\" _dump(const char32_t*, size_t):\n"                  );
};

// Raw literal operator
void operator "" _dump_raw(const char* lit)
{
    printf("operator \"\" _dump_raw(const char*)        : ===>%s<===\n",   lit);
};

template<char...> void operator "" _dump_template();       // Literal operator template

int main(int argc, const char* argv[])
{
    42_dump;
    3.1415926_dump;
    3.14e+25_dump;
     'A'_dump;
    L'B'_dump;
    u'C'_dump;
    U'D'_dump;
      "Hello World"_dump;
     L"Wide String"_dump;
    u8"UTF-8 String"_dump;
     u"UTF-16 String"_dump;
     U"UTF-32 String"_dump;
    42_dump_raw;
    3.1415926_dump_raw;
    3.14e+25_dump_raw;

    // There is no raw literal operator or literal operator template support on these types:
    //  'A'_dump_raw;
    // L'B'_dump_raw;
    // u'C'_dump_raw;
    // U'D'_dump_raw;
    //   "Hello World"_dump_raw;
    //  L"Wide String"_dump_raw;
    // u8"UTF-8 String"_dump_raw;
    //  u"UTF-16 String"_dump_raw;
    //  U"UTF-32 String"_dump_raw;
}
```

```Output
operator "" _dump(unsigned long long int) : ===>42<===
operator "" _dump(long double)            : ===>3.141593<===
operator "" _dump(long double)            : ===>31399999999999998506827776.000000<===
operator "" _dump(char)                   : ===>A<===
operator "" _dump(wchar_t)                : ===>66<===
operator "" _dump(char16_t)               : ===>67<===
operator "" _dump(char32_t)               : ===>68<===
operator "" _dump(const     char*, size_t): ===>Hello World<===
operator "" _dump(const  wchar_t*, size_t): ===>Wide String<===
operator "" _dump(const     char*, size_t): ===>UTF-8 String<===
operator "" _dump(const char16_t*, size_t):
operator "" _dump(const char32_t*, size_t):
operator "" _dump_raw(const char*)        : ===>42<===
operator "" _dump_raw(const char*)        : ===>3.1415926<===
operator "" _dump_raw(const char*)        : ===>3.14e+25<===
```
