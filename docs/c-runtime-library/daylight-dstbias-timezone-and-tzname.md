---
title: _daylight、_dstbias、_timezone、および _tzname
ms.date: 11/04/2016
f1_keywords:
- tzname
- _timezone
- timezone
- _daylight
- _tzname
- daylight
helpviewer_keywords:
- time zones
- time adjustments
- timezone variables
- _tzname function
- _daylight function
- _timezone function
- daylight function
- local time adjustments
- timezone function
- tzname function
- time-zone variables
ms.assetid: d06c7292-6b99-4aba-b284-16a96570c856
ms.openlocfilehash: 3f9f78d0798140399960cade7ead408f958450ba
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748256"
---
# <a name="daylight-dstbias-timezone-and-tzname"></a>_daylight、_dstbias、_timezone、および _tzname

`_daylight`、`_dstbias`、`_timezone`、`_tzname` は、日付と時刻に関する一部のルーチンでローカル時刻の調整に使われます。 これらのグローバル変数は非推奨となりました。セキュリティを強化したバージョンを代わりに使う必要があります。

|グローバル変数|機能的に同等なバージョン|
|---------------------|---------------------------|
|`_daylight`|[_get_daylight](../c-runtime-library/reference/get-daylight.md)|
|`_dstbias`|[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)|
|`_timezone`|[_get_timezone](../c-runtime-library/reference/get-timezone.md)|
|`_tzname`|[_get_tzname](../c-runtime-library/reference/get-tzname.md)|

これらは、Time.h で次のように宣言されています。

## <a name="syntax"></a>構文

```
extern int _daylight;
extern int _dstbias;
extern long _timezone;
extern char *_tzname[2];
```

## <a name="remarks"></a>解説

`_ftime`、`localtime`、`_tzset` の呼び出しで、`_daylight`、`_dstbias`、`_timezone`、`_tzname` の値は、`TZ` 環境変数の値によって決まります。 `TZ` の値を明示的に設定していない場合、`_tzname[0]` と `_tzname[1]` にはそれぞれ既定値である "PST" と "PDT" が設定されます。  時間操作関数 ([_tzset](../c-runtime-library/reference/tzset.md)、[_ftime](../c-runtime-library/reference/ftime-ftime32-ftime64.md)、[localtime](../c-runtime-library/reference/localtime-localtime32-localtime64.md)) は、`_daylight`、`_dstbias`、`_timezone` の値を、オペレーティング システムで各変数の既定値をクエリすることによって設定します。 タイムゾーン グローバル変数の値を次の表に示します。

|変数|[値]|
|--------------|-----------|
|`_daylight`|夏時間 (DST) ゾーンであることが `TZ` で指定されている場合、またはオペレーティング システムから特定される場合は 0 以外の値。それ以外の場合は 0。 既定値は 1 です。|
|`_dstbias`|夏時間のオフセット。|
|`_timezone`|協定世界時刻と現地時刻の差 (秒単位)。 既定値は 28,800 です。|
|`_tzname[0]`|`TZ` 環境変数から得られるタイムゾーン名。 既定値は "PST" です。|
|`_tzname[1]`|`TZ` 環境変数から得られる DST ゾーン名。 既定値は "PDT" (太平洋夏時間) です。|

## <a name="see-also"></a>関連項目

[グローバル変数](../c-runtime-library/global-variables.md)<br/>
[_get_daylight](../c-runtime-library/reference/get-daylight.md)<br/>
[_get_dstbias](../c-runtime-library/reference/get-dstbias.md)<br/>
[_get_timezone](../c-runtime-library/reference/get-timezone.md)<br/>
[_get_tzname](../c-runtime-library/reference/get-tzname.md)
