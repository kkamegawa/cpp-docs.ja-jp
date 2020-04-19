---
title: div、ldiv、lldiv
ms.date: 04/05/2018
api_name:
- div
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
- api-ms-win-crt-utility-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- div
helpviewer_keywords:
- div function
- quotients, computing
- quotients
- dividing integers
- remainder computing
ms.assetid: 8ae80d97-54fd-499e-b14c-e30993b58119
ms.openlocfilehash: 5b40fa0c4cc9cdf0c0de0f6af21da04b0c70369f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70937697"
---
# <a name="div-ldiv-lldiv"></a>div、ldiv、lldiv

2 つの整数値の商と剰余を計算します。

## <a name="syntax"></a>構文

```C
div_t div(
   int numer,
   int denom
);
ldiv_t ldiv(
   long numer,
   long denom
);
lldiv_t lldiv(
   long long numer,
   long long denom
);
```

```cpp
ldiv_t div(
   long numer,
   long denom
); /* C++ only */
lldiv_t div(
   long long numer,
   long long denom
); /* C++ only */
```

### <a name="parameters"></a>パラメーター

*数値*<br/>
分子。

*デ om*<br/>
分母。

## <a name="return-value"></a>戻り値

**int**型の引数を使用して呼び出された**div**は、商と剰余で構成される**div_t**型の構造体を返します。 **Long**型の引数を持つ戻り値は**ldiv_t**であり、 **long** **long**型の引数を持つ戻り値は**lldiv_t**です。 **div_t**、 **ldiv_t**、および**lldiv_t**は、stdlib.h> \<> で定義されています。

## <a name="remarks"></a>Remarks

**Div**関数は、*数値*を*デ om*によって除算し、商と剰余を計算します。 [Div_t](../../c-runtime-library/standard-types.md)構造体には、商、 **quot**、剰余、 **rem**が含まれています。商の符号は、数学的な商の符号と同じです。 この絶対値が最も大きい整数であり、商の絶対値よりも小さくなります。 分母が 0 の場合、プログラムはエラー メッセージにより終了します。

**Long** **型または long** **long**型の引数を受け取るC++ **div**のオーバーロードは、コードでのみ使用できます。 戻り値の[型 ldiv_t](../../c-runtime-library/standard-types.md)と[lldiv_t](../../c-runtime-library/standard-types.md)には、 **div_t**のメンバーと同じ意味を持つメンバー **quot**と**rem**が含まれています。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**div**、 **ldiv**、 **lldiv**|\<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_div.c
// arguments: 876 13

// This example takes two integers as command-line
// arguments and displays the results of the integer
// division. This program accepts two arguments on the
// command line following the program name, then calls
// div to divide the first argument by the second.
// Finally, it prints the structure members quot and rem.
//

#include <stdlib.h>
#include <stdio.h>
#include <math.h>

int main( int argc, char *argv[] )
{
   int x,y;
   div_t div_result;

   x = atoi( argv[1] );
   y = atoi( argv[2] );

   printf( "x is %d, y is %d\n", x, y );
   div_result = div( x, y );
   printf( "The quotient is %d, and the remainder is %d\n",
           div_result.quot, div_result.rem );
}
```

```Output
x is 876, y is 13
The quotient is 67, and the remainder is 5
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[ldiv、lldiv](ldiv-lldiv.md)<br/>
[imaxdiv](imaxdiv.md)<br/>
