---
title: コンパイラ エラー C2528
ms.date: 11/04/2016
f1_keywords:
- C2528
helpviewer_keywords:
- C2528
ms.assetid: 2ea9d583-67a8-4b16-b35f-a50eeffc03c4
ms.openlocfilehash: f8712cfbd34e852cf852cf9758446849d75d8bdc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756267"
---
# <a name="compiler-error-c2528"></a>コンパイラ エラー C2528

' name ': 参照へのポインターが無効です。

参照へのポインターを宣言することはできません。 ポインターを宣言する前に、変数を逆参照してください。

次の例では、C2528 が生成されます。

```cpp
// C2528.cpp
int i;
int &ir = i;
int & (*irptr) = ir;    // C2528
```
