---
title: コンパイラ エラー C2910
ms.date: 11/04/2016
f1_keywords:
- C2910
helpviewer_keywords:
- C2910
ms.assetid: 09c50e6a-e099-42f6-8ed6-d80e292a7a36
ms.openlocfilehash: 0061a7171dd08440ec5d8c8b8cadb77303ff8f41
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761116"
---
# <a name="compiler-error-c2910"></a>コンパイラ エラー C2910

' function ': 明示的に特殊化することはできません。

コンパイラは、関数を2回明示的に特殊化しようとしました。

次の例では、C2910 が生成されます。

```cpp
// C2910.cpp
// compile with: /c
template <class T>
struct S;

template <> struct S<int> { void f() {} };
template <> void S<int>::f() {}   // C2910 delete this specialization
```

非テンプレートメンバーを明示的に特殊化しようとすると、C2910 を生成することもできます。 つまり、明示的に関数テンプレートを特殊化するだけで済みます。

次の例では、C2910 が生成されます。

```cpp
// C2910b.cpp
// compile with: /c
template <class T> struct A {
   A(T* p);
};

template <> struct A<void> {
   A(void* p);
};

template <class T>
inline A<T>::A(T* p) {}

template <> A<void>::A(void* p){}   // C2910
// try the following line instead
// A<void>::A(void* p){}
```

このエラーは、Visual Studio .NET 2003 で実行されたコンパイラ準拠作業の結果としても生成されます。

Visual Studio .NET 2003 と visual Studio .NET のバージョンの Visual C++studio でコードを有効にするには、`template <>`を削除します。

次の例では、C2910 が生成されます。

```cpp
// C2910c.cpp
// compile with: /c
template <class T> class A {
   void f();
};

template <> class A<int> {
   void f();
};

template <> void A<int>::f() {}   // C2910
// try the following line instead
// void A<int>::f(){}   // OK
```
