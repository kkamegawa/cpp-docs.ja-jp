---
title: '&lt;tuple&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- tuple/std::get
- tuple/std::make_tuple
- tuple/std::tie
ms.assetid: bc6be38f-5258-4c14-b81b-63caa335fd44
helpviewer_keywords:
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
- std::get [C++]
- std::make_tuple [C++]
- std::tie [C++]
ms.openlocfilehash: 46c386ecffb8fbbf7c07d40b334afd91d261ebcf
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241672"
---
# <a name="lttuplegt-functions"></a>&lt;tuple&gt; 関数

## <a name="apply"></a> 適用します。

```cpp
template <class F, class Tuple> constexpr decltype(auto) apply(F&& f, Tuple&& t);
```

### <a name="remarks"></a>Remarks

関数を呼び出す*F* 、タプルで*t*します。

## <a name="forward"></a> forward_as_tuple

```cpp
template <class... TTypes>
    constexpr tuple<TTypes&&...> forward_as_tuple(TTypes&&...) noexcept;
```

### <a name="return-value"></a>戻り値

`tuple<TTypes&&...>(std::forward<TTypes>(t)...)` を返します。

### <a name="remarks"></a>Remarks

引数への参照の組を構築します*t*関数に引数として転送用に適しています。

## <a name="get"></a> 取得

`tuple` オブジェクトから、インデックスまたは (C++14 の場合は) 型別に要素を取得します。

```cpp
// by index:
// get reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>& get(tuple<Types...>& Tuple) noexcept;

// get const reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr const tuple_element_t<Index, tuple<Types...>>& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to Index element of tuple
template <size_t Index, class... Types>
   constexpr tuple_element_t<Index, tuple<Types...>>&& get(tuple<Types...>&& Tuple) noexcept;

// (C++14) by type:
// get reference to T element of tuple
template <class T, class... Types>
   constexpr T& get(tuple<Types...>& Tuple) noexcept;

// get const reference to T element of tuple
template <class T, class... Types>
   constexpr const T& get(const tuple<Types...>& Tuple) noexcept;

// get rvalue reference to T element of tuple
template <class T, class... Types>
   constexpr T&& get(tuple<Types...>&& Tuple) noexcept;
```

### <a name="parameters"></a>パラメーター

*インデックス*\
取得する要素のインデックス。

*型*\
タプルで宣言された型のシーケンス (宣言順)。

*T*\
取得する要素の型。

*タプル*\
A`std::tuple`任意の数の要素を格納しています。

### <a name="remarks"></a>Remarks

テンプレート関数は、インデックス位置にある値への参照を返す*インデックス*、または型の*T*で、`tuple`オブジェクト。

タプルに含まれる型 T の要素の数が 1 より大きいか小さい場合、 `get<T>(Tuple)` を呼び出すと、コンパイラ エラーが生成されます。

### <a name="example"></a>例

```cpp
#include <tuple>
#include <iostream>
#include <string>

using namespace std;

int main() {
    tuple<int, double, string> tup(0, 1.42, "Call me Tuple");

    // get elements by index
    cout << " " << get<0>(tup);
    cout << " " << get<1>(tup);
    cout << " " << get<2>(tup) << endl;

    // get elements by type
    cout << " " << get<int>(tup);
    cout << " " << get<double>(tup);
    cout << " " << get<string>(tup) << endl;
}
```

```Output
0 1.42 Call me Tuple
0 1.42 Call me Tuple
```

## <a name="make_from_tuple"></a> make_from_tuple

```cpp
template <class T, class Tuple> constexpr T make_from_tuple(Tuple&& t);
```

### <a name="remarks"></a>Remarks

`return make_from_tuple_impl<T>(forward<Tuple>(t), make_index_sequence<tuple_size_v<decay_t<Tuple>>>{})` と同じ。

## <a name="make_tuple"></a> make_tuple

要素値から `tuple` を作成します。

```cpp
template <class T1, class T2, ..., class TN>
   tuple<V1, V2, ..., VN> make_tuple(const T1& t1, const T2& t2, ..., const TN& tN);
```

### <a name="parameters"></a>パラメーター

*TN*\
N 番目の関数パラメーターの型。

*TN*\
N 番目の関数パラメーターの値。

### <a name="remarks"></a>Remarks

このテンプレート関数は `tuple<V1, V2, ..., VN>(t1, t2, ..., tN)` を返します。ここで、各 `Vi` 型は、対応する `Ti` 型が `cv` `reference_wrapper<X>` である場合は `X&`、それ以外の場合は `Ti` になります。

`make_tuple` の利点の 1 つは、格納されるオブジェクトの型がコンパイラによって自動的に決定され、明示的に指定する必要がないことです。 `make_tuple<int, int>(1, 2)` を使用する場合は、`make_tuple` などの明示的なテンプレート引数を使用しないでください。これは、不必要に詳細になり、複雑な右辺値参照の問題が追加され、コンパイル エラーの原因となる可能性があるためです。

### <a name="example"></a>例

```cpp
// std__tuple__make_tuple.cpp
// compile by using: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    c0 = std::make_tuple(4, 5, 6, 7);

// display contents " 4 5 6 7"
    std::cout << std::get<0>(c0) << " ";
    std::cout << std::get<1>(c0) << " ";
    std::cout << std::get<2>(c0) << " ";
    std::cout << std::get<3>(c0) << std::endl;

    return (0);
}
```

```Output
0 1 2 3
4 5 6 7
```

## <a name="swap"></a> スワップ

```cpp
template <class... Types>
    void swap(tuple<Types...>& x, tuple<Types...>& y) noexcept(see below );
```

## <a name="tie"></a> 同順位

要素参照から `tuple` を作成します。

```cpp
template <class T1, class T2, ..., class TN>
tuple<T1&, T2&, ..., TN&> tie(T1& t1, T2& t2, ..., TN& tN);
```

### <a name="parameters"></a>パラメーター

*TN*\
N 番目の tuple 要素の基本データ型。

### <a name="remarks"></a>Remarks

このテンプレート関数は `tuple<T1&, T2&, ..., TN&>(t1, t2, ..., tN)` を返します。

### <a name="example"></a>例

```cpp
// std__tuple__tie.cpp
// compile with: /EHsc
#include <tuple>
#include <iostream>

typedef std::tuple<int, double, int, double> Mytuple;
int main() {
    Mytuple c0(0, 1, 2, 3);

// display contents " 0 1 2 3"
    std::cout << " " << std::get<0>(c0);
    std::cout << " " << std::get<1>(c0);
    std::cout << " " << std::get<2>(c0);
    std::cout << " " << std::get<3>(c0);
    std::cout << std::endl;

    int v4 = 4;
    double v5 = 5;
    int v6 = 6;
    double v7 = 7;
    std::tie(v4, v5, v6, v7) = c0;

// display contents " 0 1 2 3"
    std::cout << " " << v4;
    std::cout << " " << v5;
    std::cout << " " << v6;
    std::cout << " " << v7;
    std::cout << std::endl;

    return (0);
}
```

```Output
0 1 2 3
0 1 2 3
```

## <a name="tuple_cat"></a> tuple_cat

```cpp
template <class... Tuples> constexpr tuple<CTypes...> tuple_cat(Tuples&&...);
```

### <a name="return-value"></a>戻り値

各型の要素を初期化することによって構築された組オブジェクトです。

## <a name="tuple_element_t"></a> tuple_element_t

```cpp
template <size_t I, class T>
    using tuple_element_t = typename tuple_element<I, T>::type;
```

## <a name="tuple_size_v"></a> tuple_size_v

```cpp
template <class T>
    inline constexpr size_t tuple_size_v = tuple_size<T>::value;
```
