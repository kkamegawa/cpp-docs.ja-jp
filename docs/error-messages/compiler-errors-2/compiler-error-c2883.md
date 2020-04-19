---
title: コンパイラ エラー C2883
ms.date: 11/04/2016
f1_keywords:
- C2883
helpviewer_keywords:
- C2883
ms.assetid: 5c6d689d-ed42-41ad-b5c0-e9c2e0b8c356
ms.openlocfilehash: cb6b1043d976cfeb8cb92c8780c5b84ea9700b8b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760955"
---
# <a name="compiler-error-c2883"></a>コンパイラ エラー C2883

' name ': 関数宣言は using 宣言で導入された ' identifier ' と競合しています。

関数を複数回定義しようとしました。 最初の定義は、`using` 宣言を使用して名前空間から作成されたものです。 2つ目はローカル定義です。

次の例では、C2883 が生成されます。

```cpp
// C2883.cpp
namespace A {
   void z(int);
}

int main() {
   using A::z;
   void z(int);   // C2883  z is already defined
}
```
