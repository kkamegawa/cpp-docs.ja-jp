---
title: コンパイラ エラー C3867
ms.date: 11/04/2016
f1_keywords:
- C3867
helpviewer_keywords:
- C3867
ms.assetid: bc5de03f-e01a-4407-88c3-2c63f0016a1e
ms.openlocfilehash: 7e3f52b2b69058549cb8aa3e14d2a4b4048fc4e4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756852"
---
# <a name="compiler-error-c3867"></a>コンパイラ エラー C3867

' func ': 関数呼び出しに引数リストがありません。メンバーへのポインターを作成するには、' & func ' を使用します

メンバー関数をクラス名とアドレス演算子で修飾せずに、メンバー関数のアドレスを取得しようとしました。

このエラーは、Visual Studio 2005 に対して行われたコンパイラ準拠作業の結果として生成されることもあります。強化された pointer-to-member 準拠。 Visual Studio 2005 より前にコンパイルされたコードでは、C3867 が生成されるようになりました。

## <a name="example"></a>使用例

C3867 は、推奨されている解決方法を誤解して使用した場合にコンパイラで発生することがあります。 できる限り、最派生クラスを使用してください。

次の例では C3867 を生成し、その修正方法を示しています。

```cpp
// C3867_1.cpp
// compile with: /c
struct Base {
protected:
   void Test() {}
};

class Derived : public Base {
   virtual void Bar();
};

void Derived::Bar() {
   void (Base::*p1)() = Test;   // C3867
   &Derived::Test;   // OK
}
```

## <a name="example"></a>使用例

次の例では C3867 を生成し、その修正方法を示しています。

```cpp
// C3867_2.cpp
#include<stdio.h>

struct S {
   char *func() {
      return "message";
   }
};

class X {
public:
   void f() {}
};

int main() {
   X::f;   // C3867

   // OK
   X * myX = new X;
   myX->f();

   S s;
   printf_s("test %s", s.func);   // C3867
   printf_s("test %s", s.func());   // OK
}
```

## <a name="example"></a>使用例

次の例では C3867 を生成し、その修正方法を示しています。

```cpp
// C3867_3.cpp
class X {
public:
   void mf(){}
};

int main() {
   void (X::*pmf)() = X::mf;   // C3867

   // try the following line instead
   void (X::*pmf2)() = &X::mf;
}
```

## <a name="example"></a>使用例

次の例では C3867 が生成されます。

```cpp
// C3867_4.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b1;
      b1.p = f;   // C3867
   }
};
```

## <a name="example"></a>使用例

次の例では C3867 が生成されます。

```cpp
// C3867_5.cpp
// compile with: /EHsc
#include <iostream>

class Testpm {
public:
   void m_func1() {
      std::cout << m_num << "\tm_func1\n";
    }

   int m_num;
   typedef void (Testpm::*pmfn1)();
   void func(Testpm* p);
};

void Testpm::func(Testpm* p) {
   pmfn1 s = m_func1;   // C3867
   pmfn1 s2 = &Testpm::m_func1;   // OK
   (p->*s2)();
}

int main() {
   Testpm *pTestpm = new Testpm;
   pTestpm->m_num = 10;

   pTestpm->func(pTestpm);
}
```
