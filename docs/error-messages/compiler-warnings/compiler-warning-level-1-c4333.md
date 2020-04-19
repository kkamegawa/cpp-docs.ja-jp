---
title: コンパイラの警告 (レベル 1) C4333
ms.date: 11/04/2016
f1_keywords:
- C4333
helpviewer_keywords:
- C4333
ms.assetid: d3763c52-6110-4da0-84db-5264e3f3f166
ms.openlocfilehash: 0b4e567f07d15b47d3c1f507b43257dac9a49d66
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966052"
---
# <a name="compiler-warning-level-1-c4333"></a>コンパイラの警告 (レベル 1) C4333

' operator ': 右シフトが大きすぎるため、データが失われる

右シフト演算が大きすぎて、容量が大きすぎます。  すべての重要なビットがシフトされ、結果は常に0になります。

## <a name="example"></a>例

次の例では、C4333 が生成されます。

```cpp
// C4333.cpp
// compile with: /c /W1
unsigned shift8 (unsigned char c) {
   return c >> 8;   // C4333

   // try the following line instead
   // return c >> 4;   // OK
}
```