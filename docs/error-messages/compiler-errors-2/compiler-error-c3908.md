---
title: コンパイラ エラー C3908
ms.date: 11/04/2016
f1_keywords:
- C3908
helpviewer_keywords:
- C3908
ms.assetid: 3c322482-c79e-4197-a578-2ad9bc379d1a
ms.openlocfilehash: 2b57f3346427ff548d11fe776e909eca99433a81
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749036"
---
# <a name="compiler-error-c3908"></a>コンパイラ エラー C3908

' construct ' よりも制限の緩いアクセスレベル

プロパティアクセサーメソッド (get または set) は、プロパティ自体で指定されたアクセスよりも制限が少ないアクセス許可を持つことはできません。  同様に、イベントアクセサーメソッドについても同様です。

詳細については、「[プロパティ](../../extensions/property-cpp-component-extensions.md)と[イベント](../../extensions/event-cpp-component-extensions.md)」を参照してください。

次の例では、C3908 が生成されます。

```cpp
// C3908.cpp
// compile with: /clr
ref class X {
protected:
   property int i {
   public:   // C3908 property i is protected
      int get();
   private:
      void set(int);   // OK more restrictive
   };
};
```
