---
title: コンパイラエラー C3198
ms.date: 11/04/2016
f1_keywords:
- C3198
helpviewer_keywords:
- C3198
ms.assetid: ec4ecf61-0067-4aa4-b443-a91013a1e59d
ms.openlocfilehash: b9e0ce4a84b312e3a9277898b3fc264ea3ae22bb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739156"
---
# <a name="compiler-error-c3198"></a>コンパイラエラー C3198

浮動小数点プラグマの使い方が正しくありません: fenv_access プラグマは正確なモードでのみ動作します

[fenv_access](../../preprocessor/fenv-access.md)プラグマが **/fp: 精密**以外の[/fp](../../build/reference/fp-specify-floating-point-behavior.md)設定で使用されました。

次の例では、C3198 が生成されます。

```cpp
// C3198.cpp
// compile with: /fp:fast
#pragma fenv_access(on)   // C3198
```
