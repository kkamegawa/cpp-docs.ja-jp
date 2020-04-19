---
title: '方法: Safe_cast を使用して、 C++/CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- safe_cast keyword [C++], upcasting
ms.assetid: 0fbc87d8-ecdf-4cd5-81f4-0d8cc18e2aff
ms.openlocfilehash: 66faadba9530bc7f3c12513277582e405e1b1b34
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389087"
---
# <a name="how-to-use-safecast-in-ccli"></a>方法: Safe_cast を使用して、 C++/CLI

この記事で safe_cast を使用する方法を示しています。 C++/CLI アプリケーション。 Safe_cast についてC++/CX を参照してください[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)します。

## <a name="upcasting"></a>キャスト

アップ キャストは、派生型からその基本クラスのいずれかにキャストします。 このキャストは、安全な明示的なキャスト表記は必要ありません。 次の例は、使用、アップ キャストを実行する方法を示します`safe_cast`とこれがないです。

```cpp
// safe_upcast.cpp
// compile with: /clr
using namespace System;
interface class A {
   void Test();
};

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test");
   }

   void Test2() {
      Console::WriteLine("in B::Test2");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test");
   };
};

int main() {
   C ^ c = gcnew C;

   // implicit upcast
   B ^ b = c;
   b->Test();
   b->Test2();

   // upcast with safe_cast
   b = nullptr;
   b = safe_cast<B^>(c);
   b->Test();
   b->Test2();
}
```

```Output
in C::Test
in B::Test2
in C::Test
in B::Test2
```

## <a name="downcasting"></a>ダウン キャスト

ダウン キャストは、基本クラスから基底クラスから派生したクラスへのキャストです。  ダウン キャストは実行時に指定されるオブジェクトが派生クラスのオブジェクトをアドレス指定実際に場合にのみ安全です。  異なり`static_cast`、`safe_cast`動的チェックを実行し、スロー<xref:System.InvalidCastException>場合は、変換は失敗します。

```cpp
// safe_downcast.cpp
// compile with: /clr
using namespace System;

interface class A { void Test(); };

ref struct B : public A {
   virtual void Test() {
      Console::WriteLine("in B::Test()");
   }

   void Test2() {
      Console::WriteLine("in B::Test2()");
   }
};

ref struct C : public B {
   virtual void Test() override {
      Console::WriteLine("in C::Test()");
   }
};

interface class I {};

value struct V : public I {};

int main() {
   A^ a = gcnew C();
   a->Test();
   B^ b = safe_cast<B^>(a);
   b->Test();
   b->Test2();

   V v;
   I^ i = v;   // i boxes V
   V^ refv = safe_cast<V^>(i);

   Object^ o = gcnew B;
   A^ a2= safe_cast<A^>(o);
}
```

```Output
in C::Test()
in C::Test()
in B::Test2()
```

## <a name="safecast-with-user-defined-conversions"></a>ユーザー定義の変換を含む safe_cast

次のサンプルを使用する方法を示しています。`safe_cast`をユーザー定義の変換を呼び出します。

```cpp
// safe_cast_udc.cpp
// compile with: /clr
using namespace System;
value struct V;

ref struct R {
   int x;
   R() {
      x = 1;
   }

   R(int argx) {
      x = argx;
   }

   static operator R::V^(R^ r);
};

value struct V {
   int x;
   static operator R^(V& v) {
      Console::WriteLine("in operator R^(V& v)");
      R^ r = gcnew R();
      r->x = v.x;
      return r;
   }

   V(int argx) {
      x = argx;
   }
};

   R::operator V^(R^ r) {
      Console::WriteLine("in operator V^(R^ r)");
      return gcnew V(r->x);
   }

int main() {
   bool fReturnVal = false;
   V v(2);
   R^ r = safe_cast<R^>(v);   // should invoke UDC
   V^ v2 = safe_cast<V^>(r);   // should invoke UDC
}
```

```Output
in operator R^(V& v
in operator V^(R^ r)
```

## <a name="safecast-and-boxing-operations"></a>safe_cast およびボックス化の操作

### <a name="boxing"></a>ボックス化

ボックス化は、コンパイラが挿入された、ユーザー定義の変換として定義されます。  したがって、使用できる`safe_cast`を CLR ヒープ上の値をボックス化します。

次の例では、シンプルでユーザー定義の値の型のボックス化を示します。  A`safe_cast`ボックスの値型の変数がネイティブ スタックにあるガベージ コレクション ヒープ上の変数に割り当てることがあります。

```cpp
// safe_cast_boxing.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct V : public I {
   int m_x;

   V(int i) : m_x(i) {}
};

int main() {
   // box a value type
   V v(100);
   I^ i = safe_cast<I^>(v);

   int x = 100;
   V^ refv = safe_cast<V^>(v);
   int^ refi = safe_cast<int^>(x);
}
```

次の例は、ボックス化が経由でユーザー定義の変換で優先順位を持つことを示しています、`safe_cast`操作。

```cpp
// safe_cast_boxing_2.cpp
// compile with: /clr
static bool fRetval = true;

interface struct I {};
value struct V : public I {
   int x;

   V(int argx) {
      x = argx;
   }

   static operator I^(V v) {
      fRetval = false;
      I^ pi = v;
      return pi;
   }
};

ref struct R {
   R() {}
   R(V^ pv) {}
};

int main() {
   V v(10);
   I^ pv = safe_cast<I^>(v);   // boxing will occur, not UDC "operator I^"
}
```

### <a name="unboxing"></a>ボックス化解除

ボックス化解除すると、コンパイラが挿入された、ユーザー定義の変換として定義されます。  したがって、使用できる`safe_cast`CLR ヒープ上の値をボックス化解除します。

ユーザー定義の変換は、ボックス化解除が、ボックス化とは異なりボックス化解除する必要があります明示的 — では、実行する必要があります、 `static_cast`、C スタイル キャスト、または`safe_cast`; ボックス化解除し、暗黙的に実行できません。

```cpp
// safe_cast_unboxing.cpp
// compile with: /clr
int main() {
   System::Object ^ o = 42;
   int x = safe_cast<int>(o);
}
```

次のサンプルは、値型とプリミティブ型をボックス化解除を示しています。

```cpp
// safe_cast_unboxing_2.cpp
// compile with: /clr
using namespace System;

interface struct I {};

value struct VI : public I {};

void test1() {
   Object^ o = 5;
   int x = safe_cast<Int32>(o);
}

value struct V {
   int x;
   String^ s;
};

void test2() {
   V localv;
   Object^ o = localv;
   V unboxv = safe_cast<V>(o);
}

void test3() {
   V localv;
   V^ o2 = localv;
   V unboxv2 = safe_cast<V>(o2);
}

void test4() {
   I^ refi = VI();
   VI vi  = safe_cast<VI>(refi);
}

int main() {
   test1();
   test2();
   test3();
   test4();
}
```

## <a name="safecast-and-generic-types"></a>safe_cast 型およびジェネリック型

次のサンプルを使用する方法を示しています。`safe_cast`ジェネリック型にキャストを実行します。

```cpp
// safe_cast_generic_types.cpp
// compile with: /clr
interface struct I {};

generic<class T> where T:I
ref struct Base {
   T t;
   void test1() {}
};

generic<class T> where T:I
ref struct Derived:public Base <T> {};

ref struct R:public I {};

typedef Base<R^> GBase_R;
typedef Derived<R^> GDerived_R;

int main() {
   GBase_R^ br = gcnew GDerived_R();
   GDerived_R^ dr = safe_cast<GDerived_R^>(br);
}
```

## <a name="see-also"></a>関連項目

[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)
