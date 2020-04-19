---
title: _utime、_utime32、_utime64、_wutime、_wutime32、_wutime64
ms.date: 11/04/2016
api_name:
- _utime64
- _utime
- _wutime
- _wutime64
- _wutime32
- _utime32
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
- _tutime
- _utime64
- wutime
- utime32
- wutime64
- _utime
- wutime32
- _wutime
- utime
- utime64
- _wutime64
- _utime32
- _tutime64
- _wutime32
helpviewer_keywords:
- tutime function
- utime32 function
- utime64 function
- _utime function
- _tutime32 function
- time [C++], file modification
- wutime function
- _wutime function
- _wutime32 function
- _tutime64 function
- _tutime function
- files [C++], modification time
- _wutime64 function
- _utime32 function
- utime function
- _utime64 function
- wutime64 function
- wutime32 function
- tutime64 function
- tutime32 function
ms.assetid: 8d482d40-19b9-4591-bfee-5d7f601d1a9e
ms.openlocfilehash: d55261b59dbf201be9869f3ab9ced2d2cbab5e02
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70945730"
---
# <a name="_utime-_utime32-_utime64-_wutime-_wutime32-_wutime64"></a>_utime、_utime32、_utime64、_wutime、_wutime32、_wutime64

ファイルの変更時刻を設定します。

## <a name="syntax"></a>構文

```C
int _utime(
   const char *filename,
   struct _utimbuf *times
);
int _utime32(
   const char *filename,
   struct __utimbuf32 *times
);
int _utime64(
   const char *filename,
   struct __utimbuf64 *times
);
int _wutime(
   const wchar_t *filename,
   struct _utimbuf *times
);
int _wutime32(
   const wchar_t *filename,
   struct __utimbuf32 *times
);
int _wutime64(
   const wchar_t *filename,
   struct __utimbuf64 *times
);
```

### <a name="parameters"></a>パラメーター

*ファイル名*<br/>
パスまたはファイル名を含む文字列へのポインター。

*複数*<br/>
格納されている時刻値へのポインター。

## <a name="return-value"></a>戻り値

これらの各関数は、ファイルの変更時刻が変更されると、0 を返します。 戻り値-1 はエラーを示します。 無効なパラメーターが渡された場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているとおり、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は-1 を返し、 **errno**は次のいずれかの値に設定されます。

|errno の値|条件|
|-|-|
| **EACCES** | パスにディレクトリまたは読み取り専用ファイルが指定されている |
| **EINVAL** | *時刻*引数が無効です |
| **EMFILE** | 開いているファイルが多すぎる (変更時刻を変更するにはファイルを開く必要があります) |
| **ENOENT** | パスまたはファイル名が見つからない |

リターン コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

変更日が 1970 年 1 月 1 日午前 0 時以降で、使用する関数の終了日より前の場合、ファイルの日付を変更できます。 **_utime**と **_wutime**は64ビットの時刻値を使用するため、終了日は23:59:59、3000、UTC です。 **_USE_32BIT_TIME_T**が以前の動作を強制するように定義されている場合、終了日は23:59:59 年1月18日 2038 UTC です。 **_utime32**または **_Wutime32**は、 **_USE_32BIT_TIME_T**が定義されているかどうかに関係なく32ビットの時刻型を使用し、常に前の終了日を保持します。 **_utime64**または **_wutime64**は常に64ビットの時刻型を使用するため、これらの関数は常に後の終了日をサポートします。

## <a name="remarks"></a>Remarks

**_Utime**関数は、 *filename*によって指定されたファイルの変更時刻を設定します。 プロセスは、時刻を変更するために、ファイルに対して書き込みアクセス権が必要です。 Windows オペレーティングシステムでは、 **_utimbuf**構造体のアクセス時間と変更時間を変更できます。 *Times*が**NULL**ポインターの場合、変更時刻は現在の現地時刻に設定されます。 それ以外の場合、*時刻*は **_utimbuf**型の構造体を指す必要があります。 SYS\UTIME. で定義されています。始め.

**_Utimbuf**構造体は、ファイル変更日付を変更するために **_utime**によって使用されるファイルアクセスおよび変更時刻を格納します。 構造体には、次のフィールドがあります。このフィールドは、両方とも**time_t**型です。

| フィールド |   |
|-------|---|
| **actime** | ファイルへのアクセス時刻 |
| **modtime** | ファイルの変更時刻 |

**_Utimbuf**構造体の特定のバージョン ( **_utimebuf32**と **__utimbuf64**) は、時刻型の32ビットバージョンと64ビットバージョンを使用して定義されます。 これらは、この関数の 32 ビットおよび 64 ビットの特定バージョンで使用されます。 **_USE_32BIT_TIME_T**が定義されていない場合は、既定で **_utimbuf**自体が64ビットの時刻型を使用します。

**_utime**は **_futime**と同じですが、 **_utime**の*filename*引数が、開いているファイルのファイル記述子ではなく、ファイル名またはファイルへのパスである点が異なります。

**_wutime**は、 **_utime**のワイド文字バージョンです。 **_wutime**の*filename*引数はワイド文字列です。 それ以外では、これらの関数の動作は同じです。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tutime**|**_utime**|**_utime**|**_wutime**|
|**_tutime32**|**_utime32**|**_utime32**|**_wutime32**|
|**_tutime64**|**_utime64**|**_utime64**|**_wutime64**|

## <a name="requirements"></a>必要条件

|ルーチン|必須ヘッダー|省略可能なヘッダー|
|-------------|----------------------|----------------------|
|**_utime**、 **_utime32**、 **_utime64**|\<sys/utime.h>|\<errno.h>|
|**_utime64**|\<sys/utime.h>|\<errno.h>|
|**_wutime**|\<utime.h> または \<wchar.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

このプログラムは、 **_utime**を使用して、ファイルの変更時刻を現在の時刻に設定します。

```C
// crt_utime.c
#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/utime.h>
#include <time.h>

int main( void )
{
   struct tm tma = {0}, tmm = {0};
   struct _utimbuf ut;

   // Fill out the accessed time structure
   tma.tm_hour = 12;
   tma.tm_isdst = 0;
   tma.tm_mday = 15;
   tma.tm_min = 0;
   tma.tm_mon = 0;
   tma.tm_sec = 0;
   tma.tm_year = 103;

   // Fill out the modified time structure
   tmm.tm_hour = 12;
   tmm.tm_isdst = 0;
   tmm.tm_mday = 15;
   tmm.tm_min = 0;
   tmm.tm_mon = 0;
   tmm.tm_sec = 0;
   tmm.tm_year = 102;

   // Convert tm to time_t
   ut.actime = mktime(&tma);
   ut.modtime = mktime(&tmm);

   // Show file time before and after
   system( "dir crt_utime.c" );
   if( _utime( "crt_utime.c", &ut ) == -1 )
      perror( "_utime failed\n" );
   else
      printf( "File time modified\n" );
   system( "dir crt_utime.c" );
}
```

### <a name="sample-output"></a>出力例

```Output
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/09/2003  05:38 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
File time modified
Volume in drive C has no label.
Volume Serial Number is 9CAC-DE74

Directory of C:\test

01/15/2002  12:00 PM               935 crt_utime.c
               1 File(s)            935 bytes
               0 Dir(s)  20,742,955,008 bytes free
```

## <a name="see-also"></a>関連項目

[時間管理](../../c-runtime-library/time-management.md)<br/>
[asctime、_wasctime](asctime-wasctime.md)<br/>
[ctime、_ctime32、_ctime64、_wctime、_wctime32、_wctime64](ctime-ctime32-ctime64-wctime-wctime32-wctime64.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_ftime、_ftime32、_ftime64](ftime-ftime32-ftime64.md)<br/>
[_futime、_futime32、_futime64](futime-futime32-futime64.md)<br/>
[gmtime、_gmtime32、_gmtime64](gmtime-gmtime32-gmtime64.md)<br/>
[localtime、_localtime32、_localtime64](localtime-localtime32-localtime64.md)<br/>
[_stat、_wstat 関数](stat-functions.md)<br/>
[time、_time32、_time64](time-time32-time64.md)<br/>
