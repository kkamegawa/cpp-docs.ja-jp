---
title: realloc
ms.date: 11/04/2016
api_name:
- realloc
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
- api-ms-win-crt-heap-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _brealloc
- _nrealloc
- realloc
- _frealloc
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
ms.openlocfilehash: 6197b7bca3ec9f416696e1ded8ea5ca813392616
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949496"
---
# <a name="realloc"></a>realloc

メモリ ブロックを再割り当てします。

## <a name="syntax"></a>構文

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>パラメーター

*memblock*<br/>
以前に割り当てられたメモリ ブロックへのポインター。

*size*<br/>
新しいサイズ (バイト単位)。

## <a name="return-value"></a>戻り値

**realloc**は、再割り当てされた (移動される可能性もある) メモリブロックへの**void**ポインターを返します。

指定されたサイズまでブロックを拡張するのに十分なメモリがない場合、元のブロックは変更されず、 **NULL**が返されます。

*Size*が0の場合、 *memblock*が指すブロックは解放されます。戻り値は**NULL**で、 *memblock*は解放されたブロックを指しています。

戻り値は、どの型のオブジェクトを格納する場合でも適切なアラインメントが保証されるストレージ領域を指します。 **Void**以外の型へのポインターを取得するには、戻り値に型キャストを使用します。

## <a name="remarks"></a>Remarks

**Realloc**関数は、割り当てられたメモリブロックのサイズを変更します。 *Memblock*引数は、メモリブロックの先頭を指します。 *Memblock*が**NULL**の場合、 **realloc**は**malloc**と同じように動作し、*サイズ*バイトの新しいブロックを割り当てます。 *Memblock*が**NULL**でない場合は、 **calloc**、 **malloc**、または**realloc**の前の呼び出しによって返されたポインターである必要があります。

*Size*引数は、ブロックの新しいサイズをバイト単位で示します。 新旧のサイズのうち、小さい方のブロックの内容は変更されませんが、新しいブロックの場所は異なる場合があります。 新しいブロックは新しいメモリ位置にある可能性があるため、 **realloc**によって返されるポインターは、 *memblock*引数を通じて渡されるポインターであるとは限りません。 バッファーのサイズが増加した場合、 **realloc**は、新しく割り当てられたメモリをゼロにしません。

**realloc**は、メモリ割り当てが失敗した場合、または要求されたメモリの量が **_HEAP_MAXREQ**を超えた場合に、 **errno**を**ENOMEM**に設定します。 その他のエラー コードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

**realloc**は 、 C++ [_set_new_mode](set-new-mode.md)関数を使用して新しいハンドラーモードを設定するために malloc を呼び出します。 新しいハンドラーモードは、エラー発生時に、 **malloc**が、 [_set_new_handler](set-new-handler.md)によって設定された新しいハンドラールーチンを呼び出すかどうかを示します。 既定では、 **malloc**は、メモリの割り当てに失敗したときに新しいハンドラールーチンを呼び出しません。 この既定の動作をオーバーライドして、 **realloc**がメモリの割り当てに失敗したときに、 **new**演算子が同じ理由で失敗したときと同じ方法で新しいハンドラールーチン**を呼び出す**ことができます。 既定の動作をオーバーライドするには、次の関数を呼び出します。

```C
_set_new_mode(1);
```

この呼び出しはプログラムの最初の方で指定するか、NEWMODE.OBJ にリンクします (「[リンク オプション](../../c-runtime-library/link-options.md)」を参照してください)。

アプリケーションが C ランタイムライブラリのデバッグバージョンにリンクされている場合、 **realloc**は[_realloc_dbg](realloc-dbg.md)に解決されます。 デバッグ プロセス中のヒープの管理方法の詳細については、「[CRT デバッグ ヒープ](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。

**realloc**はと`__declspec(noalias)` `__declspec(restrict)`マークされています。つまり、関数はグローバル変数を変更せず、返されるポインターがエイリアス化されていないことが保証されます。 詳細については、「[noalias](../../cpp/noalias.md)」、および「[restrict](../../cpp/restrict.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**realloc**|\<stdlib.h> と \<malloc.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_realloc.c
// This program allocates a block of memory for
// buffer and then uses _msize to display the size of that
// block. Next, it uses realloc to expand the amount of
// memory used by buffer and then calls _msize again to
// display the new amount of memory allocated to buffer.

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   long *buffer, *oldbuffer;
   size_t size;

   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )
      exit( 1 );

   size = _msize( buffer );
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );

   // Reallocate and show new size:
   oldbuffer = buffer;     // save pointer in case realloc fails
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))
        ==  NULL )
   {
      free( oldbuffer );  // free original block
      exit( 1 );
   }
   size = _msize( buffer );
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",
            size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after malloc of 1000 longs: 4000
Size of block after realloc of 1000 more longs: 8000
```

## <a name="see-also"></a>関連項目

[メモリ割り当て](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[malloc](malloc.md)<br/>
