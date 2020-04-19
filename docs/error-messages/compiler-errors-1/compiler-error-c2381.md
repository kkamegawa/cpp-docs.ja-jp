---
title: コンパイラ エラー C2381
ms.date: 11/04/2016
f1_keywords:
- C2381
helpviewer_keywords:
- C2381
ms.assetid: cc765f67-64ac-406f-93ef-ae7d548d58d7
ms.openlocfilehash: 834b9939a99c694c702bb268b928575b4beb8856
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745396"
---
# <a name="compiler-error-c2381"></a>コンパイラ エラー C2381

' function ': 再定義します。__declspec (noreturn) が異なる

関数が宣言されて定義されましたが、定義では[noreturn](../../cpp/noreturn.md) `__declspec` 修飾子が使用されています。 `noreturn` を使用すると、関数の再定義が構成されます。宣言と定義は、`noreturn`の使用に同意する必要があります。

次の例では、C2381 が生成されます。

```cpp
// C2381.cpp
// compile with: /c
void f1();
void __declspec(noreturn) f1() {}   // C2381
void __declspec(noreturn) f2() {}   // OK
```
