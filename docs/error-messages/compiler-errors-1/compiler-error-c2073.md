---
title: コンパイラエラー C2073
ms.date: 11/04/2016
f1_keywords:
- C2073
helpviewer_keywords:
- C2073
ms.assetid: 57908234-be7a-4ce9-b0a7-8b1ad621865e
ms.openlocfilehash: 545b2b24d3bfe5a36c5554dfa898d17b05067c3d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757736"
---
# <a name="compiler-error-c2073"></a>コンパイラエラー C2073

' identifier ': 部分的に初期化された配列の要素には既定のコンストラクターが必要です

ユーザー定義型または定数の配列に指定された初期化子が少なすぎます。 明示的な初期化子とそれに対応するコンストラクターが配列メンバーに対して指定されていない場合は、既定のコンストラクターを指定する必要があります。

次の例では、C2073 が生成されます。

```cpp
// C2073.cpp
class A {
public:
   A( int );   // constructor for ints only
};
A a[3] = { A(1), A(2) };   // C2073, no default constructor
```

```cpp
// C2073b.cpp
// compile with: /c
class B {
public:
   B();   // default constructor declared
   B( int );
};
B b[3] = { B(1), B(2) };   // OK
```
