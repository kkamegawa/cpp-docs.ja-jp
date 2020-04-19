---
title: _RTC_NumErrors
ms.date: 11/04/2016
api_name:
- _RTC_NumErrors
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
- DLLExport
topic_type:
- apiref
f1_keywords:
- _RTC_NumErrors
- RTC_NumErrors
helpviewer_keywords:
- run-time errors
- _RTC_NumErrors function
- RTC_NumErrors function
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
ms.openlocfilehash: 72056208ca6d714f788ae325b90786f5be4ab443
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949031"
---
# <a name="_rtc_numerrors"></a>_RTC_NumErrors

実行時エラー チェック (RTC) で検出できるエラーの合計数を返します。 この数値は **for** ループを制御するために使用し、ループ内では各値を [_RTC_GetErrDesc](rtc-geterrdesc.md) に渡すことができます。

## <a name="syntax"></a>構文

```C

int _RTC_NumErrors( void );
```

## <a name="return-value"></a>戻り値

Visual C++ の実行時エラー チェックで検出できるエラーの合計数を表す値を持つ整数。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_RTC_NumErrors**|\<rtcapi.h>|

詳細については、「[互換性](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>関連項目

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[ランタイム エラー チェック](../../c-runtime-library/run-time-error-checking.md)<br/>
