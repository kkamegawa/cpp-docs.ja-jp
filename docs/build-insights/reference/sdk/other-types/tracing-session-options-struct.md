---
title: TRACING_SESSION_OPTIONS 構造体
description: C++ BUILD Insights SDK TRACING_SESSION_OPTIONS 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_OPTIONS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 3f02552d5df4ffe71bc4be5c46e4b5239f25d73c
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333870"
---
# <a name="tracing_session_options-structure"></a>TRACING_SESSION_OPTIONS 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`TRACING_SESSION_OPTIONS` 構造体は、 [ANALYSIS_DESCRIPTOR](analysis-descriptor-struct.md)または[RELOG_DESCRIPTOR](relog-descriptor-struct.md)構造体を初期化するときに使用されます。 トレースのコレクション中にキャプチャするイベントについて説明します。

## <a name="syntax"></a>構文

```cpp
typedef struct TRACING_SESSION_OPTIONS_TAG
{
    unsigned long long SystemEventFlags;
    unsigned long long MsvcEventFlags;

} TRACING_SESSION_OPTIONS;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `SystemEventFlags` | キャプチャするシステムイベントを記述するビットマスク。 詳細については、「 [TRACING_SESSION_SYSTEM_EVENT_FLAGS](tracing-session-system-event-flags-constants.md)」を参照してください。 |
| `MsvcEventFlags` | キャプチャする MSVC イベントを記述するビットマスク。 詳細については、「 [TRACING_SESSION_MSVC_EVENT_FLAGS](tracing-session-msvc-event-flags-constants.md)」を参照してください。 |

::: moniker-end
