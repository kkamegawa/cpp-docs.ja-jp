---
title: asctime、_wasctime
ms.date: 11/04/2016
api_name:
- _wasctime
- asctime
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
- _tasctime
- asctime
- _wasctime
helpviewer_keywords:
- asctime function
- tasctime function
- wasctime function
- _tasctime function
- _wasctime function
- time structure conversion
- time, converting
ms.assetid: 974f1727-10ff-4ed4-8cac-2eb2d681f576
ms.openlocfilehash: 9ca9bbcbfff3d2bef41443ff1744a1b612727c20
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939669"
---
# <a name="asctime-_wasctime"></a>asctime、_wasctime

**Tm**時間構造体を文字列に変換します。 これらの関数のセキュリティを強化したバージョンを使用できます。「[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
char *asctime(
   const struct tm *timeptr
);
wchar_t *_wasctime(
   const struct tm *timeptr
);
```

### <a name="parameters"></a>パラメーター

*timeptr*<br/>
時刻/日付の構造体。

## <a name="return-value"></a>戻り値

**asctime**は、文字列の結果へのポインターを返します。 **_wasctime**は、ワイド文字列の結果へのポインターを返します。 エラーの戻り値はありません。

## <a name="remarks"></a>Remarks

これらの関数のセキュリティを強化したバージョンを使用できます。「[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)」を参照してください。

**Asctime**関数は、構造体として格納されている時刻を文字列に変換します。 *Timeptr*値は、通常、 **gmtime**または**localtime**の呼び出しから取得されます。この場合、両方とも、TIME で定義された**tm**構造体へのポインターが返されます。始め.

|timeptr メンバー|値|
|--------------------|-----------|
|**tm_hour**|深夜からの時間 (0-23)|
|**tm_isdst**|夏時間が有効な場合は正、夏時間が無効な場合は 0、夏時間かどうかが不明な場合は負。 C ランタイム ライブラリでは、アメリカ合衆国の規則を前提に夏時間 (DST) を計算します。|
|**tm_mday**|月の通算日 (1-31)|
|**tm_min**|分後 (分) (0-59)|
|**tm_mon**|月 (0-11;1月 = 0)|
|**tm_sec**|秒後の秒数 (0-59)|
|**tm_wday**|曜日 (0-6;日曜日 = 0)|
|**tm_yday**|年の通算日 (0-365;1月1日 = 0)|
|**tm_year**|年 (実際の西暦から 1900 を引いた数)|

変換された文字列も、ローカル タイム ゾーンの設定に従って調整されます。 ローカル タイムの設定の詳細については、[time](time-time32-time64.md)、[_ftime](ftime-ftime32-ftime64.md)、および [localtime](localtime-localtime32-localtime64.md) の関数を参照してください。また、タイム ゾーン環境とグローバル変数の定義の詳細については、[_tzset](tzset.md) 関数を参照してください。

**Asctime**によって生成される文字列の結果は、26文字`Wed Jan 02 02:03:55 1980\n\0`で、という形式になっています。 24 時間制が使用されます。 すべてのフィールドには一定の幅があります。 文字列の最後の 2 つの位置には、改行文字と null 文字が入ります。 **asctime**は、静的に割り当てられた単一のバッファーを使用して、返される文字列を保持します。 この関数を呼び出すたびに、前の呼び出しの結果は破棄されます。

**_wasctime**は、 **asctime**のワイド文字バージョンです。 それ以外では、 **_wasctime**と**asctime**は同じように動作します。

これらの関数では、パラメーターの検証が行われます。 *Timeptr*が null ポインターの場合、または範囲外の値が含まれている場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、関数は**NULL**を返し、 **errno**を**EINVAL**に設定します。

### <a name="generic-text-routine-mapping"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tasctime**|**asctime**|**asctime**|**_wasctime**|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**asctime**|\<time.h>|
|**_wasctime**|\<time.h> または \<wchar.h>|

## <a name="example"></a>例

このプログラムは、システム時刻を長整数の**aclock**に配置し、それを構造体の**newtime**に変換した後、 **asctime**関数を使用して出力用の文字列形式に変換します。

```C
// crt_asctime.c
// compile with: /W3

#include <time.h>
#include <stdio.h>

int main( void )
{
    struct tm   *newTime;
    time_t      szClock;

    // Get time in seconds
    time( &szClock );

    // Convert time to struct tm form
    newTime = localtime( &szClock );

    // Print local time as a string.
    printf_s( "Current date and time: %s", asctime( newTime ) ); // C4996
    // Note: asctime is deprecated; consider using asctime_s instead
}
```

```Output
Current date and time: Sun Feb 03 11:38:58 2002
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_tzset](tzset.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
