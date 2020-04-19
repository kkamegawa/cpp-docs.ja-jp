---
title: _strtime、_wstrtime
ms.date: 11/04/2016
api_name:
- _wstrtime
- _strtime
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
- _wstrtime
- _strtime
- wstrtime
- strtime
- _tstrtime
helpviewer_keywords:
- strtime function
- _strtime function
- _wstrtime function
- copying time to buffers
- wstrtime function
- tstrtime function
- _tstrtime function
- time, copying
ms.assetid: 9e538161-cf49-44ec-bca5-c0ab0b9e4ca3
ms.openlocfilehash: ea4a2b304dc30ec167f8a9094bcf278ff0d31f77
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70946558"
---
# <a name="_strtime-_wstrtime"></a>_strtime、_wstrtime

時刻をバッファーにコピーします。 これらの関数のセキュリティを強化したバージョンを使用できます。「[_strtime_s、_wstrtime_s (_strtime_s、_wstrtime_s)](strtime-s-wstrtime-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
char *_strtime(
   char *timestr
);
wchar_t *_wstrtime(
   wchar_t *timestr
);
template <size_t size>
char *_strtime(
   char (&timestr)[size]
); // C++ only
template <size_t size>
wchar_t *_wstrtime(
   wchar_t (&timestr)[size]
); // C++ only
```

### <a name="parameters"></a>パラメーター

*timestr*<br/>
時刻の文字列。

## <a name="return-value"></a>戻り値

結果の文字列*timestr*へのポインターを返します。

## <a name="remarks"></a>Remarks

**_Strtime**関数は、 *timestr*が指すバッファーに現在の現地時刻をコピーします。 時刻は**hh: mm: ss**として書式設定されます。ここで、 **hh**は24時間表記の時間を表す2桁の数字、 **mm**は2桁の数字を表し、 **ss**は秒を表す2桁の数字です。 たとえば、文字列**18:23:44**は、午後6時24分と44秒を表します。 バッファーは 9 バイト以上の長さである必要があります。

**_wstrtime**は、 **_strtime**のワイド文字バージョンです。 **_wstrtime**の引数と戻り値はワイド文字列です。 それ以外では、これらの関数の動作は同じです。 *Timestr*が**NULL**ポインターの場合、または*timestr*が正しく書式設定されていない場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 例外の継続が許可された場合、これらの関数は**null**を返し、 **errno**を**EINVAL**に設定します。 *timestr*が**null**の場合、または*timestr*が正しく書式設定されていない場合は**errno**を**ERANGE**に設定します。

C++ では、これらの関数にテンプレートのオーバーロードがあります。このオーバーロードは、これらの関数に対応するセキュリティで保護された新しい関数を呼び出します。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tstrtime**|**_strtime**|**_strtime**|**_wstrtime**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_strtime**|\<time.h>|
|**_wstrtime**|\<time.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_strtime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
   char tbuffer [9];
   _strtime( tbuffer ); // C4996
   // Note: _strtime is deprecated; consider using _strtime_s instead
   printf( "The current time is %s \n", tbuffer );
}
```

```Output
The current time is 14:21:44
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
