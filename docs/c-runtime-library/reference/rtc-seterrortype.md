---
title: _RTC_SetErrorType
ms.date: 11/04/2016
api_name:
- _RTC_SetErrorType
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
- RTC_SetErrorType
- _RTC_SetErrorType
helpviewer_keywords:
- run-time errors
- RTC_SetErrorType function
- _RTC_SetErrorType function
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
ms.openlocfilehash: 6c1eff5920931aa3b72bf3dbc6232c371828b16a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948920"
---
# <a name="_rtc_seterrortype"></a>_RTC_SetErrorType

ランタイム エラー チェック (RTC) で検出されたエラーを特定の種類に関連付けます。 エラー ハンドラーは、指定した型のエラーを出力する方法を処理します。

## <a name="syntax"></a>構文

```C
int _RTC_SetErrorType(
   _RTC_ErrorNumber errnum,
   int ErrType
);
```

### <a name="parameters"></a>パラメーター

*errnum*<br/>
0 から [_RTC_NumErrors](rtc-numerrors.md) によって戻される値より 1 少ない値までの範囲の数値。

*ErrType*<br/>
この *errnum*に割り当てる値。 たとえば、 **_CRT_ERROR**を使用できます。 **_CrtDbgReport**をエラーハンドラーとして使用している場合、 *Errtype*には[_CrtSetReportMode](crtsetreportmode.md)で定義されているシンボルの1つのみを指定できます。 独自のエラー ハンドラー ([_RTC_SetErrorFunc](rtc-seterrorfunc.md)) がある場合、 *errnum*の数だけ *ErrType*を指定できます。

**_CrtSetReportMode**の*errtype*には特別な意味があります (_s)このエラーは無視されます。

## <a name="return-value"></a>戻り値

エラーの種類の*種類*の以前の値。

## <a name="remarks"></a>Remarks

既定では、すべてのエラーは *_CRT_ERROR* に対応する **ErrType**= 1 に設定されます。 既定のエラーの種類 ( **_CRT_ERROR** など) について詳しくは、[_CrtDbgReport](crtdbgreport-crtdbgreportw.md) をご覧ください。

この関数を呼び出すには、まず、実行時エラー チェックの初期化関数の 1 つを呼び出す必要があります。「[Using Run-Time Checks without the C Run-Time Library (C ランタイム ライブラリなしのランタイム チェックの使用)](/visualstudio/debugger/using-run-time-checks-without-the-c-run-time-library)」をご覧ください

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_RTC_SetErrorType**|\<rtcapi.h>|

詳細については、「[互換性](../../c-runtime-library/compatibility.md)」をご覧ください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>関連項目

[_RTC_GetErrDesc](rtc-geterrdesc.md)<br/>
[ランタイム エラー チェック](../../c-runtime-library/run-time-error-checking.md)<br/>
