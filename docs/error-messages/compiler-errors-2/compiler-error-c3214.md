---
title: コンパイラ エラー C3214
ms.date: 11/04/2016
f1_keywords:
- C3214
helpviewer_keywords:
- C3214
ms.assetid: 49ee4a9a-2549-4adb-9d3a-38e154303c2e
ms.openlocfilehash: 4eda0abd0bbfb3bf5757e39062fa3c229f698624
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756189"
---
# <a name="compiler-error-c3214"></a>コンパイラ エラー C3214

'type': ジェネリック 'generic_type' のジェネリック パラメーター 'param' の型引数が無効です。制約 'constraint' を満たしていません

ジェネリック クラスの制約を満たしていないジェネリック クラスをインスタンス化するために型を指定しました。

次の例では C3214 が生成されます。

```cpp
// C3214.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A
ref class C {};

ref class X : public A {};

int main() {
   C<int>^ c = new C<int>;   // C3214
   C<X ^> ^ c2 = new C<X^>;   // OK
}
```
