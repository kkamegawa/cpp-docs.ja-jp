---
title: LTCG クラス
description: C++ BUILD INSIGHTS SDK LTCG クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LTCG
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 8e75795e46d64752fd4d1a643585cf6f131cb096
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334674"
---
# <a name="ltcg-class"></a>LTCG クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`LTCG` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 このメソッドを使用して、 [LTCG](../event-table.md#ltcg)イベントに一致させます。

## <a name="syntax"></a>構文

```cpp
class LTCG : public Activity
{
public:
    LTCG(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

[アクティビティ](activity.md)基本クラスから継承されたメンバーと共に、`LTCG` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[LTCG](#ltcg)

## <a name="ltcg"></a>LTCG

```cpp
LTCG(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[LTCG](../event-table.md#ltcg)イベント。

::: moniker-end
