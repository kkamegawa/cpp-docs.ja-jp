---
title: expm1、expm1f、expm1l
ms.date: 04/05/2018
api_name:
- expm1l
- expm1
- expm1f
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
- expm1l
- expm1
- expm1f
helpviewer_keywords:
- expm1f function
- expm1l function
- expm1 function
ms.assetid: 2a4dd2d9-370c-42b0-9067-0625efa272e0
ms.openlocfilehash: 77bd44975e97cc646f7d2fd100d86b6661b8c2e9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941547"
---
# <a name="expm1-expm1f-expm1l"></a>expm1、expm1f、expm1l

e を底とする値のべき乗から 1 を引く計算を行います。

## <a name="syntax"></a>構文

```C
double expm1(
   double x
);
float expm1(
   float x
);  // C++ only
long double expm1(
   long double x
);  // C++ only
float expm1f(
   float x
);
long double expm1l(
   long double x
);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
浮動小数点の指数値。

## <a name="return-value"></a>戻り値

**Expm1**関数は、成功した場合は、e<sup>x</sup> -1 を表す浮動小数点値を返します。 オーバーフローでは、 **expm1**は**HUGE_VAL**を返し、 **expm1f**は**HUGE_VALF**を返し **、expm1l は**HUGE_VALL**を返し、** **errno**は**ERANGE**に設定されます。 リターン コードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

オーバー ロードを呼び出すことができますので、C++ ではオーバー ロード、 **expm1**を受け取って返す**float**と**long** **double**値。 C プログラムでは、 **expm1**は常に**double**を受け取り、返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**expm1**、 **expm1f**、 **expm1l**|\<math.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[exp2、exp2f、exp2l](exp2-exp2f-exp2l.md)<br/>
[pow、powf、powl](pow-powf-powl.md)<br/>
