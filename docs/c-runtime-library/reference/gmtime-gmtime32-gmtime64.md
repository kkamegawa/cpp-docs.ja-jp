---
title: gmtime、_gmtime32、_gmtime64
ms.date: 11/04/2016
api_name:
- _gmtime32
- gmtime
- _gmtime64
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
- gmtime
- _gmtime32
- _gmtime64
helpviewer_keywords:
- gmtime32 function
- _gmtime64 function
- gmtime function
- time functions
- _gmtime32 function
- gmtime64 function
- time structure conversion
ms.assetid: 315501f3-477e-475d-a414-ef100ee0db27
ms.openlocfilehash: ca5f424ac7006d2976ea03bbae9f0ad3a96abf6c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954849"
---
# <a name="gmtime-_gmtime32-_gmtime64"></a>gmtime、_gmtime32、_gmtime64

**Time_t** time 値を**tm**構造体に変換します。 これらの関数のセキュリティを強化したバージョンを使用できます。「[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
struct tm *gmtime( const time_t *sourceTime );
struct tm *_gmtime32( const __time32_t *sourceTime );
struct tm *_gmtime64( const __time64_t *sourceTime );
```

### <a name="parameters"></a>パラメーター

*sourceTime*<br/>
格納されている時刻へのポインター。 時刻は、世界協定時刻 (UTC: Coordinated Universal Time) の 1970 年 1 月 1 日の深夜 00:00:00 から経過した時間 (秒単位) を表します。

## <a name="return-value"></a>戻り値

型 [tm](../../c-runtime-library/standard-types.md) 構造体へのポインター。 返される構造体のフィールドには、 *sourcetime*引数の評価値が現地時刻ではなく UTC で格納されます。 構造体の各フィールドの型は**int**で、次のようになります。

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
|**tm_isdst**|**Gmtime**の場合は常に0です。|

**Gmtime**、 [mktime](mktime-mktime32-mktime64.md)、 [mkgmtime](mkgmtime-mkgmtime32-mkgmtime64.md)、および[localtime](localtime-localtime32-localtime64.md)の32ビットバージョンと64ビットバージョンの両方で、変換にスレッドごとに1つの共通の**tm**構造が使用されます。 これらの関数を呼び出すたびに、前の呼び出しの結果は破棄されます。 *Sourcetime*が1970年1月1日午前0時より前の日付を表している場合、 **gmtime**は**NULL**を返します。 エラーの戻り値はありません。

**__time64_t**構造体を使用する **_gmtime64**では、23:59:59 年12月31日から3000日までの日付を表すことができます。一方、 **_Gmtime32**は、2038年1月18日から23:59:59 までの日付のみを表します。 これらの関数の日付範囲の下限は、どちらも 1970 年 1 月 1 日の午前 0 時です。

**gmtime**は、 **_gmtime64**に評価されるインライン関数で、 **_USE_32BIT_TIME_T**が定義されていない限り、 **time_t**は **__time64_t**に相当します。 以前の32ビットの**time_t**として**time_t**を解釈するようにコンパイラに強制する必要がある場合は、 **_USE_32BIT_TIME_T**を定義できますが、これを行うと、 **gmtime**が **_gmtime32**と**time_t**にインラインで定義され、__ として定義されるようになります。 **time32_t**。 この方法は使用しないことをお勧めします。これは 64 ビット プラットフォームでは使用できず、また 2038 年 1 月 18 日以降はアプリケーションでエラーが発生する可能性があるためです。

これらの関数では、パラメーターの検証が行われます。 *Sourcetime*が null ポインターの場合、または*sourcetime*値が負の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、関数は**NULL**を返し、 **errno**を**EINVAL**に設定します。

## <a name="remarks"></a>Remarks

**_Gmtime32**関数は、 *sourcetime*値を分割し、time で定義された**tm**型の静的に割り当てられた構造体に格納します。始め. *Sourcetime*の値は、通常、 [time](time-time32-time64.md)関数の呼び出しから取得されます。

> [!NOTE]
> ほとんどの場合は、対象の環境で夏時間が有効かどうかを確認してください。 C ランタイム ライブラリでは、夏時間 (DST) の計算にアメリカ合衆国の規則が使用されていることを前提とします。

## <a name="requirements"></a>必要条件

|ルーチン|必須の C ヘッダー|必須の C++ ヘッダー|
|-------------|---------------------|-|
|**gmtime**、 **_gmtime32**、 **_gmtime64**|\<time.h>|\<ctime > また\<は time .h >|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_gmtime.c
// compile with: /W3
// This program uses _gmtime64 to convert a long-
// integer representation of coordinated universal time
// to a structure named newtime, then uses asctime to
// convert this structure to an output string.

#include <time.h>
#include <stdio.h>

int main( void )
{
   struct tm *newtime;
   __int64 ltime;
   char buff[80];

   _time64( &ltime );

   // Obtain coordinated universal time:
   newtime = _gmtime64( &ltime ); // C4996
   // Note: _gmtime64 is deprecated; consider using _gmtime64_s
   asctime_s( buff, sizeof(buff), newtime );
   printf( "Coordinated universal time is %s\n", buff );
}
```

```Output
Coordinated universal time is Tue Feb 12 23:11:31 2002
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[_mkgmtime、_mkgmtime32、_mkgmtime64](mkgmtime-mkgmtime32-mkgmtime64.md)<br/>
[mktime、_mktime32、_mktime64](mktime-mktime32-mktime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
