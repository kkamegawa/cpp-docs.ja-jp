---
title: コンパイラの警告 (レベル 1) C4401
ms.date: 11/04/2016
f1_keywords:
- C4401
helpviewer_keywords:
- C4401
ms.assetid: 2e7ca136-f144-4b40-b847-82976e8643fc
ms.openlocfilehash: 242c854339608c88d139c898d81d142c52f90134
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966312"
---
# <a name="compiler-warning-level-1-c4401"></a>コンパイラの警告 (レベル 1) C4401

' ビットフィールド ': メンバーはビットフィールドです

インラインアセンブリコードは、ビットフィールドメンバーにアクセスしようとします。 インラインアセンブリはビットフィールドメンバーにアクセスできないため、ビットフィールドメンバーが使用される前の最後のパッキング境界が使用されます。

この警告を回避するには、インラインアセンブリコードで参照を作成する前に、ビットフィールドを適切な型にキャストします。 次の例では、C4401 が生成されます。

```cpp
// C4401.cpp
// compile with: /W1
// processor: x86
typedef struct bitfield {
   signed bit : 1;
} mybitfield;

int main() {
   mybitfield bf;
   bf.bit = 0;
   __asm {
      mov bf.bit,0;   // C4401
   }

   /* use the following __asm block to resolve the warning
   int i = (int)bf.bit;
   __asm {
      mov i,0;
   }
   */
}
```