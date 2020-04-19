---
title: 配列の宣言
ms.date: 11/04/2016
helpviewer_keywords:
- multidimensional arrays
- declaring arrays
- arrays [C++], declaring
ms.assetid: 5f958b97-cef0-4058-bbc6-37c460aaed9b
ms.openlocfilehash: 4bc75e86601da77758490544cc5b02c485dcee46
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147777"
---
# <a name="array-declarations"></a>配列の宣言

"配列宣言" では、配列に名前を付けて、その要素の型を指定します。 また、配列の要素数も定義できます。 配列型の変数は、配列要素の型へのポインターと見なされます。

## <a name="syntax"></a>構文

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-specifiers* *init-declarator-list*<sub>opt</sub> **;**

*init-declarator-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*init-declarator-list*  **,**  *init-declarator*

*init-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declarator* **=** *initializer*

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*: /\* 関数宣言子 \*/<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*direct-declarator*  **[**  *constant-expression*<sub>opt</sub> **]**

*constant-expression* は省略可能であるため、構文には以下の 2 つの形式があります。

- 最初の形式は、配列変数の定義です。 角かっこ内の *constant-expression* 引数には、配列内の要素数を指定します。 *constant-expression* は、存在する場合、0 より大きい整数型の値を持つ必要があります。 各要素は、*type-specifier* で指定した型になります。これには、`void` を除く任意の型を指定できます。 配列の要素を関数型にすることはできません。

- 2 番目の形式は、別の場所で定義されている変数の宣言です。 この場合、角かっこ内の *constant-expression* 引数を省略しますが、角かっこは必要です。 この形式を使用できるのは、以前に配列を初期化しているか、パラメーターとして宣言している場合、または、プログラム内の他の場所で明示的に定義された配列への参照として宣言している場合だけです。

どちらの形式でも、*direct-declarator* で変数に名前を付け、変数の型を変更できます。 *direct-declarator* の後に続く角かっこ (**[ ]**) により、宣言子が配列型に変更されます。

配列型オブジェクト宣言で型修飾子を使用できますが、修飾子は配列自体にではなく、要素に適用されます。

次の形式で、配列宣言子に続けて角かっこで囲んだ定数式のリストを指定することにより、配列の配列 ("多次元" 配列) を宣言できます。

> *type-specifier* *declarator* **[** *constant-expression* **]** **[** *constant-expression* **]** ...

角かっこ内の各 *constant-expression* によって、特定の次元の要素数が定義されます。2 次元配列には角かっこで囲まれた式が 2 つあり、3 次元配列には 3 つあります (以下、同様です)。 配列を初期化しているか、パラメーターとして宣言している場合、または、プログラム内の他の場所で明示的に定義された配列への参照として宣言している場合は、最初の定数式を省略できます。

「[Interpreting More Complex Declarators](../c-language/interpreting-more-complex-declarators.md)」 (さらに複雑な宣言子の解釈) に説明されているように、複雑な宣言を使用して、さまざまな型のオブジェクトへのポインターの配列を定義できます。

配列は行ごとに格納されます。 たとえば、次の配列はそれぞれに 3 つの列がある 2 つの行で構成されています。

```C
char A[2][3];
```

最初の行の 3 つの列が先に格納され、その後で 2 行目の 3 つの列が格納されます。 これは、最後の添字が最もすばやく変化することを意味しています。

配列の個々の要素を参照するには、「[Postfix Operators](../c-language/postfix-operators.md)」 (後置形式の演算子) の説明に従って添字式を使用します。

## <a name="examples"></a>使用例

これらの例は配列宣言を示しています。

```C
float matrix[10][15];
```

`matrix` という 2 次元配列には 150 の要素があり、それぞれが **float** 型です。

```C
struct {
    float x, y;
} complex[100];
```

これは、構造体の配列の宣言です。 この配列には 100 個の要素があります。各要素は、2 つのメンバーを含む構造体です。

```C
extern char *name[];
```

このステートメントは、`char` へのポインターの配列の型と名前を宣言しています。 `name` の実際の定義は、他の場所で発生します。

**Microsoft 固有の仕様**

配列の最大サイズを保持するために必要な整数型は、**size_t** のサイズになります。 STDDEF.H ヘッダー ファイルに定義されている **size_t** は、0x00000000 - 0x7CFFFFFF の範囲の `unsigned int` です。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[宣言子と変数宣言](../c-language/declarators-and-variable-declarations.md)
