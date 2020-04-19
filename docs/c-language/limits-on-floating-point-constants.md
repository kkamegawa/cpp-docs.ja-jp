---
title: 浮動小数点定数の制限
ms.date: 11/04/2016
helpviewer_keywords:
- ranges, floating-point constants
- floating-point constants, limits
- FLOAT.H header file
- constants, floating-point
- limits, floating-point constants
- floating-point numbers, floating limits
ms.assetid: 2d975868-2af6-45d7-a8af-db79f2c6b67b
ms.openlocfilehash: df39ee719a4474f6dfd55d31a2848169a1168390
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148752"
---
# <a name="limits-on-floating-point-constants"></a>浮動小数点定数の制限

**Microsoft 固有の仕様**

浮動小数点定数の値に関する制限を次の表に示します。 ヘッダー ファイル FLOAT.H にこの情報が含まれています。

### <a name="limits-on-floating-point-constants"></a>浮動小数点定数の制限

|定数|説明|[値]|
|--------------|-------------|-----------|
|**FLT_DIG**<br />**DBL_DIG**<br />**LDBL_DIG**|*q* 桁の浮動小数点数を、有効桁数を失わずに丸めて浮動小数点表現にしたり、戻したりできる桁数 *q*。|6<br />16<br />16|
|**FLT_EPSILON**<br />**DBL_EPSILON**<br />**LDBL_EPSILON**|*x* + 1.0 が 1.0 に等しくならないような最小の正数 *x*|1.192092896e-07F<br />2.2204460492503131e-016<br />2.2204460492503131e-016|
|**FLT_GUARD**||0|
|**FLT_MANT_DIG**<br />**DBL_MANT_DIG**<br />**LDBL_MANT_DIG**|浮動小数点の有効桁で **FLT_RADIX** により指定された基数の桁数。 基数は 2 です。したがって、これらの値はビットを指定します。|24<br />53<br />53|
|**FLT_MAX**<br />**DBL_MAX**<br />**LDBL_MAX**|表現可能な最大浮動小数点数。|3.402823466e+38F<br />1.7976931348623158e+308<br />1.7976931348623158e+308|
|**FLT_MAX_10_EXP**<br />**DBL_MAX_10_EXP**<br />**LDBL_MAX_10_EXP**|10 をその数値分累乗した結果が表現可能な浮動小数点数となる最大の整数。|38<br />308<br />308|
|**FLT_MAX_EXP**<br />**DBL_MAX_EXP**<br />**LDBL_MAX_EXP**|**FLT_RADIX** をその数値分累乗した結果が表現可能な浮動小数点数となる最大の整数。|128<br />1024<br />1024|
|**FLT_MIN**<br />**DBL_MIN**<br />**LDBL_MIN**|正の最小数。|1.175494351e-38F<br />2.2250738585072014e-308<br />2.2250738585072014e-308|
|**FLT_MIN_10_EXP**<br />**DBL_MIN_10_EXP**<br />**LDBL_MIN_10_EXP**|10 をその数値分累乗した結果が表現可能な浮動小数点数となる最小の負の整数。|-37<br />-307<br />-307|
|**FLT_MIN_EXP**<br />**DBL_MIN_EXP**<br />**LDBL_MIN_EXP**|**FLT_RADIX** をその数値分累乗した結果が表現可能な浮動小数点数となる最小の負の整数。|-125<br />-1021<br />-1021|
|**FLT_NORMALIZE**||0|
|**FLT_RADIX**<br />**_DBL_RADIX**<br />**_LDBL_RADIX**|指数表記の基数。|2<br />2<br />2|
|**FLT_ROUNDS**<br />**_DBL_ROUNDS**<br />**_LDBL_ROUNDS**|浮動小数点加算の丸めモード。|1 (近接)<br />1 (近接)<br />1 (近接)|

上記の表の情報は、将来の実装では変わる可能性があることに注意してください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[C 浮動小数点定数](../c-language/c-floating-point-constants.md)
