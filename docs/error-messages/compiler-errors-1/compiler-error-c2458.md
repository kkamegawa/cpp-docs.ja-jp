---
title: コンパイラ エラー C2458
ms.date: 11/04/2016
f1_keywords:
- C2458
helpviewer_keywords:
- C2458
ms.assetid: ed21901f-1067-42f5-b275-19b480decf5c
ms.openlocfilehash: 93e0159ca680b37aed2031c6e2ec41463e7e389d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744005"
---
# <a name="compiler-error-c2458"></a>コンパイラ エラー C2458

' identifier ': 定義内で再定義します

クラス、構造体、共用体、または列挙型は、独自の宣言で再定義されます。

次の例では、C2458 が生成されます。

```cpp
// C2458.cpp
class C {
   enum i { C };   // C2458
};
```
