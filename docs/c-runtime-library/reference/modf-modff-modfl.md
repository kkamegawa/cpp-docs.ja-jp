---
title: modf、modff、modfl
ms.date: 04/05/2018
api_name:
- modff
- modf
- modfl
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
- modff
- _modfl
- modf
- modfl
- math/modf
- math/modff
- math/modfl
helpviewer_keywords:
- modf function
- modff function
- modfl function
ms.assetid: b1c7abf5-d476-43ca-a03c-02072a86e32d
ms.openlocfilehash: 32caadb787031dca0b0726c546a11c5cd6722b82
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951540"
---
# <a name="modf-modff-modfl"></a>modf、modff、modfl

浮動小数点値を小数部と整数部に分割します。

## <a name="syntax"></a>構文

```C
double modf( double x, double * intptr );
float modff( float x, float * intptr );
long double modfl( long double x, long double * intptr );
```

```cpp
float modf( float x, float * intptr );  // C++ only
long double modf( long double x, long double * intptr );  // C++ only
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点値。

*代わりに*<br/>
格納された整数部分へのポインター。

## <a name="return-value"></a>戻り値

この関数は *x* の符号付き小数部を返します。 エラーの戻り値はありません。

## <a name="remarks"></a>Remarks

**Modf**関数は、浮動小数点値*x*を小数部と整数部に分割し、それぞれが*x*と同じ符号を持ちます。 *X*の符号付き小数部が返されます。 整数部分は、 *intptr*に浮動小数点値として格納されます。

**modf**には、ストリーミング SIMD 拡張命令 2 (SSE2) を使用する実装があります。 SSE2 実装の使い方の詳細および制約については、「[_set_SSE2_enable](set-sse2-enable.md)」をご覧ください。

C++ではオーバーロードが可能であるため、 **float**または**long** **double**パラメーターを受け取って返す**modf**のオーバーロードを呼び出すことができます。 C プログラムでは、 **modf**は常に2つの double 値を受け取り、double 値を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**modf**、 **modff**、 **modff**|C: \<math.h><br /><br /> C++: \<cmath> または \<math.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_modf.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y, n;

   x = -14.87654321;      /* Divide x into its fractional */
   y = modf( x, &n );     /* and integer parts            */

   printf( "For %f, the fraction is %f and the integer is %.f\n",
           x, y, n );
}
```

```Output
For -14.876543, the fraction is -0.876543 and the integer is -14
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[ldexp](ldexp.md)<br/>
