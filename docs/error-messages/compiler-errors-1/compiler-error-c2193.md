---
title: コンパイラ エラー C2193
ms.date: 11/04/2016
f1_keywords:
- C2193
helpviewer_keywords:
- C2193
ms.assetid: 9813e853-d581-4f51-bb75-4e242298a844
ms.openlocfilehash: 25ebfc73fb46eca3a27875075af2d4ed46ed2fef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758555"
---
# <a name="compiler-error-c2193"></a>コンパイラ エラー C2193

' identifier ': 既にセグメントに含まれています

関数は、`alloc_text` と `code_seg` プラグマを使用して2つの異なるセグメントに配置されました。

次の例では、C2193 が生成されます。

```cpp
// C2193.cpp
// compile with: /c
extern "C" void MYFUNCTION();
#pragma alloc_text(MYCODE, MYFUNCTION)
#pragma code_seg("MYCODE2")
extern "C" void MYFUNCTION() {}   // C2193
extern "C" void MYFUNCTION2() {}
```
