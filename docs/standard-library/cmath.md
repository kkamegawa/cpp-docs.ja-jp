---
title: '&lt;cmath&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cmath>
helpviewer_keywords:
- cmath header
ms.assetid: 80df1dba-60ca-4918-9c2e-fbf446eaa7d6
ms.openlocfilehash: d01b02d8fa169aa7fddbc3e51d75e5328b400d2b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459274"
---
# <a name="ltcmathgt"></a>&lt;cmath&gt;

標準 C ライブラリ ヘッダー \<math.h> をインクルードし、関連する名前を `std` 名前空間に追加します。

## <a name="syntax"></a>構文

```cpp
#include <cmath>
```

## <a name="constants-and-types"></a>定数と型

```cpp
namespace std {
    using float_t = see below ;
    using double_t = see below ;
}

#define HUGE_VAL see below
#define HUGE_VALF see below
#define HUGE_VALL see below
#define INFINITY see below
#define NAN see below
#define FP_INFINITE see below
#define FP_NAN see below
#define FP_NORMAL see below
#define FP_SUBNORMAL see below
#define FP_ZERO see below
#define FP_FAST_FMA see below
#define FP_FAST_FMAF see below
#define FP_FAST_FMAL see below
#define FP_ILOGB0 see below
#define FP_ILOGBNAN see below
#define MATH_ERRNO see below
#define MATH_ERREXCEPT see below
#define math_errhandling see below
```

## <a name="functions"></a>関数

```cpp
float acos(float x);
double acos(double x);
long double acos(long double x);
float acosf(float x);
long double acosl(long double x);
float asin(float x);
double asin(double x);
long double asin(long double x);
float asinf(float x);
long double asinl(long double x);
float atan(float x);
double atan(double x);
long double atan(long double x);
float atanf(float x);
long double atanl(long double x);
float atan2(float y, float x);
double atan2(double y, double x);
long double atan2(long double y, long double x);
float atan2f(float y, float x);
long double atan2l(long double y, long double x);
float cos(float x);
double cos(double x);
long double cos(long double x);
float cosf(float x);
long double cosl(long double x);
float sin(float x);
double sin(double x);
long double sin(long double x);
float sinf(float x);
long double sinl(long double x);
float tan(float x);
double tan(double x);
long double tan(long double x);
float tanf(float x);
long double tanl(long double x);
float acosh(float x);
double acosh(double x);
long double acosh(long double x);
float acoshf(float x);
long double acoshl(long double x);
float asinh(float x);
double asinh(double x);
long double asinh(long double x);
float asinhf(float x);
long double asinhl(long double x);
float atanh(float x);
double atanh(double x);
long double atanh(long double x);
float atanhf(float x);
long double atanhl(long double x);
float cosh(float x);
double cosh(double x);
long double cosh(long double x);
float coshf(float x);
long double coshl(long double x);
float sinh(float x);
double sinh(double x);
long double sinh(long double x);
float sinhf(float x);
long double sinhl(long double x);
float tanh(float x);
double tanh(double x);
long double tanh(long double x);
float tanhf(float x);
long double tanhl(long double x);
float exp(float x);
double exp(double x);
long double exp(long double x);
float expf(float x);
long double expl(long double x);
float exp2(float x);
double exp2(double x);
long double exp2(long double x);
float exp2f(float x);
long double exp2l(long double x);
float expm1(float x);
double expm1(double x);
long double expm1(long double x);
float expm1f(float x);
long double expm1l(long double x);
float frexp(float value, int* exp);
double frexp(double value, int* exp);
long double frexp(long double value, int* exp);
float frexpf(float value, int* exp);
long double frexpl(long double value, int* exp);
int ilogb(float x);
int ilogb(double x);
int ilogb(long double x);
int ilogbf(float x);
int ilogbl(long double x);
float ldexp(float x, int exp);
double ldexp(double x, int exp);
long double ldexp(long double x, int exp);
float ldexpf(float x, int exp);
long double ldexpl(long double x, int exp);
float log(float x);
double log(double x);
long double log(long double x);
float logf(float x);
long double logl(long double x);
float log10(float x);
double log10(double x);
long double log10(long double x);
float log10f(float x);
long double log10l(long double x);
float log1p(float x);
double log1p(double x);
long double log1p(long double x);
float log1pf(float x);
long double log1pl(long double x);
float log2(float x);
double log2(double x);
long double log2(long double x);
float log2f(float x);
long double log2l(long double x);
float logb(float x);
double logb(double x);
long double logb(long double x);
float logbf(float x);
long double logbl(long double x);
float modf(float value, float* iptr);
double modf(double value, double* iptr);
long double modf(long double value, long double* iptr);
float modff(float value, float* iptr);
long double modfl(long double value, long double* iptr);
float scalbn(float x, int n);
double scalbn(double x, int n);
long double scalbn(long double x, int n);
float scalbnf(float x, int n);
long double scalbnl(long double x, int n);
float scalbln(float x, long int n);
double scalbln(double x, long int n);
long double scalbln(long double x, long int n);
float scalblnf(float x, long int n);
long double scalblnl(long double x, long int n);
float cbrt(float x);
double cbrt(double x);
long double cbrt(long double x);
float cbrtf(float x);
long double cbrtl(long double x);
```

## <a name="absolute-values"></a>絶対値

```cpp
int abs(int j);
long int abs(long int j);
long long int abs(long long int j);
float abs(float j);
double abs(double j);
long double abs(long double j);
float fabs(float x);
double fabs(double x);
long double fabs(long double x);
float fabsf(float x);
long double fabsl(long double x);
float hypot(float x, float y);
double hypot(double x, double y);
long double hypot(double x, double y);
float hypotf(float x, float y);
long double hypotl(long double x, long double y);
```

## <a name="three-dimensional-hypotenuse"></a>3次元の斜辺

```cpp
float hypot(float x, float y, float z);
double hypot(double x, double y, double z);
long double hypot(long double x, long double y, long double z);
float pow(float x, float y);
double pow(double x, double y);
long double pow(long double x, long double y);
float powf(float x, float y);
long double powl(long double x, long double y);
float sqrt(float x);
double sqrt(double x);
long double sqrt(long double x);
float sqrtf(float x);
long double sqrtl(long double x);
float erf(float x);
double erf(double x);
long double erf(long double x);
float erff(float x);
long double erfl(long double x);
float erfc(float x);
double erfc(double x);
long double erfc(long double x);
float erfcf(float x);
long double erfcl(long double x);
float lgamma(float x);
double lgamma(double x);
long double lgamma(long double x);
float lgammaf(float x);
long double lgammal(long double x);
float tgamma(float x);
double tgamma(double x);
long double tgamma(long double x);
float tgammaf(float x);
long double tgammal(long double x);
float ceil(float x);
double ceil(double x);
long double ceil(long double x);
float ceilf(float x);
long double ceill(long double x);
float floor(float x);
double floor(double x);
long double floor(long double x);
float floorf(float x);
long double floorl(long double x);
float nearbyint(float x);
double nearbyint(double x);
long double nearbyint(long double x);
float nearbyintf(float x);
long double nearbyintl(long double x);
float rint(float x);
double rint(double x);
long double rint(long double x);
float rintf(float x);
long double rintl(long double x);
long int lrint(float x);
long int lrint(double x);
long int lrint(long double x);
long int lrintf(float x);
long int lrintl(long double x);
long long int llrint(float x);
long long int llrint(double x);
long long int llrint(long double x);
long long int llrintf(float x);
long long int llrintl(long double x);
float round(float x);
double round(double x);
long double round(long double x);
float roundf(float x);
long double roundl(long double x);
long int lround(float x);
long int lround(double x);
long int lround(long double x);
long int lroundf(float x);
long int lroundl(long double x);
long long int llround(float x);
long long int llround(double x);
long long int llround(long double x);
long long int llroundf(float x);
long long int llroundl(long double x);
float trunc(float x);
double trunc(double x);
long double trunc(long double x);
float truncf(float x);
long double truncl(long double x);
float fmod(float x, float y);
double fmod(double x, double y);
long double fmod(long double x, long double y);
float fmodf(float x, float y);
long double fmodl(long double x, long double y);
float remainder(float x, float y);
double remainder(double x, double y);
long double remainder(long double x, long double y);
float remainderf(float x, float y);
long double remainderl(long double x, long double y);
float remquo(float x, float y, int* quo);
double remquo(double x, double y, int* quo);
long double remquo(long double x, long double y, int* quo);
float remquof(float x, float y, int* quo);
long double remquol(long double x, long double y, int* quo);
float copysign(float x, float y);
double copysign(double x, double y);
long double copysign(long double x, long double y);
float copysignf(float x, float y);
long double copysignl(long double x, long double y);
double nan(const char* tagp);
float nanf(const char* tagp);
long double nanl(const char* tagp);
float nextafter(float x, float y);
double nextafter(double x, double y);
long double nextafter(long double x, long double y);
float nextafterf(float x, float y);
long double nextafterl(long double x, long double y);
float nexttoward(float x, long double y);
double nexttoward(double x, long double y);
long double nexttoward(long double x, long double y);
float nexttowardf(float x, long double y);
long double nexttowardl(long double x, long double y);
float fdim(float x, float y);
double fdim(double x, double y);
long double fdim(long double x, long double y);
float fdimf(float x, float y);
long double fdiml(long double x, long double y);
float fmax(float x, float y);
double fmax(double x, double y);
long double fmax(long double x, long double y);
float fmaxf(float x, float y);
long double fmaxl(long double x, long double y);
float fmin(float x, float y);
double fmin(double x, double y);
long double fmin(long double x, long double y);
float fminf(float x, float y);
long double fminl(long double x, long double y);
float fma(float x, float y, float z);
double fma(double x, double y, double z);
long double fma(long double x, long double y, long double z);
float fmaf(float x, float y, float z);
long double fmal(long double x, long double y, long double z);
```

## <a name="classification--comparison-functions"></a>分類/比較関数

```cpp
int fpclassify(float x);
int fpclassify(double x);
int fpclassify(long double x);
int isfinite(float x);
int isfinite(double x);
int isfinite(long double x);
int isinf(float x);
int isinf(double x);
int isinf(long double x);
int isnan(float x);
int isnan(double x);
int isnan(long double x);
int isnormal(float x);
int isnormal(double x);
int isnormal(long double x);
int signbit(float x);
int signbit(double x);
int signbit(long double x);
int isgreater(float x, float y);
int isgreater(double x, double y);
int isgreater(long double x, long double y);
int isgreaterequal(float x, float y);
int isgreaterequal(double x, double y);
int isgreaterequal(long double x, long double y);
int isless(float x, float y);
int isless(double x, double y);
int isless(long double x, long double y);
int islessequal(float x, float y);
int islessequal(double x, double y);
int islessequal(long double x, long double y);
int islessgreater(float x, float y);
int islessgreater(double x, double y);
int islessgreater(long double x, long double y);
int isunordered(float x, float y);
int isunordered(double x, double y);
int isunordered(long double x, long double y);
```

## <a name="mathematical-special-functions"></a>数学的特殊関数

### <a name="associated-laguerre-polynomials"></a>関連付けられている Laguerre polynomials

```cpp
double assoc_laguerre(unsigned n, unsigned m, double x);
float assoc_laguerref(unsigned n, unsigned m, float x);
long double assoc_laguerrel(unsigned n, unsigned m, long double x);
```

### <a name="associated-legendre-functions"></a>関連付けられている Legendre 関数

```cpp
double assoc_legendre(unsigned l, unsigned m, double x);
float assoc_legendref(unsigned l, unsigned m, float x);
long double assoc_legendrel(unsigned l, unsigned m, long double x);
```

### <a name="beta-function"></a>ベータ関数

```cpp
double beta(double x, double y);
float betaf(float x, float y);
long double betal(long double x, long double y);
```

### <a name="complete-elliptic-integral-of-the-first-kind"></a>最初の種類の楕円積分を完了します。

```cpp
double comp_ellint_1(double k);
float comp_ellint_1f(float k);
long double comp_ellint_1l(long double k);
```

### <a name="complete-elliptic-integral-of-the-second-kind"></a>2番目の種類の楕円積分を完了します。

```cpp
double comp_ellint_2(double k);
float comp_ellint_2f(float k);
long double comp_ellint_2l(long double k);
```

### <a name="complete-elliptic-integral-of-the-third-kind"></a>3番目の種類の楕円積分を完了します。

```cpp
double comp_ellint_3(double k, double nu);
float comp_ellint_3f(float k, float nu);
long double comp_ellint_3l(long double k, long double nu);
```

### <a name="regular-modified-cylindrical-bessel-functions"></a>通常変更された円柱ベッセル関数

```cpp
double cyl_bessel_i(double nu, double x);
float cyl_bessel_if(float nu, float x);
long double cyl_bessel_il(long double nu, long double x);
```

### <a name="cylindrical-bessel-functions-of-the-first-kind"></a>最初の種類の円筒型のベッセル関数

```cpp
double cyl_bessel_j(double nu, double x);
float cyl_bessel_jf(float nu, float x);
long double cyl_bessel_jl(long double nu, long double x);
```

### <a name="irregular-modified-cylindrical-bessel-functions"></a>不規則に変更された円柱ベッセル関数

```cpp
double cyl_bessel_k(double nu, double x);
float cyl_bessel_kf(float nu, float x);
long double cyl_bessel_kl(long double nu, long double x);
```

### <a name="cylindrical-neumann-functions"></a>円柱ノイマン関数

```cpp
double cyl_neumann(double nu, double x);
float cyl_neumannf(float nu, float x);
long double cyl_neumannl(long double nu, long double x);
```

### <a name="incomplete-elliptic-integral-of-the-first-kind"></a>最初の種類の不完全な楕円整数

```cpp
double ellint_1(double k, double phi);
float ellint_1f(float k, float phi);
long double ellint_1l(long double k, long double phi);
```

### <a name="incomplete-elliptic-integral-of-the-second-kind"></a>2番目の種類の不完全な楕円整数

```cpp
double ellint_2(double k, double phi);
float ellint_2f(float k, float phi);
long double ellint_2l(long double k, long double phi);
```

### <a name="incomplete-elliptic-integral-of-the-third-kind"></a>3番目の種類の不完全な楕円整数

```cpp
double ellint_3(double k, double nu, double phi);
float ellint_3f(float k, float nu, float phi);
long double ellint_3l(long double k, long double nu, long double phi);
```

### <a name="exponential-integral"></a>指数整数

```cpp
double expint(double x);
float expintf(float x);
long double expintl(long double x);
```

### <a name="hermite-polynomials"></a>Hermite polynomials

```cpp
double hermite(unsigned n, double x);
float hermitef(unsigned n, float x);
long double hermitel(unsigned n, long double x);
```

### <a name="laguerre-polynomials"></a>Laguerre polynomials

```cpp
double laguerre(unsigned n, double x);
float laguerref(unsigned n, float x);
long double laguerrel(unsigned n, long double x);
```

### <a name="legendre-polynomials"></a>Legendre polynomials

```cpp
double legendre(unsigned l, double x);
float legendref(unsigned l, float x);
long double legendrel(unsigned l, long double x);
```

### <a name="riemann-zeta-function"></a>リーマンゼータ関数

```cpp
double riemann_zeta(double x);
float riemann_zetaf(float x);
long double riemann_zetal(long double x);
```

### <a name="spherical-bessel-functions-of-the-first-kind"></a>最初の種類の球ベッセル関数

```cpp
double sph_bessel(unsigned n, double x);
float sph_besself(unsigned n, float x);
long double sph_bessell(unsigned n, long double x);
```

### <a name="spherical-associated-legendre-functions"></a>球面に関連付けられた Legendre 関数

```cpp
double sph_legendre(unsigned l, unsigned m, double theta);
float sph_legendref(unsigned l, unsigned m, float theta);
long double sph_legendrel(unsigned l, unsigned m, long double theta);
```

### <a name="spherical-neumann-functions"></a>球面ノイマン関数

```cpp
double sph_neumann(unsigned n, double x);
float sph_neumannf(unsigned n, float x);
long double sph_neumannl(unsigned n, long double x);
```

## <a name="remarks"></a>Remarks

このヘッダーをインクルードすると、標準 C ライブラリ ヘッダーの外部リンケージで宣言された名前が、`std` 名前空間でも宣言されます。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリの概要](../standard-library/cpp-standard-library-overview.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
