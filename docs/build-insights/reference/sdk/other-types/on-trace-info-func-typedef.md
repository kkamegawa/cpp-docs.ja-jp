---
title: OnTraceInfoFunc typedef
description: C++ BUILD Insights SDK OnTraceInfoFunc typedef リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnTraceInfoFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b168d6783b31454f6a2837bcad1fc81199ce9054
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333990"
---
# <a name="ontraceinfofunc-typedef"></a>OnTraceInfoFunc typedef

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`OnTraceInfoFunc` typedef は、 [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)および[RELOG_CALLBACKS](relog-callbacks-struct.md)構造体で使用される関数シグネチャの1つです。

## <a name="syntax"></a>構文

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnTraceInfoFunc)(
    const TRACE_INFO_DATA*          traceInfo,
    void*                           callbackContext);
```

### <a name="parameters"></a>パラメーター

*Traceinfo*\
現在分析または再ログに記録されているトレースに関する情報を格納している[TRACE_INFO_DATA](../c-event-data-types/trace-info-data-struct.md)オブジェクト。

*\ の*テキスト
[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)または[RELOG_DESCRIPTOR](relog-descriptor-struct.md)でこのコールバックに対して設定されたコンテキスト値。

### <a name="return-value"></a>戻り値

次に発生する内容を制御する[CALLBACK_CODE](callback-code-enum.md)値。

::: moniker-end
