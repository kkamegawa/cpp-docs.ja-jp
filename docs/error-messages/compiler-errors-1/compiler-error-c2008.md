---
title: コンパイラエラー C2008
ms.date: 11/04/2016
f1_keywords:
- C2008
helpviewer_keywords:
- C2008
ms.assetid: e748ccbe-ffd4-4008-aca7-e53c25225209
ms.openlocfilehash: 292f5c6ab9a4e14077f848ff57ff08adefeb09a1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757333"
---
# <a name="compiler-error-c2008"></a>コンパイラエラー C2008

'character' : マクロ定義内で指定された文字の使い方が間違っています。

マクロ名の直後に文字が表示されます。 このエラーを解決するには、マクロ名の後にスペースが必要です。

次の例では、C2008 が生成されます。

```cpp
// C2008.cpp
#define TEST1"mytest1"    // C2008
```

解決方法:

```cpp
// C2008b.cpp
// compile with: /c
#define TEST2 "mytest2"
```
