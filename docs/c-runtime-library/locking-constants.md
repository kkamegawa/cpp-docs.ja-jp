---
title: _locking 定数
ms.date: 11/04/2016
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
helpviewer_keywords:
- LK_UNLCK constant
- LK_NBRLCK constant
- _LK_NBRLCK constant
- _LK_NBLCK constant
- _LK_LOCK constant
- LK_NBLCK constant
- _LK_UNLCK constant
- LK_RLCK constant
- _LK_RLCK constant
- LK_LOCK constant
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
ms.openlocfilehash: d559a68e8fede6e0b6dd40505a041b14da703681
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738493"
---
# <a name="locking-constants"></a>_locking 定数

## <a name="syntax"></a>構文

```
#include <sys/locking.h>
```

## <a name="remarks"></a>解説

`_locking` 関数の呼び出しにおける *mode* 引数によって、実行されるロック操作が指定されます。

*mode* 引数は、次のマニフェスト定数のいずれかである必要があります。

|||
|-|-|
| `_LK_LOCK`  | 指定したバイトをロックします。 バイトをロックできない場合は、関数によって 1 秒後に再試行されます。 10 回試行した後、バイトをロックできなかった場合、関数はエラーを返します。  |
| `_LK_RLCK`  | `_LK_LOCK` と同じ。  |
|`_LK_NBLCK`  | 指定したバイトをロックします。 バイトをロックできない場合、関数はエラーを返します。  |
| `_LK_NBRLCK`  | `_LK_NBLCK` と同じ。  |
| `_LK_UNLCK`  | 指定したバイトをロック解除します。 (バイトはすでにロックされている必要があります)。  |

## <a name="see-also"></a>関連項目

[_locking](../c-runtime-library/reference/locking.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
