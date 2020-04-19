---
title: コンパイラの警告 (レベル 1) C4630
ms.date: 11/04/2016
f1_keywords:
- C4630
helpviewer_keywords:
- C4630
ms.assetid: d8926376-7acc-4fc7-8438-6f0de3468870
ms.openlocfilehash: 893364183594782b825377f57fa4e525338d62d8
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052556"
---
# <a name="compiler-warning-level-1-c4630"></a>コンパイラの警告 (レベル 1) C4630

' symbol ': ' extern ' ストレージクラス指定子がメンバー定義で無効です。

データメンバーまたはメンバー関数は、`extern`として定義されます。 オブジェクト全体を使用できますが、メンバーを外部にすることはできません。 コンパイラは `extern` キーワードを無視します。 次の例では、C4630 が生成されます。

```cpp
// C4630.cpp
// compile with: /W1 /LD
class A {
   void func();
};

extern void A::func() {   // C4630, remove 'extern' to resolve
}
```