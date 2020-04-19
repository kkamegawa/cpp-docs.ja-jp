---
title: コンパイラ エラー C2289
ms.date: 11/04/2016
f1_keywords:
- C2289
helpviewer_keywords:
- C2289
ms.assetid: cb41a29e-1b06-47dc-bfce-8d73bd63a0df
ms.openlocfilehash: 32afd6b99b84fba1ef9c2c701306abc67488337c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759127"
---
# <a name="compiler-error-c2289"></a>コンパイラ エラー C2289

同じ型の修飾子が 2 度以上使われています。

型の宣言または定義で、型修飾子 (`const`、 `volatile`、 `signed`、または `unsigned`) が 2 回以上使用されています。ANSI 互換のオプション ( **/Za**) を指定している場合はエラーになります。

次の例では C2286 が生成されます。

```cpp
// C2289.cpp
// compile with: /Za /c
volatile volatile int i;   // C2289
volatile int j;   // OK
```
