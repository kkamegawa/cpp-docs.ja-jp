---
title: _CrtCheckMemory
ms.date: 11/04/2016
api_name:
- _CrtCheckMemory
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
- CrtCheckMemory
- _CrtCheckMemory
helpviewer_keywords:
- _CrtCheckMemory function
- CrtCheckMemory function
ms.assetid: 457cc72e-60fd-4177-ab5c-6ae26a420765
ms.openlocfilehash: 7e458825a81b7032310458ccda52d9299e126a35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938862"
---
# <a name="_crtcheckmemory"></a>_CrtCheckMemory

デバッグ ヒープで割り当てられたメモリ ブロックの整合性を確認します (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C

int _CrtCheckMemory( void );
```

## <a name="return-value"></a>戻り値

成功した場合、 **_CrtCheckMemory**は TRUE を返します。それ以外の場合、関数は FALSE を返します。

## <a name="remarks"></a>Remarks

**_CrtCheckMemory**関数は、基になるベースヒープを確認し、各メモリブロックを調べることによって、デバッグヒープマネージャーによって割り当てられたメモリを検証します。 基になるベースヒープ、デバッグヘッダー情報、または上書きバッファーでエラーやメモリの不整合が発生した場合、 **_CrtCheckMemory**はエラー状態を説明する情報を含むデバッグレポートを生成します。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_CrtCheckMemory**の呼び出しはプリプロセス中に削除されます。

**_CrtCheckMemory**の動作を制御するには、 [_CrtSetDbgFlag](crtsetdbgflag.md)関数を使用して[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)フラグのビットフィールドを設定します。 **_CRTDBG_CHECK_ALWAYS_DF**ビットフィールドをオンにすると、メモリ割り当て操作が要求されるたびに **_CrtCheckMemory**が呼び出されます。 この方法は実行速度を低下させますが、エラーをすばやく見つけるために役立ちます。 **_CRTDBG_ALLOC_MEM_DF**ビットフィールドをオフにすると、 **_CrtCheckMemory**はヒープを検証せず、すぐに**TRUE**を返します。

この関数は **TRUE** または **FALSE** を返すため、[_ASSERT](assert-asserte-assert-expr-macros.md) 系マクロに渡すことによって、デバッグ用の単純なエラー処理機構を作成できます。 次の例は、ヒープの破損が検出された場合に、アサーション エラーを発生させます。

```C
_ASSERTE( _CrtCheckMemory( ) );
```

**_CrtCheckMemory**を他のデバッグ関数と共に使用する方法の詳細については、「[ヒープ状態レポート機能](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。 メモリ管理とデバッグ ヒープの概要については、「[CRT デバッグ ヒープ](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_CrtCheckMemory**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="example"></a>例

**_CrtCheckMemory**の使用例については、 [crt_dbg1](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg1)を参照してください。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtSetDbgFlag](crtsetdbgflag.md)<br/>
