---
title: コンパイラ エラー C3045
ms.date: 11/04/2016
f1_keywords:
- C3045
helpviewer_keywords:
- C3045
ms.assetid: 9351ba3e-3d3f-455f-ac90-a810fa9fd947
ms.openlocfilehash: 88c0c9747f98c6850f3e9b4341bdcdef915ac754
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761352"
---
# <a name="compiler-error-c3045"></a>コンパイラ エラー C3045

OpenMP 'sections' ディレクティブの後に複合ステートメントが必要です。 '{' が必要です

中かっこで区切られたコード ブロックを [セクション](../../parallel/openmp/reference/sections-openmp.md) ディレクティブの後に続ける必要があります。

次の例では C3045 が生成されます。

```cpp
// C3045.cpp
// compile with: /openmp /c
#include "omp.h"

int main() {
   int n2 = 2, n3 = 3;

   #pragma omp parallel
   {
      ++n2;

      #pragma omp sections
         ++n2;   // C3045

      #pragma omp sections   // OK
      {
         ++n3;
      }
   }
}
```
