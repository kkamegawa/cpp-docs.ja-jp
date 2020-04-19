---
title: コンパイラ エラー C2255
ms.date: 11/04/2016
f1_keywords:
- C2255
helpviewer_keywords:
- C2255
ms.assetid: 67dc4cb0-de6b-4405-bd64-d47736367a93
ms.openlocfilehash: 758c77b5f54404321eafcc55953c44d2ac7c5412
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758828"
---
# <a name="compiler-error-c2255"></a>コンパイラ エラー C2255

'element' : クラス定義外では使用できません

たとえば、非メンバー関数が `friend`として宣言されているとします。

次の例では、C2255 が生成されます。

```cpp
// C2255.cpp
// compile with: /c
class A {
private:
   void func1();
   friend void func2();
};

friend void func1() {}   // C2255
void func2(){}
```
