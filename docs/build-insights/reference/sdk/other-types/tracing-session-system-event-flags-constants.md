---
title: TRACING_SESSION_SYSTEM_EVENT_FLAGS 定数
description: C++ビルドインサイト SDK TRACING_SESSION_SYSTEM_EVENT_FLAGS 定数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TRACING_SESSION_SYSTEM_EVENT_FLAGS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ce0b0ea373ec53f0d5bcf228269299d69b49bb95
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333996"
---
# <a name="tracing_session_system_event_flags-constants"></a>TRACING_SESSION_SYSTEM_EVENT_FLAGS 定数

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`TRACING_SESSION_SYSTEM_EVENT_FLAGS` 定数は、トレース中に収集するシステムイベントを記述するために使用されます。 それらを使用して、 [TRACING_SESSION_OPTIONS](tracing-session-options-struct.md)構造体の `SystemEventFlags` フィールドを初期化します。

## <a name="syntax"></a>構文

```cpp
static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT      = 0x1ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES  = 0x2ULL;

static const unsigned long long
    TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL          = 0xFFFFFFFFFFFFFFFFULL;
```

## <a name="members"></a>メンバー

| Name | このフラグによって有効にされるイベント |
|--|--|
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CONTEXT` | このフラグは、明示的に指定C++されていない場合でも、BUILD Insights SDK によって既定でアクティブになります。 これにより、ビルドインサイトでC++正常に機能するために必要な基本的なシステムイベントが有効になります。 このフラグによって有効にされたイベントは、プロセス、スレッド、およびイメージの読み込みに関する情報を提供します。 これらのイベントを無効にすることはできません。 |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_CPU_SAMPLES` | CPU のサンプル |
| `TRACING_SESSION_SYSTEM_EVENT_FLAGS_ALL` | このフラグは、すべてのシステムイベントをオンにします。 |

::: moniker-end
