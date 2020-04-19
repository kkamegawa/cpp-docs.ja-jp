---
title: isfinite、_finite、_finitef
ms.date: 01/31/2019
api_name:
- _finite
- _finitef
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- isfinite
- finite
- _finite
- _finitef
- math/isfinite
- math/_finite
- math/_finitef
- float/_finite
helpviewer_keywords:
- finite function
- _finite function
- _finitef function
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
ms.openlocfilehash: a2cde4d3a57884413f0c48aa299b171334c5f988
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957178"
---
# <a name="isfinite-_finite-_finitef"></a>isfinite、_finite、_finitef

浮動小数点値が有限かどうかを決定します。

## <a name="syntax"></a>構文

```C
int isfinite(
   /* floating-point */ x
); /* C-only macro */

template <class FloatingType>
inline bool isfinite(
   FloatingType x
) throw(); /* C++-only template function */

int _finite(
   double x
);

int _finitef(
   float x
); /* x64 and ARM/ARM64 only */
```

### <a name="parameters"></a>パラメーター

*x*<br/>
テストする浮動小数点値。

## <a name="return-value"></a>戻り値

X が normal または`_finitef` subnormal の有限値の場合、 `_finite` `isfinite`マクロと関数および関数は0以外の値を返します。 引数が無限または NaN の場合は、0を返します。 インラインC++テンプレート関数`isfinite`は同じように動作しますが、 **true**または**false**を返します。

## <a name="remarks"></a>Remarks

`isfinite`は、C としてコンパイルされた場合はマクロであり、 C++としてコンパイルされた場合はインラインテンプレート関数です。 関数`_finite` と`_finitef`関数は、Microsoft 固有の関数です。 `_finitef` 関数は、x86、ARM、または ARM64 プラットフォーム用にコンパイルするときにのみ使用できます。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー (C)|必須ヘッダー (C++)|
|--------------|---------------------------|-------------------------------|
|`_finite`|\<float.h> または \<math.h>|\<float.h>、\<math.h>、\<cfloat>、または \<cmath>|
|`isfinite`, `_finitef`|\<math.h>|\<math.h> または \<cmath>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[fpclassify](fpclassify.md)<br/>
[_fpclass、_fpclassf](fpclass-fpclassf.md)<br/>
[isinf](isinf.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[isnormal](isnormal.md)<br/>
