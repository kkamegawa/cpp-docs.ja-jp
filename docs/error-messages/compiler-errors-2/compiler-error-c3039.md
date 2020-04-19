---
title: コンパイラ エラー C3039
ms.date: 11/04/2016
f1_keywords:
- C3039
helpviewer_keywords:
- C3039
ms.assetid: 02776f16-f57a-4ffd-b7f7-9c696b633e08
ms.openlocfilehash: 344fd32e66881c2529ddb1f9185c25752f0a736c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754980"
---
# <a name="compiler-error-c3039"></a>コンパイラ エラー C3039

'var' : OpenMP 'for' ステートメントのインデックス変数を減少変数にすることはできません

インデックス変数は暗黙的にプライベートであるため、囲む [parallel](../../parallel/openmp/reference/reduction.md) ディレクティブ内の [reduction](../../parallel/openmp/reference/parallel.md) 句で、変数を使用することはできません。

## <a name="example"></a>使用例

次の例では C3039 が生成されます。

```cpp
// C3039.cpp
// compile with: /openmp /c
int g_i;

int main() {
   int i;

   #pragma omp parallel reduction(+: i)
   {
      #pragma omp for
      for (i = 0; i < 10; ++i)   // C3039
         g_i += i;
   }
}
```
