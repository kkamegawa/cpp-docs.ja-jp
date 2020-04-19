---
title: StartTracingSessionA
description: C++ BUILD Insights SDK StartTracingSessionA 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6c5069a2b521472ee4fd06ee313a66de5d7aa814
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334272"
---
# <a name="starttracingsessiona"></a>StartTracingSessionA

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`StartTracingSessionA` 関数は、トレースセッションを開始します。 この関数を呼び出す実行可能ファイルには、管理者特権が必要です。

## <a name="syntax"></a>構文

```cpp
enum RESULT_CODE StartTracingSessionA(
    const char*                    sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>パラメーター

*セッション名*\
開始するトレースセッションの名前。 [StopTracingSessionA](stop-tracing-session.md)またはその他の stop トレース関数を呼び出すときには、同じ名前を使用します。

*オプション*\
[TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md)オブジェクトへのポインター。 このオブジェクトを使用して、トレースセッションによって収集されるイベントを選択します。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md)列挙型の結果コード。

::: moniker-end
