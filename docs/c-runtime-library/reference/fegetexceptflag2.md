---
title: fegetexceptflag
ms.date: 04/05/2018
api_name:
- fegetexceptflag
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
- fegetexceptflag
- fenv/fegetexceptflag
helpviewer_keywords:
- fegetexceptflag function
ms.assetid: 2d28f0ca-70c9-4cff-be8b-3d876eacde71
ms.openlocfilehash: b840408ce704ad5519fbf233de41c8d5422006ad
ms.sourcegitcommit: ba4180a2d79d7e391f2f705797505d4aedbc2a5e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2020
ms.locfileid: "76972186"
---
# <a name="fegetexceptflag"></a>fegetexceptflag

指定した浮動小数点例外フラグの現在の状態を格納します。

## <a name="syntax"></a>構文

```C
int fegetexceptflag(
   fexcept_t* pstatus,
   int excepts
);
```

### <a name="parameters"></a>パラメーター

*pstatus*<br/>
*Removed*によって指定された例外フラグの現在の値を格納する**fexcept_t**オブジェクトへのポインター。

*removed*<br/>
*Pstatus*に格納する浮動小数点例外フラグ。

## <a name="return-value"></a>戻り値

成功した場合は 0 を返します。 それ以外の場合は、0 以外の値を返します。

## <a name="remarks"></a>コメント

**Fegetexceptflag**関数は、 *pstatus*が指す**fexcept_t**オブジェクト内の*removed*で指定された浮動小数点例外状態フラグの現在の状態を格納します。  *pstatus*は有効な**fexcept_t**オブジェクトを指している必要があります。それ以降の動作は未定義です。 **Fegetexceptflag**関数は、次の例外マクロをサポートしています。これらのマクロは \<fenv.h> > で定義されています。

|例外処理マクロ|説明|
|---------------------|-----------------|
|FE_DIVBYZERO|前の浮動小数点演算で特異点エラーまたは極エラーが発生しました。無限大の値が作成されました。|
|FE_INEXACT|前の浮動小数点演算の格納結果は強制的に丸められました。|
|FE_INVALID|前の浮動小数点演算でドメイン エラーが発生しました。|
|FE_OVERFLOW|範囲エラーが発生しました。前の浮動小数点演算結果は大きすぎて表現できませんでした。|
|FE_UNDERFLOW|前の浮動小数点演算結果は小さすぎて最大有効桁数で表現できませんでした。|
|FE_ALL_EXCEPT|すべてのサポートされる浮動小数点例外のビット演算 OR。|

*Removed*引数には、0、サポートされている浮動小数点例外マクロの1つ、または2つ以上のマクロのビットごとの or を指定できます。 他の引数値の結果は未定義です。

この関数を使用するには、呼び出しの前に `#pragma fenv_access(on)` ディレクティブを使用してアクセスを妨げる可能性のある浮動小数点の最適化をオフにする必要があります。 詳細については、「 [fenv_access](../../preprocessor/fenv-access.md)」を参照してください。

## <a name="requirements"></a>要件

|関数|C ヘッダー|C++ ヘッダー|
|--------------|--------------|------------------|
|**fegetexceptflag**|\<fenv.h>|\<cfenv>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
