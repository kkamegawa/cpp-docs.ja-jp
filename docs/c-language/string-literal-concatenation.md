---
title: 文字列リテラルの連結
ms.date: 11/04/2016
helpviewer_keywords:
- concatenating strings
- strings [C++], concatenating
ms.assetid: 51486b1f-4b1e-4061-9add-1aa38c6cdb3c
ms.openlocfilehash: cdd9a7811635bf43cd76ecbc84d8ab364e7f9dab
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152574"
---
# <a name="string-literal-concatenation"></a>文字列リテラルの連結

複数の行にわたる文字列リテラルを作成するときには、2 つの文字列を連結できます。 これには、円記号を入力してから Enter キーを押します。 円記号を入力すると、コンパイラは後続の改行文字を無視します。 たとえば、次の文字列リテラル

```
"Long strings can be bro\
ken into two or more pieces."
```

は、次の文字列と同じです。

```
"Long strings can be broken into two or more pieces."
```

文字列の連結は、円記号に続けて改行文字を使用することでどこでも使用でき、これによって 1 行より長い文字列を入力できます。

文字列リテラル内で改行を強制するには、文字列内の改行位置で、改行エスケープ シーケンス (**\n**) を次のように入力します。

```
"Enter a number between 1 and 100\nOr press Return"
```

文字列は、ソース コード内の任意の列から開始でき、長い文字列は次の行の任意の列で続行できるため、ソース コードが読みやすくなるように文字列を配置できます。 どのようにした場合も、出力時の画面上の表現は影響を受けません。 次に例を示します。

```
printf_s ( "This is the first half of the string, "
           "this is the second half ") ;
```

文字列の各部分が二重引用符で囲まれている限り、それらの部分は連結され、1 つの文字列として出力されます。 この連結は、[翻訳の各フェーズ](../preprocessor/phases-of-translation.md)により指定されたコンパイル中のイベントのシーケンスに従って発生します。

```
"This is the first half of the string, this is the second half"
```

空白のみで区切られた 2 つの文字列リテラルとして初期化された文字列ポインターは、1 つの文字列として格納されます (ポインターについては、「[ポインター宣言](../c-language/pointer-declarations.md)」で説明します)。 次の例のように適切に参照すると、結果は前の例と同じになります。

```
char *string = "This is the first half of the string, "
               "this is the second half";

printf_s( "%s" , string ) ;
```

隣接する文字列リテラルまたは隣接するワイド文字列リテラルの任意のシーケンスで指定されたマルチバイト文字シーケンスは、変換フェーズ 6 で連結され、単一のマルチバイト文字シーケンスになります。 したがって、実行時に文字列リテラルの変更を許可するようにプログラムをデザインしないでください。 ANSI C 規格では、文字列の変更結果は未定義であると規定されています。

## <a name="see-also"></a>関連項目

[C 文字列リテラル](../c-language/c-string-literals.md)
