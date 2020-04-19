---
title: コンパイラ エラー C3283
ms.date: 11/04/2016
f1_keywords:
- C3283
helpviewer_keywords:
- C3283
ms.assetid: c51d912c-cde3-4928-904e-26734c8954ce
ms.openlocfilehash: a1aa7a0744c2eca2101931ba9ef0ad6ee212d5a7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757567"
---
# <a name="compiler-error-c3283"></a>コンパイラ エラー C3283

'type': インターフェイスにインスタンス コンストラクターを含めることはできません

CLR [インターフェイス](../../extensions/interface-class-cpp-component-extensions.md) にインスタンス コンストラクターを含めることはできません。  静的コンストラクターが許可されます。

次の例では C3283 が生成されます。

```cpp
// C3283.cpp
// compile with: /clr
interface class I {
   I();   // C3283
};
```

解決方法:

```cpp
// C3283b.cpp
// compile with: /clr /c
interface class I {
   static I(){}
};
```
