---
title: C コメント
ms.date: 06/25/2018
helpviewer_keywords:
- code comments, C code
- comments, documenting code
- comments, C code
- /* */ comment delimiters
- comments
ms.assetid: 0f5f2825-e673-49e7-8669-94e2f5294989
ms.openlocfilehash: fd2c08855bcc3ef3b4068f3841ce177d8162ff5b
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152730"
---
# <a name="c-comments"></a>C コメント

"コメント" は、コンパイラによって 1 個の空白文字として扱われる、スラッシュとアスタリスクの組み合わせ (<strong>/\*</strong>) で始まる文字シーケンスです。それ以外の場合は無視されます。 コメントには、"コメント終了" 区切り記号 (<strong>\*/</strong>) を除いて、改行文字も含む、表現できる文字セットの文字の任意の組み合わせを含めることができます。 コメントは複数行にわたって記述できますが、入れ子にすることはできません。

コメントは、空白文字を使用できる任意の場所に記述することができます。 コンパイラはコメントを 1 個の空白文字として扱うため、コメントをトークン内に含めることはできません。 コンパイラは、コメント内の文字を無視します。

コメントを使用してコードの内容を文章で説明します。 次の例は、コンパイラに許容されるコメントです。

```C
/* Comments can contain keywords such as
   for and while without generating errors. */
```

コメントは、コード ステートメントと同じ行に記述することができます。

```C
printf( "Hello\n" );  /* Comments can go here */
```

関数またはプログラム モジュールの前に説明的なコメント ブロックを配置できます。

```C
/* MATHERR.C illustrates writing an error routine
* for math functions.
*/
```

コメントには入れ子になったコメントを含めることができないため、この例ではエラーが発生します。

```C
/* Comment out this routine for testing

   /* Open file */
    fh = _open( "myfile.c", _O_RDONLY );
    .
    .
    .
*/
```

エラーは、コンパイラが、`*/` という語の後の最初の `Open file` をコメントの終わりとして認識したために発生しました。 残りのテキストを処理しようとして、注釈の外部に `*/` が見つかった時点でエラーが生成されます。

テスト目的でコメントを使用して特定のコード行を無効にすることができますが、プリプロセッサ ディレクティブの `#if` および `#endif` と条件付きコンパイルを利用して同じことを実行することもできます。 詳細については、「*プリプロセッサ リファレンス*」の「[プリプロセッサ ディレクティブ](../preprocessor/preprocessor-directives.md)」を参照してください。

**Microsoft 固有の仕様**

Microsoft コンパイラは、2 つのスラッシュ (__//__) で始まる 1 行コメントもサポートします。 /Za (ANSI 規格) を使用してコンパイルすると、このコメントでエラーが発生します。 このコメントは次の行に続けることはできません。

```C
// This is a valid comment
```

2 つのスラッシュ (__//__) で始まるコメントは、エスケープ文字が前に付いていない次の改行文字で終了します。 次の例では、改行文字の前にバックスラッシュ (**\\**) が付いて、"エスケープ シーケンス" が作成されています。 このエスケープ シーケンスによって、コンパイラは次の行を前の行の一部として処理します  (詳細については、「[エスケープ シーケンス](../c-language/escape-sequences.md)」を参照してください)。

```C
// my comment \
    i++;
```

したがって、`i++;` ステートメントはコメント アウトされます。

Microsoft C の既定では、Microsoft 拡張機能が有効になっています。 これらの拡張機能を無効にするには、/Za を使用します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[C トークン](../c-language/c-tokens.md)
