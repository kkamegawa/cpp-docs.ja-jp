---
title: コンパイラ エラー C2208
ms.date: 11/04/2016
f1_keywords:
- C2208
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
ms.openlocfilehash: 208e15e98a05089c0e9b1c98400f5267e4f3a48f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758932"
---
# <a name="compiler-error-c2208"></a>コンパイラ エラー C2208

' type ': この型を使用して定義されたメンバーはありません

型名に解決される識別子が集計宣言内にありますが、コンパイラはメンバーを宣言できません。

次の例では、C2208 が生成されます。

```cpp
// C2208.cpp
class C {
   C;   // C2208
   C(){}   // OK
};
```
