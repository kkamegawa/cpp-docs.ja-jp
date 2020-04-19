---
title: コンパイラ エラー C3915
ms.date: 11/04/2016
f1_keywords:
- C3915
helpviewer_keywords:
- C3915
ms.assetid: 2b0a5e5f-3aec-4a4b-9157-233031817084
ms.openlocfilehash: 26fdcd3b7989d9030249133e6dc1d277aa1a9f44
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756280"
---
# <a name="compiler-error-c3915"></a>コンパイラ エラー C3915

' type ' には、既定のインデックス付きプロパティ (クラスインデクサー) がありません

型には、既定のインデックス付きプロパティがありません。

詳細については、「 [property](../../extensions/property-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3915 が生成されます。

```cpp
// C3915.cpp
// compile with: /clr
ref class X {
public:
// uncomment property to resolve this C3915
//   property int default[]
//   {
//      int get(int i)
//      {
//         return 863;
//      }
//   }
};

int main() {
   X^ x = new X;
   System::Console::WriteLine(x[1]);   // C3915
}
```

## <a name="example"></a>使用例

また、C3915 <xref:System.Reflection.DefaultMemberAttribute>で定義されているのと同じコンパイル単位で既定のインデクサーを使用しようとした場合にも発生する可能性があります。

次の例では、C3915 が生成されます。

```cpp
// C3915_b.cpp
// compile with: /clr
using namespace System;

[Reflection::DefaultMember("XXX")]
ref struct A {
   property Double XXX[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
};

ref struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
};

int main() {
   A ^ mya = gcnew A();
   Console::WriteLine("{0}", mya[3]);   // C3915

   B ^ myb = gcnew B();
   Console::WriteLine("{0}", myb[3]);   // OK
}
```
