---
title: ANALYSIS_CALLBACKS 構造体
description: C++ BUILD Insights SDK ANALYSIS_CALLBACKS 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ANALYSIS_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8c35e740d97488969a6b69467d54412297e49227
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334146"
---
# <a name="analysis_callbacks-structure"></a>ANALYSIS_CALLBACKS 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`ANALYSIS_CALLBACKS` 構造体は、 [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)または[RELOG_DESCRIPTOR](relog-descriptor-struct.md)オブジェクトを初期化するときに使用されます。 これは、Windows イベントトレーシング (ETW) トレースの分析または再ログ記録中に呼び出す関数を指定します。

## <a name="syntax"></a>構文

```cpp
typedef struct ANALYSIS_CALLBACKS_TAG
{
    OnAnalysisEventFunc     OnStartActivity;
    OnAnalysisEventFunc     OnStopActivity;
    OnAnalysisEventFunc     OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginAnalysis;
    OnBeginEndPassFunc      OnEndAnalysis;
    OnBeginEndPassFunc      OnBeginAnalysisPass;
    OnBeginEndPassFunc      OnEndAnalysisPass;
} ANALYSIS_CALLBACKS;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `OnStartActivity` | アクティビティの開始イベントを処理するために呼び出されます。 |
| `OnStopActivity` | アクティビティ停止イベントを処理するために呼び出されます。 |
| `OnSimpleEvent` | 単純なイベントを処理するために呼び出されます。 |
| `OnTraceInfo` | 分析セッションの場合は、各分析パスの先頭で呼び出されます。 再ログセッションの場合は。各分析パスの先頭で呼び出され、再ログパスの先頭で再び呼び出されます。 この関数は、OnBeginAnalysisPass が呼び出された後にのみ呼び出されます。 |
| `OnBeginAnalysis` | 分析セッションの場合は、分析パスが開始される前に呼び出されます。 再ログセッションの場合、分析フェーズが開始される前に2回呼び出されます。再ログセッションの開始を通知し、1回後に分析フェーズの開始を通知します。 |
| `OnEndAnalysis` | 分析セッションの場合、この関数は、すべての分析が終了した後に呼び出されます。 再ログセッションの場合、この関数は、分析フェーズのすべての分析パスが終了したときに呼び出されます。 次に、再ログパスが終了した後に、再度呼び出されます。 |
| `OnBeginAnalysisPass` | すべてのイベントを処理する前に、分析パスまたは再ログパスの開始時に呼び出されます。 |
| `OnEndAnalysisPass` | すべてのイベントを処理した後、分析パスまたは再ログパスを終了するときに呼び出されます。 |

## <a name="remarks"></a>解説

再ログセッションの分析フェーズは再ログセッションの一部と見なされ、複数の分析パスが含まれる場合があります。 このため、再ログセッションの開始時に、行で `OnBeginAnalysis` が2回呼び出されます。 `OnEndAnalysis` は、再ログ記録フェーズを開始する前に、分析フェーズの最後に呼び出され、再ログ記録フェーズの最後に再び呼び出されます。 再ログ記録フェーズには、常に単一の再ログパスが含まれます。

アナライザーは、再ログセッションの分析と再ログのフェーズの両方に含まれる可能性があります。 これらのアナライザーは、OnBeginAnalysis と `OnEndAnalysis` の呼び出しペアを追跡することで、現在進行中のフェーズを特定できます。 `OnEndAnalysis` 呼び出しなしの2つの `OnBeginAnalysis` 呼び出しは、分析フェーズが進行中であることを意味します。 2つの `OnBeginAnalysis` 呼び出しと1つの `OnEndAnalysis` 呼び出しは、再ログ記録フェーズが進行中であることを意味します。 2つの OnBeginAnalysis 呼び出しと2つの `OnEndAnalysis` 呼び出しは、両方のフェーズが終了したことを意味します。

`ANALYSIS_CALLBACKS` 構造体のすべてのメンバーは、有効な関数を指す必要があります。 許容される関数シグネチャの詳細については、「 [OnAnalysisEventFunc](on-analysis-event-func-typedef.md)、 [ontraceinfofunc](on-trace-info-func-typedef.md)、および[OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)」を参照してください。

::: moniker-end
