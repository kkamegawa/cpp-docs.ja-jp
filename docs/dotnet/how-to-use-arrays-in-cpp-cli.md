---
title: '方法: 配列を使用して、c++/cli CLI'
ms.date: 11/04/2016
helpviewer_keywords:
- arrays [C++], single-dimension
ms.assetid: 301cfb3e-199f-42c8-8151-629dce9e87f3
ms.openlocfilehash: 65d384cbac7691d000ae6e895c9cf63e71726689
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387189"
---
# <a name="how-to-use-arrays-in-ccli"></a>方法: 配列を使用して、c++/cli CLI

この記事は、C + で配列を使用する方法を説明します/cli CLI。

## <a name="single-dimension-arrays"></a>1 次元の配列

次の例では、参照、値、およびネイティブ ポインター型の 1 次元の配列を作成する方法を示します。 また、1 次元配列を引数として関数に渡す方法と、関数からの 1 次元配列を返す方法も説明します。

```cpp
// mcppv2_sdarrays.cpp
// compile with: /clr
using namespace System;

#define ARRAY_SIZE 2

value struct MyStruct {
   int m_i;
};

ref class MyClass {
public:
   int m_i;
};

struct MyNativeClass {
   int m_i;
};

// Returns a managed array of a reference type.
array<MyClass^>^ Test0() {
   int i;
   array< MyClass^ >^ local = gcnew array< MyClass^ >(ARRAY_SIZE);

   for (i = 0 ; i < ARRAY_SIZE ; i++) {
      local[i] = gcnew MyClass;
      local[i] -> m_i = i;
   }
   return local;
}

// Returns a managed array of Int32.
array<Int32>^ Test1() {
   int i;
   array< Int32 >^ local = gcnew array< Int32 >(ARRAY_SIZE);

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      local[i] = i + 10;
   return local;
}

// Modifies an array.
void Test2(array< MyNativeClass * >^ local) {
   for (int i = 0 ; i < ARRAY_SIZE ; i++)
      local[i] -> m_i = local[i] -> m_i + 2;
}

int main() {
   int i;

   // Declares an array of user-defined reference types
   // and uses a function to initialize.
   array< MyClass^ >^ MyClass0;
   MyClass0 = Test0();

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine("MyClass0[{0}] = {1}", i, MyClass0[i] -> m_i);
   Console::WriteLine();

   // Declares an array of value types and uses a function to initialize.
   array< Int32 >^ IntArray;
   IntArray = Test1();

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine("IntArray[{0}] = {1}", i, IntArray[i]);
   Console::WriteLine();

   // Declares and initializes an array of user-defined
   // reference types.
   array< MyClass^ >^ MyClass1 = gcnew array< MyClass^ >(ARRAY_SIZE);
   for (i = 0 ; i < ARRAY_SIZE ; i++) {
      MyClass1[i] = gcnew MyClass;
      MyClass1[i] -> m_i = i + 20;
   }

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine("MyClass1[{0}] = {1}", i, MyClass1[i] -> m_i);
   Console::WriteLine();

   // Declares and initializes an array of pointers to a native type.
   array< MyNativeClass * >^ MyClass2 = gcnew array<
      MyNativeClass * >(ARRAY_SIZE);
   for (i = 0 ; i < ARRAY_SIZE ; i++) {
      MyClass2[i] = new MyNativeClass();
      MyClass2[i] -> m_i = i + 30;
   }

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine("MyClass2[{0}] = {1}", i, MyClass2[i]->m_i);
   Console::WriteLine();

   Test2(MyClass2);
   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine("MyClass2[{0}] = {1}", i, MyClass2[i]->m_i);
   Console::WriteLine();

   delete[] MyClass2[0];
   delete[] MyClass2[1];

   // Declares and initializes an array of user-defined value types.
   array< MyStruct >^ MyStruct1 = gcnew array< MyStruct >(ARRAY_SIZE);
   for (i = 0 ; i < ARRAY_SIZE ; i++) {
      MyStruct1[i] = MyStruct();
      MyStruct1[i].m_i = i + 40;
   }

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine("MyStruct1[{0}] = {1}", i, MyStruct1[i].m_i);
}
```

```Output
MyClass0[0] = 0
MyClass0[1] = 1

IntArray[0] = 10
IntArray[1] = 11

MyClass1[0] = 20
MyClass1[1] = 21

MyClass2[0] = 30
MyClass2[1] = 31

MyClass2[0] = 32
MyClass2[1] = 33

MyStruct1[0] = 40
MyStruct1[1] = 41
```

次の例では、1 次元マネージ配列の集約の初期化を実行する方法を示します。

```cpp
// mcppv2_sdarrays_aggregate_init.cpp
// compile with: /clr
using namespace System;

ref class G {
public:
   G(int i) {}
};

value class V {
public:
   V(int i) {}
};

class N {
public:
   N(int i) {}
};

int main() {
   // Aggregate initialize a single-dimension managed array.
   array<String^>^ gc1 = gcnew array<String^>{"one", "two", "three"};
   array<String^>^ gc2 = {"one", "two", "three"};

   array<G^>^ gc3 = gcnew array<G^>{gcnew G(0), gcnew G(1), gcnew G(2)};
   array<G^>^ gc4 = {gcnew G(0), gcnew G(1), gcnew G(2)};

   array<Int32>^ value1 = gcnew array<Int32>{0, 1, 2};
   array<Int32>^ value2 = {0, 1, 2};

   array<V>^ value3 = gcnew array<V>{V(0), V(1), V(2)};
   array<V>^ value4 = {V(0), V(1), V(2)};

   array<N*>^ native1 = gcnew array<N*>{new N(0), new N(1), new N(2)};
   array<N*>^ native2 = {new N(0), new N(1), new N(2)};
}
```

```Output
MyClass0[0, 0] = 0
MyClass0[0, 1] = 0
MyClass0[1, 0] = 1
MyClass0[1, 1] = 1

IntArray[0, 0] = 10
IntArray[0, 1] = 10
IntArray[1, 0] = 11
IntArray[1, 1] = 11
```

この例では、マルチ ディメンションのマネージ配列で集約の初期化を実行する方法を示します。

```cpp
// mcppv2_mdarrays_aggregate_initialization.cpp
// compile with: /clr
using namespace System;

ref class G {
public:
   G(int i) {}
};

value class V {
public:
   V(int i) {}
};

class N {
public:
   N(int i) {}
};

int main() {
   // Aggregate initialize a multidimension managed array.
   array<String^, 2>^ gc1 = gcnew array<String^, 2>{ {"one", "two"},
       {"three", "four"} };
   array<String^, 2>^ gc2 = { {"one", "two"}, {"three", "four"} };

   array<G^, 2>^ gc3 = gcnew array<G^, 2>{ {gcnew G(0), gcnew G(1)},
       {gcnew G(2), gcnew G(3)} };
   array<G^, 2>^ gc4 = { {gcnew G(0), gcnew G(1)}, {gcnew G(2), gcnew G(3)} };

   array<Int32, 2>^ value1 = gcnew array<Int32, 2>{ {0, 1}, {2, 3} };
   array<Int32, 2>^ value2 = { {0, 1}, {2, 3} };

   array<V, 2>^ value3 = gcnew array<V, 2>{ {V(0), V(1)}, {V(2), V(3)} };
   array<V, 2>^ value4 = { {V(0), V(1)}, {V(2), V(3)} };

   array<N*, 2>^ native1 = gcnew array<N*, 2>{ {new N(0), new N(1)},
      {new N(2), new N(3)} };
   array<N*, 2>^ native2 = { {new N(0), new N(1)}, {new N(2), new N(3)} };
}
```

## <a name="jagged-arrays"></a>ジャグ配列

このセクションでは、参照、値、およびネイティブ ポインター型のマネージ配列の 1 次元の配列を作成する方法を示します。 また、1 次元配列を引数として関数に渡す方法と、関数からマネージ配列の 1 次元配列を取得する方法についても説明します。

```cpp
// mcppv2_array_of_arrays.cpp
// compile with: /clr
using namespace System;

#define ARRAY_SIZE 2

value struct MyStruct {
   int m_i;
};

ref class MyClass {
public:
   int m_i;
};

// Returns an array of managed arrays of a reference type.
array<array<MyClass^>^>^ Test0() {
   int size_of_array = 4;
   array<array<MyClass^>^>^ local = gcnew
      array<array<MyClass^>^>(ARRAY_SIZE);

   for (int i = 0 ; i < ARRAY_SIZE ; i++, size_of_array += 4) {
      local[i] = gcnew array<MyClass^>(size_of_array);
      for (int k = 0; k < size_of_array ; k++) {
         local[i][k] = gcnew MyClass;
         local[i][k] -> m_i = i;
      }
   }

   return local;
}

// Returns a managed array of Int32.
array<array<Int32>^>^ Test1() {
   int i;
   array<array<Int32>^>^ local = gcnew array<array< Int32 >^>(ARRAY_SIZE);

   for (i = 0 ; i < ARRAY_SIZE ; i++) {
      local[i] = gcnew array< Int32 >(ARRAY_SIZE);
         for ( int j = 0 ; j < ARRAY_SIZE ; j++ )
            local[i][j] = i + 10;
   }
   return local;
}

int main() {
   int i, j;

   // Declares an array of user-defined reference types
   // and uses a function to initialize.
   array< array< MyClass^ >^ >^ MyClass0;
   MyClass0 = Test0();

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      for ( j = 0 ; j < ARRAY_SIZE ; j++ )
         Console::WriteLine("MyClass0[{0}] = {1}", i, MyClass0[i][j] -> m_i);
   Console::WriteLine();

   // Declares an array of value types and uses a function to initialize.
   array< array< Int32 >^ >^ IntArray;
   IntArray = Test1();

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      for (j = 0 ; j < ARRAY_SIZE ; j++)
      Console::WriteLine("IntArray[{0}] = {1}", i, IntArray[i][j]);
   Console::WriteLine();

   // Declares and initializes an array of user-defined value types.
   array< MyStruct >^ MyStruct1 = gcnew array< MyStruct >(ARRAY_SIZE);
   for (i = 0 ; i < ARRAY_SIZE ; i++) {
      MyStruct1[i] = MyStruct();
      MyStruct1[i].m_i = i + 40;
   }

   for (i = 0 ; i < ARRAY_SIZE ; i++)
      Console::WriteLine(MyStruct1[i].m_i);
}
```

```Output
MyClass0[0] = 0
MyClass0[0] = 0
MyClass0[1] = 1
MyClass0[1] = 1

IntArray[0] = 10
IntArray[0] = 10
IntArray[1] = 11
IntArray[1] = 11

40
41
```

次の例では、ジャグ配列と集約の初期化を実行する方法を示します。

```cpp
// mcppv2_array_of_arrays_aggregate_init.cpp
// compile with: /clr
using namespace System;
#define ARRAY_SIZE 2
int size_of_array = 4;
int count = 0;

ref class MyClass {
public:
   int m_i;
};

struct MyNativeClass {
   int m_i;
};

int main() {
   // Declares an array of user-defined reference types
   // and performs an aggregate initialization.
   array< array< MyClass^ >^ >^ MyClass0 = gcnew array<array<MyClass^>^> {
      gcnew array<MyClass^>{ gcnew MyClass(), gcnew MyClass() },
      gcnew array<MyClass^>{ gcnew MyClass(), gcnew MyClass() }
   };

   for ( int i = 0 ; i < ARRAY_SIZE ; i++, size_of_array += 4 )
      for ( int k = 0 ; k < ARRAY_SIZE ; k++ )
         MyClass0[i][k] -> m_i = i;

   for ( int i = 0 ; i < ARRAY_SIZE ; i++ )
      for ( int j = 0 ; j < ARRAY_SIZE ; j++ )
         Console::WriteLine("MyClass0[{0}] = {1}", i, MyClass0[i][j] -> m_i);
   Console::WriteLine();

   // Declares an array of value types and performs an aggregate initialization.
   array< array< Int32 >^ >^ IntArray = gcnew array<array< Int32 >^> {
      gcnew array<Int32>{1,2},
      gcnew array<Int32>{3,4,5}
   };

   for each ( array<int>^ outer in IntArray ) {
      Console::Write("[");

      for each( int i in outer )
         Console::Write(" {0}", i);

      Console::Write(" ]");
      Console::WriteLine();
   }
   Console::WriteLine();

   // Declares and initializes an array of pointers to a native type.
   array<array< MyNativeClass * >^ > ^ MyClass2 =
      gcnew array<array< MyNativeClass * > ^> {
         gcnew array<MyNativeClass *>{ new MyNativeClass(), new MyNativeClass() },
         gcnew array<MyNativeClass *>{ new MyNativeClass(), new MyNativeClass(), new MyNativeClass() }
      };

   for each ( array<MyNativeClass *> ^ outer in MyClass2 )
      for each( MyNativeClass* i in outer )
         i->m_i = count++;

   for each ( array<MyNativeClass *> ^ outer in MyClass2 ) {
      Console::Write("[");
      for each( MyNativeClass* i in outer )
         Console::Write(" {0}", i->m_i);
      Console::Write(" ]");
      Console::WriteLine();
   }
   Console::WriteLine();

   // Declares and initializes an array of two-dimensional arrays of strings.
   array<array<String ^,2> ^> ^gc3 = gcnew array<array<String ^,2> ^>{
      gcnew array<String ^>{ {"a","b"}, {"c", "d"}, {"e","f"} },
      gcnew array<String ^>{ {"g", "h"} }
   };

   for each ( array<String^, 2> ^ outer in gc3 ){
      Console::Write("[");
      for each( String ^ i in outer )
         Console::Write(" {0}", i);
      Console::Write(" ]");
      Console::WriteLine();
   }
}
```

```Output
MyClass0[0] = 0
MyClass0[0] = 0
MyClass0[1] = 1
MyClass0[1] = 1

[ 1 2 ]
[ 3 4 5 ]

[ 0 1 ]
[ 2 3 4 ]

[ a b c d e f ]
[ g h ]
```

## <a name="managed-arrays-as-template-type-parameters"></a>テンプレート型パラメーターとして配列を管理します。

この例では、マネージ配列をテンプレートにパラメーターとして使用する方法を示します。

```cpp
// mcppv2_template_type_params.cpp
// compile with: /clr
using namespace System;
template <class T>
class TA {
public:
   array<array<T>^>^ f() {
      array<array<T>^>^ larr = gcnew array<array<T>^>(10);
      return larr;
   }
};

int main() {
   int retval = 0;
   TA<array<array<Int32>^>^>* ta1 = new TA<array<array<Int32>^>^>();
   array<array<array<array<Int32>^>^>^>^ larr = ta1->f();
   retval += larr->Length - 10;
   Console::WriteLine("Return Code: {0}", retval);
}
```

```Output
Return Code: 0
```

## <a name="typedefs-for-managed-arrays"></a>マネージ配列の typedef

この例では、マネージ配列の typedef を作成する方法を示します。

```cpp
// mcppv2_typedef_arrays.cpp
// compile with: /clr
using namespace System;
ref class G {};

typedef array<array<G^>^> jagged_array;

int main() {
   jagged_array ^ MyArr = gcnew jagged_array (10);
}
```

## <a name="sorting-arrays"></a>配列の並べ替え

標準の C++ 配列とは異なりマネージ配列は、共通の動作を継承する元となる配列の基本クラスから暗黙的に派生します。 例としては、`Sort`メソッドは、配列内の項目の並べ替えに使用できます。

呼び出すことができます、基本的な組み込み型を含む配列に対して、`Sort`メソッド。 並べ替えの条件をオーバーライドしては、必要な複雑な型の配列の並べ替えを行うときにします。 この場合、配列要素の型を実装する必要があります、<xref:System.IComparable.CompareTo%2A>メソッド。

```cpp
// array_sort.cpp
// compile with: /clr
using namespace System;

int main() {
   array<int>^ a = { 5, 4, 1, 3, 2 };
   Array::Sort( a );
   for (int i=0; i < a->Length; i++)
      Console::Write("{0} ", a[i] );
}
```

## <a name="sorting-arrays-by-using-custom-criteria"></a>カスタム条件を使用して配列の並べ替え

基本的な組み込み型を含む配列を並べ替えるを呼び出すだけです、`Array::Sort`メソッド。 ただし、複合型を含んでいるか、既定の並べ替え条件を上書きするにはオーバーライド並べ替え配列を<xref:System.IComparable.CompareTo%2A>メソッド。

構造体では、次の例では、名前`Element`から派生<xref:System.IComparable>、提供に書き込まれると、<xref:System.IComparable.CompareTo%2A>並べ替え条件として 2 つの整数の平均値を使用するメソッド。

```cpp
using namespace System;

value struct Element : public IComparable {
   int v1, v2;

   virtual int CompareTo(Object^ obj) {
      Element^ o = dynamic_cast<Element^>(obj);
      if (o) {
         int thisAverage = (v1 + v2) / 2;
         int thatAverage = (o->v1 + o->v2) / 2;
         if (thisAverage < thatAverage)
            return -1;
         else if (thisAverage > thatAverage)
            return 1;
         return 0;
         }
      else
         throw gcnew ArgumentException
      ("Object must be of type 'Element'");
   }
};

int main() {
   array<Element>^ a = gcnew array<Element>(10);
   Random^ r = gcnew Random;

   for (int i=0; i < a->Length; i++) {
      a[i].v1 = r->Next() % 100;
      a[i].v2 = r->Next() % 100;
   }

   Array::Sort( a );
   for (int i=0; i < a->Length; i++) {
      int v1 = a[i].v1;
      int v2 = a[i].v2;
      int v = (v1 + v2) / 2;
      Console::WriteLine("{0}  (({1}+{2})/2) ", v, v1, v2);
   }
}
```

## <a name="array-covariance"></a>配列の共変性

直接または間接基本クラス B を持つ参照クラス D を指定するには、種類 D の配列割り当てることができますをタイプ b の配列変数

```cpp
// clr_array_covariance.cpp
// compile with: /clr
using namespace System;

int main() {
   // String derives from Object.
   array<Object^>^ oa = gcnew array<String^>(20);
}
```

配列要素への代入は代入互換性純益、配列の動的な型を使用します。 互換性のない型を持つ配列要素への代入と`System::ArrayTypeMismatchException`がスローされます。

値クラス型の配列には、配列の共変性は適用されません。 たとえば、int32 型の配列をオブジェクトに変換できません ^ 配列、ボックス化を使用してもありません。

```cpp
// clr_array_covariance2.cpp
// compile with: /clr
using namespace System;

ref struct Base { int i; };
ref struct Derived  : Base {};
ref struct Derived2 : Base {};
ref struct Derived3 : Derived {};
ref struct Other { short s; };

int main() {
   // Derived* d[] = new Derived*[100];
   array<Derived^> ^ d = gcnew array<Derived^>(100);

   // ok by array covariance
   array<Base ^> ^  b = d;

   // invalid
   // b[0] = new Other;

   // error (runtime exception)
   // b[1] = gcnew Derived2;

   // error (runtime exception),
   // must be "at least" a Derived.
   // b[0] = gcnew Base;

   b[1] = gcnew Derived;
   b[0] = gcnew Derived3;
}
```

## <a name="see-also"></a>関連項目

[配列](../extensions/arrays-cpp-component-extensions.md)
