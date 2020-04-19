---
title: SimpleEvent クラス
description: Build C++ Insights SDK simpleevent クラスの参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- SimpleEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4c30f81236138328322d8c870d4ad69d9988b49a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334590"
---
# <a name="simpleevent-class"></a>SimpleEvent クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`SimpleEvent` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 任意の単純なイベントと一致させるために使用します。 `SimpleEvent` クラスによって照合できるすべてのイベントを表示するには、[イベントテーブル](../event-table.md)を参照してください。

## <a name="syntax"></a>構文

```cpp
class SimpleEvent : public Event
{
public:
    SimpleEvent(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

[イベント](event.md)基本クラスから継承されたメンバーと共に、`SimpleEvent` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[SimpleEvent](#simple-event)

## <a name="simple-event"></a>SimpleEvent

```cpp
SimpleEvent(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
任意の単純なイベント。

::: moniker-end
