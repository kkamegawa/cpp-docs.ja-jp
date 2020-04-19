---
title: erf、erff、erfl、erfc、erfcf、erfcl
ms.date: 01/31/2019
api_name:
- erff
- erfl
- erf
- erfc
- erfcf
- erfcl
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
- erfl
- erf
- erff
- erfc
- erfcf
- erfcl
helpviewer_keywords:
- erfl function
- erff function
- erf function
- erfcl function
- erfcf function
- erfc function
ms.assetid: 144d90d3-e437-41c2-a659-cd57596023b5
ms.openlocfilehash: df724ed056c02d79b5b51f97ae4aaf8ae267fde5
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "70937616"
---
# <a name="erf-erff-erfl-erfc-erfcf-erfcl"></a>erf、erff、erfl、erfc、erfcf、erfcl

値の誤差関数または相補誤差関数を計算します。

## <a name="syntax"></a>構文

```C
double erf(
   double x
);
float erf(
   float x
); // C++ only
long double erf(
   long double x
); // C++ only
float erff(
   float x
);
long double erfl(
   long double x
);
double erfc(
   double x
);
float erfc(
   float x
); // C++ only
long double erfc(
   long double x
); // C++ only
float erfcf(
   float x
);
long double erfcl(
   long double x
);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点値。

## <a name="return-value"></a>戻り値

誤差**関数は、** *x*のガウス誤差 error 関数を返します。 **Erfc**関数は、 *x*の相補的なガウス誤差 error 関数を返します。

## <a name="remarks"></a>Remarks

誤差**関数は** *x*のガウス誤差 error 関数を計算します。これは次のように定義されています。

![X の error 関数](media/crt_erf_formula.PNG "x の誤差関数")

相補的なガウス誤差 error 関数は、1-誤差 (x) として定義されています。 -1.0 ~ 1.0 の範囲の値が**返されます**。 エラーの戻り値はありません。 **Erfc**関数は、0 ~ 2 の範囲の値を返します。 *X*が**erfc**に対して大きすぎる場合、 **errno**変数は**ERANGE**に設定されます。

でC++はオーバーロードが可能であるため、 **float**型および**long** **double**型を受け取って返す**erfc** **のオーバーロード**を呼び出すことができます。 C プログラムでは、 **erfc**は常に**double**を**受け取り、返し**ます。

## <a name="requirements"></a>［要件］

|機能|必須ヘッダー|
|--------------|---------------------|
|erfc、 **erff**、 **erff**、、 **erfcf**、 **erff**|\<math.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
