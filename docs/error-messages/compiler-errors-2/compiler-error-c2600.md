---
title: コンパイラエラー C2600
ms.date: 11/04/2016
f1_keywords:
- C2600
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
ms.openlocfilehash: b2d95460cadf03f9152599ef47ae703030326dd1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740742"
---
# <a name="compiler-error-c2600"></a>コンパイラエラー C2600

'関数' : コンパイラで生成された特殊メンバー関数を定義できません (クラスで最初に宣言されなければなりません)

コンス トラクターやデストラクターなどのメンバー関数は、クラスに対して定義する前に、そのクラスで宣言する必要があります。 クラスで宣言されていない場合は、既定のコンス トラクターとデストラクター (特殊なメンバー関数と呼ばれます) をコンパイラで生成できます。 ただし、クラスに一致する宣言がない状態で、これらの関数のいずれかを定義すると、コンパイラによって競合が検出されます。

このエラーを修正するには、クラス宣言で、クラス宣言の外側で定義した各メンバー関数を宣言します。

次の例では警告 C2600 が生成されます。

```cpp
// C2600.cpp
// compile with: /c
class C {};
C::~C() {}   // C2600

class D {
   D::~D();
};

D::~D() {}
```
