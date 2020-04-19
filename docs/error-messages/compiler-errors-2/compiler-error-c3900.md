---
title: コンパイラ エラー C3900
ms.date: 11/04/2016
f1_keywords:
- C3900
helpviewer_keywords:
- C3900
ms.assetid: a94cc561-8fa8-4344-9e01-e81ff462fae5
ms.openlocfilehash: f1289fb9a4d60f2c75b54fd573c83064f1517282
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749101"
---
# <a name="compiler-error-c3900"></a>コンパイラ エラー C3900

' member ': 現在のスコープでは許可されていません

プロパティブロックには、関数宣言とインライン関数定義のみを含めることができます。 プロパティブロックでは、関数以外のメンバーは許可されません。 Typedef、演算子、または friend 関数は使用できません。 詳細については、「 [property](../../extensions/property-cpp-component-extensions.md)」を参照してください。

イベント定義には、アクセスメソッドと関数のみを含めることができます。

次の例では、C3900 が生成されます。

```cpp
// C3900.cpp
// compile with: /clr
ref class X {
   property int P {
      void set(int);   // OK
      int i;   // C3900 variable declaration
   };
};
```

次の例では、C3900 が生成されます。

```cpp
// C3900b.cpp
// compile with: /clr
using namespace System;
delegate void H();
ref class X {
   event H^ E {
      int m;   // C3900

      // OK
      void Test() {}

      void add( H^ h ) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```
