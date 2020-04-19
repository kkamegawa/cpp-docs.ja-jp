---
title: コンパイラ エラー C2460
ms.date: 11/04/2016
f1_keywords:
- C2460
helpviewer_keywords:
- C2460
ms.assetid: d969fca9-3ac5-4e4e-88fc-df05510e2093
ms.openlocfilehash: a7d20a7658a75a492e19b9e81acaa3b6fce5cae7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743940"
---
# <a name="compiler-error-c2460"></a>コンパイラ エラー C2460

' identifier1 ': 定義されている ' identifier2 ' を使用します

クラスまたは構造体 (`identifier2`) がそれ自体のメンバーとして宣言されています (`identifier1`)。 クラスと構造体の再帰定義は許可されていません。

次の例では、C2460 が生成されます。

```cpp
// C2460.cpp
class C {
   C aC;    // C2460
};
```

代わりに、クラスでポインター参照を使用します。

```cpp
// C2460.cpp
class C {
   C * aC;    // OK
};
```
