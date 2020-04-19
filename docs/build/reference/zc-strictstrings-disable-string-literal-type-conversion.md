---
title: /Zc:strictStrings (文字列リテラル型の変換の無効化)
ms.date: 03/06/2018
f1_keywords:
- /Zc:strictStrings
- strictStrings
helpviewer_keywords:
- /Zc:strictStrings
- -Zc compiler options (C++)
- strictStrings
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
ms.openlocfilehash: 954088955a3f1530bb298aadbc35c7dd74150b7a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315665"
---
# <a name="zcstrictstrings-disable-string-literal-type-conversion"></a>/Zc:strictStrings (文字列リテラル型の変換の無効化)

指定された場合、コンパイラは、文字列リテラルを使用して初期化されたポインターに対して `const` 修飾による標準への厳密な準拠を要求します。

## <a name="syntax"></a>構文

> **/Zc:strictStrings**[**-**]

## <a name="remarks"></a>Remarks

場合 **/Zc:strictStrings**を指定すると、コンパイラは、標準の C++`const`型として、文字列リテラルの 'の配列`const char`' または 'の配列`const wchar_t`' 宣言によって、します。 文字列リテラルは変更不可であり、文字列リテラルの内容を変更しようとすると、実行時にアクセス違反エラーが発生します。 文字列ポインターは `const` として宣言して文字列リテラルで初期化するか、明示的な `const_cast` を使用して非 `const` ポインターを初期化する必要があります。 既定では、場合 **/Zc:strictStrings-** を指定すると、コンパイラは C++ の標準を強制しない`const`文字列リテラルを使用して初期化された文字列ポインターの制限があります。

**/Zc:strictStrings**オプションは既定でオフです。 [/Permissive -](permissive-standards-conformance.md)コンパイラ オプションでは、このオプションは、暗黙的に設定しますを使用してオーバーライドできます **/Zc:strictStrings-** します。

使用して、 **/Zc:strictStrings**不適切なコードのコンパイルを回避するにはオプションです。 この例では、単純な宣言エラーが実行時のクラッシュを招くことを示しています。

```cpp
// strictStrings_off.cpp
// compile by using: cl /W4 strictStrings_off.cpp
int main() {
   wchar_t* str = L"hello";
   str[2] = L'a'; // run-time error: access violation
}
```

ときに **/Zc:strictStrings**が有効にすると、同じコードでの宣言でエラーを報告`str`します。

```cpp
// strictStrings_on.cpp
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp
int main() {
   wchar_t* str = L"hello"; // error: Conversion from string literal
   // loses const qualifier
   str[2] = L'a';
}
```

`auto` を使用して文字列ポインターを宣言すると、正しい `const` ポインター型宣言がコンパイラによって作成されます。 `const` ポインターの内容を変更しようとすると、コンパイラによってエラーとして報告されます。

> [!NOTE]
> Visual Studio 2013 での C++ 標準ライブラリはサポートしていません、 **/Zc:strictStrings**デバッグ コンパイラ オプションをビルドします。 いくつか表示される場合[C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md)ビルドでエラー出力、原因があります。

Visual C++ の準拠に関する問題について詳しくは、「 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)」をご覧ください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. 変更、**追加オプション**含めるプロパティを **/Zc:strictStrings**選び、 **OK**します。

## <a name="see-also"></a>関連項目

[/Zc (準拠)](zc-conformance.md)<br/>
