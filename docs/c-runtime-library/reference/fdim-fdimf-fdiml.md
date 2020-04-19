---
title: fdim、fdimf、fdiml
ms.date: 04/05/2018
api_name:
- fdim
- fdimf
- fdiml
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
- fdim
- fdimf
- fdiml
- math/fdim
- math/fdimf
- math/fdiml
helpviewer_keywords:
- fdim function
- fdimf function
- fdiml function
ms.assetid: 2d4ac639-51e9-462d-84ab-fb03b06971a0
ms.openlocfilehash: 74935f724b678b08e39604d9916c7c5de5925aee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941301"
---
# <a name="fdim-fdimf-fdiml"></a>fdim、fdimf、fdiml

1 番目と 2 番目の値の間の正の値の差を求めます。

## <a name="syntax"></a>構文

```C
double fdim(
   double x,
   double y
);

float fdim(
   float x,
   float y
); //C++ only

long double fdim(
   long double x,
   long double y
); //C++ only

float fdimf(
   float x,
   float y
);

long double fdiml(
   long double x,
   long double y
);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
最初の値。

*y*<br/>
2 番目の値。

## <a name="return-value"></a>戻り値

*X*と*y*の間の正の差を返します。

|戻り値|シナリオ|
|------------------|--------------|
|x-y|x > y の場合|
|0|x <= y の場合|

それ以外の場合は、次のエラーのいずれかを返すことがあります。

|問題|Return|
|-----------|------------|
|オーバーフロー範囲エラー|+HUGE_VAL、+HUGE_VALF、または +HUGE_VALL|
|アンダーフロー範囲エラー|丸めた後の正確な値|
|*x*または*y*が NaN|NaN|

エラーは、[_matherr](matherr.md) で指定されたとおりに報告されます。

## <a name="remarks"></a>Remarks

オーバー ロードを呼び出すことができますので、C++ ではオーバー ロード、 **fdim** を受け取って返す **float**と**long** **double**型。 C プログラムでは、 **fdim**は常に**double**を取得し、double を返します。

NaN の処理を除き、この関数はと同じ`fmax(x - y, 0)`です。

## <a name="requirements"></a>必要条件

|関数|C ヘッダー|C++ ヘッダー|
|--------------|--------------|------------------|
|**fdim**、 **fdimf**、 **fdiml**|\<math.h>|\<cmath>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[fmax、fmaxf、fmaxl](fmax-fmaxf-fmaxl.md)<br/>
[abs、labs、llabs、_abs64](abs-labs-llabs-abs64.md)<br/>
