---
title: コンパイラの警告 (レベル 1) C4052
ms.date: 11/04/2016
f1_keywords:
- C4052
helpviewer_keywords:
- C4052
ms.assetid: f9955421-16ab-46e5-8f9d-bf1639a519ef
ms.openlocfilehash: 848db5df19908150d9f869bf2995ed69c24a1ec0
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626971"
---
# <a name="compiler-warning-level-1-c4052"></a>コンパイラの警告 (レベル 1) C4052

関数に対する宣言の 1 つに可変個の引数が含まれていません。

関数の 1 つの宣言に、可変個の引数が含まれません。 これは無視されます。

次の例では C4052 が生成されます。

```c
// C4052.c
// compile with: /W4 /c
int f();
int f(int i, ...);   // C4052
```