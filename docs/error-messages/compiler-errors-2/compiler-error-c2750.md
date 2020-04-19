---
title: コンパイラエラー C2750
ms.date: 11/04/2016
f1_keywords:
- C2750
helpviewer_keywords:
- C2750
ms.assetid: 30450034-feb5-448c-9655-b8c5f3639695
ms.openlocfilehash: 56f4e6e1d6c392fc377fe5fdf11643ae8a2e503a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759608"
---
# <a name="compiler-error-c2750"></a>コンパイラエラー C2750

' type ': 参照型で ' new ' を使用することはできません。代わりに ' gcnew ' を使用してください

CLR 型のインスタンスを作成して、ガベージコレクトされたヒープにインスタンスを配置するには、 [gcnew](../../extensions/ref-new-gcnew-cpp-component-extensions.md)を使用する必要があります。

次の例では、C2750 が生成されます。

```cpp
// C2750.cpp
// compile with: /clr
ref struct Y1 {};

int main() {
   Y1 ^ x = new Y1;   // C2750

   // try the following line instead
   Y1 ^ x2 = gcnew Y1;
}
```
