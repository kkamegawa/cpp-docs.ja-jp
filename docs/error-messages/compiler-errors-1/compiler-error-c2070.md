---
title: コンパイラエラー C2070
ms.date: 11/04/2016
f1_keywords:
- C2070
helpviewer_keywords:
- C2070
ms.assetid: 4c8dea63-1227-4aba-be26-2462537f86fb
ms.openlocfilehash: 40ecce3c95f1c429fa1699b26d74e62a5d1f4d9c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757762"
---
# <a name="compiler-error-c2070"></a>コンパイラエラー C2070

' type ': sizeof オペランドが無効です。

[Sizeof](../../cpp/sizeof-operator.md)演算子には、式または型名が必要です。

次の例では、C2070 が生成されます。

```cpp
// C2070.cpp
void func() {}
int main() {
   int a;
   a = sizeof(func);   // C2070
}
```

解決方法:

```cpp
// C2070b.cpp
void func() {}
int main() {
   int a;
   a = sizeof(a);
}
```
