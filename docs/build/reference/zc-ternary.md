---
title: /Zc:ternary (条件演算子ルールの強制)
ms.date: 09/12/2019
f1_keywords:
- /Zc:ternary
helpviewer_keywords:
- /Zc:ternary
- Zc:ternary
- -Zc:ternary
ms.openlocfilehash: 5c38a09b92b4173ca962412a413abc283db590ff
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927504"
---
# <a name="zcternary-enforce-conditional-operator-rules"></a>/Zc:ternary (条件演算子ルールの強制)

条件演算子式C++の2番目と3番目のオペランドの型および const または volatile (cv) 修飾子に対して、標準規則の適用を有効にします。

## <a name="syntax"></a>構文

> **/Zc:ternary**[ **-** ]

## <a name="remarks"></a>Remarks

Visual Studio 2017 以降では、コンパイラはC++標準の*条件演算子*( **?:** ) 動作をサポートしています。 これは、*三項演算子*とも呼ばれます。 標準C++では、次の3つの条件のいずれかを満たす必要があります。オペランドは、同じ型、 **const**または**volatile**修飾子 (cv 修飾子) である必要があります。または、1つのオペランドだけを同じ型に明確に変換できる必要があります。 または、一方または両方のオペランドが throw 式である必要があります。 Visual Studio 2017 バージョン15.5 より前のバージョンでは、コンパイラは標準であいまいと見なされる変換を許可していました。

**/Zc: 三項**オプションを指定すると、コンパイラは標準に準拠します。 一致する型の規則を満たしていないコードと、2番目と3番目のオペランドの cv 修飾子を拒否します。

**/Zc: 三項**オプションは、Visual Studio 2017 では既定でオフになっています。 以前の非準拠コンパイラの動作を明示的に指定するには、 **/zc: 三項**を使用して、準拠の動作を有効にするか、 **/zc: 三項**を使用します。 [/Permissive-](permissive-standards-conformance.md)オプションはこのオプションを暗黙的に有効にしますが、 **/zc: 三項-** を使用してオーバーライドできます。

### <a name="examples"></a>使用例

このサンプルでは、型からの非明示的な初期化と型への変換の両方を提供するクラスがあいまいな変換につながる可能性があることを示します。 このコードは、既定ではコンパイラによって受け入れられますが、 **/zc: 三項**または **/permissive-** が指定されている場合は拒否されます。

```cpp
// zcternary1.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary1.cpp

struct A
{
   long l;
   A(int i) : l{i} {}    // explicit prevents conversion of int
   operator int() const { return static_cast<int>(l); }
};

int main()
{
   A a(42);
   // Accepted when /Zc:ternary (or /permissive-) is not used
   auto x = true ? 7 : a;  // old behavior prefers A(7) over (int)a
   auto y = true ? A(7) : a;   // always accepted
   auto z = true ? 7 : (int)a; // always accepted
   return x + y + z;
}
```

このコードを修正するには、優先共通型への明示的なキャストを行うか、型変換の一方向を回避します。 変換を明示的に行うことによって、コンパイラが型変換に一致しないようにすることができます。

この一般的なパターンの重要な例外は`const char*`、オペランドの型が、 `const char16_t*`、など、null で終わる文字列型の1つである場合です。 また、配列型と、それらが減衰するポインター型を使用して効果を再現することもできます。 の実際の2番目または3番`?:`目のオペランドが、対応する型の文字列リテラルである場合の動作は、使用される言語標準によって異なります。 C++17 では、C++14 からこのケースのセマンティクスが変更されています。 その結果、コンパイラは、次の例のコードを既定の **/std:c++14**の下で受け入れますが、 **/std:c++17**を指定すると、このコードは拒否されます。

```cpp
// zcternary2.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /std:c++17 zcternary2.cpp

struct MyString
{
   const char * p;
   MyString(const char* s = "") noexcept : p{s} {} // from char*
   operator const char*() const noexcept { return p; } // to char*
};

int main()
{
   MyString s;
   auto x = true ? "A" : s; // MyString: permissive prefers MyString("A") over (const char*)s
}
```

このコードを修正するには、いずれかのオペランドを明示的にキャストします。

**/Zc: 三項**では、コンパイラは、引数のいずれかが**void**型で、もう一方が throw 式ではない条件演算子を拒否します。 このパターンの一般的な用途は、アサートに似たマクロです。

```cpp
// zcternary3.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary /c zcternary3.cpp

void myassert(const char* text, const char* file, int line);
#define ASSERT(ex) (void)((ex) ? 0 : myassert(#ex, __FILE__, __LINE__))
// To fix, define it this way instead:
// #define ASSERT(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))

int main()
{
   ASSERT(false);  // C3447
}
```

一般的な解決策は、void 以外の引数をに`void()`置き換えることです。

このサンプルでは、 **/zc: 三項**と **/zc: 三項-: の**両方でエラーが生成されるコードを示します。

```cpp
// zcternary4.cpp
// Compile by using:
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp
//   cl /EHsc /W4 /nologo /Zc:ternary zcternary4.cpp

int main() {
   auto p1 = [](int a, int b) { return a > b; };
   auto p2 = [](int a, int b) { return a > b; };
   auto p3 = true ? p1 : p2; // C2593 under /Zc:ternary, was C2446
}
```

このコードでは、以前に次のエラーが発生しました。

```Output
error C2446: ':': no conversion from 'foo::<lambda_f6cd18702c42f6cd636bfee362b37033>' to 'foo::<lambda_717fca3fc65510deea10bc47e2b06be4>'
note: No user-defined-conversion operator available that can perform this conversion, or the operator cannot be called
```

**/Zc: 三項**を使用すると、エラーの原因が明確になります。 実装で定義されたいくつかの呼び出し規約を使用して、各ラムダを生成できます。 ただし、コンパイラは、使用可能なラムダ署名を明確に区別するための優先順位規則を持ちません。 新しい出力は次のようになります。

```Output
error C2593: 'operator ?' is ambiguous
note: could be 'built-in C++ operator?(bool (__cdecl *)(int,int), bool (__cdecl *)(int,int))'
note: or       'built-in C++ operator?(bool (__stdcall *)(int,int), bool (__stdcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__fastcall *)(int,int), bool (__fastcall *)(int,int))'
note: or       'built-in C++ operator?(bool (__vectorcall *)(int,int), bool (__vectorcall *)(int,int))'
note: while trying to match the argument list '(foo::<lambda_717fca3fc65510deea10bc47e2b06be4>, foo::<lambda_f6cd18702c42f6cd636bfee362b37033>)'
```

**/Zc: 三項**で見つかった問題の一般的な原因は、テンプレートメタプログラミングで使用される条件演算子です。 このスイッチでは、結果の種類の一部が変更されます。 次の例は、 **/zc: 三項**が非メタプログラミングコンテキストで条件式の結果型を変更する2つのケースを示しています。

```cpp
// zcternary5.cpp
// Compile by using: cl /EHsc /W4 /nologo /Zc:ternary zcternary5.cpp

int main(int argc, char**) {
   char a = 'A';
   const char b = 'B';
   decltype(auto) x = true ? a : b; // char without, const char& with /Zc:ternary
   const char(&z)[2] = argc > 3 ? "A" : "B"; // const char* without /Zc:ternary
   return x > *z;
}
```

一般的な修正では、以前`std::remove_reference`の動作を維持するために必要な場合に、結果の種類に特徴を適用します。

Visual C++ の準拠に関する問題について詳しくは、「 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)」をご覧ください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[構成プロパティ]**  >  **[C/C++]**  >  **[コマンド ライン]** プロパティ ページを選択します。

1. **[追加オプション]** プロパティを、 **/zc: 三項**または **/zc: 三項**を含むように変更し、[ **OK]** を選択します。

## <a name="see-also"></a>関連項目

[/Zc (準拠)](zc-conformance.md)
