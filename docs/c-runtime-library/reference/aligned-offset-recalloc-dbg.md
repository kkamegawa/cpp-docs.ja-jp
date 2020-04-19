---
title: _aligned_offset_recalloc_dbg
ms.date: 11/04/2016
api_name:
- _aligned_offset_recalloc_dbg
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
- aligned_offset_recalloc_dbg
- _aligned_offset_recalloc_dbg
helpviewer_keywords:
- aligned_offset_recalloc_dbg function
- _aligned_offset_recalloc_dbg function
ms.assetid: 7ab719c3-77e0-4d2e-934f-01529d062fbf
ms.openlocfilehash: e363a1cb104db9973f5f9e9c67a5d40693d405ee
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939745"
---
# <a name="_aligned_offset_recalloc_dbg"></a>_aligned_offset_recalloc_dbg

[_aligned_malloc](aligned-malloc.md) または [_aligned_offset_malloc](aligned-offset-malloc.md) で割り当てられたメモリ ブロックのサイズを変更し、メモリを 0 に初期化します (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
void * _aligned_offset_recalloc_dbg(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment,
   size_t offset,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>パラメーター

*memblock*<br/>
現在のメモリ ブロック ポインター。

*number*<br/>
要素の数。

*size*<br/>
各要素の長さ (バイト単位)。

*alignment*<br/>
アラインメント値。2 の整数乗である必要があります。

*オフセット*<br/>
アラインメントを強制するためのメモリ割り当てへのオフセット。

*ファイル名*<br/>
Realloc 操作を要求したソースファイルの名前へのポインターまたは**NULL**。

*行番号*<br/>
Realloc 操作が要求されたソースファイル内の行番号または**NULL**。

## <a name="return-value"></a>戻り値

**_aligned_offset_recalloc_dbg**は、再割り当てされた (移動される可能性もある) メモリブロックへの void ポインターを返します。 サイズが0でバッファー引数が**null**でない場合、またはブロックを指定されたサイズに拡張するのに十分なメモリがない場合、戻り値は**null**になります。 最初の場合には、元のブロックは解放されます。 2 番目の場合には、元のブロックは変更されません。 戻り値は、どの型のオブジェクトを格納する場合でも適切なアラインメントが保証されるストレージ領域を指します。 void 以外の型へのポインターを取得するには、戻り値の型キャストを使用します。

## <a name="remarks"></a>Remarks

**_aligned_offset_realloc_dbg**は、 [_aligned_offset_recalloc](aligned-offset-recalloc.md)関数のデバッグバージョンです。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_aligned_offset_recalloc_dbg**の各呼び出しは **_aligned_offset_recalloc**の呼び出しに限定されます。 **_Aligned_offset_recalloc**と **_aligned_offset_recalloc_dbg**は、どちらもベースヒープ内のメモリブロックを再割り当てしますが、 **_aligned_offset_recalloc_dbg**は複数のデバッグ機能に対応しています。ユーザー部分の両側のバッファーです。リークをテストするブロックの、および*ファイル名*/*linenumber*情報を使用して、割り当て要求の発生元を特定します。 ブロックの型パラメーターを使用して特定の割り当ての種類を追跡することは、固定された割り当てのデバッグ機能としてサポートされていません。 アラインされた割り当ては、_NORMAL_BLOCK ブロック型として表示されます。

**_aligned_offset_realloc_dbg**は、要求された*newSize*よりも若干多くの領域を使用して、指定されたメモリブロックを再割り当てします。 *newSize*が、最初に割り当てられたメモリブロックのサイズより大きいか小さい可能性があります。 追加の領域は、デバッグ メモリ ブロックをリンクし、アプリケーションにデバッグ ヘッダー情報と上書きバッファーを提供するために、デバッグ ヒープ マネージャーによって使用されます。 再割り当てによって、元のメモリ ブロックがヒープ内の別の位置に移動されたり、メモリ ブロックのサイズが変わったりする場合があります。 メモリ ブロックが移動される場合、元のブロックの内容は上書きされます。

この関数は、メモリ割り当てが失敗した場合、または要求されたサイズ (*数値* * *サイズ*) が **_HEAP_MAXREQ**を超えた場合に、 **errno**を**ENOMEM**に設定します。 **Errno**の詳細については、「 [errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。 また、 **_aligned_offset_recalloc_dbg**はそのパラメーターを検証します。 *Alignment*が2の累乗でない場合、または*オフセット*が要求されたサイズ以上で0以外の場合、この関数は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は**NULL**を返し、 **errno**を**EINVAL**に設定します。

デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 割り当てブロック型と、それらがどのように使用されるかについては、「[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 標準で呼び出すヒープ関数と、アプリケーションのデバッグ ビルドで呼び出すデバッグ バージョンのヒープ関数との違いの詳細については、「[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_aligned_offset_recalloc_dbg**|\<malloc.h>|

## <a name="see-also"></a>関連項目

[データの整列](../../c-runtime-library/data-alignment.md)<br/>
