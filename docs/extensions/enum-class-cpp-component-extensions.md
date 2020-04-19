---
title: enum class (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
ms.assetid: 8010fa8c-bad6-45b4-8214-b4db64d7ffe1
ms.openlocfilehash: da9097a02de08fd1615f5401d08c438c5f64c139
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516597"
---
# <a name="enum-class--ccli-and-ccx"></a>enum class (C++/CLI および C++/CX)

名前空間スコープで列挙型を宣言します。列挙型とは、列挙子と呼ばれる一連の名前付き定数で構成されるユーザー定義型です。

## <a name="all-runtimes"></a>すべてのランタイム

### <a name="remarks"></a>解説

C++/CX および C++/CLI では、**public enum class** と **private enum class** をサポートします。これらは、標準 C++ の **enum class** に似ていますが、アクセシビリティ指定子が追加されている点が異なります。 **/clr** では、C++11 の **enum class** 型を使用できますが、C++/CX と C++/CLI の型ではなく ISO の列挙型でよいかどうかを確認する警告 C4472 が生成されます。 ISO 標準 C++ の **enum** キーワードについて詳しくは、「[列挙型](../cpp/enumerations-cpp.md)」をご覧ください。

## <a name="windows-runtime"></a>Windows ランタイム

### <a name="syntax"></a>構文

```cpp
      access
      enum class
      enumeration-identifier
      [:underlying-type] { enumerator-list } [var];
accessenum structenumeration-identifier[:underlying-type] { enumerator-list } [var];
```

### <a name="parameters"></a>パラメーター

*access*<br/>
列挙型のアクセシビリティ。**public** または **private** を指定できます。

*enumeration-identifier*<br/>
列挙型の名前。

*underlying-type*<br/>
(省略可能) 列挙型の基になる型。

(省略可能、 Windows ランタイムのみ) 列挙型の基になる型。**bool**、**char**、`char16`、`int16`、`uint16`、**int**、`uint32`、`int64`,、または `uint64` を指定できます。

*enumerator-list*<br/>
列挙子名のコンマ区切りのリスト。

それぞれの列挙子の値は、コンパイラによって暗黙的に定義された定数式か、" *enumerator*`=`*constant-expression*」をご覧ください。 既定では、最初の列挙子が暗黙的に定義されている場合、その値は 0 です。 それ以降の暗黙的に定義された列挙子の値は、前の列挙子の値に 1 を加算した値になります。

*var*<br/>
(省略可能) 列挙型の変数の名前。

### <a name="remarks"></a>解説

使用例を含む詳細については、「 [列挙型](../cppcx/enums-c-cx.md)」をご覧ください。

列挙子の値を定義する定数式が *underlying-type*で表すことができない場合、コンパイラはエラー メッセージを生成します。  ただし、基になる型に対して値が不適切であるというエラーは生成されません。 次に例を示します。

- *underlying-type* が数値であり、列挙子がその型の最大値を指定する場合は、次に暗黙的に定義されている列挙型の値は表すことができません。

- *underlying-type* が **bool** であり、3 つ以上の列挙子が暗黙的に定義されている場合、最初の 2 つの列挙子より後の列挙子は表すことができません。

- *underlying-type* が `char16`であり、列挙型の値が 0xD800 から 0xDFFF の範囲にある場合、その値を表すことができます。 この値は Unicode サロゲート ペアの一方を表していますが、このペアは分離して表すことができないため、論理的にはこの値は正しくありません。

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

### <a name="syntax"></a>構文

```cpp
      access
      enum class
      name [:type] { enumerator-list } var;
accessenum structname [:type] { enumerator-list } var;
```

### <a name="parameters"></a>パラメーター

*access*<br/>
列挙型のアクセシビリティ。 **public** または **private** を指定できます。

*enumerator-list*<br/>
列挙型に含まれる識別子 (列挙子) のコンマ区切りのリスト。

*name*<br/>
列挙型の名前。 匿名のマネージド列挙型は使用できません。

*type*<br/>
(省略可能) "*識別子*" の基になる型。 符号付きまたは符号なしの **int**、**short**、**long** など、任意のスカラー型を指定できます。  **bool** または **char** も使用できます。

*var*<br/>
(省略可能) 列挙型の変数の名前。

### <a name="remarks"></a>解説

**enum class** と **enum struct** は同等の宣言です。

列挙型には、マネージド (C++/CX) 列挙型と標準列挙型の 2 種類があります。

マネージド (C++/CX) 列挙型は、たとえば次のように定義されます。

```cpp
public enum class day {sun, mon };
```

これは、次のコードと同じ意味です。

```cpp
ref class day {
public:
   static const int sun = 0;
   static const int mon = 1;
};
```

標準列挙型は、たとえば次のように定義されます。

```cpp
enum day2 { sun, mon };
```

これは、次のコードと同じ意味です。

```cpp
static const int sun = 0;
static const int mon = 1;
```

マネージド列挙子の名前 (*識別子*) は、列挙型が定義されるスコープに挿入されません。列挙子へのすべての参照が完全修飾名であることが必要です (*名前*`::`*識別子*)。  そのため、匿名のマネージド列挙型は定義できません。

標準列挙型の列挙子は外側のスコープに厳密に挿入されます。  そのため、列挙子と同じ名前を持つ別のシンボルが外側のスコープにある場合、コンパイラはエラーを生成します。

Visual Studio 2002 と Visual Studio 2003 では、列挙子は弱く挿入されていました (同じ名前の別の識別子が存在していない限り、外側のスコープで参照可能)。

C++ 標準列挙型が定義されている (**class** または **struct** は指定されていない) 場合、`/clr` を指定してコンパイルすると、列挙型がマネージド列挙型としてコンパイルされます。  この列挙型のセマンティクスはアンマネージ列挙型のままです。  コンパイラは、その列挙型をネイティブ列挙型にするというプログラマの意図を示すために、`Microsoft::VisualC::NativeEnumAttribute` 属性を挿入します。  他のコンパイラは、標準列挙型を単にマネージド列挙型として認識します。

`/clr` を指定してコンパイルされた名前付きの標準列挙型は、アセンブリでマネージド列挙型として参照可能であり、他のマネージド コンパイラでも実行できます。   ただし、名前のない標準列挙体は、アセンブリからパブリックに参照することができません。

Visual Studio 2002 と Visual Studio 2003 では、標準列挙型は関数のパラメーターの型として使用されていました。

```cpp
// mcppv2_enum.cpp
// compile with: /clr
enum E { a, b };
void f(E) {System::Console::WriteLine("hi");}

int main() {
   E myi = b;
   f(myi);
}
```

これは、関数のシグネチャに対応して MSIL に次の出力を行います。

```cpp
void f(int32);
```

ただし、現在のバージョンのコンパイラでは、[NativeEnumAttribute] を指定すると標準列挙型がマネージド列挙型として出力され、関数のシグネチャに対応して MSIL に次の出力を行います。

```cpp
void f(E)
```

ネイティブ列挙型の詳細については、「 [C++ 列挙体の宣言](../cpp/enumerations-cpp.md)」を参照してください。

CLR 列挙型の詳細については、次のページを参照してください。

- [Underlying Type of an Enum (列挙型の基になる型)](../dotnet/how-to-define-and-consume-enums-in-cpp-cli.md)

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

```cpp
// mcppv2_enum_2.cpp
// compile with: /clr
// managed enum
public enum class m { a, b };

// standard enum
public enum n { c, d };

// unnamed, standard enum
public enum { e, f } o;

int main()
{
   // consume managed enum
   m mym = m::b;
   System::Console::WriteLine("no automatic conversion to int: {0}", mym);
   System::Console::WriteLine("convert to int: {0}", (int)mym);

   // consume standard enum
   n myn = d;
   System::Console::WriteLine(myn);

   // consume standard, unnamed enum
   o = f;
   System::Console::WriteLine(o);
}
```

```Output
no automatic conversion to int: b

convert to int: 1

1

1
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)