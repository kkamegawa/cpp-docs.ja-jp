---
title: コンパイラ エラー C2229
ms.date: 11/04/2016
f1_keywords:
- C2229
helpviewer_keywords:
- C2229
ms.assetid: 933c7cf2-a463-4e74-b0b4-59dedad987fb
ms.openlocfilehash: 2d974c4f0630a592daad956448bf21cea21efb7c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759270"
---
# <a name="compiler-error-c2229"></a>コンパイラ エラー C2229

型 ' identifier ' には、無効な0サイズの配列が含まれています

構造体またはビットフィールドのメンバーに、最後のメンバーではない、サイズが0の配列が含まれています。

サイズが0の配列は、構造体の最後のメンバーとして持つことができるため、構造体を割り当てるときにそのサイズを指定する必要があります。

サイズが0の配列が構造体の最後のメンバーでない場合、コンパイラは残りのフィールドのオフセットを計算できません。

次の例では、C2229 が生成されます。

```cpp
// C2229.cpp
struct S {
   int a[0];  // C2229  zero-sized array
   int b[1];
};

struct S2 {
   int a;
   int b[0];
};

int main() {
   // allocate 7 elements for b field
   S2* s2 = (S2*)new int[sizeof(S2) + 7*sizeof(int)];
   s2->b[6] = 100;
}
```
