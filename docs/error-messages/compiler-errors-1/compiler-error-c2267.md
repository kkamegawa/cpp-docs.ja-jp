---
title: コンパイラ エラー C2267
ms.date: 11/04/2016
f1_keywords:
- C2267
helpviewer_keywords:
- C2267
ms.assetid: ea63bebb-6208-4367-8440-39be07f9c360
ms.openlocfilehash: c897f8e6b38743ee98ec29707b222901ddde9d7c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758737"
---
# <a name="compiler-error-c2267"></a>コンパイラ エラー C2267

' function ': ブロックスコープを持つ静的関数は無効です

ローカル関数は `static`として宣言されています。 静的関数にはグローバルスコープが必要です。

次の例では、C2267 が生成されます。

```cpp
// C2267.cpp
static int func2();   // OK
int main() {
    static int func1();   // C2267
}
```
