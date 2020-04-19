---
title: Activity クラス
description: Build C++ Insights SDK アクティビティクラスのリファレンスです。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- Activity
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 6de411c375b42e4acfb44bf0fac9d28ad57f1ca7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78335028"
---
# <a name="activity-class"></a>Activity クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`Activity` クラスは、 [Matchevent](../functions/match-event.md)、 [matcheventinmemberfunction](../functions/match-event-in-member-function.md)、 [Matcheventstack](../functions/match-event-stack.md)、および[matcheventstackinmemberfunction](../functions/match-event-stack-in-member-function.md)関数と共に使用されます。 任意のアクティビティイベントと一致させるには、これを使用します。 `Activity` クラスによって照合できるすべてのイベントを表示するには、[イベントテーブル](../event-table.md)を参照してください。

## <a name="syntax"></a>構文

```cpp
class Activity : public Event
{
public:
    Activity(const RawEvent& event);

    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;
    const long long& ExclusiveDurationTicks() const;
    const long long& CPUTicks() const;
    const long long& ExclusiveCPUTicks() const;
    const long long& WallClockTimeResponsibilityTicks() const;
    const long long& ExclusiveWallClockTimeResponsibilityTicks() const;

    std::chrono::nanoseconds Duration() const;
    std::chrono::nanoseconds ExclusiveDuration() const;
    std::chrono::nanoseconds CPUTime() const ;
    std::chrono::nanoseconds ExclusiveCPUTime() const;
    std::chrono::nanoseconds WallClockTimeResponsibility() const;
    std::chrono::nanoseconds ExclusiveWallClockTimeResponsibility() const;
};
```

## <a name="remarks"></a>解説

`Activity` クラスのいくつかのメンバー関数は、ティック数を返します。 C++ビルドインサイトでは、Windows のパフォーマンスカウンターをタイマー刻みのソースとして使用します。 ティック数をティックの頻度と共に使用して、秒などの時間単位に変換する必要があります。 [イベント](event.md)基本クラスで使用できる `TickFrequency` メンバー関数は、ティック頻度を取得するために呼び出すことができます。 [EVENT_DATA](../c-event-data-types/event-data-struct.md#tick-conversion-example)のページには、ティックを時間単位に変換する例が示されています。

タイマー刻みを時間単位に変換しない場合、`Activity` クラスには、時間値をナノ秒単位で返すメンバー関数が用意されています。 標準C++ `chrono` ライブラリを使用して、他の時間単位に変換します。

## <a name="members"></a>メンバー

`Activity` クラスには、[イベント](event.md)基本クラスから継承されたメンバーと共に、次のメンバーが含まれています。

### <a name="constructor"></a>Constructor

[アクティビティ](#activity)

### <a name="functions"></a>関数

[Cpu タイマー刻み](#cpu-ticks)\
[Cpu 時間](#cpu-time)\
[期間](#duration)\
[ExclusiveCPUTicks](#exclusive-cpu-ticks)\
[ExclusiveCPUTime](#exclusive-cpu-time)\
[ExclusiveDuration](#exclusive-duration)\
[ExclusiveDurationTicks](#exclusive-duration-ticks)\
[ExclusiveWallClockTimeResponsibility](#exclusive-wall-clock-time-responsibility)\
[ExclusiveWallClockTimeResponsibilityTicks](#exclusive-wall-clock-time-responsibility-ticks)\
[Starttimestamp](#start-timestamp)\
[Stoptimestamp](#stop-timestamp)\
[WallClockTimeResponsibility](#wall-clock-time-responsibility)\
[WallClockTimeResponsibilityTicks](#wall-clock-time-responsibility-ticks)

## <a name="activity"></a>演習

```cpp
Activity(const RawEvent& event);
```

### <a name="parameters"></a>パラメーター

*event*\
任意のアクティビティイベント。

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

## <a name="duration"></a>全

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>戻り値

アクティビティの継続時間 (ナノ秒単位)。

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

このアクティビティの全体的なウォールクロック時間に対する影響を表すティック数。 ウォールクロックの時間の責任は、通常のティックとは異なります。 ウォールクロックの責任のタイマー刻みは、アクティビティ間の並列化を考慮します。 2つの並列アクティビティの期間は、50タイマー刻み、開始時刻と終了時刻が同じである場合があります。 この場合、両方の get に25ティックのウォールクロック時間が割り当てられます。

::: moniker-end
