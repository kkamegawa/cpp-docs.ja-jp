---
title: コンパイラの警告 (レベル 1) C4602
ms.date: 11/04/2016
f1_keywords:
- C4602
helpviewer_keywords:
- C4602
ms.assetid: c1f0300f-e2a2-4c9e-a7c3-4c7318d10509
ms.openlocfilehash: 7cacadea560dc5a68d396ac607deb3a5a3c236ee
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965912"
---
# <a name="compiler-warning-level-1-c4602"></a>コンパイラの警告 (レベル 1) C4602

\#プラグマ pop_macro: ' macro name ' は、この識別子に対して以前の #pragma push_macro がありません

特定のマクロに [pop_macro](../../preprocessor/pop-macro.md) を使用する場合は、そのマクロ名を [push_macro](../../preprocessor/push-macro.md)にまず渡す必要があります。 たとえば、次の例では C4602 が生成されます。

```cpp
// C4602.cpp
// compile with: /W1
int main()
{
   #pragma pop_macro("x")   // C4602 x is not on the stack
}
```