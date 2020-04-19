---
title: コンパイラ エラー C3860
ms.date: 11/04/2016
f1_keywords:
- C3860
helpviewer_keywords:
- C3860
ms.assetid: 1fb5110d-594e-4f1c-8773-888233af1313
ms.openlocfilehash: 38113ba9c75ab3e3e9b0ea058cb96e733a484f13
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757788"
---
# <a name="compiler-error-c3860"></a>コンパイラ エラー C3860

クラス型名の後にある型引数リストは、型パラメーターリストで使用されている順序でパラメーターを一覧表示する必要があります

ジェネリックまたはテンプレート引数リストの形式が正しくありません。

次の例では、C3860 が生成されます。

```cpp
// C3860.cpp
// compile with: /LD
template <class T1, class T2>
struct A {
   void f();
};

template <class T2, class T1>
void A<T1, T2>::f() {}   // C3860
```

解決方法:

```cpp
// C3860b.cpp
// compile with: /c
template <class T1, class T2>
struct A {
   void f();
};

template <class T2, class T1>
void A<T2, T1>::f() {}
```

C3860 は、ジェネリックを使用する場合にも発生する可能性があります。

```cpp
// C3860c.cpp
// compile with: /clr
generic<class T,class U>
ref struct GC {
   void f();
};

generic<class T, class U>
void GC<T,T>::f() {}   // C3860
```

解決方法:

```cpp
// C3860d.cpp
// compile with: /clr /c
generic<class T,class U>
ref struct GC {
   void f();
};

generic<class T, class U>
void GC<T,U>::f() {}
```
