---
title: メンバーへのポインター演算子:. */&gt;*
ms.date: 11/04/2016
f1_keywords:
- .*
- ->*
helpviewer_keywords:
- expressions [C++], pointer
- pointer-to-member operators [C++]
- .* operator
- expressions [C++], operators
- ->* operator
ms.assetid: 2632be3f-1c81-4523-b56c-982a92a68688
ms.openlocfilehash: 60dad0e3134662957ee21396d330af795e80918e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267664"
---
# <a name="pointer-to-member-operators--and--gt"></a>メンバーへのポインター演算子:. */&gt;*

## <a name="syntax"></a>構文

```
expression .* expression
expression ->* expression
```

## <a name="remarks"></a>Remarks

メンバーへのポインター演算子。 * および ->\*、式の左側にある指定されたオブジェクトの特定のクラス メンバーの値を返します。  右側では、クラスのメンバーを指定する必要があります。  これらの演算子を使用する方法を次の例に示します。

```cpp
// expre_Expressions_with_Pointer_Member_Operators.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;

class Testpm {
public:
   void m_func1() { cout << "m_func1\n"; }
   int m_num;
};

// Define derived types pmfn and pmd.
// These types are pointers to members m_func1() and
// m_num, respectively.
void (Testpm::*pmfn)() = &Testpm::m_func1;
int Testpm::*pmd = &Testpm::m_num;

int main() {
   Testpm ATestpm;
   Testpm *pTestpm = new Testpm;

// Access the member function
   (ATestpm.*pmfn)();
   (pTestpm->*pmfn)();   // Parentheses required since * binds
                        // less tightly than the function call.

// Access the member data
   ATestpm.*pmd = 1;
   pTestpm->*pmd = 2;

   cout  << ATestpm.*pmd << endl
         << pTestpm->*pmd << endl;
   delete pTestpm;
}
```

## <a name="output"></a>出力

```Output
m_func1
m_func1
1
2
```

前の例では、メンバー関数 `pmfn` を呼び出すのに、メンバー `m_func1` へのポインターが使用されています。 メンバーへの別のポインター `pmd` は、`m_num` メンバーにアクセスするために使用されます。

二項演算子 .* は、クラス型のオブジェクトである最初のオペランドを、メンバーへのポインター型である 2 番目のオペランドと組み合わせます。

二項演算子 -> * 最初のオペランド、クラス型のオブジェクトへのポインターである必要がありますをメンバーへのポインター型である必要があります、2 番目のオペランドを結合します。

.* 演算子を含む式では、最初のオペランドは、2 番目のオペランドで指定されるメンバーへのポインターのクラス型であってそのポインターにアクセスできるか、または、そのクラスから明確に派生しているアクセス可能な型であってそのクラスにアクセスできる必要があります。

]-> [を含む式で * 演算子、最初のオペランド型の「クラス型へのポインター」型を指定する 2 番目のオペランドかにする必要がある型の明確にそのクラスから派生します。

## <a name="example"></a>例

次のクラスとプログラムのフラグメントを考えます。

```cpp
// expre_Expressions_with_Pointer_Member_Operators2.cpp
// C2440 expected
class BaseClass {
public:
   BaseClass(); // Base class constructor.
   void Func1();
};

// Declare a pointer to member function Func1.
void (BaseClass::*pmfnFunc1)() = &BaseClass::Func1;

class Derived : public BaseClass {
public:
   Derived();  // Derived class constructor.
   void Func2();
};

// Declare a pointer to member function Func2.
void (Derived::*pmfnFunc2)() = &Derived::Func2;

int main() {
   BaseClass ABase;
   Derived ADerived;

   (ABase.*pmfnFunc1)();   // OK: defined for BaseClass.
   (ABase.*pmfnFunc2)();   // Error: cannot use base class to
                           // access pointers to members of
                           // derived classes.

   (ADerived.*pmfnFunc1)();   // OK: Derived is unambiguously
                              // derived from BaseClass.
   (ADerived.*pmfnFunc2)();   // OK: defined for Derived.
}
```

結果、。 * または ->\*メンバーへのポインター演算子は、オブジェクトまたはメンバーへのポインターの宣言で指定された型の関数。 このため、上の例では、式 `ADerived.*pmfnFunc1()` の結果は void を返す関数へのポインターです。 この結果は、第 2 オペランドが左辺値の場合は左辺値です。

> [!NOTE]
>  メンバーへのポインター演算子のいずれかの結果が関数である場合、結果は関数呼び出し演算子のオペランドとしてのみ使用できます。

## <a name="see-also"></a>関連項目

[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)