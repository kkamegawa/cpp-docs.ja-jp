---
title: _CrtMemDumpStatistics
ms.date: 11/04/2016
api_name:
- _CrtMemDumpStatistics
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
- CrtMemDumpStatistics
- _CrtMemDumpStatistics
helpviewer_keywords:
- _CrtMemDumpStatistics function
- CrtMemDumpStatistics function
ms.assetid: 27b9d731-3184-4a2d-b9a7-6566ab28a9fe
ms.openlocfilehash: 7aba82e3dfea220f2edc3bd3a689a48e316a0087
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938697"
---
# <a name="_crtmemdumpstatistics"></a>_CrtMemDumpStatistics

指定されたヒープ状態のデバッグ ヘッダー情報をユーザーが判読できる形式でダンプします (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
void _CrtMemDumpStatistics(
   const _CrtMemState *state
);
```

### <a name="parameters"></a>パラメーター

*state*<br/>
ダンプするヒープ状態へのポインター。

## <a name="remarks"></a>Remarks

**_CrtMemDumpStatistics**関数は、ヒープの指定された状態のデバッグヘッダー情報をユーザーが判読できる形式でダンプします。 ダンプ統計情報は、割り当ての追跡とメモリの問題の検出のためにアプリケーションで使用できます。 メモリ状態には、特定のヒープ状態、または 2 つの状態の相違点を含めることができます。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_CrtMemDumpStatistics**の呼び出しはプリプロセス中に削除されます。

*State*パラメーターは、 **_CrtMemDumpStatistics**が呼び出される前に、 [_CrtMemCheckpoint](crtmemcheckpoint.md)によって入力された、または[_CrtMemDifference](crtmemdifference.md)によって返された **_CrtMemState**構造体へのポインターである必要があります。 *State*が**NULL**の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno**は**EINVAL**に設定され、アクションは実行されません。 詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

ヒープ状態関数と **_CrtMemState**構造体の詳細については、「[ヒープ状態レポート関数](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。 デバッグ バージョンのベース ヒープでのメモリ ブロックの割り当て、初期化、管理の方法について詳しくは、「 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)」をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|省略可能なヘッダー|
|-------------|---------------------|----------------------|
|**_CrtMemDumpStatistics**|\<crtdbg.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

**ライブラリ**[CRT ライブラリ機能](../../c-runtime-library/crt-library-features.md)のデバッグバージョンのみ。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
