---
title: _CrtDumpMemoryLeaks
ms.date: 11/04/2016
api_name:
- _CrtDumpMemoryLeaks
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
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
ms.openlocfilehash: dae93577f5c0c0297606577c05d6b6ef2040c831
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938828"
---
# <a name="_crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks

メモリ リークが発生したときに、デバッグ ヒープ内のすべてのメモリ ブロックをダンプします (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C

int _CrtDumpMemoryLeaks( void );
```

## <a name="return-value"></a>戻り値

**_CrtDumpMemoryLeaks**は、メモリリークが見つかった場合に TRUE を返します。 それ以外の場合、関数は FALSE を返します。

## <a name="remarks"></a>Remarks

**_CrtDumpMemoryLeaks**関数は、プログラムの実行開始以降にメモリリークが発生したかどうかを判断します。 メモリ リークが見つかると、ヒープ内のすべてのオブジェクトのデバッグ ヘッダー情報が、ユーザーが判読できる形式でダンプされます。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_CrtDumpMemoryLeaks**の呼び出しはプリプロセス中に削除されます。

**_CrtDumpMemoryLeaks**は、プログラムの実行の終了時に頻繁に呼び出され、アプリケーションによって割り当てられたすべてのメモリが解放されたことを確認します。 関数は、 [_CrtSetDbgFlag](crtsetdbgflag.md)関数を使用して[_CrtDbgFlag](../../c-runtime-library/crtdbgflag.md)フラグの **_CRTDBG_LEAK_CHECK_DF**ビットフィールドを有効にすることで、プログラムの終了時に自動的に呼び出すことができます。

**_CrtDumpMemoryLeaks**は、 [_CrtMemCheckpoint](crtmemcheckpoint.md)を呼び出してヒープの現在の状態を取得し、解放されていないブロックの状態をスキャンします。 解放さブロックが検出されると、 **_CrtDumpMemoryLeaks**は[_CrtMemDumpAllObjectsSince](crtmemdumpallobjectssince.md)を呼び出して、プログラムの実行開始からヒープに割り当てられたすべてのオブジェクトの情報をダンプします。

既定では、内部 C ランタイムブロック ( **_CRT_BLOCK**) はメモリダンプ操作に含まれません。 [_CrtSetDbgFlag](crtsetdbgflag.md)関数を使用すると、 **_crtDbgFlag**の **_CRTDBG_CHECK_CRT_DF**ビットをオンにして、これらのブロックをリーク検出プロセスに含めることができます。

ヒープ状態関数と **_CrtMemState**構造体の詳細については、「[ヒープ状態レポート関数](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。 デバッグ バージョンのベース ヒープでのメモリ ブロックの割り当て、初期化、管理の方法について詳しくは、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_CrtDumpMemoryLeaks**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="example"></a>例

**_CrtDumpMemoryLeaks**の使用例については、 [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)を参照してください。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
