---
title: fma、fmaf、fmal
ms.date: 04/05/2018
api_name:
- fma
- fmaf
- fmal
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
- fma
- fmaf
- fmal
- math/fma
- math/fmaf
- math/fmal
helpviewer_keywords:
- fma function
- fmaf function
- fmal function
ms.assetid: 584a6037-da1e-4e86-9f0c-97aae86de0c0
ms.openlocfilehash: 4ddc4061e5a24ee3b5176aedc569d134d85e0002
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957102"
---
# <a name="fma-fmaf-fmal"></a>fma、fmaf、fmal

2 つの値を乗算、3 番目の値を追加し、結果を丸めます。中間丸め処理による精度の低下はありません。

## <a name="syntax"></a>構文

```C
double fma(
   double x,
   double y,
   double z
);

float fma(
   float  x,
   float  y,
   float z
); //C++ only

long double fma(
   long double  x,
   long double  y,
   long double z
); //C++ only

float fmaf(
   float  x,
   float  y,
   float z
);

long double fmal(
   long double  x,
   long double  y,
   long double z
);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
乗算する 1 番目の値。

*y*<br/>
乗算する 2 番目の値。

*z*<br/>
加算する値。

## <a name="return-value"></a>戻り値

`(x * y) + z` を返します。 さらに戻り値は、現在の丸めの形式を使用して丸められます。

それ以外の場合は、次の値のいずれかを返します。

|問題|Return|
|-----------|------------|
|*x* = 無限大、 *y* = 0 または<br /><br /> *x* = 0、 *y* = 無限大|NaN|
|*x*または*y* = 正確な±無限大、 *z* = 無限大と逆の符号|NaN|
|*x*または*y* = NaN|NaN|
|not (*x* = 0、 *y*= 不定)、 *z* = NaN<br /><br /> not (*x*= 不定, *y*= 0) および*z* = NaN|NaN|
|オーバーフロー範囲エラー|± HUGE_VAL、± HUGE_VALF、または± HUGE_VALL|
|アンダーフロー範囲エラー|丸めた後の正確な値。|

エラーは、[_matherr](matherr.md) で指定されたとおりに報告されます。

## <a name="remarks"></a>Remarks

でC++はオーバーロードが可能であるため、**浮動小数点**型および**long** **double**型を受け取って返す**fma**のオーバーロードを呼び出すことができます。 C プログラムでは、 **fma**は常に**倍精度浮動小数点数**を取得し、double を返します。

この関数は、値を無限の精度とするかのように計算し、最終的な結果を丸めます。

## <a name="requirements"></a>必要条件

|関数|C ヘッダー|C++ ヘッダー|
|--------------|--------------|------------------|
|**fma**、 **fmaf**、 **fマル**|\<math.h>|\<cmath>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[remainder、remainderf、remainderl](remainder-remainderf-remainderl.md)<br/>
[remquo、remquof、remquol](remquo-remquof-remquol.md)<br/>
