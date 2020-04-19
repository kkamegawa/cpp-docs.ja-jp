---
title: コンパイラエラー C3131
ms.date: 11/04/2016
f1_keywords:
- C3131
helpviewer_keywords:
- C3131
ms.assetid: 38f20fac-83c9-4cd9-b7b5-74ca8f650ea6
ms.openlocfilehash: 3fe217a14b75ddedec8e1c703c36a66f747f79c5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760193"
---
# <a name="compiler-error-c3131"></a>コンパイラエラー C3131

プロジェクトには ' name ' プロパティを持つ ' module ' 属性が必要です

[Module](../../windows/module-cpp.md)属性には name パラメーターが必要です。

次の例では、C3131 が生成されます。

```cpp
// C3131.cpp
[emitidl];
[module];   // C3131
// try the following line instead
// [module (name="MyLib")];

[public]
typedef long int LongInt;
```
