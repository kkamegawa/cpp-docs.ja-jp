---
title: コンパイラ エラー C3833
ms.date: 11/04/2016
f1_keywords:
- C3833
helpviewer_keywords:
- C3833
ms.assetid: 8152be53-e01e-48cd-9eef-9de38723664c
ms.openlocfilehash: c762ca80dc52398d9f246ada86ab29cb6e902129
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741548"
---
# <a name="compiler-error-c3833"></a>コンパイラ エラー C3833

' type ': pointer_type のターゲット型が無効です

[Interior_ptr](../../extensions/interior-ptr-cpp-cli.md)または[pin_ptr](../../extensions/pin-ptr-cpp-cli.md)が正しく宣言されていません。

次の例では、C3833 が生成されます。

```cpp
// C3833.cpp
// compile with: /clr

ref class MyClass {
public:
   int data;
   MyClass() : data(35) {}
};

int main() {
   interior_ptr<MyClass> p;   // C3833

   // OK
   MyClass ^ h_MyClass = gcnew MyClass;
   interior_ptr<int> i = &(h_MyClass->data);
   System::Console::WriteLine(*i);
}
```

次の例では、C3833 が生成されます。

```cpp
// C3833b.cpp
// compile with: /clr /c
ref class G {
public:
   int i;
};

int main() {
   G ^ pG = gcnew G;
   pin_ptr<G> ppG = &pG;   // C3833 can't pin a whole object

   // OK
   pin_ptr<int> ppG2 = &pG->i;
   *ppG2 = 54;
   int * pi = ppG2;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(*ppG2);

   *pi = 55;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(*ppG2);

   *ppG2 = 56;
   System::Console::WriteLine(*pi);
   System::Console::WriteLine(*ppG2);
}
```
