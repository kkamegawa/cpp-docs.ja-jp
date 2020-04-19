---
title: コンパイラ エラー C2292
ms.date: 11/04/2016
f1_keywords:
- C2292
helpviewer_keywords:
- C2292
ms.assetid: 256b392f-2b8f-4162-b578-e7633984e162
ms.openlocfilehash: 82d381fddc4cafd364bc0e45e70e5fb5c1cb3d84
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759114"
---
# <a name="compiler-error-c2292"></a>コンパイラ エラー C2292

' identifier ': ベストケース継承表現: ' representation1 ' が宣言されていますが、' representation2 ' が必要です

[/Vmb](../../build/reference/vmb-vmg-representation-method.md)を使用して次のコードをコンパイルすると、C2292 が発生します。

```cpp
// C2292.cpp
// compile with: /vmb
class __single_inheritance X;

struct A { };
struct B { };
struct X : A, B { };  // C2292, X uses multiple inheritance
```
