---
title: _cabs
ms.date: 11/04/2016
api_name:
- _cabs
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
- cabsl
- _cabs
- _cabsl
helpviewer_keywords:
- cabs function
- cabsl function
- absolute values
- _cabsl function
- _cabs function
- calculating absolute values
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
ms.openlocfilehash: 5e2536fbeed2f466d3795e2ed26e643279e8bc67
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943412"
---
# <a name="_cabs"></a>_cabs

複素数の絶対値を計算します。

## <a name="syntax"></a>構文

```C
double _cabs(
   struct _complex z
);
```

### <a name="parameters"></a>パラメーター

*z*<br/>
複素数。

## <a name="return-value"></a>戻り値

cab が成功した場合、その引数の絶対値が返されます **(_t)** 。 オーバーフロー時に**は、** **HUGE_VAL**が返され、 **errno**が**ERANGE**に設定されます。 エラー処理は [_matherr](matherr.md) で変更できます。

## <a name="remarks"></a>Remarks

**Cab**関数は、複素数の絶対値を計算します。この値は[、complex 型](../../c-runtime-library/standard-types.md)の構造体である必要があります。 構造体*z*は、実際のコンポーネント*x*と虚数成分*y*で構成されています。 **Cab**を呼び出すと、式`sqrt( z.x * z.x + z.y * z.y )`の値と等価の値が生成されます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_cabs**|\<math.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_cabs.c
// Using _cabs, this program calculates
// the absolute value of a complex number.

#include <math.h>
#include <stdio.h>

int main( void )
{
   struct _complex number = { 3.0, 4.0 };
   double d;

   d = _cabs( number );
   printf( "The absolute value of %f + %fi is %f\n",
           number.x, number.y, d );
}
```

```Output
The absolute value of 3.000000 + 4.000000i is 5.000000
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[abs、labs、llabs、_abs64](abs-labs-llabs-abs64.md)<br/>
[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)