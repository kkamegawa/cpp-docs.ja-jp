---
title: _execl、_wexecl
ms.date: 11/04/2016
api_name:
- _execl
- _wexecl
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
- _execl
- _wexecl
- wexecl
helpviewer_keywords:
- _execl function
- wexecl function
- _wexecl function
- execl function
ms.assetid: 81fefb8a-0a06-4221-b2bc-be18e38e89f4
ms.openlocfilehash: 714ef80c4909e92100c4fa869b7544239f8edeb7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941950"
---
# <a name="_execl-_wexecl"></a>_execl、_wexecl

新しい子プロセスを読み込んで実行します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
intptr_t _execl(
   const char *cmdname,
   const char *arg0,
   ... const char *argn,
   NULL
);
intptr_t _wexecl(
   const wchar_t *cmdname,
   const wchar_t *arg0,
   ... const wchar_t *argn,
   NULL
);
```

### <a name="parameters"></a>パラメーター

*cmdname*<br/>
実行されるファイルのパス。

*arg0*、...*argn*<br/>
パラメーターへのポインターのリスト。

## <a name="return-value"></a>戻り値

成功した場合、これらの関数が呼び出しプロセスに戻ることはありません。 戻り値-1 はエラーを示します。この場合、 **errno**グローバル変数が設定されます。

|errno の値|説明|
|-----------------|-----------------|
|**E2BIG**|引数と環境設定には、32 KB を超える領域が必要です。|
|**EACCES**|指定されたファイルでロック違反または共有違反が発生しています。|
|**EINVAL**|無効なパラメーター (1 つまたは複数のパラメーターが null ポインターまたは空の文字列の場合)。|
|**EMFILE**|開いているファイルの数が多すぎます (指定されたファイルは、実行可能ファイルであるかどうかを確認するために開く必要があります)。|
|**ENOENT**|ファイルまたはパスが見つかりません。|
|**ENOEXEC**|指定されたファイルが実行可能ファイルでないか、無効な実行可能ファイル形式です。|
|**ENOMEM**|新しいプロセスを実行するのに十分なメモリがないか、使用できるメモリが破損しているか、または無効なブロックが存在します (呼び出しプロセスが正しく割り当てられていないことを示します)。|

## <a name="remarks"></a>Remarks

これらの各関数は新しいプロセスを読み込んで実行し、各コマンド ライン引数を個別のパラメーターとして渡します。 1 番目の引数はコマンドまたは実行可能ファイルの名前で、2 番目の引数は、1 番目と同じにする必要があります。 これは、実行されるプロセスの `argv[0]` になります。 3 番目の引数は、実行されるプロセスの 1 番目の引数 `argv[1]` です。

これら**の関数は**、パラメーターを検証します。 *Cmdname*または*arg0*が null ポインターまたは空の文字列の場合、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、これらの関数は無効なパラメーターハンドラーを呼び出します。実行の継続が許可された場合、これらの関数は**errno**をに**設定します。EINVAL**を返し、-1 を返します。 新しいプロセスは実行されません。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|オプション ヘッダー|
|--------------|---------------------|---------------------|
|**_execl**|\<process.h>|\<errno.h>|
|**_wexecl**|\<process.h> または \<wchar.h>|\<errno.h>|

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
