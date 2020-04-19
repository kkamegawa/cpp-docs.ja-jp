---
title: asinh、asinhf、asinhl
ms.date: 04/05/2018
api_name:
- asinh
- asinhf
- asinhl
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
- asinhf
- asinhl
- asinh
helpviewer_keywords:
- asinh function
- asinhl function
- asinhf function
ms.assetid: 4488babe-1a7e-44ca-8b7b-c2db0a70084f
ms.openlocfilehash: f4d93f121c0124293a5bdff9041d0adfaab5d83c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939638"
---
# <a name="asinh-asinhf-asinhl"></a>asinh、asinhf、asinhl

逆ハイパーボリック サインを計算します。

## <a name="syntax"></a>構文

```C
double asinh( double x );
float asinhf( float x );
long double asinhl( long double x );
```

```cpp
float asinh( float x );  // C++ only
long double asinh( long double x );  // C++ only
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点値。

## <a name="return-value"></a>戻り値

**Asinh**関数は、 *x*の逆ハイパーボリックサイン (アークハイパーボリックサイン) を返します。 この関数は浮動小数点ドメインで有効です。 *X*が簡易な NaN、無限、または無限大の場合は、同じ値が返されます。

|入力|SEH 例外|**_matherr**例外的|
|-----------|-------------------|--------------------------|
|± QNAN、IND、INF|none|none|

## <a name="remarks"></a>Remarks

をC++使用すると、 **float 型**または**long** **double**型の値を受け取って返す**asinh**のオーバーロードを呼び出すことができます。 C プログラムでは、 **asinh**は常にを受け取り、 **double**を返します。

## <a name="requirements"></a>必要条件

|関数|必須の C ヘッダー|必須の C++ ヘッダー|
|--------------|--------------|------------------|
|**asinh**、 **asinhf**、 **asinhf**|\<math.h>|\<cmath > また\<は math. h <|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_asinh.c
// Compile by using: cl /W4 crt_asinh.c
// This program displays the hyperbolic sine of pi / 4
// and the arc hyperbolic sine of the result.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double pi = 3.1415926535;
   double x, y;

   x = sinh( pi / 4 );
   y = asinh( x );
   printf( "sinh( %f ) = %f\n", pi/4, x );
   printf( "asinh( %f ) = %f\n", x, y );
}
```

```Output
sinh( 0.785398 ) = 0.868671
asinh( 0.868671 ) = 0.785398
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[acosh、acoshf、acoshl](acosh-acoshf-acoshl.md)<br/>
[atanh、atanhf、atanhl](atanh-atanhf-atanhl.md)<br/>
[cosh、coshf、coshl](cosh-coshf-coshl.md)<br/>
[sinh、sinhf、sinhl](sinh-sinhf-sinhl.md)<br/>
[tanh、tanhf、tanhl](tanh-tanhf-tanhl.md)<br/>
