---
title: isnan、_isnan、_isnanf
ms.date: 01/31/2019
apiname:
- _isnan
- _isnanf
- isnan
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 8a907dd33803cebd7bc5d71789834d115333b6a0
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703091"
---
# <a name="isnan-isnan-isnanf"></a>isnan、_isnan、_isnanf

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

C では、 **isnan**マクロと **_isnan**と **_isnanf**関数が 0 以外の値を返す場合、引数*x* NAN は、それ以外の0 を返します。

C++ では、 **isnan**テンプレート関数を返します**true**場合、引数*x* ; nan を返しますそれ以外の場合**false**します。

## <a name="remarks"></a>Remarks

NaN 値をその他の NaN 値と同じ比較しません、ため、いずれかを検出するためにこれらの関数またはマクロのいずれかを使用する必要があります。 浮動小数点演算の結果を指定した型の IEEE 754 浮動小数点形式で表すことはできません、NaN が発生します。 出力の NaN が表現される方法の詳細については、次を参照してください。 [printf](printf-printf-l-wprintf-wprintf-l.md)します。

C++ としてコンパイルされるときに、 **isnan**マクロが定義されていないと**isnan**テンプレート関数は、代わりに定義されます。 型の値を返しますが、マクロと同様に動作**bool**整数ではなく。

**_Isnan**と **_isnanf**関数は、Microsoft に固有です。 **_Isnanf**関数は、x64 用にコンパイルされるときに使用できるのみです。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー (C)|必須ヘッダー (C++)|
|-------------|---------------------------|-------------------------------|
|**isnan**, **_isnanf**|\<math.h>|\<math.h> または \<cmath>|
|**_isnan**|\<float.h>|\<float.h> または \<cfloat>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isfinite _finite、_finitef](finite-finitef.md)<br/>
[isinf](isinf.md)<br/>
[isnormal](isnormal.md)<br/>
