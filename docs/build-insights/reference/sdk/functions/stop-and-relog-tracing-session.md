---
title: StopAndRelogTracingSession
description: C++ BUILD Insights SDK StopAndRelogTracingSession 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: e99568f9b509b89ccd0f0711433dec9d96d904bc
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334200"
---
# <a name="stopandrelogtracingsession"></a>StopAndRelogTracingSession

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`StopAndRelogTracingSession` 関数は、実行中のトレースセッションを停止し、結果のトレースを一時ファイルに保存します。 次に、一時ファイルを入力として使用して、再ログセッションが直ちに開始されます。 再ログセッションによって生成された最後の再ログトレースは、呼び出し元によって指定されたファイルに保存されます。 この関数を呼び出す実行可能ファイルには、管理者特権が必要です。

## <a name="syntax"></a>構文

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const char*                                   sessionName,
    const char*                                   outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE StopAndRelogTracingSession(
    const wchar_t*                                sessionName,
    const wchar_t*                                outputLogFile,
    TRACING_SESSION_STATISTICS*                   statistics,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>パラメーター

*セッション名*\
停止するトレースセッションの名前。 [StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)、または[StartTracingSessionW](start-tracing-session-w.md)に渡されたものと同じセッション名を使用します。

*Outputlogfile*\
再ログセッションによって生成される再ログトレースを書き込むファイル。

*統計*\
[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)オブジェクトへのポインター。 `StopAndRelogTracingSession` は、を返す前に、このオブジェクトのトレースコレクションの統計情報を書き込みます。

*Numberofanalytics Sispの*\
トレースで実行する分析パスの数。 トレースは、分析パスごとに1回、指定されたアナライザーグループを通じて渡されます。

*systemEventsRetentionFlags*\
再ログトレースに保持するシステム ETW イベントを指定する[RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md)ビットマスク。

*analyzerGroup*\
再ログセッションの分析フェーズに使用されるアナライザーグループ。 [MakeStaticAnalyzerGroup](make-static-analyzer-group.md)を呼び出して、analyzer グループを作成します。 [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)から取得した動的アナライザーグループを使用する場合は、まず、そのアドレスを `MakeStaticAnalyzerGroup`に渡すことによって、静的なアナライザーグループ内にカプセル化します。

*reloggerGroup*\
*Outputlogfile*に指定されているトレースファイルにイベントを再度記録する relogger グループ。 [MakeStaticReloggerGroup](make-static-relogger-group.md)を呼び出して、relogger グループを作成します。 [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md)から取得した動的再ロガーグループを使用する場合は、まず、そのアドレスを `MakeStaticReloggerGroup`に渡すことによって、静的 relogger グループ内にカプセル化します。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md)列挙型の結果コード。

### <a name="remarks"></a>解説

入力トレースは、アナライザーグループの*Numberofanalyzer Sisp・* の時間を通じて渡されます。 再ログ記録には同様のオプションはありません。 すべての分析パスが完了すると、トレースは relogger グループに trough 渡されます。

Relogging クラス内の CPU サンプルなどのシステムイベントの再ログ記録はサポートされていません。 *SystemEventsRetentionFlags*パラメーターを使用して、出力トレースに保持するシステムイベントを決定します。

::: moniker-end
