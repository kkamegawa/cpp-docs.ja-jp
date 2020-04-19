---
title: テンプレート (C++)
ms.date: 12/27/2019
f1_keywords:
- template_cpp
helpviewer_keywords:
- templates, C++
- templates [C++]
ms.assetid: 90fcc14a-2092-47af-9d2e-dba26d25b872
ms.openlocfilehash: 36ada3cc3b933e99e9b29b3b58463f6bc526fc7d
ms.sourcegitcommit: 00f50ff242031d6069aa63c81bc013e432cae0cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/30/2019
ms.locfileid: "75546407"
---
# <a name="templates-c"></a>テンプレート (C++)

テンプレートは、のC++一般的なプログラミングの基礎となります。 厳密に型指定されたC++言語として、では、プログラマが明示的に宣言するか、コンパイラによって推測される、すべての変数に特定の型を持たせる必要があります。 ただし、操作する型に関係なく、多くのデータ構造とアルゴリズムは同じように見えます。 テンプレートを使用すると、クラスまたは関数の操作を定義し、その操作がどの具象型で動作するかをユーザーが指定できるようになります。

## <a name="defining-and-using-templates"></a>テンプレートの定義と使用

テンプレートは、ユーザーがテンプレートパラメーターに指定した引数に基づいて、コンパイル時に通常の型または関数を生成するコンストラクトです。 たとえば、次のような関数テンプレートを定義できます。

```cpp
template <typename T>
T minimum(const T& lhs, const T& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

上記のコードでは、1つの型パラメーター *T*を持つジェネリック関数のテンプレートについて説明します。このテンプレートの戻り値と呼び出しパラメーター (lhs と rhs) はすべてこの型です。 型パラメーターには任意の名前を指定できますが、慣例により、1つの大文字が最もよく使用されます。 *T*はテンプレートパラメーターです。**typename**キーワードは、このパラメーターが型のプレースホルダーであることを示します。 関数が呼び出されると、コンパイラは、`T` のすべてのインスタンスを、ユーザーによって指定されるか、コンパイラによって推測される具象型引数に置き換えます。 コンパイラがテンプレートからクラスまたは関数を生成するプロセスを、*テンプレートのインスタンス化*と呼びます。`minimum<int>` は、テンプレート `minimum<T>`のインスタンス化です。

他の場所では、ユーザーは、int に特化したテンプレートのインスタンスを宣言できます。 get_a () と get_b () が int を返す関数であることを前提としています。

```cpp
int a = get_a();
int b = get_b();
int i = minimum<int>(a, b);
```

ただし、これは関数テンプレートであるため、コンパイラは引数*a*と*b*から `T` の型を推測できます。通常の関数と同じように呼び出すことができます。

```cpp
int i = minimum(a, b);
```

コンパイラは、最後のステートメントを検出すると、テンプレート内の*T*のすべての出現箇所を**int**に置き換える新しい関数を生成します。

```cpp
int minimum(const int& lhs, const int& rhs)
{
    return lhs < rhs ? lhs : rhs;
}
```

コンパイラが関数テンプレートで型推論を実行する方法に関する規則は、通常の関数の規則に基づいています。 詳細については、「[関数テンプレート呼び出しのオーバーロードの解決](../cpp/overload-resolution-of-function-template-calls.md)」を参照してください。

## <a id="type_parameters"></a>型パラメーター

上の `minimum` テンプレートでは、型パラメーター *t*は、const および参照修飾子が追加される関数呼び出しパラメーターで使用されるまで、どのような方法でも修飾されていないことに注意してください。

型パラメーターの数に実際の制限はありません。 複数のパラメーターはコンマで区切ります。

```cpp
template <typename T, typename U, typename V> class Foo{};
```

キーワード**class**と等価**typename**このコンテキストでします。 前の例を次のように表すことができます。

```cpp
template <class T, class U, class V> class Foo{};
```

省略記号演算子 (...) を使用すると、任意の数の0個以上の型パラメーターを受け取るテンプレートを定義できます。

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
```

任意の組み込みまたはユーザー定義型を型引数として使用できます。 たとえば、標準ライブラリの[std:: vector](../standard-library/vector-class.md)を使用して、 **int**、 **double**、 [std:: string](../standard-library/basic-string-class.md)、`MyClass`、 **const** `MyClass`*、`MyClass&`などの型の変数を格納できます。 テンプレートを使用する場合の主な制限は、型引数が型パラメーターに適用されるすべての操作をサポートする必要があることです。 たとえば、次の例のように `MyClass` を使用して `minimum` を呼び出したとします。

```cpp
class MyClass
{
public:
    int num;
    std::wstring description;
};

int main()
{
    MyClass mc1 {1, L"hello"};
    MyClass mc2 {2, L"goodbye"};
    auto result = minimum(mc1, mc2); // Error! C2678
}
```

`MyClass` に **<** 演算子のオーバーロードが指定されていないため、コンパイラエラーが生成されます。

特定のテンプレートの型引数がすべて同じオブジェクト階層に属しているという固有の要件はありませんが、このような制限を適用するテンプレートを定義することはできます。 オブジェクト指向の手法とテンプレートを組み合わせることができます。たとえば、派生した * をベクター\<Base\*> に格納することができます。    引数はポインターである必要があることに注意してください。

```cpp
vector<MyClass*> vec;
   MyDerived d(3, L"back again", time(0));
   vec.push_back(&d);

   // or more realistically:
   vector<shared_ptr<MyClass>> vec2;
   vec2.push_back(make_shared<MyDerived>());
```

`std::vector` およびその他の標準ライブラリコンテナーが `T` の要素に適用する基本的な要件は、コピーによる割り当てが可能で、コピーによる構築が可能である `T` ことです。

## <a name="non-type-parameters"></a>非型パラメーター

や Java などの他の言語のC#ジェネリック型とC++は異なり、テンプレートでは、値パラメーターとも呼ばれる*非型パラメーター*がサポートされています。 たとえば、標準ライブラリの[std:: array](../standard-library/array-class-stl.md)クラスに似た次の例のように、配列の長さを指定する定数整数値を指定できます。

```cpp
template<typename T, size_t L>
class MyArray
{
    T arr[L];
public:
    MyArray() { ... }
};
```

テンプレート宣言の構文に注意してください。 `size_t` 値はコンパイル時にテンプレート引数として渡され、 **const**または**constexpr**式である必要があります。 次のように使用します。

```cpp
MyArray<MyClass*, 10> arr;
```

ポインターや参照を含むその他の種類の値は、非型パラメーターとして渡すことができます。 たとえば、関数オブジェクトまたは関数オブジェクトへのポインターを渡して、テンプレートコード内の一部の操作をカスタマイズできます。

### <a name="type-deduction-for-non-type-template-parameters"></a>非型テンプレートパラメーターの型推論

Visual Studio 2017 以降では、推測で宣言されている非型テンプレート引数の型は、 **/std: c++ 17**モードでコンパイラによって次**のようになります。**

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

## <a id="template_parameters"></a>テンプレートパラメーターとしてのテンプレート

テンプレートは、テンプレートパラメーターにすることができます。 この例では、MyClass2 には、typename パラメーター *T*とテンプレートパラメーター *Arr*の2つのテンプレートパラメーターがあります。

```cpp
template<typename T, template<typename U, int I> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
    U u; //Error. U not in scope
};
```

*Arr*パラメーター自体には本体がないため、パラメーター名は必要ありません。 実際には、`MyClass2`の本文内から*Arr*の typename またはクラスパラメーター名を参照するとエラーになります。 このため、次の例に示すように、 *Arr*の型パラメーター名を省略できます。

```cpp
template<typename T, template<typename, int> class Arr>
class MyClass2
{
    T t; //OK
    Arr<T, 10> a;
};
```

## <a name="default-template-arguments"></a>既定のテンプレート引数

クラステンプレートと関数テンプレートには、既定の引数を指定できます。 テンプレートに既定の引数がある場合は、使用時にそのままにしておくことができます。 たとえば、std:: vector テンプレートには、アロケーターの既定の引数があります。

```cpp
template <class T, class Allocator = allocator<T>> class vector;
```

ほとんどの場合、既定の std:: アロケータークラスが許容されるため、次のようなベクターを使用します。

```cpp
vector<int> myInts;
```

ただし、必要に応じて、次のようにカスタムアロケーターを指定することもできます。

```cpp
vector<int, MyAllocator> ints;
```

テンプレート引数が複数ある場合、最初の既定の引数の後は、すべての引数に既定の引数が必要です。

パラメーターがすべて既定値であるテンプレートを使用する場合は、空の山かっこを使用します。

```cpp
template<typename A = int, typename B = double>
class Bar
{
    //...
};
...
int main()
{
    Bar<> bar; // use all default type arguments
}
```

## <a name="template-specialization"></a>テンプレートの特殊化

場合によっては、テンプレートで任意の型に対してまったく同じコードを定義することはできません。 たとえば、型引数がポインター、std:: wstring、または特定の基底クラスから派生した型である場合にのみ実行されるコードパスを定義できます。  そのような場合は、特定の種類のテンプレートの*特殊化*を定義できます。 ユーザーがその型を使用してテンプレートをインスタンス化すると、コンパイラは特殊化を使用してクラスを生成し、それ以外のすべての型については、コンパイラがより一般的なテンプレートを選択します。 すべてのパラメーターが特殊化されている特殊化は*完全な特殊化*です。 一部のパラメーターのみが特殊化されている場合は、*部分的特殊化*と呼ばれます。

```cpp
template <typename K, typename V>
class MyMap{/*...*/};

// partial specialization for string keys
template<typename V>
class MyMap<string, V> {/*...*/};
...
MyMap<int, MyClass> classes; // uses original template
MyMap<string, MyClass> classes2; // uses the partial specialization
```

テンプレートは、特化された各型パラメーターが一意である限り、任意の数の特殊化を持つことができます。 クラステンプレートのみが部分的に特殊化されている場合があります。 テンプレートのすべての完全な特殊化と部分的特殊化は、元のテンプレートと同じ名前空間で宣言する必要があります。

詳細については、「[テンプレートの特殊化](../cpp/template-specialization-cpp.md)」を参照してください。