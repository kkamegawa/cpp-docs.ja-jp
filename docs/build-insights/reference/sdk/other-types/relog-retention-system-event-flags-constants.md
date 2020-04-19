---
title: RELOG_RETENTION_SYSTEM_EVENT_FLAGS 定数
description: C++ビルドインサイト SDK RELOG_RETENTION_SYSTEM_EVENT_FLAGS 定数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_RETENTION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 74afc10faa26ba39a669a05aa3e3cabd1a211293
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333966"
---
# <a name="relog_retention_system_event_flags-constants"></a>RELOG_RETENTION_SYSTEM_EVENT_FLAGS 定数

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`RELOG_RETENTION_SYSTEM_EVENT_FLAGS` 定数は、再ログトレースに保持するシステムイベントを示すために使用されます。 それらを使用して、 [RELOG_DESCRIPTOR](relog-descriptor-struct.md)構造体の `SystemEventsRetentionFlags` フィールドを初期化します。

## <a name="syntax"></a>構文

```cpp
static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES = 0x1ULL;

static const unsigned long long
    RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL         = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | CPU サンプルシステムイベントを再ログ記録されたトレースに保持します。 |
| `RELOG_RETENTION_SYSTEM_EVENT_FLAGS_ALL` | すべてのシステムイベントを再ログ記録されたトレースに保持します。 |

## <a name="remarks"></a>解説

::: moniker-end
