---
title: コンパイラの警告 (レベル 1) C4558
ms.date: 11/04/2016
f1_keywords:
- C4558
helpviewer_keywords:
- C4558
ms.assetid: 52bb0324-7bec-468c-b35b-13a08d38e578
ms.openlocfilehash: d47e2a619cb84838144b3be6fd45d1f79ecc8661
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965999"
---
# <a name="compiler-warning-level-1-c4558"></a>コンパイラの警告 (レベル 1) C4558

オペランド ' value ' の値が ' 上限 ' の範囲外です

アセンブリ言語命令に渡された値が、パラメーターに指定された範囲を超えています。 値は切り捨てられます。

次の例では、C4558 が生成されます。

```cpp
// C4558.cpp
// compile with: /W1
// processor: x86
void asm_test() {
   __asm pinsrw   mm1, eax, 8;   // C4558
}

int main() {
}
```