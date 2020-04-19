---
title: コンパイラエラー C2014
ms.date: 11/04/2016
f1_keywords:
- C2014
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
ms.openlocfilehash: 6c7e941970415c933b38f35b6c09247a3c0fd411
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757398"
---
# <a name="compiler-error-c2014"></a>コンパイラエラー C2014

プリプロセッサコマンドは最初のシャープ空白 space として起動する必要があります

プリプロセッサディレクティブの `#` 署名は、空白ではない行の最初の文字である必要があります。

次の例では、C2014 が生成されます。

```cpp
// C2014.cpp
int k; #include <stdio.h>   // C2014
```

解決方法:

```cpp
// C2014b.cpp
// compile with: /c
int k;
#include <stdio.h>
```
