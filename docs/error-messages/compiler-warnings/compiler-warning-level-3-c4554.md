---
title: コンパイラの警告 (レベル 3) C4554
ms.date: 11/04/2016
f1_keywords:
- C4554
helpviewer_keywords:
- C4554
ms.assetid: 55bb68f0-2e80-4330-8921-51083c4f8d53
ms.openlocfilehash: 45f9d85f272bb5093fd418981ea3dbdc8cb7f1c0
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992007"
---
# <a name="compiler-warning-level-3-c4554"></a>コンパイラの警告 (レベル 3) C4554

' operator ': 演算子の優先順位に誤りがあることを確認してください。かっこを使用して優先順位を明確にする

次の例では、C4554 が生成されます。

```cpp
// C4554.cpp
// compile with: /W3 /WX
int main() {
   int a = 0, b = 0, c = 0;
   a = a << b + c;   // C4554
   // probably intended (a << b) + c,
   // but will get a << (b + c)
}
```
