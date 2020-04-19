---
title: _query_new_mode
ms.date: 11/04/2016
api_name:
- _query_new_mode
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
- query_new_mode
- _query_new_mode
helpviewer_keywords:
- query_new_mode function
- handler modes
- _query_new_mode function
ms.assetid: e185c5f9-b73b-4257-8eff-b47648374768
ms.openlocfilehash: 59724dafdc6488596478d0b44b254c4f498fce99
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70950111"
---
# <a name="_query_new_mode"></a>_query_new_mode

**Malloc**に対して **_set_new_mode**によって設定された新しいハンドラーモードを示す整数を返します。

## <a name="syntax"></a>構文

```C
int _query_new_mode(
   void
);
```

## <a name="return-value"></a>戻り値

**Malloc**の現在の新しいハンドラーモード (0 または 1) を返します。 戻り値1は、メモリの割り当てが失敗したときに、 **malloc**が新しいハンドラールーチンを呼び出すことを示します。戻り値が0の場合は、そうでないことを示します。

## <a name="remarks"></a>Remarks

C++ **_query_new_mode**関数は、 C++ [malloc](malloc.md)の[_set_new_mode](set-new-mode.md)関数によって設定された新しいハンドラーモードを示す整数を返します。 新しいハンドラーモードは、メモリの割り当てに失敗したときに、 **malloc**が、 [_set_new_handler](set-new-handler.md)によって設定された新しいハンドラールーチンを呼び出すかどうかを示します。 既定では、 **malloc**はエラー発生時に新しいハンドラールーチンを呼び出しません。 **_set_new_mode**を使用すると、この動作をオーバーライドして、**new**演算子がメモリの割り当てに失敗したときと同じ方法で、エラー **malloc**が新しいハンドラールーチンを呼び出すようにすることができます。 詳細については、C++ 言語リファレンスの「[new および delete 演算子](../../cpp/new-and-delete-operators.md)」の説明をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_query_new_mode**|\<new.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>関連項目

[メモリ割り当て](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
[_query_new_handler](query-new-handler.md)<br/>
