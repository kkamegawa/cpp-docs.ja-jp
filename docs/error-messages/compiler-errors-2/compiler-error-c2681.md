---
title: コンパイラエラー C2681
ms.date: 11/04/2016
f1_keywords:
- C2681
helpviewer_keywords:
- C2681
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
ms.openlocfilehash: d7cf39e89f70f27471fb3a251aac12793f1fb33b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760297"
---
# <a name="compiler-error-c2681"></a>コンパイラエラー C2681

' type ': 名前の式の型が無効です。

キャスト演算子が無効な型から変換しようとしました。 たとえば、 [dynamic_cast](../../cpp/dynamic-cast-operator.md)演算子を使用して式をポインター型に変換する場合、ソース式はポインターである必要があります。

次の例では、C2681 が生成されます。

```cpp
// C2681.cpp
class A { virtual void f(); };

void g(int i) {
    A* pa;
    pa = dynamic_cast<A*>(i);  // C2681
}
```
