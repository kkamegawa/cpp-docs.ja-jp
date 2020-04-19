---
title: コンパイラ エラー C3149
ms.date: 11/04/2016
f1_keywords:
- C3149
helpviewer_keywords:
- C3149
ms.assetid: cf6e2616-2f06-46da-8a8a-d449cb481c51
ms.openlocfilehash: 263eb03b7a9f45458f8d8b586adc6f1cfc5805be
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745981"
---
# <a name="compiler-error-c3149"></a>コンパイラ エラー C3149

' type ': 最上位の ' char ' を指定せずにこの型を使用することはできません

宣言が正しく指定されていません。

たとえば、CLR 型をグローバルスコープで定義し、その型の変数を定義の一部として作成しようとした場合などです。 CLR 型のグローバル変数は使用できないため、コンパイラは C3149 を生成します。

このエラーを解決するには、関数または型定義内で CLR 型の変数を宣言します。

次の例では、C3149 が生成されます。

```cpp
// C3149.cpp
// compile with: /clr
using namespace System;
int main() {
   // declare an array of value types
   array< Int32 ^> IntArray;   // C3149
   array< Int32>^ IntArray2;   // OK
}
```

次の例では、C3149 が生成されます。

```cpp
// C3149b.cpp
// compile with: /clr /c
delegate int MyDelegate(const int, int);
void Test1(MyDelegate m) {}   // C3149
void Test2(MyDelegate ^ m) {}   // OK
```
