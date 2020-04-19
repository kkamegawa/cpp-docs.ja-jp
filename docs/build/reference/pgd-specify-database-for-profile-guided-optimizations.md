---
title: /PGD (ガイド付き最適化のプロファイル用のデータベースの指定)
ms.date: 03/14/2018
f1_keywords:
- VC.Project.VCLinkerTool.ProfileGuidedDatabase
helpviewer_keywords:
- -PGD linker option
- /PGD linker option
ms.assetid: 9f312498-493b-461f-886f-92652257e443
ms.openlocfilehash: e1d7c9fcb94a9351ce94b66e04b4bfc523248f4e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319799"
---
# <a name="pgd-specify-database-for-profile-guided-optimizations"></a>/PGD (ガイド付き最適化のプロファイル用のデータベースの指定)

**/PGD オプションが非推奨とされます。** 必要に応じて、Visual Studio 2015 以降、 [/GENPROFILE または/FASTGENPROFILE](genprofile-fastgenprofile-generate-profiling-instrumented-build.md)リンカー オプションの代わりにします。 このオプションを使用して、プロファイル ガイド付き最適化のプロセスによって使用される .pgd ファイルの名前を指定します。

## <a name="syntax"></a>構文

> **/PGD:**_ファイル名_

## <a name="argument"></a>引数

*ファイル名*<br/>
実行中のプログラムに関する情報を保持するために使用される .pgd ファイルの名前を指定します。

## <a name="remarks"></a>Remarks

非推奨を使用する場合[/LTCG:PGINSTRUMENT](ltcg-link-time-code-generation.md)オプションを使用して **/PGD**既定以外の名前または .pgd ファイルの場所を指定します。 指定しない場合 **/PGD**、.pgd ファイルのベース名は、出力ファイル (.exe または .dll) のベース名と同じとリンクを開いたのと同じディレクトリに作成されます。

非推奨を使用する場合 **/LTCG:PGOPTIMIZE**オプションを使用して、 **/PGD**オプションを使用して、最適化されたイメージを作成する .pgd ファイルの名前を指定します。 *Filename*引数に一致する必要があります、 *filename*に対して指定された **/LTCG:PGINSTRUMENT**。

詳細については、次を参照してください。[ガイド付き最適化の](../profile-guided-optimizations.md)します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **最適化**プロパティ ページ。

1. 変更、**プロファイル ガイド付きデータベース**プロパティ。 **OK** を選択して変更を保存してください。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)<br/>
