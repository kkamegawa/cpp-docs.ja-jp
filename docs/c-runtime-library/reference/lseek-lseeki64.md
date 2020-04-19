---
title: _lseek、_lseeki64
ms.date: 11/04/2016
api_name:
- _lseeki64
- _lseek
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lseeki64
- _lseek
- lseeki64
helpviewer_keywords:
- lseek function
- _lseek function
- _lseeki64 function
- lseeki64 function
- file pointers [C++], moving
- seek file pointers
ms.assetid: aba8a768-d40e-48c3-b38e-473dbd782f93
ms.openlocfilehash: 67bcce2a9936cd09973e8ddf1828704944866439
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952985"
---
# <a name="_lseek-_lseeki64"></a>_lseek、_lseeki64

指定した場所にファイル ポインターを移動します。

## <a name="syntax"></a>構文

```C
long _lseek(
   int fd,
   long offset,
   int origin
);
__int64 _lseeki64(
   int fd,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
開いているファイルを参照するファイル記述子。

*オフセット*<br/>
*配信元*からのバイト数。

*配信元*<br/>
最初の位置。

## <a name="return-value"></a>戻り値

**_lseek**は、ファイルの先頭からの新しい位置のオフセットをバイト単位で返します。 **_lseeki64**は、64ビット整数のオフセットを返します。 この関数は、エラーを示す-1L を返します。 不適切なファイル記述子、*origin* の値が無効、*オフセット*によって指定された位置がファイルの開始より前であるなど、無効なパラメーターが渡された場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」の説明にあるとおり、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は**errno**を**EBADF**に設定し、-1l を返します。 (ターミナルやポインターなどの) シーク非対応のデバイスでは、戻り値は未定義です。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Lseek**関数は、 *fd*に関連付けられたファイルポインターを、*原点*から*オフセット*バイトである新しい場所に移動します。 ファイルの次の操作は、新しい場所で行われます。 *origin* 引数は、Stdio.h で定義されている、次の定数のいずれかである必要があります。

|*配信元*の値||
|-|-|
| **SEEK_SET** | ファイルの先頭。 |
| **SEEK_CUR** | ファイル ポインターの現在の位置。 |
| **SEEK_END** | EOF (ファイル終端)。 |

**_Lseek**を使用すると、ファイルの任意の場所またはファイルの末尾を越える位置にポインターを移動できます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_lseek**|\<io.h>|
|**_lseeki64**|\<io.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_lseek.c
/* This program first opens a file named lseek.txt.
* It then uses _lseek to find the beginning of the file,
* to find the current position in the file, and to find
* the end of the file.
*/

#include <io.h>
#include <fcntl.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

int main( void )
{
   int fh;
   long pos;               /* Position of file pointer */
   char buffer[10];

   _sopen_s( &fh, "crt_lseek.c_input", _O_RDONLY, _SH_DENYNO, 0 );

   /* Seek the beginning of the file: */
   pos = _lseek( fh, 0L, SEEK_SET );
   if( pos == -1L )
      perror( "_lseek to beginning failed" );
   else
      printf( "Position for beginning of file seek = %ld\n", pos );

   /* Move file pointer a little */
    _read( fh, buffer, 10 );

   /* Find current position: */
   pos = _lseek( fh, 0L, SEEK_CUR );
   if( pos == -1L )
      perror( "_lseek to current position failed" );
   else
      printf( "Position for current position seek = %ld\n", pos );

   /* Set the end of the file: */
   pos = _lseek( fh, 0L, SEEK_END );
   if( pos == -1L )
      perror( "_lseek to end failed" );
   else
      printf( "Position for end of file seek = %ld\n", pos );

   _close( fh );
}
```

### <a name="input-crt_lseekc_input"></a>入力: crt_lseek.c_input

```Input
Line one.
Line two.
Line three.
Line four.
Line five.
```

### <a name="output"></a>Output

```Output
Position for beginning of file seek = 0
Position for current position seek = 10
Position for end of file seek = 57
```

## <a name="see-also"></a>関連項目

[下位入出力](../../c-runtime-library/low-level-i-o.md)<br/>
[fseek、_fseeki64](fseek-fseeki64.md)<br/>
[_tell、_telli64](tell-telli64.md)<br/>
