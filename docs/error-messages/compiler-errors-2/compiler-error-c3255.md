---
title: コンパイラ エラー C3255
ms.date: 11/04/2016
f1_keywords:
- C3255
helpviewer_keywords:
- C3255
ms.assetid: 877ffca2-fd92-44b6-9060-6091b928b1c1
ms.openlocfilehash: 43538ce87e1d832fcfc4fca882a9f129b917aad5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754213"
---
# <a name="compiler-error-c3255"></a>コンパイラ エラー C3255

' 値の型 ': この値型のオブジェクトをネイティブヒープで動的に割り当てることはできません

マネージメンバーを含む値の型のインスタンス (「[クラスと構造体](../../extensions/classes-and-structs-cpp-component-extensions.md)」を参照) は、スタック上で作成できますが、ヒープ上に作成することはできません。

次の例では、C3255 が生成されます。

```cpp
// C3255.cpp
// compile with: /clr
using namespace System;
value struct V {
   Object^ o;
};

value struct V2 {
   int i;
};

int main() {
   V* pv = new V;   // C3255
   V2* pv2 = new V2;
   V v2;
}
```
