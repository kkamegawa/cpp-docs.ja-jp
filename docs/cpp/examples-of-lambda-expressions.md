---
title: ラムダ式の例
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++], examples
ms.assetid: 52506b15-0771-4190-a966-2f302049ca86
ms.openlocfilehash: f9f2c3e014e44c9f6a9ce10dd8388a1578ba3987
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222093"
---
# <a name="examples-of-lambda-expressions"></a>ラムダ式の例

この記事では、プログラムでラムダ式を使用する方法を示します。 ラムダ式の概要については、次を参照してください。[ラムダ式](../cpp/lambda-expressions-in-cpp.md)します。 ラムダ式の構造の詳細については、次を参照してください。[ラムダ式の構文](../cpp/lambda-expression-syntax.md)します。

##  <a name="declaringLambdaExpressions"></a> ラムダ式の宣言

### <a name="example-1"></a>例 1

ラムダ式が入力されているためにを割り当てることができます、**auto**変数または、[関数](../standard-library/function-class.md)オブジェクトを次に示します。

### <a name="code"></a>コード

```cpp
// declaring_lambda_expressions1.cpp
// compile with: /EHsc /W4
#include <functional>
#include <iostream>

int main()
{

    using namespace std;

    // Assign the lambda expression that adds two numbers to an auto variable.
    auto f1 = [](int x, int y) { return x + y; };

    cout << f1(2, 3) << endl;

    // Assign the same lambda expression to a function object.
    function<int(int, int)> f2 = [](int x, int y) { return x + y; };

    cout << f2(3, 4) << endl;
}
```

### <a name="output"></a>出力

```Output
5
7
```

### <a name="remarks"></a>Remarks

詳細については、次を参照してください。[自動](../cpp/auto-cpp.md)、 [function クラス](../standard-library/function-class.md)、および[関数を呼び出す](../cpp/function-call-cpp.md)します。

ラムダ式は関数の本体で最も頻繁に宣言されますが、変数を初期化できる場所ならどこでも宣言できます。

### <a name="example-2"></a>例 2

MicrosoftC++式が呼び出されたときの代わりに、式が宣言されている場合、コンパイラがそのキャプチャされた変数にラムダ式をバインドします。 次の例では、ローカル変数 `i` を明示的に値でキャプチャし、ローカル変数 `j` を暗黙的に参照でキャプチャするラムダ式を示しています。 ラムダ式は `i` を値でキャプチャするため、プログラムが後で `i` を再割り当てしても式の結果に影響しません。 ただし、ラムダ式は `j` を参照でキャプチャするため、`j` の再割り当ては式の結果に影響します。

### <a name="code"></a>コード

```cpp
// declaring_lambda_expressions2.cpp
// compile with: /EHsc /W4
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   int i = 3;
   int j = 5;

   // The following lambda expression captures i by value and
   // j by reference.
   function<int (void)> f = [i, &j] { return i + j; };

   // Change the values of i and j.
   i = 22;
   j = 44;

   // Call f and print its result.
   cout << f() << endl;
}
```

### <a name="output"></a>出力

```Output
47
```

[[この記事の内容](#top)]

##  <a name="callingLambdaExpressions"></a> ラムダ式の呼び出し

次のコード スニペットに示しているように、ラムダ式は直接呼び出すことができます。 2 番目のスニペットでは、C++ 標準ライブラリ アルゴリズムに引数としてラムダをなど渡す方法を示しています。`find_if`します。

### <a name="example-1"></a>例 1

この例は、2 つの整数値の合計を返し、引数 `5` と `4` で直接、式を呼び出すラムダ式を宣言します。

### <a name="code"></a>コード

```cpp
// calling_lambda_expressions1.cpp
// compile with: /EHsc
#include <iostream>

int main()
{
   using namespace std;
   int n = [] (int x, int y) { return x + y; }(5, 4);
   cout << n << endl;
}
```

### <a name="output"></a>出力

```Output
9
```

### <a name="example-2"></a>例 2

この例は、`find_if` 関数の引数としてラムダ式を渡します。 ラムダ式から返される**true**そのパラメーターが偶数である場合。

### <a name="code"></a>コード

```cpp
// calling_lambda_expressions2.cpp
// compile with: /EHsc /W4
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    // Create a list of integers with a few initial elements.
    list<int> numbers;
    numbers.push_back(13);
    numbers.push_back(17);
    numbers.push_back(42);
    numbers.push_back(46);
    numbers.push_back(99);

    // Use the find_if function and a lambda expression to find the
    // first even number in the list.
    const list<int>::const_iterator result =
        find_if(numbers.begin(), numbers.end(),[](int n) { return (n % 2) == 0; });

    // Print the result.
    if (result != numbers.end()) {
        cout << "The first even number in the list is " << *result << "." << endl;
    } else {
        cout << "The list contains no even numbers." << endl;
    }
}
```

### <a name="output"></a>出力

```Output
The first even number in the list is 42.
```

### <a name="remarks"></a>Remarks

詳細については、`find_if`関数を参照してください[find_if](../standard-library/algorithm-functions.md#find_if)します。 一般的なアルゴリズムを実行する C++ 標準ライブラリ関数の詳細については、次を参照してください。 [\<アルゴリズム >](../standard-library/algorithm.md)します。

[[この記事の内容](#top)]

##  <a name="nestingLambdaExpressions"></a> ラムダ式の入れ子

### <a name="example"></a>例

この例に示しているように、ラムダ式を別のラムダ式の入れ子にすることができます。 内側のラムダ式は、その引数を 2 倍し、その結果を返します。 外側のラムダ式は、引数を持つ内側のラムダ式を呼び出し、結果に 3 を追加します。

### <a name="code"></a>コード

```cpp
// nesting_lambda_expressions.cpp
// compile with: /EHsc /W4
#include <iostream>

int main()
{
    using namespace std;

    // The following lambda expression contains a nested lambda
    // expression.
    int timestwoplusthree = [](int x) { return [](int y) { return y * 2; }(x) + 3; }(5);

    // Print the result.
    cout << timestwoplusthree << endl;
}
```

### <a name="output"></a>出力

```Output
13
```

### <a name="remarks"></a>Remarks

この例では、`[](int y) { return y * 2; }` は入れ子になったラムダ式です。

[[この記事の内容](#top)]

##  <a name="higherOrderLambdaExpressions"></a> 高階ラムダ関数

### <a name="example"></a>例

多くのプログラミング言語の概念をサポートする、*高階関数。* 高階関数は、引数として別のラムダ式を受け取るか、ラムダ式を返すラムダ式です。 使用することができます、[関数](../standard-library/function-class.md)などの高階関数の動作を C++ ラムダ式を有効にするクラス。 この例は、`function` オブジェクトを返すラムダ式と、`function` オブジェクトを引数として受け取るラムダ式を示しています。

### <a name="code"></a>コード

```cpp
// higher_order_lambda_expression.cpp
// compile with: /EHsc /W4
#include <iostream>
#include <functional>

int main()
{
    using namespace std;

    // The following code declares a lambda expression that returns
    // another lambda expression that adds two numbers.
    // The returned lambda expression captures parameter x by value.
    auto addtwointegers = [](int x) -> function<int(int)> {
        return [=](int y) { return x + y; };
    };

    // The following code declares a lambda expression that takes another
    // lambda expression as its argument.
    // The lambda expression applies the argument z to the function f
    // and multiplies by 2.
    auto higherorder = [](const function<int(int)>& f, int z) {
        return f(z) * 2;
    };

    // Call the lambda expression that is bound to higherorder.
    auto answer = higherorder(addtwointegers(7), 8);

    // Print the result, which is (7+8)*2.
    cout << answer << endl;
}
```

### <a name="output"></a>出力

```Output
30
```

[[この記事の内容](#top)]

##  <a name="methodLambdaExpressions"></a> 関数でラムダ式の使用

### <a name="example"></a>例

関数の本体でラムダ式を使用できます。 ラムダ式は、外側の関数がアクセスできる任意の関数またはデータ メンバーにアクセスできます。 明示的または暗黙的にキャプチャできます、**this**外側のクラスのメンバー関数とデータ メンバーにアクセスできるようにへのポインター。
**Visual Studio 2017 バージョン 15.3 以降**(で使用可能な[/std:c++17](../build/reference/std-specify-language-standard-version.md))。キャプチャ**this**値によって (`[*this]`) ときに、ラムダで使用される非同期または並列操作コードが、元のオブジェクトがスコープ外になった後に実行可能性があります。

使用することができます、**this**関数の場合、次に示すように明示的にポインター。

```cpp
// capture "this" by reference
void ApplyScale(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [this](int n) { cout << n * _scale << endl; });
}

// capture "this" by value (Visual Studio 2017 version 15.3 and later)
void ApplyScale2(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [*this](int n) { cout << n * _scale << endl; });
}
```

キャプチャすることも、**this**ポインターに暗黙的に。

```cpp
void ApplyScale(const vector<int>& v) const
{
   for_each(v.begin(), v.end(),
      [=](int n) { cout << n * _scale << endl; });
}
```

次の例は、スケール値をカプセル化する `Scale` クラスを示しています。

```cpp
// function_lambda_expression.cpp
// compile with: /EHsc /W4
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

class Scale
{
public:
    // The constructor.
    explicit Scale(int scale) : _scale(scale) {}

    // Prints the product of each element in a vector object
    // and the scale value to the console.
    void ApplyScale(const vector<int>& v) const
    {
        for_each(v.begin(), v.end(), [=](int n) { cout << n * _scale << endl; });
    }

private:
    int _scale;
};

int main()
{
    vector<int> values;
    values.push_back(1);
    values.push_back(2);
    values.push_back(3);
    values.push_back(4);

    // Create a Scale object that scales elements by 3 and apply
    // it to the vector object. Does not modify the vector.
    Scale s(3);
    s.ApplyScale(values);
}
```

### <a name="output"></a>出力

```Output
3
6
9
12
```

### <a name="remarks"></a>Remarks

`ApplyScale` 関数は、ラムダ式を使用してスケール値と `vector` オブジェクト内の各要素の積を出力します。 ラムダ式が暗黙的にキャプチャ**this**にアクセスできるように、`_scale`メンバー。

[[この記事の内容](#top)]

##  <a name="templateLambdaExpressions"></a> テンプレートでラムダ式の使用

### <a name="example"></a>例

ラムダ式は型指定されているため、それらを C++ テンプレートで使用できます。 `negate_all` 関数および `print_all` 関数の例を次に示します。 `negate_all`関数に適用される単項**演算子 -** 内の各要素に、`vector`オブジェクト。 `print_all` 関数は、`vector` オブジェクトの各要素をコンソールに出力します。

### <a name="code"></a>コード

```cpp
// template_lambda_expression.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

// Negates each element in the vector object. Assumes signed data type.
template <typename T>
void negate_all(vector<T>& v)
{
    for_each(v.begin(), v.end(), [](T& n) { n = -n; });
}

// Prints to the console each element in the vector object.
template <typename T>
void print_all(const vector<T>& v)
{
    for_each(v.begin(), v.end(), [](const T& n) { cout << n << endl; });
}

int main()
{
    // Create a vector of signed integers with a few elements.
    vector<int> v;
    v.push_back(34);
    v.push_back(-43);
    v.push_back(56);

    print_all(v);
    negate_all(v);
    cout << "After negate_all():" << endl;
    print_all(v);
}
```

### <a name="output"></a>出力

```Output
34
-43
56
After negate_all():
-34
43
-56
```

### <a name="remarks"></a>Remarks

C++ テンプレートの詳細については、次を参照してください。[テンプレート](../cpp/templates-cpp.md)します。

[[この記事の内容](#top)]

##  <a name="ehLambdaExpressions"></a> 例外の処理

### <a name="example"></a>例

ラムダ式の本体は、構造化例外処理 (SEH: Structured Exception Handling) および C++ 例外処理の規則に従います。 発生した例外をラムダ式の本体で処理するか、または例外処理を外側のスコープに延期することができます。 次の例では、 **for_each**関数とラムダ式を入力する、`vector`もう 1 つの値を持つオブジェクト。 使用して、**try**/**catch**最初のベクトルに無効なアクセスを処理するためにブロックします。

### <a name="code"></a>コード

```cpp
// eh_lambda_expression.cpp
// compile with: /EHsc /W4
#include <vector>
#include <algorithm>
#include <iostream>
using namespace std;

int main()
{
    // Create a vector that contains 3 elements.
    vector<int> elements(3);

    // Create another vector that contains index values.
    vector<int> indices(3);
    indices[0] = 0;
    indices[1] = -1; // This is not a valid subscript. It will trigger an exception.
    indices[2] = 2;

    // Use the values from the vector of index values to
    // fill the elements vector. This example uses a
    // try/catch block to handle invalid access to the
    // elements vector.
    try
    {
        for_each(indices.begin(), indices.end(), [&](int index) {
            elements.at(index) = index;
        });
    }
    catch (const out_of_range& e)
    {
        cerr << "Caught '" << e.what() << "'." << endl;
    };
}
```

### <a name="output"></a>出力

```Output
Caught 'invalid vector<T> subscript'.
```

### <a name="remarks"></a>Remarks

例外処理の詳細については、次を参照してください。[例外処理](../cpp/exception-handling-in-visual-cpp.md)します。

[[この記事の内容](#top)]

##  <a name="managedLambdaExpressions"></a> ラムダ式を使用してマネージ型 (C +/cli CLI)

### <a name="example"></a>例

ラムダ式の capture 句には、マネージド型の変数を含めることができません。 ただし、ラムダ式のパラメーター リストにマネージ型の引数を渡すことができます。 この例に示しているラムダ式は、ローカル非マネージ型変数 `ch` を値でキャプチャし、<xref:System.String?displayProperty=fullName> オブジェクトをパラメーターとして受け取ります。

### <a name="code"></a>コード

```cpp
// managed_lambda_expression.cpp
// compile with: /clr
using namespace System;

int main()
{
    char ch = '!'; // a local unmanaged variable

    // The following lambda expression captures local variables
    // by value and takes a managed String object as its parameter.
    [=](String ^s) {
        Console::WriteLine(s + Convert::ToChar(ch));
    }("Hello");
}
```

### <a name="output"></a>出力

```Output
Hello!
```

### <a name="remarks"></a>Remarks

ラムダ式を STL/CLR ライブラリで使用することもできます。 詳細については、次を参照してください。 [STL/CLR ライブラリ リファレンス](../dotnet/stl-clr-library-reference.md)します。

> [!IMPORTANT]
>  ラムダは、これらの共通言語ランタイム (CLR) によって管理されるエンティティでサポートされていません: **ref クラス**、 **ref 構造体**、**値クラス**、および**値構造体**.

[[この記事の内容](#top)]

## <a name="see-also"></a>関連項目

[ラムダ式](../cpp/lambda-expressions-in-cpp.md)<br/>
[ラムダ式の構文](../cpp/lambda-expression-syntax.md)<br/>
[auto](../cpp/auto-cpp.md)<br/>
[function クラス](../standard-library/function-class.md)<br/>
[find_if](../standard-library/algorithm-functions.md#find_if)<br/>
[\<algorithm>](../standard-library/algorithm.md)<br/>
[関数呼び出し](../cpp/function-call-cpp.md)<br/>
[テンプレート](../cpp/templates-cpp.md)<br/>
[例外処理](../cpp/exception-handling-in-visual-cpp.md)<br/>
[STL/CLR ライブラリ リファレンス](../dotnet/stl-clr-library-reference.md)