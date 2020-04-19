---
title: StartTracingSession
description: C++ BUILD Insights SDK StartTracingSession 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSession
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: de9d46b4a684d66bf01f76e7ea753694cf40d2cd
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334224"
---
# <a name="starttracingsession"></a>StartTracingSession

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`StartTracingSession` 関数は、トレースセッションを開始します。 この関数を呼び出す実行可能ファイルには、管理者特権が必要です。

## <a name="syntax"></a>構文

```cpp
RESULT_CODE StartTracingSession(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS& options);

RESULT_CODE StartTracingSession(
    const wchar_t*                 sessionName,
    const TRACING_SESSION_OPTIONS& options);
```

### <a name="parameters"></a>パラメーター

*セッション名*\
開始するトレースセッションの名前。 [StopTracingSession](stop-tracing-session.md)またはその他の stop トレース関数を呼び出すときには、同じ名前を使用します。

*オプション*\
[TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md)オブジェクトへのポインター。 このオブジェクトを使用して、トレースセッションによって収集されるイベントを選択します。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md)列挙型の結果コード。

::: moniker-end
