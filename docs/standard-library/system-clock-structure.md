---
title: system_clock 構造体
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::system_clock
- chrono/std::chrono::system_clock::from_time_t
- chrono/std::chrono::system_clock::now
- chrono/std::chrono::system_clock::to_time_t
- chrono/std::chrono::system_clock::is_monotonic Constant
- chrono/std::chrono::system_clock::is_steady Constant
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
ms.openlocfilehash: 7a9fd83840883de5172df8b2e1e451984a95ea47
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450187"
---
# <a name="systemclock-structure"></a>system_clock 構造体

システムのリアルタイム クロックに基づく*クロックの型*を表します。

## <a name="syntax"></a>構文

```cpp
struct system_clock;
```

## <a name="remarks"></a>Remarks

*クロック型*は、UTC で現在時刻を取得するために使用されます。 型は [duration](../standard-library/duration-class.md) とクラス テンプレート [time_point](../standard-library/time-point-class.md) のインスタンス化を具体化し、時間を返す静的メンバー関数 `now()` を定義します。

`now()` への最初の呼び出しによって返される値が、`now()` への以降の呼び出しによって返される値以下である場合、クロックは常に*単調*になります。

*単調*で、クロックのティック間の時間が一定のクロックは*安定しています*。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|`system_clock::duration`|`duration<rep, period>` と同義。|
|`system_clock::period`|`duration` に含まれるインスタンス化のティック間隔を表すために使用される型と同義です。|
|`system_clock::rep`|`duration` に含まれるインスタンス化のクロック ティックの数を表すために使用される型と同義です。|
|`system_clock::time_point`|`time_point<Clock, duration>` と同義です。ここで、`Clock` はクロック型自体または同じエポックに基づいた別のクロック型と同義で、同じ入れ子になった `duration` 型を持っています。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[from_time_t](#from_time_t)|静的。 指定された時間に最も近い `time_point` を返します。|
|[今](#now)|静的。 現在の時間を返します。|
|[to_time_t](#to_time_t)|静的。 指定された `time_t` に最も近い `time_point` オブジェクトを返します。|

### <a name="public-constants"></a>パブリック定数

|名前|説明|
|----------|-----------------|
|[system_clock::is_monotonic 定数](#is_monotonic_constant)|クロック型が単調かどうかを指定します。|
|[system_clock::is_steady 定数](#is_steady_constant)|クロック型が一定かどうかを指定します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<chrono >

**名前空間:** std::chrono

## <a name="from_time_t"></a>  system_clock::from_time_t

*Tm*で表される時間に最も近い[time_point](../standard-library/time-point-class.md)を返す静的メソッド。

```cpp
static time_point from_time_t(time_t Tm) noexcept;
```

### <a name="parameters"></a>パラメーター

*メモリ*\
[time_t](../c-runtime-library/standard-types.md) オブジェクト

## <a name="is_monotonic_constant"></a>  system_clock::is_monotonic 定数

クロックの型が単調かどうかを指定する静的な値。

```cpp
static const bool is_monotonic = false;
```

### <a name="return-value"></a>戻り値

この実装では`system_clock::is_monotonic` 、は常に**false**を返します。

### <a name="remarks"></a>Remarks

`now()` への最初の呼び出しによって返される値が、`now()` への以降の呼び出しによって返される値以下である場合、クロックは常に*単調*になります。

## <a name="is_steady_constant"></a>  system_clock::is_steady 定数

クロックの型が*安定している*かどうかを指定する静的な値。

```cpp
static const bool is_steady = false;
```

### <a name="return-value"></a>戻り値

この実装では`system_clock::is_steady` 、は常に**false**を返します。

### <a name="remarks"></a>Remarks

[単調](#is_monotonic_constant)で、クロックのティック間の時間が一定のクロックは*安定しています*。

## <a name="now"></a>  system_clock::now

現在時刻を返す静的メソッドです。

```cpp
static time_point now() noexcept;
```

### <a name="return-value"></a>戻り値

現在時刻を表す [time_point](../standard-library/time-point-class.md) オブジェクト。

## <a name="to_time_t"></a>  system_clock::to_time_t

*時間*によって表される時間に最も近い[time_t](../c-runtime-library/standard-types.md)を返す静的メソッド。

```cpp
static time_t to_time_t(const time_point& Time) noexcept;
```

### <a name="parameters"></a>パラメーター

*ごと*\
[time_point](../standard-library/time-point-class.md) オブジェクト。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[steady_clock 構造体](../standard-library/steady-clock-struct.md)
