---
title: _exec、_wexec 系関数
ms.date: 11/04/2016
api_location:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _texecve
- texecl
- _texeclpe
- texecve
- texecv
- texeclp
- texecle
- exec
- texeclpe
- _texecvp
- _texecl
- _texecle
- wexec
- _exec
- _texeclp
- _texecvpe
- texecvpe
- _texecv
- _wexec
helpviewer_keywords:
- _texecle function
- _texecv function
- texeclpe function
- texecle function
- _texecl function
- texecv function
- _texeclp function
- _texecve function
- texecl function
- texecve function
- exec function
- texeclp function
- texecvp function
- texecvpe function
- processes, executing new
- _texecvp function
- _texeclpe function
- _wexec functions
- wexec functions
- _exec function
- _texecvpe function
ms.assetid: a261df93-206a-4fdc-b8ac-66aa7db83bc6
ms.openlocfilehash: dab670c5baef1c51c39a4c936380fab92c5103cc
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300307"
---
# <a name="_exec-_wexec-functions"></a>_exec、_wexec 系関数

この系列の各関数は、新しいプロセスを読み込んで実行します。

|||
|-|-|
|[_execl、_wexecl](../c-runtime-library/reference/execl-wexecl.md)|[_execv、_wexecv](../c-runtime-library/reference/execv-wexecv.md)|
|[_execle、_wexecle](../c-runtime-library/reference/execle-wexecle.md)|[_execve、_wexecve](../c-runtime-library/reference/execve-wexecve.md)|
|[_execlp、_wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|[_execvp、_wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|
|[_execlpe、_wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|[_execvpe、_wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|

関数名の最後の文字は、関数の種類を示します。

|_exec 関数のサフィックス|説明|
|----------------------------|-----------------|
|`e`|環境設定へのポインター配列 `envp` が新しいプロセスに渡されます。|
|`l`|コマンド ライン引数が `_exec` 関数に個別に渡されます。 通常は、新しいプロセスに渡すパラメーターの個数が事前にわかっている場合に使用します。|
|`p`|`PATH` 環境変数を使用して、実行するファイルを検索します。|
|`v`|コマンド ライン引数へのポインター配列 `argv` が `_exec` に渡されます。 通常は、新しいプロセスに渡すパラメーターの個数に変動がある場合に使用します。|

## <a name="remarks"></a>コメント

各 `_exec` 関数は、新しいプロセスを読み込んで実行します。 `_exec` 系関数はすべて、同じオペレーティング システム関数 ([CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw)) を使います。 `_exec` 系関数は、現在使用中のマルチバイト コード ページに従ってマルチバイト文字シーケンスを認識し、マルチバイト文字列の引数を適切な方法で自動的に処理します。 `_wexec` 系関数は、`_exec` 系関数のワイド文字バージョンです。 `_wexec` 系関数の処理内容は `_exec` 系関数とほぼ同様ですが、マルチバイト文字列は処理しません。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_texecl`|`_execl`|`_execl`|`_wexecl`|
|`_texecle`|`_execle`|`_execle`|`_wexecle`|
|`_texeclp`|`_execlp`|`_execlp`|`_wexeclp`|
|`_texeclpe`|`_execlpe`|`_execlpe`|`_wexeclpe`|
|`_texecv`|`_execv`|`_execv`|`_wexecv`|
|`_texecve`|`_execve`|`_execve`|`_wexecve`|
|`_texecvp`|`_execvp`|`_execvp`|`_wexecvp`|
|`_texecvpe`|`_execvpe`|`_execvpe`|`_wexecvpe`|

パラメーター `cmdname` には、新しいプロセスとして実行するファイルを指定します。 完全パス (ルートからのパス)、相対パス (現在の作業ディレクトリからのパス)、またはファイル名のいずれでも指定できます。 `cmdname` にファイル名の拡張子がない場合、または末尾にピリオド (.) がない場合、`_exec` 系関数はその名前でファイルを検索します。 検索に失敗すると、同じ基本名で拡張子が .com のファイルを検索し、続いて拡張子が .exe、.bat、.cmd のファイルを順に検索します。 `cmdname` に拡張子がある場合は、その拡張子のファイルだけを検索します。 `cmdname` の末尾にピリオドがある場合、`_exec` 関数はファイル名拡張子がない `cmdname` を検索します。 `_execlp`、`_execlpe`、`_execvp`、および `_execvpe` は、`cmdname` 環境変数に指定されたディレクトリ内で同じ処理手順を使用して `PATH` を検索します。 `cmdname` にドライブ指定子やスラッシュが含まれている場合、つまり相対パスが指定されている場合、`_exec` 呼び出しは指定のファイルだけを検索し、パスは検索しません。

`_exec` 呼び出しのパラメーターとして文字列へのポインターを指定することにより、新しいプロセスにパラメーターが渡されます。 これらの文字列が新しいプロセスのパラメーター リストとなります。 呼び出しプロセスから継承した環境設定の文字列と、新しいプロセスのパラメーター リストの文字列を合わせた長さが、32 KB を超えないようにしてください。 各文字列の終端を表す NULL 文字 ('\0') はカウントされませんが、パラメーターを区切るために自動的に挿入されるスペース文字はカウントされます。

> [!NOTE]
>  文字列に空白が含まれる場合、予期しない動作になることがあります。たとえば、`_exec` を `"hi there"` という文字列に渡すと、新しいプロセスは `"hi"` と `"there"` という 2 つの引数を使用する結果になります。 新しいプロセスでは "hi there" というファイルを開こうとするため、プロセスは失敗します。 この問題を回避するには、`"\"hi there\""` のように文字列を引用符で囲みます。

> [!IMPORTANT]
>  ユーザー入力のコンテンツを明示的にチェックしないまま `_exec` に渡さないでください。 `_exec` によって [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) が呼び出されます。そのため、パス名が修飾されていない場合、セキュリティ上の脆弱性につながる可能性があります。

`_exec` 関数は、パラメーターを検証します。 いずれかのパラメーターが null ポインター、空の文字列、または省略されている場合、「[パラメーターの検証](../c-runtime-library/parameter-validation.md)」で説明されているように、`_exec` 関数は無効なパラメーター ハンドラーを呼び出します。 実行の継続が許可された場合、これらの関数は `errno` を `EINVAL` に設定し、-1 を返します。 新しいプロセスは実行されません。

`_execl`、`_execle`、`_execlp`、および `_execlpe` では引数へのポインターが個別のパラメーターとして渡され、`_execv`、`_execve`、`_execvp`、および `_execvpe` ではポインターの配列として渡されます。 新しいプロセスには、少なくとも 1 つのパラメーター `arg0` を渡す必要があり、このパラメーターが新しいプロセスの `argv`[0] となります。 通常、このパラメーターは `cmdname` のコピーです。 ただし、別の値を使用しても、エラーは発生しません。

`_execl`、`_execle`、`_execlp`、`_execlpe` の各呼び出しは、通常、パラメーターの個数が事前にわかっている場合に使用します。 通常の場合、`arg0` パラメーターは `cmdname` へのポインターです。 パラメーター `arg1` ～ `argn` は、新しいパラメーター リストを構成する文字列を指します。 `argn` の後には、パラメーター リストの終端を示すために NULL ポインターが必要です。

`_execv`、`_execve`、`_execvp`、および `_execvpe` の各呼び出しは、新しいプロセスのパラメーターの数が変化する場合に便利です。 パラメーターへのポインターは、配列 `argv` として渡されます。 通常の場合、パラメーター `argv`[0] は `cmdname` へのポインターです。 パラメーター `argv`[1] ～ `argv`[`n`] は、新しいパラメーター リストを構成する文字列を指します。 パラメーター リストの終端を示すために、パラメーター `argv`[`n`+1] は **NULL** ポインターである必要があります。

`_exec` 呼び出しを作成するときに開いたファイルは、新しいプロセスでも開いたままです。 `_execl`、`_execlp`、`_execv`、および `_execvp` の各呼び出しでは、新しいプロセスが呼び出しプロセスの環境を継承します。 `_execle`、`_execlpe`、`_execve`、および `_execvpe` の各呼び出しでは、`envp` パラメーターを使用して環境設定のリストを渡すことで、新しいプロセスの環境を変更できます。 `envp` は文字ポインターの配列であり、最後の要素以外の各要素は、環境変数を定義する null で終わる文字列を指します。 通常、このような文字列の形式は `NAME`=`value` であり、`NAME` は環境変数名、`value` はその変数に設定する文字列の値です。 (`value` は二重引用符で囲まれていないことに注意してください)。`envp` 配列の最後の要素は**NULL**にする必要があります。 `envp` 自身が **NULL** である場合、新しいプロセスは呼び出しプロセスの環境設定を継承します。

`_exec` 系関数で実行されるプログラムは、常に、プログラムの .exe ファイル ヘッダーの maximum allocation フィールドが既定値 0xFFFFH であるかのように、メモリに読み込まれます。

`_exec` 呼び出しは、開いているファイルの変換モードを保持しません。 呼び出しプロセスから継承されたファイルを新しいプロセスで使う必要がある場合は、[_setmode](../c-runtime-library/reference/setmode.md) ルーチンを使って、ファイルの変換モードを必要なモードに設定します。 `fflush` 系関数を呼び出す前に、`_flushall` または `_exec` を使用してストリームを明示的にフラッシュするか、ストリームを閉じる必要があります。 `_exec` ルーチンの呼び出しによって作成された新しいプロセスでは、呼び出し側のシグナル設定が保持されません。 シグナル設定は、新しいプロセスでは既定値にリセットされます。

## <a name="example"></a>使用例

```c
// crt_args.c
// Illustrates the following variables used for accessing
// command-line arguments and environment variables:
// argc  argv  envp
// This program will be executed by crt_exec which follows.

#include <stdio.h>

int main( int argc,  // Number of strings in array argv
char *argv[],       // Array of command-line argument strings
char **envp )       // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    printf( "\nCommand-line arguments:\n" );
    for( count = 0; count < argc; count++ )
        printf( "  argv[%d]   %s\n", count, argv[count] );

    // Display each environment variable.
    printf( "\nEnvironment variables:\n" );
    while( *envp != NULL )
        printf( "  %s\n", *(envp++) );

    return;
}
```

次のプログラムを使用して Crt_args.exe を実行します。

```c
// crt_exec.c
// Illustrates the different versions of exec, including
//      _execl          _execle          _execlp          _execlpe
//      _execv          _execve          _execvp          _execvpe
//
// Although CRT_EXEC.C can exec any program, you can verify how
// different versions handle arguments and environment by
// compiling and specifying the sample program CRT_ARGS.C. See
// "_spawn, _wspawn Functions" for examples of the similar spawn
// functions.

#include <stdio.h>
#include <conio.h>
#include <process.h>

char *my_env[] =     // Environment for exec?e
{
   "THIS=environment will be",
   "PASSED=to new process by",
   "the EXEC=functions",
   NULL
};

int main( int ac, char* av[] )
{
   char *args[4];
   int ch;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <program> <number (1-8)>\n", av[0] );
      return;
   }

   // Arguments for _execv?
   args[0] = av[1];
   args[1] = "exec??";
   args[2] = "two";
   args[3] = NULL;

   switch( atoi( av[2] ) )
   {
   case 1:
      _execl( av[1], av[1], "_execl", "two", NULL );
      break;
   case 2:
      _execle( av[1], av[1], "_execle", "two", NULL, my_env );
      break;
   case 3:
      _execlp( av[1], av[1], "_execlp", "two", NULL );
      break;
   case 4:
      _execlpe( av[1], av[1], "_execlpe", "two", NULL, my_env );
      break;
   case 5:
      _execv( av[1], args );
      break;
   case 6:
      _execve( av[1], args, my_env );
      break;
   case 7:
      _execvp( av[1], args );
      break;
   case 8:
      _execvpe( av[1], args, my_env );
      break;
   default:
      break;
   }

   // This point is reached only if exec fails.
   printf( "\nProcess was not execed." );
   exit( 0 );
}
```

## <a name="requirements"></a>要件

**ヘッダー:** process.h

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../c-runtime-library/process-and-environment-control.md)<br/>
[abort](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit、_Exit、_exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_spawn 系関数と _wspawn 系関数](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](../c-runtime-library/reference/system-wsystem.md)
