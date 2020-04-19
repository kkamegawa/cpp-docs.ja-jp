---
title: creal、crealf、creall
ms.date: 03/30/2018
api_name:
- creal
- crealf
- creall
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
- creal
- crealf
- creall
- complex/creal
- complex/crealf
- complex/creall
helpviewer_keywords:
- creal function
- crealf function
- creall function
ms.assetid: fa3ac62f-7aa3-4238-a71f-d6b00cd0c7c8
ms.openlocfilehash: ebd52a23765177d74f2bff5660f806ee5c4a9573
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942600"
---
# <a name="creal-crealf-creall"></a>creal、crealf、creall

複素数の実数部を取得します。

## <a name="syntax"></a>構文

```C
double creal( _Dcomplex z );
float crealf( _Fcomplex z );
long double creall( _Lcomplex z );
```

```cpp
float creal( _Fcomplex z );  // C++ only
long double creal( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>パラメーター

*z*<br/>
複素数。

## <a name="return-value"></a>戻り値

*Z*の実数部。

## <a name="remarks"></a>Remarks

でC++はオーバーロードが可能であるため、 **_Fcomplex**値または **_Lcomplex**値を受け取る**creal**のオーバーロードを呼び出し、 **float**型または**long double 型**の値を返すことができます。 C プログラムでは、 **creal**は常に**値を受け取り、** **double**値を返します。

## <a name="requirements"></a>必要条件

|ルーチン|C ヘッダー|C++ ヘッダー|
|-------------|--------------|------------------|
|**creal**、 **crealf**、 **creal**|\<complex.h>|\<ccomplex>|

**_Fcomplex**、_Lcomplex **、および**型は、それぞれ、実装されていないネイティブの C99 型**float**、Complex、 **double complex**、および**long double complex**の各型に相当します。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[_Cbuild、_FCbuild、_LCbuild](cbuild-fcbuild-lcbuild.md)<br/>
[norm、normf、norml](norm-normf-norml1.md)<br/>
[cproj、cprojf、cprojl](cproj-cprojf-cprojl.md)<br/>
[conj、conjf、conjl](conj-conjf-conjl.md)<br/>
[cimag、cimagf、cimagl](cimag-cimagf-cimagl.md)<br/>
[carg、cargf、cargl](carg-cargf-cargl.md)<br/>
[cabs、cabsf、cabsl](cabs-cabsf-cabsl.md)<br/>