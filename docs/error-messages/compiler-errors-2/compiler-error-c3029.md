---
title: コンパイラ エラー C3029
ms.date: 11/04/2016
f1_keywords:
- C3029
helpviewer_keywords:
- C3029
ms.assetid: 655eb04d-504a-468d-8c0c-bda1e5f297b7
ms.openlocfilehash: 12c06757ed6ec7560f7dd647e241ddd08a0484d5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736751"
---
# <a name="compiler-error-c3029"></a>コンパイラ エラー C3029

'symbol' : OpenMP ディレクティブのデータ共有句で一度だけ使用することができます

シンボルは、ディレクティブの 1 つ以上の句で複数回使用されました。 シンボルは、ディレクティブで一度だけ使用することができます。

次の例では C3029 が生成されます。

```cpp
// C3029.cpp
// compile with: /openmp /link vcomps.lib
#include "omp.h"

int g_i;

int main() {
   int i, x;

   #pragma omp parallel reduction(+ : x, x)   // C3029
      ;

   #pragma omp parallel reduction(+ : x)   // OK
      ;

   #pragma omp parallel private(x) reduction(+ : x)   // C3029
      ;

   #pragma omp parallel reduction(+ : x)   // OK
      ;
}
```
