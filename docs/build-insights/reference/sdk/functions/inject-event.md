---
title: InjectEvent
description: C++ BUILD Insights SDK InjectEvent 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InjectEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7b53eb71cf7a2ae40d04dbc3f8b5829f2737aba4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334416"
---
# <a name="injectevent"></a>InjectEvent

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`InjectEvent` 関数は、 [irelogger](../other-types/irelogger-class.md)インターフェイスを実装する relogger 内で呼び出されます。 これは、再ログセッションの出力トレースファイルに Windows イベントトレーシング (ETW) イベントを書き込むために使用されます。

## <a name="syntax"></a>構文

```cpp
void InjectEvent(
    const void* relogSession,
    LPCGUID providerId,
    PCEVENT_DESCRIPTOR eventDescriptor,
    unsigned long processId,
    unsigned long threadId,
    unsigned short processorIndex,
    long long timestamp,
    unsigned char* data,
    unsigned long byteCount);
```

### <a name="parameters"></a>パラメーター

*Relogsession*\
再ログセッションへのポインター。 再ログセッションは、`IRelogger` インターフェイスを実装する relogging に提供されます。 詳細については、「 [Irelogger](../other-types/irelogger-class.md)」を参照してください。

*providerId*の\
ETW イベントを再ログに記録する Windows イベントトレーシング (ETW) プロバイダー GUID。

*Eventdescriptor*\
再ログされた ETW イベントの ETW イベント記述子。

*processId*\
再ログに記録される ETW イベントのプロセス識別子 (PID)。

*threadId*\
再ログに記録される ETW イベントのスレッド識別子 (TID)。

*Processorindex*\
再ログに記録される ETW イベントのプロセッサインデックス。

*タイムスタンプ*\
再ログに記録される ETW イベントのタイムスタンプ。

*データ*\
再ログされた ETW イベントに含まれるデータへのポインター。

*byteCount*\
データが指すデータのサイズ (バイト単位 *)。*

## <a name="remarks"></a>解説

*プロバイダー GUID*や*イベント記述子*などの etw の概念の詳細については、 [etw のドキュメント](/windows/win32/etw/about-event-tracing)を参照してください。 C++ BUILD Insights SDK を使用して再ログセッションを開始する方法の詳細については、「 [Relog](relog.md)」を参照してください。

::: moniker-end
