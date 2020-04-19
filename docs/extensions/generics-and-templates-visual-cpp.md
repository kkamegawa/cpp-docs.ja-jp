---
title: ジェネリックとテンプレート (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
ms.openlocfilehash: 74cfd791e8400b788d38f272eed3d421ca4230e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516357"
---
# <a name="generics-and-templates-ccli"></a>ジェネリックとテンプレート (C++/CLI)

ジェネリックとテンプレートは、どちらもパラメーター化された型のサポートを提供する言語機能です。 ただし、それらは同じではなく、用途が異なっています。 このトピックでは、多くの相違点について、その概要を説明します。

詳細については、「[Windows ランタイムおよびマネージド テンプレート (C++/CLI および C++/CX)](windows-runtime-and-managed-templates-cpp-component-extensions.md)」を参照してください。

## <a name="comparing-templates-and-generics"></a>テンプレートとジェネリックの比較

ジェネリックと C++ テンプレートの重要な相違点:

- ジェネリックは、実行時にそれらが型に置き換えられるまではジェネリックのままです。 テンプレートはコンパイル時に特殊化され、実行時にパラメーター化されていない型のままではありません。

- 共通言語ランタイムでは、特に MSIL でジェネリックをサポートします。 このランタイムではジェネリック型が認識されるため、ジェネリック型を含むアセンブリの参照時に、ジェネリック型を特定の型に置き換えることができます。 これに対し、テンプレートでは、コンパイル時に通常の型に解決され、他のアセンブリではその型を特殊化できない場合があります。

- 2 つの異なるアセンブリで同じ型引数に特殊化されたジェネリックは、同じ型になります。 2 つの異なるアセンブリで同じ型引数に特殊化されたテンプレートは、実行時に異なる型とみなされます。

- ジェネリックは、すべての参照型の引数で使用される単一の実行可能コードとして生成されます (これは値型には当てはまりません。値型には、値型ごとに独自の実装があります)。 JIT コンパイラではジェネリックが認識されるるため、型引数として使用される参照型または値型のコードを最適化できます。 テンプレートは、それぞれの特殊化に対して、個別のランタイム コードを生成します。

- ジェネリックでは、`template <int i> C {}` などのテンプレートの型パラメーターではないパラメーターは許可されません。 テンプレートでは可能です。

- ジェネリックでは、明示的な特殊化 (特定の型用のテンプレートのカスタム実装) は許可されません。 テンプレートでは可能です。

- ジェネリックでは、部分的な特殊化 (型引数のサブセットのカスタム実装) は許可されません。 テンプレートでは可能です。

- ジェネリックでは、ジェネリック型の基底クラスとしての型パラメーターは許可されません。 テンプレートでは可能です。

- テンプレートでは、テンプレート対テンプレートのパラメーター (例: `template<template<class T> class X> class MyClass`) をサポートしますが、ジェネリックではサポートしません。

## <a name="combining-templates-and-generics"></a>テンプレートとジェネリックの組み合わせ

ジェネリックの基本的な相違点には、テンプレートとジェネリックを組み合わせたアプリケーションをビルドするという言外の意味があります。 たとえば、テンプレートを他の言語にジェネリックとして公開するためのジェネリック ラッパーを作成したいテンプレート クラスがあるとします。 テンプレートではコンパイル時に型パラメーターが必要ですが、ジェネリックでは型は実行時まで解決されないため、テンプレートに渡される型パラメーターをジェネリックで使用することはできません。 コンパイル時にテンプレートを展開して実行時にインスタンス化できる任意のジェネリック型にする方法はないため、ジェネリックの中にテンプレートを入れ子にしても機能しません。

## <a name="example"></a>例

### <a name="description"></a>説明

次の例では、テンプレートとジェネリックを一緒に使用する単純な例を示します。 この例では、テンプレート クラスがジェネリック型にそのパラメーターを渡します。 逆は不可能です。

この方法は、C++/CLI アセンブリにとってローカルなテンプレート コードを既存のジェネリック API 上にビルドするか、ジェネリック型にパラメーター化の層を追加して、ジェネリックではサポートされていないテンプレートの特定の機能を利用する場合に使用できます。

### <a name="code"></a>コード

```cpp
// templates_and_generics.cpp
// compile with: /clr
using namespace System;

generic <class ItemType>
ref class MyGeneric {
   ItemType m_item;

public:
   MyGeneric(ItemType item) : m_item(item) {}
   void F() {
      Console::WriteLine("F");
   }
};

template <class T>
public ref class MyRef {
MyGeneric<T>^ ig;

public:
   MyRef(T t) {
      ig = gcnew MyGeneric<T>(t);
      ig->F();
    }
};

int main() {
   // instantiate the template
   MyRef<int>^ mref = gcnew MyRef<int>(11);
}
```

```Output
F
```

## <a name="see-also"></a>関連項目

[ジェネリック](generics-cpp-component-extensions.md)