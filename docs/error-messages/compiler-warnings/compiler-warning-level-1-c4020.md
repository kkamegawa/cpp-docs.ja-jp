---
title: コンパイラの警告 (レベル 1) C4020
ms.date: 11/04/2016
f1_keywords:
- C4020
helpviewer_keywords:
- C4020
ms.assetid: 8c4cd6be-9371-4c8c-b0ff-a5ad367bbab0
ms.openlocfilehash: ccab8eaac42932491fc8b88cd28f2d3334b2e849
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626318"
---
# <a name="compiler-warning-level-1-c4020"></a>コンパイラの警告 (レベル 1) C4020

' function ': 実引数が多すぎます。

関数呼び出しの実際のパラメーターの数が、関数プロトタイプまたは定義内の仮引数の数を超えています。 コンパイラは、関数の呼び出し規則に従って、余分な実際のパラメーターを渡します。

次の例では、C4020 が生成されます。

```c
// C4020.c
// compile with: /W1 /c
void f(int);
int main() {
   f(1,2);   // C4020
}
```

考えられる解決方法:

```c
// C4020b.c
// compile with: /c
void f(int);
int main() {
   f(1);
}
```