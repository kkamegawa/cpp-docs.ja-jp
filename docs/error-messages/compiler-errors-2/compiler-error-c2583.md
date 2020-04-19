---
title: コンパイラ エラー C2583
ms.date: 11/04/2016
f1_keywords:
- C2583
helpviewer_keywords:
- C2583
ms.assetid: b1c952dc-872c-47e4-9fc8-4dd72bcee6f9
ms.openlocfilehash: a0154d1d9a57d0faa795e639640eb6cb42e7c7cb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748646"
---
# <a name="compiler-error-c2583"></a>コンパイラ エラー C2583

' identifier ': ' const/volatile ' ' this ' ポインターはコンストラクターまたはデストラクターでは無効です

コンストラクターまたはデストラクターが `const` または `volatile`として宣言されています。 これは許可されていません。

次の例では、C2583 が生成されます。

```cpp
// C2583.cpp
// compile with: /c
class A {
public:
   int i;
   A() const;   // C2583

   // try the following line instead
   // A();
};
```
