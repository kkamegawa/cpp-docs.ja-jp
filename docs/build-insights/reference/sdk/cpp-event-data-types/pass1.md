---
title: Pass1 クラス
description: C++ BUILD Insights SDK Pass1 クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Pass1
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: d81a933e21f6976624808be358230305459e4992
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334626"
---
# <a name="pass1-class"></a>Pass1 クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`Pass1` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [PASS1](../event-table.md#pass1)イベントと照合する場合に使用します。

## <a name="syntax"></a>構文

```cpp
class Pass1 : public LinkerPass
{
public:
    Pass1(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

`Pass1` クラスには、 [LinkerPass](linker-pass.md)基底クラスから継承されたメンバーと共に、次のメンバーが含まれています。

### <a name="constructors"></a>コンストラクター

[Pass1](#pass1)

## <a name="pass1"></a>Pass1

```cpp
Pass1(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[PASS1](../event-table.md#pass1)イベントです。

::: moniker-end
