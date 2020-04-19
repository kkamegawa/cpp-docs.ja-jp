---
title: StopTracingSessionW
description: C++ BUILD Insights SDK StopTracingSessionW 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fbb31b600d6aee8c03cb0b52f71c0afcb8b8e3b3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334170"
---
# <a name="stoptracingsessionw"></a>StopTracingSessionW

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`StopTracingSessionW` 関数は、実行中のトレースセッションを停止し、生のトレースファイルを生成します。 分析セッションを開始するために、生のトレースファイルを[analyze](analyze.md)、analysis [zea](analyze-a.md)、および[analyze](analyze-w.md)の各関数に渡すことができます。 また、生のトレースファイルを[Relog](relog.md)、 [Reloga](relog-a.md)、 [reloga](relog-w.md)の各関数に渡して、再ログセッションを開始することもできます。 `StopTracingSessionW` を呼び出す実行可能ファイルには、管理者特権が必要です。

## <a name="syntax"></a>構文

```cpp
enum RESULT_CODE StopTracingSessionW(
    const wchar_t*              sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics);
```

### <a name="parameters"></a>パラメーター

*セッション名*\
停止するトレースセッションの名前。 [StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)、または[StartTracingSessionW](start-tracing-session-w.md)に渡されたものと同じセッション名を使用します。

*Outputlogfile*\
生のトレースを保存する最終的な出力ログファイルのパス。

*統計*\
[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)オブジェクトへのポインター。 `StopTracingSessionW` は、を返す前に、このオブジェクトのトレースコレクションの統計情報を書き込みます。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md)列挙型の結果コード。

::: moniker-end
