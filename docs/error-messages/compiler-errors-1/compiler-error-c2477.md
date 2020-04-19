---
title: コンパイラ エラー C2477
ms.date: 11/04/2016
f1_keywords:
- C2477
helpviewer_keywords:
- C2477
ms.assetid: 60bc324b-6605-4833-8099-a291efc712e7
ms.openlocfilehash: aa276ea839f11574609b183d78b46e08581a1b51
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743654"
---
# <a name="compiler-error-c2477"></a>コンパイラ エラー C2477

' member ': 静的データメンバーを派生クラスで初期化することはできません

テンプレートクラスの静的データメンバーが正しく初期化されませんでした。 これは、ISO C++ C++標準に準拠するために、Visual Studio .net 2003 より前のバージョンの Microsoft compiler では互換性に影響する変更点です。

次の例では、C2477 が生成されます。

```cpp
// C2477.cpp
// compile with: /Za /c
template <class T>
struct S {
   static int n;
};

struct X {};
struct A: S<X> {};

int A::n = 0;   // C2477

template<>
int S<X>::n = 0;
```
