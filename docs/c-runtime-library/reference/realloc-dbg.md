---
title: _realloc_dbg
ms.date: 11/04/2016
api_name:
- _realloc_dbg
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
- _realloc_dbg
- realloc_dbg
helpviewer_keywords:
- reallocating memory blocks
- realloc_dbg function
- memory blocks, reallocating
- memory, reallocating
- _realloc_dbg function
ms.assetid: 7c3cb780-51ed-4d9c-9929-cdde606d846a
ms.openlocfilehash: 58d12ed6f4b013996f3f59cba1b146b823adbee6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949513"
---
# <a name="_realloc_dbg"></a>_realloc_dbg

ブロックの移動やサイズ変更によって、ヒープ内の指定されたメモリのブロックを再割り当てします (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
void *_realloc_dbg(
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
再割り当てされるブロックのために要求するサイズ (バイト)。

*blockType*<br/>
再割り当てされたブロックの要求された型: **_CLIENT_BLOCK**または **_NORMAL_BLOCK**。

*ファイル名*<br/>
**Realloc**操作を要求したソースファイルの名前へのポインターまたは**NULL**。

*行番号*<br/>
**Realloc**操作が要求されたソースファイル内の行番号または**NULL**。

*Filename*パラメーターと*linenumber*パラメーターは、 **_realloc_dbg**が明示的に呼び出された場合、または[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)プリプロセッサ定数が定義されている場合にのみ使用できます。

## <a name="return-value"></a>戻り値

正常に完了した場合、この関数は再割り当てされたメモリブロックのユーザー部分へのポインターを返すか、新しいハンドラー関数を呼び出すか、 **NULL**を返します。 戻る動作の詳細については、後の「解説」のセクションを参照してください。 新しいハンドラー関数がどのように使用されるかの詳細については、[realloc](realloc.md) 関数を参照してください。

## <a name="remarks"></a>Remarks

**_realloc_dbg**は、 [realloc](realloc.md)関数のデバッグバージョンです。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_realloc_dbg**の各呼び出しは、 **realloc**の呼び出しに限定されます。 **Realloc**と **_realloc_dbg**はどちらもベースヒープ内のメモリブロックを再割り当てしますが、 **_realloc_dbg**にはいくつかのデバッグ機能があります。リークをテストするために、ブロックのユーザー部分の両側のバッファーを使用します。特定の割り当ての種類と*filename*/*linenumber*情報を追跡して、割り当て要求の発生元を特定します。

**_realloc_dbg**は、要求された*newSize*よりも若干多くの領域を使用して、指定されたメモリブロックを再割り当てします。 *newSize*が、最初に割り当てられたメモリブロックのサイズより大きいか小さい可能性があります。 追加の領域は、デバッグ メモリ ブロックをリンクし、アプリケーションにデバッグ ヘッダー情報と上書きバッファーを提供するために、デバッグ ヒープ マネージャーによって使用されます。 再割り当てによって、元のメモリ ブロックがヒープ内の別の位置に移動されたり、メモリ ブロックのサイズが変わったりする場合があります。 メモリ ブロックが移動される場合、元のブロックの内容は上書きされます。

**_realloc_dbg**は、メモリ割り当てが失敗した場合、または必要なメモリの量 (前に説明したオーバーヘッドを含む) が **_HEAP_MAXREQ**を超えた場合に**errno**を**ENOMEM**に設定します。 このエラー コードと他のエラーコードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 割り当てブロック型と、それらがどのように使用されるかについては、「[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 標準で呼び出すヒープ関数と、アプリケーションのデバッグ ビルドで呼び出すデバッグ バージョンのヒープ関数との違いの詳細については、「[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_realloc_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="example"></a>例

「[_msize_dbg](msize-dbg.md)」のトピックの例を参照してください。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
