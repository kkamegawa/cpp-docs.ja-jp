---
title: コンパイラエラー C2027
ms.date: 11/04/2016
f1_keywords:
- C2027
helpviewer_keywords:
- C2027
ms.assetid: a39150c0-ec04-45ec-934c-a838bfe76627
ms.openlocfilehash: 62cf208d9d0025afba06d32a15b9a1e50777c473
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751002"
---
# <a name="compiler-error-c2027"></a>コンパイラエラー C2027

未定義の型 ' type ' が使用されています。

型は、定義されるまで使用できません。 エラーを解決するには、型が参照前に完全に定義されていることを確認してください。

## <a name="example"></a>使用例

次の例では、C2027 が生成されます。

```cpp
// C2027.cpp
class C;
class D {
public:
   void func() {
   }
};

int main() {
   C *pC;
   pC->func();   // C2027

   D *pD;
   pD->func();
}
```

## <a name="example"></a>使用例

宣言されているが未定義の型へのポインターを宣言することができます。 ただしC++ 、未定義の型への参照は許可されません。

次の例では、C2027 が生成されます。

```cpp
// C2027_b.cpp
class A;
A& CreateA();

class B;
B* CreateB();

int main() {
   CreateA();   // C2027
   CreateB();   // OK
}
```
