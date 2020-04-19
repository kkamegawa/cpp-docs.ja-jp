---
title: コンパイラ エラー C2884
ms.date: 11/04/2016
f1_keywords:
- C2884
helpviewer_keywords:
- C2884
ms.assetid: 8b4d43e3-3fb5-4360-86c8-de59d8736d4f
ms.openlocfilehash: d0e283c7cd6116655a56f8df67ab4eecf9923b68
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760942"
---
# <a name="compiler-error-c2884"></a>コンパイラ エラー C2884

' name ': using 宣言によって導入されたローカル関数 ' function ' と競合しています

関数を複数回定義しようとしました。 最初の定義はローカル定義です。 2つ目は、`using` 宣言を持つ名前空間のものです。

次の例では、C2884 が生成されます。

```cpp
// C2884.cpp
namespace A {
   void z(int);
}

void f() {
   void z(int);
   using A::z;   // C2884 z is already defined
}
```
