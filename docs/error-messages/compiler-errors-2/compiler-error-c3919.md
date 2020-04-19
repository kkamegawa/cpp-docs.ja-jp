---
title: コンパイラ エラー C3919
ms.date: 11/04/2016
f1_keywords:
- C3919
helpviewer_keywords:
- C3919
ms.assetid: 5f8eddda-d751-478b-930d-e18f7191ddfb
ms.openlocfilehash: 78a42b264129ee365e664b1242c8aa58dd1244bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758477"
---
# <a name="compiler-error-c3919"></a>コンパイラ エラー C3919

' event_method ': 関数には型 ' type ' を指定しなければなりません

イベントのアクセサーメソッドが正しく宣言されていません。

イベントの詳細については、「 [event](../../extensions/event-cpp-component-extensions.md)」を参照してください。

次の例では、C3919 が生成されます。

```cpp
// C3919.cpp
// compile with: /clr /c
using namespace System;
delegate void D(String^);
ref class R {
   event D^ e {
      int add(int);   // C3919
      int remove(int);   // C3919

      void add(D^);   // OK
      void remove(D^);   // OK
   }
};
```
