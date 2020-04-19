---
title: コンパイラ エラー C2045
ms.date: 11/04/2016
f1_keywords:
- C2045
helpviewer_keywords:
- C2045
ms.assetid: 2fca668e-9b20-4933-987a-18c0fd0187df
ms.openlocfilehash: cf3644c49e424315fb406fa9548fcf6ce1bfcbc7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740378"
---
# <a name="compiler-error-c2045"></a>コンパイラ エラー C2045

'identifier' : ラベルが再定義されました

このラベルは同じ関数内の複数のステートメントの前にあります。

次の例では C2045 が生成されます。

```cpp
// C2045.cpp
int main() {
   label: {
   }
   goto label;
   label: {}   // C2045
}
```
