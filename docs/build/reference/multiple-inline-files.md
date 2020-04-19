---
title: 複数のインライン ファイル
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: 71f17ff6717e717693facb21b4a4341a040b14c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320592"
---
# <a name="multiple-inline-files"></a>複数のインライン ファイル

コマンドは、1 つ以上のインライン ファイルを作成できます。

## <a name="syntax"></a>構文

```
command << <<
inlinetext
<<[KEEP | NOKEEP]
inlinetext
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>Remarks

ファイルごとに 1 つまたは複数の行のインライン テキストが続く、区切り記号を表す終了行を指定します。 最初のファイルの区切り線の次の行に 2 番目のファイルのテキストを開始します。

## <a name="see-also"></a>関連項目

[メイクファイルのインライン ファイル](inline-files-in-a-makefile.md)
