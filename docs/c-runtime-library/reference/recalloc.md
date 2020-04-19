---
title: _recalloc
ms.date: 11/04/2016
api_name:
- _recalloc
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
- _recalloc
- recalloc
helpviewer_keywords:
- _recalloc function
- recalloc function
ms.assetid: 1db8305a-3f03-418c-8844-bf9149f63046
ms.openlocfilehash: f06631fe4dd0abcb0b18895ccb04e5b52cda6a2c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949447"
---
# <a name="_recalloc"></a>_recalloc

**Realloc**と**calloc**の組み合わせ。 メモリ内の配列を再割り当てし、その要素を 0 に初期化します。

## <a name="syntax"></a>構文

```C
void *_recalloc(
   void *memblock
   size_t num,
   size_t size
);
```

### <a name="parameters"></a>パラメーター

*memblock*<br/>
以前に割り当てられたメモリ ブロックへのポインター。

*number*<br/>
要素の数。

*size*<br/>
各要素の長さ (バイト単位)。

## <a name="return-value"></a>戻り値

**_recalloc**は、再割り当てされた (移動される可能性もある) メモリブロックへの**void**ポインターを返します。

指定されたサイズまでブロックを拡張するのに十分なメモリがない場合、元のブロックは変更されず、 **NULL**が返されます。

要求されたサイズが0の場合、 *memblock*が指すブロックは解放されます。戻り値は**NULL**で、 *memblock*は解放されたブロックを指しています。

戻り値は、どの型のオブジェクトを格納する場合でも適切なアラインメントが保証されるストレージ領域を指します。 **Void**以外の型へのポインターを取得するには、戻り値に型キャストを使用します。

## <a name="remarks"></a>Remarks

**_Recalloc**関数は、割り当てられたメモリブロックのサイズを変更します。 *Memblock*引数は、メモリブロックの先頭を指します。 *Memblock*が**NULL**の場合、 **_recalloc**は[calloc](calloc.md)と同じように動作し、新しい*サイズ*のバイト*数の* * ブロックを割り当てます。 各要素は 0 に初期化されます。 *Memblock*が**NULL**でない場合は、 **calloc**、 [malloc](malloc.md)、または[realloc](realloc.md)の前の呼び出しによって返されたポインターである必要があります。

新しいブロックは新しいメモリ位置にある可能性があるため、 **_recalloc**によって返されるポインターは、 *memblock*引数を通じて渡されるポインターであるとは限りません。

**_recalloc**は、メモリ割り当てが失敗した場合、または要求されたメモリの量が **_HEAP_MAXREQ**を超えた場合に、 **errno**を**ENOMEM**に設定します。 その他のエラー コードの詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

**recalloc**は 、 C++ [_set_new_mode](set-new-mode.md)関数を使用して新しいハンドラーモードを設定するために realloc を呼び出します。 新しいハンドラーモードは、エラー発生時に、 [_set_new_handler](set-new-handler.md)によって**設定され**た新しいハンドラールーチンを呼び出すかどうかを示します。 既定では、 **realloc**は、メモリの割り当てに失敗したときに新しいハンドラールーチンを呼び出しません。 この既定の動作をオーバーライドして、 **_recalloc**がメモリの割り当てに失敗したときに、 **new**演算子が同じ理由で失敗したときと同じ方法で新しいハンドラールーチン**を呼び出す**ことができます。 既定の動作をオーバーライドするには、次の関数を呼び出します。

```C
_set_new_mode(1);
```

この呼び出しはプログラムの最初の方で指定するか、NEWMODE.OBJ にリンクします。

アプリケーションが C ランタイムライブラリのデバッグバージョンにリンクされている場合、 **_recalloc**は[_recalloc_dbg](recalloc-dbg.md)に解決されます。 デバッグ プロセス中のヒープの管理方法の詳細については、「[CRT デバッグ ヒープ](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。

**_recalloc**はと`__declspec(noalias)` `__declspec(restrict)`マークされています。つまり、関数がグローバル変数を変更しないこと、および返されるポインターがエイリアス化されていないことが保証されることを意味します。 詳細については、「[noalias](../../cpp/noalias.md)」、および「[restrict](../../cpp/restrict.md)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_recalloc**|\<stdlib.h> と \<malloc.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[メモリ割り当て](../../c-runtime-library/memory-allocation.md)<br/>
[_recalloc_dbg](recalloc-dbg.md)<br/>
[_aligned_recalloc](aligned-recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
[free](free.md)<br/>
[リンク オプション](../../c-runtime-library/link-options.md)<br/>
