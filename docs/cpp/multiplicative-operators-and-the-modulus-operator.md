---
title: 乗算演算子と剰余演算子
ms.date: 11/04/2016
f1_keywords:
- '%'
- /
helpviewer_keywords:
- operators [C++], multiplicative
- arithmetic operators [C++], multiplicative operators
- modulus operator [C++]
- '* operator'
- division operator [C++], multiplicative operators
- '% operator'
- multiplication operator [C++], multiplicative operators
- multiplicative operators [C++]
- division operator
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
ms.openlocfilehash: 9a01672976703634c06724c9c655605bb433facf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301826"
---
# <a name="multiplicative-operators-and-the-modulus-operator"></a>乗算演算子と剰余演算子

## <a name="syntax"></a>構文

```
expression * expression
expression / expression
expression % expression
```

## <a name="remarks"></a>Remarks

乗算演算子は次のとおりです。

- 乗算 (<strong>\*</strong>)

- 除算 (**/**)

- 剰余 (除算の剰余) (**%**)

これらの二項演算子の結合規則は、左から右方向です。

乗算演算子は、数値型のオペランドを受け取ります。 剰余演算子 (**%**) より厳しい要件を持つことで、そのオペランドが整数型でなければなりません。 (浮動小数点除算の剰余を取得、実行時の関数を使用する[fmod](../c-runtime-library/reference/fmod-fmodf.md))。変換は、「[標準変換](standard-conversions.md)オペランドに適用され結果は変換後の型のです。

乗算演算子は、最初のオペランドを 2 番目のオペランドで乗算した結果を生成します。

除算演算子は、最初のオペランドを 2 番目のオペランドで除算した結果を生成します。

剰余演算子は、次の式で指定された残りの部分を生成ここ*e1*最初のオペランドと*e2* 2 番目の: *e1* -(*e1* /  *e2*) \* *e2*両方のオペランドが整数型が、します。

除算または剰余式における 0 での除算は未定義になり、実行時エラーが発生します。 したがって、次の式は未定義の間違った結果を生成します。

```cpp
i % 0
f / 0.0
```

乗算式、除算式、剰余式への両方のオペランドに同じ符号がある場合、結果は正の値になります。 それ以外の場合、結果は負になります。 剰余演算の符号の結果は実装定義されます。

> [!NOTE]
>  乗算演算子によって実行される変換ではオーバーフロー条件やアンダーフロー条件が提供されないため、乗算演算の結果を変換後のオペランドの型で表すことができない場合、情報が失われる可能性があります。

**Microsoft 固有の仕様**

Microsoft C++ では、剰余式の結果は常に最初のオペランドと同じ符号になります。

**Microsoft 固有の仕様はここまで**

2 つの整数の計算された除算が正確ではなく、1 つのオペランドだけが負の値の場合、結果は、除算演算で算出された正確な値未満の最大の整数 (大きさでは、符号を無視します) になります。 たとえば、-11 計算値-3.666666666 は。 整数の除算の結果は-3 です。

乗算演算子の間のリレーションシップは、id で指定されます (*e1* / *e2*) \* *e2*  +  *e1* % *e2* == *e1*します。

## <a name="example"></a>例

次のプログラムは乗算演算子を示します。 注意のいずれかのオペランド`10 / 3`型に明示的にキャストする必要があります**float**ように両方のオペランド型の切り捨てを回避するために**float**除算する前にします。

```cpp
// expre_Multiplicative_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   int x = 3, y = 6, z = 10;
   cout  << "3 * 6 is " << x * y << endl
         << "6 / 3 is " << y / x << endl
         << "10 % 3 is " << z % x << endl
         << "10 / 3 is " << (float) z / x << endl;
}
```

## <a name="see-also"></a>関連項目

[二項演算子を含む式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 乗算演算子](../c-language/c-multiplicative-operators.md)