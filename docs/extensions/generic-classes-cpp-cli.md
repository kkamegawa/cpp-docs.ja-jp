---
title: ジェネリック クラス (C++/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- classes [C++], generic
- generic classes [C++], about generic classes
- data types [C++], generic
- generic classes
- generics [C++], declaring generic classes
ms.assetid: 0beb99e1-1ec4-4fee-9836-ce9657d67a3a
ms.openlocfilehash: 71850807f6332f31195ef9bafbd9468f48cb6fb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516387"
---
# <a name="generic-classes-ccli"></a>ジェネリック クラス (C++/CLI)

ジェネリック クラスは、次の構文を使用して宣言されます。

## <a name="syntax"></a>構文

```cpp
[attributes]
generic <class-key type-parameter-identifier(s)>
[constraint-clauses]
[accessibility-modifiers] ref class identifier  [modifiers]
[: base-list]
{
class-body
} [declarators] [;]
```

## <a name="remarks"></a>解説

上記の構文では、次の用語が使用されています。

*属性*<br/>
(省略可能) 追加の宣言情報。 属性と属性クラスについては、「属性」を参照してください。

*class-key*<br/>
**class** または **typename** のいずれか。

*type-parameter-identifier(s)* 。型パラメーターの名前を指定する識別子のコンマ区切りの一覧。

*constraint-clauses*<br/>
型パラメーターの制約を指定する **where** 句の一覧 (コンマ区切りではありません)。 次の書式を使用します。

> **where** *type-parameter-identifier* **:** *constraint-list*  **...**

*constraint-list*<br/>
*class-or-interface*[`,` *...* ]

*accessibility-modifiers*<br/>
ジェネリック クラスのアクセシビリティ修飾子。 Windows ランタイムでは、許可される唯一の修飾子は **private** です。 共通言語ランタイムでは、許可される修飾子は **private** と **public** です。

*identifier*<br/>
ジェネリック クラスの名前。任意の有効な C++ 識別子です。

*modifiers*<br/>
(省略可能) 許可される修飾子は **sealed** と **abstract** です。

*base-list*<br/>
1 つの基底クラスと、実装されるすべてのインターフェイスを含む、コンマ区切りの一覧。

*class-body*<br/>
フィールド、メンバー関数などを含む、クラスの本文。

*declarators*<br/>
この型の任意の変数の宣言。 例: `^`*identifier*[`,` ...]

次のようなジェネリック クラスを宣言できます (**typename** の代わりに **class** キーワードを使用できることに注意してください)。 この例では、`ItemType`、`KeyType`、および `ValueType` は、型の指定場所では不明な型です。 `HashTable<int, int>` は、ジェネリック型 `HashTable<KeyType, ValueType>` の構築型です。 1 つのジェネリック型から、多数の異なる構築型を構築できます。 ジェネリック クラスから構築された構築型は、他の ref クラス型のように扱われます。

```cpp
// generic_classes_1.cpp
// compile with: /clr
using namespace System;
generic <typename ItemType>
ref struct Stack {
   // ItemType may be used as a type here
   void Add(ItemType item) {}
};

generic <typename KeyType, typename ValueType>
ref class HashTable {};

// The keyword class may be used instead of typename:
generic <class ListItem>
ref class List {};

int main() {
   HashTable<int, Decimal>^ g1 = gcnew HashTable<int, Decimal>();
}
```

ジェネリック型引数として、両方の値型 (**int** や **double** などの組み込み型、またはユーザー定義の値型) と参照型を使用できます。 ジェネリック定義内の構文は、どちらでも同じです。 構文上、不明な型は、参照型であるかのように扱われます。 ただし、ランタイムは、実際に使用される型が値型であるかどうかを判断し、メンバーに直接アクセスするために生成される適切なコードに置換できます。 ジェネリック型引数として使用される値型はボックス化されないため、ボックス化に関連するパフォーマンスの低下は発生しません。 ジェネリックの本文内で使用される構文では、`.` ではなく、`T^` と `->` にする必要があります。 型パラメーターでの [ref new、gcnew](ref-new-gcnew-cpp-component-extensions.md) の使用は、値引数が値型の場合は、ランタイムによって、値型の単純な作成であると適切に解釈されます。

型パラメーターで使用できる型に対して、[ジェネリック型パラメーターの制約 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)があるジェネリック クラスを宣言することもできます。 次の例では、`ItemType` で使用される任意の型で `IItem` インターフェイスを実装する必要があります。 たとえば `IItem` を実装しない **int** を使用しようとすると、型引数が制約を満たしていないという理由でコンパイル時エラーが発生します。

```cpp
// generic_classes_2.cpp
// compile with: /clr /c
interface class IItem {};
generic <class ItemType>
where ItemType : IItem
ref class Stack {};
```

同じ名前空間のジェネリック クラスは、型パラメーターの数または型を変更するだけではオーバーロードできません。 ただし、各クラスが別の名前空間にある場合はオーバーロードできます。 たとえば、名前空間 `A` と `B` にある次の 2 つのクラス (`MyClass` と `MyClass<ItemType>`) について考えます。 この 2 つのクラスは、3 番目の名前空間 C 内でオーバーロードできます。

```cpp
// generic_classes_3.cpp
// compile with: /clr /c
namespace A {
   ref class MyClass {};
}

namespace B {
   generic <typename ItemType>
   ref class MyClass2 { };
}

namespace C {
   using namespace A;
   using namespace B;

   ref class Test {
      static void F() {
         MyClass^ m1 = gcnew MyClass();   // OK
         MyClass2<int>^ m2 = gcnew MyClass2<int>();   // OK
      }
   };
}
```

基底クラスと基底インターフェイスを型パラメーターにすることはできません。 ただし、基底クラスでは、次の例のように、引数として型パラメーターを含めることができます。

```cpp
// generic_classes_4.cpp
// compile with: /clr /c
generic <typename ItemType>
interface class IInterface {};

generic <typename ItemType>
ref class MyClass : IInterface<ItemType> {};
```

コンストラクターとデストラクターは、オブジェクト インスタンスごとに (通常どおりに) 1 回実行されます。静的コンストラクターは、構築型ごとに 1 回実行されます。

## <a name="fields-in-generic-classes"></a>ジェネリック クラスのフィールド

このセクションでは、ジェネリック クラスのインスタンスと静的フィールドの使用を示します。

### <a name="instance-variables"></a>インスタンス変数

ジェネリック クラスのインスタンス変数は、外側のクラスからの型と任意の型パラメーターを含む変数初期化子を持つことができます。

## <a name="example"></a>例

次の例では、適切な型引数 (**int**、**double**、および **string**) を使用して、ジェネリック クラス MyClass\<ItemType> の 3 つの異なるインスタンスが作成されます。

```cpp
// generics_instance_fields1.cpp
// compile with: /clr
// Instance fields on generic classes
using namespace System;

generic <typename ItemType>
ref class MyClass {
// Field of the type ItemType:
public :
   ItemType field1;
   // Constructor using a parameter of the type ItemType:
   MyClass(ItemType p) {
   field1 = p;
   }
};

int main() {
   // Instantiate an instance with an integer field:
   MyClass<int>^ myObj1 = gcnew MyClass<int>(123);
   Console::WriteLine("Integer field = {0}", myObj1->field1);

   // Instantiate an instance with a double field:
   MyClass<double>^ myObj2 = gcnew MyClass<double>(1.23);
   Console::WriteLine("Double field = {0}", myObj2->field1);

   // Instantiate an instance with a String field:
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>("ABC");
   Console::WriteLine("String field = {0}", myObj3->field1);
   }
```

```Output
Integer field = 123
Double field = 1.23
String field = ABC
```

## <a name="static-variables"></a>静的変数

新しいジェネリック型の作成時に、静的変数の新しいインスタンスが作成され、その型の任意の静的コンストラクターが実行されます。

静的変数では、外側のクラスから任意の型パラメーターを使用できます。

## <a name="example"></a>例

次の例では、静的コンストラクター内での静的フィールドと汎用クラスの使用を示します。

```cpp
// generics_static2.cpp
// compile with: /clr
using namespace System;

interface class ILog {
   void Write(String^ s);
};

ref class DateTimeLog : ILog {
public:
   virtual void Write(String^ s) {
      Console::WriteLine( "{0}\t{1}", DateTime::Now, s);
   }
};

ref class PlainLog : ILog {
public:
   virtual void Write(String^ s) { Console::WriteLine(s); }
};

generic <typename LogType>
where LogType : ILog
ref class G {
   static LogType s_log;

public:
   G(){}
   void SetLog(LogType log) { s_log = log; }
   void F() { s_log->Write("Test1"); }
   static G() { Console::WriteLine("Static constructor called."); }
};

int main() {
   G<PlainLog^>^ g1 = gcnew G<PlainLog^>();
   g1->SetLog(gcnew PlainLog());
   g1->F();

   G<DateTimeLog^>^ g2 = gcnew G<DateTimeLog^>();
   g2->SetLog(gcnew DateTimeLog());

   // prints date
   // g2->F();
}
```

```Output
Static constructor called.
Static constructor called.
Static constructor called.
Test1
```

## <a name="methods-in-generic-classes"></a>ジェネリック クラスのメソッド

ジェネリック クラスのメソッドそのものをジェネリックにすることができます。非ジェネリック メソッドは、クラスの型パラメーターによって暗黙的にパラメーター化されます。

ジェネリック クラス内のメソッドには、次の特別なルールが適用されます。

- ジェネリック クラスのメソッドでは、パラメーター、戻り値の型、またはローカル変数として型パラメーターを使用できます。

- ジェネリック クラスのメソッドでは、パラメーター、戻り値の型、またはローカル変数として、オープンまたはクローズ構築型を使用できます。

### <a name="non-generic-methods-in-generic-classes"></a>ジェネリック クラスの非ジェネリック メソッド

追加の型パラメーターを持たないジェネリック クラスのメソッドは、通常は非ジェネリックとして参照されますが、それらは外側のジェネリック クラスによって暗黙的にパラメーター化されます。

非ジェネリック メソッドのシグネチャには、外側のクラスの 1 つまたは複数の型パラメーターを含めることができます(直接的に、またはオープン構築型のいずれか)。 次に例を示します。

`void MyMethod(MyClass<ItemType> x) {}`

このようなメソッドの本文でも、これらの型パラメーターを使用できます。

## <a name="example"></a>例

次の例では、ジェネリック クラス `MyClass<ItemType>` 内に非ジェネリック メソッド `ProtectData` を宣言します。 このメソッドは、クラス型パラメーター `ItemType` をオープン構築型のシグニチャ内で使用します。

```cpp
// generics_non_generic_methods1.cpp
// compile with: /clr
// Non-generic methods within a generic class.
using namespace System;

generic <typename ItemType>
ref class MyClass {
public:
   String^ name;
   ItemType data;

   MyClass(ItemType x) {
      data = x;
   }

   // Non-generic method using the type parameter:
   virtual void ProtectData(MyClass<ItemType>^ x) {
      data = x->data;
   }
};

// ItemType defined as String^
ref class MyMainClass: MyClass<String^> {
public:
   // Passing "123.00" to the constructor:
   MyMainClass(): MyClass<String^>("123.00") {
      name = "Jeff Smith";
   }

   virtual void ProtectData(MyClass<String^>^ x) override {
      x->data = String::Format("${0}**", x->data);
   }

   static void Main() {
      MyMainClass^ x1 = gcnew MyMainClass();

      x1->ProtectData(x1);
      Console::WriteLine("Name: {0}", x1->name);
      Console::WriteLine("Amount: {0}", x1->data);
   }
};

int main() {
   MyMainClass::Main();
}
```

```Output
Name: Jeff Smith
Amount: $123.00**
```

## <a name="generic-methods-in-generic-classes"></a>ジェネリック クラスのジェネリック メソッド

ジェネリックと非ジェネリック クラスの両方でジェネリック メソッドを宣言できます。 次に例を示します。

## <a name="example"></a>例

```cpp
// generics_method2.cpp
// compile with: /clr /c
generic <typename Type1>
ref class G {
public:
   // Generic method having a type parameter
   // from the class, Type1, and its own type
   // parameter, Type2
   generic <typename Type2>
   void Method1(Type1 t1, Type2 t2) { F(t1, t2); }

   // Non-generic method:
   // Can use the class type param, Type1, but not Type2.
   void Method2(Type1 t1) { F(t1, t1); }

   void F(Object^ o1, Object^ o2) {}
};
```

非ジェネリック メソッドは、クラスの型パラメーターによってパラメーター化されるが追加の型パラメーターを持たないという意味ではジェネリックのままです。

ジェネリック クラスのメソッドのすべての型は、静的、インスタンス、および仮想メソッドを含むジェネリックにすることができます。

## <a name="example"></a>例

次の例では、ジェネリック クラス内でジェネリック メソッドを宣言して使用することを示します。

```cpp
// generics_generic_method2.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class MyClass {
public:
   // Declare a generic method member.
   generic <class Type1>
   String^ MyMethod(ItemType item, Type1 t) {
      return String::Concat(item->ToString(), t->ToString());
   }
};

int main() {
   // Create instances using different types.
   MyClass<int>^ myObj1 = gcnew MyClass<int>();
   MyClass<String^>^ myObj2 = gcnew MyClass<String^>();
   MyClass<String^>^ myObj3 = gcnew MyClass<String^>();

   // Calling MyMethod using two integers.
   Console::WriteLine("MyMethod returned: {0}",
            myObj1->MyMethod<int>(1, 2));

   // Calling MyMethod using an integer and a string.
   Console::WriteLine("MyMethod returned: {0}",
            myObj2->MyMethod<int>("Hello #", 1));

   // Calling MyMethod using two strings.
   Console::WriteLine("MyMethod returned: {0}",
       myObj3->MyMethod<String^>("Hello ", "World!"));

   // generic methods can be called without specifying type arguments
   myObj1->MyMethod<int>(1, 2);
   myObj2->MyMethod<int>("Hello #", 1);
   myObj3->MyMethod<String^>("Hello ", "World!");
}
```

```Output
MyMethod returned: 12
MyMethod returned: Hello #1
MyMethod returned: Hello World!
```

## <a name="using-nested-types-in-generic-classes"></a>ジェネリック クラスでの入れ子にされた型の使用

通常のクラスと同様、ジェネリック クラス内に他の型を宣言できます。 入れ子になったクラス宣言は、外側のクラス宣言の型パラメーターによって暗黙的にパラメーター化されます。 そのため、個別の入れ子になったクラスは、外側の構築型ごとに定義されます。 たとえば、次の宣言があるとします。

```cpp
// generic_classes_5.cpp
// compile with: /clr /c
generic <typename ItemType>
ref struct Outer {
   ref class Inner {};
};
```

`Outer<int>::Inner` 型は、`Outer<double>::Inner` 型と同じではありません。

ジェネリック クラスのジェネリック メソッドと同様、入れ子にされた型に対して、追加の型パラメーターを定義できます。 内側と外側のクラスで同じ型パラメーター名を使用した場合、内側の型パラメーターによって外側の型パラメーターが隠されます。

```cpp
// generic_classes_6.cpp
// compile with: /clr /c
generic <typename ItemType>
ref class Outer {
   ItemType outer_item;   // refers to outer ItemType

   generic <typename ItemType>
   ref class Inner {
      ItemType inner_item;   // refers to Inner ItemType
   };
};
```

外側の型パラメーターを参照する手段がないため、このような状況では、コンパイラによって警告が生成されます。

入れ子になったジェネリック構築型に名前がある場合、内側の型が外側の型の型パラメーターによって暗黙的にパラメーター化されるにもかかわらず、外側の型の型パラメーターは内側の型の型パラメーターの一覧に含まれることはありません。 上記の場合、構築型の名前は、`Outer<int>::Inner<string>` になります。

次の例では、ジェネリック クラスの入れ子にされた型を使用して、リンクされた一覧をビルドして読み取ることを示します。

## <a name="example"></a>例

```cpp
// generics_linked_list.cpp
// compile with: /clr
using namespace System;
generic <class ItemType>
ref class LinkedList {
// The node class:
public:
   ref class Node {
   // The link field:
   public:
      Node^ next;
      // The data field:
      ItemType item;
   } ^first, ^current;
};

ref class ListBuilder {
public:
   void BuildIt(LinkedList<double>^ list) {
      /* Build the list */
      double m[5] = {0.1, 0.2, 0.3, 0.4, 0.5};
      Console::WriteLine("Building the list:");

      for (int n=0; n<=4; n++) {
         // Create a new node:
         list->current = gcnew LinkedList<double>::Node();

         // Assign a value to the data field:
         list->current->item = m[n];

         // Set the link field "next" to be the same as
         // the "first" field:
         list->current->next = list->first;

         // Redirect "first" to the new node:
         list->first = list->current;

         // Display node's data as it builds:
         Console::WriteLine(list->current->item);
      }
   }

   void ReadIt(LinkedList<double>^ list) {
      // Read the list
      // Make "first" the "current" link field:
      list->current = list->first;
      Console::WriteLine("Reading nodes:");

      // Read nodes until current == null:
      while (list->current != nullptr) {
         // Display the node's data field:
         Console::WriteLine(list->current->item);

         // Move to the next node:
         list->current = list->current->next;
      }
   }
};

int main() {
   // Create a list:
   LinkedList<double>^ aList = gcnew LinkedList<double>();

   // Initialize first node:
   aList->first = nullptr;

   // Instantiate the class, build, and read the list:
   ListBuilder^ myListBuilder = gcnew ListBuilder();
   myListBuilder->BuildIt(aList);
   myListBuilder->ReadIt(aList);
}
```

```Output
Building the list:
0.1
0.2
0.3
0.4
0.5
Reading nodes:
0.5
0.4
0.3
0.2
0.1
```

## <a name="properties-events-indexers-and-operators-in-generic-classes"></a>ジェネリック クラスのプロパティ、イベント、インデクサー、および演算子

- プロパティ、イベント、インデクサー、および演算子では、`ItemType` がクラスの型パラメーターである場合などに、外側のジェネリック クラスの型パラメーターを、戻り値、パラメーター、またはローカル変数として使用できます。

    ```cpp
    public ItemType MyProperty {}
    ```

- プロパティ、イベント、インデクサー、おおび演算子そのものをパラメーター化することはできません。

## <a name="example"></a>例

この例では、ジェネリック クラス内のインスタンス プロパティの宣言を示します。

```cpp
// generics_generic_properties1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref class MyClass {
private:
   property ItemType myField;

public:
   property ItemType MyProperty {
      ItemType get() {
         return myField;
      }
      void set(ItemType value) {
         myField = value;
      }
   }
};

int main() {
   MyClass<String^>^ c = gcnew MyClass<String^>();
   MyClass<int>^ c1 = gcnew MyClass<int>();

   c->MyProperty = "John";
   c1->MyProperty = 234;

   Console::Write("{0}, {1}", c->MyProperty, c1->MyProperty);
}
```

```Output
John, 234
```

## <a name="example"></a>例

次の例では、イベントを持つジェネリック クラスを示します。

```cpp
// generics_generic_with_event.cpp
// compile with: /clr
// Declare a generic class with an event and
// invoke events.
using namespace System;

// declare delegates
generic <typename ItemType>
delegate void ClickEventHandler(ItemType);

// generic class that defines events
generic <typename ItemType>
ref class EventSource {
public:
   // declare the event OnClick
   event ClickEventHandler<ItemType>^ OnClick;
   void FireEvents(ItemType item) {
      // raises events
      OnClick(item);
   }
};

// generic class that defines methods that will called when
// event occurs
generic <typename ItemType>
ref class EventReceiver {
public:
   void OnMyClick(ItemType item) {
   Console::WriteLine("OnClick: {0}", item);
   }
};

int main() {
   EventSource<String^>^ MyEventSourceString =
                   gcnew EventSource<String^>();
   EventSource<int>^ MyEventSourceInt = gcnew EventSource<int>();
   EventReceiver<String^>^ MyEventReceiverString =
                   gcnew EventReceiver<String^>();
   EventReceiver<int>^ MyEventReceiverInt = gcnew EventReceiver<int>();

   // hook handler to event
   MyEventSourceString->OnClick += gcnew ClickEventHandler<String^>(
       MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick += gcnew ClickEventHandler<int>(
             MyEventReceiverInt, &EventReceiver<int>::OnMyClick);

   // invoke events
   MyEventSourceString->FireEvents("Hello");
   MyEventSourceInt->FireEvents(112);

   // unhook handler to event
   MyEventSourceString->OnClick -= gcnew ClickEventHandler<String^>(
        MyEventReceiverString, &EventReceiver<String^>::OnMyClick);
   MyEventSourceInt->OnClick -= gcnew ClickEventHandler<int>(
        MyEventReceiverInt, &EventReceiver<int>::OnMyClick);
}
```

## <a name="generic-structs"></a>ジェネリック構造体

ジェネリック構造体を宣言して使用するためのルールは、Visual C++ 言語リファレンスに記載されている違いを除いて、ジェネリック クラスのルールと同じです。

## <a name="example"></a>例

次の例では、1 つのフィールド `myField` があるジェネリック構造体 `MyGenStruct`を宣言し、そのフィールドに異なる型 (**int**、**double**、`String^`) の値を割り当てます。

```cpp
// generics_generic_struct1.cpp
// compile with: /clr
using namespace System;

generic <typename ItemType>
ref struct MyGenStruct {
public:
   ItemType myField;

   ItemType AssignValue(ItemType item) {
      myField = item;
      return myField;
   }
};

int main() {
   int myInt = 123;
   MyGenStruct<int>^ myIntObj = gcnew MyGenStruct<int>();
   myIntObj->AssignValue(myInt);
   Console::WriteLine("The field is assigned the integer value: {0}",
            myIntObj->myField);

   double myDouble = 0.123;
   MyGenStruct<double>^ myDoubleObj = gcnew MyGenStruct<double>();
   myDoubleObj->AssignValue(myDouble);
   Console::WriteLine("The field is assigned the double value: {0}",
            myDoubleObj->myField);

   String^ myString = "Hello Generics!";
   MyGenStruct<String^>^ myStringObj = gcnew MyGenStruct<String^>();
   myStringObj->AssignValue(myString);
   Console::WriteLine("The field is assigned the string: {0}",
            myStringObj->myField);
}
```

```Output
The field is assigned the integer value: 123
The field is assigned the double value: 0.123
The field is assigned the string: Hello Generics!
```

## <a name="see-also"></a>関連項目

[ジェネリック](generics-cpp-component-extensions.md)