---
title: コンパイラ エラー C2863
ms.date: 11/04/2016
f1_keywords:
- C2863
helpviewer_keywords:
- C2863
ms.assetid: 32561d67-a795-486b-b3b6-4b90a1acb176
ms.openlocfilehash: 127db2f3e7d334b684502587f9b330959063234e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755071"
---
# <a name="compiler-error-c2863"></a>コンパイラ エラー C2863

' interface ': インターフェイスはフレンドを持つことができません

インターフェイスでのフレンドの宣言は許可されていません。

次の例では、C2863 が生成されます。

```cpp
// C2863.cpp
// compile with: /c
#include <unknwn.h>

class CMyClass {
   void *f();
};

__interface IMyInterface {
   void g();

   friend int h();   // 2863
   friend interface IMyInterface1;  // C2863
   friend void *CMyClass::f();  // C2863
};
```
