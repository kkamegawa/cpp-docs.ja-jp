---
title: /IDLOUT (MIDL 出力ファイルの指定)
ms.date: 11/04/2016
f1_keywords:
- /idlout
- VC.Project.VCLinkerTool.MergedIDLBaseFileName
helpviewer_keywords:
- MIDL, output file names
- .idl files, path
- MIDL
- /IDLOUT linker option
- IDL files, path
- -IDLOUT linker option
- IDLOUT linker option
ms.assetid: 10d00a6a-85b4-4de1-8732-e422c6931509
ms.openlocfilehash: 3816bb85cb3c711075e3fefeec2d706c2f8cc2ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291577"
---
# <a name="idlout-name-midl-output-files"></a>/IDLOUT (MIDL 出力ファイルの指定)

```
/IDLOUT:[path\]filename
```

## <a name="parameters"></a>パラメーター

*path*<br/>
絶対パスまたは相対パス仕様では。 .Idl ファイルの場所のみに影響するパスを指定すると、その他のすべてのファイルは、プロジェクト ディレクトリに配置されます。

*ファイル名*<br/>
MIDL コンパイラによって作成された .idl ファイルの名前を指定します。 ファイル拡張子は想定されていません。指定*filename*.idl .idl 拡張する場合。

## <a name="remarks"></a>Remarks

/IDLOUT オプションは、.idl ファイルの拡張機能と名前を指定します。

持つプロジェクトをリンクするときに、MIDL コンパイラは、MSVC リンカーによって呼び出されます、[モジュール](../../windows/module-cpp.md)属性。

/IDLOUT には、MIDL コンパイラに関連付けられているその他の出力ファイルのファイル名も指定します。

- *ファイル名*.tlb

- *filename*_p.c

- *filename*_i.c

- *ファイル名*.h

*ファイル名*/IDLOUT に渡すパラメーターです。 場合[/TLBOUT](tlbout-name-dot-tlb-file.md) /TLBOUT からその名前を取得、.tlb ファイル指定*filename*します。

/IDLOUT も/TLBOUT を指定する場合、リンカーは、vc70.tlb、vc70.idl、vc70_p.c、vc70_i.c、および vc70.h に作成されます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**埋め込み IDL**プロパティ ページ。

1. 変更、 **IDL ベース ファイル名のマージ**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MergedIDLBaseFileName%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)<br/>
[/IGNOREIDL (属性を MIDL に挿入しない)](ignoreidl-don-t-process-attributes-into-midl.md)<br/>
[/MIDL (MIDL コマンド ライン オプションの指定)](midl-specify-midl-command-line-options.md)<br/>
[属性付きプログラムの作成](../../windows/building-an-attributed-program.md)
