---
title: コンストラクター (C++)
ms.date: 12/27/2019
helpviewer_keywords:
- constructors [C++]
- objects [C++], creating
- instance constructors
ms.assetid: 3e9f7211-313a-4a92-9584-337452e061a9
ms.openlocfilehash: 985c63c5c937f9e85b6898cdbcc61f347688b96d
ms.sourcegitcommit: 00f50ff242031d6069aa63c81bc013e432cae0cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/30/2019
ms.locfileid: "75546394"
---
# <a name="constructors-c"></a>コンストラクター (C++)

クラスメンバーを初期化する方法をカスタマイズしたり、クラスのオブジェクトが作成されたときに関数を呼び出したりするには、*コンストラクター*を定義します。 コンストラクターにはクラスと同じ名前があり、戻り値はありません。 さまざまな方法で初期化をカスタマイズするために、必要に応じてオーバーロードされたコンストラクターをいくつでも定義できます。 通常、クラス定義または継承階層の外部にあるコードでクラスのオブジェクトを作成できるように、コンストラクターにはパブリックアクセシビリティがあります。 ただし、コンストラクターを**protected**または**private**として宣言することもできます。

コンストラクターは、必要に応じてメンバーの init リストを受け取ることができます。 これは、コンストラクター本体で値を割り当てるよりも、クラスメンバーを初期化するより効率的な方法です。 次の例は、3つのオーバーロードされたコンストラクターを持つ `Box` クラスを示しています。 最後の2つの使用メンバーの初期化リスト:

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    explicit Box(int i) : m_width(i), m_length(i), m_height(i) // member init list
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}

    int Volume() { return m_width * m_length * m_height; }

private:
    // Will have value of 0 when default constructor is called.
    // If we didn't zero-init here, default constructor would
    // leave them uninitialized with garbage values.
    int m_width{ 0 };
    int m_length{ 0 };
    int m_height{ 0 };
};
```

クラスのインスタンスを宣言すると、コンパイラは、オーバーロードの解決の規則に基づいて、どのコンストラクターを呼び出すかを選択します。

```cpp
int main()
{
    Box b; // Calls Box()

    // Using uniform initialization (preferred):
    Box b2 {5}; // Calls Box(int)
    Box b3 {5, 8, 12}; // Calls Box(int, int, int)

    // Using function-style notation:
    Box b4(2, 4, 6); // Calls Box(int, int, int)
}
```

- コンストラクターは、 **inline**、 [explicit](#explicit_constructors)、 **friend** 、または[constexpr](#constexpr_constructors)として宣言できます。
- コンストラクターは、 **const**、 **volatile** 、または**const volatile**として宣言されたオブジェクトを初期化できます。 コンストラクターが完了すると、オブジェクトは**const**になります。
- 実装ファイルでコンストラクターを定義するには、他のメンバー関数と同じように修飾名を指定します。 `Box::Box(){...}`。

## <a name="member_init_list"></a>メンバー初期化子リスト

コンストラクターは、必要に応じてメンバー初期化子リストを持つことができます。これにより、コンストラクター本体の実行前にクラスメンバーが初期化されます。 (メンバー初期化子リストは、型[std:: initializer_list\<t >](../standard-library/initializer-list-class.md)の*初期化子リスト*と同じではありません)。

メンバーを直接初期化するので、コンストラクターの本体に値を割り当てるよりも、メンバー初期化子リストを使用することをお勧めします。 次の例では、メンバー初期化子リストは、コロンの後のすべての**識別子 (引数)** 式で構成されています。

```cpp
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
```

識別子はクラスメンバーを参照する必要があります。引数の値を使用して初期化されます。 引数には、コンストラクターパラメーター、関数呼び出し、または[std:: initializer_list\<t >](../standard-library/initializer-list-class.md)のいずれかを指定できます。

**const**メンバーと参照型のメンバーは、メンバー初期化子リストで初期化する必要があります。

パラメーター化された基本クラスコンストラクターの呼び出しは、派生コンストラクターを実行する前に基底クラスが完全に初期化されるように、初期化子リストで行う必要があります。

## <a name="default_constructors"></a>既定のコンストラクター

*既定のコンストラクター*には通常、パラメーターはありませんが、既定値を持つパラメーターを持つことができます。

```cpp
class Box {
public:
    Box() { /*perform any required default initialization steps*/}

    // All params have default values
    Box (int w = 1, int l = 1, int h = 1): m_width(w), m_height(h), m_length(l){}
...
}
```

既定のコンストラクターは、[特別なメンバー関数](special-member-functions.md)の1つです。 クラスでコンストラクターが宣言されていない場合、コンパイラは暗黙的な**インライン**既定コンストラクターを提供します。

```cpp
#include <iostream>
using namespace std;

class Box {
public:
    int Volume() {return m_width * m_height * m_length;}
private:
    int m_width { 0 };
    int m_height { 0 };
    int m_length { 0 };
};

int main() {
    Box box1; // Invoke compiler-generated constructor
    cout << "box1.Volume: " << box1.Volume() << endl; // Outputs 0
}
```

暗黙の既定のコンストラクターを使用する場合は、前の例で示したように、クラス定義のメンバーを初期化してください。 これらの初期化子がない場合、メンバーは初期化されず、Volume () 呼び出しによってガベージ値が生成されます。 一般に、暗黙的な既定のコンストラクターに依存していない場合でも、この方法でメンバーを初期化することをお勧めします。

[削除済み](#explicitly_defaulted_and_deleted_constructors)として定義することで、コンパイラが暗黙的な既定のコンストラクターを生成しないようにすることができます。

```cpp
    // Default constructor
    Box() = delete;
```

コンパイラによって生成される既定のコンストラクターは、クラスメンバーが既定で構築可能でない場合は、削除済みとして定義されます。 たとえば、クラス型のすべてのメンバーとそのクラス型のメンバーは、既定のコンストラクターとアクセス可能なデストラクターを持つ必要があります。 参照型および**const**メンバーのすべてのデータメンバーには、既定のメンバー初期化子が必要です。

コンパイラによって生成された既定のコンストラクターを呼び出し、かっこを使用しようとすると、警告が発行されます。

```cpp
class myclass{};
int main(){
myclass mc();     // warning C4930: prototyped function not called (was a variable definition intended?)
}
```

これは最も厄介な解析の例です。 例の式は、関数の宣言としても、既定のコンストラクターの呼び出しとしても解釈できるため、さらに、C++ パーサーが宣言を最優先に処理するため、この式は関数宣言として扱われます。 詳細については、「[最も厄介な解析](https://en.wikipedia.org/wiki/Most_vexing_parse)」を参照してください。

既定以外のコンストラクターが宣言されている場合は、コンパイル時に既定のコンストラクターは生成されません。

```cpp
class Box {
public:
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height){}
private:
    int m_width;
    int m_length;
    int m_height;

};

int main(){

    Box box1(1, 2, 3);
    Box box2{ 2, 3, 4 };
    Box box3; // C2512: no appropriate default constructor available
}
```

クラスに既定のコンストラクターがない場合、そのクラスのオブジェクトの配列は、角かっこ構文を使用して構築することはできません。 たとえば、前に示したコード ブロックでは、Boxes の配列は次のように宣言することはできません。

```cpp
Box boxes[3]; // C2512: no appropriate default constructor available
```

ただし、一連の初期化子リストを使用して、Box オブジェクトの配列を初期化することができます。

```cpp
Box boxes[3]{ { 1, 2, 3 }, { 4, 5, 6 }, { 7, 8, 9 } };
```

詳細については、「[初期化子](initializers.md)」を参照してください。

## <a name="copy_and_move_constructors"></a>コピーコンストラクター

*コピーコンストラクター*は、同じ型のオブジェクトからメンバー値をコピーすることによって、オブジェクトを初期化します。 クラスメンバーがスカラー値などのすべての単純型である場合、コンパイラによって生成されるコピーコンストラクターは十分であり、独自に定義する必要はありません。 クラスでより複雑な初期化が必要な場合は、カスタムコピーコンストラクターを実装する必要があります。 たとえば、クラスメンバーがポインターである場合、コピーコンストラクターを定義して新しいメモリを割り当て、もう一方のオブジェクトから値をコピーする必要があります。 コンパイラによって生成されたコピーコンストラクターは、ポインターを単にコピーして、新しいポインターがもう一方のメモリ位置を参照するようにします。

コピーコンストラクターは、次のいずれかのシグネチャを持つことができます。

```cpp
    Box(Box& other); // Avoid if possible--allows modification of other.
    Box(const Box& other);
    Box(volatile Box& other);
    Box(volatile const Box& other);

    // Additional parameters OK if they have default values
    Box(Box& other, int i = 42, string label = "Box");
```

コピーコンストラクターを定義する場合は、コピー代入演算子 (=) も定義する必要があります。 詳細については、「[代入](assignment.md)および[コピーコンストラクター」および「コピー代入演算子](copy-constructors-and-copy-assignment-operators-cpp.md)」を参照してください。

コピーコンストラクターを削除済みとして定義することで、オブジェクトがコピーされないようにすることができます。

```cpp
    Box (const Box& other) = delete;
```

オブジェクトをコピーしようとすると、エラー C2280 が発生します。*削除された関数を参照しようと*しています。

## <a name="move_constructors"></a>移動コンストラクター

*移動コンストラクター*は、既存のオブジェクトのデータの所有権を、元のデータをコピーせずに新しい変数に移動する特別なメンバー関数です。 最初のパラメーターとして右辺値参照を受け取り、追加のパラメーターには既定値が必要です。 移動コンストラクターを使用すると、大きなオブジェクトを渡すときにプログラムの効率を大幅に向上させることができます。

```cpp
Box(Box&& other);
```

コンパイラは、オブジェクトが破棄され、リソースを必要としなくなる同じ型の別のオブジェクトによって初期化されている特定の状況で、移動コンストラクターを選択します。 次の例は、オーバーロードの解決によって移動コンストラクターが選択された場合の1つのケースを示しています。 `get_Box()`を呼び出すコンストラクターでは、戻り値は*xvalue* (有効期限が切れた値) になります。 変数に割り当てられていないため、スコープ外に出ます。 この例の意図を示すために、ボックスに、その内容を表す文字列の大きなベクターを用意します。 移動コンストラクターは、ベクターとその文字列をコピーするのではなく、新しいオブジェクトに追加されるように、有効期限切れの値 "box" からそれを "盗み" ます。 `vector` と `string` の両方のクラスに独自の移動コンストラクターが実装されているため、`std::move` を呼び出す必要があります。

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
using namespace std;

class Box {
public:
    Box() { std::cout << "default" << std::endl; }
    Box(int width, int height, int length)
       : m_width(width), m_height(height), m_length(length)
    {
        std::cout << "int,int,int" << std::endl;
    }
    Box(Box& other)
       : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        std::cout << "copy" << std::endl;
    }
    Box(Box&& other) : m_width(other.m_width), m_height(other.m_height), m_length(other.m_length)
    {
        m_contents = std::move(other.m_contents);
        std::cout << "move" << std::endl;
    }
    int Volume() { return m_width * m_height * m_length; }
    void Add_Item(string item) { m_contents.push_back(item); }
    void Get_Contents()
    {
        for (const auto& item : m_contents)
        {
            cout << item << " ";
        }
    }
private:
    int m_width{ 0 };
    int m_height{ 0 };
    int m_length{ 0 };
    vector<string> m_contents;
};

Box get_Box()
{
    Box b(5, 10, 18); // "int,int,int"
    b.Add_Item("Toupee");
    b.Add_Item("Megaphone");
    b.Add_Item("Suit");

    return b;
}

int main()
{
    Box b; // "default"
    Box b1(b); // "copy"
    Box b2(get_Box()); // "move"
    cout << "b2 contents: ";
    b2.Get_Contents(); // Prove that we have all the values

    char ch;
    cin >> ch; // keep window open
    return 0;
}
```

クラスで移動コンストラクターが定義されていない場合、ユーザーが宣言したコピーコンストラクター、コピー代入演算子、移動代入演算子、またはデストラクターが存在しない場合、コンパイラは暗黙的なコンストラクターを生成します。 明示的または暗黙的な移動コンストラクターが定義されていない場合、移動コンストラクターを使用する操作では、代わりにコピーコンストラクターが使用されます。 クラスで移動コンストラクターまたは移動代入演算子が宣言されている場合、暗黙的に宣言されたコピーコンストラクターは削除済みとして定義されます。

暗黙的に宣言された移動コンストラクターは、クラス型のメンバーがデストラクターを持たないか、またはコンパイラが移動操作に使用するコンストラクターを判断できない場合、deleted として定義されます。

自明でない移動コンストラクターを記述する方法の詳細については、「[移動コンストラクターと移動代入C++演算子 ()](../cpp/move-constructors-and-move-assignment-operators-cpp.md)」を参照してください。

## <a name="explicitly_defaulted_and_deleted_constructors"></a>明示的に既定化および削除されたコンストラクター

コピーコンストラクター、既定のコンストラクター、移動コンストラクター、コピー代入演算子、移動代入演算子、およびデストラクターを明示的に*既定*で使用できます。 すべての特殊なメンバー関数を明示的に*削除*できます。

```cpp
class Box
{
public:
    Box2() = delete;
    Box2(const Box2& other) = default;
    Box2& operator=(const Box2& other) = default;
    Box2(Box2&& other) = default;
    Box2& operator=(Box2&& other) = default;
    //...
};
```

詳細については、「[明示的に既定化および削除された関数](../cpp/explicitly-defaulted-and-deleted-functions.md)」を参照してください。

## <a name="constexpr_constructors"></a>constexpr コンストラクター

コンストラクターは、の場合、 [constexpr](constexpr-cpp.md)として宣言できます。

- これは、既定値として宣言されているか、 [constexpr 関数](constexpr-cpp.md#constexpr_functions)のすべての条件を満たしています。
- クラスには仮想基底クラスがありません。
- 各パラメーターは[リテラル型](trivial-standard-layout-and-pod-types.md#literal_types)です。
- 本文が関数 try ブロックではありません。
- すべての非静的データメンバーと基底クラスサブオブジェクトが初期化されます。
- クラスが (a) バリアントメンバーを持つ共用体、または (b) が匿名共用体を持つ場合、1つの共用体メンバーだけが初期化されます。
- クラス型のすべての非静的データメンバーと、すべての基底クラスサブオブジェクトに constexpr コンストラクターがある

## <a name="init_list_constructors"></a>初期化子リストコンストラクター

コンストラクターが[std:: initializer_list\<t\>](../standard-library/initializer-list-class.md)をパラメーターとして受け取り、その他のパラメーターに既定の引数がある場合、直接初期化によってクラスがインスタンス化されるときに、そのコンストラクターはオーバーロードの解決で選択されます。 Initializer_list を使用して、それを受け入れることができるすべてのメンバーを初期化できます。 たとえば、Box クラス (前に示した) に `std::vector<string>` メンバー `m_contents`があるとします。 次のようなコンストラクターを指定できます。

```cpp
    Box(initializer_list<string> list, int w = 0, int h = 0, int l = 0)
        : m_contents(list), m_width(w), m_height(h), m_length(l)
{}
```

次のように Box オブジェクトを作成します。

```cpp
    Box b{ "apples", "oranges", "pears" }; // or ...
    Box b2(initializer_list<string> { "bread", "cheese", "wine" }, 2, 4, 6);
```

## <a name="explicit_constructors"></a>明示的なコンストラクター

クラスが 1 つのパラメーターを持つコンストラクターを含む場合、または 1 つを除くすべてのパラメーターに既定値がある場合は、パラメーター型をクラス型へ暗黙的に変換できます。 `Box` クラスに次のようなコンストラクターがある場合を例に説明します。

```cpp
Box(int size): m_width(size), m_length(size), m_height(size){}
```

次のように、ボックスを初期化することができます。

```cpp
Box b = 42;
```

または、int をボックスを受け取る関数に渡します。

```cpp
class ShippingOrder
{
public:
    ShippingOrder(Box b, double postage) : m_box(b), m_postage(postage){}

private:
    Box m_box;
    double m_postage;
}
//elsewhere...
    ShippingOrder so(42, 10.8);
```

このような変換が便利な場合もありますが、微妙でありながら重大なコードのエラーにつながることが多くあります。 一般的な規則として、コンストラクター (およびユーザー定義演算子) に対して**explicit**キーワードを使用して、この種の暗黙的な型変換を防止する必要があります。

```cpp
explicit Box(int size): m_width(size), m_length(size), m_height(size){}
```

コンストラクターが明示的な場合、次の行ではコンパイラ エラーが発生します: `ShippingOrder so(42, 10.8);`。  詳細については、「[ユーザー定義型の変換](../cpp/user-defined-type-conversions-cpp.md)」を参照してください。

## <a name="order_of_construction"></a>構築の順序

コンストラクターによる処理は次の順序で実行されます。

1. 基底クラスとメンバーのコンストラクターを宣言の順序で呼び出します。

1. クラスが仮想基底クラスから派生されている場合は、オブジェクトの仮想基底ポインターを初期化します。

1. クラスが仮想関数を含むか継承する場合は、オブジェクトの仮想関数ポインターを初期化します。 仮想関数ポインターは、クラスの仮想関数テーブルをポイントし、コードへの仮想関数呼び出しの正しいバインドを可能にします。

1. その関数本体のコードをすべて実行します。

次の例に、基底クラスとメンバーのコンストラクターが派生クラスのコンストラクターで呼び出される順序を示します。 まず、基底コンストラクターが呼び出され、基底クラスのメンバーがクラス宣言内の出現順に初期化されて、その後に派生コンストラクターが呼び出されます。

```cpp
#include <iostream>

using namespace std;

class Contained1 {
public:
    Contained1() { cout << "Contained1 ctor\n"; }
};

class Contained2 {
public:
    Contained2() { cout << "Contained2 ctor\n"; }
};

class Contained3 {
public:
    Contained3() { cout << "Contained3 ctor\n"; }
};

class BaseContainer {
public:
    BaseContainer() { cout << "BaseContainer ctor\n"; }
private:
    Contained1 c1;
    Contained2 c2;
};

class DerivedContainer : public BaseContainer {
public:
    DerivedContainer() : BaseContainer() { cout << "DerivedContainer ctor\n"; }
private:
    Contained3 c3;
};

int main() {
    DerivedContainer dc;
}
```

出力を次に示します。

```Output
Contained1 ctor
Contained2 ctor
BaseContainer ctor
Contained3 ctor
DerivedContainer ctor
```

派生クラスのコンストラクターは常に、基底クラスのコンストラクターを呼び出します。それにより、完全に構築された基底クラスに依存して、追加の処理を実行できるようになります。 基底クラスのコンストラクターは、派生の順序で呼び出されます。たとえば、`ClassA` が `ClassC`から派生した `ClassB`から派生している場合は、最初に `ClassC` コンストラクター、次に `ClassB` コンストラクター、次に `ClassA` コンストラクターを呼び出します。

基底クラスに既定のコンストラクターがない場合は、派生クラスのコンストラクターで基底クラスのコンストラクターのパラメーターを指定する必要があります。

```cpp
class Box {
public:
    Box(int width, int length, int height){
       m_width = width;
       m_length = length;
       m_height = height;
    }

private:
    int m_width;
    int m_length;
    int m_height;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, const string label&) : Box(width, length, height){
        m_label = label;
    }
private:
    string m_label;
};

int main(){

    const string aLabel = "aLabel";
    StorageBox sb(1, 2, 3, aLabel);
}
```

コンストラクターが例外をスローした場合、破棄の順序はコンストラクションの順序と逆になります。

1. コンストラクター関数本体のコードがアンワインドされます。

1. 基底クラスとメンバーのオブジェクトが宣言とは逆の順序で破棄されます。

1. コンストラクターがデリゲート コンストラクターでない場合は、完全に構築されたすべての基底クラスのオブジェクトとメンバーが破棄されます。 ただし、オブジェクト自体が完全に構築されていないため、デストラクターは実行されません。

## <a name="extended_aggregate"></a>派生コンストラクターと拡張集計初期化

基底クラスのコンストラクターがパブリックではなく、派生クラスからアクセスできる場合は、Visual Studio 2017 以降の **/std: c++ 17**モードでは、空の中かっこを使用して派生型のオブジェクトを初期化することはできません。

次の例では、C++14 の準拠ビヘイビアーを示します。

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};

Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

C++17 で、`Derived` は集約型と見なされるようになりました。 つまり、既定のプライベート コンストラクターによる `Base` の初期化は、集約初期化ルールの一部として直接実行されます。 以前、`Base` プライベート コンストラクターは `Derived` コンストラクターを介して呼び出され、friend 宣言があるために成功していました。

次の例では、Visual Studio 2017 以降の C++ 17 の動作を、 **/std: c++ 17**モードで示します。

```cpp
struct Derived;

struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};

Derived d1; // OK. No aggregate init involved.

Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="constructors-for-classes-that-have-multiple-inheritance"></a>多重継承を持つクラスのコンストラクター

クラスが複数の基底クラスから派生されている場合、基底クラスのコンストラクターは、派生クラスの宣言で示されている順序で呼び出されます。

```cpp
#include <iostream>
using namespace std;

class BaseClass1 {
public:
    BaseClass1() { cout << "BaseClass1 ctor\n"; }
};
class BaseClass2 {
public:
    BaseClass2() { cout << "BaseClass2 ctor\n"; }
};
class BaseClass3 {
public:
    BaseClass3() { cout << "BaseClass3 ctor\n"; }
};
class DerivedClass : public BaseClass1,
                     public BaseClass2,
                     public BaseClass3
                     {
public:
    DerivedClass() { cout << "DerivedClass ctor\n"; }
};

int main() {
    DerivedClass dc;
}
```

予想される出力を次に示します。

```Output
BaseClass1 ctor
BaseClass2 ctor
BaseClass3 ctor
DerivedClass ctor
```

## <a name="delegating_constructors"></a>コンストラクターのデリゲート

*デリゲートコンストラクター*は、初期化の作業の一部を実行するために、同じクラス内の別のコンストラクターを呼び出します。 これは、すべてのコンストラクターが同様の処理を実行する必要がある場合に便利です。 メインロジックを1つのコンストラクターに記述し、他のコンストラクターから呼び出すことができます。 次の簡単な例では、Box (int) は、その作業を Box (int, int, int) にデリゲートします。

```cpp
class Box {
public:
    // Default constructor
    Box() {}

    // Initialize a Box with equal dimensions (i.e. a cube)
    Box(int i) :  Box(i, i, i);  // delegating constructor
    {}

    // Initialize a Box with custom dimensions
    Box(int width, int length, int height)
        : m_width(width), m_length(length), m_height(height)
    {}
    //... rest of class as before
};
```

コンストラクターによって作成されたオブジェクトは、コンストラクターが終了するとすぐに完全に初期化されます。 詳細については、「[コンストラクターの委任](../cpp/delegating-constructors.md)」を参照してください。

## <a name="inheriting_constructors"></a>コンストラクターの継承 (C++ 11)

派生クラスは、次の例に示すように**using**宣言を使用して、直接基底クラスからコンストラクターを継承できます。

```cpp
#include <iostream>
using namespace std;

class Base
{
public:
    Base() { cout << "Base()" << endl; }
    Base(const Base& other) { cout << "Base(Base&)" << endl; }
    explicit Base(int i) : num(i) { cout << "Base(int)" << endl; }
    explicit Base(char c) : letter(c) { cout << "Base(char)" << endl; }

private:
    int num;
    char letter;
};

class Derived : Base
{
public:
    // Inherit all constructors from Base
    using Base::Base;

private:
    // Can't initialize newMember from Base constructors.
    int newMember{ 0 };
};

int main()
{
    cout << "Derived d1(5) calls: ";
    Derived d1(5);
    cout << "Derived d1('c') calls: ";
    Derived d2('c');
    cout << "Derived d3 = d2 calls: " ;
    Derived d3 = d2;
    cout << "Derived d4 calls: ";
    Derived d4;
}

/* Output:
Derived d1(5) calls: Base(int)
Derived d1('c') calls: Base(char)
Derived d3 = d2 calls: Base(Base&)
Derived d4 calls: Base()*/
```

::: moniker range=">=vs-2017"

**Visual Studio 2017 以降**: **/std: c++ 17**モードの using ステートメントは、派生クラスのコンストラクターに対し**て**同じシグネチャを持つものを除き、基本クラスからのすべてのコンストラクターのスコープを設定します。 一般に、派生クラスが新しいデータ メンバーまたはコンストラクターを宣言しない場合は、コンストラクターの継承を使用することをお勧めします。 「 [Visual Studio 2017 バージョン15.7 の機能強化](https://docs.microsoft.com/cpp/overview/cpp-conformance-improvements?view=vs-2017#improvements_157)」も参照してください。

::: moniker-end

型が基底クラスを指定している場合、クラス テンプレートは型の引数からすべてのコンストラクターを継承できます。

```cpp
template< typename T >
class Derived : T {
    using T::T;   // declare the constructors from T
    // ...
};
```

派生クラスは、複数の基底クラスに同じシグネチャを持つコンストラクターがある場合、複数の基底クラスからは継承できません。

## <a name="constructors_in_composite_classes"></a>コンストラクターと複合クラス

クラス型のメンバーを含むクラスは、*複合クラス*と呼ばれます。 複合クラスのクラス型のメンバーが作成されると、そのコンストラクターはクラス自体のコンストラクターの前に呼び出されます。 含まれるクラスに既定のコンストラクターがないときは、複合クラスのコンストラクターで初期化リストを使用する必要があります。 前に示した `StorageBox` の例で、`m_label` メンバー変数の型を新しい `Label` クラスに変更した場合、両方の基底クラスのコンストラクターを呼び出し、`m_label` のコンストラクターで `StorageBox` 変数を初期化する必要があります。

```cpp
class Label {
public:
    Label(const string& name, const string& address) { m_name = name; m_address = address; }
    string m_name;
    string m_address;
};

class StorageBox : public Box {
public:
    StorageBox(int width, int length, int height, Label label)
        : Box(width, length, height), m_label(label){}
private:
    Label m_label;
};

int main(){
// passing a named Label
    Label label1{ "some_name", "some_address" };
    StorageBox sb1(1, 2, 3, label1);

    // passing a temporary label
    StorageBox sb2(3, 4, 5, Label{ "another name", "another address" });

    // passing a temporary label as an initializer list
    StorageBox sb3(1, 2, 3, {"myname", "myaddress"});
}
```

## <a name="in-this-section"></a>このセクションの内容

- [コピーコンストラクターとコピー代入演算子](copy-constructors-and-copy-assignment-operators-cpp.md)
- [移動コンストラクターと移動代入演算子](move-constructors-and-move-assignment-operators-cpp.md)
- [コンストラクターのデリゲート](delegating-constructors.md)

## <a name="see-also"></a>関連項目

[クラスと構造体](classes-and-structs-cpp.md)
