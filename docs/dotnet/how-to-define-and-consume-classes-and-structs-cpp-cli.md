---
title: '方法: クラスと構造体定義および使用 (C +/cli CLI)'
ms.date: 09/12/2018
helpviewer_keywords:
- structs [C++]
- classes [C++], instantiating
ms.assetid: 1c03cb0d-1459-4b5e-af65-97d6b3094fd7
ms.openlocfilehash: 5fe7d6876b094c84fe3d4cdbba417106edcca528
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447299"
---
# <a name="how-to-define-and-consume-classes-and-structs-ccli"></a>方法: クラスと構造体定義および使用 (C +/cli CLI)

この記事では、ユーザー定義の参照型と c++ の値の型定義および使用する方法を示しています。/cli CLI。

##  <a name="BKMK_Contents"></a> 目次

[オブジェクトのインスタンス化](#BKMK_Object_instantiation)

[暗黙的な抽象クラス](#BKMK_Implicitly_abstract_classes)

[型の可視性](#BKMK_Type_visibility)

[メンバーの可視性](#BKMK_Member_visibility)

[パブリックおよびプライベートなネイティブ クラス](#BKMK_Public_and_private_native_classes)

[静的コンストラクター](#BKMK_Static_constructors)

[このセマンティクスのポインター](#BKMK_Semantics_of_the_this_pointer)

[関数のシグネチャによる非表示にします。](#BKMK_Hide_by_signature_functions)

[コピー コンストラクター](#BKMK_Copy_constructors)

[デストラクターとファイナライザー](#BKMK_Destructors_and_finalizers)

##  <a name="BKMK_Object_instantiation"></a> オブジェクトのインスタンス化

マネージ ヒープ、スタックまたはネイティブ ヒープ、参照 (ref) 型をインスタンス化のみできます。 値の型は、スタックや、マネージ ヒープでインスタンス化することができます。

```cpp
// mcppv2_ref_class2.cpp
// compile with: /clr
ref class MyClass {
public:
   int i;

   // nested class
   ref class MyClass2 {
   public:
      int i;
   };

   // nested interface
   interface struct MyInterface {
      void f();
   };
};

ref class MyClass2 : public MyClass::MyInterface {
public:
   virtual void f() {
      System::Console::WriteLine("test");
   }
};

public value struct MyStruct {
   void f() {
      System::Console::WriteLine("test");
   }
};

int main() {
   // instantiate ref type on garbage-collected heap
   MyClass ^ p_MyClass = gcnew MyClass;
   p_MyClass -> i = 4;

   // instantiate value type on garbage-collected heap
   MyStruct ^ p_MyStruct = gcnew MyStruct;
   p_MyStruct -> f();

   // instantiate value type on the stack
   MyStruct p_MyStruct2;
   p_MyStruct2.f();

   // instantiate nested ref type on garbage-collected heap
   MyClass::MyClass2 ^ p_MyClass2 = gcnew MyClass::MyClass2;
   p_MyClass2 -> i = 5;
}
```

##  <a name="BKMK_Implicitly_abstract_classes"></a> 暗黙的な抽象クラス

*暗黙的な抽象クラス*インスタンス化することはできません。 クラスの基本型がインターフェイスで、そのクラスによって一部のインターフェイスのメンバー関数が実装されていない場合、そのクラスは暗黙的な抽象クラスです。

インターフェイスから派生したクラスからオブジェクトを構築できない場合は、それが暗黙的な抽象クラスであることが原因の可能性があります。 抽象クラスの詳細については、次を参照してください。[抽象](../extensions/abstract-cpp-component-extensions.md)します。

次のコード例は、`MyClass` が実装されていないため、`MyClass::func2` クラスをインスタンス化できないことを示しています。 例をコンパイルできるようにするには、`MyClass::func2` のコメントを解除します。

```cpp
// mcppv2_ref_class5.cpp
// compile with: /clr
interface struct MyInterface {
   void func1();
   void func2();
};

ref class MyClass : public MyInterface {
public:
   void func1(){}
   // void func2(){}
};

int main() {
   MyClass ^ h_MyClass = gcnew MyClass;   // C2259
                                          // To resolve, uncomment MyClass::func2.
}
```

##  <a name="BKMK_Type_visibility"></a> 型の可視性

共通言語ランタイム (CLR: Common Language Runtime) 型の可視性を制御できるため、アセンブリが参照された場合、アセンブリ内の型は、アセンブリ外で表示または非表示にできます。

`public` 含むソース ファイルに表示されることを示します、`#using`型を含むアセンブリのディレクティブ。  `private` 型が含むソース ファイルに表示されないことを示します、`#using`型を含むアセンブリのディレクティブ。 ただし、プライベート型は、同じアセンブリ内には表示されます。 既定では、クラスの可視性は `private` です。

Visual Studio 2005 の前に、既定では、ネイティブ型には、アセンブリ外にパブリック アクセシビリティが必要があります。 有効にする[コンパイラの警告 (レベル 1) C4692](../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)プライベート ネイティブ型が使用されている正しく確認できるようにします。 使用して、 [make_public](../preprocessor/make-public.md)プラグマで変更できないソース コード ファイルをネイティブ型にパブリック アクセシビリティをできるようにします。

詳細については、「[#using ディレクティブ](../preprocessor/hash-using-directive-cpp.md)」を参照してください。

次の例では、型を宣言してアクセシビリティを指定し、アセンブリ内でこれらの型にアクセスする方法を示しています。 もちろん、`#using` を使用して、プライベート型を含むアセンブリが参照された場合、そのアセンブリ内で表示されるのはパブリック型のみです。

```cpp
// type_visibility.cpp
// compile with: /clr
using namespace System;
// public type, visible inside and outside assembly
public ref struct Public_Class {
   void Test(){Console::WriteLine("in Public_Class");}
};

// private type, visible inside but not outside assembly
private ref struct Private_Class {
   void Test(){Console::WriteLine("in Private_Class");}
};

// default accessibility is private
ref class Private_Class_2 {
public:
   void Test(){Console::WriteLine("in Private_Class_2");}
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   a->Test();

   Private_Class ^ b = gcnew Private_Class;
   b->Test();

   Private_Class_2 ^ c = gcnew Private_Class_2;
   c->Test();
}
```

**出力**

```Output
in Public_Class
in Private_Class
in Private_Class_2
```

ここで、DLL としてビルドされるように前のサンプルを記述し直しましょう。

```cpp
// type_visibility_2.cpp
// compile with: /clr /LD
using namespace System;
// public type, visible inside and outside the assembly
public ref struct Public_Class {
   void Test(){Console::WriteLine("in Public_Class");}
};

// private type, visible inside but not outside the assembly
private ref struct Private_Class {
   void Test(){Console::WriteLine("in Private_Class");}
};

// by default, accessibility is private
ref class Private_Class_2 {
public:
   void Test(){Console::WriteLine("in Private_Class_2");}
};
```

次の例は、アセンブリ外で型にアクセスする方法を示しています。 このサンプルでは、クライアントは、前の例でビルドされたコンポーネントを実装しています。

```cpp
// type_visibility_3.cpp
// compile with: /clr
#using "type_visibility_2.dll"
int main() {
   Public_Class ^ a = gcnew Public_Class;
   a->Test();

   // private types not accessible outside the assembly
   // Private_Class ^ b = gcnew Private_Class;
   // Private_Class_2 ^ c = gcnew Private_Class_2;
}
```

**出力**

```Output
in Public_Class
```

##  <a name="BKMK_Member_visibility"></a> メンバーの可視性

アセンブリ外からパブリック クラスのメンバーにアクセスするのとは別に、同じアセンブリからそのメンバーにアクセスするには、アクセス指定子のペア `public`、`protected`、および `private` を使用します

次の表は、さまざまなアクセス指定子の効果を示しています。

|指定子|効果|
|---------------|------------|
|public|アセンブリの内部と外部の両方でメンバーにアクセスできます。  参照してください[パブリック](../cpp/public-cpp.md)詳細についてはします。|
|private|アセンブリの内部と外部の両方でメンバーにアクセスできません。  参照してください[プライベート](../cpp/private-cpp.md)詳細についてはします。|
|protected|アセンブリの内部と外部の両方で、派生型のメンバーにのみアクセスできます。  参照してください[保護](../cpp/protected-cpp.md)詳細についてはします。|
|internal|メンバーは、アセンブリ内でパブリック、プライベート アセンブリの外側です。  `internal` は状況依存のキーワードです。  詳細については、次を参照してください。[状況依存のキーワード](../extensions/context-sensitive-keywords-cpp-component-extensions.md)します。|
|パブリックの保護の - または - は保護されたパブリック|メンバーはアセンブリ内ではパブリックですが、アセンブリ外では保護されています。|
|秘密の保護の - または - は保護されたプライベート|メンバーはアセンブリ内では保護されていますが、アセンブリ外ではプライベートです。|

次の例は、さまざまなアクセシビリティで宣言されたメンバーを持つパブリック型と、アセンブリ内からこれらのメンバーへのアクセスを示しています。

```cpp
// compile with: /clr
using namespace System;
// public type, visible inside and outside the assembly
public ref class Public_Class {
public:
   void Public_Function(){System::Console::WriteLine("in Public_Function");}

private:
   void Private_Function(){System::Console::WriteLine("in Private_Function");}

protected:
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}

internal:
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}

protected public:
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}

public protected:
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}

private protected:
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}

protected private:
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}
};

// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Private_Function();
      Private_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   MyClass ^ b = gcnew MyClass;
   a->Public_Function();
   a->Protected_Public_Function();
   a->Public_Protected_Function();

   // accessible inside but not outside the assembly
   a->Internal_Function();

   // call protected functions
   b->Test();

   // not accessible inside or outside the assembly
   // a->Private_Function();
}
```

**出力**

```Output
in Public_Function
in Protected_Public_Function
in Public_Protected_Function
in Internal_Function
=======================
in function of derived class
in Protected_Function
in Protected_Private_Function
in Private_Protected_Function
exiting function of derived class
=======================
```

次は、前のサンプルを DLL としてビルドします。

```cpp
// compile with: /clr /LD
using namespace System;
// public type, visible inside and outside the assembly
public ref class Public_Class {
public:
   void Public_Function(){System::Console::WriteLine("in Public_Function");}

private:
   void Private_Function(){System::Console::WriteLine("in Private_Function");}

protected:
   void Protected_Function(){System::Console::WriteLine("in Protected_Function");}

internal:
   void Internal_Function(){System::Console::WriteLine("in Internal_Function");}

protected public:
   void Protected_Public_Function(){System::Console::WriteLine("in Protected_Public_Function");}

public protected:
   void Public_Protected_Function(){System::Console::WriteLine("in Public_Protected_Function");}

private protected:
   void Private_Protected_Function(){System::Console::WriteLine("in Private_Protected_Function");}

protected private:
   void Protected_Private_Function(){System::Console::WriteLine("in Protected_Private_Function");}
};

// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Private_Function();
      Private_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};
```

次の例では、前の例で作成されたコンポーネントを使用するため、アセンブリ外からメンバーにアクセスする方法を示しています。

```cpp
// compile with: /clr
#using "type_member_visibility_2.dll"
using namespace System;
// a derived type, calls protected functions
ref struct MyClass : public Public_Class {
   void Test() {
      Console::WriteLine("=======================");
      Console::WriteLine("in function of derived class");
      Protected_Function();
      Protected_Public_Function();
      Public_Protected_Function();
      Console::WriteLine("exiting function of derived class");
      Console::WriteLine("=======================");
   }
};

int main() {
   Public_Class ^ a = gcnew Public_Class;
   MyClass ^ b = gcnew MyClass;
   a->Public_Function();

   // call protected functions
   b->Test();

   // can't be called outside the assembly
   // a->Private_Function();
   // a->Internal_Function();
   // a->Protected_Private_Function();
   // a->Private_Protected_Function();
}
```

**出力**

```Output
in Public_Function
=======================
in function of derived class
in Protected_Function
in Protected_Public_Function
in Public_Protected_Function
exiting function of derived class
=======================
```

##  <a name="BKMK_Public_and_private_native_classes"></a> パブリックおよびプライベートなネイティブ クラス

ネイティブ型はマネージド型から参照できます。  たとえば、マネージド型の関数は、型がネイティブ構造体であるパラメーターを受け取ることができます。  マネージド型と関数がアセンブリ内でパブリックの場合は、ネイティブ型もパブリックである必要があります。

```cpp
// native type
public struct N {
   N(){}
   int i;
};
```

次に、ネイティブ型を使用するソース コード ファイルを作成します。

```cpp
// compile with: /clr /LD
#include "mcppv2_ref_class3.h"
// public managed type
public ref struct R {
   // public function that takes a native type
   void f(N nn) {}
};
```

次に、クライアントをコンパイルします。

```cpp
// compile with: /clr
#using "mcppv2_ref_class3.dll"

#include "mcppv2_ref_class3.h"

int main() {
   R ^r = gcnew R;
   N n;
   r->f(n);
}
```

##  <a name="BKMK_Static_constructors"></a> 静的コンストラクター

クラスや構造体などの CLR 型は、静的データ メンバーの初期化に使用できる静的コンストラクターを持つことができます。  静的コンストラクターが呼び出されるのは、型の静的メンバーが初めてアクセスされる前の 1 度だけです。

静的コンストラクターの後は、インスタンス コンストラクターが常に実行されています。

クラスに静的コンストラクターがあると、コンパイラはコンストラクターへの呼び出しをインライン展開できません。  クラスが値型で、静的コンストラクターがあり、インスタンス コンストラクターがないと、コンパイラはメンバー関数への呼び出しをインライン展開できません。  CLR は呼び出しをインライン展開できますが、コンパイラはできません。

静的コンストラクターは、CLR によってのみ呼び出されることが想定されているため、プライベート メンバー関数として定義します。

静的コンス トラクターの詳細については、次を参照してください。[方法。インターフェイス静的コンス トラクターの定義 (C +/cli CLI)](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)します。

```cpp
// compile with: /clr
using namespace System;

ref class MyClass {
private:
   static int i = 0;

   static MyClass() {
      Console::WriteLine("in static constructor");
      i = 9;
   }

public:
   static void Test() {
      i++;
      Console::WriteLine(i);
   }
};

int main() {
   MyClass::Test();
   MyClass::Test();
}
```

**出力**

```Output
in static constructor
10
11
```

##  <a name="BKMK_Semantics_of_the_this_pointer"></a> このセマンティクスのポインター

Visual C++ を使用して型を定義する場合、参照型の `this` ポインターは "ハンドル" 型です。 値型の `this` ポインターは "内部ポインター" 型です。

`this` ポインターのセマンティクスが異なることで、既定のインデクサーが呼び出されるときに予期しない動作が発生する場合があります。 次の例は、参照型と値型の両方で既定のインデクサーに適切にアクセスする方法を示しています。

詳細については、次のトピックを参照してください。

- [オブジェクト演算子 (^) へのハンドル](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md)

- [interior_ptr (C++/CLI)](../extensions/interior-ptr-cpp-cli.md)

```cpp
// compile with: /clr
using namespace System;

ref struct A {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }

   A() {
      // accessing default indexer
      Console::WriteLine("{0}", this[3.3]);
   }
};

value struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
   void Test() {
      // accessing default indexer
      Console::WriteLine("{0}", this->default[3.3]);
   }
};

int main() {
   A ^ mya = gcnew A();
   B ^ myb = gcnew B();
   myb->Test();
}
```

**出力**

```Output
10.89
10.89
```

##  <a name="BKMK_Hide_by_signature_functions"></a> 関数のシグネチャによる非表示にします。

標準 C++ では、基底クラスの関数は、派生クラスで同じ名前を持つ関数によって、その派生クラス関数に同じ数または種類のパラメーターがない場合でも非表示になります。 呼ばれる*名前によって隠ぺい*セマンティクスです。 参照型では、基底クラスの関数は、名前とパラメーター リストの両方が同じ場合に、派生クラスの関数によってのみ非表示にできます。 これと呼ばれます*シグネチャで隠ぺい*セマンティクスです。

クラスの関数すべてがメタデータで `hidebysig` としてマークされていると、そのクラスはシグネチャによる隠ぺいクラスと見なされます。 既定では、下に作成されるすべてのクラスによって **/clr**が`hidebysig`関数。 クラスに `hidebysig` 関数が含まれる場合、コンパイラが、直接基底クラスで名前によって関数を隠ぺいすることはありませんが、継承チェーンで名前による隠ぺいクラスが見つかると、名前による隠ぺい動作が続行されます。

シグネチャによる隠ぺいセマンティクスでは、関数がオブジェクトで呼び出されると、関数呼び出しを満たす関数を含む最派生クラスがコンパイラによって特定されます。 呼び出しを満たす関数がクラスに 1 つしかない場合は、その関数がコンパイラによって呼び出されます。 呼び出しを満たす関数がクラスに複数ある場合、呼び出される関数は、オーバーロードの解決規則によって決まります。 オーバー ロード規則の詳細については、次を参照してください。[関数のオーバー ロード](../cpp/function-overloading.md)します。

特定の関数呼び出しについては、基底クラスの関数のシグネチャの方が、派生クラスの関数よりも若干適していることがあるのですが、 派生クラスのオブジェクトで関数が明示的に呼び出されると、派生クラスの関数が呼び出されます。

戻り値は関数のシグネチャの一部と見なされないため、基底クラス関数が派生クラス関数と同じ名前を持ち、同じ数と種類の引数を受け取る場合、戻り値の型が異なっていても、その基底クラス関数は非表示になります。

次の例は、派生クラスの関数によって非表示にならない基底クラスの関数を示しています。

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   void Test() {
      Console::WriteLine("Base::Test");
   }
};

ref struct Derived : public Base {
   void Test(int i) {
      Console::WriteLine("Derived::Test");
   }
};

int main() {
   Derived ^ t = gcnew Derived;
   // Test() in the base class will not be hidden
   t->Test();
}
```

**出力**

```Output
Base::Test
```

次の例を示します MicrosoftC++コンパイラは、最派生クラスで関数を呼び出す-場合でも、1 つまたは複数のパラメーターと一致する変換が必要です: 関数呼び出しにより適合する基底クラスで関数を呼び出していません。

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   void Test2(Single d) {
      Console::WriteLine("Base::Test2");
   }
};

ref struct Derived : public Base {
   void Test2(Double f) {
      Console::WriteLine("Derived::Test2");
   }
};

int main() {
   Derived ^ t = gcnew Derived;
   // Base::Test2 is a better match, but the compiler
   // calls a function in the derived class if possible
   t->Test2(3.14f);
}
```

**出力**

```Output
Derived::Test2
```

次の例は、基底クラスのシグネチャが派生クラスと同じであっても、関数を非表示にできることを示しています。

```cpp
// compile with: /clr
using namespace System;
ref struct Base {
   int Test4() {
      Console::WriteLine("Base::Test4");
      return 9;
   }
};

ref struct Derived : public Base {
   char Test4() {
      Console::WriteLine("Derived::Test4");
      return 'a';
   }
};

int main() {
   Derived ^ t = gcnew Derived;

   // Base::Test4 is hidden
   int i = t->Test4();
   Console::WriteLine(i);
}
```

**出力**

```Output
Derived::Test4
97
```

##  <a name="BKMK_Copy_constructors"></a> コピー コンス トラクター

C++ 標準では、オブジェクトの移動時にコピー コンストラクターが呼び出されることを通知します。このため、オブジェクトの作成と破棄が同じアドレスで行われます。

ただし、 **/clr**コンパイルおよび MSIL 呼び出しのネイティブ関数がネイティブにコンパイルされた関数に使用されます: または 1 つ以上の — 値とコピー コンス トラクターやデストラクター、コピーなしネイティブ クラスにはここで渡されるコンス トラクターを呼び出すし、は異なるアドレスが作成された時に、オブジェクトが破棄されます。 これにより、クラスにそのクラス自身へのポインターが含まれる場合、またはコードがアドレスによってオブジェクトを追跡している場合に問題が発生する可能性があります。

詳細については、「[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)」を参照してください。

次の例は、コピー コンストラクターが生成されない場合を示しています。

```cpp
// compile with: /clr
#include<stdio.h>

struct S {
   int i;
   static int n;

   S() : i(n++) {
      printf_s("S object %d being constructed, this=%p\n", i, this);
   }

   S(S const& rhs) : i(n++) {
      printf_s("S object %d being copy constructed from S object "
               "%d, this=%p\n", i, rhs.i, this);
   }

   ~S() {
      printf_s("S object %d being destroyed, this=%p\n", i, this);
   }
};

int S::n = 0;

#pragma managed(push,off)
void f(S s1, S s2) {
   printf_s("in function f\n");
}
#pragma managed(pop)

int main() {
   S s;
   S t;
   f(s,t);
}
```

**出力**

```Output
S object 0 being constructed, this=0018F378
S object 1 being constructed, this=0018F37C
S object 2 being copy constructed from S object 1, this=0018F380
S object 3 being copy constructed from S object 0, this=0018F384
S object 4 being copy constructed from S object 2, this=0018F2E4
S object 2 being destroyed, this=0018F380
S object 5 being copy constructed from S object 3, this=0018F2E0
S object 3 being destroyed, this=0018F384
in function f
S object 5 being destroyed, this=0018F2E0
S object 4 being destroyed, this=0018F2E4
S object 1 being destroyed, this=0018F37C
S object 0 being destroyed, this=0018F378
```

##  <a name="BKMK_Destructors_and_finalizers"></a> デストラクターとファイナライザー

参照型のデストラクターでは、リソースの確定的なクリーンアップを実行します。 ファイナライザーでは、アンマネージ リソースがクリーンアップされます。また、ファイナライザーはデストラクターが確定的に呼び出すか、ガベージ コレクターが非確定的に呼び出すことができます。 標準 C++ のデストラクターについては、次を参照してください。[デストラクター](../cpp/destructors-cpp.md)します。

```cpp
class classname {
   ~classname() {}   // destructor
   ! classname() {}   // finalizer
};
```

Visual C++ マネージド クラスのデストラクターの動作は、C++ のマネージド拡張機能とは異なります。 この変更の詳細については、次を参照してください。[のデストラクターのセマンティクスの変更](../dotnet/changes-in-destructor-semantics.md)します。

CLR ガベージ コレクターは、不要になった未使用マネージド オブジェクトを削除し、そのメモリを解放します。 ただし、型によって使用されているリソースの解放方法を、ガベージ コレクターが把握していないことがあります。 これらのリソースは、アンマネージ リソース (ネイティブ ファイル ハンドルなど) と呼ばれます。 アンマネージ リソースはすべて、ファイナライザーで解放することをお勧めします。 ガベージ コレクターでは、マネージド リソースが非確定的に解放されるため、ファイナライザーでマネージド リソースを参照するのは安全ではありません。ガベージ コレクターは、そのマネージド リソースを既にクリーンアップしている可能性があるためです。

Visual C++ ファイナライザーは、<xref:System.Object.Finalize%2A> メソッドと同じではありません  (CLR ドキュメントでは、ファイナライザーと <xref:System.Object.Finalize%2A> メソッドが同じ意味で使用されます)。 <xref:System.Object.Finalize%2A> メソッドはガベージ コレクターによって呼び出され、これにより、クラス継承チェーンの各ファイナライザーが開始されます。 Visual C++ デストラクターとは異なり、派生クラスのファイナライザーの呼び出しにより、コンパイラがすべての基底クラスのファイナライザーを開始することはありません。

MicrosoftC++コンパイラは、リソースの確定的解放をサポートしている、実装しようとしないでください、<xref:System.IDisposable.Dispose%2A>または<xref:System.Object.Finalize%2A>メソッド。 ただし、これらのメソッドに慣れている方を対象に、ここでは、Visual C++ ファイナライザーとそのファイナライザーを呼び出すデストラクターが、どのように <xref:System.IDisposable.Dispose%2A> パターンに割り当てられるかを示します。

```cpp
// Visual C++ code
ref class T {
   ~T() { this->!T(); }   // destructor calls finalizer
   !T() {}   // finalizer
};

// equivalent to the Dispose pattern
void Dispose(bool disposing) {
   if (disposing) {
      ~T();
   } else {
      !T();
   }
}
```

マネージド型が、確定的に解放することが望ましいマネージド リソースを使用しており、オブジェクトが不要になった後のある時点においてガベージ コレクターで非確定的に解放したくないこともあります。 リソースを確定的に解放すると、パフォーマンスが大幅に向上する可能性があります。

MicrosoftC++コンパイラ確定的にオブジェクトをクリーンアップするデストラクターの定義を有効にします。 デストラクターを使用して、確定的に解放するすべてのリソースを解放します。  ファイナライザーが存在する場合は、デストラクターからそのファイナライザーを呼び出して、コードの重複を回避します。

```cpp
// compile with: /clr /c
ref struct A {
   // destructor cleans up all resources
   ~A() {
      // clean up code to release managed resource
      // ...
      // to avoid code duplication,
      // call finalizer to release unmanaged resources
      this->!A();
   }

   // finalizer cleans up unmanaged resources
   // destructor or garbage collector will
   // clean up managed resources
   !A() {
      // clean up code to release unmanaged resources
      // ...
   }
};
```

型を使用するコードによってデストラクターが呼び出されない場合、ガベージ コレクターは、最終的に、すべてのマネージド リソースを解放します。

デストラクターが存在するからといって、ファイナライザーが存在するとは限りません。 ただし、ファイナライザーが存在する場合は、デストラクターを定義し、そのデストラクターからファイナライザーを呼び出す必要があることを意味します。 これにより、アンマネージ リソースが確定的に解放されます。

デストラクターを呼び出すと、<xref:System.GC.SuppressFinalize%2A> を使用して、オブジェクトの終了処理が回避されます。 デストラクターが呼び出されない場合は、ガベージ コレクターによって最終的に型のファイナライザーが呼び出されます。

デストラクターを呼び出すことでオブジェクトのリソースを確定的にクリーンアップすると、CLR で非確定的にオブジェクトを終了できるようにするのに比べてパフォーマンスが向上します。

Visual C で記述されコンパイルを使用しているコードを **/clr**場合、型のデストラクターが実行されます。

- スタック セマンティクスを使用して作成されたオブジェクトがスコープから外れる。 詳細については、次を参照してください。[参照型の C++ スタック セマンティクス](../dotnet/cpp-stack-semantics-for-reference-types.md)します。

- オブジェクトの作成時に例外がスローされる。

- オブジェクトが、デストラクターが実行されているオブジェクトのメンバーである。

- 呼び出す、[削除](../cpp/delete-operator-cpp.md)ハンドル演算子 ([オブジェクト演算子 (^) へのハンドル](../extensions/handle-to-object-operator-hat-cpp-component-extensions.md))。

- 明示的にデストラクターを呼び出す。

クライアントによって使用されている型が他の言語で記述された場合、デストラクターは次のように呼び出されます。

- <xref:System.IDisposable.Dispose%2A> への呼び出しで。

- 型の `Dispose(void)` への呼び出しで。

- 型が C# `using` ステートメントのスコープ外になる場合。

(参照型の場合は、スタック セマンティクスを使用しない)、マネージ ヒープ上の参照型のオブジェクトを作成する場合は、使用[、try-finally](../cpp/try-finally-statement.md)こと例外は、デストラクターが実行されないことを確認するための構文。

```cpp
// compile with: /clr
ref struct A {
   ~A() {}
};

int main() {
   A ^ MyA = gcnew A;
   try {
      // use MyA
   }
   finally {
      delete MyA;
   }
}
```

型にデストラクターがある場合は、`Dispose` を実装する <xref:System.IDisposable> メソッドがコンパイラによって生成されます。 型が Visual C++ で記述されており、他の言語で実行されるデストラクターがその型にある場合は、その型で `IDisposable::Dispose` を呼び出すと、その型のデストラクターが呼び出されます。 型が Visual C++ クライアントで実行されている場合は、`Dispose` を直接呼び出すことはできません。代わりに、`delete` 演算子を使用して、デストラクターを呼び出します。

型にファイナライザーがある場合は、`Finalize(void)` をオーバーライドする <xref:System.Object.Finalize%2A> メソッドがコンパイラによって生成されます。

型にデストラクターまたはファイナライザーのいずれかがある場合は、デザイン パターンに従って `Dispose(bool)` メソッドが生成されます  (詳しくは、次を参照してください。 [Dispose パターン](/dotnet/standard/design-guidelines/dispose-pattern))。 `Dispose(bool)` を Visual C++ で明示的に作成したり呼び出したりすることはできません。

デザイン パターンに準拠する基底クラスが型にある場合、すべての基底クラスのデストラクターは、派生クラスのデストラクターが呼び出されるときに呼び出されます  (型が Visual C++ で記述されている場合は、このパターンが型で実装されることがコンパイラによって保証されます)。つまり、C++ 標準で指定されているように、参照クラスのデストラクターが基底クラスとメンバーに連結され、最初に、クラスのデストラクターが実行されます。次に、メンバーのデストラクターが、そのデストラクターが構築された順とは逆の順序で実行され、最後に、基底クラスのデストラクターが、そのデストラクターが構築された順とは逆の順序で実行されます。

デストラクターとファイナライザーは、値型またはインターフェイス内では許可されません。

ファイナライザーは、参照型でのみ定義または宣言できます。 コンストラクターおよびデストラクターと同様、ファイナライザーには戻り値の型がありません。

オブジェクトのファイナライザーの実行後に、すべての基底クラスのファイナライザーも呼び出されます。最初に呼び出されるのは最小限の派生型です。 データ メンバーのファイナライザーに、クラスのファイナライザーが自動的に連結することはありません。

ファイナライザーによってマネージド型のネイティブ ポインターが削除された場合は、ネイティブ ポインターへの参照、またはネイティブ ポインターを介した参照の収集が途中で終了していないことを確認する必要があります。<xref:System.GC.KeepAlive%2A> を使用する代わりに、マネージド型でデストラクターを呼び出してください。

コンパイル時に、型にファイナライザーまたはデストラクターがあるかどうかを検出できます。 詳細については、次を参照してください。[型の特徴のコンパイラ サポート](../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)します。

次の例は 2 つの型を示しています。1 つにはアンマネージド リソースが、もう 1 つには確定的に解放されたマネージド リソースが含まれます。

```cpp
// compile with: /clr
#include <vcclr.h>
#include <stdio.h>
using namespace System;
using namespace System::IO;

ref class SystemFileWriter {
   FileStream ^ file;
   array<Byte> ^ arr;
   int bufLen;

public:
   SystemFileWriter(String ^ name) : file(File::Open(name, FileMode::Append)),
                                     arr(gcnew array<Byte>(1024)) {}

   void Flush() {
      file->Write(arr, 0, bufLen);
      bufLen = 0;
   }

   ~SystemFileWriter() {
      Flush();
      delete file;
   }
};

ref class CRTFileWriter {
   FILE * file;
   array<Byte> ^ arr;
   int bufLen;

   static FILE * getFile(String ^ n) {
      pin_ptr<const wchar_t> name = PtrToStringChars(n);
      FILE * ret = 0;
      _wfopen_s(&ret, name, L"ab");
      return ret;
   }

public:
   CRTFileWriter(String ^ name) : file(getFile(name)), arr(gcnew array<Byte>(1024) ) {}

   void Flush() {
      pin_ptr<Byte> buf = &arr[0];
      fwrite(buf, 1, bufLen, file);
      bufLen = 0;
   }

   ~CRTFileWriter() {
      this->!CRTFileWriter();
   }

   !CRTFileWriter() {
      Flush();
      fclose(file);
   }
};

int main() {
   SystemFileWriter w("systest.txt");
   CRTFileWriter ^ w2 = gcnew CRTFileWriter("crttest.txt");
}
```

## <a name="see-also"></a>関連項目

[クラスと構造体](../extensions/classes-and-structs-cpp-component-extensions.md)<br/>
[クラスと構造体](../extensions/classes-and-structs-cpp-component-extensions.md)
