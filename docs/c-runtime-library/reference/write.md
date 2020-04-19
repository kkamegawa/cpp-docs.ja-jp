---
title: _write
ms.date: 11/04/2016
api_name:
- _write
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
- _write
helpviewer_keywords:
- _write function
- write function
- files [C++], writing to
ms.assetid: 7b868c33-766f-4e1a-95a7-e8d25f0604c4
ms.openlocfilehash: 5eaee64c1bf6ad4b4d59c3a7b1a1434741e74454
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821793"
---
# <a name="_write"></a>_write

ファイルにデータを書き込みます。

## <a name="syntax"></a>構文

```C
int _write(
   int fd,
   const void *buffer,
   unsigned int count
);
```

### <a name="parameters"></a>パラメーター

*fd*<br/>
データを書き込むファイルのファイル記述子。

*バッファー*<br/>
書き込むデータ。

*count*<br/>
バイト数。

## <a name="return-value"></a>戻り値

成功した場合、 **_write**は書き込まれたバイト数を返します。 ディスク上に残っている実際の領域が、関数がディスクに書き込もうとしているバッファーのサイズよりも小さい場合、 **_write**は失敗し、バッファーの内容はディスクにフラッシュされません。 戻り値-1 はエラーを示します。 無効なパラメーターが渡されると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、この関数は無効なパラメーター ハンドラーを呼び出します。 実行の継続が許可された場合、この関数は-1 を返し、 **errno**は3つの値のいずれかに設定され**ます。これは、ファイル**記述子が無効であるか、ファイルが書き込み用に開かれていないことを意味します。**ENOSPC**。これは、操作に必要な領域がデバイスに残っていないことを意味します。または**EINVAL**。*バッファー*が null ポインターであるか、また*は奇数のバイト数が*Unicode モードでファイルに書き込まれるように渡されたことを示します。

これらのリターン コードとその他のリターン コードの詳細については、「[errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

ファイルがテキストモードで開かれている場合、各ラインフィード文字は出力のキャリッジリターンラインフィードのペアで置き換えられます。 置換は戻り値には影響しません。

ファイルが Unicode 変換モードで開かれている場合 (たとえば、 **_open**または **_sopen**と、 **_O_WTEXT**、 **_O_U16TEXT**、または **_O_U8TEXT**を含むモードパラメーターを使用して*fd*が開かれている場合、または**fopen**を使用して開かれており、かつ、 **ccs = unicode**、 **ccs = 16LE**、または**ccs**を含むモードパラメーター**を使用し**て開かれている場合は、*バッファー*はへのポインターと解釈されます**utf-16**データを含む**wchar_t**の配列。 このモードで奇数バイトの書き込みを試みると、パラメーター検証エラーが発生します。

## <a name="remarks"></a>Remarks

**_Write**関数は、*バッファー*のバイト*数*を*fd*に関連付けられたファイルに書き込みます。 書き込み操作は、指定されたファイルに関連付けられたファイル ポインター (存在する場合) の現在の位置で開始されます。 ファイルが追加用に開かれている場合、操作はファイルの現在の末尾で開始されます。 書き込み操作の後、ファイルポインターは、書き込まれたバイト数だけ増加します。

テキストモードで開かれたファイルに書き込む場合、 **_write**は CTRL + Z 文字をファイルの論理終端として扱います。 デバイスに書き込む場合、 **_write**はバッファー内の CTRL + Z 文字を出力ターミネータとして扱います。

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_write**|\<io.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>使用例

```C
// crt__write.c
//
// This program opens a file for output and uses _write to write
// some bytes to the file.

#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <fcntl.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <errno.h>
#include <share.h>

char buffer[] = "This is a test of '_write' function";

int main( void )
{
   int         fileHandle = 0;
   unsigned    bytesWritten = 0;

   if ( _sopen_s(&fileHandle, "write.o", _O_RDWR | _O_CREAT,
                  _SH_DENYNO, _S_IREAD | _S_IWRITE) )
      return -1;

   if (( bytesWritten = _write( fileHandle, buffer, sizeof( buffer ))) == -1 )
   {
      switch(errno)
      {
         case EBADF:
            perror("Bad file descriptor!");
            break;
         case ENOSPC:
            perror("No space left on device!");
            break;
         case EINVAL:
            perror("Invalid parameter: buffer was NULL!");
            break;
         default:
            // An unrelated error occurred
            perror("Unexpected error!");
      }
   }
   else
   {
      printf_s( "Wrote %u bytes to file.\n", bytesWritten );
   }
   _close( fileHandle );
}
```

```Output
Wrote 36 bytes to file.
```

## <a name="see-also"></a>関連項目

[下位入出力](../../c-runtime-library/low-level-i-o.md)<br/>
[fwrite](fwrite.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_read](read.md)<br/>
[_setmode](setmode.md)<br/>
