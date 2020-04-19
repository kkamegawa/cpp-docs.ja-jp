---
title: コンパイラ エラー C2148
ms.date: 11/04/2016
f1_keywords:
- C2148
helpviewer_keywords:
- C2148
ms.assetid: e510c2c9-7b57-4ce8-be03-ba363e2cc5d9
ms.openlocfilehash: aac14024e7ed2942eaf80c45817ba9c208e7e1ce
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756501"
---
# <a name="compiler-error-c2148"></a>コンパイラ エラー C2148

配列の合計サイズは、0x7fffffff バイトを超えることはできません

配列が制限を超えています。 配列のサイズを小さくします。

## <a name="example"></a>使用例

次の例では、C2148 が生成されます。

```cpp
// C2148.cpp
#include <stdio.h>
#include <stdlib.h>

int main( ) {
   char MyArray[0x7ffffffff];   // C2148
   char * MyArray2 = (char *)malloc(0x7fffffff);

   if (MyArray2)
      printf_s("It worked!");
   else
      printf_s("It didn't work.");
}
```
