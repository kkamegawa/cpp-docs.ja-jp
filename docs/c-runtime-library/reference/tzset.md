---
title: _tzset
ms.date: 11/04/2016
api_name:
- _tzset
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
- _tzset
helpviewer_keywords:
- _tzset function
- time environment variables
- environment variables, setting time
ms.assetid: 3f6ed537-b414-444d-b272-5dd377481930
ms.openlocfilehash: e9ea454ede370a20779b5852b426b418db81757c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957558"
---
# <a name="_tzset"></a>_tzset

時間環境変数を設定します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
void _tzset( void );
```

## <a name="remarks"></a>Remarks

**_Tzset**関数**は、環境**変数**TZ**の現在の設定を**使用し**て、3つのグローバル変数に値を**割り当てます。** これらの変数は、世界協定時刻 (UTC) から現地時刻への修正を行うために、 [_ftime](ftime-ftime32-ftime64.md)関数と[localtime](localtime-localtime32-localtime64.md)関数によって使用されます。また、[時刻](time-time32-time64.md)関数によってシステム時刻から UTC を計算するために使用されます。 **TZ**環境変数を設定するには、次の構文を使用します。

> **SET TZ =** _tzn_&#124;] hh:mm\[: ss]] [dzn]\[ \[ **+** **-**

|パラメーター|説明|
|-|-|
| *tzn* | PST など、3 文字のタイム ゾーンの名前。 現地時刻から UTC への適切なオフセットを指定する必要があります。 |
| *hh* | UTC と現地時刻の時差。 正の値のための符号 (+) オプション。 |
| *mm* | 分。 *Hh*からコロン ( **:** ) で区切られます。 |
| *ss* | 秒。 *Mm*からコロン ( **:** ) で区切られます。 |
| *dzn* | PDT など、3 文字の夏時間のタイム ゾーン。 地域で夏時間が適用されない場合は、 *dzn*の値を指定せずに**TZ**を設定します。 C ランタイム ライブラリでは、アメリカ合衆国の規則を前提に夏時間 (DST) を計算します。 |

> [!NOTE]
> 計算時には時差の符号に注意してください。 時差は現地時刻から UTC に変換する場合のオフセットである (逆ではない) であるため、符号は直感的に考えるものとは逆である場合があります。 UTC より早いタイム ゾーンの場合、時差は負になります。UTC より遅い場合、時差は正になります。

たとえば、 **TZ**環境変数をドイツの現在のタイムゾーンに対応するように設定するには、コマンドラインで次のように入力します。

> **set TZ = GST-1GDT**

このコマンドは、GST によってドイツの標準時刻であることを示し、UTC がドイツの時刻よりも 1 時間遅い (またはドイツは UTC より 1 時間早い) と想定し、さらにドイツでは夏時間が採用されていると想定しています。

**TZ**値が設定されていない場合、 **_tzset**はオペレーティングシステムによって指定されたタイムゾーン情報を使用しようとします。 Windows オペレーティング システムの場合、この情報は [コントロール パネル] の [日付/時刻] で指定します。 **_Tzset**がこの情報を取得できない場合、既定で PST8PDT が使用されます。これは、太平洋標準時ゾーンを表します。

**TZ**環境変数の値に基づいて、 **_tzset**が呼び出され**たときに**、次の値がグローバル変数 **(** **_tzname) に**割り当てられます。

|グローバル変数|説明|既定値|
|---------------------|-----------------|-------------------|
|**夏時間 (_c)**|**TZ**設定で夏時間のタイムゾーンが指定されている場合は0以外の値それ以外の場合は0です。|1|
|**_timezone**|現地時刻と UTC の秒単位での時差。|28800 (28800 秒は 8 時間に相当)|
|**_tzname**0|**TZ**環境変数からのタイムゾーン名の文字列値です。**TZ**が設定されていない場合は空です。|PST|
|**_tzname**1|夏時間のタイムゾーンの文字列値。**TZ**環境変数から夏時間のタイムゾーンが省略されている場合は空です。|PDT|

上記の表では、**夏時間**と **_tzname**配列の既定値は "PST8PDT" に対応しています。 DST ゾーンが**TZ**環境変数から省略されている場合、**夏時間**の値は0で、 [_ftime](ftime-ftime32-ftime64.md)、 [gmtime](gmtime-gmtime32-gmtime64.md)、および[localtime](localtime-localtime32-localtime64.md)の各関数は、それぞれの dst フラグに対して0を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_tzset**|\<time.h>|

**_Tzset**関数は、Microsoft 固有の関数です。 詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_tzset.cpp
// This program uses _tzset to set the global variables
// named _daylight, _timezone, and _tzname. Since TZ is
// not being explicitly set, it uses the system time.

#include <time.h>
#include <stdlib.h>
#include <stdio.h>

int main( void )
{
    _tzset();
    int daylight;
    _get_daylight( &daylight );
    printf( "_daylight = %d\n", daylight );
    long timezone;
    _get_timezone( &timezone );
    printf( "_timezone = %ld\n", timezone );
    size_t s;
    char tzname[100];
    _get_tzname( &s, tzname, sizeof(tzname), 0 );
    printf( "_tzname[0] = %s\n", tzname );
    exit( 0 );
}
```

```Output
_daylight = 1
_timezone = 28800
_tzname[0] = Pacific Standard Time
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
