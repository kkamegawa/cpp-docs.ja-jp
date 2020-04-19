---
title: コンパイラ エラー C3918
ms.date: 11/04/2016
f1_keywords:
- C3918
helpviewer_keywords:
- C3918
ms.assetid: a8b3a90a-3fe1-4244-a5ff-a31cdae97d98
ms.openlocfilehash: ff2b59338c707767fa1d3c382feaa1bfcdf29ce2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758490"
---
# <a name="compiler-error-c3918"></a>コンパイラ エラー C3918

使用するには、' member ' がデータメンバーである必要があります

C3918 は、イベントに関連するいくつかの理由で発生する可能性があります。

## <a name="example"></a>使用例

C3918 は、現在のコンテキストでクラスメンバーが必要であるために発生する可能性があります。 次の例では、C3918 が生成されます。

```cpp
// C3918.cpp
// compile with: /clr /c
public ref class C {
public:
   System::Object ^ o;
   delegate void Del();

   event Del^ MyEvent {
      void add(Del^ev) {
         if ( MyEvent != nullptr) {}   // C3918
         if ( o != nullptr) {}   // OK
   }
   void remove(Del^){}
   }
};
```

## <a name="example"></a>使用例

また、C3918 は、単純なイベントを null に対してチェックしようとした場合にも発生します (イベント名は、イベントのバッキングストアデリゲートへの直接アクセスを提供しなくなります)。

次の例では、C3918 が生成されます。

```cpp
// C3918_2.cpp
// compile with: /clr /c
using namespace System;
public delegate int MyDel(int);

interface struct IEFace {
   event MyDel ^ E;
};

ref struct EventSource : public IEFace {
   virtual event MyDel ^ E;
   void Fire_E(int i) {
      if (E)   // C3918
         E(i);
   }
};
```

## <a name="example"></a>使用例

C3918 は、誤ってイベントをサブスクライブしている場合にも発生する可能性があります。 次の例では、C3918 が生成されます。

```cpp
// C3918_3.cpp
// compile with: /clr /c
using namespace System;

public delegate void del();

public ref class A {
public:
   event del^ e {
      void add(del ^handler ) {
         d += handler;
      }

      void remove(del ^handler) {
         d -= handler;
      }

      void raise() {
         d();
      }
   }

   del^ d;
   void f() {}

   A() {
      e = gcnew del(this, &A::f);   // C3918
      // try the following line instead
      // e += gcnew del(this, &A::f);
      e();
   }
};

int main() {
   A a;
}
```
