---
title: コンパイラ エラー C2808
ms.date: 11/04/2016
f1_keywords:
- C2808
helpviewer_keywords:
- C2808
ms.assetid: 3d745102-d3b3-4735-a7d2-ad42d5bf3cfa
ms.openlocfilehash: c5be25e8606329589e1ac3a215f30fe6ce74c594
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760596"
---
# <a name="compiler-error-c2808"></a>コンパイラ エラー C2808

単項演算子 ' operator operator ' に含まれている仮引数が多すぎます

単項演算子に void 以外のパラメーターリストがあります。

次の例では、C2808 が生成されます。

```cpp
// C2808.cpp
// compile with: /c
class X {
public:
   X operator! ( X );   // C2808 nonvoid parameter list
   X operator! ( void );   // OK
};
```
