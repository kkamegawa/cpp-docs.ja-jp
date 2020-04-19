---
title: TRACE_INFO_DATA 構造体
description: C++ BUILD Insights SDK TRACE_INFO_DATA 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACE_INFO_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 04cb5c013bca8879507983d169b38e5af0f1322b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335052"
---
# <a name="trace_info_data-structure"></a>TRACE_INFO_DATA 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`TRACE_INFO_DATA` 構造は、分析または再ログされるトレースを記述します。

## <a name="syntax"></a>構文

```cpp
typedef struct TRACE_INFO_DATA_TAG
{
    unsigned long           LogicalProcessorCount;
    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;

} TRACE_INFO_DATA;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `LogicalProcessorCount` | トレースが収集されたコンピューター上の論理プロセッサの数。 |
| `TickFrequency` | ティック単位で計測された期間を評価するときに使用する1秒あたりのタイマー刻みの数。 |
| `StartTimestamp` | このフィールドは、トレースが開始されたときにキャプチャされるティック値に設定されます。 |
| `StopTimestamp` | このフィールドは、トレースが停止されたときにキャプチャされるティック値に設定されます。 |

## <a name="remarks"></a>解説

`StopTimestamp` から `StartTimestamp` を減算して、トレース全体で経過したタイマー刻みの数を取得します。 結果の値を時間単位に変換するには、`TickFrequency` を使用します。 ティックを時間単位に変換する例については、「 [EVENT_DATA](event-data-struct.md)」を参照してください。

::: moniker-end
