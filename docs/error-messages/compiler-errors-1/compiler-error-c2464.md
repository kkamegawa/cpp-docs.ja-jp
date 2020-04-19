---
title: コンパイラ エラー C2464
ms.date: 11/04/2016
f1_keywords:
- C2464
helpviewer_keywords:
- C2464
ms.assetid: ace953d6-b414-49ee-bfef-90578a8da00c
ms.openlocfilehash: e4952f4702d871ecf1c818b1fc7394e54a1a295f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743888"
---
# <a name="compiler-error-c2464"></a>コンパイラ エラー C2464

' identifier ': 参照を割り当てるために ' new ' を使用することはできません

`new` 演算子で参照識別子が割り当てられました。 参照はメモリオブジェクトではないため、`new` はそれらへのポインターを返すことができません。 参照を宣言するには、標準変数宣言の構文を使用します。

次の例では、C2464 が生成されます。

```cpp
// C2464.cpp
int main() {
   new ( int& ir );   // C2464
}
```
