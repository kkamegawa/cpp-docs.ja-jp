---
title: コンパイラ エラー C3253
ms.date: 11/04/2016
f1_keywords:
- C3253
helpviewer_keywords:
- C3253
ms.assetid: da40be26-0f78-4730-8727-ad11cddf8869
ms.openlocfilehash: c895def372fd74f077725479112873020264371f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754265"
---
# <a name="compiler-error-c3253"></a>コンパイラ エラー C3253

' function ': 明示的なオーバーライドでエラーが発生しています。

明示的なオーバーライドが正しく指定されませんでした。 たとえば、純粋として指定するオーバーライドの実装を指定することはできません。 詳細については、「[明示的なオーバーライド](../../extensions/explicit-overrides-cpp-component-extensions.md)」を参照してください。

次の例では、C3253 が生成されます。

```cpp
// C3253.cpp
// compile with: /clr
public interface struct I {
   void a();
   void b();
   void c();
};

public ref struct R : I {
   virtual void a() = 0, I::a {}   // C3253
   virtual void b() = I::a {}   // OK
   virtual void c() = 0;   // OK
};
```
