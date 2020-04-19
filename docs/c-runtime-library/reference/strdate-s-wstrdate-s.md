---
title: _strdate_s、_wstrdate_s
description: _strdate_s と _wstrdate_s は、現在の日付をバッファーに格納する、_strdate および _wstrdate 関数のセキュリティで保護された CRT バージョンです。
ms.date: 11/01/2019
api_name:
- _strdate_s
- _wstrdate_s
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
- api-ms-win-crt-time-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _strdate_s
- wstrdate_s
- _wstrdate_s
- strdate_s
- _tstrdate_s
helpviewer_keywords:
- dates, copying
- tstrdate_s function
- wstrdate_s function
- _tstrdate_s function
- strdate_s function
- copying dates
- _strdate_s function
- _wstrdate_s function
ms.assetid: d41d8ea9-e5ce-40d4-864e-1ac29b455991
ms.openlocfilehash: 7d04c134fcd19753ac0cecf8cc3b87e902d92e83
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625756"
---
# <a name="_strdate_s-_wstrdate_s"></a>_strdate_s、_wstrdate_s

現在のシステム日付をバッファーにコピーします。 これらの関数は、「 [CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの[_strdate、_wstrdate](strdate-wstrdate.md)です。

## <a name="syntax"></a>構文

```C
errno_t _strdate_s(
   char *buffer,
   size_t size
);
errno_t _wstrdate_s(
   wchar_t *buffer,
   size_t size
);
template <size_t size>
errno_t _strdate_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrdate_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>パラメーター

*バッファー* \
書式設定された日付文字列を格納するバッファーへのポインター。

\*サイズ*
バッファーのサイズ (文字単位)。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。 エラーが発生した場合、戻り値はエラーコードです。 エラー コードは ERRNO.H で定義されます。この関数によって生成される正確なエラーについては、下記の表をご覧ください。 エラー コードの詳細については、「[errno 定数](../../c-runtime-library/errno-constants.md)」をご覧ください。

## <a name="error-conditions"></a>エラー条件

|*バッファー*|*size*|Return|*バッファー*の内容|
|--------------|------------------------|------------|--------------------------|
|**NULL**|(任意)|**EINVAL**|変更されない|
|Not **NULL** (有効なバッファーを指す)|0|**EINVAL**|変更されない|
|Not **NULL** (有効なバッファーを指す)|0 <*サイズ*< 9|**EINVAL**|空の文字列|
|Not **NULL** (有効なバッファーを指す)|*サイズ*> = 9|0|コメントで指定されている書式設定の、現在の日付|

## <a name="security-issues"></a>セキュリティの問題

*Size*パラメーターが9よりも大きい場合、*バッファー*に NULL 以外の無効な値を渡すとアクセス違反になります。

*バッファー*の実際のサイズより大きい*サイズ*の値を渡すと、バッファーオーバーランが発生します。

## <a name="remarks"></a>Remarks

これらの関数は、より安全なバージョンの **_strdate**と **_wstrdate**を提供します。 **_Strdate_s**関数は、現在のシステム日付を*バッファー*が指すバッファーにコピーします。 形式は `mm/dd/yy`です。 `mm` は2桁の月、`dd` は2桁の日、`yy` は年の最後の2桁です。 たとえば、文字列 `12/05/99` は、1999 年 12 月 5 日を表します。 バッファーの長さは9文字以上である必要があります。

**_wstrdate_s**は、 **_strdate_s**のワイド文字バージョンです。 **_wstrdate_s**の引数と戻り値はワイド文字列です。 それ以外では、これらの関数の動作は同じです。

*バッファー*が**NULL**ポインターの場合、または*サイズ*が9文字未満の場合は、無効なパラメーターハンドラーが呼び出されます。 詳細については、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」を参照してください。 実行の継続が許可された場合、これらの関数は-1 を返します。 バッファーが**NULL**の場合、または*size*が0以下の場合は、 **errno**を**EINVAL**に設定します。 または、 *size*が9より小さい場合は、 **errno**を**ERANGE**に設定します。

でC++は、これらの関数の使用はテンプレートのオーバーロードによって簡略化されています。 オーバーロードでは、バッファー長を自動的に推論できるため、*サイズ*引数を指定する必要がなくなります。 また、セキュリティで保護されていない関数を、より安全な新しい関数に自動的に置き換えることができます。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

これらの関数のデバッグライブラリバージョンは、最初にバッファーを0xFE で埋めます。 この動作を無効にするには、[_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md) を使用します。

### <a name="generic-text-routine-mapping"></a>汎用テキストルーチンのマッピング:

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrdate_s**|**_strdate_s**|**_strdate_s**|**_wstrdate_s**|

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_strdate**|\<time.h>|
|**_wstrdate**|\<time.h> または \<wchar.h>|
|**_strdate_s**|\<time.h>|

## <a name="example"></a>例

[time](time-time32-time64.md) の例を参照してください。

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)\
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)\
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)\
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)\
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)\
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)\
[time、_time32、_time64](time-time32-time64.md)\
[_tzset](tzset.md)
