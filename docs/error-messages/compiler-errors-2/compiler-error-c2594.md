---
title: コンパイラ エラー C2594
ms.date: 11/04/2016
f1_keywords:
- C2594
helpviewer_keywords:
- C2594
ms.assetid: 68cd708f-266e-44b0-a211-3e3ab63b11bf
ms.openlocfilehash: ade657f9ada2a2249d2f96b7caada7b9719195d1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759335"
---
# <a name="compiler-error-c2594"></a>コンパイラ エラー C2594

' operator ': ' type1 ' から ' type1 ' へのあいまいな変換です

*Type1 から type1*への変換は、他よりもダイレクトされ*ています*。 *Type1 から type1*に変換するには、2つのソリューションを使用することをお勧め*します。* 最初のオプションは、 *type1 から type1* *への*直接変換を定義すること*です。 2*番目のオプションでは、 *type1 から type1*への変換のシーケンスを指定します。

次の例では、C2594 が生成されます。 エラーに対して推奨される解決策は、変換のシーケンスです。

```cpp
// C2594.cpp
// compile with: /c
struct A{};
struct I1 : A {};
struct I2 : A {};
struct D : I1, I2 {};

A *f (D *p) {
   return (A*) (p);    // C2594

// try the following line instead
// return static_cast<A *>(static_cast<I1 *>(p));
}
```
