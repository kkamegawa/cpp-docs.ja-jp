---
title: MatchEvent
description: C++ BUILD Insights SDK matchevent 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: f8022953e2f56f7c8917f161b094c50e0c5ecbdf
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334356"
---
# <a name="matchevent"></a>MatchEvent

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEvent` 関数は、イベントをイベントの種類の一覧と照合するために使用されます。 イベントがリスト内の型と一致する場合は、後続の処理のためにハンドラーに転送されます。

## <a name="syntax"></a>構文

```cpp
template <
    typename        TEvent,
    typename...     TEvents,
    typename        TCallable,
    typename...     TExtraArgs>
bool MatchEvent(
    const RawEvent& event,
    TCallable&&     callable,
    TExtraArgs&&... extraArgs);
```

### <a name="parameters"></a>パラメーター

*Tevent*\
照合する最初のイベントの種類。

*Tevents*\
照合する残りのイベントの種類。

*Tcallable*可能\
`operator()`をサポートする型。 この演算子に渡される引数の詳細については、*呼び出し*可能なパラメーターの説明を参照してください。

*TExtraArgs*\
`MatchEvent`に渡された余分な引数の型。

*event*\
*Tevent*および*tevent*によって記述されるイベントの種類と照合するイベント。

*呼び出し*可能\
`MatchEvent` は、 *Tevent*および*tevent*に記述されているイベントの種類とイベントを正常に照合した後に、*呼び出し*可能を呼び出します。 *呼び出し*可能に渡される最初の引数は、一致したイベントの種類の r 値です。 *ExtraArgs* parameter pack は、*呼び出し*可能な残りのパラメーターで完全に転送されます。  

*extraArgs*\
一致するイベントの種類と共に、*呼び出し*可能に完全に転送される引数。

### <a name="return-value"></a>戻り値

一致が成功した場合は**true** 、それ以外の場合は**false**の**ブール**値。

## <a name="remarks"></a>解説

*Tevent*および*tevent*パラメーターに使用するイベントの種類は、*キャプチャクラス*の一覧から選択されます。 イベントとそれらを照合するために使用できるキャプチャクラスの一覧については、「 [event table](../event-table.md)」を参照してください。

## <a name="example"></a>例

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEvent<Function, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});

    bool b2 = MatchEvent<CodeGeneration, Thread>(
        functionEvent, [](auto matchedEvent){ /* Do something... */});


    // b1: true because the list of types contains Function, which is
    //     the type of the event we are trying to match.
    // b2: false because the list of types doesn't contain Function.
}
```

::: moniker-end
