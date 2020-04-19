---
title: Pass2 クラス
description: C++ BUILD Insights SDK Pass2 クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Pass2
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 0deca0a06a74e4728cb2c78657bf5e077b42878b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334614"
---
# <a name="pass2-class"></a>Pass2 クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`Pass2` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [PASS2](../event-table.md#pass2)イベントと照合する場合に使用します。

## <a name="syntax"></a>構文

```cpp
class Pass2 : public LinkerPass
{
public:
    Pass2(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

`Pass2` クラスには、 [LinkerPass](linker-pass.md)基底クラスから継承されたメンバーと共に、次のメンバーが含まれています。

### <a name="constructors"></a>コンストラクター

[Pass2](#pass2)

## <a name="pass2"></a>Pass2

```cpp
Pass2(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[PASS2](../event-table.md#pass2)イベントです。

::: moniker-end
