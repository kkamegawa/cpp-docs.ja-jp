---
title: コンパイラ エラー C2233
ms.date: 11/04/2016
f1_keywords:
- C2233
helpviewer_keywords:
- C2233
ms.assetid: 236bdf0b-9607-4f26-a249-d8def0b1333c
ms.openlocfilehash: 066f28bfaacd1ad2e7645822aef082e43e863327
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759257"
---
# <a name="compiler-error-c2233"></a>コンパイラ エラー C2233

' identifier ': サイズが0の配列を含むオブジェクトの配列は無効です

配列内の各オブジェクトには、少なくとも1つの要素が含まれている必要があります。

次の例では、C2233 が生成されます。

```cpp
// C2233.cpp
// compile with: /c
class A {
   char somearray[1];
};

class B {
   char zeroarray[];
};

A array[100];   // OK
B array2[100];   // C2233
```
