---
title: _calloc_dbg
ms.date: 11/04/2016
api_name:
- _calloc_dbg
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
- _calloc_dbg
- calloc_dbg
helpviewer_keywords:
- _calloc_dbg function
- calloc_dbg function
ms.assetid: 7f62c42b-eb9f-4de5-87d0-df57036c87de
ms.openlocfilehash: eab17348e473a4f642e784defe4569e0e799299e
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939319"
---
# <a name="_calloc_dbg"></a>_calloc_dbg

デバッグ ヘッダーと上書きバッファー用の追加の領域を持つ多数のメモリ ブロックをヒープに割り当てます (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
void *_calloc_dbg(
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*number*<br/>
要求するメモリ ブロックの数。

*size*<br/>
要求する各メモリ ブロックのサイズ (バイト)。

*blockType*<br/>
要求されたメモリブロックの種類: **_CLIENT_BLOCK**または **_NORMAL_BLOCK**。

割り当てブロック型と、それらがどのように使用されるかについては、「[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。

*ファイル名*<br/>
割り当て操作を要求したソースファイルの名前へのポインターまたは**NULL**。

*行番号*<br/>
割り当て操作が要求されたソースファイル内の行番号または**NULL**。

*Filename*パラメーターと*linenumber*パラメーターは、 **_calloc_dbg**が明示的に呼び出された場合、または[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)プリプロセッサ定数が定義されている場合にのみ使用できます。

## <a name="return-value"></a>戻り値

正常に完了した場合、この関数は最後に割り当てられたメモリブロックのユーザー部分へのポインターを返すか、新しいハンドラー関数を呼び出すか、 **NULL**を返します。 戻る動作の詳細については、「解説」のセクションを参照してください。 新しいハンドラー関数がどのように使用されるかの詳細については、[calloc](calloc.md) 関数を参照してください。

## <a name="remarks"></a>Remarks

**_calloc_dbg**は、 [calloc](calloc.md)関数のデバッグバージョンです。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_calloc_dbg**の各呼び出しは**calloc**の呼び出しに限定されます。 **Calloc**と **_calloc_dbg**は、どちらもベースヒープ内のメモリブロックを割り当てますが、 **_calloc_dbg**に*はいくつか*のデバッグ機能が用意されています。

- リークをテストするための、ブロックのユーザー部分の両側のバッファー。

- 特定の割り当ての種類を追跡するためのブロック型パラメーター。

- *ファイル名*/*linenumber*は、割り当て要求の発生元を特定するための情報です。

**_calloc_dbg**は、要求された*サイズ*よりも若干多くの領域を使用して、各メモリブロックを割り当てます。 追加の領域は、デバッグ メモリ ブロックをリンクし、アプリケーションにデバッグ ヘッダー情報と上書きバッファーを提供するために、デバッグ ヒープ マネージャーによって使用されます。 ブロックが割り当てられると、ブロックのユーザー部分には値 0xCD が設定され、各上書きバッファーには 0xFD が設定されます。

**_calloc_dbg**は、メモリ割り当てが失敗した場合に**errno**を**ENOMEM**に設定します。必要なメモリの量 (前に説明したオーバーヘッドを含む) が **_HEAP_MAXREQ**を超えると、 **EINVAL**が返されます。 このエラー コードと他のエラーコードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 標準で呼び出すヒープ関数と、アプリケーションのデバッグ ビルドで呼び出すデバッグ バージョンのヒープ関数との違いの詳細については、「[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_calloc_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_callocd.c
// This program uses _calloc_dbg to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>
#include <crtdbg.h>

int main( void )
{
    long *bufferN, *bufferC;

    // Call _calloc_dbg to include the filename and line number
    // of our allocation request in the header and also so we can
    // allocate CLIENT type blocks specifically
    bufferN = (long *)_calloc_dbg( 40, sizeof(long), _NORMAL_BLOCK, __FILE__, __LINE__ );
    bufferC = (long *)_calloc_dbg( 40, sizeof(long), _CLIENT_BLOCK, __FILE__, __LINE__ );
    if( bufferN != NULL && bufferC != NULL )
        printf( "Allocated memory successfully\n" );
    else
        printf( "Problem allocating memory\n" );

    / _free_dbg must be called to free CLIENT type blocks
    free( bufferN );
    _free_dbg( bufferC, _CLIENT_BLOCK );
}
```

```Output
Allocated memory successfully
```

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
[calloc](calloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
