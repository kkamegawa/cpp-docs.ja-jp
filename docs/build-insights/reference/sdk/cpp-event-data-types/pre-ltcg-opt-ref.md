---
title: PreLTCGOptRef クラス
description: C++ BUILD Insights SDK PreLTCGOptRef クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- PreLTCGOptRef
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4690feddcf615a82226ce5ad2f3ee242749db04a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334608"
---
# <a name="preltcgoptref-class"></a>PreLTCGOptRef クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`PreLTCGOptRef` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [PRE_LTCG_OPT_REF](../event-table.md#pre-ltcg-opt-ref)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class PreLTCGOptRef : public Activity
{
public:
    PreLTCGOptRef(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

[アクティビティ](activity.md)基本クラスから継承されたメンバーと共に、`PreLTCGOptRef` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[PreLTCGOptRef](#pre-ltcg-opt-ref)

## <a name="pre-ltcg-opt-ref"></a>PreLTCGOptRef

```cpp
PreLTCGOptRef(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[PRE_LTCG_OPT_REF](../event-table.md#pre-ltcg-opt-ref)イベントです。

::: moniker-end
