---
title: コンパイラ エラー C2280
ms.date: 04/25/2017
f1_keywords:
- C2280
helpviewer_keywords:
- C2280
ms.assetid: e6c5b1fb-2b9b-4554-8ff9-775eeb37161b
ms.openlocfilehash: e1ec032878fefdc1992605df5ee1aa13c673d4cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388905"
---
# <a name="compiler-error-c2280"></a>コンパイラ エラー C2280

'*宣言*': 削除された関数を参照しようとしています。

コンパイラを参照しようとしました、`deleted`関数。 として明示的にマークされている、メンバー関数への呼び出しによってこのエラーは発生する`= deleted`ソース コードにします。 このエラーは、構造体またはクラスが自動的に宣言され、マークの暗黙的な特殊なメンバー関数の呼び出しによっても発生する`deleted`コンパイラによって。 コンパイラが自動的に生成するときの詳細については`default`または`deleted`特殊なメンバー関数を参照してください[特殊なメンバー関数](../../cpp/special-member-functions.md)します。

## <a name="example-explicitly-deleted-functions"></a>例:明示的に削除指定関数

呼び出しを明示的に`deleted`関数にこのエラーが発生します。 明示的に`deleted`メンバー関数を意味するクラスまたは構造体は意図的にこの問題を解決するため、使用を防ぐために設計されています、これを回避するためにコードを変更する必要があります。

```cpp
// C2280_explicit.cpp
// compile with: cl /c /W4 C2280_explicit.cpp
struct A {
    A();
    A(int) = delete;
};

struct B {
    A a1;
    A a2 = A(3); // C2280, calls deleted A::A(int)
    // To fix, remove the call to A(int)
};

void f() {
    B b;    // calls implicit B::B(void)
}
```

## <a name="example-uninitialized-data-members"></a>例:初期化されていないデータ メンバー

初期化されていない参照型のデータ メンバーまたは`const`データ メンバーが暗黙的に宣言するコンパイラを`deleted`既定のコンス トラクター。 この問題を解決するには、宣言されている場合、データ メンバーを初期化します。

```cpp
// C2280_uninit.cpp
// compile with: cl /c C2280_uninit.cpp
struct A {
    const int i; // uninitialized const-qualified data
    // members or reference type data members cause
    // the implicit default constructor to be deleted.
    // To fix, initialize the value in the declaration:
    // const int i = 42;
} a;    // C2280
```

## <a name="example-reference-and-const-data-members"></a>例:参照、const データ メンバー

A`const`を宣言するコンパイラが参照型のデータ メンバーや、`deleted`コピー代入演算子。 初期化されると、単純なコピーまたは移動が動作することはできませんのでこれらのメンバーは、代入できません。 この問題を解決するには、エラーが発生する割り当て操作を削除するユーザー ロジックを変更するをお勧めします。

```cpp
// C2280_ref.cpp
// compile with: cl /c C2280_ref.cpp
extern int k;
struct A {
    A();
    int& ri = k; // a const or reference data member causes
    // implicit copy assignment operator to be deleted.
};

void f() {
    A a1, a2;
    // To fix, consider removing this assignment.
    a2 = a1;    // C2280
}
```

## <a name="example-movable-deletes-implicit-copy"></a>例:移動可能な暗黙的なコピーを削除します。

コンパイラが暗黙的にコピー コンス トラクターを宣言し、としてそれを定義クラス宣言の移動コンス トラクターまたは移動代入演算子、コピー コンス トラクターを明示的に宣言しない場合は、`deleted`します。 同様に、クラス宣言の移動コンス トラクターまたは移動代入演算子、コピー代入演算子を明示的に宣言しない場合は、コンパイラに暗黙的に宣言コピー代入演算子と定義として`deleted`します。 この問題を解決するには、これらのメンバーを明示的に宣言する必要があります。

エラー c2280 を発行に関連して表示、`unique_ptr`がほぼ確実には、コピー コンス トラクターを呼び出すしようとしているため、`deleted`関数。 仕様では、`unique_ptr`コピーすることはできません。 移動コンス トラクターを使用すると、代わりに所有権を転送できます。

```cpp
// C2280_move.cpp
// compile with: cl /c C2280_move.cpp
class base
{
public:
    base();
    ~base();
    base(base&&);
    // Move constructor causes copy constructor to be
    // implicitly declared as deleted. To fix this
    // issue, you can explicitly declare a copy constructor:
    // base(base&);
    // If you want the compiler default version, do this:
    // base(base&) = default;
};

void copy(base *p)
{
    base b{*p};  // C2280
}
```

## <a name="example-variant-and-volatile-members"></a>例:Variant と揮発性のメンバー

バージョンの Visual Studio 2015 Update 2 の前に、コンパイラは、非準拠と生成された既定のコンス トラクターとデストラクターの無名共用体でした。 として暗黙的に宣言されたようになりましたこれら`deleted`します。 これらのバージョンには、暗黙の定義の非準拠も許可されている`default`コピーし、移動コンス トラクターと`default`コピーし、移動代入演算子では、クラスと構造体を持つ`volatile`メンバー変数。 コンパイラは、ここでが自明でないコンス トラクターと代入演算子を検討しが生成されない`default`実装します。 コピーと移動コンス トラクターと共用体またはクラスのコピーと移動の代入演算子が暗黙的に定義としてこのようなクラスが共用体、またはクラスの内部で匿名共用体のメンバーである場合は、`deleted`します。 この問題を解決するには、必要な特殊なメンバー関数を明示的に宣言する必要があります。

```cpp
// C2280_variant.cpp
// compile with: cl /c C2280_variant.cpp
struct A {
    A() = default;
    A(const A&);
};

struct B {
    union {
        A a;
        int i;
    };
    // To fix this issue, declare the required
    // special member functions:
    // B();
    // B(const B& b);
};

int main() {
    B b1;
    B b2(b1);  // C2280
}
```

## <a name="example-indirect-base-members-deleted"></a>例:間接の基本メンバーを削除

Visual Studio 2015 Update 2 の前に、コンパイラのバージョンが非準拠と特殊なメンバーの関数を呼び出す間接的に派生した派生クラスの許可`private virtual`基本クラス。 コンパイラは、このような呼び出しが行われたときに今すぐコンパイラ エラー C2280 を発行します。

この例では、クラス`top`仮想プライベートから直接派生した`base`します。 メンバーは、この準拠のコードで`base`にアクセスできない`top`; 型のオブジェクトを`top`既定が構築されたか、破棄することはできません。 以前のコンパイラの動作に依存するコードでこの問題を解決するを使用する中間クラスを変更`protected virtual`派生、または変更、`top`クラスを直接の派生を使用します。

```cpp
// C2280_indirect.cpp
// compile with: cl /c C2280_indirect.cpp
class base
{
protected:
    base();
    ~base();
};

class middle : private virtual base {};
// Possible fix: Replace line above with:
// class middle : protected virtual base {};
class top : public virtual middle {};    // C4594, C4624
// Another possible fix: use direct derivation:
// class top : public virtual middle, private virtual base {};

void destroy(top *p)
{
    delete p;  // C2280
}
```
