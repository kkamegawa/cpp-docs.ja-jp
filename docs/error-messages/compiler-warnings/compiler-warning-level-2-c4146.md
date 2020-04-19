---
title: コンパイラの警告 (レベル 2) C4146
ms.date: 11/04/2016
f1_keywords:
- C4146
helpviewer_keywords:
- C4146
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
ms.openlocfilehash: d595befc80d954c8fb84f83ad6c4e0cb5f4fcf26
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052167"
---
# <a name="compiler-warning-level-2-c4146"></a>コンパイラの警告 (レベル 2) C4146

単項マイナス演算子が符号なしの型に適用されましたが、結果はまだ符号なしです。

符号なしの型は負以外の値のみを保持できます。そのため、符号なしの型に適用した場合、単項マイナス (否定) は意味がありません。 オペランドと結果の両方が負ではありません。

これは事実上、プログラマが最小の整数値 (-2147483648) を表す場合に発生します。 式は2つの段階で処理されるため、この値を-2147483648 として書き込むことはできません。

1. 数値2147483648が評価されます。 この値は最大整数値2147483647を超えているため、2147483648の型は[int](../../c-language/integer-types.md)ではなく `unsigned int`になります。

1. 単項マイナスは、符号なしの結果を使用して値に適用されます。これは2147483648にもなります。

結果の符号なしの型は、予期しない動作を引き起こす可能性があります。 比較で結果を使用する場合は、たとえば、もう一方のオペランドが `int`の場合などに、符号なしの比較を使用することができます。 ここでは、サンプルプログラムが1行だけを出力する理由について説明します。

`((unsigned int)1) > 2147483648` が false であるため、予定されている2行目の `1 is greater than the most negative int`は印刷されません。

C4146 の INT_MIN を使用すると、型が**signed INT**になっているため、これを回避できます。

## <a name="example"></a>例

次の例では、C4146 が生成されます。

```cpp
// C4146.cpp
// compile with: /W2
#include <stdio.h>

void check(int i)
{
    if (i > -2147483648)   // C4146
        printf_s("%d is greater than the most negative int\n", i);
}

int main()
{
    check(-100);
    check(1);
}
```