---
title: '等値演算子: == および !='
ms.date: 11/04/2016
f1_keywords:
- not_eq
- '!='
- ==
helpviewer_keywords:
- '!= operator'
- equality operator
- not equal to comparison operator
- equality operator [C++], syntax
- == operator
- not_eq operator
- equal to operator
ms.assetid: ba4e9659-2392-4fb4-be5a-910a2a6df45a
ms.openlocfilehash: d6248d4a31c478b62e5fbe304d9bde9b51b7cb06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392170"
---
# <a name="equality-operators--and-"></a>等値演算子: == および !=

## <a name="syntax"></a>構文

```
expression == expression
expression != expression
```

## <a name="remarks"></a>Remarks

これらの二項等値演算子はそれぞれオペランドを比較し、等しいか、等しくないかを判別します。

"等しい" (`==`) および "等しくない" (`!=`) の等値演算子は関係演算子より優先順位が下ですが、動作は同じです。 これらの演算子の結果型は**bool**します。

等号演算子 (`==`) を返します**true**場合は (1) 両方のオペランドが同じ値を持つ以外を返しますそれ以外の場合、 **false** (0)。 Not の演算子 (`!=`) を返します**true**オペランドには、同じ値がない場合、それを返します**false**します。

## <a name="operator-keyword-for-"></a>!= の演算子キーワード

`not_eq` 演算子は `!=` の代替表現です。 アクセスする 2 つの方法がある、`not_eq`プログラムで演算子: ヘッダー ファイルをインクルード`iso646.h`、使用してコンパイル、 [/Za](../build/reference/za-ze-disable-language-extensions.md) (言語拡張を無効にする) コンパイラ オプション。

## <a name="example"></a>例

```cpp
// expre_Equality_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

int main() {
   cout  << boolalpha
         << "The true expression 3 != 2 yields: "
         << (3 != 2) << endl
         << "The false expression 20 == 10 yields: "
         << (20 == 10) << endl;
}
```

等値演算子は、同じ型のメンバーへのポインターを比較できます。 このような比較の場合は、メンバーへのポインター変換が実行されます。 メンバーへのポインターは、0 として評価される定数式と比較することもできます。

## <a name="see-also"></a>関連項目

[二項演算子を含む式](../cpp/expressions-with-binary-operators.md)<br/>
[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 関係演算子と等値演算子](../c-language/c-relational-and-equality-operators.md)