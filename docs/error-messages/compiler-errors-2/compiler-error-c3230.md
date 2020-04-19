---
title: コンパイラ エラー C3230
ms.date: 11/04/2016
f1_keywords:
- C3230
helpviewer_keywords:
- C3230
ms.assetid: 5ec53f25-59f6-4801-81e7-7b68bf04994d
ms.openlocfilehash: 69ea279ac5e11c03f366711484ba0c250fc50225
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743316"
---
# <a name="compiler-error-c3230"></a>コンパイラ エラー C3230

'function' : 'template' のテンプレート型引数にジェネリック型パラメーター 'param' を含めることはできません

テンプレートはコンパイル時にインスタンス化されますが、ジェネリックは実行時にインスタンス化されます。 したがって、ジェネリック型が最終的に確定する実行時にテンプレートをインスタンス化することはできないため、テンプレートを呼び出せるジェネリック コードを生成することができません。

次の例では C3230 が生成されます。

```cpp
// C3230.cpp
// compile with: /clr /LD
template <class S>
void f(S t);

generic <class U>
ref class C {
   void f1(U x) {
      f(x);   // C3230
   }
};
```
