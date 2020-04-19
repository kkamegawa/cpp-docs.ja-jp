---
title: '&lt;algorithm&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- algorithm/std::adjacent_find
- algorithm/std::all_of
- algorithm/std::any_of
- algorithm/std::binary_search
- algorithm/std::copy
- algorithm/std::copy_backward
- algorithm/std::copy_if
- algorithm/std::copy_n
- algorithm/std::equal
- algorithm/std::equal_range
- algorithm/std::fill
- algorithm/std::fill_n
- algorithm/std::find
- algorithm/std::find_end
- algorithm/std::find_first_of
- algorithm/std::find_if
- algorithm/std::find_if_not
- algorithm/std::for_each
- algorithm/std::generate
- algorithm/std::generate_n
- algorithm/std::includes
- algorithm/std::inplace_merge
- algorithm/std::is_heap
- algorithm/std::is_heap_until
- algorithm/std::is_partitioned
- algorithm/std::is_permutation
- algorithm/std::is_sorted
- algorithm/std::is_sorted_until
- algorithm/std::iter_swap
- algorithm/std::lexicographical_compare
- algorithm/std::lower_bound
- algorithm/std::make_heap
- algorithm/std::max
- algorithm/std::max_element
- algorithm/std::merge
- algorithm/std::min
- algorithm/std::minmax
- algorithm/std::minmax_element
- algorithm/std::min_element
- algorithm/std::mismatch
- algorithm/std::move
- algorithm/std::move_backward
- algorithm/std::next_permutation
- algorithm/std::none_of
- algorithm/std::nth_element
- algorithm/std::partial_sort
- algorithm/std::partial_sort_copy
- algorithm/std::partition
- algorithm/std::partition_point
- algorithm/std::pop_heap
- algorithm/std::prev_permutation
- algorithm/std::push_heap
- algorithm/std::random_shuffle
- algorithm/std::remove
- algorithm/std::remove_copy
- algorithm/std::remove_copy_if
- algorithm/std::remove_if
- algorithm/std::replace
- algorithm/std::replace_copy
- algorithm/std::replace_copy_if
- algorithm/std::replace_if
- algorithm/std::reverse
- algorithm/std::reverse_copy
- algorithm/std::rotate
- algorithm/std::rotate_copy
- algorithm/std::search
- algorithm/std::search_n
- algorithm/std::set_difference
- algorithm/std::set_intersection
- algorithm/std::set_symmetric_difference
- algorithm/std::set_union
- algorithm/std::shuffle
- algorithm/std::sort
- algorithm/std::sort_heap
- algorithm/std::stable_partition
- algorithm/std::stable_sort
- algorithm/std::swap_ranges
- algorithm/std::transform
- algorithm/std::unique
- algorithm/std::unique_copy
- algorithm/std::upper_bound
- xutility/std::copy
- xutility/std::copy_backward
- xutility/std::copy_n
- xutility/std::count
- xutility/std::equal
- xutility/std::fill
- xutility/std::fill_n
- xutility/std::find
- xutility/std::is_permutation
- xutility/std::lexicographical_compare
- xutility/std::move
- xutility/std::move_backward
- xutility/std::reverse
- xutility/std::rotate
- algorithm/std::count_if
- algorithm/std::partition_copy
- algorithm/std::swap
ms.assetid: c10b0c65-410c-4c83-abf8-8b7f61bba8d0
helpviewer_keywords:
- std::adjacent_find [C++]
- std::all_of [C++]
- std::any_of [C++]
- std::binary_search [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_if [C++]
- std::copy_n [C++]
- std::equal [C++]
- std::equal_range [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::find_end [C++]
- std::find_first_of [C++]
- std::find_if [C++]
- std::find_if_not [C++]
- std::for_each [C++]
- std::generate [C++]
- std::generate_n [C++]
- std::includes [C++]
- std::inplace_merge [C++]
- std::is_heap [C++]
- std::is_heap_until [C++]
- std::is_partitioned [C++]
- std::is_permutation [C++]
- std::is_sorted [C++]
- std::is_sorted_until [C++]
- std::iter_swap [C++]
- std::lexicographical_compare [C++]
- std::lower_bound [C++]
- std::make_heap [C++]
- std::max [C++]
- std::max_element [C++]
- std::merge [C++]
- std::min [C++]
- std::minmax [C++]
- std::minmax_element [C++]
- std::min_element [C++]
- std::mismatch [C++]
- std::move [C++]
- std::move_backward [C++]
- std::next_permutation [C++]
- std::none_of [C++]
- std::nth_element [C++]
- std::partial_sort [C++]
- std::partial_sort_copy [C++]
- std::partition [C++]
- std::partition_point [C++]
- std::pop_heap [C++]
- std::prev_permutation [C++]
- std::push_heap [C++]
- std::random_shuffle [C++]
- std::remove [C++]
- std::remove_copy [C++]
- std::remove_copy_if [C++]
- std::remove_if [C++]
- std::replace [C++]
- std::replace_copy [C++]
- std::replace_copy_if [C++]
- std::replace_if [C++]
- std::reverse [C++]
- std::reverse_copy [C++]
- std::rotate [C++]
- std::rotate_copy [C++]
- std::search [C++]
- std::search_n [C++]
- std::set_difference [C++]
- std::set_intersection [C++]
- std::set_symmetric_difference [C++]
- std::set_union [C++]
- std::shuffle [C++]
- std::sort [C++]
- std::sort_heap [C++]
- std::stable_partition [C++]
- std::stable_sort [C++]
- std::swap_ranges [C++]
- std::transform [C++]
- std::unique [C++]
- std::unique_copy [C++]
- std::upper_bound [C++]
- std::copy [C++]
- std::copy_backward [C++]
- std::copy_n [C++]
- std::count [C++]
- std::equal [C++]
- std::fill [C++]
- std::fill_n [C++]
- std::find [C++]
- std::is_permutation [C++]
- std::lexicographical_compare [C++]
- std::move [C++]
- std::move_backward [C++]
- std::reverse [C++]
- std::rotate [C++]
- std::count_if [C++]
- std::partition_copy [C++]
- std::swap [C++]
ms.openlocfilehash: 199634997397cca0008c60843b5d977633277331
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821884"
---
# <a name="ltalgorithmgt-functions"></a>&lt;algorithm&gt; 関数

## <a name="adjacent_find"></a>adjacent_find

等しいか、または指定された条件を満たす 2 個の隣接する要素を検索します。

```cpp
template<class ForwardIterator>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator , class BinaryPredicate>
ForwardIterator adjacent_find(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator adjacent_find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
検索範囲内の先頭の要素の位置を示す前方反復子。

*最後*の\
検索範囲の最後の要素の 1 つ後ろの位置を示す前方反復子。

*pred*\
検索範囲内の隣接する要素の値によって満たされる条件を提供する二項述語。

### <a name="return-value"></a>戻り値

このような要素のペアが見つかった場合に、互いに等しい (最初のバージョンでは)、または二項述語によって指定された条件を満たす、隣接する要素の1番目の反復子。 それ以外の場合は、 *last*を指す反復子が返されます。

### <a name="remarks"></a>コメント

`adjacent_find` アルゴリズムは、変化しないシーケンス アルゴリズムです。 検索範囲が有効であり、すべてのポインターが逆参照可能であって、かつ先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。 アルゴリズムの時間の複雑さは、範囲に含まれる要素の数に比例します。

要素間の一致を判断するために使用される `operator==` によって、そのオペランド間の等価関係関係が強制される必要があります。

### <a name="example"></a>使用例

```cpp
// alg_adj_fnd.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

// Returns whether second element is twice the first
bool twice (int elem1, int elem2 )
{
    return elem1 * 2 == elem2;
}

int main()
{
    using namespace std;
    list<int> L;
    list<int>::iterator Iter;
    list<int>::iterator result1, result2;

    L.push_back( 50 );
    L.push_back( 40 );
    L.push_back( 10 );
    L.push_back( 20 );
    L.push_back( 20 );

    cout << "L = ( " ;
    for ( Iter = L.begin( ) ; Iter != L.end( ) ; Iter++ )
        cout << *Iter << " ";
    cout << ")" << endl;

    result1 = adjacent_find( L.begin( ), L.end( ) );
    if ( result1 == L.end( ) )
        cout << "There are not two adjacent elements that are equal."
            << endl;
    else
        cout << "There are two adjacent elements that are equal.\n"
            << "They have a value of "
            << *( result1 ) << "." << endl;

    result2 = adjacent_find( L.begin( ), L.end( ), twice );
    if ( result2 == L.end( ) )
        cout << "There are not two adjacent elements where the "
            << "second is twice the first." << endl;
    else
    {
        cout << "There are two adjacent elements where "
            << "the second is twice the first.\n"
            << "They have values of " << *(result2++)
            << " & " << *result2 << "." << endl;
    }
}
```

```Output
L = ( 50 40 10 20 20 )
There are two adjacent elements that are equal.
They have a value of 20.
There are two adjacent elements where the second is twice the first.
They have values of 10 & 20.
```

## <a name="all_of"></a>all_of

指定された範囲内の各要素に条件が存在する場合に**true**を返します。

```cpp
template<class InputIterator, class UnaryPredicate>
bool all_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool all_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
条件のチェックを開始する位置を示す入力反復子。 反復子は、要素の範囲の開始位置をマークします。

*最後*の\
条件をチェックする要素の範囲の終了を示す入力反復子。

*pred*\
テストする条件。 これは、チェックされる要素によって満たされる条件を定義するユーザー定義の述語関数オブジェクトです。 単項述語は1つの引数を取り、 **true**または**false**を返します。

### <a name="return-value"></a>戻り値

指定された範囲内の各要素で条件が検出された場合、または範囲が空の場合は**true**を返し、それ以外の場合は**false**を返します。

### <a name="remarks"></a>コメント

このテンプレート関数は、`[0, last - first)`範囲内の各 `N` に対して、述語 `pred(*(first + N))` が**true**の場合にのみ**true**を返します。

### <a name="example"></a>使用例

```cpp
// alg_all_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 50, 40, 10, 20, 20 };
    list<int>::iterator iter;

    cout << "li = ( ";
    for (iter = li.begin(); iter != li.end(); iter++)
        cout << *iter << " ";
    cout << ")" << endl;

    // Check if all elements in li are even.
    auto is_even = [](int elem){ return !(elem % 2); };
    if (all_of(li.begin(), li.end(), is_even))
        cout << "All the elements are even numbers.\n";
    else
        cout << "Not all the elements are even numbers.\n";
}
```

```Output
li = ( 50 40 10 20 20 )
All the elements are even numbers.
```

## <a name="any_of"></a>any_of

指定された要素の範囲内に条件が1回以上存在する場合に**true**を返します。

```cpp
template<class InputIterator, class UnaryPredicate>
bool any_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool any_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
条件の要素の範囲のチェックを開始する位置を示す入力反復子。

*最後*の\
条件をチェックする要素の範囲の終了を示す入力反復子。

*pred*\
テストする条件。 これは、ユーザー定義の述語関数オブジェクトによって提供されます。 述語は、テスト対象の要素によって満たされる条件を定義します。 単項述語は1つの引数を取り、 **true**または**false**を返します。

### <a name="return-value"></a>戻り値

指定された範囲で少なくとも1回条件が検出された場合は**true**を返します。条件が検出されない場合は**false**を返します。

### <a name="remarks"></a>コメント

このテンプレート関数は、範囲内の `N` の場合にのみ**true**を返します。

`[0, last - first)`、述語 `pred(*(first + N))` は true です。

### <a name="example"></a>使用例

```cpp
// alg_any_of.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;

    list<int> li { 51, 41, 11, 21, 20 };

    cout << "li = ( ";
    for (auto const& el : li)
        cout << el << " ";
    cout << ")" << endl;

    // Check if there is an even elememt in li.
    auto is_even = [](int const elem){ return !(elem % 2); };
    if (any_of(li.begin(), li.end(), is_even))
        cout << "There's an even element in li.\n";
    else
        cout << "There are no even elements in li.\n";
}
```

```Output
li = ( 51 41 11 21 20 )
There's an even element in li.
```

## <a name="binary_search"></a>binary_search

並べ替えられた範囲に、指定された値と等しい要素が存在するか、または二項述語で指定された意味で、指定された値と等価の要素が存在するかどうかをテストします。

```cpp
template<class ForwardIterator, class Type>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class BinaryPredicate>
bool binary_search(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*最初*の\
検索範囲内の先頭の要素の位置を示す前方反復子。

*最後*の\
検索範囲の最後の要素の 1 つ後ろの位置を示す前方反復子。

*value*\
要素の値が一致する必要がある値、または二項述語で指定された要素の値によって条件を満たす必要がある値。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="return-value"></a>戻り値

指定した値と等しいか等しい範囲内に要素が見つかった場合は**true** 。それ以外の場合は**false**。

### <a name="remarks"></a>コメント

参照される並べ替えられたソースの範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

`binary_search` アルゴリズムを適用するための事前条件として、それぞれの並べ替えられた範囲は、結合された範囲の並べ替えにアルゴリズムが使用したのと同じ順序の基準に従って並べ替えられている必要があります。

ソースの範囲は `binary_search` によって変更されません。

前方反復子の値の型は、小なり (less-than) 比較ができる必要があります。これにより、2 個の要素が与えられたときに、それらが等しいか (いずれも他方より小さくない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます

アルゴリズムの複雑さは、ランダムアクセス反復子の場合は対数、それ以外の場合は (`last` - `first`) のステップ数に比例して線形的になります。

### <a name="example"></a>使用例

```cpp
// alg_bin_srch.cpp
// compile with: /EHsc
#include <list>
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    list<int> List1;

    List1.push_back( 50 );
    List1.push_back( 10 );
    List1.push_back( 30 );
    List1.push_back( 20 );
    List1.push_back( 25 );
    List1.push_back( 5 );

    List1.sort();

    cout << "List1 = ( " ;
    for ( auto Iter : List1 )
        cout << Iter << " ";
    cout << ")" << endl;

    // default binary search for 10
    if ( binary_search(List1.begin(), List1.end(), 10) )
        cout << "There is an element in list List1 with a value equal to 10."
        << endl;
    else
        cout << "There is no element in list List1 with a value equal to 10."
        << endl;

    // a binary_search under the binary predicate greater
    List1.sort(greater<int>());
    if ( binary_search(List1.begin(), List1.end(), 10, greater<int>()) )
        cout << "There is an element in list List1 with a value greater than 10 "
        << "under greater than." << endl;
    else
        cout << "No element in list List1 with a value greater than 10 "
        << "under greater than." << endl;

    // a binary_search under the user-defined binary predicate mod_lesser
    vector<int> v1;

    for ( auto i = -2; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    sort(v1.begin(), v1.end(), mod_lesser);

    cout << "Ordered using mod_lesser, vector v1 = ( " ;
    for ( auto Iter : v1 )
        cout << Iter << " ";
    cout << ")" << endl;

    if ( binary_search(v1.begin(), v1.end(), -3, mod_lesser) )
        cout << "There is an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
    else
        cout << "There is not an element with a value equivalent to -3 "
        << "under mod_lesser." << endl;
}
```

```Output
List1 = ( 5 10 20 25 30 50 )
There is an element in list List1 with a value equal to 10.
There is an element in list List1 with a value greater than 10 under greater than.
Ordered using mod_lesser, vector v1 = ( 0 -1 1 -2 2 3 4 )
There is an element with a value equivalent to -3 under mod_lesser.
```

## <a name="clamp"></a>クリップ

値を上限および下限と比較し、値が境界の間にある場合はその値への参照を返します。値が上または下にある場合は下限または下限を返します。

```cpp
template<class Type>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper);

template<class Type, class Compare>
constexpr const Type& clamp(
    const Type& value,
    const Type& lower,
    const Type& upper,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*value*\
*Upper*と*lower*の比較対象の値。

*下*\
*値*がクランプされる値の下限。

*上限*\
*値*がクランプされる値の上限。

*pred*\
*値*を*下*または*上*に比較するために使用される述語。 比較述語は2つの引数を受け取り、最初の値が2番目の意味を持つ場合は**true** 、それ以外の場合は**false**を返します。

### <a name="return-value"></a>戻り値

`value < lower`の場合は*下位*への参照を返し、`upper < value`の場合は*upper*への参照を返します。 それ以外の場合は、 *value*への参照を返します。

### <a name="remarks"></a>コメント

*Upper*の値が*低い*場合、動作は未定義です。

## <a name="copy"></a>copy

要素のソース シーケンス全体を繰り返し、順方向の新しい位置を割り当てて、ソース範囲内からターゲットの範囲に要素の値を割り当てます。

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator copy(
    InputIterator first,
    InputIterator last,
    OutputIterator destBeg);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
ソース範囲内の先頭の要素の位置を示す入力反復子。

*最後*の\
ソース範囲内の最後の要素の 1 つ後ろの位置を示す入力反復子。

*destBeg*\
ターゲット範囲の最初の要素の位置を示す出力反復子。

### <a name="return-value"></a>戻り値

ターゲット範囲の最後の要素の1つ後ろの位置を示す出力反復子。つまり、反復子が `result` + (*最後*の - *最初*の)。

### <a name="remarks"></a>コメント

ソース範囲内が有効で、コピーするすべての要素を保持する十分な領域がターゲットに必要です。

アルゴリズムは最初の要素で始まる順序でソース要素をコピーするため、ソース範囲の*最後*の位置がターゲット範囲に含まれていない場合、ターゲット範囲はソース範囲と重複する可能性があります。 `copy` は、ソースとターゲットの範囲間に重複がない場合を除き、要素を左にシフトするために使用できますが、右側には移動できません。 任意の位置の数だけ右にシフトにするには、[copy_backward](../standard-library/algorithm-functions.md#copy_backward) アルゴリズムを使用します。

`copy` アルゴリズムは、反復子が指す値のみを変更し、ターゲット範囲の要素に新しい値を割り当てます。 これは、新しい要素の作成には使用できず、空のコンテナーに要素を直接挿入することはできません。

### <a name="example"></a>使用例

```cpp
// alg_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1.push_back( 10 * i );

    int ii;
    for ( ii = 0 ; ii <= 10 ; ii++ )
        v2.push_back( 3 * ii );

    cout << "v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To copy the first 3 elements of v1 into the middle of v2
    copy( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 4 );

    cout << "v2 with v1 insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To shift the elements inserted into v2 two positions
    // to the left
    copy( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 2 );

    cout << "v2 with shifted insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;
}
```

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 0 10 20 10 20 21 24 27 30 )
```

## <a name="copy_backward"></a>copy_backward

要素のソース シーケンス全体を繰り返し、逆方向の新しい位置を割り当てて、ソース範囲内からターゲットの範囲に要素の値を割り当てます。

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 copy_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>パラメーター

*最初*の\
ソース範囲内の先頭の要素の位置を示す双方向反復子。

*最後*の\
ソース範囲の最後の要素の 1 つ後ろの位置を示す双方向反復子。

*Destend*\
移動先範囲の最後の要素の 1 つ後ろの位置を示す双方向反復子。

### <a name="return-value"></a>戻り値

ターゲット範囲の最後の要素の1つ後ろの位置を示す出力反復子。つまり、反復子は*Destend* (*last* - *first*) をアドレス指定します。

### <a name="remarks"></a>コメント

ソース範囲内が有効で、コピーするすべての要素を保持する十分な領域がターゲットに必要です。

`copy_backward` アルゴリズムは、`copy` アルゴリズムよりも厳しい要件を課します。 入力反復子と出力反復子はどちらも、双方向である必要があります。

`copy_backward` と [move_backward](../standard-library/algorithm-functions.md#move_backward) のアルゴリズムは、ターゲット範囲の末尾を指す反復子の出力範囲を指定する唯一の C++ 標準ライブラリのアルゴリズムです。

アルゴリズムは最後の要素で始まる順序でソース要素をコピーするため、ソース範囲の*最初*の位置がターゲット範囲に含まれていない場合、ターゲット範囲はソース範囲と重複する可能性があります。 `copy_backward` は要素を右にシフトするために使用できますが、ソースとターゲットの範囲間に重複がない場合を除いて、左にはシフトできません。 任意の位置の数だけ左にシフトにするには、[copy](../standard-library/algorithm-functions.md#copy) アルゴリズムを使用します。

`copy_backward` アルゴリズムは、反復子が指す値のみを変更し、ターゲット範囲の要素に新しい値を割り当てます。 これは、新しい要素の作成には使用できず、空のコンテナーに要素を直接挿入することはできません。

### <a name="example"></a>使用例

```cpp
// alg_copy_bkwd.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 5 ; ++i )
        v1.push_back( 10 * i );

    int ii;
    for ( ii = 0 ; ii <= 10 ; ++ii )
        v2.push_back( 3 * ii );

    cout << "v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; ++Iter1 )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To copy_backward the first 3 elements of v1 into the middle of v2
    copy_backward( v1.begin( ), v1.begin( ) + 3, v2.begin( ) + 7 );

    cout << "v2 with v1 insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // To shift the elements inserted into v2 two positions
    // to the right
    copy_backward( v2.begin( )+4, v2.begin( ) + 7, v2.begin( ) + 9 );

    cout << "v2 with shifted insert = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")" << endl;
}
```

```Output
v1 = ( 0 10 20 30 40 50 )
v2 = ( 0 3 6 9 12 15 18 21 24 27 30 )
v2 with v1 insert = ( 0 3 6 9 0 10 20 21 24 27 30 )
v2 with shifted insert = ( 0 3 6 9 0 10 0 10 20 27 30 )
```

## <a name="copy_if"></a>copy_if

要素の範囲内で、指定した条件に**該当**する要素をコピーします。

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator dest,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
条件をチェックする範囲の先頭を指定する入力反復子。

*最後*の\
範囲の終了位置を示す入力反復子。

*dest*\
コピーした要素のコピー先を示す出力反復子。

*pred*\
範囲内のすべての要素がテストされる条件。 この条件は、ユーザー定義の述語関数オブジェクトによって提供されます。 単項述語は1つの引数を受け取り、 **true**または**false**を返します。

### <a name="return-value"></a>戻り値

条件を満たす各要素について、 *dest*が1回インクリメントされる出力反復子。 言い換えると、戻り値から*dest*を引いた値は、コピーされた要素の数と同じになります。

### <a name="remarks"></a>コメント

このテンプレート関数は、

`if (pred(*first + N)) * dest++ = *(first + N))`

を `[0, last - first)` の範囲で、各 `N` に対して 1 回評価し、`N` の値を最低値から厳密に 1 ずつ増やします。 *Dest*と*最初*にストレージの領域を指定する場合は、 *dest*を `[ first, last )`の範囲に含めることはできません。

### <a name="example"></a>使用例

```cpp
// alg_copy_if.cpp
// compile with: /EHsc
#include <list>
#include <algorithm>
#include <iostream>

void listlist(std::list<int> l)
{
    std::cout << "( ";
    for (auto const& el : l)
        std::cout << el << " ";
    std::cout << ")" << std::endl;
}

int main()
{
    using namespace std;
    list<int> li{ 46, 59, 88, 72, 79, 71, 60, 5, 40, 84 };
    list<int> le(li.size()); // le = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };
    list<int> lo(li.size()); // lo = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    cout << "li = ";
    listlist(li);

    // is_even checks if the element is even.
    auto is_even = [](int const elem) { return !(elem % 2); };
    // use copy_if to select only even elements from li 
    // and copy them to le, starting from le's begin position
    auto ec = copy_if(li.begin(),li.end(), le.begin(), is_even);
    le.resize(std::distance(le.begin(), ec));  // shrink le to new size

    cout << "Even numbers are le = ";
    listlist(le);

    // is_odd checks if the element is odd.
    auto is_odd = [](int const elem) { return (elem % 2); };
    // use copy_if to select only odd elements from li
    // and copy them to lo, starting from lo's begin position
    auto oc = copy_if(li.begin(), li.end(), lo.begin(), is_odd);
    lo.resize(std::distance(lo.begin(), oc));  // shrink lo to new size

    cout << "Odd numbers are lo = ";
    listlist(lo);
}
```

```Output
li = ( 46 59 88 72 79 71 60 5 40 84 )
Even numbers are le = ( 46 88 72 60 40 84 )
Odd numbers are lo = ( 59 79 71 5 )
```

## <a name="copy_n"></a>copy_n

指定された数の要素をコピーします。

```cpp
template<class InputIterator, class Size, class OutputIterator>
OutputIterator copy_n(
    InputIterator first,
    Size count,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class Size, class ForwardIterator2>
ForwardIterator2 copy_n(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    Size count,
    ForwardIterator2 dest);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
要素のコピー元となる場所を示す入力反復子。

*カウント*\
コピーする要素の数を指定する符号付きまたは符号なし整数型。

*dest*\
要素のコピー先となる場所を示す出力反復子。

### <a name="return-value"></a>戻り値

要素のコピー先となった場所を示す出力反復子を返します。 これは、 *dest*パラメーターの戻り値と同じです。

### <a name="remarks"></a>コメント

このテンプレート関数は、`[0, count)`範囲内の各 `N` に対して `*(dest + N) = *(first + N))` を1回評価します。これにより、`N` の値が最小値から厳密に増加します。 その後で `dest + N` が返されます。 *Dest*と*最初*にストレージの領域を指定する場合は、 *dest*を `[first, last)`の範囲に含めることはできません。

### <a name="example"></a>使用例

```cpp
// alg_copy_n.cpp
// compile with: cl /EHsc /W4 alg_copy_n.cpp
#include <algorithm>
#include <iostream>
#include <string>

int main()
{
    using namespace std;
    string s1{"dandelion"};
    string s2{"badger"};

    cout << s1 << " + " << s2 << " = ";

    // Copy the first 3 letters from s1
    // to the first 3 positions in s2
    copy_n(s1.begin(), 3, s2.begin());

    cout << s2 << endl;
}
```

```Output
dandelion + badger = danger
```

## <a name="count"></a>数

範囲内で値が指定された値と一致する要素の数を返します。

```cpp
template<class InputIterator, class Type>
typename iterator_traits<InputIterator>::difference_type count(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
typename iterator_traits<ForwardIterator>::difference_type
count(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
走査範囲内の最初の要素の位置を示す入力反復子。

*最後*の\
走査範囲内の最後の要素の 1 つ後ろの位置を示す入力反復子。

*value*\
カウントされる要素の値。

### <a name="return-value"></a>戻り値

値の*値*を持つ範囲 [*first*, *last*) 内の要素の数をカウントする `InputIterator` の差の型。

### <a name="remarks"></a>コメント

要素と指定された値の間の一致を判断するために使用される `operator==` によって、オペランド間の等価関係が強制される必要があります。

このアルゴリズムは、テンプレート関数 [count_if](../standard-library/algorithm-functions.md#count_if) を使用してすべての述語を満たす要素をカウントするために汎用化されます。

### <a name="example"></a>使用例

```cpp
// alg_count.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( " ;
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result;
    result = count(v1.begin(), v1.end(), 10);
    cout << "The number of 10s in v2 is: " << result << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of 10s in v2 is: 3.
```

## <a name="count_if"></a>count_if

範囲内で値が指定された条件を満たす要素の数を返します。

```cpp
template<class InputIterator, class UnaryPredicate>
typename iterator_traits<InputIterator>::difference_type count_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
typename iterator_traits<ForwardIterator>::difference_type
count_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
検索範囲内の最初の要素の位置を示す入力反復子。

*最後*の\
検索範囲内の最後の要素の 1 つ後ろの位置を示す入力反復子。

*pred*\
要素がカウントされる場合に満たされる条件を定義するユーザー定義の述語関数オブジェクト。 単項述語は1つの引数を取り、 **true**または**false**を返します。

### <a name="return-value"></a>戻り値

述語で指定された条件を満たす要素の数。

### <a name="remarks"></a>コメント

このテンプレート関数は、アルゴリズム [count](../standard-library/algorithm-functions.md#count) を汎化したものであり、"特定の値に等しい" ことを示す述語を任意の述語に置き換えます。

### <a name="example"></a>使用例

```cpp
// alg_count_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater10(int value)
{
    return value > 10;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(10);
    v1.push_back(40);
    v1.push_back(10);

    cout << "v1 = ( ";
    for (Iter = v1.begin(); Iter != v1.end(); Iter++)
        cout << *Iter << " ";
    cout << ")" << endl;

    vector<int>::iterator::difference_type result1;
    result1 = count_if(v1.begin(), v1.end(), greater10);
    cout << "The number of elements in v1 greater than 10 is: "
         << result1 << "." << endl;
}
```

```Output
v1 = ( 10 20 10 40 10 )
The number of elements in v1 greater than 10 is: 2.
```

## <a name="equal"></a>つの

二項述語によって指定された等値または等価について、2 つの範囲を要素ごとに比較します。

異なる種類のコンテナー (たとえば `vector` と `list`) 内の要素を比較する場合、異なる要素型を比較する場合、またはコンテナー内のサブ範囲を比較する必要がある場合は、`std::equal` を使用します。 そうではなく、同じ種類のコンテナー内の同じ型の要素を比較する場合は、各コンテナーによって提供される非メンバーの `operator==` を使用します。

C++14 コードでは 2 範囲のオーバーロードを使用します。これは、2 つ目の範囲に対して 1 つの反復子のみを受け取るオーバーロードでは、2 つ目の範囲が 1 つ目の範囲より大きい場合にその差を検出できず、2 つ目の範囲が 1 つ目の範囲より小さい場合に未定義の動作が発生するためです。

```cpp
template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred); // C++14

template<class InputIterator1, class InputIterator2>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class BinaryPredicate>
bool equal(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool equal(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
テストする 1 つ目の範囲内の最初の要素の位置を示す入力反復子。

*last1*\
テストする 1 つ目の範囲内の最後の要素の 1 つ後の位置を示す入力反復子。

*first2*\
テストする 2 つ目の範囲内の最初の要素の位置を示す入力反復子。

*last2*\
テストする 2 つ目の範囲内の最後の要素の 1 つ後の位置を示す入力反復子。

*pred*\
2 つの要素が等価であると見なされた場合に条件が満たされると定義する、ユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="return-value"></a>戻り値

二項述語の下で、要素ごとに比較したとき、範囲が同一または等価の場合に限り **true**。それ以外の場合は **false**。

### <a name="remarks"></a>コメント

検索対象の範囲が有効であること、すべての反復子が逆参照可能であること、さらに先頭位置からのインクリメントにより最後の位置に到達可能であることが必要です。

2 つの範囲の長さが等しい場合、アルゴリズムの時間の複雑さは、範囲に含まれる要素の数に比例します。 それ以外の場合、関数は直ちに**false**を返します。

`operator==` でもユーザー定義の述語でも、そのオペランド間で対称的、再帰的、および推移的な等価関係を強制する必要はありません。

### <a name="example"></a>使用例

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main()
{
    vector<int> v1 { 0, 5, 10, 15, 20, 25 };
    vector<int> v2 { 0, 5, 10, 15, 20, 25 };
    vector<int> v3 { 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50 };

    // Using range-and-a-half equal:
    bool b = equal(v1.begin(), v1.end(), v2.begin());
    cout << "v1 and v2 are equal: "
       << b << endl; // true, as expected

    b = equal(v1.begin(), v1.end(), v3.begin());
    cout << "v1 and v3 are equal: "
       << b << endl; // true, surprisingly

    // Using dual-range equal:
    b = equal(v1.begin(), v1.end(), v3.begin(), v3.end());
    cout << "v1 and v3 are equal with dual-range overload: "
       << b << endl; // false

    return 0;
}
```

## <a name="equal_range"></a>equal_range

順序付けられた対象範囲で、すべての要素が指定された値と等価であるサブ範囲を検索します。

```cpp
template<class ForwardIterator, class Type>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
pair<ForwardIterator, ForwardIterator> equal_range(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*最初*の\
検索範囲内の先頭の要素の位置を示す前方反復子。

*最後*の\
検索範囲の最後の要素の 1 つ後ろの位置を示す前方反復子。

*value*\
順序付けられた範囲内で検索する値。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 比較述語は2つの引数を受け取り、満たされた場合は**true**を返し、満たされていない場合は**false**を返します。

### <a name="return-value"></a>戻り値

検索対象の範囲内に含まれる、サブ範囲を指定する前方反復子のペア。すべての要素は、使用される二項述語によって定義された意味の*値*に相当します ( *pred*または既定値未満)。

範囲内の要素が*value*と等価でない場合、戻り値のペアの前方反復子は等しいため、範囲の順序には関係なく、*値*を挿入できる位置を指定します。

### <a name="remarks"></a>コメント

アルゴリズムによって返されるペアの 1 番目の反復子は [lower_bound](../standard-library/algorithm-functions.md#lower_bound) で、2 番目の反復子は [upper_bound](../standard-library/algorithm-functions.md#upper_bound) です。

対象範囲は `equal_range` に提供される述語に従って並べ替えられている必要があります。 たとえば、大なり (greater-than) 述語を使用する場合は、範囲を降順に並べ替える必要があります。

`equal_range` によって返される反復子のペアによって定義される、空の可能性があるサブ範囲の要素は、使用される述語によって定義される意味の*値*と同じになります。

アルゴリズムの複雑さは、ランダムアクセス反復子の場合は対数、それ以外の場合はに比例するステップ数 (*最後* - *最初*) です。

### <a name="example"></a>使用例

```cpp
// alg_equal_range.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>()
#include <iostream>
#include <string>
using namespace std;

template<class T> void dump_vector( const vector<T>& v, pair<typename vector<T>::iterator, typename vector<T>::iterator> range )
{
    // prints vector v with range delimited by [ and ]

    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        if ( i == range.first )
        {
            cout << "[ ";
        }
        if ( i == range.second )
        {
            cout << "] ";
        }

        cout << *i << " ";
    }
    cout << endl;
}

template<class T> void equal_range_demo( const vector<T>& original_vector, T value )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end() );
    cout << "Vector sorted by the default binary predicate <:" << endl << '\t';
    for ( vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<vector<T>::iterator, vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), value );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

template<class T, class F> void equal_range_demo( const vector<T>& original_vector, T value, F pred, string predname )
{
    vector<T> v(original_vector);

    sort( v.begin(), v.end(), pred );
    cout << "Vector sorted by the binary predicate " << predname << ":" << endl << '\t';
    for ( typename vector<T>::const_iterator i = v.begin(); i != v.end(); ++i )
    {
        cout << *i << " ";
    }
    cout << endl << endl;

    pair<typename vector<T>::iterator, typename vector<T>::iterator> result
        = equal_range( v.begin(), v.end(), value, pred );

    cout << "Result of equal_range with value = " << value << ":" << endl << '\t';
    dump_vector( v, result );
    cout << endl;
}

// Return whether absolute value of elem1 is less than absolute value of elem2
bool abs_lesser( int elem1, int elem2 )
{
    return abs(elem1) < abs(elem2);
}

// Return whether string l is shorter than string r
bool shorter_than(const string& l, const string& r)
{
    return l.size() < r.size();
}

int main()
{
    vector<int> v1;

    // Constructing vector v1 with default less than ordering
    for ( int i = -1; i <= 4; ++i )
    {
        v1.push_back(i);
    }

    for ( int i =-3; i <= 0; ++i )
    {
        v1.push_back( i );
    }

    equal_range_demo( v1, 3 );
    equal_range_demo( v1, 3, greater<int>(), "greater" );
    equal_range_demo( v1, 3, abs_lesser, "abs_lesser" );

    vector<string> v2;

    v2.push_back("cute");
    v2.push_back("fluffy");
    v2.push_back("kittens");
    v2.push_back("fun");
    v2.push_back("meowmeowmeow");
    v2.push_back("blah");

    equal_range_demo<string>( v2, "fred" );
    equal_range_demo<string>( v2, "fred", shorter_than, "shorter_than" );
}
```

## <a name="fill"></a>入力

指定された範囲のすべての要素に同じ新しい値を割り当てます。

```cpp
template<class ForwardIterator, class Type>
void fill(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void fill(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
走査対象の範囲内の最初の要素の位置を示す前方反復子。

*最後*の\
走査対象の範囲内の最後の要素の 1 つ後ろの位置を示す前方反復子。

*value*\
範囲 [*first*, *last*) 内の要素に割り当てられる値。

### <a name="remarks"></a>コメント

割り当て先の範囲が有効であり、すべてのポインターが逆参照可能であって、かつ先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。 複雑さは、範囲のサイズに応じて線形的です。

### <a name="example"></a>使用例

```cpp
// alg_fill.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Fill the last 5 positions with a value of 2
    fill( v1.begin( ) + 5, v1.end( ), 2 );

    cout << "Modified v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 30 35 40 45 )
Modified v1 = ( 0 5 10 15 20 2 2 2 2 2 )
```

## <a name="fill_n"></a>fill_n

特定の要素で始まる要素範囲で、指定された数の要素に新しい値を割り当てます。

```cpp
template<class OutputIterator, class Size, class Type>
OutputIterator fill_n(
    OutputIterator first,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator fill_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    const Type& value);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
値*値*が割り当てられる範囲内の最初の要素の位置を示す出力反復子。

*カウント*\
値を代入する要素の数を指定する符号付きまたは符号なし整数の型。

*value*\
範囲 [*first*, *first + count*) の要素に割り当てられる値。

### <a name="return-value"></a>戻り値

*Count* > 0 の場合は、最後の要素の後にある要素への反復子。それ以外の場合は最初の要素。

### <a name="remarks"></a>コメント

割り当て先の範囲が有効であり、すべてのポインターが逆参照可能であって、かつ先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。 複雑さは、範囲のサイズに応じて線形的です。

### <a name="example"></a>使用例

```cpp
// alg_fill_n.cpp
// compile using /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v;

    for ( auto i = 0 ; i < 9 ; ++i )
        v.push_back( 0 );

    cout << " vector v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the first 3 positions with a value of 1, saving position.
    auto pos = fill_n( v.begin(), 3, 1 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the next 3 positions with a value of 2, using last position.
    fill_n( pos, 3, 2 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;

    // Fill the last 3 positions with a value of 3, using relative math.
    fill_n( v.end()-3, 3, 3 );

    cout << "modified v = ( " ;
    for ( const auto &w : v )
        cout << w << " ";
    cout << ")" << endl;
}
```

## <a name="find"></a>探す

範囲内で指定された値を持つ要素が最初に出現する位置を検索します。

```cpp
template<class InputIterator, class Type>
InputIterator find(
    InputIterator first,
    InputIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator find(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
指定された値に対する検索範囲内の先頭の要素の位置を示す入力反復子。

*最後*の\
指定された値に対する検索範囲内の末尾の要素の 1 つ後ろの位置を示す入力反復子。

*value*\
検索対象の値。

### <a name="return-value"></a>戻り値

指定された値が検索範囲内で最初に出現する位置を示す入力反復子。 同等の値を持つ要素が見つからない場合、は*last*を返します。

### <a name="remarks"></a>コメント

要素と指定された値の間の一致を判断するために使用される `operator==` によって、オペランド間の等価関係が強制される必要があります。

`find()` を使用したコード例については、「[find_if](../standard-library/algorithm-functions.md#find_if)」を参照してください。

## <a name="find_end"></a>find_end

範囲内で指定されたシーケンスと等しい、つまり二項述語で指定された意味で等価である最後のサブシーケンスを検索します。

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class Pred>
ForwardIterator1 find_end(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Pred pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_end(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*first1*\
検索範囲内の先頭の要素の位置を示す前方反復子。

*last1*\
検索範囲の最後の要素の 1 つ後ろの位置を示す前方反復子。

*first2*\
検索範囲内の先頭の要素の位置を示す前方反復子。

*last2*\
検索範囲の最後の要素の 1 つ後ろの位置を示す前方反復子。

*pred*\
2 つの要素が等価であると見なされた場合に条件が満たされると定義する、ユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="return-value"></a>戻り値

指定されたシーケンス [first2, last2) に一致する、[first1, last1) 内の最後のサブシーケンスの最初の要素の位置を示す前方反復子。

### <a name="remarks"></a>コメント

要素と指定された値の間の一致を判断するために使用される `operator==` によって、オペランド間の等価関係が強制される必要があります。

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

### <a name="example"></a>使用例

```cpp
// alg_find_end.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
    return 2 * elem1 == elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    int ii;
    for ( ii = 1 ; ii <= 4 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 2 ; iii <= 4 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Searching v1 for a match to L1 under identity
    vector<int>::iterator result1;
    result1 = find_end ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a match of L1 in v1 that begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = find_end ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

    if ( result2 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a sequence of elements in v1 that "
            << "are equivalent to those\n in v2 under the binary "
            << "predicate twice and that begins at position "
            << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 5 10 15 20 )
Vector v2 = ( 20 30 40 )
There is a match of L1 in v1 that begins at position 7.
There is a sequence of elements in v1 that are equivalent to those
in v2 under the binary predicate twice and that begins at position 8.
```

## <a name="find_first_of"></a>find_first_of

対象範囲内で複数の値のうち最初に出現するもの、つまり二項述語で指定された意味で、指定された要素のセットと等価である複数の要素のうち最初に出現するものを検索します。

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 find_first_of(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1,
class ForwardIterator2, class BinaryPredicate>
ForwardIterator1
find_first_of(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*first1*\
検索範囲内の先頭の要素の位置を示す前方反復子。

*last1*\
検索範囲の最後の要素の 1 つ後ろの位置を示す前方反復子。

*first2*\
照合範囲内の先頭の要素の位置を示す前方反復子。

*last2*\
照合範囲の最後の要素の 1 つ後ろの位置を示す前方反復子。

*pred*\
2 つの要素が等価であると見なされた場合に条件が満たされると定義する、ユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="return-value"></a>戻り値

指定したシーケンスと一致するか二項述語で指定された意味で等価である、最初のサブシーケンスの最初の要素の位置を指す前方反復子。

### <a name="remarks"></a>コメント

要素と指定された値の間の一致を判断するために使用される `operator==` によって、オペランド間の等価関係が強制される必要があります。

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

### <a name="example"></a>使用例

```cpp
// alg_find_first_of.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
    return 2 * elem1 == elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    int ii;
    for ( ii = 3 ; ii <= 4 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 2 ; iii <= 4 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Searching v1 for first match to L1 under identity
    vector<int>::iterator result1;
    result1 = find_first_of ( v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = find_first_of ( v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

    if ( result2 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a sequence of elements in v1 that "
            << "are equivalent\n to those in v2 under the binary "
            << "predicate twice\n and the first one begins at position "
            << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 15 20 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
and the first one begins at position 3.
There is a sequence of elements in v1 that are equivalent
to those in v2 under the binary predicate twice
and the first one begins at position 2.
```

## <a name="find_if"></a>find_if

範囲内で指定された条件を満たす要素が最初に出現する位置を検索します。

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*最初*の\
検索範囲内の最初の要素の位置を示す入力反復子。

*最後*の\
検索範囲内の最後の要素の 1 つ後ろの位置を示す入力反復子。

*pred*\
ユーザー定義の述語関数オブジェクト、または検索対象の要素によって満たされる条件を定義する[ラムダ式](../cpp/lambda-expressions-in-cpp.md)。 単項述語は1つの引数を受け取り、満たされた場合は**true**を返し、満たされていない場合は**false**を返します。 *Pred*のシグネチャは、実際には `bool pred(const T& arg);`である必要があります。 `T` は、逆参照するときに `InputIterator` を暗黙的に変換できる型です。 **Const**キーワードは、関数オブジェクトまたはラムダが引数を変更できないことを示すためにのみ表示されます。

### <a name="return-value"></a>戻り値

述語によって指定された条件を満たす範囲内の最初の要素を参照する入力反復子 (述語の結果は**true**になります)。 述語を満たす要素が見つからない場合、は*last*を返します。

### <a name="remarks"></a>コメント

このテンプレート関数は、アルゴリズム [find](../standard-library/algorithm-functions.md#find) を汎化したものであり、"特定の値に等しい" ことを示す述語を任意の述語に置き換えます。 論理的に反対のもの (述語の条件を満たさない最初の要素を検索) については、「[find_if_not](../standard-library/algorithm-functions.md#find_if_not)」を参照してください。

### <a name="example"></a>使用例

```cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <vector>
#include <algorithm>
#include <iostream>
#include <string>

using namespace std;

template <typename S> void print(const S& s) {
for (const auto& p : s) {
        cout << "(" << p << ") ";
    }
    cout << endl;
}

// Test std::find()
template <class InputIterator, class T>
void find_print_result(InputIterator first, InputIterator last, const T& value) {

    // call <algorithm> std::find()
    auto p = find(first, last, value);

    cout << "value " << value;
    if (p == last) {
        cout << " not found." << endl;
    } else {
        cout << " found." << endl;
    }
}

// Test std::find_if()
template <class InputIterator, class Predicate>
void find_if_print_result(InputIterator first, InputIterator last,
    Predicate Pred, const string& Str) {

    // call <algorithm> std::find_if()
    auto p = find_if(first, last, Pred);

    if (p == last) {
        cout << Str << " not found." << endl;
    } else {
        cout << "first " << Str << " found: " << *p << endl;
    }
}

// Function to use as the UnaryPredicate argument to find_if() in this example
bool is_odd_int(int i) {
    return ((i % 2) != 0);
}

int main()
{
    // Test using a plain old array.
    const int x[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
    cout << "array x[] contents: ";
    print(x);
    // Using non-member std::begin()/std::end() to get input iterators for the plain old array.
    cout << "Test std::find() with array..." << endl;
    find_print_result(begin(x), end(x), 10);
    find_print_result(begin(x), end(x), 42);
    cout << "Test std::find_if() with array..." << endl;
    find_if_print_result(begin(x), end(x), is_odd_int, "odd integer"); // function name
    find_if_print_result(begin(x), end(x), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");

    // Test using a vector.
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back((i + 1) * 10);
    }
    cout << endl << "vector v contents: ";
    print(v);
    cout << "Test std::find() with vector..." << endl;
    find_print_result(v.begin(), v.end(), 20);
    find_print_result(v.begin(), v.end(), 12);
    cout << "Test std::find_if() with vector..." << endl;
    find_if_print_result(v.begin(), v.end(), is_odd_int, "odd integer");
    find_if_print_result(v.begin(), v.end(), // lambda
        [](int i){ return ((i % 2) == 0); }, "even integer");
}
```

## <a name="find_if_not"></a>find_if_not

指定された範囲内で条件を満たさない最初の要素を返します。

```cpp
template<class InputIterator, class UnaryPredicate>
InputIterator find_if_not(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator find_if_not(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*最初*の\
検索範囲内の最初の要素の位置を示す入力反復子。

*最後*の\
検索範囲内の最後の要素の 1 つ後ろの位置を示す入力反復子。

*pred*\
検索対象の要素が満たさない条件を定義する、ユーザー定義の述語関数オブジェクトまたは[ラムダ式](../cpp/lambda-expressions-in-cpp.md)。 単項述語は1つの引数を受け取り、満たされた場合は**true**を返し、満たされていない場合は**false**を返します。 *Pred*のシグネチャは、実際には `bool pred(const T& arg);`である必要があります。 `T` は、逆参照するときに `InputIterator` を暗黙的に変換できる型です。 **Const**キーワードは、関数オブジェクトまたはラムダが引数を変更できないことを示すためにのみ表示されます。

### <a name="return-value"></a>戻り値

述語によって指定された条件を満たさない範囲内の最初の要素を参照する入力反復子 (述語は**false**になります)。 すべての要素が述語を満たす場合 (述語はすべての要素に対して**true**になります)、は*last*を返します。

### <a name="remarks"></a>コメント

このテンプレート関数は、アルゴリズム [find](../standard-library/algorithm-functions.md#find) を汎化したものであり、"特定の値に等しい" ことを示す述語を任意の述語に置き換えます。 論理的に反対のもの (述語の条件を満たす最初の要素を検索) については、「[find_if](../standard-library/algorithm-functions.md#find_if)」を参照してください。

`find_if_not()` に簡単に適用できるコード例については、「[find_if](../standard-library/algorithm-functions.md#find_if)」を参照してください。

## <a name="for_each"></a>for_each

範囲内で順方向順序で各要素に対して指定された関数を適用し、関数オブジェクトを返します。

```cpp
template<class InputIterator, class Function>
Function for_each(
    InputIterator first,
    InputIterator last,
    Function func);

template<class ExecutionPolicy, class ForwardIterator, class Function>
void for_each(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Function func);
```

### <a name="parameters"></a>パラメーター

*最初*の\
操作範囲内の最初の要素の位置を示す入力反復子。

*最後*の\
操作範囲内の最後の要素の 1 つ後ろの位置を示す入力反復子。

*func*\
範囲内の各要素に適用されるユーザー定義関数オブジェクト。

### <a name="return-value"></a>戻り値

範囲内のすべての要素に適用後の関数オブジェクトのコピー。

### <a name="remarks"></a>コメント

アルゴリズム `for_each` は非常に柔軟で、範囲内の各要素をユーザーが指定したさまざまな方法で変更できます。 テンプレート化された関数は、異なるパラメーターを渡すことで、変更されたフォームで再利用することができます。 ユーザー定義関数は、範囲内のすべての要素を処理した後にアルゴリズムが返す可能性のある内部状態内に情報を蓄積することができます。

参照される範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

複雑さは線形的で、最大で (*最後* - *最初*) の比較があります。

### <a name="example"></a>使用例

```cpp
// alg_for_each.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
private:
    Type Factor;   // The value to multiply by
public:
    // Constructor initializes the value to multiply by
    MultValue ( const Type& value ) : Factor ( value ) {
    }

    // The function call for the element to be multiplied
    void operator( ) ( Type& elem ) const
    {
        elem *= Factor;
    }
};

// The function object to determine the average
class Average
{
private:
    long num;      // The number of elements
    long sum;      // The sum of the elements
public:
    // Constructor initializes the value to multiply by
    Average( ) : num ( 0 ) , sum ( 0 )
    {
    }

    // The function call to process the next elment
    void operator( ) ( int elem )
    {
        num++;      // Increment the element count
        sum += elem;   // Add the value to the partial sum
    }

    // return Average
    operator double( )
    {
        return static_cast<double> (sum) /
            static_cast<double> (num);
    }
};

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Using for_each to multiply each element by a Factor
    for_each ( v1.begin( ), v1.end( ), MultValue<int> ( -2 ) );

    cout << "Multiplying the elements of the vector v1\n "
            << "by the factor -2 gives:\n v1mod1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // The function object is templatized and so can be
    // used again on the elements with a different Factor
    for_each (v1.begin( ), v1.end( ), MultValue<int> (5 ) );

    cout << "Multiplying the elements of the vector v1mod\n "
            << "by the factor 5 gives:\n v1mod2 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // The local state of a function object can accumulate
    // information about a sequence of actions that the
    // return value can make available, here the Average
    double avemod2 = for_each ( v1.begin( ), v1.end( ),
        Average( ) );
    cout << "The average of the elements of v1 is:\n Average ( v1mod2 ) = "
            << avemod2 << "." << endl;
}
```

```Output
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
Multiplying the elements of the vector v1
by the factor -2 gives:
v1mod1 = ( 8 6 4 2 0 -2 -4 ).
Multiplying the elements of the vector v1mod
by the factor 5 gives:
v1mod2 = ( 40 30 20 10 0 -10 -20 ).
The average of the elements of v1 is:
Average ( v1mod2 ) = 10.
```

## <a name="for_each_n"></a>for_each_n

```cpp
template<class InputIterator, class Size, class Function>
InputIterator for_each_n(
    InputIterator first,
    Size n,
    Function f);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Function>
ForwardIterator for_each_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size n,
    Function f);
```

## <a name="generate"></a>生み

範囲内の各要素に関数オブジェクトによって生成される値を割り当てます。

```cpp
template<class ForwardIterator, class Generator>
void generate(
    ForwardIterator first,
    ForwardIterator last,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Generator>
void generate(
    ExecutionPolicy&& exec,
    ForwardIterator first, ForwardIterator last,
    Generator gen);
```

### <a name="parameters"></a>パラメーター

*最初*の\
値が割り当てられる範囲の最初の要素の位置を示す前方反復子。

*最後*の\
値が割り当てられる範囲の最初の要素の 1 つ後ろの位置を示す前方反復子。

*gen*\
引数を指定しないで呼び出され、範囲内の各要素に割り当てられる値を生成するために使用される関数オブジェクト。

### <a name="remarks"></a>コメント

関数オブジェクトは範囲内の要素ごとに呼び出されます。呼び出されるたびに同じ値を返す必要はありません。 たとえば、ファイルから読み取る、ローカル状態を参照して変更するなどのことができます。 ジェネレーターの結果の型は、その範囲の前方反復子の値の型に変換可能である必要があります。

参照される範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

複雑さは線形的で、必要なジェネレーターに対して正確に (`last` - `first`) の呼び出しが行われます。

### <a name="example"></a>使用例

```cpp
// alg_generate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

int main()
{
    using namespace std;

    // Assigning random values to vector integer elements
    vector<int> v1 ( 5 );
    vector<int>::iterator Iter1;
    deque<int> deq1 ( 5 );
    deque<int>::iterator d1_Iter;

    generate ( v1.begin( ), v1.end( ), rand );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Assigning random values to deque integer elements
    generate ( deq1.begin( ), deq1.end( ), rand );

    cout << "Deque deq1 is ( " ;
    for ( d1_Iter = deq1.begin( ) ; d1_Iter != deq1.end( ) ; d1_Iter++ )
        cout << *d1_Iter << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 41 18467 6334 26500 19169 ).
Deque deq1 is ( 15724 11478 29358 26962 24464 ).
```

## <a name="generate_n"></a>generate_n

範囲内の指定された数の要素に関数オブジェクトによって生成される値を割り当て、最後に割り当てられた値を 1 つ超えた位置を返します。

```cpp
template<class OutputIterator, class Diff, class Generator>
void generate_n(
    OutputIterator first,
    Diff count,
    Generator gen);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Generator>
ForwardIterator generate_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    Size count,
    Generator gen);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
値が割り当てられる範囲の最初の要素の位置を示す出力反復子。

*カウント*\
ジェネレーター関数によって値が割り当てられる要素の数を指定する符号付きまたは符号なし整数の型。

*gen*\
引数を指定しないで呼び出され、範囲内の各要素に割り当てられる値を生成するために使用される関数オブジェクト。

### <a name="remarks"></a>コメント

関数オブジェクトは範囲内の要素ごとに呼び出されます。呼び出されるたびに同じ値を返す必要はありません。 たとえば、ファイルから読み取る、ローカル状態を参照して変更するなどのことができます。 ジェネレーターの結果の型は、その範囲の前方反復子の値の型に変換可能である必要があります。

参照される範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

複雑さは、要求されているジェネレーターへの呼び出し回数 `count` に正確に比例して線形的です。

### <a name="example"></a>使用例

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <deque>
#include <iostream>
#include <string>
#include <algorithm>
#include <random>

using namespace std;

template <typename C>
void print(const string& s, const C& c)
{
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    const int elemcount = 5;
    vector<int> v(elemcount);
    deque<int> dq(elemcount);

    // Set up random number distribution
    random_device rd;
    mt19937 engine(rd());
    uniform_int_distribution<int> dist(-9, 9);

    // Call generate_n, using a lambda for the third parameter
    generate_n(v.begin(), elemcount, [&](){ return dist(engine); });
    print("vector v is: ", v);

    generate_n(dq.begin(), elemcount, [&](){ return dist(engine); });
    print("deque dq is: ", dq);
}
```

## <a name="includes"></a>が含まれ

1 つの並べ替えられた範囲に、別の並べ替えられた範囲内のすべての要素が含まれるかどうかをテストします。要素間の順序または等価の基準は二項述語によって指定できます。

```cpp
template<class InputIterator1, class InputIterator2>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2);

template<class InputIterator1, class InputIterator2, class Compare>
bool includes(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool includes(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
2 番目のすべての要素が 1 番目に含まれているかどうかをテストするため、2 つの並べ替えられたソース範囲の、最初の範囲の最初の要素の位置を示す入力反復子。

*last1*\
2 番目のすべての要素が 1 番目に含まれているかどうかをテストするため、2 つの並べ替えられたソース範囲の、最初の範囲の最後の要素の 1 つ後ろの位置を示す入力反復子。

*first2*\
2 番目のすべての要素が 1 番目に含まれているかどうかをテストするため、2 つの連続する並べ替えられたソース範囲の、2 番目の範囲の最初の要素の位置を示す入力反復子。

*last2*\
2 番目のすべての要素が 1 番目に含まれているかどうかをテストするため、2 つの連続する並べ替えられたソース範囲の、2 番目の範囲の最後の要素の 1 つ後ろの位置を示す入力反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 比較述語は2つの引数を受け取り、満たされた場合は**true**を返し、満たされていない場合は**false**を返します。

### <a name="return-value"></a>戻り値

最初の並べ替えられた範囲に 2 番目の並べ替えられた範囲内のすべての要素が含まれている場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>コメント

このテストを検討する別の方法は、テストによって 2 番目のソース範囲が最初のソース範囲のサブセットであるかどうかが決定したことです。

参照される並べ替えられたソース範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

アルゴリズムを適用するための事前条件として、それぞれの並べ替えられたソース範囲は、結合された範囲の並べ替えにアルゴリズムが使用したのと同じ順序の基準に従って並べ替えられている必要があります。

ソース範囲は、`merge`アルゴリズムによって変更されることはありません。

入力反復子の値の型は、小なり (less-than) 比較ができる必要があります。これにより、2 つの要素が与えられたときに、それらが等しいか (いずれも他方より小さくない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 より正確には、アルゴリズムは、指定した二項述語の下で最初の並べ替えられた範囲内のすべての要素に 2 番目の並べ替えられた範囲内の要素と同等の順序があるかどうかをテストします。

アルゴリズムの複雑さは線形的で、空でないソース範囲に対して最大 `2 * ((last1 - first1) - (last2 - first2)) - 1` の比較があります。

### <a name="example"></a>使用例

```cpp
// alg_includes.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b;
    vector<int>::iterator Iter1a, Iter1b;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -2 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-2 ; ii <= 3 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b );
    vector<int>::iterator Iter2a, Iter2b;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );
    v2a.pop_back( );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) ;
    vector<int>::iterator Iter3a, Iter3b;
    reverse (v3a.begin( ), v3a.end( ) );
    v3a.pop_back( );
    v3a.pop_back( );
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To test for inclusion under an asscending order
    // with the default binary predicate less<int>( )
    bool Result1;
    Result1 = includes ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ) );
    if ( Result1 )
        cout << "All the elements in vector v1b are "
            << "contained in vector v1a." << endl;
    else
        cout << "At least one of the elements in vector v1b "
            << "is not contained in vector v1a." << endl;

    // To test for inclusion under descending
    // order specify binary predicate greater<int>( )
    bool Result2;
    Result2 = includes ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ), greater<int>( ) );
    if ( Result2 )
        cout << "All the elements in vector v2b are "
            << "contained in vector v2a." << endl;
    else
        cout << "At least one of the elements in vector v2b "
            << "is not contained in vector v2a." << endl;

    // To test for inclusion under a user
    // defined binary predicate mod_lesser
    bool Result3;
    Result3 = includes ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), mod_lesser );
    if ( Result3 )
        cout << "All the elements in vector v3b are "
            << "contained under mod_lesser in vector v3a."
            << endl;
    else
        cout << "At least one of the elements in vector v3b is "
            << " not contained under mod_lesser in vector v3a."
            << endl;
}
```

```Output
Original vector v1a with range sorted by the
binary predicate less than is v1a = ( -2 -1 0 1 2 3 4 ).
Original vector v1b with range sorted by the
binary predicate less than is v1b = ( -2 -1 0 1 2 3 ).
Original vector v2a with range sorted by the
binary predicate greater is v2a = ( 4 3 2 1 0 -1 ).
Original vector v2b with range sorted by the
binary predicate greater is v2b = ( 3 2 1 0 -1 -2 ).
Original vector v3a with range sorted by the
binary predicate mod_lesser is v3a = ( 0 1 2 3 4 ).
Original vector v3b with range sorted by the
binary predicate mod_lesser is v3b = ( 0 -1 1 -2 2 3 ).
All the elements in vector v1b are contained in vector v1a.
At least one of the elements in vector v2b is not contained in vector v2a.
At least one of the elements in vector v3b is not contained under mod_lesser in vector v3a.
```

## <a name="inplace_merge"></a>inplace_merge

2 つの連続する並べ替えられた範囲の要素を単一の並べ替えられた範囲として連結します。順序の基準は二項述語によって指定できます。

```cpp
template<class BidirectionalIterator>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class BidirectionalIterator, class Compare>
void inplace_merge(
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);

template<class ExecutionPolicy, class BidirectionalIterator>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator, class Compare>
void inplace_merge(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator middle,
    BidirectionalIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
結合して単一の範囲に分類する 2 つの連続する並べ替えられた範囲の、最初の範囲の最初の要素の位置を示す双方向反復子。

*中央*\
結合して単一の範囲に分類する 2 つの連続する並べ替えられた範囲の、2 番目の範囲の最初の要素の位置を示す双方向反復子。

*最後*の\
結合して単一の範囲に分類する 2 つの連続する並べ替えられたソース範囲の、2 番目の範囲の最後の要素の 1 つ後ろの位置を示す双方向反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 比較述語は2つの引数を受け取り、最初の要素が2番目の要素より小さい場合は**true**を返し、それ以外の場合は**false**を返します。

### <a name="remarks"></a>コメント

参照される並べ替えられた連続する範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

`inplace_merge` アルゴリズムを適用するための事前条件として、それぞれの並べ替えられた連続する範囲は、結合された範囲の並べ替えにアルゴリズムが使用したのと同じ順序の基準に従って並べ替えられている必要があります。 各範囲内の要素の相対順序は維持されるため、操作は安定しています。 両方のソース範囲に同等の要素がある場合は、結合された範囲では、最初の範囲の要素が、2 番目の範囲の要素よりも前に置かれます。

複雑さは、アルゴリズムがメモリを一時バッファーに割り当てる際に使用可能なメモリによって異なります。 使用可能なメモリが十分にある場合、最適なケースは `(last - first) - 1` 比較で線形的になります。補助メモリが使用できない場合、最悪のケースは `N log(N)`*になります。ここ*で、 *N* = *最後*に - ます。

### <a name="example"></a>使用例

```cpp
// alg_inplace_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      //For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, Iter3;

    // Constructing vector v1 with default less-than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
    {
        v1.push_back( ii );
    }

    cout << "Original vector v1 with subranges sorted by the\n "
            << "binary predicate less than is v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2 ( v1 );
    vector<int>::iterator break2;
    break2 = find ( v2.begin( ), v2.end( ), -5 );
    sort ( v2.begin( ), break2 , greater<int>( ) );
    sort ( break2 , v2.end( ), greater<int>( ) );
    cout << "Original vector v2 with subranges sorted by the\n "
            << "binary predicate greater is v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3 ( v1 );
    vector<int>::iterator break3;
    break3 = find ( v3.begin( ), v3.end( ), -5 );
    sort ( v3.begin( ), break3 , mod_lesser );
    sort ( break3 , v3.end( ), mod_lesser );
    cout << "Original vector v3 with subranges sorted by the\n "
            << "binary predicate mod_lesser is v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")" << endl;

    vector<int>::iterator break1;
    break1 = find (v1.begin( ), v1.end( ), -5 );
    inplace_merge ( v1.begin( ), break1, v1.end( ) );
    cout << "Merged inplace with default order,\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To merge inplace in descending order, specify binary
    // predicate greater<int>( )
    inplace_merge ( v2.begin( ), break2 , v2.end( ) , greater<int>( ) );
    cout << "Merged inplace with binary predicate greater specified,\n "
            << "vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")" << endl;

    // Applying a user defined (UD) binary predicate mod_lesser
    inplace_merge ( v3.begin( ), break3, v3.end( ), mod_lesser );
    cout << "Merged inplace with binary predicate mod_lesser specified,\n "
            << "vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector v1 with subranges sorted by the
binary predicate less than is v1 = ( 0 1 2 3 4 5 -5 -4 -3 -2 -1 0 )
Original vector v2 with subranges sorted by the
binary predicate greater is v2 = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Original vector v3 with subranges sorted by the
binary predicate mod_lesser is v3 = ( 0 1 2 3 4 5 0 -1 -2 -3 -4 -5 )
Merged inplace with default order,
vector v1mod = ( -5 -4 -3 -2 -1 0 0 1 2 3 4 5 )
Merged inplace with binary predicate greater specified,
vector v2mod = ( 5 4 3 2 1 0 0 -1 -2 -3 -4 -5 )
Merged inplace with binary predicate mod_lesser specified,
vector v3mod = ( 0 0 1 -1 2 -2 3 -3 4 -4 5 -5 )
```

## <a name="is_heap"></a>is_heap

指定された範囲の要素がヒープを形成する場合に**true**を返します。

```cpp
template<class RandomAccessIterator>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
bool is_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
bool is_heap(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
ヒープをチェックする範囲の先頭を指定するランダム アクセス反復子。

*最後*の\
範囲の最後を指定するランダム アクセス反復子。

*pred*\
要素の並べ替えをテストするための条件。 比較述語は2つの引数を受け取り、 **true**または**false**を返します。

### <a name="return-value"></a>戻り値

指定された範囲の要素がヒープを形成する場合は**true** 、それ以外の場合は**false**を返します。

### <a name="remarks"></a>コメント

1つ目のテンプレート関数は、 [is_heap_until](../standard-library/algorithm-functions.md#is_heap_until)`(first , last) == last`を返します。

2 番目のテンプレート関数は、以下を返します。

`is_heap_until(first, last, pred) == last`.

## <a name="is_heap_until"></a>is_heap_until

ヒープの順序付け条件を満たしていない範囲 [`first`、`last`) の最初の要素に配置された反復子を返します。または、範囲がヒープを形成している場合は*終了*します。

```cpp
template<class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
RandomAccessIterator is_heap_until(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
ヒープを確認する範囲の最初の要素を指定するランダム アクセス反復子。

*最後*の\
ヒープを確認する範囲の末尾を指定するランダム アクセス反復子。

*pred*\
ヒープを定義する厳密弱順序の条件を指定する二項述語。 既定の述語は、 *pred*が指定されていない場合に `std::less<>` ます。

### <a name="return-value"></a>戻り値

指定された範囲がヒープを形成する場合、または1つ以下の要素が含まれる場合は、 *last*を返します。 それ以外の場合、ヒープの条件を満たさない最初の要素の反復子を返します。

### <a name="remarks"></a>コメント

最初のテンプレート関数は、`[first, last)` 内の最後の反復子 `next` を返します。 `[first, next)` は、関数オブジェクト `std::less<>`によって順序付けられたヒープです。 `last - first` 距離が2未満の場合、関数は*last*を返します。

2番目のテンプレート関数は、ヒープの順序付け条件として `std::less<>` ではなく述語*pred*を使用する点を除いて、1番目の関数と同じように動作します。

## <a name="is_partitioned"></a>is_partitioned

条件の**true**をテストする特定の範囲のすべての要素が、 **false**をテストする要素の前にある場合に**true**を返します。

```cpp
template<class InputIterator, class UnaryPredicate>
bool is_partitioned(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool is_partitioned(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
条件をチェックする範囲の先頭を指定する入力反復子。

*最後*の\
範囲の終了位置を示す入力反復子。

*pred*\
テストする条件。 これは、検索対象の要素によって満たされる条件を定義するユーザー定義の述語関数オブジェクトによって提供されます。 単項述語は1つの引数を取り、 **true**または**false**を返します。

### <a name="return-value"></a>戻り値

条件の**true**をテストする特定の範囲のすべての要素が、 **false**をテストする要素の前にある場合は**true**を返します。それ以外の場合は**false**を返します。

### <a name="remarks"></a>コメント

このテンプレート関数は、`[first, last)` 内のすべての要素が*pred*によってパーティション分割されている場合にのみ**true**を返します。つまり、`pred (Y)` が**false**であるすべての要素 `Y` する前に、`pred (X)` が true である `[first, last)` に `X` すべての要素が発生します。

## <a name="is_permutation"></a>is_permutation

要素が同じ順序であるかどうかに関係なく、両方の範囲に同じ要素が含まれる場合に true を返します。 C++14 コードでは 2 範囲のオーバーロードを使用します。これは、2 つ目の範囲に対して 1 つの反復子のみを受け取るオーバーロードでは、2 つ目の範囲が 1 つ目の範囲より大きい場合にその差を検出できず、2 つ目の範囲が 1 つ目の範囲より小さい場合に未定義の動作が発生するためです。

```cpp
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate Pred);

// C++14
template<class ForwardIterator1, class ForwardIterator2>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
bool is_permutation(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*first1*\
範囲の最初の要素を参照する前方反復子。

*last1*\
範囲の最後の要素の 1 つ後ろの要素を参照する前方反復子。

*first2*\
比較に使用される、2 つ目の範囲の最初の要素を参照する前方反復子。

*last2*\
比較に使用される、2 つ目の範囲の最後の要素の 1 つ後ろの要素を参照する前方反復子。

*pred*\
等価性をテストし、**ブール**値を返す述語。

### <a name="return-value"></a>戻り値

比較演算子の述語に従って同一になるように範囲を再配置できる場合は**true** 。それ以外の場合は**false**。

### <a name="remarks"></a>コメント

`is_permutation` は、最悪の場合に 2 次の複雑さを持ちます。

1つ目のテンプレート関数では、`[first1, last1)`によって指定された範囲内にあるため、 *first2*で始まる範囲内に要素が複数あることを前提としています。 2 つ目の範囲にそれよりも多くの要素がある場合、それらの要素は無視されます。2 つ目の範囲にそれよりも少ない要素がある場合は、未定義の動作が発生します。 3 つ目のテンプレート関数 (C++ 14 以降) では、この想定を行っていません。 両方とも**true**を返します。 `[first1, last1)` によって指定された範囲内の各要素 x には、 *first2*または `[first2, last2)`で始まる範囲内にある x = = y と同じ範囲内の要素 Y が1つだけ存在します。 ここでは、`operator==` オペランド間のペアの比較を実行する必要があります。

2 つ目と 4 つ目のテンプレート関数も同様に動作しますが、`operator==(X, Y)` を `Pred(X, Y)` に置き換えている点が異なります。 正常に動作するには、述語が対称的、推移的、および再帰的である必要があります。

### <a name="example"></a>使用例

`is_permutation` を使用する方法を次の例に示します。

```cpp
#include <vector>
#include <iostream>
#include <algorithm>
#include <string>

using namespace std;

int main()
{
    vector<int> vec_1{ 2, 3, 0, 1, 4, 5 };
    vector<int> vec_2{ 5, 4, 0, 3, 1, 2 };

    vector<int> vec_3{ 4, 9, 13, 3, 6, 5 };
    vector<int> vec_4{ 7, 4, 11, 9, 2, 1 };

    cout << "(1) Compare using built-in == operator: ";
    cout << boolalpha << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // true

    cout << "(2) Compare after modifying vec_2: ";
    vec_2[0] = 6;
    cout << is_permutation(vec_1.begin(), vec_1.end(),
        vec_2.begin(), vec_2.end()) << endl; // false

    // Define equivalence as "both are odd or both are even"
    cout << "(3) vec_3 is a permutation of vec_4: ";
    cout << is_permutation(vec_3.begin(), vec_3.end(),
        vec_4.begin(), vec_4.end(),
        [](int lhs, int rhs) { return lhs % 2 == rhs % 2; }) << endl; // true

    // Initialize a vector using the 's' string literal to specify a std::string
    vector<string> animals_1{ "dog"s, "cat"s, "bird"s, "monkey"s };
    vector<string> animals_2{ "donkey"s, "bird"s, "meerkat"s, "cat"s };

    // Define equivalence as "first letters are equal":
    bool is_perm = is_permutation(animals_1.begin(), animals_1.end(), animals_2.begin(), animals_2.end(),
        [](const string& lhs, const string& rhs)
    {
        return lhs[0] == rhs[0]; //std::string guaranteed to have at least a null terminator
    });

    cout << "animals_2 is a permutation of animals_1: " << is_perm << endl; // true

    cout << "Press a letter" << endl;
    char c;
    cin >> c;

    return 0;
}
```

## <a name="is_sorted"></a>is_sorted

指定された範囲の要素が並べ替えられた順序である場合に**true**を返します。

```cpp
template<class ForwardIterator>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
bool is_sorted(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
bool is_sorted(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
チェックする範囲の開始位置を示す前方反復子。

*最後*の\
範囲の終了位置を示す前方反復子。

*pred*\
2 つの要素間の順序を決定するテストの条件。 比較述語は2つの引数を受け取り、 **true**または**false**を返します。 これは `operator<` と同じタスクを実行します。

### <a name="remarks"></a>コメント

1つ目のテンプレート関数は、 [is_sorted_until](#is_sorted_until)`( first, last ) == last`を返します。 `operator<` 関数は、順序の比較を実行します。

2番目のテンプレート関数は、`is_sorted_until( first, last , pred ) == last`を返します。 *Pred*述語関数は、順序の比較を実行します。

## <a name="is_sorted_until"></a>is_sorted_until

指定した範囲から並べ替え順序で最後の要素に設定されている `ForwardIterator` を返します。

2番目のバージョンでは、2つの指定した要素が並べ替えられた順序である場合に**true**を返す比較関数オブジェクトを指定できます。それ以外の場合は**false**を返します。

```cpp
template<class ForwardIterator>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator is_sorted_until(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
チェックする範囲の開始位置を示す前方反復子。

*最後*の\
範囲の終了位置を示す前方反復子。

*pred*\
2 つの要素間の順序を決定するテストの条件。 比較述語は2つの引数を受け取り、 **true**または**false**を返します。

### <a name="return-value"></a>戻り値

並べ替え順序で最後の要素に設定された `ForwardIterator` を返します。 並べ替えられたシーケンスは、*最初*から開始されます。

### <a name="remarks"></a>コメント

最初のテンプレート関数は、`[first, last]` 内の最後の反復子 `next` を返します。これにより、`[first, next)` は `operator<`によって並べ替えられた並べ替え済みのシーケンスになります。 `distance()` が2未満の場合、関数は*last*を返します。

2 番目のテンプレート関数は、`operator<(X, Y)` と `pred(X, Y)` を置き換える点を除いて、同じ動作をします。

## <a name="iter_swap"></a>iter_swap

指定された反復子のペアで参照される 2 個の値を交換します。

```cpp
template<class ForwardIterator1, class ForwardIterator2>
void iter_swap( ForwardIterator1 left, ForwardIterator2 right );
```

### <a name="parameters"></a>パラメーター

*左*\
値が交換される前方反復子の 1 つ。

*右*\
値が交換される 2 つ目の前方反復子。

### <a name="remarks"></a>コメント

`swap` は、旧バージョンとC++の互換性のために標準に含まれていた**iter_swap**に優先して使用する必要があります。 `Fit1` および `Fit2` が前方反復子の場合、`iter_swap( Fit1, Fit2 )`は `swap( *Fit1, *Fit2 )`と同じです。

入力前方反復子の値の型は、同じ値にする必要があります。

### <a name="example"></a>使用例

```cpp
// alg_iter_swap.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt&   operator=( const CInt& rhs ) { m_nVal =
    rhs.m_nVal; return *this; }
    bool operator<( const CInt& rhs ) const
        { return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt(" << rhs.m_nVal << ")";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    CInt c1 = 5, c2 = 1, c3 = 10;
    deque<CInt> deq1;
    deque<CInt>::iterator d1_Iter;

    deq1.push_back ( c1 );
    deq1.push_back ( c2 );
    deq1.push_back ( c3 );

    cout << "The original deque of CInts is deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Exchanging first and last elements with iter_swap
    iter_swap ( deq1.begin( ), --deq1.end( ) );

    cout << "The deque of CInts with first & last elements swapped is:\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Swapping back first and last elements with swap
    swap ( *deq1.begin( ), *(deq1.end( ) -1 ) );

    cout << "The deque of CInts with first & last elements swapped back is:\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    // Swapping a vector element with a deque element
    vector<int> v1;
    vector<int>::iterator Iter1;
    deque<int> deq2;
    deque<int>::iterator d2_Iter;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 4 ; ii <= 5 ; ii++ )
    {
        deq2.push_back( ii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Deque deq2 is ( " ;
    for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
        cout << *d2_Iter << " ";
    cout << ")." << endl;

    iter_swap ( v1.begin( ), deq2.begin( ) );

    cout << "After exchanging first elements,\n vector v1 is: v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl << " & deque deq2 is: deq2 = ( ";
    for ( d2_Iter = deq2.begin( ) ; d2_Iter != deq2.end( ) ; d2_Iter++ )
        cout << *d2_Iter << " ";
    cout << ")." << endl;
}
```

```Output
The original deque of CInts is deq1 = ( CInt(5), CInt(1), CInt(10) ).
The deque of CInts with first & last elements swapped is:
deq1 = ( CInt(10), CInt(1), CInt(5) ).
The deque of CInts with first & last elements swapped back is:
deq1 = ( CInt(5), CInt(1), CInt(10) ).
Vector v1 is ( 0 1 2 3 ).
Deque deq2 is ( 4 5 ).
After exchanging first elements,
vector v1 is: v1 = ( 4 1 2 3 ).
& deque deq2 is: deq2 = ( 0 5 ).
```

## <a name="lexicographical_compare"></a>lexicographical_compare

2 つのシーケンスを要素ごとに比較して、2 つのうちどちらが小さいかを判断します。

```cpp
template<class InputIterator1, class InputIterator2>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class Compare>
bool lexicographical_compare(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Compare>
bool lexicographical_compare(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
比較する 1 つ目の範囲内の最初の要素の位置を示す入力反復子。

*last1*\
比較する 1 つ目の範囲内の最後の要素の 1 つ後ろの位置を示す入力反復子。

*first2*\
比較する 2 つ目の範囲内の最初の要素の位置を示す入力反復子。

*last2*\
比較する 2 つ目の範囲内の最後の要素の 1 つ後ろの位置を示す入力反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 比較述語は2つの引数を受け取り、満たされた場合は**true**を返し、満たされていない場合は**false**を返します。

### <a name="return-value"></a>戻り値

最初の範囲が 2 番目の範囲よりも辞書順で小さい場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>コメント

シーケンス間の辞書式比較は、次の条件を満たすまで要素ごとに比較します。

- 2 つの対応する要素が等しくない場合、比較の結果はシーケンス間の比較の結果として取得されます。

- 不等値が見つからなくても、1 つのシーケンスに他より多くの要素がある場合、短いシーケンスは長いシーケンスより小さいと見なされます。

- 不等ずが見つかりません。シーケンスの要素数が同じであるため、シーケンスは等しく、比較の結果は**false**になります。

### <a name="example"></a>使用例

```cpp
// alg_lex_comp.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice ( int elem1, int elem2 )
{
    return 2 * elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    int ii;
    for ( ii = 0 ; ii <= 6 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 5 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Self lexicographical_comparison of v1 under identity
    bool result1;
    result1 = lexicographical_compare (v1.begin( ), v1.end( ),
                    v1.begin( ), v1.end( ) );
    if ( result1 )
        cout << "Vector v1 is lexicographically_less than v1." << endl;
    else
        cout << "Vector v1 is not lexicographically_less than v1." << endl;

    // lexicographical_comparison of v1 and L2 under identity
    bool result2;
    result2 = lexicographical_compare (v1.begin( ), v1.end( ),
                    L1.begin( ), L1.end( ) );
    if ( result2 )
        cout << "Vector v1 is lexicographically_less than L1." << endl;
    else
        cout << "Vector v1 is lexicographically_less than L1." << endl;

    bool result3;
    result3 = lexicographical_compare (v1.begin( ), v1.end( ),
                    v2.begin( ), v2.end( ), twice );
    if ( result3 )
        cout << "Vector v1 is lexicographically_less than v2 "
            << "under twice." << endl;
    else
        cout << "Vector v1 is not lexicographically_less than v2 "
            << "under twice." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 )
List L1 = ( 0 5 10 15 20 25 30 )
Vector v2 = ( 0 10 20 30 40 50 )
Vector v1 is not lexicographically_less than v1.
Vector v1 is lexicographically_less than L1.
Vector v1 is not lexicographically_less than v2 under twice.
```

## <a name="lower_bound"></a>lower_bound

順序の基準が二項述語で指定できる場合に、順序付けられた範囲内で、指定した値と等価以上の値を持つ最初の要素の位置を検索します。

```cpp
template<class ForwardIterator, class Type>
ForwardIterator lower_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value );

template<class ForwardIterator, class Type, class BinaryPredicate>
ForwardIterator lower_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    BinaryPredicate pred );
```

### <a name="parameters"></a>パラメーター

*最初*の\
検索範囲内の先頭の要素の位置を示す前方反復子。

*最後*の\
検索範囲の最後の要素の 1 つ後ろの位置を示す前方反復子。

*value*\
順序付けられた範囲内で、最初の位置や可能な最初の位置を検索する対象の値。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="return-value"></a>戻り値

等価の基準が二項述語で指定できる場合に、順序付けられた範囲内で、指定した値と等価以上の値を持つ最初の要素の位置にある前方反復子。

### <a name="remarks"></a>コメント

参照される並べ替えられたソースの範囲が有効であり、すべての反復子が逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

`lower_bound` を使用する事前条件として、対象の範囲は、二項述語によって指定された基準と同じ順序の基準を使用して並べ替えられている必要があります。

対象範囲は、`lower_bound` アルゴリズムによって変更されません。

前方反復子の値の型は、小なり (less-than) 比較ができる必要があります。これにより、2 個の要素が与えられたときに、それらが等しいか (いずれも他方より小さくない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます

アルゴリズムの複雑さは、ランダムアクセス反復子では対数的であり、そうでない場合は (`last - first`) のステップ数に比例して線形的です。

### <a name="example"></a>使用例

```cpp
// alg_lower_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        << "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate lower_bound

    vector<int>::iterator Result;

    // lower_bound of 3 in v1 with default binary predicate less<int>()
    Result = lower_bound(v1.begin(), v1.end(), 3);
    cout << "The lower_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = lower_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The lower_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // lower_bound of 3 in v3 with the binary predicate mod_lesser
    Result = lower_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The lower_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```

## <a name="make_heap"></a>make_heap

指定された範囲の要素を、最初の要素が最大であるヒープに変換します。並べ替えの基準は二項述語によって指定できます。

```cpp
template<class RandomAccessIterator>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void make_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred );
```

### <a name="parameters"></a>パラメーター

*最初*の\
ヒープに変換される範囲内の最初の要素の位置を示すランダム アクセス反復子。

*最後*の\
ヒープに変換される範囲内の最後の要素の 1 つ後ろの位置を示すランダム アクセス反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="remarks"></a>コメント

ヒープには次の 2 つのプロパティがあります。

- 最初の要素は常に最大です。

- 要素は体数時間で追加または削除できます。

ヒープは、優先順位キューを実装するのに最適な方法です。C++ 標準ライブラリ コンテナー アダプター [priority_queue Class](../standard-library/priority-queue-class.md) の実装に使用されます。

複雑さは線形的で、`3 * (last - first)` の比較が必要です。

### <a name="example"></a>使用例

```cpp
// alg_make_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    random_shuffle( v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Make v1 a heap with default less than ordering
    make_heap ( v1.begin( ), v1.end( ) );
    cout << "The heaped version of vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Make v1 a heap with greater than ordering
    make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The greater-than heaped version of v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="max"></a>制限

2 つのオブジェクトを比較し、大きい方のオブジェクトを返します。順序の基準は、二項述語によって指定できます。

```cpp
template<class Type>
constexpr Type& max(
    const Type& left,
    const Type& right);
template<class Type, class Pr>
constexpr Type& max(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);
template<class Type>
constexpr Type& max (
    initializer_list<Type> ilist);
template<class Type, class Pr>
constexpr Type& max(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*左*\
比較される 2 つのオブジェクトの 1 番目のオブジェクト。

*右*\
比較される 2 つのオブジェクトの 2 番目のオブジェクト。

*pred*\
2 つのオブジェクトの比較で使用される二項述語。

*引数*\
比較されるオブジェクトを含む初期化子リスト。

### <a name="return-value"></a>戻り値

2 つのオブジェクトのうち大きい方のオブジェクト。大きいオブジェクトが存在しない場合は、2 つのオブジェクトのうち 1 番目のオブジェクトが返されます。 initializer_list を使用する場合、リスト内にある最大のオブジェクトが返されます。

### <a name="remarks"></a>コメント

`max` アルゴリズムでは、パラメーターとして渡されるオブジェクトを使うことはほとんどありません。 C++ 標準ライブラリの多くのアルゴリズムは、パラメーターとして渡された反復子によって位置が指定されている要素の範囲で動作します。 要素の範囲で動作する関数が必要な場合は、代わりに [max_element](../standard-library/algorithm-functions.md#max_element) を使用してください。 Visual Studio 2017 では、initializer_list を受け取るオーバーロードで**constexpr**が有効になります。

### <a name="example"></a>使用例

```cpp
// alg_max.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt&   operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether absolute value of elem1 is greater than
// absolute value of elem2
bool abs_greater ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = -elem1;
    if ( elem2 < 0 )
        elem2 = -elem2;
    return elem1 < elem2;
};

int main()
{
    int a = 6, b = -7;
    // Return the integer with the larger absolute value
    const int& result1 = max(a, b, abs_greater);
    // Return the larger integer
    const int& result2 = max(a, b);

    cout << "Using integers 6 and -7..." << endl;
    cout << "The integer with the greater absolute value is: "
            << result1 << "." << endl;
    cout << "The integer with the greater value is: "
            << result2 << "." << endl;
    cout << endl;

    // Comparing the members of an initializer_list
    const int& result3 = max({ a, b });
    const int& result4 = max({ a, b }, abs_greater);

    cout << "Comparing the members of an initializer_list..." << endl;
    cout << "The member with the greater value is: " << result3 << endl;
    cout << "The integer with the greater absolute value is: " << result4 << endl;

    // Comparing set containers with elements of type CInt
    // using the max algorithm
    CInt c1 = 1, c2 = 2, c3 = 3;
    set<CInt> s1, s2, s3;
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s2.insert ( c2 );
    s2.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
    cout << " " << *s1_Iter << " )." << endl;

    cout << "s2 = (";
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
        cout << " " << *s2_Iter << ",";
    s2_Iter = --s2.end( );
    cout << " " << *s2_Iter << " )." << endl;

    s3 = max ( s1, s2 );
    cout << "s3 = max ( s1, s2 ) = (";
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
        cout << " " << *s3_Iter << ",";
    s3_Iter = --s3.end( );
    cout << " " << *s3_Iter << " )." << endl << endl;

    // Comparing vectors with integer elements using the max algorithm
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

    int i;
    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
    {
        v2.push_back( ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 2 ; iii++ )
    {
        v3.push_back( 2 * iii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "Vector v3 is ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;

    v4 = max ( v1, v2 );
    v5 = max ( v1, v3 );

    cout << "Vector v4 = max (v1,v2) is ( " ;
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
        cout << *Iter4 << " ";
    cout << ")." << endl;

    cout << "Vector v5 = max (v1,v3) is ( " ;
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
        cout << *Iter5 << " ";
    cout << ")." << endl;
}
```

```Output
Using integers 6 and -7...
The integer with the greater absolute value is: -7
The integer with the greater value is: 6.
Comparing the members of an initializer_list...The member with the greater value is: 6The integer with the greater absolute value is: -7
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = max ( s1, s2 ) = ( CInt( 2 ), CInt( 3 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = max (v1,v2) is ( 0 1 2 ).
Vector v5 = max (v1,v3) is ( 0 2 4 ).
```

## <a name="max_element"></a>max_element

並べ替え基準をバイナリ述語で指定できる、指定された範囲内の最大の要素の最初の出現箇所を検索します。

```cpp
template<class ForwardIterator>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator max_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator max_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
最大の要素の検索範囲内の先頭の要素の位置を示す前方反復子。

*最後*の\
最大の要素の検索範囲内の末尾の要素の 1 つ後の位置を示す前方反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 比較述語は2つの引数を受け取り、最初の要素が2番目の要素より小さい場合は**true**を返し、それ以外の場合は**false**を返します。

### <a name="return-value"></a>戻り値

検索範囲内の最大の要素の最初の出現位置を示す前方反復子。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

複雑さは線形的で、空でない範囲に対して `(last - first) - 1` 比較が必要です。

### <a name="example"></a>使用例

```cpp
// alg_max_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<(ostream& osIn, const CInt& rhs)
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is greater than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Searching a set container with elements of type CInt
    // for the maximum element
    CInt c1 = 1, c2 = 2, c3 = -3;
    set<CInt> s1;
    set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s1.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
    cout << " " << *s1_Iter << " )." << endl;

    s1_R1_Iter = max_element ( s1.begin( ), s1.end( ) );

    cout << "The largest element in s1 is: " << *s1_R1_Iter << endl;
    cout << endl;

    // Searching a vector with elements of type int for the maximum
    // element under default less than & mod_lesser binary predicates
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 1 ; ii <= 4 ; ii++ )
    {
        v1.push_back( - 2 * ii );
    }

    cout << "Vector v1 is ( " ;
    for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
        cout << *v1_Iter << " ";
    cout << ")." << endl;

    v1_R1_Iter = max_element ( v1.begin( ), v1.end( ) );
    v1_R2_Iter = max_element ( v1.begin( ), v1.end( ), mod_lesser);

    cout << "The largest element in v1 is: " << *v1_R1_Iter << endl;
    cout << "The largest element in v1 under the mod_lesser"
            << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

## <a name="merge"></a>マージ

2 つの並べ替えられたソース範囲のすべての要素を、単一の並べ替えられたターゲット範囲として連結します。順序の基準は二項述語によって指定できます。

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator merge(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator merge(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
結合して単一の範囲に分類する 2 つの並べ替えられたソース範囲の、最初の範囲の最初の要素の位置を示す入力反復子。

*last1*\
結合して単一の範囲に分類する 2 つの並べ替えられたソース範囲の、最初の範囲の最後の要素の 1 つ後ろの位置を示す入力反復子。

*first2*\
結合して単一の範囲に分類する 2 つの連続する並べ替えられたソース範囲の、2 番目の範囲の最初の要素の位置を示す入力反復子。

*last2*\
結合して単一の範囲に分類する 2 つの連続する並べ替えられたソース範囲の、2 番目の範囲の最後の要素の 1 つ後ろの位置を示す入力反復子。

*結果*\
2 つのソース範囲が単一の並べ替えられた範囲に結合されるターゲット範囲の、最初の要素の位置を示す出力反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 比較述語は2つの引数を受け取り、最初の要素が2番目の要素より小さい場合は**true**を返し、それ以外の場合は**false**を返します。

### <a name="return-value"></a>戻り値

並べ替えられたターゲット範囲内の最後の要素の 1 つ後ろの位置を示す出力反復子。

### <a name="remarks"></a>コメント

参照される並べ替えられたソース範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

ターゲット範囲はソース範囲のいずれかと重ならないようにします。また、ターゲット範囲を格納するのに十分な大きさが必要です。

`merge` アルゴリズムを適用するための事前条件として、それぞれの並べ替えられたソース範囲は、結合された範囲の並べ替えにアルゴリズムが使用したのと同じ順序の基準に従って並べ替えられている必要があります。

各範囲内の要素の相対順序はターゲット範囲内でも維持されるため、操作は安定しています。 ソース範囲は、`merge`アルゴリズムによって変更されることはありません。

入力反復子の値の型は、小なり (less-than) 比較ができる必要があります。これにより、2 つの要素が与えられたときに、それらが等しいか (いずれも他方より小さくない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 両方のソース範囲に同等の要素がある場合は、ターゲット範囲では、最初の範囲の要素が、2 番目のソース範囲の要素よりも前に置かれます。

アルゴリズムの複雑さは線形的で、最大 `(last1 - first1) - (last2 - first2) - 1` の比較があります。

[list クラス](../standard-library/list-class.md)には、2 つのリストの要素を結合するメンバー関数 "merge" が用意されています。

### <a name="example"></a>使用例

```cpp
// alg_merge.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 ) {
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main() {
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1;

    // Constructing vector v1a and v1b with default less than ordering
    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-5 ; ii <= 0 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
            << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
            << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vector v2 with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
            << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
            << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vector v3 with ranges sorted by mod_lesser
    vector<int> v3a( v1a ), v3b( v1b ) , v3( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
            << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
            << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To merge inplace in ascending order with default binary
    // predicate less<int>( )
    merge ( v1a.begin( ), v1a.end( ), v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Merged inplace with default order,\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To merge inplace in descending order, specify binary
    // predicate greater<int>( )
    merge ( v2a.begin( ), v2a.end( ), v2b.begin( ), v2b.end( ),
        v2.begin( ), greater<int>( ) );
    cout << "Merged inplace with binary predicate greater specified,\n "
            << "vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // Applying A user-defined (UD) binary predicate mod_lesser
    merge ( v3a.begin( ), v3a.end( ), v3b.begin( ), v3b.end( ),
        v3.begin( ), mod_lesser );
    cout << "Merged inplace with binary predicate mod_lesser specified,\n "
            << "vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="min"></a>」

2 つのオブジェクトを比較し、小さい方のオブジェクトを返します。順序の基準は、二項述語によって指定できます。

```cpp
template<class Type>
constexpr const Type& min(
    const Type& left,
    const Type& right);

template<class Type, class Pr>
constexpr const Type& min(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);

template<class Type>
constexpr Type min(
    initializer_list<Type> ilist);

template<class Type, class Pr>
constexpr Type min(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*左*\
比較される 2 つのオブジェクトの 1 番目のオブジェクト。

*右*\
比較される 2 つのオブジェクトの 2 番目のオブジェクト。

*pred*\
2 つのオブジェクトの比較で使用される二項述語。

*引数*\
比較するメンバーが含まれている `initializer_list`。

### <a name="return-value"></a>戻り値

2 つのオブジェクトのうち小さい方のオブジェクト。小さいオブジェクトが存在しない場合は、2 つのオブジェクトのうち 1 番目のオブジェクトが返されます。 `initializer_list`の場合は、リスト内の最小のオブジェクトが返されます。

### <a name="remarks"></a>コメント

`min` アルゴリズムでは、パラメーターとして渡されるオブジェクトを使うことはほとんどありません。 C++ 標準ライブラリの多くのアルゴリズムは、パラメーターとして渡された反復子によって位置が指定されている要素の範囲で動作します。 要素の範囲を使用する関数が必要な場合は、[min_element](../standard-library/algorithm-functions.md#min_element) を使用してください。 [constexpr](../cpp/constexpr-cpp.md)は、Visual Studio 2017 の `initializer_list` オーバーロードで有効にされました。

### <a name="example"></a>使用例

```cpp
// alg_min.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<(ostream& osIn, const CInt& rhs);

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Comparing integers directly using the min algorithm with
    // binary predicate mod_lesser & with default less than
    int a = 6, b = -7, c = 7 ;
    const int& result1 = min ( a, b, mod_lesser );
    const int& result2 = min ( b, c );

    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result1 << "." << endl;
    cout << "The lesser of the integers -7 & 7 is: "
        << result2 << "." << endl;
    cout << endl;

    // Comparing the members of an initializer_list
    const int& result3 = min({ a, c });
    const int& result4 = min({ a, b }, mod_lesser);

    cout << "The lesser of the integers 6 & 7 is: "
        << result3 << "." << endl;
    cout << "The mod_lesser of the integers 6 & -7 is: "
        << result4 << "." << endl;
    cout << endl;

    // Comparing set containers with elements of type CInt
    // using the min algorithm
    CInt c1 = 1, c2 = 2, c3 = 3;
    set<CInt> s1, s2, s3;
    set<CInt>::iterator s1_Iter, s2_Iter, s3_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s2.insert ( c2 );
    s2.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
        cout << " " << *s1_Iter << " )." << endl;

    cout << "s2 = (";
    for ( s2_Iter = s2.begin( ); s2_Iter != --s2.end( ); s2_Iter++ )
        cout << " " << *s2_Iter << ",";
    s2_Iter = --s2.end( );
    cout << " " << *s2_Iter << " )." << endl;

    s3 = min ( s1, s2 );
    cout << "s3 = min ( s1, s2 ) = (";
    for ( s3_Iter = s3.begin( ); s3_Iter != --s3.end( ); s3_Iter++ )
        cout << " " << *s3_Iter << ",";
    s3_Iter = --s3.end( );
    cout << " " << *s3_Iter << " )." << endl << endl;

    // Comparing vectors with integer elements using min algorithm
    vector<int> v1, v2, v3, v4, v5;
    vector<int>::iterator Iter1, Iter2, Iter3, Iter4, Iter5;

    int i;
    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
    {
        v2.push_back( ii );
    }

    int iii;
    for ( iii = 0 ; iii <= 2 ; iii++ )
    {
        v3.push_back( 2 * iii );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "Vector v3 is ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;

    v4 = min ( v1, v2 );
    v5 = min ( v1, v3 );

    cout << "Vector v4 = min ( v1,v2 ) is ( " ;
    for ( Iter4 = v4.begin( ) ; Iter4 != v4.end( ) ; Iter4++ )
        cout << *Iter4 << " ";
    cout << ")." << endl;

    cout << "Vector v5 = min ( v1,v3 ) is ( " ;
    for ( Iter5 = v5.begin( ) ; Iter5 != v5.end( ) ; Iter5++ )
        cout << *Iter5 << " ";
    cout << ")." << endl;
}
```

```Output
The mod_lesser of the integers 6 & -7 is: 6.
The lesser of the integers -7 & 7 is: -7.
The lesser of the integers 6 & 7 is: 6.The mod_lesser of the integers 6 & -7 is: 6.
s1 = ( CInt( 1 ), CInt( 2 ) ).
s2 = ( CInt( 2 ), CInt( 3 ) ).
s3 = min ( s1, s2 ) = ( CInt( 1 ), CInt( 2 ) ).

Vector v1 is ( 0 1 2 ).
Vector v2 is ( 0 1 2 ).
Vector v3 is ( 0 2 4 ).
Vector v4 = min ( v1,v2 ) is ( 0 1 2 ).
Vector v5 = min ( v1,v3 ) is ( 0 1 2 ).
```

## <a name="min_element"></a>min_element

指定された範囲内の最小の要素の最初の出現箇所を検索します。順序の基準は二項述語によって指定できます。

```cpp
template<class ForwardIterator>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last );

template<class ForwardIterator, class Compare>
constexpr ForwardIterator min_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
ForwardIterator min_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
最小の要素の検索範囲内の先頭の要素の位置を示す前方反復子。

*最後*の\
最小の要素の検索範囲内の最後の要素の 1 つ後ろの位置を示す前方反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 比較述語は2つの引数を受け取り、最初の要素が2番目の要素より小さい場合は**true**を返し、それ以外の場合は**false**を返します。

### <a name="return-value"></a>戻り値

検索範囲内の最小の要素の最初の出現位置を示す前方反復子。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

複雑さは線形的で、空でない範囲に対して `(last - first) - 1` 比較が必要です。

### <a name="example"></a>使用例

```cpp
// alg_min_element.cpp
// compile with: /EHsc
#include <vector>
#include <set>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt& operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Searching a set container with elements of type CInt
    // for the minimum element
    CInt c1 = 1, c2 = 2, c3 = -3;
    set<CInt> s1;
    set<CInt>::iterator s1_Iter, s1_R1_Iter, s1_R2_Iter;

    s1.insert ( c1 );
    s1.insert ( c2 );
    s1.insert ( c3 );

    cout << "s1 = (";
    for ( s1_Iter = s1.begin( ); s1_Iter != --s1.end( ); s1_Iter++ )
        cout << " " << *s1_Iter << ",";
    s1_Iter = --s1.end( );
    cout << " " << *s1_Iter << " )." << endl;

    s1_R1_Iter = min_element ( s1.begin( ), s1.end( ) );

    cout << "The smallest element in s1 is: " << *s1_R1_Iter << endl;
    cout << endl;

    // Searching a vector with elements of type int for the maximum
    // element under default less than & mod_lesser binary predicates
    vector<int> v1;
    vector<int>::iterator v1_Iter, v1_R1_Iter, v1_R2_Iter;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii = 1 ; ii <= 4 ; ii++ )
    {
        v1.push_back( - 2 * ii );
    }

    cout << "Vector v1 is ( " ;
    for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
        cout << *v1_Iter << " ";
    cout << ")." << endl;

    v1_R1_Iter = min_element ( v1.begin( ), v1.end( ) );
    v1_R2_Iter = min_element ( v1.begin( ), v1.end( ), mod_lesser);

    cout << "The smallest element in v1 is: " << *v1_R1_Iter << endl;
    cout << "The smallest element in v1 under the mod_lesser"
        << "\n binary predicate is: " << *v1_R2_Iter << endl;
}
```

```Output
s1 = ( CInt( -3 ), CInt( 1 ), CInt( 2 ) ).
The smallest element in s1 is: CInt( -3 )

Vector v1 is ( 0 1 2 3 -2 -4 -6 -8 ).
The smallest element in v1 is: -8
The smallest element in v1 under the mod_lesser
binary predicate is: 0
```

## <a name="minmax_element"></a>minmax_element

`min_element` と `max_element` によって実行される作業を 1 回の呼び出しで実行します。

```cpp
template<class ForwardIterator>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class Compare>
constexpr pair<ForwardIterator, ForwardIterator> minmax_element(
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class Compare>
pair<ForwardIterator, ForwardIterator> minmax_element(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
範囲の開始位置を示す前方反復子。

*最後*の\
範囲の終了位置を示す前方反復子。

*pred*\
1つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 比較述語は2つの引数を受け取り、最初の引数が2番目の引数より小さい場合は**true**を、それ以外の場合は**false**を返します。

### <a name="return-value"></a>戻り値

を返します。

`pair<ForwardIterator, ForwardIterator>( min_element(first, last), max_element(first, last))`.

### <a name="remarks"></a>コメント

1 番目のテンプレート関数は、以下を返します。

`pair<ForwardIterator,ForwardIterator>(min_element(first,last), max_element(first,last))`.

2 番目のテンプレート関数は、`operator<(X, Y)` と `pred(X, Y)` を置き換える点を除いて、同じ動作をします。

シーケンスが空でない場合、関数は最大 `3 * (last - first - 1) / 2` の比較を実行します。

## <a name="minmax"></a>minmax

2 つの入力パラメーターを比較し、それらを昇順のペアとして返します。

```cpp
template<class Type>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right);

template<class Type, class BinaryPredicate>
constexpr pair<const Type&, const Type&> minmax(
    const Type& left,
    const Type& right,
    BinaryPredicate pred);

template<class Type>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist);

template<class Type, class BinaryPredicate>
constexpr pair<Type&, Type&> minmax(
    initializer_list<Type> ilist,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*左*\
比較される 2 つのオブジェクトの 1 番目のオブジェクト。

*右*\
比較される 2 つのオブジェクトの 2 番目のオブジェクト。

*pred*\
2 つのオブジェクトの比較で使用される二項述語。

*引数*\
比較するメンバーが含まれている `initializer_list`。

### <a name="remarks"></a>コメント

最初のテンプレート関数は、 *right*が*left*より小さい場合に `pair<const Type&, const Type&>( right, left )` を返します。 それ以外の場合は、 `pair<const Type&, const Type&>( left, right )`を返します。

2番目のメンバー関数は、1番目の要素が小さい方のペアを返します。2番目の要素は、述語*pred*によって比較されたときに大きくなります。

残りのテンプレート関数は同じように動作しますが、 *left*および*right*パラメーターを*引数*に置き換える点が異なります。

関数は比較を 1 回だけ実行します。

## <a name="mismatch"></a>不一致

要素ごとに 2 つの範囲を比較し、最初に違いが発生する位置を特定します。

C++14 コードでは 2 範囲のオーバーロードを使用します。これは、2 つ目の範囲に対して 1 つの反復子のみを受け取るオーバーロードでは、2 つ目の範囲が 1 つ目の範囲より大きい場合にその差を検出できず、2 つ目の範囲が 1 つ目の範囲より小さい場合に未定義の動作が発生するためです。

```cpp
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    BinaryPredicate pred );

//C++14
template<class InputIterator1, class InputIterator2>
pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2 );

template<class InputIterator1, class InputIterator2, class BinaryPredicate> pair<InputIterator1, InputIterator2>>
mismatch(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    BinaryPredicate pred);

//C++17
template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
pair<ForwardIterator1, ForwardIterator2>
mismatch(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
テストする 1 つ目の範囲内の最初の要素の位置を示す入力反復子。

*last1*\
テストする 1 つ目の範囲内の最後の要素の 1 つ後の位置を示す入力反復子。

*first2*\
テストする 2 つ目の範囲内の最初の要素の位置を示す入力反復子。

*last2*\
テストする 2 つ目の範囲内の最後の要素の 1 つ後の位置を示す入力反復子。

*pred*\
各範囲内の現在の要素を比較し、それらが等しいかどうかを判定するための、ユーザー定義の述語関数オブジェクト。 条件が満たされている場合は **true**、満たされていない場合は **false** を返します。

### <a name="return-value"></a>戻り値

2 つの範囲で一致しない位置を示す反復子のペア。ペアを構成する 1 つ目の反復子は 1 つ目の範囲内の位置を示し、2 つ目の反復子は 2 つ目の範囲内の位置を示します。 比較する各範囲内の要素間に違いがない場合、または 2 つの範囲内のすべての要素ペアによって 2 つ目のバージョンの二項述語が満たされている場合、1 つ目の反復子は 1 つ目の範囲内の最後の要素の 1 つ後の位置を示し、2 つ目の反復子は 2 つ目の範囲内の最後のテスト対象の要素の 1 つ後の位置を示します。

### <a name="remarks"></a>コメント

1 つ目のテンプレート関数では、first2 で始まる範囲内に、[first1, last1) で指定された範囲内にあるのと同じ数の要素があると想定しています。 2つ目の範囲にさらに値がある場合は無視されます。値が少ない場合は、未定義の動作が発生します。

検索対象の範囲が有効であること、すべての反復子が逆参照可能であること、さらに先頭位置からのインクリメントにより最後の位置に到達可能であることが必要です。

アルゴリズムの時間計算量は、短い方の範囲に含まれる要素の数に比例します。

ユーザー定義の述語では、そのオペランド間で対称的、再帰的、および推移的な等価関係を強制する必要はありません。

### <a name="example"></a>使用例

mismatch の使用例を次に示します。 C++03 オーバーロードは、これにより予期しない結果が引き起こされるしくみを示すことのみを目的に記載しています。

```cpp
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>
#include <string>
#include <utility>

using namespace std;

// Return whether first element is twice the second
// Note that this is not a symmetric, reflexive and transitive equivalence.
// mismatch and equal accept such predicates, but is_permutation does not.
bool twice(int elem1, int elem2)
{
    return elem1 == elem2 * 2;
}

void PrintResult(const string& msg, const pair<vector<int>::iterator, vector<int>::iterator>& result,
    const vector<int>& left, const vector<int>& right)
{
    // If either iterator stops before reaching the end of its container,
    // it means a mismatch was detected.
    if (result.first != left.end() || result.second != right.end())
    {
        string leftpos(result.first == left.end() ? "end" : to_string(*result.first));
        string rightpos(result.second == right.end() ? "end" : to_string(*result.second));
        cout << msg << "mismatch. Left iterator at " << leftpos
            << " right iterator at " << rightpos << endl;
    }
    else
    {
        cout << msg << " match." << endl;
    }
}

int main()
{

    vector<int> vec_1{ 0, 5, 10, 15, 20, 25 };
    vector<int> vec_2{ 0, 5, 10, 15, 20, 25, 30 };

    // Testing different length vectors for mismatch (C++03)
    auto match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin());
    bool is_mismatch = match_vecs.first != vec_1.end();
    cout << "C++03: vec_1 and vec_2 are a mismatch: " << boolalpha << is_mismatch << endl;

    // Using dual-range overloads:

    // Testing different length vectors for mismatch (C++14)
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14: vec_1 and vec_2: ", match_vecs, vec_1, vec_2);

    // Identify point of mismatch between vec_1 and modified vec_2.
    vec_2[3] = 42;
    match_vecs = mismatch(vec_1.begin(), vec_1.end(), vec_2.begin(), vec_2.end());
    PrintResult("C++14 vec_1 v. vec_2 modified: ", match_vecs, vec_1, vec_2);

    // Test vec_3 and vec_4 for mismatch under the binary predicate twice (C++14)
    vector<int> vec_3{ 10, 20, 30, 40, 50, 60 };
    vector<int> vec_4{ 5, 10, 15, 20, 25, 30 };
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. vec_4 with pred: ", match_vecs, vec_3, vec_4);

    vec_4[5] = 31;
    match_vecs = mismatch(vec_3.begin(), vec_3.end(), vec_4.begin(), vec_4.end(), twice);
    PrintResult("vec_3 v. modified vec_4 with pred: ", match_vecs, vec_3, vec_4);

    // Compare a vector<int> to a list<int>
    list<int> list_1{ 0, 5, 10, 15, 20, 25 };
    auto match_vec_list = mismatch(vec_1.begin(), vec_1.end(), list_1.begin(), list_1.end());
    is_mismatch = match_vec_list.first != vec_1.end() || match_vec_list.second != list_1.end();
    cout << "vec_1 and list_1 are a mismatch: " << boolalpha << is_mismatch << endl;

    char c;
    cout << "Press a key" << endl;
    cin >> c;

}
```

```Output
C++03: vec_1 and vec_2 are a mismatch: false
C++14: vec_1 and vec_2: mismatch. Left iterator at end right iterator at 30
C++14 vec_1 v. vec_2 modified: mismatch. Left iterator at 15 right iterator at 42
C++14 vec_3 v. vec_4 with pred: match.
C++14 vec_3 v. modified vec_4 with pred: mismatch. Left iterator at 60 right iterator at 31
C++14: vec_1 and list_1 are a mismatch: false
Press a key
```

## <a name="alg_move"></a>&lt;alg&gt; 移動

指定された範囲に関連付けられている要素を移動します。

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator move(
    InputIterator first,
    InputIterator last,
    OutputIterator dest);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 move(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
移動する要素の範囲の先頭を示す入力反復子。

*最後*の\
移動する要素の範囲の最後を示す入力反復子。

*dest*\
移動された要素が格納される出力反復子。

### <a name="remarks"></a>コメント

このテンプレート関数は、`[0, last - first)`範囲内の各 `N` に対して `*(dest + N) = move(*(first + N))` を1回評価します。これにより、`N` の値が最小値から厳密に増加します。 その後で `dest + N` が返されます。 `dest` し、*最初*にストレージの領域を指定する場合は、 *dest*を `[first, last)`の範囲に指定することはできません。

## <a name="move_backward"></a>move_backward

ある反復子の要素を別の反復子に移動します。 移動は、指定した範囲の最後の要素から開始され、その範囲内の先頭の要素で終了します。

```cpp
template<class BidirectionalIterator1, class BidirectionalIterator2>
BidirectionalIterator2 move_backward(
    BidirectionalIterator1 first,
    BidirectionalIterator1 last,
    BidirectionalIterator2 destEnd);
```

### <a name="parameters"></a>パラメーター

*最初*の\
要素の移動元の範囲の先頭を指定する反復子。

*最後*の\
要素の移動元の範囲の最後を指定する反復子。 この要素は移動されません。

*Destend*\
移動先範囲の最後の要素の 1 つ後ろの位置を示す双方向反復子。

### <a name="remarks"></a>コメント

このテンプレート関数は、`[0, last - first)`範囲内の各 `N` に対して `*(destEnd - N - 1) = move(*(last - N - 1))` を1回評価します。これにより、`N` の値が最小値から厳密に増加します。 その後で `destEnd - (last - first)` が返されます。 *Destend*と*最初*にストレージの領域を指定した場合、 *destend*を `[first, last)`の範囲に含めることはできません。

`move` と `move_backward` は、移動反復子と共に `copy` と `copy_backward` を使用するのと機能的には同じです。

## <a name="next_permutation"></a>next_permutation

範囲内の要素の順序を変更し、元の順序を辞書式に次に大きい順列 (存在する場合) に置き換えます。next の意味は二項述語によって指定できます。

```cpp
template<class BidirectionalIterator>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool next_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*最初*の\
順序を変える範囲内の最初の要素の位置を指す双方向反復子。

*最後*の\
順序を変える範囲内の最後の要素の 1 つ後ろの位置を指す双方向反復子。

*pred*\
順序内の次の要素によって満たされる比較条件を定義するユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="return-value"></a>戻り値

辞書順序で次の順列が存在し、範囲の元の順序を置き換えた場合は **true**、それ以外の場合は **false**。この場合は、順序が辞書式の最小の順列に変換されています。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

既定の二項述語はより小さく、次の順列が適切に定義されていることを保証するために、範囲内の要素は比較可能である必要があります。

複雑さは線形的で、最大 `(last - first) / 2` のスワップがあります。

### <a name="example"></a>使用例

```cpp
// alg_next_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt
{
public:
    CInt( int n = 0 ) : m_nVal( n ) {}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ) {}
    CInt& operator=( const CInt& rhs ) {m_nVal =
        rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        { return ( m_nVal < rhs.m_nVal ); }
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs )
{
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Reordering the elements of type CInt in a deque
    // using the prev_permutation algorithm
    CInt c1 = 5, c2 = 1, c3 = 10;
    bool deq1Result;
    deque<CInt> deq1, deq2, deq3;
    deque<CInt>::iterator d1_Iter;

    deq1.push_back ( c1 );
    deq1.push_back ( c2 );
    deq1.push_back ( c3 );

    cout << "The original deque of CInts is deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    deq1Result = next_permutation ( deq1.begin( ), deq1.end( ) );

    if ( deq1Result )
        cout << "The lexicographically next permutation "
            << "exists and has\nreplaced the original "
            << "ordering of the sequence in deq1." << endl;
    else
        cout << "The lexicographically next permutation doesn't "
            << "exist\n and the lexicographically "
            << "smallest permutation\n has replaced the "
            << "original ordering of the sequence in deq1." << endl;

    cout << "After one application of next_permutation,\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl << endl;

    // Permuting vector elements with binary function mod_lesser
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = -3 ; i <= 3 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    next_permutation ( v1.begin( ), v1.end( ), mod_lesser );

    cout << "After the first next_permutation, vector v1 is:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= 5 ) {
        next_permutation ( v1.begin( ), v1.end( ), mod_lesser );
        cout << "After another next_permutation of vector v1,\n v1 =   ( " ;
        for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
            cout << *Iter1 << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 5 ), CInt( 1 ), CInt( 10 ) ).
The lexicographically next permutation exists and has
replaced the original ordering of the sequence in deq1.
After one application of next_permutation,
deq1 = ( CInt( 5 ), CInt( 10 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first next_permutation, vector v1 is:
v1 = ( -3 -2 -1 0 1 3 2 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 2 1 3 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 2 3 1 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 3 1 2 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 0 3 2 1 ).
After another next_permutation of vector v1,
v1 =   ( -3 -2 -1 1 0 2 3 ).
```

## <a name="nth_element"></a>nth_element

範囲内のシーケンスの *n* 番目の要素を正しく検索し、その要素の前にあるすべての要素がその要素以下、シーケンス内でその要素に続くすべての要素がその要素以上になるようにして、要素の範囲を分割します。

```cpp
template<class RandomAccessIterator>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void nth_element(
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void nth_element(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator nth,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
パーティション分割される範囲内の最初の要素の位置を示すランダム アクセス反復子。

*n 番目*の\
パーティションの境界で正しく並べ替えられる要素の位置を示すランダム アクセス反復子。

*最後*の\
パーティション分割される範囲内の最後の要素の 1 つ後ろの位置を示すランダム アクセス反復子。

*pred*\
順序内の次の要素によって満たされる比較条件を定義するユーザー定義の述語関数オブジェクト。 比較述語は2つの引数を受け取り、満たされた場合は**true**を返し、満たされていない場合は**false**を返します。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

`nth_element` アルゴリズムでは、 *n*番目の要素の両側の要素が並べ替えられることは保証されません。 そのため、一定の選択した要素を下回る範囲内の要素を並べ替える `partial_sort` よりも保証は少なくなり、下の範囲の要素を並べ替えが不要な場合に `partial_sort` のより高速な代替として使用することができます。

どちらの要素も他方より小さくない場合、要素は同等ですが、必ずしも等しいわけではありません。

並べ替えの複雑さの平均は、 *last first*に関して線形的です。

### <a name="example"></a>使用例

```cpp
// alg_nth_elem.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 ) {
    return elem1 > elem2;
}

int main() {
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
        v1.push_back( 3 * i );

    int ii;
    for ( ii = 0 ; ii <= 5 ; ii++ )
        v1.push_back( 3 * ii + 1 );

    int iii;
    for ( iii = 0 ; iii <= 5 ; iii++ )
        v1.push_back( 3 * iii +2 );

    cout << "Original vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    nth_element(v1.begin( ), v1.begin( ) + 3, v1.end( ) );
    cout << "Position 3 partitioned vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To sort in descending order, specify binary predicate
    nth_element( v1.begin( ), v1.begin( ) + 4, v1.end( ),
            greater<int>( ) );
    cout << "Position 4 partitioned (greater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    random_shuffle( v1.begin( ), v1.end( ) );
    cout << "Shuffled vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    nth_element( v1.begin( ), v1.begin( ) + 5, v1.end( ), UDgreater );
    cout << "Position 5 partitioned (UDgreater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

## <a name="none_of"></a>none_of

指定された範囲内の要素間に条件が存在しない場合に**true**を返します。

```cpp
template<class InputIterator, class UnaryPredicate>
bool none_of(
    InputIterator first,
    InputIterator last,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
bool none_of(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
条件の要素の範囲のチェックを開始する位置を示す入力反復子。

*最後*の\
要素の範囲の最後を示す入力反復子。

*pred*\
テストする条件。 これは、条件を定義するユーザー定義の述語関数オブジェクトによって提供されます。 単項述語は1つの引数を取り、 **true**または**false**を返します。

### <a name="return-value"></a>戻り値

指定された範囲で少なくとも1回条件が検出されなかった場合は**true** 、条件が検出された場合は**false**を返します。

### <a name="remarks"></a>コメント

このテンプレート関数は、`[0, last - first)`範囲の一部の `N` では、述語 `pred(*(first + N))` が常に**false**である場合にのみ**true**を返します。

## <a name="partial_sort"></a>partial_sort

範囲内で指定された数の、より小さい要素を、降順以外の順序、または二項述語で指定された順序の基準に従って配置します。

```cpp
template<class RandomAccessIterator>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void partial_sort(
    RandomAccessIterator first,
    RandomAccessIterator sortEnd,
    RandomAccessIterator last
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void partial_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator middle,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
並べ替えられる範囲内の最初の要素の位置を示すランダム アクセス反復子。

*Sortend*\
並べ替えられるサブ範囲内の最後の要素の 1 つ後ろの位置を示すランダム アクセス反復子。

*最後*の\
部分的に並べ替えられる範囲内の最後の要素の 1 つ後ろの位置を示すランダム アクセス反復子。

*pred*\
順序内の次の要素によって満たされる比較条件を定義するユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

どちらの要素も他方より小さくない場合、要素は同等ですが、必ずしも等しいわけではありません。 `sort` アルゴリズムは安定しておらず、同等の要素の相対順序が保持されることは保証されません。 アルゴリズム `stable_sort` は元の順序を保持します。

部分的な並べ替えの複雑さの平均は、 *O*((`last`- `first`) ログ (`sortEnd`- `first`)) です。

### <a name="example"></a>使用例

```cpp
// alg_partial_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
    return elem1 > elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    int ii;
    for ( ii = 0 ; ii <= 5 ; ii++ )
    {
        v1.push_back( 2 * ii +1 );
    }

    cout << "Original vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    partial_sort(v1.begin( ), v1.begin( ) + 6, v1.end( ) );
    cout << "Partially sorted vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To partially sort in descending order, specify binary predicate
    partial_sort(v1.begin( ), v1.begin( ) + 4, v1.end( ), greater<int>( ) );
    cout << "Partially resorted (greater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    partial_sort(v1.begin( ), v1.begin( ) + 8, v1.end( ), UDgreater );
    cout << "Partially resorted (UDgreater) vector:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector:
v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Partially sorted vector:
v1 = ( 0 1 2 3 4 5 10 8 6 7 9 11 )
Partially resorted (greater) vector:
v1 = ( 11 10 9 8 0 1 2 3 4 5 6 7 )
Partially resorted (UDgreater) vector:
v1 = ( 11 10 9 8 7 6 5 4 0 1 2 3 )
```

## <a name="partial_sort_copy"></a>partial_sort_copy

ソース範囲からターゲット範囲に要素をコピーします。ソース要素は小なりまたは指定された別の二項述語によって並べ替えられます。

```cpp
template<class InputIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2 );

template<class InputIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    InputIterator first1,
    InputIterator last1,
    RandomAccessIterator first2,
    RandomAccessIterator last2,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last);

template<class ExecutionPolicy, class ForwardIterator, class RandomAccessIterator, class Compare>
RandomAccessIterator partial_sort_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    RandomAccessIterator result_first,
    RandomAccessIterator result_last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
ソース範囲内の先頭の要素の位置を示す入力反復子。

*last1*\
ソース範囲内の最後の要素の 1 つ後ろの位置を示す入力反復子。

*first2*\
並べ替えられたターゲット範囲内の最初の要素の位置を示すランダム アクセス反復子。

*last2*\
並べ替えられたターゲット範囲内の最後の要素の 1 つ後ろの位置を示すランダム アクセス反復子。

*pred*\
順序内の次の要素によって満たされる比較条件を定義するユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="return-value"></a>戻り値

ソース範囲から挿入された最後の要素の 1 つ後ろの位置のターゲット範囲内の要素を示すランダム アクセス反復子。

### <a name="remarks"></a>コメント

ソース範囲とターゲット範囲は重複できません。また、両方とも有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

二項述語は、同等でない要素は順序付けされ、同等の要素は順序付けされないように、厳密弱順序を提供する必要があります。 2 つの要素がどちらも他方より小さくない場合、2 つの要素は同等ですが、必ずしも等しいわけではありません。

### <a name="example"></a>使用例

```cpp
// alg_partial_sort_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    list<int> list1;
    vector<int>::iterator iter1, iter2;
    list<int>::iterator list1_Iter, list1_inIter;

    int i;
    for (i = 0; i <= 9; i++)
        v1.push_back(i);

    random_shuffle(v1.begin(), v1.end());

    list1.push_back(60);
    list1.push_back(50);
    list1.push_back(20);
    list1.push_back(30);
    list1.push_back(40);
    list1.push_back(10);

    cout << "Vector v1 = ( " ;
    for (iter1 = v1.begin(); iter1 != v1.end(); iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;

    cout << "List list1 = ( " ;
    for (list1_Iter = list1.begin();
         list1_Iter!= list1.end();
         list1_Iter++)
        cout << *list1_Iter << " ";
    cout << ")" << endl;

    // Copying a partially sorted copy of list1 into v1
    vector<int>::iterator result1;
    result1 = partial_sort_copy(list1.begin(), list1.end(),
             v1.begin(), v1.begin() + 3);

    cout << "List list1 Vector v1 = ( " ;
    for (iter1 = v1.begin() ; iter1 != v1.end() ; iter1++)
        cout << *iter1 << " ";
    cout << ")" << endl;
    cout << "The first v1 element one position beyond"
         << "\n the last L 1 element inserted was " << *result1
         << "." << endl;

    // Copying a partially sorted copy of list1 into v2
    int ii;
    for (ii = 0; ii <= 9; ii++)
        v2.push_back(ii);

    random_shuffle(v2.begin(), v2.end());
    vector<int>::iterator result2;
    result2 = partial_sort_copy(list1.begin(), list1.end(),
             v2.begin(), v2.begin() + 6);

    cout << "List list1 into Vector v2 = ( " ;
    for (iter2 = v2.begin() ; iter2 != v2.end(); iter2++)
        cout << *iter2 << " ";
    cout << ")" << endl;
    cout << "The first v2 element one position beyond"
         << "\n the last L 1 element inserted was " << *result2
         << "." << endl;
}
```

## <a name="partition"></a>partition

範囲内の要素を 2 つの分離されたセットに分類し、単項述語を満たす要素が単項述語を満たさない要素よりも前に来るように配置します。

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator partition(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
パーティション分割される範囲内の最初の要素の位置を示す双方向反復子。

*最後*の\
パーティション分割される範囲内の最後の要素の 1 つ後ろの位置を示す双方向反復子。

*pred*\
要素が分類される場合に満たされる条件を定義するユーザー定義の述語関数オブジェクト。 単項述語は1つの引数を取り、 **true**または**false**を返します。

### <a name="return-value"></a>戻り値

述語条件を満たさない範囲内の最初の要素の位置を示す双方向反復子。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

要素*a*と*b*は同等ですが、必ずしも等しいとは限りません。両方の `pred( a, b )` が false で `pred( b, a )` が false である場合、 *pred*はパラメーター指定の述語です。 `partition` アルゴリズムは安定しておらず、同等の要素の相対順序が保持されることは保証されません。 アルゴリズム `stable_partition` は元の順序を保持します。

複雑さは線形的であり、 *pred*のアプリケーションと、最大で `(last - first)/2` スワップの `(last - first)` アプリケーションがあります。

### <a name="example"></a>使用例

```cpp
// alg_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 10 ; i++ )
    {
        v1.push_back( i );
    }
    random_shuffle( v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Partition the range with predicate greater10
    partition ( v1.begin( ), v1.end( ), greater5 );
    cout << "The partitioned set of elements in v1 is: ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="partition_copy"></a>partition_copy

条件が**true**である要素を1つの変換先にコピーし、条件を**false**にします。 要素は指定された範囲に含まれている必要があります。

```cpp
template<class InputIterator, class OutputIterator1, class OutputIterator2, class UnaryPredicate>
pair<OutputIterator1, OutputIterator2> partition_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator1 dest1,
    OutputIterator2 dest2,
    UnaryPredicate pred);

template <class ExecutionPolicy, class ForwardIterator, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
pair<ForwardIterator1, ForwardIterator2> partition_copy(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    ForwardIterator1 out_true,
    ForwardIterator2 out_false,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
条件をチェックする範囲の先頭を指定する入力反復子。

*最後*の\
範囲の終了位置を示す入力反復子。

*dest1*\
*Pred*を使用してテストされた条件に対して true を返す要素をコピーするために使用される出力反復子。

*dest2*\
*Pred*を使用してテストされた条件に対して false を返す要素をコピーするために使用される出力反復子。

*pred*\
テストする条件。 これは、テストする条件を定義するユーザー定義の述語関数オブジェクトによって提供されます。 単項述語は1つの引数を取り、 **true**または**false**を返します。

### <a name="remarks"></a>コメント

このテンプレート関数は、`[first,last)` 内の各要素 `X` を `*dest1++` にコピーします (`pred(X)` が true の場合)。または、それ以外の場合は `*dest2++` します。 `pair<OutputIterator1, OutputIterator2>(dest1, dest2)` を返します。

## <a name="partition_point"></a>partition_point

特定の範囲内で条件を満たさない最初の要素を返します。 要素は、条件を満たす要素が条件を満たさない要素の前に来るように並べ替えられます。

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator partition_point(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*最初*の\
条件をチェックする範囲の先頭を指定する `ForwardIterator`。

*最後*の\
範囲の終了位置を示す `ForwardIterator`。

*pred*\
テストする条件。 これは、検索対象の要素によって満たされる条件を定義するユーザー定義の述語関数オブジェクトによって提供されます。 単項述語は1つの引数を取り、 **true**または**false**を返します。

### <a name="return-value"></a>戻り値

*Pred*によってテストされた条件を満たさない最初の要素を参照する `ForwardIterator` を返します。見つからない場合は、 *last*を返します。

### <a name="remarks"></a>コメント

このテンプレート関数は、`pred(*it)` が**false**である `[first, last)` 内の最初の反復子 `it` を検索します。 シーケンスは、 *pred*によって順序付けされている必要があります。

## <a name="pop_heap"></a>pop_heap

ヒープの先頭と範囲内の最後から 2 番目の位置との間で最大の要素を削除し、残りの要素から新しいヒープを形成します。

```cpp
template<class RandomAccessIterator>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class BinaryPredicate>
void pop_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*最初*の\
ヒープ内の最初の要素の位置を示すランダム アクセス反復子。

*最後*の\
ヒープ内の最後の要素の 1 つ後ろの位置を示すランダム アクセス反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="remarks"></a>コメント

`pop_heap` アルゴリズムは、push_heap アルゴリズムで実行されるのと逆の操作で、ヒープに追加される要素が既にヒープ内にある他のどの要素よりも大きい場合に、範囲の最後から 2 番目の位置にある要素が範囲内の前の要素を構成するヒープに追加されます。

ヒープには次の 2 つのプロパティがあります。

- 最初の要素は常に最大です。

- 要素は体数時間で追加または削除できます。

ヒープは、優先順位キューを実装するのに最適な方法です。C++ 標準ライブラリ コンテナー アダプター [priority_queue Class](../standard-library/priority-queue-class.md) の実装に使用されます。

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

最後に新しく追加された要素の除外範囲は、ヒープである必要があります。

複雑さは対数で、最大 `log (last - first)` の比較が必要です。

### <a name="example"></a>使用例

```cpp
// alg_pop_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 1 ; i <= 9 ; i++ )
        v1.push_back( i );

    // Make v1 a heap with default less than ordering
    random_shuffle( v1.begin( ), v1.end( ) );
    make_heap ( v1.begin( ), v1.end( ) );
    cout << "The heaped version of vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Add an element to the back of the heap
    v1.push_back( 10 );
    push_heap( v1.begin( ), v1.end( ) );
    cout << "The reheaped v1 with 10 added is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove the largest element from the heap
    pop_heap( v1.begin( ), v1.end( ) );
    cout << "The heap v1 with 10 removed is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl << endl;

    // Make v1 a heap with greater-than ordering with a 0 element
    make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
    v1.push_back( 0 );
    push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The 'greater than' reheaped v1 puts the smallest "
        << "element first:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Application of pop_heap to remove the smallest element
    pop_heap( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The 'greater than' heaped v1 with the smallest element\n "
        << "removed from the heap is: ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="prev_permutation"></a>prev_permutation

範囲内の要素の順序を変更し、元の順序を辞書式で前の大きい順列 (存在する場合) に置き換えます。previous の意味は二項述語によって指定できます。

```cpp
template<class BidirectionalIterator>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class BidirectionalIterator, class BinaryPredicate>
bool prev_permutation(
    BidirectionalIterator first,
    BidirectionalIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*最初*の\
順序を変える範囲内の最初の要素の位置を指す双方向反復子。

*最後*の\
順序を変える範囲内の最後の要素の 1 つ後ろの位置を指す双方向反復子。

*pred*\
順序内の次の要素によって満たされる比較条件を定義するユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="return-value"></a>戻り値

辞書式前の順列が存在し、範囲の元の順序を置き換えた場合は**true** 。それ以外の場合は**false**。この場合、順序は辞書式の最大の順列に変換されます。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

既定の二項述語はよりも小さく、範囲内の要素は、前の順列が適切に定義されていることを確認するために比較可能である必要があります。

複雑さは線形的で、最大で (`last` - `first`)/2 のスワップがあります。

### <a name="example"></a>使用例

```cpp
// alg_prev_perm.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>
#include <ostream>

using namespace std;
class CInt;
ostream& operator<<( ostream& osIn, const CInt& rhs );

class CInt {
public:
    CInt( int n = 0 ) : m_nVal( n ){}
    CInt( const CInt& rhs ) : m_nVal( rhs.m_nVal ){}
    CInt&   operator=( const CInt& rhs ) {m_nVal =
    rhs.m_nVal; return *this;}
    bool operator<( const CInt& rhs ) const
        {return ( m_nVal < rhs.m_nVal );}
    friend ostream& operator<<( ostream& osIn, const CInt& rhs );

private:
    int m_nVal;
};

inline ostream& operator<<( ostream& osIn, const CInt& rhs ) {
    osIn << "CInt( " << rhs.m_nVal << " )";
    return osIn;
}

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 ) {
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
};

int main()
{
    // Reordering the elements of type CInt in a deque
    // using the prev_permutation algorithm
    CInt c1 = 1, c2 = 5, c3 = 10;
    bool deq1Result;
    deque<CInt> deq1, deq2, deq3;
    deque<CInt>::iterator d1_Iter;

    deq1.push_back ( c1 );
    deq1.push_back ( c2 );
    deq1.push_back ( c3 );

    cout << "The original deque of CInts is deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl;

    deq1Result = prev_permutation ( deq1.begin( ), deq1.end( ) );

    if ( deq1Result )
        cout << "The lexicographically previous permutation "
            << "exists and has \nreplaced the original "
            << "ordering of the sequence in deq1." << endl;
    else
        cout << "The lexicographically previous permutation doesn't "
            << "exist\n and the lexicographically "
            << "smallest permutation\n has replaced the "
            << "original ordering of the sequence in deq1." << endl;

    cout << "After one application of prev_permutation,\n deq1 = (";
    for ( d1_Iter = deq1.begin( ); d1_Iter != --deq1.end( ); d1_Iter++ )
        cout << " " << *d1_Iter << ",";
    d1_Iter = --deq1.end( );
    cout << " " << *d1_Iter << " )." << endl << endl;

    // Permutating vector elements with binary function mod_lesser
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = -3 ; i <= 3 ; i++ )
        v1.push_back( i );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );

    cout << "After the first prev_permutation, vector v1 is:\n v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= 5 ) {
        prev_permutation ( v1.begin( ), v1.end( ), mod_lesser );
        cout << "After another prev_permutation of vector v1,\n v1 =   ( " ;
        for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ;Iter1 ++ )
            cout << *Iter1 << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

```Output
The original deque of CInts is deq1 = ( CInt( 1 ), CInt( 5 ), CInt( 10 ) ).
The lexicographically previous permutation doesn't exist
and the lexicographically smallest permutation
has replaced the original ordering of the sequence in deq1.
After one application of prev_permutation,
deq1 = ( CInt( 10 ), CInt( 5 ), CInt( 1 ) ).

Vector v1 is ( -3 -2 -1 0 1 2 3 ).
After the first prev_permutation, vector v1 is:
v1 = ( -3 -2 0 3 2 1 -1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 3 -1 2 1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 3 -1 1 2 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 3 1 -1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 -1 3 1 ).
After another prev_permutation of vector v1,
v1 =   ( -3 -2 0 2 -1 1 3 ).
```

## <a name="push_heap"></a>push_heap

範囲の末尾にある要素を、範囲内の以前の要素で構成される既存のヒープに追加します。

```cpp
template<class RandomAccessIterator>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last );

template<class RandomAccessIterator, class BinaryPredicate>
void push_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*最初*の\
ヒープ内の最初の要素の位置を示すランダム アクセス反復子。

*最後*の\
ヒープに変換される範囲内の最後の要素の 1 つ後ろの位置を示すランダム アクセス反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="remarks"></a>コメント

最初に要素を既存のヒープの最後にプッシュ バックしてから、アルゴリズムを使用してこの要素を既存のヒープに追加する必要があります。

ヒープには次の 2 つのプロパティがあります。

- 最初の要素は常に最大です。

- 要素は体数時間で追加または削除できます。

ヒープは、優先順位キューを実装するのに最適な方法です。C++ 標準ライブラリ コンテナー アダプター [priority_queue Class](../standard-library/priority-queue-class.md) の実装に使用されます。

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

最後に新しく追加された要素の除外範囲は、ヒープである必要があります。

複雑さは対数で、最大 `log(last - first)` の比較が必要です。

### <a name="example"></a>使用例

```cpp
// alg_push_heap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 1 ; i <= 9 ; i++ )
        v1.push_back( i );

    random_shuffle( v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Make v1 a heap with default less than ordering
    make_heap ( v1.begin( ), v1.end( ) );
    cout << "The heaped version of vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Add an element to the heap
    v1.push_back( 10 );
    cout << "The heap v1 with 10 pushed back is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    push_heap( v1.begin( ), v1.end( ) );
    cout << "The reheaped v1 with 10 added is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl << endl;

    // Make v1 a heap with greater than ordering
    make_heap ( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The greater-than heaped version of v1 is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    v1.push_back(0);
    cout << "The greater-than heap v1 with 11 pushed back is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    push_heap( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "The greater than reheaped v1 with 11 added is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="random_shuffle"></a>random_shuffle

Std:: random_shuffle () 関数は非推奨となり、 [std:: シャッフル](../standard-library/algorithm-functions.md#shuffle)に置き換えられました。 コード例と詳細については、「 [\<random >](../standard-library/random.md) 」と「 [std:: Random_shuffle メソッドが c++ 14 で非推奨 Stack Overflow とされる理由](https://go.microsoft.com/fwlink/p/?linkid=397954)」を参照してください。

## <a name="remove"></a>から

特定の範囲から指定された値を除去します。残りの要素の順序に影響を及ぼすことはなく、指定された値を含まない新しい範囲の末尾を返します。

```cpp
template<class ForwardIterator, class Type>
ForwardIterator remove(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Type>
ForwardIterator remove(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
要素が削除される範囲内の先頭の要素の位置を示す前方反復子。

*最後*の\
要素が削除される範囲内の末尾の要素の 1 つ後の位置を示す前方反復子。

*value*\
範囲から削除される値。

### <a name="return-value"></a>戻り値

変更された範囲の新しい末尾の位置、つまり、指定された値を含まない残されたシーケンスの最後の要素の 1 つ後を示す前方反復子。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

削除されなかった要素の順序はそのままになります。

要素間の等価性を決定するために使用される `operator==` は、そのオペランド間の同値関係を示している必要があります。

複雑さは線形的です。等しいかどうか (`last` - `first`) の比較があります。

[List クラス](../standard-library/list-class.md)には、`remove`のより効率的なメンバー関数バージョンが用意されています。これもポインターをエディットコンティニュします。

### <a name="example"></a>使用例

```cpp
// alg_remove.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements with a value of 7
    new_end = remove ( v1.begin( ), v1.end( ), 7 );

    cout << "Vector v1 with value 7 removed is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To change the sequence size, use erase
    v1.erase (new_end, v1.end( ) );

    cout << "Vector v1 resized with value 7 removed is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="remove_copy"></a>remove_copy

ソース範囲からターゲット範囲に要素をコピーしますが、指定された値の要素はコピーされません。残りの要素の順序に影響を及ぼすことはなく、新しいターゲット範囲の末尾を返します。

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator remove_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 remove_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& value);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
要素が削除される範囲内の最初の要素の位置を示す入力反復子。

*最後*の\
要素が削除される範囲内の最後の要素の 1 つ後ろの位置を示す入力反復子。

*結果*\
要素が削除されるターゲット範囲内の最初の要素の位置を示す出力反復子。

*value*\
範囲から削除される値。

### <a name="return-value"></a>戻り値

ターゲット範囲の新しい末尾の位置、つまり、指定された値を含まない残されたシーケンス コピーの最後の要素の 1 つ後ろを示す前方反復子。

### <a name="remarks"></a>コメント

参照されているソース範囲とターゲット範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

ターゲット範囲には、指定した値の要素が削除された後にコピーされる残りの要素を格納するのに十分な領域が必要です。

削除されなかった要素の順序はそのままになります。

要素間の等価性を決定するために使用される `operator==` は、そのオペランド間の同値関係を示している必要があります。

複雑さは線形的です。(`last` - `first`) の等価比較と、最大で (`last` - `first`) の割り当てがあります。

### <a name="example"></a>使用例

```cpp
// alg_remove_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle (v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:     ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements with a value of 7
    new_end = remove_copy ( v1.begin( ), v1.end( ), v2.begin( ), 7 );

    cout << "Vector v1 is left unchanged as ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is a copy of v1 with the value 7 removed:\n ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="remove_copy_if"></a>remove_copy_if

述語を満たす要素を除き、ソース範囲からターゲット範囲に要素をコピーします。 要素は、残りの要素の順序に支障をきたすことなくコピーされます。 新しいターゲット範囲の末尾を返します。

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate>
OutputIterator remove_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate>
ForwardIterator2 remove_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
要素が削除される範囲内の最初の要素の位置を示す入力反復子。

*最後*の\
要素が削除される範囲内の最後の要素の 1 つ後ろの位置を示す入力反復子。

*結果*\
要素が削除されるターゲット範囲内の最初の要素の位置を示す出力反復子。

*pred*\
満たす必要のある単項述語は、置き換えられる要素の値です。

### <a name="return-value"></a>戻り値

ターゲット範囲の最後の新しい位置、つまり、述語を満たす要素を含まない残されたシーケンスの最後の要素の 1 つ後ろを示す前方反復子。

### <a name="remarks"></a>コメント

参照されているソース範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

ターゲット範囲には、指定した値の要素が削除された後にコピーされる残りの要素を格納するのに十分な領域が必要です。

削除されなかった要素の順序はそのままになります。

要素間の等価性を決定するために使用される `operator==` は、そのオペランド間の同値関係を示している必要があります。

複雑さは線形的であり、(`last` - `first`) の等価比較と、最大で (`last` - `first`) の割り当てがあります。

これらの関数の動作については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>使用例

```cpp
// alg_remove_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value ) {
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2(10);
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:      ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements with a value greater than 6
    new_end = remove_copy_if ( v1.begin( ), v1.end( ),
        v2.begin( ), greater6 );

    cout << "After the appliation of remove_copy_if to v1,\n "
         << "vector v1 is left unchanged as ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is a copy of v1 with values greater "
         << "than 6 removed:\n ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != new_end ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="remove_if"></a>remove_if

特定の範囲から述語を満たす要素を除去します。残りの要素の順序に影響を及ぼすことはなく、指定された値を含まない新しい範囲の末尾を返します。

```cpp
template<class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate>
ForwardIterator remove_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
要素が削除される範囲内の最初の要素の位置を指定する前方反復子。

*最後*の\
要素が削除される範囲内の最後の要素の 1 つ後ろの位置を指定する前方反復子。

*pred*\
満たす必要のある単項述語は、置き換えられる要素の値です。

### <a name="return-value"></a>戻り値

変更された範囲の新しい末尾の位置、つまり、指定された値を含まない残されたシーケンスの最後の要素の 1 つ後を示す前方反復子。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

削除されなかった要素の順序はそのままになります。

要素間の等価性を決定するために使用される `operator==` は、そのオペランド間の同値関係を示している必要があります。

複雑さは線形的であり、(`last` - `first`) の等価比較があります。

list には、ポインターを再リンクする remove のより効率的なメンバー関数バージョンがあります。

### <a name="example"></a>使用例

```cpp
// alg_remove_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, new_end;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Remove elements satisfying predicate greater6
    new_end = remove_if (v1.begin( ), v1.end( ), greater6 );

    cout << "Vector v1 with elements satisfying greater6 removed is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To change the sequence size, use erase
    v1.erase (new_end, v1.end( ) );

    cout << "Vector v1 resized elements satisfying greater6 removed is\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace"></a>ら

範囲内の各要素が指定された値に一致するかどうかを調べ、一致する場合は置き換えます。

```cpp
template<class ForwardIterator, class Type>
void replace(
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator, class Type>
void replace(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
要素が置き換えられる範囲内の最初の要素の位置を指定する前方反復子。

*最後*の\
要素が置き換えられる範囲内の最後の要素の 1 つ後ろの位置を指定する前方反復子。

*Oldval*\
置き換えられる要素の古い値。

*Newval*\
古い値を持つ要素に割り当てられる新しい値。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

置き換えられなかった要素の順序はそのままになります。

要素間の等価性を決定するために使用される `operator==` は、そのオペランド間の同値関係を示している必要があります。

複雑さは線形的です。(`last` - `first`) の等価比較と、最大で (`last` - `first`) の新しい値の割り当てがあります。

### <a name="example"></a>使用例

```cpp
// alg_replace.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle (v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements with a value of 7 with a value of 700
    replace (v1.begin( ), v1.end( ), 7 , 700);

    cout << "The vector v1 with a value 700 replacing that of 7 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace_copy"></a>replace_copy

ソース範囲内の各要素が指定された値に一致するかどうかを調べ、一致する場合は置き換えて結果を新しいターゲット範囲にコピーします。

```cpp
template<class InputIterator, class OutputIterator, class Type>
OutputIterator replace_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    const Type& oldVal,
    const Type& newVal);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class Type>
ForwardIterator2 replace_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    const Type& oldVal,
    const Type& newVal);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
要素が置き換えられる範囲内の最初の要素の位置を指定する入力反復子。

*最後*の\
要素が置き換えられる範囲内の最後の要素の 1 つ後ろの位置を指定する入力反復子。

*結果*\
変更された要素シーケンスのコピー先ターゲット範囲の、最初の要素を指定する出力反復子。

*Oldval*\
置き換えられる要素の古い値。

*Newval*\
古い値を持つ要素に割り当てられる新しい値。

### <a name="return-value"></a>戻り値

変更された要素のシーケンスがコピーされるターゲット範囲内の最後の要素の1つ後ろの位置を指す出力反復子。

### <a name="remarks"></a>コメント

参照されているソース範囲とターゲット範囲は重複できません。また、両方とも有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

置き換えられなかった要素の順序はそのままになります。

要素間の等価性を決定するために使用される `operator==` は、そのオペランド間の同値関係を示している必要があります。

複雑さは線形的であり、(`last` - `first`) の等価比較と、最大で (`last` - `first`) の新しい値の割り当てがあります。

### <a name="example"></a>使用例

```cpp
// alg_replace_copy.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (15);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );

    int iii;
    for ( iii = 0 ; iii <= 15 ; iii++ )
        v1.push_back( 1 );

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements in one part of a vector with a value of 7
    // with a value of 70 and copy into another part of the vector
    replace_copy ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -15, 7 , 70);

    cout << "The vector v1 with a value 70 replacing that of 7 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements in a vector with a value of 70
    // with a value of 1 and copy into a list
    replace_copy ( v1.begin( ), v1.begin( ) + 14,L1.begin( ), 7 , 1);

    cout << "The list copy L1 of v1 with the value 0 replacing "
            << "that of 7 is:\n ( " ;
    for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
        cout << *L_Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace_copy_if"></a>replace_copy_if

ソース範囲内の各要素が指定された述語を満たすかどうかを調べ、満たす場合は置き換えて結果を新しいターゲット範囲にコピーします。

```cpp
template<class InputIterator, class OutputIterator, class UnaryPredicate, class Type>
OutputIterator replace_copy_if(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryPredicate, class Type>
ForwardIterator2 replace_copy_if(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
要素が置き換えられる範囲内の最初の要素の位置を指定する入力反復子。

*最後*の\
要素が置き換えられる範囲内の最後の要素の 1 つ後ろの位置を指定する入力反復子。

*結果*\
要素のコピー先ターゲット範囲内の最初の要素の位置を指し示す出力反復子。

*pred*\
満たす必要のある単項述語は、置き換えられる要素の値です。

*value*\
古い値が述語を満たす要素に割り当てられている新しい値。

### <a name="return-value"></a>戻り値

変更された要素のシーケンスがコピーされるターゲット範囲内の最後の要素の1つ後ろの位置を指す出力反復子。

### <a name="remarks"></a>コメント

参照されているソース範囲とターゲット範囲は重複できません。また、両方とも有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

置き換えられなかった要素の順序はそのままになります。

要素間の等価性を決定するために使用される `operator==` は、そのオペランド間の同値関係を示している必要があります。

複雑さは線形的です。(`last` - `first`) の等価比較と、最大で (`last` - `first`) の新しい値の割り当てがあります。

### <a name="example"></a>使用例

```cpp
// alg_replace_copy_if.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    list<int> L1 (13);
    vector<int>::iterator Iter1;
    list<int>::iterator L_Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );

    int iii;
    for ( iii = 0 ; iii <= 13 ; iii++ )
        v1.push_back( 1 );

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements with a value of 7 in the 1st half of a vector
    // with a value of 70 and copy it into the 2nd half of the vector
    replace_copy_if ( v1.begin( ), v1.begin( ) + 14,v1.end( ) -14,
        greater6 , 70);

    cout << "The vector v1 with values of 70 replacing those greater"
        << "\n than 6 in the 1st half & copied into the 2nd half is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements in a vector with a value of 70
    // with a value of 1 and copy into a list
    replace_copy_if ( v1.begin( ), v1.begin( ) + 13,L1.begin( ),
        greater6 , -1 );

    cout << "A list copy of vector v1 with the value -1\n replacing "
        << "those greater than 6 is:\n ( " ;
    for ( L_Iter1 = L1.begin( ) ; L_Iter1 != L1.end( ) ; L_Iter1++ )
        cout << *L_Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="replace_if"></a>replace_if

範囲内の各要素が指定された述語を満たすかどうかを調べ、満たす場合は置き換えます。

```cpp
template<class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class UnaryPredicate, class Type>
void replace_if(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    UnaryPredicate pred,
    const Type& value);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
要素が置き換えられる範囲内の最初の要素の位置を指定する前方反復子。

*最後*の\
要素が置き換えられる範囲内の最後の要素の 1 つ後ろの位置を指定する反復子。

*pred*\
満たす必要のある単項述語は、置き換えられる要素の値です。

*value*\
古い値が述語を満たす要素に割り当てられている新しい値。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

置き換えられなかった要素の順序はそのままになります。

アルゴリズム `replace_if` はアルゴリズム `replace`を一般化したものであり、指定された定数値と等価ではなく、任意の述語を指定できます。

要素間の等価性を決定するために使用される `operator==` は、そのオペランド間の同値関係を示している必要があります。

複雑さは線形的であり、(`last` - `first`) の等価比較と、最大で (`last` - `first`) の新しい値の割り当てがあります。

### <a name="example"></a>使用例

```cpp
// alg_replace_if.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater6 ( int value )
{
    return value > 6;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
        v1.push_back( 7 );

    random_shuffle ( v1.begin( ), v1.end( ) );
    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Replace elements satisfying the predicate greater6
    // with a value of 70
    replace_if ( v1.begin( ), v1.end( ), greater6 , 70);

    cout << "The vector v1 with a value 70 replacing those\n "
         << "elements satisfying the greater6 predicate is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="reverse"></a>後ろ向き

範囲内の要素の順序を反転させます。

```cpp
template<class BidirectionalIterator>
void reverse(
    BidirectionalIterator first,
    BidirectionalIterator last);

template<class ExecutionPolicy, class BidirectionalIterator>
void reverse(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
要素の順序を変える範囲内の最初の要素の位置を指し示す双方向反復子。

*最後*の\
要素の順序を変える範囲内の、最後の要素の 1 つ後ろの位置を指し示す入力反復子。

### <a name="remarks"></a>コメント

参照されているソース範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

### <a name="example"></a>使用例

```cpp
// alg_reverse.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Reverse the elements in the vector
    reverse (v1.begin( ), v1.end( ) );

    cout << "The modified vector v1 with values reversed is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 0 1 2 3 4 5 6 7 8 9 ).
The modified vector v1 with values reversed is:
( 9 8 7 6 5 4 3 2 1 0 ).
```

## <a name="reverse_copy"></a>reverse_copy

ソース範囲内の要素の順序を反転し、結果をターゲット範囲にコピーします。

```cpp
template<class BidirectionalIterator, class OutputIterator>
OutputIterator reverse_copy(
    BidirectionalIterator first,
    BidirectionalIterator last,
    OutputIterator result);

template<class ExecutionPolicy, class BidirectionalIterator, class ForwardIterator>
ForwardIterator reverse_copy(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    ForwardIterator result);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
要素の順序を変えるソース範囲内の最初の要素の位置を指し示す双方向反復子。

*最後*の\
要素の順序を変えるソース範囲内の、最後の要素の 1 つ後ろの位置を指し示す入力反復子。

*結果*\
要素のコピー先ターゲット範囲内の最初の要素の位置を指し示す出力反復子。

### <a name="return-value"></a>戻り値

変更された要素のシーケンスがコピーされるターゲット範囲内の最後の要素の1つ後ろの位置を指す出力反復子。

### <a name="remarks"></a>コメント

参照されているソース範囲とターゲット範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

### <a name="example"></a>使用例

```cpp
// alg_reverse_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2( 10 );
    vector<int>::iterator Iter1, Iter2;

    int i;
    for ( i = 0 ; i <= 9 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "The original vector v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Reverse the elements in the vector
    reverse_copy (v1.begin( ), v1.end( ), v2.begin( ) );

    cout << "The copy v2 of the reversed vector v1 is:\n ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    cout << "The original vector v1 remains unmodified as:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;
}
```

## <a name="rotate"></a>回転

2 つの隣接する範囲の要素を交換します。

```cpp
template<class ForwardIterator>
void rotate(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator rotate(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
回転対象の範囲内の最初の要素の位置を示す前方反復子。

*中央*\
範囲の境界を定義する前方反復子。範囲の最初の部分にある要素と交換される要素が含まれる 2 番目の部分の最初の要素の位置を示します。

*最後*の\
回転対象の範囲内の最後の要素の 1 つ後ろの位置を示す前方反復子。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

複雑さは線形的で、最大で (`last` - `first`) のスワップがあります。

### <a name="example"></a>使用例

```cpp
// alg_rotate.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main() {
    using namespace std;
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
    deque<int>::iterator d1Iter1;

    int i;
    for ( i = -3 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =0 ; ii <= 5 ; ii++ )
    {
        d1.push_back( ii );
    }

    cout << "Vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    rotate ( v1.begin( ), v1.begin( ) + 3 , v1.end( ) );
    cout << "After rotating, vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) ) {
        rotate ( d1.begin( ), d1.begin( ) + 1 , d1.end( ) );
        cout << "After the rotation of a single deque element to the back,\n d1 is   ( " ;
        for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
            cout << *d1Iter1 << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

```Output
Vector v1 is ( -3 -2 -1 0 1 2 3 4 5 ).
After rotating, vector v1 is ( 0 1 2 3 4 5 -3 -2 -1 ).
The original deque d1 is ( 0 1 2 3 4 5 ).
After the rotation of a single deque element to the back,
d1 is   ( 1 2 3 4 5 0 ).
After the rotation of a single deque element to the back,
d1 is   ( 2 3 4 5 0 1 ).
After the rotation of a single deque element to the back,
d1 is   ( 3 4 5 0 1 2 ).
After the rotation of a single deque element to the back,
d1 is   ( 4 5 0 1 2 3 ).
After the rotation of a single deque element to the back,
d1 is   ( 5 0 1 2 3 4 ).
After the rotation of a single deque element to the back,
d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="rotate_copy"></a>rotate_copy

ソース範囲内の 2 つの隣接する範囲の要素を交換し、結果をターゲット範囲にコピーします。

```cpp
template<class ForwardIterator, class OutputIterator>
OutputIterator rotate_copy(
    ForwardIterator first,
    ForwardIterator middle,
    ForwardIterator last,
    OutputIterator result );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 rotate_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 middle,
    ForwardIterator1 last,
    ForwardIterator2 result);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
回転対象の範囲内の最初の要素の位置を示す前方反復子。

*中央*\
範囲の境界を定義する前方反復子。範囲の最初の部分にある要素と交換される要素が含まれる 2 番目の部分の最初の要素の位置を示します。

*最後*の\
回転対象の範囲内の最後の要素の 1 つ後ろの位置を示す前方反復子。

*結果*\
ターゲット範囲の最初の要素の位置を示す出力反復子。

### <a name="return-value"></a>戻り値

ターゲット範囲の最後の要素の 1 つ後ろの位置を示す出力反復子。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

複雑さは線形的で、最大で (`last` - `first`) のスワップがあります。

### <a name="example"></a>使用例

```cpp
// alg_rotate_copy.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1 , v2 ( 9 );
    deque<int> d1 , d2 ( 6 );
    vector<int>::iterator v1Iter , v2Iter;
    deque<int>::iterator d1Iter , d2Iter;

    int i;
    for ( i = -3 ; i <= 5 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii =0 ; ii <= 5 ; ii++ )
        d1.push_back( ii );

    cout << "Vector v1 is ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    rotate_copy ( v1.begin( ), v1.begin( ) + 3 , v1.end( ), v2.begin( ) );
    cout << "After rotating, the vector v1 remains unchanged as:\n v1 = ( " ;
    for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ;v1Iter ++ )
        cout << *v1Iter << " ";
    cout << ")." << endl;

    cout << "After rotating, the copy of vector v1 in v2 is:\n v2 = ( " ;
    for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ;v2Iter ++ )
        cout << *v2Iter << " ";
    cout << ")." << endl;

    cout << "The original deque d1 is ( " ;
    for ( d1Iter = d1.begin( ) ; d1Iter != d1.end( ) ;d1Iter ++ )
        cout << *d1Iter << " ";
    cout << ")." << endl;

    int iii = 1;
    while ( iii <= d1.end( ) - d1.begin( ) )
    {
        rotate_copy ( d1.begin( ), d1.begin( ) + iii , d1.end( ), d2.begin( ) );
        cout << "After the rotation of a single deque element to the back,\n d2 is   ( " ;
        for ( d2Iter = d2.begin( ) ; d2Iter != d2.end( ) ;d2Iter ++ )
            cout << *d2Iter << " ";
        cout << ")." << endl;
        iii++;
    }
}
```

## <a name="sample"></a>サンプル

```cpp
template<class PopulationIterator, class SampleIterator, class Distance, class UniformRandomBitGenerator>
SampleIterator sample(
    PopulationIterator first,
    PopulationIterator last,
    SampleIterator out,
    Distance n,
    UniformRandomBitGenerator&& g);
```

## <a name="search"></a>サーチ

要素が特定の要素シーケンス内の要素と等しいか、または要素が二項述語で指定される意味において特定のシーケンス内の要素と等価であるシーケンスが、対象範囲内で最初に出現する位置を検索します。

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class BinaryPredicate>
ForwardIterator1 search(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    BinaryPredicate pred);

template <class ForwardIterator, class Searcher>
ForwardIterator search(
    ForwardIterator first,
    ForwardIterator last,
    const Searcher& searcher);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
検索範囲内の先頭の要素の位置を示す前方反復子。

*last1*\
検索範囲の最後の要素の 1 つ後ろの位置を示す前方反復子。

*first2*\
照合範囲内の先頭の要素の位置を示す前方反復子。

*last2*\
照合範囲の最後の要素の 1 つ後ろの位置を示す前方反復子。

*pred*\
2 つの要素が等価であると見なされた場合に条件が満たされると定義する、ユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

*サーチャー*\
検索するパターンと使用する検索アルゴリズムをカプセル化するサーチャー。 Searchers の詳細については、「 [default_searcher クラス](default-searcher-class.md)、 [boyer_moore_horspool_searcher クラス](boyer-moore-horspool-searcher-class.md)、および[boyer_moore_searcher クラス](boyer-moore-searcher-class.md)」を参照してください。

### <a name="return-value"></a>戻り値

指定したシーケンスと一致するか二項述語で指定された意味で等価である、最初のサブシーケンスの最初の要素の位置を指す前方反復子。

### <a name="remarks"></a>コメント

要素と指定された値の間の一致を判断するために使用される `operator==` によって、オペランド間の等価関係が強制される必要があります。

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

平均の複雑さは、検索範囲のサイズに対して線形的で、最も複雑な場合は、検索対象のシーケンスのサイズに対しても線形的です。

### <a name="example"></a>使用例

```cpp
// alg_search.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is twice the first
bool twice (int elem1, int elem2 )
{
    return 2 * elem1 == elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    list<int> L1;
    vector<int>::iterator Iter1, Iter2;
    list<int>::iterator L1_Iter, L1_inIter;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    int ii;
    for ( ii = 4 ; ii <= 5 ; ii++ )
    {
        L1.push_back( 5 * ii );
    }

    int iii;
    for ( iii = 2 ; iii <= 4 ; iii++ )
    {
        v2.push_back( 10 * iii );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    cout << "List L1 = ( " ;
    for ( L1_Iter = L1.begin( ) ; L1_Iter!= L1.end( ) ; L1_Iter++ )
        cout << *L1_Iter << " ";
    cout << ")" << endl;

    cout << "Vector v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
        cout << ")" << endl;

    // Searching v1 for first match to L1 under identity
    vector<int>::iterator result1;
    result1 = search (v1.begin( ), v1.end( ), L1.begin( ), L1.end( ) );

    if ( result1 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is at least one match of L1 in v1"
            << "\n and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for a match to L1 under the binary predicate twice
    vector<int>::iterator result2;
    result2 = search (v1.begin( ), v1.end( ), v2.begin( ), v2.end( ), twice );

    if ( result2 == v1.end( ) )
        cout << "There is no match of L1 in v1."
            << endl;
    else
        cout << "There is a sequence of elements in v1 that "
            << "are equivalent\n to those in v2 under the binary "
            << "predicate twice\n and the first one begins at position "
            << result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 0 5 10 15 20 25 )
List L1 = ( 20 25 )
Vector v2 = ( 20 30 40 )
There is at least one match of L1 in v1
and the first one begins at position 4.
There is a sequence of elements in v1 that are equivalent
to those in v2 under the binary predicate twice
and the first one begins at position 2.
```

## <a name="search_n"></a>search_n

特定の値を持つか、二項述語によって指定される値と関連する、指定された数の要素で構成される範囲内の最初のサブシーケンスを検索します。

```cpp
template<class ForwardIterator1, class Diff2, class Type>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value);

template<class ForwardIterator1, class Diff2, class Type, class BinaryPredicate>
ForwardIterator1 search_n(
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    Diff2 count,
    const Type& value,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value);

template<class ExecutionPolicy, class ForwardIterator, class Size, class Type, class BinaryPredicate>
ForwardIterator search_n(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    Size count,
    const Type& value,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
検索範囲内の先頭の要素の位置を示す前方反復子。

*last1*\
検索範囲の最後の要素の 1 つ後ろの位置を示す前方反復子。

*カウント*\
検索対象のサブシーケンスのサイズ。

*value*\
検索対象のシーケンス内の要素の値。

*pred*\
2 つの要素が等価であると見なされた場合に条件が満たされると定義する、ユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="return-value"></a>戻り値

指定したシーケンスと一致するか二項述語で指定された意味で等価である、最初のサブシーケンスの最初の要素の位置を指す前方反復子。

### <a name="remarks"></a>コメント

要素と指定された値の間の一致を判断するために使用される `operator==` によって、オペランド間の等価関係が強制される必要があります。

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

複雑さは、検索されたサイズに対して線形的です。

### <a name="example"></a>使用例

```cpp
// alg_search_n.cpp
// compile with: /EHsc
#include <vector>
#include <list>
#include <algorithm>
#include <iostream>

// Return whether second element is 1/2 of the first
bool one_half ( int elem1, int elem2 )
{
    return elem1 == 2 * elem2;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 5 );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 5 * i );
    }

    for ( i = 0 ; i <= 2 ; i++ )
    {
        v1.push_back( 10 );
    }

    cout << "Vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // Searching v1 for first match to (5 5 5) under identity
    vector<int>::iterator result1;
    result1 = search_n ( v1.begin( ), v1.end( ), 3, 5 );

    if ( result1 == v1.end( ) )
        cout << "There is no match for a sequence ( 5 5 5 ) in v1."
            << endl;
    else
        cout << "There is at least one match of a sequence ( 5 5 5 )"
            << "\n in v1 and the first one begins at "
            << "position "<< result1 - v1.begin( ) << "." << endl;

    // Searching v1 for first match to (5 5 5) under one_half
    vector<int>::iterator result2;
    result2 = search_n (v1.begin( ), v1.end( ), 3, 5, one_half );

    if ( result2 == v1.end( ) )
        cout << "There is no match for a sequence ( 5 5 5 ) in v1"
            << " under the equivalence predicate one_half." << endl;
    else
        cout << "There is a match of a sequence ( 5 5 5 ) "
            << "under the equivalence\n predicate one_half "
            << "in v1 and the first one begins at "
            << "position "<< result2 - v1.begin( ) << "." << endl;
}
```

```Output
Vector v1 = ( 0 5 10 15 20 25 5 5 5 0 5 10 15 20 25 10 10 10 )
There is at least one match of a sequence ( 5 5 5 )
in v1 and the first one begins at position 6.
There is a match of a sequence ( 5 5 5 ) under the equivalence
predicate one_half in v1 and the first one begins at position 15.
```

## <a name="set_difference"></a>set_difference

1 つの並べ替えられたソース範囲内に属するが、2 番目の並べ替えられたソース範囲には属さないすべての要素を単一の並べ替えられたターゲット範囲として結合します。順序の基準は二項述語によって指定できます。

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
2 つのソース範囲の差を表すために単一の範囲に結合され並べ替えられる 2 つの並べ替え済みソース範囲の、最初の範囲の最初の要素の位置を示す入力反復子。

*last1*\
2 つのソース範囲の差を表すために単一の範囲に結合され並べ替えられる 2 つの並べ替え済みソース範囲の、最初の範囲の最後の要素の 1 つ後ろの位置を示す入力反復子。

*first2*\
2 つのソース範囲の差を表すために単一の範囲に結合され並べ替えられる 2 つの連続する並べ替え済みソース範囲の、2 番目の範囲の最初の要素の位置を示す入力反復子。

*last2*\
2 つのソース範囲の差を表すために単一の範囲に結合され並べ替えられる 2 つの連続する並べ替え済みソース範囲の、2 番目の範囲の最後の要素の 1 つ後ろの位置を示す入力反復子。

*結果*\
2 つのソース範囲の差を表すために 2 つのソース範囲が単一の並べ替え済みの範囲に結合されるターゲット範囲の、最初の要素の位置を示す出力反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 2 項述語は 2 つの引数を受け取り、最初の要素が 2 番目の要素より小さい場合は **true** 、そうでない場合は **false** を返す必要があります。

### <a name="return-value"></a>戻り値

2 つのソース範囲の差を表すための並べ替え済みのターゲット範囲の、最後の要素の 1 つ後ろの位置を示す出力反復子。

### <a name="remarks"></a>コメント

参照される並べ替えられたソース範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

ターゲット範囲はソース範囲のいずれかと重ならないようにします。また、最初のソース範囲を格納するのに十分な大きさが必要です。

`set_difference` アルゴリズムを適用するための事前条件として、それぞれの並べ替えられたソース範囲は、結合された範囲の並べ替えにアルゴリズムが使用したのと同じ順序の基準に従って並べ替えられている必要があります。

各範囲内の要素の相対順序はターゲット範囲内でも維持されるため、操作は安定しています。 ソース範囲が merge アルゴリズムによって変更されることはありません。

入力反復子の値の型は、小なり (less-than) 比較ができる必要があります。これにより、2 つの要素が与えられたときに、それらが等しいか (いずれも他方より小さくない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 両方のソース範囲に同等の要素がある場合は、ターゲット範囲では、最初の範囲の要素が、2 番目のソース範囲の要素よりも前に置かれます。 ソース範囲で要素が重複している場合、たとえば、最初のソース範囲の要素の数が 2 番目のソース範囲の要素の数を上回る場合、ターゲット範囲には、最初のソース範囲と 2 番目のソース範囲の該当する要素の出現回数の差を示す数値が含まれます。

アルゴリズムの複雑さは線形的で、空でないソース範囲に対して最大 `2 * ((last1 - first1) - (last2 - first2)) - 1` の比較があります。

### <a name="example"></a>使用例

```cpp
// alg_set_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if (elem1 < 0)
        elem1 = - elem1;
    if (elem2 < 0)
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a difference in asscending
    // order with the default binary predicate less<int>( )
    Result1 = set_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a difference in descending
    // order specify binary predicate greater<int>( )
    Result2 = set_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_intersection"></a>set_intersection

両方の並べ替えられたソース範囲に属するすべての要素を単一の並べ替えられたターゲット範囲として結合します。順序の基準は二項述語によって指定できます。

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result);

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_intersection(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_intersection(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
2 つのソース範囲の交差を表すために単一の範囲に結合され並べ替えられる 2 つの並べ替え済みソース範囲の、最初の範囲の最初の要素の位置を示す入力反復子。

*last1*\
2 つのソース範囲の交差を表すために単一の範囲に結合され並べ替えられる 2 つの並べ替え済みソース範囲の、最初の範囲の最後の要素の 1 つ後ろの位置を示す入力反復子。

*first2*\
2 つのソース範囲の交差を表すために単一の範囲に結合され並べ替えられる 2 つの連続する並べ替え済みソース範囲の、2 番目の範囲の最初の要素の位置を示す入力反復子。

*last2*\
2 つのソース範囲の交差を表すために単一の範囲に結合され並べ替えられる 2 つの連続する並べ替え済みソース範囲の、2 番目の範囲の最後の要素の 1 つ後ろの位置を示す入力反復子。

*結果*\
2 つのソース範囲の交差を表すために 2 つのソース範囲が単一の並べ替え済みの範囲に結合されるターゲット範囲の、最初の要素の位置を示す出力反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 2 項述語は 2 つの引数を受け取り、最初の要素が 2 番目の要素より小さい場合は **true** 、そうでない場合は **false** を返す必要があります。

### <a name="return-value"></a>戻り値

2 つのソース範囲の交差を表すための並べ替え済みのターゲット範囲の、最後の要素の 1 つ後ろの位置を示す出力反復子。

### <a name="remarks"></a>コメント

参照される並べ替えられたソース範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

ターゲット範囲はソース範囲のいずれかと重ならないようにします。また、ターゲット範囲を格納するのに十分な大きさが必要です。

merge アルゴリズムを適用するための事前条件として、それぞれの並べ替えられたソース範囲は、結合された範囲の並べ替えにアルゴリズムが使用したのと同じ順序の基準に従って並べ替えられている必要があります。

各範囲内の要素の相対順序はターゲット範囲内でも維持されるため、操作は安定しています。 ソース範囲がこのアルゴリズムによって変更されることはありません。

入力反復子の値の型は、小なり (less-than) 比較ができる必要があります。これにより、2 つの要素が与えられたときに、それらが等しいか (いずれも他方より小さくない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 両方のソース範囲に同等の要素がある場合は、ターゲット範囲では、最初の範囲の要素が、2 番目のソース範囲の要素よりも前に置かれます。 ソース範囲内で要素が重複している場合、ターゲット範囲は、両方のソース範囲内に存在する該当する要素の最大数を含みます。

アルゴリズムの複雑さは線形的で、空でないソース範囲に対して最大 `2 * ((last1 - first1) + (last2 - first2)) - 1` の比較があります。

### <a name="example"></a>使用例

```cpp
// alg_set_intersection.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>   // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
        v1a.push_back( i );

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
        v1b.push_back( ii );

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into an intersection in asscending order with the
    // default binary predicate less<int>( )
    Result1 = set_intersection ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Intersection of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; ++Iter1 )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into an intersection in descending order, specify
    // binary predicate greater<int>( )
    Result2 = set_intersection ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Intersection of source ranges with binary predicate"
            << " greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; ++Iter2 )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into an intersection applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_intersection ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Intersection of source ranges with binary predicate "
            << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; ++Iter3 )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_symmetric_difference"></a>set_symmetric_difference

並べ替えられたソース範囲の一方には属するが、両方には属さないすべての要素を単一の並べ替えられたターゲット範囲として結合します。順序の基準は二項述語によって指定できます。

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_symmetric_difference(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_symmetric_difference(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
2 つのソース範囲の対称差を表すために単一の範囲に結合され並べ替えられる 2 つの並べ替え済みソース範囲の、最初の範囲の最初の要素の位置を示す入力反復子。

*last1*\
2 つのソース範囲の対称差を表すために単一の範囲に結合され並べ替えられる 2 つの並べ替え済みソース範囲の、最初の範囲の最後の要素の 1 つ後ろの位置を示す入力反復子。

*first2*\
2 つのソース範囲の対称差を表すために単一の範囲に結合され並べ替えられる 2 つの連続する並べ替え済みソース範囲の、2 番目の範囲の最初の要素の位置を示す入力反復子。

*last2*\
2 つのソース範囲の対称差を表すために単一の範囲に結合され並べ替えられる 2 つの連続する並べ替え済みソース範囲の、2 番目の範囲の最後の要素の 1 つ後ろの位置を示す入力反復子。

*結果*\
2 つのソース範囲の対称差を表すために 2 つのソース範囲が単一の並べ替え済みの範囲に結合されるターゲット範囲の、最初の要素の位置を示す出力反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 2 項述語は 2 つの引数を受け取り、最初の要素が 2 番目の要素より小さい場合は **true** 、そうでない場合は **false** を返す必要があります。

### <a name="return-value"></a>戻り値

2 つのソース範囲の対称差を表すための並べ替え済みのターゲット範囲の、最後の要素の 1 つ後ろの位置を示す出力反復子。

### <a name="remarks"></a>コメント

参照される並べ替えられたソース範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

ターゲット範囲はソース範囲のいずれかと重ならないようにします。また、ターゲット範囲を格納するのに十分な大きさが必要です。

`merge*` アルゴリズムを適用するための事前条件として、それぞれの並べ替えられたソース範囲は、結合された範囲の並べ替えにアルゴリズムが使用したのと同じ順序の基準に従って並べ替えられている必要があります。

各範囲内の要素の相対順序はターゲット範囲内でも維持されるため、操作は安定しています。 ソース範囲が merge アルゴリズムによって変更されることはありません。

入力反復子の値の型は、小なり (less-than) 比較ができる必要があります。これにより、2 つの要素が与えられたときに、それらが等しいか (いずれも他方より小さくない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 両方のソース範囲に同等の要素がある場合は、ターゲット範囲では、最初の範囲の要素が、2 番目のソース範囲の要素よりも前に置かれます。 ソース範囲内で要素が重複している場合、ターゲット範囲には、1 番目と 2 番目のソース範囲内の該当する要素の出現回数の差を示す絶対値が含まれます。

アルゴリズムの複雑さは線形的で、空でないソース範囲に対して最大 `2 * ((last1 - first1) - (last2 - first2)) - 1` の比較があります。

### <a name="example"></a>使用例

```cpp
// alg_set_sym_diff.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser (int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less-than ordering
    int i;
    for ( i = -1 ; i <= 4 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 0 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in ascending
    // order with the default binary predicate less<int>( )
    Result1 = set_symmetric_difference ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Set_symmetric_difference of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference in descending
    // order, specify binary predicate greater<int>( )
    Result2 = set_symmetric_difference ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Set_symmetric_difference of source ranges with binary"
         << "predicate greater specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a symmetric difference applying a user
    // defined binary predicate mod_lesser
    Result3 = set_symmetric_difference ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Set_symmetric_difference of source ranges with binary "
         << "predicate mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="set_union"></a>set_union

2 つの並べ替えられたソース範囲の少なくとも一方に属するすべての要素を単一の並べ替えられたターゲット範囲として結合します。順序の基準は二項述語によって指定できます。

```cpp
template<class InputIterator1, class InputIterator2, class OutputIterator>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result );

template<class InputIterator1, class InputIterator2, class OutputIterator, class Compare>
OutputIterator set_union(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    InputIterator2 last2,
    OutputIterator result,
    Compare pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class Compare>
ForwardIterator set_union(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator2 last2,
    ForwardIterator result,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
2 つのソース範囲の和集合を表すために単一の範囲に結合され並べ替えられる 2 つの並べ替え済みソース範囲の、最初の範囲の最初の要素の位置を示す入力反復子。

*last1*\
2 つのソース範囲の和集合を表すために単一の範囲に結合され並べ替えられる 2 つの並べ替え済みソース範囲の、最初の範囲の最後の要素の 1 つ後ろの位置を示す入力反復子。

*first2*\
2 つのソース範囲の和集合を表すために単一の範囲に結合され並べ替えられる 2 つの連続する並べ替え済みソース範囲の、2 番目の範囲の最初の要素の位置を示す入力反復子。

*last2*\
2 つのソース範囲の和集合を表すために単一の範囲に結合され並べ替えられる 2 つの連続する並べ替え済みソース範囲の、2 番目の範囲の最後の要素の 1 つ後ろの位置を示す入力反復子。

*結果*\
2 つのソース範囲の和集合を表すために 2 つのソース範囲が単一の並べ替え済みの範囲に結合されるターゲット範囲の、最初の要素の位置を示す出力反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 2 項述語は 2 つの引数を受け取り、最初の要素が 2 番目の要素より小さい場合は **true** 、そうでない場合は **false** を返す必要があります。

### <a name="return-value"></a>戻り値

2 つのソース範囲の和集合を表すための並べ替え済みのターゲット範囲の、最後の要素の 1 つ後ろの位置を示す出力反復子。

### <a name="remarks"></a>コメント

参照される並べ替えられたソース範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

ターゲット範囲はソース範囲のいずれかと重ならないようにします。また、ターゲット範囲を格納するのに十分な大きさが必要です。

`merge` アルゴリズムを適用するための事前条件として、それぞれの並べ替えられたソース範囲は、結合された範囲の並べ替えにアルゴリズムが使用したのと同じ順序の基準に従って並べ替えられている必要があります。

各範囲内の要素の相対順序はターゲット範囲内でも維持されるため、操作は安定しています。 ソース範囲は、`merge`アルゴリズムによって変更されることはありません。

入力反復子の値の型は、小なり (less-than) 比較ができる必要があります。これにより、2 つの要素が与えられたときに、それらが等しいか (いずれも他方より小さくない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 両方のソース範囲に同等の要素がある場合は、ターゲット範囲では、最初の範囲の要素が、2 番目のソース範囲の要素よりも前に置かれます。 ソース範囲内で要素が重複している場合、ターゲット範囲は、両方のソース範囲内に存在する該当する要素の最大数を含みます。

アルゴリズムの複雑さは線形的で、最大 `2 * ((last1 - first1) - (last2 - first2)) - 1` の比較があります。

### <a name="example"></a>使用例

```cpp
// alg_set_union.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;
    vector<int> v1a, v1b, v1 ( 12 );
    vector<int>::iterator Iter1a, Iter1b, Iter1, Result1;

    // Constructing vectors v1a & v1b with default less than ordering
    int i;
    for ( i = -1 ; i <= 3 ; i++ )
    {
        v1a.push_back( i );
    }

    int ii;
    for ( ii =-3 ; ii <= 1 ; ii++ )
    {
        v1b.push_back( ii );
    }

    cout << "Original vector v1a with range sorted by the\n "
         << "binary predicate less than is v1a = ( " ;
    for ( Iter1a = v1a.begin( ) ; Iter1a != v1a.end( ) ; Iter1a++ )
        cout << *Iter1a << " ";
    cout << ")." << endl;

    cout << "Original vector v1b with range sorted by the\n "
         << "binary predicate less than is v1b = ( " ;
    for ( Iter1b = v1b.begin( ) ; Iter1b != v1b.end( ) ; Iter1b++ )
        cout << *Iter1b << " ";
    cout << ")." << endl;

    // Constructing vectors v2a & v2b with ranges sorted by greater
    vector<int> v2a ( v1a ) , v2b ( v1b ) , v2 ( v1 );
    vector<int>::iterator Iter2a, Iter2b, Iter2, Result2;
    sort ( v2a.begin( ), v2a.end( ), greater<int>( ) );
    sort ( v2b.begin( ), v2b.end( ), greater<int>( ) );

    cout << "Original vector v2a with range sorted by the\n "
         << "binary predicate greater is   v2a = ( " ;
    for ( Iter2a = v2a.begin( ) ; Iter2a != v2a.end( ) ; Iter2a++ )
        cout << *Iter2a << " ";
    cout << ")." << endl;

    cout << "Original vector v2b with range sorted by the\n "
         << "binary predicate greater is   v2b = ( " ;
    for ( Iter2b = v2b.begin( ) ; Iter2b != v2b.end( ) ; Iter2b++ )
        cout << *Iter2b << " ";
    cout << ")." << endl;

    // Constructing vectors v3a & v3b with ranges sorted by mod_lesser
    vector<int> v3a ( v1a ), v3b ( v1b ) , v3 ( v1 );
    vector<int>::iterator Iter3a, Iter3b, Iter3, Result3;
    sort ( v3a.begin( ), v3a.end( ), mod_lesser );
    sort ( v3b.begin( ), v3b.end( ), mod_lesser );

    cout << "Original vector v3a with range sorted by the\n "
         << "binary predicate mod_lesser is   v3a = ( " ;
    for ( Iter3a = v3a.begin( ) ; Iter3a != v3a.end( ) ; Iter3a++ )
        cout << *Iter3a << " ";
    cout << ")." << endl;

    cout << "Original vector v3b with range sorted by the\n "
         << "binary predicate mod_lesser is   v3b = ( " ;
    for ( Iter3b = v3b.begin( ) ; Iter3b != v3b.end( ) ; Iter3b++ )
        cout << *Iter3b << " ";
    cout << ")." << endl;

    // To combine into a union in ascending order with the default
        // binary predicate less<int>( )
    Result1 = set_union ( v1a.begin( ), v1a.end( ),
        v1b.begin( ), v1b.end( ), v1.begin( ) );
    cout << "Union of source ranges with default order,"
         << "\n vector v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != Result1 ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // To combine into a union in descending order, specify binary
    // predicate greater<int>( )
    Result2 = set_union ( v2a.begin( ), v2a.end( ),
        v2b.begin( ), v2b.end( ),v2.begin( ), greater<int>( ) );
    cout << "Union of source ranges with binary predicate greater "
         << "specified,\n vector v2mod = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != Result2 ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // To combine into a union applying a user-defined
    // binary predicate mod_lesser
    Result3 = set_union ( v3a.begin( ), v3a.end( ),
        v3b.begin( ), v3b.end( ), v3.begin( ), mod_lesser );
    cout << "Union of source ranges with binary predicate "
         << "mod_lesser specified,\n vector v3mod = ( " ; ;
    for ( Iter3 = v3.begin( ) ; Iter3 != Result3 ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

## <a name="shuffle"></a>シャッフル

乱数ジェネレーターを使用して、指定された範囲の要素をシャッフル (再配置) します。

```cpp
template<class RandomAccessIterator, class UniformRandomNumberGenerator>
void shuffle(
    RandomAccessIterator first,
    RandomAccessIterator last,
    UniformRandomNumberGenerator&& gen);
```

### <a name="parameters"></a>パラメーター

*最初*の\
シャッフルされる範囲 (境界を含む) の最初の要素に対する反復子。 `RandomAccessIterator` および `ValueSwappable` の要件を満たしている必要があります。

*最後*の\
シャッフルされる範囲 (境界を含まない) の最後の要素に対する反復子。 `RandomAccessIterator` および `ValueSwappable` の要件を満たしている必要があります。

*gen*\
`shuffle()` 関数が操作で使用する乱数ジェネレーター。 `UniformRandomNumberGenerator` の要件を満たしている必要があります。

### <a name="remarks"></a>コメント

`shuffle()` を使用するコード サンプルの詳細については、「[\<random>](../standard-library/random.md)」を参照してください。

## <a name="sort"></a>基づく

指定された範囲の要素を、降順以外の順序、または二項述語で指定された順序の基準に従って配置します。

```cpp
template<class RandomAccessIterator>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);

template<class ExecutionPolicy, class RandomAccessIterator>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
並べ替えられる範囲内の最初の要素の位置を示すランダム アクセス反復子。

*最後*の\
並べ替えられる範囲内の最後の要素の 1 つ後ろの位置を示すランダム アクセス反復子。

*pred*\
順序内の次の要素によって満たされる比較条件を定義するユーザー定義の述語関数オブジェクト。 この二項述語は2つの引数を受け取り、2つの引数が順序付けられている場合は**true**を返し、それ以外の場合は**false**を返します。 この比較子関数は、シーケンスからの要素のペアで厳密弱順序を強制する必要があります。 詳細については、「[アルゴリズム](../standard-library/algorithms.md)」をご覧ください。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

どちらの要素も他方より小さくない場合、要素は同等ですが、必ずしも等しいわけではありません。 `sort` アルゴリズムは安定していないため、同等の要素の相対順序が保持されることを保証しません。 アルゴリズム `stable_sort` は元の順序を保持します。

並べ替えの複雑さの平均は `O( N log N )`*です。ここ*で、 *N* = *最後*に - ます。

### <a name="example"></a>使用例

```cpp
// alg_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater ( int elem1, int elem2 )
{
    return elem1 > elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    int ii;
    for ( ii = 0 ; ii <= 5 ; ii++ )
    {
        v1.push_back( 2 * ii + 1 );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    sort( v1.begin( ), v1.end( ) );
    cout << "Sorted vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To sort in descending order. specify binary predicate
    sort( v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "Resorted (greater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    sort( v1.begin( ), v1.end( ), UDgreater );
    cout << "Resorted (UDgreater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 1 3 5 7 9 11 )
Sorted vector v1 = ( 0 1 2 3 4 5 6 7 8 9 10 11 )
Resorted (greater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
Resorted (UDgreater) vector v1 = ( 11 10 9 8 7 6 5 4 3 2 1 0 )
```

## <a name="sort_heap"></a>sort_heap

ヒープを並べ替えられた範囲に変換します。

```cpp
template<class RandomAccessIterator>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class RandomAccessIterator, class Compare>
void sort_heap(
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*最初*の\
ターゲット ヒープ内の最初の要素の位置を示すランダム アクセス反復子。

*最後*の\
ターゲット ヒープ内の最後の要素の 1 つ後ろの位置を示すランダム アクセス反復子。

*pred*\
1 つの要素が別の要素より小さいという意味を定義するユーザー定義の述語関数オブジェクト。 比較述語は2つの引数を受け取り、満たされた場合は**true**を返し、満たされていない場合は**false**を返します。

### <a name="remarks"></a>コメント

ヒープには次の 2 つのプロパティがあります。

- 最初の要素は常に最大です。

- 要素は体数時間で追加または削除できます。

このアルゴリズムの適用後、適用された範囲はヒープではなくなります。

これは、同等の要素の相対順序が保持されるとは限らないため、安定した並べ替えではありません。

ヒープは、優先順位キューを実装するのに最適な方法です。C++ 標準ライブラリ コンテナー アダプター [priority_queue Class](../standard-library/priority-queue-class.md) の実装に使用されます。

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

複雑さは最大 `N log N`であり、 *N* = *最後* - *最初*になります。

### <a name="example"></a>使用例

```cpp
// alg_sort_heap.cpp
// compile with: /EHsc
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>
#include <string>
#include <vector>
using namespace std;

void print(const string& s, const vector<int>& v)
{
    cout << s << ": ( ";

    for (auto i = v.begin(); i != v.end(); ++i)
    {
        cout << *i << " ";
    }

    cout << ")" << endl;
}

int main()
{
    vector<int> v;
    for (int i = 1; i <= 9; ++i)
    {
        v.push_back(i);
    }
    print("Initially", v);

    random_shuffle(v.begin(), v.end());
    print("After random_shuffle", v);

    make_heap(v.begin(), v.end());
    print("     After make_heap", v);

    sort_heap(v.begin(), v.end());
    print("     After sort_heap", v);

    random_shuffle(v.begin(), v.end());
    print("             After random_shuffle", v);

    make_heap(v.begin(), v.end(), greater<int>());
    print("After make_heap with greater<int>", v);

    sort_heap(v.begin(), v.end(), greater<int>());
    print("After sort_heap with greater<int>", v);
}
```

## <a name="stable_partition"></a>stable_partition

範囲内の要素を 2 つの分離されたセットに分類し、等価要素の相対順序は維持して、単項述語を満たす要素が単項述語を満たさない要素よりも前に来るように配置します。

```cpp
template<class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred );

template<class ExecutionPolicy, class BidirectionalIterator, class UnaryPredicate>
BidirectionalIterator stable_partition(
    ExecutionPolicy&& exec,
    BidirectionalIterator first,
    BidirectionalIterator last,
    UnaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
パーティション分割される範囲内の最初の要素の位置を示す双方向反復子。

*最後*の\
パーティション分割される範囲内の最後の要素の 1 つ後ろの位置を示す双方向反復子。

*pred*\
要素が分類される場合に満たされる条件を定義するユーザー定義の述語関数オブジェクト。 単項述語は1つの引数を受け取り、満たされた場合は**true**を返し、満たされていない場合は**false**を返します。

### <a name="return-value"></a>戻り値

述語条件を満たさない範囲内の最初の要素の位置を示す双方向反復子。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

要素*a*と*b*は同等ですが、必ずしも等しいとは限りません。両方の `pred( a, b )` が false で `pred( b, a )` が false である場合、 *pred*はパラメーター指定の述語です。 `stable_partition` アルゴリズムは安定しており、同等の要素の相対順序が保持されることを保証します。 アルゴリズム `partition` は、必ずしもこの順序を維持するわけではありません。

### <a name="example"></a>使用例

```cpp
// alg_stable_partition.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

bool greater5 ( int value )
{
    return value > 5;
}

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

    int i;
    for ( i = 0 ; i <= 10 ; i++ )
        v1.push_back( i );

    int ii;
    for ( ii = 0 ; ii <= 4 ; ii++ )
        v1.push_back( 5 );

    random_shuffle(v1.begin( ), v1.end( ) );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Partition the range with predicate greater10
    result = stable_partition (v1.begin( ), v1.end( ), greater5 );
    cout << "The partitioned set of elements in v1 is:\n ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "The first element in v1 to fail to satisfy the"
         << "\n predicate greater5 is: " << *result << "." << endl;
}
```

## <a name="stable_sort"></a>stable_sort

指定された範囲の要素を、降順以外の順序、または二項述語で指定された順序の基準に従って、等価要素の相対順序を維持して配置します。

```cpp
template<class BidirectionalIterator>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last );

template<class BidirectionalIterator, class Compare>
void stable_sort(
    BidirectionalIterator first,
    BidirectionalIterator last,
    Compare pred );

template<class ExecutionPolicy, class RandomAccessIterator>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last);

template<class ExecutionPolicy, class RandomAccessIterator, class Compare>
void stable_sort(
    ExecutionPolicy&& exec,
    RandomAccessIterator first,
    RandomAccessIterator last,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
並べ替えられる範囲内の最初の要素の位置を示す双方向反復子。

*最後*の\
並べ替えられる範囲内の最後の要素の 1 つ後ろの位置を示す双方向反復子。

*pred*\
順序内の次の要素によって満たされる比較条件を定義するユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

どちらの要素も他方より小さくない場合、要素は同等ですが、必ずしも等しいわけではありません。 `sort` アルゴリズムは安定しており、同等の要素の相対順序が保持されることを保証します。

`stable_sort` の実行時の複雑さは、使用可能なメモリの量によって異なりますが、最適なケース (十分なメモリ) が `O(N log N)`、最悪のケースは `O(N (log N)^2)`に*なります*。ここで、 *N* = *最後*に - します。 通常、`sort` アルゴリズムは `stable_sort`よりも大幅に高速です。

### <a name="example"></a>使用例

```cpp
// alg_stable_sort.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // For greater<int>( )
#include <iostream>

// Return whether first element is greater than the second
bool UDgreater (int elem1, int elem2 )
{
    return elem1 > elem2;
}

int main()
{
    using namespace std;
    vector<int> v1;
    vector<int>::iterator Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( 2 * i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    stable_sort(v1.begin( ), v1.end( ) );
    cout << "Sorted vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // To sort in descending order, specify binary predicate
    stable_sort(v1.begin( ), v1.end( ), greater<int>( ) );
    cout << "Resorted (greater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;

    // A user-defined (UD) binary predicate can also be used
    stable_sort(v1.begin( ), v1.end( ), UDgreater );
    cout << "Resorted (UDgreater) vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")" << endl;
}
```

```Output
Original vector v1 = ( 0 2 4 6 8 10 0 2 4 6 8 10 )
Sorted vector v1 = ( 0 0 2 2 4 4 6 6 8 8 10 10 )
Resorted (greater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
Resorted (UDgreater) vector v1 = ( 10 10 8 8 6 6 4 4 2 2 0 0 )
```

## <a name="swap"></a>フォト

最初のオーバーライドは 2 つのオブジェクトの値を交換します。 2 番目のオーバーライドは、オブジェクトの 2 つの配列間で値を交換します。

```cpp
template<class Type>
void swap(
    Type& left,
    Type& right);
template<class Type, size_t N>
void swap(
    Type (& left)[N],
    Type (& right)[N]);
```

### <a name="parameters"></a>パラメーター

*左*\
最初のオーバーライドでは、最初のオブジェクトがそのコンテンツを交換させます。 2 番目のオーバーライドでは、オブジェクトの最初の配列がそのコンテンツを交換させます。

*右*\
最初のオーバーライドでは、2 番目のオブジェクトがそのコンテンツを交換させます。 2 番目のオーバーライドでは、オブジェクトの 2 番目の配列がそのコンテンツを交換させます。

### <a name="remarks"></a>コメント

最初のオーバーロードは、個々のオブジェクトで動作するように設計されています。 2 番目のオーバー ロードは、2 つの配列間でオブジェクトのコンテンツをスワップします。

### <a name="example"></a>使用例

```cpp
// alg_swap.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2;
    vector<int>::iterator Iter1, Iter2, result;

    for ( int i = 0 ; i <= 10 ; i++ )
    {
        v1.push_back( i );
    }

    for ( int ii = 0 ; ii <= 4 ; ii++ )
    {
        v2.push_back( 5 );
    }

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    swap( v1, v2 );

    cout << "Vector v1 is ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    cout << "Vector v2 is ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
Vector v2 is ( 5 5 5 5 5 ).
Vector v1 is ( 5 5 5 5 5 ).
Vector v2 is ( 0 1 2 3 4 5 6 7 8 9 10 ).
```

## <a name="swap_ranges"></a>swap_ranges

1 つの範囲の要素を、同じサイズの別の範囲の要素と交換します。

```cpp
template<class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
   ForwardIterator1 first1,
   ForwardIterator1 last1,
   ForwardIterator2 first2 );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 swap_ranges(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
要素が交換される最初の範囲の最初の位置を指す前方反復子。

*last1*\
要素が交換される最初の範囲の最後の位置の 1 つ後ろを指す前方反復子。

*first2*\
要素が交換される 2 番目の範囲の最初の位置を指す前方反復子。

### <a name="return-value"></a>戻り値

要素が交換される 2 番目の範囲の最後の位置の 1 つ後ろを指す前方反復子。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。 2 番目の範囲は最初の範囲と同じ大きさにする必要があります。

複雑さは線形的で、 *last1* - *first1*のスワップが実行されます。 同じ種類のコンテナーから要素がスワップされる場合、そのコンテナーの `swap` メンバー関数を使用する必要があります。これは、メンバー関数には一般的に一定の複雑さがあるからです。

### <a name="example"></a>使用例

```cpp
// alg_swap_ranges.cpp
// compile with: /EHsc
#include <vector>
#include <deque>
#include <algorithm>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1;
    deque<int> d1;
    vector<int>::iterator v1Iter1;
    deque<int>::iterator d1Iter1;

    int i;
    for ( i = 0 ; i <= 5 ; i++ )
    {
        v1.push_back( i );
    }

    int ii;
    for ( ii =4 ; ii <= 9 ; ii++ )
    {
        d1.push_back( 6 );
    }

    cout << "Vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "Deque d1 is  ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;

    swap_ranges ( v1.begin( ), v1.end( ), d1.begin( ) );

    cout << "After the swap_range, vector v1 is ( " ;
    for ( v1Iter1 = v1.begin( ) ; v1Iter1 != v1.end( ) ;v1Iter1 ++ )
        cout << *v1Iter1 << " ";
    cout << ")." << endl;

    cout << "After the swap_range deque d1 is   ( " ;
    for ( d1Iter1 = d1.begin( ) ; d1Iter1 != d1.end( ) ;d1Iter1 ++ )
        cout << *d1Iter1 << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 0 1 2 3 4 5 ).
Deque d1 is  ( 6 6 6 6 6 6 ).
After the swap_range, vector v1 is ( 6 6 6 6 6 6 ).
After the swap_range deque d1 is   ( 0 1 2 3 4 5 ).
```

## <a name="transform"></a>変換

指定された関数オブジェクトをソース範囲内の各要素、または 2 つのソース範囲内の要素のペアに適用し、関数オブジェクトの戻り値をターゲット範囲にコピーします。

```cpp
template<class InputIterator, class OutputIterator, class UnaryFunction>
OutputIterator transform(
    InputIterator first1,
    InputIterator last1,
    OutputIterator result,
    UnaryFunction func );

template<class InputIterator1, class InputIterator2, class OutputIterator, class BinaryFunction>
OutputIterator transform(
    InputIterator1 first1,
    InputIterator1 last1,
    InputIterator2 first2,
    OutputIterator result,
    BinaryFunction func );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class UnaryOperation>
ForwardIterator2 transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    UnaryOperation op);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2, class ForwardIterator, class BinaryOperation>
ForwardIterator transform(
    ExecutionPolicy&& exec,
    ForwardIterator1 first1,
    ForwardIterator1 last1,
    ForwardIterator2 first2,
    ForwardIterator result,
    BinaryOperation binary_op);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*first1*\
操作する最初のソース範囲内の最初の要素の位置を示す入力反復子。

*last1*\
操作する最初のソース範囲内の最後の要素の 1 つ後ろの位置を示す入力反復子。

*first2*\
操作する 2 番目のソース範囲内の最初の要素の位置を示す入力反復子。

*結果*\
ターゲット範囲の最初の要素の位置を示す出力反復子。

*func*\
最初のソース範囲内の各要素に適用されるアルゴリズムの最初のバージョンで使用されるユーザー定義の単項関数オブジェクト、または順方向順序で 2 つのソース範囲内にペアで適用されるアルゴリズムの 2 番目のバージョンで使用されるユーザー定義 (UD) の二項関数オブジェクト。

### <a name="return-value"></a>戻り値

関数オブジェクトで変換された出力要素を受け取るターゲット範囲の最後の要素の 1 つ後ろの位置を示す出力反復子。

### <a name="remarks"></a>コメント

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつ各シーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。 変換先の範囲は、変換されたソース範囲を格納するのに十分な大きさである必要があります。

最初のバージョンのアルゴリズムで*result*が*first1*に設定されている場合、ソースとターゲットの範囲は同じになり、シーケンスはインプレースで変更されます。 ただし、*結果*は [`first1` + 1, `last1`) の範囲内の位置をアドレス指定できない場合があります。

複雑さは線形的で、最大で (`last1` - `first1`) の比較があります。

### <a name="example"></a>使用例

```cpp
// alg_transform.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>

// The function object multiplies an element by a Factor
template <class Type>
class MultValue
{
private:
    Type Factor;   // The value to multiply by
public:
    // Constructor initializes the value to multiply by
    MultValue ( const Type& value ) : Factor ( value ) { }

    // The function call for the element to be multiplied
    Type operator( ) ( Type& elem ) const
    {
        return elem * Factor;
    }
};

int main()
{
    using namespace std;
    vector<int> v1, v2 ( 7 ), v3 ( 7 );
    vector<int>::iterator Iter1, Iter2 , Iter3;

    // Constructing vector v1
    int i;
    for ( i = -4 ; i <= 2 ; i++ )
    {
        v1.push_back( i );
    }

    cout << "Original vector v1 = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Modifying the vector v1 in place
    transform (v1.begin( ), v1.end( ), v1.begin( ), MultValue<int> ( 2 ) );
    cout << "The elements of the vector v1 multiplied by 2 in place gives:"
            << "\n v1mod = ( " ;
    for ( Iter1 = v1.begin( ) ; Iter1 != v1.end( ) ; Iter1++ )
        cout << *Iter1 << " ";
    cout << ")." << endl;

    // Using transform to multiply each element by a factor of 5
    transform ( v1.begin( ), v1.end( ), v2.begin( ), MultValue<int> ( 5 ) );

    cout << "Multiplying the elements of the vector v1mod\n "
            << "by the factor 5 & copying to v2 gives:\n v2 = ( " ;
    for ( Iter2 = v2.begin( ) ; Iter2 != v2.end( ) ; Iter2++ )
        cout << *Iter2 << " ";
    cout << ")." << endl;

    // The second version of transform used to multiply the
    // elements of the vectors v1mod & v2 pairwise
    transform ( v1.begin( ), v1.end( ), v2.begin( ), v3.begin( ),
        multiplies<int>( ) );

    cout << "Multiplying elements of the vectors v1mod and v2 pairwise "
            << "gives:\n v3 = ( " ;
    for ( Iter3 = v3.begin( ) ; Iter3 != v3.end( ) ; Iter3++ )
        cout << *Iter3 << " ";
    cout << ")." << endl;
}
```

```Output
Original vector v1 = ( -4 -3 -2 -1 0 1 2 ).
The elements of the vector v1 multiplied by 2 in place gives:
v1mod = ( -8 -6 -4 -2 0 2 4 ).
Multiplying the elements of the vector v1mod
by the factor 5 & copying to v2 gives:
v2 = ( -40 -30 -20 -10 0 10 20 ).
Multiplying elements of the vectors v1mod and v2 pairwise gives:
v3 = ( 320 180 80 20 0 20 80 ).
```

## <a name="unique"></a>固有

指定された範囲内の互いに隣接する重複要素を削除します。

```cpp
template<class ForwardIterator>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last);

template<class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);

template<class ExecutionPolicy, class ForwardIterator>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last);

template<class ExecutionPolicy, class ForwardIterator, class BinaryPredicate>
ForwardIterator unique(
    ExecutionPolicy&& exec,
    ForwardIterator first,
    ForwardIterator last,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
重複削除のスキャン範囲内の先頭の要素の位置を示す前方反復子。

*最後*の\
重複削除のスキャン範囲内の最後の要素の 1 つ後ろの位置を示す前方反復子。

*pred*\
2 つの要素が等価であると見なされた場合に条件が満たされると定義する、ユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="return-value"></a>戻り値

連続する重複を含まない変更されたシーケンスの新しい末尾への前方反復子。削除されていない最後の要素の 1 つ後ろの位置を示します。

### <a name="remarks"></a>コメント

アルゴリズムの両方の形式により、連続した等値要素ペアの 2 番目の重複が削除されます。

アルゴリズムの動作は安定しているため、削除が取り消された要素の相対順序は変更されません。

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。 シーケンス内の要素の数は `unique` アルゴリズムによって変更されず、変更されたシーケンスの末尾を越えた要素はかつインクリメントされますが、指定されていません。

複雑さは線形的で、`(last - first) - 1` の比較が必要です。

リストは、パフォーマンスを向上させるより効率的なメンバー関数 "unique" を提供します。

連想コンテナーでは、これらのアルゴリズムを使用できません。

### <a name="example"></a>使用例

```cpp
// alg_unique.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 == elem2;
};

int main()
{
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2, v1_Iter3,
            v1_NewEnd1, v1_NewEnd2, v1_NewEnd3;

    int i;
    for ( i = 0 ; i <= 3 ; i++ )
    {
        v1.push_back( 5 );
        v1.push_back( -5 );
    }

    int ii;
    for ( ii = 0 ; ii <= 3 ; ii++ )
    {
        v1.push_back( 4 );
    }
    v1.push_back( 7 );

    cout << "Vector v1 is ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Remove consecutive duplicates
    v1_NewEnd1 = unique ( v1.begin( ), v1.end( ) );

    cout << "Removing adjacent duplicates from vector v1 gives\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Remove consecutive duplicates under the binary prediate mod_equals
    v1_NewEnd2 = unique ( v1.begin( ), v1_NewEnd1 , mod_equal );

    cout << "Removing adjacent duplicates from vector v1 under the\n "
            << " binary predicate mod_equal gives\n ( " ;
    for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
        cout << *v1_Iter2 << " ";
    cout << ")." << endl;

    // Remove elements if preceded by an element that was greater
    v1_NewEnd3 = unique ( v1.begin( ), v1_NewEnd2, greater<int>( ) );

    cout << "Removing adjacent elements satisfying the binary\n "
            << " predicate mod_equal from vector v1 gives ( " ;
    for ( v1_Iter3 = v1.begin( ) ; v1_Iter3 != v1_NewEnd3 ; v1_Iter3++ )
        cout << *v1_Iter3 << " ";
    cout << ")." << endl;
}
```

```Output
Vector v1 is ( 5 -5 5 -5 5 -5 5 -5 4 4 4 4 7 ).
Removing adjacent duplicates from vector v1 gives
( 5 -5 5 -5 5 -5 5 -5 4 7 ).
Removing adjacent duplicates from vector v1 under the
  binary predicate mod_equal gives
( 5 4 7 ).
Removing adjacent elements satisfying the binary
  predicate mod_equal from vector v1 gives ( 5 7 ).
```

## <a name="unique_copy"></a>unique_copy

互いに隣接する重複要素を除き、ソース範囲の要素をターゲット範囲にコピーします。

```cpp
template<class InputIterator, class OutputIterator>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result );

template<class InputIterator, class OutputIterator, class BinaryPredicate>
OutputIterator unique_copy(
    InputIterator first,
    InputIterator last,
    OutputIterator result,
    BinaryPredicate pred );

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2>
ForwardIterator2 unique_copy(
    ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result);

template<class ExecutionPolicy, class ForwardIterator1, class ForwardIterator2,
class BinaryPredicate>
ForwardIterator2 unique_copy(ExecutionPolicy&& exec,
    ForwardIterator1 first,
    ForwardIterator1 last,
    ForwardIterator2 result,
    BinaryPredicate pred);
```

### <a name="parameters"></a>パラメーター

*exec*\
使用する実行ポリシー。

*最初*の\
ソース範囲内のコピーする最初の要素の位置を示す前方反復子。

*最後*の\
ソース範囲内のコピーする最後の要素の 1 つ後ろの位置を示す前方反復子。

*結果*\
連続する重複が削除されたコピーを受け取るターゲット範囲の最初の要素の位置を示す出力反復子。

*pred*\
2 つの要素が等価であると見なされた場合に条件が満たされると定義する、ユーザー定義の述語関数オブジェクト。 二項述語は 2 つの引数を受け取り、条件が満たされている場合は **true** 、満たされていない場合は **false** を返します。

### <a name="return-value"></a>戻り値

連続する重複が削除されたコピーを受け取るターゲット範囲の最後の要素の 1 つ後ろの位置を示す出力反復子。

### <a name="remarks"></a>コメント

アルゴリズムの両方の形式により、連続した等値要素ペアの 2 番目の重複が削除されます。

アルゴリズムの動作は安定しているため、削除が取り消された要素の相対順序は変更されません。

参照されている範囲が有効であり、すべてのポインターが逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

複雑さは線形的で、(`last` - `first`) 比較が必要です。

### <a name="example"></a>使用例

```cpp
// alg_unique_copy.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>
#include <iostream>
#include <ostream>

using namespace std;

// Return whether modulus of elem1 is equal to modulus of elem2
bool mod_equal ( int elem1, int elem2 ) {
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 == elem2;
};

int main() {
    vector<int> v1;
    vector<int>::iterator v1_Iter1, v1_Iter2,
            v1_NewEnd1, v1_NewEnd2;

    int i;
    for ( i = 0 ; i <= 1 ; i++ ) {
        v1.push_back( 5 );
        v1.push_back( -5 );
    }

    int ii;
    for ( ii = 0 ; ii <= 2 ; ii++ )
        v1.push_back( 4 );
    v1.push_back( 7 );

    int iii;
    for ( iii = 0 ; iii <= 5 ; iii++ )
        v1.push_back( 10 );

    cout << "Vector v1 is\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1.end( ) ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    // Copy first half to second, removing consecutive duplicates
    v1_NewEnd1 = unique_copy ( v1.begin( ), v1.begin( ) + 8, v1.begin( ) + 8 );

    cout << "Copying the first half of the vector to the second half\n "
            << "while removing adjacent duplicates gives\n ( " ;
    for ( v1_Iter1 = v1.begin( ) ; v1_Iter1 != v1_NewEnd1 ; v1_Iter1++ )
        cout << *v1_Iter1 << " ";
    cout << ")." << endl;

    int iv;
    for ( iv = 0 ; iv <= 7 ; iv++ )
        v1.push_back( 10 );

    // Remove consecutive duplicates under the binary prediate mod_equals
    v1_NewEnd2 = unique_copy ( v1.begin( ), v1.begin( ) + 14,
        v1.begin( ) + 14 , mod_equal );

    cout << "Copying the first half of the vector to the second half\n "
            << " removing adjacent duplicates under mod_equals gives\n ( " ;
    for ( v1_Iter2 = v1.begin( ) ; v1_Iter2 != v1_NewEnd2 ; v1_Iter2++ )
        cout << *v1_Iter2 << " ";
    cout << ")." << endl;
}
```

## <a name="upper_bound"></a>upper_bound

順序の基準が二項述語で指定できる場合に、順序付けられた範囲内で、指定した値を超える値を持つ最初の要素の位置を検索します。

```cpp
template<class ForwardIterator, class Type>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value);

template<class ForwardIterator, class Type, class Compare>
ForwardIterator upper_bound(
    ForwardIterator first,
    ForwardIterator last,
    const Type& value,
    Compare pred);
```

### <a name="parameters"></a>パラメーター

*最初*の\
検索する要素範囲内の最初の要素の位置。

*最後*の\
検索する要素範囲内の最後の要素の 1 つ後ろの位置。

*value*\
返された反復子によってアドレス指定される要素の値が超える必要がある、順序付けられた範囲内の値。

*pred*\
1つの要素が別の要素より小さいという意味を定義するユーザー定義の比較述語関数オブジェクト。 比較述語は2つの引数を受け取り、満たされた場合は**true**を返し、満たされていない場合は**false**を返します。

### <a name="return-value"></a>戻り値

指定した値を超える値を持つ最初の要素の位置への前方反復子。

### <a name="remarks"></a>コメント

参照される並べ替えられたソースの範囲が有効であり、すべての反復子が逆参照可能であって、かつシーケンス内で先頭位置からのインクリメントにより最後の位置に到達可能である必要があります。

並べ替えられた範囲は、`upper_bound` を使用するための前提条件であり、順序の基準は比較述語によって指定されたものと同じです。

対象範囲は、`upper_bound` によって変更されません。

前方反復子の値の型は、小なり (less-than) 比較ができる必要があります。これにより、2 個の要素が与えられたときに、それらが等しいか (いずれも他方より小さくない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます

アルゴリズムの複雑さは、ランダムアクセス反復子では対数的であり、そうでない場合は (`last - first`) のステップ数に比例して線形的です。

### <a name="example"></a>使用例

```cpp
// alg_upper_bound.cpp
// compile with: /EHsc
#include <vector>
#include <algorithm>
#include <functional>      // greater<int>( )
#include <iostream>

// Return whether modulus of elem1 is less than modulus of elem2
bool mod_lesser( int elem1, int elem2 )
{
    if ( elem1 < 0 )
        elem1 = - elem1;
    if ( elem2 < 0 )
        elem2 = - elem2;
    return elem1 < elem2;
}

int main()
{
    using namespace std;

    vector<int> v1;
    // Constructing vector v1 with default less-than ordering
    for ( auto i = -1 ; i <= 4 ; ++i )
    {
        v1.push_back( i );
    }

    for ( auto ii =-3 ; ii <= 0 ; ++ii )
    {
        v1.push_back( ii );
    }

    cout << "Starting vector v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    sort(v1.begin(), v1.end());
    cout << "Original vector v1 with range sorted by the\n "
        << "binary predicate less than is v1 = ( " ;
    for (const auto &Iter : v1)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vector v2 with range sorted by greater
    vector<int> v2(v1);

    sort(v2.begin(), v2.end(), greater<int>());

    cout << "Original vector v2 with range sorted by the\n "
        << "binary predicate greater is v2 = ( " ;
    for (const auto &Iter : v2)
        cout << Iter << " ";
    cout << ")." << endl;

    // Constructing vectors v3 with range sorted by mod_lesser
    vector<int> v3(v1);
    sort(v3.begin(), v3.end(), mod_lesser);

    cout << "Original vector v3 with range sorted by the\n "
        << "binary predicate mod_lesser is v3 = ( " ;
    for (const auto &Iter : v3)
        cout << Iter << " ";
    cout << ")." << endl;

    // Demonstrate upper_bound

    vector<int>::iterator Result;

    // upper_bound of 3 in v1 with default binary predicate less<int>()
    Result = upper_bound(v1.begin(), v1.end(), 3);
    cout << "The upper_bound in v1 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v2 with the binary predicate greater<int>( )
    Result = upper_bound(v2.begin(), v2.end(), 3, greater<int>());
    cout << "The upper_bound in v2 for the element with a value of 3 is: "
        << *Result << "." << endl;

    // upper_bound of 3 in v3 with the binary predicate mod_lesser
    Result = upper_bound(v3.begin(), v3.end(), 3, mod_lesser);
    cout << "The upper_bound in v3 for the element with a value of 3 is: "
        << *Result << "." << endl;
}
```
