---
title: interface class (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- interface_CPP
helpviewer_keywords:
- interface class keyword
- interface struct keyword
ms.assetid: 3ccea701-f50b-4da7-ad6b-f0ee1203e2b9
ms.openlocfilehash: 60e8965e3ef2538554d8c664b35bd0849bd5e69e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515707"
---
# <a name="interface-class--ccli-and-ccx"></a>interface class (C++/CLI および C++/CX)

インターフェイスを宣言します。  ネイティブ インターフェイスについては、[__interface](../cpp/interface.md) を参照してください。

## <a name="all-runtimes"></a>すべてのランタイム

### <a name="syntax"></a>構文

```cpp
interface_access
interface class
name :  inherit_accessbase_interface{};interface_accessinterface structname :  inherit_accessbase_interface{};
```

### <a name="parameters"></a>パラメーター

*interface_access*<br/>
アセンブリの外部のインターフェイスのアクセシビリティ。  指定できる値は **public** と **private** です。  既定値は **private** です。 入れ子になったインターフェイスでは、*interface_access* 指定子は指定できません。

*name*<br/>
インターフェイスの名前。

*inherit_access*<br/>
*base_interface* のアクセシビリティ。  基底インターフェイスで許可されるアクセシビリティは **public** (既定値) だけです。

*base_interface*<br/>
(省略可能) インターフェイス *name* の基底インターフェイス。

### <a name="remarks"></a>解説

**interface struct** は **interface class** と同等です。

インターフェイスには、関数、イベント、およびプロパティの宣言を含めることができます。  すべてのインターフェイス メンバーには、パブリック アクセシビリティがあります。 インターフェイスには静的データ メンバー、関数、イベント、およびプロパティを含めることもでき、これらの静的メンバーはインターフェイスに定義する必要があります。

インターフェイスは、クラスを実装できる方法を定義します。 インターフェイスはクラスではなく、クラスだけがインターフェイスを実装できます。 インターフェイスに宣言される関数をクラスで定義すると、オーバーライドなしで関数が実装されます。 そのため、名前の参照には、インターフェイス メンバーは含まれません。

インターフェイスから派生するクラスまたは構造体は、インターフェイスのすべてのメンバーを実装する必要があります。 インターフェイス *name* の実装時に、`base_interface` の一覧のインターフェイスも実装する必要があります。

詳細については次を参照してください:

- [インターフェイス静的コンストラクター](../dotnet/how-to-define-an-interface-static-constructor-cpp-cli.md)

- [ジェネリック インターフェイス (C++/CLI)](generic-interfaces-visual-cpp.md)

他の CLR 型については、[クラスと構造体](classes-and-structs-cpp-component-extensions.md)に関する記事を参照してください。

コンパイル時に、型が `__is_interface_class(type)` のインターフェイスかどうかを検出できます。 詳細については、「[型の特徴のコンパイラ サポート](compiler-support-for-type-traits-cpp-component-extensions.md)」を参照してください。

開発環境では、キーワード (例: `interface class`) を強調表示し、F1 を押すことで、これらのキーワードの F1 ヘルプを取得できます。

## <a name="windows-runtime"></a>Windows ランタイム

### <a name="remarks"></a>解説

(この言語機能には Windows ランタイムのみに適用される特記事項がありません。)

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

### <a name="remarks"></a>解説

(この言語機能には共通言語ランタイムのみに適用される特記事項がありません。)

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次のコード例では、インターフェイスで clock 関数の動作を定義する方法を示します。

```cpp
// mcppv2_interface_class.cpp
// compile with: /clr
using namespace System;

public delegate void ClickEventHandler(int, double);

// define interface with nested interface
public interface class Interface_A {
   void Function_1();

   interface class Interface_Nested_A {
      void Function_2();
   };
};

// interface with a base interface
public interface class Interface_B : Interface_A {
   property int Property_Block;
   event ClickEventHandler^ OnClick;
   static void Function_3() { Console::WriteLine("in Function_3"); }
};

// implement nested interface
public ref class MyClass : public Interface_A::Interface_Nested_A {
public:
   virtual void Function_2() { Console::WriteLine("in Function_2"); }
};

// implement interface and base interface
public ref class MyClass2 : public Interface_B {
private:
   int MyInt;

public:
   // implement non-static function
   virtual void Function_1() { Console::WriteLine("in Function_1"); }

   // implement property
   property int Property_Block {
      virtual int get() { return MyInt; }
      virtual void set(int value) { MyInt = value; }
   }
   // implement event
   virtual event ClickEventHandler^ OnClick;

   void FireEvents() {
      OnClick(7, 3.14159);
   }
};

// class that defines method called when event occurs
ref class EventReceiver {
public:
   void OnMyClick(int i, double d) {
      Console::WriteLine("OnClick: {0}, {1}", i, d);
   }
};

int main() {
   // call static function in an interface
   Interface_B::Function_3();

   // instantiate class that implements nested interface
   MyClass ^ x = gcnew MyClass;
   x->Function_2();

   // instantiate class that implements interface with base interface
   MyClass2 ^ y = gcnew MyClass2;
   y->Function_1();
   y->Property_Block = 8;
   Console::WriteLine(y->Property_Block);

   EventReceiver^ MyEventReceiver = gcnew EventReceiver();

   // hook handler to event
   y->OnClick += gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // invoke events
   y->FireEvents();

   // unhook handler to event
   y->OnClick -= gcnew ClickEventHandler(MyEventReceiver, &EventReceiver::OnMyClick);

   // call implemented function via interface handle
   Interface_A^ hi = gcnew MyClass2();
   hi->Function_1();
}
```

```Output
in Function_3

in Function_2

in Function_1

8

OnClick: 7, 3.14159

in Function_1
```

次のコード例では、同じシグネチャが宣言された複数のインターフェイスと、これらのインターフェイスがクラスによって使用される場所を指定して関数を実装する 2 つの方法を示します。

```cpp
// mcppv2_interface_class_2.cpp
// compile with: /clr /c
interface class I {
   void Test();
   void Test2();
};

interface class J : I {
   void Test();
   void Test2();
};

ref struct R : I, J {
   // satisfies the requirement to implement Test in both interfaces
   virtual void Test() {}

   // implement both interface functions with explicit overrides
   virtual void A() = I::Test2 {}
   virtual void B() = J::Test2 {}
};
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)