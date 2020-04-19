---
title: コンパイラ エラー C2548
ms.date: 11/04/2016
f1_keywords:
- C2548
helpviewer_keywords:
- C2548
ms.assetid: 01e9c835-9bf3-4020-9295-5ee448c519f3
ms.openlocfilehash: f89208314c1d2e8ddb5100da72aa600a411b4608
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756800"
---
# <a name="compiler-error-c2548"></a>コンパイラ エラー C2548

' class:: member ': パラメーターパラメーターの既定のパラメーターがありません

既定のパラメーターリストにパラメーターがありません。 パラメーターリスト内の任意の場所に既定のパラメーターを指定する場合は、後続のすべてのパラメーターに対して既定のパラメーターを定義する必要があります。

## <a name="example"></a>使用例

次の例では、C2548 が生成されます。

```cpp
// C2548.cpp
// compile with: /c
void func( int = 1, int, int = 3);  // C2548

// OK
void func2( int, int, int = 3);
void func3( int, int = 2, int = 3);
```
