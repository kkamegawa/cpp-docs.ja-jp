---
title: コンパイラエラー C2021
ms.date: 11/04/2016
f1_keywords:
- C2021
helpviewer_keywords:
- C2021
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
ms.openlocfilehash: 24463abcf123fda285356c86e3394d7274f2f6c8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751041"
---
# <a name="compiler-error-c2021"></a>コンパイラエラー C2021

'character' でなく指数の値が必要です

浮動小数点定数の指数として使用されている文字が、有効な数値ではありません。 範囲内の指数を使用するようにしてください。

## <a name="example"></a>使用例

次の例では、C2021 が生成されます。

```cpp
// C2021.cpp
float test1=1.175494351E;   // C2021
```

## <a name="example"></a>使用例

解決方法:

```cpp
// C2021b.cpp
// compile with: /c
float test2=1.175494351E8;
```
