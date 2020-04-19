---
title: _CrtMemDifference
ms.date: 11/04/2016
api_name:
- _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
ms.openlocfilehash: 51bfa014d54f55843fcb112f318f143774abf8f3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938709"
---
# <a name="_crtmemdifference"></a>_CrtMemDifference

2 つのメモリ状態を比較し、その違いを返します (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
int _CrtMemDifference(
   _CrtMemState *stateDiff,
   const _CrtMemState *oldState,
   const _CrtMemState *newState
);
```

### <a name="parameters"></a>パラメーター

*stateDiff*<br/>
2つのメモリ状態 (返される) の相違点を格納するために使用される **_CrtMemState**構造体へのポインター。

*oldState*<br/>
以前のメモリ状態 ( **_CrtMemState**構造体) へのポインター。

*newState*<br/>
後のメモリ状態 ( **_CrtMemState**構造体) へのポインター。

## <a name="return-value"></a>戻り値

メモリ状態が大きく異なる場合、 **_CrtMemDifference**は TRUE を返します。 それ以外の場合、関数は FALSE を返します。

## <a name="remarks"></a>Remarks

**_CrtMemDifference**関数は、 *Oldstate*と*newState*を比較し、それらの相違点を*statediff*に格納します。これをアプリケーションで使用して、メモリリークなどのメモリの問題を検出できます。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_CrtMemDifference**の呼び出しはプリプロセス中に削除されます。

*newState*と*Oldstate*は、crtdbg.h で定義されている **_CrtMemState**構造体への有効なポインターである必要があります。これは、 **_CrtMemDifference**を呼び出す前に、 [_CrtMemCheckpoint](crtmemcheckpoint.md)によって入力されています。 *Statediff*は、 **_CrtMemState**構造体の以前に割り当てられたインスタンスへのポインターである必要があります。 *Statediff*、 *newState*、または*oldstate*が**NULL**の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 [errno、_doserrno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)は**EINVAL**に設定され、関数は FALSE を返します。

**_CrtMemDifference**は、 *oldstate*のブロックの **_CrtMemState**フィールド値と*newState*内のブロックの値を比較し、その結果を*statediff*に格納します。 割り当てられているブロックの型の数または各型に割り当てられているブロックの合計数が 2 つのメモリ状態で異なる場合、この 2 つの状態は、大きく異なると言えます。 2つの状態に対して一度に割り当てられた最大量と、2つの状態の合計割り当ての差は*Statediff*にも格納されます。

既定では、内部 C ランタイムブロック ( **_CRT_BLOCK**) は、メモリ状態操作に含まれません。 [_CrtSetDbgFlag](crtsetdbgflag.md)関数を使用すると、 **_crtDbgFlag**の **_CRTDBG_CHECK_CRT_DF**ビットをオンにして、これらのブロックをリーク検出などのメモリ状態操作に含めることができます。 解放されたメモリブロック ( **_FREE_BLOCK**) では、 **_CrtMemDifference**が TRUE を返すことはありません。

ヒープ状態関数と **_CrtMemState**構造体の詳細については、「[ヒープ状態レポート関数](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。 デバッグ バージョンのベース ヒープに対するメモリ ブロックの割り当て、初期化、管理方法については、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_CrtMemDifference**|\<crtdbg.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

**ライブラリ**[CRT ライブラリ機能](../../c-runtime-library/crt-library-features.md)のデバッグバージョンのみ。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
