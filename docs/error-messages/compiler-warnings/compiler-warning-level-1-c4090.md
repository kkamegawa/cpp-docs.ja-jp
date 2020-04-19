---
title: コンパイラの警告 (レベル 1) C4090
ms.date: 11/04/2016
f1_keywords:
- C4090
helpviewer_keywords:
- C4090
ms.assetid: baad469d-23d4-45aa-ad9c-305b32d61e9a
ms.openlocfilehash: 88ed48e9bf7057c55ee4004ca1bb1eb18cd4be51
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626167"
---
# <a name="compiler-warning-level-1-c4090"></a>コンパイラの警告 (レベル 1) C4090

' operation ': 異なる ' modifier ' 修飾子です

操作で使用される変数は、コンパイラによって検出されることなく変更されないように、指定された修飾子を使用して定義されます。 式は、変更せずにコンパイルされます。

この警告は、 **const**または `volatile` 項目へのポインターが、 **const**または `volatile`を指すように宣言されていないポインターに割り当てられた場合に発生することがあります。

この警告は C プログラムに対して発行されます。 C++プログラムでは、コンパイラがエラー [C2440](../../error-messages/compiler-errors-1/compiler-error-c2440.md)を発行します。

次の例では、C4090 が生成されます。

```c
// C4090.c
// compile with: /W1
int *volatile *p;
int *const *q;
int **r;

int main() {
   p = q;   // C4090
   p = r;
   q = p;   // C4090
   q = r;
   r = p;   // C4090
   r = q;   // C4090
}
```