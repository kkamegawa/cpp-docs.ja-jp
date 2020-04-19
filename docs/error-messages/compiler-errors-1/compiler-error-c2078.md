---
title: コンパイラエラー C2078
ms.date: 11/04/2016
f1_keywords:
- C2078
helpviewer_keywords:
- C2078
ms.assetid: 9bead850-4123-46cf-a634-5c77ba974b2b
ms.openlocfilehash: 514776c0feb12c46dea56dd8e85043345754a229
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756449"
---
# <a name="compiler-error-c2078"></a>コンパイラエラー C2078

初期化子の数が多すぎます。

初期化子の数が初期化されるオブジェクトの数を超えています。

初期化子リストで内側の中かっこが省略されている場合、コンパイラは、オブジェクトおよび内部のオブジェクトに対する正しい初期化子の割り当てを推測できます。 中かっこを完全な形で使用すれば、あいまいさが排除され、正しい割り当てが行われます。 中かっこを部分的に使用すると、オブジェクトへの初期化子の割り当てがあいまいになり、C2078 が発生することがあります。

次の例では、C2078 を生成し、その修正方法を示しています。

```cpp
// C2078.cpp
// Compile by using: cl /c /W4 C2078.cpp
struct S {
   struct {
      int x, y;
   } z[2];
};

int main() {
   int d[2] = {1, 2, 3};   // C2078
   int e[2] = {1, 2};      // OK

   char a[] = {"a", "b"};  // C2078
   char *b[] = {"a", "b"}; // OK
   char c[] = {'a', 'b'};  // OK

   S s1{1, 2, 3, 4};       // OK
   S s2{{1, 2}, {3, 4}};   // C2078
   S s3{{1, 2, 3, 4}};     // OK
   S s4{{{1, 2}, {3, 4}}}; // OK
}
```
