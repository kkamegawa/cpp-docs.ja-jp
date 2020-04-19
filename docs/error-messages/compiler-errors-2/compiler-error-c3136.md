---
title: コンパイラエラー C3136
ms.date: 10/03/2018
f1_keywords:
- C3136
helpviewer_keywords:
- C3136
ms.assetid: c77103cd-00f7-408e-b74b-4f8562039d31
ms.openlocfilehash: 75862f3b80d617b607a7b3e735cb3e16e9a40bb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757385"
---
# <a name="compiler-error-c3136"></a>コンパイラエラー C3136

' interface ': COM インターフェイスは他の COM インターフェイスからのみ継承できます。 ' interface ' は COM インターフェイスではありません。

インターフェイス[属性](../../windows/attributes/interface-attributes.md)を適用したインターフェイスは、COM インターフェイスではないインターフェイスから継承されます。 COM インターフェイスは、最終的には `IUnknown`から継承します。 インターフェイス属性が前に置かれているインターフェイスは、COM インターフェイスです。

次の例では、C3136 が生成されます。

```cpp
// C3136.cpp
#include "unknwn.h"

__interface A   // C3136
// try the following line instead
// _interface A : IUnknown
{
   int a();
};

[object]
__interface B : A
{
   int aa();
};
```
