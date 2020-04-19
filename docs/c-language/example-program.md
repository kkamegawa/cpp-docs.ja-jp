---
title: サンプル プログラム
ms.date: 11/04/2016
ms.assetid: fc22ef82-9caa-425f-b201-2891bc123d1f
ms.openlocfilehash: fc00ee391fd845039791b8cec727623074a7aeff
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147127"
---
# <a name="example-program"></a>サンプル プログラム

次の C ソース プログラムは 2 つのソース ファイルで構成されています。 C プログラムで使用できるさまざまな宣言と定義の一部について、概要を示します。 後のセクションでは、これらの宣言、定義、および初期化を記述する方法と、**static** や `extern` のような C のキーワードを使用する方法について説明します。 `printf` 関数は C ヘッダー ファイル STDIO.H. で宣言されます。

`main` 関数と `max` 関数は、別のファイルにあると解釈され、プログラムの実行は `main` 関数で始まります。 明示的なユーザー関数は `main` の前には実行されません。

```
/*****************************************************************
                    FILE1.C - main function
*****************************************************************/

#define ONE     1
#define TWO     2
#define THREE   3
#include <stdio.h>

int a = 1;                       // Defining declarations
int b = 2;                       //  of external variables

extern int max( int a, int b );  // Function prototype

int main()                       // Function definition
{                                //  for main function
    int c;                       // Definitions for
    int d;                       //  two uninitialized
                                 //  local variables

    extern int u;                // Referencing declaration
                                 //  of external variable
                                 //  defined elsewhere
    static int v;                // Definition of variable
                                 //  with continuous lifetime

    int w = ONE, x = TWO, y = THREE;
    int z = 0;

    z = max( x, y );             // Executable statements
    w = max( z, w );
    printf_s( "%d %d\n", z, w );
    return 0;
}

/****************************************************************
            FILE2.C - definition of max function
****************************************************************/

int max( int a, int b )          // Note formal parameters are
                                 //  included in function header
{
    if( a > b )
        return( a );
    else
        return( b );
}
```

FILE1.C には `max` 関数のプロトタイプが含まれます。 この種類の宣言は、関数が使用前に宣言されるため、"前方宣言" と呼ばれることがあります。 `main` 関数の定義は `max` への呼び出しを含みます。

`#define` で始まる行は、プリプロセッサ ディレクティブです。 これらのディレクティブは、識別子 `ONE`、`TWO`、および `THREE` をそれぞれ数 `1`、`2`、および `3` に FILE1.C 全体で置き換えるようにプリプロセッサに指示します。 ただし、ディレクティブは、個別にコンパイルされて FILE1.C にリンクされる FILE2.C には適用されません。 `#include` で始まる行は、`printf` 関数のプロトタイプを含む STDIO.H ファイルを含めるようにコンパイラに指示します。 [プリプロセッサ ディレクティブ](../preprocessor/preprocessor-directives.md)については、「*プリプロセッサ リファレンス*」を参照してください。

FILE1.C では、宣言の定義を使用して、グローバル変数の `a` と `b` を初期化しています。 ローカル変数の `c` と `d` が宣言されていますが、初期化されていません。 これらの変数すべてに対して、ストレージが割り当てられます。 静的変数および外部変数の `u` と `v` は自動的に 0 に初期化されます。 したがって、`a`、`b`、`u`、および `v` にのみ宣言時に意味のある値が含まれます。明示的または暗黙的に初期化されるためです。 FILE2.C には `max` 関数の定義が含まれます。 この定義は、FILE1.C の `max` への呼び出しを満たします。

識別子の有効期間と可視性については、「[有効期間、スコープ、可視性、およびリンケージ](../c-language/lifetime-scope-visibility-and-linkage.md)」で説明します。 関数の詳細については、「[関数](../c-language/functions-c.md)」を参照してください。

## <a name="see-also"></a>関連項目

[ソース ファイルとソース プログラム](../c-language/source-files-and-source-programs.md)
