---
title: コンパイラ エラー C2258
ms.date: 11/04/2016
f1_keywords:
- C2258
helpviewer_keywords:
- C2258
ms.assetid: 105eaa87-befb-4ecb-9a3f-e09e14d2f5bf
ms.openlocfilehash: 916ccf444bf82c9d6c0c9ad290afb65353a4f5b2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758802"
---
# <a name="compiler-error-c2258"></a>コンパイラ エラー C2258

純粋仮想関数の宣言に構文上の誤りがあります、'= 0' でなければなりません。

純粋仮想関数が正しくない構文で宣言されています。

次の例では C2258 が生成されます。

```cpp
// C2258.cpp
// compile with: /c
class A {
public:
   void virtual func1() = 1; // C2258
   void virtual func2() = 0;   // OK
};
```
