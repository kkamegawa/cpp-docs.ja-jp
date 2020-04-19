---
title: 時間管理
ms.date: 11/04/2016
f1_keywords:
- c.memory
helpviewer_keywords:
- dates, run-time library members
- time, time management
- date functions
- time functions
ms.assetid: 93599220-c011-45d5-978f-12182abfdd2f
ms.openlocfilehash: e9842d8c24089c7fbb33745c3bf5d4edb1d29343
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446786"
---
# <a name="time-management"></a>時間管理

以下の関数を使用すると、現在の時刻を取得して、必要に応じて変換、調整、保存を行うことができます。 現在の時刻とはシステム時刻のことです。

**_ftime** および **localtime** ルーチンでは **TZ** 環境変数が使用されます。 **TZ** が設定されていない場合、ランタイム ライブラリはオペレーティング システムで指定されるタイム ゾーン情報を使用します。 この情報が使用できないとき、これらの関数では既定値 PST8PDT が使用されます。 **TZ** の詳細については、「[_tzset](../c-runtime-library/reference/tzset.md)」のほか、「[_daylight、timezone、および _tzname](../c-runtime-library/daylight-dstbias-timezone-and-tzname.md)」も参照してください。

### <a name="time-routines"></a>時間のルーチン

|関数|使用|
|--------------|---------|
|[asctime, _wasctime](../c-runtime-library/reference/asctime-wasctime.md), [asctime_s, _wasctime_s](../c-runtime-library/reference/asctime-s-wasctime-s.md)|時刻を **struct tm** 型から文字列に変換します。 これらの関数のうち、 **_s** サフィックスの付いているバージョンがより安全です。|
|[clock](../c-runtime-library/reference/clock.md)|プロセスの実際の経過時間を返します。|
|[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](../c-runtime-library/reference/ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)、[_ctime_s、_ctime32_s、_ctime64_s、_wctime_s、_wctime32_s、_wctime64_s](../c-runtime-library/reference/ctime-s-ctime32-s-ctime64-s-wctime-s-wctime32-s-wctime64-s.md)|時刻を **time_t** 型、 **__time32_t** 型、または **__time64_t** 型から文字列に変換します。 これらの関数のうち、 **_s** サフィックスの付いているバージョンがより安全です。|
|[difftime、_difftime32、_difftime64](../c-runtime-library/reference/difftime-difftime32-difftime64.md)|2 つの時刻の差を計算します。|
|[_ftime, _ftime32, _ftime64](../c-runtime-library/reference/ftime-ftime32-ftime64.md)、[_ftime_s, _ftime32_s, _ftime64_s](../c-runtime-library/reference/ftime-s-ftime32-s-ftime64-s.md)|**struct _timeb** 型または **struct __timeb64** これらの関数のうち、 **_s** サフィックスの付いているバージョンがより安全です。|
|[_futime、_futime32、_futime64](../c-runtime-library/reference/futime-futime32-futime64.md)|開いているファイルの変更時刻を設定します。|
|[gmtime、_gmtime32、_gmtime64](../c-runtime-library/reference/gmtime-gmtime32-gmtime64.md)、[gmtime_s、_gmtime32_s、_gmtime64_s](../c-runtime-library/reference/gmtime-s-gmtime32-s-gmtime64-s.md)|時刻を **time_t** 型から **struct tm** に変換するか、 **__time64_t** 型から **struct tm** に変換します。これらの関数のうち、 **_s** サフィックスの付いているバージョンがより安全です。|
|[localtime、_localtime32、_localtime64](../c-runtime-library/reference/localtime-localtime32-localtime64.md)、[localtime_s、_localtime32_s、_localtime64_s](../c-runtime-library/reference/localtime-s-localtime32-s-localtime64-s.md)|時刻を **time_t** 型から **struct tm** に変換するか、 **__time64_t** 型からローカル時刻に修正した **struct tm** に変換します。 これらの関数のうち、 **_s** サフィックスの付いているバージョンがより安全です。|
|[_mkgmtime、_mkgmtime32、_mkgmtime64](../c-runtime-library/reference/mkgmtime-mkgmtime32-mkgmtime64.md)|時刻をグリニッジ標準時のカレンダーの値に変換します。|
|[mktime、_mktime32、_mktime64](../c-runtime-library/reference/mktime-mktime32-mktime64.md)|時刻をカレンダーの値に変換します。|
|[_strdate, _wstrdate](../c-runtime-library/reference/strdate-wstrdate.md), [_strdate_s, _wstrdate_s](../c-runtime-library/reference/strdate-s-wstrdate-s.md)|現在のシステム日付を文字列として返します。 これらの関数のうち、 **_s** サフィックスの付いているバージョンがより安全です。|
|[strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)|国際対応するように日付と時刻の文字列の書式を設定します。|
|[_strtime, _wstrtime](../c-runtime-library/reference/strtime-wstrtime.md)、 [_strtime_s、_wstrtime_s](../c-runtime-library/reference/strtime-s-wstrtime-s.md)|現在のシステム時刻を文字列として返します。 これらの関数のうち、 **_s** サフィックスの付いているバージョンがより安全です。|
|[time、_time32、_time64](../c-runtime-library/reference/time-time32-time64.md)|**time_t** 型、 **__time32_t** 型、または **__time64_t** 型で、現在のシステム時刻を取得します。|
|[_tzset](../c-runtime-library/reference/tzset.md)|時刻の環境変数 **TZ** で時刻の外部変数を設定します。|
|[_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md)|現在の時刻または構造体に格納された時刻の値を使用して、指定されたファイルの変更時刻を設定します。|

> [!NOTE]
> Microsoft C/C++ バージョン 7.0 を除くすべてのバージョンの Microsoft C/C++ と、すべてのバージョンの Visual C++ で、時刻の関数は、現在の時刻を 1970 年 1 月 1 日の午前 0 時から経過した秒数として返します。 Microsoft C/C++ バージョン 7.0 では、**time** は、現在の時刻を 1899 年 12 月 31 日の午前 0 時から経過した秒数として返していました。

> [!NOTE]
> Visual Studio 2005 より前の Visual C++ および Microsoft C/C++ のバージョンでは、**time_t** は **long** **int** (32 ビット) であったため、2038 年 1 月 19 日 3 時 14 分 07 秒 (UTC) を超えた日付には使用できませんでした。 現在、既定で **time_t** は **__time64_t** と同じです。ただし、 **_USE_32BIT_TIME_T** を定義すると、**time_t** は **__time32_t** に変更され、多くの時刻関数は強制的に 32 ビットの **time_t** を取得するバージョンを呼び出すことになります。 詳細については、「[基本データ型](../c-runtime-library/standard-types.md)」のほか、それぞれの時刻関数に関するドキュメントのコメントを参照してください。

## <a name="see-also"></a>関連項目

[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
