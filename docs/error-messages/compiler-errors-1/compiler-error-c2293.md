---
title: コンパイラ エラー C2293
ms.date: 11/04/2016
f1_keywords:
- C2293
helpviewer_keywords:
- C2293
ms.assetid: 17e7b4e2-368b-4dd7-a01b-d82be60f8e56
ms.openlocfilehash: c2c3760bcc7fcc84f914424d16a937cb3e9a0b09
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759101"
---
# <a name="compiler-error-c2293"></a>コンパイラ エラー C2293

'identifier': メンバー変数を __based の指定子にできません。

`__based` 修飾子に対する指定子は、メンバーではないポインターでなければなりません。

次の例では C2293 が生成されます。

```cpp
// C2293.cpp
// compile with: /c
class A {
   static int *i;
   void __based(i) *bp;   // C2293
   void *bp2;   // OK
};
```
