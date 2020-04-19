---
title: catan、catanf、catanl
ms.date: 11/04/2016
api_name:
- catan
- catanf
- catanl
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
- catan
- catanf
- catanl
- complex/catan
- complex/catanf
- complex/catanl
helpviewer_keywords:
- catan function
- catanf function
- catanl function
ms.assetid: 8415ed9c-7909-4d08-b532-4630bafdc7e8
ms.openlocfilehash: 204a05b4293fefa4378e54ce93a625bf890cf4d5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943360"
---
# <a name="catan-catanf-catanl"></a>catan、catanf、catanl

虚数軸に沿って区間 [-1; + 1] の外側にある分岐カットを使用して、複素数のアークタンジェントを取得します。

## <a name="syntax"></a>構文

```C
_Dcomplex catan( _Dcomplex z );
_Fcomplex catanf( _Fcomplex z );
_Lcomplex catanl( _Lcomplex z );
```

```cpp
_Fcomplex catan( _Fcomplex z );  // C++ only
_Lcomplex catan( _Lcomplex z );  // C++ only
```

### <a name="parameters"></a>パラメーター

*z*<br/>
角度をラジアンで表す複素数。

## <a name="return-value"></a>戻り値

*Z*のアークタンジェント (ラジアン)。 結果は、虚数軸に沿って、実際の軸に沿って [-π/2; + π/2] の間隔で無制限になります。

## <a name="remarks"></a>Remarks

でC++はオーバーロードが可能であるため、 **_Fcomplex**と **_Lcomplex**の値を受け取って返す**catan**のオーバーロードを呼び出すことができます。 C プログラムでは、 **catan**は常にを受け取り、**戻り値を**返します。

## <a name="requirements"></a>必要条件

|ルーチン|C ヘッダー|C++ ヘッダー|
|-------------|--------------|------------------|
|**catan**、 **catanf**、 **catanl**|\<complex.h>|\<ccomplex>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[catanh、catanhf、catanhl](catanh-catanhf-catanhl.md)<br/>
[ctanh、ctanhf、ctanhl](ctanh-ctanhf-ctanhl.md)<br/>
[csinh、csinhf、csinhl](csinh-csinhf-csinhl.md)<br/>
[casinh、casinhf、casinhl](casinh-casinhf-casinhl.md)<br/>
[ccosh、ccoshf、ccoshl](ccosh-ccoshf-ccoshl.md)<br/>
[cacosh、cacoshf、cacoshl](cacosh-cacoshf-cacoshl.md)<br/>
[cacos、cacosf、cacosl](cacos-cacosf-cacosl.md)<br/>
[ctan、ctanf、ctanl](ctan-ctanf-ctanl.md)<br/>
[csin、csinf、csinl](csin-csinf-csinl.md)<br/>
[casin、casinf、casinl](casin-casinf-casinl.md)<br/>
[ccos、ccosf、ccosl](ccos-ccosf-ccosl.md)<br/>
[csqrt、csqrtf、csqrtl](csqrt-csqrtf-csqrtl.md)<br/>
