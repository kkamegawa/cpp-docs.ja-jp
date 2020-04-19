---
title: localtime、_localtime32、_localtime64
ms.date: 11/04/2016
api_name:
- _localtime64
- _localtime32
- localtime
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
- localtime64
- _localtime64
- localtime32
- localtime
- _localtime32
helpviewer_keywords:
- localtime32 function
- _localtime32 function
- _localtime64 function
- localtime64 function
- localtime function
- time, converting values
ms.assetid: 4260ec3d-43ee-4538-b998-402a282bb9b8
ms.openlocfilehash: 7e2f39b3a1b6376e24d8a812d1074840862f398a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953345"
---
# <a name="localtime-_localtime32-_localtime64"></a>localtime、_localtime32、_localtime64

時刻値を変換し、ローカル タイム ゾーンに合わせて修正します。 これらの関数にはセキュリティを強化したバージョンがあります。[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md) を参照してください。

## <a name="syntax"></a>構文

```C
struct tm *localtime( const time_t *sourceTime );
struct tm *_localtime32( const __time32_t *sourceTime );
struct tm *_localtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>パラメーター

*sourceTime*<br/>
格納されている時刻へのポインター。

## <a name="return-value"></a>戻り値

構造体の結果へのポインターを返すか、関数に渡された日付がの場合は**NULL**を返します。

- 1970 年 1 月 1 日午前 0 時より前。

- 03:14:07 年1月 2038 19 日、UTC ( **_time32**および**time32_t**を使用)。

- 23:59:59 年12月 31 3000 日の後、 **_time64**と **__time64_t**を使用します。

**__time64_t**構造体を使用する **_localtime64**では、23:59:59 年12月31日から3000年12月31日までの日付を表すことができます。一方、 **_Localtime32**は2038年1月18日から23:59:59 までの日付を表します。形式.

**localtime**は、 **_localtime64**に評価されるインライン関数で、 **time_t**は **__time64_t**に相当します。 以前の32ビットの**time_t**として**time_t**を解釈するようにコンパイラに強制する必要がある場合は、 **_USE_32BIT_TIME_T**を定義できます。 これを行うと、 **localtime**が **_localtime32**に評価されます。 ただし、この方法は推奨されません。2038 年 1 月 18 日以降にアプリケーションがエラーになる可能性があり、また、64 ビット プラットフォームでは使用できないためです。

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

## <a name="remarks"></a>Remarks

**Localtime**関数は、 [time_t](../../c-runtime-library/standard-types.md)値として格納されている時間を変換し、その結果を[tm](../../c-runtime-library/standard-types.md)型の構造体に格納します。 **Long** Value *sourcetime*は、午前0時 (00:00:00)、1970年1月1日からの経過秒数を表します。 通常、この値は[time](time-time32-time64.md)関数から取得されます。

[Gmtime](gmtime-gmtime32-gmtime64.md)、 [mktime](mktime-mktime32-mktime64.md)、 [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)、および**localtime**の32ビットバージョンと64ビットバージョンの両方で、変換にスレッドごとに1つの**tm**構造が使用されます。 これらのルーチンを呼び出すたびに、前の呼び出しの結果は破棄されます。

**localtime**は、ユーザーが最初にグローバル環境変数**TZ**を設定した場合、ローカルタイムゾーンを修正します。 **TZ**が設定されている場合、他の3つの環境変数 ((**timezone**、 **_tzname** **、および**) も自動的に設定されます。 **TZ**変数が設定されていない場合、 **Localtime**は、コントロールパネルの [日付/時刻] アプリケーションで指定されたタイムゾーン情報を使用しようとします。 この情報を取得できない場合、既定では、太平洋タイム ゾーンを表す PST8PDT が使用されます。 これらの変数の説明については、[_tzset](tzset.md) を参照してください。 **TZ**は Microsoft 拡張機能であり、 **localtime**の ANSI 標準定義の一部ではありません。

> [!NOTE]
> 対象の環境は、夏時間が有効かどうかを判断しようとします。

これらの関数では、パラメーターの検証が行われます。 *Sourcetime*が null ポインターの場合、または*sourcetime*値が負の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、関数は**NULL**を返し、 **errno**を**EINVAL**に設定します。

## <a name="requirements"></a>必要条件

|ルーチン|必須の C ヘッダー|必須の C++ ヘッダー|
|-------------|---------------------|-|
|**localtime**、 **_localtime32**、 **_localtime64**|\<time.h>|\<ctime > また\<は time .h >|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_localtime.cpp
// compile with: /W3
// This program uses _time64 to get the current time
// and then uses localtime64() to convert this time to a structure
// representing the local time. The program converts the result
// from a 24-hour clock to a 12-hour clock and determines the
// proper extension (AM or PM).

#include <stdio.h>
#include <string.h>
#include <time.h>

int main( void )
{
    struct tm *newtime;
    char am_pm[] = "AM";
    __time64_t long_time;

    _time64( &long_time );             // Get time as 64-bit integer.
                                       // Convert to local time.
    newtime = _localtime64( &long_time ); // C4996
    // Note: _localtime64 deprecated; consider _localetime64_s

    if( newtime->tm_hour > 12 )        // Set up extension.
        strcpy_s( am_pm, sizeof(am_pm), "PM" );
    if( newtime->tm_hour > 12 )        // Convert from 24-hour
        newtime->tm_hour -= 12;        //   to 12-hour clock.
    if( newtime->tm_hour == 0 )        // Set hour to 12 if midnight.
        newtime->tm_hour = 12;

    char buff[30];
    asctime_s( buff, sizeof(buff), newtime );
    printf( "%.19s %s\n", buff, am_pm );
}
```

```Output
Tue Feb 12 10:05:58 AM
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
