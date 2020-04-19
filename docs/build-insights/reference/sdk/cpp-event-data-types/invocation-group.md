---
title: InvocationGroup クラス
description: C++ BUILD Insights SDK InvocationGroup クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- InvocationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: b9a2bbcd2b7649b9b5703adc08ed41b272e10276
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334752"
---
# <a name="invocationgroup-class"></a>InvocationGroup クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`InvocationGroup` クラスは、 [Matcheventstack](../functions/match-event-stack.md)関数および[Matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 これを使用して、[コンパイラ](../event-table.md#compiler)イベントと[リンカー](../event-table.md#linker)イベントの組み合わせを含むグループを照合します。

## <a name="syntax"></a>構文

```cpp
class InvocationGroup : public EventGroup<Invocation>
{
public:
    InvocationGroup(std::deque<Invocation>&& group);
};
```

## <a name="members"></a>メンバー

`InvocationGroup` クラスには、 [Eventgroup\<呼び出し\>](event-group.md)基底クラスから継承されたメンバーと共に、次のメンバーが含まれています。

### <a name="constructors"></a>コンストラクター

[InvocationGroup](#invocation-group)

## <a name="invocation-group"></a>InvocationGroup

```cpp
InvocationGroup(std::deque<Invocation>&& group);
```

### <a name="parameters"></a>パラメーター

*グループ*\
[コンパイラ](../event-table.md#compiler)イベントと[リンカー](../event-table.md#linker)イベントの組み合わせを含むグループ。

::: moniker-end
