---
title: コンパイラエラー C2648
ms.date: 11/04/2016
f1_keywords:
- C2648
helpviewer_keywords:
- C2648
ms.assetid: ce338337-9154-4f85-bb61-b05fdbfad75d
ms.openlocfilehash: 74e1aa18d49e8a705a95f17c83bb201e9022d8c5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755721"
---
# <a name="compiler-error-c2648"></a>コンパイラエラー C2648

' identifier ': メンバーを既定のパラメーターとして使用するには、静的メンバーが必要です

非静的メンバーは、既定のパラメーターとして使用されます。

次の例では、C2648 が生成されます。

```cpp
// C2648.cpp
// compile with: /c
class C {
public:
   int i;
   static int j;
   void func1( int i = i );  // C2648  i is not static
   void func2( int i = j );  // OK
};
```
