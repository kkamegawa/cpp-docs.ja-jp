---
title: scanf 関数と wscanf 関数の書式指定フィールド
ms.date: 11/04/2016
api_location:
- msvcr80.dll
- msvcr110.dll
- msvcr90.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wscanf
- scanf
helpviewer_keywords:
- width, specifications in scanf function
- scanf format specifications
- scanf width specifications
- scanf type field characters
- type fields, scanf function
- format specification fields for scanf function
- type fields
ms.assetid: 7e95de1b-0b71-4de3-9f81-c9560c78e039
ms.openlocfilehash: 78b64ea29aebdfb355525be69dc7a9fdece55367
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944413"
---
# <a name="format-specification-fields-scanf-and-wscanf-functions"></a>scanf 関数と wscanf 関数の書式指定フィールド

ここにある情報は、セキュリティが強化されたバージョンを含む `scanf` 系の関数すべてに当てはまり、`scanf` に対する `stdin` などの入力ストリームを解析してプログラム変数に挿入する値に変換する方法を `scanf` 関数に指示するために使用するシンボルについても説明します。

書式指定は、次の形式で行います。

`%`[`*`] [[幅](../c-runtime-library/scanf-width-specification.md)] [{[h &#124; l &#124; ll &#124; I64 &#124; L](../c-runtime-library/scanf-width-specification.md)}][型](../c-runtime-library/scanf-type-field-characters.md)

`format` 引数では入力の解釈方法を指定します。次の文字を 1 つ以上指定できます。

- 空白文字: 空白 (' ')、タブ ('\t')、または改行 ('\n')。 空白文字が現れると、`scanf` は、次の非空白文字が現れるまで、入力データ内の連続するすべての空白文字を読み取ります。ただし、読み取るだけで格納しません。 書式に指定された 1 つの空白文字は、入力データ内の任意の個数 (0 を含む) の空白文字および任意の組み合わせの空白文字と一致します。

- パーセント記号 (`%`) 以外の非空白文字。 非空白文字が現れると、`scanf` 関数は、一致する非空白文字を読み取ります。ただし、読み取るだけで格納しません。 入力ストリーム中の次の文字が一致しないと、`scanf` 関数は終了します。

- パーセント記号 (`%`) に続く書式指定。 書式指定がある場合、`scanf` 関数は、入力データ中の文字を読み取り、指定されている型の値に変換します。 変換後の値は、引数リスト内の引数に代入されます。

書式は左から右へ読み取られます。 書式指定以外の文字は、入力ストリーム内の一連の文字列に一致するものと想定されます。これらの文字は入力ストリーム内でスキャンされますが格納はされません。 入力ストリーム内の文字が書式指定に合わないと、`scanf` 関数は終了し、その文字は読み取られなかったものとして入力ストリームに残ります。

最初の書式指定が見つかると、最初の入力フィールドの値がこの指定に従って変換され、最初の `argument` で指定された位置に格納されます。 2 番目の書式指定が見つかると、2 番目の入力フィールドが変換され、2 番目の `argument` に格納されます。この手順は、書式指定文字列が終わるまで続きます。

入力フィールドは、最初の空白文字 (空白、タブ、または改行) までのすべての文字、書式指定に従って変換できない最初の文字までのすべての文字、またはフィールド幅 (指定されている場合) に到達するまでのすべての文字として定義されます。 書式指定に対して引数が多すぎる場合、余分な引数は評価されるだけで無視されます。 書式指定に必要な引数が足りない場合、結果は予測できません。

各書式指定フィールドには、特定の書式を表す 1 つの文字または数字を指定します。 `type` 文字は省略可能な最後の書式フィールドの次に指定し、入力フィールドを文字、文字列、または数値のうちいずれとして解釈するかを決定します。

最も簡単な書式指定は、パーセント記号と `type` 文字だけ (`%s` など) で行います。 パーセント記号 (`%`) の後に書式指定文字として意味がない文字が続くと、その文字と以降の文字は、次のパーセント記号が現れるまで、普通の文字列、つまり入力に一致しなければならない一連の文字列として処理されます。 パーセント記号を入力文字として処理するには、`%%` と指定します。

パーセント記号の後にアスタリスク (`*`) を指定すると、次の入力フィールドは指定されている型のフィールドとして解釈されますが、引数には代入されません。 このフィールドはスキャンされるだけで、値は格納されません。

`_s` 系の関数で `scanf` サフィックスが付いているセキュリティが強化されたバージョンでは、型が `c`、`C`、`s`、`S`、または `[` であるすべてのパラメーターに続けてバッファー サイズのパラメーターを渡す必要があります。 `scanf` 系の関数のセキュリティが強化されたバージョンの詳細については、「[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)」を参照してください。

## <a name="see-also"></a>関連項目

[scanf 関数の文字幅指定](../c-runtime-library/scanf-width-specification.md)<br/>
[scanf 関数の型フィールド文字](../c-runtime-library/scanf-type-field-characters.md)<br/>
[scanf、_scanf_l、wscanf、_wscanf_l](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)<br/>
[scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)
