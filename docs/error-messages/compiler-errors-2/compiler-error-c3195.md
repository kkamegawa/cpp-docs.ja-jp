---
title: コンパイラエラー C3195
ms.date: 11/04/2016
f1_keywords:
- C3195
helpviewer_keywords:
- C3195
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
ms.openlocfilehash: c8274e121e953c3e51a0f2ff8c68c315759ce3e1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760427"
---
# <a name="compiler-error-c3195"></a>コンパイラエラー C3195

'operator' : 予約されているため、値型または ref クラスのメンバーとして使用することはできません。 CLR または WinRT の演算子は、'operator' キーワードを使用して定義されなければなりません

コンパイラは、C++ マネージド拡張構文を使用した演算子定義を検出しました。 演算子にはC++構文を使用する必要があります。

次の例では、C3195 を生成し、その修正方法を示しています。

```cpp
// C3195.cpp
// compile with: /clr /LD
#using <mscorlib.dll>
value struct V {
   static V op_Addition(V v, int i);   // C3195
   static V operator +(V v, char c);   // OK for new C++ syntax
};
```
