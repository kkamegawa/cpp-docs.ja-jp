---
title: コンパイラ エラー C2203
ms.date: 11/04/2016
f1_keywords:
- C2203
helpviewer_keywords:
- C2203
ms.assetid: 5497df43-86f6-43d5-b6cb-723c4c589b10
ms.openlocfilehash: db36afa1376a0b64b3e110acd1722d3e0f2af449
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758958"
---
# <a name="compiler-error-c2203"></a>コンパイラ エラー C2203

delete 演算子で配列の境界を指定することはできません

**/Za** (ANSI) オプションを使用すると、`delete` 演算子は配列全体を削除できますが、配列の一部または特定のメンバーを削除することはできません。

次の例では、C2203 が生成されます。

```cpp
// C2203.cpp
// compile with: /Za
int main() {
   int *ar = new int[10];
   delete [4] ar;   // C2203
   // try the following line instead
   // delete [] ar;
}
```
