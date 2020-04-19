---
title: コンパイラ エラー C3913
ms.date: 11/04/2016
f1_keywords:
- C3913
helpviewer_keywords:
- C3913
ms.assetid: a678bfce-9524-470d-9f23-7d08ecb972c8
ms.openlocfilehash: 0dfe8274c2b9ee5d2861239c8bb1464d9642ebc9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74741262"
---
# <a name="compiler-error-c3913"></a>コンパイラ エラー C3913

既定のプロパティにはインデックスを付ける必要があります

既定のプロパティが正しく定義されていません。

詳細については、「 [property](../../extensions/property-cpp-component-extensions.md)」を参照してください。

次の例では、C3913 が生成されます。

```cpp
// C3913.cpp
// compile with: /clr /c
ref struct X {
   property int default {   // C3913
   // try the following line instead
   // property int default[int] {
      int get(int) { return 0; }
      void set(int, int) {}
   }
};
```
