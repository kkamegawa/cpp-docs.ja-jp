---
title: _recalloc_dbg
ms.date: 11/04/2016
api_name:
- _recalloc_dbg
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
- recalloc_dbg
- _recalloc_dbg
helpviewer_keywords:
- _recalloc_dbg function
- recalloc_dbg function
ms.assetid: 43c3e9b2-be6d-4508-9b0f-3220c8a47ca3
ms.openlocfilehash: 6274e749b2c4e6f64c7c7f82f8764dcf5ba642fe
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949468"
---
# <a name="_recalloc_dbg"></a>_recalloc_dbg

配列を再割り当てし、その要素を 0 に初期化します (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
void *_recalloc_dbg(
   void *userData,
   size_t num,
   size_t size,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*userData*<br/>
以前に割り当てられていたメモリ ブロックへのポインター。

*number*<br/>
要求するメモリ ブロックの数。

*size*<br/>
要求する各メモリ ブロックのサイズ (バイト)。

*blockType*<br/>
要求されたメモリブロックの種類: **_CLIENT_BLOCK**または **_NORMAL_BLOCK**。

割り当てブロック型と、それらがどのように使用されるかについては、「[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。

*ファイル名*<br/>
割り当て操作を要求したソースファイルの名前へのポインターまたは**NULL**。

*行番号*<br/>
割り当て操作が要求されたソースファイル内の行番号または**NULL**。

*Filename*パラメーターと*linenumber*パラメーターは、 **_recalloc_dbg**が明示的に呼び出された場合、または[_CRTDBG_MAP_ALLOC](../../c-runtime-library/crtdbg-map-alloc.md)プリプロセッサ定数が定義されている場合にのみ使用できます。

## <a name="return-value"></a>戻り値

正常に完了した場合、この関数は再割り当てされたメモリブロックのユーザー部分へのポインターを返すか、新しいハンドラー関数を呼び出すか、 **NULL**を返します。 戻る動作の詳細については、後の「解説」のセクションを参照してください。 新しいハンドラー関数がどのように使用されるかの詳細については、[_recalloc](recalloc.md) 関数を参照してください。

## <a name="remarks"></a>Remarks

**_recalloc_dbg**は、 [_recalloc](recalloc.md)関数のデバッグバージョンです。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_recalloc_dbg**の各呼び出しは **_recalloc**の呼び出しに限定されます。 **_Recalloc**と **_recalloc_dbg**はどちらもベースヒープ内のメモリブロックを再割り当てしますが、 **_recalloc_dbg**はいくつかのデバッグ機能に対応しています。リークをテストするための、ブロックのユーザー部分の両側のバッファーは、ブロック型パラメーターです。特定の割り当ての種類を追跡するには、および*ファイル名*/*linenumber*情報を参照して、割り当て要求の発生元を特定します。

**_recalloc_dbg**は、指定されたメモリブロックを、要求されたサイズ (*数値* * *サイズ*) よりも若干多くの領域を使用して再割り当てします。これは、最初に割り当てられたメモリブロックのサイズより大きいか小さい可能性があります。 追加の領域は、デバッグ メモリ ブロックをリンクし、アプリケーションにデバッグ ヘッダー情報と上書きバッファーを提供するために、デバッグ ヒープ マネージャーによって使用されます。 再割り当てによって、元のメモリ ブロックがヒープ内の別の位置に移動されたり、メモリ ブロックのサイズが変わったりする場合があります。 ブロックのユーザー部分には値 0xCD が設定され、各上書きバッファーには 0xFD が設定されます。

**_recalloc_dbg**は、メモリ割り当てが失敗した場合に**errno**を**ENOMEM**に設定します。必要なメモリの量 (前に説明したオーバーヘッドを含む) が **_HEAP_MAXREQ**を超えると、 **EINVAL**が返されます。 このエラー コードと他のエラーコードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 標準で呼び出すヒープ関数と、アプリケーションのデバッグ ビルドで呼び出すデバッグ バージョンのヒープ関数との違いの詳細については、「[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_recalloc_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
