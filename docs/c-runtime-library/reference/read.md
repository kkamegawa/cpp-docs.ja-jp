---
title: _read
ms.date: 02/13/2019
api_name:
- _read
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
- _read
helpviewer_keywords:
- data [CRT]
- _read function
- read function
- data [C++], reading
- reading data [C++]
- files [C++], reading
ms.assetid: 2ce9c433-57ad-47fe-9ac1-4a7d4c883d30
ms.openlocfilehash: 32238923aeef14230f68def15e27c676753faf61
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949532"
---
# <a name="_read"></a>_read

ファイルからデータを読み取ります。

## <a name="syntax"></a>構文

```C
int _read(
   int const fd,
   void * const buffer,
   unsigned const buffer_size
);
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
開いているファイルを参照するファイル記述子。

*バッファー*<br/>
データの格納場所。

*buffer_size*<br/>
読み取る最大バイト数。

## <a name="return-value"></a>戻り値

**_read**は、読み取ったバイト数を返します。これは、ファイルに残っている*buffer_size*バイトが少ない場合、またはファイルがテキストモードで開かれた場合、 *buffer_size*よりも小さくなることがあります。 テキストモードでは、各キャリッジリターンラインフィードの`\r\n`ペアが1つのラインフィード文字`\n`に置き換えられます。 戻り値には、単一行フィード文字だけがカウントされます。 この置き換えは、ファイル ポインターには影響しません。

この関数はファイルの終わりで読み取りをすると、0 を返します。 *Fd*が有効でない場合、ファイルが読み取り用に開かれていない場合、またはファイルがロックされている場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は-1 を返し、 **errno**を**EBADF**に設定します。

*Buffer*が**NULL**の場合、または*buffer_size* > **INT_MAX**の場合は、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は-1 を返し、 **errno**は**EINVAL**に設定されます。

このリターン コードとその他のリターン コードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Read**関数は、 *fd*に関連付けられているファイルから、最大*buffer_size*バイトを*バッファー*に読み込みます。 読み取り操作は、指定されたファイルに関連付けられたファイル ポインターの現在の位置で開始されます。 読み取り操作後、ファイル ポインターは、次の未読の文字を指します。

ファイルがテキストモードで開かれた場合、 **_read**が CTRL + Z 文字を検出すると、読み取りが終了します。これはファイルの終端インジケーターとして扱われます。 ファイルの終わりのインジケーターをクリアするには、[_lseek](lseek-lseeki64.md) を使用します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_read**|\<io.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

```C
// crt_read.c
/* This program opens a file named crt_read.txt
* and tries to read 60,000 bytes from
* that file using _read. It then displays the
* actual number of bytes read.
*/

#include <fcntl.h>      /* Needed only for _O_RDWR definition */
#include <io.h>
#include <stdlib.h>
#include <stdio.h>
#include <share.h>

char buffer[60000];

int main( void )
{
   int fh, bytesread;
   unsigned int nbytes = 60000;

   /* Open file for input: */
   if ( _sopen_s( &fh, "crt_read.txt", _O_RDONLY, _SH_DENYNO, 0 ))
   {
      perror( "open failed on input file" );
      exit( 1 );
   }

   /* Read in input: */
   if (( bytesread = _read( fh, buffer, nbytes )) <= 0 )
      perror( "Problem reading file" );
   else
      printf( "Read %u bytes from file\n", bytesread );

   _close( fh );
}
```

### <a name="input-crt_readtxt"></a>入力: crt_read.txt

```Input
Line one.
Line two.
```

### <a name="output"></a>Output

```Output
Read 19 bytes from file
```

## <a name="see-also"></a>関連項目

[下位入出力](../../c-runtime-library/low-level-i-o.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[fread](fread.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_write](write.md)<br/>
