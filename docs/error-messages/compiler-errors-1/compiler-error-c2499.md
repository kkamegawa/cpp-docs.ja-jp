---
title: コンパイラ エラー C2499
ms.date: 11/04/2016
f1_keywords:
- C2499
helpviewer_keywords:
- C2499
ms.assetid: b323ff4d-b3c1-4bfd-b052-ae7292d53222
ms.openlocfilehash: 29fbb691304f9fc101f2367e014ae1e4e2231ff0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756982"
---
# <a name="compiler-error-c2499"></a>コンパイラ エラー C2499

' class ': クラスは、それ自体の基底クラスにすることはできません

定義しようとしているクラスを基底クラスとして指定しようとしました。

次の例では、C2499 が生成されます。

```cpp
// C2499.cpp
// compile with: /c
class CMyClass : public CMyClass {};   // C2499
class CMyClass{};   // OK
```
