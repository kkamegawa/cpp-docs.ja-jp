---
title: 汎用デリゲート (C++/CLI)
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- generic delegates
- delegates, generic [C++]
ms.assetid: 09d430b2-1aef-4fbc-87f9-9d7b8185d798
ms.openlocfilehash: 449659126f52997d548ebd7785a78c1200038ee6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515767"
---
# <a name="generic-delegates-ccli"></a>汎用デリゲート (C++/CLI)

デリゲートでジェネリック型パラメーターを使用できます。 デリゲートの詳細については、「[delegate (C++/CLI and C++/CX) (デリゲート (C++/CLI および C++/CX))](delegate-cpp-component-extensions.md)」を参照してください。

## <a name="syntax"></a>構文

```cpp
[attributes]
generic < [class | typename] type-parameter-identifiers>
[type-parameter-constraints-clauses]
[accessibility-modifiers] delegate result-type identifier
([formal-parameters]);
```

### <a name="parameters"></a>パラメーター

*attributes*<br/>
(省略可能) 追加の宣言情報。 属性と属性クラスについては、「属性」を参照してください。

*type-parameter-identifier(s)*<br/>
型パラメーターのコンマ区切りの識別子の一覧。

*type-parameter-constraints-clauses*<br/>
「[Constraints on Generic Type Parameters (C++/CLI) ジェネリック型パラメーターの制約 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)」に指定された書式を使用します。

*accessibility-modifiers*<br/>
(省略可能) アクセシビリティ修飾子 (例: **public**、**private**)。

*result-type*<br/>
デリゲートの戻り値の型。

*identifier*<br/>
デリゲートの名前。

*formal-parameters*<br/>
(省略可能) デリゲートのパラメーターの一覧。

## <a name="example"></a>例

デリゲート型パラメーターは、デリゲート オブジェクトが作成されるポイントで指定されます。 デリゲートとそれに関連付けられているメソッドの両方に、同じシグネチャを含める必要があります。 汎用デリゲート宣言の例を次に示します。

```cpp
// generics_generic_delegate1.cpp
// compile with: /clr /c
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);
```

## <a name="example"></a>例

次の例は、以下を示しています。

- 同じデリゲート オブジェクトを、異なる構築された型で使用することはできません。 型が異なる別のデリゲート オブジェクトを作成してください。

- 汎用デリゲートを汎用メソッドに関連付けることができます。

- ジェネリック メソッドが型引数を指定せずに呼び出されると、コンパイラは、その呼び出しの型引数を推論しようとします。

```cpp
// generics_generic_delegate2.cpp
// compile with: /clr
generic <class ItemType>
delegate ItemType GenDelegate(ItemType p1, ItemType% p2);

generic <class ItemType>
ref struct MyGenClass {
   ItemType MyMethod(ItemType i, ItemType % j) {
      return ItemType();
   }
};

ref struct MyClass {
   generic <class ItemType>
   static ItemType MyStaticMethod(ItemType i, ItemType % j) {
      return ItemType();
   }
};

int main() {
   MyGenClass<int> ^ myObj1 = gcnew MyGenClass<int>();
   MyGenClass<double> ^ myObj2 = gcnew MyGenClass<double>();
   GenDelegate<int>^ myDelegate1 =
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);

   GenDelegate<double>^ myDelegate2 =
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);

   GenDelegate<int>^ myDelegate =
      gcnew GenDelegate<int>(&MyClass::MyStaticMethod<int>);
}
```

## <a name="example"></a>例

次の例では、汎用デリゲート `GenDelegate<ItemType>` を宣言した後、それを型パラメーター `ItemType` を使用する `MyMethod` メソッドに関連付けることによってインスタンス化します。 デリゲートの 2 つのインスタンス (integerと double) が作成されて呼び出されます。

```cpp
// generics_generic_delegate.cpp
// compile with: /clr
using namespace System;

// declare generic delegate
generic <typename ItemType>
delegate ItemType GenDelegate (ItemType p1, ItemType% p2);

// Declare a generic class:
generic <typename ItemType>
ref class MyGenClass {
public:
   ItemType MyMethod(ItemType p1, ItemType% p2) {
      p2 = p1;
      return p1;
    }
};

int main() {
   int i = 0, j = 0;
   double m = 0.0, n = 0.0;

   MyGenClass<int>^ myObj1 = gcnew MyGenClass<int>();
   MyGenClass<double>^ myObj2 = gcnew MyGenClass<double>();

   // Instantiate a delegate using int.
   GenDelegate<int>^ MyDelegate1 =
      gcnew GenDelegate<int>(myObj1, &MyGenClass<int>::MyMethod);

   // Invoke the integer delegate using MyMethod.
   i = MyDelegate1(123, j);

   Console::WriteLine(
      "Invoking the integer delegate: i = {0}, j = {1}", i, j);

   // Instantiate a delegate using double.
   GenDelegate<double>^ MyDelegate2 =
      gcnew GenDelegate<double>(myObj2, &MyGenClass<double>::MyMethod);

   // Invoke the integer delegate using MyMethod.
   m = MyDelegate2(0.123, n);

   Console::WriteLine(
      "Invoking the double delegate: m = {0}, n = {1}", m, n);
}
```

```Output
Invoking the integer delegate: i = 123, j = 123
Invoking the double delegate: m = 0.123, n = 0.123
```

## <a name="see-also"></a>関連項目

[ジェネリック](generics-cpp-component-extensions.md)