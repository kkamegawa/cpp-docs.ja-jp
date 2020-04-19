---
title: コンパイラ エラー C3699
ms.date: 11/04/2016
f1_keywords:
- C3699
helpviewer_keywords:
- C3699
ms.assetid: 47c29afc-ab8b-4238-adfe-788dd6e00b3b
ms.openlocfilehash: ec902266550e591623894823e6336bd2436bfbd5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758035"
---
# <a name="compiler-error-c3699"></a>コンパイラ エラー C3699

' operator ': この間接参照を型 ' type ' で使用することはできません

`type`で許可されていない間接参照を使用しようとしました。

## <a name="example"></a>使用例

次の例では、C3699 が生成されます。

```cpp
// C3699.cpp
// compile with: /clr /c
using namespace System;
int main() {
   String * s;   // C3699
   // try the following line instead
   // String ^ s2;
}
```

## <a name="example"></a>使用例

Trivial プロパティに参照型を含めることはできません。 詳細については、「 [property](../../extensions/property-cpp-component-extensions.md) 」を参照してください。 次の例では、C3699 が生成されます。

```cpp
// C3699_b.cpp
// compile with: /clr /c
ref struct C {
   property System::String % x;   // C3699
   property System::String ^ y;   // OK
};
```

## <a name="example"></a>使用例

"ポインターへのポインター" 構文に相当するものは、追跡参照へのハンドルです。 次の例では、C3699 が生成されます。

```cpp
// C3699_c.cpp
// compile with: /clr /c
using namespace System;
void Test(String ^^ i);   // C3699
void Test2(String ^% i);
```
