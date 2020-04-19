---
title: コンパイラ エラー C3040
ms.date: 11/04/2016
f1_keywords:
- C3040
helpviewer_keywords:
- C3040
ms.assetid: 29e857ac-74f0-4ec6-becf-9026e38c160e
ms.openlocfilehash: 8a7ee7b814be1963e2d98b54e547cc5965eef9d3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754954"
---
# <a name="compiler-error-c3040"></a>コンパイラ エラー C3040

'var': 'reduction' 句の変数の型は、減少演算子 'operator' と互換性がありません

[reduction](../../parallel/openmp/reference/reduction.md) 句内の変数は、減少演算子では使用できません。

次の例では C3040 が生成されます。

```cpp
// C3040.cpp
// compile with: /openmp /c
#include "omp.h"
double d;

int main() {
   #pragma omp parallel reduction(&:d)   // C3040
      ;

   #pragma omp parallel reduction(-:d)  // OK
      ;
}
```
