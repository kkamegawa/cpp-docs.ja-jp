---
title: コンパイラエラー C2646
ms.date: 11/04/2016
f1_keywords:
- C2646
helpviewer_keywords:
- C2646
ms.assetid: 92ff1f02-5eaf-40a5-8b7a-a682f149e967
ms.openlocfilehash: a5c4dbc967c304fc6b13eb00e2c7093380ec8be9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758217"
---
# <a name="compiler-error-c2646"></a>コンパイラエラー C2646

グローバルまたは名前空間スコープの匿名構造体または匿名共用体は静的に宣言する必要があります

匿名構造体または匿名共用体にはグローバル スコープまたは名前空間のスコープがありますが、`static` 宣言されていません。

次の例では、C2646 を生成し、その修正方法を示しています。

```cpp
// C2646.cpp
// compile with: /c
union { int i; };   // C2646 not static

// OK
static union { int j; };
union U { int i; };
```
