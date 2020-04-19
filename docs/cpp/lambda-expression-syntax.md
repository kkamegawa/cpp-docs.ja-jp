---
title: ラムダ式の構文
ms.date: 05/07/2019
helpviewer_keywords:
- lambda expressions [C++], syntax
ms.assetid: 5d6154a4-f34d-4a15-970d-7e7de45f54e9
ms.openlocfilehash: 37e4a512678bf276b5244fd54945f49a37ff8d01
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222387"
---
# <a name="lambda-expression-syntax"></a>ラムダ式の構文

この記事では、ラムダ式の構文と構造体要素を説明します。 ラムダ式については、次を参照してください。[ラムダ式](../cpp/lambda-expressions-in-cpp.md)します。

## <a name="function-objects-vs-lambdas"></a>関数オブジェクトとラムダ

問題を解決し、計算を実行して使用する場合に特には、関数ポインターと関数オブジェクトをおそらく使用するコードを記述するときに[C++ 標準ライブラリ アルゴリズム](../cpp/algorithms-modern-cpp.md)します。 関数ポインターと関数オブジェクトには、それぞれに利点と欠点があります。たとえば、関数ポインターは、最小限の構文オーバーヘッドで済みますが、スコープ内の状態を保持しません。関数オブジェクトは、状態を保持できますが、クラス定義の構文オーバーヘッドが必要となります。

ラムダは、関数ポインターと関数オブジェクトの両方の利点を持ち、それらの欠点を回避できます。 ラムダは、関数オブジェクトのように柔軟性があり状態を保持できますが、関数オブジェクトとは異なり、その簡潔な構文には明示的なクラス定義は必要ありません。 ラムダを使用すると、同等の関数オブジェクトのコードよりも使いやすくエラーが発生しにくいコードを作成できます。

次の例では、ラムダの使用と関数オブジェクトの使用を比較しています。 最初の例では、ラムダを使用して `vector` オブジェクト内の各要素が偶数か奇数であるかをコンソールに出力します。 2 番目の例では、関数オブジェクトを使用して同じタスクを行っています。

## <a name="example-1-using-a-lambda"></a>例 1: ラムダの使用

この例では、ラムダ、 **for_each**関数。 ラムダは、`vector` オブジェクト内の各要素が偶数か奇数かを示す結果を出力します。

### <a name="code"></a>コード

```cpp
// even_lambda.cpp
// compile with: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

int main()
{
   // Create a vector object that contains 9 elements.
   vector<int> v;
   for (int i = 1; i < 10; ++i) {
      v.push_back(i);
   }

   // Count the number of even numbers in the vector by
   // using the for_each function and a lambda.
   int evenCount = 0;
   for_each(v.begin(), v.end(), [&evenCount] (int n) {
      cout << n;
      if (n % 2 == 0) {
         cout << " is even " << endl;
         ++evenCount;
      } else {
         cout << " is odd " << endl;
      }
   });

   // Print the count of even numbers to the console.
   cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

### <a name="comments"></a>コメント

3 番目の引数の例で、 **for_each**関数は、ラムダ。 `[&evenCount]` の部分は、式の capture 句を指定します。`(int n)` はパラメーター リストを指定します。残りの部分は、式の本体を指定します。

## <a name="example-2-using-a-function-object"></a>例 2:関数オブジェクトを使用します。

ラムダは、前の例よりも拡張するのがはるかに複雑になる場合があります。 次の例と共に、ラムダではなく、関数オブジェクトを使用して、 **for_each**例 1 と同じ結果を生成する関数。 どちらの例でも `vector` オブジェクトに含まれる偶数の数を格納します。 操作の状態を保持するために、`FunctorClass` クラスはメンバー変数の参照として `m_evenCount` 変数を格納します。 操作を実行する`FunctorClass`、関数呼び出し演算子を実装する**operator()** します。 MicrosoftC++コンパイラ サイズと例 1 でのラムダ コードのパフォーマンスに匹敵するコードを生成します。 ここで紹介したような基本的な問題の場合は、おそらく、より単純なラムダのデザインの方が関数オブジェクトよりも適切です。 ただし、後で大幅な機能拡張が必要となる可能性がある場合は、コードの保守が容易になるように、関数オブジェクトのデザインを使用します。

詳細については、 **operator()** を参照してください[関数を呼び出す](../cpp/function-call-cpp.md)します。 詳細については、 **for_each**関数を参照してください[for_each](../standard-library/algorithm-functions.md#for_each)します。

### <a name="code"></a>コード

```cpp
// even_functor.cpp
// compile with: /EHsc
#include <algorithm>
#include <iostream>
#include <vector>
using namespace std;

class FunctorClass
{
public:
    // The required constructor for this example.
    explicit FunctorClass(int& evenCount)
        : m_evenCount(evenCount) { }

    // The function-call operator prints whether the number is
    // even or odd. If the number is even, this method updates
    // the counter.
    void operator()(int n) const {
        cout << n;

        if (n % 2 == 0) {
            cout << " is even " << endl;
            ++m_evenCount;
        } else {
            cout << " is odd " << endl;
        }
    }

private:
    // Default assignment operator to silence warning C4512.
    FunctorClass& operator=(const FunctorClass&);

    int& m_evenCount; // the number of even variables in the vector.
};

int main()
{
    // Create a vector object that contains 9 elements.
    vector<int> v;
    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }

    // Count the number of even numbers in the vector by
    // using the for_each function and a function object.
    int evenCount = 0;
    for_each(v.begin(), v.end(), FunctorClass(evenCount));

    // Print the count of even numbers to the console.
    cout << "There are " << evenCount
        << " even numbers in the vector." << endl;
}
```

```Output
1 is odd
2 is even
3 is odd
4 is even
5 is odd
6 is even
7 is odd
8 is even
9 is odd
There are 4 even numbers in the vector.
```

## <a name="see-also"></a>関連項目

[ラムダ式](../cpp/lambda-expressions-in-cpp.md)<br/>
[ラムダ式の例](../cpp/examples-of-lambda-expressions.md)<br/>
[generate](../standard-library/algorithm-functions.md#generate)<br/>
[generate_n](../standard-library/algorithm-functions.md#generate_n)<br/>
[for_each](../standard-library/algorithm-functions.md#for_each)<br/>
[例外の仕様 (スロー)](../cpp/exception-specifications-throw-cpp.md)<br/>
[コンパイラの警告 (レベル 1) C4297](../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md)<br/>
[Microsoft 固有の修飾子](../cpp/microsoft-specific-modifiers.md)