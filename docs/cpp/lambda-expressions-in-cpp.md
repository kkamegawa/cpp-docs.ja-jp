---
title: C++ でのラムダ式
ms.date: 11/19/2018
helpviewer_keywords:
- lambda expressions [C++]
- lambda expressions [C++], overview
- lambda expressions [C++], vs. function objects
ms.assetid: 713c7638-92be-4ade-ab22-fa33417073bf
ms.openlocfilehash: 9ebe4fec06996e908c619b6ac14af098b1c07a01
ms.sourcegitcommit: fe1e21df175cd004d21c6e4659082efceb649a8b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53978310"
---
# <a name="lambda-expressions-in-c"></a>C++ でのラムダ式

C++ 11 以降では、ラムダ式: と呼ばれます、*ラムダ*— は無名関数オブジェクトを定義するのに便利です (、*クロージャ*) 呼び出される、または引数として渡された場所で関数。 一般に、ラムダは、アルゴリズムまたは非同期のメソッドに渡される数行のコードをカプセル化するために使用されます。 ここでは、ラムダとはどのようなものかを定義して他のプログラミング手法と比較した上で、その利点を説明し、基本的な例を示します。

## <a name="related-topics"></a>関連トピック

- [Vs. function オブジェクトのラムダ式](lambda-expression-syntax.md)
- [ラムダ式の操作](examples-of-lambda-expressions.md)
- [constexpr ラムダ式](lambda-expressions-constexpr.md)

## <a name="parts-of-a-lambda-expression"></a>ラムダ式のパーツ

ISO C++ 標準では、`std::sort()` 関数の 3 番目の引数として渡される単純なラムダを示しています。

```cpp
#include <algorithm>
#include <cmath>

void abssort(float* x, unsigned n) {
    std::sort(x, x + n,
        // Lambda expression begins
        [](float a, float b) {
            return (std::abs(a) < std::abs(b));
        } // end of lambda expression
    );
}
```

次の図は、ラムダのパーツを示しています。

![ラムダ式の構造体要素](../cpp/media/lambdaexpsyntax.png "ラムダ式の構造要素")

1. *capture 句*(とも呼ばれる、*ラムダ導入子*C++ 仕様です)。

1. *パラメーター リスト*(省略可能)。 (別名、*ラムダ宣言子*)

1. *変更可能な指定*(省略可能)。

1. *例外仕様*(省略可能)。

1. *後続の戻り値の型*(省略可能)。

1. *ラムダ式の本体*します。

### <a name="capture-clause"></a>capture 句

ラムダの本体で新しい変数を導入できます (で**c++ 14**) とことも、アクセス、または*キャプチャ*、周辺のスコープから変数。 ラムダは capture 句で始まります (*ラムダ導入子*標準構文内)、どの変数をキャプチャして、キャプチャは、値渡しまたは参照渡しかどうかを指定します。 アンパサンド (`&`) プレフィックス付きの変数は参照でアクセスされ、アンパサンド プレフィックスなしの変数は値でアクセスされます。

空のキャプチャ句 `[ ]` は、ラムダ式の本体が外側のスコープ内の変数にアクセスしないことを示します。

既定のキャプチャ モードを使用することができます (*キャプチャ既定*標準構文内) を任意の外部のラムダで参照されている変数をキャプチャする方法を示すために:`[&]`によってを参照するすべての変数をキャプチャする手段参照、および`[=]`値によってキャプチャされることを意味します。 既定のキャプチャ モードを使用してから、特定の変数には明示的に反対のモードを指定することができます。 たとえば、ラムダ式の本体が参照によって外部変数 `total` にアクセスし、値によって外部変数 `factor` にアクセスする場合、次の capture 句は同じ結果になります。

```cpp
[&total, factor]
[factor, &total]
[&, factor]
[factor, &]
[=, &total]
[&total, =]
```

既定のキャプチャを使用する場合、ラムダで記述されている変数のみがキャプチャされます。

Capture 句には、キャプチャ既定値が含まれている場合`&`、されません`identifier`で、`capture`の capture 句には、フォームを持つことができます`& identifier`します。 同様に、capture 句には、キャプチャ既定値が含まれている場合`=`、されません`capture`の capture 句には、フォームを持つことができます`= identifier`します。 識別子または**この**を capture 句で複数回表示されることはできません。 次のコードでは、そのいくつかの例を示しています。

```cpp
struct S { void f(int i); };

void S::f(int i) {
    [&, i]{};      // OK
    [&, &i]{};     // ERROR: i preceded by & when & is the default
    [=, this]{};   // ERROR: this when = is the default
    [=, *this]{ }; // OK: captures this by value. See below.
    [i, i]{};      // ERROR: i repeated
}
```

これで示すように、後ろに省略記号のキャプチャがパック展開では、[可変個引数テンプレート](../cpp/ellipses-and-variadic-templates.md)例。

```cpp
template<class... Args>
void f(Args... args) {
    auto x = [args...] { return g(args...); };
    x();
}
```

クラスのメソッドの本体でラムダ式を使用するには**この**外側のクラスのメソッドとデータ メンバーにアクセスを提供する capture 句へのポインター。

**Visual Studio 2017 バージョン 15.3 以降**(で使用可能な[/std:c + + 17](../build/reference/std-specify-language-standard-version.md))。**この**ポインターを指定することで値によってキャプチャされる可能性があります`*this`capture 句でします。 値でキャプチャすることで全体*クロージャ*、無名関数オブジェクトをその encapulates ラムダ式は、ラムダが呼び出されるすべての呼び出しサイトにコピーされます。 値によってキャプチャは、ラムダは、NUMA などの特定のハードウェア アーキテクチャで特に並列または非同期の操作で実行する場合に便利です。

クラスのメソッドをラムダ式を使用する方法を示す例を参照してください"の例。使用して、メソッドのラムダ式"で[ラムダ式の例](../cpp/examples-of-lambda-expressions.md)します。

capture 句を使用するとき、特にマルチスレッドでラムダを使用するときは、次の重要点に注意することをお勧めします。

- 参照キャプチャは外部の変数を変更するために使用できますが、値キャプチャはその目的には使用できません (**変更可能な**でコピーを変更しますが、元ではありません)。

- 参照キャプチャでは更新が外部の変数に反映されますが、値キャプチャでは反映されません。

- 参照キャプチャは有効期間に依存しますが、値キャプチャは依存しません。 これは、ラムダを非同期的に実行する場合は特に重要です。 非同期のラムダで参照によってローカルをキャプチャする場合は、そのローカルは非常に高い可能性でラムダが実行するまでになくなり、結果として実行時にアクセス違反となります。

### <a name="generalized-capture-c-14"></a>汎用化されたキャプチャ (C++ 14)

C++ 14 では、capture 句にある新しい変数がラムダ関数の外側のスコープに存在する必要なしに、この変数を導入し、初期化することができます。 初期化は、任意の式として表現できます。新しい変数の型は、式によって生成される型から推測されます。 この機能の利点の 1 つは、C++ 14 では移動のみの変数 (std::unique_ptr) を周辺のスコープからキャプチャして、ラムダで使用できることです。

```cpp
pNums = make_unique<vector<int>>(nums);
//...
      auto a = [ptr = move(pNums)]()
        {
           // use ptr
        };
```

### <a name="parameter-list"></a>パラメーター リスト

変数をキャプチャするだけでなく、ラムダは入力パラメーターを受け入れることができます。 パラメーター リスト (*ラムダ宣言子*標準構文内) は省略可能で、ほとんどの面での 関数のパラメーター リストと似ています。

```cpp
auto y = [] (int first, int second)
{
    return first + second;
};
```

**C++ 14**パラメーターの型がジェネリックの場合は、型指定子として auto キーワードを使用できます。 これにより、コンパイラにテンプレートとして関数呼び出し演算子を作成するように指示します。 パラメーター リストの auto の各インスタンスは、別個の型パラメーターと同等です。

```cpp
auto y = [] (auto first, auto second)
{
    return first + second;
};
```

ラムダ式は、引数として別のラムダ式を受け取ることができます。 詳細については、トピックの「上位ラムダ式」を参照してください。[ラムダ式の例](../cpp/examples-of-lambda-expressions.md)します。

パラメーター リストは省略可能であるため、ラムダ式に引数を渡さないし、そのラムダ宣言子が含まれていない場合、空のかっこを省略できます*例外仕様*、 *後続の戻り値の型*、または**変更可能な**します。

### <a name="mutable-specification"></a>変更可能な指定

通常、ラムダの関数呼び出し演算子は const 値ずつがの使用、**変更可能な**アウトこのキーワードをキャンセルします。これによりデータ メンバーが変更可能になることはありません。 mutable の指定により、ラムダ式の本体で値キャプチャされる変数を変更できるようになります。 この記事の後半の例のいくつかの方法を使用して**変更可能な**します。

### <a name="exception-specification"></a>例外の指定

`noexcept` 例外の指定を使用して、ラムダ式が例外をスローしないことを示すことができます。 Visual C コンパイラが警告を生成する通常の関数として[C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)ラムダ式を宣言する場合、`noexcept`例外仕様とラムダ式の本体は、ここに示すように、例外がスローします。

```cpp
// throw_lambda_expression.cpp
// compile with: /W4 /EHsc
int main() // C4297 expected
{
   []() noexcept { throw 5; }();
}
```

詳細については、次を参照してください。[例外の仕様 (スロー)](../cpp/exception-specifications-throw-cpp.md)します。

### <a name="return-type"></a>戻り値の型

ラムダ式の戻り値の型は自動的に推測されます。 使用する必要はありません、[自動](../cpp/auto-cpp.md)キーワードを指定しない限り、*後続の戻り値の型*します。 *後続の戻り値の型*通常のメソッドまたは関数の戻り値の型の部分に似ています。 ただし、戻り値の型はパラメーター リストに従い、戻り値の型の前に trailing-return-type キーワード `->` を含める必要があります。

ラムダ式の本体に return ステートメントが 1 つだけ含まれるか、ラムダ式が値を返さない場合は、ラムダ式の return-type 部分を省略できます。 ラムダの本体が単一の return ステートメントで構成される場合、コンパイラは return 式の型から戻り値の型を推測します。 それ以外の場合、コンパイラはする戻り値の型を推測**void**します。 この原理を説明する次のコード例について考えてみましょう。

```cpp
auto x1 = [](int i){ return i; }; // OK: return type is int
auto x2 = []{ return{ 1, 2 }; };  // ERROR: return type is void, deducing
                                  // return type from braced-init-list is not valid
```

ラムダ式は、戻り値として別のラムダ式を作成できます。 詳細については、「上位ラムダ式」を参照してください[ラムダ式の例](../cpp/examples-of-lambda-expressions.md)します。

### <a name="lambda-body"></a>ラムダ式の本体

ラムダ式の本体 (*複合ステートメント*標準構文内) のラムダ式何でも使用できますが、通常のメソッドまたは関数の本文に含めることができます。 通常の関数の本体もラムダ式の本体も次の種類の変数にアクセスできます。

- 前に説明したように、外側のスコープから変数がキャプチャされました。

- パラメーター

- ローカル宣言変数

- クラス内で宣言されている場合、データ メンバーをクラスおよび**この**がキャプチャ

- 静的ストレージ存続期間の任意の変数 (たとえば、グローバル変数)

次の例には、変数 `n` を明示的に値でキャプチャし、変数 `m` を暗黙的に参照でキャプチャするラムダ式が含まれています。

```cpp
// captures_lambda_expression.cpp
// compile with: /W4 /EHsc
#include <iostream>
using namespace std;

int main()
{
   int m = 0;
   int n = 0;
   [&, n] (int a) mutable { m = ++n + a; }(4);
   cout << m << endl << n << endl;
}
```

```Output
5
0
```

変数 `n` は値でキャプチャされるため、ラムダ式への呼び出しの後も値は `0` のまま残ります。 **変更可能な**仕様により`n`ラムダ内で変更します。

ラムダ式は自動ストレージ存続期間がある変数のみキャプチャできますが、ラムダ式の本体では静的ストレージ存続期間がある変数を使用できます。 次の例では、`generate` 関数とラムダ式を使用して、`vector` オブジェクトの各要素に値を代入します。 ラムダ式は、静的変数を変更して次の要素の値を生成します。

```cpp
void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}
```

詳細については、次を参照してください。[生成](../standard-library/algorithm-functions.md#generate)します。

次のコード例から前の例では、関数を使用して、C++ 標準ライブラリ アルゴリズムを使用するラムダ式の例を追加`generate_n`します。 このラムダ式は `vector` オブジェクトの要素を前の 2 つの要素の合計に代入します。 **変更可能な**キーワードを使用すると、ラムダ式の本体は、外部変数のコピーを変更できるように`x`と`y`ラムダ式が値でキャプチャします。 ラムダ式は元の変数 `x` および `y` を値でキャプチャするため、それらの値はラムダの実行後も `1` のまま残ります。

```cpp
// compile with: /W4 /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

void fillVector(vector<int>& v)
{
    // A local static variable.
    static int nextValue = 1;

    // The lambda expression that appears in the following call to
    // the generate function modifies and uses the local static
    // variable nextValue.
    generate(v.begin(), v.end(), [] { return nextValue++; });
    //WARNING: this is not thread-safe and is shown for illustration only
}

int main()
{
    // The number of elements in the vector.
    const int elementCount = 9;

    // Create a vector object with each element set to 1.
    vector<int> v(elementCount, 1);

    // These variables hold the previous two elements of the vector.
    int x = 1;
    int y = 1;

    // Sets each element in the vector to the sum of the
    // previous two elements.
    generate_n(v.begin() + 2,
        elementCount - 2,
        [=]() mutable throw() -> int { // lambda is the 3rd parameter
        // Generate current value.
        int n = x + y;
        // Update previous two values.
        x = y;
        y = n;
        return n;
    });
    print("vector v after call to generate_n() with lambda: ", v);

    // Print the local variables x and y.
    // The values of x and y hold their initial values because
    // they are captured by value.
    cout << "x: " << x << " y: " << y << endl;

    // Fill the vector with a sequence of numbers
    fillVector(v);
    print("vector v after 1st call to fillVector(): ", v);
    // Fill the vector with the next sequence of numbers
    fillVector(v);
    print("vector v after 2nd call to fillVector(): ", v);
}
```

```Output
vector v after call to generate_n() with lambda: 1 1 2 3 5 8 13 21 34
x: 1 y: 1
vector v after 1st call to fillVector(): 1 2 3 4 5 6 7 8 9
vector v after 2nd call to fillVector(): 10 11 12 13 14 15 16 17 18
```

詳細については、次を参照してください。 [generate_n](../standard-library/algorithm-functions.md#generate_n)します。

## <a name="constexpr-lambda-expressions"></a>constexpr ラムダ式

**Visual Studio 2017 バージョン 15.3 以降**(で使用可能な[/std:c + + 17](../build/reference/std-specify-language-standard-version.md))。ラムダ式として宣言することがあります`constexpr`または定数式の中でキャプチャまたは導入される各データ メンバーの初期化が許可されている場合、定数式で使用します。

```cpp
    int y = 32;
    auto answer = [y]() constexpr
    {
        int x = 10;
        return y + x;
    };

    constexpr int Increment(int n)
    {
        return [n] { return n + 1; }();
    }
```

ラムダは暗黙的に`constexpr`その結果の要件を満たしている場合、`constexpr`関数。

```cpp
    auto answer = [](int n)
    {
        return 32 + n;
    };

    constexpr int response = answer(10);
```

ラムダが暗黙的または明示的に場合`constexpr`、関数ポインターへの変換を生成、`constexpr`関数。

```cpp
    auto Increment = [](int n)
    {
        return n + 1;
    };

    constexpr int(*inc)(int) = Increment;
```

## <a name="microsoft-specific"></a>Microsoft 固有

ラムダは、次の共通言語ランタイム (CLR) によって管理されるエンティティでサポートされていません: **ref クラス**、 **ref 構造体**、**値クラス**、または**値構造体**.

など、Microsoft 固有の修飾子を使用している場合[_ _declspec](../cpp/declspec.md)、ラムダ式に挿入することができますの直後に、 `parameter-declaration-clause`: 例。

```cpp
auto Sqr = [](int t) __declspec(code_seg("PagedMem")) -> int { return t*t; };
```

修飾子はラムダでサポートされているかどうかを判断するでに関する記事を参照してください。、 [Microsoft 固有の修飾子](../cpp/microsoft-specific-modifiers.md)ドキュメントのセクション。

C++ 11 標準ラムダ機能、に加えては、Visual Studio は、任意の呼び出し規約を使用して関数ポインターへのオムニに変換できるは、ステートレス ラムダをサポートします。

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[C++ 標準ライブラリの関数オブジェクト](../standard-library/function-objects-in-the-stl.md)<br/>
[関数呼び出し](../cpp/function-call-cpp.md)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)
