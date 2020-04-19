---
title: 配列 (C++)
ms.date: 11/14/2019
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 91c57a9c4ef190dcace1813dd81739ac72e6b358
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188987"
---
# <a name="arrays-c"></a>配列 (C++)

配列は、連続したメモリ領域を占有する同じ型のオブジェクトのシーケンスです。 従来の C スタイルの配列は多くのバグの原因ですが、特に古いコードベースでは一般的です。 現代C++では、このセクションで説明する C スタイルの配列ではなく、 [std:: vector](../standard-library/vector-class.md)または[std:: array](../standard-library/array-class-stl.md)を使用することを強くお勧めします。 これらの標準ライブラリ型はどちらも、要素を連続したメモリブロックとして格納しますが、シーケンス内の有効な位置を指すことが保証される反復子と共に、より高いタイプセーフを提供します。 詳細については、「[コンテナー C++(モダン)](containers-modern-cpp.md)」を参照してください。

## <a name="stack-declarations"></a>スタック宣言

C++配列の宣言では、配列のサイズは、他の言語のように、型名の後ではなく、変数名の後に指定されます。 次の例では、スタックに割り当てられる1000倍精度の配列を宣言しています。 要素の数は、整数リテラルとして指定するか、定数式として指定する必要があります。これは、コンパイラが割り当てるスタック領域の量を知る必要があるためです。実行時に計算された値を使用することはできません。 配列の各要素には、既定値の0が割り当てられます。 既定値を割り当てない場合、各要素には、その場所で発生するランダムな値が最初に含まれます。

```cpp
    constexpr size_t size = 1000;

    // Declare an array of doubles to be allocated on the stack
    double numbers[size] {0};

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i-1] * 1.1;
    }

    // Access each element
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }
```

配列の最初の要素は0番目の要素で、最後の要素は (*n-1*) 要素です。ここで、 *n*は配列に格納できる要素の数です。 宣言内の要素の数は、整数型で、0より大きい値である必要があります。 プログラムが `(size - 1)`より大きい添字演算子に値を渡さないようにするのは、お客様の責任です。

サイズが0の配列は、配列が**構造体**または**共用体**の最後のフィールドであり、Microsoft 拡張機能 (/ze) が有効になっている場合にのみ有効です。

スタックベースの配列は、ヒープベースの配列よりも、割り当てやアクセスが高速になりますが、要素の数が大きくなりすぎて、スタックメモリが過剰に消費されることはありません。 プログラムに依存している量が多すぎます。 プロファイリングツールを使用すると、配列が大きすぎるかどうかを判断できます。

## <a name="heap-declarations"></a>ヒープ宣言

スタックに割り当てるには大きすぎる配列が必要な場合、またはコンパイル時にそのサイズを認識できない場合は、[新しい\[\]](new-operator-cpp.md)式を使用してヒープに割り当てることができます。 演算子は、最初の要素へのポインターを返します。 添字演算子は、スタックベースの配列の場合と同様に、ポインター変数と共に使用できます。 [ポインター演算](../c-language/pointer-arithmetic.md)を使用して、配列内の任意の要素にポインターを移動することもできます。 次のことを保証する必要があります。

- 配列が不要になったときにメモリを削除できるように、常に元のポインターアドレスのコピーを保持します。
- 配列の境界を越えてポインターアドレスをインクリメントまたはデクリメントすることはできません。

次の例は、実行時にヒープに配列を定義する方法と、添字演算子またはポインター演算を使用して配列要素にアクセスする方法を示しています。

```cpp

void do_something(size_t size)
{
    // Declare an array of doubles to be allocated on the heap
    double* numbers = new double[size]{ 0 };

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i - 1] * 1.1;
    }

    // Access each element with subscript operator
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }

    // Access each element with pointer arithmetic
    // Use a copy of the pointer for iterating
    double* p = numbers;

    for (size_t i = 0; i < size; i++)
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    // Alternate method:
    // Reset p to numbers[0]:
    p = numbers;

    // Use address of pointer to compute bounds.
    // The compiler computes size as the number
    // of elements * (bytes per element).
    while (p < (numbers + size))
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    delete[] numbers; // don't forget to do this!

}
int main()
{
    do_something(108);
}

```

## <a name="initializing-arrays"></a>配列の初期化

ループ内の配列、一度に1つの要素、または1つのステートメント内の配列を初期化できます。 次の2つの配列の内容は同じです。

```cpp
    int a[10];
    for (int i = 0; i < 10; ++i)
    {
        a[i] = i + 1;
    }

    int b[10]{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

## <a name="passing-arrays-to-functions"></a>関数への配列の引き渡し

配列が関数に渡されると、最初の要素へのポインターとして渡されます。 これは、スタックベースとヒープベースの両方の配列に当てはまります。 ポインターには、追加のサイズまたは型情報が含まれていません。 この動作は*ポインターの減衰*と呼ばれます。 関数に配列を渡す場合は、常に個別のパラメーターの要素数を指定する必要があります。 この動作は、配列が関数に渡されたときに配列要素がコピーされないことも意味します。 関数によって要素が変更されないようにするには、パラメーターを**const**要素へのポインターとして指定します。

次の例は、配列と長さを受け入れる関数を示しています。 ポインターは、コピーではなく元の配列を指しています。 パラメーターが**const**ではないため、関数は配列の要素を変更できます。

```cpp
void process(double p*, const size_t len)
{
    std::cout << "process:\n";
    for (size_t i = 0; i < len; ++i)
    {
        // do something with p[i]
    }
}
```

関数ブロック内で読み取り専用になるように、配列を const として宣言します。

```cpp
void process(const double p*, const size_t len);
```

これらの方法でも同じ関数を宣言できますが、動作は変更されません。 配列は、最初の要素へのポインターとして渡されます。

```cpp
// Unsized array
void process(const double p[] const size_t len);

// Fixed-size array. Length must still be specified explicitly.
void process(const double p[1000], const size_t len);
```

## <a name="multidimensional-arrays"></a>多次元配列

他の配列から生成された配列は、多次元配列です。 これらの多次元配列は、角かっこで囲まれた定数式を複数並べることで指定されます。 たとえば、次の宣言について考えます。

```cpp
int i2[5][7];
```

ここでは、次の図に示すように、**整数**型の配列を指定しています。この配列は、5行と7列の2次元行列で概念的に配置されています。

![多次元&#45;配列の概念レイアウト](../cpp/media/vc38rc1.gif "多次元&#45;配列の概念レイアウト") <br/>
多次元配列の概念レイアウト

初期化子リストを持つ多次元配列の宣言 (「[初期化子](../cpp/initializers.md)」を参照) では、最初の次元の境界を指定する定数式を省略できます。 例 :

```cpp
// arrays2.cpp
// compile with: /c
const int cMarkets = 4;
// Declare a float that represents the transportation costs.
double TransportCosts[][cMarkets] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};
```

前の宣言は、3 行 x 4 列の配列を定義します。 行はファクトリを表し、列はファクトリの出荷先のマーケットを表します。 値は、ファクトリからマーケットへの輸送コストです。 配列の最初の次元は省かれますが、コンパイラは初期化子を調べることによってこれを入力します。

N 次元の配列型で間接演算子 (*) を使用すると、n-1 次元配列が生成されます。 n が 1 の場合、スカラー (または配列要素) が生成されます。

C++ 配列は、行優先順で格納されます。 行優先は、最後の添字が最も速く変化することを意味します。

## <a name="example"></a>例

多次元配列の最初の次元の境界指定を省略する手法は、次のとおり関数宣言で使用することもできます。

```cpp
// multidimensional_arrays.cpp
// compile with: /EHsc
// arguments: 3
#include <limits>   // Includes DBL_MAX
#include <iostream>

const int cMkts = 4, cFacts = 2;

// Declare a float that represents the transportation costs
double TransportCosts[][cMkts] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};

// Calculate size of unspecified dimension
const int cFactories = sizeof TransportCosts /
                  sizeof( double[cMkts] );

double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);

using namespace std;

int main( int argc, char *argv[] ) {
   double MinCost;

   if (argv[1] == 0) {
      cout << "You must specify the number of markets." << endl;
      exit(0);
   }
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);
   cout << "The minimum cost to Market " << argv[1] << " is: "
       << MinCost << "\n";
}

double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {
   double MinCost = DBL_MAX;

   for( size_t i = 0; i < cFacts; ++i )
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?
         MinCost : TransportCosts[i][Mkt];

   return MinCost;
}
```

```Output
The minimum cost to Market 3 is: 17.29
```

`FindMinToMkt` 関数は、新しいファクトリを追加してもコード変更の必要はなく、再コンパイルだけすればいいように書かれています。

## <a name="initializing-arrays"></a>配列の初期化

クラスにコンストラクターがある場合、そのクラスの配列はコンストラクターによって初期化されます。 配列の要素よりも初期化子リスト内の項目が少ない場合、残りの要素には既定のコンストラクターが使用されます。 クラスに対して既定のコンストラクターが定義されていない場合は、完全な初期化子リストが必要です。つまり、配列の各要素に 1 つずつ初期化子が必要です。

2 つのコンストラクターを定義する `Point` クラスを考えます。

```cpp
// initializing_arrays1.cpp
class Point
{
public:
   Point()   // Default constructor.
   {
   }
   Point( int, int )   // Construct from two ints
   {
   }
};

// An array of Point objects can be declared as follows:
Point aPoint[3] = {
   Point( 3, 3 )     // Use int, int constructor.
};

int main()
{
}
```

`aPoint` の最初の要素はコンストラクター `Point( int, int )` を使用して構築されます。残りの 2 つの要素は既定のコンストラクターを使用して構築されます。

静的メンバー配列 ( **const**かどうかに関係なく) は、その定義で (クラス宣言の外側で) 初期化できます。 例 :

```cpp
// initializing_arrays2.cpp
class WindowColors
{
public:
    static const char *rgszWindowPartList[7];
};

const char *WindowColors::rgszWindowPartList[7] = {
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };
int main()
{
}
```

## <a name="accessing-array-elements"></a>配列要素へのアクセス

配列添字演算子 (`[ ]`) を使用すると、配列の個々の要素にアクセスできます。 一次元配列が添字のない式で使用されている場合、配列名は配列の最初の要素へのポインターに評価されます。

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

多次元配列を使用すると、式でさまざまな組み合わせを使用できます。

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

上記のコードでは、`multi` は**double**型の3次元配列です。 `p2multi` ポインターは、サイズが3の**double**型の配列を指します。 この例では、配列が 1 つ、2 つ、および 3 つの添字と共に使用されています。 `cout` ステートメントのように、すべての添字を指定する方が一般的ですが、`cout` に続くステートメントのように、配列要素の特定のサブセットを選択した方が便利なこともあります。

## <a name="overloading-subscript-operator"></a>添字演算子のオーバーロード

他の演算子と同様に、添字演算子 (`[]`) はユーザーが再定義できます。 添字演算子の既定の動作では、オーバーロードしない場合、次のメソッドを使用して配列名と添字を組み合わせます。

`*((array_name) + (subscript))`

ポインター型を含むすべての加算と同様に、スケーリングは型のサイズを調整するように自動的に実行されます。 したがって、結果の値は、配列名の原点からの*n*バイトではありません。代わりに、配列の*n*番目の要素です。 この変換の詳細については、「[加法演算子](additive-operators-plus-and.md)」を参照してください。

同様に、多次元配列の場合は、次のメソッドを使用してアドレスが派生されます。

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>式の配列

配列型の識別子が `sizeof`、address of (`&`)、または reference の初期化以外の式に含まれている場合は、最初の配列要素へのポインターに変換されます。 例 :

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

ポインター `psz` は、配列 `szError1` の最初の要素をポイントします。 ポインターとは異なり、配列は変更可能な左辺値ではありません。 したがって、次の割り当ては正しくありません。

```cpp
szError1 = psz;
```

## <a name="see-also"></a>参照

[std:: array](../standard-library/array-class-stl.md)
