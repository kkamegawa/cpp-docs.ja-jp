﻿---
title: exit、_Exit、_exit
ms.date: 1/02/2018
apiname:
- _exit
- exit
apilocation:
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
ms.openlocfilehash: 7b2a22649d779f382bb4055b1e44c14312627ccd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451754"
---
# <a name="exit-exit-exit"></a>exit、_Exit、_exit

呼び出しプロセスを終了します。 **exit**はクリーンアップ後に、関数が終了されます。**\_exit**と **\_Exit**は直ちに終了します。

> [!NOTE]
> テスト シナリオまたはデバッグ シナリオを除く、ユニバーサル Windows プラットフォーム (UWP) アプリをシャット ダウンは、このメソッドを使用しないでください。 ストア アプリを終了するプログラムや UI の方法はに従って許可されていません、 [Microsoft Store ポリシー](/legal/windows/agreements/store-policies)します。 詳細については、次を参照してください。 [UWP アプリのライフ サイクル](/windows/uwp/launch-resume/app-lifecycle)します。 Windows 10 アプリについて詳しくは、「 [Windows 10 アプリの使用方法のガイド](https://developer.microsoft.com/windows/apps)」をご覧ください。

## <a name="syntax"></a>構文

```C
void exit(
   int const status
);
void _Exit(
   int const status
);
void _exit(
   int const status
);
```

### <a name="parameters"></a>パラメーター

*status*<br/>
終了ステータス コード。

## <a name="remarks"></a>Remarks

**exit**、 **\_Exit**と **\_exit**関数が呼び出し元のプロセスを終了します。 **exit**関数がデストラクターを呼び出します、スレッド ローカル オブジェクトの呼び出し、— 後入れ先出し (LIFO) の順序で — によって登録されている関数**atexit**と **\_onexit**をプロセスが終了する前にすべてのファイル バッファーをフラッシュします。 **_Exit**と **_exit**関数は、スレッド ローカル オブジェクトの破棄または処理せず、プロセスを終了**atexit**または **_onexit**関数、ストリーム バッファーのフラッシュもしないでします。

ですが、 **exit**、 **\_Exit** と **\_exit** 呼び出しは、値の値を返しません *状態* ホスト環境を使用可能にまたは、プロセスの終了後、存在する場合、呼び出し元のプロセスを待機しています。 呼び出し元のセットでは、通常、 *状態* 値を通常の終了を示す 0 またはその他の値はエラーを示します。 *状態* 値は、オペレーティング システムのバッチ コマンドを使用可能な **ERRORLEVEL** は 2 つの定数のいずれかで表されます: **EXIT\_SUCCESS** 値を表す0、または **EXIT\_FAILURE** 1 の値を表します。

**exit**、 **\_Exit**、 **\_exit**、 **quick\_exit**、 **\_cexit**、および **\_c\_exit**関数の動作は次のようにします。

|関数|説明|
|--------------|-----------------|
|**exit**|完全な C ライブラリの終了処理を実行してプロセスを終了し、指定されたステータス コードをホスト環境に提供します。|
|**_Exit**|最低限の C ライブラリの終了処理を実行してプロセスを終了し、指定されたステータス コードをホスト環境に提供します。|
|**_exit**|最低限の C ライブラリの終了処理を実行してプロセスを終了し、指定されたステータス コードをホスト環境に提供します。|
|**quick_exit**|高速な C ライブラリの終了処理を実行してプロセスを終了し、指定されたステータス コードをホスト環境に提供します。|
|**_cexit**|完全な C ライブラリの終了処理を実行し、呼び出し元に戻ります。 プロセスを終了しません。|
|**_c_exit**|最低限の C ライブラリの終了処理を実行し、呼び出し元に戻ります。 プロセスを終了しません。|

呼び出すと、 **exit**、 **\_Exit** または **_exit** 関数の呼び出し時に存在する一時または自動オブジェクトのデストラクターは呼び出されません。 自動オブジェクトは、関数で定義されている非静的ローカル オブジェクトです。 一時オブジェクトは、関数呼び出しによって返される値など、コンパイラによって作成されるオブジェクトです。 呼び出す前に、自動オブジェクトを破棄する **exit**、 **\_Exit**、 または **\_exit**、 明示的に次のように、オブジェクトのデストラクターを呼び出します。

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

使用しない**DLL_PROCESS_ATTACH**を呼び出す**exit**から**DllMain**します。 終了する、 **DLLMain**関数を返す**FALSE**から**DLL_PROCESS_ATTACH**します。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**exit**、 **_Exit**、 **_exit**|\<process.h> または \<stdlib.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_exit.c
// This program returns an exit code of 1. The
// error code could be tested in a batch file.

#include <stdlib.h>

int main( void )
{
   exit( 1 );
}
```

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit、_c_exit](cexit-c-exit.md)<br/>
[_exec、_wexec 系関数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn 系関数と _wspawn 系関数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
