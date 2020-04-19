---
title: コンパイラの警告 (レベル 4) C4709
ms.date: 11/04/2016
f1_keywords:
- C4709
helpviewer_keywords:
- C4709
ms.assetid: 8abfdd45-8c70-4c27-b0fb-ca0c3f0fccf9
ms.openlocfilehash: 4dd06baf9da3ae454bf87747bdafb2639d817fef
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989868"
---
# <a name="compiler-warning-level-4-c4709"></a>コンパイラの警告 (レベル 4) C4709

配列インデックス式内のコンマ演算子

配列インデックス式でコンマが出現すると、コンパイラは最後のコンマの後に値を使用します。

## <a name="example"></a>使用例

次の例では、C4709 が生成されます。

```cpp
// C4709.cpp
// compile with: /W4
#include <stdio.h>

int main()
{
    int arr[2][2];
    arr[0][0] = 10;
    arr[0][1] = 11;

    // Prints 10, not 11
    printf_s("\n%d",arr[0][1,0]);   // C4709
}
```
