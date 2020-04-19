---
title: コンパイラエラー C2786
ms.date: 11/04/2016
f1_keywords:
- C2786
helpviewer_keywords:
- C2786
ms.assetid: 6676d8c0-86dd-4a39-bdda-b75a35f4d137
ms.openlocfilehash: ba5d05e9c7cc702509144fb876a1301bfc8bf3d4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739611"
---
# <a name="compiler-error-c2786"></a>コンパイラエラー C2786

' type ': __uuidof の無効なオペランドです

[__Uuidof](../../cpp/uuidof-operator.md)演算子は、GUID が割り当てられたユーザー定義型、またはそのようなユーザー定義型のオブジェクトを受け取ります。  次の原因が考えられます。

1. 引数がユーザー定義型ではありません。

1. `__uuidof` が引数から GUID を抽出できません。

次の例では、C2786 が生成されます。

```cpp
// C2786.cpp
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};

int main() {
   __uuidof(int);   // C2786
   __uuidof(int *);   // C2786
   __uuidof(A **);   // C2786

   // no error
   __uuidof(A);
   __uuidof(A *);
   __uuidof(A &);
   __uuidof(A[]);

   int i;
   int *pi;
   A **ppa;

   __uuidof(i);      // C2786
   __uuidof(pi);     // C2786
   __uuidof(ppa);    // C2786
}
```
