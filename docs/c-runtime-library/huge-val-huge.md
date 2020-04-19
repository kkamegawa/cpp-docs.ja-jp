---
title: HUGE_VAL, _HUGE
ms.date: 11/04/2016
api_name:
- _HUGE
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _HUGE
- HUGE_VAL
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
ms.openlocfilehash: 3a0469b7158e765b1b1c6f34cb01c0e90beb1401
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940265"
---
# <a name="huge_val-_huge"></a>HUGE_VAL, _HUGE

## <a name="syntax"></a>構文

```
#include <math.h>
```

## <a name="remarks"></a>解説

`HUGE_VAL`表現可能な最大の double 値です。 エラーが発生した場合に、多くのランタイム数値演算関数でこの値が返されます。 一部の関数について -`HUGE_VAL` が返されます。 `HUGE_VAL` は `_HUGE` と定義されますが、ランタイム数値演算関数は `HUGE_VAL` を返します。 一貫性を保つのため、コードでも `HUGE_VAL` を使用する必要があります。

## <a name="see-also"></a>関連項目

[グローバル定数](../c-runtime-library/global-constants.md)
