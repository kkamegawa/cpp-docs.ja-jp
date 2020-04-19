---
title: StopAndAnalyzeTracingSession
description: C++ BUILD Insights SDK StopAndAnalyzeTracingSession 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndAnalyzeTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b1c605bb63ac093f90128a03c37b186226130912
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334218"
---
# <a name="stopandanalyzetracingsession"></a>StopAndAnalyzeTracingSession

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`StopAndAnalyzeTracingSession` 関数は、実行中のトレースセッションを停止し、結果のトレースを一時ファイルに保存します。 その後、分析セッションは、一時ファイルを入力として使用してすぐに開始されます。 この関数を呼び出す実行可能ファイルには、管理者特権が必要です。

## <a name="syntax"></a>構文

```cpp
template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const char*                                   sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);

template <typename... TAnalyzerGroupMembers>
RESULT_CODE StopAndAnalyzeTracingSession(
    const wchar_t*                                sessionName,
    unsigned                                      numberOfAnalysisPasses,
    TRACING_SESSION_STATISTICS*                   statistics,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup);
```

### <a name="parameters"></a>パラメーター

*セッション名*\
停止するトレースセッションの名前。 [StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)、または[StartTracingSessionW](start-tracing-session-w.md)に渡されたものと同じセッション名を使用します。

*Numberofanalytics Sispの*\
トレースで実行する分析パスの数。 トレースは、分析パスごとに1回、指定されたアナライザーグループを通じて渡されます。

*統計*\
[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)オブジェクトへのポインター。 `StopAndAnalyzeTracingSession` は、を返す前に、このオブジェクトのトレースコレクションの統計情報を書き込みます。

*analyzerGroup*\
分析に使用するアナライザーグループ。 [MakeStaticAnalyzerGroup](make-static-analyzer-group.md)を呼び出して、analyzer グループを作成します。 [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)から取得した動的アナライザーグループを使用する場合は、まず、そのアドレスを `MakeStaticAnalyzerGroup`に渡すことによって、静的なアナライザーグループ内にカプセル化します。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md)列挙型の結果コード。

::: moniker-end
