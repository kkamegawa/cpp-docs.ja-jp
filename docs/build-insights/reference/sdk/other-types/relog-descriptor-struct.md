---
title: RELOG_DESCRIPTOR 構造体
description: C++ BUILD Insights SDK RELOG_DESCRIPTOR 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_DESCRIPTOR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f6f20835ed6535dd05def629200c113772e8f077
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333972"
---
# <a name="relog_descriptor-structure"></a>RELOG_DESCRIPTOR 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`RELOG_DESCRIPTOR` 構造体は、 [Reloga](../functions/relog-a.md)関数と[reloga](../functions/relog-w.md)関数で使用されます。 ここでは、Windows イベントトレーシング (ETW) トレースを再ログ記録する方法について説明します。

## <a name="syntax"></a>構文

```cpp
typedef struct RELOG_DESCRIPTOR_TAG
{
    unsigned                NumberOfAnalysisPasses;
    ANALYSIS_CALLBACKS      AnalysisCallbacks;
    RELOG_CALLBACKS         RelogCallbacks;
    unsigned long long      SystemEventsRetentionFlags;
    void*                   AnalysisContext;
    void*                   RelogContext;
} RELOG_DESCRIPTOR;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `NumberOfAnalysisPasses` | 再ログセッションの分析フェーズ中に ETW トレースで実行される分析パスの数。 |
| `AnalysisCallbacks` | 再ログセッションの分析フェーズ中に呼び出す関数を指定する[ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)オブジェクト。 |
| `RelogCallbacks` | 再ログセッションの再ログフェーズ中に呼び出す関数を指定する[RELOG_CALLBACKS](relog-callbacks-struct.md)オブジェクト。 |
| `SystemEventsRetentionFlags` | 再ログトレースに保持するシステム ETW イベントを指定する[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](relog-retention-system-event-flags-constants.md)ビットマスク。 |
| `AnalysisContext` | で指定されたすべて `AnalysisCallbacks` のコールバック関数に引数として渡されるユーザー指定のコンテキスト。 |
| `RelogContext` | で指定されたすべて `RelogCallbacks` のコールバック関数に引数として渡されるユーザー指定のコンテキスト。 |

## <a name="remarks"></a>解説

再ログセッション中の ETW イベントの再ログは、`RelogCallbacks`で指定されたコールバック関数を介してユーザーによって制御されます。 ただし、CPU サンプルなどのシステム ETW イベントは、これらのコールバック関数に転送されません。 システム ETW イベントの再ログ記録を制御するには、[`SystemEventsRetentionFlags`] フィールドを使用します。

`AnalysisCallbacks` および `RelogCallbacks` 構造体は、非メンバー関数へのポインターのみを受け入れます。 この制限は、オブジェクトポインターに設定することによって回避できます。 このオブジェクトポインターは、すべての非メンバーコールバック関数に引数として渡されます。 メンバー関数を非メンバーコールバック関数内から呼び出すには、このポインターを使用します。

再ログセッションの分析フェーズは、再ログ記録フェーズの前に常に実行されます。

::: moniker-end
