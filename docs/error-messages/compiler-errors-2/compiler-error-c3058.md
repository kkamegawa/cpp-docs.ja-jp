---
title: コンパイラ エラー C3058
ms.date: 11/04/2016
f1_keywords:
- C3058
helpviewer_keywords:
- C3058
ms.assetid: 669d08c8-0b58-4351-88aa-c6e6e1af481c
ms.openlocfilehash: 618c9bd127a4e8a11cd858ab9642a5c52eee8d30
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761129"
---
# <a name="compiler-error-c3058"></a>コンパイラ エラー C3058

'symbol' : シンボルは、'copyin' 句の中で使用される前に 'threadprivate' として宣言されていません

シンボルは、 [copyin](../../parallel/openmp/reference/threadprivate.md) 句で使用する前に、最初に [threadprivate](../../parallel/openmp/reference/copyin.md) として宣言されている必要があります。

次の例では C3058 が生成されます。

```cpp
// C3058.cpp
// compile with: /openmp
int x, y, z;
#pragma omp threadprivate(x, z)

void test() {
   #pragma omp parallel copyin(x, y)   // C3058
   {
   }
}
```

解決方法:

```cpp
// C3058b.cpp
// compile with: /openmp /LD
int x, y, z;
#pragma omp threadprivate(x, y)

void test() {
   #pragma omp parallel copyin(x, y)
   {
   }
}
```
