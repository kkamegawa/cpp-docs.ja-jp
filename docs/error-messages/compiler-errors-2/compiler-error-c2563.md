---
title: コンパイラ エラー C2563
ms.date: 11/04/2016
f1_keywords:
- C2563
helpviewer_keywords:
- C2563
ms.assetid: 54abba68-6458-4ca5-894d-3babdb7b3552
ms.openlocfilehash: 983788f041651fcd313c0707a4a7c64cc6e33c5a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755539"
---
# <a name="compiler-error-c2563"></a>コンパイラ エラー C2563

仮パラメーターリストが一致しません

関数 (または関数へのポインター) の仮パラメーターリストが、別の関数 (またはメンバー関数へのポインター) の仮パラメーターリストと一致しません。 その結果、関数またはポインターの割り当てを行うことはできません。

次の例では、C2563 が生成されます。

```cpp
// C2563.cpp
void func( int );
void func( int, int );
int main() {
   void *fp();
   fp = func;   // C2563
}
```
