---
title: コンパイラエラー C2706
ms.date: 11/04/2016
f1_keywords:
- C2706
helpviewer_keywords:
- C2706
ms.assetid: e18da924-c42d-4b09-8e29-f4e0382d7dc6
ms.openlocfilehash: bca86d3c0cf886c64a1d668468c793d0e77b2867
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757463"
---
# <a name="compiler-error-c2706"></a>コンパイラエラー C2706

一致する _try \_のない __except があります (\__try ブロックに '} ' がありません)。

コンパイラで、`__try` ブロックの右中かっこが見つかりませんでした。

次の例では、C2706 が生成されます。

```cpp
// C2706.cpp
int main() {
   __try {
      void f();
   // C2706  } missing here
   __except(GetExceptionCode() == 0x0) {
   }
}
```
