---
title: コンパイラエラー C2682
ms.date: 11/04/2016
f1_keywords:
- C2682
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
ms.openlocfilehash: c1ce0132ed0db418359effe60f59e1eb2d3cc221
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760284"
---
# <a name="compiler-error-c2682"></a>コンパイラエラー C2682

casting_operator を使用して ' type1 ' から ' type1 ' に変換することはできません

キャスト演算子が互換性のない型を変換しようとしました。 たとえば、 [dynamic_cast](../../cpp/dynamic-cast-operator.md)演算子を使用してポインターを参照に変換することはできません。 `dynamic_cast` 演算子は、修飾子のキャストには使用できません。 型のすべての修飾子が一致している必要があります。

`const_cast` 演算子を使用すると、`const`、`volatile`、`__unaligned`などの属性を削除できます。

次の例では、C2682 が生成されます。

```cpp
// C2682.cpp
class A { virtual void f(); };
class B: public A {};

void g(A* pa) {
    B& rb = dynamic_cast<B&>(pa); // C2682
}
```

次の例では、C2682 が生成されます。

```cpp
// C2682b.cpp
// compile with: /clr
ref struct R{};
ref struct RR : public R{};
ref struct H {
   RR^ r ;
   short s;
   int i;
};

int main() {
   H^ h = gcnew H();
   interior_ptr<int>lr = &(h->i);
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK
}
```
