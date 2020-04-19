---
title: _aligned_free_dbg
ms.date: 11/04/2016
api_name:
- _aligned_free_dbg
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
- _aligned_free_dbg
- aligned_free_dbg
helpviewer_keywords:
- _aligned_free_dbg function
- aligned_free_dbg function
ms.assetid: eb0cb3c8-0992-4db8-bac3-65f1b8311ca6
ms.openlocfilehash: b510d16b6e784202094bb05e6364f7af1b1fff97
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939916"
---
# <a name="_aligned_free_dbg"></a>_aligned_free_dbg

[_aligned_malloc](aligned-malloc.md) または [_aligned_offset_malloc](aligned-offset-malloc.md) で割り当てられたメモリ ブロックを解放します (デバッグのみ)。

## <a name="syntax"></a>構文

```C
void _aligned_free_dbg(
   void *memblock
);
```

### <a name="parameters"></a>パラメーター

*memblock*<br/>
[_Aligned_malloc](aligned-malloc.md)または[_aligned_offset_malloc](aligned-offset-malloc.md)関数に返されたメモリブロックへのポインター。

## <a name="remarks"></a>Remarks

**_Aligned_free_dbg**関数は、 [_aligned_free](aligned-free.md)関数のデバッグバージョンです。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_aligned_free_dbg**の各呼び出しはの`_aligned_free`呼び出しに限定されます。 と`_aligned_free` **_aligned_free_dbg**はどちらもベースヒープ内のメモリブロックを解放しますが、 **_aligned_free_dbg**はデバッグ機能に対応しています。これは、解放されたブロックをヒープのリンクリストに保持してメモリ不足の状態をシミュレートする機能です。

**_aligned_free_dbg**は、無料操作を実行する前に、指定されたすべてのファイルとブロックの場所に対して有効性チェックを実行します。 アプリケーションは、この情報を提供する必要はありません。 メモリ ブロックが解放されると、デバッグ ヒープ マネージャーはユーザー部分の前後のバッファーの整合性を自動的にチェックし、それらのバッファーが上書きされていた場合はエラー レポートを発行します。 [_CrtDbgFlag](../../c-runtime-library/crtdbgflag.md)フラグの _CRTDBG_DELAY_FREE_MEM_DF ビットフィールドが設定されている場合、解放されたブロックは値0xdd を格納し、_FREE_BLOCK ブロック型が割り当てられ、ヒープのメモリブロックのリンクリストに保持されます。

メモリの解放でエラーが発生すると、エラーの性質に関するオペレーティング システムからの情報が `errno` に設定されます。 詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 割り当てブロック型と、それらがどのように使用されるかについては、「[デバッグ ヒープ上のメモリ ブロックの型](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。 標準で呼び出すヒープ関数と、アプリケーションのデバッグ ビルドで呼び出すデバッグ バージョンのヒープ関数との違いの詳細については、「[デバッグ バージョンのヒープ割り当て関数](/visualstudio/debugger/debug-versions-of-heap-allocation-functions)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_aligned_free_dbg**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)