---
title: FrontEndPass クラス
description: C++ BUILD Insights SDK FrontEndPass クラス参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- FrontEndPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: cc0bf38c46b51d4a49da46be88e23afa64c12cc8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334782"
---
# <a name="frontendpass-class"></a>FrontEndPass クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`FrontEndPass` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [FRONT_END_PASS](../event-table.md#front-end-pass)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class FrontEndPass : public CompilerPass
{
public:
    FrontEndPass(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

`FrontEndPass` クラスには、 [CompilerPass](compiler-pass.md)基底クラスから継承されたメンバーと共に、次のメンバーが含まれています。

### <a name="constructors"></a>コンストラクター

[FrontEndPass](#front-end-pass)

## <a name="front-end-pass"></a>FrontEndPass

```cpp
FrontEndPass(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[FRONT_END_PASS](../event-table.md#front-end-pass)イベントです。

::: moniker-end
