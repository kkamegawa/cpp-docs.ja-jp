---
title: コンパイラ エラー C2048
ms.date: 11/04/2016
f1_keywords:
- C2048
helpviewer_keywords:
- C2048
ms.assetid: 44704726-85fc-42f0-afb9-194df8c4ca7c
ms.openlocfilehash: 039be85541a7cd3864187433e5b3299bca7d067e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740131"
---
# <a name="compiler-error-c2048"></a>コンパイラ エラー C2048

switch 文の中に 2 つ以上の 'default' があります。

`switch` ステートメントに複数の `default` ラベルが含まれています。 このエラーを解決するには、 `default` ラベルを 1 つ削除します。

次の例では C2048 が生成されます。

```cpp
// C2048.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
      default:   // C2048
         a = 3;
   }
}
```

解決方法:

```cpp
// C2048b.cpp
int main() {
   int a = 1;
   switch (a) {
      case 1:
         a = 0;
      default:
         a = 2;
   }
}
```
