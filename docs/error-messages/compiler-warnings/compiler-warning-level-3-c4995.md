---
title: コンパイラの警告 (レベル 3) C4995
ms.date: 11/04/2016
f1_keywords:
- C4995
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
ms.openlocfilehash: c361563c2272da002a0edc185cc924c64f6b5e5c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991665"
---
# <a name="compiler-warning-level-3-c4995"></a>コンパイラの警告 (レベル 3) C4995

' function ': 名前が非推奨として #pragma としてマークされました

コンパイラは、プラグマが[非推奨](../../preprocessor/deprecated-c-cpp.md)としてマークされた関数を検出しました。 この関数は、将来のリリースではサポートされなくなる可能性があります。 [警告](../../preprocessor/warning.md)プラグマ (次の例を参照) を使用して、この警告をオフにすることができます。

## <a name="example"></a>使用例

次の例では、C4995 が生成されます。

```cpp
// C4995.cpp
// compile with: /W3
#include <stdio.h>

// #pragma warning(disable : 4995)
void func1(void)
{
    printf("\nIn func1");
}

int main()
{
    func1();
    #pragma deprecated(func1)
    func1();   // C4995
}
```
