---
title: 右辺値参照宣言子:&amp;&amp;
ms.date: 11/04/2016
f1_keywords:
- '&&'
helpviewer_keywords:
- '&& rvalue reference declarator'
ms.assetid: eab0ce3a-c5a3-4992-aa70-6a8ab1f7491d
ms.openlocfilehash: d6aa6aa9caed77f92b3b183cc49c63aaaa6c724f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498561"
---
# <a name="rvalue-reference-declarator-ampamp"></a>右辺値参照宣言子:&amp;&amp;

右辺値の式への参照を保持します。

## <a name="syntax"></a>構文

```
type-id && cast-expression
```

## <a name="remarks"></a>Remarks

右辺値参照を使用すると、左辺値を右辺値と区別できます。 左辺値参照と右辺値参照は構文的および意味的に似ていますが、従う規則が少し異なります。 左辺値と右辺値の詳細については、「[左辺値と右辺値](../cpp/lvalues-and-rvalues-visual-cpp.md)」を参照してください。 左辺値参照の詳細については、「[左辺値参照宣言子: &](../cpp/lvalue-reference-declarator-amp.md)」を参照してください。

以下のセクションでは、右辺値参照が*移動セマンティクス*と*完全転送*の実装をサポートする方法について説明します。

## <a name="move-semantics"></a>移動セマンティクス

右辺値参照は、アプリケーションのパフォーマンスを大幅に向上させることができる*移動セマンティクス*の実装をサポートします。 移動セマンティクスにより、オブジェクト間でリソース (動的に割り当てられるメモリなど) を転送するコードを記述できます。 移動セマンティクスが機能するのは、プログラム内の他の場所からは参照できない一時オブジェクトからリソースを転送できるようになるためです。

移動セマンティクスを実装するには、通常、移動*コンストラクター*と、必要に応じて移動代入演算子 (**operator =** ) をクラスに提供します。 その後は、ソースが右辺値であるコピーおよび代入演算では、移動セマンティクスが自動的に利用されます。 既定のコピー コンストラクターとは異なり、コンパイラは既定の移動コンストラクターを提供しません。 移動コンストラクターを記述する方法と、移動コンストラクターをアプリケーションで使用する方法の詳細については、「[移動コンストラクターとC++移動代入演算子 ()](../cpp/move-constructors-and-move-assignment-operators-cpp.md)」を参照してください。

移動セマンティクスを活用するために、通常の関数と演算子をオーバーロードすることもできます。 Visual Studio 2010 では、標準ライブラリC++への移動セマンティクスが導入されています。 たとえば、`string` クラスは、移動セマンティクスを実行する操作を実装しています。 複数の文字列を連結し、結果を出力する次の例を考えます。

```cpp
// string_concatenation.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

int main()
{
   string s = string("h") + "e" + "ll" + "o";
   cout << s << endl;
}
```

Visual Studio 2010 より前では、 **operator +** を呼び出すたびに、 `string`新しい一時オブジェクト (右辺値) が割り当てられ、返されます。 **演算子 +** は、ソース文字列が左辺値または右辺値かどうかを認識しないため、1つの文字列を他の文字列に追加することはできません。 ソース文字列が両方とも左辺値である場合、それらのソース文字列はプログラム内の他の場所で参照されている場合があるため、変更しないでください。 右辺値参照を使用することにより、 **operator +** を変更して右辺値を取ることができます。これは、プログラム内の他の場所では参照できません。 したがって、 **operator +** は、1つの文字列を別の文字列に追加できるようになりました。 これによって、`string` クラスが実行する必要がある動的メモリ割り当ての数を大幅に減らすことができます。 クラスの`string`詳細については、「 [basic_string クラス](../standard-library/basic-string-class.md)」を参照してください。

また、コンパイラが戻り値の最適化 (RVO) または名前付き戻り値の最適化 (NRVO) を使用できない場合に、移動セマンティクスが役立ちます。 このような場合、型が移動コンストラクターを定義していれば、コンパイラはその移動コンストラクターを呼び出します。 名前付き戻り値の最適化の詳細については、「 [Visual Studio 2005 での名前付きの戻り値の最適化](/previous-versions/ms364057(v=vs.80))」を参照してください。

移動セマンティクスをより深く理解するために、`vector` オブジェクトに要素を挿入する例について考えてみましょう。   `vector` オブジェクトの容量が超過した場合、`vector` オブジェクトは、挿入された要素の領域を作成するために、各要素にメモリを再割り当てして、別のメモリ位置に各要素をコピーする必要があります。 挿入操作が要素をコピーするときは、新しい要素を作成し、コピー コンストラクターを呼び出して前の要素から新しい要素にデータをコピーした後、前の要素を破棄します。 移動セマンティクスを使用すると、負荷の高いメモリ割り当てとコピー操作を実行する必要がなく、オブジェクトを直接移動できます。

  `vector` の例で移動セマンティクスを利用するには、オブジェクト間でデータを移動する移動コンストラクターを記述します。

Visual Studio 2010 のC++標準ライブラリへの移動セマンティクスの導入の詳細については、「 [ C++標準ライブラリ](../standard-library/cpp-standard-library-reference.md)」を参照してください。

## <a name="perfect-forwarding"></a>完全転送

完全転送により、オーバーロード関数の必要性が低くなり、転送の問題を回避できます。 *転送の問題*は、パラメーターとして参照を受け取るジェネリック関数を記述し、それらのパラメーターを別の関数に渡す (または*転送*する) ときに発生する可能性があります。 たとえば、ジェネリック関数が `const T&` 型のパラメーターを受け取る場合、呼び出される関数はそのパラメーターの値を変更できません。 ジェネリック関数が `T&` 型のパラメーターを受け取る場合は、右辺値 (一時的なオブジェクトや整数リテラルなど) を使用して関数を呼び出すことはできません。

通常、この問題を解決するには、各パラメーターに `T&` と `const T&` の両方を受け取る、ジェネリック関数のオーバーロードされたバージョンを用意する必要があります。 その結果、オーバーロードされた関数の数は、パラメーターの数と共に指数関数的に増加します。 右辺値の参照を使用すると、1 つのバージョンの関数を作成し、任意の引数を受け取って別の関数に転送して、その関数が直接呼び出されたかのようにすることができます。

  `W`、`X`、`Y`、および `Z` の 4 つの型を宣言する次の例を考えます。 各型のコンストラクターは、パラメーターとして**const**および非**定数**左辺値参照の異なる組み合わせを使用します。

```cpp
struct W
{
   W(int&, int&) {}
};

struct X
{
   X(const int&, int&) {}
};

struct Y
{
   Y(int&, const int&) {}
};

struct Z
{
   Z(const int&, const int&) {}
};
```

オブジェクトを生成するジェネリック関数を記述するとします。 次の例は、この関数を記述する方法の 1 つを示しています。

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1& a1, A2& a2)
{
   return new T(a1, a2);
}
```

次の例は、`factory` 関数への有効な呼び出しを示しています。

```cpp
int a = 4, b = 5;
W* pw = factory<W>(a, b);
```

ただし、次の例には `factory` 関数の有効な呼び出しは含まれていません。`factory` はパラメーターとして変更可能な左辺値の参照を受け取りますが、右辺値を使用して呼び出されているためです。

```cpp
Z* pz = factory<Z>(2, 2);
```

通常、この問題を解決するには、`factory` および `A&` パラメーターの任意の組み合わせで、`const A&` 関数のオーバーロードされたバージョンを作成する必要があります。 右辺値参照を使用すると、次の例に示すように、1 つのバージョンの `factory` 関数を作成できます。

```cpp
template <typename T, typename A1, typename A2>
T* factory(A1&& a1, A2&& a2)
{
   return new T(std::forward<A1>(a1), std::forward<A2>(a2));
}
```

この例では、`factory` 関数へのパラメーターとして、右辺値参照を使用しています。 [Std:: forward](../standard-library/utility-functions.md#forward)関数の目的は、ファクトリ関数のパラメーターをテンプレートクラスのコンストラクターに転送することです。

次の例は、`main`、`factory`、`W`、および `X` クラスのインスタンスを作成するために、変更済みの `Y` 関数を使用する `Z` 関数を示します。 変更された `factory` 関数は、そのパラメーター (左辺値または右辺値) を適切なクラス コンストラクターに転送します。

```cpp
int main()
{
   int a = 4, b = 5;
   W* pw = factory<W>(a, b);
   X* px = factory<X>(2, b);
   Y* py = factory<Y>(a, 2);
   Z* pz = factory<Z>(2, 2);

   delete pw;
   delete px;
   delete py;
   delete pz;
}
```

## <a name="additional-properties-of-rvalue-references"></a>右辺値参照の追加プロパティ

**関数をオーバーロードして、左辺値参照と右辺値参照を受け取ることができます。**

関数をオーバーロードして**定数**の左辺値参照または右辺値参照を取得することにより、変更できないオブジェクト (lvalues) と変更可能な一時的な値 (右辺値) を区別するコードを記述できます。 オブジェクトが**const**としてマークされていない場合は、右辺値参照を受け取る関数にオブジェクトを渡すことができます。 次の例は、左辺値参照と右辺値参照を受け取るためにオーバーロードされた関数 `f` を示しています。   `main` 関数は、左辺値と右辺値の両方で `f` を呼び出します。

```cpp
// reference-overload.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void f(const MemoryBlock&)
{
   cout << "In f(const MemoryBlock&). This version cannot modify the parameter." << endl;
}

void f(MemoryBlock&&)
{
   cout << "In f(MemoryBlock&&). This version can modify the parameter." << endl;
}

int main()
{
   MemoryBlock block;
   f(block);
   f(MemoryBlock());
}
```

この例を実行すると、次の出力が生成されます。

```Output
In f(const MemoryBlock&). This version cannot modify the parameter.
In f(MemoryBlock&&). This version can modify the parameter.
```

この例では、`f` の最初の呼び出しで、引数としてローカル変数 (左辺値) を渡します。   `f` の 2 番目の呼び出しでは、引数として一時オブジェクトを渡します。 一時オブジェクトはプログラムの他の場所で参照できないため、呼び出しは右辺値の参照を受け取る、`f` のオーバーロードされたバージョンにバインドされます。そのため、オブジェクトは自由に変更できます。

**コンパイラは、右辺値参照を左辺値として処理し、名前のない右辺値参照を右辺値として扱います。**

右辺値参照をパラメーターとして受け取る関数を記述すると、そのパラメーターは関数本体で左辺値として扱われます。 名前付きオブジェクトはプログラムの複数の部分から参照できるため、コンパイラは名前付きの右辺値を左辺値として処理します。プログラムの複数の部分にオブジェクト リソースの変更または削除を許可することは危険です。 たとえば、プログラム内の複数の部分で同じオブジェクトからリソースを転送しようとすると、リソースが正常に転送されるのは最初の部分だけです。

次の例は、左辺値参照と右辺値参照を受け取るためにオーバーロードされた関数 `g` を示しています。 関数 `f` は右辺値参照をパラメーター (名前付きの右辺値参照) として受け取り、右辺値参照 (名前のない右辺値参照) を返します。   `g` からの `f` の呼び出しでは、`g` の本体がパラメーターを左辺値として処理するので、オーバーロードの解決は、左辺値参照を受け取る `f` のバージョンを選択します。   `g` からの `main` の呼び出しでは、`g` が右辺値参照を返すので、オーバーロードの解決は、右辺値参照を受け取る `f` のバージョンを選択します。

```cpp
// named-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

MemoryBlock&& f(MemoryBlock&& block)
{
   g(block);
   return move(block);
}

int main()
{
   g(f(MemoryBlock()));
}
```

この例を実行すると、次の出力が生成されます。

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

この例では、`main` 関数は右辺値を `f` に渡します。   `f` の本体は、名前付きパラメーターを左辺値として処理します。   `f` からの `g` の呼び出しにより、パラメーターは左辺値参照 (`g` の最初のオーバーロードされたバージョン) にバインドされます。

- **左辺値を右辺値参照にキャストできます。**

C++標準ライブラリ[std:: move](../standard-library/utility-functions.md#move)関数を使用すると、オブジェクトをそのオブジェクトへの右辺値参照に変換できます。 また、次の例に示すように、 **static_cast**キーワードを使用して左辺値を右辺値参照にキャストすることもできます。

```cpp
// cast-reference.cpp
// Compile with: /EHsc
#include <iostream>
using namespace std;

// A class that contains a memory resource.
class MemoryBlock
{
   // TODO: Add resources for the class here.
};

void g(const MemoryBlock&)
{
   cout << "In g(const MemoryBlock&)." << endl;
}

void g(MemoryBlock&&)
{
   cout << "In g(MemoryBlock&&)." << endl;
}

int main()
{
   MemoryBlock block;
   g(block);
   g(static_cast<MemoryBlock&&>(block));
}
```

この例を実行すると、次の出力が生成されます。

```cpp
In g(const MemoryBlock&).
In g(MemoryBlock&&).
```

**関数テンプレートは、テンプレート引数の型を推測し、参照の折りたたみ規則を使用します。**

パラメーターを別の関数に渡す (または*転送*する) 関数テンプレートを記述するのが一般的です。 右辺値参照を受け取る関数テンプレートに対して、テンプレート型推論がどのように機能するかを理解しておくことは重要です。

関数の引数が右辺値の場合、コンパイラは引数が右辺値参照であると推測します。 たとえば、パラメーターとして `X` 型を受け取るテンプレート関数に、`T&&` 型のオブジェクトへの右辺値参照を渡すと、テンプレート引数の推論は `T` が `X` であると推測します。 したがって、パラメーターの型は `X&&` になります。 関数の引数が左辺値または**const**左辺値の場合、コンパイラはその型を左辺値参照または**const**左辺値参照として推測します。

次の例では、1 つの構造テンプレートを宣言し、それをさまざまな参照型に特化します。   `print_type_and_value` 関数は、パラメーターとして右辺値参照を取り、`S::print` メソッドの適切な特殊化バージョンにそれを転送します。   `main` 関数は `S::print` メソッドを呼び出すさまざまな方法を示します。

```cpp
// template-type-deduction.cpp
// Compile with: /EHsc
#include <iostream>
#include <string>
using namespace std;

template<typename T> struct S;

// The following structures specialize S by
// lvalue reference (T&), const lvalue reference (const T&),
// rvalue reference (T&&), and const rvalue reference (const T&&).
// Each structure provides a print method that prints the type of
// the structure and its parameter.

template<typename T> struct S<T&> {
   static void print(T& t)
   {
      cout << "print<T&>: " << t << endl;
   }
};

template<typename T> struct S<const T&> {
   static void print(const T& t)
   {
      cout << "print<const T&>: " << t << endl;
   }
};

template<typename T> struct S<T&&> {
   static void print(T&& t)
   {
      cout << "print<T&&>: " << t << endl;
   }
};

template<typename T> struct S<const T&&> {
   static void print(const T&& t)
   {
      cout << "print<const T&&>: " << t << endl;
   }
};

// This function forwards its parameter to a specialized
// version of the S type.
template <typename T> void print_type_and_value(T&& t)
{
   S<T&&>::print(std::forward<T>(t));
}

// This function returns the constant string "fourth".
const string fourth() { return string("fourth"); }

int main()
{
   // The following call resolves to:
   // print_type_and_value<string&>(string& && t)
   // Which collapses to:
   // print_type_and_value<string&>(string& t)
   string s1("first");
   print_type_and_value(s1);

   // The following call resolves to:
   // print_type_and_value<const string&>(const string& && t)
   // Which collapses to:
   // print_type_and_value<const string&>(const string& t)
   const string s2("second");
   print_type_and_value(s2);

   // The following call resolves to:
   // print_type_and_value<string&&>(string&& t)
   print_type_and_value(string("third"));

   // The following call resolves to:
   // print_type_and_value<const string&&>(const string&& t)
   print_type_and_value(fourth());
}
```

この例を実行すると、次の出力が生成されます。

```cpp
print<T&>: first
print<const T&>: second
print<T&&>: third
print<const T&&>: fourth
```

  `print_type_and_value` 関数の各呼び出しを解決するため、コンパイラは最初にテンプレート引数の推論を実行します。 次に、コンパイラは、推測されたテンプレート引数にパラメーター型を置き換えるときに、参照縮小規則を適用します。 たとえば、`s1` 関数にローカル変数 `print_type_and_value` を渡すと、コンパイラで次の関数シグネチャが生成されます。

```cpp
print_type_and_value<string&>(string& && t)
```

コンパイラは、参照縮小規則を使用して以下のようにシグネチャを減らします。

```cpp
print_type_and_value<string&>(string& t)
```

このバージョンの `print_type_and_value` 関数は、`S::print` メソッドの正しい特化されたバージョンにパラメーターを転送します。

次の表は、テンプレートの引数の型を推論するときの参照縮小規則をまとめたものです。

|||
|-|-|
|展開された型|縮小された型|
|`T& &`|`T&`|
|`T& &&`|`T&`|
|`T&& &`|`T&`|
|`T&& &&`|`T&&`|

テンプレート引数の推論は、完全転送を実装するうえでの重要な要素です。 このトピックの前の方の「完全転送」のセクションでは、完全転送についてより詳細に説明しています。

## <a name="summary"></a>まとめ

右辺値参照は、左辺値を右辺値と区別します。 不要なメモリ割り当てとコピー操作の必要性をなくすことで、アプリケーションのパフォーマンスを向上させることができます。 任意の引数を受け取って別の関数に転送し、他の関数が直接呼び出されたかのようにする、1 つのバージョンの関数を記述することもできます。

## <a name="see-also"></a>関連項目

[単項演算子を含む式](../cpp/expressions-with-unary-operators.md)<br/>
[左辺値参照宣言子: &](../cpp/lvalue-reference-declarator-amp.md)<br/>
[左辺値と右辺値](../cpp/lvalues-and-rvalues-visual-cpp.md)<br/>
[移動コンストラクターと移動代入演算子 (C++)](../cpp/move-constructors-and-move-assignment-operators-cpp.md)<br/>
[.NET 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
