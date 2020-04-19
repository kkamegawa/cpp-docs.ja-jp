---
title: コンパイラ エラー C2443
ms.date: 11/04/2016
f1_keywords:
- C2443
helpviewer_keywords:
- C2443
ms.assetid: 315330d5-24bc-4193-a531-0642095be58f
ms.openlocfilehash: a088f86e09671bb07b516cbae279f31d75717308
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744213"
---
# <a name="compiler-error-c2443"></a>コンパイラ エラー C2443

オペランドのサイズの競合

命令では、オペランドのサイズが同じである必要があります。

次の例では、C2443 が生成されます。

```cpp
// C2443.cpp
// processor: x86
short var;
int main() {
   __asm xchg ax,bl   // C2443
   __asm mov al,red   // C2443
   __asm mov al,BYTE PTR var   // OK
}
```
