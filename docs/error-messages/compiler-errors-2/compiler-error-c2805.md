---
title: コンパイラ エラー C2805
ms.date: 11/04/2016
f1_keywords:
- C2805
helpviewer_keywords:
- C2805
ms.assetid: c997dc56-e199-442f-b94e-ac551ec9b015
ms.openlocfilehash: 500660d70616a530fce3d8674f0f116ce219d1d8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760635"
---
# <a name="compiler-error-c2805"></a>コンパイラ エラー C2805

バイナリ ' operator operator ' のパラメーターが少なすぎます

二項演算子にはパラメーターがありません。

次の例では、C2805 が生成されます。

```cpp
// C2805.cpp
// compile with: /c
class X {
public:
   X operator< ( void );   // C2805 must take one parameter
   X operator< ( X );   // OK
};
```
