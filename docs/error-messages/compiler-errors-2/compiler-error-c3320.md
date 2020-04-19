---
title: コンパイラ エラー C3320
ms.date: 11/04/2016
f1_keywords:
- C3320
helpviewer_keywords:
- C3320
ms.assetid: 2ef72d9a-1f1d-4b2e-b244-9fd3f3e70cb6
ms.openlocfilehash: 622e7366dda4cd6693d9b6128855fa0966e07952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222480"
---
# <a name="compiler-error-c3320"></a>コンパイラ エラー C3320

'type': 型には、モジュール 'name' プロパティと同じ名前を指定することはできません

渡されるパラメーターとして、エクスポートされたユーザー定義型 (UDT)、構造体、クラス、列挙型、または共用体である可能性が、あるが、同じ名前を持つことはできません、[モジュール](../../windows/module-cpp.md)属性の name プロパティです。

## <a name="example"></a>例

次の例では C3320 が生成されます。

```cpp
// C3320.cpp
#include "unknwn.h"
[module(name="xx")];

[export] struct xx {   // C3320
// Try the following line instead
// [export] struct yy {
   int i;
};
```