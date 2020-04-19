---
title: /LINKREPROTARGET (リンク再現ファイル名)
description: リンカーまたはライブラリツールオプションリンクを再現するためのターゲットファイル名を設定します。
ms.date: 09/24/2019
f1_keywords:
- /LINKREPROTARGET
helpviewer_keywords:
- LINKREPROTARGET linker option
- /LINKREPROTARGET linker option
- -LINKREPROTARGET linker option
- linker repro reporting
ms.openlocfilehash: d629c4c2665239d03f38569677fa579b6c8d37e0
ms.sourcegitcommit: a361362354f6ce51eda4ffdb016b81c24cd225cb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71712682"
---
# <a name="linkreprotarget-link-repro-file-name"></a>/LINKREPROTARGET (リンク再現ファイル名)

ターゲットに指定されたファイル名がある場合にのみリンク再現を生成するようにリンカーまたはライブラリツールに指示します。

## <a name="syntax"></a>構文

> **/Linkreprotarget:** _ファイル名_

### <a name="arguments"></a>引数

**/Linkreprotarget:** _ファイル名_\
フィルター処理の対象となるファイルの名前。 リンク再現は、名前付きファイルが出力ターゲットである場合にのみ生成されます。 スペースを含むファイル名は、二重引用符で囲む必要があります。 ファイル名には、ベース名と拡張子を含める必要がありますが、パスは含めないでください。

## <a name="remarks"></a>コメント

**/Linkreprotarget**オプションを使用して、*リンクを再現*するターゲットファイル名を指定します。 リンク再現は、Microsoft がリンク時またはライブラリ操作中に発生する問題を再現できるようにする一連のビルド成果物です。 リンカーまたはライブラリツールは、 [/link再現](linkrepro.md)オプションを指定した場合、またはコマンドラインビルド環境で `link_repro` 環境変数を設定した場合に、リンク再現機能を生成します。

**/Linkreprotarget**オプションは、リンカーまたはライブラリツールを複数回呼び出す複雑なビルドで役に立ちます。 これにより、*問題の .dll*など、リンク再現の特定のターゲットを指定できます。 このツールを使用すると、特定のファイルが生成された場合にのみ、リンク再現を生成できます。

リンク再現の作成方法とタイミングの詳細については、「 [Microsoft C++ツールセットの問題を報告する方法](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)」の「[リンク](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros)の再現」セクションを参照してください。

/ **Linkreprotarget**オプションを有効にするには、 **/link再現**オプションと[/out](out-output-file-name.md)オプションを設定する必要があります。

**/Linkreprotarget**は、Visual Studio 2019 バージョン16.1 以降で使用できます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **構成プロパティ** > **リンカー** > **コマンドライン**プロパティページを選択します。

1. **[追加のオプション]** ボックスに、 **「/linkreprotarget:** _ファイル名_」オプションを入力します。 **[OK]** を選択して変更を適用します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーリファレンス](linking.md)\
[MSVC リンカーオプション](linker-options.md)\
[/LINK再現](linkrepro.md)
