---
title: コンパイラ エラー C2807
ms.date: 11/04/2016
f1_keywords:
- C2807
helpviewer_keywords:
- C2807
ms.assetid: bd7a207a-f379-4de6-8ee8-c7cab78b3480
ms.openlocfilehash: 8376f7aba0d090fa43ae675fe32cbfee182a6230
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760609"
---
# <a name="compiler-error-c2807"></a>コンパイラ エラー C2807

後置形式の ' operator operator ' に対する2番目の仮パラメーターは ' int ' でなければなりません

後置演算子の2番目のパラメーターの型が正しくありません。

次の例では、C2807 が生成されます。

```cpp
// C2807.cpp
// compile with: /c
class X {
public:
   X operator++ ( X );   // C2807 nonvoid parameter
   X operator++ ( int );   // OK, int parameter
};
```
