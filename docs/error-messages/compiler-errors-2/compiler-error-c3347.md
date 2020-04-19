---
title: コンパイラ エラー C3347
ms.date: 11/04/2016
f1_keywords:
- C3347
helpviewer_keywords:
- C3347
ms.assetid: e939ad29-0b78-4681-9618-9bdae5675cee
ms.openlocfilehash: 9f62d66148aa75040f7bab5ea69931d2ef9c474a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755617"
---
# <a name="compiler-error-c3347"></a>コンパイラ エラー C3347

'arg': 必要な引数が属性 idl_module 内で指定されていません

[idl_module](../../windows/idl-module.md) 属性に必須の引数が渡されていません。

次の例では C3347 が生成されます。

```cpp
// C3347.cpp
// compile with: /c
[module(name="xx")];

[idl_module(dllname="x")];    // C3347
// try the following line instead
// [idl_module(name="test", dllname="x")];
```
