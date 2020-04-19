---
title: nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl
ms.date: 04/05/2018
api_name:
- nextafterf
- _nextafterf
- nextafter
- nextafterl
- _nextafter
- nexttoward
- nexttowardf
- nexttowardl
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
- nextafter
- _nextafter
- nextafterf
- nextafterl
- _nextafterf
- math/nextafter
- math/nextafterf
- math/nextafterl
- nexttoward
- nexttowardf
- nexttowardl
- math/nexttoward
- math/nexttowardf
- math/nexttowardl
helpviewer_keywords:
- _nextafter function
- nextafter function
- _nextafterf function
- nextafterf function
- nextafterl function
- nexttoward function
- nexttowardf function
- nexttowardl function
ms.assetid: 9785bfb9-de53-4bd0-9637-f05fa0c1f6ab
ms.openlocfilehash: c6b100fb24d879a16780650d8a374ec26f28c048
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857724"
---
# <a name="nextafter-nextafterf-nextafterl-_nextafter-_nextafterf-nexttoward-nexttowardf-nexttowardl"></a>nextafter、nextafterf、nextafterl、_nextafter、_nextafterf、nexttoward、nexttowardf、nexttowardl

次の表現可能な浮動小数点値を返します。

## <a name="syntax"></a>構文

```C
double nextafter( double x, double y );
float nextafterf( float x, float y );
long double nextafterl( long double x, long double y );

double _nextafter( double x, double y );
float _nextafterf( float x, float y ); /* x64 only */

double nexttoward( double x, long double y );
float nexttowardf( float x, long double y );
long double nexttowardl( long double x, long double y );
```

```cpp
float nextafter( float x, float y ); /* C++ only, requires <cmath> */
long double nextafter( long double x, long double y ); /* C++ only, requires <cmath> */

float nexttoward( float x, long double y ); /* C++ only, requires <cmath> */
long double nexttoward( long double x, long double y ); /* C++ only, requires <cmath> */
```

### <a name="parameters"></a>パラメーター

*x*<br/>
開始する浮動小数点値。

*y*<br/>
移動する浮動小数点値。

## <a name="return-value"></a>戻り値

*Y*方向の*x*の後に戻り値の型の次の表現可能な浮動小数点値を返します。 *X*と*y*が等しい場合、関数は、戻り値の型に変換された*y*を返します。例外は発生しません。 *X*が*y*と等しくなく、結果が denormal または0の場合は、 **FE_UNDERFLOW**と**FE_INEXACT**の浮動小数点例外の状態が設定され、正しい結果が返されます。 *X*または*y*が NAN の場合、戻り値は入力 nan のいずれかになります。 *X*が有限で、結果が無限であるか、または型で表現できない場合、正しく署名された無限大または NAN が返され、 **FE_OVERFLOW**と**FE_INEXACT**浮動小数点例外の状態が設定され、 **errno**が**ERANGE**に設定されます。

## <a name="remarks"></a>Remarks

パラメーターの型が*y*の場合を除き、 **nextafter**関数と**nextafter**関数ファミリは同等です。 *X*と*y*が等しい場合、返される値は、戻り値の型に変換された*y*になります。

でC++はオーバーロードが可能であるため \<cmath > を含めた場合は、 **float**型および**long** **double**型を返す**nextafter**と**nextafter**のオーバーロードを呼び出すことができます。 C プログラムでは、 **nextafter**と**nextafter**は常に**double**を返します。

**_Nextafter**関数と **_nextafterf**関数は、Microsoft 固有の関数です。 **_Nextafterf**関数は、x64 用にコンパイルする場合にのみ使用できます。

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー (C)|必須ヘッダー (C++)|
|-------------|---------------------------|-------------------------------|
|**nextafter**、 **nextafterf**、 **nextafterl**、 **_nextafterf**、 **nextafter**、 **nexttowardf**、 **nexttowardl**|\<math.h>|\<math.h> または \<cmath>|
|**_nextafter**|\<float.h>|\<float.h> または \<cfloat>|

互換性について詳しくは、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>参照

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
