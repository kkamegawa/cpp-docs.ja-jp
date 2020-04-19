---
title: Thread クラス
description: ビルドC++インサイト SDK スレッドクラスの参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Thread
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: a74eb130bd3f8be949fef0c19d545f61a72f3934
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334518"
---
# <a name="thread-class"></a>Thread クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`Thread` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [スレッド](../event-table.md#thread)イベントと一致させるには、このメソッドを使用します。

## <a name="syntax"></a>構文

```cpp
class Thread : public Activity
{
public:
    Thread(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

[アクティビティ](activity.md)基本クラスから継承されたメンバーと共に、`Thread` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[スレッド](#thread)

## <a name="thread"></a>レッド

```cpp
Thread(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[スレッド](../event-table.md#thread)イベント。

::: moniker-end
