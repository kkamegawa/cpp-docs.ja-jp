---
title: コンパイラエラー C2658
ms.date: 11/04/2016
f1_keywords:
- C2658
helpviewer_keywords:
- C2658
ms.assetid: 638368e8-7893-4a14-abec-13c768a9543a
ms.openlocfilehash: 77a9122d20561ceee4f211394b3b81900d5580ac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756085"
---
# <a name="compiler-error-c2658"></a>コンパイラエラー C2658

' member ': 無名構造体または共用体で再定義される

2つの匿名構造体または共用体に、同じ識別子を持ち、型が異なるメンバー宣言が含まれています。 [/Za](../../build/reference/za-ze-disable-language-extensions.md)では、同じ識別子と型のメンバーに対してもこのエラーが発生します。

次の例では、C2658 が生成されます。

```cpp
// C2658.cpp
// compile with: /c
struct X {
   union { // can be struct too
      int i;
   };
   union {
      int i;   // Under /Za, C2658
      // int i not needed here because it is defined in the first union
   };
};

struct Z {
   union {
      char *i;
   };

   union {
      void *i;   // C2658 redefinition of 'i'
      // try the following line instead
      // void *ii;
   };
};
```
