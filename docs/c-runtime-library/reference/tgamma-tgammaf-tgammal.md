---
title: tgamma、tgammaf、tgammal
ms.date: 04/05/2018
api_name:
- tgamma
- tgammaf
- tgammal
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
- tgamma
- tgammaf
- tgammal
- math/tgamma
- math/tgammaf
- math/tgammal
helpviewer_keywords:
- tgamma function
- tgammaf function
- tgammal function
ms.assetid: f1bd2681-8af2-48a9-919d-5358fd068acd
ms.openlocfilehash: 02926fa49bbabeb9cf532f53cfa6e30a77805e70
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946208"
---
# <a name="tgamma-tgammaf-tgammal"></a>tgamma、tgammaf、tgammal

指定した値のガンマ関数を決定します。

## <a name="syntax"></a>構文

```C
double tgamma(
   double x
);

float tgamma(
   float x
); //C++ only

long double tgamma(
   long double x
); //C++ only

float tgammaf(
   float x
);

long double tgammal(
   long double x
);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
ガンマを検索する値。

## <a name="return-value"></a>戻り値

成功した場合は、 *x*のガンマを返します。

*X*の大きさがデータ型に対して大きすぎるか小さすぎる場合、範囲エラーが発生することがあります。 *X* < = 0 の場合は、ドメインエラーまたは範囲エラーが発生する可能性があります。

|問題|Return|
|-----------|------------|
|x = ±0|±無限大|
|x = 負の整数|NaN|
|x =-無限大|NaN|
|x = +INFINITY|+INFINITY|
|x = NaN|NaN|
|ドメイン エラー|NaN|
|極エラー|± HUGE_VAL、± HUGE_VALF、または± HUGE_VALL|
|オーバーフロー範囲エラー|± HUGE_VAL、± HUGE_VALF、または± HUGE_VALL|
|アンダーフロー範囲エラー|丸めた後の正確な値。|

エラーは、[_matherr](matherr.md) で指定されたとおりに報告されます。

## <a name="remarks"></a>Remarks

オーバー ロードを呼び出すことができますので、C++ ではオーバー ロード、 **tgamma**を受け取って返す**float**と**long** **double**型。 C プログラムでは、 **tgamma**は常に**double**を取得し、double を返します。

x が自然数の場合、この関数は (x-1) の階乗を返します。

## <a name="requirements"></a>必要条件

|関数|C ヘッダー|C++ ヘッダー|
|--------------|--------------|------------------|
|**tgamma**、 **tgammaf**、 **tgammal**|\<math.h>|\<cmath>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[lgamma、lgammaf、lgammal](lgamma-lgammaf-lgammal.md)<br/>
