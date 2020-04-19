---
title: ccos、ccosf、ccosl
ms.date: 11/04/2016
api_name:
- ccos
- ccosf
- ccosl
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
- ccos
- ccosf
- ccosl
- complex/ccos
- complex/ccosf
- complex/ccosl
helpviewer_keywords:
- ccos function
- ccosf function
- ccosl function
ms.assetid: 4ab936ac-ff85-49ac-9418-2b69cf5d4696
ms.openlocfilehash: 1d6acddf979b7488be722bd850fe9e16816d1030
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943182"
---
# <a name="ccos-ccosf-ccosl"></a>ccos、ccosf、ccosl

複素数のコサインを返します。

## <a name="syntax"></a>構文

```C
_Dcomplex ccos(
   _Dcomplex z
);
_Fcomplex ccos(
   _Fcomplex z
);  // C++ only
_Lcomplex ccos(
   _Lcomplex z
);  // C++ only
_Fcomplex ccosf(
   _Fcomplex z
);
_Lcomplex ccosl(
   _Lcomplex z
);
```

### <a name="parameters"></a>パラメーター

*z*<br/>
角度をラジアンで表す複素数。

## <a name="return-value"></a>戻り値

*Z*のコサイン (ラジアン)。

## <a name="remarks"></a>Remarks

でC++はオーバーロードが可能であるため、 **_Fcomplex**と **_Lcomplex**の値を受け取って返す**ccos**のオーバーロードを呼び出すことができます。 C プログラムでは、 **ccos**は常にを受け取り、**戻り値を**返します。

## <a name="requirements"></a>必要条件

|ルーチン|C ヘッダー|C++ ヘッダー|
|-------------|--------------|------------------|
|**ccos**、 **ccosf**、 **ccosl**|\<complex.h>|\<ccomplex>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[catanh、catanhf、catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh、ctanhf、ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[catan、catanf、catanl](catan-catanf-catanl.md)<br/>
[csinh、csinhf、csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh、casinhf、casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh、ccoshf、ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh、cacoshf、cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos、cacosf、cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan、ctanf、ctanl](ctan-ctanf-ctanl.md)<br/>
[csin、csinf、csinl](csin-csinf-csinl.md)<br/>
[casin、casinf、casinl](casin-casinf-casinl.md)<br/>
[csqrt、csqrtf、csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
