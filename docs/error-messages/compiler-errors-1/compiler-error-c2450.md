---
title: コンパイラ エラー C2450
ms.date: 11/04/2016
f1_keywords:
- C2450
helpviewer_keywords:
- C2450
ms.assetid: 929f1c06-8774-468b-be2a-f428757875a2
ms.openlocfilehash: 2d015bd165986467a82f33a2ae0dda08c6f6d248
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744148"
---
# <a name="compiler-error-c2450"></a>コンパイラ エラー C2450

型 ' type ' の switch 式は無効です

`switch` 式が無効な型に評価されます。 整数型または整数型へのあいまいな変換を使用して、整数型またはクラス型に評価される必要があります。 ユーザー定義型に評価される場合は、変換演算子を指定する必要があります。

次の例では、C2450 が生成されます。

```cpp
// C2450.cpp
class X {
public:
   int i;
} x;

class Y {
public:
   int i;
   operator int() { return i; }   // conversion operator
} y;

int main() {
   int j = 1;
   switch ( x ) {   // C2450, x is not type int
   // try the following line instead
   // switch ( y ) {
      default:  ;
   }
}
```
