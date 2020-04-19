---
title: _spawn 系関数と _wspawn 系関数
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _spawn
- _tspawnlp
- _tspawnlpe
- _tspawnve
- _tspawnvp
- _tspawnvpe
- _tspawnl
- spawn
- _tspawnv
- _tspawnle
- wspawn
helpviewer_keywords:
- _tspawnve function
- _spawn functions
- _tspawnlpe function
- tspawnvpe function
- processes, creating
- tspawnve function
- _tspawnvp function
- spawn functions
- tspawnl function
- tspawnlp function
- _tspawnvpe function
- _tspawnl function
- tspawnvp function
- tspawnv function
- processes, executing new
- _tspawnv function
- tspawnle function
- process creation
- _tspawnlp function
- tspawnlpe function
- _tspawnle function
ms.assetid: bb47c703-5216-4e09-8023-8cf25bbf2cf9
ms.openlocfilehash: 81f4bf6c60a0c0e4011536e8d3bc104bbc33e04f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301705"
---
# <a name="_spawn-_wspawn-functions"></a>_spawn 系関数と _wspawn 系関数

各 `_spawn` 関数は、新しいプロセスを作成して実行します。

|||
|-|-|
|[_spawnl、_wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv、_wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|
|[_spawnle、_wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve、_wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|
|[_spawnlp、_wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp、_wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|
|[_spawnlpe、_wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe、_wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|

関数名の最後の文字は、関数の種類を示します。

|Letter|バリアント|
|-|-|
| `e`  | 環境設定へのポインター配列 `envp` が新しいプロセスに渡されます。  |
| `l`  | コマンド ライン引数が `_spawn` 関数に個別に渡されます。 このサフィックスは、通常は、新しいプロセスに渡すパラメーターの個数が事前にわかっている場合に使用します。  |
| `p`  | `PATH` 環境変数を使用して、実行するファイルを検索します。  |
| `v`  | コマンド ライン引数へのポインター配列 `argv` が `_spawn` 関数に渡されます。 このサフィックスは、通常は、新しいプロセスに渡すパラメーターの個数が可変の場合に使用します。  |

## <a name="remarks"></a>コメント

`_spawn` 関数はそれぞれ新しいプロセスを作成して実行します。 それらの関数は、現在使用中のマルチバイト コード ページに従ってマルチバイト文字シーケンスを認識し、マルチバイト文字列の引数を適切な方法で自動的に処理します。 `_wspawn` 関数は、`_spawn` 関数のワイド文字バージョンで、マルチバイト文字の文字列を処理しません。 それ以外の点では、`_wspawn` 関数は対応する `_spawn` 関数と同じように動作します。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tspawnl`|`_spawnl`|`_spawnl`|`_wspawnl`|
|`_tspawnle`|`_spawnle`|`_spawnle`|`_wspawnle`|
|`_tspawnlp`|`_spawnlp`|`_spawnlp`|`_wspawnlp`|
|`_tspawnlpe`|`_spawnlpe`|`_spawnlpe`|`_wspawnlpe`|
|`_tspawnv`|`_spawnv`|`_spawnv`|`_wspawnv`|
|`_tspawnve`|`_spawnve`|`_spawnve`|`_wspawnve`|
|`_tspawnvp`|`_spawnvp`|`_spawnvp`|`_wspawnvp`|
|`_tspawnvpe`|`_spawnvpe`|`_spawnvpe`|`_wspawnvpe`|

新しいプロセスを読み込んで実行するには、十分なメモリが必要です。 `mode` 引数は、`_spawn` の前とその実行中に、呼び出しプロセスによって実行されるアクションを決定します。 次の `mode` の値は、Process.h で定義されます。

|||
|-|-|
| `_P_OVERLAY`  | 新しいプロセスで呼び出しプロセスをオーバーレイし、呼び出しプロセスを破棄します (`_exec` 呼び出しと同じ影響)。  |
| `_P_WAIT`  | 新しいプロセスの実行が完了するまで、呼び出しスレッドが中断されます (同期 `_spawn`)。  |
| `_P_NOWAIT` または `_P_NOWAITO`  | 新しいプロセスと同時に呼び出しプロセスを実行し続けます (非同期 `_spawn`)。  |
| `_P_DETACH`  | 呼び出しプロセスを実行し続けます。新しいプロセスは、コンソールまたはキーボードへのアクセスなしでバックグラウンドで実行されます。 新しいプロセスに対して `_cwait` を呼び出すと失敗します (非同期 `_spawn`)。  |

`cmdname` 引数は、新しいプロセスとして実行されるファイルを指定し、完全パス (ルートから)、部分パス (現在の作業ディレクトリから)、またはファイル名のみを指定できます。 `cmdname` にファイル名拡張子がない、またはピリオド (.) で終わらない場合、`_spawn` 関数は .com ファイル名拡張子、.exe ファイル名拡張子、.bat ファイル名拡張子、.cmd ファイル名拡張子の順に試行します。

`cmdname` にファイル名拡張子がある場合は、その拡張子だけが使用されます。 `cmdname` の末尾にピリオドがある場合、`_spawn` 呼び出しはファイル名拡張子がない `cmdname` を検索します。 `_spawnlp` 関数、`_spawnlpe` 関数、`_spawnvp` 関数、`_spawnvpe` 関数は、`PATH` 環境変数に指定されたディレクトリ内で同じ処理手順を使用して `cmdname` を検索します。

`cmdname` にドライブ指定子やスラッシュが含まれている場合、つまり相対パスが指定されている場合、`_spawn` 呼び出しは指定のファイルだけを検索し、パスは検索しません。

以前は、成功時にこれらのいくつかの関数が `errno` を 0 に設定しましたが、現在の動作は、C 標準で指定されているとおり、成功時に `errno` をそのままにします。 以前の動作をエミュレートする必要がある場合は、これらの関数を呼び出す直前に `errno` を 0 に設定します。

> [!NOTE]
>  オーバーレイの初期化と終了が正しく行われるようにするため、オーバーレイ ルーチンを出入りするのに `setjmp` または `longjmp` 関数を使用しないでください。

## <a name="arguments-for-the-spawned-process"></a>生成されたプロセスの引数

新しいプロセスに引数を渡すには、文字列への 1 つ以上のポインターを `_spawn` 呼び出しの引数として指定します。 これらの文字列が生成されたプロセスの引数リストとなります。 新しいプロセスの引数リストを形成する文字列を合わせた長さは 1024 バイト以下でなければなりません。 各文字列の終端を表す NULL 文字 ('\0') はカウントされませんが、引数を区切るために自動的に挿入されるスペース文字はカウントされます。

> [!NOTE]
>  文字列に空白が含まれる場合、予期しない動作になることがあります。たとえば、`_spawn` を `"hi there"` という文字列に渡すと、新しいプロセスは `"hi"` と `"there"` という 2 つの引数を使用する結果になります。 新しいプロセスでは "hi there" というファイルを開こうとするため、プロセスは失敗します。 この問題を回避するには、`"\"hi there\""` のように文字列を引用符で囲みます。

> [!IMPORTANT]
>  ユーザー入力のコンテンツを明示的にチェックしないまま `_spawn` に渡さないでください。 `_spawn` によって [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) が呼び出されます。そのため、パス名が修飾されていない場合、セキュリティ上の脆弱性につながる可能性があります。

`_spawnl`、`_spawnle`、`_spawnlp`、`_spawnlpe` では引数へのポインターが個別の引数として渡され、`_spawnv`、`_spawnve`、`_spawnvp`、`_spawnvpe` ではポインターの配列として渡されます。 少なくとも 1 つの引数 (`arg0` または `argv`[0]) を生成されたプロセスに渡す必要があります。 規則上、この引数は、コマンド ラインの場合に入力するはずのプログラムの名前です。 ただし、別の値を使用しても、エラーは発生しません。

`_spawnl`、`_spawnle`、`_spawnlp`、`_spawnlpe` の各呼び出しは、通常、引数の個数が事前にわかっている場合に使用します。 `arg0` 引数は通常、`cmdname` へのポインターです。 引数 `arg1` ～ `argn` は、新しい引数リストを構成する文字列へのポインターです。 `argn`の後には、引数リストの末尾を示すために **NULL** ポインターが必要です。

`_spawnv`、`_spawnve`、`_spawnvp`、`_spawnvpe` の各呼び出しは、新しいプロセスの引数の数が変化する場合に便利です。 引数へのポインターは、配列 `argv` *として渡されます。* `argv`[0] 引数は、通常、リアル モードのパスまたは保護モードのプログラム名へのポインターです。 `argv`[1] 引数～ `argv`[`n`] 引数は、新しい引数リストを形成する文字列へのポインターです。 引数リストの末尾を示すために、 `argv`[`n` +1] 引数は **NULL** ポインターである必要があります。

## <a name="environment-of-the-spawned-process"></a>生成されたプロセスの環境

`_spawn` 呼び出しを作成するときに開いたファイルは、新しいプロセスでも開いたままです。 `_spawnl`、`_spawnlp`、`_spawnv`、`_spawnvp` の各呼び出しでは、新しいプロセスが呼び出しプロセスの環境を継承します。 `envp` 引数を使用して環境設定のリストを渡すことで、`_spawnle`、`_spawnlpe`、`_spawnve`、`_spawnvpe` の各呼び出しを使用して、新しいプロセスの環境を変更できます。 引数 `envp` は文字ポインターの配列であり、最後の要素以外の各要素は、環境変数を定義する null で終わる文字列を指します。 通常、このような文字列の形式は `NAME`=`value` であり、`NAME` は環境変数名、`value` はその変数に設定する文字列の値です。 (`value` は二重引用符で囲まれていないことに注意してください)。`envp` 配列の最後の要素は**NULL**にする必要があります。 `envp` 自身が **NULL** である場合、生成されたプロセスは親プロセスの環境設定を継承します。

`_spawn` 関数は、開いているファイルに関するすべての情報 (変換モードを含む) を新しいプロセスに渡すことができます。 この情報は環境内の `C_FILE_INFO` エントリを通してリアル モードで渡されます。 通常、スタートアップ コードはこのエントリを処理してから、環境から削除します。 ただし、`_spawn` 関数によって C 以外のプロセスが生成される場合、このエントリは環境内に残されます。 環境を印刷すると、環境情報がバイナリ形式でリアル モードで渡されているため、このエントリの定義文字列にグラフィック文字が示されます。 これ以外の影響が通常の操作に及ぶことはありません。 保護モードでは、環境情報はテキスト形式で渡されるため、グラフィック文字は含まれません。

`_spawn` 系関数を呼び出す前に、`fflush` または `_flushall` を使用してストリームを明示的にフラッシュするか、ストリームを閉じる必要があります。

`_spawn` ルーチンの呼び出しによって作成された新しいプロセスでは、シグナル設定が保持されません。 代わりに、生成されたプロセスでは、シグナル設定が既定値にリセットされます。

## <a name="redirecting-output"></a>出力のリダイレクト

`_spawn` を DLL または GUI アプリケーションから呼び出して、出力をパイプにリダイレクトするには、次の 2 つのオプションがあります。

- Win32 API を使用してパイプを作成し、[AllocConsole](/windows/console/allocconsole) を呼び出し、ハンドル値をスタートアップ構造体に設定し、[CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) を呼び出します。

- [_popen、_wpopen](../c-runtime-library/reference/popen-wpopen.md) を呼び出してパイプを作成し、**cmd.exe /c** (または **command.exe /c**) を使用してアプリを呼び出します。

## <a name="example"></a>使用例

```c
// crt_spawn.c
// This program accepts a number in the range
// 1-8 from the command line. Based on the number it receives,
// it executes one of the eight different procedures that
// spawn the process named child. For some of these procedures,
// the CHILD.EXE file must be in the same directory; for
// others, it only has to be in the same path.
//

#include <stdio.h>
#include <process.h>

char *my_env[] =
{
   "THIS=environment will be",
   "PASSED=to child.exe by the",
   "_SPAWNLE=and",
   "_SPAWNLPE=and",
   "_SPAWNVE=and",
   "_SPAWNVPE=functions",
   NULL
};

int main( int argc, char *argv[] )
{
   char *args[4];

   // Set up parameters to be sent:
   args[0] = "child";
   args[1] = "spawn??";
   args[2] = "two";
   args[3] = NULL;

   if (argc <= 2)
   {
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );
      exit( 1 );
   }

   switch (argv[1][0])   // Based on first letter of argument
   {
   case '1':
      _spawnl( _P_WAIT, argv[2], argv[2], "_spawnl", "two", NULL );
      break;
   case '2':
      _spawnle( _P_WAIT, argv[2], argv[2], "_spawnle", "two",
               NULL, my_env );
      break;
   case '3':
      _spawnlp( _P_WAIT, argv[2], argv[2], "_spawnlp", "two", NULL );
      break;
   case '4':
      _spawnlpe( _P_WAIT, argv[2], argv[2], "_spawnlpe", "two",
                NULL, my_env );
      break;
   case '5':
      _spawnv( _P_OVERLAY, argv[2], args );
      break;
   case '6':
      _spawnve( _P_OVERLAY, argv[2], args, my_env );
      break;
   case '7':
      _spawnvp( _P_OVERLAY, argv[2], args );
      break;
   case '8':
      _spawnvpe( _P_OVERLAY, argv[2], args, my_env );
      break;
   default:
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );
      exit( 1 );
   }
   printf( "from SPAWN!\n" );
}
```

```Output
child process output
from SPAWN!
```

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../c-runtime-library/process-and-environment-control.md)<br/>
[abort](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[_exec、_wexec 系関数](../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_flushall](../c-runtime-library/reference/flushall.md)<br/>
[_getmbcp](../c-runtime-library/reference/getmbcp.md)<br/>
[_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_setmbcp](../c-runtime-library/reference/setmbcp.md)<br/>
[system、_wsystem](../c-runtime-library/reference/system-wsystem.md)
