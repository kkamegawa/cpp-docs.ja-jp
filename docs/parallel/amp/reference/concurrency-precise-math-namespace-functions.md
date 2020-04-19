---
title: Concurrency::precise_math 名前空間関数
ms.date: 11/04/2016
f1_keywords:
- amp_math/Concurrency::precise_math::acos
- amp_math/Concurrency::precise_math::acosh
- amp_math/Concurrency::precise_math::acoshf
- amp_math/Concurrency::precise_math::asinf
- amp_math/Concurrency::precise_math::asinh
- amp_math/Concurrency::precise_math::atan
- amp_math/Concurrency::precise_math::atan2
- amp_math/Concurrency::precise_math::atanf
- amp_math/Concurrency::precise_math::atanh
- amp_math/Concurrency::precise_math::cbrt
- amp_math/Concurrency::precise_math::cbrtf
- amp_math/Concurrency::precise_math::ceilf
- amp_math/Concurrency::precise_math::copysign
- amp_math/Concurrency::precise_math::cos
- amp_math/Concurrency::precise_math::cosf
- amp_math/Concurrency::precise_math::coshf
- amp_math/Concurrency::precise_math::cospi
- amp_math/Concurrency::precise_math::erf
- amp_math/Concurrency::precise_math::erfc
- amp_math/Concurrency::precise_math::erfcinv
- amp_math/Concurrency::precise_math::erfcinvf
- amp_math/Concurrency::precise_math::erfinv
- amp_math/Concurrency::precise_math::erfinvf
- amp_math/Concurrency::precise_math::exp10
- amp_math/Concurrency::precise_math::exp10f
- amp_math/Concurrency::precise_math::exp2f
- amp_math/Concurrency::precise_math::expf
- amp_math/Concurrency::precise_math::expm1f
- amp_math/Concurrency::precise_math::fabs
- amp_math/Concurrency::precise_math::floor
- amp_math/Concurrency::precise_math::fdim
- amp_math/Concurrency::precise_math::floorf
- amp_math/Concurrency::precise_math::fmaf
- amp_math/Concurrency::precise_math::fmaxf
- amp_math/Concurrency::precise_math::fmin
- amp_math/Concurrency::precise_math::fmod
- amp_math/Concurrency::precise_math::fmodf
- amp_math/Concurrency::precise_math::frexp
- amp_math/Concurrency::precise_math::frexpf
- amp_math/Concurrency::precise_math::hypotf
- amp_math/Concurrency::precise_math::ilogb
- amp_math/Concurrency::precise_math::isfinite
- amp_math/Concurrency::precise_math::isinf
- amp_math/Concurrency::precise_math::isnormal
- amp_math/Concurrency::precise_math::ldexp
- amp_math/Concurrency::precise_math::lgamma
- amp_math/Concurrency::precise_math::lgammaf
- amp_math/Concurrency::precise_math::log10
- amp_math/Concurrency::precise_math::log10f
- amp_math/Concurrency::precise_math::log1pf
- amp_math/Concurrency::precise_math::log2
- amp_math/Concurrency::precise_math::logb
- amp_math/Concurrency::precise_math::logbf
- amp_math/Concurrency::precise_math::modf
- amp_math/Concurrency::precise_math::modff
- amp_math/Concurrency::precise_math::nanf
- amp_math/Concurrency::precise_math::nearbyint
- amp_math/Concurrency::precise_math::nextafter
- amp_math/Concurrency::precise_math::nextafterf
- amp_math/Concurrency::precise_math::phif
- amp_math/Concurrency::precise_math::pow
- amp_math/Concurrency::precise_math::probit
- amp_math/Concurrency::precise_math::probitf
- amp_math/Concurrency::precise_math::rcbrtf
- amp_math/Concurrency::precise_math::remainder
- amp_math/Concurrency::precise_math::remquo
- amp_math/Concurrency::precise_math::remquof
- amp_math/Concurrency::precise_math::roundf
- amp_math/Concurrency::precise_math::rsqrt
- amp_math/Concurrency::precise_math::scalb
- amp_math/Concurrency::precise_math::scalbf
- amp_math/Concurrency::precise_math::scalbnf
- amp_math/Concurrency::precise_math::signbit
- amp_math/Concurrency::precise_math::sin
- amp_math/Concurrency::precise_math::sincos
- amp_math/Concurrency::precise_math::sinf
- amp_math/Concurrency::precise_math::sinh
- amp_math/Concurrency::precise_math::sinpi
- amp_math/Concurrency::precise_math::sinpif
- amp_math/Concurrency::precise_math::sqrtf
- amp_math/Concurrency::precise_math::tan
- amp_math/Concurrency::precise_math::tanh
- amp_math/Concurrency::precise_math::tanhf
- amp_math/Concurrency::precise_math::tanpif
- amp_math/Concurrency::precise_math::tgamma
- amp_math/Concurrency::precise_math::trunc
- amp_math/Concurrency::precise_math::truncf
ms.assetid: fae53ab4-d1c5-45bb-a6a0-a74258e9aea3
ms.openlocfilehash: 53ebaf8d9cc1bca53b1fe51464668d6df8e08424
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126948"
---
# <a name="concurrencyprecise_math-namespace-functions"></a>Concurrency::precise_math 名前空間関数

||||
|-|-|-|
|[acos](#acos)|[acosf](#acosf)|[acosh](#acosh)|
|[acoshf](#acoshf)|[asin](#asin)|[asinf](#asinf)|
|[asinh](#asinh)|[asinhf](#asinhf)|[atan](#atan)|
|[atan2](#atan2)|[atan2f](#atan2f)|[atanf](#atanf)|
|[atanh](#atanh)|[atanhf](#atanhf)|[cbrt](#cbrt)|
|[cbrtf](#cbrtf)|[ceil](#ceil)|[ceilf](#ceilf)|
|[copysign](#copysign)|[copysignf](#copysignf)|[cos](#cos)|
|[cosf](#cosf)|[cosh](#cosh)|[coshf](#coshf)|
|[cospi](#cospi)|[cospif](#cospif)|[erf](#erf)|
|[erfc](#erfc)|[erfcf](#erfcf)|[erfcinv](#erfcinv)|
|[erfcinvf](#erfcinvf)|[erff](#erff)|[erfinv](#erfinv)|
|[erfinvf](#erfinvf)|[exp](#exp)|[exp10](#exp10)|
|[exp10f](#exp10f)|[exp2](#exp2)|[exp2f](#exp2f)|
|[expf](#expf)|[expm1](#expm1)|[expm1f](#expm1f)|
|[fabs](#fabs)|[fabsf](#fabsf)|[floor](#floor)|
|[fdim](#fdim)|[fdimf](#fdimf)||
|[floorf](#floorf)|[fma](#fma)|[fmaf](#fmaf)|
[fmax](#fmax)|[fmaxf](#fmaxf)||
|[fmin](#fmin)|[fminf](#fminf)|[fmod](#fmod)|
|[fmodf](#fmodf)|[fpclassify](#fpclassify)|[frexp](#frexp)|
|[frexpf](#frexpf)|[hypot](#hypot)|[hypotf](#hypotf)|
|[ilogb](#ilogb)|[ilogbf](#ilogbf)|[isfinite](#isfinite)|
|[isinf](#isinf)|[isnan](#isnan)|[isnormal](#isnormal)|
|[ldexp](#ldexp)|[ldexpf](#ldexpf)|[lgamma](#lgamma)|
|[lgammaf](#lgammaf)|[log](#log)|[log10](#log10)|
|[log10f](#log10f)|[log1p](#log1p)|[log1pf](#log1pf)|
|[log2](#log2)|[log2f](#log2f)|[logb](#logb)|
|[logbf](#logbf)|[logf](#logf)|[modf](#modf)|
|[modff](#modff)|[nan](#nan)|[nanf](#nanf)|
|[nearbyint](#nearbyint)|[nearbyintf](#nearbyintf)|[nextafter](#nextafter)|
|[nextafterf](#nextafterf)|[phi](#phi)|[phif](#phif)|
|[pow](#pow)|[powf](#powf)|[probit](#probit)|
|[probitf](#probitf)|[rcbrt](#rcbrt)|[rcbrtf](#rcbrtf)|
|[remainder](#remainder)|[remainderf](#remainderf)|[remquo](#remquo)|
|[remquof](#remquof)|[round](#round)|[roundf](#roundf)|
|[rsqrt](#rsqrt)|[rsqrtf](#rsqrtf)|[scalb](#scalb)|
|[scalbf](#scalbf)|[scalbn](#scalbn)|[scalbnf](#scalbnf)|
|[signbit](#signbit)|[signbitf](#signbitf)|[sin](#sin)|
|[sincos](#sincos)|[sincosf](#sincosf)|[sinf](#sinf)|
|[sinh](#sinh)|[sinhf](#sinhf)|[sinpi](#sinpi)|
|[sinpif](#sinpif)|[sqrt](#sqrt)|[sqrtf](#sqrtf)|
|[tan](#tan)|[tanf](#tanf)|[tanh](#tanh)|
|[tanhf](#tanhf)|[tanpi](#tanpi)|[tanpif](#tanpif)|
|[tgamma](#tgamma)|[tgammaf](#tgammaf)|[trunc](#trunc)|
|[truncf](#truncf)|

## <a name="acos"></a>  acos

引数の逆余弦を計算します。

```cpp
inline float acos(float _X) restrict(amp);

inline double acos(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のアークコサイン値を返します。

## <a name="acosf"></a>acosf

引数の逆余弦を計算します。

```cpp
inline float acosf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のアークコサイン値を返します。

## <a name="acosh"></a>acosh

引数の逆双曲線余弦を計算します。

```cpp
inline float acosh(float _X) restrict(amp);

inline double acosh(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の逆双曲線余弦の値を返します。

## <a name="acoshf"></a>acoshf

引数の逆双曲線余弦を計算します。

```cpp
inline float acoshf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の逆双曲線余弦の値を返します。

## <a name="asin"></a>  asin

引数の逆正弦を計算します。

```cpp
inline float asin(float _X) restrict(amp);

inline double asin(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のアークサイン値を返します。

## <a name="asinf"></a>asinf

引数の逆正弦を計算します。

```cpp
inline float asinf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のアークサイン値を返します。

## <a name="asinh"></a>asinh

引数の逆双曲線正弦を計算します。

```cpp
inline float asinh(float _X) restrict(amp);

inline double asinh(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の逆双曲線正弦の値を返します。

## <a name="asinhf"></a>asinhf

引数の逆双曲線正弦を計算します。

```cpp
inline float asinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の逆双曲線正弦の値を返します。

## <a name="atan"></a>  atan

引数の逆正接を計算します。

```cpp
inline float atan(float _X) restrict(amp);

inline double atan(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のアークタンジェント値を返します。

## <a name="atan2"></a>  atan2

_Y/_X の逆正接を計算します。

```cpp
inline float atan2(
    float _Y,
    float _X) restrict(amp);

inline double atan2(
    double _Y,
    double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Y*<br/>
浮動小数点値

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_Y/_X のアークタンジェント値を返します。

## <a name="atan2f"></a>atan2f

_Y/_X の逆正接を計算します。

```cpp
inline float atan2f(
    float _Y,
    float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Y*<br/>
浮動小数点値

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_Y/_X のアークタンジェント値を返します。

## <a name="atanf"></a>atanf

引数の逆正接を計算します。

```cpp
inline float atanf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のアークタンジェント値を返します。

## <a name="atanh"></a>atanh

引数の逆双曲線正接を計算します。

```cpp
inline float atanh(float _X) restrict(amp);

inline double atanh(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の逆双曲線正接値を返します。

## <a name="atanhf"></a>atanhf

引数の逆双曲線正接を計算します。

```cpp
inline float atanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の逆双曲線正接値を返します。

## <a name="cbrt"></a>cbrt

引数の実際のキューブルートを計算します。

```cpp
inline float cbrt(float _X) restrict(amp);

inline double cbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の実際のキューブルートを返します。

## <a name="cbrtf"></a>cbrtf

引数の実際のキューブルートを計算します。

```cpp
inline float cbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の実際のキューブルートを返します。

## <a name="ceil"></a>ceil

引数の切り上げを計算します。

```cpp
inline float ceil(float _X) restrict(amp);

inline double ceil(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の切り上げ値を返します。

## <a name="ceilf"></a>ceilf

引数の切り上げを計算します。

```cpp
inline float ceilf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の切り上げ値を返します。

## <a name="copysign"></a>copysign

_X の大きさとの符号を使用して値を生成 _Y

```cpp
inline float copysign(
    float _X,
    float _Y) restrict(amp);

inline double copysign(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X の大きさとの符号を持つ値を返し _Y

## <a name="copysignf"></a>copysignf

_X の大きさとの符号を使用して値を生成 _Y

```cpp
inline float copysignf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X の大きさとの符号を持つ値を返し _Y

## <a name="cos"></a>  cos

引数の余弦を計算します。

```cpp
inline float cos(float _X) restrict(amp);

inline double cos(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のコサイン値を返します。

## <a name="cosf"></a>cosf

引数の余弦を計算します。

```cpp
inline float cosf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のコサイン値を返します。

## <a name="cosh"></a>  cosh

引数の双曲線余弦の値を計算します。

```cpp
inline float cosh(float _X) restrict(amp);

inline double cosh(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のハイパーボリックコサイン値を返します。

## <a name="coshf"></a>coshf

引数の双曲線余弦の値を計算します。

```cpp
inline float coshf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のハイパーボリックコサイン値を返します。

## <a name="cospi"></a>cospi

Pi \* のコサイン値を計算し _X

```cpp
inline float cospi(float _X) restrict(amp);

inline double cospi(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

Pi \* のコサイン値を返し _X

## <a name="cospif"></a>cospif

Pi \* のコサイン値を計算し _X

```cpp
inline float cospif(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

Pi \* のコサイン値を返し _X

## <a name="erf"></a>erf

_X のエラー関数を計算します。

```cpp
inline float erf(float _X) restrict(amp);

inline double erf(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

の error 関数を返し _X

## <a name="erfc"></a>erfc

_X の補完的エラー関数を計算します。

```cpp
inline float erfc(float _X) restrict(amp);

inline double erfc(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

の補完的なエラー関数を返し _X

## <a name="erfcf"></a>erfcf

_X の補完的エラー関数を計算します。

```cpp
inline float erfcf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

の補完的なエラー関数を返し _X

## <a name="erfcinv"></a>erfcinv

_X の逆補完的エラー関数を計算します。

```cpp
inline float erfcinv(float _X) restrict(amp);

inline double erfcinv(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

の逆補完的エラー関数を返し _X

## <a name="erfcinvf"></a>erfcinvf

_X の逆補完的エラー関数を計算します。

```cpp
inline float erfcinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

の逆補完的エラー関数を返し _X

## <a name="erff"></a>erff

_X のエラー関数を計算します。

```cpp
inline float erff(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

の error 関数を返し _X

## <a name="erfinv"></a>erfinv

_X の逆エラー関数を計算します。

```cpp
inline float erfinv(float _X) restrict(amp);

inline double erfinv(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

の逆エラー関数を返し _X

## <a name="erfinvf"></a>erfinvf

_X の逆エラー関数を計算します。

```cpp
inline float erfinvf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

の逆エラー関数を返し _X

## <a name="exp10"></a>exp10

10を底とする引数の指数を計算します。

```cpp
inline float exp10(float _X) restrict(amp);

inline double exp10(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

10を底とする引数の指数を返します。

## <a name="exp10f"></a>exp10f

10を底とする引数の指数を計算します。

```cpp
inline float exp10f(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

10を底とする引数の指数を返します。

## <a name="expm1"></a>expm1

e を底とする引数のべき乗マイナス 1 を計算します。

```cpp
inline float expm1(float exponent) restrict(amp);

inline double expm1(double exponent) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*累乗*<br/>
数値式の指数語*n* `e`<sup>n</sup>です。ここで `e` は自然対数の底です。

### <a name="return-value"></a>戻り値

e を底とする引数のべき乗マイナス 1 を返します。

## <a name="expm1f"></a>expm1f

e を底とする引数のべき乗マイナス 1 を計算します。

```cpp
inline float expm1f(float exponent) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*累乗*<br/>
数値式の指数語*n* `e`<sup>n</sup>です。ここで `e` は自然対数の底です。

### <a name="return-value"></a>戻り値

e を底とする引数のべき乗マイナス 1 を返します。

## <a name="exp"></a>  exp

e を底とする引数のべき乗を計算します。

```cpp
inline float exp(float _X) restrict(amp);

inline double exp(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

E を底とする引数の指数を返します。

## <a name="expf"></a>expf

e を底とする引数のべき乗を計算します。

```cpp
inline float expf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

E を底とする引数の指数を返します。

## <a name="exp2"></a>exp2

2 を底とする引数のべき乗を計算します。

```cpp
inline float exp2(float _X) restrict(amp);

inline double exp2(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

底 2 を引数で累乗した値を返します。

## <a name="exp2f"></a>exp2f

2 を底とする引数のべき乗を計算します。

```cpp
inline float exp2f(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

底 2 を引数で累乗した値を返します。

## <a name="fabs"></a>fabs

引数の絶対値を返します。

```cpp
inline float fabs(float _X) restrict(amp);

inline double fabs(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の絶対値を返します。

## <a name="fabsf"></a>fabsf

引数の絶対値を返します。

```cpp
inline float fabsf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の絶対値を返します。

## <a name="fdim"></a>fdim

引数間の正の値の差を計算します。

```cpp
inline float fdim(
   float _X,
   float _Y
) restrict(amp);
inline double fdim(
   double _X,
   double _Y
) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値の *_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X が _Y を超える場合の _X と _Y の違いそれ以外の場合は + 0 です。

## <a name="fdimf"></a>fdimf

引数間の正の値の差を計算します。

```cpp
inline float fdimf(
   float _X,
   float _Y
) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値の *_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X が _Y を超える場合の _X と _Y の違いそれ以外の場合は + 0 です。

## <a name="floor"></a>階数

引数の切り捨てを計算します。

```cpp
inline float floor(float _X) restrict(amp);

inline double floor(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の floor を返します。

## <a name="floorf"></a>floorf

引数の切り捨てを計算します。

```cpp
inline float floorf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の floor を返します。

## <a name="a-namefma-fma"></a>fma の <a name="fma">

1 番目と 2 番目に指定された引数の積を計算し、その結果に 3 番目に指定された引数を加えます。全体の計算は単一の操作として実行されます。

```cpp
inline float fma(
   float _X,
   float _Y,
   float _Z
) restrict(amp);

inline double fma(
   double _X,
   double _Y,
   double _Z
) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
最初の浮動小数点引数。
*_Y*<br/>
2 番目の浮動小数点引数。
*_Z*<br/>
3 番目の浮動小数点引数。

### <a name="return-value"></a>戻り値

式の結果 (_X \* _Y) + _Z。 全体の計算は単一の操作として実行されます。つまり、サブ式は無限の精度で計算され、最終結果だけが丸められます。

## <a name="fmaf"></a>fmaf

1 番目と 2 番目に指定された引数の積を計算し、その結果に 3 番目に指定された引数を加えます。全体の計算は単一の操作として実行されます。

```cpp
inline float fmaf(
   float _X,
   float _Y,
   float _Z
) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
最初の浮動小数点引数。
*_Y*<br/>
2 番目の浮動小数点引数。
*_Z*<br/>
3 番目の浮動小数点引数。

### <a name="return-value"></a>戻り値

式の結果 (_X \* _Y) + _Z。 全体の計算は単一の操作として実行されます。つまり、サブ式は無限の精度で計算され、最終結果だけが丸められます。

## <a name="fmax"></a>fmax

引数の最大数値を判断します。

```cpp
inline float fmax(
    float _X,
    float _Y) restrict(amp);

inline double fmax(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の最大数値を返します。

## <a name="fmaxf"></a>fmaxf

引数の最大数値を判断します。

```cpp
inline float fmaxf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の最大数値を返します。

## <a name="fmin"></a>fmin

引数の最小数値を判断します。

```cpp
inline float fmin(
    float _X,
    float _Y) restrict(amp);

inline double fmin(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の最小数値を返します。

## <a name="fminf"></a>fminf

引数の最小数値を判断します。

```cpp
inline float fminf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の最小数値を返します。

## <a name="fmod"></a>fmod 関数 (C++ AMP)

2 番目の指定された引数で除算した 1 番目の指定された引数の剰余を計算します。

```cpp
inline float fmod(
    float _X,
    float _Y) restrict(amp);

inline double fmod(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
最初の浮動小数点引数。

*_Y*<br/>
2 番目の浮動小数点引数。

### <a name="return-value"></a>戻り値

`_X` の残りの部分は `_Y`で除算されます。つまり、`_X`の値  - `_Y`*n*になります。ここで、 *n*は整数であり *、n は*`_X` - の大きさが `_Y`の大きさ未満であることを示します。`_Y`

## <a name="fmodf"></a>fmodf

2 番目の指定された引数で除算した 1 番目の指定された引数の剰余を計算します。

```cpp
inline float fmodf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
最初の浮動小数点引数。

*_Y*<br/>
2 番目の浮動小数点引数。

### <a name="return-value"></a>戻り値

`_X` の残りの部分は `_Y`で除算されます。つまり、`_X`の値  - `_Y`*n*になります。ここで、 *n*は整数であり *、n は*`_X` - の大きさが `_Y`の大きさ未満であることを示します。`_Y`

## <a name="fpclassify"></a>fpclassify

引数の値を NaN、無限、標準、subnormal、0として分類します。

```cpp
inline int fpclassify(float _X) restrict(amp);

inline int fpclassify(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の値に適切な数値分類マクロの値を返します。

## <a name="frexp"></a>frexp

_X の仮数と指数を取得します。

```cpp
inline float frexp(
    float _X,
    _Out_ int* _Exp) restrict(amp);

inline double frexp(
    double _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Exp*<br/>
浮動小数点値の _X の整数の指数を返します

### <a name="return-value"></a>戻り値

仮数を返し _X

## <a name="frexpf"></a>frexpf

_X の仮数と指数を取得します。

```cpp
inline float frexpf(
    float _X,
    _Out_ int* _Exp) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Exp*<br/>
浮動小数点値の _X の整数の指数を返します

### <a name="return-value"></a>戻り値

仮数を返し _X

## <a name="hypot"></a>hypot

_X との2乗の和の平方根を計算し _Y

```cpp
inline float hypot(
    float _X,
    float _Y) restrict(amp);

inline double hypot(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X との2乗の和の平方根を返し _Y

## <a name="hypotf"></a>hypotf

_X との2乗の和の平方根を計算し _Y

```cpp
inline float hypotf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X との2乗の和の平方根を返し _Y

## <a name="ilogb"></a>ilogb

_X の指数を符号付き整数値として抽出する

```cpp
inline int ilogb(float _X) restrict(amp);

inline int ilogb(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X の指数を符号付き整数値として返します。

## <a name="ilogbf"></a>ilogbf

_X の指数を符号付き整数値として抽出する

```cpp
inline int ilogbf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X の指数を符号付き整数値として返します。

## <a name="isfinite"></a>isfinite

引数に有限値が存在するかどうかを判断します。

```cpp
inline int isfinite(float _X) restrict(amp);

inline int isfinite(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

は、引数に有限の値がある場合にのみ、0以外の値を返します。

## <a name="isinf"></a>isinf

引数が無限値であるかどうかを判断します。

```cpp
inline int isinf(float _X) restrict(amp);

inline int isinf(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

は、引数に無限値がある場合にのみ、0以外の値を返します。

## <a name="isnan"></a>isnan

引数が NaN であるかどうかを判断します。

```cpp
inline int isnan(float _X) restrict(amp);

inline int isnan(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

は、引数に NaN 値がある場合にのみ、0以外の値を返します。

## <a name="isnormal"></a>isnormal

引数が正常であるかどうかを判断します

```cpp
inline int isnormal(float _X) restrict(amp);

inline int isnormal(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数に通常の値が指定されている場合にのみ、0以外の値を返します。

## <a name="ldexp"></a>ldexp

指定された仮数と指数から実数を計算します。

```cpp
inline float ldexp(
    float _X,
    int _Exp) restrict(amp);

inline double ldexp(
    double _X,
    double _Exp) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点の値、仮数

*_Exp*<br/>
整数値、指数

### <a name="return-value"></a>戻り値

2 ^ \* _X を返し _Exp

## <a name="ldexpf"></a>ldexpf

指定された仮数と指数から実数を計算します。

```cpp
inline float ldexpf(
    float _X,
    int _Exp) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点の値、仮数

*_Exp*<br/>
整数値、指数

### <a name="return-value"></a>戻り値

2 ^ \* _X を返し _Exp

## <a name="lgamma"></a>lgamma

引数のガンマの絶対値の自然対数を計算します。

```cpp
inline float lgamma(
    float _X,
    _Out_ int* _Sign) restrict(amp);

inline double lgamma(
    double _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Sign*<br/>
符号を返します

### <a name="return-value"></a>戻り値

引数のガンマの絶対値の自然対数を返します。

## <a name="lgammaf"></a>lgammaf

引数のガンマの絶対値の自然対数を計算します。

```cpp
inline float lgammaf(
    float _X,
    _Out_ int* _Sign) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Sign*<br/>
符号を返します

### <a name="return-value"></a>戻り値

引数のガンマの絶対値の自然対数を返します。

## <a name="log"></a>  log

e を底とする引数の対数を計算します。

```cpp
inline float log(float _X) restrict(amp);

inline double log(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

E を底とする引数の対数を返します。

## <a name="log10"></a>  log10

10 を底とする引数の対数を計算します。

```cpp
inline float log10(float _X) restrict(amp);

inline double log10(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

10を底とする引数の対数を返します。

## <a name="log10f"></a>log10f

10 を底とする引数の対数を計算します。

```cpp
inline float log10f(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

10を底とする引数の対数を返します。

## <a name="log1p"></a>log1p

1に引数を加算した底-e の対数を計算します。

```cpp
inline float log1p(float _X) restrict(amp);

inline double log1p(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

1を引数として底とする対数を返します。

## <a name="log1pf"></a>log1pf

1に引数を加算した底-e の対数を計算します。

```cpp
inline float log1pf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

1を引数として底とする対数を返します。

## <a name="log2"></a>log2

2 を底とする引数の対数を計算します。

```cpp
inline float log2(float _X) restrict(amp);

inline double log2(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

10を底とする引数の対数を返します。

## <a name="log2f"></a>log2f

2 を底とする引数の対数を計算します。

```cpp
inline float log2f(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

10を底とする引数の対数を返します。

## <a name="logb"></a>logb

_X の指数を、浮動小数点形式の符号付き整数値として抽出します。

```cpp
inline float logb(float _X) restrict(amp);

inline double logb(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

の符号付き指数を返し _X

## <a name="logbf"></a>logbf

_X の指数を、浮動小数点形式の符号付き整数値として抽出します。

```cpp
inline float logbf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

の符号付き指数を返し _X

## <a name="logf"></a>logf

e を底とする引数の対数を計算します。

```cpp
inline float logf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

E を底とする引数の対数を返します。

## <a name="modf"></a>modf

指定された引数を小数部と整数部に分割します。

```cpp
inline float modf(
    float _X,
    _Out_ float* _Iptr) restrict(amp);

inline double modf(
    double _X,
    _Out_ double* _Iptr) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Iptr*<br/>
入出力浮動小数点値として `_X`の整数部分。

### <a name="return-value"></a>戻り値

`_X` の符号付の小数部分。

## <a name="modff"></a>modff

指定された引数を小数部と整数部に分割します。

```cpp
inline float modff(
    float _X,
    _Out_ float* _Iptr) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Iptr*<br/>
浮動小数点値としての、`_X` の整数部分。

### <a name="return-value"></a>戻り値

`_X` の符号付き小数部を返します。

## <a name="nan"></a>nan

簡易な NaN を返します

```cpp
inline double nan(int _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
整数値

### <a name="return-value"></a>戻り値

使用可能な場合は、に示されている内容と共に、非表示の NaN を返し _X

## <a name="nanf"></a>nanf

簡易な NaN を返します

```cpp
inline float nanf(int _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
整数値

### <a name="return-value"></a>戻り値

使用可能な場合は、に示されている内容と共に、非表示の NaN を返し _X

## <a name="nearbyint"></a>nearbyint

現在の丸め方向を使用して、引数を浮動小数点形式の整数値に丸めます。

```cpp
inline float nearbyint(float _X) restrict(amp);

inline double nearbyint(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

丸められた整数値を返します。

## <a name="nearbyintf"></a>nearbyintf

現在の丸め方向を使用して、引数を浮動小数点形式の整数値に丸めます。

```cpp
inline float nearbyintf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

丸められた整数値を返します。

## <a name="nextafter"></a>nextafter

_Y 方向での _X の後、関数の型で次に表示できる値を確認します

```cpp
inline float nextafter(
    float _X,
    float _Y) restrict(amp);

inline double nextafter(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_Y 方向での _X の後で、関数の型で次に表示できる値を返します

## <a name="nextafterf"></a>nextafterf

_Y 方向での _X の後、関数の型で次に表示できる値を確認します

```cpp
inline float nextafterf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_Y 方向での _X の後で、関数の型で次に表示できる値を返します

## <a name="phi"></a>phi

引数の累積分布関数を返します。

```cpp
inline float phi(float _X) restrict(amp);

inline double phi(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の累積分布関数を返します。

## <a name="phif"></a>phif

引数の累積分布関数を返します。

```cpp
inline float phif(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の累積分布関数を返します。

## <a name="pow"></a>  pow

_X の _Y 乗を計算します。

```cpp
inline float pow(
    float _X,
    float _Y) restrict(amp);

inline double pow(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値、ベース

*_Y*<br/>
浮動小数点値、指数

### <a name="return-value"></a>戻り値

## <a name="powf"></a>powf

_X の _Y 乗を計算します。

```cpp
inline float powf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値、ベース

*_Y*<br/>
浮動小数点値、指数

### <a name="return-value"></a>戻り値

## <a name="probit"></a>probit

引数の逆累積分布関数を返します。

```cpp
inline float probit(float _X) restrict(amp);

inline double probit(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の逆累積分布関数を返します。

## <a name="probitf"></a>probitf

引数の逆累積分布関数を返します。

```cpp
inline float probitf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の逆累積分布関数を返します。

## <a name="rcbrt"></a>rcbrt

引数の cube ルートの逆数を返します。

```cpp
inline float rcbrt(float _X) restrict(amp);

inline double rcbrt(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の cube ルートの逆数を返します。

## <a name="rcbrtf"></a>rcbrtf

引数の cube ルートの逆数を返します。

```cpp
inline float rcbrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の cube ルートの逆数を返します。

## <a name="remainder"></a>後述

剰余を計算します: _X REM _Y

```cpp
inline float remainder(
    float _X,
    float _Y) restrict(amp);

inline double remainder(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

REM _X を返し _Y

## <a name="remainderf"></a>remainderf

剰余を計算します: _X REM _Y

```cpp
inline float remainderf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

REM _X を返し _Y

## <a name="remquo"></a>remquo

2 番目の指定された引数で除算した 1 番目の指定された引数の剰余を計算します。 また、1 番目に指定された引数の有効桁数を 2 番目に指定された引数の有効桁で割った商を計算し、3 番目の引数で指定された位置を使用して商を返します。

```cpp
inline float remquo(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);

inline double remquo(
    double _X,
    double _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
最初の浮動小数点引数。

*_Y*<br/>
2 番目の浮動小数点引数。

*_Quo*<br/>
入出力`_Y`の小数部で割った `_X` の小数部の商を返すために使用される整数のアドレス。

### <a name="return-value"></a>戻り値

`_X` を `_Y` で割った剰余を返します。

## <a name="remquof"></a>remquof

2 番目の指定された引数で除算した 1 番目の指定された引数の剰余を計算します。 また、1 番目に指定された引数の有効桁数を 2 番目に指定された引数の有効桁で割った商を計算し、3 番目の引数で指定された位置を使用して商を返します。

```cpp
inline float remquof(
    float _X,
    float _Y,
    _Out_ int* _Quo) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
最初の浮動小数点引数。

*_Y*<br/>
2 番目の浮動小数点引数。

*_Quo*<br/>
入出力`_Y`の小数部で割った `_X` の小数部の商を返すために使用される整数のアドレス。

### <a name="return-value"></a>戻り値

`_X` を `_Y` で割った剰余を返します。

## <a name="round"></a>誤差

_X を最も近い整数値に丸めます。

```cpp
inline float round(float _X) restrict(amp);

inline double round(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

最も近い整数を返し _X

## <a name="roundf"></a>roundf

_X を最も近い整数値に丸めます。

```cpp
inline float roundf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

最も近い整数を返し _X

## <a name="rsqrt"></a>rsqrt

引数の平方根の逆数を返します。

```cpp
inline float rsqrt(float _X) restrict(amp);

inline double rsqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の平方根の逆数を返します。

## <a name="rsqrtf"></a>rsqrtf

引数の平方根の逆数を返します。

```cpp
inline float rsqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の平方根の逆数を返します。

## <a name="scalb"></a>scalb

FLT_RADIX によって _X を指数 _Y に乗算します

```cpp
inline float scalb(
    float _X,
    float _Y) restrict(amp);

inline double scalb(
    double _X,
    double _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

\* _X を返します (FLT_RADIX ^ _Y)

## <a name="scalbf"></a>scalbf

FLT_RADIX によって _X を指数 _Y に乗算します

```cpp
inline float scalbf(
    float _X,
    float _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

\* _X を返します (FLT_RADIX ^ _Y)

## <a name="scalbn"></a>scalbn

FLT_RADIX によって _X を指数 _Y に乗算します

```cpp
inline float scalbn(
    float _X,
    int _Y) restrict(amp);

inline double scalbn(
    double _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
整数値

### <a name="return-value"></a>戻り値

\* _X を返します (FLT_RADIX ^ _Y)

## <a name="scalbnf"></a>scalbnf

FLT_RADIX によって _X を指数 _Y に乗算します

```cpp
inline float scalbnf(
    float _X,
    int _Y) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_Y*<br/>
整数値

### <a name="return-value"></a>戻り値

\* _X を返します (FLT_RADIX ^ _Y)

## <a name="signbit"></a>signbit

_X の符号が負であるかどうかを判断します。

```cpp
inline int signbit(float _X) restrict(amp);

inline int signbit(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X の符号が負の場合にのみ、0以外の値を返します。

## <a name="signbitf"></a>signbitf

_X の符号が負であるかどうかを判断します。

```cpp
inline int signbitf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X の符号が負の場合にのみ、0以外の値を返します。

## <a name="sin"></a>  sin

引数の正弦値を計算します。

```cpp
inline float sin(float _X) restrict(amp);

inline double sin(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のサイン値を返します。

## <a name="sinf"></a>sinf

引数の正弦値を計算します。

```cpp
inline float sinf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のサイン値を返します。

## <a name="sincos"></a>sincos

_X の正弦と余弦の値を計算します

```cpp
inline void sincos(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);

inline void sincos(
    double _X,
    _Out_ double* _S,
    _Out_ double* _C) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_S*<br/>
のサイン値を返し _X

*_C*<br/>
のコサイン値を返し _X

## <a name="sincosf"></a>sincosf

_X の正弦と余弦の値を計算します

```cpp
inline void sincosf(
    float _X,
    _Out_ float* _S,
    _Out_ float* _C) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

*_S*<br/>
のサイン値を返し _X

*_C*<br/>
のコサイン値を返し _X

## <a name="sinh"></a>  sinh

引数の双曲線正弦の値を計算します。

```cpp
inline float sinh(float _X) restrict(amp);

inline double sinh(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のハイパーボリックサイン値を返します。

## <a name="sinhf"></a>sinhf

引数の双曲線正弦の値を計算します。

```cpp
inline float sinhf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のハイパーボリックサイン値を返します。

## <a name="sinpi"></a>sinpi

Pi \* の正弦の値を計算し _X

```cpp
inline float sinpi(float _X) restrict(amp);

inline double sinpi(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

Pi \* のサイン値を返し _X

## <a name="sinpif"></a>sinpif

Pi \* の正弦の値を計算し _X

```cpp
inline float sinpif(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

Pi \* のサイン値を返し _X

## <a name="sqrt"></a>  sqrt

引数の squre ルートを計算します。

```cpp
inline float sqrt(float _X) restrict(amp);

inline double sqrt(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の squre 返します。

## <a name="sqrtf"></a>sqrtf

引数の squre ルートを計算します。

```cpp
inline float sqrtf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の squre 返します。

## <a name="tan"></a>  tan

引数の正接値を計算します。

```cpp
inline float tan(float _X) restrict(amp);

inline double tan(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のタンジェント値を返します。

## <a name="tanf"></a>tanf

引数の正接値を計算します。

```cpp
inline float tanf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のタンジェント値を返します。

## <a name="tanh"></a>  tanh

引数の双曲線正接の値を計算します。

```cpp
inline float tanh(float _X) restrict(amp);

inline double tanh(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のハイパーボリックタンジェント値を返します。

## <a name="tanhf"></a>tanhf

引数の双曲線正接の値を計算します。

```cpp
inline float tanhf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数のハイパーボリックタンジェント値を返します。

## <a name="tanpi"></a>tanpi

Pi \* のタンジェント値を計算し _X

```cpp
inline float tanpi(float _X) restrict(amp);

inline double tanpi(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

Pi \* のタンジェント値を返し _X

## <a name="tanpif"></a>tanpif

Pi \* のタンジェント値を計算し _X

```cpp
inline float tanpif(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

Pi \* のタンジェント値を返し _X

## <a name="tgamma"></a>tgamma

_X のガンマ関数を計算します。

```cpp
inline float tgamma(float _X) restrict(amp);

inline double tgamma(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X のガンマ関数の結果を返します。

## <a name="tgammaf"></a>tgammaf

_X のガンマ関数を計算します。

```cpp
inline float tgammaf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

_X のガンマ関数の結果を返します。

## <a name="trunc"></a>trunc

引数を整数コンポーネントに切り捨てます。

```cpp
inline float trunc(float _X) restrict(amp);

inline double trunc(double _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の整数部分を返します。

## <a name="truncf"></a>truncf

引数を整数コンポーネントに切り捨てます。

```cpp
inline float truncf(float _X) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_X*<br/>
浮動小数点値

### <a name="return-value"></a>戻り値

引数の整数部分を返します。

## <a name="see-also"></a>参照

[Concurrency::precise_math 名前空間](concurrency-precise-math-namespace.md)
