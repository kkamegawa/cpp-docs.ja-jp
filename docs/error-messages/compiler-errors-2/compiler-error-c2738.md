---
title: コンパイラエラー C2738
ms.date: 11/04/2016
f1_keywords:
- C2738
helpviewer_keywords:
- C2738
ms.assetid: 896b4640-1ee0-4cd8-9910-de3efa30006a
ms.openlocfilehash: cd83f0099e48b53db8055d8bc3282b672c1adc78
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759673"
---
# <a name="compiler-error-c2738"></a>コンパイラエラー C2738

' 宣言 ': があいまいであるか、' type ' のメンバーではありません。

関数が正しく宣言されていません。

次の例では、C2738 が生成されます。

```cpp
// C2738.cpp
struct A {
   template <class T> operator T*();
   // template <class T> operator T();
};

template <>
A::operator int() {   // C2738

// try the following line instead
// A::operator int*() {

// or use the commented member declaration

   return 0;
}
```
