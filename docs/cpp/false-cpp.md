---
title: false (C++)
ms.date: 11/04/2016
f1_keywords:
- false_cpp
helpviewer_keywords:
- false keyword [C++]
ms.assetid: cc13aec5-1f02-4d38-8dbf-5473ea2b354f
ms.openlocfilehash: 5fc27c7f1dfde7d1f686f0a752652773ade9cc0e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183727"
---
# <a name="false-c"></a>false (C++)

キーワードは型の変数の 2 つの値の 1 つ[bool](../cpp/bool-cpp.md)または条件式 (条件式は、 **true**ブール式)。 たとえば場合、`i`型の変数は、 **bool**、`i = false;`ステートメント割り当てます**false**に`i`します。

## <a name="example"></a>例

```cpp
// bool_false.cpp
#include <stdio.h>

int main()
{
    bool bb = true;
    printf_s("%d\n", bb);
    bb = false;
    printf_s("%d\n", bb);
}
```

```Output
1
0
```

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)