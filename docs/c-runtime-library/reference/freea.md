---
title: _freea
ms.date: 11/04/2016
api_name:
- _freea
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
- freea
- _freea
helpviewer_keywords:
- _freea function
- freea function
- memory deallocation
ms.assetid: dcd30584-dd9d-443b-8c4c-13237a1cecac
ms.openlocfilehash: dcad8bea4f8cec28d8cb15a9937b1032593ef0cc
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956707"
---
# <a name="_freea"></a>_freea

メモリ ブロックを割り当て解除または解放します。

## <a name="syntax"></a>構文

```C
void _freea(
   void *memblock
);
```

### <a name="parameters"></a>パラメーター

*memblock*<br/>
以前割り当てられ、解放されるメモリ ブロック。

## <a name="return-value"></a>戻り値

なし。

## <a name="remarks"></a>Remarks

**_Freea**関数は、以前に[_malloca](malloca.md)への呼び出しによって割り当てられたメモリブロック (*memblock*) を解放します。 **_freea**は、ヒープまたはスタックにメモリが割り当てられたかどうかを確認します。 スタックに割り当てられている場合、 **_freea**は何も行いません。 ヒープ上で割り当てられている場合、解放されるバイト数は、ブロックが割り当てられたときに要求されたバイト数と同じです。 *Memblock*が**NULL**の場合、ポインターは無視され、 **_freea**は直ちにを返します。 無効なポインター ( **_malloca**によって割り当てられていないメモリブロックへのポインター) を解放しようとすると、後続の割り当て要求に影響し、エラーが発生する可能性があります。

**_freea**は、メモリがヒープに割り当てられていることが判明した場合に、内部的に**解放**を呼び出します。 メモリが、ヒープまたはスタックのどちらにあるかは、割り当てられたメモリの直前のアドレスにメモリ内で配置されたマーカーによって決まります。

メモリの解放中にエラーが発生した場合、エラーの性質上、オペレーティングシステムからの情報が**errno**に設定されます。 詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

メモリ ブロックを解放すると、[_heapmin](heapmin.md) が、未使用の領域を結合して、それらをオペレーティング システムに戻すことで、ヒープ上の空きメモリの量を最小限に抑えます。 オペレーティング システムにリリースされない解放されたメモリは、空きプールに復元され、再度割り当てに使用できます。

**_Freea**の呼び出しは、 **_malloca**のすべての呼び出しに付随している必要があります。 また、同じメモリ上で **_freea**を2回呼び出すこともできません。 アプリケーションが C ランタイムライブラリのデバッグバージョンにリンクされている場合 (特に、 **_CRTDBG_MAP_ALLOC**を定義することで有効にされた[_malloc_dbg](malloc-dbg.md)機能の場合)、 **_freea**の呼び出しが見つからないか、重複していることがわかりやすくなります。 デバッグ プロセス中のヒープの管理方法の詳細については、「[CRT デバッグ ヒープ](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。

**_freea**はと`__declspec(noalias)`マークされています。つまり、関数はグローバル変数を変更しないことが保証されます。 詳細については、「[noalias](../../cpp/noalias.md)」を参照してください。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**_freea**|\<stdlib.h> と \<malloc.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[_malloca](malloca.md)」の例を参照してください。

## <a name="see-also"></a>関連項目

[メモリ割り当て](../../c-runtime-library/memory-allocation.md)<br/>
[_malloca](malloca.md)<br/>
[calloc](calloc.md)<br/>
[malloc](malloc.md)<br/>
[_malloc_dbg](malloc-dbg.md)<br/>
[realloc](realloc.md)<br/>
[_free_dbg](free-dbg.md)<br/>
[_heapmin](heapmin.md)<br/>
