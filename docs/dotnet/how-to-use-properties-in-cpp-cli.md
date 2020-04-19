---
title: '方法: プロパティを使用して、c++/cli CLI'
ms.date: 07/21/2017
helpviewer_keywords:
- simple properties
- properties [C++], simple
ms.assetid: f5d82547-e214-4f05-9e1b-ddb6d0dc5e4c
ms.openlocfilehash: 47cfd4c633942874b7b349da5635b34ea42090ee
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447313"
---
# <a name="how-to-use-properties-in-ccli"></a>方法: プロパティを使用して、c++/cli CLI

この記事では、c++ のプロパティを使用する方法を示しています。/cli CLI。

## <a name="basic-properties"></a>基本プロパティ

基本プロパティ: だけを割り当てるし、プライベート データ メンバーを取得する、明示的に get を定義およびプロパティのデータ型だけを指定するときに、コンパイラが自動的に提供するためのアクセサー関数を設定する必要はありません。 このコードでは、基本的なプロパティを示しています。

```cpp
// SimpleProperties.cpp
// compile with: /clr
using namespace System;

ref class C {
public:
   property int Size;
};

int main() {
   C^ c = gcnew C;
   c->Size = 111;
   Console::WriteLine("c->Size = {0}", c->Size);
}
```

```Output
c->Size = 111
```

## <a name="static-properties"></a>静的プロパティ

このコード サンプルでは、宣言および静的プロパティを使用する方法を示します。  静的プロパティは、そのクラスの静的メンバーにのみアクセスできます。

```cpp
// mcppv2_property_3.cpp
// compile with: /clr
using namespace System;

ref class StaticProperties {
   static int MyInt;
   static int MyInt2;

public:
   static property int Static_Data_Member_Property;

   static property int Static_Block_Property {
      int get() {
         return MyInt;
      }

      void set(int value) {
         MyInt = value;
      }
   }
};

int main() {
   StaticProperties::Static_Data_Member_Property = 96;
   Console::WriteLine(StaticProperties::Static_Data_Member_Property);

   StaticProperties::Static_Block_Property = 47;
   Console::WriteLine(StaticProperties::Static_Block_Property);
}
```

```Output
96
47
```

## <a name="indexed-properties"></a>インデックス付きプロパティ

インデックス付きプロパティは、通常、添字演算子を使用してアクセスされるデータ構造を公開します。

使用する場合は、既定のインデックス付きプロパティがデータ構造は、クラス名を参照するだけでアクセスできるユーザー定義のインデックス付きプロパティを使用する場合は、データ構造にアクセスするプロパティ名を指定する必要があります。

記述されたインデクサーを使用する方法についてはC#を参照してください[方法。使用、C#インデクサー (C +/cli CLI)](../dotnet/how-to-consume-a-csharp-indexer-cpp-cli.md)します。

このコード サンプルでは、既定値とユーザー定義のインデックス付きプロパティを使用する方法を示します。

```cpp
// mcppv2_property_2.cpp
// compile with: /clr
using namespace System;
public ref class C {
   array<int>^ MyArr;

public:
   C() {
      MyArr = gcnew array<int>(5);
   }

   // default indexer
   property int default[int] {
      int get(int index) {
         return MyArr[index];
      }
      void set(int index, int value) {
         MyArr[index] = value;
      }
   }

   // user-defined indexer
   property int indexer1[int] {
      int get(int index) {
         return MyArr[index];
      }
      void set(int index, int value) {
         MyArr[index] = value;
      }
   }
};

int main() {
   C ^ MyC = gcnew C();

   // use the default indexer
   Console::Write("[ ");
   for (int i = 0 ; i < 5 ; i++) {
      MyC[i] = i;
      Console::Write("{0} ", MyC[i]);
   }

   Console::WriteLine("]");

   // use the user-defined indexer
   Console::Write("[ ");
   for (int i = 0 ; i < 5 ; i++) {
      MyC->indexer1[i] = i * 2;
      Console::Write("{0} ", MyC->indexer1[i]);
   }

   Console::WriteLine("]");
}
```

```Output
[ 0 1 2 3 4 ]
[ 0 2 4 6 8 ]
```

次のサンプルを使用して既定のインデクサーを呼び出す方法を示しています、`this`ポインター。

```cpp
// call_default_indexer_through_this_pointer.cpp
// compile with: /clr /c
value class Position {
public:
   Position(int x, int y) : position(gcnew array<int, 2>(100, 100)) {
      this->default[x, y] = 1;
   }

   property int default[int, int] {
      int get(int x, int y) {
         return position[x, y];
      }

      void set(int x, int y, int value) {}
   }

private:
   array<int, 2> ^ position;
};
```

このサンプルは、使用する方法を示します<xref:System.Reflection.DefaultMemberAttribute>を既定のインデクサーを指定します。

```cpp
// specify_default_indexer.cpp
// compile with: /LD /clr
using namespace System;
[Reflection::DefaultMember("XXX")]
public ref struct Squares {
   property Double XXX[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
};
```

次の例では、前の例で作成されたメタデータを消費します。

```cpp
// consume_default_indexer.cpp
// compile with: /clr
#using "specify_default_indexer.dll"
int main() {
   Squares ^ square = gcnew Squares();
   System::Console::WriteLine("{0}", square[3]);
}
```

```Output
9
```

## <a name="virtual-properties"></a>仮想プロパティ

このコード サンプルでは、宣言および仮想のプロパティを使用する方法を示します。

```cpp
// mcppv2_property_4.cpp
// compile with: /clr
using namespace System;
interface struct IEFace {
public:
   property int VirtualProperty1;
   property int VirtualProperty2 {
      int get();
      void set(int i);
   }
};

// implement virtual events
ref class PropImpl : public IEFace {
   int MyInt;
public:
   virtual property int VirtualProperty1;

   virtual property int VirtualProperty2 {
      int get() {
         return MyInt;
      }
      void set(int i) {
         MyInt = i;
      }
   }
};

int main() {
   PropImpl ^ MyPI = gcnew PropImpl();
   MyPI->VirtualProperty1 = 93;
   Console::WriteLine(MyPI->VirtualProperty1);

   MyPI->VirtualProperty2 = 43;
   Console::WriteLine(MyPI->VirtualProperty2);
}
```

```Output
93
43
```

## <a name="abstract-and-sealed-properties"></a>Abstract および sealed プロパティ

[抽象](../extensions/abstract-cpp-component-extensions.md)と[シール](../extensions/sealed-cpp-component-extensions.md)キーワードは、ECMA で有効と指定されたC++、microsoft の/CLI 仕様C++コンパイラ、ことはできませんに指定しても、単純なプロパティでの非 trivial プロパティのプロパティの宣言。

Sealed または抽象プロパティを宣言するには、重要なプロパティを定義し、指定する必要があります、`abstract`または`sealed`キーワードを get と set アクセサー関数。

```cpp
// properties_abstract_sealed.cpp
// compile with: /clr
ref struct A {
protected:
   int m_i;

public:
   A() { m_i = 87; }

   // define abstract property
   property int Prop_1 {
      virtual int get() abstract;
      virtual void set(int i) abstract;
   }
};

ref struct B : A {
private:
   int m_i;

public:
   B() { m_i = 86; }

   // implement abstract property
   property int Prop_1 {
      virtual int get() override { return m_i; }
      virtual void set(int i) override { m_i = i; }
   }
};

ref struct C {
private:
   int m_i;

public:
   C() { m_i = 87; }

   // define sealed property
   property int Prop_2 {
      virtual int get() sealed { return m_i; }
      virtual void set(int i) sealed { m_i = i; };
   }
};

int main() {
   B b1;
   // call implementation of abstract property
   System::Console::WriteLine(b1.Prop_1);

   C c1;
   // call sealed property
   System::Console::WriteLine(c1.Prop_2);
}
```

```Output
86
87
```

## <a name="multidimensional-properties"></a>多次元プロパティ

多次元プロパティを使用すると、パラメーターの非標準の数を取得するプロパティのアクセサー メソッドを定義します。

```cpp
// mcppv2_property_5.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(0) {}
   property double MultiDimProp[int, int, int] {
      double get(int, int, int) {
         return d;
      }
      void set(int i, int j, int k, double l) {
         // do something with those ints
         d = l;
      }
   }

   property double MultiDimProp2[int] {
      double get(int) {
         return d;
      }
      void set(int i, double l) {
         // do something with those ints
         d = l;
      }
   }

};

int main() {
   X ^ MyX = gcnew X();
   MyX->MultiDimProp[0,0,0] = 1.1;
   System::Console::WriteLine(MyX->MultiDimProp[0, 0, 0]);
}
```

```Output
1.1
```

## <a name="overloading-property-accessors"></a>プロパティ アクセサーをオーバー ロード

次の例では、インデックス付きプロパティをオーバー ロードする方法を示します。

```cpp
// mcppv2_property_6.cpp
// compile with: /clr
ref class X {
   double d;
public:
   X() : d(0.0) {}
   property double MyProp[int] {
      double get(int i) {
         return d;
      }

      double get(System::String ^ i) {
         return 2*d;
      }

      void set(int i, double l) {
         d = i * l;
      }
   }   // end MyProp definition
};

int main() {
   X ^ MyX = gcnew X();
   MyX->MyProp[2] = 1.7;
   System::Console::WriteLine(MyX->MyProp[1]);
   System::Console::WriteLine(MyX->MyProp["test"]);
}
```

```Output
3.4
6.8
```

## <a name="see-also"></a>関連項目

[プロパティ](../extensions/property-cpp-component-extensions.md)
