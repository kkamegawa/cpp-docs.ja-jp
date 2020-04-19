---
title: _CrtSetAllocHook
ms.date: 11/04/2016
api_name:
- _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
ms.openlocfilehash: 303f682b54abc5e44cb7fdd4c89012dd9913288b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938481"
---
# <a name="_crtsetallochook"></a>_CrtSetAllocHook

C ランタイム デバッグ メモリ割り当てプロセスにフックして、クライアント定義割り当て関数をインストールします (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
_CRT_ALLOC_HOOK _CrtSetAllocHook(
   _CRT_ALLOC_HOOK allocHook
);
```

### <a name="parameters"></a>パラメーター

*allocHook*<br/>
C ランタイム デバッグ メモリ割り当てプロセスにフックする新しいクライアント定義割り当て関数。

## <a name="return-value"></a>戻り値

以前に定義された割り当てフック関数を返します。 *allocHook*が**null**の場合は**null**を返します。

## <a name="remarks"></a>Remarks

**_CrtSetAllocHook**を使用すると、アプリケーションは独自の割り当て関数を C ランタイムデバッグライブラリのメモリ割り当てプロセスにフックできます。 そのため、メモリ ブロックの割り当て、再割り当て、または解放を行うためのデバッグ割り当て関数へのすべての呼び出しは、アプリケーションのフック関数への呼び出しをトリガーします。 **_CrtSetAllocHook**は、アプリケーションがメモリ不足の状況をどのように処理するか、割り当てパターンを調べる機能、および後で分析するために割り当て情報を記録する機会をテストするための簡単な方法をアプリケーションに提供します。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_CrtSetAllocHook**の呼び出しはプリプロセス中に削除されます。

**_CrtSetAllocHook**関数は、 *allocHook*で指定された新しいクライアント定義割り当て関数をインストールし、以前に定義されたフック関数を返します。 次の例は、クライアント定義割り当てフックをどのようにプロトタイプ宣言するかを示しています。

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

**Alloctype**引数は、割り当てのフック関数への呼び出しをトリガーした割り当て操作 ( **_HOOK_ALLOC**、 **_HOOK_REALLOC**、および **_HOOK_FREE**) の種類を指定します。 トリガーの割り当ての種類が **_HOOK_FREE**である場合、 *userData*は解放されるメモリブロックのユーザーデータセクションへのポインターです。 ただし、トリガーする割り当ての種類が **_HOOK_ALLOC**または **_HOOK_REALLOC**の場合、メモリブロックがまだ割り当てられていないため、 *userData*は**NULL**になります。

*size*は、メモリブロックのサイズをバイト単位で指定します。 *blocktype*はメモリブロックの種類を示し、 *requestnumber*はメモリブロックのオブジェクト割り当て順序番号です。使用可能な場合は、 *filename*と lineNumber を指定します。トリガーする割り当て操作が開始されたソースファイル名と行番号を指定します。

フック関数は処理の完了後、続行方法を主要な C ランタイム割り当てプロセスに伝えるブール値を返す必要があります。 フック関数が呼び出されたことがないかのようにメイン割り当てプロセスが続行されるようにする場合、フック関数は**TRUE**を返します。 このようにすると、元のトリガーする割り当て操作が実行されます。 フック関数は、この実装を使用して、現在の割り当て操作またはデバッグ ヒープの状態に影響を与えずに、後で分析するための割り当て情報を収集および保存できます。

トリガーされた割り当て操作が呼び出されて失敗したかのように、フック関数がメイン割り当てプロセスを続行する場合、フック関数は**FALSE**を返す必要があります。 フック関数は、この実装を使用して、さまざまなメモリの状況とデバッグ ヒープの状態をシミュレートし、各状況をアプリケーションがどのように処理するかをテストできます。

フック関数をクリアするには、 **NULL**を **_CrtSetAllocHook**に渡します。

**_CrtSetAllocHook**を他のメモリ管理関数と共に使用する方法、または独自のクライアント定義フック関数を記述する方法の詳細については、「[デバッグ用フック関数の書き込み](/visualstudio/debugger/debug-hook-function-writing)」を参照してください。

> [!NOTE]
> **_CrtSetAllocHook**は **/clr: pure**ではサポートされていません。 **/Clr: pure**および **/clr: safe**コンパイラオプションは visual studio 2015 で非推奨とされており、visual studio 2017 では削除されています。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="example"></a>例

**_CrtSetAllocHook**の使用例については、 [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)を参照してください。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
