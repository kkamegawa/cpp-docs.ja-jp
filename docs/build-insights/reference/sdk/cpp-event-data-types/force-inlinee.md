---
title: ForceInlinee クラス
description: C++ BUILD Insights SDK ForceInlinee クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- ForceInlinee
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 7d3cce13601a0b3edbcd2b57664b2d0d94a7d3df
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334836"
---
# <a name="forceinlinee-class"></a>ForceInlinee クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`ForceInlinee` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 [FORCE_INLINEE](../event-table.md#force-inlinee)イベントと一致させるには、これを使用します。

## <a name="syntax"></a>構文

```cpp
class ForceInlinee : public SimpleEvent
{
public:
    ForceInlinee(const RawEvent& event);

    const char*             Name() const;
    const unsigned short&   Size() const;
};
```

## <a name="members"></a>メンバー

[Simpleevent](simple-event.md)基本クラスから継承されたメンバーと共に、`ForceInlinee` クラスには次のメンバーが含まれます。

### <a name="constructors"></a>コンストラクター

[ForceInlinee](#force-inlinee)

### <a name="functions"></a>関数

[名前](#name)
[サイズ](#size)

## <a name="force-inlinee"></a>ForceInlinee

```cpp
ForceInlinee(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
[FORCE_INLINEE](../event-table.md#force-inlinee)イベントです。

## <a name="name"></a> Name

```cpp
const char* Name() const;
```

### <a name="return-value"></a>戻り値

UTF-8 でエンコードされた強制インライン関数の名前。

## <a name="size"></a>幅

```cpp
const unsigned short& Size() const;
```

### <a name="return-value"></a>戻り値

中間命令カウントとしての強制インライン関数のサイズ。

::: moniker-end
