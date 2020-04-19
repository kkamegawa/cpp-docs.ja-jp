---
title: コンパイラ エラー C3830
ms.date: 11/04/2016
f1_keywords:
- C3830
helpviewer_keywords:
- C3830
ms.assetid: c9798f88-5001-4067-9fb1-09957ddc6fa8
ms.openlocfilehash: 14272d2c0b0f8de63f55d2ba3d1c01cf04e0dfbd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741639"
---
# <a name="compiler-error-c3830"></a>コンパイラ エラー C3830

' type1 ': ' type1 ' から継承することはできません。値型はインターフェイスクラスからのみ継承できます

値型は基底クラスを継承できません。  詳細については、「[クラスと構造体](../../extensions/classes-and-structs-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3830 が生成されます。

```cpp
// C3830a.cpp
// compile with: /clr /c
public value struct MyStruct4 {
   int i;
};

public value class MyClass : public MyStruct4 {};   // C3830

// OK
public interface struct MyInterface4 {
   void i();
};

public value class MyClass2 : public MyInterface4 {
public:
   virtual void i(){}
};
```
