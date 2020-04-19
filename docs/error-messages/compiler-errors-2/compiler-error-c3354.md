---
title: コンパイラ エラー C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: e5945b2112d1d03e4f18944d15028229cce4b668
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738597"
---
# <a name="compiler-error-c3354"></a>コンパイラ エラー C3354

'function': デリゲートを作成するための関数に、戻り値の型 'type' を指定することはできません。

次の型は、 `delegate`の戻り値の型として正しくありません。

- 関数へのポインター

- メンバーへのポインター

- メンバー関数へのポインター

- 関数への参照

- メンバー関数への参照

次の例では C3354 が生成されます。

```cpp
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
