---
title: feupdateenv
ms.date: 04/05/2018
api_name:
- feupdateenv
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
api_type:
- HeaderDef
f1_keywords:
- feupdateenv
- fenv/feupdateenv
helpviewer_keywords:
- feupdateenv function
ms.assetid: 3d170042-dfd5-4e4f-a55f-038cf2296cc9
ms.openlocfilehash: 8f40cab42e4a89b1fc5a100587b11b0e2aeeb55c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940989"
---
# <a name="feupdateenv"></a>feupdateenv

現在発生している浮動小数点例外を保存し、指定した浮動小数点環境状態を復元し、保存されている浮動小数点例外を発生させます。

## <a name="syntax"></a>構文

```C
int feupdateenv(
   const fenv_t* penv
);
```

### <a name="parameters"></a>パラメーター

*ペン v*<br/>
[Fegetenv](fegetenv1.md)または[feholdexcept](feholdexcept2.md)の呼び出しによって設定された浮動小数点環境を含む**fenv_t**オブジェクトへのポインター。 また、FE_DFL_ENV マクロを使用して、既定のスタートアップ浮動小数点環境を指定することもできます。

## <a name="return-value"></a>戻り値

すべてのアクションが正常に完了した場合は、0 を返します。 それ以外の場合は、0 以外の値を返します。

## <a name="remarks"></a>Remarks

**Feupdateenv**関数は、複数のアクションを実行します。 まず、現在発生している浮動小数点例外状態フラグを自動ストレージに格納します。 次に、 **fenv_t**が指すオブジェクトに格納されている値から現在の浮動小数点環境を設定*します。* **FE_DFL_ENV**が*ない場合、または有効*な**fenv_t**オブジェクトを指していない場合、後続の動作は未定義になります。 最後に、 **feupdateenv**はローカルに格納された浮動小数点例外を発生させます。

この関数を使用するには、呼び出しの前に `#pragma fenv_access(on)` ディレクティブを使用してアクセスを妨げる可能性のある浮動小数点の最適化をオフにする必要があります。 詳細については、「 [fenv_access](../../preprocessor/fenv-access.md)」を参照してください。

## <a name="requirements"></a>必要条件

|関数|C ヘッダー|C++ ヘッダー|
|--------------|--------------|------------------|
|**feupdateenv**|\<fenv.h>|\<cfenv>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
