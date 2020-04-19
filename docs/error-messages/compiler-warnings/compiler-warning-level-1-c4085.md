---
title: コンパイラの警告 (レベル 1) C4085
ms.date: 11/04/2016
f1_keywords:
- C4085
helpviewer_keywords:
- C4085
ms.assetid: 2bc6eb25-058f-4597-b351-fd69587b5170
ms.openlocfilehash: bf006a2e566fe79b44f71192e95278392fe4f59e
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626863"
---
# <a name="compiler-warning-level-1-c4085"></a>コンパイラの警告 (レベル 1) C4085

プラグマに、'on' か 'off' のパラメーターが必要です。

プラグマには、 **on** または **off** パラメーターが必要です。 このプラグマは無視されます。

次の例では C4085 が生成されます。

```cpp
// C4085.cpp
// compile with: /W1 /LD
#pragma optimize( "t", maybe )  // C4085
```