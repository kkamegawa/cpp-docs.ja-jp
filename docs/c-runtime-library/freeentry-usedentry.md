---
title: _FREEENTRY、_USEDENTRY
ms.date: 11/04/2016
f1_keywords:
- USEDENTRY
- _USEDENTRY
- _FREEENTRY
- FREEENTRY
helpviewer_keywords:
- _USEDENTRY constant
- _FREEENTRY constant
- FREEENTRY constant
- USEDENTRY constant
ms.assetid: 26f658e6-6846-4a4e-9984-262cfe392770
ms.openlocfilehash: a8aa11173dcc76089a916d19fd319e0d317724ce
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751936"
---
# <a name="freeentry-usedentry"></a>_FREEENTRY、_USEDENTRY

## <a name="syntax"></a>構文

```
#include <malloc.h>
```

## <a name="remarks"></a>解説

これらの定数は、`_heapwalk` ルーチンから **_HEAPINFO** 構造体の **_useflag** 要素に割り当てられた値を表します。 これらはヒープ エントリの状態を示します。

## <a name="see-also"></a>関連項目

[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
