---
title: コンパイラ エラー C3849
ms.date: 11/04/2016
f1_keywords:
- C3849
helpviewer_keywords:
- C3849
ms.assetid: 5347140e-1a81-4841-98c0-b63d98264b64
ms.openlocfilehash: 8492f108b57fbc63bd171276b1aa601f96a28b24
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754889"
---
# <a name="compiler-error-c3849"></a>コンパイラ エラー C3849

型 ' type ' の式で関数形式の呼び出しを行うと、使用可能なすべての演算子オーバーロードの const または volatile 修飾子が失われます

Const volatile 型が指定された変数は、同じまたはそれ以上の const volatile 修飾子で定義されたメンバー関数のみを呼び出すことができます。

このエラーを修正するには、適切なメンバー関数を指定します。 変換によって修飾が失われる場合、const または volatile で修飾されたオブジェクトに対して変換を実行することはできません。 修飾子を取得することはできますが、変換で修飾子を失うことはできません。

次のサンプルでは、C3849 が生成されます。

```cpp
// C3849.cpp
void glbFunc3(int i, char c)
{
   i;
}
typedef void (* pFunc3)(int, char);

void glbFunc2(int i)
{
   i;
}

typedef void (* pFunc2)(int);

void glbFunc1()
{
}
typedef void (* pFunc1)();

struct S4
{
   operator ()(int i)
   {
      i;
   }

   operator pFunc1() const
   {
      return &glbFunc1;
   }

   operator pFunc2() volatile
   {
      return &glbFunc2;
   }

   operator pFunc3()
   {
      return &glbFunc3;
   }

   // operator pFunc1() const volatile
   // {
   //    return &glbFunc1;
   // }
};

int main()
{
   // Cannot call any of the 4 overloads of "operator ()(.....)" and
   // "operator pFunc()" because none is declared as "const volatile"
   const volatile S4 s4;  // can only call cv member functions of S4
   s4();   // C3849 to resolve, uncomment member function
}
```
