---
title: TopDown クラス
description: C++ BUILD Insights SDK topdown クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TopDown
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2d4ef1f2f824bca9ab8e45f8fb030727e6e4007b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334506"
---
# <a name="topdown-class"></a>TopDown クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`TopDown` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [TOP_DOWN](../event-table.md#top-down)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class TopDown : public Activity
{
public:
    TopDown(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

[アクティビティ](activity.md)基本クラスから継承されたメンバーと共に、`TopDown` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[TopDown](#top-down)

## <a name="top-down"></a>TopDown

```cpp
TopDown(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[TOP_DOWN](../event-table.md#top-down)イベントです。

::: moniker-end
