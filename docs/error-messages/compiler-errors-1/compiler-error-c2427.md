---
title: コンパイラ エラー C2427
ms.date: 11/04/2016
f1_keywords:
- C2427
helpviewer_keywords:
- C2427
ms.assetid: a7d421af-6180-40b4-b7a6-9f3bc7dfaaf9
ms.openlocfilehash: d92f3bce54a4558702d2a6d3870323eb0edd5d4d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744616"
---
# <a name="compiler-error-c2427"></a>コンパイラ エラー C2427

' class ': このスコープではクラスを定義できません

入れ子になったクラスを定義しようとしましたが、入れ子になったクラスは基底クラスのメンバーであり、最も外側のクラスではありません。

次の例では、C2427 が生成されます。

```cpp
// C2427.cpp
// compile with: /c
template <class T>
struct S {
   struct Inner;
};

struct Y : S<int> {};

struct Y::Inner {};   // C2427

// OK
template<typename T>
struct S<T>::Inner {};
```
