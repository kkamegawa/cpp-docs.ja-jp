---
title: Relog (英語の可能性あり)
description: ビルドC++インサイト SDK の Relog 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Relog
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 1ce09101deebd957de4b9305762dc37f38b53f4e
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334284"
---
# <a name="relog"></a>Relog (英語の可能性あり)

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`Relog` 関数は、Windows イベントトレーシング (ETW) トレースから MSVC イベントを読み取り、それを新しい変更された ETW トレースに書き込むために使用されます。

## <a name="syntax"></a>構文

```cpp
template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const char*                                   inputLogFile,
    const char*                                   outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);

template <
    typename... TAnalyzerGroupMembers,
    typename... TReloggerGroupMembers>
RESULT_CODE Relog(
    const wchar_t*                                inputLogFile,
    const wchar_t*                                outputLogFile,
    unsigned                                      numberOfAnalysisPasses,
    unsigned long long                            systemEventsRetentionFlags,
    StaticAnalyzerGroup<TAnalyzerGroupMembers...> analyzerGroup,
    StaticReloggerGroup<TReloggerGroupMembers...> reloggerGroup);
```

### <a name="parameters"></a>パラメーター

*TAnalyzerGroupMembers*\
このパラメーターは常に推測されます。

*TReloggerGroupMembers*\
このパラメーターは常に推測されます。

*Inputlogfile*\
イベントの読み取り元の入力 ETW トレース。

*Outputlogfile*\
新しいイベントを書き込むファイル。

*Numberofanalytics Sispの*\
入力トレースで実行する分析パスの数。 トレースは、分析パスごとに1回、指定されたアナライザーグループを通じて渡されます。

*systemEventsRetentionFlags*\
再ログトレースに保持するシステム ETW イベントを指定するビットマスク。 詳細については、「 [RELOG_RETENTION_SYSTEM_EVENT_FLAGS](../other-types/relog-retention-system-event-flags-constants.md)」を参照してください。

*analyzerGroup*\
再ログセッションの分析フェーズに使用されるアナライザーグループ。 [MakeStaticAnalyzerGroup](make-static-analyzer-group.md)を呼び出して、analyzer グループを作成します。 [MakeDynamicAnalyzerGroup](make-dynamic-analyzer-group.md)から取得した動的アナライザーグループを使用するには、まず、そのアドレスを `MakeStaticAnalyzerGroup`に渡すことによって、静的なアナライザーグループ内にカプセル化します。

*reloggerGroup*\
*Outputlogfile*に指定されているトレースファイルにイベントを再度記録する relogger グループ。 [MakeStaticReloggerGroup](make-static-relogger-group.md)を呼び出して、relogger グループを作成します。 [MakeDynamicReloggerGroup](make-dynamic-relogger-group.md)から取得した動的再ロガーグループを使用するには、まず、そのアドレスを `MakeStaticReloggerGroup`に渡すことによって、静的 relogger グループ内にカプセル化します。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md)列挙型の結果コード。

### <a name="remark"></a>注記

入力トレースは、アナライザーグループの*Numberofanalyzer Sisp・* の時間を通じて渡されます。 再ログ記録には同様のオプションはありません。 すべての分析パスが完了すると、トレースは relogger グループに trough 渡されます。

Relogging クラス内の CPU サンプルなどのシステムイベントの再ログ記録はサポートされていません。 *SystemEventsRetentionFlags*パラメーターを使用して、出力トレースに保持するシステムイベントを決定します。

::: moniker-end
