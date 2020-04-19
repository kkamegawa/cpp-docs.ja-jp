---
title: メイクファイルのプリプロセス ディレクティブ
ms.date: 08/11/2019
f1_keywords:
- '!UNDEF'
- '!INCLUDE'
- '!IFNDEF'
- '!MESSAGE'
helpviewer_keywords:
- ERROR directive
- '!MESSAGE directive'
- IF directive
- '!UNDEF directive'
- IFDEF directive
- '!ELSEIF directive'
- '!IFDEF directive'
- '!IF directive'
- UNDEF directive
- '!CMDSWITCHES directive'
- ENDIF directive
- directives, makefile preprocessing
- INCLUDE directive
- IFNDEF directive
- preprocessing directives, makefiles
- '!IFNDEF directive'
- ELSEIFNDEF directive
- NMAKE program, expressions
- ELSEIF directive
- '!ERROR directive'
- '!ENDIF directive'
- MESSAGE directive
- '!INCLUDE directive'
- '!ELSEIFNDEF directive'
- CMDSWITCHES directive
- '!ELSEIFDEF directive'
- '!ELSE directive'
- NMAKE program, preprocessor directives
- makefiles, preprocessing directives
- ELSE directive
- ELSEIFDEF directive
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
ms.openlocfilehash: 4825ca180cb1b419a9ffa5232575ba1a24f8805d
ms.sourcegitcommit: db1ed91fa7451ade91c3fb76bc7a2b857f8a5eef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68980509"
---
# <a name="makefile-preprocessing-directives"></a>メイクファイルのプリプロセス ディレクティブ

プリプロセスディレクティブでは、大文字と小文字は区別されません。 最初の感嘆符 (!) は、行の先頭に置く必要があります。 インデントの場合は、感嘆符の後に0個以上の空白またはタブを表示できます。

- `!CMDSWITCHES`{`+` &#124; } オプション... `-`

   各*オプション*をオンまたはオフにします。 スペースまたはタブは、また`+`は`-`演算子の前に指定する必要があります。演算子と[オプションの文字](running-nmake.md#nmake-options)の間には使用できません。 文字は大文字と小文字が区別されず`/`、スラッシュ () なしで指定されます。 一部のオプションを有効にし、他のオプションを無効に`!CMDSWITCHES`するには、の個別の仕様を使用します。

   メイクファイルで使用できるのは、/D、/I、/N、および/S だけです。 ツール .ini では、/F、/HELP、/NOLOGO、/X、/? 以外のすべてのオプションを使用できます。 Description ブロックで指定された変更は、次の説明ブロックまで有効になりません。 このディレクティブは、 **Makeflags**を更新します。**Makeflags**が指定されている場合、再帰中に変更が継承されます。

- `!ERROR`*テキスト*

   エラー U1050 に*テキスト*を表示し、/k、/i、 `.IGNORE`、 `!CMDSWITCHES`、またはダッシュ (`-`) のコマンド修飾子が使用されている場合でも、NMAKE を停止します。 *テキスト*の前のスペースまたはタブは無視されます。

- `!MESSAGE`*テキスト*

   *テキスト*を標準出力に表示します。 *テキスト*の前のスペースまたはタブは無視されます。

- `!INCLUDE`[ `<` ]*ファイル名*[ `>` ]

   *ファイル名*をメイクファイルとして読み取り、現在のメイクファイルで続行します。 NMAKE は、指定したディレクトリまたは現在のディレクトリで*ファイル名*を検索し、親メイク*ファイル*のディレクトリを再帰的に検索します`< >`。次に、filename が山かっこ ()**で囲まれている場合は、INCLUDE**マクロ。最初は include 環境変数に設定されています。 設定、 `.SUFFIXES` `.PRECIOUS`、および推論規則を再帰的なメイクメイクに渡す場合に便利です。

- `!IF`*constant_expression*

   と`!IF` の間`!ENDIF`のステートメントを処理します。または、constant_expressionが0以外の値に評価される場合はを処理し`!ELSE`ます。

- `!IFDEF`*macroname*

   `!IFDEF`と次`!ELSE`の間のステートメントを`!ENDIF`処理します。また、 *macroname*が定義されている場合はを処理します。 Null マクロは定義されていると見なされます。

- `!IFNDEF`*macroname*

   と`!IFNDEF` の間`!ENDIF`のステートメントを処理します。また、macronameが定義されていない場合はを処理し`!ELSE`ます。

- `!ELSE`[`IF` &#124; *constant_expression* &#124; *macroname*マクロ名] `IFDEF` `IFNDEF`

   `!ELSE` `!ENDIF`前の、`!IFDEF`、または`!IFNDEF`ステートメントが0に評価された場合、との間のステートメントを処理します。 `!IF` 省略可能なキーワードを使うと、前処理をさらに制御できます。

- `!ELSEIF`

   `!ELSE IF` と同義。

- `!ELSEIFDEF`

   `!ELSE IFDEF` と同義。

- `!ELSEIFNDEF`

   `!ELSE IFNDEF` と同義。

- `!ENDIF`

   `!IF` 、`!IFDEF`、または`!IFNDEF`ブロックの末尾をマークします。 同じ行の`!ENDIF`後のテキストは無視されます。

- `!UNDEF`*macroname*

   *Macroname*を未定義にします。

## <a name="see-also"></a>関連項目

- [メイクファイルのプリプロセス](makefile-preprocessing.md)