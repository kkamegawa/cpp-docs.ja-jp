---
title: /TLBOUT (.TLB ファイル名の指定)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.TypeLibraryFile
- /tlbout
helpviewer_keywords:
- tlb files, renaming
- TLBOUT linker option
- /TLBOUT linker option
- .tlb files, renaming
- -TLBOUT linker option
ms.assetid: 0df6d078-2e48-46c9-a1a5-02674d85dce8
ms.openlocfilehash: 4e04514933a521bbf9d927fa6b47bacb87896353
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317641"
---
# <a name="tlbout-name-tlb-file"></a>/TLBOUT (.TLB ファイル名の指定)

```
/TLBOUT:[path\]filename
```

## <a name="arguments"></a>引数

*path*<br/>
.Tlb ファイルを作成する必要があります絶対または相対パス仕様。

*ファイル名*<br/>
MIDL コンパイラによって作成された .tlb ファイルの名前を指定します。 ファイル拡張子は想定されていません。指定*filename*.tlb 拡張子 .tlb を付加する場合。

## <a name="remarks"></a>Remarks

/TLBOUT オプションは、.tlb ファイルの拡張子と名前を指定します。

持つプロジェクトをリンクするときに、MIDL コンパイラは、MSVC リンカーによって呼び出されます、[モジュール](../../windows/module-cpp.md)属性。

.Tlb ファイルから、その名前を受け取ります/TLBOUT が指定されていない場合[/IDLOUT](idlout-name-midl-output-files.md) *filename*します。 /IDLOUT が指定されていない場合、.tlb ファイルには、vc70.tlb が呼び出されます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**埋め込み IDL**プロパティ ページ。

1. 変更、**タイプ ライブラリ**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TypeLibraryFile%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)<br/>
[/IGNOREIDL (属性を MIDL に挿入しない)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (MIDL コマンド ライン オプションの指定)](midl-specify-midl-command-line-options.md)<br/>
[属性付きプログラムの作成](../../windows/building-an-attributed-program.md)
