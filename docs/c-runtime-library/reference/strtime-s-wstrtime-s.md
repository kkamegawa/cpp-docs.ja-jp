---
title: _strtime_s、_wstrtime_s
ms.date: 11/04/2016
api_name:
- _wstrtime_s
- _strtime_s
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
- _wstrtime_s
- strtime_s
- wstrtime_s
- _strtime_s
helpviewer_keywords:
- wstrtime_s function
- copying time to buffers
- strtime_s function
- _wstrtime_s function
- time, copying
- _strtime_s function
ms.assetid: 42acf013-c334-485d-b610-84c0af8a46ec
ms.openlocfilehash: c74e7359f68469fd8322ba1c9348acffd636282a
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625915"
---
# <a name="_strtime_s-_wstrtime_s"></a>_strtime_s、_wstrtime_s

現在の時刻をバッファーにコピーします。 これらは、「[Security Features in the CRT](../../c-runtime-library/security-features-in-the-crt.md)」 (CRT のセキュリティ機能) の説明にあるとおり、セキュリティが強化されたバージョンの [_strtime、_wstrtime](strtime-wstrtime.md) です。

## <a name="syntax"></a>構文

```C
errno_t _strtime_s(
   char *buffer,
   size_t numberOfElements
);
errno_t _wstrtime_s(
   wchar_t *buffer,
   size_t numberOfElements
);
template <size_t size>
errno_t _strtime_s(
   char (&buffer)[size]
); // C++ only
template <size_t size>
errno_t _wstrtime_s(
   wchar_t (&buffer)[size]
); // C++ only
```

### <a name="parameters"></a>パラメーター

*バッファー*<br/>
バッファーの長さは少なくとも 10 バイトで、時刻が書き込まれます。

*numberOfElements*<br/>
バッファーのサイズ。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。

エラー状況が発生した場合は、「[パラメータの検証](../../c-runtime-library/parameter-validation.md)」に説明されているとおり、無効なパラメーター ハンドラーが呼び出されます。 障害が発生した場合、戻り値はエラー コードを示します。 エラー コードは ERRNO.H で定義されます。この関数によって生成される正確なエラーについては、下記の表をご覧ください。 エラー コードの詳細については、「[errno 定数](../../c-runtime-library/errno-constants.md)」をご覧ください。

### <a name="error-conditions"></a>エラー条件

|*バッファー*|*numberOfElements*|Return|*バッファー*の内容|
|--------------|------------------------|------------|--------------------------|
|**NULL**|(任意)|**EINVAL**|変更されない|
|Not **NULL** (有効なバッファーを指す)|0|**EINVAL**|変更されない|
|Not **NULL** (有効なバッファーを指す)|0 < サイズ < 9|**EINVAL**|空の文字列|
|Not **NULL** (有効なバッファーを指す)|サイズ > 9|0|コメントで指定されている書式設定の、現在の時刻|

## <a name="security-issues"></a>セキュリティ上の問題

無効な**NULL**以外の値をバッファーに渡すと、 *numberofelements*パラメーターが9よりも大きい場合、アクセス違反が発生します。

*Numberofelements*の値をバッファーの実際のサイズより大きい値に渡すと、バッファーオーバーランが発生します。

## <a name="remarks"></a>Remarks

これらの関数は、より安全なバージョンの[_strtime](strtime-wstrtime.md)と[_wstrtime](strtime-wstrtime.md)を提供します。 **_Strtime_s**関数は、 *timestr*が指すバッファーに現在の現地時刻をコピーします。 時刻は**hh: mm: ss**として書式設定されます。ここで、 **hh**は24時間表記の時間を表す2桁の数字、 **mm**は2桁の数字を表し、 **ss**は秒を表す2桁の数字です。 たとえば、文字列**18:23:44**は、午後6時24分と44秒を表します。 バッファーは少なくとも 9 バイト長である必要があります。実際のサイズは、2 番目のパラメーターによって指定されます。

**_wstrtime**は、 **_strtime**のワイド文字バージョンです。 **_wstrtime**の引数と戻り値はワイド文字列です。 それ以外では、これらの関数の動作は同じです。

C++ では、これらの関数の使用はテンプレートのオーバーロードによって簡素化されます。オーバーロードでは、バッファー長を自動的に推論できる (サイズの引数を指定する必要がなくなる) だけでなく、古くてセキュリティが万全ではない関数を新しく安全な関数に自動的に置き換えることができます。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

これらの関数のデバッグライブラリバージョンは、最初にバッファーを0xFE で埋めます。 この動作を無効にするには、[_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md) を使用します。

### <a name="generic-text-routine-mapping"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime_s**|**_strtime_s**|**_strtime_s**|**_wstrtime_s**|

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_strtime_s**|\<time.h>|
|**_wstrtime_s**|\<time.h> または \<wchar.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// strtime_s.c

#include <time.h>
#include <stdio.h>

int main()
{
    char tmpbuf[9];
    errno_t err;

    // Set time zone from TZ environment variable. If TZ is not set,
    // the operating system is queried to obtain the default value
    // for the variable.
    //
    _tzset();

    // Display operating system-style date and time.
    err = _strtime_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
      exit(1);
    }
    printf( "OS time:\t\t\t\t%s\n", tmpbuf );
    err = _strdate_s( tmpbuf, 9 );
    if (err)
    {
       printf("_strdate_s failed due to an invalid argument.");
       exit(1);
    }
    printf( "OS date:\t\t\t\t%s\n", tmpbuf );

}
```

```Output
OS time:            14:37:49
OS date:            04/25/03
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
