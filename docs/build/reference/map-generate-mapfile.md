---
title: /MAP (マップ ファイルの生成)
ms.date: 11/04/2016
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
helpviewer_keywords:
- mapfiles, creating linker
- generate mapfile linker option
- mapfile linker option
- mapfiles, information about program being linked
- MAP linker option
- -MAP linker option
- mapfiles, specifying file name
- /MAP linker option
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
ms.openlocfilehash: 9a45fd5ea44b8908e77f847275bde42b86385cdb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321606"
---
# <a name="map-generate-mapfile"></a>/MAP (マップ ファイルの生成)

```
/MAP[:filename]
```

## <a name="arguments"></a>引数

*ファイル名*<br/>
マップ ファイルのユーザー指定の名前。 既定の名前が置き換えられます。

## <a name="remarks"></a>Remarks

/MAP オプションを使用すると、リンカーは、マップ ファイルを作成します。

既定では、リンカーは、プログラムと拡張機能の .map の基本名を持つマップ ファイルを名します。 省略可能な*filename*マップ ファイルの既定の名前をオーバーライドすることができます。

マップ ファイルは、リンクされているプログラムに関する次の情報を含むテキスト ファイルです。

- これは、ファイルの基本名モジュール名

- (ファイル システム) からではなく、プログラム ファイルのヘッダーからのタイムスタンプ

- 各グループの開始アドレスと、プログラムでは、グループの一覧 (として*セクション*:*オフセット*)、長さ、グループ名、およびクラス

- 各アドレスに、パブリック シンボルの一覧 (として*セクション*:*オフセット*)、名前、フラット アドレス、およびシンボルが定義されている .obj ファイルのシンボル

- エントリ ポイント (として*セクション*:*オフセット*)

[/MAPINFO](mapinfo-include-information-in-mapfile.md)オプションは、マップ ファイルに含まれる追加の情報を指定します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**デバッグ**プロパティ ページ。

1. 変更、**マップ ファイルの生成**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A> 」および「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>」を参照してください。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
