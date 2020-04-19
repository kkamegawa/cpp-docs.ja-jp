---
title: 'アドレス演算子: &amp;'
ms.date: 11/04/2016
f1_keywords:
- '&'
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
ms.openlocfilehash: a03a6100c372e059bd9ef2ddde0558da307923dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385025"
---
# <a name="address-of-operator-amp"></a>アドレス演算子: &amp;

## <a name="syntax"></a>構文

```
& cast-expression
```

## <a name="remarks"></a>Remarks

単項アドレス演算子 ( **&** ) は、オペランドのアドレスを取得します。 アドレス演算子のオペランドには、関数指定子またはビットフィールドではないオブジェクトを指定する左辺値のいずれかを指定できます。

アドレス演算子は、ファイルスコープレベルで宣言された 基本型、構造体型、クラス型、共用体型の変数、または添字配列参照だけに適用できます。 これらの式では、アドレス演算子を含まない定数式を、アドレス式に加算したりアドレス式から減算できます。

関数または左辺値に適用されたときの式の結果は、オペランドの型から派生したポインター型 (右辺値) です。 たとえば、オペランドの型が **char**の場合、式の結果は **char** ポインター型になります。 **const** または **volatile** オブジェクトにアドレス演算子を適用した場合 `const type *` または `volatile type *` に評価されます（**type** とは元のオブジェクト型）。

アドレス演算子が修飾名に適用された場合、その結果は指定した修飾名が静的メンバーかどうか次第です。もしそうなら、結果はメンバーの宣言で指定した型へのポインターです。メンバーが静的でない場合、その結果は*修飾クラス名*で示されたクラスメンバーの *名前* へのポインターです。 (*修飾クラス名* の詳細については [一次式](../cpp/primary-expressions.md) を参照してください)。次のコード片ではメンバーが静的かどうかによってどのように結果が変わるかを示しています。

```cpp
// expre_Address_Of_Operator.cpp
// C2440 expected
class PTM {
public:
    int iValue;
    static float fValue;
};

int main() {
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static
   float *spfValue     = &PTM::fValue;  // OK
}
```

この例では、`&PTM::fValue` 式は `fValue` が静的メンバーであるため `float PTM::*` 型の代わりに `float *` 型を生成します。

多重定義された関数のアドレスは、どのバージョンの関数が参照されているかが明らかな場合にのみ受け取ることができます。 多重定義されたうちの特定の関数のアドレスを取得する方法については [関数のオーバーロード](function-overloading.md) を参照してください。

参照型にアドレス演算子を適用すると、参照がバインドされたオブジェクトに演算子を適用するのと同じ結果を生成します。 例として:

## <a name="example"></a>例

```cpp
// expre_Address_Of_Operator2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
int main() {
   double d;        // Define an object of type double.
   double& rd = d;  // Define a reference to the object.

   // Obtain and compare their addresses
   if( &d == &rd )
      cout << "&d equals &rd" << endl;
}
```

## <a name="output"></a>出力

```Output
&d equals &rd
```

次の例ではアドレス演算子を使用してポインター引数を関数へ受け渡します。

```cpp
// expre_Address_Of_Operator3.cpp
// compile with: /EHsc
// Demonstrate address-of operator &

#include <iostream>
using namespace std;

// Function argument is pointer to type int
int square( int *n ) {
   return (*n) * (*n);
}

int main() {
   int mynum = 5;
   cout << square( &mynum ) << endl;   // pass address of int
}
```

## <a name="output"></a>出力

```Output
25
```

## <a name="see-also"></a>関連項目

[単項演算子を含む式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[左辺値参照宣言子: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[間接演算子とアドレス演算子](../c-language/indirection-and-address-of-operators.md)
