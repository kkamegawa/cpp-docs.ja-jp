---
title: _aligned_recalloc
ms.date: 11/04/2016
api_name:
- _aligned_recalloc
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
- aligned_recalloc
- _aligned_recalloc
helpviewer_keywords:
- aligned_recalloc function
- _aligned_recalloc function
ms.assetid: d3da3dcc-79ef-4273-8af5-ac7469420142
ms.openlocfilehash: ef25769a04b27b02ccda16e86451a068ab0a0b84
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943778"
---
# <a name="_aligned_recalloc"></a>_aligned_recalloc

[_aligned_malloc](aligned-malloc.md) または [_aligned_offset_malloc](aligned-offset-malloc.md) で割り当てられたメモリ ブロックのサイズを変更し、メモリを 0 に初期化します。

## <a name="syntax"></a>構文

```C
void * _aligned_recalloc(
   void *memblock,
   size_t num,
   size_t size,
   size_t alignment
);
```

### <a name="parameters"></a>パラメーター

*memblock*<br/>
現在のメモリ ブロック ポインター。

*number*<br/>
要素の数。

*size*<br/>
各要素のサイズ (バイト単位)。

*alignment*<br/>
アラインメント値。2 の整数乗である必要があります。

## <a name="return-value"></a>戻り値

**_aligned_recalloc**は、再割り当てされた (移動される可能性もある) メモリブロックへの void ポインターを返します。 サイズが0でバッファー引数が**null**でない場合、またはブロックを指定されたサイズに拡張するのに十分なメモリがない場合、戻り値は**null**になります。 最初の場合には、元のブロックは解放されます。 2 番目の場合には、元のブロックは変更されません。 戻り値は、どの型のオブジェクトを格納する場合でも適切なアラインメントが保証されるストレージ領域を指します。 void 以外の型へのポインターを取得するには、戻り値の型キャストを使用します。

メモリを再割り当てしてブロックのアラインメントを変更すると、エラーになります。

## <a name="remarks"></a>Remarks

**_aligned_recalloc**は**malloc**に基づいています。 **_Aligned_offset_malloc**の使用方法の詳細については、「 [malloc](malloc.md)」を参照してください。

メモリ割り当てが失敗した場合、または要求されたサイズが **_HEAP_MAXREQ**より大きい場合、この関数は**errno**を**ENOMEM**に設定します。 **Errno**の詳細については、「 [errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。 また、 **_aligned_recalloc**はそのパラメーターを検証します。 *Alignment*が2の累乗でない場合、この関数は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は**NULL**を返し、 **errno**を**EINVAL**に設定します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_aligned_recalloc**|\<malloc.h>|

## <a name="see-also"></a>関連項目

[データの整列](../../c-runtime-library/data-alignment.md)<br/>
[_recalloc](recalloc.md)<br/>
[_aligned_offset_recalloc](aligned-offset-recalloc.md)<br/>
