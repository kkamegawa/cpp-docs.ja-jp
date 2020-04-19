---
title: コンパイラエラー C2087
ms.date: 11/04/2016
f1_keywords:
- C2087
helpviewer_keywords:
- C2087
ms.assetid: 89761e83-415a-4468-a4c6-b6dedfd1dd6a
ms.openlocfilehash: 576ac394585b91f7c6ceadcdd07d25c639854990
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757905"
---
# <a name="compiler-error-c2087"></a>コンパイラエラー C2087

' identifier ': 添字がありません。

複数の添字を持つ配列の定義に、1より大きい次元の添字の値がありません。

次の例では、C2087 が生成されます。

```cpp
// C2087.cpp
int main() {
   char a[10][];   // C2087
}
```

解決方法:

```cpp
// C2087b.cpp
int main() {
   char b[4][5];
}
```
