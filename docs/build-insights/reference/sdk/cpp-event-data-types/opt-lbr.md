---
title: OptLBR クラス
description: C++ビルドインサイト SDK OptLBR クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- OptLBR
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: fb2482ce943dbf393e74d6398498cc185410140a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334632"
---
# <a name="optlbr-class"></a>OptLBR クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`OptLBR` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [OPT_LBR](../event-table.md#opt-lbr)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class OptLBR : public Activity
{
public:
    OptLBR(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

[アクティビティ](activity.md)基本クラスから継承されたメンバーと共に、`OptLBR` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[OptLBR](#opt-lbr)

## <a name="opt-lbr"></a>OptLBR

```cpp
OptLBR(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[OPT_LBR](../event-table.md#opt-lbr)イベントです。

::: moniker-end
