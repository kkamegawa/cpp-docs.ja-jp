---
title: timespec_get, _timespec32_get, _timespec64_get1
ms.date: 11/04/2016
api_name:
- timespec_get
- _timespec32_get
- _timespec64_get
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
- timespec_get
- _timespec32_get
- _timespec64_get
- time/timespec_get
- time/_timespec32_get
- time/_timespec64_get
- timespec
- _timespec32
- _timespec64
helpviewer_keywords:
- timespec_get function
- _timespec32_get function
- _timespec64_get function
ms.assetid: ed757258-b4f2-4c1d-a91b-22ea6ffce4ab
ms.openlocfilehash: c0517c974bf58d502133ccd9868149bd178790d6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957627"
---
# <a name="timespec_get-_timespec32_get-_timespec64_get"></a>timespec_get、_timespec32_get、_timespec64_get

指定された時間の基準に基づいて、最初の引数が指す間隔を現在のカレンダーの時間に設定します。

## <a name="syntax"></a>構文

```C
int timespec_get(
    struct timespec* const time_spec,
    int const base
);
int _timespec32_get(
    struct _timespec32* const time_spec,
    int const base
);
int _timespec64_get(
    struct _timespec64* const time_spec,
    int const base
);
```

### <a name="parameters"></a>パラメーター

*time_spec*<br/>
エポックの開始以降の時間 (秒およびナノ秒単位) に設定される構造体へのポインター。

*base*<br/>
時間の基準を指定する実装固有の値 (0 以外)。

## <a name="return-value"></a>戻り値

成功した場合は*base*の値。それ以外の場合は0を返します。

## <a name="remarks"></a>Remarks

**Timespec_get**関数は、 *time_spec*引数によって示される構造体の現在の時刻を設定します。 この構造体のすべてのバージョンには、 **tv_sec**と**tv_nsec**の2つのメンバーがあります。 **Tv_sec**の値は、秒の整数に設定され、 **tv_nsec**は*base*で指定されたエポックの開始以降、システムクロックの解像度に丸められます。

**Microsoft 固有の仕様**

これらの関数は、*ベース*値として**TIME_UTC**のみをサポートします。 これにより、 *time_spec*の値が、現地時刻 (UTC) であるエポックの開始日1970午前0時 (UTC) の秒数とナノ秒数に設定されます。 **構造体**では、 **tv_sec**は **__time32_t** **の値**です。 **構造体** **の場合、** **tv_sec**は **__time64_t**値です。 **構造体**の**timespec**では、 **tv_sec**は、プリプロセッサマクロ _USE_32BIT_TIME_T が定義されているかどうかに応じて、32ビットまたは64ビットの長さの**time_t**型です。 **Timespec_get**関数は、_USE_32BIT_TIME_T が定義されている場合に **_timespec32_get**を呼び出すインライン関数です。それ以外の場合は、 **_timespec64_get**を呼び出します。

**END Microsoft 固有の仕様**

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**timespec_get**、 **_timespec32_get**、 **_timespec64_get**|C: \<time.h>、C++: \<ctime> または \<time.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[asctime_s、_wasctime_s](asctime-s-wasctime-s.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[gmtime_s、_gmtime32_s、_gmtime64_s](gmtime-s-gmtime32-s-gmtime64-s.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[localtime_s、_localtime32_s、_localtime64_s](localtime-s-localtime32-s-localtime64-s.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
[_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64](utime-utime32-utime64-wutime-wutime32-wutime64.md)<br/>
