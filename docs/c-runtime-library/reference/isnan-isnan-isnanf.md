---
title: isnan、_isnan、_isnanf
ms.date: 01/31/2019
api_name:
- _isnan
- _isnanf
- isnan
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
- _isnan
- isnan
- math/isnan
- math/_isnan
- math/_isnanf
- _isnanf
helpviewer_keywords:
- NAN (not a number)
- _isnan function
- IEEE floating-point representation
- Not a Number (NANs)
- isnan function
ms.assetid: 391fbc5b-89a4-4fba-997e-68f1131caf82
ms.openlocfilehash: a0cc60fb80f8d5b78ec2947a87fde82a536b413c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953764"
---
# <a name="isnan-_isnan-_isnanf"></a>isnan、_isnan、_isnanf

浮動小数点値が非数 (NaN) かどうかをテストします。

## <a name="syntax"></a>構文

```C
int isnan(
   /* floating-point */ x
); /* C-only macro */

int _isnan(
   double x
);

int _isnanf(
   float x
); /* x64 only */

template <class T>
bool isnan(
   T x
) throw(); /* C++ only */
```

### <a name="parameters"></a>パラメーター

*x*<br/>
テストする浮動小数点値。

## <a name="return-value"></a>戻り値

C では、引数*x*が NAN の場合、 **isnan**マクロと **_isnan**および **_isnanf**関数は0以外の値を返します。それ以外の場合は0を返します。

でC++は、 **isnan**テンプレート関数は、引数*x*が NaN の場合に**true**を返します。それ以外の場合は**false**を返します。

## <a name="remarks"></a>Remarks

NaN 値は他の NaN 値と等しいとは比較されないため、これらの関数またはマクロのいずれかを使用して検出する必要があります。 浮動小数点演算の結果を、指定された型の IEEE-754 浮動小数点形式で表現できない場合、NaN が生成されます。 出力の NaN の表現方法については、「 [printf](printf-printf-l-wprintf-wprintf-l.md)」を参照してください。

としてC++コンパイルされた場合、 **isnan**マクロは定義されず、代わりに**isnan**テンプレート関数が定義されます。 マクロと同じように動作しますが、整数ではなく**bool**型の値を返します。

**_Isnan**関数と **_isnanf**関数は、Microsoft 固有の関数です。 **_Isnanf**関数は、x64 用にコンパイルされた場合にのみ使用できます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー (C)|必須ヘッダー (C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**、 **_isnanf**|\<math.h>|\<math.h> または \<cmath>|
|**_isnan**|\<float.h>|\<float.h> または \<cfloat>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite、_finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
