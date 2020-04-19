---
title: コンパイラエラー C2739
ms.date: 11/04/2016
f1_keywords:
- C2739
helpviewer_keywords:
- C2739
ms.assetid: 5b63e435-7631-43d7-805e-f2adefb7e517
ms.openlocfilehash: 18cece8d9630aa93e867329acc7cefea30da3286
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759660"
---
# <a name="compiler-error-c2739"></a>コンパイラエラー C2739

'number': 明示的なマネージドまたは WinRT 配列の次元は 1 から 32 の間でなければなりません

配列の次元が 1 ～ 32 ではありませんでした。

次の例では、C2739 を生成し、その修正方法を示しています。

```cpp
// C2739.cpp
// compile with: /clr
int main() {
   array<int, -1>^a;   // C2739
   // try the following line instead
   // array<int, 2>^a;
}
```
