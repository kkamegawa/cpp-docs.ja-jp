---
title: ローカルに宣言された名前の名前解決
ms.date: 11/04/2016
ms.assetid: 743b88f3-de11-48f4-ae83-931449ea3886
ms.openlocfilehash: 91ed065a6c8aca6c7f740f0236cb13c8133fc96f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345916"
---
# <a name="name-resolution-for-locally-declared-names"></a>ローカルに宣言された名前の名前解決

テンプレートの名前自体は、テンプレート引数の有無に関係なく参照できます。 クラス テンプレートのスコープ内で、名前がテンプレートを示します。 テンプレートの特殊化または部分的特殊化のスコープ内で、名前は単独で特殊化または部分的特殊化を示します。 テンプレートのその他の特化または部分的な特化は、適切なテンプレート引数を使用して参照できます。

## <a name="example"></a>例

次のコードは、クラス テンプレートの名前 A が特殊化または部分的特殊化のスコープ内で異なる方法で解釈されることを示します。

```cpp
// template_name_resolution3.cpp
// compile with: /c
template <class T> class A {
   A* a1;   // A refers to A<T>
   A<int>* a2;  // A<int> refers to a specialization of A.
   A<T*>* a3;   // A<T*> refers to the partial specialization A<T*>.
};

template <class T> class A<T*> {
   A* a4; // A refers to A<T*>.
};

template<> class A<int> {
   A* a5; // A refers to A<int>.
};
```

## <a name="example"></a>例

テンプレート パラメーターと別のオブジェクト間で名前が競合するときは、テンプレート パラメーターを隠せる場合と隠せない場合があります。 次の規則は、優先度の決定に使用できます。

テンプレート パラメーターは、最初に表示されたポイントから、クラスまたは関数テンプレートの末尾までのスコープにあります。 名前がテンプレート引数リストまたは基底クラスのリストに再度表示された場合、同じ型を示します。 標準 C++ では、同じスコープ内でテンプレート パラメーターと同じ名前を他の名前として宣言することはできません。 Microsoft 拡張機能は、テンプレート パラメーターがテンプレートのスコープ内で再定義できるようにします。 次の例は、クラス テンプレートの基本仕様におけるテンプレート パラメーターの使用を示します。

```cpp
// template_name_resolution4.cpp
// compile with: /EHsc
template <class T>
class Base1 {};

template <class T>
class Derived1 : Base1<T> {};

int main() {
   // Derived1<int> d;
}
```

## <a name="example"></a>例

クラス テンプレートの外部でテンプレートのメンバー関数を定義するときは、異なるテンプレート パラメーター名を使用できます。 テンプレート メンバー関数定義で、テンプレート パラメーターに宣言とは異なる名前が使用され、定義で使用される名前が宣言の他のメンバーと競合する場合、テンプレート宣言のメンバーが優先されます。

```cpp
// template_name_resolution5.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T> class C {
public:
   struct Z {
      Z() { cout << "Z::Z()" << endl; }
   };
   void f();
};

template <class Z>
void C<Z>::f() {
   // Z refers to the struct Z, not to the template arg;
   // Therefore, the constructor for struct Z will be called.
   Z z;
}

int main() {
   C<int> c;
   c.f();
}
```

```Output
Z::Z()
```

## <a name="example"></a>例

テンプレートが宣言された名前空間の外部でテンプレート関数またはメンバー関数を定義するときは、テンプレート引数が名前空間の他のメンバーの名前より優先されます。

```cpp
// template_name_resolution6.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

namespace NS {
   void g() { cout << "NS::g" << endl; }

   template <class T> struct C {
      void f();
      void g() { cout << "C<T>::g" << endl; }
   };
};

template <class T>
void NS::C<T>::f() {
   g(); // C<T>::g, not NS::g
};

int main() {
   NS::C<int> c;
   c.f();
}
```

```Output
C<T>::g
```

## <a name="example"></a>例

テンプレート クラス宣言の外側の定義で、テンプレート クラスに、テンプレート引数に依存しない基底クラスがあり、その基底クラスまたはそのメンバーがテンプレート引数と同じ名前である場合、基底クラスまたはメンバー名にはテンプレート引数が表示されません。

```cpp
// template_name_resolution7.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct B {
   int i;
   void print() { cout << "Base" << endl; }
};

template <class T, int i> struct C : public B {
   void f();
};

template <class B, int i>
void C<B, i>::f() {
   B b;   // Base class b, not template argument.
   b.print();
   i = 1; // Set base class's i to 1.
}

int main() {
   C<int, 1> c;
   c.f();
   cout << c.i << endl;
}
```

```Output
Base
1
```

## <a name="see-also"></a>関連項目

[名前解決](../cpp/templates-and-name-resolution.md)