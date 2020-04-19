---
title: コンパイラ エラー C3048
ms.date: 11/04/2016
f1_keywords:
- C3048
helpviewer_keywords:
- C3048
ms.assetid: 48e07091-94d9-471d-befe-7e2507631edd
ms.openlocfilehash: bec5921ea3d44c60d5d385da811beb6674c1a8d5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761313"
---
# <a name="compiler-error-c3048"></a>コンパイラ エラー C3048

'#pragma omp atomic' の後の式は、正しくない形式を含んでいます

atomic ディレクティブが正しく指定されていません。

次の例では C3048 が生成されます。

```cpp
// C3048.cpp
// compile with: /openmp vcomps.lib
#include "omp.h"
#include <stdio.h>

int main() {
   int a[10];
   omp_set_num_threads(4);
   #pragma omp parallel
   {
      #pragma omp atomic
      a[0] = 1;   // C3048
      // try the following line instead
      // a[0] += 1;
   }
}
```
