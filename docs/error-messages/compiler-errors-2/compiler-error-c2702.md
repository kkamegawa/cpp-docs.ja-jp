---
title: コンパイラエラー C2702
ms.date: 11/04/2016
f1_keywords:
- C2702
helpviewer_keywords:
- C2702
ms.assetid: 6def15d4-9a8d-43e7-ae35-42d7cb57c27e
ms.openlocfilehash: 03a982ee35f0ac49a12568fc428de333f57f3ffa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758321"
---
# <a name="compiler-error-c2702"></a>コンパイラエラー C2702

__except が終了ブロックに含まれていない可能性があります

例外ハンドラー (`__try`/`__except`) を `__finally` ブロック内に入れ子にすることはできません。

次の例では、C2702 が生成されます。

```cpp
// C2702.cpp
// processor: x86 IPF
int Counter;
int main() {
   __try {}
   __finally {
      __try {}   // C2702
      __except( Counter ) {}   // C2702
   }
}
```
