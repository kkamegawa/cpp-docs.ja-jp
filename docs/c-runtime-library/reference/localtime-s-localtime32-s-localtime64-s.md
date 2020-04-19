---
title: localtime_s、_localtime32_s、_localtime64_s
ms.date: 07/09/2019
api_name:
- _localtime64_s
- _localtime32_s
- localtime_s
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
- _localtime32_s
- localtime32_s
- localtime_s
- localtime64_s
- _localtime64_s
helpviewer_keywords:
- _localtime64_s function
- localtime32_s function
- _localtime32_s function
- localtime64_s function
- time, converting values
- localtime_s function
ms.assetid: 842d1dc7-d6f8-41d3-b340-108d4b90df54
ms.openlocfilehash: c00a5d23441612d0e70bfafd571bcb25250edb09
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953338"
---
# <a name="localtime_s-_localtime32_s-_localtime64_s"></a>localtime_s、_localtime32_s、_localtime64_s

**Time_t** time 値を**tm**構造体に変換し、ローカルタイムゾーンを修正します。 これらは、「[Security Features in the CRT](../../c-runtime-library/security-features-in-the-crt.md)」 (CRT のセキュリティ機能) で説明されているように、セキュリティが強化されたバージョンの [localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md) です。

## <a name="syntax"></a>構文

```C
errno_t localtime_s(
   struct tm* const tmDest,
   time_t const* const sourceTime
);
errno_t _localtime32_s(
   struct tm* tmDest,
   __time32_t const* sourceTime
);
errno_t _localtime64_s(
   struct tm* tmDest,
   __time64_t const* sourceTime
);
```

### <a name="parameters"></a>パラメーター

*tmDest*<br/>
目的の情報を格納する時間構造体へのポインター。

*sourceTime*<br/>
格納されている時刻へのポインター。

## <a name="return-value"></a>戻り値

正常終了した場合は 0。 障害が発生した場合、戻り値はエラー コードを示します。 エラー コードは、Errno.h で定義されています。 これらのエラー一覧については、「[errno](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

### <a name="error-conditions"></a>エラー条件

|*tmDest*|*sourceTime*|戻り値|*Tmdest*の値|無効なパラメーター ハンドラーを呼び出す|
|-----------|------------|------------------|--------------------|---------------------------------------|
|**NULL**|任意|**EINVAL**|変更されない|[はい]|
|Not **NULL** (有効なメモリを指す)|**NULL**|**EINVAL**|すべてのフィールドが -1 に設定される|[はい]|
|Not **NULL** (有効なメモリを指す)|0より小さいか、または **_MAX__TIME64_T**を超えています。|**EINVAL**|すべてのフィールドが -1 に設定される|いいえ|

最初の 2 つのエラーの場合は、「[Parameter Validation](../../c-runtime-library/parameter-validation.md)」 (パラメーターの検証) に説明されているとおり、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は**errno**を**einval**に設定し、 **einval**を返します。

## <a name="remarks"></a>Remarks

**Localtime_s**関数は、 [time_t](../../c-runtime-library/standard-types.md)値として格納されている時間を変換し、その結果を[tm](../../c-runtime-library/standard-types.md)型の構造体に格納します。 **Time_t** Value *sourcetime*は、午前0時 (00:00:00)、1970年1月1日からの経過秒数を表します。 通常、この値は[time](time-time32-time64.md)関数から取得されます。

**localtime_s**は、ユーザーが最初にグローバル環境変数**TZ**を設定した場合、ローカルタイムゾーンを修正します。 **TZ**が設定されている場合、他の3つの環境変数 ((**timezone**、 **_tzname** **、および**) も自動的に設定されます。 **TZ**変数が設定されていない場合、 **Localtime_s**は、コントロールパネルの [日付/時刻] アプリケーションで指定されたタイムゾーン情報を使用しようとします。 この情報を取得できない場合、既定では、太平洋タイム ゾーンを表す PST8PDT が使用されます。 これらの変数の説明については、[_tzset](tzset.md) を参照してください。 **TZ**は Microsoft 拡張機能であり、 **localtime**の ANSI 標準定義の一部ではありません。

> [!NOTE]
> 対象の環境は、夏時間が有効かどうかを判断しようとします。

**__time64_t**構造体を使用する **_localtime64_s**では、23:59:59 年1月18日から3001年1月18日までの日付を表すことができます。一方、 **_Localtime32_s**は23:59:59 年1月18日までの日付を表します。2038、UTC。

**localtime_s**は、 **_localtime64_s**に評価されるインライン関数で、 **time_t**は **__time64_t**に相当します。 以前の32ビットの**time_t**として**time_t**を解釈するようにコンパイラに強制する必要がある場合は、 **_USE_32BIT_TIME_T**を定義できます。 これを行うと、 **localtime_s**が **_localtime32_s**に評価されます。 ただし、この方法は推奨されません。2038 年 1 月 18 日以降にアプリケーションがエラーになる可能性があり、また、64 ビット プラットフォームでは使用できないためです。

Structure 型[tm](../../c-runtime-library/standard-types.md)のフィールドは、次の値を格納します。各値は**int**です。

|フィールド|説明|
|-|-|
|**tm_sec**|秒後 (0-59)。|
|**tm_min**|分後 (0-59)。|
|**tm_hour**|深夜からの時間 (0-23)。|
|**tm_mday**|月の通算日 (1-31)。|
|**tm_mon**|月 (0-11;1月 = 0)。|
|**tm_year**|年 (実際の西暦から 1900 を引いた数)|
|**tm_wday**|曜日 (0-6;日曜日 = 0)。|
|**tm_yday**|年の通算日 (0-365;1月1日 = 0)。|
|**tm_isdst**|夏時間が有効な場合は正の値、夏時間が無効な場合は 0、夏時間かどうか状態が不明な場合は負の値。|

**TZ**環境変数が設定されている場合、C ランタイムライブラリは、夏時間 (DST) の計算を実装するために、米国に適した規則を前提としています。

## <a name="requirements"></a>必要条件

|ルーチン|必須の C ヘッダー|必須の C++ ヘッダー|
|-------------|---------------------|-|
|**localtime_s**、 **_localtime32_s**、 **_localtime64_s**|\<time.h>|\<ctime > また\<は time .h >|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_localtime_s.c
// This program uses _time64 to get the current time
// and then uses _localtime64_s() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm newtime;
    char am_pm[] = "AM";
    __time64_t long_time;
    char timebuf[26];
    errno_t err;

    // Get time as 64-bit integer.
    _time64( &long_time );
    // Convert to local time.
    err = _localtime64_s( &newtime, &long_time );
    if (err)
    {
        printf("Invalid argument to _localtime64_s.");
        exit(1);
    }
    if( newtime.tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime.tm_hour > 12 )        // Convert from 24-hour
        newtime.tm_hour -= 12;        // to 12-hour clock.
    if( newtime.tm_hour == 0 )        // Set hour to 12 if midnight.
        newtime.tm_hour = 12;

    // Convert to an ASCII representation.
    err = asctime_s(timebuf, 26, &newtime);
    if (err)
    {
        printf("Invalid argument to asctime_s.");
        exit(1);
    }
    printf( "%.19s %s\n", timebuf, am_pm );
}
```

```Output
Fri Apr 25 01:19:27 PM
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
