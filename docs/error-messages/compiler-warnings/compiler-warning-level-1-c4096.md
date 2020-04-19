---
title: コンパイラの警告 (レベル 1) C4096
ms.date: 11/04/2016
f1_keywords:
- C4096
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
ms.openlocfilehash: 8f526b26eda4c02825d225aa007c6029cc4b03dd
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627072"
---
# <a name="compiler-warning-level-1-c4096"></a>コンパイラの警告 (レベル 1) C4096

' a ': インターフェイスは COM インターフェイスではありません。IDL には出力されません

COM インターフェイスとして指定したインターフェイス定義は COM インターフェイスとして定義されていないため、IDL ファイルには出力されません。

インターフェイスが COM インターフェイスであることを示すリスト属性については、「[インターフェイス属性](../../windows/attributes/interface-attributes.md)」を参照してください。

次の例では、C4096 が生成されます。

```cpp
// C4096.cpp
// compile with: /W1 /LD
#include "windows.h"
[module(name="xx")];

// [object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct b : a
{
};   // C4096, remove coclass or uncomment object
```