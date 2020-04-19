---
title: コンパイラの警告 (レベル 4) C4245
ms.date: 11/04/2016
f1_keywords:
- C4245
helpviewer_keywords:
- C4245
ms.assetid: 85083d53-9cc2-4d12-b58c-6dad28f15cbe
ms.openlocfilehash: 321451f0cc2ac538dbd0779001e22be047a3cc4d
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991420"
---
# <a name="compiler-warning-level-4-c4245"></a>コンパイラの警告 (レベル 4) C4245

' conversion ': ' type1 ' から ' type1 ' への変換、符号付き/符号なしの不一致

負の値を持つ符号付き**定数**を `unsigned`に変換しようとしました。

次の例では、C4245 が生成されます。

```cpp
// C4245.cpp
// compile with: /W4 /c
const int i = -1;
unsigned int j = i; // C4245

const int k = 1;
unsigned int l = k; // okay

int m = -1;
unsigned int n = m; // okay

void Test(size_t i) {}

int main() {
   Test( -19 );   // C4245
}
```
