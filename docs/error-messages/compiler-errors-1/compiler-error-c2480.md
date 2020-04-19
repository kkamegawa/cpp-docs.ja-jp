---
title: コンパイラ エラー C2480
ms.date: 11/04/2016
f1_keywords:
- C2480
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
ms.openlocfilehash: 3e495a8019405a558511637467133877dae1183e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743524"
---
# <a name="compiler-error-c2480"></a>コンパイラ エラー C2480

' identifier ': ' thread ' は静的なデータ項目に対してのみ有効です

`thread` 属性を、自動変数、非静的データメンバー、関数パラメーター、または関数の宣言または定義で使用することはできません。

グローバル変数、静的データメンバー、およびローカルの静的変数に対してのみ、`thread` 属性を使用します。

次の例では、C2480 が生成されます。

```cpp
// C2480.cpp
// compile with: /c
__declspec( thread ) void func();   // C2480
__declspec( thread ) static int i;   // OK
```
