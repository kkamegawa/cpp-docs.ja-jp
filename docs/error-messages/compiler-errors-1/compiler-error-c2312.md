---
title: コンパイラ エラー C2312
ms.date: 11/04/2016
f1_keywords:
- C2312
helpviewer_keywords:
- C2312
ms.assetid: c8bcfd06-12c1-4323-bb53-ba392d36daa4
ms.openlocfilehash: 0a0fbefcb1122e5c3395580a2508420b1ccea17c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748139"
---
# <a name="compiler-error-c2312"></a>コンパイラ エラー C2312

'exception1': 行番号の 'exception2' でキャッチされました

2 つのハンドラーが同じ例外型をキャッチします。

次の例では C2312 が生成されます。

```cpp
// C2312.cpp
// compile with: /EHsc
#include <eh.h>
int main() {
    try {
        throw "ooops!";
    }
    catch( signed int ) {}
    catch( int ) {}   // C2312
}
```
