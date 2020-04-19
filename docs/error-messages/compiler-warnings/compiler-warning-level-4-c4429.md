---
title: コンパイラの警告 (レベル 4) C4429
ms.date: 11/04/2016
f1_keywords:
- C4429
helpviewer_keywords:
- C4429
ms.assetid: a3e4cf1f-a869-4e47-834a-850c21eb5297
ms.openlocfilehash: 6702db4af5c31d21610e02b1a4ec75af27ad10f2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990827"
---
# <a name="compiler-warning-level-4-c4429"></a>コンパイラの警告 (レベル 4) C4429

不完全または不適切な形式のユニバーサル文字名です。

コンパイラは、正しくない形式のユニバーサル文字名である可能性がある文字シーケンスを検出しました。 ユニバーサル文字名の後に4桁の16進数が続き、`\U` の後に8桁の16進数が続く `\u` ます。

次の例では、C4429 が生成されます。

```cpp
// C4429.cpp
// compile with: /W4 /WX
int \ug0e4 = 0;   // C4429
// Try the following line instead:
// int \u00e4 = 0;   // OK, a well-formed universal character name.
```
