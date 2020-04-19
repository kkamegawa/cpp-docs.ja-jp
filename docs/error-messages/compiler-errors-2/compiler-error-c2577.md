---
title: コンパイラ エラー C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: acb42f9b792b3908a153737bcec93a449b656147
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755448"
---
# <a name="compiler-error-c2577"></a>コンパイラ エラー C2577

' member ': デストラクターまたはファイナライザーは戻り値の型を持つことはできません

デストラクターまたはファイナライザーは、`void` またはその他の型の値を返すことはできません。 デストラクター定義から `return` ステートメントを削除します。

## <a name="example"></a>使用例

次の例では、C2577 が生成されます。

```cpp
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```
