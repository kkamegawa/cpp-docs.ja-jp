---
title: コンパイラ エラー C2251
ms.date: 11/04/2016
f1_keywords:
- C2251
helpviewer_keywords:
- C2251
ms.assetid: fefe050c-f8d3-4316-b237-8007dbcdd3bf
ms.openlocfilehash: d44ed7af3552f0a7c9cc9b5b2b0d14a468713254
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759699"
---
# <a name="compiler-error-c2251"></a>コンパイラ エラー C2251

名前空間 'namespace' にはメンバー 'member' がありません。'member' は正しいですか。

コンパイラは、指定された名前空間で識別子を見つけられませんでした。

次の例では C2251 が生成されます。

```cpp
// C2251.cpp
// compile with: /c
namespace A {
   namespace B {
      void f1();
   }

   using namespace B;
}

void A::f1() {}   // C2251
void A::B::f1() {}   // OK
```
