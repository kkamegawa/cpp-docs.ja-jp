---
title: steady_clock 構造体
ms.date: 05/22/2018
f1_keywords:
- chrono/std::chrono::steady_clock
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
ms.openlocfilehash: 19e9f5c4dcfc7306b989605894e9a0787e0920ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62412398"
---
# <a name="steady_clock-struct"></a>steady_clock 構造体

表す、*定常*クロック。

## <a name="syntax"></a>構文

```cpp
struct steady_clock;
```

## <a name="remarks"></a>Remarks

Windows で`steady_clock`ラップ、`QueryPerformanceCounter`関数。

`now` への最初の呼び出しによって返される値が、`now` への以降の呼び出しによって返される値以下である場合、クロックは常に*単調*になります。 *単調*で、クロックのティック間の時間が一定のクロックは*安定しています*。

`high_resolution_clock` typedef は、`steady_clock`します。

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|`steady_clock::duration`|シノニム`nanoseconds`で定義された\<chrono >。|
|`steady_clock::period`|シノニム`nano`で定義された\<ratio >。|
|`steady_clock::rep`|シノニム**long** **long**に含まれているインスタンス化のクロック ティック数を表すために使用される型`duration`します。|
|`steady_clock::time_point`|`chrono::time_point<steady_clock>` と同義。|

## <a name="public-functions"></a>パブリック関数

|関数|説明|
|--------------|-----------------|
|`now`|として現在の時刻を返します、`time_point`値。|

## <a name="public-constants"></a>パブリック定数

|名前|説明|
|----------|-----------------|
|`steady_clock::is_steady`|保持している**true**します。 `steady_clock` は*安定*しています。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<chrono >

**名前空間:** std::chrono

## <a name="see-also"></a>関連項目

- [ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
- [\<chrono>](../standard-library/chrono.md)
- [system_clock 構造体](../standard-library/system-clock-structure.md)
