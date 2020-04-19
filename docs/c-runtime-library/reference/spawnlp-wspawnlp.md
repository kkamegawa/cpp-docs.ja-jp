---
title: _spawnlp、_wspawnlp
ms.date: 11/04/2016
api_name:
- _wspawnlp
- _spawnlp
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
- api-ms-win-crt-process-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wspawnlp
- wspawnlp
- _spawnlp
helpviewer_keywords:
- wspawnlp function
- _spawnlp function
- processes, creating
- processes, executing new
- _wspawnlp function
- process creation
- spawnlp function
ms.assetid: 74fc6e7a-4f24-4103-9387-7177875875e6
ms.openlocfilehash: 98d5609d17f5932a81be916b878eb25333869591
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70947742"
---
# <a name="_spawnlp-_wspawnlp"></a>_spawnlp、_wspawnlp

新しいプロセスを作成して実行します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
intptr_t _spawnlp(
   int mode,
   const char *cmdname,
   const char *arg0,
   const char *arg1,
   ... const char *argn,
   NULL
);
intptr_t _wspawnlp(
   int mode,
   const wchar_t *cmdname,
   const wchar_t *arg0,
   const wchar_t *arg1,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>パラメーター

*モード*<br/>
呼び出しプロセスの実行モード。

*cmdname*<br/>
実行されるファイルのパス。

*arg0*、 *arg1*、...*argn*<br/>
引数へのポインターのリスト。 *Arg0*引数は通常、 *cmdname*へのポインターです。 引数*arg1* ~ *argn*は、新しい引数リストを形成する文字列へのポインターです。 *Argn*の後に、引数リストの末尾を示す**NULL**ポインターが必要です。

## <a name="return-value"></a>戻り値

同期 **_spawnlp**または **_wspawnlp** (*モード*用に指定された **_P_WAIT** ) からの戻り値は、新しいプロセスの終了ステータスです。 非同期の **_spawnlp**または **_wspawnlp** (*モード*用に指定された **_P_NOWAIT**または **_P_NOWAITO** ) からの戻り値は、プロセスハンドルです。 プロセスが正常に終了した場合、終了ステータスは 0 です。 生成されたプロセスが明示的に0以外の引数で**終了**ルーチンを呼び出す場合は、終了ステータスを0以外の値に設定できます。 新しいプロセスが明示的に終了ステータスを正の値に設定しなかった場合、正の値の終了ステータスは中止または割り込みによる異常終了を示します。 戻り値-1 はエラーを示します (新しいプロセスは開始されません)。 この場合、 **errno**は次のいずれかの値に設定されます。

|||
|-|-|
| **E2BIG** | 引数リストが 1024 バイトを超えています。 |
| **EINVAL** | *モード*引数が無効です。 |
| **ENOENT** | ファイルまたはパスが見つかりません。 |
| **ENOEXEC** | 指定されたファイルが実行可能ファイルでないか、無効な実行可能ファイル形式です。 |
| **ENOMEM** | 新しいプロセスを実行するのに十分なメモリがありません。 |

リターン コードの詳細については、「 [_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

これらの各関数は新しいプロセスを作成して実行し、各コマンドライン引数を個別のパラメーターとして渡し、 **PATH**環境変数を使用して実行するファイルを検索します。

これらの関数では、パラメーターの検証が行われます。 *Cmdname*または*arg0*のいずれかが空の文字列または null ポインターの場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーター例外を生成します。 実行の継続が許可された場合、これらの関数は**errno**を**EINVAL**に設定し、-1 を返します。 新しいプロセスは起動されません。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_spawnlp**|\<process.h>|
|**_wspawnlp**|\<stdio.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「 [_spawn 系関数と _wspawn 系関数](../../c-runtime-library/spawn-wspawn-functions.md)」の使用例を参照してください。

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn 系関数と _wspawn 系関数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 系関数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_flushall](flushall.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
