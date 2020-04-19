---
title: コンパイラの警告 (レベル 1) C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 27023e6886638be63db1e1fb654c0caa70769a56
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052529"
---
# <a name="compiler-warning-level-1-c4659"></a>コンパイラの警告 (レベル 1) C4659

\#プラグマ ' pragma ': 予約セグメント ' segment ' の使用には定義されていない動作があります。 #pragma コメントを使用してください (リンカー,...)

.Drectve オプションは、リンカーにオプションを渡すために使用されました。 代わりに、リンカーオプションを渡すためにプラグマ[コメント](../../preprocessor/comment-c-cpp.md)を使用してください。

```cpp
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```