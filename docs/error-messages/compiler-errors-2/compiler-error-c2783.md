---
title: コンパイラエラー C2783
ms.date: 11/04/2016
f1_keywords:
- C2783
helpviewer_keywords:
- C2783
ms.assetid: 1ce94a11-bb8b-4be3-a222-f1f105da74b3
ms.openlocfilehash: adba87853bac764d4975d6b6fa9aa44940ced03c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739676"
---
# <a name="compiler-error-c2783"></a>コンパイラエラー C2783

' 宣言 ': ' identifier ' のテンプレート引数を推測できませんでした

コンパイラは、テンプレート引数を特定できません。 既定の引数を使用してテンプレート引数を推定することはできません。

次の例では、C2783 が生成されます。

```cpp
// C2783.cpp
template<typename T1, typename T2>
T1 f(T2) {
   return 248;
}

int main() {
   f(1);   // C2783
   // try the following line instead
   int i = f<int>(1);
}
```

C2783 は、ジェネリックを使用する場合にも発生する可能性があります。

```cpp
// C2783b.cpp
// compile with: /clr
using namespace System;
generic<typename T1, typename T2>
T1 gf(T2) {
   T1 t1 = safe_cast<T1>( Activator::CreateInstance(T1::typeid));
   return t1;
}

ref class MyClass{};

int main() {
   int i;
   i = gf(9);   // C2783

   // OK
   i = gf<int>(9);
}
```
