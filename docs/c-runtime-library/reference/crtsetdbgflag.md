---
title: _CrtSetDbgFlag
ms.date: 11/04/2016
api_name:
- _CrtSetDbgFlag
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
- _CRTDBG_REPORT_FLAG
- _CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_EVERY_128_DF
- CRTDBG_CHECK_EVERY_1024_DF
- _CRTDBG_CHECK_EVERY_128_DF
- CrtSetDbgFlag
- CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_EVERY_1024_DF
- _CrtSetDbgFlag
- CRTDBG_REPORT_FLAG
helpviewer_keywords:
- _CRTDBG_CHECK_EVERY_16_DF macro
- CRTDBG_CHECK_EVERY_16_DF macro
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_ALLOC_MEM_DF macro
- CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_ALLOC_MEM_DF macro
- _CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_1024_DF macro
- CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_CHECK_EVERY_1024_DF macro
- _CrtSetDbgFlag function
- CrtSetDbgFlag function
- _CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: b5657ffb-6178-4cbf-9886-1af904ede94c
ms.openlocfilehash: 8506b593a579c8dd1791e56c320bd9d8e2ee9ba2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938613"
---
# <a name="_crtsetdbgflag"></a>_CrtSetDbgFlag

**_crtDbgFlag** フラグの状態を取得または変更して、デバッグ ヒープ マネージャーの割り当て動作を制御します (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
int _CrtSetDbgFlag(
   int newFlag
);
```

### <a name="parameters"></a>パラメーター

*newFlag*<br/>
**_crtDbgFlag** の新しい状態。

## <a name="return-value"></a>戻り値

**_crtDbgFlag** の以前の状態を返します。

## <a name="remarks"></a>Remarks

**_CrtSetDbgFlag**関数を使用すると、アプリケーションは、 **_crtDbgFlag**フラグのビットフィールドを変更することによって、デバッグヒープマネージャーがメモリ割り当てを追跡する方法を制御できます。 ビットを設定する (オンにする) ことによって、アプリケーションはデバッグ ヒープ マネージャーに特別なデバッグ操作の実行を指示できます。たとえば、アプリケーション終了時にメモリ リークを確認し、リークを発見した場合に報告したり、解放されたメモリ ブロックをヒープのリンク リストに残すように指定してメモリ不足状況をシミュレーションしたり、すべての割り当て要求時に各メモリ ブロックを検査してヒープの整合性を検証したりすることができます。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_CrtSetDbgFlag**の呼び出しはプリプロセス中に削除されます。

次の表は、 **_crtDbgFlag** のビット フィールドと、その動作の説明の一覧です。 ビットを設定すると、診断出力が増加し、プログラムの実行速度が低下するため、これらのビットは既定では設定されていません (オフになっています)。 これらのビット フィールドの詳細については、「[ヒープの状態をレポートする関数](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。

|ビット フィールド|既定値|説明|
|---------------|-------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|ON|代わっデバッグヒープ割り当てを有効にし、 **_CLIENT_BLOCK**などのメモリブロック型識別子の使用を有効にします。 オートヒープのリンクリストに新しい割り当てを追加しますが、block type を **_IGNORE_BLOCK**に設定します。<br /><br /> ヒープ頻度チェック マクロのいずれかと組み合わせることもできます。|
|**_CRTDBG_CHECK_ALWAYS_DF**|OFF|代わっ割り当てと割り当て解除のすべての要求で[_CrtCheckMemory](crtcheckmemory.md)を呼び出します。 OFF: **_CrtCheckMemory**は明示的に呼び出す必要があります。<br /><br /> このフラグが設定されている場合、ヒープ頻度チェック マクロは効果がありません。|
|**_CRTDBG_CHECK_CRT_DF**|OFF|代わっリーク検出とメモリ状態の違いの操作に **_CRT_BLOCK** types を含めます。 オートランタイムライブラリによって内部的に使用されるメモリは、これらの操作によって無視されます。<br /><br /> ヒープ頻度チェック マクロのいずれかと組み合わせることもできます。|
|**_CRTDBG_DELAY_FREE_MEM_DF**|OFF|代わっ解放されたメモリブロックをヒープのリンクリストに保持し、それらを **_FREE_BLOCK**型に割り当てて、バイト値0xdd を格納します。 オート解放されたブロックをヒープのリンクリストに保持しないでください。<br /><br /> ヒープ頻度チェック マクロのいずれかと組み合わせることもできます。|
|**_CRTDBG_LEAK_CHECK_DF**|OFF|代わっ[_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md)の呼び出しによってプログラムの終了時に自動リークチェックを実行し、アプリケーションが割り当てたメモリをすべて解放できなかった場合はエラーレポートを生成します。 オートプログラムの終了時に自動的にリークチェックを実行しません。<br /><br /> ヒープ頻度チェック マクロのいずれかと組み合わせることもできます。|

**ヒープ頻度チェック マクロ**

C ランタイムライブラリが**malloc**、 **realloc**、 **free**、および **_msize**への呼び出しの回数に基づいてデバッグヒープ ( **_CrtCheckMemory**) の検証を実行する頻度を指定できます。

次に、 **_CrtSetDbgFlag**は、値の*newflag*パラメーターの上位16ビットを調べます。 指定された値は、 **_CrtCheckMemory**呼び出し間の**malloc**、 **realloc**、 **free**、および **_msize**の呼び出しの数です。 この目的のために、4 つの定義済みマクロが用意されています。

|マクロ|_CrtCheckMemory の呼び出し間の malloc、realloc、free、および _msize の呼び出し数|
|-----------|------------------------------------------------------------------------------------------|
|_CRTDBG_CHECK_EVERY_16_DF|16|
|_CRTDBG_CHECK_EVERY_128_DF|128|
|_CRTDBG_CHECK_EVERY_1024_DF|1024|
|_CRTDBG_CHECK_DEFAULT_DF|0 (既定では、ヒープ チェックなし)|

既定では、 **_CrtCheckMemory**は、 **malloc**、 **realloc**、 **free**、および **_msize**を呼び出すたびに、1024回呼び出されます。

たとえば、次のコードを使用して、16の**malloc**、 **realloc**、 **free**、および **_msize**の各操作ごとにヒープチェックを指定できます。

```C
#include <crtdbg.h>
int main( )
{
    int tmp;

    // Get the current bits
    tmp = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);

    // Clear the upper 16 bits and OR in the desired frequency
    tmp = (tmp & 0x0000FFFF) | _CRTDBG_CHECK_EVERY_16_DF;

    // Set the new bits
    _CrtSetDbgFlag(tmp);
}
```

_CRTDBG_CHECK_ALWAYS_DF を指定した場合、 *Newflag*パラメーターの上位16ビットは無視されます。 この場合、 **malloc**、 **realloc**、 **free**、および **_msize**を呼び出すたびに **_CrtCheckMemory**が呼び出されます。

*Newflag*は、 **_crtDbgFlag**に適用する新しい状態であり、各ビットフィールドの値の組み合わせです。

### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>これらのビット フィールドを変更して、フラグの新しい状態を作成するには

1. **_CRTDBG_REPORT_FLAG**に等しい*newflag*を使用して **_CrtSetDbgFlag**を呼び出し、現在の **_crtDbgFlag**の状態を取得し、戻り値を一時変数に格納します。

1. 対応するビットマスクを持つ一時変数のビットごとの**or**を使用してビットをオンにします (アプリケーションコードではマニフェスト定数で表されます)。

1. 一時変数と、適切なビットマスクのビットごとの **NOT** との **AND** 演算を行い、他のビットをオフにします。

1. **_CrtDbgFlag**の新しい状態を設定するには、一時変数に格納されている値と等しい*newflag*を使用して **_CrtSetDbgFlag**を呼び出します。

次のコードは、解放されたメモリブロックをヒープのリンクリストに保持してメモリ不足の状態をシミュレートし、割り当て要求のたびに **_CrtCheckMemory**が呼び出されないようにする方法を示しています。

```C
// Get the current state of the flag
// and store it in a temporary variable
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn On (OR) - Keep freed memory blocks in the
// heap's linked list and mark them as freed
tmpFlag |= _CRTDBG_DELAY_FREE_MEM_DF;

// Turn Off (AND) - prevent _CrtCheckMemory from
// being called at every allocation request
tmpFlag &= ~_CRTDBG_CHECK_ALWAYS_DF;

// Set the new state for the flag
_CrtSetDbgFlag( tmpFlag );
```

メモリ管理とデバッグ ヒープの概要については、「[CRT デバッグ ヒープ](/visualstudio/debugger/crt-debug-heap-details)」を参照してください。

**_CrtSetDbgFlag**関数でフラグを無効にするには、変数**と**、ビットマスクのビットごとの**not**を使用する必要があります。

*Newflag*が有効な値でない場合、この関数は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は**errno**を**EINVAL**に設定し、 **_crtDbgFlag**の以前の状態を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_CrtSetDbgFlag**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="example"></a>例

```C
// crt_crtsetdflag.c
// compile with: /c -D_DEBUG /MTd -Od -Zi -W3 /link -verbose:lib /debug

// This program concentrates on allocating and freeing memory
// blocks to test the functionality of the _crtDbgFlag flag.

#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main( )
{
    char *p1, *p2;
    int tmpDbgFlag;

    _CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_FILE );
    _CrtSetReportFile( _CRT_ERROR, _CRTDBG_FILE_STDERR );

    // Set the debug-heap flag to keep freed blocks in the
    // heap's linked list - This will allow us to catch any
    // inadvertent use of freed memory
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_DELAY_FREE_MEM_DF;
    tmpDbgFlag |= _CRTDBG_LEAK_CHECK_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Allocate 2 memory blocks and store a string in each
    p1 = malloc( 34 );
    p2 = malloc( 38 );
    strcpy_s( p1, 34, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 38, "p2 points to a Client allocation block" );

    // Free both memory blocks
    free( p2 );
    free( p1 );

    // Set the debug-heap flag to no longer keep freed blocks in the
    // heap's linked list and turn on Debug type allocations (CLIENT)
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_ALLOC_MEM_DF;
    tmpDbgFlag &= ~_CRTDBG_DELAY_FREE_MEM_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Explicitly call _malloc_dbg to obtain the filename and
    // line number of our allocation request and also so we can
    // allocate CLIENT type blocks specifically for tracking
    p1 = _malloc_dbg( 40, _NORMAL_BLOCK, __FILE__, __LINE__ );
    p2 = _malloc_dbg( 40, _CLIENT_BLOCK, __FILE__, __LINE__ );
    strcpy_s( p1, 40, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 40, "p2 points to a Client allocation block" );

    // _free_dbg must be called to free the CLIENT block
    _free_dbg( p2, _CLIENT_BLOCK );
    free( p1 );

    // Allocate p1 again and then exit - this will leave unfreed
    // memory on the heap
    p1 = malloc( 10 );
}
```

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtCheckMemory](crtcheckmemory.md)<br/>
