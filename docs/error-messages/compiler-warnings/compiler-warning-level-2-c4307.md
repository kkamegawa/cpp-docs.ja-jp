---
title: コンパイラの警告 (レベル 2) C4307
ms.date: 11/04/2016
f1_keywords:
- C4307
helpviewer_keywords:
- C4307
ms.assetid: 7cca11e9-be61-49e4-8b15-88b84f0cbf07
ms.openlocfilehash: b5566bca22c328328a49e82268b96e8ec0fedc95
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052067"
---
# <a name="compiler-warning-level-2-c4307"></a>コンパイラの警告 (レベル 2) C4307

' operator ': 整数定数がオーバーフローしています。

演算子は、割り当てられた領域を整数定数でオーバーフローする式で使用されます。 定数には、より大きな型を使用することが必要になる場合があります。 符号**付き整数は**、符号を表すために1ビット**を使用する**ため、`unsigned int` よりも小さい値を保持します。

次の例では、C4307 が生成されます。

```cpp
// C4307.cpp
// compile with: /W2
int i = 2000000000 + 2000000000;   // C4307
int j = (unsigned)2000000000 + 2000000000;   // OK

int main()
{
}
```