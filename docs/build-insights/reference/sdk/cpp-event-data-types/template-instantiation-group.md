---
title: TemplateInstantiationGroup クラス
description: C++ BUILD Insights SDK TemplateInstantiationGroup クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TemplateInstantiationGroup
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 281088b4c6cbd39b2fb7677180a7966b490ec3ac
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334542"
---
# <a name="templateinstantiationgroup-class"></a>TemplateInstantiationGroup クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`TemplateInstantiationGroup` クラスは、 [Matcheventstack](../functions/match-event-stack.md)関数および[Matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 これを使用して[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)イベントのグループを照合します。

## <a name="syntax"></a>構文

```cpp
class TemplateInstantiationGroup : public EventGroup<TemplateInstantiation>
{
public:
    TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
};
```

## <a name="members"></a>メンバー

`TemplateInstantiationGroup` クラスには、 [Eventgroup\<TemplateInstantiation\>](event-group.md)の基底クラスから継承されたメンバーと共に、次のメンバーが含まれています。

### <a name="constructors"></a>コンストラクター

[TemplateInstantiationGroup](#template-instantiation-group)

## <a name="template-instantiation-group"></a>TemplateInstantiationGroup

```cpp
TemplateInstantiationGroup(std::deque<TemplateInstantiation>&& group);
```

### <a name="parameters"></a>パラメーター

*グループ*\
[TEMPLATE_INSTANTIATION](../event-table.md#template-instantiation)イベントのグループ。

::: moniker-end
