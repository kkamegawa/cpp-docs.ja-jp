---
title: _aligned_free
ms.date: 11/04/2016
api_name:
- _aligned_free
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
- aligned_free
- _aligned_free
helpviewer_keywords:
- _aligned_free function
- aligned_free function
ms.assetid: ed1ce952-cdfc-4682-85cc-f75d4101603d
ms.openlocfilehash: 44556d3f044a567f4903ef14a4b2a9b353af02ff
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943971"
---
# <a name="_aligned_free"></a>_aligned_free

[_aligned_malloc](aligned-malloc.md) または [_aligned_offset_malloc](aligned-offset-malloc.md) で割り当てられたメモリ ブロックを解放します。

## <a name="syntax"></a>構文

```C
void _aligned_free (
   void *memblock
);
```

### <a name="parameters"></a>パラメーター

*memblock*<br/>
`_aligned_malloc` または `_aligned_offset_malloc` 関数に返されたメモリ ブロックへのポインター。

## <a name="remarks"></a>Remarks

**_aligned_free**はと`__declspec(noalias)`マークされています。つまり、関数はグローバル変数を変更しないことが保証されます。 詳細については、「[noalias](../../cpp/noalias.md)」を参照してください。

この関数は、他の _aligned CRT 関数とは異なり、パラメーターを検証しません。 *Memblock*が NULL ポインターの場合、この関数は単にアクションを実行しません。 この関数は `errno` を変更せず、無効なパラメーター ハンドラーを呼び出しません。 以前にメモリのブロックを割り当てるために _aligned 関数を使用しなかったために関数でエラーが発生する場合、または何らかの予期しない災害によってメモリの不整合が発生する場合、関数は [_RPT、_RPTF、_RPTW、_RPTFW のマクロ](rpt-rptf-rptw-rptfw-macros.md)からデバッグ レポートを生成します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_aligned_free**|\<malloc.h>|

## <a name="example"></a>例

詳細については、「[_aligned_malloc](aligned-malloc.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データの整列](../../c-runtime-library/data-alignment.md)