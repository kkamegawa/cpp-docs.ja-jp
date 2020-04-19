---
title: コンパイラエラー C2683
ms.date: 11/04/2016
f1_keywords:
- C2683
helpviewer_keywords:
- C2683
ms.assetid: db605e4f-601b-4d05-92a1-c43ca24de08d
ms.openlocfilehash: 8526dc1fe3cacc872aa91ca058677d15318fd703
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760271"
---
# <a name="compiler-error-c2683"></a>コンパイラエラー C2683

' cast ': ' type ' はポリモーフィックな型ではありません

[Dynamic_cast](../../cpp/dynamic-cast-operator.md)を使用して、非ポリモーフィッククラス (仮想関数を持たないクラス) から変換することはできません。

[Static_cast](../../cpp/static-cast-operator.md)を使用すると、非ポリモーフィック型の変換を実行できます。 ただし、`static_cast` では、実行時チェックは実行されません。

次の例では、C2683 が生成されます。

```cpp
// C2683.cpp
// compile with: /c
class B { };
class D : public B { };

void f(B* pb) {
   D* pd1 = dynamic_cast<D*>(pb);  // C2683
   D* pd1 = static_cast<D*>(pb);   // OK
}
```
