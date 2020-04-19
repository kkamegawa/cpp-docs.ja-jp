---
title: コンパイラ エラー C3697
ms.date: 11/04/2016
f1_keywords:
- C3697
helpviewer_keywords:
- C3697
ms.assetid: 2d3f63c4-b7f8-421d-a7a5-2bf17fd054f9
ms.openlocfilehash: e642c744bbce5db4bb341a32769b2d9f74654044
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758061"
---
# <a name="compiler-error-c3697"></a>コンパイラ エラー C3697

' qualifier ': この修飾子を ' ^ ' で使用することはできません

追跡ハンドル (^) が、設計されていない修飾子に適用されました。

次の例では、C3697 が生成されます。

```cpp
// C3697.cpp
// compile with: /clr
using namespace System;
int main() {
   String ^__restrict s;   // C3697
   String ^ s2;   // OK
}
```
