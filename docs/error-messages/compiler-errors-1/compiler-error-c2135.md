---
title: コンパイラ エラー C2135
ms.date: 11/04/2016
f1_keywords:
- C2135
helpviewer_keywords:
- C2135
ms.assetid: aa360d22-4f79-4de1-b384-93cadd10975f
ms.openlocfilehash: 4bc9d8bc3db5fbd826ded37d93ac812116356eb2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757489"
---
# <a name="compiler-error-c2135"></a>コンパイラ エラー C2135

'bit operator': ビット フィールドの演算が正しくありません

アドレス演算子 (`&`) は、ビット フィールドに適用できません。

次の例では C2135 が生成されます。

```cpp
// C2135.cpp
struct S {
   int i : 1;
};

struct T {
   int j;
};
int main() {
   &S::i;   // C2135 address of a bit field
   &T::j;   // OK
}
```
