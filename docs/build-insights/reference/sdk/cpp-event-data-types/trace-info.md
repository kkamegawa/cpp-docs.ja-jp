---
title: TraceInfo クラス
description: C++ビルドインサイト SDK traceinfo クラスリファレンス。
ms.date: 02/12/2020
helpviewer_keywords:
- C++ Build Insights
- C++ Build Insights SDK
- TraceInfo
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 5cf32c8dc954a803a11888231d35b1050ac81cc3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2020
ms.locfileid: "78334500"
---
# <a name="traceinfo-class"></a>TraceInfo クラス

::: moniker range="<=vs-2015"

Build C++ Insights SDK は、Visual Studio 2017 以降と互換性があります。 これらのバージョンのドキュメントを表示するには、この記事の Visual Studio バージョンセレクターコントロールを Visual Studio 2017 または Visual Studio 2019 に設定します。

::: moniker-end
::: moniker range=">=vs-2017"

`TraceInfo` クラスは、分析または再ログされるトレースに関する有用なプロパティにアクセスするために使用されます。

## <a name="syntax"></a>構文

```cpp
class TraceInfo
{
public:
    TraceInfo(const TRACE_INFO_DATA& data);

    const unsigned long& LogicalProcessorCount() const;

    const long long& TickFrequency() const;
    const long long& StartTimestamp() const;
    const long long& StopTimestamp() const;

    std::chrono::nanoseconds Duration() const;
};
```

## <a name="remarks"></a>解説

`StopTimestamp` から `StartTimestamp` を減算して、トレース全体で経過したタイマー刻みの数を取得します。 結果の値を時間単位に変換するには、`TickFrequency` を使用します。 タイマー刻みを time に変換する例については、「 [EVENT_DATA](../c-event-data-types/event-data-struct.md)」を参照してください。

タイマー刻みを自分で変換しない場合、`TraceInfo` クラスには、トレース時間をナノ秒単位で返すメンバー関数が用意されています。 標準C++ `chrono` ライブラリを使用して、この値を他の時間単位に変換します。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

[TraceInfo](#trace-info)

### <a name="functions"></a>関数

[期間](#duration)
[logicalprocessorcount](#logical-processor-count)
[starttimestamp](#start-timestamp)
[stoptimestamp](#stop-timestamp)
[TickFrequency](#tick-frequency)

## <a name="duration"></a>全

```cpp
std::chrono::nanoseconds Duration() const;
```

### <a name="return-value"></a>戻り値

アクティビティの継続時間 (ナノ秒単位)。

## <a name="logical-processor-count"></a>LogicalProcessorCount

```cpp
const unsigned long& LogicalProcessorCount() const;
```

### <a name="return-value"></a>戻り値

トレースが収集されたコンピューター上の論理プロセッサの数。

## <a name="start-timestamp"></a>StartTimestamp

```cpp
const long long& StartTimestamp() const;
```

### <a name="return-value"></a>戻り値

トレースが開始されたときにキャプチャされるティック値。

## <a name="stop-timestamp"></a>StopTimestamp

```cpp
const long long& StopTimestamp() const;
```

### <a name="return-value"></a>戻り値

トレースが停止したときにキャプチャされたティック値。

## <a name="tick-frequency"></a>TickFrequency

```cpp
const long long& TickFrequency() const;
```

### <a name="return-value"></a>戻り値

ティック単位で計測された期間を評価するときに使用する1秒あたりのタイマー刻みの数。

## <a name="trace-info"></a>TraceInfo

```cpp
TraceInfo(const TRACE_INFO_DATA& data);
```

### <a name="parameters"></a>パラメーター

*データ*\
トレースに関する情報を格納しているデータ。

::: moniker-end
