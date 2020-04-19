---
title: remainder、remainderf、remainderl
ms.date: 04/05/2018
api_name:
- remainderl
- remainder
- remainderf
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
- remainderf
- remainder
- remainderl
helpviewer_keywords:
- remainderf
- remainderl
- remainder
ms.assetid: 5f721fb3-8b78-4597-9bc0-ca9bcd1f1d0e
ms.openlocfilehash: 851f022325bb617cb2b0ae9a331b680b9d9fd303
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949423"
---
# <a name="remainder-remainderf-remainderl"></a>remainder、remainderf、remainderl

2 つの浮動小数点値の商の剰余を最も近い整数値に丸めて計算します。

## <a name="syntax"></a>構文

```C
double remainder( double x, double y );
float remainderf( float x, float y );
long double remainderl( long double x, long double y );
```

```cpp
float remainder( float x, float y ); /* C++ only */
long double remainder( long double x, long double y ); /* C++ only */
```

### <a name="parameters"></a>パラメーター

*x*<br/>
分子。

*y*<br/>
分母。

## <a name="return-value"></a>戻り値

*X* / *y*の浮動小数点の剰余。 *Y*の値が0.0 の場合、**剰余**は簡易な NaN を返します。 **Printf**ファミリによる簡易な NaN の表現については、「 [printf、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)」を参照してください。

## <a name="remarks"></a>Remarks

\* **剰余**関数は、x*y* *y* /  =  の浮動小数点の剰余rを計算します(n +  *)。* *x* /  &#124; &#124;  - y の値に最も近い整数を指定します。 n x y = 1/2 の場合は、n になります。 /  *R* = 0 の場合、 *r*は*x*と同じ符号を持ちます。

オーバー ロードを呼び出すことができますので、C++ ではオーバー ロード、**remainder**を受け取って返す**float**または**long** **double**値。 C プログラムでは、**remainder**は常に2つの**double**引数を受け取り、 **double**を返します。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー (C)|必須ヘッダー (C++)|
|--------------|---------------------|-|
|**残り、残りの部分**は **、** 残って**います。**|\<math.h>|\<cmath> または \<math.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_remainder.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = remainder(w, x);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv、lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod、fmodf](fmod-fmodf.md)<br/>
[remquo、remquof、remquol](remquo-remquof-remquol.md)<br/>
