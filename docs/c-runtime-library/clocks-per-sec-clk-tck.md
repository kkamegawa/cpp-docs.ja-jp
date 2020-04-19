---
title: CLOCKS_PER_SEC、CLK_TCK
ms.date: 11/04/2016
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
ms.openlocfilehash: eef065ac4fcedf13f3a5d54d4df0563fd04ef965
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750677"
---
# <a name="clockspersec-clktck"></a>CLOCKS_PER_SEC、CLK_TCK

## <a name="syntax"></a>構文

```
#include <time.h>
```

## <a name="remarks"></a>解説

`clock` 関数の戻り値であり、`CLOCKS_PER_SEC` で除算された秒単位の時間を表します。 `CLK_TCK` も同じものですが、古い形式とされます。

## <a name="see-also"></a>関連項目

[clock](../c-runtime-library/reference/clock.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
