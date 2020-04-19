---
title: RawEvent クラス
description: Build C++ Insights SDK RawEvent クラスの参照。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- RawEvent
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4088920d6070e14d64ccd046238c1c49b2556ea1
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334602"
---
# <a name="rawevent-class"></a>RawEvent クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`RawEvent` クラスは、 [Eventstack](event-stack.md)内の一般的なイベントを表すために使用されます。

## <a name="syntax"></a>構文

```cpp
class RawEvent
{
public:
    RawEvent(const EVENT_DATA& event);

    const unsigned short&        EventId() const;
    const unsigned long long&    EventInstanceId() const;
    const long long&             TickFrequency() const;
    const long long&             StartTimestamp() const;
    const long long&             StopTimestamp() const;
    const long long&             ExclusiveDurationTicks() const;
    const long long&             CPUTicks() const;
    const long long&             ExclusiveCPUTicks() const;
    const long long&             WallClockTimeResponsibilityTicks() const;
    const long long&             ExclusiveWallClockTimeResponsibilityTicks() const;
    const void*                  Data() const;
    const unsigned long&         ProcessId() const;
    const unsigned long&         ThreadId() const;
    const unsigned short&        ProcessorIndex() const;
    const char*                  EventName() const;
    const wchar_t*               EventWideName() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>解説

`RawEvent` クラスのいくつかのメンバー関数は、ティック数を返します。 C++ビルドインサイトでは、Windows のパフォーマンスカウンターをタイマー刻みのソースとして使用します。 ティック数をティックの頻度と共に使用して、秒などの時間単位に変換する必要があります。 `TickFrequency` メンバー関数を呼び出して、ティックの頻度を取得できます。 ティックを時間単位に変換する方法の例については、 [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example)のページを参照してください。

タイマー刻みを自分で変換しない場合、`RawEvent` クラスには、時間値をナノ秒単位で返すメンバー関数が用意されています。 Standard C++ `chrono` ライブラリを使用して、ナノ秒を他の時間単位に変換します。

## <a name="members"></a>メンバー

### <a name="constructor"></a>Constructor

[RawEvent](#raw-event)

### <a name="functions"></a>関数

[Cpu タイマー刻み](#cpu-ticks)\
[Cpu 時間](#cpu-time)\
[データ](#data)\
[期間](#duration)\
[EventId](#event-id)
[Eventinstanceid](#event-instance-id)
[EventName](#event-name)\
[EventWideName](#event-wide-name)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[ProcessId](#process-id)\
[Processorindex](#processor-index)\
[Starttimestamp](#start-timestamp)\
[Stoptimestamp](#stop-timestamp)\
[ThreadId](#thread-id)\
[TickFrequency](#tick-frequency)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="raw-event"></a>RawEvent

```cpp
RawEvent(const EVENT_DATA& data);
```

### <a name="parameters"></a>パラメーター

*event*\
イベントのデータ。

## <a name="cpu-ticks"></a>Cpu タイマー刻み

```cpp
const long long& CPUTicks() const;
```

### <a name="return-value"></a>戻り値

このアクティビティ中に発生した CPU タイマー刻みの数。 CPU の目盛りは、通常のティックとは異なります。 CPU タイマー刻みは、CPU がアクティビティ内のコードを実行している場合にのみカウントされます。 CPU タイマー刻みは、アクティビティに関連付けられているスレッドがスリープ状態のときにはカウントされません。

## <a name="cpu-time"></a>CPUTime

```cpp
std::chrono::nanoseconds CPUTime()() const;
```

### <a name="return-value"></a>戻り値

CPU がこのアクティビティ内でコードを実行していた時間の長さ。 子アクティビティが個別のスレッドで実行される場合、この値はアクティビティの期間よりも長くなる可能性があります。 値はナノ秒単位で返されます。

## <a name="data"></a>データ

```cpp
const void* Data() const;
```

### <a name="return-value"></a>戻り値

このイベントに格納されている追加のデータへのポインター。 このフィールドを解釈する方法の詳細については、「 [EVENT_DATA](../c-event-data-types/event-data-struct.md)」を参照してください。

## <a name="duration"></a>全

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>戻り値

アクティビティの継続時間 (ナノ秒単位)。

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

[EventId](#event-id)によって識別されるイベントの種類の名前を含むワイド文字列。

## <a name="exclusive-cpu-ticks"></a>ExclusiveCPUTicks

```cpp
const long long& ExclusiveCPUTicks() const;
```

### <a name="return-value"></a>戻り値

CPU タイマー[刻みと同じ](#cpu-ticks)ですが、子アクティビティで発生した CPU ティックは含まれません。

## <a name="exclusive-cpu-time"></a>ExclusiveCPUTime

```cpp
std::chrono::nanoseconds ExclusiveCPUTime() const;
```

### <a name="return-value"></a>戻り値

子アクティビティの CPU 時間は含まれない点を除いて、cpu[時間](#cpu-time)と同じです。

## <a name="exclusive-duration"></a>ExclusiveDuration

```cpp
std::chrono::nanoseconds ExclusiveDuration() const;
```

### <a name="return-value"></a>戻り値

アクティビティの継続時間 (ナノ秒単位)。子アクティビティで費やされた時間は含まれません。

## <a name="exclusive-duration-ticks"></a>ExclusiveDurationTicks

```cpp
const long long& ExclusiveDurationTicks() const;
```

### <a name="return-value"></a>戻り値

このアクティビティで発生したタイマー刻みの数。子アクティビティで発生したタイマー刻みの数は除外されます。

## <a name="exclusive-wall-clock-time-responsibility"></a>ExclusiveWallClockTimeResponsibility

```cpp
std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
```

### <a name="return-value"></a>戻り値

[WallClockTimeResponsibility](#wall-clock-time-responsibility)と同じですが、子アクティビティのウォールクロックの時間は含まれません。

## <a name="exclusive-wall-clock-time-responsibility-ticks"></a>ExclusiveWallClockTimeResponsibilityTicks

```cpp
const long long& ExclusiveWallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>戻り値

[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)と同じですが、子アクティビティのウォールクロック時間の責任を含みません。

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

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>戻り値

アクティビティが開始された時点でキャプチャされたティック値。

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>戻り値

アクティビティが停止した時点でキャプチャされたティック値。

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

## <a name="wall-clock-time-responsibility"></a>WallClockTimeResponsibility

```cpp
std::chrono::nanoseconds WallClockTimeResponsibility() const;
```

### <a name="return-value"></a>戻り値

このアクティビティのウォールクロックの時間 (ナノ秒単位)。 ウォールクロックの時間の役割の詳細については、「 [WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)」を参照してください。

## <a name="wall-clock-time-responsibility-ticks"></a>WallClockTimeResponsibilityTicks

```cpp
const long long& WallClockTimeResponsibilityTicks() const;
```

### <a name="return-value"></a>戻り値

このアクティビティの全体的なウォールクロック時間に対する影響を表すティック数。 ウォールクロックの時間の責任は、通常のティックとは異なります。 ウォールクロックの責任のタイマー刻みは、アクティビティ間の並列化を考慮します。 2つの並列アクティビティの期間は、50ティック、開始時刻と終了時刻が同じである場合があります。 この場合、両方の get に25ティックのウォールクロック時間が割り当てられます。

::: moniker-end
