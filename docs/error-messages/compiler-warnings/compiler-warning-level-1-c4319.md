---
title: コンパイラの警告 (レベル 1) C4319
ms.date: 01/18/2018
f1_keywords:
- C4319
helpviewer_keywords:
- C4319
ms.assetid: 1fac8048-9bd6-4552-a21c-192c67772bb9
ms.openlocfilehash: 2d5ae8fcf5a527031c3a974b227f713675f31ffa
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926100"
---
# <a name="compiler-warning-level-1-c4319"></a>コンパイラの警告 (レベル 1) C4319

> ' ~ ': サイズが大きい ' type1 ' を '*type1* *' に*拡張することはできません。

**~** (ビットごとの補数) 演算子の結果は符号なしになり、大きな型に変換されるとゼロ拡張になります。

## <a name="example"></a>例

次の例では`~(a - 1)` 、は、32ビットの符号なし long 式として評価された後、ゼロ拡張によって64ビットに変換されます。 これは、予期しない操作結果になる可能性があります。

```cpp
// C4319.cpp
// compile with: cl /W4 C4319.cpp
int main() {
   unsigned long a = 0;
   unsigned long long q = 42;
   q = q & ~(a - 1);    // C4319 expected
}
```
