---
title: コンパイラ エラー C2156
ms.date: 11/04/2016
f1_keywords:
- C2156
helpviewer_keywords:
- C2156
ms.assetid: 136f9c67-2c27-4f61-b7e6-ccd202eca697
ms.openlocfilehash: da8a5a9bcdeb33a9b308e24b129fded0595449a3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755903"
---
# <a name="compiler-error-c2156"></a>コンパイラ エラー C2156

プラグマは、関数の外に指定されなければなりません。

グローバル レベル (関数本体外) で指定する必要があるプラグマが関数内にあります。

次の例では C2156 が生成されます。

```cpp
// C2156.cpp
#pragma optimize( "l", on )   // OK
int main() {
   #pragma optimize( "l", on )   // C2156
}
```
