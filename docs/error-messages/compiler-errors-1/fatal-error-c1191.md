---
title: 致命的なエラー C1191
ms.date: 11/04/2016
f1_keywords:
- C1191
helpviewer_keywords:
- C1191
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
ms.openlocfilehash: 7c6756dec29138af534278742d99c2f77109b1cc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747294"
---
# <a name="fatal-error-c1191"></a>致命的なエラー C1191

' dll ' はグローバルスコープでのみインポートできます

/Clr プログラミングを使用するプログラムに mscorlib.dll をインポートする手順は、名前空間または関数には記述できませんが、グローバルスコープでは指定する必要があります。

次の例では、C1191 が生成されます。

```cpp
// C1191.cpp
// compile with: /clr
namespace sample {
   #using <mscorlib.dll>   // C1191 not at global scope
}
```

解決方法:

```cpp
// C1191b.cpp
// compile with: /clr /c
#using <mscorlib.dll>
namespace sample {}
```
