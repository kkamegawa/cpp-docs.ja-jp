---
title: fmod、fmodf、fmodl
ms.date: 04/05/2018
api_name:
- fmod
- fmodf
- fmodl
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
- fmod
- _fmodl
- fmodf
helpviewer_keywords:
- calculating floating-point remainders
- fmodf function
- fmodl function
- fmod function
- floating-point numbers, calculating remainders
ms.assetid: 6962d369-d11f-40b1-a6d7-6f67239f8a23
ms.openlocfilehash: e98432a73df8b872593d4cd610139bdfa72a25c4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957078"
---
# <a name="fmod-fmodf-fmodl"></a>fmod、fmodf、fmodl

浮動小数点の剰余を計算します。

## <a name="syntax"></a>構文

```C
double fmod(
   double x,
   double y
);
float fmod(
   float x,
   float y
);  // C++ only
long double fmod(
   long double x,
   long double y
);  // C++ only
float fmodf(
   float x,
   float y
);
long double fmodl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>パラメーター

*x*、 *y*<br/>
浮動小数点値。

## <a name="return-value"></a>戻り値

**fmod**は、 *x* / *y*の浮動小数点の剰余を返します。 *Y*の値が0.0 の場合、 **fmod**は簡易な NaN を返します。 **Printf**ファミリによる簡易な NaN の表現については、「 [printf](printf-printf-l-wprintf-wprintf-l.md)」を参照してください。

## <a name="remarks"></a>Remarks

**Fmod**関数は x*y* *の* / 浮動小数点の剰余*f*を計算*します (* *x* = *i* \* *y* + *f*)。は整数で、 *f*は*x*と同じ符号を持ち、 *f*の絶対値は*y*の絶対値より小さい値です。

C++ではオーバーロードが可能であるため、 **float 型**および**long** **double**型の値を受け取って返す**fmod**のオーバーロードを呼び出すことができます。 C プログラムでは、 **fmod**は常に2つの**double**引数を受け取り、 **double**を返します。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**fmod**、 **fmodf**、 **fmodl**|\<math.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_fmod.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;

   z = fmod( w, x );
   printf( "The remainder of %.2f / %.2f is %f\n", w, x, z );
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[ceil、ceilf、ceill](ceil-ceilf-ceill.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[_CIfmod](../../c-runtime-library/cifmod.md)<br/>
