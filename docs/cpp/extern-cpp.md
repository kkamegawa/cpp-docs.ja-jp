---
title: extern (C++)
description: 言語 extern キーワードC++のガイド。
ms.date: 01/28/2020
f1_keywords:
- extern
- extern_CPP
helpviewer_keywords:
- extern keyword [C++], linkage to non-C++ functions
- declarations, external
- external linkage, extern modifier
ms.assetid: 1e2f0ae3-ae98-4410-85b5-222d6abc865a
no-loc:
- extern
- const
- constexpr
- permissive
ms.openlocfilehash: 422b6960802c59f1c45e0c22a4a85988c808a5b3
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821767"
---
# <a name="opno-locextern-c"></a>extern (C++)

**extern** キーワードは、グローバル変数、関数、またはテンプレート宣言に適用できます。 シンボルに*外部リンケージ*があることを指定します。 リンケージの背景情報と、グローバル変数の使用を推奨しない理由については、「[翻訳単位とリンケージ](program-and-linkage-cpp.md)」を参照してください。

**extern** キーワードには、コンテキストに応じて次の4つの意味があります。

- **const** 以外のグローバル変数宣言では、 **extern** は、変数または関数が別の翻訳単位で定義されていることを指定します。 **extern** は、変数が定義されているものを除くすべてのファイルに適用する必要があります。

- **const** 変数宣言では、変数に外部リンケージがあることを指定します。 **extern** は、すべてのファイルのすべての宣言に適用する必要があります。 (グローバル **const** 変数には、既定で内部リンケージがあります)。

- **extern "c"** は、関数が他の場所で定義され、C 言語の呼び出し規約を使用することを指定します。 extern "C" 修飾子は、ブロック内の複数の関数宣言にも適用できます。

- テンプレート宣言では、 **extern** は、テンプレートが別の場所で既にインスタンス化されていることを指定します。 **extern** は、現在の場所に新しいインスタンスを作成するのではなく、他のインスタンス化を再利用できるようにコンパイラに指示します。 この **extern** の使用方法の詳細については、「[明示的なインスタンス化](explicit-instantiation.md)」を参照してください。

## <a name="opno-locextern-linkage-for-non-opno-locconst-globals"></a>const 以外のグローバルのリンケージの extern

リンカーは、グローバル変数宣言の前に **extern** を認識すると、別の翻訳単位で定義を検索します。 グローバルスコープでの非 **const** 変数の宣言は、既定では外部です。 定義を提供しない宣言にのみ **extern** を適用します。

```cpp
//fileA.cpp
int i = 42; // declaration and definition

//fileB.cpp
extern int i;  // declaration only. same as i in FileA

//fileC.cpp
extern int i;  // declaration only. same as i in FileA

//fileD.cpp
int i = 43; // LNK2005! 'i' already has a definition.
extern int i = 43; // same error (extern is ignored on definitions)
```

## <a name="opno-locextern-linkage-for-opno-locconst-globals"></a>const globals の extern リンケージ

**const** のグローバル変数には、既定で内部リンケージがあります。 変数に外部リンケージを設定する場合は、 **extern** キーワードを定義に、他のファイル内の他のすべての宣言に適用します。

```cpp
//fileA.cpp
extern const int i = 42; // extern const definition

//fileB.cpp
extern const int i;  // declaration only. same as i in FileA
```

## <a name="opno-locextern-opno-locconstexpr-linkage"></a>constexpr リンケージの extern

Visual Studio 2017 バージョン15.3 以前では、変数が **extern** としてマークされている場合でも、コンパイラは常に **constexpr** 変数の内部リンケージを与えました。 Visual Studio 2017 バージョン15.5 以降では、 [/zc: externConstexpr](../build/reference/zc-externconstexpr.md)コンパイラスイッチを使用すると、正しい標準準拠の動作が有効になります。 最終的には、このオプションが既定値になります。 [/permissive-](../build/reference/permissive-standards-conformance.md)オプションでは、 **/zc: externConstexpr**は有効になりません。

```cpp
extern constexpr int x = 10; //error LNK2005: "int const x" already defined
```

ヘッダーファイルに **extern** **constexpr** として宣言された変数が含まれている場合は、重複する宣言を正しく結合するために、`__declspec(selectany)` としてマークする必要があります。

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

## <a name="opno-locextern-c-and-opno-locextern-c-function-declarations"></a>extern "C" および extern "C++" 関数の宣言

でC++は、文字列と共に使用する場合、 **extern** は別の言語のリンケージ規則が宣言子に使用されることを指定します。 C 関数とデータは、以前に C リンケージを持つように宣言されている場合にのみアクセスできます。 ただし、別にコンパイルされた翻訳単位で定義する必要があります。

Microsoft C++では、*文字列リテラル*フィールドに文字列 **"C"** と**C++""** をサポートしています。 すべての標準インクルードファイルは、 **"C" 構文extern** を使用して、プログラムでC++ランタイムライブラリ関数を使用できるようにします。

## <a name="example"></a>使用例

次の例は、C リンケージを持つ名前を宣言する方法を示しています。

```cpp
// Declare printf with C linkage.
extern "C" int printf(const char *fmt, ...);

//  Cause everything in the specified
//  header files to have C linkage.
extern "C" {
    // add your #include statements here
#include <stdio.h>
}

//  Declare the two functions ShowChar
//  and GetChar with C linkage.
extern "C" {
    char ShowChar(char ch);
    char GetChar(void);
}

//  Define the two functions
//  ShowChar and GetChar with C linkage.
extern "C" char ShowChar(char ch) {
    putchar(ch);
    return ch;
}

extern "C" char GetChar(void) {
    char ch;
    ch = getchar();
    return ch;
}

// Declare a global variable, errno, with C linkage.
extern "C" int errno;
```

関数に複数のリンケージ指定がある場合は、それに同意する必要があります。 関数を C とC++リンケージの両方を持つように宣言すると、エラーになります。 また、プログラム内に、リンケージ指定子を含む関数宣言と含まない関数宣言がある場合、リンケージ指定子を含む宣言を最初に記述する必要があります。 既にリンケージ指定を持つ関数の冗長な宣言には、最初の宣言で指定したリンケージが与えられます。 例:

```cpp
extern "C" int CFunc1();
...
int CFunc1();            // Redeclaration is benign; C linkage is
                         //  retained.

int CFunc2();
...
extern "C" int CFunc2(); // Error: not the first declaration of
                         //  CFunc2;  cannot contain linkage
                         //  specifier.
```

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)\
[翻訳単位とリンケージ](program-and-linkage-cpp.md)\
[C\ でのストレージクラス指定子のextern](../c-language/extern-storage-class-specifier.md)
[C\ での識別子の動作](../c-language/behavior-of-identifiers.md)
[C でのリンケージ](../c-language/linkage.md)
