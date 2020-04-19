---
title: コンパイラ エラー C2199
ms.date: 11/04/2016
f1_keywords:
- C2199
helpviewer_keywords:
- C2199
ms.assetid: 6a92a1b7-7906-49e6-a31f-e8bffbc7706a
ms.openlocfilehash: 8bd6d587d28b8e7c190f7d3d58448fda501796cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758984"
---
# <a name="compiler-error-c2199"></a>コンパイラ エラー C2199

構文エラー: グローバルスコープで ' identifier (' が見つかりました (宣言が意図されていたかどうか)

指定されたコンテキストにより、構文エラーが発生しました。 宣言の構文が正しくありません。

次の例では、C2199 が生成されます。

```cpp
// C2199.cpp
// compile with: /c
int j = int(1) int(1);   // C2199
int j = 1;   // OK
```
