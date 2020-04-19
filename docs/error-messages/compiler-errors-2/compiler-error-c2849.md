---
title: コンパイラ エラー C2849
ms.date: 11/04/2016
f1_keywords:
- C2849
helpviewer_keywords:
- C2849
ms.assetid: e28f6b3e-e0e7-4f92-b006-ebaa81d368e6
ms.openlocfilehash: 8a67c81fd58312921ef01209d7bc2f96eecaed4b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738883"
---
# <a name="compiler-error-c2849"></a>コンパイラ エラー C2849

' デストラクター ': インターフェイスにデストラクターを含めることはできません

ビジュアルC++ [インターフェイス](../../cpp/interface.md)にデストラクターを含めることはできません。

次の例では、C2849 が生成されます。

```cpp
// C2849.cpp
// compile with: /c
__interface C {
   ~C();   // C2849 destructor not allowed in an interface
};
```
