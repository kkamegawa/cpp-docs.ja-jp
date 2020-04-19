---
title: 単項算術演算子
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], unary
- tilde (~) one's complement operator
- bitwise-complement operator
- arithmetic operators [C++], unary
- + operator, unary operators
- unary operators
- exclamation points
- ~ operator, one's complement operator
- logical negation
- '! operator, unary arithmetic operators'
ms.assetid: 78c91415-d469-499e-9dfe-4435350fd333
ms.openlocfilehash: f64bc5107cf0df55fd445d04d557e952702deaee
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150832"
---
# <a name="unary-arithmetic-operators"></a>単項算術演算子

C の単項プラス演算子、算術否定演算子、補数演算子、および論理否定演算子については、後の一覧で説明します。

|演算子|説明|
|--------------|-----------------|
|**+**|かっこ内の式に続く単項プラス演算子は、かっこで囲まれた演算のグループ化を強制します。 これは、複数の結合的または可換的な二項演算子を含む式で使用されます。 オペランドは数値型である必要があります。 結果はオペランドの値です。 整数オペランドには整数の上位変換が加えられます。 結果の型は、昇格されたオペランドの型です。|
|**-**|算術否定演算子は、オペランドの負数 (2 の補数) を生成します。 オペランドは整数値または浮動小数点値である必要があります。 この演算子は、通常の算術変換を行います。|
|`~`|ビットごとの補数 (またはビットごとの NOT) 演算子は、オペランドのビットごとの補数を生成します。 オペランドは整数型である必要があります。 この演算子は、通常の算術変換を行います。結果は変換後のオペランドの型です。|
|**!**|論理否定 (論理 NOT) 演算子は、オペランドが true (ゼロ以外) の場合は値 0、オペランドが false の場合 (0) は値 1 を生成します。 結果は `int` 型になります。 オペランドは整数値、浮動小数点値またはポインター値である必要があります。|

ポインターの単項算術演算は無効です。

## <a name="examples"></a>使用例

次の例は、単項算術演算子を示します。

```
short x = 987;
    x = -x;
```

上の例では、`x` の新しい値は 987 の負の値、つまり -987 です。

```
unsigned short y = 0xAAAA;
    y = ~y;
```

この例では、`y` に割り当てられた新しい値は、符号なしの値 0xAAAA の補数、または 0x5555 です。

```
if( !(x < y) )
```

`x` が `y` 以上の場合、式の結果は 1 (true) になります。 `x` が `y` よりも小さい場合、結果は 0 (false) になります。

## <a name="see-also"></a>関連項目

[単項演算子を含む式](../cpp/expressions-with-unary-operators.md)
