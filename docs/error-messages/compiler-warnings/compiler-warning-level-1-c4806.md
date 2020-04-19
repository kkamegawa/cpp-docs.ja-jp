---
title: コンパイラの警告 (レベル 1) C4806
ms.date: 11/04/2016
f1_keywords:
- C4806
helpviewer_keywords:
- C4806
ms.assetid: 79eb74cd-b925-4b5b-84e1-8ae6f33e38b3
ms.openlocfilehash: dae6ed7d7a38daf0ce525ae62409823212db711b
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052363"
---
# <a name="compiler-warning-level-1-c4806"></a>コンパイラの警告 (レベル 1) C4806

'operation': 安全でない演算: 'type' 型から 'type' 型への上位変換を行うと与えられた定数に等しくなりません

このメッセージは、 `b == 3`に `b` 型がある `bool`などのコードに対して警告を行います。 上位変換の規則に従って、 `bool` が `int`に上位変換されます。 これは有効ですが、 **true**にすることはできません。 次の例では C4806 が生成されます。

```cpp
// C4806.cpp
// compile with: /W1
int main()
{
   bool b = true;
   // try..
   // int b = true;

   if (b == 3)   // C4806
   {
      b = false;
   }
}
```