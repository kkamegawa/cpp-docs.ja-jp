---
title: コンパイラ エラー C2100
ms.date: 11/04/2016
f1_keywords:
- C2100
helpviewer_keywords:
- C2100
ms.assetid: 9ed5ea11-9d55-4ddf-8b1a-162c74f3c390
ms.openlocfilehash: 08ff3b138db4ae07b73eb130983903cb60549e15
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752354"
---
# <a name="compiler-error-c2100"></a>コンパイラ エラー C2100

無効な間接参照

間接演算子 (`*`) は nonpointer 値に適用されます。

次の例では、C2100 が生成されます。

```cpp
// C2100.cpp
int main() {
   int r = 0, *s = 0;
   s = &r;
   *r = 200;   // C2100
   *s = 200;   // OK
}
```
