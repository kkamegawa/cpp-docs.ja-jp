---
title: /WINMD (Windows メタデータの生成)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
ms.openlocfilehash: 45d6492c87b7543a54d031f02dcf09e319150131
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449736"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (Windows メタデータの生成)

Windows ランタイム メタデータ (.winmd) ファイルの生成を有効にします。

> **/WINMD**\[ **:** {**NO**\|**ONLY**}]

## <a name="arguments"></a>引数

**/WINMD**<br/>
ユニバーサル Windows プラットフォーム アプリの既定の設定。 リンカーは、バイナリ実行可能ファイルと .winmd のメタデータ ファイルの両方を生成します。

**/WINMD:NO**<br/>
のみ、バイナリ実行可能ファイルですが .winmd ファイルではなく、リンカーが生成されます。

**/WINMD:ONLY**<br/>
.Winmd ファイルのみが、バイナリ実行可能ファイルではなく、リンカーが生成されます。

## <a name="remarks"></a>Remarks

**/WINMD**リンカー オプションは Windows ランタイム メタデータ (.winmd) ファイルの作成を制御する UWP アプリと Windows ランタイム コンポーネントを使用します。 .Winmd ファイルは、Windows ランタイム型と、ランタイム コンポーネントでは、これらの型の実装の場合、メタデータを含んでいる DLL の一種です。 メタデータに依存して、 [ECMA 335](https://www.ecma-international.org/publications/standards/Ecma-335.htm)標準。

既定では、出力ファイル名には、フォーム*binaryname*.winmd します。 別のファイル名を指定するには、使用、 [/WINMDFILE](winmdfile-specify-winmd-file.md)オプション。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. 選択、**構成プロパティ** > **リンカー** > **Windows メタデータ**プロパティ ページ。

1. **Windows メタデータの生成**ドロップダウン リスト ボックスで、目的のオプションを選択します。

## <a name="see-also"></a>関連項目

[チュートリアル: 単純な Windows ランタイム コンポーネントの作成および JavaScript による呼び出し](/windows/uwp/winrt-components/walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript)<br/>
[Microsoft インターフェイス定義言語 3.0 の概要](/uwp/midl-3/intro)<br/>
[/WINMDFILE (winmd ファイルの指定)](winmdfile-specify-winmd-file.md)<br/>
[/WINMDKEYFILE (キー ファイルの指定)](winmdkeyfile-specify-winmd-key-file.md)<br/>
[/WINMDKEYCONTAINER (キー コンテナーの指定)](winmdkeycontainer-specify-key-container.md)<br/>
[/WINMDDELAYSIGN (winmd の部分署名)](winmddelaysign-partially-sign-a-winmd.md)<br/>
[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
