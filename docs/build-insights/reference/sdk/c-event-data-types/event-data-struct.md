---
title: EVENT_DATA 構造体
description: C++ BUILD Insights SDK EVENT_DATA 構造体リファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- EVENT_DATA
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 572cbdaba346ddb77b665b5677b978c83a80aa3d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78857094"
---
# <a name="event_data-structure"></a>EVENT_DATA 構造体

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`EVENT_DATA` 構造は、分析または再ログセッションから受信したイベントを表します。 これらのセッションは、 [analyze](../functions/analyze.md)、 [analyze ea](../functions/analyze-a.md)、 [analyze](../functions/analyze-w.md)、 [Relog](../functions/relog.md)、 [reloga](../functions/relog-a.md)、または[reloga](../functions/relog-w.md)関数を呼び出すことによって開始されます。

## <a name="syntax"></a>構文

```cpp
typedef struct EVENT_DATA_TAG
{
    unsigned short          EventId;
    unsigned long long      EventInstanceId;

    long long               TickFrequency;
    long long               StartTimestamp;
    long long               StopTimestamp;
    long long               ExclusiveDurationTicks;
    long long               CPUTicks;
    long long               ExclusiveCPUTicks;
    long long               WallClockTimeResponsibilityTicks;
    long long               ExclusiveWallClockTimeResponsibilityTicks;

    const void*             Data;

    unsigned long           ProcessId;
    unsigned long           ThreadId;
    unsigned short          ProcessorIndex;

    const char*             EventName;
    const wchar_t*          EventWideName;

} EVENT_DATA;
```

## <a name="members"></a>メンバー

|  |  |
|--|--|
| `EventId` | イベントを識別する番号。 イベント識別子の一覧については、「 [EVENT_ID](event-id-enum.md)」を参照してください。 |
| `EventInstanceId` | トレース内の現在のイベントを一意に識別する数値。 同じトレースを複数回分析または再ログ記録する場合、この値は変わりません。 このフィールドを使用すると、複数の分析で同じイベントを識別したり、同じトレースに対してログを再ログに記録したりすることができます。 |
| `TickFrequency` | ティック単位で計測された期間を評価するときに使用する1秒あたりのタイマー刻みの数。 |
| `StartTimestamp` | イベントが*アクティビティ*の場合、このフィールドは、アクティビティの開始時にキャプチャされたティック値に設定されます。 このイベントが*単純なイベント*の場合、このフィールドは、イベントが発生したときにキャプチャされるティック値に設定されます。 |
| `StopTimestamp` | イベントが*アクティビティ*の場合、このフィールドは、アクティビティが停止したときにキャプチャされるティック値に設定されます。 停止イベントがこのアクティビティに対してまだ受信されていない場合、このフィールドは0に設定されます。 このイベントが*単純なイベント*の場合、このフィールドは0に設定されます。 |
| `ExclusiveDurationTicks` | このイベントが*アクティビティ*の場合、このフィールドは、このアクティビティで直接発生したタイマー刻みの数に設定されます。 子アクティビティで発生したタイマー刻みの数は除外されます。 *単純なイベント*の場合、このフィールドは0に設定されます。 |
| `CPUTicks` | このイベントが*アクティビティ*の場合、このフィールドは、このアクティビティの実行中に発生した CPU タイマー刻みの数に設定されます。 CPU の目盛りは、通常のティックとは異なります。 CPU タイマー刻みは、CPU がアクティビティ内のコードを実行している場合にのみカウントされます。 CPU タイマー刻みは、アクティビティに関連付けられているスレッドがスリープ状態のときにはカウントされません。 *単純なイベント*の場合、このフィールドは0に設定されます。 |
| `ExclusiveCPUTicks` | このフィールドは `CPUTicks`と同じ意味を持ちますが、子アクティビティで発生した CPU ティックは含まれていません。 *単純なイベント*の場合、このフィールドは0に設定されます。 |
| `WallClockTimeResponsibilityTicks` | このイベントが*アクティビティ*の場合、このフィールドは、このアクティビティの全体的なウォールクロック時間に対する影響を表すティック数に設定されます。 ウォールクロックの時間の責任は、通常のティックとは異なります。 ウォールクロックの責任のタイマー刻みは、アクティビティ間の並列化を考慮します。 たとえば、2つの並列アクティビティは、期間が50で、開始時刻と終了時刻が同じである場合があります。 この場合、両方に25ティックのウォールクロック時間の責任が割り当てられます。 *単純なイベント*の場合、このフィールドは0に設定されます。 |
| `ExclusiveWallClockTimeResponsibilityTicks` | このフィールドは、`WallClockTimeResponsibilityTicks`と同じ意味になります。ただし、子アクティビティのウォールクロックの時間単位のタイマー刻みは含まれません。 *単純なイベント*の場合、このフィールドは0に設定されます。 |
| `Data` | イベントに格納されている追加データを指します。 ポイントされているデータの型は、`EventId` フィールドによって異なります。 |
| `ProcessId` | イベントが発生したプロセスの識別子。 |
| `ThreadId` | イベントが発生したスレッドの識別子。 |
| `ProcessorIndex` | イベントが発生した CPU のインデックス番号 (0 から始まる)。 |
| `EventName` | `EventId`によって識別されるエンティティの名前を格納している ANSI 文字列。 |
| `EventWideName` | `EventId`によって識別されるエンティティの名前を格納しているワイド文字列。 |

## <a name="remarks"></a>解説

`EVENT_DATA` の多くのフィールドには、ティックカウントが含まれています。 C++Build Insights では、タイマー刻みのソースとして Window のパフォーマンスカウンターを使用します。 ティック数を `TickFrequency` フィールドと共に使用して、秒などの適切な時間単位に変換する必要があります。 この変換を実行するには、次の例を参照してください。 `EVENT_DATA` には、アクティビティの定期的なティックカウントのフィールドが含まれていません。 この値を取得するには、`StopTimestamp`から `StartTimestamp` を減算します。 `EVENT_DATA` は、C API ユーザーが使用することを意図した構造です。 API C++ユーザーについては、[イベント](../cpp-event-data-types/event.md)などのクラスによって自動的に変換されます。

[`EVENT_DATA` `Data`] フィールドの値は、`EventId` フィールドの値によって決まります。 `Data` の値については、次の表で説明します。 次の表に、いくつかのエンティティ識別子が不足している可能性があります。 この場合、`Data` フィールドは `nullptr` または0に設定されます。

| `EventId` 値 | `Data` が指す型 |
|--|--|
| `EVENT_ID_BACK_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_COMMAND_LINE` | `const wchar_t` |
| `EVENT_ID_COMPILER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_ENVIRONMENT_VARIABLE` | [NAME_VALUE_PAIR_DATA](name-value-pair-data-struct.md) |
| `EVENT_ID_EXECUTABLE_IMAGE_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_EXP_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FILE_INPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_FORCE_INLINE` | [FUNCTION_FORCE_INLINEE_DATA](function-force-inlinee-data-struct.md) |
| `EVENT_ID_FRONT_END_FILE` | [FRONT_END_FILE_DATA](front-end-file-data-struct.md) |
| `EVENT_ID_FRONT_END_PASS` | [CL_PASS_DATA](cl-pass-data-struct.md) |
| `EVENT_ID_FUNCTION` | [FUNCTION_DATA](function-data-struct.md) |
| `EVENT_ID_IMP_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LIB_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_LINKER` | [INVOCATION_DATA](invocation-data-struct.md) |
| `EVENT_ID_OBJ_OUTPUT` | [FILE_DATA](file-data-struct.md) |
| `EVENT_ID_SYMBOL_NAME` | [SYMBOL_NAME_DATA](symbol-name-data-struct.md) |
| `EVENT_ID_TEMPLATE_INSTANTIATION` | [TEMPLATE_INSTANTIATION_DATA](template-instantiation-data-struct.md) |

## <a name="tick-conversion-example"></a>ティック変換の例

```cpp
//
// We have the elapsed number of ticks, along with the
// number of ticks per second. We use these values
// to convert to the number of elapsed microseconds.
// To guard against loss-of-precision, we convert
// to microseconds *before* dividing by ticks-per-second.
//

long long ConvertDurationToMicroseconds(const sruct EVENT_DATA& eventData)
{
    long long duration = eventData.StopTimestamp - eventData.StartTimestamp;
    long long duration *= 1000000;
    return duration / eventData.TickFrequency;
}
```

::: moniker-end
