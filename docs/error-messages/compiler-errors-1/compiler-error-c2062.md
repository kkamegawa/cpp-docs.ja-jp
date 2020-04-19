---
title: コンパイラエラー C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: a709a540b24756a7e08f98552c5888a55c3ea601
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735971"
---
# <a name="compiler-error-c2062"></a>コンパイラエラー C2062

予期しない型 ' type ' です

コンパイラは型名を予期していませんでした。

次の例では、C2062 が生成されます。

```cpp
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

C2062 は、コンパイラがコンストラクターのパラメーターリストで未定義の型を処理する方法によって発生することもあります。 コンパイラが未定義の (スペルミスの) 型を検出した場合は、コンストラクターが式であると想定し、C2062 を発行します。 解決するには、コンストラクターのパラメーターリストで定義されている型のみを使用します。
