---
title: コンパイラ エラー C2860
ms.date: 11/04/2016
f1_keywords:
- C2860
helpviewer_keywords:
- C2860
ms.assetid: ccc83553-90ed-4e94-b5e9-38b58ae38e31
ms.openlocfilehash: 6a6bb4bc12e791e36a31ffc4cf417e21cb71dbdd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760968"
---
# <a name="compiler-error-c2860"></a>コンパイラ エラー C2860

' (void) ' を除き、' void ' を引数型にすることはできません

型 `void` を他の引数と共に引数の型として使用することはできません。

次の例では、C2860 が生成されます。

```cpp
// C2860.cpp
// compile with: /c
void profunc1(void, int i);   // C2860
void func10(void);   // OK
```
