---
title: コンパイラ エラー C2589
ms.date: 11/04/2016
f1_keywords:
- C2589
helpviewer_keywords:
- C2589
ms.assetid: 1d7942c7-8a81-4bb4-b272-76a0019e8513
ms.openlocfilehash: 76cc35e57c1577ed23c043740f37c602600da542
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748503"
---
# <a name="compiler-error-c2589"></a>コンパイラ エラー C2589

' identifier ': ':: ' の右側に無効なトークンがあります

クラス、構造体、または共用体の名前がスコープ解決演算子 (2 つのコロン) の左側に表示される場合、右側のトークンはクラス、構造体、または共用体のメンバーである必要があります。 それ以外の場合は、任意のグローバル識別子を右側に表示できます。

スコープ解決演算子をオーバーロードすることはできません。

次の例では、C2589 が生成されます。

```cpp
// C2589.cpp
void Test(){}
class A {};
void operator :: ();   // C2589

int main() {
   ::Test();
}
```
