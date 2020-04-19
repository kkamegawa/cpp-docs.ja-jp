---
title: コンパイラの警告 (レベル 4) C4343
ms.date: 11/04/2016
f1_keywords:
- C4343
helpviewer_keywords:
- C4343
ms.assetid: a721b710-e04f-4d15-b678-e4a2c8fd0181
ms.openlocfilehash: 59803440966b8396ba231dc5a7265620c37f9cc1
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991196"
---
# <a name="compiler-warning-level-4-c4343"></a>コンパイラの警告 (レベル 4) C4343

\#pragma optimize ("g", off) は/Og オプションをオーバーライドします

この警告 (Itanium プロセッサ ファミリ (IPF) コンパイラでのみ有効) は、pragma [optimize](../../preprocessor/optimize.md) が [/Og](../../build/reference/og-global-optimizations.md) コンパイラ オプションをオーバーライドしたことを報告します。

次の例では C4343 が生成されます。

```cpp
// C4343.cpp
// compile with: /Og /W4 /LD
// processor: IPF
#pragma optimize ("g", off)   // C4343
```
