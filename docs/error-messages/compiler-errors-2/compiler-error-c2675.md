---
title: コンパイラエラー C2675
ms.date: 11/04/2016
f1_keywords:
- C2675
helpviewer_keywords:
- C2675
ms.assetid: 4b92a12b-bff8-4dd5-a109-620065fc146c
ms.openlocfilehash: 0b7b81ce7314fbad02d6873403fc5cf1bdd54709
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760375"
---
# <a name="compiler-error-c2675"></a>コンパイラエラー C2675

単項演算子 ' operator ': ' type ' は、この演算子または定義済みの演算子に使用できる型への変換を定義していません

単項演算子を使用するときに C2675 を使用することもできます。また、型によって演算子が定義されていないか、または定義済みの演算子で受け入れ可能な型への変換も行われません。 この演算子を使うには、型を指定してこの演算子をオーバーロードするか、この演算子が定義された型への変換を定義する必要があります。

## <a name="example"></a>使用例

次の例では、C2675 が生成されます。

```cpp
// C2675.cpp
struct C {
   C(){}
} c;

struct D {
   D(){}
   void operator-(){}
} d;

int main() {
   -c;   // C2675
   -d;   // OK
}
```
