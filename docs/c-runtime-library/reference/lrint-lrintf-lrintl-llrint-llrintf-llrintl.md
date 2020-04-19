---
title: lrint、lrintf、lrintl、llrint、llrintf、llrintl
ms.date: 04/05/2018
api_name:
- lrint
- lrintl
- lrintf
- llrint
- llrintf
- llrintl
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
- lrint
- lrintf
- lrintl
- llrint
- llrintf
- llrintl
- math/lrint
- math/lrintf
- math/lrintl
- math/llrint
- math/llrintf
- math/llrintl
helpviewer_keywords:
- lrint function
- lrintf function
- lrintl function
- llrint function
- llrintf function
- llrintl function
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
ms.openlocfilehash: c7831842eb4d3c1eef9c4c9e83bbddb557cec0e3
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857750"
---
# <a name="lrint-lrintf-lrintl-llrint-llrintf-llrintl"></a>lrint、lrintf、lrintl、llrint、llrintf、llrintl

現在の丸めモードと方向を使用して、指定された浮動小数点値を最も近い整数値に丸めます。

## <a name="syntax"></a>構文

```C
long int lrint(
   double x
);

long int lrint(
   float x
); //C++ only

long int lrint(
   long double x
); //C++ only

long int lrintf(
   float x
);

long int lrintl(
   long double x
);

long long int llrint(
   double x
);

long long int llrint(
   float x
); //C++ only

long long int llrint(
   long double x
); //C++ only

long long int llrintf(
   float x
);

long long int llrintl(
   long double x
);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
丸める値。

## <a name="return-value"></a>戻り値

成功した場合は、 *x*の丸められた整数値を返します。

|問題|Return|
|-----------|------------|
|*x*が戻り値の型の範囲外です。<br /><br /> *x* = ±∞<br /><br /> *x* = NaN|**FE_INVALID**を発生させ、ゼロ (0) を返します。|

## <a name="remarks"></a>Remarks

でC++はオーバーロードが可能であるため、 **float**型および**long** **double**型を受け取る**lrint**と**llrint**のオーバーロードを呼び出すことができます。 C プログラムでは、 **lrint**と**llrint**は常に**double**を受け取ります。

*X*が整数値に相当する浮動小数点値を表さない場合、これらの関数は**FE_INEXACT**を発生させます。

**Microsoft 固有**: 結果が戻り値の型の範囲外の場合、またはパラメーターが NaN または無限大の場合、戻り値は実装定義になります。 Microsoft コンパイラは0 の値を返します。

## <a name="requirements"></a>要件

|機能|C ヘッダー|C++ ヘッダー|
|--------------|--------------|------------------|
|**lrint**、 **lrintf**、 **lrintl**、 **llrint**、 **llrintf**、 **llrintl**|\<math.h>|\<cmath>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>参照

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
