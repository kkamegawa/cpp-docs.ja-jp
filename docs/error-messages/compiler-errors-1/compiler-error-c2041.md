---
title: コンパイラエラー C2041
ms.date: 11/04/2016
f1_keywords:
- C2041
helpviewer_keywords:
- C2041
ms.assetid: c9a33bb1-f9cf-47d6-bd21-7d867a8c37d5
ms.openlocfilehash: 7e148ced19e34a57172e3d606c6efdb2f5d012d6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740456"
---
# <a name="compiler-error-c2041"></a>コンパイラエラー C2041

ベース ' number ' の数字 ' character ' は無効です

指定された文字は、基数の有効な数字ではありません (8 進数または16進数など)。

次の例では、C2041 が生成されます。

```cpp
// C2041.cpp
int i = 081;   // C2041  8 is not a base 8 digit
```

解決方法:

```cpp
// C2041b.cpp
// compile with: /c
int j = 071;
```
