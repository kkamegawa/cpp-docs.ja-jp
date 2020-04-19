---
title: コンパイラ エラー C2360
ms.date: 11/04/2016
f1_keywords:
- C2360
helpviewer_keywords:
- C2360
ms.assetid: 51bfd2ee-8108-4777-aa93-148b9cebfa83
ms.openlocfilehash: 226fcd8a27c9abdb789b8191a5cf4e59cc4a66cc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759907"
---
# <a name="compiler-error-c2360"></a>コンパイラ エラー C2360

' identifier ' の初期化は ' case ' ラベルによってスキップされます

`identifier` の初期化は、`switch` ステートメントではスキップできます。 宣言がブロックで囲まれている場合を除き、初期化子を使用して宣言をスキップすることはできません。 (ブロック内で宣言されていない限り、変数は、`switch` ステートメントが終了するまでスコープ内にあります)。

次の例では、C2360 が生成されます。

```cpp
// C2360.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      int i = 1;
      { int j = 1; }
   case 1 :   // C2360
      int k = 1;
   }
}
```

解決方法:

```cpp
// C2360b.cpp
int main() {
   int x = 0;
   switch ( x ) {
   case 0 :
      { int j = 1; int i = 1;}
   case 1 :
      int k = 1;
   }
}
```
