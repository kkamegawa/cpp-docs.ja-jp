---
title: MatchEventStack
description: C++ビルドインサイト SDK MatchEventStack 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 445c2d00c24da10754d32256de0c691e82b557e1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334362"
---
# <a name="matcheventstack"></a>MatchEventStack

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEventStack` 関数は、イベントスタックを特定のイベント階層と照合するために使用されます。 一致する階層は、さらに処理するためにハンドラーに転送されます。 イベント、イベントスタック、および階層の詳細については、「 [event table](../event-table.md)」を参照してください。

## <a name="syntax"></a>構文

```cpp
template <
    typename          TEvent,
    typename...       TEvents,
    typename          TCallable,
    typename...       TExtraArgs>
bool MatchEventStack(
    const EventStack& eventStack,
    TCallable&&       callable,
    TExtraArgs&&...   extraArgs);
```

### <a name="parameters"></a>パラメーター

*Tevent*\
イベントスタックで一致する eldest 親の型。

*Tevents*\
イベントスタックで一致させる残りの型。

*Tcallable*可能\
`operator()`をサポートする型。 この演算子に渡される引数の詳細については、*呼び出し*可能なパラメーターの説明を参照してください。

*TExtraArgs*\
`MatchEventStack`に渡される追加の引数の型。

*Eventstack*\
*Tevent*および*tevent*によって記述されるイベントの種類の階層と照合するイベントスタック。

*呼び出し*可能\
イベントスタックと*tevent*および*tevent*によって記述されたイベントの種類の階層とが正常に照合されると、`MatchEventStack` は呼び出し可能な呼び出しを*行います。* これは、イベント階層内の型ごとに1つの r 値引数を*呼び出し*可能に渡します。 *ExtraArgs* parameter pack は、*呼び出し*可能な残りのパラメーターで完全に転送されます。

*extraArgs*\
一致するイベントの種類と共に、*呼び出し*可能に完全に転送される引数。

### <a name="return-value"></a>戻り値

一致が成功した場合は**true** 、それ以外の場合は**false**の**ブール**値。

## <a name="remarks"></a>解説

*Eventstack*の最後のイベントは、連結された \[*tevent*, *tevent...* \] type リストの最後のエントリと常に一致します。 他のすべての*Tevent*エントリと*tevent*エントリは、同じ順序で指定されていれば、最後のイベントを除く、 *eventstack*内の任意の位置と一致することができます。

*Tevent*および*tevent*パラメーターに使用するイベントの種類は、*キャプチャクラス*の一覧から選択されます。 イベントとそれらを照合するために使用できるキャプチャクラスの一覧については、「 [event table](../event-table.md)」を参照してください。

## <a name="example"></a>例

```cpp
void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStack<Compiler, BackEndPass, C2DLL,
                CodeGeneration, Thread, Function>(
        eventStack, [](Compiler cl, BackEndPass bep, C2DLL c2,
            CodeGeneration cg, Thread t, Function f){ /* Do something ... */ });

    bool b2 = MatchEventStack<Compiler, Function>(
        eventStack, [](Compiler cl, Function f){ /* Do something... */ });

    bool b3 = MatchEventStack<Thread, Compiler, Function>(
        eventStack, [](Thread t, Compiler cl Function f){ /* Do something... */ });

    bool b4 = MatchEventStack<Compiler>(
        eventStack, [](Compiler cl){ /* Do something... */ });


    // b1: true because the list of types matches the eventStack exactly.
    // b2: true because Function is the last entry in both the type list
    //     and 'eventStack', and also because Compiler comes before
    //     Function in 'eventStack' and in the type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', they aren't listed in the
    //     right order in the type list.
    // b4: false because the last entry in the type list is Compiler,
    //     which doesn't match the last entry in 'eventStack' (Function).
}
```

::: moniker-end
