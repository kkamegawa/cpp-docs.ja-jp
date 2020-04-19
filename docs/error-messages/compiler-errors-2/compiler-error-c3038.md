---
title: コンパイラ エラー C3038
ms.date: 11/04/2016
f1_keywords:
- C3038
helpviewer_keywords:
- C3038
ms.assetid: 140ada3e-5636-43ef-a4ee-22a9f66a771f
ms.openlocfilehash: 26fee4f5d636ac56ae01499f6b600d38f56bbe46
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754967"
---
# <a name="compiler-error-c3038"></a>コンパイラ エラー C3038

'var': 'private' 句の変数を、それを囲むコンテキスト内で減少変数にすることはできません

parallel ディレクティブの [reduction](../../parallel/openmp/reference/reduction.md) 句に出現する変数を、parallel コンストラクトにバインドされる動作共有ディレクティブの [private](../../parallel/openmp/reference/private-openmp.md) 句に指定することはできません。

次の例では C3038 が生成されます。

```cpp
// C3038.cpp
// compile with: /openmp /c
int g_i, g_i2;

int main() {
   int i;

   #pragma omp parallel reduction(+: g_i)
   {
      #pragma omp for private(g_i)   // C3038
      // try the following line instead
      // #pragma omp for private(g_i2)
      for (i = 0; i < 10; ++i)
         g_i += i;
   }
}
```
