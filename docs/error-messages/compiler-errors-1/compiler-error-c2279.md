---
title: コンパイラ エラー C2279
ms.date: 11/04/2016
f1_keywords:
- C2279
helpviewer_keywords:
- C2279
ms.assetid: 1b5c88ef-2336-49b8-9ddb-d61f97c73e14
ms.openlocfilehash: b3b37788d6e4727761ab993f0502746edace18e9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759179"
---
# <a name="compiler-error-c2279"></a>コンパイラ エラー C2279

例外指定は typedef 宣言には記述できません

**/Za**では、typedef 宣言では[例外指定](../../cpp/exception-specifications-throw-cpp.md)は許可されません。

次の例では、C2279 が生成されます。

```cpp
// C2279.cpp
// compile with: /Za /c
typedef int (*xy)() throw(...);   // C2279
typedef int (*xyz)();   // OK
```
