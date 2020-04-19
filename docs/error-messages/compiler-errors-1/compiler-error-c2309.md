---
title: コンパイラ エラー C2309
ms.date: 11/04/2016
f1_keywords:
- C2309
helpviewer_keywords:
- C2309
ms.assetid: 6303d5b5-72cf-42b8-92ce-b1eb48e80d48
ms.openlocfilehash: 2567562b5d8a75a40afcb4a94ad453ee65709a00
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759036"
---
# <a name="compiler-error-c2309"></a>コンパイラ エラー C2309

catch ハンドラーには、かっこで囲まれた例外宣言が必要です

Catch ハンドラーには、かっこで囲まれた型がありません。

次の例では、C2309 が生成されます。

```cpp
// C2309.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
   try {
      throw "ooops!";
   }
   catch C {}   // C2309
   // try the following line instead
   // catch( C ) {}
}
```
