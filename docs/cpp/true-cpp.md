---
title: true (C++)
ms.date: 11/04/2016
f1_keywords:
- true_cpp
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
ms.openlocfilehash: 5cfc99f446499201a0f54c8e5b1dcc2d7152445c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404703"
---
# <a name="true-c"></a>true (C++)

## <a name="syntax"></a>構文

```
bool-identifier = true ;
bool-expression logical-operator true ;
```

## <a name="remarks"></a>Remarks

このキーワードは、2 つの型の変数値のいずれかの[bool](../cpp/bool-cpp.md)または条件式 (条件式は true ブール式ではようになりました)。 場合`i`の種類は**bool**、then ステートメント`i = true;`割り当てます**true**に`i`します。

## <a name="example"></a>例

```cpp
// bool_true.cpp
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