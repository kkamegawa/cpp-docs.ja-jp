---
title: コンパイラエラー C2655
ms.date: 11/04/2016
f1_keywords:
- C2655
helpviewer_keywords:
- C2655
ms.assetid: beaefa6e-51b3-4df9-9150-960f3fbf40e0
ms.openlocfilehash: dbef9f00145c84a5c562915da966f2a49995c3ba
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756111"
---
# <a name="compiler-error-c2655"></a>コンパイラエラー C2655

' identifier ': 現在のスコープでは定義または再宣言が無効です

識別子は、グローバルスコープでのみ再宣言できます。

次の例では、C2655 が生成されます。

```cpp
// C2655.cpp
class A {};
class B {
public:
   static int i;
};

int B::i;  // OK

int main() {
   A B::i;  // C2655
}
```
