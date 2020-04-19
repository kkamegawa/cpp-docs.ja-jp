---
title: タプル クラス
ms.date: 11/04/2016
f1_keywords:
- tuple/std::tuple
- tuple/std::tuple::operator=
helpviewer_keywords:
- tuple class
ms.assetid: c38749be-ae4d-41f3-98ea-6aa3250de9a3
ms.openlocfilehash: 9890a6a9dea1671f14b66897a80f4b49861dff2b
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257105"
---
# <a name="tuple-class"></a>タプル クラス

要素の固定長シーケンスをラップします。

## <a name="syntax"></a>構文

```cpp
class tuple {
   tuple();
   explicit tuple(P1, P2, ..., PN); // 0 < N
   tuple(const tuple&);
   template <class U1, class U2, ..., class UN>
      tuple(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>
      tuple(const pair<U1, U2>&); // N == 2

   void swap(tuple& right);
   tuple& operator=(const tuple&);
   template <class U1, class U2, ..., class UN>
      tuple& operator=(const tuple<U1, U2, ..., UN>&);
   template <class U1, class U2>
      tuple& operator=(const pair<U1, U2>&); // N == 2
};
```

### <a name="parameters"></a>パラメーター

*TN*\
N 番目の tuple 要素の型。

## <a name="remarks"></a>コメント

クラステンプレートは、`T1`、`T2`、...、`TN`の型の N 個のオブジェクトをそれぞれ `0 <= N <= Nmax`で格納するオブジェクトを表します。 `tuple<T1, T2, ..., TN>` 組インスタンスの範囲は、そのテンプレート引数の `N` 数です。 テンプレート引数の `Ti` と、その型の対応する格納値のインデックスが `i - 1`ます。 このドキュメントでは、1から N の型に番号を付けますが、対応するインデックス値の範囲は 0 ~ N-1 です。

## <a name="example"></a>例

```cpp
// tuple.cpp
// compile with: /EHsc

#include <vector>
#include <iomanip>
#include <iostream>
#include <tuple>
#include <string>

using namespace std;

typedef tuple <int, double, string> ids;

void print_ids(const ids& i)
{
   cout << "( "
        << get<0>(i) << ", "
        << get<1>(i) << ", "
        << get<2>(i) << " )." << endl;
}

int main( )
{
   // Using the constructor to declare and initialize a tuple
   ids p1(10, 1.1e-2, "one");

   // Compare using the helper function to declare and initialize a tuple
   ids p2;
   p2 = make_tuple(10, 2.22e-1, "two");

   // Making a copy of a tuple
   ids p3(p1);

   cout.precision(3);
   cout << "The tuple p1 is: ( ";
   print_ids(p1);
   cout << "The tuple p2 is: ( ";
   print_ids(p2);
   cout << "The tuple p3 is: ( ";
   print_ids(p3);

   vector<ids> v;

   v.push_back(p1);
   v.push_back(p2);
   v.push_back(make_tuple(3, 3.3e-2, "three"));

   cout << "The tuples in the vector are" << endl;
   for(vector<ids>::const_iterator i = v.begin(); i != v.end(); ++i)
   {
      print_ids(*i);
   }
}
```

```Output
The tuple p1 is: ( 10, 0.011, one ).
The tuple p2 is: ( 10, 0.222, two ).
The tuple p3 is: ( 10, 0.011, one ).
The tuples in the vector are
( 10, 0.011, one ).
( 10, 0.222, two ).
( 3, 0.033, three ).
```

## <a name="op_eq"></a>operator =

`tuple` オブジェクトを割り当てます。

```cpp
tuple& operator=(const tuple& right);

template <class U1, class U2, ..., class UN>
   tuple& operator=(const tuple<U1, U2, ..., UN>& right);

template <class U1, class U2>
   tuple& operator=(const pair<U1, U2>& right); // N == 2

tuple& operator=(tuple&& right);

template <class U1, class U2>
   tuple& operator=(pair<U1, U2>&& right);
```

### <a name="parameters"></a>パラメーター

\ の*解除*
N 番目のコピーされたタプル要素の型。

*右*\
コピー元のタプル。

### <a name="remarks"></a>コメント

最初の2つのメンバー演算子は、*右*の要素を `*this`の対応する要素に代入します。 3 番目のメンバー演算子は、`right.first` のインデックス 0 位置の要素に `*this` を割り当て、インデックス 1 の要素に `right.second` を割り当てます。 これらの 3 つすべてのメンバー演算子は、`*this` を返します。

残りのメンバー演算子はそれ以前のコンストラクターと似ていますが、[Rvalue 参照宣言子: &&](../cpp/rvalue-reference-declarator-amp-amp.md) を使用します。

### <a name="example"></a>例

```cpp
// std__tuple__tuple_operator_as.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>
#include <utility>

typedef std::tuple<int, double, int, double> Mytuple;
int main()
    {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1;
    c1 = c0;

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c1);
    std::cout << " " << std::get<1>(c1);
    std::cout << " " << std::get<2>(c1);
    std::cout << " " << std::get<3>(c1);
    std::cout << std::endl;

    std::tuple<char, int> c2;
    c2 = std::make_pair('x', 4);

// display contents " x 4"
    std::cout << " " << std::get<0>(c2);
    std::cout << " " << std::get<1>(c2);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
x 4
```

## <a name="tuple_swap"></a>フォト

2 つのタプルの要素を交換します。

```cpp
template <class... Types>
   void swap(tuple<Types...&> left, tuple<Types...&> right);
```

### <a name="parameters"></a>パラメーター

*左*\
要素が組*right*の要素と交換される組。

*右*\
要素が*左*の組の要素と交換される組。

### <a name="remarks"></a>コメント

この関数は、`left.swap(right)` を実行します。

## <a name="tuple"></a>タプル

`tuple` オブジェクトを構築します。

```cpp
constexpr tuple();
explicit constexpr tuple(const Types&...);
template <class... UTypes>
   explicit constexpr tuple(UTypes&&...);

tuple(const tuple&) = default;
tuple(tuple&&) = default;

template <class... UTypes>
   constexpr tuple(const tuple<UTypes...>&);
template <class... UTypes>
   constexpr tuple(tuple<UTypes...>&&);

// only if sizeof...(Types) == 2
template <class U1, class U2>
   constexpr tuple(const pair<U1, U2>&);
template <class U1, class U2>
   constexpr tuple(pair<U1, U2>&&);
```

### <a name="parameters"></a>パラメーター

\ の*解除*
N 番目のコピーされたタプル要素の型。

*右*\
コピー元のタプル。

### <a name="remarks"></a>コメント

1 つ目のコンストラクターは、要素が既定で構築されるオブジェクトを構築します。

2 番目のコンス トラクターは、引数 `P1`、`P2`...`PN` に基づいて構築されるコピーを要素とするオブジェクトを構築します。これらの `Pi` は、インデックス `i - 1` で要素を初期化します。

3番目と4番目のコンストラクターは、*右*の対応する要素から構築されたコピーを要素として持つオブジェクトを構築します。

5 番目のコンストラクターは、インデックス 0 の要素が `right.first` から構築されたコピーで、インデックス 1 の要素が `right.second` から構築されたコピーであるオブジェクトを構築します。

残りのコンストラクターはそれ以前のコンストラクターと似ていますが、[Rvalue 参照宣言子: &&](../cpp/rvalue-reference-declarator-amp-amp.md) を使用します。

### <a name="example"></a>例

```cpp
// std__tuple__tuple_tuple.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>
#include <utility>

typedef std::tuple<int, double, int, double> Mytuple;
int main()
{
    Mytuple c0(0, 1, 2, 3);

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0);
    std::cout << std::endl;

    Mytuple c1;
    c1 = c0;

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c1) << " ";
    std::cout << std::get<1>(c1) << " ";
    std::cout << std::get<2>(c1) << " ";
    std::cout << std::get<3>(c1);
    std::cout << std::endl;

    std::tuple<char, int> c2(std::make_pair('x', 4));

    // display contents "x 4"
    std::cout << std::get<0>(c2) << " ";
    std::cout << std::get<1>(c2);
    std::cout << std::endl;

    Mytuple c3(c0);

    // display contents "0 1 2 3"
    std::cout << std::get<0>(c3) << " ";
    std::cout << std::get<1>(c3) << " ";
    std::cout << std::get<2>(c3) << " ";
    std::cout << std::get<3>(c3);
    std::cout << std::endl;

    typedef std::tuple<int, float, int, float> Mytuple2;
    Mytuple c4(Mytuple2(4, 5, 6, 7));

    // display contents "4 5 6 7"
    std::cout << std::get<0>(c4) << " ";
    std::cout << std::get<1>(c4) << " ";
    std::cout << std::get<2>(c4) << " ";
    std::cout << std::get<3>(c4);
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
x 4
0 1 2 3
4 5 6 7
```
