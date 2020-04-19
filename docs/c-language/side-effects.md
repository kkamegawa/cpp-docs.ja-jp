---
title: 副作用
ms.date: 11/04/2016
helpviewer_keywords:
- expression evaluation, side effects
- side effects in expression evaluation
ms.assetid: d9b3004a-830e-43a0-bea5-8989d501d670
ms.openlocfilehash: de5e398afd8b95cfe5596f487a36b6a2d27e3287
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147478"
---
# <a name="side-effects"></a>副作用

式の評価の順序は、言語が特定の評価順序を保証する場合を除き、特定の実装によって定義されます (「[評価の優先順位と順序](../c-language/precedence-and-order-of-evaluation.md)」で説明)。 たとえば、次の関数呼び出しでは副作用が起きます。

```
add( i + 1, i = j + 2 );
myproc( getc(), getc() );
```

関数呼び出しの引数は、任意の順序で評価できます。 式 `i + 1` は `i = j + 2` の前に評価される場合があり、`i = j + 2` は `i + 1` の前に評価される場合があります。 それぞれの場合で、結果は異なります。 同様に、`myproc` に実際にどの文字が渡されるかを保証することはできません。 単項インクリメントおよびデクリメント演算は代入を含むため、このような操作により、次の例に示すような副作用が発生する可能性があります。

```
x[i] = i++;
```

この例では、変更された `x` の値は予測できません。 添字の値は `i` の新規または古い値である可能性があります。 結果は、コンパイラや最適化レベルが異なると変わります。

C は副作用の評価順序を定義しないため、前に示した評価メソッドはどちらも正しく、どちらでも実行できます。 コードの移植性と明確さを確実に実現するために、副作用に関する評価の特定の順序に依存するステートメントを使用しないでください。

## <a name="see-also"></a>関連項目

[式の評価](../c-language/expression-evaluation-c.md)
