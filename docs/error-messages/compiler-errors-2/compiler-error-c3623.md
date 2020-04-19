---
title: コンパイラ エラー C3623
ms.date: 11/04/2016
f1_keywords:
- C3623
helpviewer_keywords:
- C3623
ms.assetid: a0341b45-062a-4f67-beb9-ba74201ed1ed
ms.openlocfilehash: 5d83e75d46fb078db3e74bf389563ca2ff34bb61
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740872"
---
# <a name="compiler-error-c3623"></a>コンパイラ エラー C3623

'variable': ビット フィールドは、マネージド型または WinRT 型ではサポートされていません。

マネージド クラスまたは WinRT クラスの変数に対して、ビット フィールドは使用できません。

次の例では C3623 が生成されます。

```cpp
// C3623.cpp
// compile with: /clr
using namespace System;
ref class CMyClass {
public:
   int i : 1;   // C3623
};

int main() {
   CMyClass^ pMyClass = gcnew CMyClass();
   pMyClass->i = 3;
   Console::Out->WriteLine(pMyClass->i);
}
```
