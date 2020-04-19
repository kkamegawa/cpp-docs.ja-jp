---
title: コンパイラエラー C2650
ms.date: 11/04/2016
f1_keywords:
- C2650
helpviewer_keywords:
- C2650
ms.assetid: 49a8ac6e-aa6d-4616-917c-a3cfcdbad5a4
ms.openlocfilehash: f71996c6d04d8be2101762fb0fb17634e6b25a1a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756137"
---
# <a name="compiler-error-c2650"></a>コンパイラエラー C2650

' operator ': 仮想関数にすることはできません。

`new` または `delete` 演算子が `virtual`として宣言されています。 これらの演算子は `static` メンバー関数であり、`virtual`できません。

## <a name="example"></a>使用例

次の例では、C2650 が生成されます。

```cpp
// C2650.cpp
// compile with: /c
class A {
   virtual void* operator new( unsigned int );   // C2650
   // try the following line instead
   // void* operator new( unsigned int );
};
```
