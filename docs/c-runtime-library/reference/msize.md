---
title: _msize
ms.date: 11/04/2016
api_name:
- _msize
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
- msize
- _msize
helpviewer_keywords:
- memory blocks
- msize function
- _msize function
ms.assetid: 02b1f89e-d0d7-4f12-938a-9eeba48a0f88
ms.openlocfilehash: c1760cfa6a416e2eb4cd7b549cb5ae9bed00a609
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951430"
---
# <a name="_msize"></a>_msize

ヒープで割り当てられたメモリ ブロックのサイズを返します。

## <a name="syntax"></a>構文

```C
size_t _msize(
   void *memblock
);
```

### <a name="parameters"></a>パラメーター

*memblock*<br/>
メモリ ブロックへのポインター。

## <a name="return-value"></a>戻り値

**_msize**は、符号なし整数としてサイズ (バイト単位) を返します。

## <a name="remarks"></a>Remarks

**_Msize**関数は、 **calloc**、 **malloc**、または**realloc**への呼び出しによって割り当てられたメモリブロックのサイズをバイト単位で返します。

アプリケーションが C ランタイムライブラリのデバッグバージョンにリンクされている場合、 **_msize**は[_msize_dbg](msize-dbg.md)に解決されます。 デバッグ プロセス中のヒープの管理方法の詳細については、「[CRT デバッグ ヒープ](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。

この関数は、そのパラメーターを検証します。 *Memblock*が null ポインターの場合、 **_Msize**は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 エラーが処理された場合、関数は**errno**を**EINVAL**に設定し、-1 を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="example"></a>例

「[realloc](realloc.md)」の例を参照してください。

## <a name="see-also"></a>関連項目

[メモリ割り当て](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[_expand](expand.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
