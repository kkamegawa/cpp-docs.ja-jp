---
title: /MIDL (MIDL コマンド ライン オプションの指定)
ms.date: 09/05/2018
f1_keywords:
- /midl
- VC.Project.VCLinkerTool.MidlCommandFile
helpviewer_keywords:
- -MIDL linker option
- MIDL
- /MIDL linker option
- MIDL linker option
- MIDL, command line options
ms.assetid: 22dc259e-b34c-4ed3-a380-4beb734482c1
ms.openlocfilehash: ca172428943d2446490eeb10741966f5e8c9ea85
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492716"
---
# <a name="midl-specify-midl-command-line-options"></a>/MIDL (MIDL コマンド ライン オプションの指定)

MIDL コマンドラインオプションの応答ファイルを指定します。

## <a name="syntax"></a>構文

> **/MIDL:\@** <em>ファイル</em>

## <a name="arguments"></a>引数

*file*<br/>
[MIDL コマンドラインオプション](/windows/win32/Midl/general-midl-command-line-syntax)を含むファイルの名前。

## <a name="remarks"></a>Remarks

IDL ファイルから TLB ファイルへの変換に関するすべてのオプションは、*ファイル*で指定する必要があります。MIDL コマンドラインオプションは、リンカーのコマンドラインでは指定できません。 /Midl が指定されていない場合は、IDL ファイル名のみを使用して MIDL コンパイラが呼び出され、その他のオプションは呼び出されません。

ファイルには、1行につき1つの MIDL コマンドラインオプションが含まれている必要があります。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. [**構成プロパティ** > ] [**リンカー** > **埋め込み IDL**プロパティ] ページを選択します。

1. **MIDL コマンド**のプロパティを変更します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MidlCommandFile%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)<br/>
[/IDLOUT (MIDL 出力ファイルの指定)](idlout-name-midl-output-files.md)<br/>
[/IGNOREIDL (属性を MIDL に挿入しない)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/TLBOUT (.TLB ファイル名の指定)](tlbout-name-dot-tlb-file.md)<br/>
[属性付きプログラムの作成](../../windows/building-an-attributed-program.md)
