---
title: fseek、_fseeki64
ms.date: 11/04/2016
api_name:
- _fseeki64
- fseek
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
- fseek
- _fseeki64
helpviewer_keywords:
- _fseeki64 function
- fseeki64 function
- fseek function
- file pointers [C++], moving
- file pointers [C++]
- seek file pointers
ms.assetid: f6bb1f8b-891c-426e-9e14-0e7e5c62df70
ms.openlocfilehash: e3da603c3c7f1b083ddb7f7f9577adae9be5e4f1
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956574"
---
# <a name="fseek-_fseeki64"></a>fseek、_fseeki64

指定した場所にファイル ポインターを移動します。

## <a name="syntax"></a>構文

```C
int fseek(
   FILE *stream,
   long offset,
   int origin
);
int _fseeki64(
   FILE *stream,
   __int64 offset,
   int origin
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
**FILE** 構造体へのポインター。

*オフセット*<br/>
*配信元*からのバイト数。

*配信元*<br/>
最初の位置。

## <a name="return-value"></a>戻り値

成功した場合、 **fseek**と **_fseeki64**は0を返します。 それ以外の場合は、0 以外の値を返します。 シーク非対応のデバイスでは、戻り値は未定義です。 *Stream*が null ポインターの場合、または*origin*が以下で説明する許可値のいずれでもない場合、 **fseek**と **_fseeki64**は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は**errno**を**EINVAL**に設定し、-1 を返します。

## <a name="remarks"></a>Remarks

**Fseek**関数と **_fseeki64**関数は、*ストリーム*に関連付けられているファイルポインター (存在する場合) を、*原点*からの*オフセット*バイトである新しい場所に移動します。 ストリームの次の操作は、新しい場所で行われます。 更新用に開かれているストリームでの次の操作は読み取りまたは書き込みのいずれかです。 引数の*origin*は、STDIO で定義されている、次の定数のいずれかである必要があります。始め

|配信元の値|説明|
|-|-|
| **SEEK_CUR** | ファイル ポインターの現在の位置。 |
| **SEEK_END** | EOF (ファイル終端)。 |
| **SEEK_SET** | ファイルの先頭。 |

**Fseek**と **_fseeki64**を使用して、ファイル内の任意の場所にポインターを移動できます。 ポインターは、ファイルの末尾を越えて配置することもできます。 **fseek**と **_fseeki64**は、ファイルの終端のインジケーターをクリアし、*ストリーム*に対する以前の[ungetc](ungetc-ungetwc.md)呼び出しの効果を否定します。

データを追加するためにファイルを開く場合、現在のファイルの位置は、次の書き込みが発生する場所ではなく最後の I/O 操作によって決まります。 追加のために開かれたファイルで I/O 操作がまだ発生していない場合、ファイルの位置はファイルの先頭です。

テキストモードで開かれたストリームの場合、 **fseek**と **_fseeki64**の使用は限られています。これは、キャリッジリターンラインフィードの変換によって、 **fseek**と **_fseeki64**が予期しない結果を生成する可能性があるためです。 テキストモードで開かれたストリームで動作することが保証されている**fseek**操作と **_fseeki64**操作は次のとおりです。

- 元の値のいずれかに対して相対的なオフセット 0 でシークします。

- **_Fseeki64**を使用するときに**fseek**または[_ftelli64](ftell-ftelli64.md)を使用する場合に、 [ftell](ftell-ftelli64.md)の呼び出しから返されるオフセット値を使用して、ファイルの先頭からシークします。

テキスト モードでも、Ctrl + Z は入力時に EOF (EOF: end-of-file) 文字として解釈されます。 読み取り/書き込み用に開かれたファイルでは、 [fopen](fopen-wfopen.md)と関連するすべてのルーチンで、ファイルの末尾に CTRL + Z があるかどうかを確認し、可能であれば削除します。 これは、 **fseek**と[ftell](ftell-ftelli64.md)または **_fseeki64**と[_ftelli64](ftell-ftelli64.md)の組み合わせを使用して、CTRL + Z で終わるファイル内を移動すると、の末尾付近で**fseek**または **_fseeki64**が正しく動作しない可能性があるためです。拡張子.

バイト オーダー マーク (BOM) で始まるファイルを CRT で開くときには、ファイル ポインターは BOM の後ろ (つまり、ファイルの実際のコンテンツの開始位置) に配置されます。 ファイルの先頭を**fseek**する必要がある場合は、 [ftell](ftell-ftelli64.md)を使用して最初の位置を取得し、0の位置ではなく**fseek**を使用します。

この関数では、実行中に他のスレッドをロックするので、スレッド セーフです。 ロックしないバージョンについては、「[_fseek_nolock、_fseeki64_nolock](fseek-nolock-fseeki64-nolock.md)」を参照してください。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**fseek**|\<stdio.h>|
|**_fseeki64**|\<stdio.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_fseek.c
// This program opens the file FSEEK.OUT and
// moves the pointer to the file's beginning.

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char line[81];
   int  result;

   if ( fopen_s( &stream, "fseek.out", "w+" ) != 0 )
   {
      printf( "The file fseek.out was not opened\n" );
      return -1;
   }
   fprintf( stream, "The fseek begins here: "
                    "This is the file 'fseek.out'.\n" );
   result = fseek( stream, 23L, SEEK_SET);
   if( result )
      perror( "Fseek failed" );
   else
   {
      printf( "File pointer is set to middle of first line.\n" );
      fgets( line, 80, stream );
      printf( "%s", line );
    }
   fclose( stream );
}
```

```Output
File pointer is set to middle of first line.
This is the file 'fseek.out'.
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[ftell、_ftelli64](ftell-ftelli64.md)<br/>
[_lseek、_lseeki64](lseek-lseeki64.md)<br/>
[rewind](rewind.md)<br/>
