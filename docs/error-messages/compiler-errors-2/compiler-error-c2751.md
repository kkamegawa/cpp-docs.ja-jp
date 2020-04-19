---
title: コンパイラエラー C2751
ms.date: 11/04/2016
f1_keywords:
- C2751
helpviewer_keywords:
- C2751
ms.assetid: 44a3abdf-8a87-4a09-b34b-532c220c310a
ms.openlocfilehash: 7b9d8ca4acbbda011cdfa7a467cbb8323dcc7cc5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759595"
---
# <a name="compiler-error-c2751"></a>コンパイラエラー C2751

' parameter ': 関数パラメーターの名前を修飾できません

修飾名を関数パラメーターとして使用することはできません。

次の例では、C2751 が生成されます。

```cpp
// C2751.cpp
namespace std {
   template<typename T>
   class list {};
}

#define list std::list
void f(int &list){}   // C2751
```
