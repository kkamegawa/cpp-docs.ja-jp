---
title: __restrict
ms.date: 10/10/2018
f1_keywords:
- __restrict_cpp
- __restrict
- _restrict
helpviewer_keywords:
- __restrict keyword [C++]
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
ms.openlocfilehash: 76cdf9424e6eab33a3a92b3f98d9c2b0b04ff667
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183753"
---
# <a name="__restrict"></a>__restrict

ように、 **_ _declspec ([制限](../cpp/restrict.md))** 修飾子、 **_ _restrict**キーワードは、シンボルがエイリアス化された現在のスコープ内ではないことを示します。 **_ _Restrict**キーワードとは異なります、`__declspec ( restrict )`修飾子は、次の方法で。

- **_ _Restrict**キーワードは、変数にのみ有効ですし、`__declspec ( restrict )`関数宣言と定義でのみ有効です。

- **_ _restrict**のような**制限**C99 仕様からが **_ _restrict**で使用できるC++または C プログラム。

- ときに **_ _restrict**が使用すると、コンパイラは伝達されません変数の非エイリアスのプロパティ。 つまりを割り当てた場合、 **_ _restrict**変数以外に **_ _restrict**変数コンパイラも、-_ _restrict 以外には別名を変数。 これは、別の動作、**制限**C99 仕様のキーワード。

一般に、関数全体の動作に影響を及ぼす場合、キーワードよりも `__declspec ( restrict )` を使用する方が適切です。

以前のバージョンとの互換性のため **_restrict**のシノニムです **_ _restrict**しない限り、コンパイラ オプション[/Za\(言語拡張機能を無効にする)](../build/reference/za-ze-disable-language-extensions.md)は指定します。

Visual Studio 2015 以降では、 **_ _restrict**で使用できるC++参照。

> [!NOTE]
>  持っている変数に対して使用すると、[volatile](../cpp/volatile-cpp.md)キーワード、**volatile**が優先されます。

## <a name="example"></a>例

```cpp
// __restrict_keyword.c
// compile with: /LD
// In the following function, declare a and b as disjoint arrays
// but do not have same assurance for c and d.
void sum2(int n, int * __restrict a, int * __restrict b,
          int * c, int * d) {
   int i;
   for (i = 0; i < n; i++) {
      a[i] = b[i] + c[i];
      c[i] = b[i] + d[i];
    }
}

// By marking union members as __restrict, tell compiler that
// only z.x or z.y will be accessed in any given scope.
union z {
   int * __restrict x;
   double * __restrict y;
};
```

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)