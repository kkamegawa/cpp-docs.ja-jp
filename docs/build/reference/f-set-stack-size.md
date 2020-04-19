---
title: /F (スタック サイズの設定)
ms.date: 11/04/2016
f1_keywords:
- /f
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
ms.openlocfilehash: 9db595daa7de7820b594a8515ece7481b4382c98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293096"
---
# <a name="f-set-stack-size"></a>/F (スタック サイズの設定)

プログラムのスタック サイズをバイト単位で設定します。

## <a name="syntax"></a>構文

> **/F** *number*

## <a name="arguments"></a>引数

*number*<br/>
スタック サイズ (バイト単位)。

## <a name="remarks"></a>Remarks

このオプションを指定せず、スタック サイズは 1 MB に既定値です。 *数*引数は、10 進数または C 言語表記で指定できます。 引数の範囲は 1 からリンカーによって受け付け最大スタック サイズです。 リンカーは、最も近い 4 バイトに指定した値を丸めます。 間のスペース **/F**と*数*は省略可能です。

プログラム スタック オーバーフローのメッセージを取得する場合は、スタック サイズを大きく必要があります。

スタック サイズを設定することもできます。

- 使用して、 **/stack**リンカー オプション。 詳細については、次を参照してください。 [/stack](stack.md)します。

- .Exe ファイルを EDITBIN を使用します。 詳細については、次を参照してください。 [EDITBIN リファレンス](editbin-reference.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
