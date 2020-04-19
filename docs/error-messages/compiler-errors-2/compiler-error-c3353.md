---
title: コンパイラ エラー C3353
ms.date: 11/04/2016
f1_keywords:
- C3353
helpviewer_keywords:
- C3353
ms.assetid: 5699c04b-d504-46ce-bf71-c200318fed71
ms.openlocfilehash: 332e0b253aed53f2adadf448b6a9c0681abc825e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747452"
---
# <a name="compiler-error-c3353"></a>コンパイラ エラー C3353

'delegate': デリゲートはマネージド型または WinRT 型のグローバル関数またはメンバー関数からのみ作成できます

[Delegate](../../extensions/delegate-cpp-component-extensions.md)キーワードで宣言されたデリゲートは、グローバルスコープでのみ宣言できます。

次の例では C3353 が生成されます。

```cpp
// C3353.cpp
// compile with: /clr
delegate int f;   // C3353
```
