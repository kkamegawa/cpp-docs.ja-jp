---
title: /PDBALTPATH (別の PDB パスを使用)
ms.date: 11/04/2016
f1_keywords:
- /pdbaltpath
helpviewer_keywords:
- .pdb files, path
- PDBALTPATH dumpbin option
- -PDBALTPATH dumpbin option
- /PDBALTPATH dumpbin option
- PDB files, path
ms.assetid: 72e200aa-e2c3-4ad8-b687-25528da1aaaf
ms.openlocfilehash: 660e39a97b9fed0c5a9228fe011e7c0fa2566e68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320033"
---
# <a name="pdbaltpath-use-alternate-pdb-path"></a>/PDBALTPATH (別の PDB パスを使用)

```
/PDBALTPATH:pdb_file_name
```

## <a name="arguments"></a>引数

*pdb_file_name*<br/>
.pdb ファイルのパスとファイル名です。

## <a name="remarks"></a>Remarks

このオプションを使って、コンパイルされたバイナリ ファイルにプログラム データベース (.pdb) ファイルの別の場所を提供します。 通常、リンカーは作成するバイナリの中に .pdb ファイルの場所を記録します。 このオプションを使って .pdb ファイルに異なるパスとファイル名を提供できます。 /PDBALTPATH で提供される情報は、実際の .pdb ファイルの場所や名前を変更するわけではなく、リンカーがバイナリ ファイルに書き込む情報を変更します。 これにより、ビルド コンピューターのファイル構造とは独立したパスを提供できます。 このオプションの 2 つの一般的な使用方法は、ネットワーク パスまたはパス情報のないファイルを提供することです。

値*pdb_file_name*は、任意の文字列、環境変数、または **% _PDB**します。 リンカーはなどを展開し、環境変数 **%systemroot%**、その値にします。 リンカーは、環境変数を定義します。 **% _PDB**と**展開**します。 **% _PDB**展開し、パス情報がない実際の .pdb ファイルのファイル名と**展開**は、生成された実行可能ファイルの拡張機能です。

## <a name="see-also"></a>関連項目

[DUMPBIN オプション](dumpbin-options.md)<br/>
[/PDBPATH](pdbpath.md)
