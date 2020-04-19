---
title: コンパイラの警告 (レベル 1) C4405
ms.date: 11/04/2016
f1_keywords:
- C4405
helpviewer_keywords:
- C4405
ms.assetid: 155c64d6-58ae-4455-b61f-ccd711c5da96
ms.openlocfilehash: 182f9ff061fd2a8ebe5ea0046545412fca5f646a
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965586"
---
# <a name="compiler-warning-level-1-c4405"></a>コンパイラの警告 (レベル 1) C4405

' identifier ': 識別子は予約語です

インラインアセンブリ用に予約された単語は、変数名として使用されます。 これにより、予測できない結果が生じる可能性があります。 この警告を解決するには、インラインアセンブリ用に予約されている単語に変数の名前を付けないようにします。 次の例では、C4405 が生成されます。

```cpp
// C4405.cpp
// compile with: /W1
// processor: x86
void func1() {
   int mov = 0, i = 0;
   _asm {
      mov mov, 0;   // C4405
      // instead, try ..
      // mov i, 0;
   }
}

int main() {
}
```