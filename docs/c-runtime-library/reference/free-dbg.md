---
title: _free_dbg
ms.date: 11/04/2016
api_name:
- _free_dbg
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
- _free_dbg
- free_dbg
helpviewer_keywords:
- memory blocks, deallocating
- freeing memory
- _free_dbg function
- free_dbg function
ms.assetid: fc5e8299-616d-48a0-b979-e037117278c6
ms.openlocfilehash: 43591ce8710dd25ad33832a5f084ca6e84bba979
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956803"
---
# <a name="_free_dbg"></a>_free_dbg

ヒープ内のメモリ ブロックを解放します (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
void _free_dbg(
   void *userData,
   int blockType
);
```

### <a name="parameters"></a>パラメーター

*userData*<br/>
解放される、割り当てられていたメモリ ブロックへのポインター。

*blockType*<br/>
解放される割り当て済みメモリブロックの型: **_CLIENT_BLOCK**、 **_NORMAL_BLOCK**、または **_IGNORE_BLOCK**。

## <a name="remarks"></a>Remarks

**_Free_dbg**関数は、 [free](free.md)関数のデバッグバージョンです。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_free_dbg**への各呼び出しは**無料**の呼び出しに限定されます。 **Free**と **_free_dbg**はどちらもベースヒープ内のメモリブロックを解放しますが、 **_free_dbg**は2つのデバッグ機能を利用できます。解放されたブロックをヒープのリンクリストに保持してメモリ不足の状態をシミュレートし、ブロック型パラメーターをにします。特定の割り当ての種類を解放します。

**_free_dbg**は、無料操作を実行する前に、指定されたすべてのファイルとブロックの場所に対して有効性チェックを実行します。 アプリケーションは、この情報を提供する必要はありません。 メモリ ブロックが解放されると、デバッグ ヒープ マネージャーはユーザー部分の前後のバッファーの整合性を自動的にチェックし、それらのバッファーが上書きされていた場合はエラー レポートを発行します。 [_CrtDbgFlag](../../c-runtime-library/crtdbgflag.md)フラグの **_CRTDBG_DELAY_FREE_MEM_DF**ビットフィールドが設定されている場合、解放されたブロックは値0xdd を格納し、 **_FREE_BLOCK**ブロック型が割り当てられ、ヒープのメモリブロックのリンクリストに保持されます。

メモリの解放中にエラーが発生した場合、エラーの性質上、オペレーティングシステムからの情報が**errno**に設定されます。 詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 割り当てブロック型と、それらがどのように使用されるかについては、「[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 標準で呼び出すヒープ関数と、アプリケーションのデバッグ ビルドで呼び出すデバッグ バージョンのヒープ関数との違いの詳細については、「[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_free_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

**_Free_dbg**の使用例については、 [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)を参照してください。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
