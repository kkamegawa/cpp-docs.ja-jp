---
title: main 関数とコマンドライン引数 (C++)
description: main 関数は、 C++プログラムのエントリポイントです。
ms.date: 01/15/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
no-loc:
- main
- wmain
- inline
- static
- _tmain
- void
- exit
- argc
- argv
- envp
- CreateProcess
- GetModuleFileName
- char
- wchar_t
- extern
ms.openlocfilehash: 33753e30304a9bb63c135979d3f20098e6b6401a
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123904"
---
# <a name="opno-locmain-function-and-command-line-arguments"></a>main 関数とコマンドライン引数

すべてC++のプログラムには `main` 機能が必要です。 main 関数を使用せずC++に *.exe*プロジェクトをコンパイルしようとすると、コンパイラによってエラーが発生します。 (ダイナミックリンクライブラリと static ライブラリには、`main` の機能はありません)。`main` 関数は、ソースコードの実行を開始しますが、プログラムが `main` 関数に入る前に、明示的な初期化子を持たないすべての static クラスメンバーを0に設定します。 Microsoft C++では、グローバル static オブジェクトも `main`に入る前に初期化されます。 `main` 関数には、他の関数には適用されないC++いくつかの制限が適用されます。 `main` 関数:

- オーバーロードできません (「[関数のオーバーロード](function-overloading.md)」を参照してください)。
- を **inline** として宣言することはできません。
- を **static** として宣言することはできません。
- そのアドレスを取得することはできません。
- 呼び出すことはできません。

main 関数は、言語に組み込まれているため、宣言を持ちません。 これが行われた場合、`main` の宣言構文は次のようになります。

```cpp
int main();
int main(int argc, char *argv[], char *envp[]);
```

**Microsoft 固有の仕様**

ソースファイルで Unicode ワイド文字が使用されている場合は、`main`のワイド文字バージョンである `wmain`を使用できます。 `wmain` の宣言構文は次のとおりです。

```cpp
int wmain( );
int wmain(int argc, wchar_t *argv[], wchar_t *envp[]);
```

また、tchar.h で定義されている `_tmain`を使用することもできます。 `_tmain` は、_UNICODE が定義されていない限り、`main` に解決されます。 定義されている場合、`_tmain` は `wmain` に解決されます。

戻り値が指定されていない場合、コンパイラは戻り値として0を指定します。 または、`main` 関数と `wmain` 関数を、 **void** を返すように宣言できます (戻り値はありません)。 **void** を返すように `main` または `wmain` を宣言する場合、 [return](../cpp/return-statement-in-program-termination-cpp.md)ステートメントを使用して、親プロセスまたはオペレーティングシステムに exit コードを返すことはできません。 `main` または `wmain` が **void** として宣言されている場合に exit コードを返すには、 [exit](../cpp/exit-function.md)関数を使用する必要があります。

**END Microsoft 固有の仕様**

## <a name="command-line-arguments"></a>コマンド ライン引数

`main` または `wmain` の引数を使用すると、コマンドラインで引数を簡単に解析できるだけでは、必要に応じて環境変数にアクセスできます。 `argc` と `argv` の型は、言語によって定義されています。 `argc`、`argv`、`envp` は従来の名前ですが、好きな名前を付けることができます。

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

引数の定義は、次のとおりです。

*argc*<br/>
*argv* で後に続く引数の数を含む整数。 *argc* パラメーターは常に1以上です。

*argv*<br/>
プログラムのユーザーが入力したコマンド ライン引数を表す、null で終了する文字列配列。 慣例により、`argv[0]` はプログラムの呼び出しに使用するコマンド、`argv[1]` は最初のコマンドライン引数、`argv[argc]`までは常に NULL になります。 コマンドライン処理の抑制については、「[コマンドライン処理のカスタマイズ](../cpp/customizing-cpp-command-line-processing.md)」を参照してください。

最初のコマンド ライン引数は、必ず `argv[1]` となり、最後のコマンド ライン引数は、`argv[argc - 1]` になります。

> [!NOTE]
> 慣例により、`argv[0]` はプログラムが呼び出されるコマンドです。 ただし、 [CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)を使用してプロセスを生成することができます。1番目と2番目の引数 (*Lpapplicationname*と*lpapplicationname*) の両方を使用すると、`argv[0]` は実行可能ファイル名ではない可能性があります。[GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)を使用して、実行可能ファイル名とその完全修飾パスを取得します。

**Microsoft 固有の仕様**

*envp*<br/>
*envp* 配列は、多くの UNIX システムで共通の拡張機能であり、Microsoft C++で使用されています。 これは、ユーザーの環境で設定された変数を表す文字列の配列です。 この配列は NULL エントリで終了します。 これは、 **char** (`char *envp[]`) へのポインターの配列として、または **char** (`char **envp`) へのポインターへのポインターとして宣言できます。 プログラムで `main`ではなく `wmain` を使用する場合は、 **char** ではなく **wchar_t** データ型を使用します。 `main` に渡される環境ブロックと `wmain` は、現在の環境の "固定" コピーです。 後で `putenv` または `_wputenv`の呼び出しを使用して環境を変更した場合、(`getenv` または `_wgetenv` によって返された) 現在の環境、および `_environ` または `_wenviron` 変数) は変更されますが、envp が指すブロックは変更されません。 環境処理の抑制については、「[コマンドライン処理のカスタマイズ](../cpp/customizing-cpp-command-line-processing.md)」を参照してください。 この引数は、C では ANSI 互換ですが、C++ では非互換です。

**END Microsoft 固有の仕様**

### <a name="example"></a>使用例

次の例は、 *argc* 、 *argv* 、および *envp* 引数を使用して `main`する方法を示しています。

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int main( int argc, char *argv[], char *envp[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; envp[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << envp[i] << "\n";
    }
}
```

## <a name="parsing-c-command-line-arguments"></a>コマンドC++ライン引数の解析

**Microsoft 固有の仕様**

Microsoft C/C++ 起動コードは、オペレーティング システムのコマンド ラインで指定された引数を解釈する場合に、次の規則を使用します。

- 引数は、空白 (スペースまたはタブ) で区切ります。

- キャレット (^) は、エスケープ文字やデリミターとしては認識されません。 文字は、プログラムの `argv` 配列に渡される前に、オペレーティング システムのコマンド ライン パーサーによって完全に処理されます。

- 二重引用符で囲まれた文字列 ("*string*") は、内に空白が含まれていなくても、単一の引数として解釈されます。 二重引用符で囲んだ文字列を引数に埋め込むこともできます。

- 円記号を前に付けた二重引用符 (\\") は、リテラル二重引用符文字 (") として解釈されます。

- 二重引用符の直前にある円記号以外は、円記号 (\) として解釈されます。

- 二重引用符の直前に円記号が偶数個あると、円記号のペアごとに 1 個の円記号が `argv` 配列に配置されます。この場合、二重引用符は文字列の区切り記号として解釈されます。

- 二重引用符の直前に円記号が奇数個あると、円記号のペアごとに 1 個の円記号が `argv` 配列に配置されます。この場合、二重引用符は残った円記号によってエスケープされます。これにより、リテラル二重引用符 (") が `argv` に配置されます。

### <a name="example"></a>使用例

次のプログラムは、コマンド ライン引数がどのように受け渡されるかを示します。

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int main( int argc,      // Number of strings in array argv
          char *argv[],   // Array of command-line argument strings
          char *envp[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < argc; count++ )
         cout << "  argv[" << count << "]   "
                << argv[count] << "\n";
}
```

次の表は、前の一覧の規則を示しながら、入力例と予想される出力を示しています。

### <a name="results-of-parsing-command-lines"></a>コマンドラインの解析結果

|コマンド ライン入力|argv[1]|argv[2]|argv[3]|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**END Microsoft 固有の仕様**

## <a name="wildcard-expansion"></a>ワイルドカードの展開

**Microsoft 固有の仕様**

コマンド ラインでファイル名とパスの引数を指定するときに、ワイルドカード (疑問符 (?) およびアスタリスク (*)) を使用できます。

コマンドライン引数は `_setargv` (ワイド文字環境では `_wsetargv`) と呼ばれるルーチンによって処理されます。既定では、ワイルドカードは `argv` 文字列配列内の個別の文字列に展開されません。 ワイルドカードの展開を有効にする方法の詳細については、「[ワイルドカード引数の展開](../c-language/expanding-wildcard-arguments.md)」を参照してください。

**END Microsoft 固有の仕様**

## <a name="customizing-c-command-line-processing"></a>C++ のコマンド ライン処理のカスタマイズ

**Microsoft 固有の仕様**

プログラムがコマンド ラインの引数を受け取らない場合は、コマンド ライン処理を実行するライブラリ ルーチンの使用を制約することで、領域を節約できます。 このルーチンは `_setargv` と呼ばれ、[ワイルドカードの展開](../cpp/wildcard-expansion.md)で説明されています。 使用しないようにするには、`main` 関数を含むファイルで何も実行しないルーチンを定義し、`_setargv`という名前を指定します。 `_setargv`の定義によって `_setargv` の呼び出しが満たされ、ライブラリのバージョンが読み込まれません。

同様に、`envp` 引数を使用して環境テーブルにアクセスしない場合は、環境処理ルーチン `_setenvp`の代わりに独自の空のルーチンを使用することができます。 `_setargv` 関数と同様に、`_setenvp` は **extern "C"** として宣言する必要があります。

プログラムによって、C ランタイムライブラリで `spawn` または `exec` のルーチンファミリが呼び出される場合があります。 存在する場合は、環境処理ルーチンを抑制しないでください。このルーチンは、親プロセスから子プロセスに環境を渡すために使用されるためです。

**END Microsoft 固有の仕様**

## <a name="see-also"></a>関連項目

[基本的な概念](../cpp/basic-concepts-cpp.md)
