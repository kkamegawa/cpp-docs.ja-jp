---
title: pow、powf、powl
ms.date: 04/05/2018
api_name:
- powl
- pow
- powf
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
- powl
- pow
- _powl
- powf
helpviewer_keywords:
- exponential calculations
- powl function
- _powl function
- exponentiation
- powers, calculating
- calculating exponentials
- powf function
- pow function
ms.assetid: e75c33ed-2e59-48b1-be40-81da917324f1
ms.openlocfilehash: 863d2b76ec131670b10eefc086fa3485bd0a983d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950289"
---
# <a name="pow-powf-powl"></a>pow、powf、powl

*X*の累乗を*y*で計算します。

## <a name="syntax"></a>構文

```C
double pow( double x, double y );
float powf( float x, float y );
long double powl( long double x, long double y );
```

```cpp
double pow( double x, int y );  // C++ only
float pow( float x, float y );  // C++ only
float pow( float x, int y );  // C++ only
long double pow( long double x, long double y );  // C++ only
long double pow( long double x, int y );  // C++ only
```

### <a name="parameters"></a>パラメーター

*x*<br/>
底。

*y*<br/>
指数。

## <a name="return-value"></a>戻り値

*X*<sup>*y*</sup>の値を返します。 オーバーフローまたはアンダーフロー時に、エラー メッセージは印刷されません。

|x の値と y の値|pow の値を返す|
|-----------------------|-------------------------|
|*x* ! = 0.0 および*y* = = 0.0|1|
|*x* = = 0.0 および*y* = = 0.0|1|
|*x* = = 0.0 および*y* < 0|INF|

## <a name="remarks"></a>Remarks

**pow**は、2<sup>64</sup>を超える整数の浮動小数点値を認識しません (たとえば、1.0 e100)。

**pow**には、ストリーミング SIMD 拡張命令 2 (SSE2) を使用する実装があります。 SSE2 実装の使い方の詳細および制約については、「[_set_SSE2_enable](set-sse2-enable.md)」をご覧ください。

でC++はオーバーロードが可能であるため、 **pow**のさまざまなオーバーロードを呼び出すことができます。 C プログラムでは、 **pow**は常に2つの**double**値を受け取り、 **double**値を返します。

`pow(int, int)` オーバーロードは使用できなくなりました。 このオーバーロードを使用する場合、コンパイラは[C2668](../../error-messages/compiler-errors-2/compiler-error-c2668.md)を生成することがあります。 この問題を回避するには、最初のパラメーターを**double**、 **float**、または**long** **double**にキャストします。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー (C)|必須ヘッダー (C++)|
|-|-|-|
|**pow**、 **powf**、 **powl**|\<math.h>|\<math.h> または \<cmath>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_pow.c

#include <math.h>
#include <stdio.h>

int main( void )
{
   double x = 2.0, y = 3.0, z;

   z = pow( x, y );
   printf( "%.1f to the power of %.1f is %.1f\n", x, y, z );
}
```

```Output
2.0 to the power of 3.0 is 8.0
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md) <br/>
[exp、expf、expl](exp-expf.md) <br/>
[log、logf、log10、log10f](log-logf-log10-log10f.md) <br/>
[sqrt、sqrtf、sqrtl](sqrt-sqrtf-sqrtl.md) <br/>
[_CIpow](../../c-runtime-library/cipow.md)<br/>
