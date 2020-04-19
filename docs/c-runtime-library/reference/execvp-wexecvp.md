---
title: _execvp、_wexecvp
ms.date: 11/04/2016
api_name:
- _execvp
- _wexecvp
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
- _execvp
- wexecvp
- _wexecvp
helpviewer_keywords:
- _execvp function
- _wexecvp function
- wexecvp function
- execvp function
ms.assetid: a4db15df-b204-4987-be7c-de84c3414380
ms.openlocfilehash: 60de62a61c78152cd4a2d8053da41a37a4091424
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941787"
---
# <a name="_execvp-_wexecvp"></a>_execvp、_wexecvp

新しい子プロセスを読み込んで実行します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
intptr_t _execvp(
   const char *cmdname,
   const char *const *argv
);
intptr_t _wexecvp(
   const wchar_t *cmdname,
   const wchar_t *const *argv
);
```

### <a name="parameters"></a>パラメーター

*cmdname*<br/>
実行するファイルのパス。

*argv*<br/>
パラメーターへのポインターの配列。

## <a name="return-value"></a>戻り値

成功した場合、これらの関数が呼び出しプロセスに戻ることはありません。 戻り値-1 はエラーを示します。この場合、 **errno**グローバル変数が設定されます。

|**errno**値|説明|
|-------------------|-----------------|
|**E2BIG**|引数と環境設定には、32 KB を超える領域が必要です。|
|**EACCES**|指定されたファイルでロック違反または共有違反が発生しています。|
|**EINVAL**|無効なパラメーター。|
|**EMFILE**|開いているファイルの数が多すぎます (指定されたファイルは、実行可能ファイルであるかどうかを確認するために開く必要があります)。|
|**ENOENT**|ファイルまたはパスが見つかりません。|
|**ENOEXEC**|指定されたファイルが実行可能ファイルでないか、無効な実行可能ファイル形式です。|
|**ENOMEM**|新しいプロセスを実行するのに十分なメモリがないか、使用できるメモリが破損しているか、または無効なブロックが存在します (呼び出しプロセスが正しく割り当てられていないことを示します)。|

リターン コードの詳細については、「[_doserrno、errno、_sys_errlist、および _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」を参照してください。

## <a name="remarks"></a>Remarks

これらの各関数は、新しいプロセスを読み込んで実行し、コマンドライン引数へのポインターの配列を渡し、 **PATH**環境変数を使用して実行するファイルを検索します。

これら**の関数は**、パラメーターを検証します。 *Cmdname*が null ポインターの場合、または*argv*が null ポインター、空の配列へのポインター、または配列に最初の引数として空の文字列が含まれている場合、これらの関数は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は**errno**を**EINVAL**に設定し、-1 を返します。 プロセスは起動されません。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|オプション ヘッダー|
|--------------|---------------------|---------------------|
|**_execvp**|\<process.h>|\<errno.h>|
|**_wexecvp**|\<process.h> または \<wchar.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[_exec 関数、_wexec 関数](../../c-runtime-library/exec-wexec-functions.md)」の例を参照してください。

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[_exec、_wexec 系関数](../../c-runtime-library/exec-wexec-functions.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_spawn 系関数と _wspawn 系関数](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
