---
title: コンパイラ エラー C2133
ms.date: 11/04/2016
f1_keywords:
- C2133
helpviewer_keywords:
- C2133
ms.assetid: 8942f9e8-9818-468f-97db-09dbd124fcae
ms.openlocfilehash: b51b556ea576e02b85a5c2ee5032909af39c7b2f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758438"
---
# <a name="compiler-error-c2133"></a>コンパイラ エラー C2133

' identifier ': サイズが不明です

可変長配列は、クラス、構造体、共用体、または列挙体のメンバーとして宣言されます。 /Za (ANSI C) オプションでは、可変長メンバー配列は許可されません。

次の例では、C2133 が生成されます。

```cpp
// C2133.cpp
// compile with: /Za
struct X {
   int a[0];   // C2133 unsized array
};
```

解決方法:

```cpp
// C2133b.cpp
// compile with: /c
struct X {
   int a[0];   // no /Za
};
```
