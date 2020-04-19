---
title: コンパイラ エラー C3241
ms.date: 11/04/2016
f1_keywords:
- C3241
helpviewer_keywords:
- C3241
ms.assetid: 2ca14879-bba0-4a23-b22a-72cfff92d6a4
ms.openlocfilehash: 6a618a9c538558d2aa4b995cbc9071bb8e94a5bc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754578"
---
# <a name="compiler-error-c3241"></a>コンパイラ エラー C3241

' method ': このメソッドは ' interface ' によって導入されていません

関数を明示的にオーバーライドする場合、関数のシグネチャは、オーバーライドする関数の宣言と完全に一致する必要があります。

次の例では、C3241 が生成されます。

```cpp
// C3241.cpp
#pragma warning(disable:4199)

__interface IX12A {
   void mf();
};

__interface IX12B {
   void mf(int);
};

class CX12 : public IX12A, public IX12B { // C3241
   void IX12A::mf(int);
};
```
