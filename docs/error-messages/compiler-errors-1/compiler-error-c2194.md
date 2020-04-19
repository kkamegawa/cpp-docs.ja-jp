---
title: コンパイラ エラー C2194
ms.date: 11/04/2016
f1_keywords:
- C2194
helpviewer_keywords:
- C2194
ms.assetid: df6e631c-0062-4844-9088-4cc7a0ff879f
ms.openlocfilehash: 7d7c1324ea295752a09cf9c87ef37164ab6a06db
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758542"
---
# <a name="compiler-error-c2194"></a>コンパイラ エラー C2194

' identifier ': テキストセグメントです

`data_seg` プラグマは、`code_seg`と共に使用されるセグメント名を使用します。

次の例では、C2194 が生成されます。

```cpp
// C2194.cpp
// compile with: /c
#pragma code_seg("MYCODE")
#pragma data_seg("MYCODE")   // C2194
#pragma data_seg("MYCODE2")   // OK
```
