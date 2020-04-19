---
title: コンパイラ エラー C2380
ms.date: 11/04/2016
f1_keywords:
- C2380
helpviewer_keywords:
- C2380
ms.assetid: 717b1e6e-ddfe-4bac-a5f3-7f9a4dcb1572
ms.openlocfilehash: ca249bc592bd66c2e461a37fdc18204077f51db2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745435"
---
# <a name="compiler-error-c2380"></a>コンパイラ エラー C2380

' identifier ' の前の型 (戻り値の型を持つコンストラクター、または現在のクラス名の再定義が無効です)

コンストラクターは、値を返すか、またはクラス名を再定義します。

次の例では C2326 が生成されます。

```cpp
// C2380.cpp
// compile with: /c
class C {
public:
   int C();   // C2380, specifies an int return
   int C;   // C2380, redefinition of i
   C();   // OK
};
```
