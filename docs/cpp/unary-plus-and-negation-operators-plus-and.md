---
title: '単項加算演算子と否定演算子: + および -'
ms.date: 11/04/2016
f1_keywords:
- +
- '-'
helpviewer_keywords:
- unary operators [C++], plus
- '- operator'
- negation operator
- + operator [C++], unary operators
- + operator
ms.assetid: 2c58c4f4-0d92-4ae3-9d0c-1a6157875cc1
ms.openlocfilehash: 83fedd9d3cc6cd7c08ba79d2ed83e9f62d919e29
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857243"
---
# <a name="unary-plus-and-negation-operators--and--"></a>単項加算演算子と否定演算子: + および -

## <a name="syntax"></a>構文

```
+ cast-expression
- cast-expression
```

## <a name="-operator"></a>+ 演算子

単項プラス演算子 ( **+** ) の結果は、そのオペランドの値です。 単項プラス演算子のオペランドは数値型である必要があります。

整数の上位変換が整数オペランドに対して実行されます。 結果の型は、オペランドの上位変換先の型です。 このため、式 `+ch`では、`ch` は**char**型であるため、 **int**型になります。値が変更されていません。 プロモーションの実行方法の詳細については、「[標準変換](standard-conversions.md)」を参照してください。

## <a name="--operator"></a>- 演算子

単項否定演算子 ( **-** ) は、そのオペランドの負の値を生成します。 単項否定演算子のオペランドには数値型を指定する必要があります。

整数の上位変換は、整数オペランドに対して実行され、結果の型は、そのオペランドが昇格される型になります。 昇格の実行方法の詳細については、「[標準変換](standard-conversions.md)」を参照してください。

**Microsoft 固有の仕様**

符号なし数値の単項否定演算は、2^n からオペランドの値を減算することによって実行されます。この n は、指定した符号なし型のオブジェクトのビット数です。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[単項演算子を含む式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)