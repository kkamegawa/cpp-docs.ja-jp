---
title: ジェネリック関数 (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- functions [C++], generic
- generic methods
- generics [C++], functions
- methods [C++], generic
- generic functions
ms.assetid: 8e409364-58f9-4360-b486-e7d555e0c218
ms.openlocfilehash: a4a1702c8b9902f5265a8a5f92316d7c82751609
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516377"
---
# <a name="generic-functions-ccli"></a>ジェネリック関数 (C++/CLI)

ジェネリック関数は、型パラメーターで宣言される関数です。 呼び出されると、型パラメーターではなく実際の型が使用されます。

## <a name="all-platforms"></a>すべてのプラットフォーム

### <a name="remarks"></a>解説

この機能は、すべてのプラットフォームには適用されません。

## <a name="windows-runtime"></a>Windows ランタイム

### <a name="remarks"></a>解説

Windows ランタイムでは、この機能はサポートされていません。

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

ジェネリック関数は、型パラメーターで宣言される関数です。 呼び出されると、型パラメーターではなく実際の型が使用されます。

### <a name="syntax"></a>構文

```cpp
[attributes] [modifiers]
return-type identifier<type-parameter identifier(s)>
[type-parameter-constraints clauses]

([formal-parameters])
{function-body}
```

### <a name="parameters"></a>パラメーター

*属性*<br/>
(省略可能) 追加の宣言情報。 属性と属性クラスについては、「属性」を参照してください。

*modifiers*<br/>
(省略可能) 関数の修飾子です (static など)。  仮想メソッドはジェネリックではない可能性があるため、**virtual** は許可されません。

*return-type*<br/>
メソッドによって返される型。 戻り値が void の場合、戻り値は要求されません。

*identifier*<br/>
関数名。

*type-parameter identifier(s)*<br/>
コンマ区切りの識別子の一覧。

*formal-parameters*<br/>
(省略可能) パラメーターの一覧。

*type-parameter-constraints-clauses*<br/>
これは、型引数として使用できる型に対する制約を指定し、「[ジェネリック型パラメーターの制約 (C++/CLI)](constraints-on-generic-type-parameters-cpp-cli.md)」に指定されている書式を使用します。

*function-body*<br/>
型パラメーターの識別子を参照できるメソッドの本体。

### <a name="remarks"></a>解説

ジェネリック関数は、ジェネリック型パラメーターで宣言される関数です。 クラスまたは構造体のメソッド、またはスタンドアロン関数が可能です。 単一のジェネリック宣言は、ジェネリック型パラメーターに置換される実際の型だけが異なる関数ファミリを暗黙的に宣言します。

クラスまたは構造体のコンストラクターは、ジェネリック型パラメーターで宣言することはできません。

呼び出されると、ジェネリック型パラメーターは、実際の型に置換されます。 テンプレート関数の呼び出しに似た構文を使用して、実際の型を山かっこで囲んで明示的に指定できます。 型パラメーターなしで呼び出すと、コンパイラは、関数呼び出しで提供されたパラメーターから実際の型を推測しようとします。 使用しているパラメーターから目的の型引数を推測できない場合、コンパイラはエラーを報告します。

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次のコード例では、ジェネリック関数を示します。

```cpp
// generics_generic_function_1.cpp
// compile with: /clr
generic <typename ItemType>
void G(int i) {}

ref struct A {
   generic <typename ItemType>
   void G(ItemType) {}

   generic <typename ItemType>
   static void H(int i) {}
};

int main() {
   A myObject;

   // generic function call
   myObject.G<int>(10);

   // generic function call with type parameters deduced
   myObject.G(10);

   // static generic function call
   A::H<int>(10);

   // global generic function call
   G<int>(10);
}
```

ジェネリック関数は、関数の署名またはアリティ (型パラメーターの数) に基づいてオーバー ロードできます。 また、ジェネリック関数は、いくつかの型パラメーターが異なっている限り、同じ名前の非ジェネリック関数でオーバー ロードできます。 たとえば、次の関数をオーバー ロードできます。

```cpp
// generics_generic_function_2.cpp
// compile with: /clr /c
ref struct MyClass {
   void MyMythod(int i) {}

   generic <class T>
   void MyMythod(int i) {}

   generic <class T, class V>
   void MyMythod(int i) {}
};
```

次の例では、ジェネリック関数を使用して、配列内の最初の要素を検索します。 `MyClass` を宣言し、基底クラス `MyBaseClass` から継承します。 `MyClass` には、基底クラス内の別のジェネリック関数 `MyBaseClassFunction` を呼び出すジェネリック関数 `MyFunction` が含まれます。 `main` で、別の型引数を使用して、ジェネリック関数 `MyFunction` が呼び出されます。

```cpp
// generics_generic_function_3.cpp
// compile with: /clr
using namespace System;

ref class MyBaseClass {
protected:
   generic <class ItemType>
   ItemType MyBaseClassFunction(ItemType item) {
      return item;
   }
};

ref class MyClass: public MyBaseClass {
public:
   generic <class ItemType>
   ItemType MyFunction(ItemType item) {
      return MyBaseClass::MyBaseClassFunction<ItemType>(item);
   }
};

int main() {
   MyClass^ myObj = gcnew MyClass();

   // Call MyFunction using an int.
   Console::WriteLine("My function returned an int: {0}",
                           myObj->MyFunction<int>(2003));

   // Call MyFunction using a string.
   Console::WriteLine("My function returned a string: {0}",
   myObj->MyFunction<String^>("Hello generic functions!"));
}
```

```Output
My function returned an int: 2003
My function returned a string: Hello generic functions!
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)<br/>
[ジェネリック](generics-cpp-component-extensions.md)
