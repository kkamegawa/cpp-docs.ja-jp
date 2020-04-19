---
title: Concurrency::fast_math 名前空間
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::fast_math
ms.assetid: 54fed939-9902-49db-9f29-e98fd9821508
ms.openlocfilehash: 57e2134a2254dc4bc34d515e65e2ec629efeff33
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139505"
---
# <a name="concurrencyfast_math-namespace"></a>Concurrency::fast_math 名前空間

`fast_math` 名前空間の関数は精度が低く、単精度 (`float`) のみをサポートし、DirectX の組み込み関数を呼び出します。 各関数には、2 種類のバージョン (たとえば、`cos` と `cosf`) があります。 どちらのバージョンも `float` を受け取り、返しますが、それぞれの DirectX の同じ組み込み関数を呼び出します。

## <a name="syntax"></a>構文

```cpp
namespace fast_math;
```

## <a name="members"></a>メンバー

### <a name="functions"></a>関数

|Name|説明|
|----------|-----------------|
|[cos](concurrency-fast-math-namespace-functions.md#cos)|引数の逆余弦を計算します。|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|引数の逆余弦を計算します。|
|[asin](concurrency-fast-math-namespace-functions.md#asin)|引数の逆正弦を計算します。|
|[asinf](concurrency-fast-math-namespace-functions.md#asinf)|引数の逆正弦を計算します。|
|[atan](concurrency-fast-math-namespace-functions.md#atan)|引数の逆正接を計算します。|
|[atan2](concurrency-fast-math-namespace-functions.md#atan2)|_Y/_X の逆正接を計算します。|
|[atan2f](concurrency-fast-math-namespace-functions.md#atan2f)|_Y/_X の逆正接を計算します。|
|[atanf](concurrency-fast-math-namespace-functions.md#atanf)|引数の逆正接を計算します。|
|[ceil](concurrency-fast-math-namespace-functions.md#ceil)|引数の切り上げを計算します。|
|[ceilf](concurrency-fast-math-namespace-functions.md#ceilf)|引数の切り上げを計算します。|
|[cos](concurrency-fast-math-namespace-functions.md#cos)|引数の余弦を計算します。|
|[cosf](concurrency-fast-math-namespace-functions.md#cosf)|引数の余弦を計算します。|
|[cosh](concurrency-fast-math-namespace-functions.md#cosh)|引数の双曲線余弦の値を計算します。|
|[coshf](concurrency-fast-math-namespace-functions.md#coshf)|引数の双曲線余弦の値を計算します。|
|[exp](concurrency-fast-math-namespace-functions.md#exp)|e を底とする引数のべき乗を計算します。|
|[exp2](concurrency-fast-math-namespace-functions.md#exp2)|2 を底とする引数のべき乗を計算します。|
|[exp2f](concurrency-fast-math-namespace-functions.md#exp2f)|2 を底とする引数のべき乗を計算します。|
|[expf](concurrency-fast-math-namespace-functions.md#expf)|e を底とする引数のべき乗を計算します。|
|[fabs](concurrency-fast-math-namespace-functions.md#fabs)|引数の絶対値を返します。|
|[fabsf](concurrency-fast-math-namespace-functions.md#fabsf)|引数の絶対値を返します。|
|[floor](concurrency-fast-math-namespace-functions.md#floor)|引数の切り捨てを計算します。|
|[floorf](concurrency-fast-math-namespace-functions.md#floorf)|引数の切り捨てを計算します。|
|[fmax](concurrency-fast-math-namespace-functions.md#fmax)|引数の最大数値を判断します。|
|[fmaxf](concurrency-fast-math-namespace-functions.md#fmaxf)|引数の最大数値を判断します。|
|[fmin](concurrency-fast-math-namespace-functions.md#fmin)|引数の最小数値を判断します。|
|[fminf](concurrency-fast-math-namespace-functions.md#fminf)|引数の最小数値を判断します。|
|[fmod](concurrency-fast-math-namespace-functions.md#fmod)|_X/_Y の浮動小数点の剰余を計算します。|
|[fmodf](concurrency-fast-math-namespace-functions.md#fmodf)|_X/_Y の浮動小数点の剰余を計算します。|
|[frexp](concurrency-fast-math-namespace-functions.md#frexp)|_X の仮数と指数を取得します。|
|[frexpf](concurrency-fast-math-namespace-functions.md#frexpf)|_X の仮数と指数を取得します。|
|[isfinite](concurrency-fast-math-namespace-functions.md#isfinite)|引数に有限値が存在するかどうかを判断します。|
|[isinf](concurrency-fast-math-namespace-functions.md#isinf)|引数が無限値であるかどうかを判断します。|
|[isnan](concurrency-fast-math-namespace-functions.md#isnan)|引数が NaN であるかどうかを判断します。|
|[ldexp](concurrency-fast-math-namespace-functions.md#ldexp)|仮数と指数から実数を計算します。|
|[ldexpf](concurrency-fast-math-namespace-functions.md#ldexpf)|仮数と指数から実数を計算します。|
|[log](concurrency-fast-math-namespace-functions.md#log)|e を底とする引数の対数を計算します。|
|[log10](concurrency-fast-math-namespace-functions.md#log10)|10 を底とする引数の対数を計算します。|
|[log10f](concurrency-fast-math-namespace-functions.md#log10f)|10 を底とする引数の対数を計算します。|
|[log2](concurrency-fast-math-namespace-functions.md#log2)|2 を底とする引数の対数を計算します。|
|[log2f](concurrency-fast-math-namespace-functions.md#log2f)|2 を底とする引数の対数を計算します。|
|[logf](concurrency-fast-math-namespace-functions.md#logf)|e を底とする引数の対数を計算します。|
|[modf](concurrency-fast-math-namespace-functions.md#modf)|_X を小数部と整数部に分割します。|
|[modff](concurrency-fast-math-namespace-functions.md#modff)|_X を小数部と整数部に分割します。|
|[pow](concurrency-fast-math-namespace-functions.md#pow)|_X の _Y 乗を計算します。|
|[powf](concurrency-fast-math-namespace-functions.md#powf)|_X の _Y 乗を計算します。|
|[round](concurrency-fast-math-namespace-functions.md#round)|_X を最も近い整数値に丸めます。|
|[roundf](concurrency-fast-math-namespace-functions.md#roundf)|_X を最も近い整数値に丸めます。|
|[rsqrt](concurrency-fast-math-namespace-functions.md#rsqrt)|引数の平方根の逆数を返します。|
|[rsqrtf](concurrency-fast-math-namespace-functions.md#rsqrtf)|引数の平方根の逆数を返します。|
|[signbit](concurrency-fast-math-namespace-functions.md#signbit)|引数の正弦を返します。|
|[signbitf](concurrency-fast-math-namespace-functions.md#signbitf)|引数の正弦を返します。|
|[sin](concurrency-fast-math-namespace-functions.md#sin)|引数の正弦値を計算します。|
|[sincos](concurrency-fast-math-namespace-functions.md#sincos)|_X の正弦と余弦の値を計算します|
|[sincosf](concurrency-fast-math-namespace-functions.md#sincosf)|_X の正弦と余弦の値を計算します|
|[sinf](concurrency-fast-math-namespace-functions.md#sinf)|引数の正弦値を計算します。|
|[sinh](concurrency-fast-math-namespace-functions.md#sinh)|引数の双曲線正弦の値を計算します。|
|[sinhf](concurrency-fast-math-namespace-functions.md#sinhf)|引数の双曲線正弦の値を計算します。|
|[sqrt](concurrency-fast-math-namespace-functions.md#sqrt)|引数の平方根を計算します。|
|[sqrtf](concurrency-fast-math-namespace-functions.md#sqrtf)|引数の平方根を計算します。|
|[tan](concurrency-fast-math-namespace-functions.md#tan)|引数の正接値を計算します。|
|[tanf](concurrency-fast-math-namespace-functions.md#tanf)|引数の正接値を計算します。|
|[tanh](concurrency-fast-math-namespace-functions.md#tanh)|引数の双曲線正接の値を計算します。|
|[tanhf](concurrency-fast-math-namespace-functions.md#tanhf)|引数の双曲線正接の値を計算します。|
|[trunc](concurrency-fast-math-namespace-functions.md#trunc)|引数を整数コンポーネントに切り捨てます。|
|[truncf](concurrency-fast-math-namespace-functions.md#truncf)|引数を整数コンポーネントに切り捨てます。|

## <a name="requirements"></a>要件

**ヘッダー:** amp_math

**名前空間:** Concurrency:: fast_math

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
