---
title: コンパイラ エラー C2534
ms.date: 11/04/2016
f1_keywords:
- C2534
helpviewer_keywords:
- C2534
ms.assetid: 481f9f54-5b51-4aa0-8eea-218f10807705
ms.openlocfilehash: 4b1e481c733f52b0be419b7fd786b26a90362f9c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737090"
---
# <a name="compiler-error-c2534"></a>コンパイラ エラー C2534

' identifier ': コンストラクターは値を返せません。

コンストラクターが値を返さないか、戻り値の型を持つことができません (戻り値の型が `void` であっても)。

このエラーは、コンストラクターの定義から `return` ステートメントを削除することによって解決できる場合があります。

次の例では、C2534 が生成されます。

```cpp
// C2534.cpp
class A {
public:
   int i;
   A() { return i; }   // C2534
};
```
