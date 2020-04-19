---
title: lround、lroundf、lroundl、llround、llroundf、llroundl
ms.date: 04/05/2018
api_name:
- llround
- llroundf
- llroundl
- lroundf
- lround
- lroundl
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
- lround
- lroundl
- llroundl
- llround
- lroundf
- llroundf
helpviewer_keywords:
- lround function
- llroundl function
- llround function
- lroundf function
- llroundf function
- lroundl function
ms.assetid: cfb88a35-54c6-469f-85af-f7d695dcfdd8
ms.openlocfilehash: d849e838811abbed83499d6da283148650bab875
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953009"
---
# <a name="lround-lroundf-lroundl-llround-llroundf-llroundl"></a>lround、lroundf、lroundl、llround、llroundf、llroundl

浮動小数点値を最も近い整数に丸めます。

## <a name="syntax"></a>構文

```C
long lround(
   double x
);
long lround(
   float x
);  // C++ only
long lround(
   long double x
);  // C++ only
long lroundf(
   float x
);
long lroundl(
   long double x
);
long long llround(
   double x
);
long long llround(
   float x
);  // C++ only
long long llround(
   long double x
);  // C++ only
long long llroundf(
   float x
);
long long llroundl(
   long double x
);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
丸める浮動小数点値。

## <a name="return-value"></a>戻り値

**Lround**関数と**llround**関数では、最も近い**long**型または**long** **型の整数が** *x*に返されます。 中間の値は、浮動小数点丸めモードの設定にかかわらず、ゼロから離れる方向に丸められます。 エラーの戻り値はありません。

|入力|SEH 例外|Matherr 例外|
|-----------|-------------------|-----------------------|
|± **QNAN**、 **IND**|none|**_DOMAIN**|

## <a name="remarks"></a>Remarks

でC++はオーバーロードが可能であるため、**浮動小数**点と**long** **double**型の値を受け取って返す**lround**または**llround**のオーバーロードを呼び出すことができます。 C プログラムでは、 **lround**と**llround**は常に**double**を取得して返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**lround**、 **lroundf**、 **lroundl**、 **llround**、 **llroundf**、 **llroundl**|\<math.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_lround.c
// Build with: cl /W4 /Tc crt_lround.c
// This example displays the rounded results of
// the floating-point values 2.499999, -2.499999,
// 2.8, -2.8, 3.5 and -3.5.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.499999;
   float y = 2.8f;
   long double z = 3.5L;

   printf("lround(%f) is %d\n", x, lround(x));
   printf("lround(%f) is %d\n", -x, lround(-x));
   printf("lroundf(%f) is %d\n", y, lroundf(y));
   printf("lroundf(%f) is %d\n", -y, lroundf(-y));
   printf("lroundl(%Lf) is %d\n", z, lroundl(z));
   printf("lroundl(%Lf) is %d\n", -z, lroundl(-z));
}
```

```Output
lround(2.499999) is 2
lround(-2.499999) is -2
lroundf(2.800000) is 3
lroundf(-2.800000) is -3
lroundl(3.500000) is 4
lroundl(-3.500000) is -4
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[ceil、ceilf、ceill](ceil-ceilf-ceill.md)<br/>
[floor、floorf、floorl](floor-floorf-floorl.md)<br/>
[fmod、fmodf](fmod-fmodf.md)<br/>
[lrint、lrintf、lrintl、llrint、llrintf、llrintl](lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)<br/>
[round、roundf、roundl](round-roundf-roundl.md)<br/>
[nearbyint、nearbyintf、nearbyintl](nearbyint-nearbyintf-nearbyintl1.md)<br/>
[rint、rintf、rintl](rint-rintf-rintl.md)<br/>
