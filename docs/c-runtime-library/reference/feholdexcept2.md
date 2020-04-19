---
title: feholdexcept
ms.date: 04/05/2018
api_name:
- feholdexcept
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
- feholdexcept
- fenv/feholdexcept
helpviewer_keywords:
- feholdexcept function
ms.assetid: 88e512ae-b5d8-452c-afe9-c824cd3ef1d8
ms.openlocfilehash: bd55a4ed627d731f7246d589d4b74b4173e31d4e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941186"
---
# <a name="feholdexcept"></a>feholdexcept

指定したオブジェクトに現在の浮動小数点環境を格納し、浮動小数点状態フラグをクリアし、可能であれば、浮動小数点環境を無停止モードにします。

## <a name="syntax"></a>構文

```C
int feholdexcept(
   fenv_t *penv
);
```

### <a name="parameters"></a>パラメーター

*ペン v*<br/>
浮動小数点環境のコピーを格納する**fenv_t**オブジェクトへのポインター。

## <a name="return-value"></a>戻り値

関数が非停止浮動小数点例外処理を正常に有効にできる場合にのみ、0を返します。

## <a name="remarks"></a>Remarks

Feholdexcept 関数は、現在の浮動小数点環境の状態を、が指す**fenv_t**オブジェクトに格納し *、浮動*小数点例外の実行を中断しないように環境を設定するために使用されます。 これは無停止モードと呼ばれます。  このモードは、[fesetenv](fesetenv1.md) または [feupdateenv](feupdateenv.md) を使用して環境が復元されるまで継続します。

この関数は、1 つまたは複数の浮動小数点例外を呼び出し元から隠す必要があるサブルーチンの開始時に使用できます。 例外を報告するには、 [feclearexcept](feclearexcept1.md)を使用して不要な例外をクリアし、 **feupdateenv**の呼び出しで非ストップモードを終了するだけです。

この関数を使用するには、呼び出しの前に `#pragma fenv_access(on)` ディレクティブを使用してアクセスを妨げる可能性のある浮動小数点の最適化をオフにする必要があります。 詳細については、「 [fenv_access](../../preprocessor/fenv-access.md)」を参照してください。

## <a name="requirements"></a>必要条件

|関数|C ヘッダー|C++ ヘッダー|
|--------------|--------------|------------------|
|**feholdexcept**|\<fenv.h>|\<cfenv>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[fesetenv](fesetenv1.md)<br/>
[feupdateenv](feupdateenv.md)<br/>
