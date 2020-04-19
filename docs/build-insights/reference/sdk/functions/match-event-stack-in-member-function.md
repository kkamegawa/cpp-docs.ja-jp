---
title: MatchEventStackInMemberFunction
description: C++ビルドインサイト SDK MatchEventStackInMemberFunction 関数リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- MatchEventStackInMemberFunction
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2a966ea5209a25a62c08cb0873d0565299a15d27
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334368"
---
# <a name="matcheventstackinmemberfunction"></a>MatchEventStackInMemberFunction

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`MatchEventStackInMemberFunction` 関数は、メンバー関数のパラメーターリストによって記述される特定のイベント階層に対してイベントスタックを照合するために使用されます。 一致する階層は、後続の処理のためにメンバー関数に転送されます。 イベント、イベントスタック、および階層の詳細については、「 [event table](../event-table.md)」を参照してください。

## <a name="syntax"></a>構文

```cpp
template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, TExtraParams...),
    TExtraArgs&&...           extraArgs);

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, TExtraParams...),
    TExtraArgs&&...           extraArgs);

// Etc...

template <
    typename     TInterface,
    typename     TReturn,
    typename     T1,
    typename     T2,
    typename     T3,
    typename     T4,
    typename     T5,
    typename     T6,
    typename     T7,
    typename     T8,
    typename     T9,
    typename     T10,
    typename...  TExtraParams,
    typename...  TExtraArgs>
bool MatchEventStackInMemberFunction(
    const EventStack&         eventStack,
    TInterface*               objectPtr,
    TReturn (TInterface::*    memberFunc)(T1, T2, T3, T4, T5, T6, T7, T8, T9, T10, TExtraParams...),
    TExtraArgs&&...           extraArgs);
```

### <a name="parameters"></a>パラメーター

*Tinterface*\
メンバー関数を格納している型。

*Treturn*\
メンバー関数の戻り値の型。

*T1*、...、 *T10*\
照合するイベント階層を記述する型。

*TExtraParams*\
メンバー関数によって受け入れられる追加パラメーターの型、およびイベント階層型。

*TExtraArgs*\
`MatchEventStackInMemberFunction`に渡された余分な引数の型。

*Eventstack*\
*T1*によって*T10*によって記述されるイベントの種類の階層と照合するイベントスタック。

*Objectptr*\
*Memberfunc*が呼び出されるオブジェクトへのポインター。

*Memberfunc*\
照合するイベントの種類の階層を記述するメンバー関数。

*extraArgs*\
イベントの種類の階層のパラメーターと共に*Memberfunc*に完全に転送される引数。

### <a name="return-value"></a>戻り値

一致が成功した場合は**true** 、それ以外の場合は**false**の**ブール**値。

## <a name="remarks"></a>解説

*Eventstack*の最後のイベントは、一致するイベントの種類の階層の最後のエントリと常に一致します。 イベントの種類の階層内の他のすべての型は、同じ順序で指定されていれば、最後のイベントを除く、 *Eventstack*内の任意の位置と一致させることができます。

*T1*によって*T10*パラメーターに使用するイベントの種類は、*キャプチャクラス*の一覧から選択されます。 イベントとそれらを照合するために使用できるキャプチャクラスの一覧については、「 [event table](../event-table.md)」を参照してください。

## <a name="example"></a>例

```cpp
void MyClass::Foo1(Compiler cl, BackEndPass bep, C2DLL c2,
    CodeGeneration cg, Thread t, Function f) { }

void MyClass::Foo2(Compiler cl, Function f) { }

void MyClass::Foo3(Thread t, Compiler cl, Function f) { }

void MyClass::Foo4(Compiler cl) { }

void MyClass::OnStartActivity(const EventStack& eventStack)
{
    // Let's assume eventStack contains:
    // [Compiler, BackEndPass, C2DLL, CodeGeneration, Thread, Function]

    bool b1 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo1);

    bool b2 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo2);

    bool b3 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo3);

    bool b4 = MatchEventStackInMemberFunction(
        eventStack, this, &MyClass::Foo4);

    // b1: true because the parameter types of Foo1 match the eventStack
    //     exactly.
    // b2: true because Function is the last entry in both the member
    //     function parameter list and 'eventStack', and also because
    //     Compiler comes before Function in 'eventStack' and in the
    //     parameter type list.
    // b3: false because, even though both Thread and Compiler come
    //     before Function in 'eventStack', the member function parameter
    //     list doesn't list them in the right order.
    // b4: false because the last entry in the member function parameter
    //     list is Compiler, which doesn't match the last entry in 'eventStack'
    //     (Function).
}
```

::: moniker-end
