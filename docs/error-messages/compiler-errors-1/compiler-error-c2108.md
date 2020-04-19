---
title: コンパイラ エラー C2108
ms.date: 11/04/2016
f1_keywords:
- C2108
helpviewer_keywords:
- C2108
ms.assetid: c84f0b47-5e2c-47d2-8edb-427a40e17c36
ms.openlocfilehash: 069f369627f42314cc14688a9e0c0a55808db507
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752029"
---
# <a name="compiler-error-c2108"></a>コンパイラ エラー C2108

添字に整数でない型が使われました。

配列の添字が整数式ではありません。

## <a name="example"></a>使用例

C2108 は、型の既定のインデクサーにアクセスするために値型の `this` ポインターを誤って使用した場合に発生する可能性があります。 詳細については、「 [this ポインターのセマンティクス](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Semantics_of_the_this_pointer)」を参照してください。

次の例では、C2108 が生成されます。

```cpp
// C2108.cpp
// compile with: /clr
using namespace System;

value struct B {
   property Double default[Double] {
      Double get(Double data) {
         return data*data;
      }
   }
   void Test() {
      Console::WriteLine("{0}", this[3.3]);   // C2108
      Console::WriteLine("{0}", this->default[3.3]);   // OK
   }
};

int main() {
   B ^ myb = gcnew B();
   myb->Test();
}
```
