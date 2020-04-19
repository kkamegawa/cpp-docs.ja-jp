---
title: コンパイラ エラー C2298
ms.date: 11/04/2016
f1_keywords:
- C2298
helpviewer_keywords:
- C2298
ms.assetid: eb0120ad-c850-4bdd-911d-0361229cc859
ms.openlocfilehash: b53ba11de7ecbb8e3d7f664ceaf8d99e395fac28
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759062"
---
# <a name="compiler-error-c2298"></a>コンパイラ エラー C2298

' operation ': メンバー関数式へのポインターに対する操作が正しくありません

メンバー関数へのポインターは、メンバー関数を呼び出す必要があります。

## <a name="example"></a>使用例

次の例では、C2298 が生成されます。

```cpp
// C2298.cpp
#include <stdio.h>

struct X {
   void mf() {
      puts("in X::mf");
   }

   void mf2() {
      puts("in X::mf2");
   }
};

X x;
// pointer to member functions with no params and void return in X
typedef void (X::*pmf_t)();

// a pointer to member function X::mf
void (X::*pmf)() = &X::mf;

int main() {
   int (*pf)();
   pf = x.*pmf;   // C2298
   +(x.*pmf);     // C2298

   pmf_t pf2 = &X::mf2;
   (x.*pf2)();   // uses X::mf2
   (x.*pmf)();   // uses X::mf
}
```

## <a name="example"></a>使用例

次の例では、C2298 が生成されます。

```cpp
// C2298_b.cpp
// compile with: /c
void F() {}

class Measure {
public:
   void SetTrackingFunction(void (Measure::*fnc)()) {
      TrackingFunction = this->*fnc;   // C2298
      TrackingFunction = fnc;   // OK
      GlobalTracker = F;   // OK
   }
private:
   void (Measure::*TrackingFunction)(void);
   void (*GlobalTracker)(void);
};
```
