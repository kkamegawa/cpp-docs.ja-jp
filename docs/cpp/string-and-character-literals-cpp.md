---
title: 文字列リテラルと文字リテラルC++()
description: でC++文字列リテラルと文字リテラルを宣言して定義する方法。
ms.date: 02/18/2020
f1_keywords:
- R
- L
- u
- u8
- LR
- uR
- u8R
helpviewer_keywords:
- literal strings [C++]
- string literals [C++]
ms.assetid: 61de8f6f-2714-4e7b-86b6-a3f885d3b9df
ms.openlocfilehash: 1b4cfb8059b116b0d91886f5b78b3911e8dc316c
ms.sourcegitcommit: b9aaaebe6e7dc5a18fe26f73cc7cf5fce09262c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504466"
---
# <a name="string-and-character-literals-c"></a>文字列リテラルと文字リテラルC++()

C++ はさまざまな文字列と文字型をサポートし、これらの型のリテラル値を表す方法を提供しています。 ソース コードでは、文字セットを使用して文字リテラルと文字列リテラルの内容を表現します。 ユニバーサル文字名とエスケープ文字を使用すると、基本ソース文字セットのみを使用してあらゆる文字列を表現できます。 未加工文字列リテラルを使用すると、エスケープ文字の使用を避けられるとともに、全種類の文字列リテラルを表すことができます。 また、追加の構築や変換の手順を実行することなく `std::string` リテラルを作成することもできます。

```cpp
#include <string>
using namespace std::string_literals; // enables s-suffix for std::string literals

int main()
{
    // Character literals
    auto c0 =   'A'; // char
    auto c1 = u8'A'; // char
    auto c2 =  L'A'; // wchar_t
    auto c3 =  u'A'; // char16_t
    auto c4 =  U'A'; // char32_t

    // Multicharacter literals
    auto m0 = 'abcd'; // int, value 0x61626364

    // String literals
    auto s0 =   "hello"; // const char*
    auto s1 = u8"hello"; // const char*, encoded as UTF-8
    auto s2 =  L"hello"; // const wchar_t*
    auto s3 =  u"hello"; // const char16_t*, encoded as UTF-16
    auto s4 =  U"hello"; // const char32_t*, encoded as UTF-32

    // Raw string literals containing unescaped \ and "
    auto R0 =   R"("Hello \ world")"; // const char*
    auto R1 = u8R"("Hello \ world")"; // const char*, encoded as UTF-8
    auto R2 =  LR"("Hello \ world")"; // const wchar_t*
    auto R3 =  uR"("Hello \ world")"; // const char16_t*, encoded as UTF-16
    auto R4 =  UR"("Hello \ world")"; // const char32_t*, encoded as UTF-32

    // Combining string literals with standard s-suffix
    auto S0 =   "hello"s; // std::string
    auto S1 = u8"hello"s; // std::string
    auto S2 =  L"hello"s; // std::wstring
    auto S3 =  u"hello"s; // std::u16string
    auto S4 =  U"hello"s; // std::u32string

    // Combining raw string literals with standard s-suffix
    auto S5 =   R"("Hello \ world")"s; // std::string from a raw const char*
    auto S6 = u8R"("Hello \ world")"s; // std::string from a raw const char*, encoded as UTF-8
    auto S7 =  LR"("Hello \ world")"s; // std::wstring from a raw const wchar_t*
    auto S8 =  uR"("Hello \ world")"s; // std::u16string from a raw const char16_t*, encoded as UTF-16
    auto S9 =  UR"("Hello \ world")"s; // std::u32string from a raw const char32_t*, encoded as UTF-32
}
```

文字列リテラルは、プレフィックスを省略することも、 `u8`、 `L`、 `u`、または  `U` プレフィックスを使用することもできます。これらは、それぞれ、ナロー文字 (単一バイトまたは複数バイト)、UTF-8、ワイド文字 (UCS-2 または UTF-16)、UTF-16、UTF-32 エンコーディングを表します。 未加工の文字列リテラルには、これらのエンコーディングの `R`、`u8R`、`LR`、`uR`、および `UR` プレフィックスを含めることができます。  一時的または静的な `std::string` 値を作成するには、文字列リテラルまたは未加工の文字列リテラルを `s` サフィックスと共に使用できます。 詳細については、後述する「[文字列リテラル](#string-literals)」を参照してください。 基本ソース文字セット、ユニバーサル文字名、ソースコードの拡張コードページからの文字の使用の詳細については、「[文字セット](../cpp/character-sets.md)」を参照してください。

## <a name="character-literals"></a>文字リテラル

*文字リテラル* は、定数文字で構成されます。 これは、単一引用符で囲まれた文字で表されます。 文字リテラルには、次の5種類があります。

- たとえば、 **char**型の通常の文字リテラル `'a'`

- **Char**型の utf-8 文字リテラル (c++ 20 では**char8_t** )。たとえば、`u8'a'`

- `wchar_t`型のワイド文字リテラル。たとえば `L'a'`

- たとえば `char16_t`型の UTF-16 文字リテラル `u'a'`

- たとえば `char32_t`型の UTF 32 文字リテラル `U'a'`

文字リテラルに使用される文字には、予約文字 ('\\')、単一引用符 (')、または改行を除く任意の文字を使用できます。 予約文字は、エスケープ シーケンスを使用して指定することができます。 型が文字を保持するのに十分な大きさであれば、文字はユニバーサル文字名を使用して指定することができます。

### <a name="encoding"></a>エンコード

文字リテラルは、プレフィックスに基づいて異なる方法でエンコードされます。

- プレフィックスのない文字リテラルは、通常の文字リテラルです。 実行文字セットで表すことができる単一の文字、エスケープシーケンス、またはユニバーサル文字名を含む通常の文字リテラルの値には、実行文字セットにおけるそのエンコードの数値と同じ値が設定されています。 複数の文字、エスケープシーケンス、またはユニバーサル文字名を含む通常の文字リテラルは、*多文字リテラル*です。 実行文字セットで表現できない多文字リテラルまたは通常の文字リテラルは**int**型であり、その値は実装定義されています。 MSVC については、以下の「 **Microsoft 固有**のセクション」を参照してください。

- `L` プレフィックスで始まる文字リテラルは、ワイド文字リテラルです。 1つの文字、エスケープシーケンス、またはユニバーサル文字名を含むワイド文字リテラルの値には、文字リテラルにが含まれていない限り、実行ワイド文字セットのエンコードの数値と同じ値が設定されます。実行ワイド文字セット。この場合、値は実装定義になります。 複数の文字、エスケープシーケンス、またはユニバーサル文字名を含むワイド文字リテラルの値は、実装によって定義されます。 MSVC については、以下の「 **Microsoft 固有**のセクション」を参照してください。

- `u8` プレフィックスで始まる文字リテラルは、UTF-8 文字リテラルです。 1文字、エスケープシーケンス、またはユニバーサル文字名を含む UTF-8 文字リテラルの値は、1つの UTF-8 コード単位 (C0 コントロールと基本ラテン語に対応) で表すことができる場合は、ISO 10646 コードポイント値と同じ値になります。Unicode ブロック)。 値を1つの UTF-8 コード単位で表すことができない場合、プログラムの形式が正しくありません。 複数の文字、エスケープシーケンス、またはユニバーサル文字名を含む UTF-8 文字リテラルの形式が正しくありません。

- `u` プレフィックスで始まる文字リテラルは、UTF-16 文字リテラルです。 1文字、エスケープシーケンス、またはユニバーサル文字名を含む UTF-16 文字リテラルの値は、1つの UTF-16 コード単位で表すことができる場合は、ISO 10646 コードポイント値と同じ値を持ちます (基本的な多言語面に対応します)。). 値を1つの UTF-16 コード単位で表すことができない場合、プログラムの形式が正しくありません。 複数の文字、エスケープシーケンス、またはユニバーサル文字名を含む UTF-16 文字リテラルの形式が正しくありません。

- `U` プレフィックスで始まる文字リテラルは、32文字リテラルです。 1つの文字、エスケープシーケンス、またはユニバーサル文字名を含む 32 UTF-8 文字リテラルの値には、ISO 10646 のコードポイント値と同じ値が指定されています。 複数の文字、エスケープシーケンス、またはユニバーサル文字名を含む 32 UTF-8 文字リテラルの形式が正しくありません。

### <a name="bkmk_Escape"></a>エスケープシーケンス

エスケープ シーケンスには、単純、8 進数、16 進数という 3 つの種類があります。 エスケープシーケンスには、次のいずれかの値を指定できます。

|値|エスケープ シーケンス|
|-----------|---------------------|
| 改行 | \\n |
| 円記号 | \\\\ |
| 水平タブ | \\t |
| 疑問符 | ? または \\? |
| 垂直タブ | \\v |
| 単一引用符 (') | \\' |
| バックスペース | \\b |
| 二重引用符 (") | \\" |
| キャリッジ リターン | \\r |
| null 文字 | \\0 |
| フォーム フィード | \\f |
| 8 進数 | ooo \\ |
| 警告 (ベル) | \\a |
| 16 進数 | \\xhhh |

8進数のエスケープシーケンスは、円記号とそれに続く 1 ~ 3 桁の8進数のシーケンスです。 8進数のエスケープシーケンスは、3番目の桁よりも早く検出された場合、8進数の数字ではない最初の文字で終了します。 可能な限り最大の8進値は `\377`です。

16進数のエスケープシーケンスは、円記号の後に文字 `x`が続き、その後に1つ以上の16進数のシーケンスが続きます。 先行 0 は無視されます。 通常または u8 のプレフィックスが付いた文字リテラルでは、最大の16進値は0xFF です。 L プレフィックス付きまたは u プレフィックス付きワイド文字リテラルでは、最大の 16 進値は 0xFFFF です。 U プレフィックス付きワイド文字リテラルでは、最大の 16 進値は 0xFFFFFFFF です。

このサンプルコードでは、通常の文字リテラルを使用したエスケープ文字の例をいくつか示します。 同じエスケープシーケンス構文は、他の文字リテラル型に対して有効です。

```cpp
#include <iostream>
using namespace std;

int main() {
    char newline = '\n';
    char tab = '\t';
    char backspace = '\b';
    char backslash = '\\';
    char nullChar = '\0';

    cout << "Newline character: " << newline << "ending" << endl;
    cout << "Tab character: " << tab << "ending" << endl;
    cout << "Backspace character: " << backspace << "ending" << endl;
    cout << "Backslash character: " << backslash << "ending" << endl;
    cout << "Null character: " << nullChar << "ending" << endl;
}
/* Output:
Newline character:
ending
Tab character:  ending
Backspace character:ending
Backslash character: \ending
Null character:  ending
*/
```

円記号 (\\) は、行の末尾に配置されている場合は、行連結文字です。 円記号が文字リテラルとして表示されるようにするには、円記号を 2 つ並べて (`\\`) 入力する必要があります。 行連結文字について詳しくは、「 [Phases of Translation](../preprocessor/phases-of-translation.md)」をご覧ください。

#### <a name="microsoft-specific"></a>Microsoft 固有の仕様

ナロー多文字リテラルから値を作成するために、コンパイラは、1つの引用符の間の文字または文字シーケンスを32ビット整数内の8ビット値に変換します。 リテラル内の複数の文字に対応するバイトが、必要に応じて、上位から下位に入力されます。 次に、通常の規則に従って、整数が変換先の型に変換されます。 たとえば、 **char**値を作成する場合、コンパイラは下位バイトを取得します。 **Wchar_t**または `char16_t` の値を作成するために、コンパイラは下位ワードを受け取ります。 割り当てられたバイトまたはワードを上回るビットが設定された場合、コンパイラは結果が切り捨てられることを警告します。

```cpp
char c0    = 'abcd';    // C4305, C4309, truncates to 'd'
wchar_t w0 = 'abcd';    // C4305, C4309, truncates to '\x6364'
int i0     = 'abcd';    // 0x61626364
```

3桁を超える数値が含まれているように見える8進数のエスケープシーケンスは、3桁の8進数シーケンスとして扱われ、その後に多文字リテラルの文字として後続の数字が続きます。これにより、驚くほどの結果が得られます。 例 :

```cpp
char c1 = '\100';   // '@'
char c2 = '\1000';  // C4305, C4309, truncates to '0'
```

8進数以外の文字が含まれているように見えるエスケープシーケンスは、最後の8進数文字までの8進数シーケンスとして評価され、その後に多文字リテラルの後続の文字として残りの文字が続きます。 Warning C4125 は、8進数以外の最初の文字が10進数の場合に生成されます。 例 :

```cpp
char c3 = '\009';   // '9'
char c4 = '\089';   // C4305, C4309, truncates to '9'
char c5 = '\qrs';   // C4129, C4305, C4309, truncates to 's'
```

`\377` よりも大きい値を持つ8進数のエスケープシーケンスでは、エラー C2022: '*decimal*': 文字に対して大きすぎるというエラーが発生します。

16進数と16進数以外の文字を含むエスケープシーケンスは、最後の16進数文字までの16進数のエスケープシーケンスと、それに続く16進数以外の文字が含まれる多文字リテラルとして評価されます。 16進数字を含まない16進数のエスケープシーケンスでは、コンパイラエラーいう c2153: "16 進数リテラルには少なくとも1つの16進数が必要です" が発生します。

```cpp
char c6 = '\x0050'; // 'P'
char c7 = '\x0pqr'; // C4305, C4309, truncates to 'r'
```

`L` で始まるワイド文字リテラルに多文字シーケンスが含まれている場合は、最初の文字から値が取得され、コンパイラによって警告 C4066 が生成されます。 同等の通常の多文字リテラルの動作とは異なり、後続の文字は無視されます。

```cpp
wchar_t w1 = L'\100';   // L'@'
wchar_t w2 = L'\1000';  // C4066 L'@', 0 ignored
wchar_t w3 = L'\009';   // C4066 L'\0', 9 ignored
wchar_t w4 = L'\089';   // C4066 L'\0', 89 ignored
wchar_t w5 = L'\qrs';   // C4129, C4066 L'q' escape, rs ignored
wchar_t w6 = L'\x0050'; // L'P'
wchar_t w7 = L'\x0pqr'; // C4066 L'\0', pqr ignored
```

**Microsoft 固有**のセクションはここで終了します。

### <a name="bkmk_UCN"></a> ユニバーサル文字名

文字リテラルとネイティブ (未加工ではない) 文字列リテラルでは、ユニバーサル文字名であらゆる文字を表すことができます。  ユニバーサル文字名は、プレフィックス `\U`、8桁の Unicode コードポイント、またはプレフィックス `\u` の後に4桁の Unicode コードポイントが続く形式によって形成されます。 正しい形式のユニバーサル文字名を作成するには、それぞれ、8 桁または 4 桁のすべてが存在する必要があります。

```cpp
char u1 = 'A';          // 'A'
char u2 = '\101';       // octal, 'A'
char u3 = '\x41';       // hexadecimal, 'A'
char u4 = '\u0041';     // \u UCN 'A'
char u5 = '\U00000041'; // \U UCN 'A'
```

#### <a name="surrogate-pairs"></a>サロゲート ペア

ユニバーサル文字名は、サロゲートコードポイント範囲 D800 内の値をエンコードできません-DFFF。 Unicode サロゲート ペアの場合は、 `\UNNNNNNNN`を使用してユニバーサル文字名を指定します。ここで、NNNNNNNN は文字用の 8 桁のコード ポイントです。 必要に応じて、コンパイラによってサロゲートペアが生成されます。

C++03 では、ユニバーサル文字名で表現できたのは文字のサブセットに過ぎず、許可されていた一部のユニバーサル文字名は実際には正しい Unicode 文字を表していませんでした。 この誤りは、C++ 11 標準で修正されました。 C++11 では、文字リテラルと文字列リテラルの両方と識別子でユニバーサル文字名を使用できます。  ユニバーサル文字名について詳しくは、「 [Character Sets](../cpp/character-sets.md)」をご覧ください。 Unicode について詳しくは、「 [Unicode](/windows/win32/intl/unicode)」をご覧ください。 サロゲート ペアについて詳しくは、「 [サロゲート ペアと補助文字](/windows/win32/Intl/surrogates-and-supplementary-characters)」をご覧ください。

## <a name="string-literals"></a>文字列リテラル

文字列リテラルは文字のシーケンスを表し、その全体が、null で終わる文字列を形成します。 文字列は二重引用符で囲む必要があります。 文字列リテラルの種類は次のとおりです。

### <a name="narrow-string-literals"></a>ナロー文字列リテラル

ナロー文字列リテラルは、プレフィックスがなく、二重引用符で区切られ、null で終わる `const char[n]`型の配列です。ここで、n は配列の長さ (バイト単位) です。 ナロー文字列リテラルには、二重引用符 (`"`)、円記号 (`\`)、または改行文字を除く、任意のグラフィック文字を含めることができます。 ナロー文字列リテラルには、上記のエスケープ シーケンスと、1 バイトに収まるユニバーサル文字名を含めることもできます。

```cpp
const char *narrow = "abcd";

// represents the string: yes\no
const char *escaped = "yes\\no";
```

#### <a name="utf-8-encoded-strings"></a>UTF-8 でエンコードされた文字列

UTF-8 でエンコードされた文字列は、u8 プレフィックスが付いた、二重引用符で区切られ、null で終わる `const char[n]`型の配列です。ここで、 *n*は、エンコードされた配列の長さ (バイト単位) です。 u8 プレフィックス付き文字列リテラルには、二重引用符 (`"`)、円記号 (`\`)、または改行文字を除く、任意のグラフィック文字を含めることができます。 u8 プレフィックス付き文字列リテラルには、上記のエスケープ シーケンスと、任意のユニバーサル文字名を含めることもできます。

```cpp
const char* str1 = u8"Hello World";
const char* str2 = u8"\U0001F607 is O:-)";
```

### <a name="wide-string-literals"></a>ワイド文字列リテラル

ワイド文字列リテラルは、null で終わる定数**wchar_t**の配列で、'`L`' にプレフィックスが付けられ、二重引用符 (")、円記号 (\\)、または改行文字を除く任意のグラフィック文字が含まれます。 ワイド文字列リテラルには、上記のエスケープ シーケンスと、任意のユニバーサル文字名を含めることができます。

```cpp
const wchar_t* wide = L"zyxw";
const wchar_t* newline = L"hello\ngoodbye";
```

#### <a name="char16_t-and-char32_t-c11"></a>char16_t および char32_t (C++11)

C++11 では、移植可能な `char16_t` (16 ビット Unicode) および `char32_t` (32 ビット Unicode) 文字型が導入されています。

```cpp
auto s3 = u"hello"; // const char16_t*
auto s4 = U"hello"; // const char32_t*
```

### <a name="raw-string-literals-c11"></a>未加工の文字列リテラル (C++ 11)

未加工文字列リテラルは、任意の文字型の null で終わる配列で、二重引用符 (")、円記号 (\\)、または改行文字を含む任意のグラフィック文字で構成されます。 未加工文字列リテラルは、文字クラスを使用する正規表現や、HTML 文字列、XML 文字列でよく使用されます。 例については、記事「 [C++11 に関する Bjarne Stroustrup の FAQ](http://www.stroustrup.com/C++11FAQ.html)」をご覧ください。

```cpp
// represents the string: An unescaped \ character
const char* raw_narrow = R"(An unescaped \ character)";
const wchar_t* raw_wide = LR"(An unescaped \ character)";
const char*       raw_utf8  = u8R"(An unescaped \ character)";
const char16_t* raw_utf16 = uR"(An unescaped \ character)";
const char32_t* raw_utf32 = UR"(An unescaped \ character)";
```

区切り記号は、16文字までのユーザー定義シーケンスで、未加工の文字列リテラルの始めかっこの直前にあり、終わりかっこの直後に続きます。  たとえば、 `R"abc(Hello"\()abc"` では、区切り記号シーケンスが `abc` で、文字列コンテンツが `Hello"\(`です。 区切り記号を使用することで、二重引用符とかっこの両方を含む未加工の文字列の曖昧さを解消できます。 この文字列リテラルでは、コンパイラエラーが発生します。

```cpp
// meant to represent the string: )"
const char* bad_parens = R"()")";  // error C2059
```

しかし、区切り文字を使用することで、エラーは解決します。

```cpp
const char* good_parens = R"xyz()")xyz";
```

次のように、ソースの改行 (エスケープ文字ではない) を含む未加工の文字列リテラルを作成できます。

```cpp
// represents the string: hello
//goodbye
const wchar_t* newline = LR"(hello
goodbye)";
```

### <a name="stdstring-literals-c14"></a>std:: string リテラル (C++ 14)

`std::string` リテラルは、`"xyz"s` (`s` サフィックスを持つ) として表されるユーザー定義リテラルの標準ライブラリの実装です (下記参照)。 このような種類の文字列リテラルでは、指定されたプレフィックスに応じて、`std::string`、`std::wstring`、`std::u32string`、または `std::u16string`型の一時オブジェクトが生成されます。 プレフィックスが使用されていない場合、上記のように、`std::string` が生成されます。 `L"xyz"s` によって `std::wstring`が生成されます。 `u"xyz"s` によって[std:: u16string](../standard-library/string-typedefs.md#u16string)が生成され、`U"xyz"s` [std:: u32string](../standard-library/string-typedefs.md#u32string)が生成されます。

```cpp
//#include <string>
//using namespace std::string_literals;
string str{ "hello"s };
string str2{ u8"Hello World" };
wstring str3{ L"hello"s };
u16string str4{ u"hello"s };
u32string str5{ U"hello"s };
```

`s` サフィックスは、未加工の文字列リテラルでも使用できます。

```cpp
u32string str6{ UR"(She said "hello.")"s };
```

`std::string` リテラルは、\<文字列 > ヘッダーファイル内の `std::literals::string_literals` 名前空間で定義されています。 `std::literals::string_literals`、および `std::literals` はいずれも [インライン名前空間](../cpp/namespaces-cpp.md)として宣言されているため、 `std::literals::string_literals` は名前空間 `std`に直接属しているかのように処理されます。

### <a name="size-of-string-literals"></a>文字列リテラルのサイズ

ANSI `char*` 文字列およびその他の1バイトエンコーディング (UTF-8 ではない) では、文字列リテラルのサイズ (バイト単位) は、終端の null 文字の文字数に1を加えた値になります。 その他のすべての文字列型では、サイズが文字数と厳密に関連していません。 UTF-8 では、最大4つの**char**要素を使用して一部の*コード単位*をエンコードします。また、utf-16 としてエンコードされた `char16_t` または `wchar_t` は、1つの*コード単位*をエンコードするために2つの要素 (合計4バイト) を使用する場合があります。 この例では、ワイド文字列リテラルのサイズがバイト単位で表示されます。

```cpp
const wchar_t* str = L"Hello!";
const size_t byteSize = (wcslen(str) + 1) * sizeof(wchar_t);
```

`strlen()` と `wcslen()` には、終端の null 文字のサイズが含まれていないことに注意してください。サイズは文字列型の要素サイズと同じです。 `char*` または `char8_t*` 文字列の1バイト、`wchar_t*` または `char16_t*` 文字列の2バイト、`char32_t*` 文字列に4バイトです。

文字列リテラルの最大長は65535バイトです。 この制限は、ナローとワイドの両方の文字列リテラルに適用されます。

### <a name="modifying-string-literals"></a>文字列リテラルの変更

文字列リテラル (`std::string` リテラルは含まない) は定数であるため、変更しようとすると (たとえば `str[2] = 'A'`)、コンパイラエラーが発生します。

#### <a name="microsoft-specific"></a>Microsoft 固有の仕様

Microsoft C++では、文字列リテラルを使用して、非 const **char**または**wchar_t**へのポインターを初期化できます。 この非定数初期化は C99 コードで許可されていますが、C++ 98 では非推奨とされており、C++ 11 では削除されています。 文字列を変更すると、この例のようにアクセス違反が発生します。

```cpp
wchar_t* str = L"hello";
str[2] = L'a'; // run-time error: access violation
```

[/Zc: strictStrings (文字列リテラル型の変換を無効にする)](../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md)コンパイラオプションを設定すると、文字列リテラルが非 const 文字ポインターに変換されたときに、コンパイラがエラーを出力することがあります。 標準に準拠した移植可能なコードの場合にこれをお勧めします。 また、 **auto**キーワードを使用して、文字列リテラルに初期化されたポインターを宣言することをお勧めします。これは、正しい (const) 型に解決されるためです。 たとえば、このコード例ではコンパイル時に文字列リテラルへの書き込みの試みがキャッチされます。

```cpp
auto str = L"hello";
str[2] = L'a'; // C3892: you cannot assign to a variable that is const.
```

場合によっては、実行可能ファイルの領域を節約するために、同じ文字列リテラルをプールできます。 文字列リテラルのプールでは、各参照が文字列リテラルの各インスタンスを指すのではなく、コンパイラにより、特定の文字列リテラルへのすべての参照がメモリ内の同じ場所を指します。 文字列プールを有効にするには、 [/GF](../build/reference/gf-eliminate-duplicate-strings.md) コンパイラ オプションを使用します。

**Microsoft 固有**のセクションはここで終了します。

### <a name="concatenating-adjacent-string-literals"></a>隣接する文字列リテラルの連結

隣接するワイド文字列リテラルまたはナロー文字列リテラルは連結されます。 次の宣言は、

```cpp
char str[] = "12" "34";
```

次の宣言と同じです。

```cpp
char atr[] = "1234";
```

次の宣言も同じです。

```cpp
char atr[] =  "12\
34";
```

埋め込みの 16 進数エスケープ コードを使用して文字列リテラルを指定すると、予期しない結果が生じることがあります。 次の例では、ASCII 文字 5 の後に文字列 f、i、v、および e を含む文字列リテラルを作成しようとしています。

```cpp
"\x05five"
```

実際の結果は、16 進数値 5F (アンダースコアの ASCII コード) に文字列 i、v、および e が続きます。 正しい結果を得るには、次のいずれかのエスケープシーケンスを使用します。

```cpp
"\005five"     // Use octal literal.
"\x05" "five"  // Use string splicing.
```

`std::string` リテラルは `std::string` 型であるため、 [basic_string](../standard-library/basic-string-class.md)型に対して定義されている `+` 演算子と連結できます。 隣接する文字列リテラルと同じ方法で連結することもできます。 いずれの場合も、次のように文字列のエンコードとサフィックスは一致していなければなりません。

```cpp
auto x1 = "hello" " " " world"; // OK
auto x2 = U"hello" " " L"world"; // C2308: disagree on prefix
auto x3 = u8"hello" " "s u8"world"s; // OK, agree on prefixes and suffixes
auto x4 = u8"hello" " "s u8"world"z; // C3688, disagree on suffixes
```

### <a name="string-literals-with-universal-character-names"></a>ユニバーサル文字名を持つ文字列リテラル

ネイティブ (未加工でない) 文字列リテラルは、ユニバーサル文字名が文字列型の 1 つ以上の文字としてエンコードできる限り、ユニバーサル文字名を使用して任意の文字を表すことができます。  たとえば、拡張文字を表すユニバーサル文字名は、ANSI コードページを使用してナロー文字列でエンコードすることはできませんが、一部のマルチバイトコードページ、UTF-8 文字列、またはワイド文字列では、ナロー文字列でエンコードすることができます。 C++ 11 では、Unicode のサポートは `char16_t*` と `char32_t*` の文字列型によって拡張されています。

```cpp
// ASCII smiling face
const char*     s1 = ":-)";

// UTF-16 (on Windows) encoded WINKING FACE (U+1F609)
const wchar_t*  s2 = L"😉 = \U0001F609 is ;-)";

// UTF-8  encoded SMILING FACE WITH HALO (U+1F607)
const char*     s3 = u8"😇 = \U0001F607 is O:-)";

// UTF-16 encoded SMILING FACE WITH OPEN MOUTH (U+1F603)
const char16_t* s4 = u"😃 = \U0001F603 is :-D";

// UTF-32 encoded SMILING FACE WITH SUNGLASSES (U+1F60E)
const char32_t* s5 = U"😎 = \U0001F60E is B-)";
```

## <a name="see-also"></a>参照

[文字セット](../cpp/character-sets.md)\
[数値、ブール値、およびポインターのリテラル](../cpp/numeric-boolean-and-pointer-literals-cpp.md)\
[ユーザー定義リテラル](../cpp/user-defined-literals-cpp.md)
