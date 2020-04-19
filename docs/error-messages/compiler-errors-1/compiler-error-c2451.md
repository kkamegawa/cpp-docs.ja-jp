---
title: コンパイラ エラー C2451
ms.date: 11/04/2016
f1_keywords:
- C2451
helpviewer_keywords:
- C2451
ms.assetid: a64c93a5-ab8d-4d39-ae57-9ee7ef803036
ms.openlocfilehash: 1c42f9349323b08a86b0f8bb9ff79e8f0da6ed77
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744122"
---
# <a name="compiler-error-c2451"></a>コンパイラ エラー C2451

型 ' type ' の条件式は無効です

条件式は、整数型に評価されます。

次の例では、C2451 が生成されます。

```cpp
// C2451.cpp
class B {};

int main () {
   B b1;
   int i = 0;
   if (b1)   // C2451
   // try the following line instead
   // if (i)
      ;
}
```
