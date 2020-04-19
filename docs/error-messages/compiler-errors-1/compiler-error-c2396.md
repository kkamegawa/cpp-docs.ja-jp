---
title: コンパイラ エラー C2396
ms.date: 11/04/2016
f1_keywords:
- C2396
helpviewer_keywords:
- C2396
ms.assetid: 1b515ef6-7af4-400f-b4ed-564313ea15f6
ms.openlocfilehash: 5020732ce5186ee1c6e9d2ea13f452fe9988bdfa
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744837"
---
# <a name="compiler-error-c2396"></a>コンパイラ エラー C2396

' your_type:: 演算子 ' type ' ': CLR または WinRT ユーザー定義の変換関数が無効です。 次のいずれかに変換または変換する必要があります: t ^ '、' t ^% '、' t ^ & '、T = ' your_type '

Windows ランタイム型またはマネージド型の変換関数に、変換関数が含まれる型と同じ型を持つ 1 つ以上のパラメーターがありません。

次の例では、C2396 を生成し、その修正方法を示しています。

```cpp
// C2396.cpp
// compile with: /clr /c

ref struct Y {
   static operator int(char c);   // C2396

   // OK
   static operator int(Y^ hY);
   // or
   static operator Y^(char c);
};
```
