---
title: コンパイラ エラー C2248
ms.date: 11/04/2016
f1_keywords:
- C2248
helpviewer_keywords:
- C2248
ms.assetid: 7a3ba0e8-d3b9-4bb9-95db-81ef17e31d23
ms.openlocfilehash: d9b9a6c04e7e9a5d88df516125280b6b23894a01
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302555"
---
# <a name="compiler-error-c2248"></a>コンパイラ エラー C2248

'*メンバー*': アクセスできない'*access_level*'クラスで宣言されたメンバー'*クラス*'

派生クラスのメンバーにアクセスできない`private`基底クラスのメンバー。 アクセスできない`private`または`protected`クラスのインスタンスのメンバー。

## <a name="example"></a>例

クラスのプロテクト メンバーは、クラスの外部からアクセスまたは次の例は、C2248 とプライベートを生成します。 この問題を解決するには、クラスの外部で直接これらのメンバーはアクセスしません。 パブリック メンバー データおよびメンバー関数を使用して、クラスとやり取りします。

```cpp
// C2248_access.cpp
// compile with: cl /EHsc /W4 C2248_access.cpp
#include <stdio.h>

class X {
public:
    int  m_publicMember;
    void setPrivateMember( int i ) {
        m_privateMember = i;
        printf_s("\n%d", m_privateMember);
    }
protected:
    int  m_protectedMember;

private:
    int  m_privateMember;
} x;

int main() {
    x.m_publicMember = 4;
    printf_s("\n%d", x.m_publicMember);
    x.m_protectedMember = 2; // C2248 m_protectedMember is protected
    x.m_privateMember = 3;   // C2248  m_privMemb is private
    x.setPrivateMember(0);   // OK uses public access function
}
```

C2248 準拠の問題は、テンプレートのフレンドおよび特殊化です。 この問題を解決するには、テンプレート関数フレンドを宣言、空のテンプレート パラメーター リスト <> または特定のテンプレート パラメーターを使用しています。

```cpp
// C2248_template.cpp
// compile with: cl /EHsc /W4 C2248_template.cpp
template<class T>
void f(T t) {
    t.i;   // C2248
}

struct S {
private:
    int i;

public:
    S() {}
    friend void f(S);   // refer to the non-template function void f(S)
    // To fix, comment out the previous line and
    // uncomment the following line.
    // friend void f<S>(S);
};

int main() {
    S s;
    f<S>(s);
}
```

C2248 準拠の問題は、クラスがクラスのスコープ内のフレンド宣言に表示されない場合、クラスのフレンドを宣言しようとした場合です。 この問題を解決するには、外側のクラスをフレンドシップを付与します。

```cpp
// C2248_enclose.cpp
// compile with: cl /W4 /c C2248_enclose.cpp
class T {
    class S {
        class E {};
    };
    friend class S::E;   // C2248
};

class A {
    class S {
        class E {};
        friend class A;  // grant friendship to enclosing class
    };
    friend class S::E;   // OK
};
```