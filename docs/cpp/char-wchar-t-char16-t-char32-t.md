---
title: char、wchar_t、char16_t、char32_t
ms.date: 02/14/2018
f1_keywords:
- char_cpp
- char16_t_cpp
- wchar_t_cpp
- char32_t_cpp
ms.assetid: 6b33e9f5-455b-4e49-8f12-a150cbfe2e5b
ms.openlocfilehash: 542751cdbd5bb21bb70467163c823e2669373e24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331169"
---
# <a name="char-wchar_t-char16_t-char32_t"></a>char、wchar_t、char16_t、char32_t

**char**、 **wchar_t**、 **char16_t** `および **char32_t**型は、英数字以外のグリフや非印字文字を表す組み込み型です。

## <a name="syntax"></a>構文

```cpp
char     ch1{ 'a' };  // or { u8'a' }
wchar_t  ch2{ L'a' };
char16_t ch3{ u'a' };
char32_t ch4{ U'a' };
```

## <a name="remarks"></a>Remarks

**char** 型は、C および C++ に由来する文字型です。 **unsigned char**型はC++で組み込み型ではない*バイト*を表現するためによく使用されます。 **char**型は、ASCII文字セットやISO-8859文字セットのいずれかの文字、Shift-JISやUnicode文字セットのUTF-8エンコーディングなどのマルチバイト文字の個々のバイトを格納するために使用できます。 **char**型の文字列は、マルチ バイト文字のエンコードに使用する場合でも、ナロー文字列と*呼ばれます*。 Microsoft コンパイラで**char**は、8 ビット型です。

**wchar_t**型は、ワイド文字の実装定義型です。 Microsoft コンパイラでするのに対して、UTF 16LE としてエンコードされた Unicode の格納に使用する 16 ビットのワイド文字を表す Windows オペレーティング システムでネイティブ文字の種類。 ユニバーサル C ランタイム (UCRT) ライブラリの関数の使用方法のワイド文字バージョン**wchar_t**し、そのポインターと配列の型パラメーターと戻り値としては、ネイティブ Windows API のワイド文字バージョンです。

**char16_t**と**char32_t**型はそれぞれ 16 ビットおよび 32 ビットのワイド文字を表します。 Unicode utf-16 に格納できるようにエンコード、 **char16_t**型、および Unicode utf-32 に格納できるようにエンコード、 **char32_t**型。 これらの型の文字列と**wchar_t**はすべて呼ば*ワイド*多くの場合とは具体的には文字列の場合は、文字列**wchar_t**型。

C++ 標準ライブラリで、`basic_string`ナローとワイドの両方の文字列の型が特殊化します。 使用`std::string`型の文字が場合**char**、`std::u16string`型の文字が場合**char16_t**、`std::u32string`型の文字が場合**char32_t**、および`std::wstring`型の文字が場合**wchar_t**します。 その他のテキストを表す型を含む`std::stringstream`と`std::cout`ナローとワイド文字列の特殊化があります。