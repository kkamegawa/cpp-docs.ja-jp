---
title: integer_sequence クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::index_sequence
- type_traits/std::make_index_sequence
- type_traits/std::integer_sequence
- type_traits/std::make_integer_sequence
- type_traits/std::index_sequence_for
helpviewer_keywords:
- std::index_sequence
- std::make_index_sequence
- std::integer_sequence
- std::make_integer_sequence
- std::index_sequence_for
ms.assetid: 2cfdddee-819d-478e-bb78-c8a9c2696803
ms.openlocfilehash: ca923933ac7a401f6a3ef14f821ceb04b844797b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451021"
---
# <a name="integersequence-class"></a>integer_sequence クラス

整数のシーケンスを表します。 このクラスを使用して、関数に引数として渡される std::tuple\<T...> などの可変個引数型のパラメーター パックを推測および拡大できます。

## <a name="syntax"></a>構文

```cpp
template <class T, T... Vals>
struct integer_sequence
```

### <a name="parameters"></a>パラメーター

*\T*\
値の型。整数型である必要があります (bool、char、char16_t、char32_t、wchar_t、符号付きまたは符号なしの整数型)。

*Vals*\
整数型 T の値のシーケンスを表す非型パラメーター パック。

## <a name="members"></a>メンバー

|||
|-|-|
|`static size_t size() noexcept`|シーケンス内の要素の数。|
|`typedef T value_type`|シーケンス内の各要素の型。 整数型である必要があります。|

## <a name="remarks"></a>Remarks

関数に直接渡されるパラメーター パックは、特別なライブラリ ヘルパーなしでアンパックできます。 パラメーター パックが関数に渡される型の一部であるときに要素にアクセスするためにインデックスが必要な場合、これをアンパックする最も簡単な方法は、`integer_sequence` とその関連する型のエイリアス `make_integer_sequence`、`index_sequence`、`make_index_sequence`、`index_sequence_for` を使用する方法です。

## <a name="example"></a>例

次の例は、[N3658](http://open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html) に関する記事を原案としています。 この例では、`integer_sequence` を使用して `std::array<T,N>` から `std::tuple` を作成する方法と、`integer_sequence` を使用してタプルのメンバーにアクセスする方法を示しています。

`a2t` 関数の `index_sequence` は、`size_t` 整数型に基づく `integer_sequence` のエイリアスです。 `make_index_sequence` は、0 から始まり、呼び出し元によって渡される配列と同じ数の要素を持つ `index_sequence` をコンパイル時に作成するエイリアスです。 `a2t` は値によって `index_sequence` を `a2t_` に渡します。ここで、式 `a[I]...` により `I` がアンパックされ、要素が `make_tuple` に渡されます。ここで、要素が個々の引数として使用されます。 たとえば、シーケンスに 3 つの要素が含まれる場合、`make_tuple` は make_tuple(a[0], a[1], a[2]) として呼び出されます。 もちろん、配列の要素は任意の型を持つことができます。

Apply 関数は、 [std:: tuple](../standard-library/tuple-class.md)を受け取り、 `integer_sequence` `tuple_size`ヘルパークラスを使用してを生成します。 [Tuple_size](../standard-library/tuple-size-class-tuple.md)は参照型では動作しないため、 [std::d ecay_t](../standard-library/decay-class.md)が必要であることに注意してください。 `apply_` 関数がタプルのメンバーをアンパックし、別個の引数として関数呼び出しに転送します。 この例の関数は、値を印刷する単純なラムダ式です。

```cpp
#include <stddef.h>
#include <iostream>
#include <tuple>
#include <utility>
#include <array>
#include <string>

using namespace std;

// Create a tuple from the array and the index_sequence
template<typename Array, size_t... I>
auto a2t_(const Array& a, index_sequence<I...>)
{
    return make_tuple(a[I]...);
}

// Create an index sequence for the array, and pass it to the
// implementation function a2t_
template<typename T, size_t N>
auto a2t(const array<T, N>& a)
{
    return a2t_(a, make_index_sequence<N>());
}

// Call function F with the tuple members as separate arguments.
template<typename F, typename Tuple = tuple<T...>, size_t... I>
decltype(auto) apply_(F&& f, Tuple&& args, index_sequence<I...>)
{
    return forward<F>(f)(get<I>(forward<Tuple>(args))...);
}

// Create an index_sequence for the tuple, and pass it with the
// function object and the tuple to the implementation function apply_
template<typename F, typename Tuple = tuple<T...>>
decltype(auto) apply(F&& f, Tuple&& args)
{
    using Indices = make_index_sequence<tuple_size<decay_t<Tuple>>::value >;
    return apply_(forward<F>(f), forward<Tuple>(args), Indices());
}

int main()
{
    const array<string, 3> arr { "Hello", "from", "C++14" };

    //Create a tuple given a array
    auto tup = a2t(arr);

    // Extract the tuple elements
    apply([](const string& a, const string& b, const string& c) {cout << a << " " << b << " " << c << endl; }, tup);

    char c;
    cin >> c;
}
```

`index_sequence` をパラメーター パック用に設定するために `index_sequence_for`\<T...> を使用していますが、これは `make_index_sequence`\<sizeof...(T)> のエイリアスです。

## <a name="requirements"></a>必要条件

ヘッダー: \<type_traits\>

名前空間: std

## <a name="see-also"></a>関連項目

[省略記号と可変個引数テンプレート](../cpp/ellipses-and-variadic-templates.md)
