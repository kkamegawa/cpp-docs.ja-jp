---
title: コンパイラ エラー C2469
ms.date: 11/04/2016
f1_keywords:
- C2469
helpviewer_keywords:
- C2469
ms.assetid: 3814bdff-581a-4d3e-8b47-8de6887cea69
ms.openlocfilehash: eafb3ed3a26fe127b39558542b6d415be65cefb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743758"
---
# <a name="compiler-error-c2469"></a>コンパイラ エラー C2469

'operator': 'type' オブジェクトを割り当てることができません

演算子に無効な型が渡されました。

次の例では C2469 が生成されます。

```cpp
// C2469.cpp
int main() {
   int *i = new void;   // C2469
   int *i = new int;   // OK
}
```
