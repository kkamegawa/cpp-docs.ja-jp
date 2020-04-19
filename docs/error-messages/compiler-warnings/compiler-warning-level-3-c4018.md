---
title: コンパイラの警告 (レベル 3) C4018 由来
ms.date: 11/04/2016
f1_keywords:
- C4018
helpviewer_keywords:
- C4018
ms.assetid: 6e8cbb04-d914-4319-b431-cbc2fbe40eb1
ms.openlocfilehash: e136a82f8a0ecb3f5375d3a486dd017df7edb6e0
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051982"
---
# <a name="compiler-warning-level-3-c4018"></a>コンパイラの警告 (レベル 3) C4018 由来

' expression ': 符号付きまたは符号なしの不一致です。

符号付きと符号なしの数値を比較するには、コンパイラが符号付きの値を符号なしに変換する必要がありました。

この警告は、署名付きの型と符号なしの型をテストするときに、2つの型のいずれかをキャストすると解決される場合があります。

次の例では、C4018 由来が生成されます。

```cpp
// C4018.cpp
// compile with: /W3
int main() {
   unsigned int uc = 0;
   int c = 0;
   unsigned int c2 = 0;

   if (uc < c) uc = 0;   // C4018

   // OK
   if (uc == c2) uc = 0;
}
```