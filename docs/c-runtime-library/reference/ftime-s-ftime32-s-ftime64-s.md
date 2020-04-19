---
title: _ftime_s、_ftime32_s、_ftime64_s
ms.date: 11/04/2016
api_name:
- _ftime_s
- _ftime64_s
- _ftime32_s
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
- _ftime_s
- _ftime64_s
- ftime_s
- _ftime32_s
- ftime32_s
- ftime64_s
helpviewer_keywords:
- ftime32_s function
- ftime_s function
- _ftime64_s function
- current time
- ftime64_s function
- time, getting current
- _ftime_s function
- _ftime32_s function
ms.assetid: d03080d9-a520-45be-aa65-504bdb197e8b
ms.openlocfilehash: b45a22afc824a33e81170f954e6f99088b629f83
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956323"
---
# <a name="_ftime_s-_ftime32_s-_ftime64_s"></a>_ftime_s、_ftime32_s、_ftime64_s

現在の時刻を取得します。 これらは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」で説明されているように、セキュリティが強化されたバージョンの [_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md) です。

## <a name="syntax"></a>構文

```C
errno_t _ftime_s( struct _timeb *timeptr );
errno_t _ftime32_s( struct __timeb32 *timeptr );
errno_t _ftime64_s( struct __timeb64 *timeptr );
```

### <a name="parameters"></a>パラメーター

*timeptr*<br/>
**_Timeb**、 **__ timeb32**、または **__ timeb64**構造体へのポインター。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。 *Timeptr*が**NULL**の場合、戻り値は**EINVAL**になります。

## <a name="remarks"></a>Remarks

**_Ftime_s**関数は、現在の現地時刻を取得し、 *timeptr*によって示される構造体に格納します。 **_Timeb**、 **__ timeb32**、および **__ timeb64**構造体は、sysで定義されています。 これらは、次の表に示す 4 つのフィールドを含んでいます。

|フィールド|説明|
|-|-|
|**dstflag**|ローカルのタイム ゾーンで夏時間が現在有効になっている場合は 0 以外の値です (夏時間を判断する方法の詳細については、[_tzset](tzset.md) を参照してください)。|
|**millitm**|ミリ秒単位での秒の小数部。|
|**time**|世界協定時刻 (UTC: Coordinated Universal Time) の 1970 年 1 月 1 日の深夜 00:00:00 から経過した時間 (秒単位)。|
|**timezone**|西に移動するときの UTC と現地時刻の間の差 (分単位)。 **タイムゾーン**の値は、グローバル変数の**タイムゾーン**の値から設定されます (「 **_tzset**」を参照してください)。|

**_Ftime64_s**関数では、 **__ timeb64**構造体を使用して、ファイル作成日を23:59:59 年12月 31 3000 日 (UTC) で表すことができます。一方2038、 **_ftime32_s**は、23:59:59 年1月18日からまでの日付のみを表します。 これらの関数の日付範囲の下限は、いずれも 1970 年 1 月 1 日の午前 0 時です。

**_Ftime_s**関数は **_ftime64_s**に相当し、 **_timeb**には64ビットの時刻が含まれます。ただし、 **_USE_32BIT_TIME_T**が定義されている場合は、古い動作が有効になります。 **_ftime_s**は32ビットの時刻を使用し、 **_timeb**には32ビットの時刻が含まれます。

**_ftime_s**は、そのパラメーターを検証します。 *Timeptr*として null ポインターが渡された場合、関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、関数は**errno**を**EINVAL**に設定します。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**_ftime_s**|\<sys/types.h> と \<sys/timeb.h>|
|**_ftime32_s**|\<sys/types.h> と \<sys/timeb.h>|
|**_ftime64_s**|\<sys/types.h> と \<sys/timeb.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_ftime64_s.c
// This program uses _ftime64_s to obtain the current
// time and then stores this time in timebuffer.

#include <stdio.h>
#include <sys/timeb.h>
#include <time.h>

int main( void )
{
   struct _timeb timebuffer;
   char timeline[26];
   errno_t err;
   time_t time1;
   unsigned short millitm1;
   short timezone1;
   short dstflag1;

   _ftime64_s( &timebuffer );

    time1 = timebuffer.time;
    millitm1 = timebuffer.millitm;
    timezone1 = timebuffer.timezone;
    dstflag1 = timebuffer.dstflag;

   printf( "Seconds since midnight, January 1, 1970 (UTC): %I64d\n",
   time1);
   printf( "Milliseconds: %d\n", millitm1);
   printf( "Minutes between UTC and local time: %d\n", timezone1);
   printf( "Daylight savings time flag (1 means Daylight time is in "
           "effect): %d\n", dstflag1);

   err = ctime_s( timeline, 26, & ( timebuffer.time ) );
   if (err)
   {
       printf("Invalid argument to ctime_s. ");
   }
   printf( "The time is %.19s.%hu %s", timeline, timebuffer.millitm,
           &timeline[20] );
}
```

```Output
Seconds since midnight, January 1, 1970 (UTC): 1051553334
Milliseconds: 230
Minutes between UTC and local time: 480
Daylight savings time flag (1 means Daylight time is in effect): 1
The time is Mon Apr 28 11:08:54.230 2003
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
