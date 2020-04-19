---
title: コンパイラ エラー C2195
ms.date: 11/04/2016
f1_keywords:
- C2195
helpviewer_keywords:
- C2195
ms.assetid: 9f9f035c-9c51-4173-a8ea-c6f907fc5c63
ms.openlocfilehash: 748516dbcdf5e135964e720d6215f31091bfed9e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758529"
---
# <a name="compiler-error-c2195"></a>コンパイラ エラー C2195

' identifier ': データセグメントです

`code_seg` プラグマは、`data_seg` プラグマと共に使用されるセグメント名を使用します。

次の例では、C2195 が生成されます。

```cpp
// C2195.cpp
#pragma data_seg("MYDATA")
#pragma code_seg("MYDATA")   // C2195
#pragma code_seg("MYDATA2")   // OK
```
