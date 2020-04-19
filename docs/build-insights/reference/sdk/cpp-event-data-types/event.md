---
title: イベント クラス
description: Build C++ Insights SDK イベントクラスのリファレンスです。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Event
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 205a4e0ca9dd9449933f38f02d4ceafd5df8ead2
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334890"
---
# <a name="event-class"></a>イベント クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`Event` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 任意のイベントと一致させるために使用します。

## <a name="syntax"></a>構文

```cpp
class Event
{
public:
    Event(const RawEvent& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             Timestamp() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;
};
```

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

[イベント](#entity)

### <a name="functions"></a>関数

[データ](#data)
[EventId](#event-id)\
[Eventinstanceid](#event-instance-id)\
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ProcessId](#process-id)\
[Processorindex](#processor-index)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[Timestamp](#timestamp)

## <a name="entity"></a>場合

```cpp
Event(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
任意のイベント。

## <a name="data"></a>データ

```cpp
const void* Data() const;
```

### <a name="return-value"></a>戻り値

このイベントに格納されている追加のデータへのポインター。 このフィールドを解釈する方法の詳細については、「 [EVENT_DATA](../c-event-data-types/event-data-struct.md)」を参照してください。

## <a name="event-id"></a>イベント

```cpp
const unsigned short& EventId() const;
```

### <a name="return-value"></a>戻り値

イベントの種類を識別する番号。 イベント識別子の一覧については、「 [EVENT_ID](../c-event-data-types/event-id-enum.md)」を参照してください。

## <a name="event-instance-id"></a>EventInstanceId

```cpp
const unsigned long long& EventInstanceId() const;
```

### <a name="return-value"></a>戻り値

トレース内のイベントを一意に識別する数値。 同じトレースを複数回分析または再ログ記録する場合、この値は変わりません。 この値を使用して、複数の分析で同じイベントを識別したり、同じトレースに対して再度ログを記録したりします。

## <a name="event-name"></a>EventName

```cpp
const char* EventName() const;
```

### <a name="return-value"></a>戻り値

[EventId](#event-id)によって識別されるイベントの種類の名前を含む ANSI 文字列。

## <a name="event-wide-name"></a>EventWideName

```cpp
const wchar_t* EventWideName() const;
```

### <a name="return-value"></a>戻り値

[EventId](#event-id)によって識別されるイベントの名前を含むワイド文字列。

## <a name="process-id"></a>ProcessId

```cpp
const unsigned long& ProcessId() const;
```

### <a name="return-value"></a>戻り値

イベントが発生したプロセスの識別子。

## <a name="processor-index"></a>ProcessorIndex

```cpp
const unsigned short& ProcessorIndex() const;
```

### <a name="return-value"></a>戻り値

イベントが発生した論理プロセッサの0から始まるインデックス。

## <a name="thread-id"></a>Id

```cpp
const unsigned long& ThreadId() const;
```

### <a name="return-value"></a>戻り値

イベントが発生したスレッドの識別子。

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>戻り値

このイベントのタイマー刻みで計測された期間を評価するときに使用する1秒あたりのタイマー刻みの数。

## <a name="timestamp"></a>タイムスタンプ

```cpp
const long long& Timestamp() const;
```

### <a name="return-value"></a>戻り値

イベントがアクティビティの場合、この関数は、アクティビティが開始された時点でキャプチャされたティック値を返します。 単純なイベントの場合、この関数は、イベントが発生したときにキャプチャされたティック値を返します。

::: moniker-end
