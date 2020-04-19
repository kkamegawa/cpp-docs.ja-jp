---
title: コンパイラエラー C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: e30ed7016ca3a4d4948a08c5c09268e52c9a407d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761674"
---
# <a name="compiler-error-c3181"></a>コンパイラエラー C3181

' type ': 演算子に対して無効なオペランドです

[Typeid](../../extensions/typeid-cpp-component-extensions.md)演算子に無効なパラメーターが渡されました。 パラメーターはマネージ型である必要があります。

コンパイラは、共通言語ランタイムの型にマップされるネイティブ型にエイリアスを使用することに注意してください。

次の例では、C3181 が生成されます。

```cpp
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```
