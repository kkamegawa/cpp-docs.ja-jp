---
title: コンパイラ エラー C2803
ms.date: 11/04/2016
f1_keywords:
- C2803
helpviewer_keywords:
- C2803
ms.assetid: 2cdbe374-8cc4-4c4e-ba15-062a7479e937
ms.openlocfilehash: d39f737ba02f3fa9c9d5f61594ddf730db6739a5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760661"
---
# <a name="compiler-error-c2803"></a>コンパイラ エラー C2803

' operator operator ' には、クラス型の仮引数が少なくとも1つ必要です

オーバーロードされた演算子にクラス型のパラメーターがありません。

参照によってパラメーターを1つ以上渡す必要があります (ポインターを使用しないでください)。または、値によって "a < b" (a と b が型クラス A である) を書き込むことができます。

両方のパラメーターがポインターである場合は、ポインターアドレスの純粋な比較であり、ユーザー定義の変換は使用されません。

次の例では、C2803 が生成されます。

```cpp
// C2803.cpp
// compile with: /c
class A{};
bool operator< (const A *left, const A *right);   // C2803
// try the following line instead
// bool operator< (const A& left, const A& right);
```
