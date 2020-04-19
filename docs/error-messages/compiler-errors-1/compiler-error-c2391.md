---
title: コンパイラ エラー C2391
ms.date: 11/04/2016
f1_keywords:
- C2391
helpviewer_keywords:
- C2391
ms.assetid: 63a9c6b9-03cc-4517-885c-bdcd048643b3
ms.openlocfilehash: 7dd47ffbd9481f69f3799a94a17a53ccdffb2a84
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745019"
---
# <a name="compiler-error-c2391"></a>コンパイラ エラー C2391

' identifier ': ' friend ' は型定義中には使用できません

`friend` の宣言には、完全なクラス宣言が含まれています。 `friend` 宣言では、メンバー関数または詳細な型指定子を指定できますが、完全なクラス宣言は指定できません。

次の例では C2326 が生成されます。

```cpp
// C2391.cpp
// compile with: /c
class D {
   void func( int );
};

class A {
   friend class B { int i; };   // C2391

   // OK
   friend class C;
   friend void D::func(int);
};
```
