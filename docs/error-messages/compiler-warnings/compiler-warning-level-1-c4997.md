---
title: コンパイラの警告 (レベル 1) C4997
ms.date: 11/04/2016
f1_keywords:
- C4997
helpviewer_keywords:
- C4997
ms.assetid: d39678fd-0c1a-4104-8a45-9e3f20de0407
ms.openlocfilehash: 7f531374a0aaa06372b811d25e1ce45bee10656f
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052215"
---
# <a name="compiler-warning-level-1-c4997"></a>コンパイラの警告 (レベル 1) C4997

'class': コクラスは COM インターフェイスまたは擬似インターフェイスを実装しません

[coclass](../../windows/coclass.md) 属性でマークされているクラスがインターフェイスを実装しませんでした。

次の例では C4997 が生成されます。

```cpp
// C4997.cpp
// compile with: /WX
// to resolve this C4997, uncomment all code
#include <objbase.h>

[ object ]
__interface I {
   HRESULT func();
};

[ coclass ]
struct C /*: I*/ {
   /*
   HRESULT func() {
      return S_OK;
   }
   */
};   // C4997
```