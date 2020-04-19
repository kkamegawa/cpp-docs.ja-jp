---
title: 単項演算子を含む式
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], unary operators
- unary operators [C++], expressions with
- expressions [C++], operators
ms.assetid: 1217685b-b85d-4b48-9ff4-d90f56a26c1b
ms.openlocfilehash: a13b86755a5e309a51a0e2e14faa1157b7e95ea0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183872"
---
# <a name="expressions-with-unary-operators"></a>単項演算子を含む式

単項演算子は、式の中で 1 つのオペランドに対してのみ作用します。 単項演算子は、次のとおりです。

- [間接演算子 (*)](../cpp/indirection-operator-star.md)

- [Address-of 演算子 (&)](../cpp/address-of-operator-amp.md)

- [単項プラス演算子 (+)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [単項否定演算子 (-)](../cpp/unary-plus-and-negation-operators-plus-and.md)

- [論理否定演算子 (!)](../cpp/logical-negation-operator-exclpt.md)

- [1 の補数演算子 (~)](../cpp/one-s-complement-operator-tilde.md)

- [前置インクリメント演算子 (+ +)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [前置デクリメント演算子 (-)](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)

- [キャスト演算子)](../cpp/cast-operator-parens.md)

- [sizeof 演算子](../cpp/sizeof-operator.md)

- [_ _uuidof 演算子](../cpp/uuidof-operator.md)

- [_ _alignof 演算子](../cpp/alignof-operator.md)

- [new 演算子](../cpp/new-operator-cpp.md)

- [delete 演算子](../cpp/delete-operator-cpp.md)

これらの演算子の結合規則は、右から左方向です。 単項式は構文では一般に後置式または 1 次式より優先されます。

以下は単項式の可能な形式です。

- *postfix-expression*

- `++` *unary-expression*

- `--` *unary-expression*

- *unary-operator* *cast-expression*

- **sizeof** *unary-expression*

- `sizeof(` *type-name* `)`

- `decltype(` *expression* `)`

- *allocation-expression*

- *deallocation-expression*

すべて*後置式*と見なされます、*単項式*、し、どの 1 次式と見なされるため、*後置式*、どの 1 次式は、見なされます、*単項式*もします。 詳細については、次を参照してください。[後置式](../cpp/postfix-expressions.md)と[一次式](../cpp/primary-expressions.md)します。

A*単項演算子*の 1 つ以上の次の記号で構成されます。 `* & + - ! ~`

*キャスト式*単項式の種類を変更する、省略可能なキャストです。 詳細については、次を参照してください。[キャスト演算子: ()](../cpp/cast-operator-parens.md)します。

*式*式にできます。 詳細については、次を参照してください。[式](../cpp/expressions-cpp.md)します。

*割り当て式*を指す、**new**演算子。 *解放式*を指す、**delete**演算子。 詳細については、このトピックで前述したリンクを参照してください。

## <a name="see-also"></a>関連項目

[式の型](../cpp/types-of-expressions.md)
