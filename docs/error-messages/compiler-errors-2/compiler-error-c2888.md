---
title: コンパイラ エラー C2888
ms.date: 11/04/2016
f1_keywords:
- C2888
helpviewer_keywords:
- C2888
ms.assetid: 244f593e-ff25-4dad-b31f-84dafa3bc84a
ms.openlocfilehash: 93fe37c72a04e8c942f910ed3a631e5ba2a542bc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760916"
---
# <a name="compiler-error-c2888"></a>コンパイラ エラー C2888

' identifier ': シンボルを名前空間 ' namespace ' 内で定義することはできません

名前空間 A に属するシンボルは、を囲む名前空間で定義されている必要があります。

次の例では、C2888 が生成されます。

```cpp
// C2888.cpp
// compile with: /c
namespace M {
   namespace N {
      void f1();
      void f2();
   }

   void N::f1() {}   // OK: namspace M encloses N
}

namespace O {
   void M::N::f2() {}   // C2888 namespace O does not enclose M
}
```
