---
title: コンパイラ エラー C2571
ms.date: 11/04/2016
f1_keywords:
- C2571
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
ms.openlocfilehash: 7bd87f0732e1a632b8c86cc57fab1a0f104b2c77
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755500"
---
# <a name="compiler-error-c2571"></a>コンパイラ エラー C2571

' function ': 仮想関数を共用体 ' union ' に指定することはできません。

共用体が仮想関数で宣言されています。 仮想関数は、クラスまたは構造体でのみ宣言できます。  考えられる解決策は次のとおりです。

1. 共用体をクラスまたは構造体に変更します。

1. 関数を非仮想にします。

次の例では、C2571 が生成されます。

```cpp
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```
