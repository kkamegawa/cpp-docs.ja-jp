---
title: コンパイラ エラー C3890
ms.date: 11/04/2016
f1_keywords:
- C3890
helpviewer_keywords:
- C3890
ms.assetid: 2f22c2fd-c14e-45e1-b936-b739ffc0b135
ms.openlocfilehash: 8d93afa2ac8e365eff2f9256235b391f561cb977
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736543"
---
# <a name="compiler-error-c3890"></a>コンパイラ エラー C3890

' var ': リテラルデータメンバーのアドレスを取得することはできません。

リテラルデータメンバーは、ガベージコレクションヒープに存在します。  ガベージコレクションヒープ上のオブジェクトは移動できるので、アドレスを使用しても役に立ちません。

次の例では、C3890 が生成されます。

```cpp
// C3890.cpp
// compile with: /clr
ref struct Y1 {
   literal int staticConst = 9;
};

int main() {
   int p = &Y1::staticConst;   // C3890
   int p2 = Y1::staticConst;   // OK
}
```
