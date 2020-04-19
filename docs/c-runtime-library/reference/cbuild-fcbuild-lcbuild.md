---
title: _Cbuild、_FCbuild、_LCbuild
ms.date: 03/30/2018
api_name:
- _Cbuild
- _FCbuild
- _LCbuild
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _Cbuild
- _FCbuild
- _LCbuild
- complex/_Cbuild
- complex/_FCbuild
- complex/_LCbuild
helpviewer_keywords:
- _Cbuild function
- _FCbuild function
- _LCbuild function
ms.openlocfilehash: b0ae50f40f0ca0a926e1eef586c6610a04b6ea7a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943225"
---
# <a name="_cbuild-_fcbuild-_lcbuild"></a>_Cbuild、_FCbuild、_LCbuild

実数部および虚数部から複素数を構築します。

## <a name="syntax"></a>構文

```C
_Dcomplex _Cbuild( double real, double imaginary );
_Fcomplex _FCbuild( float real, float imaginary );
_Lcomplex _LCbuild( long double real, long double imaginary );
```

### <a name="parameters"></a>パラメーター

*real*<br/>
構築する複素数の実数部。

*imaginary*<br/>
構築する複素数の虚数部。

## <a name="return-value"></a>戻り値

指定された浮動小数点型の値に対する複素数 (*実数*、*虚数* \* i) を**表す、** **_Fcomplex**、または **_Lcomplex**構造体。

## <a name="remarks"></a>Remarks

**_Cbuild**、 **(fcbuild**)、および**lcbuild**関数は、複合型の作成を簡略化します。 表示される複素数の実数部と虚数部を取得するには、 [creal、crealf、creal](creal-crealf-creall.md) 、および[cimag、cimagf、cimagf](cimag-cimagf-cimagl.md)関数を使用します。

## <a name="requirements"></a>必要条件

|ルーチン|C ヘッダー|C++ ヘッダー|
|-------------|--------------|------------------|
|**_Cbuild**、( **fcbuild**)、 **lcbuild**|\<complex.h>|\<ccomplex>|

これらの関数は、Microsoft 固有の関数です。 型 **(_t**、 **_Fcomplex**、および **_Lcomplex** ) は、実装されていない C99 ネイティブ型に対して、それぞれ**Complex**、 **float**、および**long double complex**の各型に相当します。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[_Cmulcc、_FCmulcc、_LCmulcc](cmulcc-fcmulcc-lcmulcc.md)<br/>
[_Cmulcr、_FCmulcr、_LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
