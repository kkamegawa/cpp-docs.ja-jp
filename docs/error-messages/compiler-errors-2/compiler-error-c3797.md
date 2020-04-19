---
title: コンパイラ エラー C3797
ms.date: 11/04/2016
f1_keywords:
- C3797
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
ms.openlocfilehash: 7236cb75aef4250440a1e992415df07fb5b7da3f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757177"
---
# <a name="compiler-error-c3797"></a>コンパイラ エラー C3797

' override ': イベント宣言は、オーバーライド指定子を含むことはできません (イベントの追加/削除/raise メソッドに配置する必要があります)

自明なイベント (明示的に定義されたアクセサーメソッドを使用しないイベント) は、別の自明なイベントと共にオーバーライドすることはできません。 オーバーライドするイベントでは、アクセサー関数を使用した動作を定義する必要があります。

詳細については、「 [event](../../extensions/event-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3797 が生成されます。

```cpp
// C3797.cpp
// compile with: /clr /c
delegate void MyDel();

ref class Class1 {
public:
   virtual event MyDel ^ E;
};

ref class Class2 : public Class1 {
public:
   virtual event MyDel ^ E override;   // C3797
};

// OK
ref class Class3 : public Class1 {
public:
   virtual event MyDel ^ E {
      void add(MyDel ^ d) override {}
      void remove(MyDel ^ d) override {}
   }
};
```
