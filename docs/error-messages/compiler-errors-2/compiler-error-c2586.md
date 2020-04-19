---
title: コンパイラ エラー C2586
ms.date: 11/04/2016
f1_keywords:
- C2586
helpviewer_keywords:
- C2586
ms.assetid: dae703c7-5c38-4db6-8411-4d1b22713eb5
ms.openlocfilehash: be98f475bdcfb4dfdd7f7f37d78f4977d71c52b1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755422"
---
# <a name="compiler-error-c2586"></a>コンパイラ エラー C2586

不適切なユーザー定義の変換構文です: 間接指定が無効です。

変換演算子の間接参照は許可されていません。

次の例では、C2586 が生成されます。

```cpp
// c2586.cpp
// compile with: /c
struct C {
   * operator int();   // C2586
   operator char();   // OK
};
```
