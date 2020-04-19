---
title: ldexp、ldexp、ldexp
ms.date: 04/05/2018
api_name:
- ldexp
- ldexpf
- ldexpl
- _ldexpl
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
- ldexp
- ldexpf
- ldexpl
- _ldexpl
helpviewer_keywords:
- calculating real numbers
- computing real numbers
- mantissas, floating-point variables
- ldexp function
- ldexpf function
- ldexpl function
- exponent, floating-point numbers
- floating-point functions, mantissa and exponent
ms.assetid: aa7f5310-3879-4f63-ae74-86a39fbdedfa
ms.openlocfilehash: 7fabd00c7ddc5c430c158089b7e5769158b46328
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953501"
---
# <a name="ldexp-ldexpf-ldexpl"></a>ldexp、ldexp、ldexp

浮動小数点数に整数である 2 の累乗を乗算します。

## <a name="syntax"></a>構文

```C
double ldexp(
   double x,
   int exp
);
float ldexp(
   float x,
   int exp
);  // C++ only
long double ldexp(
   long double x,
   int exp
);  // C++ only
float ldexpf(
   float x,
   int exp
);
long double ldexpl(
   long double x,
   int exp
);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点値。

*exp*<br/>
整数の指数。

## <a name="return-value"></a>戻り値

**Ldexp**関数は、成功した場合、 *x* \* 2<sup>*exp*</sup>の値を返します。 オーバーフローでは、 *x*の符号によっては、 **ldexp**は +/- **HUGE_VAL**; を返します。**errno**値は**ERANGE**に設定されます。

**Errno**および考えられるエラーの戻り値の詳細については、「 [errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

でC++はオーバーロードが可能であるため、**浮動小数点**型または**long** **double**型を受け取る**ldexp**のオーバーロードを呼び出すことができます。 C プログラムでは、 **ldexp**は常に**double**と**int**を受け取り、 **double**を返します。

## <a name="requirements"></a>必要条件

|ルーチン|C ヘッダー|C++ ヘッダー|
|-------------|--------------|------------------|
|**ldexp**、 **ldexp**、 **ldexp**|\<math.h>|\<cmath>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="example"></a>例

```C
// crt_ldexp.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 4.0, y;
   int p = 3;

   y = ldexp( x, p );
   printf( "%2.1f times two to the power of %d is %2.1f\n", x, p, y );
}
```

## <a name="output"></a>Output

```Output
4.0 times two to the power of 3 is 32.0
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[frexp](frexp.md)<br/>
[modf、modff、modfl](modf-modff-modfl.md)<br/>
