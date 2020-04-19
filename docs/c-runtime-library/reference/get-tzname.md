---
title: _get_tzname
ms.date: 10/22/2018
api_name:
- _get_tzname
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
- _get_tzname
- get_tzname
helpviewer_keywords:
- _get_tzname function
- time zones
- get_tzname function
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
ms.openlocfilehash: 9f86a4997c328e86597e3bad8a7f7a3a5f5f50b6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70955624"
---
# <a name="_get_tzname"></a>_get_tzname

タイム ゾーン名または夏時間ゾーン名 (DST) の文字列表現を取得します。

## <a name="syntax"></a>構文

```C
errno_t _get_tzname(
    size_t* pReturnValue,
    char* timeZoneName,
    size_t sizeInBytes,
    int index
);
```

### <a name="parameters"></a>パラメーター

*pReturnValue*<br/>
Null 終端文字を含む*Timezonename*の文字列長。

*timeZoneName*<br/>
*インデックス*に応じて、タイムゾーン名または夏時間タイムゾーン名 (DST) の表現に使用する文字列のアドレス。

*sizeInBytes*<br/>
*Timezonename*文字列のサイズ (バイト単位)。

*index*<br/>
取得する 2 つのタイム ゾーン名のいずれかのインデックス。

|*index*|*Timezonename*の内容|*Timezonename*の既定値|
|-|-|-|
|0|タイム ゾーン名|「PST」|
|1|夏時間ゾーン名|「PDT」|
|> 1 または < 0|**errno**が**EINVAL**に設定される|変更されない|

実行時に値を明示的に変更しない限り、既定値はそれぞれ「PST」および「PDT」です。

## <a name="return-value"></a>戻り値

成功した場合は0。それ以外の場合は**errno**型の値。

*Timezonename*が**NULL**であるか、または*sizeinbytes*がゼロまたは0未満 (両方ではない) の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は**errno**を**einval**に設定し、 **einval**を返します。

### <a name="error-conditions"></a>エラー条件

|*pReturnValue*|*timeZoneName*|*sizeInBytes*|*index*|戻り値|*Timezonename*の内容|
|--------------------|--------------------|-------------------|-------------|------------------|--------------------------------|
|TZ 名のサイズ|**NULL**|0|0 または 1|0|変更されない|
|TZ 名のサイズ|任意|> 0|0 または 1|0|TZ 名|
|変更されない|**NULL**|> 0|任意|**EINVAL**|変更されない|
|変更されない|任意|ゼロ|任意|**EINVAL**|変更されない|
|変更されない|任意|> 0|> 1|**EINVAL**|変更されない|

## <a name="remarks"></a>Remarks

**_Get_tzname**関数は、現在のタイムゾーン名または夏時間のタイムゾーン名 (DST) の文字列形式を、インデックス値に応じて*timezonename*のアドレスに、の文字列のサイズと共に取得します。*Preturnvalue*ます。 *Timezonename*が**NULL**で*sizeinbytes*が0の場合、指定されたタイムゾーンを保持するために必要な文字列のサイズとバイト単位の終端の NULL が*preturnvalue*値として返されます。 インデックス値は、標準タイムゾーンの場合は0、夏時間タイムゾーンの場合は1にする必要があります。その他の*インデックス*の値には、不明な結果があります。

## <a name="example"></a>例

このサンプルでは、 **_get_tzname**を呼び出して、現在の夏時間のタイムゾーン名を表示するために必要なバッファーサイズを取得し、そのサイズのバッファーを割り当て、 **_get_tzname**を再度呼び出してバッファーに名前を読み込み、それをコンソールに出力します。

```C
// crt_get_tzname.c
// Compile by using: cl /W4 crt_get_tzname.c
#include <stdio.h>
#include <time.h>
#include <malloc.h>

enum TZINDEX {
    STD,
    DST
};

int main()
{
    size_t tznameSize = 0;
    char * tznameBuffer = NULL;

    // Get the size of buffer required to hold DST time zone name
    if (_get_tzname(&tznameSize, NULL, 0, DST))
        return 1;    // Return an error value if it failed

    // Allocate a buffer for the name
    if (NULL == (tznameBuffer = (char *)(malloc(tznameSize))))
        return 2;    // Return an error value if it failed

    // Load the name in the buffer
    if (_get_tzname(&tznameSize, tznameBuffer, tznameSize, DST))
        return 3;    // Return an error value if it failed

    printf_s("The current Daylight standard time zone name is %s.\n", tznameBuffer);
    return 0;
}
```

### <a name="output"></a>Output

```Output
The current Daylight standard time zone name is PDT.
```

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_get_tzname**|\<time.h>|

詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)<br/>
[_get_daylight](get-daylight.md)<br/>
[_get_dstbias](get-dstbias.md)<br/>
[_get_timezone](get-timezone.md)<br/>
