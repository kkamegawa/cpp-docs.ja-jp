---
title: コンパイラ エラー C2157
ms.date: 11/04/2016
f1_keywords:
- C2157
helpviewer_keywords:
- C2157
ms.assetid: babbca24-16dc-4b69-be14-a675029249c1
ms.openlocfilehash: 2fa73148c9dbce843d3d1d075ca836f47b5ae074
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755890"
---
# <a name="compiler-error-c2157"></a>コンパイラ エラー C2157

'function' : プラグマ リスト内で参照される前に宣言されていなければなりません

[alloc_text](../../preprocessor/alloc-text.md) プラグマの関数の一覧で参照される前に関数名が宣言されていません。

次の例では C2157 が生成されます。

```cpp
// C2157.cpp
// compile with: /c
#pragma alloc_text( "func", func)   // C2157

// OK
extern "C" void func();
#pragma alloc_text( "func", func)
```
