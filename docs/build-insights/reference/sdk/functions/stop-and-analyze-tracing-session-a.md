---
title: StopAndAnalyzeTracingSessionA
description: C++ BUILD Insights SDK StopAndAnalyzeTracingSessionA 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 076cb96935c8734d6a00d0c389238236de1560ec
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334230"
---
# <a name="stopandanalyzetracingsessiona"></a>StopAndAnalyzeTracingSessionA

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`StopAndAnalyzeTracingSessionA` 関数は、実行中のトレースセッションを停止し、結果のトレースを一時ファイルに保存します。 その後、分析セッションは、一時ファイルを入力として使用してすぐに開始されます。 この関数を呼び出す実行可能ファイルには、管理者特権が必要です。

## <a name="syntax"></a>構文

```cpp
enum RESULT_CODE StopAndAnalyzeTracingSessionA(
    const char*                 sessionName,
    TRACING_SESSION_STATISTICS* statistics,
    const ANALYSIS_DESCRIPTOR*  analysisDescriptor);
```

### <a name="parameters"></a>パラメーター

*セッション名*\
停止するトレースセッションの名前。 [StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)、または[StartTracingSessionW](start-tracing-session-w.md)に渡されたものと同じセッション名を使用します。

*統計*\
[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)オブジェクトへのポインター。 `StopAndAnalyzeTracingSessionA` は、を返す前に、このオブジェクトのトレースコレクションの統計情報を書き込みます。

*analysisDescriptor*\
[ANALYSIS_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)オブジェクトへのポインター。 `StopAndAnalyzeTracingSessionA`によって開始される分析セッションを構成するには、このオブジェクトを使用します。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md)列挙型の結果コード。

::: moniker-end
