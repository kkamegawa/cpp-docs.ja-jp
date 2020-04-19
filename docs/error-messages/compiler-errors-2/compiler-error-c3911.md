---
title: コンパイラ エラー C3911
ms.date: 11/04/2016
f1_keywords:
- C3911
helpviewer_keywords:
- C3911
ms.assetid: b786da59-0e99-479d-bc0d-551126e940f2
ms.openlocfilehash: f803d6f575d78fd7a9a9157f06b3f64c4eeb3d77
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748789"
---
# <a name="compiler-error-c3911"></a>コンパイラ エラー C3911

' event_accessor_method ': 関数は ' signature ' 型でなければなりません

イベントのアクセサーメソッドが正しく宣言されていません。

詳細については、「 [event](../../extensions/event-cpp-component-extensions.md)」を参照してください。

次の例では、C3911 が生成されます。

```cpp
// C3911.cpp
// compile with: /clr
using namespace System;
delegate void H(String^, int);

ref class X {
   event H^ E1 {
      void add() {}   // C3911
      // try the following line instead
      // void add(H ^ h) {}

      void remove(){}
      // try the following line instead
      // void remove(H ^ h) {}

      void raise(){}
      // try the following line instead
      // void raise(String ^ s, int i) {}
   };
};
```
