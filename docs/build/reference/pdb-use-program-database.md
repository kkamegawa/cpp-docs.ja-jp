---
title: /PDB (プログラム データベースの使用)
ms.date: 11/04/2016
f1_keywords:
- /pdb
- VC.Project.VCLinkerTool.ProgramDatabaseFile
helpviewer_keywords:
- -PDB linker option
- /PDB linker option
- PDB linker option
- PDB files, creating
- .pdb files, creating
ms.assetid: d23db0ce-10cb-427a-bc60-d6b2a852723d
ms.openlocfilehash: ddcf83cafd5f499158f3116f04e40397b7f8d0a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320085"
---
# <a name="pdb-use-program-database"></a>/PDB (プログラム データベースの使用)

```
/PDB:filename
```

## <a name="arguments"></a>引数

*ファイル名*<br/>
プログラム データベース (PDB)、リンカーによって作成されるユーザー指定の名前。 既定の名前が置き換えられます。

## <a name="remarks"></a>Remarks

既定では、ときに[/debug](debug-generate-debug-info.md)を指定すると、リンカーはデバッグ情報を保持するプログラム データベース (PDB) を作成します。 PDB の既定のファイル名は、プログラムと拡張子 .pdb の基本の名前を持ちます。

/PDB を使用して:*filename* PDB ファイルの名前を指定します。 /DEBUG が指定されていない場合は、/PDB オプションは無視されます。

PDB ファイルには、最大 2 GB を指定できます。

詳細については、次を参照してください。[リンカー入力としての .pdb ファイル](dot-pdb-files-as-linker-input.md)します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**デバッグ**プロパティ ページ。

1. 変更、**プログラム データベース ファイルの生成**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProgramDatabaseFile%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
