---
title: _CrtSetBreakAlloc
ms.date: 11/04/2016
api_name:
- _CrtSetBreakAlloc
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
- CrtSetBreakAlloc
- _CrtSetBreakAlloc
helpviewer_keywords:
- CrtSetBreakAlloc function
- _CrtSetBreakAlloc function
ms.assetid: 33bfc6af-a9ea-405b-a29f-1c2d4d9880a1
ms.openlocfilehash: e13c908c1efd1af9196885dee6e3b0f45845946b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942313"
---
# <a name="_crtsetbreakalloc"></a>_CrtSetBreakAlloc

指定されたオブジェクト割り当て順序番号にブレークポイントを設定します (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
long _CrtSetBreakAlloc(
   long lBreakAlloc
);
```

### <a name="parameters"></a>パラメーター

*lBreakAlloc*<br/>
ブレークポイントを設定する割り当て順序番号。

## <a name="return-value"></a>戻り値

ブレークポイントが設定されていた、以前のオブジェクト割り当て順序番号を返します。

## <a name="remarks"></a>Remarks

**_CrtSetBreakAlloc**を使用すると、アプリケーションはメモリ割り当ての特定の時点で中断し、要求の発生元にさかのぼってトレースすることで、メモリリークの検出を実行できます。 関数は、メモリ ブロックがヒープ上に割り当てられたときに決められた、シーケンシャルなオブジェクト割り当て順序番号を使用します。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_CrtSetBreakAlloc**の呼び出しはプリプロセス中に削除されます。

オブジェクト割り当て順序番号は、Crtdbg.h で定義されている **_CrtMemBlockHeader** 構造体の *lRequest* フィールドに格納されます。 メモリブロックに関する情報がいずれかのデバッグダンプ関数によって報告された場合、この数はの{36}ように中かっこで囲まれます。

**_CrtSetBreakAlloc**を他のメモリ管理関数と共に使用する方法の詳細については、「[ヒープ割り当て要求の追跡](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。 デバッグ バージョンのベース ヒープでのメモリ ブロックの割り当て、初期化、管理の方法について詳しくは、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_CrtSetBreakAlloc**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="example"></a>例

```C
// crt_setbrkal.c
// compile with: -D_DEBUG /MTd -Od -Zi -W3 /c /link -verbose:lib -debug

/*
* In this program, a call is made to the _CrtSetBreakAlloc routine
* to verify that the debugger halts program execution when it reaches
* a specified allocation number.
*/

#include <malloc.h>
#include <crtdbg.h>

int main( )
{
        long allocReqNum;
        char *my_pointer;

        /*
         * Allocate "my_pointer" for the first
         * time and ensure that it gets allocated correctly
         */
        my_pointer = malloc(10);
        _CrtIsMemoryBlock(my_pointer, 10, &allocReqNum, NULL, NULL);

        /*
         * Set a breakpoint on the allocation request
         * number for "my_pointer"
         */
        _CrtSetBreakAlloc(allocReqNum+2);

        /*
         * Alternate freeing and reallocating "my_pointer"
         * to verify that the debugger halts program execution
         * when it reaches the allocation request
         */
        free(my_pointer);
        my_pointer = malloc(10);
        free(my_pointer);
        my_pointer = malloc(10);
        free(my_pointer);
}
```

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
