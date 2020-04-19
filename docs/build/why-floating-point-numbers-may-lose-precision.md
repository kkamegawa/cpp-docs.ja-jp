---
title: 浮動小数点数の精度の低下
ms.date: 11/04/2016
helpviewer_keywords:
- DBL_EPSILON constant
- FLT_EPSILON constant
- floating-point numbers, precision
ms.assetid: 1acb1add-ac06-4134-a2fd-aff13d8c4c15
ms.openlocfilehash: 373ce9fa2c2c96fac349940076873a4a637a9dbe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298715"
---
# <a name="why-floating-point-numbers-may-lose-precision"></a>浮動小数点数の精度の低下

浮動小数点値には、通常、正確なバイナリ表現がありません。 これは、CPU が浮動小数点データを表す方法の副作用です。 このため、精度の低下が発生する可能性があり、一部の浮動小数点演算では予期しない結果が生じる可能性があります。

この動作は、次のいずれかの結果になります。

- 10進数のバイナリ表現は正確でない場合があります。

- 使用されている数値の間に型の不一致があります (float と double の混合など)。

この動作を解決するには、ほとんどのプログラマが、値が必要な値より大きいか小さいか、または有効桁数を維持するバイナリのコード化された Decimal (BCD) ライブラリを取得して使用します。

浮動小数点値のバイナリ表現は、浮動小数点演算の精度と精度に影響します。 Microsoft Visual C++は[、IEEE 浮動小数点形式](ieee-floating-point-representation.md)を使用します。

## <a name="example"></a>使用例

```c
// Floating-point_number_precision.c
// Compile options needed: none. Value of c is printed with a decimal
// point precision of 10 and 6 (printf rounded value by default) to
// show the difference
#include <stdio.h>

#define EPSILON 0.0001   // Define your own tolerance
#define FLOAT_EQ(x,v) (((v - EPSILON) < x) && (x <( v + EPSILON)))

int main() {
   float a, b, c;

   a = 1.345f;
   b = 1.123f;
   c = a + b;
   // if (FLOAT_EQ(c, 2.468)) // Remove comment for correct result
   if (c == 2.468)            // Comment this line for correct result
      printf_s("They are equal.\n");
   else
      printf_s("They are not equal! The value of c is %13.10f "
                "or %f",c,c);
}
```

```Output
They are not equal! The value of c is  2.4679999352 or 2.468000
```

## <a name="comments"></a>コメント

イプシロンの場合は、1.192092896 e-07F として定義されている定数 FLT_EPSILON を使用するか、2.2204460492503131 016 として定義されている DBL_EPSILON を使用できます。 これらの定数には、float を含める必要があります。 これらの定数は、x + 1.0 が1.0 と等しくならないように、最小の正の数値 x として定義されます。 これは非常に小さな数値であるため、非常に大きな数値を含む計算にはユーザー定義の許容範囲を使用する必要があります。

## <a name="see-also"></a>関連項目

[コードの最適化](optimizing-your-code.md)
