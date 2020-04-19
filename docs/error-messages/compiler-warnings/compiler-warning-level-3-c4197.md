---
title: コンパイラの警告 (レベル 3) C4197
ms.date: 11/04/2016
f1_keywords:
- C4197
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
ms.openlocfilehash: d7c8cee42f17ad3301980852b8333ea37f5ca6be
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051784"
---
# <a name="compiler-warning-level-3-c4197"></a>コンパイラの警告 (レベル 3) C4197

' type ': キャストの最上位レベルの volatile は無視されます

コンパイラは、 [volatile](../../cpp/volatile-cpp.md)で修飾された r 値型へのキャスト、または、volatile で修飾された型への r 値型のキャストを検出しました。 C 標準 (6.5.3) によれば、修飾型に関連付けられているプロパティは、左辺値の式に対してのみ意味があります。

次の例では、C4197 が生成されます。

```cpp
// C4197.cpp
// compile with: /W3
#include <stdio.h>
#include <signal.h>
#include <stdlib.h>

void sigproc(int);
struct S
{
   int i;
} s;

int main()
{
   signal(SIGINT, sigproc);
   s.i = 1;
   S *pS = &s;
   for ( ; (volatile int)pS->i ; )   // C4197
      break;
   // for ( ; *(volatile int *)&pS->i ; )   // OK
   //    break;
}

void sigproc(int) // ctrl-C
{
   signal(SIGINT, sigproc);
   s.i = 0;
}
```