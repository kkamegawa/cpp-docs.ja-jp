---
title: MatchEventInMemberFunction
description: C++ビルドインサイト SDK MatchEventInMemberFunction 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: eabbb8a91609b1447ebcc19af32df2ffed347c24
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334380"
---
# <a name="matcheventinmemberfunction"></a>MatchEventInMemberFunction

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEventInMemberFunction` 関数は、メンバー関数の最初のパラメーターで記述される型に対してイベントを照合するために使用されます。 一致するイベントは、後続の処理のためにメンバー関数に転送されます。

## <a name="syntax"></a>構文

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     TEvent,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventInMemberFunction(
    const RawEvent&          event,
    TInterface*              objectPtr,
    TReturn (TInterface::*   memberFunc)(TEvent, TExtraParams...),
    TExtraArgs&&...          extraArgs);
```

### <a name="parameters"></a>パラメーター

*Tinterface*\
メンバー関数を格納している型。

*Treturn*\
メンバー関数の戻り値の型。

*Tevent*\
照合するイベントの型。

*TExtraParams*\
一致するイベントの種類と共に、メンバー関数によって受け入れられる追加パラメーターの型。

*TExtraArgs*\
`MatchEventInMemberFunction`に渡された余分な引数の型。

*event*\
*Tevent*によって記述されるイベントの種類と照合するイベント。

*Objectptr*\
*Memberfunc*が呼び出されるオブジェクトへのポインター。

*Memberfunc*\
照合するイベントの種類を記述するメンバー関数。

*extraArgs*\
イベントの種類のパラメーターと共に*Memberfunc*に完全に転送される引数。

### <a name="return-value"></a>戻り値

一致が成功した場合は**true** 、それ以外の場合は**false**の**ブール**値。

## <a name="remarks"></a>解説

*Tevent*パラメーターに使用するイベントの種類は、*キャプチャクラス*の一覧から選択できます。 イベントとそれらを照合するために使用できるキャプチャクラスの一覧については、「 [event table](../event-table.md)」を参照してください。

## <a name="example"></a>例

```cpp
void MyClass::Foo1(Function f) {}

void MyClass::Foo2(Compiler cl) {}

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    auto& functionEvent = eventStack.Back(); // The Function event

    bool b1 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo1);

    bool b2 = MatchEventInMemberFunction(
        functionEvent, this, &MyClass::Foo2);

    // b1: true because the first parameter of Foo1 is Function.
    // b2: false because the first parameter of Foo2 isn't Function.
}
```

::: moniker-end
