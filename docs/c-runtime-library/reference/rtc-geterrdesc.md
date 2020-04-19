---
title: _RTC_GetErrDesc
ms.date: 11/04/2016
api_name:
- _RTC_GetErrDesc
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
- RTC_GetErrDesc
- _RTC_GetErrDesc
helpviewer_keywords:
- run-time errors
- _RTC_GetErrDesc function
- RTC_GetErrDesc function
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
ms.openlocfilehash: 7174e9242b77a904df817886df4f8c763e3e0b2c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949054"
---
# <a name="_rtc_geterrdesc"></a>_RTC_GetErrDesc

実行時エラー チェック (RTC) の種類に関する簡単な説明を返します。

## <a name="syntax"></a>構文

```C
const char * _RTC_GetErrDesc(
   _RTC_ErrorNumber errnum
);
```

### <a name="parameters"></a>パラメーター

*errnum*<br/>
0 から **_RTC_NumErrors**によって戻される値より 1 少ない値までの範囲の数値。

## <a name="return-value"></a>戻り値

実行時エラー チェック システムによって検出されたエラーの 1 つの種類に関する簡単な説明が含まれている文字列。 エラーが 0[未満である](rtc-numerrors.md)か、または _RTC_GetErrDesc によって返された値以上である場合、は**NULL**を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_RTC_GetErrDesc**|\<rtcapi.h>|

詳細については、「[互換性](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>関連項目

[_RTC_NumErrors](rtc-numerrors.md)<br/>
[ランタイム エラー チェック](../../c-runtime-library/run-time-error-checking.md)<br/>
