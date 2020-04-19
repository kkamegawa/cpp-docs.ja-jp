---
title: LinkerGroup クラス
description: C++ BUILD Insights SDK LinkerGroup クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 95b0dcc3a771ec07ee60185a79a5ddbc29434b5d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334728"
---
# <a name="linkergroup-class"></a>LinkerGroup クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`LinkerGroup` クラスは、 [Matcheventstack](../functions/match-event-stack.md)関数および[Matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 これを使用して、[リンカー](../event-table.md#linker)イベントのグループを照合します。

## <a name="syntax"></a>構文

```cpp
class LinkerGroup : public EventGroup<Linker>
{
public:
    LinkerGroup(std::deque<Linker>&& group);
};
```

## <a name="members"></a>メンバー

`LinkerGroup` クラスには、 [Eventgroup\<リンカー\>](event-group.md)基底クラスから継承されたメンバーと共に、次のメンバーが含まれています。

### <a name="constructors"></a>コンストラクター

[LinkerGroup](#linker-group)

## <a name="linker-group"></a>LinkerGroup

```cpp
LinkerGroup(std::deque<Linker>&& group);
```

### <a name="parameters"></a>パラメーター

*グループ*\
[リンカー](../event-table.md#linker)イベントのグループ。

::: moniker-end
