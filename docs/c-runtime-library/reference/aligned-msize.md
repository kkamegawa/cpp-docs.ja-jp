---
title: _aligned_msize
ms.date: 11/04/2016
api_name:
- _aligned_msize
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
- _aligned_msize
- aligned_msize
helpviewer_keywords:
- aligned_msize function
- _aligned_msize function
ms.assetid: 10995edc-2110-4212-9ca9-5e0220a464f4
ms.openlocfilehash: 922224dc81858076770a36551df26c89940b3282
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943910"
---
# <a name="_aligned_msize"></a>_aligned_msize

ヒープで割り当てられたメモリ ブロックのサイズを返します。

## <a name="syntax"></a>構文

```C
size_t _msize(
   void *memblock,
   size_t alignment,
   size_t offset
);
```

### <a name="parameters"></a>パラメーター

*memblock*<br/>
メモリ ブロックへのポインター。

*alignment*<br/>
アラインメント値。2 の整数乗である必要があります。

*オフセット*<br/>
アラインメントを強制するためのメモリ割り当てへのオフセット。

## <a name="return-value"></a>戻り値

符号なし整数としてサイズ (バイト数) を返します。

## <a name="remarks"></a>Remarks

**_Aligned_msize**関数は、 [_aligned_malloc](aligned-malloc.md)または[_aligned_realloc](aligned-realloc.md)への呼び出しによって割り当てられたメモリブロックのサイズをバイト単位で返します。 *アラインメント*値と*オフセット*値は、ブロックを割り当てた関数に渡された値と同じである必要があります。

アプリケーションが C ランタイムライブラリのデバッグバージョンにリンクされている場合、 **_aligned_msize**は[_aligned_msize_dbg](aligned-msize-dbg.md)に解決されます。 デバッグ プロセス中のヒープの管理方法の詳細については、「[CRT デバッグ ヒープ](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。

この関数は、そのパラメーターを検証します。 *Memblock*が null ポインターであるか、または*アラインメント*が2の累乗ではない場合、 **_Msize**は「パラメーターの[検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 エラーが処理された場合、関数は**errno**を**EINVAL**に設定し、-1 を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_msize**|\<malloc.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>関連項目

[メモリ割り当て](../../c-runtime-library/memory-allocation.md)<br/>
