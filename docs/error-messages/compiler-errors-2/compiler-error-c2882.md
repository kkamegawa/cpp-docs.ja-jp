---
title: コンパイラ エラー C2882
ms.date: 11/04/2016
f1_keywords:
- C2882
helpviewer_keywords:
- C2882
ms.assetid: 617018ee-5a0d-4b8d-9612-77e8ae52679b
ms.openlocfilehash: a1c6f20ae33a545ae2e6bd7b373ecf2444e0d1d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736166"
---
# <a name="compiler-error-c2882"></a>コンパイラ エラー C2882

' name ': 式の中で名前空間の識別子が正しく使用されることはありません

式で名前空間の名前を使用しようとしました。

次の例では、C2882 が生成されます。

```cpp
// C2882.cpp
// compile with: /c
namespace A {
   int k;
}

int i = A;   // C2882, can't assign A to i
```
