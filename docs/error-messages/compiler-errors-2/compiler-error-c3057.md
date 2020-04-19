---
title: コンパイラ エラー C3057
ms.date: 11/04/2016
f1_keywords:
- C3057
helpviewer_keywords:
- C3057
ms.assetid: b0b2ba88-9c74-4bec-bf60-8fc72eade34c
ms.openlocfilehash: da7742a8268adfd2345c0606e2f60dae4e58887c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761143"
---
# <a name="compiler-error-c3057"></a>コンパイラ エラー C3057

'symbol' : 'threadprivate' シンボルの動的な初期化は現在サポートされていません

[threadprivate](../../parallel/openmp/reference/threadprivate.md) 句で使用するシンボルの初期値は、コンパイル時に既知である必要があります。

次の例では C3057 が生成されます。

```cpp
// C3057.cpp
// compile with: /openmp /c
extern int f();
int x, y = f();
int a, b;
#pragma omp threadprivate(x, y)   // C3057

#pragma omp threadprivate(a, b)

int main() {
   // Delete the following 4 lines to resolve.
   #pragma omp parallel copyin(x, y)
   {
      x = y;
   }

   #pragma omp parallel copyin(a, b)
   {
      a = b;
   }
}
```

次の例では C3057 が生成されます。

```cpp
// C3057b.cpp
// compile with: /openmp /c
extern int Initialize();
int main() {
   #pragma omp parallel
   {
      static int var = Initialize();
      #pragma omp threadprivate(var)   // C3057
   }

   // OK
   #pragma omp parallel
   {
      static int var2;
      static bool initialized2;
      #pragma omp threadprivate(var2, initialized2)
      if (!initialized2) {
         var2 = Initialize();
         initialized2 = true;
      }
   }
}
```
