---
title: コンパイラ エラー C2507
ms.date: 11/04/2016
f1_keywords:
- C2507
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
ms.openlocfilehash: 23433dccd7fc4f86c2e848359ac50c796fcccab0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746800"
---
# <a name="compiler-error-c2507"></a>コンパイラ エラー C2507

' identifier ': 基底クラスの仮想修飾子が多すぎます

クラスまたは構造体が `virtual` として宣言されています。 基底クラスのリストの各クラスに対して、1つの `virtual` 修飾子のみを表示できます。

次の例では、C2507 が生成されます。

```cpp
// C2507.cpp
// compile with: /c
class A {};
class B : virtual virtual public A {};   // C2507
class C : virtual public A {};   // OK
```
