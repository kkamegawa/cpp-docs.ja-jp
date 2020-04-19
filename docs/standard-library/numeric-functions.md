---
title: '&lt;numeric&gt; 関数'
description: C++標準ライブラリの &lt;numeric&gt;ヘッダーによって提供される関数テンプレートについて説明します。
ms.date: 10/30/2019
f1_keywords:
- numeric/std::accumulate
- numeric/std::adjacent_difference
- numeric/std::exclusive_scan
- numeric/std::gcd
- numeric/std::inclusive_scan
- numeric/std::inner_product
- numeric/std::iota
- numeric/std::lcm
- numeric/std::partial_sum
- numeric/std::reduce
- numeric/std::transform_exclusive_scan
- numeric/std::transform_inclusive_scan
- numeric/std::transform_reduce
ms.assetid: a4b0449a-c80c-4a1d-8d9f-d7fcd0058f8b
helpviewer_keywords:
- std::accumulate [C++]
- std::adjacent_difference [C++]
- std::exclusive_scan [C++]
- std::gcd [C++]
- std::inclusive_scan [C++]
- std::inner_product [C++]
- std::iota [C++]
- std::lcm [C++]
- std::partial_sum [C++]
- std::reduce [C++]
- std::transform_exclusive_scan [C++]
- std::transform_inclusive_scan [C++]
- std::transform_reduce [C++]
ms.openlocfilehash: 88a97a3d110c684090b78570077927e32541eed7
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627447"
---
# <a name="ltnumericgt-functions"></a>&lt;numeric&gt; 関数

## <a name="accumulate"></a>加算

連続する部分和を計算することによって、初期値を含め、指定した範囲のすべての要素の合計を計算します。 またはは、指定された二項演算の連続する部分的な結果の結果を計算します。

```cpp
template <class InputIterator, class Type>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init);

template <class InputIterator, class Type, class BinaryOperation>
Type accumulate(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>パラメーター

*最初*の \
*Binary_op*を使用して合計または結合する範囲内の最初の要素を示す入力反復子。

*最後*の \
*Binary_op*を使用して合計または結合する範囲内の最後の要素を示す入力反復子。これは、反復累積に実際に含まれる最後の要素の1つ後ろの位置です。

*初期化*\
*Binary_op*を使用して各要素が追加または結合される初期値。

*binary_op*\
指定された範囲内の各要素に適用する二項演算と、以前のアプリケーションの結果。

### <a name="return-value"></a>戻り値

最初のテンプレート関数の指定した範囲内にある*init*とすべての要素の合計。2番目のテンプレート関数の場合は、sum 演算ではなく二項演算*binary_op*を適用した結果が (* partialresult, in_ になります。 *iter*)。 *partialresult*は、操作の以前のアプリケーションの結果であり、 *in_iter*は範囲内の次の要素を指す反復子です。

### <a name="remarks"></a>Remarks

初期値によって、範囲が空の場合に適切に定義された結果が得られます。この場合、 *init*が返されます。 二項演算は、結合または可換である必要はありません。 結果は初期値の*init*に初期化され、*結果* = *binary_op*(*result*, *in_iter*) が範囲を通じて反復的に計算されます。ここで、 *in_iter*はそれぞれを指す反復子です。範囲内の連続する要素。 範囲は有効である必要があり、複雑さは範囲のサイズに比例します。 2 項演算子の戻り値の型は、反復中のクロージャを確実にするために、**Type** に変換可能である必要があります。

### <a name="example"></a>例

```cpp
// numeric_accum.cpp
// compile with: /EHsc
#include <vector>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector <int> v1, v2(20);
   vector <int>::iterator iter1, iter2;

   int i;
   for (i = 1; i < 21; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   // The first member function for the accumulated sum
   int total;
   total = accumulate(v1.begin(), v1.end(), 0);

   cout << "The sum of the integers from 1 to 20 is: "
        << total << "." << endl;

   // Constructing a vector of partial sums
   int j = 0, partotal;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      partotal = accumulate(v1.begin(), iter1 + 1, 0);
      v2[j] = partotal;
      j++;
   }

   cout << "The vector of partial sums is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function for the accumulated product
   vector <int> v3, v4(10);
   vector <int>::iterator iter3, iter4;

   int s;
   for (s = 1; s < 11; s++)
   {
      v3.push_back(s);
   }

   cout << "The original vector v3 is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl;

   int ptotal;
   ptotal = accumulate(v3.begin(), v3.end(), 1, multiplies<int>());

   cout << "The product of the integers from 1 to 10 is: "
        << ptotal << "." << endl;

   // Constructing a vector of partial products
   int k = 0, ppartotal;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++) {
      ppartotal = accumulate(v3.begin(), iter3 + 1, 1, multiplies<int>());
      v4[k] = ppartotal;
      k++;
   }

   cout << "The vector of partial products is:\n ( " ;
   for (iter4 = v4.begin(); iter4 != v4.end(); iter4++)
      cout << *iter4 << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 ).
The sum of the integers from 1 to 20 is: 210.
The vector of partial sums is:
( 1 3 6 10 15 21 28 36 45 55 66 78 91 105 120 136 153 171 190 210 ).

The original vector v3 is:
( 1 2 3 4 5 6 7 8 9 10 ).
The product of the integers from 1 to 10 is: 3628800.
The vector of partial products is:
( 1 2 6 24 120 720 5040 40320 362880 3628800 ).
```

## <a name="adjacent_difference"></a>adjacent_difference

入力範囲内の各要素とその先行要素との連続する差を計算します。 結果をターゲット範囲に出力します。 またはは、差分演算が指定された別の二項演算に置き換えられる、一般化されたプロシージャの結果を計算します。

```cpp
template <class InputIterator, class OutIterator>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIterator, class BinaryOperation>
OutputIterator adjacent_difference(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template <class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 adjacent_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>パラメーター

*exec*\
実行ポリシー。

*最初*の \
含まれる要素がそれぞれの先行要素と差分処理されるか、または値のペアが別の指定された二項演算で処理される入力範囲の先頭の要素を示す入力反復子。

*最後*の \
含まれる要素がそれぞれの先行要素と差分処理されるか、または値のペアが別の指定された二項演算で処理される入力範囲の最後の要素を示す入力反復子。

*結果*\
一連の差分または指定された演算の結果が格納されるターゲット範囲の先頭の要素を示す出力反復子。

*binary_op*\
一般化された操作で適用する二項演算で、差分プロシージャの減算演算を置き換えます。

### <a name="return-value"></a>戻り値

ターゲット範囲の末尾を示す出力反復子: `result` + (`last` - `first`)。

### <a name="remarks"></a>Remarks

出力反復子の*結果*は、*最初*に入力反復子と同じ反復子になることができるため、`adjacent_difference` 値が適切に計算される可能性があります。

入力範囲内の*1、* *a 2、* *a*3 の値のシーケンスの場合 *、1つ*目のテンプレート関数は、連続した `adjacent_difference`*値を 1*、2- *a*1、a3- *a*2 をターゲット範囲に格納します。

入力範囲に*1、a 2、* *a*3*の値のシーケンスがある場合*、2番目のテンプレート関数は、連続した *`adjacent_difference` 値 (* 1、2 *binary_op* *a* *1、* *a*3 *binary_op* *a*2) をに格納します。ターゲット範囲。

二項演算*binary_op*は、適用される操作の順序が指定されているため、結合または可換である必要はありません。

### <a name="example"></a>例

```cpp
// numeric_adj_diff.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;

   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend, LIterend2;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t * t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the adjacent_differences of
   // elements in a list output to a vector
   VIterend = adjacent_difference ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "Output vector containing adjacent_differences is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the adjacent products of the elements in a list
   VIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the adjacent products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of adjacent_differences in place
   LIterend2 = adjacent_difference ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "In place output adjacent_differences in list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend2 ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="exclusive_scan"></a>exclusive_scan

初期値を指定して、`std::plus<>()` または指定した二項演算子を範囲に対して使用して、排他的プレフィックスの合計演算を実行します。 指定したコピー先で始まる範囲に結果を書き込みます。 *排他的プレフィックス*合計は、n*番目*の入力要素が*n*番目の合計に含まれていないことを意味します。 実行ポリシー引数を含むオーバーロードは、指定したポリシーに従って実行されます。

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init);

template<class InputIterator, class OutputIterator, class Type, class BinaryOperation>
OutputIterator exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation>
ForwardIterator2 exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>パラメーター

*exec*\
実行ポリシー。

*最初*の \
*Binary_op*を使用して合計または結合する範囲内の最初の要素を示す入力反復子。

*最後*の \
*Binary_op*を使用して合計または結合する範囲内の最後の要素を示す入力反復子。これは、反復累積に実際に含まれる最後の要素の1つ後ろの位置です。

*結果*\
一連の合計または指定した演算の結果が格納されるターゲット範囲の最初の要素を示す出力反復子。

*初期化*\
*Binary_op*を使用して各要素が追加または結合される初期値。

*binary_op*\
指定された範囲内の各要素に適用する二項演算と、以前のアプリケーションの結果。

### <a name="return-value"></a>戻り値

ターゲット範囲の末尾を示す出力反復子: *result* + (*last* - *first*)。

## <a name="gcd"></a>gcd

M と n の整数の最大公約数を計算します。

```cpp
template <class M, class N>
constexpr common_type_t<M,N> gcd(M m, N n);
```

### <a name="parameters"></a>パラメーター

*m*、 *n*\
整数型の値。

### <a name="return-value"></a>戻り値

*M*と*n*の絶対値の最大公約数を返します。 *m*と*n*の両方が0の場合は0を返します。 *M*または*n*の絶対値が `common_type_t<M,N>`型の値として表現できない場合、結果は未定義になります。

## <a name="inclusive_scan"></a>inclusive_scan

初期値を指定して、範囲に対して `std::plus<>()` または指定した二項演算子のいずれかを使用して、包括プレフィックスの合計操作を計算します。 指定したコピー先で始まる範囲に結果を書き込みます。 *包括プレフィックス*合計は *、n 番目の*入力要素が*n*番目の合計に含まれることを意味します。 実行ポリシー引数を含むオーバーロードは、指定したポリシーに従って実行されます。

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template<class InputIterator, class OutputIterator, class BinaryOperation>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class Type>
OutputIterator inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryOperation, class Type>
ForwardIterator2 inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    Type init);
```

### <a name="parameters"></a>パラメーター

*exec*\
実行ポリシー。

*最初*の \
*Binary_op*を使用して合計または結合する範囲内の最初の要素を示す入力反復子。

*最後*の \
*Binary_op*を使用して合計または結合する範囲内の最後の要素を示す入力反復子。これは、反復累積に実際に含まれる最後の要素の1つ後ろの位置です。

*結果*\
一連の合計または指定した演算の結果が格納されるターゲット範囲の最初の要素を示す出力反復子。

*初期化*\
*Binary_op*を使用して各要素が追加または結合される初期値。

*binary_op*\
指定された範囲内の各要素に適用する二項演算と、以前のアプリケーションの結果。

### <a name="return-value"></a>戻り値

ターゲット範囲の末尾を示す出力反復子: *result* + (*last* - *first*)。

## <a name="inner_product"></a>inner_product

2 つの範囲の要素ごとの積の合計を計算し、それを指定された初期値に加算するか、または和や積の二項演算が指定された別の二項演算に置き換えられた汎用化されたプロシージャの結果を計算します。

```cpp
template <class InputIterator1, class InputIterator2, class Type>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init);

template <class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type inner_product(
    InputIterator1   first1,
    InputIterator1   last1,
    InputIterator2   first2,
    Type             init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);
```

### <a name="parameters"></a>パラメーター

*first1* \
2 番目の範囲との内積または一般化された内積を計算する必要がある、1 番目の範囲内の先頭の要素を示す入力反復子。

*last1* \
2 番目の範囲との内積または一般化された内積を計算する必要がある、1 番目の範囲内の最後の要素を示す入力反復子。

*first2* \
1 番目の範囲との内積または一般化された内積を計算する必要がある、2 番目の範囲内の先頭の要素を示す入力反復子。

*初期化*\
範囲間の内積または一般化された内積を追加する必要がある初期値。

*binary_op1*\
内積の一般化における要素ごとの内積に適用される内積の合計演算を置き換える二項演算。

*binary_op2*\
内積の一般化における内積の要素ごとの乗算演算を置き換える二項演算。

### <a name="return-value"></a>戻り値

1 番目のメンバー関数は、要素ごとの積の合計を返し、それを指定された初期値に追加します。 したがって、*a*i と *b*i の値の範囲の場合、次を返します。

*init* + (*a*1 \* *b*1) + (*a*2 \* *b*2) +... + (*a*n \* *b*n)

*init*を*init* + (*a*i \* *b*i) に繰り返し置換する。

2 番目のメンバー関数は次を返します。

*init* *binary_op1* (*a*1 *binary_op2* *b*1) *binary_op1* (*a*2 *binary_op2* *b*2) *binary_op1* ...*binary_op1* (*a*n *binary_op2* *b*n)

*init*を*init* *binary_op1* (*a*i *binary_op2* *b*i) に繰り返し置換する。

### <a name="remarks"></a>Remarks

初期値は、範囲が空の場合に、適切に定義された結果があることを保証します。 その場合は、 *init*が返されます。 二項演算は、結合または可換的である必要はありません。 範囲は有効である必要があり、複雑さは範囲のサイズに比例します。 2 項演算子の戻り値の型は、反復中のクロージャを確実にするために、**Type** に変換可能である必要があります。

### <a name="example"></a>例

```cpp
// numeric_inner_prod.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main()
{
   using namespace std;

   vector <int> v1, v2(7), v3(7);
   vector <int>::iterator iter1, iter2, iter3;

   int i;
   for (i = 1; i <= 7; i++)
   {
      v1.push_back(i);
   }

   cout << "The original vector v1 is:\n ( " ;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
      cout << *iter1 << " ";
   cout << ")." << endl;

   list <int> l1, l2(7);
   list <int>::iterator lIter1, lIter2;

   int t;
   for (t = 1; t <= 7; t++)
   {
      l1.push_back(t);
   }

   cout << "The original list l1 is:\n ( " ;
   for (lIter1 = l1.begin(); lIter1 != l1.end(); lIter1++)
      cout << *lIter1 << " ";
   cout << ")." << endl;

   // The first member function for the inner product
   int inprod;
   inprod = inner_product(v1.begin(), v1.end(), l1.begin(), 0);

   cout << "The inner_product of the vector v1 and the list l1 is: "
        << inprod << "." << endl;

   // Constructing a vector of partial inner_products between v1 & l1
   int j = 0, parinprod;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++) {
      parinprod = inner_product(v1.begin(), iter1 + 1, l1.begin(), 0);
      v2[j] = parinprod;
      j++;
   }

   cout << "Vector of partial inner_products between v1 & l1 is:\n ( " ;
   for (iter2 = v2.begin(); iter2 != v2.end(); iter2++)
      cout << *iter2 << " ";
   cout << ")." << endl << endl;

   // The second member function used to compute
   // the product of the element-wise sums
   int inprod2;
   inprod2 = inner_product (v1.begin(), v1.end(),
      l1.begin(), 1, multiplies<int>(), plus<int>());

   cout << "The sum of the element-wise products of v1 and l1 is: "
        << inprod2 << "." << endl;

   // Constructing a vector of partial sums of element-wise products
   int k = 0, parinprod2;
   for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
   {
      parinprod2 =
         inner_product(v1.begin(), iter1 + 1, l1.begin(), 1,
         multiplies<int>(), plus<int>());
      v3[k] = parinprod2;
      k++;
   }

   cout << "Vector of partial sums of element-wise products is:\n ( " ;
   for (iter3 = v3.begin(); iter3 != v3.end(); iter3++)
      cout << *iter3 << " ";
   cout << ")." << endl << endl;
}
```

## <a name="iota"></a>イオータ

最初の要素から開始値を格納し、その値の連続する値 (`value++`) を `[first,  last)`間隔の各要素に入力します。

```cpp
template <class ForwardIterator, class Type>
void iota(ForwardIterator first, ForwardIterator last, Type value);
```

### <a name="parameters"></a>パラメーター

*最初*の \
入力する必要がある、範囲内の先頭の要素を示す入力反復子。

*最後*の \
入力する必要がある、範囲内の最後の要素を示す入力反復子。

*value*\
最初の要素に格納し、後の要素に対して連続してインクリメントする開始値。

### <a name="example"></a>例

次の例は、`iota` 関数のいくつかの使用法を示しています。整数の [list](../standard-library/list.md) を入力し、次に、[vector](../standard-library/vector.md) に `list` を入力することで、[random_shuffle](../standard-library/algorithm-functions.md#random_shuffle) 関数を使用できます。

```cpp
// compile by using: cl /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <numeric>
#include <list>
#include <vector>
#include <iostream>

using namespace std;

int main(void)
{
    list <int> intList(10);
    vector <list<int>::iterator> intVec(intList.size());

    // Fill the list
    iota(intList.begin(), intList.end(), 0);

    // Fill the vector with the list so we can shuffle it
    iota(intVec.begin(), intVec.end(), intList.begin());

    random_shuffle(intVec.begin(), intVec.end());

    // Output results
    cout << "Contents of the integer list: " << endl;
    for (auto i: intList) {
        cout << i << ' ';
    }
    cout << endl << endl;

    cout << "Contents of the integer list, shuffled by using a vector: " << endl;
    for (auto i: intVec) {
        cout << *i << ' ';
    }
    cout << endl;
}
```

## <a name="lcm"></a>lcm

```cpp
template <class M, class N>
constexpr common_type_t<M,N> lcm(M m, N n);
```

## <a name="partial_sum"></a>partial_sum

最初の要素から*n*番目の要素までの入力範囲に含まれる一連の合計を計算し、その各合計の結果をターゲット範囲の*n*番目の要素に格納します。 またはは、sum 操作が別の指定された二項演算に置き換えられた一般化されたプロシージャの結果を計算します。

```cpp
template <class InputIterator, class OutIt>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result);

template <class InputIterator, class OutIt, class Fn2>
OutputIterator partial_sum(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>パラメーター

*最初*の \
指定された二項演算に従って、部分的に合計または結合される範囲内の先頭の要素を示す入力反復子。

*最後*の \
指定された二項演算に従って、部分的に合計または結合される範囲内の最後の要素、つまり反復処理され累積に実際に含まれる最後の要素の 1 つ次の位置を示す入力反復子。

*結果*\
一連の部分合計を格納するターゲット範囲の最初の要素、または指定された二項演算の連続する結果を示す出力反復子。

*binary_op*\
部分和プロシージャの合計演算を置き換える、一般化された操作で適用する二項演算。

### <a name="return-value"></a>戻り値

ターゲット範囲の末尾を示す出力反復子: *result* + (*last* - *first*)。

### <a name="remarks"></a>Remarks

出力反復子の*結果*は、*最初*に入力反復子と同じ反復子にすることができます。そのため、部分的な合計が計算される可能性があります。

値のシーケンスの 1 *、2*、 *.* ..1つ目のテンプレート関数は、入力範囲内*の x を*ターゲット範囲に格納します。 *N*番目の要素は、によって指定され*ます (1*+ *a*2 + *a*3 +... + *a*n)。

入力範囲内の1、a 2、 *3 の*値のシーケンスの場合 *、2番*目のテンプレート関数は、一連の*結果をターゲット*範囲に格納します。 *N*番目の要素は (...((*a*1 *binary_op* *a*2) *binary_op* *a*3)*binary_op* ...)*binary_op* *a*n)。

二項演算*binary_op*は、適用される操作の順序が指定されているため、結合または可換である必要はありません。

### <a name="example"></a>例

```cpp
// numeric_partial_sum.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <numeric>
#include <functional>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> V1( 10 ), V2( 10 );
   vector<int>::iterator VIter1, VIter2, VIterend, VIterend2;

   list <int> L1;
   list <int>::iterator LIter1, LIterend;

   int t;
   for ( t = 1 ; t <= 10 ; t++ )
   {
      L1.push_back( t );
   }

   cout << "The input list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != L1.end( ) ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;

   // The first member function for the partial sums of
   // elements in a list output to a vector
   VIterend = partial_sum ( L1.begin ( ) , L1.end ( ) ,
      V1.begin ( ) );

   cout << "The output vector containing the partial sums is:\n ( " ;
   for ( VIter1 = V1.begin( ) ; VIter1 != VIterend ; VIter1++ )
      cout << *VIter1 << " ";
   cout << ")." << endl;

   // The second member function used to compute
   // the partial product of the elements in a list
   VIterend2 = partial_sum ( L1.begin ( ) , L1.end ( ) , V2.begin ( ) ,
      multiplies<int>( ) );

   cout << "The output vector with the partial products is:\n ( " ;
   for ( VIter2 = V2.begin( ) ; VIter2 != VIterend2 ; VIter2++ )
      cout << *VIter2 << " ";
   cout << ")." << endl;

   // Computation of partial sums in place
   LIterend = partial_sum ( L1.begin ( ) , L1.end ( ) , L1.begin ( ) );
   cout << "The in place output partial_sum list L1 is:\n ( " ;
   for ( LIter1 = L1.begin( ) ; LIter1 != LIterend ; LIter1++ )
      cout << *LIter1 << " ";
   cout << ")." << endl;
}
```

## <a name="reduce"></a>落とし

任意の変えるの順序で合計を計算することによって、指定された範囲のすべての要素を減らします (初期値を含む場合もあります)。 または、指定された二項演算の結果を計算することで、を減らします。 実行ポリシー引数を含むオーバーロードは、指定したポリシーに従って実行されます。

```cpp
template<class InputIterator>
typename iterator_traits<InputIterator>::value_type reduce(
    InputIterator first,
    InputIterator last);

template<class InputIterator, class Type>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init);

template<class InputIterator, class Type, class BinaryOperation>
Type reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op);

template<class ExecutionPolicy, class ForwardIterator>
typename iterator_traits<ForwardIterator>::value_type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Type>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation>
Type reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>パラメーター

*exec*\
実行ポリシー。

*最初*の \
*Binary_op*を使用して合計または結合する範囲内の最初の要素を示す入力反復子。

*最後*の \
*Binary_op*を使用して合計または結合する範囲内の最後の要素を示す入力反復子。これは、反復累積に実際に含まれる最後の要素の1つ後ろの位置です。

*結果*\
一連の合計または指定した演算の結果が格納されるターゲット範囲の最初の要素を示す出力反復子。

*初期化*\
*Binary_op*を使用して各要素が追加または結合される初期値。

*binary_op*\
指定された範囲内の各要素に適用する二項演算と、以前のアプリケーションの結果。

### <a name="return-value"></a>戻り値

*Binary_op*または `std::plus<>()` を、 *init*に適用し、指定された範囲のすべての要素を (* partialresult, *in_iter*) に適用した結果。 *partialresult*は、操作の以前のアプリケーションの結果であり、 *in_iter*は、範囲内の要素を指す反復子です。 *Init*を指定しないオーバーロードでは、使用される*init*値は `typename iterator_traits<InputIterator>::value_type{}`に相当します。

### <a name="remarks"></a>Remarks

`reduce` の動作は、 *binary_op*が連想と可換でない限り、非決定的です。 Binary_op によって要素が変更された場合、動作は未定義になります。または、 *first*, *last*] の \[間隔で反復子を無効にします。

## <a name="transform_exclusive_scan"></a>transform_exclusive_scan

指定した単項演算子を使用して範囲の要素を変換します。次に、初期値を指定して、`std::plus<>()` または指定した二項演算子を範囲に対して使用して、排他的プレフィックスの合計演算を実行します。 指定したコピー先で始まる範囲に結果を書き込みます。 *排他的プレフィックス*合計は、n*番目*の入力要素が*n*番目の合計に含まれていないことを意味します。 実行ポリシー引数を含むオーバーロードは、指定したポリシーに従って実行されます。 合計は任意の順序で実行できます。

```cpp
template<class InputIterator, class OutputIterator, class Type, class BinaryOperation, class UnaryOperation>
OutputIterator transform_exclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_exclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>パラメーター

*exec*\
実行ポリシー。

*最初*の \
*Binary_op*を使用して合計または結合する範囲内の最初の要素を示す入力反復子。

*最後*の \
*Binary_op*を使用して合計または結合する範囲内の最後の要素を示す入力反復子。これは、反復累積に実際に含まれる最後の要素の1つ後ろの位置です。

*結果*\
一連の合計または指定した演算の結果が格納されるターゲット範囲の最初の要素を示す出力反復子。

*初期化*\
*Binary_op*を使用して各要素が追加または結合される初期値。

*binary_op*\
指定された範囲内の各要素に適用する二項演算と、以前のアプリケーションの結果。

*unary_op*\
指定された範囲内の各要素に適用する単項演算。

## <a name="transform_inclusive_scan"></a>transform_inclusive_scan

指定した単項演算子を使用して範囲の要素を変換した後、初期値を使用して、`std::plus<>()` または指定した二項演算子を範囲に対して使用して、包括プレフィックスの合計操作を計算します。 指定したコピー先で始まる範囲に結果を書き込みます。 *包括プレフィックス*合計は *、n 番目の*入力要素が*n*番目の合計に含まれることを意味します。 実行ポリシー引数を含むオーバーロードは、指定したポリシーに従って実行されます。 合計は任意の順序で実行できます。

```cpp
template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class InputIterator, class OutputIterator, class BinaryOperation, class UnaryOperation, class Type>
OutputIterator transform_inclusive_scan(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryOperation, class UnaryOperation, class Type>
ForwardIterator2 transform_inclusive_scan(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryOperation binary_op,
    UnaryOperation unary_op,
    Type init);
```

### <a name="parameters"></a>パラメーター

*exec*\
実行ポリシー。

*最初*の \
*Binary_op*を使用して合計または結合する範囲内の最初の要素を示す入力反復子。

*最後*の \
*Binary_op*を使用して合計または結合する範囲内の最後の要素を示す入力反復子。これは、反復累積に実際に含まれる最後の要素の1つ後ろの位置です。

*結果*\
一連の合計または指定した演算の結果が格納されるターゲット範囲の最初の要素を示す出力反復子。

*binary_op*\
指定された範囲内の各要素に適用する二項演算と、以前のアプリケーションの結果。

*unary_op*\
指定された範囲内の各要素に適用する単項演算。

*初期化*\
*Binary_op*を使用して各要素が追加または結合される初期値。

## <a name="transform_reduce"></a>transform_reduce

要素の範囲を変換し、変換された要素を任意の順序で縮小するファンクタを適用します。 実質的には、`transform` の後に `reduce`が続きます。

```cpp
template<class InputIterator1, class InputIterator2, class Type>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init);

template<class InputIterator1, class InputIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class InputIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    InputIterator first,
    InputIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type, class BinaryOperation1, class BinaryOperation2>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    Type init,
    BinaryOperation1 binary_op1,
    BinaryOperation2 binary_op2);

template<class ExecutionPolicy, class ForwardIterator, class Type, class BinaryOperation, class UnaryOperation>
Type transform_reduce(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Type init,
    BinaryOperation binary_op,
    UnaryOperation unary_op);
```

### <a name="parameters"></a>パラメーター

*exec*\
実行ポリシー。

*最初*の \
*Binary_op*を使用して合計または結合する範囲内の最初の要素を示す入力反復子。

*first1* \
*Binary_op1*を使用して合計または結合する範囲内の最初の要素を示す入力反復子。

*最後*の \
*Binary_op*を使用して合計または結合する範囲内の最後の要素を示す入力反復子。これは、反復累積に実際に含まれる最後の要素の1つ後ろの位置です。

*last1* \
*Binary_op1*を使用して合計または結合する範囲内の最後の要素を示す入力反復子。これは、反復累積に実際に含まれる最後の要素の1つ後ろの位置です。

*結果*\
一連の合計または指定した演算の結果が格納されるターゲット範囲の最初の要素を示す出力反復子。

*初期化*\
*Binary_op*を使用して各要素が追加または結合される初期値。

*binary_op*\
指定された範囲内の各要素に適用する二項演算と、以前のアプリケーションの結果。

*unary_op*\
指定された範囲内の各要素に適用する単項演算。

### <a name="return-value"></a>戻り値

変換後の結果が減少します。
