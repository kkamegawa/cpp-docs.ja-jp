---
title: コンパイラの警告 (レベル 1) C4717
ms.date: 11/04/2016
f1_keywords:
- C4717
helpviewer_keywords:
- C4717
ms.assetid: 5ef3c6c7-8599-4714-a973-0f5b69cdab3c
ms.openlocfilehash: 0bc95cc770914a1c02a7a40f9754415c2f013d63
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051343"
---
# <a name="compiler-warning-level-1-c4717"></a>コンパイラの警告 (レベル 1) C4717

' function ': すべてのコントロールパスで再帰的に行われます。関数は、ランタイムスタックオーバーフローを発生させます

関数を使用するすべてのパスには、関数の呼び出しが含まれます。 最初にそれ自体を再帰的に呼び出すことなく関数を終了する方法がないため、関数は終了しません。

次の例では、C4717 が生成されます。

```cpp
// C4717.cpp
// compile with: /W1 /c
// C4717 expected
int func(int x) {
   if (x > 1)
      return func(x - 1); // recursive call
   else {
      int y = func(0) + 1; // recursive call
      return y;
   }
}

int main(){
   func(1);
}
```