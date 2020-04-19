---
title: C 乗算演算子
ms.date: 11/04/2016
helpviewer_keywords:
- arithmetic operators [C++], multiplicative operators
- / operator
- / operator, multiplicative operators
- remainder operator (%)
- operators [C], multiplication
- '% operator'
- slash (/) operator
- multiplication operator [C++], multiplicative operators
ms.assetid: 495471c9-319b-4eb4-bd97-039a025fd3a9
ms.openlocfilehash: e06ef25c14f8073d2b8753b57c9593af7bb6c69f
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857126"
---
# <a name="c-multiplicative-operators"></a>C 乗算演算子

乗算演算子は、乗算 (<strong>\*</strong>)、除算 ( **/** )、および剰余 ( **%** ) 演算を実行します。

## <a name="syntax"></a>構文

*multiplicative-expression*: &nbsp;&nbsp;&nbsp;&nbsp;*cast-expression* &nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression* <strong>\*</strong> *cast-expression* &nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression* **/** *cast-expression* &nbsp;&nbsp;&nbsp;&nbsp;*multiplicative-expression* **%** *cast-expression*

剰余演算子 ( **%** ) のオペランドは整数である必要があります。 乗算 (<strong>\*</strong>) 演算子と除算 ( **/** ) 演算子は、整数型または浮動小数点型のオペランドを取ることができます。オペランドの型が違ってもかまいません。

乗算演算子は、オペランドに通常の算術変換を実行します。 結果の型は、変換後のオペランドの型です。

> [!NOTE]
>  乗算演算子によって実行される変換ではオーバーフロー条件やアンダーフロー条件が提供されないため、乗算演算の結果を変換後のオペランドの型で表すことができない場合、情報が失われる可能性があります。

C の乗算演算子について、以下に説明します。

|[演算子]|説明|
|--------------|-----------------|
|<strong>\*</strong>|乗算演算子は 2 つのオペランドを乗算します。|
|**/**|除算演算子は、最初のオペランドを 2 番目のオペランドで除算します。 2 つの整数オペランドで除算が行われ、結果が整数でない場合、結果は次の規則に従って切り捨てられます。<br/><br/>- 0 による除算の結果は、ANSI C 規格に従って未定義になります。 Microsoft C コンパイラは、コンパイル時または実行時にエラーを生成します。<br/><br/>- 両方のオペランドが正の値または符号なしである場合、結果は 0 方向に切り捨てられます。<br/><br/>- どちらかのオペランドが負の値の場合、演算の結果が代数的な商以下の最大の整数になるか代数的な商以上の最小の整数になるかは、実装定義になります。 (以下の「Microsoft 固有のセクション」を参照してください)。|
|**%**|剰余演算子の結果は、最初のオペランドを 2 番目のオペランドで除算したときの剰余です。 除算が厳密にできない場合、結果は次の規則によって決定されます。<br/><br/>- 右のオペランドがゼロの場合、結果は未定義になります。<br/><br/>- 両方のオペランドが正の値または符号なしである場合、結果は正の値になります。<br/><br/>- どちらかのオペランドが負の値で、結果が厳密でない場合、結果は実装定義になります。 (以下の「Microsoft 固有のセクション」を参照してください)。|

### <a name="microsoft-specific"></a>Microsoft 固有の仕様

いずれかのオペランドが負である除算では、切り捨ての方向は 0 方向になります。

剰余演算子による除算で、いずれかのオペランドが負の値である場合、結果は被除数 (式の 1 つ目のオペランド) と同じ符号を持ちます。

## <a name="examples"></a>使用例

次に示す宣言は、その後の例で使用されます。

```
int i = 10, j = 3, n;
double x = 2.0, y;
```

次のステートメントでは、乗算演算子を使用しています。

```
y = x * i;
```

この場合は、`x` が `i` で乗算されて、値 20.0 が返されます。 結果は **double** 型になります。

```
n = i / j;
```

この例では、10 が 3 で除算されています。 結果は 0 方向に切り捨てられ、整数値 3 が生成されます。

```
n = i % j;
```

このステートメントでは、10 を 3 で除算したときの剰余である整数 1 が `n` に代入されます。

**Microsoft 固有の仕様**

剰余の符号は、被除数の符号と同じです。 例:

```
50 % -6 = 2
-50 % 6 = -2
```

どちらの場合も、`50` と `2` の符号が同じになっています。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>参照

[乗算演算子と剰余演算子](../cpp/multiplicative-operators-and-the-modulus-operator.md)
