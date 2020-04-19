---
title: LinkerPass クラス
description: C++ BUILD Insights SDK LinkerPass クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- LinkerPass
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 49a46b57d82391f4c253128c14b1b81d52945eae
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334722"
---
# <a name="linkerpass-class"></a>LinkerPass クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`LinkerPass` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [PASS1](../event-table.md#pass1)イベントまたは[PASS2](../event-table.md#pass2)イベントと一致させるには、このメソッドを使用します。

## <a name="syntax"></a>構文

```cpp
class LinkerPass : public Activity
{
public:
    LinkerPass(const RawEvent& event);
};
```

## <a name="members"></a>メンバー

[アクティビティ](activity.md)基本クラスから継承されたメンバーと共に、`LinkerPass` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[LinkerPass](#linker-pass)

## <a name="linker-pass"></a>LinkerPass

```cpp
LinkerPass(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[PASS1](../event-table.md#pass1)または[PASS2](../event-table.md#pass2)イベント。

::: moniker-end
