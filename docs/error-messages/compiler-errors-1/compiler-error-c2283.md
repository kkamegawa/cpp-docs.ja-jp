---
title: コンパイラ エラー C2283
ms.date: 11/04/2016
f1_keywords:
- C2283
helpviewer_keywords:
- C2283
ms.assetid: 8a5b3175-b480-4598-a1f7-0b50504c5caa
ms.openlocfilehash: 7f3568aa5dfee116a225256a4452465c05f72f6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759153"
---
# <a name="compiler-error-c2283"></a>コンパイラ エラー C2283

'identifier' : 名前指定されていない struct が、純粋関数または抽象オーバーライド関数として指定されています

名前が指定されていないクラスまたは構造体のメンバー関数が、純粋指定子で宣言されていますが、これは許可されません。

次の例では C2283 が生成されます。

```cpp
// C2283.cpp
// compile with: /c
struct {
   virtual void func() = 0;   // C2283
};
struct T {
   virtual void func() = 0;   // OK
};
```
