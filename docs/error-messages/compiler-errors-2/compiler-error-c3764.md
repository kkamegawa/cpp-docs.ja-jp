---
title: コンパイラ エラー C3764
ms.date: 11/04/2016
f1_keywords:
- C3764
helpviewer_keywords:
- C3764
ms.assetid: af5d254c-8d4a-4dda-aad9-3c5c1257c868
ms.openlocfilehash: 3ede846c9068978ad5d283e97b1c96d3527bf67c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757236"
---
# <a name="compiler-error-c3764"></a>コンパイラ エラー C3764

' override_function ': 基底クラスのメソッド ' base_class_function ' をオーバーライドできません

コンパイラで、正しくない形式のオーバーライドが検出されました。 たとえば、基底クラスの関数が `virtual`ませんでした。 詳細については、「 [override](../../extensions/override-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3764 が生成されます。

```cpp
// C3764.cpp
// compile with: /clr /c
public ref struct A {
   void g(int);
   virtual void h(int);
};

public ref struct B : A {
   virtual void g(int) override {}   // C3764
   virtual void h(int) override {}   // OK
};
```

## <a name="example"></a>使用例

C3764 は、基底クラスのメソッドが明示的かつ名前付きでオーバーライドされた場合にも発生することがあります。 次の例では、C3764 が生成されます。

```cpp
// C3764_b.cpp
// compile with: /clr /c
ref struct A {
   virtual void Test() {}
};

ref struct B : public A {
   virtual void Test() override {}
   virtual void Test2() = A::Test {}   // C3764
};
```
