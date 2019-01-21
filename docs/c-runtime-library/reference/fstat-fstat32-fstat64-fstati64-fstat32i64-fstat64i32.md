---
title: _fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32
ms.date: 11/04/2016
apiname:
- _fstat32
- _fstat64
- _fstati64
- _fstat
- _fstat64i32
- _fstat32i64
apilocation:
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
apitype: DLLExport
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
ms.openlocfilehash: 36d8b0d6480266f86136119a470fb7af5859a5b8
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51331244"
---
# <a name="fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32"></a>_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32

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

ファイルのステータス情報が取得されると、0 を返します。 戻り値-1 はエラーを示します。 ファイル記述子が有効でない場合または*バッファー*は**NULL**で説明されているとおり、無効なパラメーター ハンドラーが呼び出されます[パラメーターの検証](../../c-runtime-library/parameter-validation.md)です。 続けるには、実行が許可された場合**errno**に設定されている**EBADF**、無効なファイル記述子が場合または**EINVAL**場合は、*バッファー* **NULL**します。

## <a name="remarks"></a>Remarks

**_Fstat**関数に関連付けられている開いているファイルに関する情報を取得*fd*が指す構造体に格納*バッファー*します。 **_Stat** 、sys \stat.h で定義されている構造には、次のフィールドが含まれています。

|フィールド|説明|
|-|-|
| **st_atime** | ファイルの最後のアクセスの時間。 |
| **st_ctime** | ファイルの作成の時間。 |
| **st_dev** | デバイスの場合*fd*。 それ以外の場合に 0 です。 |
| **st_mode** | ファイル モード情報のビット マスク。 **_S_IFCHR**場合に設定されます*fd*デバイスを参照します。 **_S_IFREG**場合に設定されます*fd*は通常のファイルを参照します。 読み取り/書き込みのビットは、ファイルのアクセス許可モードに応じて設定されます。 **_S_IFCHR** sys \stat.h で他の定数が定義されているとします。 |
| **st_mtime** | ファイルの最終変更時刻。 |
| **st_nlink** | 非 NTFS ファイル システムでは常に 1 です。 |
| **st_rdev** | デバイスの場合*fd*。 それ以外の場合に 0 です。 |
| **st_size** | ファイルのサイズ (バイト単位)。 |

場合*fd*デバイスを参照、 **st_atime**、 **st_ctime**、 **st_mtime**、および**st_size**フィールドは、にとって意味がありません。

Stat.h は Types.h で定義される [_dev_t](../../c-runtime-library/standard-types.md) 型を使用するため、コードで Stat.h の前に Types.h を組み込む必要があります。

**_fstat64**、使用、 **_ _stat64**構造体をその他の関数しか 23時 59分: 59 年 1 月 18 日までの日付を表すファイルの作成日を UTC; 3000 年 12 月 31 日 23時 59分: 59 秒を表すことができますUTC の 2038 年。 これらの関数の日付範囲の下限は、いずれも 1970 年 1 月 1 日の午前 0 時です。

これらの関数のバリエーションは、32 ビットや 64 ビットの時刻型と、32 ビットや 64 ビットのファイル長をサポートします。 最初の数字のサフィックス (**32**または**64**) 時間のサイズを表します型の使用は、2 番目のサフィックスは**i32**または**i64**、。ファイル サイズが 32 ビットまたは 64 ビット整数として表されるかどうかを示すです。

**_fstat**と等価 **_fstat64i32**、および**構造体** **_stat** 64 ビットの時刻が含まれています。 これは、該当しない限り、 **_USE_32BIT_TIME_T**が定義されている場合、以前の動作が有効になります。**_fstat** 32 ビットの時刻を使用し、**構造体** **_stat** 32 ビットの時刻が含まれています。 場合も同様 **_fstati64**します。

### <a name="time-type-and-file-length-type-variations-of-stat"></a>_stat の時刻型とファイル長型のバリエーション

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
