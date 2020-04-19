---
title: cbrt、cbrtf、cbrtl
ms.date: 04/05/2018
api_name:
- cbrt
- cbrtf
- cbrtl
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
- cbrtl
- cbrt
- cbrtf
helpviewer_keywords:
- cbrtl function
- cbrtf function
- cbrt function
ms.assetid: ab51d916-3db2-4beb-b46a-28b4062cd33f
ms.openlocfilehash: d3983c5d3237b1a6cb82887a690919cbf21401ab
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939290"
---
# <a name="cbrt-cbrtf-cbrtl"></a>cbrt、cbrtf、cbrtl

立方根を計算します。

## <a name="syntax"></a>構文

```C
double cbrt(
   double x
);
float cbrt(
   float x
);  // C++ only
long double cbrt(
   long double x
);  // C++ only
float cbrtf(
   float x
);
long double cbrtl(
   long double x
);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点値

## <a name="return-value"></a>戻り値

**Cbrt**関数は、 *x*の cube ルートを返します。

|入力|SEH 例外|**_matherr**例外的|
|-----------|-------------------|--------------------------|
|± ∞、QNAN、IND|none|none|

## <a name="remarks"></a>Remarks

でC++はオーバーロードが可能であるため、 **float**型または**long** **double**型を受け取る**cbrt**のオーバーロードを呼び出すことができます。 C プログラムでは、 **cbrt**は常にを受け取り、 **double**を返します。

## <a name="requirements"></a>必要条件

|関数|C ヘッダー|C++ ヘッダー|
|--------------|--------------|------------------|
|**cbrt**、 **cbrtf**、 **cbrtf**|\<math.h>|\<cmath>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_cbrt.c
// Compile using: cl /W4 crt_cbrt.c
// This program calculates a cube root.

#include <math.h>
#include <stdio.h>

int main( void )
{
   double question = -64.64;
   double answer;

   answer = cbrt(question);
   printf("The cube root of %.2f is %.6f\n", question, answer);
}
```

```Output
The cube root of -64.64 is -4.013289
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[exp、expf、expl](exp-expf.md)<br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md)<br/>
[pow、powf、powl](pow-powf-powl.md)<br/>
