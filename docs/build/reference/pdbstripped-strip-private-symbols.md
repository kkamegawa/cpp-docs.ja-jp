---
title: /PDBSTRIPPED (プライベート シンボルの除去)
ms.date: 11/04/2016
f1_keywords:
- /pdbstripped
- VC.Project.VCLinkerTool.StripPrivateSymbols
helpviewer_keywords:
- /PDBSTRIPPED linker option
- -PDBSTRIPPED linker option
- .pdb files, stripping private symbols
- PDB files, stripping private symbols
- PDBSTRIPPED linker option
ms.assetid: 9b9e0070-6a13-4142-8180-19c003fbbd55
ms.openlocfilehash: 3ed36eca727a15a3c70bc51a07cd3c143d7f66da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320137"
---
# <a name="pdbstripped-strip-private-symbols"></a>/PDBSTRIPPED (プライベート シンボルの除去)

```
/PDBSTRIPPED:pdb_file_name
```

## <a name="arguments"></a>引数

*pdb_file_name*<br/>
削除されたプログラム データベース (PDB)、リンカーによって作成されるユーザー指定の名前。

## <a name="remarks"></a>Remarks

PDB ファイルを生成するオプションのコンパイラやリンカーと、プログラム イメージをビルドするときに/PDBSTRIPPED オプションが 2 番目のプログラム データベース (PDB) ファイルを作成します ([/debug](debug-generate-debug-info.md)、 [/Z7](z7-zi-zi-debug-information-format.md)/Zd、または/Zi)。 2 番目の PDB ファイルでは、顧客に提供しないシンボルが省かれています。 2 番目の PDB ファイルにはのみが含まれます。

- パブリック シンボル

- オブジェクト ファイルと対象となる実行可能ファイルの部分の一覧

- フレーム ポインター最適化 (FPO) デバッグ レコードのスタックを走査するために使用

削除された PDB ファイルは含まれません。

- 型情報

- 行番号情報

- 関数、ローカル、および静的データなどオブジェクトごとのファイルの CodeView シンボル

/PDBSTRIPPED を使用すると、完全な PDB ファイルが生成されます。

PDB ファイルを作成しない場合は、/PDBSTRIPPED が無視されます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**デバッグ**プロパティ ページ。

1. 変更、**プライベート シンボルの除去**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.StripPrivateSymbols%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
