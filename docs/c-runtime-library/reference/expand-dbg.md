---
title: _expand_dbg
ms.date: 11/04/2016
api_name:
- _expand_dbg
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- expand_dbg
- _expand_dbg
helpviewer_keywords:
- memory blocks, changing size
- expand_dbg function
- _expand_dbg function
ms.assetid: dc58c91f-72a8-48c6-b643-fe130fb6c1fd
ms.openlocfilehash: 836b9cffcf0367f248a14469b30c1a355e2bdec2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941576"
---
# <a name="_expand_dbg"></a>_expand_dbg

ブロックの拡張や縮小によって、ヒープ内の指定されたメモリのブロックをサイズ変更します (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
void *_expand_dbg(
   void *userData,
   size_t newSize,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*userData*<br/>
以前に割り当てられていたメモリ ブロックへのポインター。

*newSize*<br/>
ブロックのために要求する新しいサイズ (バイト単位)。

*blockType*<br/>
サイズ変更されたブロックの要求された型: **_CLIENT_BLOCK**または **_NORMAL_BLOCK**。

*ファイル名*<br/>
拡張操作を要求したソースファイルの名前へのポインターまたは**NULL**。

*行番号*<br/>
展開操作が要求されたソースファイル内の行番号または**NULL**。

*Filename*パラメーターと*linenumber*パラメーターは、 **_expand_dbg**が明示的に呼び出された場合、または[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)プリプロセッサ定数が定義されている場合にのみ使用できます。

## <a name="return-value"></a>戻り値

正常に完了すると、 **_expand_dbg**は、サイズ変更されたメモリブロックへのポインターを返します。 メモリが移動されないため、アドレスは userData と同じです。 エラーが発生したか、要求されたサイズまでブロックを拡張できなかった場合は、 **NULL**を返します。 エラーが発生した場合、 **errno**には、エラーの性質に関するオペレーティングシステムからの情報が含まれます。 **Errno**の詳細については、「 [errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

**_Expand_dbg**関数は、_[expand](expand.md)関数のデバッグバージョンです。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_expand_dbg**の各呼び出しは **_expand**の呼び出しに限定されます。 **_Expand**と **_expand_dbg**はどちらもベースヒープ内のメモリブロックのサイズを変更しますが、 **_expand_dbg**にはいくつかのデバッグ機能があります。リークをテストするために、ブロックのユーザー部分の両側のバッファーを使用します。割り当て要求の発生元を特定するための、特定の割り当ての種類と*filename*/*linenumber*情報。

**_expand_dbg**は、指定されたメモリブロックのサイズを、要求された*newSize*よりもわずかに増やします。 *newSize*が、最初に割り当てられたメモリブロックのサイズより大きいか小さい可能性があります。 追加の領域は、デバッグ メモリ ブロックをリンクし、アプリケーションにデバッグ ヘッダー情報と上書きバッファーを提供するために、デバッグ ヒープ マネージャーによって使用されます。 サイズ変更は、元のメモリ ブロックを拡張または縮小することで実現されます。 **_expand_dbg**は、 [_realloc_dbg](realloc-dbg.md)関数と同様に、メモリブロックを移動しません。

*NewSize*が元のブロックサイズよりも大きい場合、メモリブロックは拡張されます。 拡張中に、要求されたサイズに合わせてメモリブロックを拡張できない場合は、 **NULL**が返されます。 *NewSize*が元のブロックサイズよりも小さい場合、メモリブロックは新しいサイズが取得されるまでコントラクトされます。

デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 割り当てブロック型と、それらがどのように使用されるかについては、「[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 標準で呼び出すヒープ関数と、アプリケーションのデバッグ ビルドで呼び出すデバッグ バージョンのヒープ関数との違いの詳細については、「[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)」をご覧ください。

この関数は、パラメーターを検証します。 *Memblock*が null ポインターの場合、または Size が **_HEAP_MAXREQ**より大きい場合、この関数は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、 **errno**は**EINVAL**に設定され、関数は**NULL**を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_expand_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="example"></a>例

```C
// crt_expand_dbg.c
//
// This program allocates a block of memory using _malloc_dbg
// and then calls _msize_dbg to display the size of that block.
// Next, it uses _expand_dbg to expand the amount of
// memory used by the buffer and then calls _msize_dbg again to
// display the new amount of memory allocated to the buffer.
//

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   long *buffer;
   size_t size;

   // Call _malloc_dbg to include the filename and line number
   // of our allocation request in the header
   buffer = (long *)_malloc_dbg( 40 * sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );
   if( buffer == NULL )
      exit( 1 );

   // Get the size of the buffer by calling _msize_dbg
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _malloc_dbg of 40 longs: %u\n", size );

   // Expand the buffer using _expand_dbg and show the new size
   buffer = (long *)_expand_dbg( buffer, size + sizeof(long),
                                 _NORMAL_BLOCK, __FILE__, __LINE__ );

   if( buffer == NULL )
      exit( 1 );
   size = _msize_dbg( buffer, _NORMAL_BLOCK );
   printf( "Size of block after _expand_dbg of 1 more long: %u\n",
           size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after _malloc_dbg of 40 longs: 160
Size of block after _expand_dbg of 1 more long: 164
```

## <a name="comment"></a>コメント

このプログラムの出力は、すべてのセクションを拡張するためのコンピューターの能力によって異なります。 すべてのセクションが展開される場合、出力は出力セクションに反映されます。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
