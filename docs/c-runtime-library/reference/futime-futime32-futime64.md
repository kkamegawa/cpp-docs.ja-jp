---
title: _futime、_futime32、_futime64
ms.date: 11/04/2016
api_name:
- _futime64
- _futime32
- _futime
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
- futime
- _futime
- futime64
- _futime64
helpviewer_keywords:
- _futime function
- futime32 function
- futime64 function
- file modification time [C++]
- _futime64 function
- futime function
- _futime32 function
ms.assetid: b942ce8f-5cc7-4fa8-ab47-de5965eded53
ms.openlocfilehash: 3de638f08882e2aae4743311730afcd888c43a60
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956231"
---
# <a name="_futime-_futime32-_futime64"></a>_futime、_futime32、_futime64

開いているファイルの変更時刻を設定します。

## <a name="syntax"></a>構文

```C
int _futime(
   int fd,
   struct _utimbuf *filetime
);
int _futime32(
   int fd,
   struct __utimbuf32 *filetime
);
int _futime64(
   int fd,
   struct __utimbuf64 *filetime
);
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
開いているファイルのファイル記述子。

*返る*<br/>
新しい変更日を含む構造体へのポインター。

## <a name="return-value"></a>戻り値

処理が正常に終了した場合は 0 を返します。 エラーが発生した場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているとおり、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は-1 を返し、 **errno**は無効なファイル記述子を示す**EBADF**に設定されるか、無効なパラメーターを示す**EINVAL**に設定されます。

## <a name="remarks"></a>Remarks

**_Futime**ルーチンは、 *fd*に関連付けられている開いているファイルの変更日とアクセス時刻を設定します。 **_futime**は[_utime](utime-utime32-utime64-wutime-wutime32-wutime64.md)と同じですが、引数がファイルの名前またはファイルのパスではなく、開いているファイルのファイル記述子である点が異なります。 **_Utimbuf**構造体には、新しい変更日とアクセス時間のフィールドが含まれています。 両方のフィールドに、有効な値が含まれている必要があります。 **_utimbuf32**と **_utimbuf64**は、それぞれ32ビットと64ビットの時刻型を使用する点を除いて **_utimbuf**と同じです。 **_futime**と **_utimbuf**は、64ビットの時刻型を使用し、 **_futime**は **_futime64**に対する動作と同じです。 以前の動作を強制する必要がある場合は、 **_USE_32BIT_TIME_T**を定義します。 これを行うと、 **_futime**が **_futime32**と同じ動作になり、 **_utimbuf**構造体で32ビットの時刻型が使用され、 **__utimbuf32**と同等になります。

**__utimbuf64**構造体を使用する **_futime64**は、23:59:59 年12月 31 3000 日、UTC; の形式でファイルの日付の読み取りと変更を行うことができます。一方、ファイルの日付が23:59:59 年1月 2038 18 日より後の場合、 **_futime32**の呼び出しは失敗します。 これらの関数の日付範囲の下限は、1970 年 1 月 1 日の午前 0 時です。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|オプション ヘッダー|
|--------------|---------------------|---------------------|
|**_futime**|\<sys/utime.h>|\<errno.h>|
|**_futime32**|\<sys/utime.h>|\<errno.h>|
|**_futime64**|\<sys/utime.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_futime.c
// This program uses _futime to set the
// file-modification time to the current time.

#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <io.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <sys/utime.h>
#include <share.h>

int main( void )
{
   int hFile;

   // Show file time before and after.
   system( "dir crt_futime.c_input" );

   _sopen_s( &hFile, "crt_futime.c_input", _O_RDWR, _SH_DENYNO, 0 );

   if( _futime( hFile, NULL ) == -1 )
      perror( "_futime failed\n" );
   else
      printf( "File time modified\n" );

   _close (hFile);

   system( "dir crt_futime.c_input" );
}
```

### <a name="input-crt_futimec_input"></a>Input: crt_futime.c_input

```Input
Arbitrary file contents.
```

### <a name="sample-output"></a>出力例

```Output
Volume in drive Z has no label.
Volume Serial Number is 5C68-57C1

Directory of Z:\crt

03/25/2004  10:40 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
Volume in drive Z has no label.
Volume Serial Number is 5C68-57C1

Directory of Z:\crt

03/25/2004  10:41 AM                24 crt_futime.c_input
               1 File(s)             24 bytes
               0 Dir(s)  24,268,476,416 bytes free
File time modified
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
