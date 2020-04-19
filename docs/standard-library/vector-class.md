---
title: vector クラス
description: クラス vector のC++ Microsoft 標準ライブラリ実装のリファレンスです。
ms.date: 02/07/2020
f1_keywords:
- vector/std::vector::allocator_type
- vector/std::vector::const_iterator
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::const_reverse_iterator
- vector/std::vector::difference_type
- vector/std::vector::iterator
- vector/std::vector::pointer
- vector/std::vector::reference
- vector/std::vector::reverse_iterator
- vector/std::vector::size_type
- vector/std::vector::value_type
- vector/std::vector::assign
- vector/std::vector::at
- vector/std::vector::back
- vector/std::vector::begin
- vector/std::vector::capacity
- vector/std::vector::cbegin
- vector/std::vector::cend
- vector/std::vector::crbegin
- vector/std::vector::crend
- vector/std::vector::clear
- vector/std::vector::data
- vector/std::vector::emplace
- vector/std::vector::emplace_back
- vector/std::vector::empty
- vector/std::vector::end
- vector/std::vector::erase
- vector/std::vector::front
- vector/std::vector::get_allocator
- vector/std::vector::insert
- vector/std::vector::max_size
- vector/std::vector::pop_back
- vector/std::vector::push_back
- vector/std::vector::rbegin
- vector/std::vector::rend
- vector/std::vector::reserve
- vector/std::vector::resize
- vector/std::vector::shrink_to_fit
- vector/std::vector::size
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], allocator_type
- std::vector [C++], const_iterator
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], const_reverse_iterator
- std::vector [C++], difference_type
- std::vector [C++], iterator
- std::vector [C++], pointer
- std::vector [C++], reference
- std::vector [C++], reverse_iterator
- std::vector [C++], size_type
- std::vector [C++], value_type
- std::vector [C++], assign
- std::vector [C++], at
- std::vector [C++], back
- std::vector [C++], begin
- std::vector [C++], capacity
- std::vector [C++], cbegin
- std::vector [C++], cend
- std::vector [C++], crbegin
- std::vector [C++], crend
- std::vector [C++], clear
- std::vector [C++], data
- std::vector [C++], emplace
- std::vector [C++], emplace_back
- std::vector [C++], empty
- std::vector [C++], end
- std::vector [C++], erase
- std::vector [C++], front
- std::vector [C++], get_allocator
- std::vector [C++], insert
- std::vector [C++], max_size
- std::vector [C++], pop_back
- std::vector [C++], push_back
- std::vector [C++], rbegin
- std::vector [C++], rend
- std::vector [C++], reserve
- std::vector [C++], resize
- std::vector [C++], shrink_to_fit
- std::vector [C++], size
- std::vector [C++], swap
ms.assetid: a3e0a8f8-7565-4fe0-93e4-e4d74ae1b70d
ms.openlocfilehash: ed987409dc99ea9b1dade632a5fa5deeb322347a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126228"
---
# <a name="vector-class"></a>vector クラス

標準C++ライブラリの vector クラスは、シーケンスコンテナーのクラステンプレートです。 ベクターは、指定された型の要素を線形の配置に格納し、任意の要素に対する高速なランダムアクセスを可能にします。 ベクターは、ランダムアクセスのパフォーマンスが premium である場合に、シーケンスに適したコンテナーです。

## <a name="syntax"></a>構文

```cpp
template <class Type, class Allocator = allocator<Type>>
class vector
```

### <a name="parameters"></a>パラメーター

*[種類]* \
ベクターに格納される要素のデータ型。

*アロケーター*\
メモリのベクターの割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクトを表す型。 この引数は省略可能であり、既定値は `allocator<Type>` です。

## <a name="remarks"></a>コメント

ベクターでは、シーケンスの末尾での挿入および削除に要する時間が一定です。 ベクターの途中での要素の挿入または削除には、線形時間を要します。 [Deque クラス](../standard-library/deque-class.md)コンテナーは、シーケンスの先頭と末尾での挿入および削除により高速になります。 [リストクラス](../standard-library/list-class.md)コンテナーは、シーケンス内の任意の場所で挿入と削除を高速に行うことができます。

ベクターの再割り当てが発生するのは、メンバー関数がベクター オブジェクトに含まれるシーケンスを現在の記憶域容量を超えて増やす必要がある場合です。 その他の挿入や消去により、シーケンス内のさまざまな記憶域のアドレスが変わることがあります。 そのような場合は常に、シーケンスのうち変更された部分を指す反復子または参照が無効になります。 再割り当てが発生しない場合は、挿入/削除が行われた地点より前の反復子および参照のみ有効のままになります。

[Vector\<bool > クラス](../standard-library/vector-bool-class.md)は、`bool`型の要素のクラステンプレートベクターを完全に特殊化したものです。 これには、特殊化によって使用される基になる型のアロケーターがあります。

[Vector\<bool > reference クラス](../standard-library/vector-bool-class.md#reference_class)は、オブジェクトが >\<ベクター内の要素 (単一ビット) への参照を提供できる入れ子になったクラスです。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[vector](#vector)|特定のサイズのベクター、特定の値の要素を持つベクター、特定の `allocator` を持つベクター、または他のベクターのコピーとして、ベクターを構築します。|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|vector オブジェクトの `allocator` クラスを表す型。|
|[const_iterator](#const_iterator)|ベクター内の **const** 要素を読み取ることができるランダム アクセス反復子を提供する型。|
|[const_pointer](#const_pointer)|ベクター内の **const** 要素へのポインターを提供する型。|
|[const_reference](#const_reference)|ベクターに格納されている**const**要素への参照を提供する型。 これは、 **const**操作の読み取りと実行に使用されます。|
|[const_reverse_iterator](#const_reverse_iterator)|ベクター内の任意の **const** 要素を読み取ることができるランダム アクセス反復子を提供する型。|
|[difference_type](#difference_type)|ベクターに含まれる 2 つの要素のアドレスの差を提供する型。|
|[Iterator](#iterator)|ベクター内の任意の要素を読み取り、または変更できるランダム アクセス反復子を提供する型。|
|[pointer](#pointer)|ベクター内の要素へのポインターを提供する型。|
|[reference](#reference)|ベクターに格納されている要素への参照を提供する型。|
|[reverse_iterator](#reverse_iterator)|反転ベクター内の要素を読み取り、または変更できるランダム アクセス反復子を提供する型。|
|[size_type](#size_type)|ベクター内の要素の数をカウントする型。|
|[value_type](#value_type)|ベクター内に格納されているデータ型を表す型。|

### <a name="functions"></a>関数

|||
|-|-|
|[assign](#assign)|ベクターを消去し、空のベクターに指定された要素をコピーします。|
|[at](#at)|ベクター内の指定位置にある要素への参照を返します。|
|[back](#back)|ベクターの最後の要素への参照を返します。|
|[begin](#begin)|ベクター内の最初の要素を示すランダム アクセス反復子を返します。|
|[容量](#capacity)|追加の記憶域を割り当てずにベクターに収容できる要素の数を返します。|
|[cbegin](#cbegin)|ベクター内の最初の要素を示すランダム アクセスの定数反復子を返します。|
|[cend](#cend)|ベクターの末尾の次の位置を指し示すランダム アクセス定数反復子を返します。|
|[crbegin](#crbegin)|反転ベクター内の最初の要素への定数反復子を返します。|
|[crend](#crend)|反転ベクター内の末尾の要素への定数反復子を返します。|
|[オフ](#clear)|ベクターの要素を消去します。|
|[data](#data)|ベクター内の最初の要素へのポインターを返します。|
|[emplace](#emplace)|その場で構築した要素をベクター内の指定位置に挿入します。|
|[emplace_back](#emplace_back)|その場で構築した要素をベクターの末尾に追加します。|
|[empty](#empty)|ベクター コンテナーが空かどうかをテストします。|
|[end](#end)|ベクターの末尾を指し示すランダム アクセス反復子を返します。|
|[erase](#erase)|指定した位置からベクター内の要素または要素範囲を削除します。|
|[front](#front)|ベクター内の最初の要素への参照を返します。|
|[get_allocator](#get_allocator)|ベクターが使用する `allocator` クラスにオブジェクトを返します。|
|[insert](#insert)|ベクター内の指定位置に 1 つまたは複数の要素を挿入します。|
|[max_size](#max_size)|ベクターの最大長を返します。|
|[pop_back](#pop_back)|ベクトルの末尾の要素を削除します。|
|[push_back](#push_back)|ベクターの末尾に要素を追加します。|
|[rbegin](#rbegin)|逆順のベクターの最初の要素への反復子を返します。|
|[rend](#rend)|反転ベクター内の末尾に反復子を返します。|
|[reserve](#reserve)|ベクター オブジェクトに最小の長さの記憶域を予約します。|
|[resize](#resize)|ベクターの新しいサイズを指定します。|
|[shrink_to_fit](#shrink_to_fit)|余分なキャパシティを破棄します。|
|[size](#size)|ベクター内の要素の数を返します。|
|[スワップ](#swap)|2 つのベクターの要素を交換します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator&#91;&#93;](#op_at)|指定した位置における vector 要素への参照を返します。|
|[operator=](#op_eq)|ベクターの要素を、別のベクターのコピーで置き換えます。|

## <a name="allocator_type"></a>allocator_type

ベクター オブジェクトのアロケーター クラスを表す型。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>コメント

`allocator_type` は、テンプレート パラメーター `Allocator` のシノニムです。

### <a name="example"></a>例

[get_allocator](#get_allocator) を使用する例については、`allocator_type` の例を参照してください。

## <a name="assign"></a>割り当てる

ベクターを消去し、空のベクターに指定された要素をコピーします。

```cpp
void assign(size_type count, const Type& value);
void assign(initializer_list<Type> init_list);

template <class InputIterator>
void assign(InputIterator first, InputIterator last);
```

### <a name="parameters"></a>パラメーター

*最初*の\
コピーする要素範囲内の最初の要素の位置。

*最後*の\
コピーする要素範囲を超える最初の要素の位置。

*カウント*\
ベクターに挿入される要素のコピーの数。

*value*\
ベクターに挿入される要素の値。

*init_list*\
挿入する要素を含む initializer_list。

### <a name="remarks"></a>コメント

まず、`assign` ベクター内の既存の要素を消去します。 次に、`assign` は、元のベクターから指定された要素の範囲をベクターに挿入するか、指定された新しい value 要素のコピーをベクターに挿入します。

### <a name="example"></a>例

```cpp
/ vector_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> v1, v2, v3;

    v1.push_back(10);
    v1.push_back(20);
    v1.push_back(30);
    v1.push_back(40);
    v1.push_back(50);

    cout << "v1 = ";
    for (auto& v : v1){
        cout << v << " ";
    }
    cout << endl;

    v2.assign(v1.begin(), v1.end());
    cout << "v2 = ";
    for (auto& v : v2){
        cout << v << " ";
    }
    cout << endl;

    v3.assign(7, 4);
    cout << "v3 = ";
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;

    v3.assign({ 5, 6, 7 });
    for (auto& v : v3){
        cout << v << " ";
    }
    cout << endl;
}
```

## <a name="at"></a>(

ベクター内の指定位置にある要素への参照を返します。

```cpp
reference at(size_type position);

const_reference at(size_type position) const;
```

### <a name="parameters"></a>パラメーター

*位置*の\
ベクター内で参照する要素を示す添字または位置の番号。

### <a name="return-value"></a>戻り値

引数に記述された要素への参照。 *Position*がベクターのサイズより大きい場合、`at` は例外をスローします。

### <a name="remarks"></a>コメント

`at` の戻り値が `const_reference`に割り当てられている場合、vector オブジェクトを変更することはできません。 `at` の戻り値が `reference` に割り当てられている場合、vector オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// vector_at.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const int &i = v1.at( 0 );
   int &j = v1.at( 1 );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="back"></a>戻る

ベクターの最後の要素への参照を返します。

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>戻り値

ベクターの最後の要素。 ベクターが空の場合、戻り値は未定義になります。

### <a name="remarks"></a>コメント

`back` の戻り値が `const_reference`に割り当てられている場合、vector オブジェクトを変更することはできません。 `back` の戻り値が `reference` に割り当てられている場合、vector オブジェクトを変更できます。

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) を 1 または 2 に定義してコンパイルすると、空のベクター内の要素にアクセスしようとした場合に実行時エラーが発生します。 詳細については、「チェックを行う[反復子](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// vector_back.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main() {
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.back( );
   const int& ii = v1.front( );

   cout << "The last integer of v1 is " << i << endl;
   i--;
   cout << "The next-to-last integer of v1 is "<< ii << endl;
}
```

## <a name="begin"></a>初め

ベクター内の最初の要素を示すランダム アクセス反復子を返します。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>戻り値

`vector` 内の最初の要素、または空の `vector` の次の位置を指すランダム アクセス反復子。 必ず[vector:: end](#end)と共に返される値を比較して、有効であることを確認します。

### <a name="remarks"></a>コメント

`begin` の戻り値が[vector:: const_iterator](#const_iterator)に割り当てられている場合、`vector` オブジェクトを変更することはできません。 `begin` の戻り値が [vector::iterator](#iterator) に割り当てられている場合、`vector` オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// vector_begin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::iterator c1_Iter;
    vector<int>::const_iterator c1_cIter;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_Iter = c1.begin();
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_Iter = c1.begin();
    *c1_Iter = 20;
    for (; c1_Iter != c1.end(); c1_Iter++)
    {
        cout << " " << *c1_Iter;
    }
    cout << endl;

    // The following line would be an error because iterator is const
    // *c1_cIter = 200;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="capacity"></a>capacity

追加の記憶域を割り当てずにベクターに収容できる要素の数を返します。

```cpp
size_type capacity() const;
```

### <a name="return-value"></a>戻り値

ベクターに割り当てられている記憶域の現在の長さ。

### <a name="remarks"></a>コメント

増加分を収容できる十分なメモリが割り当てられている場合は、メンバー関数 [resize](#resize) のほうが効率的に動作します。 割り当てられるメモリの量を指定するには、メンバー関数 [reserve](#reserve) を使用します。

### <a name="example"></a>例

```cpp
// vector_capacity.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 1 );
   cout << "The length of storage allocated is "
        << v1.capacity( ) << "." << endl;

   v1.push_back( 2 );
   cout << "The length of storage allocated is now "
        << v1.capacity( ) << "." << endl;
}
```

```Output
The length of storage allocated is 1.
The length of storage allocated is now 2.
```

## <a name="cbegin"></a>cbegin

範囲内の最初の要素を指す**定数**反復子を返します。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

範囲の最初の要素、または空の範囲の末尾の次の位置 (空の範囲の場合は `cbegin() == cend()`) を指す**const**ランダムアクセス反復子。

### <a name="remarks"></a>コメント

戻り値が `cbegin`の場合、範囲内の要素は変更できません。

`begin()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常は、次の例に示すように [auto](../cpp/auto-cpp.md) 型推論キーワードと共に使用します。 この例では、`begin()` と `cbegin()`をサポートする任意の種類の変更可能な (非**定数**) コンテナーとして `Container` を検討してください。

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

範囲内の最後の要素の次の位置を指す**定数**反復子を返します。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>戻り値

範囲の末尾の次の位置を指し示す**const**ランダムアクセス反復子。

### <a name="remarks"></a>コメント

`cend` は、反復子が範囲の末尾を超えたかどうかをテストするために使用されます。

`end()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常は、次の例に示すように [auto](../cpp/auto-cpp.md) 型推論キーワードと共に使用します。 この例では、`end()` と `cend()`をサポートする任意の種類の変更可能な (非**定数**) コンテナーとして `Container` を検討してください。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend` によって返された値を逆参照することはできません。 比較にのみ使用してください。

## <a name="clear"></a>クリア

ベクターの要素を消去します。

```cpp
void clear();
```

### <a name="example"></a>例

```cpp
// vector_clear.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "The size of v1 is " << v1.size( ) << endl;
   v1.clear( );
   cout << "The size of v1 after clearing is " << v1.size( ) << endl;
}
```

```Output
The size of v1 is 3
The size of v1 after clearing is 0
```

## <a name="const_iterator"></a>const_iterator

ベクター内の **const** 要素を読み取ることができるランダム アクセス反復子を提供する型。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>コメント

`const_iterator` 型を使用して要素の値を変更することはできません。

### <a name="example"></a>例

[ の使用例については、](#back)back`const_iterator` の例をご覧ください。

## <a name="const_pointer"></a>const_pointer

ベクター内の **const** 要素へのポインターを提供する型。

```cpp
typedef typename Allocator::const_pointer const_pointer;
```

### <a name="remarks"></a>コメント

`const_pointer` 型を使用して要素の値を変更することはできません。

ベクター要素にアクセスするために、より一般的に使用されるのは[反復子](#iterator)です。

## <a name="const_reference"></a>const_reference

ベクターに格納されている**const**要素への参照を提供する型。 これは、 **const**操作の読み取りと実行に使用されます。

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>コメント

`const_reference` 型を使用して要素の値を変更することはできません。

### <a name="example"></a>例

```cpp
// vector_const_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   const vector <int> v2 = v1;
   const int &i = v2.front( );
   const int &j = v2.back( );
   cout << "The first element is " << i << endl;
   cout << "The second element is " << j << endl;

   // The following line would cause an error as v2 is const
   // v2.push_back( 30 );
}
```

```Output
The first element is 10
The second element is 20
```

## <a name="const_reverse_iterator"></a>const_reverse_iterator

ベクター内の任意の **const** 要素を読み取ることができるランダム アクセス反復子を提供する型。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>コメント

型 `const_reverse_iterator` は要素の値を変更できず、逆にベクターを反復処理するために使用されます。

### <a name="example"></a>例

反復子を宣言して使用する方法の例については、[rbegin](#rbegin) をご覧ください。

## <a name="crbegin"></a>crbegin

反転ベクター内の最初の要素への定数反復子を返します。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>戻り値

反転された[ベクター](../standard-library/vector-class.md)の最初の要素を指すか、反転されていない `vector` の最後の要素だったものを指す、定数逆順ランダム アクセス反復子。

### <a name="remarks"></a>コメント

戻り値が `crbegin`の場合、`vector` オブジェクトを変更することはできません。

### <a name="example"></a>例

```cpp
// vector_crbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.crbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="crend"></a>crend

反転されたベクター内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>戻り値

逆順の[ベクター](../standard-library/vector-class.md)内の最後の要素の次の位置 (通常の順序の `vector` 内の最初の要素の前の位置) を指す定数逆順ランダム アクセス反復子。

### <a name="remarks"></a>コメント

`crend` は、`vector`vector::cend[ が ](#cend) で使用されるときと同様の方法により、逆順の `vector` で使用されます。

戻り値が `crend` (適切にデクリメントされます) の場合、`vector` オブジェクトを変更することはできません。

`crend` を使用して、逆順反復子が `vector` の末尾に達したかどうかをテストできます。

`crend` によって返された値を逆参照することはできません。 比較にのみ使用してください。

### <a name="example"></a>例

```cpp
// vector_crend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::const_reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="data"></a>データ

ベクター内の最初の要素へのポインターを返します。

```cpp
const_pointer data() const;

pointer data();
```

### <a name="return-value"></a>戻り値

[ベクター](../standard-library/vector-class.md)内の最初の要素へのポインター、または空の `vector` の次の位置を指すポインター。

### <a name="example"></a>例

```cpp
// vector_data.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector<int> c1;
    vector<int>::pointer c1_ptr;
    vector<int>::const_pointer c1_cPtr;

    c1.push_back(1);
    c1.push_back(2);

    cout << "The vector c1 contains elements:";
    c1_cPtr = c1.data();
    for (size_t n = c1.size(); 0 < n; --n, c1_cPtr++)
    {
        cout << " " << *c1_cPtr;
    }
    cout << endl;

    cout << "The vector c1 now contains elements:";
    c1_ptr = c1.data();
    *c1_ptr = 20;
    for (size_t n = c1.size(); 0 < n; --n, c1_ptr++)
    {
        cout << " " << *c1_ptr;
    }
    cout << endl;
}
```

```Output
The vector c1 contains elements: 1 2
The vector c1 now contains elements: 20 2
```

## <a name="difference_type"></a>difference_type

同じベクター内の要素を参照する 2 つの反復子の違いを提供する型。

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>コメント

要素へのポインターにはそのアドレスが含まれるため、`difference_type` は 2 つのポインター間の要素の数と言うこともできます。

ベクター要素にアクセスするために、より一般的に使用されるのは[反復子](#iterator)です。

### <a name="example"></a>例

```cpp
// vector_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <vector>
#include <algorithm>

int main( )
{
   using namespace std;

   vector <int> c1;
   vector <int>::iterator c1_Iter, c2_Iter;

   c1.push_back( 30 );
   c1.push_back( 20 );
   c1.push_back( 30 );
   c1.push_back( 10 );
   c1.push_back( 30 );
   c1.push_back( 20 );

   c1_Iter = c1.begin( );
   c2_Iter = c1.end( );

   vector <int>::difference_type   df_typ1, df_typ2, df_typ3;

   df_typ1 = count( c1_Iter, c2_Iter, 10 );
   df_typ2 = count( c1_Iter, c2_Iter, 20 );
   df_typ3 = count( c1_Iter, c2_Iter, 30 );
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";
}
```

```Output
The number '10' is in c1 collection 1 times.
The number '20' is in c1 collection 2 times.
The number '30' is in c1 collection 3 times.
```

## <a name="emplace"></a>emplace

その場で構築した要素をベクター内の指定位置に挿入します。

```cpp
template <class... Types>
iterator emplace(
    const_iterator position,
    Types&&... args);
```

### <a name="parameters"></a>パラメーター

*位置*の\
最初の要素を挿入する[ベクター](../standard-library/vector-class.md)内の位置。

*args*\
コンストラクター引数。 この関数は、提供された引数に基づいてコンストラクターのどのオーバーロードを呼び出すかを推測します。

### <a name="return-value"></a>戻り値

この関数は、新しい要素が `vector` 内に挿入された位置を指す反復子を返します。

### <a name="remarks"></a>コメント

挿入操作には負荷がかかる可能性があります。 `vector` のパフォーマンスの詳細については、 [vector クラス](../standard-library/vector-class.md)を参照してください。

### <a name="example"></a>例

```cpp
// vector_emplace.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.emplace( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
vv1[0] = 10 20 30
```

## <a name="emplace_back"></a>emplace_back

その場で構築した要素をベクターの末尾に追加します。

```cpp
template <class... Types>
void emplace_back(Types&&... args);
```

### <a name="parameters"></a>パラメーター

*args*\
コンストラクター引数。 この関数は、提供された引数に基づいてコンストラクターのどのオーバーロードを呼び出すかを推測します。

### <a name="example"></a>例

```cpp
#include <vector>
struct obj
{
   obj(int, double) {}
};

int main()
{
   std::vector<obj> v;
   v.emplace_back(1, 3.14); // obj in created in place in the vector
}
```

## <a name="empty"></a>指定

ベクターが空かどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

ベクターが空の場合は**true** 。ベクターが空でない場合は**false** 。

### <a name="example"></a>例

```cpp
// vector_empty.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );

   if ( v1.empty( ) )
      cout << "The vector is empty." << endl;
   else
      cout << "The vector is not empty." << endl;
}
```

```Output
The vector is not empty.
```

## <a name="end"></a>終わり

末尾超え反復子を返します。

```cpp
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>戻り値

ベクターの末尾超え反復子。 ベクターが空の場合は、`vector::end() == vector::begin()`ます。

### <a name="remarks"></a>コメント

`end` の戻り値が `const_iterator`型の変数に割り当てられている場合、vector オブジェクトを変更することはできません。 `end` の戻り値が `iterator`型の変数に割り当てられている場合、vector オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// vector_end.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_Iter = v1.begin( ) ; v1_Iter != v1.end( ) ; v1_Iter++ )
      cout << *v1_Iter << endl;
}
```

```Output
1
2
```

## <a name="erase"></a>消去

指定した位置からベクター内の要素または要素範囲を削除します。

```cpp
iterator erase(
    const_iterator position);

iterator erase(
    const_iterator first,
    const_iterator last);
```

### <a name="parameters"></a>パラメーター

*位置*の\
ベクターから削除する要素の位置。

*最初*の\
ベクターから削除する最初の要素の位置。

*最後*の\
ベクターから削除する最後の要素の次の位置。

### <a name="return-value"></a>戻り値

削除した要素の後に残る最初の要素を指定する反復子。このような要素が存在しない場合は、ベクターの末尾へのポインター。

### <a name="example"></a>例

```cpp
// vector_erase.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );
   v1.push_back( 40 );
   v1.push_back( 50 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.erase( v1.begin( ) + 1, v1.begin( ) + 3 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
}
```

```Output
v1 = 10 20 30 40 50
v1 = 20 30 40 50
v1 = 20 50
```

## <a name="front"></a>外側

ベクター内の最初の要素への参照を返します。

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>戻り値

ベクター オブジェクト内の最初の要素への参照。 ベクターが空の場合、戻り値は未定義になります。

### <a name="remarks"></a>コメント

`front` の戻り値が `const_reference`に割り当てられている場合、vector オブジェクトを変更することはできません。 `front` の戻り値が **reference** に割り当てられている場合、vector オブジェクトを変更できます。

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) を 1 または 2 に定義してコンパイルすると、空のベクター内の要素にアクセスしようとした場合に実行時エラーが発生します。 詳細については、「チェックを行う[反復子](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// vector_front.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 11 );

   int& i = v1.front( );
   const int& ii = v1.front( );

   cout << "The first integer of v1 is "<< i << endl;
   // by incrementing i, we move the front reference to the second element
   i++;
   cout << "Now, the first integer of v1 is "<< i << endl;
}
```

## <a name="get_allocator"></a>get_allocator

ベクターの構築に使用されるアロケーター オブジェクトのコピーを返します。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>戻り値

ベクターで使用されるアロケーター。

### <a name="remarks"></a>コメント

vector クラスのアロケーターは、クラスがどのようにストレージを管理するかを指定します。 C++ 標準ライブラリ コンテナー クラスで提供される既定のアロケーターは、ほとんどのプログラミング要件に対応しています。 独自のアロケータークラスを作成して使用するC++ことは、高度な機能です。

### <a name="example"></a>例

```cpp
// vector_get_allocator.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   // The following lines declare objects that use the default allocator.
   vector<int> v1;
   vector<int, allocator<int> > v2 = vector<int, allocator<int> >(allocator<int>( )) ;

   // v3 will use the same allocator class as v1
   vector <int> v3( v1.get_allocator( ) );

   vector<int>::allocator_type xvec = v3.get_allocator( );
   // You can now call functions on the allocator class used by vec
}
```

## <a name="insert"></a>insert

ベクター内の指定した位置に要素、複数の要素、または要素の範囲を挿入します。

```cpp
iterator insert(
    const_iterator position,
    const Type& value);

iterator insert(
    const_iterator position,
    Type&& value);

void insert(
    const_iterator position,
    size_type count,
    const Type& value);

template <class InputIterator>
void insert(
    const_iterator position,
    InputIterator first,
    InputIterator last);
```

### <a name="parameters"></a>パラメーター

*位置*の\
最初の要素を挿入するベクター内の位置。

*value*\
ベクターに挿入される要素の値。

*カウント*\
ベクターに挿入する要素の数。

*最初*の\
コピーする要素範囲内の最初の要素の位置。

*最後*の\
コピーする要素範囲を超える最初の要素の位置。

### <a name="return-value"></a>戻り値

最初の 2 つの `insert` 関数は、新しい要素がベクターに挿入された位置を指す反復子を返します。

### <a name="remarks"></a>コメント

事前条件として、*最初*と*最後*はベクターに反復子を指定することはできません。また、動作は定義されていません。 挿入操作には負荷がかかる可能性があります。 `vector` のパフォーマンスの詳細については、 [vector クラス](../standard-library/vector-class.md)を参照してください。

### <a name="example"></a>例

```cpp
// vector_insert.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator Iter;

   v1.push_back( 10 );
   v1.push_back( 20 );
   v1.push_back( 30 );

   cout << "v1 =" ;
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   v1.insert( v1.begin( ) + 1, 40 );
   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;
   v1.insert( v1.begin( ) + 2, 4, 50 );

   cout << "v1 =";
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )
      cout << " " << *Iter;
   cout << endl;

   const auto v2 = v1;
   v1.insert( v1.begin( )+1, v2.begin( )+2, v2.begin( )+4 );
   cout << "v1 =";
   for (Iter = v1.begin( ); Iter != v1.end( ); Iter++ )
      cout << " " << *Iter;
   cout << endl;

// initialize a vector of vectors by moving v1
   vector < vector <int> > vv1;

   vv1.insert( vv1.begin(), move( v1 ) );
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )
      {
      cout << "vv1[0] =";
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )
         cout << " " << *Iter;
      cout << endl;
      }
}
```

```Output
v1 = 10 20 30
v1 = 10 40 20 30
v1 = 10 40 50 50 50 50 20 30
v1 = 10 50 50 40 50 50 50 50 20 30
vv1[0] = 10 50 50 40 50 50 50 50 20 30
```

## <a name="iterator"></a>反

ベクター内の任意の要素を読み取り、または変更できるランダム アクセス反復子を提供する型。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>コメント

**iterator** 型を使って要素の値を変更することができます。

### <a name="example"></a>例

[begin](#begin) の例を参照してください。

## <a name="max_size"></a>max_size

ベクターの最大長を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

ベクターの可能な最大長。

### <a name="example"></a>例

```cpp
// vector_max_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   i = v1.max_size( );
   cout << "The maximum possible length of the vector is " << i << "." << endl;
}
```

## <a name="op_at"></a>演算子 []

指定した位置における vector 要素への参照を返します。

```cpp
reference operator[](size_type position);

const_reference operator[](size_type position) const;
```

### <a name="parameters"></a>パラメーター

*位置*の\
vector 要素の位置。

### <a name="return-value"></a>戻り値

指定された位置がコンテナーのサイズ以上の場合、結果は未定義になります。

### <a name="remarks"></a>コメント

`operator[]` の戻り値が `const_reference`に割り当てられている場合、vector オブジェクトを変更することはできません。 `operator[]` の戻り値が参照に割り当てられている場合、vector オブジェクトを変更できます。

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) を 1 または 2 に定義してコンパイルすると、ベクターの境界外の要素にアクセスしようとした場合に実行時エラーが発生します。 詳細については、「チェックを行う[反復子](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// vector_op_ref.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;

   v1.push_back( 10 );
   v1.push_back( 20 );

   int& i = v1[1];
   cout << "The second integer of v1 is " << i << endl;
}
```

## <a name="op_eq"></a>operator =

ベクターの要素を、別のベクターのコピーで置き換えます。

```cpp
vector& operator=(const vector& right);

vector& operator=(vector&& right);
```

### <a name="parameters"></a>パラメーター

*右*\
[ 内にコピーされる ](../standard-library/vector-class.md)vector`vector`。

### <a name="remarks"></a>コメント

`vector`内の既存の要素を消去した後、 *`operator=` の内容*を `vector`にコピーまたは移動します。

### <a name="example"></a>例

```cpp
// vector_operator_as.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int> v1, v2, v3;
   vector<int>::iterator iter;

   v1.push_back(10);
   v1.push_back(20);
   v1.push_back(30);
   v1.push_back(40);
   v1.push_back(50);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << *iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << *iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>pointer

ベクター内の要素へのポインターを提供する型。

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>コメント

**pointer** 型を使って要素の値を変更することができます。

### <a name="example"></a>例

```cpp
// vector_pointer.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
    using namespace std;
    vector<int> v;
    v.push_back( 11 );
    v.push_back( 22 );

    vector<int>::pointer ptr = &v[0];
    cout << *ptr << endl;
    ptr++;
    cout << *ptr << endl;
    *ptr = 44;
    cout << *ptr << endl;
}
```

```Output
11
22
44
```

## <a name="pop_back"></a>pop_back

ベクトルの末尾の要素を削除します。

```cpp
void pop_back();
```

### <a name="remarks"></a>コメント

コード例については、「[vector::push_back()](#push_back)」をご覧ください。

## <a name="push_back"></a>push_back

ベクトルの末尾に要素を追加します。

```cpp
void push_back(const T& value);

void push_back(T&& value);
```

### <a name="parameters"></a>パラメーター

*value*\
ベクトルの末尾に追加する要素に割り当てる値。

### <a name="example"></a>例

```cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << "  " << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

int main()
{
    vector<int> v;
    for (int i = 0; i < 10; ++i) {
        v.push_back(10 + i);
    }

    cout << "vector data: " << endl;
    print_collection(v);

    // pop_back() until it's empty, printing the last element as we go
    while (v.begin() != v.end()) {
        cout << "v.back(): "; print_elem(v.back()); cout << endl;
        v.pop_back();
    }
}
```

## <a name="rbegin"></a>rbegin

逆順のベクターの最初の要素への反復子を返します。

```cpp
reverse_iterator rbegin();
const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>戻り値

反転されたベクターの最初の要素を指すか、反転されていないベクターの最後の要素だったものを指す、逆順ランダム アクセス反復子。

### <a name="remarks"></a>コメント

`rbegin` の戻り値が `const_reverse_iterator`に割り当てられている場合、vector オブジェクトを変更することはできません。 `rbegin` の戻り値が `reverse_iterator` に割り当てられている場合、vector オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// vector_rbegin.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::iterator v1_Iter;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   v1_Iter = v1.begin( );
   cout << "The first element of vector is "
        << *v1_Iter << "." << endl;

   v1_rIter = v1.rbegin( );
   cout << "The first element of the reversed vector is "
        << *v1_rIter << "." << endl;
}
```

```Output
The first element of vector is 1.
The first element of the reversed vector is 2.
```

## <a name="reference"></a>「

ベクターに格納されている要素への参照を提供する型。

```cpp
typedef typename Allocator::reference reference;
```

### <a name="example"></a>例

vector クラスで [reference](#at) を使用する方法の例については、**at** をご覧ください。

## <a name="rend"></a>rend

反転されたベクター内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_reverse_iterator rend() const;
reverse_iterator rend();
```

### <a name="return-value"></a>戻り値

逆順のベクター内の最後の要素の次の位置 (通常の順序のベクター内の最初の要素の前の位置) を指す逆順ランダム アクセス反復子。

### <a name="remarks"></a>コメント

`rend` は、ベクターで [end](#end) を使用するのと同様に、逆順のベクターで使用します。

`rend` の戻り値が `const_reverse_iterator`に割り当てられている場合、vector オブジェクトを変更することはできません。 `rend` の戻り値が `reverse_iterator` に割り当てられている場合、vector オブジェクトを変更できます。

`rend` を使用して、逆順反復子がベクターの末尾に達したかどうかをテストできます。

`rend` によって返された値を逆参照することはできません。 比較にのみ使用してください。

### <a name="example"></a>例

```cpp
// vector_rend.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::reverse_iterator v1_rIter;

   v1.push_back( 1 );
   v1.push_back( 2 );

   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )
      cout << *v1_rIter << endl;
}
```

```Output
2
1
```

## <a name="reserve"></a>省

ベクター オブジェクトの記憶域の最小長を予約します。必要であれば、領域を割り当てます。

```cpp
void reserve(size_type count);
```

### <a name="parameters"></a>パラメーター

*カウント*\
ベクターに割り当てる記憶域の最小長。

### <a name="example"></a>例

```cpp
// vector_reserve.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
```

## <a name="resize"></a>サイズ

ベクターの新しいサイズを指定します。

```cpp
void resize(size_type new_size);
void resize(size_type new_size, Type value);
```

### <a name="parameters"></a>パラメーター

*new_size*\
ベクターの新しいサイズ。

*value*\
新しいサイズが元のサイズよりも大きい場合に、ベクターに追加される新しい要素の初期化値。 この値を省略した場合、新しいオブジェクトは既定のコンストラクターを使用します。

### <a name="remarks"></a>コメント

コンテナーのサイズが要求*new_size*されたサイズより小さい場合、`resize` は、要求されたサイズに達するまで要素をベクターに追加します。 コンテナーのサイズが要求されたサイズよりも大きい場合、`resize` は*new_size*サイズに達するまで、コンテナーの末尾に最も近い要素を削除します。 コンテナーの現在のサイズが要求されたサイズと同じ場合、アクションは実行されません。

[size](#size) はベクターの現在のサイズを反映します。

### <a name="example"></a>例

```cpp
// vectorsizing.cpp
// compile with: /EHsc /W4
// Illustrates vector::reserve, vector::max_size,
// vector::resize, vector::resize, and vector::capacity.
//
// Functions:
//
//    vector::max_size - Returns maximum number of elements vector could
//                       hold.
//
//    vector::capacity - Returns number of elements for which memory has
//                       been allocated.
//
//    vector::size - Returns number of elements in the vector.
//
//    vector::resize - Reallocates memory for vector, preserves its
//                     contents if new size is larger than existing size.
//
//    vector::reserve - Allocates elements for vector to ensure a minimum
//                      size, preserving its contents if the new size is
//                      larger than existing size.
//
//    vector::push_back - Appends (inserts) an element to the end of a
//                        vector, allocating memory for it if necessary.
//
//////////////////////////////////////////////////////////////////////

// The debugger cannot handle symbols more than 255 characters long.
// The C++ Standard Library often creates symbols longer than that.
// The warning can be disabled:
//#pragma warning(disable:4786)

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

void printvstats(const vector<int>& v) {
    cout << "   the vector's size is: " << v.size() << endl;
    cout << "   the vector's capacity is: " << v.capacity() << endl;
    cout << "   the vector's maximum size is: " << v.max_size() << endl;
}

int main()
{
    // declare a vector that begins with 0 elements.
    vector<int> v;

    // Show statistics about vector.
    cout << endl << "After declaring an empty vector:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Add one element to the end of the vector.
    v.push_back(-1);
    cout << endl << "After adding an element:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    for (int i = 1; i < 10; ++i) {
        v.push_back(i);
    }
    cout << endl << "After adding 10 elements:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(6);
    cout << endl << "After resizing to 6 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(9, 999);
    cout << endl << "After resizing to 9 elements with an initialization value of 999:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    v.resize(12);
    cout << endl << "After resizing to 12 elements without an initialization value:" << endl;
    printvstats(v);
    print("   the vector's contents: ", v);

    // Ensure there's room for at least 1000 elements.
    v.reserve(1000);
    cout << endl << "After vector::reserve(1000):" << endl;
    printvstats(v);

    // Ensure there's room for at least 2000 elements.
    v.resize(2000);
    cout << endl << "After vector::resize(2000):" << endl;
    printvstats(v);
}
```

## <a name="reverse_iterator"></a>reverse_iterator

反転ベクター内の要素を読み取り、または変更できるランダム アクセス反復子を提供する型。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>コメント

型 `reverse_iterator` は、逆の順序でベクターを反復処理するために使用します。

### <a name="example"></a>例

[rbegin](#rbegin) の例をご覧ください。

## <a name="shrink_to_fit"></a>shrink_to_fit

余分なキャパシティを破棄します。

```cpp
void shrink_to_fit();
```

### <a name="example"></a>例

```cpp
// vector_shrink_to_fit.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   //vector <int>::iterator Iter;

   v1.push_back( 1 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.reserve( 20 );
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
   v1.shrink_to_fit();
   cout << "Current capacity of v1 = "
      << v1.capacity( ) << endl;
}
```

```Output
Current capacity of v1 = 1
Current capacity of v1 = 20
Current capacity of v1 = 1
```

## <a name="size"></a>幅

ベクター内の要素の数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

ベクターの現在の長さ。

### <a name="example"></a>例

```cpp
// vector_size.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1;
   vector <int>::size_type i;

   v1.push_back( 1 );
   i = v1.size( );
   cout << "Vector length is " << i << "." << endl;

   v1.push_back( 2 );
   i = v1.size( );
   cout << "Vector length is now " << i << "." << endl;
}
```

```Output
Vector length is 1.
Vector length is now 2.
```

## <a name="size_type"></a>size_type

ベクター内の要素の数をカウントする型。

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="example"></a>例

[capacity](#capacity) の例をご覧ください。

## <a name="swap"></a>フォト

2 つのベクターの要素を交換します。

```cpp
void swap(
    vector<Type, Allocator>& right);

friend void swap(
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*右*\
交換する要素を提供するベクター。 または、ベクター内の要素と交換される要素を持つ*ベクター。*

*左*\
ベクター*右*の要素と交換される要素を持つベクター。

### <a name="example"></a>例

```cpp
// vector_swap.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector <int> v1, v2;

   v1.push_back( 1 );
   v1.push_back( 2 );
   v1.push_back( 3 );

   v2.push_back( 10 );
   v2.push_back( 20 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
   cout << endl;

   v1.swap( v2 );

   cout << "The number of elements in v1 = " << v1.size( ) << endl;
   cout << "The number of elements in v2 = " << v2.size( ) << endl;
}
```

```Output
The number of elements in v1 = 3
The number of elements in v2 = 2

The number of elements in v1 = 2
The number of elements in v2 = 3
```

## <a name="value_type"></a>value_type

ベクター内に格納されているデータ型を表す型。

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>コメント

`value_type` は、テンプレート パラメーター `Type` のシノニムです。

### <a name="example"></a>例

```cpp
// vector_value_type.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main( )
{
   using namespace std;
   vector<int>::value_type AnInt;
   AnInt = 44;
   cout << AnInt << endl;
}
```

```Output
44
```

## <a name="vector"></a>ベクトル

ベクターを構築します。 オーバーロードは、特定のサイズのベクター、または特定の値の要素を使用してベクターを構築します。 または、他のベクターの全体または一部のコピーとして。 オーバーロードによっては、使用するアロケーターを指定することもできます。

```cpp
vector();
explicit vector(const Allocator& allocator);
explicit vector(size_type count);
vector(size_type count, const Type& value);
vector(size_type count, const Type& value, const Allocator& allocator);

vector(const vector& source);
vector(vector&& source);
vector(initializer_list<Type> init_list, const Allocator& allocator);

template <class InputIterator>
vector(InputIterator first, InputIterator last);
template <class InputIterator>
vector(InputIterator first, InputIterator last, const Allocator& allocator);
```

### <a name="parameters"></a>パラメーター

*アロケーター*\
このオブジェクトに対して使用するアロケーター クラス。 [get_allocator](#get_allocator) は、オブジェクトのアロケーター クラスを返します。

*カウント*\
構築されたベクター内の要素の数。

*value*\
構築されたベクターの要素の値。

*ソース*\
構築されたベクターがコピーになる元のベクター。

*最初*の\
コピーする要素範囲内の最初の要素の位置。

*最後*の\
コピーする要素範囲を超える最初の要素の位置。

*init_list*\
コピーする要素を格納している `initializer_list`。

### <a name="remarks"></a>コメント

すべてのコンストラクターは、アロケーターオブジェクト (*アロケーター*) を格納し、ベクターを初期化します。

最初の 2 つのコンストラクターは、空の初期ベクターを指定します。 2番目のコンストラクターは、使用するアロケーターの型 (*アロケーター*) を明示的に指定します。

3番目のコンストラクターは、クラス `Type`の既定値の要素の指定された*数 (数*) の繰り返しを指定します。

4番目と5番目のコンストラクターは、値*値*の (*count*) 要素の繰り返しを指定します。

6番目のコンストラクターは、ベクター*ソース*のコピーを指定します。

7番目のコンストラクターは、ベクター*ソース*を移動します。

8 番目のコンストラクターは、initializer_list を使用して要素を指定します。

9 番目と 10 番目のコンストラクターは、ベクターの範囲 (`first`、`last`) をコピーします。

### <a name="example"></a>例

```cpp
// vector_ctor.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    vector <int>::iterator v1_Iter, v2_Iter, v3_Iter, v4_Iter, v5_Iter, v6_Iter;

    // Create an empty vector v0
    vector <int> v0;

    // Create a vector v1 with 3 elements of default value 0
    vector <int> v1(3);

    // Create a vector v2 with 5 elements of value 2
    vector <int> v2(5, 2);

    // Create a vector v3 with 3 elements of value 1 and with the allocator
    // of vector v2
    vector <int> v3(3, 1, v2.get_allocator());

    // Create a copy, vector v4, of vector v2
    vector <int> v4(v2);

    // Create a new temporary vector for demonstrating copying ranges
    vector <int> v5(5);
    for (auto i : v5) {
        v5[i] = i;
    }

    // Create a vector v6 by copying the range v5[ first,  last)
    vector <int> v6(v5.begin() + 1, v5.begin() + 3);

    cout << "v1 =";
    for (auto& v : v1){
        cout << " " << v;
    }
    cout << endl;

    cout << "v2 =";
    for (auto& v : v2){
        cout << " " << v;
    }
    cout << endl;

    cout << "v3 =";
    for (auto& v : v3){
        cout << " " << v;
    }
    cout << endl;
    cout << "v4 =";
    for (auto& v : v4){
        cout << " " << v;
    }
    cout << endl;

    cout << "v5 =";
    for (auto& v : v5){
        cout << " " << v;
    }
    cout << endl;

    cout << "v6 =";
    for (auto& v : v6){
        cout << " " << v;
    }
    cout << endl;

    // Move vector v2 to vector v7
    vector <int> v7(move(v2));
    vector <int>::iterator v7_Iter;

    cout << "v7 =";
    for (auto& v : v7){
        cout << " " << v;
    }
    cout << endl;

    vector<int> v8{ { 1, 2, 3, 4 } };
    for (auto& v : v8){
        cout << " " << v ;
    }
    cout << endl;
}
```

```Output
v1 = 0 0 0v2 = 2 2 2 2 2v3 = 1 1 1v4 = 2 2 2 2 2v5 = 0 1 2 3 4v6 = 1 2v7 = 2 2 2 2 21 2 3 4
```

## <a name="see-also"></a>参照

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
