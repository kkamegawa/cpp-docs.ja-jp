---
title: TZNAME_MAX
ms.date: 10/22/2018
f1_keywords:
- TZNAME_MAX
helpviewer_keywords:
- TZNAME_MAX constant
ms.assetid: e2286cb8-751d-4557-9650-5c4b98a8f7be
ms.openlocfilehash: 71e5becd39f49d86573483c5451a9a2415d84181
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750937"
---
# <a name="tznamemax"></a>TZNAME_MAX

**互換性のために残されています**。 タイム ゾーン名の変数に許容される文字列の最大長です。 このマクロは Visual Studio 2012 以前のバージョンで \<limits.h> に定義されています。 Visual Studio 2013 以降のバージョンでは定義されていません。 現在のタイム ゾーン名を保持するために必要な長さを取得するには、[_get_tzname](../c-runtime-library/reference/get-tzname.md) を使用します。

## <a name="syntax"></a>構文

```
#include <limits.h>
```

## <a name="see-also"></a>関連項目

[環境定数](../c-runtime-library/environmental-constants.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)
