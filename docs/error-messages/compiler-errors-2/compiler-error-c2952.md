---
title: コンパイラ エラー C2952
ms.date: 11/04/2016
f1_keywords:
- C2952
helpviewer_keywords:
- C2952
ms.assetid: a40e18a2-d02c-4511-854f-6c6fd6789a1a
ms.openlocfilehash: 9a76fc1718941ec5043f14064fa8c2609829ede3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755968"
---
# <a name="compiler-error-c2952"></a>コンパイラ エラー C2952

'declaration': 型宣言にテンプレート パラメーター リストがありません

テンプレート宣言の形式が間違っています。

次の例では C2952 が生成されます。

```cpp
// C2952.cpp
// compile with: /c
template <class T>
struct S {
   template <class T1>
   struct S1 {
      void f();
   };
};

template <class T> void S<T>::S1<T>::f() {}   // C2952

// OK
template <class T>
template <class T1>
void S<T>::S1<T1>::f() {}
```

C2952 は、ジェネリックを使用しているときも発生することがあります。

```cpp
// C2952b.cpp
// compile with: /clr /c
generic <class T>
ref struct GC {
   generic <class T1>
   ref struct GC1 {
      void f();
   };
};

generic <class T> void GC<T>::GC1<T>::f() {}   // C2952

// OK
generic <class T>
generic <class T1>
void GC<T>::GC1<T1>::f() {}
```
