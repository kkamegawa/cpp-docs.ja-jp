---
title: 浮動小数点プリミティブ
ms.date: 01/31/2019
apiname:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
helpviewer_keywords:
- _dclass
- _ldclass
- _fdclass
- _dsign
- _ldsign
- _fdsign
- _dpcomp
- _ldpcomp
- _fdpcomp
- _dtest
- _ldtest
- _fdtest
- _d_int
- _ld_int
- _fd_int
- _dscale
- _ldscale
- _fdscale
- _dunscale
- _ldunscale
- _fdunscale
- _dexp
- _ldexp
- _fdexp
- _dnorm
- _fdnorm
- _dpoly
- _ldpoly
- _fdpoly
- _dlog
- _ldlog
- _fdlog
- _dsin
- _ldsin
- _fdsin
ms.openlocfilehash: 230d0def145bcb443437b59303b2b36e348da2bb
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703485"
---
# <a name="floating-point-primitives"></a>浮動小数点プリミティブ

いくつか標準 C ランタイム ライブラリ (CRT) 浮動小数点関数を実装するために使用される Microsoft 固有のプリミティブ関数。 これらは、完全を期すため、ここに記載されているが、使用は推奨されません。 これらの関数の一部は未使用とに注意してため、有効桁数、例外処理、および IEEE 754 動作に準拠で問題が呼ばれています。 これらは、旧バージョンと互換性のためだけのライブラリに存在します。 適切な動作、移植性、および標準に準拠しているには、これらの関数より浮動小数点の標準の関数を優先します。

## <a name="dclass-ldclass-fdclass"></a>_dclass _ldclass、_fdclass

### <a name="syntax"></a>構文

```C
short __cdecl _dclass(double x);
short __cdecl _ldclass(long double x);
short __cdecl _fdclass(float x);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点関数の引数。

### <a name="remarks"></a>Remarks

これらの浮動小数点プリミティブ CRT マクロの C# バージョンを実装する[fpclassify](fpclassify.md)浮動小数点型。 引数の分類*x* math.h で定義されているこれらの定数の 1 つとして返されます。

|[値]|説明|
|-----------|-----------------|
| **FP_NAN** | クワイエット型、シグナル型、または不確定の NaN |
| **FP_INFINITE** | 正または負の無限大 |
| **FP_NORMAL** | 正規化された正または負の 0 以外の値 |
| **FP_SUBNORMAL** | 正または負の値のある (非正規化された) 値 |
| **FP_ZERO** | 正または負の 0 値 |

詳細については、Microsoft 固有を使用することができます[_fpclass、_fpclassf](fpclass-fpclassf.md)関数。 使用して、 [fpclassify](fpclassify.md)マクロまたは関数を移植性を考慮します。

## <a name="dsign-ldsign-fdsign"></a>_dsign _ldsign、_fdsign

### <a name="syntax"></a>構文

```C
int __cdecl _dsign(double x);
int __cdecl _ldsign(long double x);
int __cdecl _fdsign(float x);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点関数の引数。

### <a name="remarks"></a>Remarks

これらの浮動小数点プリミティブを実装、 [signbit](signbit.md)マクロまたは crt 関数。 引数の有効桁 (仮数) で、符号ビットが設定されている場合は、0 以外の値を返す、 *x*、符号ビットが設定されていない場合は 0。

## <a name="dpcomp-ldpcomp-fdpcomp"></a>_dpcomp _ldpcomp、_fdpcomp

### <a name="syntax"></a>構文

```C
int __cdecl _dpcomp(double x, double y);
int __cdecl _ldpcomp(long double x, long double y);
int __cdecl _fdpcomp(float x, float y);
```

### <a name="parameters"></a>パラメーター

*x*、 *y*<br/>
浮動小数点関数の引数。

### <a name="remarks"></a>Remarks

これらの浮動小数点プリミティブは、2 つの引数をとる*x*と*y*、または math.h で定義されているこれらの定数のビット演算として表される、順序付けの関係を示す値を返します。

| [値] | 説明 |
|------------|-----------------|
| **_FP_LT** | *x*対象となるより小さい*y* |
| **_FP_EQ** | *x*に等しいと見なす*y* |
| **_FP_GT** | *x*よりも大きいと見なす*y* |

これらのプリミティブの実装、 [isgreater、isgreaterequal、小さければ、islessequal、islessgreater、および isunordered](floating-point-ordering.md)マクロおよび crt 関数。

## <a name="dtest-ldtest-fdtest"></a>_dtest _ldtest、_fdtest

### <a name="syntax"></a>構文

```C
short __cdecl _dtest(double* px);
short __cdecl _ldtest(long double* px);
short __cdecl _fdtest(float* px);
```

### <a name="parameters"></a>パラメーター

*px*<br/>
浮動小数点引数へのポインター。

### <a name="remarks"></a>Remarks

これらの浮動小数点プリミティブは、C++ のバージョンの CRT 関数を実装[fpclassify](fpclassify.md)浮動小数点型。 引数*x*が評価される、math.h で定義されているこれらの定数の 1 つとして、分類が返されます。

|[値]|説明|
|-----------|-----------------|
| **FP_NAN** | クワイエット型、シグナル型、または不確定の NaN |
| **FP_INFINITE** | 正または負の無限大 |
| **FP_NORMAL** | 正規化された正または負の 0 以外の値 |
| **FP_SUBNORMAL** | 正または負の値のある (非正規化された) 値 |
| **FP_ZERO** | 正または負の 0 値 |

詳細については、Microsoft 固有を使用することができます[_fpclass、_fpclassf](fpclass-fpclassf.md)関数。 使用して、 [fpclassify](fpclassify.md)移植性の関数。

## <a name="dint-ldint-fdint"></a>_d_int _ld_int、_fd_int

### <a name="syntax"></a>構文

```C
short __cdecl _d_int(double* px, short exp);
short __cdecl _ld_int(long double* px, short exp);
short __cdecl _fd_int(float* px, short exp);
```

### <a name="parameters"></a>パラメーター

*px*<br/>
浮動小数点引数へのポインター。

*exp*<br/>
整数型としての指数。

### <a name="remarks"></a>Remarks

これらの浮動小数点プリミティブ浮動小数点値へのポインターを使用する*px*と指数値*exp*、可能であれば、特定の指数部の下の浮動小数点値の小数部を削除. 返される値は、結果の**fpclassify**で入力値に対して*px*の出力値に NaN または無限大の場合と*px*それ以外の場合。

## <a name="dscale-ldscale-fdscale"></a>_dscale _ldscale、_fdscale

### <a name="syntax"></a>構文

```C
short __cdecl _dscale(double* px, long exp);
short __cdecl _ldscale(long double* px, long exp);
short __cdecl _fdscale(float* px, long exp);
```

### <a name="parameters"></a>パラメーター

*px*<br/>
浮動小数点引数へのポインター。

*exp*<br/>
整数型としての指数。

### <a name="remarks"></a>Remarks

これらの浮動小数点プリミティブ浮動小数点値へのポインターを使用する*px*と指数値*exp*の値のスケールと*px* 2<sup> *exp*</sup>、可能な場合。 返される値は、結果の**fpclassify**で入力値に対して*px*の出力値に NaN または無限大の場合と*px*それ以外の場合。 移植性のため、必要に応じて、 [ldexp、ldexpf、ldexpl と](ldexp.md)関数。

## <a name="dunscale-ldunscale-fdunscale"></a>_dunscale _ldunscale、_fdunscale

### <a name="syntax"></a>構文

```C
short __cdecl _dunscale(short* pexp, double* px);
short __cdecl _ldunscale(short* pexp, long double* px);
short __cdecl _fdunscale(short* pexp, float* px);
```

### <a name="parameters"></a>パラメーター

*pexp*<br/>
整数型として指数へのポインター。

*px*<br/>
浮動小数点引数へのポインター。

### <a name="remarks"></a>Remarks

これらの浮動小数点プリミティブが指定した浮動小数点値を分割*px* (仮数) の有効桁と指数部、可能な場合にします。 絶対値が 0.5 以上 1.0 未満の有効桁でスケーリングします。 指数値が、 *n*元の浮動小数点値が 2 回スケールの有効桁と等しく、<sup>*n*</sup>します。 この整数の指数*n*が指す位置に格納されて*pexp*します。 返される値は、結果の**fpclassify**で入力値に対して*px* NaN または無限大の場合、それ以外の場合、出力値にします。 移植性のため、必要に応じて、 [frexp、frexpf、frexpl](frexp.md)関数。

## <a name="dexp-ldexp-fdexp"></a>_dexp _ldexp、_fdexp

### <a name="syntax"></a>構文

```C
short __cdecl _dexp(double* px, double y, long exp);
short __cdecl _ldexp(long double* px, long double y, long exp);
short __cdecl _fdexp(float* px, float y, long exp);
```

### <a name="parameters"></a>パラメーター

*y*<br/>
浮動小数点関数の引数。

*px*<br/>
浮動小数点引数へのポインター。

*exp*<br/>
整数型としての指数。

### <a name="remarks"></a>Remarks

これらの浮動小数点プリミティブ浮動小数点の値が指定した場所での構築*px*等しく*y* * 2<sup>*exp*</sup>します。 返される値は、結果の**fpclassify**で入力値に対して*y*の出力値に NaN または無限大の場合と*px*それ以外の場合。 移植性のため、必要に応じて、 [ldexp、ldexpf、ldexpl と](ldexp.md)関数。

## <a name="dnorm-fdnorm"></a>_dnorm、_fdnorm

### <a name="syntax"></a>構文

```C
short __cdecl _dnorm(unsigned short* ps);
short __cdecl _fdnorm(unsigned short* ps);
```

### <a name="parameters"></a>パラメーター

*ps*<br/>
配列として表される浮動小数点値のビットごとの表現へのポインター**符号なし****短い**します。

### <a name="remarks"></a>Remarks

これらの浮動小数点プリミティブ underflowed の浮動小数点値の小数部を正規化し、調整、*特性*、または一致するように、バイアスをかけた指数。 配列に変換する浮動小数点型のビットごとの表現として、値を渡す**符号なし****短い**を通じて、 `_double_val`、 `_ldouble_val`、または`_float_val`型math.h で punning 共用体が宣言されています。 戻り値の結果は、 **fpclassify**とそれ以外の場合、出力値に NaN または無限大の場合は、入力の浮動小数点値。

## <a name="dpoly-ldpoly-fdpoly"></a>_dpoly _ldpoly、_fdpoly

### <a name="syntax"></a>構文

```C
double __cdecl _dpoly(double x, double const* table, int n);
long double __cdecl _ldpoly(long double x, long double const* table, int n);
float __cdecl _fdpoly(float x, _float const* table, int n);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点関数の引数。

*table*<br/>
多項式の定数係数のテーブルへのポインター。

*n*<br/>
多項式の次数を評価します。

### <a name="remarks"></a>Remarks

これらの浮動小数点プリミティブの評価を返す*x* 、多項式の*n*係数を持つが対応する定数値で表される*テーブル*. たとえば場合、*テーブル*\[0] = 3.0、*テーブル*\[1] = 4.0 では、*テーブル*\[2] = 5.0、および*n*= 2、多項式 5.0 x 表します<sup>2</sup> 4.0 + x + 3.0。 この多項式が評価される場合*x* 2.0 では、結果が 31.0 します。 これらの関数は、内部的に使用されません。

## <a name="dlog-dlog-dlog"></a>_dlog _dlog、_dlog

### <a name="syntax"></a>構文

```C
double __cdecl _dlog(double x, int base_flag);
long double __cdecl _ldlog(long double x, int base_flag);
float __cdecl _fdlog(float x, int base_flag);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点関数の引数。

*base_flag*<br/>
ベースの場合は 0 を使用する底を制御するフラグ*e*底 10 の場合は 0 以外。

### <a name="remarks"></a>Remarks

これらの浮動小数点プリミティブの自然対数を返す*x*、ln (*x*) またはログ<sub>*e*</sub>(*x*)、ときに*base_flag*は 0 です。 底 10 のログを返す*x*、またはログ<sub>10</sub>(*x*) ときに、 *base_flag* 0 以外の場合します。 これらの関数は、内部的に使用されません。 移植性のため、関数は、必要に応じて[log、logf、logl、log10、log10f、および log10l](log-logf-log10-log10f.md)します。

## <a name="dsin-ldsin-fdsin"></a>_dsin _ldsin、_fdsin

### <a name="syntax"></a>構文

```C
double __cdecl _dsin(double x, unsigned int quadrant);
long double __cdecl _ldsin(long double x, unsigned int quadrant);
float __cdecl _fdsin(float x, unsigned int quadrant);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点関数の引数。

*クアドラント*<br/>
作業領域のオフセット 0、1、2、または生成するために使用する 3 `sin`、 `cos`、 `-sin`、および`-cos`結果。

### <a name="remarks"></a>Remarks

これらの浮動小数点プリミティブのサインを返します*x* 、オフセット、*クアドラント*4 剰余。 、サインの値を返しますが実際には、コサイン、サイン、とのコサイン*x*とき*クアドラント*4 は、0、1、2、3、またはそれぞれします。 これらの関数は、内部的に使用されません。 移植性のため、必要に応じて、 [sin、sinf、sinl](sin-sinf-sinl.md)、 [cos、cosf、cosl、](cos-cosf-cosl.md)関数。

## <a name="requirements"></a>必要条件

ヘッダー: \<math.h >

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite _finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
[cos、cosf、cosl](cos-cosf-cosl.md)<br/>
[frexp、frexpf、frexpl](frexp.md)<br/>
[ldexp、ldexpf、ldexpl](ldexp.md)<br/>
[log、logf、logl、log10、log10f、log10l](log-logf-log10-log10f.md)<br/>
[sin、sinf、sinl](sin-sinf-sinl.md)<br/>
