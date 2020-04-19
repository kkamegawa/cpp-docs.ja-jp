---
title: コンパイラ エラー C2466
ms.date: 11/04/2016
f1_keywords:
- C2466
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
ms.openlocfilehash: aba4de518b9296fadc4746540e4e738c74908617
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743823"
---
# <a name="compiler-error-c2466"></a>コンパイラ エラー C2466

定数サイズ0の配列を割り当てることはできません。

配列が割り当てられているか、サイズが0で宣言されています。 配列のサイズの定数式には、0より大きい整数を指定してください。 添字がゼロの配列宣言は、クラス、構造体、または共用体のメンバーに対してのみ有効で、Microsoft の拡張機能 ([/ze](../../build/reference/za-ze-disable-language-extensions.md)) でのみ有効です。

次の例では、C2466 が生成されます。

```cpp
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```
