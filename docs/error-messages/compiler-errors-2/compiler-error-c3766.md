---
title: コンパイラ エラー C3766
ms.date: 11/04/2016
f1_keywords:
- C3766
helpviewer_keywords:
- C3766
ms.assetid: b5af2089-2e1e-4e45-a41d-495b6c55656e
ms.openlocfilehash: c1cbd218b127bdf0d6784b7d35dac563d8ea198d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757216"
---
# <a name="compiler-error-c3766"></a>コンパイラ エラー C3766

' type ' はインターフェイスメソッド ' function ' の実装を指定しなければなりません

インターフェイスから継承するクラスは、インターフェイスメンバーを実装する必要があります。

## <a name="example"></a>使用例

次の例では、C3766 が生成されます。

```cpp
// C3766.cpp
// compile with: /clr /c

delegate void MyDel();

interface struct IFace {
   virtual event MyDel ^ E;
};

ref struct Class1 : public IFace {};   // C3766

// OK
ref struct Class2 : public IFace {
   virtual event MyDel ^ E {
      void add(MyDel ^) {}
      void remove(MyDel ^) {}
   }
};
```
