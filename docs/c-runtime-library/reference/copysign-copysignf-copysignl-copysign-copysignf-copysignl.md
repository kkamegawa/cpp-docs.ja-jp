---
title: copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl
ms.date: 04/05/2018
api_name:
- copysignf
- copysignl
- _copysignl
- _copysign
- _copysignf
- copysign
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
- _copysignl
- copysign
- copysignf
- _copysign
- copysignl
- _copysignf
helpviewer_keywords:
- copysignl function
- _copysignl function
- copysign function
- _copysignf function
- _copysign function
- copysignf function
ms.assetid: 009216d6-72a2-402d-aa6c-91d924b2c9e4
ms.openlocfilehash: 1575f0863b56256513cf6a93cf7b63f3d921af57
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942853"
---
# <a name="copysign-copysignf-copysignl-_copysign-_copysignf-_copysignl"></a>copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl

ある引数の絶対値と別の引数の符号を持つ値を返します。

## <a name="syntax"></a>構文

```C
double copysign(
   double x,
   double y
);
float copysign(
   float x,
   float y
); // C++ only
long double copysign(
   long double x,
   long double y
); // C++ only
float copysignf(
   float x,
   float y
); // C++ only
long double copysignl(
   long double x,
   long double y
); // C++ only
double _copysign(
   double x,
   double y
);
long double _copysignl(
   long double x,
   long double y
);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
結果の絶対値として返される浮動小数点値。

*y*<br/>
結果の符号として返される浮動小数点値。

[浮動小数点サポート ルーチン](../../c-runtime-library/floating-point-support.md)

## <a name="return-value"></a>戻り値

**Copysign**関数は、 *x*の大きさと*y*の符号を組み合わせた浮動小数点値を返します。 エラーの戻り値はありません。

## <a name="remarks"></a>Remarks

でC++はオーバーロードが可能であるため、 **float**または**long** **double**値を受け取って返す**copysign**のオーバーロードを呼び出すことができます。 C プログラムでは、 **copysign**は常に、 **double**を取得して返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_copysign**|\<float.h>|
|**copysign**、 **copysignf**、 **copysignl**、 **_copysignf**、 **_copysignl**|\<math.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[fabs、fabsf、fabsl](fabs-fabsf-fabsl.md)<br/>
[_chgsign、_chgsignf、_chgsignl](chgsign-chgsignf-chgsignl.md)<br/>
