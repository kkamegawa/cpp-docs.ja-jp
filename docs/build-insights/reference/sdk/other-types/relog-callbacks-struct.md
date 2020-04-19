---
title: RELOG_CALLBACKS 構造体
description: C++ BUILD Insights SDK RELOG_CALLBACKS 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RELOG_CALLBACKS
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: c5dbed196e6cafaa301b6e07cd0f5546a0f4d563
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78333984"
---
# <a name="relog_callbacks-structure"></a>RELOG_CALLBACKS 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`RELOG_CALLBACKS` 構造体は、 [RELOG_DESCRIPTOR](relog-descriptor-struct.md)オブジェクトを初期化するときに使用されます。 これは、Windows イベントトレーシング (ETW) トレースの再ログ記録中に呼び出す関数を指定します。

## <a name="syntax"></a>構文

```cpp
typedef struct RELOG_CALLBACKS_TAG
{
    OnRelogEventFunc        OnStartActivity;
    OnRelogEventFunc        OnStopActivity;
    OnRelogEventFunc        OnSimpleEvent;
    OnTraceInfoFunc         OnTraceInfo;
    OnBeginEndPassFunc      OnBeginRelogging;
    OnBeginEndPassFunc      OnEndRelogging;
    OnBeginEndPassFunc      OnBeginReloggingPass;
    OnBeginEndPassFunc      OnEndReloggingPass;
} RELOG_CALLBACKS;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `OnStartActivity` | アクティビティの開始イベントを処理するために呼び出されます。 |
| `OnStopActivity` | アクティビティ停止イベントを処理するために呼び出されます。 |
| `OnSimpleEvent` | 単純なイベントを処理するために呼び出されます。 |
| `OnTraceInfo` | `OnBeginReloggingPass` が呼び出された後に、再ログパスの先頭で1回呼び出されます。 |
| `OnBeginRelogging` | 再ログ記録セッションの開始時に、再ログ記録パスが開始される前に呼び出されます。 |
| `OnEndRelogging` | 再ログ記録が終了した後に、再ログセッションを終了するときに呼び出されます。 |
| `OnBeginReloggingPass` | イベントを処理する前に、再ログパスの開始時に呼び出されます。 |
| `OnEndReloggingPass` | すべてのイベントを処理した後、再ログパスの終了時に呼び出されます。 |

## <a name="remarks"></a>解説

`RELOG_CALLBACKS` 構造体のすべてのメンバーは、有効な関数を指す必要があります。 許容される関数シグネチャの詳細については、「 [OnRelogEventFunc](on-relog-event-func-typedef.md)、 [ontraceinfofunc](on-trace-info-func-typedef.md)、および[OnBeginEndPassFunc](on-begin-end-pass-func-typedef.md)」を参照してください。

::: moniker-end
