---
title: コンパイラ エラー C2372
ms.date: 11/04/2016
f1_keywords:
- C2372
helpviewer_keywords:
- C2372
ms.assetid: 406bea63-c8d3-4231-9d26-c70af6980840
ms.openlocfilehash: d5f4653ded6d2800d74418a712bbcb3d4d4d6676
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745617"
---
# <a name="compiler-error-c2372"></a>コンパイラ エラー C2372

' identifier ': 再定義します。さまざまな種類の間接参照

識別子は、別の派生型で既に定義されています。

次の例では C2326 が生成されます。

```cpp
// C2372.cpp
// compile with: /c
extern int *fp;
extern int fp[];   // C2372
extern int fp2[];   // OK
```
