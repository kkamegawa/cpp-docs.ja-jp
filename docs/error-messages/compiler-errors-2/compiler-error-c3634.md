---
title: コンパイラ エラー C3634
ms.date: 11/04/2016
f1_keywords:
- C3634
helpviewer_keywords:
- C3634
ms.assetid: fd09f10c-f863-483b-9756-71c16b760b02
ms.openlocfilehash: 2abf5191035e450dca72777cdc2b2675ac9b90de
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742588"
---
# <a name="compiler-error-c3634"></a>コンパイラ エラー C3634

' function ': マネージクラスまたは WinRTclass の抽象メソッドを定義することはできません。

マネージド クラスまたは WinRT クラスで抽象メソッドを宣言することはできますが、定義することはできません。

## <a name="example"></a>使用例

次の例では警告 C3634 が生成されます。

```cpp
// C3634.cpp
// compile with: /clr
ref class C {
   virtual void f() = 0;
};

void C::f() {   // C3634 - don't define managed class' pure virtual method
}
```
