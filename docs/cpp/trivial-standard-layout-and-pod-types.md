---
title: 単純, 標準レイアウト, POD, およびリテラル型
ms.date: 04/05/2018
ms.assetid: 2b23a7be-9bad-49fc-8298-31a9a7c556b0
ms.openlocfilehash: 2745302b3ebd7927e9d839e4661e884a2bd91042
ms.sourcegitcommit: 61121faf879cc581a4d39e4baccabf7cf1f673a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/20/2019
ms.locfileid: "65934215"
---
# <a name="trivial-standard-layout-pod-and-literal-types"></a>単純, 標準レイアウト, POD, およびリテラル型

*レイアウト*という用語は、メモリ内のクラス、構造体、共用体型のオブジェクトのメンバーの配置方法を指しています。 言語の仕様によって、レイアウトが明確に定義されている場合もあります。 ただし、クラスまたは構造体に仮想基底クラス、仮想関数、アクセス制御が異なるメンバーなど、特定の C++ 言語の機能が含まれている場合、コンパイラは自由にレイアウトを選択できます。 レイアウトは、最適化が何に対して実行されているかによって変わる可能性があり、多くの場合、オブジェクトが占有するメモリ領域が連続していない場合もあります。 たとえば、クラスに仮想関数が含まれている場合、そのクラスのすべてのインスタンスが 1 つの仮想関数テーブルを共有する場合があります。 このような型は、非常に便利ですが、制限もあります。 レイアウトが定義されていないため、C などの他の言語で書かれたプログラムに渡すことができません。また、レイアウトが連続していない場合には、`memcopy` などの高速な低レベル関数で安全にコピーしたり、ネットワーク上でシリアル化したりできません。

特定のメモリ レイアウトに依存する操作に指定した型の適合性を推測するコンパイラや C++ のプログラム、メタプログラムを有効にするため、C++14 では *単純*、*標準レイアウト*、*POD* (Plain Old Data) という、単純なクラスと構造体の 3 つのカテゴリを導入しました。 標準ライブラリには、指定した型が指定したカテゴリに属しているかどうかを判断する `is_trivial<T>`、`is_standard_layout<T>`、`is_pod<T>` の関数テンプレートが含まれています。

## <a name="trivial-types"></a>単純型

C++ のクラスまたは構造体にコンパイラから提供された、または明示的に既定値にされている特殊なメンバー関数が含まれている場合、それは単純型です。 これは連続したメモリ領域を占有します。 メンバーごとに異なるアクセス指定子を持つことができます。 C++ では、このような場合、コンパイラで自由にメンバーを配置することができます。 したがって、このようなオブジェクトは memcpy できますが、これを C プログラムから確実に使用することはできません。 単純型 T は char または符号なし char の配列にコピーし、T 変数に安全に戻すことができます。 配置の要件により、型のメンバーの間にパディング バイトが生じる場合があります。

単純型は単純な既定のコンストラクター、単純なコピー コンストラクター、単純なコピー代入演算子、単純なデストラクターを持つことができます。 各ケースにおいて、*単純*は、コンストラクター/演算子/デストラクターがユーザー指定ではなく、次のようなクラスに属していることを意味します

- 仮想関数または仮想基底クラスがない

- 対応する非単純コンストラクター/演算子/デストラクターが含まれる基底クラスがない

- 対応する非単純コンストラクター/演算子/デストラクターが含まれるクラス型のデータ メンバーがない

単純型の例を以下に示します。 Trivial2 で、`Trivial2(int a, int b)` コンストラクターが存在するには、既定のコンストラクターを指定する必要があります。 型を単純として修飾するには、そのコンストラクターを明示的に既定とする必要があります。

```cpp
struct Trivial
{
      int i;
private:
   int j;
   };

struct Trivial2
{
   int i;
   Trivial2(int a, int b) : i(a), j(b) {}
   Trivial2() = default;
   private:
   int j;   // Different access control
};
```

## <a name="standard-layout-types"></a>標準レイアウト型

クラスまたは構造体に C 言語にはない仮想関数のような特定の C++ 言語の機能が含まれておらず、すべてのメンバーに同じアクセス制御が含まれている場合、それは標準レイアウト型です。 memcpy が可能で、C プログラムで使用できるようにレイアウトが明確に定義されています。 標準レイアウト型は、ユーザー定義された特殊なメンバー関数を持つことができます。 さらに、標準レイアウト型には、次のような特性があります。

- 仮想関数または仮想基底クラスがない

- すべての非静的データ メンバーに同じアクセス制御が含まれている

- クラス型のすべての非静的メンバーが標準レイアウトである

- すべての基底クラスが標準レイアウトである

- 最初の非静的データ メンバーと同じ型の基底クラスがない

- 次のいずれかの条件を満たしています。

  - 最派生クラスに非静的データ メンバーがなく、非静的データ メンバーの基底クラスが 1 つしかない

  - 非静的データ メンバーを含む基底クラスがない

次のコードは、標準レイアウト型の一例です。

```cpp
struct SL
{
   // All members have same access:
   int i;
   int j;
   SL(int a, int b) : i(a), j(b) {} // User-defined constructor OK
};
```

最後の 2 つの要件は、コードの方がわかりやすいかもしれません。 次の例では、Base が標準レイアウトですが、`Derived` が標準レイアウトではありません。これは最派生クラスと `Base` の両方に非静的データ メンバーが含まれるためです。

```cpp
struct Base
{
   int i;
   int j;
};

// std::is_standard_layout<<Derived> == false!
struct Derived : public Base
{
   int x;
   int y;
};
```

この例では、`Base` に非静的データ メンバーが含まれないため、`Derived` は標準レイアウトです。

```cpp
struct Base
{
   void Foo() {}
};

// std::is_standard_layout<<Derived> == true
struct Derived : public Base
{
   int x;
   int y;
};
```

`Base` にデータ メンバーが含まれ、`Derived` にメンバー関数しか含まれない場合、Derived も標準レイアウトになります。

## <a name="pod-types"></a>POD 型

クラスまたは構造体が両方とも単純および標準レイアウトである場合、それは POD (Plain Old Data) 型になります。 したがって、POD 型のメモリ レイアウトは連続し、各メンバーにはそれより前に宣言されたメンバーより上位のアドレスが割り当てられるため、バイトごとのコピーとバイナリ I/O をこれらの型に対して実行することができます。  int などのスカラー型も POD 型です。 クラスである POD 型には、非静的データ メンバーの POD 型のみを含めることができます。

## <a name="example"></a>例

次の例は単純、標準レイアウト、POD 型の違いを示しています。

```cpp
#include <type_traits>
#include <iostream>

using namespace std;

struct B
{
protected:
   virtual void Foo() {}
};

// Neither trivial nor standard-layout
struct A : B
{
      int a;
   int b;
   void Foo() override {} // Virtual function
};

// Trivial but not standard-layout
struct C
   {
      int a;
private:
   int b;   // Different access control
};

// Standard-layout but not trivial
struct D
{
   int a;
   int b;
   D() {} //User-defined constructor
};

struct POD
{
   int a;
   int b;
};

int main()
{
   cout << boolalpha;
   cout << "A is trivial is " << is_trivial<A>() << endl; // false
   cout << "A is standard-layout is " << is_standard_layout<A>() << endl;  // false

   cout << "C is trivial is " << is_trivial<C>() << endl; // true
   cout << "C is standard-layout is " << is_standard_layout<C>() << endl;  // false

   cout << "D is trivial is " << is_trivial<D>() << endl;  // false
   cout << "D is standard-layout is " << is_standard_layout<D>() << endl; // true

   cout << "POD is trivial is " << is_trivial<POD>() << endl; // true
   cout << "POD is standard-layout is " << is_standard_layout<POD>() << endl; // true

   return 0;
}
```

## <a name="literal_types"></a> リテラル型

リテラル型は、コンパイル時にレイアウトを決定できます。 リテラル型を次に示します。

- void
- スカラー型
- 参照
- Void の配列、スカラー型または参照
- 自明なデストラクターを持ち、コンストラクターを移動もコピーもしない 1 つ以上の constexpr コンストラクターを持つクラス。 さらに、すべての非静的データ メンバーと基本クラスは volatile ではなくリテラル型にする必要があります。

## <a name="see-also"></a>関連項目

[基本的な概念](../cpp/basic-concepts-cpp.md)