---
title: _get_dstbias
ms.date: 11/04/2016
api_name:
- _get_dstbias
- __dstbias
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
- __dstbias
- _get_dstbias
- get_dstbias
helpviewer_keywords:
- __dstbias
- daylight saving time offset
- get_dstbias function
- _get_dstbias function
ms.assetid: e751358c-1ecc-411b-ae2c-81b2ec54ea45
ms.openlocfilehash: a48cc4fe35a1bbd18342750571214ed0977cf3ee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955948"
---
# <a name="_get_dstbias"></a>_get_dstbias

夏時間のオフセット (秒単位) を取得します。

## <a name="syntax"></a>構文

```C
error_t _get_dstbias( int* seconds );
```

### <a name="parameters"></a>パラメーター

*seconds*<br/>
夏時間のオフセット (秒単位)。

## <a name="return-value"></a>戻り値

成功した場合は0、エラーが発生した場合は**errno**値。

## <a name="remarks"></a>Remarks

**_Get_dstbias**関数は、夏時間の秒数を整数として取得します。 夏時間が適用されている場合、既定のオフセットは 3,600 秒であり、これは 1 時間の秒数です (ただし、一部の地域は 2 時間のオフセットを実施しています)。

*Seconds*が**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は**errno**を**einval**に設定し、 **einval**を返します。

**マクロで**はなく、この関数を使用することをお勧めします。または、非推奨の関数 **__ dstバイアス**です。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_get_dstbias**|\<time.h>|

詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_timezone](get-timezone.md)<br/>
[_get_tzname](get-tzname.md)<br/>
