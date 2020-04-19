---
title: remquo、remquof、remquol
ms.date: 04/05/2018
api_name:
- remquof
- remquo
- remquol
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
- remquof
- remquol
- remquo
helpviewer_keywords:
- remquol function
- remquof function
- remquo function
ms.assetid: a1d3cb8b-8027-4cd3-8deb-04eb17f299fc
ms.openlocfilehash: c96357dda007e9bf12ddaf6091af47794bfc0630
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949373"
---
# <a name="remquo-remquof-remquol"></a>remquo、remquof、remquol

2 個の整数値の剰余を計算し、パラメーターに指定された位置に、整数値を符号と商の近似値と共に格納します。

## <a name="syntax"></a>構文

```C
double remquo( double numer, double denom, int* quo );
float remquof( float numer, float denom, int* quo );
long double remquol( long double numer, long double denom, int* quo );
```

```cpp
float remquo( float numer, float denom, int* quo ); /* C++ only */
long double remquo( long double numer, long double denom, int* quo ); /* C++ only */
```

### <a name="parameters"></a>パラメーター

*数値*<br/>
分子。

*デ om*<br/>
分母。

*従来*<br/>
符号と商の近似値を持つ値を格納する整数へのポインター。

## <a name="return-value"></a>戻り値

その後、 *x* / *y*の浮動小数点の剰余**を返します**。 *Y*の値が0.0 の場合、 **Remquo** quiet NaN を返します。 **Printf**ファミリによる簡易な NaN の表現については、「 [printf、wprintf、_wprintf_l](printf-printf-l-wprintf-wprintf-l.md)」を参照してください。

## <a name="remarks"></a>Remarks

**Remquo**は x*y* *の* / 浮動小数点の剰余*f*を計算します ( *x* = *i* \* *y* + *f*)。は整数で、 *f*は*x*と同じ符号を持ち、 *f*の絶対値は*y*の絶対値より小さい値です。

C++ではオーバーロードが可能であるため、 **float 型**または**long** **double**型の値を取得して返すように、 **remquo**オーバーロードを呼び出すことができます。 C プログラムでは、 **remquo**常に2つの**double**引数を受け取り、 **double**を返します。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー (C)|必須ヘッダー (C++)|
|--------------|---------------------|-|
|**remquo** **remquof**、 **remquol**|\<math.h>|\<cmath> または \<math.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_remquo.c
// This program displays a floating-point remainder.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double w = -10.0, x = 3.0, z;
   int quo = 0;

   z = remquo(w, x, &quo);
   printf("The remainder of %.2f / %.2f is %f\n", w, x, z);
   printf("Approximate signed quotient is %d\n", quo);
}
```

```Output
The remainder of -10.00 / 3.00 is -1.000000
Approximate signed quotient is -3
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv、lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
[fmod、fmodf](fmod-fmodf.md)<br/>
[remainder、remainderf、remainderl](remainder-remainderf-remainderl.md)<br/>
