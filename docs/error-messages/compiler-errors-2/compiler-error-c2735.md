---
title: コンパイラエラー C2735
ms.date: 11/04/2016
f1_keywords:
- C2735
helpviewer_keywords:
- C2735
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
ms.openlocfilehash: 81ae9353709ddb5ab0d878e6dc157511d95a94fd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755760"
---
# <a name="compiler-error-c2735"></a>コンパイラエラー C2735

' keyword ' キーワードは、仮パラメーターの型指定子では使用できません

キーワードは、このコンテキストでは無効です。

次の例では、C2735 が生成されます。

```cpp
// C2735.cpp
void f(inline int){}   // C2735
```
