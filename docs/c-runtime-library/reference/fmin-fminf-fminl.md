---
title: fmin、fminf、fminl
ms.date: 04/05/2018
api_name:
- fmin
- fminf
- fminl
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
- fmin
- fminf
- fminl
- math/fmin
- math/fminf
- math/fminl
helpviewer_keywords:
- fmin function
- fminf function
- fminl function
ms.assetid: 1916dfb5-99c1-4b0d-aefb-513525c3f2ac
ms.openlocfilehash: df01f2205291920b8c0519db622c93048278beb1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957087"
---
# <a name="fmin-fminf-fminl"></a>fmin、fminf、fminl

指定された 2 つの値のうち、小さい方を特定します。

## <a name="syntax"></a>構文

```C
double fmin(
   double x,
   double y
);

float fmin(
   float x,
   float y
); //C++ only

long double fmin(
   long double x,
   long double y
); //C++ only

float fminf(
   float x,
   float y
);

long double fminl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
比較する最初の値です。

*y*<br/>
比較する 2 番目の値です。

## <a name="return-value"></a>戻り値

成功した場合、 *x*または*y*の小さい方を返します。

|入力|結果|
|-----------|------------|
|*x*は NaN|*y*|
|*y*は NaN|*x*|
|*x*と*y*は NaN|NaN|

関数は、 [_matherr](matherr.md)が呼び出されず、浮動小数点例外が発生することも、 **errno**の値を変更することもありません。

## <a name="remarks"></a>Remarks

オーバー ロードを呼び出すことができますので、C++ ではオーバー ロード、 **fmin**を受け取って返す**float**と**long** **double**型。 C プログラムでは、 **fmin**は常に**double**を取得し、double を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**fmin**、 **fminf**、 **fminl**|C: \<math.h><br />C++: \<math.h> または \<cmath>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[fmax、fmaxf、fmaxl](fmax-fmaxf-fmaxl.md)<br/>
