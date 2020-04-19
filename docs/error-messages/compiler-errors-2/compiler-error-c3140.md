---
title: コンパイラエラー C3140
ms.date: 11/04/2016
f1_keywords:
- C3140
helpviewer_keywords:
- C3140
ms.assetid: 122f8943-fac3-4db8-a3a8-2c5d19233de6
ms.openlocfilehash: dc1e1828583b3ac8342c12a62e6ba4c1694b5824
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760570"
---
# <a name="compiler-error-c3140"></a>コンパイラエラー C3140

同じコンパイル単位に複数の ' module ' 属性を含めることはできません

[モジュール](../../windows/module-cpp.md)属性は、プロジェクトごとに1回だけ定義できます。

次の例では、C3140 が生成されます。

```cpp
// C3140.cpp
// compile with: /c
[emitidl];
[module(name = "MyLibrary")];
[module(name = "MyLibrary2")];   // C3140
```
