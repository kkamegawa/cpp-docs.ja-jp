---
title: FrontEndFileGroup クラス
description: C++ BUILD Insights SDK FrontEndFileGroup クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndFileGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 343a5a0d798d6c719088bd49668e70b10fba6d1a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334830"
---
# <a name="frontendfilegroup-class"></a>FrontEndFileGroup クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`FrontEndFileGroup` クラスは、 [Matcheventstack](../functions/match-event-stack.md)関数および[Matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 これを使用して[FRONT_END_FILE](../event-table.md#front-end-file)イベントのグループを照合します。

## <a name="syntax"></a>構文

```cpp
class FrontEndFileGroup : public EventGroup<FrontEndFile>
{
public:
    FrontEndFileGroup(std::deque<FrontEndFile>&& group);
};
```

## <a name="members"></a>メンバー

\>基底クラスの[Eventgroup\<FrontEndFile](event-group.md)から継承されたメンバーと共に、`FrontEndFileGroup` クラスには次のメンバーが含まれています。

### <a name="constructors"></a>コンストラクター

[FrontEndFileGroup](#front-end-file-group)

## <a name="front-end-file-group"></a>FrontEndFileGroup

```cpp
FrontEndFileGroup(std::deque<FrontEndFile>&& group);
```

### <a name="parameters"></a>パラメーター

*グループ*\
[FRONT_END_FILE](../event-table.md#front-end-file)イベントのグループ。

::: moniker-end
