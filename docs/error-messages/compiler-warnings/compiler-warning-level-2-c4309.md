---
title: コンパイラの警告 (レベル 2) C4309
ms.date: 11/04/2016
f1_keywords:
- C4309
helpviewer_keywords:
- C4309
ms.assetid: cb3f41ef-fd8a-4def-baa1-924e751fca68
ms.openlocfilehash: 78d7d8130282a67c07046004ee61e802cfd97780
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052047"
---
# <a name="compiler-warning-level-2-c4309"></a>コンパイラの警告 (レベル 2) C4309

' conversion ': 定数値の切り捨て

型変換によって、定数が割り当てられた領域を超えています。 定数には、より大きな型を使用することが必要になる場合があります。

次の例では、C4309 が生成されます。

```cpp
// C4309.cpp
// compile with: /W2
int main()
{
   char c = 128;   // C4309
}
```