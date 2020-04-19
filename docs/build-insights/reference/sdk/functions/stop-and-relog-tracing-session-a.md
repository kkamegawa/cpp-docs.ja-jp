---
title: StopAndRelogTracingSessionA
description: C++ BUILD Insights SDK StopAndRelogTracingSessionA 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StopAndRelogTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c9fe2ea47b378565d3ce9785b6f4cc3e541ebe80
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334296"
---
# <a name="stopandrelogtracingsessiona"></a>StopAndRelogTracingSessionA

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`StopAndRelogTracingSessionA` 関数は、実行中のトレースセッションを停止し、結果のトレースを一時ファイルに保存します。 次に、一時ファイルを入力として使用して、再ログセッションが直ちに開始されます。 再ログセッションによって生成された最後の再ログトレースは、呼び出し元によって指定されたファイルに保存されます。 この関数を呼び出す実行可能ファイルには、管理者特権が必要です。

## <a name="syntax"></a>構文

```cpp
enum RESULT_CODE StopAndRelogTracingSessionA(
    const char*                 sessionName,
    const char*                 outputLogFile,
    TRACING_SESSION_STATISTICS* statistics,
    const RELOG_DESCRIPTOR*     relogDescriptor);
```

### <a name="parameters"></a>パラメーター

*セッション名*\
停止するトレースセッションの名前。 [StartTracingSession](start-tracing-session.md)、 [StartTracingSessionA](start-tracing-session-a.md)、または[StartTracingSessionW](start-tracing-session-w.md)に渡されたものと同じセッション名を使用します。

*Outputlogfile*\
再ログセッションによって生成される再ログトレースを書き込むファイル。

*統計*\
[TRACING_SESSION_STATISTICS](../other-types/tracing-session-statistics-struct.md)オブジェクトへのポインター。 `StopAndRelogTracingSessionA` は、を返す前に、このオブジェクトのトレースコレクションの統計情報を書き込みます。

*analysisDescriptor*\
[RELOG_DESCRIPTOR](../other-types/analysis-descriptor-struct.md)オブジェクトへのポインター。 このオブジェクトを使用して、`StopAndRelogTracingSessionA`によって開始される再ログセッションを構成します。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md)列挙型の結果コード。

::: moniker-end
