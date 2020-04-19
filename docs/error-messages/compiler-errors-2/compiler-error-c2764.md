---
title: コンパイラエラー C2764
ms.date: 11/04/2016
f1_keywords:
- C2764
helpviewer_keywords:
- C2764
ms.assetid: 3754f5af-e094-4425-be20-d0c9a9b5baec
ms.openlocfilehash: 8d318742a367487f3688717046a6a798c2add87a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759842"
---
# <a name="compiler-error-c2764"></a>コンパイラエラー C2764

' param ': テンプレートパラメーターが、部分的特殊化 ' 特殊化 ' で使用されていないか、推論できされています

テンプレートパラメーターは部分的特殊化では使用されません。 これにより、テンプレートパラメーターを推測できないため、部分的特殊化は使用できなくなります。

## <a name="example"></a>使用例

次の例では、C2764 が生成されます。

```cpp
// C2764.cpp
#include <stdio.h>
template <class T1, class T2>
struct S  {
   int m_i;
};

template <class T1, class T2>
struct S<int, T2*> {   // C2764
// try the following line instead
// struct S<T1(*)(T2), T2*> {
   char m_c;
};

int main() {
   S<int, char> s1;
   S<void (*)(short), short *> s2;
   s2.m_c = 10;
   s1.m_i = s2.m_c;
   printf_s("%d\n", s1.m_i);
}
```
