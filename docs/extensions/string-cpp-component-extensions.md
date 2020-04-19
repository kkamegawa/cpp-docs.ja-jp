---
title: 文字列 (C++/CLI および C++/CX)
ms.date: 10/08/2018
ms.topic: reference
helpviewer_keywords:
- string support with /clr
- /clr compiler option [C++], string support
ms.assetid: c695f965-9be0-4e20-9661-373bfee6557e
ms.openlocfilehash: 8440ddf510f99618c28a6b6d585c8628df85f9cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516027"
---
# <a name="string--ccli-and-ccx"></a>文字列 (C++/CLI および C++/CX)

Windows ランタイムと共通言語ランタイムでは、割り当てられたメモリを自動的に管理するオブジェクトとして文字列を表します。 つまり、文字列変数がスコープから外れたりアプリケーションが終了したりしたときに文字列のメモリを明示的に破棄する必要はありません。 文字列オブジェクトの有効期間が自動的に管理されることを示すには、文字列型の宣言で[オブジェクトを識別するハンドル (^)](handle-to-object-operator-hat-cpp-component-extensions.md) を修飾子として指定します。

## <a name="windows-runtime"></a>Windows ランタイム

Windows ランタイム アーキテクチャでは、 `String` データ型は `Platform` 名前空間に配置される必要があります。 これを簡単にするために、Visual C++ では、`string` のシノニムとして、`Platform::String` 名前空間に用意されている `default` データ型を使用することもできます。

### <a name="syntax"></a>構文

```cpp
// compile with /ZW
using namespace Platform;
using namespace default;
   Platform::String^ MyString1 = "The quick brown fox";
   String^ MyString2 = "jumped over the lazy dog.";
   String^ MyString3 = "Hello, world!";
```

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

`/clr` を指定してコンパイルする場合、文字列リテラルは <xref:System.String> 型の文字列に変換されます。 これには、既存のコードとの下位互換性を維持するために 2 つの例外があります。

- 例外処理。 文字列リテラルがスローされた場合は文字列リテラルとしてキャッチされます。

- テンプレートの推論。 文字列リテラルがテンプレート引数として渡された場合は <xref:System.String> に変換されません。 ただし、汎用引数として渡された文字列リテラルは <xref:System.String> に昇格されます。

また、コンパイラには 3 種類の演算子のサポートが組み込まれています。これらの演算子は、オーバーライドして動作をカスタマイズすることができます。

- System::String^ operator +( System::String, System::String);

- System::String^ operator +( System::Object, System::String);

- System::String^ operator +( System::String, System::Object);

コンパイラに <xref:System.String> が渡されると、必要に応じてボックス化されてから、オブジェクトが文字列と連結されます (ToString を使用)。

> [!NOTE]
> カレット ("^") は、宣言された変数が C++/CLI のマネージド オブジェクトに対するハンドルであることを示します。

詳細については、「[文字列リテラルと文字リテラル](../cpp/string-and-character-literals-cpp.md)」を参照してください。

### <a name="requirements"></a>要件

コンパイラ オプション: **/clr**

### <a name="examples"></a>使用例

文字列を連結して比較するコード例を次に示します。

```cpp
// string_operators.cpp
// compile with: /clr
// In the following code, the caret ("^") indicates that the
// declared variable is a handle to a C++/CLI managed object.
using namespace System;

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   // variables of System::String returning a System::String
   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   // accessing a character in the string
   Console::WriteLine(a[2]);

   // concatenation of three System::Strings
   Console::WriteLine(a + b + c);

   // concatenation of a System::String and string literal
   Console::WriteLine(a + "zzz");

   // you can append to a System::String^
   Console::WriteLine(a + 1);
   Console::WriteLine(a + 'a');
   Console::WriteLine(a + 3.1);

   // test System::String^ for equality
   a += b;
   Console::WriteLine(a);
   a = b;
   if (a == b)
      Console::WriteLine("a and b are equal");

   a = "abc";
   if (a != b)
      Console::WriteLine("a and b are not equal");

   // System:String^ and tracking reference
   String^% rstr1 = a;
   Console::WriteLine(rstr1);

   // testing an empty System::String^
   String^ n;
   if (n == nullptr)
      Console::WriteLine("n is empty");
}
```

```Output
abcdef

abcghi

ghiabc

c

abcdefghi

abczzz

abc1

abc97

abc3.1

abcdef

a and b are equal

a and b are not equal

abc

n is empty
```

コンパイラで提供される演算子をオーバーロードする例を次に示します。コンパイラでは、<xref:System.String> 型に基づいて関数のオーバーロードを探します。

```cpp
// string_operators_2.cpp
// compile with: /clr
using namespace System;

// a string^ overload will be favored when calling with a String
void Test_Overload(const char * a) {
   Console::WriteLine("const char * a");
}
void Test_Overload(String^ a) {
   Console::WriteLine("String^ a");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, String^ b) {
   return ("overloaded +(String^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(Object^ a, String^ b) {
   return ("overloaded +(Object^ a, String^ b)");
}

// overload will be called instead of compiler defined operator
String^ operator +(String^ a, Object^ b) {
   return ("overloaded +(String^ a, Object^ b)");
}

int main() {
   String^ a = gcnew String("abc");
   String^ b = "def";   // same as gcnew form
   Object^ c = gcnew String("ghi");

   char d[100] = "abc";

   Console::WriteLine(a + b);
   Console::WriteLine(a + c);
   Console::WriteLine(c + a);

   Test_Overload("hello");
   Test_Overload(d);
}
```

```Output
overloaded +(String^ a, String^ b)

overloaded +(String^ a, Object^ b)

overloaded +(Object^ a, String^ b)

String^ a

const char * a
```

コンパイラでネイティブの文字列と <xref:System.String> 文字列を区別する例を次に示します。

```cpp
// string_operators_3.cpp
// compile with: /clr
using namespace System;
int func() {
   throw "simple string";   // const char *
};

int func2() {
   throw "string" + "string";   // returns System::String
};

template<typename T>
void func3(T t) {
   Console::WriteLine(T::typeid);
}

int main() {
   try {
      func();
   }
   catch(char * e) {
      Console::WriteLine("char *");
   }

   try {
      func2();
   }
   catch(String^ str) {
      Console::WriteLine("String^ str");
   }

   func3("string");   // const char *
   func3("string" + "string");   // returns System::String
}
```

```Output
char *

String^ str

System.SByte*

System.String
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)<br/>
[文字列リテラルと文字リテラル](../cpp/string-and-character-literals-cpp.md)<br/>
[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)