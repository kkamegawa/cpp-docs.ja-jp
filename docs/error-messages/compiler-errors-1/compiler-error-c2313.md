---
title: コンパイラ エラー C2313
ms.date: 11/04/2016
f1_keywords:
- C2313
helpviewer_keywords:
- C2313
ms.assetid: f70eb19b-c0a3-4fb2-ade1-3890a589928d
ms.openlocfilehash: 0eb085d9959359b31b022c2268f0ea8c7b811b20
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748126"
---
# <a name="compiler-error-c2313"></a>コンパイラ エラー C2313

'type1': 行番号の参照 ('type2') でキャッチされます

例外の型には 2 つのハンドラーがあります。 2 番目の catch の型は、最初の型への参照です。

次の例では C2313 が生成されます。

```cpp
// C2313.cpp
// compile with: /EHsc
#include <eh.h>
class C {};
int main() {
    try {
        throw "ooops!";
    }
    catch( C& ) {}
    catch( C ) {}   // C2313
}
```
