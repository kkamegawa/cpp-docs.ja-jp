---
title: コンパイラ エラー C3854
ms.date: 11/04/2016
f1_keywords:
- C3854
helpviewer_keywords:
- C3854
ms.assetid: 32a9ead0-c6c7-485a-8802-c7b1fe921d3a
ms.openlocfilehash: 8c62117e9437233f614aa0e57a3848fcb8dd0c79
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754850"
---
# <a name="compiler-error-c3854"></a>コンパイラ エラー C3854

' = ' の左側の式は関数に評価されます。 関数に割り当てることはできません (関数は左辺値ではありません)

参照を再初期化することはできません。 関数への参照を逆参照すると、代入できない右辺値である関数が生成されます。 したがって、関数への参照を使用してを割り当てることはできません。

次の例では、C3854 が生成されます。

```cpp
// C3854.cpp
int afunc(int i)
{
   return i;
}

typedef int (& rFunc_t)(int);
typedef int (* pFunc_t)(int);

int main()
{
   rFunc_t rf = afunc;   // OK binding a reference to function
   pFunc_t pf = &afunc;   // OK initializing a pointer to function

   *pf = &afunc;   // C3854
   // try the following line instead
   // pf = &afunc;
   *rf = &afunc;   // C3854
}
```
