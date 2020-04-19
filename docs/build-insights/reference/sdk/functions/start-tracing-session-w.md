---
title: StartTracingSessionW
description: C++ BUILD Insights SDK StartTracingSessionW 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- StartTracingSessionW
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 072b02166f2841e6d210306ef75c9fc64fea9778
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334248"
---
# <a name="starttracingsessionw"></a>StartTracingSessionW

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`StartTracingSessionW` 関数は、トレースセッションを開始します。 この関数を呼び出す実行可能ファイルには、管理者特権が必要です。

## <a name="syntax"></a>構文

```cpp
enum RESULT_CODE StartTracingSessionW(
    const wchar_t*                 sessionName,
    const TRACING_SESSION_OPTIONS* options);
```

### <a name="parameters"></a>パラメーター

*セッション名*\
開始するトレースセッションの名前。 [StopTracingSessionW](stop-tracing-session-w.md)を呼び出すときには同じ名前を使用し、それ以外の場合は stop trace 関数を使用します。

*オプション*\
[TRACING_SESSION_OPTIONS](../other-types/tracing-session-options-struct.md)オブジェクトへのポインター。 このオブジェクトを使用して、トレースセッションによって収集されるイベントを選択します。

### <a name="return-value"></a>戻り値

[RESULT_CODE](../other-types/result-code-enum.md)列挙型の結果コード。

::: moniker-end
