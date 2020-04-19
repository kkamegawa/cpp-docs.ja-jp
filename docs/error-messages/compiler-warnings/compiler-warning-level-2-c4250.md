---
title: コンパイラの警告 (レベル 2) C4250
ms.date: 11/04/2016
f1_keywords:
- C4250
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
ms.openlocfilehash: 03826f10659cbdf6035cd4dedebecca3e3302e3a
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052115"
---
# <a name="compiler-warning-level-2-c4250"></a>コンパイラの警告 (レベル 2) C4250

' class1 ': 優先順位を使用して ' class2:: member ' を継承します

2つ以上のメンバーが同じ名前を持っています。 このメンバーを格納している他のクラスの基底クラスであるため、`class2` 内の1つのが継承されます。

C4250 を抑制するには、 [warning](../../preprocessor/warning.md)プラグマを使用します。

仮想基底クラスは複数の派生クラス間で共有されるため、派生クラスの名前は基底クラスの名前の方が優先されます。 たとえば、次のクラス階層については、ダイヤモンド内で継承される func の定義が2つあります。弱いクラスを介して vbc.exe:: func () インスタンス、および最も優先順位の高いクラスを使用して、最も優先順位の高い:: func () です。 ダイヤモンドクラスオブジェクトを介した func () の修飾されていない呼び出しでは、常に、プロセッサ:: func () インスタンスが呼び出されます。  Weak クラスが func () のインスタンスを導入する場合、どちらの定義も優位ではなく、呼び出しにあいまいなフラグが設定されます。

```cpp
// C4250.cpp
// compile with: /c /W2
#include <stdio.h>
struct vbc {
   virtual void func() { printf("vbc::func\n"); }
};

struct weak : public virtual vbc {};

struct dominant : public virtual vbc {
   void func() { printf("dominant::func\n"); }
};

struct diamond : public weak, public dominant {};

int main() {
   diamond d;
   d.func();   // C4250
}
```

## <a name="example"></a>例

次の例では、C4250 が生成されます。

```cpp
// C4250_b.cpp
// compile with: /W2 /EHsc
#include <iostream>
using namespace std;
class A {
public:
   virtual operator int () {
      return 2;
   }
};

class B : virtual public A {
public:
   virtual operator int () {
      return 3;
   }
};

class C : virtual public A {};

class E : public B, public C {};   // C4250

int main() {
   E eObject;
   cout << eObject.operator int() << endl;
}
```

## <a name="example"></a>例

このサンプルでは、より複雑な状況を示します。 次の例では、C4250 が生成されます。

```cpp
// C4250_c.cpp
// compile with: /W2 /EHsc
#include <iostream>
using namespace std;

class V {
public:
   virtual int f() {
      return 1024;
   }
};

class B : virtual public V {
public:
   int b() {
      return f(); // B::b() calls V::f()
   }
};

class M : virtual public V {
public:
   int f() {
      return 7;
   }
};

// because of dominance, f() is M::f() inside D,
// changing the meaning of B::b's f() call inside a D
class D : public B, public M {};   // C4250

int main() {
   D d;
   cout << "value is: " << d.b();   // invokes M::f()
}
```