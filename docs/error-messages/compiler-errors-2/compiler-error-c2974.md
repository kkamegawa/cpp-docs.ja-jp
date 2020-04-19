---
title: コンパイラ エラー C2974
ms.date: 11/04/2016
f1_keywords:
- C2974
helpviewer_keywords:
- C2974
ms.assetid: 1b444260-f2bf-48d7-ab1e-35573d8c4a0e
ms.openlocfilehash: fb66a4f1edb40c107a094fea4e1ab61d74f0c7ac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757658"
---
# <a name="compiler-error-c2974"></a>コンパイラ エラー C2974

型引数 ' number ' が無効です。型が必要です。

ジェネリックまたはテンプレート引数がジェネリックまたはテンプレート宣言と一致しません。 山かっこ内に型が含まれている必要があります。 ジェネリックまたはテンプレートの定義を確認して、正しい型を見つけてください。

次の例では、C2974 が生成されます。

```cpp
// C2974.cpp
// C2974 expected
template <class T>
struct TC {};

template <typename T>
void tf(T){}

int main() {
   // Delete the following 2 lines to resolve
   TC<1>* tc;
   tf<"abc">("abc");

   TC<int>* tc;
   tf<const char *>("abc");
}
```

C2974 は、ジェネリックを使用する場合にも発生する可能性があります。

```cpp
// C2974b.cpp
// compile with: /clr
// C2974 expected
using namespace System;
generic <class T>
ref struct GCtype {};

generic <typename T>
void gf(T){}

int main() {
   // Delete the following 2 lines to resolve
   GCtype<"a">^ gc;
   gf<"a">("abc");

   // OK
   GCtype<int>^ gc;
   gf<String ^>("abc");
}
```
