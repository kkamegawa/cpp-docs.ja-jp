---
title: fegetenv
ms.date: 04/05/2018
api_name:
- fetegenv
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fegetenv
- fenv/fegetenv
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
ms.openlocfilehash: b2e3566eb96174d0f0ccd6beb401824cc052c995
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941241"
---
# <a name="fegetenv"></a>fegetenv

指定したオブジェクトの現在の浮動小数点環境を格納します。

## <a name="syntax"></a>構文

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>パラメーター

*ペン v*<br/>
現在の浮動小数点環境値を格納する**fenv_t**オブジェクトへのポインター。

## <a name="return-value"></a>戻り値

浮動小数点環境が参照*v*に正常に格納された場合は0を返します。 それ以外の場合は、0 以外の値を返します。

## <a name="remarks"></a>Remarks

**Fegetenv**関数は、現在の浮動小数点環境を、参照によって指されるオブジェクトに*格納します*。 浮動小数点環境とは、浮動小数点計算に影響する一連の状態フラグと制御モードです。 浮動小数点例外の丸め方向モードと状態フラグが含まれます。  Fenv_t*が有効*なオブジェクトを指していない場合、後続の動作は定義されません。

この関数を使用するには、呼び出しの前に `#pragma fenv_access(on)` ディレクティブを使用してアクセスを妨げる可能性のある浮動小数点の最適化をオフにする必要があります。 詳細については、「 [fenv_access](../../preprocessor/fenv-access.md)」を参照してください。

## <a name="requirements"></a>必要条件

|関数|C ヘッダー|C++ ヘッダー|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
