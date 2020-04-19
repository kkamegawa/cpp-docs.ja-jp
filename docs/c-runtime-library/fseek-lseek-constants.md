---
title: fseek 定数と _lseek 定数
ms.date: 11/04/2016
f1_keywords:
- SEEK_END
- SEEK_SET
- SEEK_CUR
helpviewer_keywords:
- SEEK_SET constant
- SEEK_END constant
- SEEK_CUR constant
ms.assetid: 9deeb13e-5aa3-4c33-80d8-721c80a4de9d
ms.openlocfilehash: 2e6cb2e0d781212f3b5e7758554507dfa438a716
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743364"
---
# <a name="fseek-lseek-constants"></a>fseek 定数と _lseek 定数

## <a name="syntax"></a>構文

```
#include <stdio.h>
```

## <a name="remarks"></a>解説

*origin* 引数は初期位置を指定し、次のマニフェスト定数のいずれかになります。

|定数|説明|
|--------------|-------------|
|`SEEK_END`|ファイルの終端|
|`SEEK_CUR`|ファイル ポインターの現在の位置|
|`SEEK_SET`|ファイルの先頭|

## <a name="see-also"></a>関連項目

[fseek、_fseeki64](../c-runtime-library/reference/fseek-fseeki64.md)<br/>
[_lseek、_lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
