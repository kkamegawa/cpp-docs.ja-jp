---
title: 型変換とタイプ セーフ
ms.date: 11/19/2019
ms.topic: conceptual
ms.assetid: 629b361a-2ce1-4700-8b5d-ab4f57b245d5
ms.openlocfilehash: dbca9057622ab1a92b74e2958b8dfbe8d810fede
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246113"
---
# <a name="type-conversions-and-type-safety"></a>型変換とタイプ セーフ

このドキュメントでは、共通型の変換に伴う問題を識別し、C++ コードでそれらを回避する方法を説明します。

C ++.のプログラムを作成するときは、そのプログラムがタイプ セーフであることを確認することが重要です。 これは、すべての変数、関数の引数、および関数の戻り値が適切な種類のデータを格納すること、異なる型の値が関係する操作が "意味のある" 処理を行うこと、さらにデータ損失、ビット パターンの誤った解釈、メモリ破損を発生させないことを意味します。 プログラムが、明示的または暗黙的に、ある型の値を他の型に変換しないことが、定義上のタイプ セーフです。 ただし、型の変換、また場合によっては安全でない変換が必須になることもあります。 たとえば、浮動小数点演算の結果を**int**型の変数に格納する必要がある場合や、符号付き**int**を受け取る関数に符号なし**整数**の値を渡す必要がある場合があります。どちらの例でも、データの損失や値の再解釈が発生する可能性があるため、安全ではない変換を示しています。

コンパイラが安全ではない変換を検出した場合は、エラーまたは警告を発行します。 エラーが生じた場合はコンパイルが中止されます。警告が生じた場合は、コンパイルは続行されますが、コード内にエラーが存在する可能性が示されます。 ただし、警告なしでプログラムがコンパイルされた場合でも、正しくない結果を生成する暗黙の型変換につながるコードが存在している可能性があります。 型エラーは、コード内の明示的な変換、またはキャストによって発生する可能性があります。

## <a name="implicit-type-conversions"></a>暗黙的な型変換

式に異なる組み込み型のオペランドが含まれており、明示的なキャストが存在しない場合、コンパイラは、組み込みの*標準変換*を使用してオペランドの1つを変換し、型が一致するようにします。 コンパイラはいずれかが成功するまで、適切に定義された一連の変換を試みます。 選択した変換が上位変換である場合は、コンパイラは警告を発行しません。 変換が縮小変換である場合は、コンパイラは、データ損失の可能性に関する警告を発行します。 実際のデータ損失が発生するかどうかは、関与する実際の値に依存しますが、この警告をエラーとして扱うことをお勧めします。 ユーザー定義型が関与している場合は、コンパイラは、ユーザーがクラス定義の中で指定した変換を使用しようとします。 受け入れ可能な変換が見つからない場合は、コンパイラはエラーを発行し、プログラムをコンパイルしません。 標準変換を制御する規則の詳細については、「[標準変換](../cpp/standard-conversions.md)」を参照してください。 ユーザー定義変換の詳細については、「[ユーザー定義変換 (C++/cli)](../dotnet/user-defined-conversions-cpp-cli.md)」を参照してください。

### <a name="widening-conversions-promotion"></a>拡大変換 (上位変換)

拡大変換では、より小さい変数内の値が、より大きい変数に代入され、データは失われません。 拡大変換は常に安全であるため、コンパイラはこの変換を自動的に実行し、警告を発行しません。 次の変換は、拡大変換です。

|提供元|目的|
|----------|--------|
|**Long long**または **__int64**を除く、符号付きまたは符号なしの整数型|**double**|
|**bool**または**char**|他のすべての組み込み型|
|**short**または**wchar_t**|**int**、 **long**、long **long**|
|**int**、 **long**|**long long**|
|**float**|**double**|

### <a name="narrowing-conversions-coercion"></a>縮小変換 (強制型)

コンパイラは、暗黙的に縮小変換を実行しますが、データ損失の可能性に関する警告を発行します。 これらの警告を重大なものとして受け止めてください。 大きい変数の中にある値が、小さい変数の中に必ず収容でき、データ損失が発生しないことが確実な場合は、コンパイラが今後警告を発行しないように、明示的なキャストを追加してください。 変換が安全かどうか自信がない場合は、コード内になんらかの種類の実行時チェックを追加し、発生する可能性のあるデータ損失に対処できるようにしてください。その結果、プログラムが誤った結果を生成することはありません。

浮動小数点型から整数型へのあらゆる変換は、浮動小数点値の小数部が破棄されて失われるため、縮小変換です。

次のコード例では、いくつかの暗黙的な縮小変換と、それらに関してコンパイラが発行する警告を示します。

```cpp
int i = INT_MAX + 1; //warning C4307:'+':integral constant overflow
wchar_t wch = 'A'; //OK
char c = wch; // warning C4244:'initializing':conversion from 'wchar_t'
              // to 'char', possible loss of data
unsigned char c2 = 0xfffe; //warning C4305:'initializing':truncation from
                           // 'int' to 'unsigned char'
int j = 1.9f; // warning C4244:'initializing':conversion from 'float' to
              // 'int', possible loss of data
int k = 7.7; // warning C4244:'initializing':conversion from 'double' to
             // 'int', possible loss of data
```

### <a name="signed---unsigned-conversions"></a>符号付き - 符号なしの変換

符号付き整数型と符号なし整数型は常に同じサイズですが、値変換の目的でビット パターンを解釈する方法が異なります。 次のコード例は、同じビット パターンが符号付きの値、および符号なしの値として解釈されるときの動作を示します。 `num` と `num2` の両方に格納されているビット パターンは、前の図から決して変化していません。

```cpp
using namespace std;
unsigned short num = numeric_limits<unsigned short>::max(); // #include <limits>
short num2 = num;
cout << "unsigned val = " << num << " signed val = " << num2 << endl;
// Prints: unsigned val = 65535 signed val = -1

// Go the other way.
num2 = -1;
num = num2;
cout << "unsigned val = " << num << " signed val = " << num2 << endl;
// Prints: unsigned val = 65535 signed val = -1
```

値の再解釈が双方向で発生することに注意してください。 期待される値に対して、符号が反転したように思える奇妙な結果をプログラムが返した場合は、符号付き整数型と符号なし整数型の間で暗黙的な変換が実行された可能性に注目してください。 次の例では、式の結果 (0-1) が `num`に格納されている場合、 **int**から**unsigned int**に暗黙的に変換されます。 この結果、ビット パターンの再解釈が発生します。

```cpp
unsigned int u3 = 0 - 1;
cout << u3 << endl; // prints 4294967295
```

符号付きと符号なし整数型の間の暗黙的な変換について、コンパイラは警告を発行しません。 したがって、符号付きから符号なしへの変換を決して実施しないことをお勧めします。 このような変換を回避できない場合は、変換されようとしている値が 0 以上であるかどうか、および符号付きの型の最大値以下であるかどうかを検出する実行時チェックをコードに追加してください。 この範囲内にある値は、再解釈なしで、符号付きから符号なし、および符号なしから符号付きへと変換されます。

### <a name="pointer-conversions"></a>ポインター変換

多くの式では、C 形式の配列は、配列内の最初の要素へのポインターに暗黙的に変換され、また定数変換が警告なしで実施される可能性があります。 これは便利ですが、場合によってはエラーが発生しやすくなります。 たとえば、不適切に設計された次のコード例は、無意味のように見えますが、コンパイルして ' p ' の結果を生成します。 まず、"Help" 文字列定数リテラルは `char*` に変換されます。このポインターは 配列の最初の要素を指し、3 つの要素によってインクリメントされます。その結果、最後の要素 'p' を指すようになります。

```cpp
char* s = "Help" + 3;
```

## <a name="explicit-conversions-casts"></a>明示的な変換 (キャスト)

キャスト操作を使用すると、ある型の値を別の型に変換するようにコンパイラに指示できます。 2 つの方が完全に無関係である場合はコンパイラはエラーを生成しますが、操作がタイプ セーフでない場合でもエラーを生成しない状況が存在します。 キャストは控えめに使用してください。ある型から別の型への変換は、プログラム エラーの原因となる可能性があるためです。 ただし、時にはキャストが必須であり、すべてのキャストが等しく危険というわけでもありません。 キャストの 1 つの効率的な使用方法は、コードが縮小変換を実行し、その変換により、プログラムが不適切な結果をもたらさないことがわかっている場合です。 実際には、何を実行するかを開発者が理解していて、その点に関する警告を発行しないようにコンパイラに指示することになります。 別の使用法は、ポインターから派生クラス、およびポインターから基底クラスへのキャストです。 もう1つの用途は、変数の**const**性をキャストして、非**定数**の引数を必要とする関数に渡すことです。 これらのキャスト操作のほとんどには、ある程度のリスクが存在します。

C スタイルのプログラミングでは、同じ C スタイルのキャスト演算子が、あらゆる種類のキャストに使用されます。

```cpp
(int) x; // old-style cast, old-style syntax
int(x); // old-style cast, functional syntax
```

つまり、C スタイルのキャスト演算子は、呼び出し演算子 () と同じものであり、したがって、コードの中で目立たず、簡単に見過ごす可能性があります。 どちらも、ひとめで認識したり、検索したりするのは困難であり、 **static**、 **const**、および**reinterpret_cast**の任意の組み合わせを呼び出すのに十分な違いがあるからです。 古いスタイルのキャストの実際の動作を理解するのは困難で、エラーが発生しやすくなります。 これらすべての理由により、キャストがどうしても必要な場合は、次の C++ スタイルのキャスト操作のいずれかを使用することをお勧めします。特定の状況では、かなりタイプ セーフであり、プログラミングの意図を非常に明確に表現できるからです。

- コンパイル時にのみチェックされるキャストの**static_cast**。 完全に互換性のない型間でキャストしようとしていることがコンパイラによって検出された場合、 **static_cast**はエラーを返します。 これを、基本型へのポインターと、派生形へのポインターの間でのキャストに使用することもできますが、コンパイラはこのような変換が実行時に安全かどうかを必ず判定できるわけではありません。

    ```cpp
    double d = 1.58947;
    int i = d;  // warning C4244 possible loss of data
    int j = static_cast<int>(d);       // No warning.
    string s = static_cast<string>(d); // Error C2440:cannot convert from
                                       // double to std:string

    // No error but not necessarily safe.
    Base* b = new Base();
    Derived* d2 = static_cast<Derived*>(b);
    ```

   詳細については、「 [static_cast](../cpp/static-cast-operator.md)」を参照してください。

- セーフで、実行時にチェックされる、ポインターから派生クラスへのポインターのキャストを**dynamic_cast**します。 **Dynamic_cast**は、downcasts の**static_cast**より安全ですが、ランタイムチェックによってオーバーヘッドが発生します。

    ```cpp
    Base* b = new Base();

    // Run-time check to determine whether b is actually a Derived*
    Derived* d3 = dynamic_cast<Derived*>(b);

    // If b was originally a Derived*, then d3 is a valid pointer.
    if(d3)
    {
       // Safe to call Derived method.
       cout << d3->DoSomethingMore() << endl;
    }
    else
    {
       // Run-time check failed.
       cout << "d3 is null" << endl;
    }

    //Output: d3 is null;
    ```

   詳細については、「 [dynamic_cast](../cpp/dynamic-cast-operator.md)」を参照してください。

- **const_cast**、変数の**const**性をキャストする場合、または非**const**変数を**const**に変換する場合に使用します。 この演算子を使用して**const**性をキャストすることは、C スタイルのキャストを使用する場合と同様に、エラーが発生しやすくなります。ただし、**定数キャスト**を使用すると、誤ってキャストを実行する可能性は低くなります。 場合**によって**は、定数以外のパラメーターを受け取る関数に**const**変数を渡すために、変数の**const**性をキャストする必要があります。 その方法を次の例に示します。

    ```cpp
    void Func(double& d) { ... }
    void ConstCast()
    {
       const double pi = 3.14;
       Func(const_cast<double&>(pi)); //No error.
    }
    ```

   詳細については、「 [const_cast](../cpp/const-cast-operator.md)」を参照してください。

- **reinterpret_cast**。 **int**への**ポインター**など、関連のない型間でキャストされます。

    > [!NOTE]
    >  このキャスト演算子は、他のキャスト演算子ほどの頻度では使用されず、他のコンパイラへの移植性も保証されません。

   次の例は、 **reinterpret_cast**が**static_cast**とどのように異なるかを示しています。

    ```cpp
    const char* str = "hello";
    int i = static_cast<int>(str);//error C2440: 'static_cast' : cannot
                                  // convert from 'const char *' to 'int'
    int j = (int)str; // C-style cast. Did the programmer really intend
                      // to do this?
    int k = reinterpret_cast<int>(str);// Programming intent is clear.
                                       // However, it is not 64-bit safe.
    ```

   詳細については、「 [Reinterpret_cast 演算子](../cpp/reinterpret-cast-operator.md)」を参照してください。

## <a name="see-also"></a>参照

[C++型システム](../cpp/cpp-type-system-modern-cpp.md)<br/>
[に戻るC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[C++ 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)
