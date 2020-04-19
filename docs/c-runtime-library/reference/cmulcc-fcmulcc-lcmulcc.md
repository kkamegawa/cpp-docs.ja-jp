---
title: _Cmulcc、_FCmulcc、_LCmulcc
ms.date: 03/30/2018
api_name:
- _Cmulcc
- _FCmulcc
- _LCmulcc
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
- _Cmulcc
- _FCmulcc
- _LCmulcc
- complex/_Cmulcc
- complex/_FCmulcc
- complex/_LCmulcc
helpviewer_keywords:
- _Cmulcc function
- _FCmulcc function
- _LCmulcc function
ms.openlocfilehash: fc21f8cbd2103993bc2b3e36020c57c8520f04a1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939069"
---
# <a name="_cmulcc-_fcmulcc-_lcmulcc"></a>_Cmulcc、_FCmulcc、_LCmulcc

2つの複素数を乗算します。

## <a name="syntax"></a>構文

```C
_Dcomplex _Cmulcc( _Dcomplex x, _Dcomplex y );
_Fcomplex _FCmulcc( _Fcomplex x, _Fcomplex y );
_Lcomplex _LCmulcc( _Lcomplex x, _Lcomplex y );
```

### <a name="parameters"></a>パラメーター

*x*<br/>
乗算する複合オペランドの1つ。

*y*<br/>
乗算するもう1つの複合オペランド。

## <a name="return-value"></a>戻り値

複素数*x*と*y*の複雑な積を**表す、** **_Fcomplex**、または **_Lcomplex**構造体。

## <a name="remarks"></a>Remarks

組み込みの算術演算子は、複合型の Microsoft 実装では機能しないため、 **_Cmulcc**、 **_FCmulcc**、および **_LCmulcc**の各関数は複合型の乗算を簡略化します。

## <a name="requirements"></a>必要条件

|ルーチン|C ヘッダー|C++ ヘッダー|
|-------------|--------------|------------------|
|**_Cmulcc**、 **_FCmulcc**、 **_LCmulcc**|\<complex.h>|\<complex.h>|

これらの関数は、Microsoft 固有の関数です。 型 **(_t**、 **_Fcomplex**、および **_Lcomplex** ) は、実装されていない C99 ネイティブ型に対して、それぞれ**Complex**、 **float**、および**long double complex**の各型に相当します。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[_Cbuild、_FCbuild、_LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[_Cmulcr、_FCmulcr、_LCmulcr](cmulcr-fcmulcr-lcmulcr.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[creal、crealf、creall](creal-crealf-creall.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>
