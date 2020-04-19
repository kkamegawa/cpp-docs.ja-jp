---
title: ジェネリック型パラメーターの制約 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- where
helpviewer_keywords:
- where keyword [C++]
- constraints, C++
ms.assetid: eb828cc9-684f-48a3-a898-b327700c0a63
ms.openlocfilehash: 6eefb6a7d888a031f6ff7f88d08da4d67a4dc8c3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516207"
---
# <a name="constraints-on-generic-type-parameters-ccli"></a>ジェネリック型パラメーターの制約 (C++/CLI)

ジェネリック型またはメソッドの宣言では、型パラメーターを制約で修飾できます。 制約は、型引数として使用される型が満たす必要がある要件です。 たとえば、型引数で特定のインターフェイスを実装するか特定のクラスから継承する必要があるという制約が可能です。

制約は省略可能です。パラメーターに制約の指定がないことは、そのパラメーターを <xref:System.Object> に制限するのと同じです。

## <a name="syntax"></a>構文

```cpp
where type-parameter: constraint list
```

### <a name="parameters"></a>パラメーター

*type-parameter*<br/>
制約が適用される、いずれかの型パラメーター。

*constraint list*<br/>
*constraint list* は、制約の指定のコンマ区切りの一覧です。 一覧には、型パラメーターによって実装されるインターフェイスを含めることができます。

一覧には、クラスを含めることもできます。 型引数で基底クラスの制約を満たすには、制約と同じクラスにするか、制約から派生する必要があります。

**gcnew()** を指定して型引数にパラメーターのないコンストラクターが含まれている必要があること、または **ref class** を指定して型引数に参照型 (任意のクラス、インターフェイス、デリゲート、または配列型) が含まれている必要があること、または **value class** を指定して型引数に値型が含まれていることを指定することもできます。 Nullable\<T> を除く任意の値型を指定できます。

制約としてジェネリック パラメーターを指定することもできます。 制約が適用されている型に提供される型引数は、制約の型から派生する必要があります。 これは、生の型制約と呼ばれます。

## <a name="remarks"></a>解説

制約句は **where**、型パラメーター、コロン ( **:** )、および制約で構成され、型パラメーターに対する制約の性質を規定します。 **where** は状況依存キーワードです。詳細については、「[状況依存キーワード](context-sensitive-keywords-cpp-component-extensions.md)」を参照してください。 複数の **where** 句はスペースで分離します。

制約を型パラメーターに適用して、ジェネリック型またはメソッドの引数として使用できる型に制限を課します。

クラスまたはインターフェイスの制約では、引数の型が特定のクラスである、特定のクラスから継承される、または特定のインターフェイスを実装する必要があることを指定します。

ジェネリック型またはメソッドに対する制約の適用によって、その型またはメソッドのコードで、制約付きの型の既知の機能を活用できます。 たとえば、型パラメーターで `IComparable<T>` インターフェイスが実装されるようにジェネリック クラスを宣言できます。

```cpp
// generics_constraints_1.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : IComparable<T>
ref class List {};
```

この制約では、`T` で使用される型引数は、コンパイル時に `IComparable<T>` を実装することを要求します。 `CompareTo` などのインター フェイスメソッドを呼び出すこともできます。 インターフェイス メソッドを呼び出す型パラメーターのインスタンスへのキャストは必要ありません。

型パラメーターを介して型引数のクラスの静的メソッドを呼び出すことはできません。それらは、実際の名前付きの型を介してのみ呼び出すことができます。

**int** や **double** などの組み込み型を含め、制約を値型にすることはできません。 値型は派生クラスを持つことができないため、1 つのクラスのみが制約を満たすことができます。 その場合は、特定の値の型に置き換えられた型パラメーターを使用して、ジェネリックを書き換えることができます。

不明な型でメソッドやインターフェイスがサポートされていることが制約で示唆されない限り、コンパイラで不明な型のメソッドやその他の機能は使用できないため、制約が必要な場合があります。

同じ型パラメーターに対して、コンマ区切りの一覧で複数の制約を指定できます。

```cpp
// generics_constraints_2.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;
generic <typename T>
where T : List<T>, IComparable<T>
ref class List {};
```

複数の型パラメーターがある場合は、型パラメーターごとに 1 つの **where** 句を使用します。 次に例を示します。

```cpp
// generics_constraints_3.cpp
// compile with: /c /clr
using namespace System;
using namespace System::Collections::Generic;

generic <typename K, typename V>
   where K: IComparable<K>
   where V: IComparable<K>
ref class Dictionary {};
```

まとめると、コードでは、次の規則に従って制約を使用します。

- 複数の制約を一覧で指定する場合は、任意の順序で指定できます。

- 制約は、抽象基底クラスなどのクラス型も可能です。 ただし、制約は、値型またはシール クラスをすることはできません。

- 制約自体が型パラメーターになることはできませんが、オープン構築型の型パラメーターを含めることができます。 次に例を示します。

    ```cpp
    // generics_constraints_4.cpp
    // compile with: /c /clr
    generic <typename T>
    ref class G1 {};

    generic <typename Type1, typename Type2>
    where Type1 : G1<Type2>   // OK, G1 takes one type parameter
    ref class G2{};
    ```

## <a name="example"></a>例

次の例では、制約を使用して、型パラメーターでインスタンス メソッドを呼び出すことを示します。

```cpp
// generics_constraints_5.cpp
// compile with: /clr
using namespace System;

interface class IAge {
   int Age();
};

ref class MyClass {
public:
   generic <class ItemType> where ItemType : IAge
   bool isSenior(ItemType item) {
      // Because of the constraint,
      // the Age method can be called on ItemType.
      if (item->Age() >= 65)
         return true;
      else
         return false;
   }
};

ref class Senior : IAge {
public:
   virtual int Age() {
      return 70;
   }
};

ref class Adult: IAge {
public:
   virtual int Age() {
      return 30;
   }
};

int main() {
   MyClass^ ageGuess = gcnew MyClass();
   Adult^ parent = gcnew Adult();
   Senior^ grandfather = gcnew Senior();

   if (ageGuess->isSenior<Adult^>(parent))
      Console::WriteLine("\"parent\" is a senior");
   else
      Console::WriteLine("\"parent\" is not a senior");

   if (ageGuess->isSenior<Senior^>(grandfather))
      Console::WriteLine("\"grandfather\" is a senior");
   else
      Console::WriteLine("\"grandfather\" is not a senior");
}
```

```Output
"parent" is not a senior
"grandfather" is a senior
```

## <a name="example"></a>例

制約としてジェネリック型パラメーターを使用すると、生の型制約が呼び出されます。 生の型制約は、独自の型パラメーターを持つ名前付き関数で、パラメーターの型パラメーターをコンテナー型に制限する必要がある場合に有用です。

次の例では、`T` が `Add` メソッドのコンテキストでの生の型制約になります。

生の型制約は、ジェネリック クラス定義でも使用できます。 ジェネリック クラスでの生の型制約としての有用性は限られています。これは、コンパイラでは、<xref:System.Object> から派生することを除き、生の型制約に関して想定できることがないためです。 2 つの型パラメーター間に継承関係を適用するシナリオには、ジェネリック クラスに対する生の型制約を使用してください。

```cpp
// generics_constraints_6.cpp
// compile with: /clr /c
generic <class T>
ref struct List {
   generic <class U>
   where U : T
   void Add(List<U> items)  {}
};

generic <class A, class B, class C>
where A : C
ref struct SampleClass {};
```

## <a name="see-also"></a>関連項目

[ジェネリック](generics-cpp-component-extensions.md)