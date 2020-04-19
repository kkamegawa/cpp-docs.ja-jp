---
title: 順次評価演算子
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], sequential-evaluation
- sequential-evaluation operator
- comma operator
ms.assetid: 587514f4-c8e2-44e9-81a8-7a553ce1453a
ms.openlocfilehash: 2cbffc51fb7113ae442dbfcd1db01bbf27a67746
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149129"
---
# <a name="sequential-evaluation-operator"></a>順次評価演算子

順次評価演算子は、"コンマ演算子" とも呼ばれ、2 つのオペランドを左から右へ順番に評価します。

## <a name="syntax"></a>構文

*expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*expression* **,** *assignment-expression*

順次評価演算子の左のオペランドは、`void` 式として評価されます。 演算の結果は右のオペランドと同じ値と型を持ちます。 各オペランドは任意の型にすることができます。 順次評価演算子では、オペランド間の型変換や左辺値の生成は実行されません。 最初のオペランドの後にシーケンス ポイントがあります。つまり、左オペランドを評価したことによるすべての副作用は、右オペランドの評価が開始される前に完了します。 詳細については、「[シーケンス ポイント](../c-language/c-sequence-points.md)」を参照してください。

順次評価演算子は、通常、1 つの式しか許可されないコンテキストで 2 つ以上の式を評価するために使用されます。

コンマは、一部のコンテキストで区切り記号として使用できます。 ただし、コンマの区切り記号としての使用と演算子としての使用を混同しないように注意する必要があります。この 2 つの用途は、まったく別のものです。

## <a name="example"></a>例

次の例は、順次評価演算子を示しています。

```
for ( i = j = 1; i + j < 20; i += i, j-- );
```

この例では、**for** ステートメントの 3 番目の式の各オペランドは、個別に評価されます。 左のオペランド `i += i` が最初に評価され、次に、右のオペランド `j--` が評価されます。

```
func_one( x, y + 2, z );
func_two( (x--, y + 2), z );
```

`func_one` への関数呼び出しでは、`x`、`y + 2`、`z` の 3 つの引数がコンマで区切られて渡されます。 `func_two` の関数呼び出しでは、かっこにより、コンパイラは順次評価演算子として最初のコンマを解釈します。 この関数呼び出しは、`func_two` に 2 つの引数を渡します。 最初の引数は、順次評価演算 `(x--, y + 2)` の結果です。この演算は、式 `y + 2` の値と型を持ち、第 2 の引数は `z` です。

## <a name="see-also"></a>関連項目

[コンマ演算子: ,](../cpp/comma-operator.md)
