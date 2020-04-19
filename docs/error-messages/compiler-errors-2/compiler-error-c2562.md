---
title: コンパイラ エラー C2562
ms.date: 11/04/2016
f1_keywords:
- C2562
helpviewer_keywords:
- C2562
ms.assetid: 2c41e511-9952-4b98-9976-6b1523613e1b
ms.openlocfilehash: 78536fdc0c2a6a6e9c4842fdea6423037496b30b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755552"
---
# <a name="compiler-error-c2562"></a>コンパイラ エラー C2562

' identifier ': ' void ' 関数は値を返します

関数は `void` として宣言されていますが、値を返します。

このエラーは、関数プロトタイプが正しくないことが原因で発生する可能性があります。

関数宣言で戻り値の型を指定すると、このエラーが解決される場合があります。

次の例では、C2562 が生成されます。

```cpp
// C2562.cpp
// compile with: /c
void testfunc() {
   int i;
   return i;   // C2562 delete the return to resolve
}
```
