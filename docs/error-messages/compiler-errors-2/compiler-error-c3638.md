---
title: コンパイラ エラー C3638
ms.date: 11/04/2016
f1_keywords:
- C3638
helpviewer_keywords:
- C3638
ms.assetid: 8d8bc5ca-75aa-480e-b6b6-3178fab51b1d
ms.openlocfilehash: f8d67ac0ff6a1fa5d9efbb8d85747ff94d75c648
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742497"
---
# <a name="compiler-error-c3638"></a>コンパイラ エラー C3638

' operator ': 標準のボックス化およびボックス化解除変換演算子を再定義することはできません

コンパイラは、暗黙的なボックス化をサポートするために、各マネージクラスの変換演算子を定義します。 この演算子を再定義することはできません。

詳細については、「[暗黙的なボックス](../../extensions/boxing-cpp-component-extensions.md)化」を参照してください。

次の例では、C3638 が生成されます。

```cpp
// C3638.cpp
// compile with: /clr
value struct V {
   V(){}
   static operator V^(V);   // C3638
};

int main() {
   V myV;
   V ^ pmyV = myV;   // operator supports implicit boxing
}
```
