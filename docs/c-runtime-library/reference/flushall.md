---
title: _flushall
ms.date: 11/04/2016
api_name:
- _flushall
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _flushall
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
ms.openlocfilehash: dce7412ccc19d4870494851d366c059ff01de16a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957136"
---
# <a name="_flushall"></a>_flushall

すべてのストリームをフラッシュし、すべてのバッファーをクリアします。

## <a name="syntax"></a>構文

```C
int _flushall( void );
```

## <a name="return-value"></a>戻り値

**_flushall**は、開いているストリーム (入力と出力) の数を返します。 エラーの戻り値はありません。

## <a name="remarks"></a>Remarks

既定では、 **_flushall**関数は、開いている出力ストリームに関連付けられているすべてのバッファーの内容を適切なファイルに書き込みます。 開いている入力ストリームに関連付けられているすべてのバッファーでは、現在の内容がクリアされます。 これらのバッファーは通常はオペレーティング システムによって保持され、データをディスクに自動的に書き込むための最適なタイミングが決定されます。タイミングとしては、バッファーがいっぱいになったとき、ストリームが閉じられるとき、プログラムがストリームを閉じずに正常に終了したときがあります。

読み取りが **_flushall**の呼び出しに続いている場合、新しいデータが入力ファイルからバッファーに読み込まれます。 **_Flushall**を呼び出すと、すべてのストリームが開いたままになります。

ランタイム ライブラリのディスクへのコミットの機能を使用すると、重要なデータをオペレーティング システムのバッファーではなく、ディスクに直接書き込むことができます。 プログラムのオブジェクト ファイルを Commode.obj にリンクすると、既存のプログラムを書き直さずに、この機能を有効にできます。生成された実行可能ファイルでは、 **_flushall**を呼び出して、すべてのバッファーの内容をディスクに書き込みます。 **_Flushall**と[fflush](fflush.md)のみが、commode .obj によって影響を受けます。

ディスクへのコミットの機能の制御については、「[ストリーム入出力](../../c-runtime-library/stream-i-o.md)」、「[fopen](fopen-wfopen.md)」、および「[_fdopen](fdopen-wfdopen.md)」を参照してください。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_flushall.c
// This program uses _flushall
// to flush all open buffers.

#include <stdio.h>

int main( void )
{
   int numflushed;

   numflushed = _flushall();
   printf( "There were %d streams flushed\n", numflushed );
}
```

```Output
There were 3 streams flushed
```

## <a name="see-also"></a>関連項目

[ストリーム入出力](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
