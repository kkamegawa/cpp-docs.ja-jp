---
title: コンパイラ エラー C3855
ms.date: 11/04/2016
f1_keywords:
- C3855
helpviewer_keywords:
- C3855
ms.assetid: ed90f8c0-4154-4243-b066-493913df5727
ms.openlocfilehash: 226f87ad428e9f005e36823834cedc2b3ee0b8c6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754824"
---
# <a name="compiler-error-c3855"></a>コンパイラ エラー C3855

' class ': 型パラメーター ' param ' は宣言と互換性がありません

コンパイラは、異なる名前を持つ非型テンプレートまたはジェネリックパラメーターを検出しました。 これは、テンプレートの特殊化の定義で指定されたテンプレートパラメーターがその宣言と互換性がない場合に発生する可能性があります。

次の例では、C3855 が生成されます。

```cpp
// C3855.cpp
template <int N>
struct C {
   void f();
};

template <char N>
void C<N>::f() {}   // C3855
```

解決方法:

```cpp
// C3855b.cpp
// compile with: /c
template <int N>
struct C {
   void f();
};

template <int N>
void C<N>::f() {}
```

C3855 は、ジェネリックを使用する場合にも発生する可能性があります。

```cpp
// C3855c.cpp
// compile with: /clr
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
generic <class V>
ref struct GC1<T>::GC2 { };   // C3855
```

解決方法:

```cpp
// C3855d.cpp
// compile with: /clr /c
generic <class T>
ref struct GC1 {
   generic <class U>
   ref struct GC2;
};

generic <class T>
generic <class U>
ref struct GC1<T>::GC2 { };
```
