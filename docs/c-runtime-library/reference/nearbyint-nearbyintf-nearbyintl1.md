---
title: nearbyint、nearbyintf、nearbyintl
ms.date: 04/05/2018
api_name:
- nearbyint
- nearbyintf
- nearbyintl
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
- nearbyint
- nearbyintf
- nearbyintl
- math/nearbyint
- math/narbyintf
- math/narbyintl
helpviewer_keywords:
- nearbyint function
- nearbyintf function
- nearbyintl function
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
ms.openlocfilehash: cd0a7d00c5019dd1e483d555df6db8d9770e61c1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951392"
---
# <a name="nearbyint-nearbyintf-nearbyintl"></a>nearbyint、nearbyintf、nearbyintl

指定の浮動小数点値を整数に丸め、浮動小数点形式でその値を返します。

## <a name="syntax"></a>構文

```C
double nearbyint( double x );
float nearbyintf( float x );
long double nearbyintl( long double x );
```

```cpp
float nearbyint( float x ); //C++ only
long double nearbyint( long double x ); //C++ only
```

### <a name="parameters"></a>パラメーター

*x*<br/>
丸める値。

## <a name="return-value"></a>戻り値

成功した場合は、 [fegetround](fegetround-fesetround2.md)によって報告される現在の丸め形式を使用して、最も近い整数に丸められた*x*を返します。 それ以外の場合は、関数から次の値のいずれかが返されます。

|問題|Return|
|-----------|------------|
|*x* = ±無限大|±無限大、未変更|
|*x* = ±0|±0、未変更|
|*x* = NaN|NaN|

エラーは[_matherr](matherr.md)によって報告されません。具体的には、この関数は**FE_INEXACT**例外を報告しません。

## <a name="remarks"></a>Remarks

この関数と[rint](rint-rintf-rintl.md)の主な違いは、この関数では、不正確な浮動小数点例外が発生しないことです。

浮動小数点の最大値は正確な整数であるため、この関数が単独でオーバーフローすることはありません。むしろ、使用する関数のバージョンによっては、出力で戻り値がオーバーフローすることがあります。

C++ では、オーバー ロードのオーバー ロードを呼び出すことができますので**nearbyint**を受け取って返す**float**または**long** **double**パラメーター。 C プログラムでは、 **nearbyint**は常に2つの double 値を受け取り、double 値を返します。

## <a name="requirements"></a>必要条件

|関数|C ヘッダー|C++ ヘッダー|
|--------------|--------------|------------------|
|**nearbyint**、 **nearbyintf**、 **nearbyintl**|\<math.h>|\<cmath> または \<math.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[数値演算と浮動小数点のサポート](../floating-point-support.md)<br/>
