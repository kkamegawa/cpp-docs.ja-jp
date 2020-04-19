---
title: コンパイラ エラー C2264
ms.date: 11/04/2016
f1_keywords:
- C2264
helpviewer_keywords:
- C2264
ms.assetid: 158b72cc-cee9-4a08-bd79-b7a5955345a8
ms.openlocfilehash: df3b51c60a0546ed00a8cba7c6db066792cf50a2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758750"
---
# <a name="compiler-error-c2264"></a>コンパイラ エラー C2264

' function ': 関数の定義または宣言にエラーがあります。関数は呼び出されません。

定義または宣言が正しくないため、関数を呼び出すことはできません。

次の例では、C2264 が生成されます。

```cpp
// C2264.cpp
struct C {
   // Delete the following line to resolve.
   operator int(int = 0){}   // incorrect declaration
};

struct D {
   operator int(){return 0;}   // OK
};

int main() {
   int i;

   C c;
   i = c;   // C2264

   D d;
   i = d;   // OK
}
```
