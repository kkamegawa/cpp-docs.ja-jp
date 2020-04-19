---
title: コンパイラ エラー C3668
ms.date: 11/04/2016
f1_keywords:
- C3668
helpviewer_keywords:
- C3668
ms.assetid: 53a96698-bde4-4447-95b5-b5108291f60c
ms.openlocfilehash: 1e949a1251fcbebfd9e8fe47caf190e81b8b9f99
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758165"
---
# <a name="compiler-error-c3668"></a>コンパイラ エラー C3668

' method ': オーバーライド指定子 ' override ' を持つメソッドは、基底クラスのメソッドをオーバーライドしませんでした

関数が存在しない関数をオーバーライドしようとしました。

詳細については、「[明示的なオーバーライド](../../extensions/explicit-overrides-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3668 が生成されます。

```cpp
// C3668.cpp
// compile with: /c
__interface I {
   void f(int);   // virtual by default
};

class J {
public:
   void g(int);
   virtual void h(int);
};

struct R : I,J {
   virtual void f() override {}   // C3668
   virtual void f(int) override {}   // OK

   virtual void g(int) override {}   // C3668
   virtual void h(int) override {}   // OK
};
```
