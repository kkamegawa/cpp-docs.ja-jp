---
title: コンパイラ エラー C3013
ms.date: 11/04/2016
f1_keywords:
- C3013
helpviewer_keywords:
- C3013
ms.assetid: f896777d-27e6-4b6d-baab-1567317f3374
ms.openlocfilehash: c88d78df84af39933e719e02f8ab5839540130fd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759426"
---
# <a name="compiler-error-c3013"></a>コンパイラ エラー C3013

'clause': 句は、OpenMP 'directive' ディレクティブ上で一度だけ使用できます

句が同じディレクティブに 2 回出現しました。 句の出現の 1 つを削除します。

次の例では C3013 が生成されます。

```cpp
// C3013.cpp
// compile with: /openmp
int main() {
   int a, b, c, x, y, z;

   #pragma omp parallel shared(a,b,c) private(x)

   #pragma omp for nowait private(x) nowait   // C3013
   // The previous line generates C3013, with two nowait clauses
   // try the following line instead:
   // #pragma omp for nowait private(x)
   for (a = 0 ; a < 10 ; ++a) {
   }
}
```
