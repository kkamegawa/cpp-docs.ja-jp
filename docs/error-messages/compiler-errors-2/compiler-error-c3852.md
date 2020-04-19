---
title: コンパイラ エラー C3852
ms.date: 11/04/2016
f1_keywords:
- C3852
helpviewer_keywords:
- C3852
ms.assetid: 194e5c5e-0dfb-414e-86db-791c11eb610c
ms.openlocfilehash: f264333d802967d0350caa8ab4ba4925ffe019af
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754876"
---
# <a name="compiler-error-c3852"></a>コンパイラ エラー C3852

' member ' は型 ' type ' を持っています: 集計初期化はこのメンバーを初期化できませんでした

集計の初期化で既定の初期化を受け取ることができないデータメンバーに、集計初期化の一部として既定の初期化を割り当てようとしました。

次のサンプルでは、C3852 が生成されます。

```cpp
// C3852.cpp
struct S
{
   short s;
};

struct S1
{
   int i;
   const S s;
};

struct S2
{
   int i;
   char & rc;
};

int main()
{
   S1 s1 = { 1 };   // C3852 const member
   // try the following line instead
   // S1 s1 = { 1, 2 };

   S2 s2 = { 2 };   // C3852 reference member
   // try the following line instead
   // char c = 'a';
   S2 s2 = { 2, c };
}
```
