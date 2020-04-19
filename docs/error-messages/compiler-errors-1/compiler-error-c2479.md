---
title: コンパイラ エラー C2479
ms.date: 11/04/2016
f1_keywords:
- C2479
helpviewer_keywords:
- C2479
ms.assetid: c74c7869-e65b-4ca1-b6fa-eb39fed4458a
ms.openlocfilehash: c7bddd21faab8c55f349c6e03fbcd3db42c3fa7d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743563"
---
# <a name="compiler-error-c2479"></a>コンパイラ エラー C2479

' identifier ': ' allocate () ' は静的なデータ項目に対してのみ有効です

`__declspec( allocate())` 構文は、静的なデータに対してのみ使用できます。

次の例では、C2479 が生成されます。

```cpp
// C2479.cpp
// compile with: /c
#pragma section("mycode", read)
static __declspec(allocate("mycode")) void DoNothing() {}   // C2479
__declspec(allocate("mycode"))  int i = 0;   // OK
```
