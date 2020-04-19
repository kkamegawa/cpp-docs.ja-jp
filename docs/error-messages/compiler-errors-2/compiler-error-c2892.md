---
title: コンパイラ エラー C2892
ms.date: 11/04/2016
f1_keywords:
- C2892
helpviewer_keywords:
- C2892
ms.assetid: c22a5084-2f50-42c2-a56b-6dfe5442edc9
ms.openlocfilehash: f3868a44cf04d6c87092759ea473aa78aa0ad4c4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760890"
---
# <a name="compiler-error-c2892"></a>コンパイラ エラー C2892

ローカルクラスにはメンバーテンプレートを含めることはできません

テンプレート化されたメンバー関数は、関数で定義されているクラスでは無効です。

次の例では、C2892 が生成されます。

```cpp
// C2892.cpp
int main() {
   struct local {
      template<class T>   // C2892
      void f() {}
   };
}
```
