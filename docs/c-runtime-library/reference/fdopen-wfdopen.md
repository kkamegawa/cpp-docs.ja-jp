---
title: _fdopen、_wfdopen
ms.date: 12/12/2017
api_name:
- _fdopen
- _wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
ms.openlocfilehash: 5202c84cd1a9038faf68587f9207d376ed8c0af1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941255"
---
# <a name="_fdopen-_wfdopen"></a>_fdopen、_wfdopen

ストリームを前回下位入出力で開いたファイルに関連付けます。

## <a name="syntax"></a>構文

```C
FILE *_fdopen(
   int fd,
   const char *mode
);
FILE *_wfdopen(
   int fd,
   const wchar_t *mode
);
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
開いているファイルのファイル記述子。

*モード*<br/>
ファイル アクセスの種類。

## <a name="return-value"></a>戻り値

これらの各関数は、開いているストリームへのポインターを返します。 エラーが発生すると、NULL のポインター値を返します。 エラーが発生した場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているとおり、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno**は無効なファイル記述子を示す**EBADF**に設定されるか、または*モード*が null ポインターであることを示す**EINVAL**に設定されます。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Fdopen**関数は、 *fd*によって識別されるファイルに i/o ストリームを関連付けます。これにより、低レベル i/o 用に開かれているファイルをバッファーおよびフォーマットできるようになります。 **_wfdopen**は、 **_fdopen**のワイド文字バージョンです。 **_wfdopen**の*mode*引数は、ワイド文字列です。 **_wfdopen**と **_fdopen**は同じように動作します。

**_Fdopen**に渡されるファイル記述子は、返され**た&#42;ファイル**ストリームによって所有されます。 **_Fdopen**が成功した場合は、ファイル記述子の[ \_close](close.md)を呼び出さないでください。 返された**ファイル&#42;** で[fclose](fclose-fcloseall.md)を呼び出すと、ファイル記述子も閉じられます。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|\_UNICODE および\_MBCS が定義されていません|\_定義済みの MBCS|\_UNICODE 定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

*モード*文字列は、ファイルに対して要求されるファイルアクセスの種類を指定します。

| *モード* | アクセス |
|--------|--------|
| **"r"** | 読み取り用に開きます。 ファイルが存在しないか見つからない場合、 **fopen**呼び出しは失敗します。 |
| **"w"** | 書き込み用に空のファイルを開きます。 指定したファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **"a"** | ファイルの末尾に書き込みを行うために開きます (追加)。 ファイルが存在しない場合は、作成します。 |
| **"r+"** | 読み取りと書き込みの両方のモードで開きます。 ファイルが存在している必要があります。 |
| **"w+"** | 読み取りと書き込みの両方のモードで空のファイルを開きます。 そのファイルが既に存在すると、そのファイルの内容は破棄されます。 |
| **"a+"** | 読み取りと追加の両方のモードでファイルを開きます。 ファイルが存在しない場合は、作成します。 |

**"A"** または **"a +"** アクセスの種類を使用してファイルを開くと、すべての書き込み操作がファイルの末尾で行われます。 ファイルポインターは、 [fseek](fseek-fseeki64.md)または[rewind](rewind.md)を使用して移動できますが、書き込み操作が実行される前に、常にファイルの末尾に戻されます。したがって、既存のデータは上書きされません。 **"R +"** 、 **"w +"** 、または **"a +"** のアクセスの種類が指定されている場合は、読み取りと書き込みの両方が許可されます (ファイルは "更新" 用に開かれていると言います)。 ただし、読み取りと書き込みを切り替える場合は、複数の[fflush](fflush.md)、 [fsetpos](fsetpos.md)、 [fseek](fseek-fseeki64.md)、または[rewind](rewind.md)操作が必要です。 必要に応じて、 [fsetpos](fsetpos.md)または[fseek](fseek-fseeki64.md)操作の現在位置を指定できます。

上記の値に加えて、次の文字を*モード*で使用して、改行文字の変換モードを指定することもできます。

| *モード*修飾子 | 動作 |
|-----------------|----------|
| **t** | ファイルをテキスト (変換) モードで開きます。 このモードでは、復帰と改行 (CR-LF) の組み合わせは入力時に 1 つの改行 (LF) 文字に変換され、LF 文字は出力時に CR-LF の組み合わせに変換されます。 また、Ctrl + Z は入力時に EOF (end-of-file) 文字として解釈されます。 |
| **b** | バイナリ (無変換) モードで開きます。 **T**モードからの変換は抑制されます。 |
| **c** | 関連付けられている*ファイル名*のコミットフラグを有効にして、 **fflush**または **_flushall**が呼び出された場合に、ファイルバッファーの内容がディスクに直接書き込まれるようにします。 |
| **n** | 関連付けられている*ファイル名*のコミットフラグを "コミットなし" にリセットします。 既定値です。 プログラムを Commode.obj とリンクする場合は、グローバル コミット フラグもオーバーライドします。プログラムを明示的に Commode.obj とリンクしない場合、グローバル コミット フラグの既定の設定は "コミットなし" です。 |

**T**、 **c**、および**n** *モード*オプションは、Microsoft extensions for **fopen** and **_fdopen**です。 ANSI の移植性を維持する場合には使用しないでください。

**T**または**b**を*モード*で指定しない場合、既定の変換モードはグローバル変数[ \_fmode](../../c-runtime-library/fmode.md)によって定義されます。 **T**または**b**が引数の前に付加されている場合、関数は失敗し、NULL を返します。 テキスト モードと binary モードの詳細については、「[テキスト モードとバイナリ モードのファイル入出力](../../c-runtime-library/text-and-binary-mode-file-i-o.md)」を参照してください。

**Fopen**と **_fdopen**で使用される*モード*文字列に有効な文字は、次の表に示すように、 [ \_open](open-wopen.md)および[ \_sopen](sopen-wsopen.md)で使用される*oflag*引数に対応しています。

|*Mode*文字列の文字|**_Open**と **_sopen**に相当する*oflag*値|
|---------------------------------|---------------------------------------------------|
|**a**|**\_&#124; O wronly\_oAPPEND\_(通常は o wronly\_** **oが\_ o を付ける&#124; \_\_\_ \_ &#124; \_追加**)|
|**+**|**\_O\_ &#124; RDWRoappend\_(通常は o RDWR o append \_**  **&#124; \_\_ &#124; \_\_ \_\_** )|
|**r**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_wronly (通常**、o  **\_ &#124; &#124; wronly \_oは\_oTRUNC)\_\_ \_**|
|**w +**|**\_O\_RDWR**  **\_ (通常\_は o &#124; RDWR o&#124; TRUNC を持っている)\_ \_\_\_**|
|**b**|**\_O\_バイナリ**|
|**t**|**\_O\_TEXT**|
|**c**|なし|
|**n**|なし|

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```c
// crt_fdopen.c
// This program opens a file by using low-level
// I/O, then uses _fdopen to switch to stream
// access. It counts the lines in the file.

#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>
#include <share.h>

int main( void )
{
   FILE *stream;
   int  fd, count = 0;
   char inbuf[128];

   // Open a file.
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
      exit( 1 );

   // Get stream from file descriptor.
   if( (stream = _fdopen( fd, "r" )) == NULL )
      exit( 1 );

   while( fgets( inbuf, 128, stream ) != NULL )
      count++;

   // After _fdopen, close by using fclose, not _close.
   fclose( stream );
   printf( "Lines in file: %d\n", count );
}
```

### <a name="input-crt_fdopentxt"></a>入力: crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>Output

```Output
Lines in file: 2
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[\_dup、 \_dup2](dup-dup2.md)<br/>
[fclose、 \_fcloseall](fclose-fcloseall.md)<br/>
[fopen、 \_すべてのファイルを開く](fopen-wfopen.md)<br/>
[freopen、 \_wfreopen](freopen-wfreopen.md)<br/>
[\_開く、 \_wopen](open-wopen.md)<br/>
