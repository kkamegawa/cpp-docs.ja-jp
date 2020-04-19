---
title: ジェネリック インターフェイス (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generic interfaces
- interfaces, generic [C++}
ms.assetid: f3da788a-ba83-4db7-9dcf-9b95a8fb9d1a
ms.openlocfilehash: 035636f2723cd949f5a1852b3d5500a20f5fb493
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516367"
---
# <a name="generic-interfaces-ccli"></a>ジェネリック インターフェイス (C++/CLI)

クラスの型パラメーターに適用される制約は、インターフェイスの型パラメーターに適用されるものと同じです (「[ジェネリック クラス (C++/CLI)](generic-classes-cpp-cli.md)」を参照してください)。

メソッドのオーバーロードを制御するルールは、ジェネリック クラスまたはジェネリック インターフェイス内の関数のルールと同じです。

明示的なインターフェイス メンバーの実装は、単純なインターフェイス型と同じ方法で構築されたインターフェイス型で機能します (次の例を参照してください)。

マネージド インターフェイスの詳細については、「[interface class](interface-class-cpp-component-extensions.md)」を参照してください。

## <a name="syntax"></a>構文

```cpp
[attributes] generic <class-key type-parameter-identifier[, ...]>
[type-parameter-constraints-clauses][accesibility-modifiers] interface class identifier [: base-list] {   interface-body} [declarators] ;
```

## <a name="remarks"></a>解説

*属性*<br/>
(省略可能) 追加の宣言情報。 属性と属性クラスについては、「**属性**」を参照してください。

*class-key*<br/>
**class** または **typename**。

*type-parameter-identifier(s)*<br/>
コンマ区切りの識別子の一覧。

*type-parameter-constraints-clauses*<br/>
「[ジェネリック型パラメーターの制約 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)」に指定された書式を使用します。

*accessibility-modifiers*<br/>
(省略可能) アクセシビリティ修飾子 (例: **public、private**)。

*identifier*<br/>
インターフェイスの名前。

*base-list*<br/>
(省略可能) 1 つまたは複数のコンマで区切られた明示的な基底インターフェイスを含む一覧。

*interface-body*<br/>
インターフェイス メンバーの宣言。

*declarators*<br/>
(省略可能) この型に基づく変数の宣言。

## <a name="example"></a>例

次の例では、ジェネリック インターフェイスを宣言し、インスタンス化する方法を示します。 この例では、ジェネリック インターフェイス `IList<ItemType>` が宣言されます。 その後、2 つのジェネリック クラス (`List1<ItemType>` と `List2<ItemType>`) によって、異なる実装で実装されます。

```cpp
// generic_interface.cpp
// compile with: /clr
using namespace System;

// An exception to be thrown by the List when
// attempting to access elements beyond the
// end of the list.
ref class ElementNotFoundException : Exception {};

// A generic List interface
generic <typename ItemType>
public interface class IList {
   ItemType MoveFirst();
   bool Add(ItemType item);
   bool AtEnd();
   ItemType Current();
   void MoveNext();
};

// A linked list implementation of IList
generic <typename ItemType>
public ref class List1 : public IList<ItemType> {
   ref class Node {
      ItemType m_item;

   public:
      ItemType get_Item() { return m_item; };
      void set_Item(ItemType value) { m_item = value; };

      Node^ next;

      Node(ItemType item) {
         m_item = item;
         next = nullptr;
      }
   };

   Node^ first;
   Node^ last;
   Node^ current;

   public:
   List1() {
      first = nullptr;
      last = first;
      current = first;
   }

   virtual ItemType MoveFirst() {
      current = first;
      if (first != nullptr)
        return first->get_Item();
      else
         return ItemType();
   }

   virtual bool Add(ItemType item) {
      if (last != nullptr) {
         last->next = gcnew Node(item);
         last = last->next;
      }
      else {
         first = gcnew Node(item);
         last = first;
         current = first;
      }
      return true;
   }

   virtual bool AtEnd() {
      if (current == nullptr )
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
       if (current != nullptr)
         return current->get_Item();
       else
         throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current != nullptr)
       current = current->next;
      else
        throw gcnew ElementNotFoundException();
   }
};

// An array implementation of IList
generic <typename ItemType>
ref class List2 : public IList<ItemType> {
   array<ItemType>^ item_array;
   int count;
   int current;

   public:

   List2() {
      // not yet possible to declare an
      // array of a generic type parameter
      item_array = gcnew array<ItemType>(256);
      count = current = 0;
   }

   virtual ItemType MoveFirst() {
      current = 0;
      return item_array[0];
   }

   virtual bool Add(ItemType item) {
      if (count < 256)
         item_array[count++] = item;
      else
        return false;
      return true;
   }

   virtual bool AtEnd() {
      if (current >= count)
        return true;
      else
        return false;
   }

   virtual ItemType Current() {
      if (current < count)
        return item_array[current];
      else
        throw gcnew ElementNotFoundException();
   }

   virtual void MoveNext() {
      if (current < count)
         ++current;
      else
         throw gcnew ElementNotFoundException();
   }
};

// Add elements to the list and display them.
generic <typename ItemType>
void AddStringsAndDisplay(IList<ItemType>^ list, ItemType item1, ItemType item2) {
   list->Add(item1);
   list->Add(item2);
   for (list->MoveFirst(); ! list->AtEnd(); list->MoveNext())
   Console::WriteLine(list->Current());
}

int main() {
   // Instantiate both types of list.

   List1<String^>^ list1 = gcnew List1<String^>();
   List2<String^>^ list2 = gcnew List2<String^>();

   // Use the linked list implementation of IList.
   AddStringsAndDisplay<String^>(list1, "Linked List", "List1");

   // Use the array implementation of the IList.
   AddStringsAndDisplay<String^>(list2, "Array List", "List2");
}
```

```Output
Linked List
List1
Array List
List2
```

## <a name="example"></a>例

この例では、ジェネリック インターフェイス `IMyGenIface` と、`IMyGenIface` を特殊化する 2 つの非ジェネリック インターフェイス (`IMySpecializedInt` と `ImySpecializedString`) を宣言します。 次に、2 つの特殊化されたインターフェイスが、2 つのクラス (`MyIntClass` と `MyStringClass`) で実装されます。 この例では、ジェネリック インターフェイスを特殊化し、ジェネリック インターフェイスと非ジェネリック インターフェイスをインスタンス化し、インターフェイスの明示的に実装されたメンバーを呼び出します。

```cpp
// generic_interface2.cpp
// compile with: /clr
// Specializing and implementing generic interfaces.
using namespace System;

generic <class ItemType>
public interface class IMyGenIface {
   void Initialize(ItemType f);
};

public interface class IMySpecializedInt: public IMyGenIface<int> {
   void Display();
};

public interface class IMySpecializedString: public IMyGenIface<String^> {
   void Display();
};

public ref class MyIntClass: public IMySpecializedInt {
   int myField;

public:
   virtual void Initialize(int f) {
      myField = f;
   }

   virtual void Display() {
      Console::WriteLine("The integer field contains: {0}", myField);
   }
};

public ref struct MyStringClass: IMySpecializedString {
   String^ myField;

public:
   virtual void Initialize(String^ f) {
      myField = f;
    }

   virtual void Display() {
      Console::WriteLine("The String field contains: {0}", myField);
   }
};

int main() {
   // Instantiate the generic interface.
   IMyGenIface<int>^ myIntObj = gcnew MyIntClass();

   // Instantiate the specialized interface "IMySpecializedInt."
   IMySpecializedInt^ mySpIntObj = (IMySpecializedInt^) myIntObj;

   // Instantiate the generic interface.
   IMyGenIface<String^>^ myStringObj = gcnew MyStringClass();

   // Instantiate the specialized interface "IMySpecializedString."
   IMySpecializedString^ mySpStringObj =
            (IMySpecializedString^) myStringObj;

   // Call the explicitly implemented interface members.
   myIntObj->Initialize(1234);
   mySpIntObj->Display();

   myStringObj->Initialize("My string");
   mySpStringObj->Display();
}
```

```Output
The integer field contains: 1234
The String field contains: My string
```

## <a name="see-also"></a>関連項目

[ジェネリック](generics-cpp-component-extensions.md)