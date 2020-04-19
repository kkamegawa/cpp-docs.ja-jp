---
title: TRACING_SESSION_STATISTICS 構造体
description: C++ BUILD Insights SDK TRACING_SESSION_OPTIONS 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_STATISTICS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 9aa7c0a861d80fd3ebff85eb7ecb17dd05ae869e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333864"
---
# <a name="tracing_session_statistics-structure"></a>TRACING_SESSION_STATISTICS 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`TRACING_SESSION_STATISTICS` 構造は、収集されたトレースの統計を記述します。 そのフィールドは、トレースセッションを停止したときに設定されます。

## <a name="syntax"></a>構文

```cpp
typedef struct TRACING_SESSION_STATISTICS_TAG
{
    unsigned long MSVCEventsLost;
    unsigned long MSVCBuffersLost;
    unsigned long SystemEventsLost;
    unsigned long SystemBuffersLost;

} TRACING_SESSION_STATISTICS;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `MSVCEventsLost` | 削除された MSVC イベントの数。 |
| `MSVCBuffersLost` | 削除された MSVC イベントバッファーの数。 |
| `SystemEventsLost` | 削除されたシステムイベントの数。 |
| `SystemBuffersLost` | 削除されたシステムイベントバッファーの数。 |

## <a name="remarks"></a>解説

この構造体は、次の関数を呼び出すときに設定されます。

- [StopTracingSession](../functions/stop-tracing-session.md)
- [StopTracingSessionA](../functions/stop-tracing-session-a.md)
- [StopTracingSessionW](../functions/stop-tracing-session-w.md)
- [StopAndAnalyzeTracingSession](../functions/stop-and-analyze-tracing-session.md)
- [StopAndAnalyzeTracingSessionA](../functions/stop-and-analyze-tracing-session-a.md)
- [StopAndAnalyzeTracingSessionW](../functions/stop-and-analyze-tracing-session-w.md)
- [StopAndRelogTracingSession](../functions/stop-and-relog-tracing-session.md)
- [StopAndRelogTracingSessionA](../functions/stop-and-relog-tracing-session-a.md)
- [StopAndRelogTracingSessionW](../functions/stop-and-relog-tracing-session-w.md)

::: moniker-end
