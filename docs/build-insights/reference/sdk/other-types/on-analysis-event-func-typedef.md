---
title: OnAnalysisEventFunc typedef
description: C++ BUILD Insights SDK OnAnalysisEventFunc typedef リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OnAnalysisEventFunc
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d260f6060e759f315589abda82e31c2c2b95a65e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334062"
---
# <a name="onanalysiseventfunc-typedef"></a>OnAnalysisEventFunc typedef

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`OnAnalysisEventFunc` typedef は、 [ANALYSIS_CALLBACKS](analysis-callbacks-struct.md)構造体で使用される関数シグネチャの1つです。

## <a name="syntax"></a>構文

```cpp
typedef enum CALLBACK_CODE (BUILD_INSIGHTS_API *OnAnalysisEventFunc)(
    const EVENT_COLLECTION_DATA*    eventStack,
    void*                           callbackContext);
```

### <a name="parameters"></a>パラメーター

*Eventstack*\
現在のイベントのイベントスタック。 イベントスタックの詳細については、「 [Events](../event-table.md)」を参照してください。

*\ の*テキスト
[ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)または[RELOG_DESCRIPTOR](relog-descriptor-struct.md)でこのコールバックに対して設定されたコンテキスト値。

### <a name="return-value"></a>戻り値

次に発生する内容を制御する[CALLBACK_CODE](callback-code-enum.md)値。

::: moniker-end
