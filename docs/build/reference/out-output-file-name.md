---
title: /OUT (出力ファイル名)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- /out
helpviewer_keywords:
- output files, name linker option
- -OUT linker option
- OUT linker option
- /OUT C++ linker option
- linker [C++], output files
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
ms.openlocfilehash: be5fe929bdcf52be19955a5bc2d7aa093e194f45
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320072"
---
# <a name="out-output-file-name"></a>/OUT (出力ファイル名)

```
/OUT:filename
```

## <a name="arguments"></a>引数

*ファイル名*<br/>
ユーザーが指定した出力ファイルの名前。 既定の名前が置き換えられます。

## <a name="remarks"></a>Remarks

/OUT オプションには、既定の名前と、リンカーによって作成されるプログラムの場所がオーバーライドされます。

既定では、リンカーは、最初に指定された .obj ファイル (.exe または .dll) には、適切な拡張機能のベース名を使用して、ファイル名を形成します。

これは、オプションはマップまたはインポート ライブラリの既定の基本名。 詳細については、次を参照してください。[マップ ファイルの生成](map-generate-mapfile.md)(/map) と[/IMPLIB](implib-name-import-library.md)します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**全般**プロパティ ページ。

1. 変更、**出力ファイル**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
