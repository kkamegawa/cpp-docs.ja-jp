---
title: コンパイラ エラー C2947
ms.date: 11/04/2016
f1_keywords:
- C2947
helpviewer_keywords:
- C2947
ms.assetid: 6c056f62-ec90-4883-8a67-aeeb6ec13546
ms.openlocfilehash: 7056c13edca534701ffe82f0169897ea804f40d7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755357"
---
# <a name="compiler-error-c2947"></a>コンパイラ エラー C2947

コンストラクターを終了するために ' > ' が必要ですが、' 構文 ' が見つかりました

ジェネリックまたはテンプレートの引数リストが正しく終了していない可能性があります。

C2947 は、構文エラーによって生成されることもあります。

次の例では、C2947 が生成されます。

```cpp
// C2947.cpp
// compile with: /c
template <typename T>=   // C2947
// try the following line instead
// template <typename T>
struct A {};
```
