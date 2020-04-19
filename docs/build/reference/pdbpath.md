---
title: /PDBPATH
ms.date: 11/04/2016
f1_keywords:
- /pdbpath
helpviewer_keywords:
- .pdb files, path
- -PDBPATH dumpbin option
- /PDBPATH dumpbin option
- PDBPATH dumpbin option
- PDB files, path
ms.assetid: ccf67dcd-0b23-4250-ad47-06c48acbe82b
ms.openlocfilehash: f29b8e61fbfbdb0f373e3e7510cb3f1fe0b9cc2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319851"
---
# <a name="pdbpath"></a>/PDBPATH

```
/PDBPATH[:VERBOSE] filename
```

### <a name="parameters"></a>パラメーター

*ファイル名*<br/>
対応する .pdb ファイルを検索する .dll または .exe ファイルの名前。

**。 詳細**<br/>
(省略可能).Pdb ファイルを検索する試行が行われる場所のすべてのディレクトリを報告します。

## <a name="remarks"></a>Remarks

同じパスをたどって、デバッガーが .pdb ファイルを検索してしまいます、レポートが存在する場合に指定されたファイルに対応する .pdb ファイルをコンピューターの検索が/PDBPATH *filename*します。

Visual Studio デバッガーを使用する場合、デバッガーがデバッグしているファイルの別のバージョンを .pdb ファイルを使用しているという事実の問題が発生する可能性があります。

/PDBPATH は、次のパスに沿った .pdb ファイルを検索します。

- 実行可能ファイルが存在する場所を確認します。

- 実行可能ファイルに書き込まれた PDB の場所を確認します。 これは、イメージのリンク時に場所では、通常、します。

- Visual Studio IDE で構成されている検索パスを確認します。

- _NT_SYMBOL_PATH と _NT_ALT_SYMBOL_PATH パスに沿って、環境変数を確認します。

- Windows ディレクトリで確認します。

## <a name="see-also"></a>関連項目

[DUMPBIN オプション](dumpbin-options.md)<br/>
[/PDBALTPATH (別の PDB パスを使用)](pdbaltpath-use-alternate-pdb-path.md)
