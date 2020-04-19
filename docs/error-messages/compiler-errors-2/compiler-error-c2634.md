---
title: コンパイラエラー C2634
ms.date: 11/04/2016
f1_keywords:
- C2634
helpviewer_keywords:
- C2634
ms.assetid: 58c8f2db-ac95-4a81-9355-ef3cfb0ba7b3
ms.openlocfilehash: ae53dc8f33920c84bed152cdd7d7bf34e01f165a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759452"
---
# <a name="compiler-error-c2634"></a>コンパイラエラー C2634

' & class:: member ': 参照メンバーへのポインターが無効です

参照メンバーへのポインターが宣言されています。

次の例では、C2634 が生成されます。

```cpp
// C2634.cpp
int mem;
struct S {
   S() : rf(mem) { }
   int &rf;
};
int (S::*pdm) = &S::rf;   // C2634
```
