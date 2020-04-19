---
title: EventStack クラス
description: C++ビルドインサイト SDK eventstack クラス参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EventStack
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6da2fd25082399b82d788c5d119a39e2f7388714
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334896"
---
# <a name="eventstack-class"></a>EventStack クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`EventStack` クラスは、[イベント](event.md)オブジェクトのコレクションです。 C++ BUILD Insights SDK から受信したすべてのイベントは、`EventStack` オブジェクトの形式で取得されます。 このスタックの最後のエントリは、現在処理中のイベントです。 最後のエントリの前にあるエントリは、現在のイベントの親階層です。 ビルドインサイトでC++使用されるイベントモデルの詳細については、「 [event table](../event-table.md)」を参照してください。

## <a name="syntax"></a>構文

```cpp
class EventStack
{
public:
    EventStack(const EVENT_COLLECTION_DATA& data);

    size_t      Size() const;
    RawEvent    Back() const;
    RawEvent    operator[] (size_t index) const;
};
```

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

[EventStack](#event-stack)

### <a name="functions"></a>関数

[Back](#back)
[operator []](#subscript-operator)
[サイズ](#size)

## <a name="back"></a>戻る

```cpp
RawEvent Back() const;
```

### <a name="return-value"></a>戻り値

スタックの最後のエントリを表す[Rawevent](raw-event.md)オブジェクト。 イベントスタックの最後のエントリは、トリガーされたイベントです。

## <a name="event-stack"></a>EventStack

```cpp
EventStack(const EVENT_COLLECTION_DATA& data);
```

### <a name="parameters"></a>パラメーター

*データ*\
`EventStack` の作成元の生データ。

### <a name="remarks"></a>解説

通常、`EventStack` オブジェクトを作成する必要はありません。 これらは、分析または再C++ログセッション中にイベントが処理されるときに、BUILD Insights SDK によって提供されます。

## <a name="subscript-operator"></a>演算子 []

```cpp
RawEvent operator[] (size_t index) const;
```

### <a name="parameters"></a>パラメーター

*インデックス*\
イベントスタック内でアクセスする要素のインデックス。

### <a name="return-value"></a>戻り値

イベントスタック内の*インデックス*によって示される位置に格納されているイベントを表す[rawevent](raw-event.md)オブジェクト。

## <a name="size"></a>幅

```cpp
size_t Size() const;
```

### <a name="return-value"></a>戻り値

イベントスタックのサイズ。

::: moniker-end
