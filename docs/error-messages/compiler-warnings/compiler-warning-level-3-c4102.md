---
title: コンパイラの警告 (レベル 3) C4102
ms.date: 11/04/2016
f1_keywords:
- C4102
helpviewer_keywords:
- C4102
ms.assetid: 349f308a-daf3-48c6-bd53-6c38b73f8880
ms.openlocfilehash: 1a0c5389a5f8f6f2dc885fccecf34313308bf769
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051888"
---
# <a name="compiler-warning-level-3-c4102"></a>コンパイラの警告 (レベル 3) C4102

'label': 参照されていないラベル

ラベルが定義されていますが、一度も参照されていません。 コンパイラはこのラベルを無視します。

次の例では C4102 警告が生成されます。

```cpp
// C4102.cpp
// compile with: /W3
int main() {
   int a;

   test:   // C4102, remove the unreferenced label to resolve

   a = 1;
}
```