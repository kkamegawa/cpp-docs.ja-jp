---
title: '方法: 定義してデリゲートを使用 (C +/cli CLI)'
ms.date: 11/04/2016
helpviewer_keywords:
- delegates
ms.assetid: 1cdf3420-89c1-47c0-b796-aa984020e0f8
ms.openlocfilehash: bcbf5bf978da5b6c13dd131e7a19975381bd97a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387371"
---
# <a name="how-to-define-and-use-delegates-ccli"></a>方法: 定義してデリゲートを使用 (C +/cli CLI)

この記事では、定義および c++ のデリゲートを使用する方法を示しています。/cli CLI。

.NET Framework には、デリゲートの数が用意されていますは場合によって新しいデリゲートを定義する必要があります。

次のコード例は、というデリゲートを定義します。`MyCallback`します。 イベント処理コード — この新しいデリゲートが発生したときに呼び出される関数 — の戻り値の型があります`void`かかると、<xref:System.String>参照。

Main 関数で定義されている静的メソッドを使用して`SomeClass`をインスタンス化する、`MyCallback`を委任します。 デリゲートは、デリゲート オブジェクトを文字列"single"の送信に示すように、この関数を呼び出す別の方法になります。 次に、追加のインスタンスの`MyCallback`リンクされ、デリゲート オブジェクトを 1 回の呼び出しによって実行されます。

```cpp
// use_delegate.cpp
// compile with: /clr
using namespace System;

ref class SomeClass
{
public:
   static void Func(String^ str)
   {
      Console::WriteLine("static SomeClass::Func - {0}", str);
   }
};

ref class OtherClass
{
public:
   OtherClass( Int32 n )
   {
      num = n;
   }

   void Method(String^ str)
   {
      Console::WriteLine("OtherClass::Method - {0}, num = {1}",
         str, num);
   }

   Int32 num;
};

delegate void MyCallback(String^ str);

int main( )
{
   MyCallback^ callback = gcnew MyCallback(SomeClass::Func);
   callback("single");

   callback += gcnew MyCallback(SomeClass::Func);

   OtherClass^ f = gcnew OtherClass(99);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   f = gcnew OtherClass(100);
   callback += gcnew MyCallback(f, &OtherClass::Method);

   callback("chained");

   return 0;
}
```

```Output
static SomeClass::Func - single
static SomeClass::Func - chained
static SomeClass::Func - chained
OtherClass::Method - chained, num = 99
OtherClass::Method - chained, num = 100
```

次のコード サンプルでは、値クラスのメンバーにデリゲートを関連付ける方法を示します。

```cpp
// mcppv2_del_mem_value_class.cpp
// compile with: /clr
using namespace System;
public delegate void MyDel();

value class A {
public:
   void func1() {
      Console::WriteLine("test");
   }
};

int main() {
   A a;
   A^ ah = a;
   MyDel^ f = gcnew MyDel(a, &A::func1);   // implicit box of a
   f();
   MyDel^ f2 = gcnew MyDel(ah, &A::func1);
   f2();
}
```

```Output
test
test
```

## <a name="how-to-compose-delegates"></a>デリゲートを作成する方法

使用することができます、"`-`"演算子で構成されるデリゲートからコンポーネント デリゲートを削除します。

```cpp
// mcppv2_compose_delegates.cpp
// compile with: /clr
using namespace System;

delegate void MyDelegate(String ^ s);

ref class MyClass {
public:
   static void Hello(String ^ s) {
      Console::WriteLine("Hello, {0}!", s);
   }

   static void Goodbye(String ^ s) {
      Console::WriteLine("  Goodbye, {0}!", s);
   }
};

int main() {

   MyDelegate ^ a = gcnew MyDelegate(MyClass::Hello);
   MyDelegate ^ b = gcnew MyDelegate(MyClass::Goodbye);
   MyDelegate ^ c = a + b;
   MyDelegate ^ d = c - a;

   Console::WriteLine("Invoking delegate a:");
   a("A");
   Console::WriteLine("Invoking delegate b:");
   b("B");
   Console::WriteLine("Invoking delegate c:");
   c("C");
   Console::WriteLine("Invoking delegate d:");
   d("D");
}
```

**出力**

```Output
Invoking delegate a:
Hello, A!
Invoking delegate b:
  Goodbye, B!
Invoking delegate c:
Hello, C!
  Goodbye, C!
Invoking delegate d:
  Goodbye, D!
```

## <a name="pass-a-delegate-to-a-native-function-that-expects-a-function-pointer"></a>デリゲートに渡す ^ を関数ポインターを要求するネイティブ関数

マネージ コンポーネントから呼び出せる関数を使用したネイティブ関数ポインター パラメーターをネイティブ関数から呼び出すことができますマネージ コンポーネントのデリゲートのメンバー関数は、します。

このサンプルでは、ネイティブ関数をエクスポートする .dll を作成します。

```cpp
// delegate_to_native_function.cpp
// compile with: /LD
#include < windows.h >
extern "C" {
   __declspec(dllexport)
   void nativeFunction(void (CALLBACK *mgdFunc)(const char* str)) {
      mgdFunc("Call to Managed Function");
   }
}
```

次の例では、.dll ファイルを使用し、関数ポインターを要求するネイティブ関数にデリゲートのハンドルを渡します。

```cpp
// delegate_to_native_function_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

delegate void Del(String ^s);
public ref class A {
public:
   void delMember(String ^s) {
      Console::WriteLine(s);
   }
};

[DllImportAttribute("delegate_to_native_function", CharSet=CharSet::Ansi)]
extern "C" void nativeFunction(Del ^d);

int main() {
   A ^a = gcnew A;
   Del ^d = gcnew Del(a, &A::delMember);
   nativeFunction(d);   // Call to native function
}
```

**出力**

```Output
Call to Managed Function
```

## <a name="to-associate-delegates-with-unmanaged-functions"></a>アンマネージ関数にデリゲートを関連付ける

ネイティブ関数にデリゲートを関連付けるには必要があります、マネージ型にネイティブ関数をラップし、を介して呼び出される関数宣言`PInvoke`します。

```cpp
// mcppv2_del_to_umnangd_func.cpp
// compile with: /clr
#pragma unmanaged
extern "C" void printf(const char*, ...);
class A {
public:
   static void func(char* s) {
      printf(s);
   }
};

#pragma managed
public delegate void func(char*);

ref class B {
   A* ap;

public:
   B(A* ap):ap(ap) {}
   void func(char* s) {
      ap->func(s);
   }
};

int main() {
   A* a = new A;
   B^ b = gcnew B(a);
   func^ f = gcnew func(b, &B::func);
   f("hello");
   delete a;
}
```

**出力**

```Output
hello
```

## <a name="to-use-unbound-delegates"></a>バインドされていないデリゲートを使用するには

バインドされていないデリゲートを使用すると、デリゲートが呼び出されたときに呼び出す関数に持つ型のインスタンスを渡します。

バインドされていないデリゲートは、コレクション内のオブジェクトを反復処理する場合に特に便利です: を使用して[ごとで](../dotnet/for-each-in.md)キーワード: 各インスタンスのメンバー関数を呼び出します。

宣言、インスタンス化する方法を次に示し、呼び出しがバインドされ、デリゲートをバインド解除されました。

|アクション|デリゲートをバインドします。|バインドされていないデリゲート|
|------------|---------------------|-----------------------|
|Declare|デリゲートのシグネチャは、デリゲートを通じて呼び出す関数のシグネチャと一致する必要があります。|デリゲートのシグネチャの最初のパラメーターの型は、`this`呼び出そうとするオブジェクト。<br /><br /> 最初のパラメーターの後に、デリゲートのシグネチャがデリゲートを通じて呼び出す関数のシグネチャと一致する必要があります。|
|インスタンスを作成します。|バインドされたデリゲートをインスタンス化するときは、インスタンス関数またはグローバルまたは静的メンバー関数を指定できます。<br /><br /> 最初のパラメーターはメンバー関数を呼び出す型のインスタンスをインスタンス関数を指定して、2 番目のパラメーターに呼び出す関数のアドレスになります。<br /><br /> グローバルまたは静的メンバー関数を呼び出す場合は、グローバル関数の名前または静的メンバー関数の名前を渡すだけです。|バインドされていないデリゲートをインスタンス化するときに呼び出す関数のアドレスを渡すだけです。|
|Call|バインドされたデリゲートを呼び出すときに、デリゲートのシグネチャに必要なパラメーターを渡すだけです。|バインドされた同じデリゲートが、最初のパラメーターは呼び出す関数を含むオブジェクトのインスタンスである必要がありますに注意してください。|

このサンプルでは、宣言、インスタンス化、およびバインドされていないデリゲートを呼び出す方法を示します。

```cpp
// unbound_delegates.cpp
// compile with: /clr
ref struct A {
   A(){}
   A(int i) : m_i(i) {}
   void Print(int i) { System::Console::WriteLine(m_i + i);}

private:
   int m_i;
};

value struct V {
   void Print() { System::Console::WriteLine(m_i);}
   int m_i;
};

delegate void Delegate1(A^, int i);
delegate void Delegate2(A%, int i);

delegate void Delegate3(interior_ptr<V>);
delegate void Delegate4(V%);

delegate void Delegate5(int i);
delegate void Delegate6();

int main() {
   A^ a1 = gcnew A(1);
   A% a2 = *gcnew A(2);

   Delegate1 ^ Unbound_Delegate1 = gcnew Delegate1(&A::Print);
   // delegate takes a handle
   Unbound_Delegate1(a1, 1);
   Unbound_Delegate1(%a2, 1);

   Delegate2 ^ Unbound_Delegate2 = gcnew Delegate2(&A::Print);
   // delegate takes a tracking reference (must deference the handle)
   Unbound_Delegate2(*a1, 1);
   Unbound_Delegate2(a2, 1);

   // instantiate a bound delegate to an instance member function
   Delegate5 ^ Bound_Del = gcnew Delegate5(a1, &A::Print);
   Bound_Del(1);

   // instantiate value types
   V v1 = {7};
   V v2 = {8};

   Delegate3 ^ Unbound_Delegate3 = gcnew Delegate3(&V::Print);
   Unbound_Delegate3(&v1);
   Unbound_Delegate3(&v2);

   Delegate4 ^ Unbound_Delegate4 = gcnew Delegate4(&V::Print);
   Unbound_Delegate4(v1);
   Unbound_Delegate4(v2);

   Delegate6 ^ Bound_Delegate3 = gcnew Delegate6(v1, &V::Print);
   Bound_Delegate3();
}
```

**出力**

```Output
2
3
2
3
2
7
8
7
8
7
```

次の例は、バインドされていないデリゲートを使用する方法を示します、[ごとで](../dotnet/for-each-in.md)コレクション内のオブジェクトを反復処理し、各インスタンスのメンバー関数の呼び出しのキーワード。

```cpp
// unbound_delegates_2.cpp
// compile with: /clr
using namespace System;

ref class RefClass {
   String^ _Str;

public:
   RefClass( String^ str ) : _Str( str ) {}
   void Print() { Console::Write( _Str ); }
};

delegate void PrintDelegate( RefClass^ );

int main() {
   PrintDelegate^ d = gcnew PrintDelegate( &RefClass::Print );

   array< RefClass^ >^ a = gcnew array<RefClass^>( 10 );

   for ( int i = 0; i < a->Length; ++i )
      a[i] = gcnew RefClass( i.ToString() );

   for each ( RefClass^ R in a )
      d( R );

   Console::WriteLine();
}
```

このサンプルでは、プロパティのアクセサー関数にはバインドされていないデリゲートを作成します。

```cpp
// unbound_delegates_3.cpp
// compile with: /clr
ref struct B {
   property int P1 {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }

private:
   int m_i;
};

delegate void DelBSet(B^, int);
delegate int DelBGet(B^);

int main() {
   B^ b = gcnew B;

   DelBSet^ delBSet = gcnew DelBSet(&B::P1::set);
   delBSet(b, 11);

   DelBGet^ delBGet = gcnew DelBGet(&B::P1::get);
   System::Console::WriteLine(delBGet(b));
}
```

**出力**

```Output
11
```

次の例では、1 つのインスタンスがバインドされている、1 つのインスタンスは、バインドが、マルチキャスト デリゲートを呼び出す方法を示します。

```cpp
// unbound_delegates_4.cpp
// compile with: /clr
ref class R {
public:
   R(int i) : m_i(i) {}

   void f(R ^ r) {
      System::Console::WriteLine("in f(R ^ r)");
   }

   void f() {
      System::Console::WriteLine("in f()");
   }

private:
   int m_i;
};

delegate void Del(R ^);

int main() {
   R ^r1 = gcnew R(11);
   R ^r2 = gcnew R(12);

   Del^ d = gcnew Del(r1, &R::f);
   d += gcnew Del(&R::f);
   d(r2);
};
```

**出力**

```Output
in f(R ^ r)
in f()
```

次の例では、作成し、バインドされていないジェネリック デリゲートを呼び出す方法を示します。

```cpp
// unbound_delegates_5.cpp
// compile with: /clr
ref struct R {
   R(int i) : m_i(i) {}

   int f(R ^) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

value struct V {
   int f(V%) { return 999; }
   int f() { return m_i + 5; }

   int m_i;
};

generic <typename T>
delegate int Del(T t);

generic <typename T>
delegate int DelV(T% t);

int main() {
   R^ hr = gcnew R(7);
   System::Console::WriteLine((gcnew Del<R^>(&R::f))(hr));

   V v;
   v.m_i = 9;
   System::Console::WriteLine((gcnew DelV<V >(&V::f))(v) );
}
```

**出力**

```Output
12
14
```

## <a name="see-also"></a>関連項目

[delegate (C++ コンポーネント拡張)](../extensions/delegate-cpp-component-extensions.md)
