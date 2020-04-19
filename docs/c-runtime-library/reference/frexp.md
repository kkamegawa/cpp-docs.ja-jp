---
title: frexp、frexpf、frexpf
ms.date: 04/05/2018
api_name:
- frexp
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
- frexp
- _frexpl
helpviewer_keywords:
- _frexpl function
- mantissas, floating-point variables
- frexpl function
- exponent, floating-point numbers
- frexp function
- floating-point functions, mantissa and exponent
ms.assetid: 9b020f2e-3967-45ec-a6a8-d467a071aa55
ms.openlocfilehash: 3a67ced9bd6653a7c40c98a8cf015663c37457bb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956634"
---
# <a name="frexp-frexpf-frexpl"></a>frexp、frexpf、frexpf

浮動小数点数の仮数と指数を取得します。

## <a name="syntax"></a>構文

```C
double frexp(
   double x,
   int *expptr
);
float frexpf(
   float x,
   int * expptr
);
long double frexpl(
   long double x,
   int * expptr
);
float frexp(
   float x,
   int * expptr
);  // C++ only
long double frexp(
   long double x,
   int * expptr
);  // C++ only
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点値。

*すべての ptr*<br/>
格納された整数の指数へのポインター。

## <a name="return-value"></a>戻り値

**frexp**は仮数を返します。 *X*が0の場合、関数は仮数と指数の両方に対して0を返します。 **値が NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明され*ているよう*に、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は**errno**を**EINVAL**に設定し、0を返します。

## <a name="remarks"></a>Remarks

**Frexp**関数は、浮動小数点値 (*x*) を仮数 (*m*) と指数 (*n*) に分割します。これは、 *m*の絶対値が0.5 以上1.0 より小さく、 *x*  = であることを示します。*m* * 2<sup>*n*</sup> 整数の指数*n*は、によって示される位置に格納*されます*。

C++ではオーバーロードが可能であるため、 **frexp**のオーバーロードを呼び出すことができます。 C プログラムでは、 **frexp**は常に**double**と**int**ポインターを受け取り、 **double**を返します。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**frexp**、 **frexpf**、 **frexpf**|\<math.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_frexp.c
// This program calculates frexp( 16.4, &n )
// then displays y and n.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x, y;
   int n;

   x = 16.4;
   y = frexp( x, &n );
   printf( "frexp( %f, &n ) = %f, n = %d\n", x, y, n );
}
```

```Output
frexp( 16.400000, &n ) = 0.512500, n = 5
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[ldexp](ldexp.md)<br/>
[modf、modff、modfl](modf-modff-modfl.md)<br/>
