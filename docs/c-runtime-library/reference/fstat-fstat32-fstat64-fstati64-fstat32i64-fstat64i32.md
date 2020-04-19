---
title: _fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32
ms.date: 11/04/2016
api_name:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _fstat32i64
- fstat
- fstat64i32
- _fstat64
- _fstati64
- fstat64
- _fstat32
- fstat32i64
- fstati64
- _fstat
- fstat32
- _fstat64i32
helpviewer_keywords:
- _fstat64 function
- fstati64 function
- _fstat64i32 function
- _fstat32i64 function
- _fstat32 function
- file information
- fstat64i32 function
- fstat32 function
- fstat function
- fstat64 function
- _fstat function
- _fstati64 function
- fstat32i64 function
ms.assetid: 088f5e7a-9636-4cf7-ab8e-e28d2aa4280a
ms.openlocfilehash: 1ab71071fdf5578295cfcd72f79930787e634d5f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956461"
---
# <a name="_fstat-_fstat32-_fstat64-_fstati64-_fstat32i64-_fstat64i32"></a>_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32

開いているファイルに関する情報を取得します。

## <a name="syntax"></a>構文

```C
int _fstat(
   int fd,
   struct _stat *buffer
);
int _fstat32(
   int fd,
   struct __stat32 *buffer
);
int _fstat64(
   int fd,
   struct __stat64 *buffer
);
int _fstati64(
   int fd,
   struct _stati64 *buffer
);
int _fstat32i64(
   int fd,
   struct _stat32i64 *buffer
);
int _fstat64i32(
   int fd,
   struct _stat64i32 *buffer
);
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
開いているファイルのファイル記述子。

*バッファー*<br/>
結果を格納する構造体へのポインター。

## <a name="return-value"></a>戻り値

ファイルのステータス情報が取得されると、0 を返します。 戻り値-1 はエラーを示します。 ファイル記述子が無効であるか、*バッファー*が**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 続けるには、実行が許可された場合**errno**に設定されている**EBADF**、無効なファイル記述子が場合または**EINVAL**場合は、*バッファー* **NULL**します。

## <a name="remarks"></a>Remarks

**_Fstat**関数は、 *fd*に関連付けられている開いているファイルに関する情報を取得し、 *buffer*によって示される構造体に格納します。 **_Stat**構造体には、次のフィールドが含まれています。

|フィールド|説明|
|-|-|
| **st_atime** | ファイルの最後のアクセスの時間。 |
| **st_ctime** | ファイルの作成の時間。 |
| **st_dev** | デバイスの場合は、 *fd*の場合はそれ以外の場合は0です。 |
| **st_mode** | ファイル モード情報のビット マスク。 *Fd*がデバイスを参照する場合、 **_S_IFCHR**ビットが設定されます。 *Fd*が通常のファイルを参照する場合、 **_S_IFREG**ビットが設定されます。 読み取り/書き込みのビットは、ファイルのアクセス許可モードに応じて設定されます。 **_S_IFCHR**およびその他の定数は、sysh で定義されています。 |
| **st_mtime** | ファイルの最終変更時刻。 |
| **st_nlink** | 非 NTFS ファイル システムでは常に 1 です。 |
| **st_rdev** | デバイスの場合は、 *fd*の場合はそれ以外の場合は0です。 |
| **st_size** | ファイルのサイズ (バイト単位)。 |

*Fd*がデバイスを参照している場合、 **st_atime**、 **st_ctime**、 **st_mtime**、および**st_size**の各フィールドには意味がありません。

Stat.h は Types.h で定義される [_dev_t](../../c-runtime-library/standard-types.md) 型を使用するため、コードで Stat.h の前に Types.h を組み込む必要があります。

**_fstat64**は、 **__ stat64**構造体を使用しており、ファイル作成日を23:59:59 年12月 3000 31 日 (UTC) で表すことができます。一方、他の関数は、23:59:59 年1月18日から2038日までの日付のみを表します。 これらの関数の日付範囲の下限は、いずれも 1970 年 1 月 1 日の午前 0 時です。

これらの関数のバリエーションは、32 ビットや 64 ビットの時刻型と、32 ビットや 64 ビットのファイル長をサポートします。 最初の数字のサフィックス (**32**または**64**) は、使用された時間の種類のサイズを示します。2番目のサフィックスは、 **i32**または**i64**のいずれかで、ファイルサイズが32ビットまたは64ビットの整数で表されるかどうかを示します。

**_fstat**は **_fstat64i32**に相当し、 **struct** **_stat**には64ビットの時刻が含まれます。 これは、 **_USE_32BIT_TIME_T**が定義されていない場合に当てはまります。この場合、以前の動作が有効になります。 **_fstat**は32ビットの時刻を使用し、**構造体**の **_stat**には32ビットの時刻が含まれます。 **_Fstati64**の場合も同様です。

### <a name="time-type-and-file-length-type-variations-of-_stat"></a>_stat の時刻型とファイル長型のバリエーション

|関数|_USE_32BIT_TIME_T が定義されているか|時刻型|ファイル長型|
|---------------|------------------------------------|---------------|----------------------|
|**_fstat**|未定義|64 ビット|32 ビット|
|**_fstat**|定義済み|32 ビット|32 ビット|
|**_fstat32**|マクロ定義の影響を受けない|32 ビット|32 ビット|
|**_fstat64**|マクロ定義の影響を受けない|64 ビット|64 ビット|
|**_fstati64**|未定義|64 ビット|64 ビット|
|**_fstati64**|定義済み|32 ビット|64 ビット|
|**_fstat32i64**|マクロ定義の影響を受けない|32 ビット|64 ビット|
|**_fstat64i32**|マクロ定義の影響を受けない|64 ビット|32 ビット|

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**_fstat**|\<sys/stat.h> と \<sys/types.h>|
|**_fstat32**|\<sys/stat.h> と \<sys/types.h>|
|**_fstat64**|\<sys/stat.h> と \<sys/types.h>|
|**_fstati64**|\<sys/stat.h> と \<sys/types.h>|
|**_fstat32i64**|\<sys/stat.h> と \<sys/types.h>|
|**_fstat64i32**|\<sys/stat.h> と \<sys/types.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_fstat.c
// This program uses _fstat to report
// the size of a file named F_STAT.OUT.

#include <io.h>
#include <fcntl.h>
#include <time.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>
#include <share.h>

int main( void )
{
   struct _stat buf;
   int fd, result;
   char buffer[] = "A line to output";
   char timebuf[26];
   errno_t err;

   _sopen_s( &fd,
             "f_stat.out",
             _O_CREAT | _O_WRONLY | _O_TRUNC,
             _SH_DENYNO,
             _S_IREAD | _S_IWRITE );
   if( fd != -1 )
      _write( fd, buffer, strlen( buffer ) );

   // Get data associated with "fd":
   result = _fstat( fd, &buf );

   // Check if statistics are valid:
   if( result != 0 )
   {
      if (errno == EBADF)
        printf( "Bad file descriptor.\n" );
      else if (errno == EINVAL)
        printf( "Invalid argument to _fstat.\n" );
   }
   else
   {
      printf( "File size     : %ld\n", buf.st_size );
      err = ctime_s(timebuf, 26, &buf.st_mtime);
      if (err)
      {
         printf("Invalid argument to ctime_s.");
         exit(1);
      }
      printf( "Time modified : %s", timebuf );
   }
   _close( fd );
}
```

```Output
File size     : 16
Time modified : Wed May 07 15:25:11 2003
```

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_access、_waccess](access-waccess.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_filelength、_filelengthi64](filelength-filelengthi64.md)<br/>
[_stat、_wstat 関数](stat-functions.md)<br/>
