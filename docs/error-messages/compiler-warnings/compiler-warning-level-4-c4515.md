---
title: コンパイラの警告 (レベル 4) C4515
ms.date: 11/04/2016
f1_keywords:
- C4515
helpviewer_keywords:
- C4515
ms.assetid: 167b5177-3f89-418b-b6c8-7de634f6b28f
ms.openlocfilehash: 442852ba971fb1b9a687d5ccf2b2857aa9deab50
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990728"
---
# <a name="compiler-warning-level-4-c4515"></a>コンパイラの警告 (レベル 4) C4515

' namespace ': 名前空間はそれ自体を使用します

名前空間は再帰的に使用されます。

次の例では、C4515 が生成されます。

```cpp
// C4515.cpp
// compile with: /W4
namespace A
{
   using namespace A; // C4515
}

int main()
{
}
```
