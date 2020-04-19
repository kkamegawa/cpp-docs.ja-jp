---
title: コンパイラ エラー C2395
ms.date: 11/04/2016
f1_keywords:
- C2395
helpviewer_keywords:
- C2395
ms.assetid: 2d9e3b28-8c2c-4f41-a57f-61ef88fc2af0
ms.openlocfilehash: 2ac59856770b04dd3c4ea14360e0a83dd99f2150
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744941"
---
# <a name="compiler-error-c2395"></a>コンパイラ エラー C2395

'your_type::operator'op'' : CLR または WinRT 演算子が無効です。 少なくとも1つのパラメーターは次の型である必要があります: ' t '、' t% '、' t & '、' t ^ '、' t ^% '、' t ^ & '、where T = ' your_type '

Windows ランタイムまたはマネージド型の演算子に、演算子の戻り値の型と同じ型を持つ 1 つ以上のパラメーターがありません。

次の例では、C2395 を生成し、その修正方法を示しています。

```cpp
// C2395.cpp
// compile with: /clr /c
value struct V {
   static V operator *(int i, char c);   // C2395

   // OK
   static V operator *(V v, char c);
   // or
   static V operator *(int i, V& rv);
};
```
