---
title: set クラス
ms.date: 11/04/2016
f1_keywords:
- set/std::set
- set/std::set::allocator_type
- set/std::set::const_iterator
- set/std::set::const_pointer
- set/std::set::const_reference
- set/std::set::const_reverse_iterator
- set/std::set::difference_type
- set/std::set::iterator
- set/std::set::key_compare
- set/std::set::key_type
- set/std::set::pointer
- set/std::set::reference
- set/std::set::reverse_iterator
- set/std::set::size_type
- set/std::set::value_compare
- set/std::set::value_type
- set/std::set::begin
- set/std::set::cbegin
- set/std::set::cend
- set/std::set::clear
- set/std::set::count
- set/std::set::crbegin
- set/std::set::crend
- set/std::set::emplace
- set/std::set::emplace_hint
- set/std::set::empty
- set/std::set::end
- set/std::set::equal_range
- set/std::set::erase
- set/std::set::find
- set/std::set::get_allocator
- set/std::set::insert
- set/std::set::key_comp
- set/std::set::lower_bound
- set/std::set::max_size
- set/std::set::rbegin
- set/std::set::rend
- set/std::set::size
- set/std::set::swap
- set/std::set::upper_bound
- set/std::set::value_comp
helpviewer_keywords:
- std::set [C++]
- std::set [C++], allocator_type
- std::set [C++], const_iterator
- std::set [C++], const_pointer
- std::set [C++], const_reference
- std::set [C++], const_reverse_iterator
- std::set [C++], difference_type
- std::set [C++], iterator
- std::set [C++], key_compare
- std::set [C++], key_type
- std::set [C++], pointer
- std::set [C++], reference
- std::set [C++], reverse_iterator
- std::set [C++], size_type
- std::set [C++], value_compare
- std::set [C++], value_type
- std::set [C++], begin
- std::set [C++], cbegin
- std::set [C++], cend
- std::set [C++], clear
- std::set [C++], count
- std::set [C++], crbegin
- std::set [C++], crend
- std::set [C++], emplace
- std::set [C++], emplace_hint
- std::set [C++], empty
- std::set [C++], end
- std::set [C++], equal_range
- std::set [C++], erase
- std::set [C++], find
- std::set [C++], get_allocator
- std::set [C++], insert
- std::set [C++], key_comp
- std::set [C++], lower_bound
- std::set [C++], max_size
- std::set [C++], rbegin
- std::set [C++], rend
- std::set [C++], size
- std::set [C++], swap
- std::set [C++], upper_bound
- std::set [C++], value_comp
ms.assetid: 8991f9aa-5509-4440-adc1-371512d32018
ms.openlocfilehash: f1718b1cd362e54f63388b46025804ccc0396851
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689013"
---
# <a name="set-class"></a>set クラス

STL コンテナー クラスの set は、コレクションのデータを格納および取得するために使用されます。コレクションに含まれる要素の値は一意であり、データが自動的に順序付けられるときにキー値として使用されます。 set 内の要素の値は直接変更できません。 代わりに、以前の値を削除し、新しい値の要素を挿入する必要があります。

## <a name="syntax"></a>構文

```cpp
template <class Key,
    class Traits=less<Key>,
    class Allocator=allocator<Key>>
class set
```

### <a name="parameters"></a>パラメーター

*キー* \
set に格納される要素のデータ型。

*特徴*\
2 つの要素の値を並べ替えキーとして比較して、set 内の要素の相対順序を決定できる関数オブジェクトを提供する型。 この引数は省略可能であり、既定値は二項述語 **less** *\<Key>* です。

C++ 14 では、型パラメーターを使用せずに `std::less<>` 述語または `std::greater<>` 述語を指定することで、異種ルックアップを有効にすることができます。 詳細については、「[連想コンテナーの異種ルックアップ](../standard-library/stl-containers.md#sequence_containers)」をご覧ください。

*アロケーター* \
メモリの set の割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクトを表す型。 この引数は省略可能であり、既定値は `allocator<Key>` です。

## <a name="remarks"></a>Remarks

C++ 標準ライブラリの set の概要

- hash_map は連想コンテナーであり、関連付けられたキー値に基づいて要素の値を効率的に取得できるようにする可変サイズのコンテナーとして機能します。 さらに、単純な連想コンテナーです。これは、要素値がキー値であるためです。

- 反転することができます。これは、hash_map には、要素にアクセスするための双方向反復子が用意されているためです。

- 並べ替えが実行されます。これは、指定した比較関数に従ってコンテナー内のキー値によって要素に順序が設定されるためです。

- 一意のクラスです。これは、各要素が一意のキーを持つ必要があるためです。 set は、単純な連想コンテナーであるため、要素も一意です。

また、セットはクラステンプレートとしても記述されます。これは、提供される機能がジェネリックであり、要素として含まれる特定の型のデータに依存しないためです。 使用されているデータ型は、クラス テンプレートで比較関数やアロケーターと共にパラメーターとして指定されます。

一般的に、コンテナー型の選択は、アプリケーションにおいて必要な検索および挿入の種類に基づいている必要があります。 連想コンテナーは、検索、挿入、削除の各操作用に最適化されています。 これらの操作を明示的にサポートするメンバー関数は効率的であり、処理時間は平均的にコンテナー内にある要素の数の対数に比例します。 要素を挿入しても反復子の有効性は失われません。また、要素を削除した場合は、削除された要素を具体的に指す反復子だけが無効化されます。

値とキーを関連付ける条件をアプリケーションが満たしている場合、set は最適な連想コンテナーとなっている必要があります。 set の要素は一意であり、独自の並べ替えキーとして機能します。 この種類の構造体のモデルは、単語が 1 回だけ出現する可能性がある単語の順序付きのリストです。 キーワードを複数設定できる場合は、multiset が適切なコンテナー構造体となります。 値が一意のキーワードのリストにアタッチされている必要がある場合、map がこのデータを格納するのに適切な構造体です。 キーが一意でない場合は、multimap が最適なコンテナーです。

set では、[key_compare](#key_compare) 型の格納されている関数オブジェクトを呼び出すことによって、set が制御するシーケンスを並べ替えます。 この格納されているオブジェクトは比較関数であり、メンバー関数 [key_comp](#key_comp) を呼び出すことによってアクセスできます。 通常、要素は、この順序を確立するために小なり比較だけを実行できる必要があります。これにより、2 つの要素が指定されたときに、それらの要素が等しいか (どちらか一方が小さくはない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 テクニカル ノートでは、比較関数は、数学上の標準的な意味で厳密弱順序を発生させる二項述語であると示されています。 二項述語 *f*(*x,y*) は、2 つの引数オブジェクト (*x* および *y*) と戻り値 (**true** または **false**) を持つ関数オブジェクトです。 set に適用される順序付けは、二項述語が非再帰、反対称、推移的であり、等価性が推移的である (2 つのオブジェクト *x* と *y* が、*f*(*x,y*) と *f*(*y,x*) の両方が false の場合に等価になるように定義されている) 場合、厳密弱順序になります。 2 つのキーの等値に関する条件が等価性の条件よりも厳しく、優先される場合、順序付けは完全な順序付け (すべての要素が相互の値に基づいて並べ替えられる) となり、一致するそれぞれのキーを識別するのが難しくなります。

C++ 14 では、型パラメーターを使用せずに `std::less<>` 述語または `std::greater<>` 述語を指定することで、異種ルックアップを有効にすることができます。 詳細については、「[連想コンテナーの異種ルックアップ](../standard-library/stl-containers.md#sequence_containers)」をご覧ください。

set クラスに用意されている反復子は双方向反復子ですが、クラス メンバー関数 [insert](#insert) と [set](#set) には、弱い入力反復子をテンプレート パラメーターとして取得するバージョンがあります。この反復子の機能に関する要件は、双方向反復子のクラスで保証されている要件よりも低くなっています。 これらの反復子の機能に差異があるのは、反復子の概念が異なっているためです。 反復子の各概念には、反復子独自の一連の要件が含まれています。また、それらの要件を使用するアルゴリズムでは、反復子の種類ごとに指定されている要件に対して、前提を絞り込む必要があります。 たとえば、一部のオブジェクトを参照するために入力反復子が逆参照される可能性があることを前提とする場合があります。さらに、シーケンス内にある次の反復子に対して逆参照が増加する可能性があることを前提とする場合もあります。 これは最小限の機能ですが、クラスのメンバー関数という文脈で反復子の範囲 [ `First`, `Last`) について意味を成していれば十分です。

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[set](#set)|空の set を構築するか、他の set の全体または一部のコピーである set を構築します。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[allocator_type](#allocator_type)|set オブジェクトの `allocator` クラスを表す型。|
|[const_iterator](#const_iterator)|set 内の **const** 要素を読み取ることができる双方向反復子を提供する型。|
|[const_pointer](#const_pointer)|set 内の **const** 要素へのポインターを提供する型。|
|[const_reference](#const_reference)|読み取りと **const** 操作の実行のために、set に格納された **const** 要素への参照を提供する型。|
|[const_reverse_iterator](#const_reverse_iterator)|set 内の任意の **const** 要素を読み取ることができる双方向反復子を提供する型。|
|[difference_type](#difference_type)|set の要素の数を、反復子が指す要素の範囲に基づいて表すために使用できる符号付き整数型。|
|[Iterator](#iterator)|set 内の任意の要素の読み取りまたは変更ができる双方向反復子を提供する型。|
|[key_compare](#key_compare)|2 つの並べ替えキーを比較して、set 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。|
|[key_type](#key_type)|この型は、並べ替えキーとしてキャパシティ内で set の要素として格納されるオブジェクトを表します。|
|[pointer](#pointer)|set 内の要素へのポインターを提供する型。|
|[reference](#reference)|set に格納されている要素への参照を提供する型。|
|[reverse_iterator](#reverse_iterator)|反転された set 内の 1 つの要素の読み取りまたは変更ができる双方向反復子を提供する型。|
|[size_type](#size_type)|set 内の要素の数を表すことができる符号なし整数型。|
|[value_compare](#value_compare)|2 つの要素を比較して、set 内の要素の相対順序を決定できる関数オブジェクトを提供する型。|
|[value_type](#value_type)|この型は、値としてキャパシティ内で set の要素として格納されるオブジェクトを表します。|

### <a name="functions"></a>関数

|||
|-|-|
|[begin](#begin)|set 内の最初の要素を指す定数反復子を返します。|
|[cbegin](#cbegin)|set 内の最初の要素を指す定数反復子を返します。|
|[cend](#cend)|set 内の最後の要素の次の位置を指す定数反復子を返します。|
|[clear](#clear)|set のすべての要素を消去します。|
|[count](#count)|パラメーター指定したキーに一致するキーを持つ、set 内の要素の数を返します。|
|[crbegin](#rbegin)|反転された set 内の最初の要素を指す定数反復子を返します。|
|[crend](#rend)|反転された set 内の最後の要素の次の位置を指す定数反復子を返します。|
|[emplace](#emplace)|インプレースで構築された要素を set に挿入します。|
|[emplace_hint](#emplace_hint)|インプレースで構築された要素を、配置ヒントと共に set に挿入します。|
|[empty](#empty)|set が空かどうかをテストします。|
|[end](#end)|set 内の最後の要素の次の位置を指す反復子を返します。|
|[equal_range](#equal_range)|指定したキーよりも大きいキーを持つ、set 内の最初の要素を指す反復子のペア、およびそのキー以上のキーを持つ、set 内の最初の要素を指す反復子のペアを返します。|
|[erase](#erase)|セット内の要素または要素の範囲を指定した位置から削除するか、または指定したキーと一致する要素を削除します。|
|[find](#find)|指定したキーと同じキーを持つ、set 内の要素の位置を指す反復子を返します。|
|[get_allocator](#get_allocator)|set の構築に使用される `allocator` オブジェクトのコピーを返します。|
|[insert](#insert)|set に要素または要素範囲を挿入します。|
|[key_comp](#key_comp)|set 内のキーを並べ替えるために使用される比較オブジェクトのコピーを取得します。|
|[lower_bound](#lower_bound)|指定したキー以上のキーを持つ、set 内の最初の要素を指す反復子を返します。|
|[max_size](#max_size)|set の最大長を返します。|
|[rbegin](#rbegin)|反転された set 内の最初の要素を指す反復子を返します。|
|[rend](#rend)|反転された set 内の最後の要素の次の位置を指す反復子を返します。|
|[size](#size)|セット内の要素数を返します。|
|[swap](#swap)|2 つの set の要素を交換します。|
|[upper_bound](#upper_bound)|指定したキーよりも大きいキーを持つ、set 内の最初の要素を指す反復子を返します。|
|[value_comp](#value_comp)|set 内の要素の値を並べ替えるために使用される比較オブジェクトのコピーを取得します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](#op_eq)|別の set のコピーで set の要素を置き換えます。|

## <a name="allocator_type"></a>allocator_type

set オブジェクトのアロケータ― クラスを表す型です。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Remarks

`allocator_type` は、テンプレートパラメーター[アロケーター](../standard-library/set-class.md)のシノニムです。

multiset が要素の並べ替えに使用する関数オブジェクトを返します。テンプレート パラメーター `Allocator` です。

`Allocator` の詳細については、[set クラス](../standard-library/set-class.md)のトピックのコメントに関するセクションを参照してください。

### <a name="example"></a>例

[get_allocator](#get_allocator) を使用する例については、`allocator_type` の例を参照してください。

## <a name="begin"></a>初め

set 内の最初の要素を指す定数反復子を返します。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>戻り値

set 内の最初の要素、または空の set の次の位置を指す双方向反復子。

### <a name="remarks"></a>Remarks

@No__t_0 の戻り値が `const_iterator` に割り当てられている場合、set オブジェクト内の要素は変更できません。 @No__t_0 の戻り値が `iterator` に割り当てられている場合は、set オブジェクト内の要素を変更できます。

### <a name="example"></a>例

```cpp
// set_begin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::const_iterator s1_cIter;

   s1.insert( 1 );
   s1.insert( 2 );
   s1.insert( 3 );

   s1_Iter = s1.begin( );
   cout << "The first element of s1 is " << *s1_Iter << endl;

   s1_Iter = s1.begin( );
   s1.erase( s1_Iter );

   // The following 2 lines would err because the iterator is const
   // s1_cIter = s1.begin( );
   // s1.erase( s1_cIter );

   s1_cIter = s1.begin( );
   cout << "The first element of s1 is now " << *s1_cIter << endl;
}
```

```Output
The first element of s1 is 1
The first element of s1 is now 2
```

## <a name="cbegin"></a>cbegin

範囲内の最初の要素を指す**定数**反復子を返します。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

範囲の最初の要素、または空の範囲の末尾の次の位置 (空の範囲の場合は `cbegin() == cend()`) を指す、 **const**双方向アクセス反復子。

### <a name="remarks"></a>Remarks

`cbegin` の戻り値で範囲内の要素を変更することはできません。

`begin()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常は、次の例に示すように [auto](../cpp/auto-cpp.md) 型推論キーワードと共に使用します。 この例では、`begin()` と `cbegin()` をサポートする任意の種類の変更可能な (非**定数**) コンテナーとして `Container` を検討してください。

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

範囲の末尾の次の位置を指し示す**const**双方向アクセス反復子。

### <a name="remarks"></a>Remarks

`cend` は、反復子が範囲の末尾を超えたかどうかをテストするために使用されます。

`end()` メンバー関数の代わりにこのメンバー関数を使用して、戻り値が `const_iterator` になることを保証できます。 通常は、次の例に示すように [auto](../cpp/auto-cpp.md) 型推論キーワードと共に使用します。 この例では、`end()` と `cend()` をサポートする任意の種類の変更可能な (非**定数**) コンテナーとして `Container` を検討してください。

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

`cend` によって返された値は逆参照しないでください。

## <a name="clear"></a>クリア

set のすべての要素を消去します。

```cpp
void clear();
```

### <a name="example"></a>例

```cpp
// set_clear.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 1 );
   s1.insert( 2 );

   cout << "The size of the set is initially " << s1.size( )
        << "." << endl;

   s1.clear( );
   cout << "The size of the set after clearing is "
        << s1.size( ) << "." << endl;
}
```

```Output
The size of the set is initially 2.
The size of the set after clearing is 0.
```

## <a name="const_iterator"></a>const_iterator

set 内の **const** 要素を読み取ることができる双方向反復子を提供する型。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Remarks

`const_iterator` 型で要素の値を変更することはできません。

### <a name="example"></a>例

`const_iterator` を使用する例については、[begin](#begin) の例を参照してください。

## <a name="const_pointer"></a>const_pointer

set 内の **const** 要素へのポインターを提供する型。

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Remarks

`const_pointer` 型で要素の値を変更することはできません。

ほとんどの場合、const set オブジェクト内の要素にアクセスするには、[const_iterator](#const_iterator) を使用する必要があります。

## <a name="const_reference"></a>const_reference

読み取りと **const** 操作の実行のために、set に格納された **const** 要素への参照を提供する型。

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>例

```cpp
// set_const_ref.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the set is 10.
```

## <a name="const_reverse_iterator"></a>const_reverse_iterator

set 内の任意の **const** 要素を読み取ることができる双方向反復子を提供する型。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Remarks

`const_reverse_iterator` 型は要素の値を変更できず、逆の順序で set を反復処理するために使用します。

### <a name="example"></a>例

`const_reverse_iterator` の宣言方法や使用方法の例については、[rend](#rend) の例をご覧ください。

## <a name="count"></a>数

パラメーター指定したキーに一致するキーを持つ、set 内の要素の数を返します。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
照合される set の要素のキー。

### <a name="return-value"></a>戻り値

並べ替えキーがパラメーター キーと一致する要素が set に含まれている場合は 1。 set に一致するキーを持つ要素が含まれていない場合は 0。

### <a name="remarks"></a>Remarks

メンバー関数は、次の範囲内の要素の数を返します。

\[ lower_bound (*キー*)、upper_bound (*キー*))。

### <a name="example"></a>例

set::count メンバー関数の使用例を次に示します。

```cpp
// set_count.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;
    set<int> s1;
    set<int>::size_type i;

    s1.insert(1);
    s1.insert(1);

    // Keys must be unique in set, so duplicates are ignored
    i = s1.count(1);
    cout << "The number of elements in s1 with a sort key of 1 is: "
         << i << "." << endl;

    i = s1.count(2);
    cout << "The number of elements in s1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in s1 with a sort key of 1 is: 1.
The number of elements in s1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>crbegin

反転された set 内の最初の要素を指す定数反復子を返します。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>戻り値

反転された set 内の最初の要素を示す、または反転されていない set 内の最後の要素だったものを示す const 反転双方向反復子。

### <a name="remarks"></a>Remarks

`crbegin` は、[begin](#begin) が set で使用されるように、逆順の set で使用されます。

戻り値が `crbegin` の場合、set オブジェクトは変更できません。

### <a name="example"></a>例

```cpp
// set_crbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crbegin( );
   cout << "The first element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
```

## <a name="crend"></a>crend

反転された set 内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>戻り値

逆順の set 内の最後の要素の次の場所 (通常の順序の set 内の最初の要素の前の場所) を指す定数逆順双方向反復子。

### <a name="remarks"></a>Remarks

`crend` は、[end](#end) が set で使用されるように、逆順の set で使用されます。

戻り値が `crend` の場合、set オブジェクトは変更できません。 `crend` によって返された値は逆参照しないでください。

`crend` を使用して、逆順反復子が set の末尾に達したかどうかをテストできます。

### <a name="example"></a>例

```cpp
// set_crend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_crIter = s1.crend( );
   s1_crIter--;
   cout << "The last element in the reversed set is "
        << *s1_crIter << "." << endl;
}
```

## <a name="difference_type"></a>difference_type

set の要素の数を、反復子が指す要素の範囲に基づいて表すために使用できる符号付き整数型。

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Remarks

`difference_type` は、コンテナーの反復子を減算またはインクリメントするときに返される型です。 通常 `difference_type` は、 *[ first,  last)* の範囲内で、反復子 `first` と `last` の間にある要素の数を表すために使用され、`first` が指す要素と、`last` が指す要素の 1 つ前までの範囲の要素を含みます。

`difference_type` は、入力反復子の要件を満たすすべての反復子 (set などの反転可能なコンテナーによってサポートされる双方向反復子のクラスを含む) に対して使用できますが、反復子間の減算は、vector などのランダム アクセス コンテナーによって提供される、ランダム アクセス反復子によってのみサポートされます。

### <a name="example"></a>例

```cpp
// set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <set>
#include <algorithm>

int main( )
{
   using namespace std;

   set <int> s1;
   set <int>::iterator s1_Iter, s1_bIter, s1_eIter;

   s1.insert( 20 );
   s1.insert( 10 );
   s1.insert( 20 );   // won't insert as set elements are unique

   s1_bIter = s1.begin( );
   s1_eIter = s1.end( );

   set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( s1_bIter, s1_eIter, 5 );
   df_typ10 = count( s1_bIter, s1_eIter, 10 );
   df_typ20 = count( s1_bIter, s1_eIter, 20 );

   // the keys, and hence the elements of a set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in set s1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in set s1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in set s1.\n";

   // count the number of elements in a set
   set <int>::difference_type  df_count = 0;
   s1_Iter = s1.begin( );
   while ( s1_Iter != s1_eIter)
   {
      df_count++;
      s1_Iter++;
   }

   cout << "The number of elements in the set s1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in set s1.
The number '10' occurs 1 times in set s1.
The number '20' occurs 1 times in set s1.
The number of elements in the set s1 is: 2.
```

## <a name="emplace"></a>emplace

インプレースで構築された (コピーまたは移動操作が実行されない) 要素を挿入します。

```cpp
template <class... Args>
pair<iterator, bool>
emplace(
    Args&&... args);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*value*|値が同じ順序付けになる要素がセットにまだ含まれていない場合に、セットに挿入される要素を構築するために転送される引数。|

### <a name="return-value"></a>戻り値

[pair](../standard-library/pair-structure.md)。その bool コンポーネントは、挿入が行われた場合は true を返し、マップに既に等しい順序の値を持つ要素が含まれている場合は false を返します。 戻り値ペアの反復子コンポーネントは、新しい要素が挿入されるアドレス (bool コンポーネントが true の場合) または要素が既に配置されているアドレス (bool コンポーネントが false の場合) を返します。

### <a name="remarks"></a>Remarks

この関数では、反復子や参照は無効になりません。

配置の実行中、例外がスローされるとコンテナーの状態は変更されません。

### <a name="example"></a>例

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    auto ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
        cout << "set not modified" << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;

    ret = s1.emplace("ten");

    if (!ret.second){
        cout << "Emplace failed, element with value \"ten\" already exists."
            << endl << "  The existing element is (" << *ret.first << ")"
            << endl;
    }
    else{
        cout << "set modified, now contains ";
        print(s1);
    }
    cout << endl;
}
```

## <a name="emplace_hint"></a>emplace_hint

インプレースで構築された (コピーまたは移動操作が実行されない) 要素を、配置ヒントと一緒に挿入します。

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>パラメーター

*args* \
挿入される要素をセットがまだ含んでいない場合、より一般的には、値が同じ順序付けになる要素がセットにまだ含まれていない場合に、セットに挿入される要素を構築するために転送される引数。

*\*
正しい挿入ポイントの検索を開始する場所 (その位置がの直前にある*場合、挿入*は、対数時間ではなく償却定数時間で実行できます)。

### <a name="return-value"></a>戻り値

新しく挿入される要素を指す反復子。

要素が既に存在するために挿入が失敗した場合は、既存の要素を指す反復子を返します。

### <a name="remarks"></a>Remarks

この関数では、反復子や参照は無効になりません。

配置の実行中、例外がスローされるとコンテナーの状態は変更されません。

### <a name="example"></a>例

```cpp
// set_emplace.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: " << endl;

    for (const auto& p : s) {
        cout << "(" << p <<  ") ";
    }

    cout << endl;
}

int main()
{
    set<string> s1;

    // Emplace some test data
    s1.emplace("Anna");
    s1.emplace("Bob");
    s1.emplace("Carmine");

    cout << "set starting data: ";
    print(s1);
    cout << endl;

    // Emplace with hint
    // s1.end() should be the "next" element after this emplacement
    s1.emplace_hint(s1.end(), "Doug");

    cout << "set modified, now contains ";
    print(s1);
    cout << endl;
}
```

## <a name="empty"></a>指定

set が空かどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

set が空の場合は **true**、set が空ではない場合は **false**。

### <a name="example"></a>例

```cpp
// set_empty.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2;
   s1.insert ( 1 );

   if ( s1.empty( ) )
      cout << "The set s1 is empty." << endl;
   else
      cout << "The set s1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The set s2 is empty." << endl;
   else
      cout << "The set s2 is not empty." << endl;
}
```

```Output
The set s1 is not empty.
The set s2 is empty.
```

## <a name="end"></a>終わり

末尾超え反復子を返します。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>戻り値

末尾超え反復子。 set が空の場合は、`set::end() == set::begin()`。

### <a name="remarks"></a>Remarks

**end** は、反復子が set の末尾を超えたかどうかをテストするために使用します。

**end** によって返された値は逆参照しないでください。

コード例については、「[set::find](#find)」を参照してください。

## <a name="equal_range"></a>equal_range

指定したキー以上のキーを持つ、set 内の最初の要素を指す反復子のペア、およびそのキーより大きいキーを持つ、set 内の最初の要素を指す反復子のペアを返します。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の set 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

1 番目がそのキーの [lower_bound](#lower_bound)、2 番目がそのキーの [upper_bound](#upper_bound) である、反復子のペア。

メンバー関数によって返されるペア `pr` 最初の反復子にアクセスするには、`pr` を使用します。 **最初**に、下限の反復子を逆参照するには、\* (`pr` を使用します。 **最初**)。 メンバー関数によって返さ `pr` ペアの2番目の反復子にアクセスするには、`pr` を使用します。 **次**に、上限の反復子を逆参照するには、\* (`pr` を使用します。 **2 番目**)。

### <a name="example"></a>例

```cpp
// set_equal_range.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   typedef set<int, less< int > > IntSet;
   IntSet s1;
   set <int, less< int > > :: const_iterator s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   pair <IntSet::const_iterator, IntSet::const_iterator> p1, p2;
   p1 = s1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the set s1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   s1_RcIter = s1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *s1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = s1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == s1.end( ) ) && ( p2.second == s1.end( ) ) )
      cout << "The set s1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of set s1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the set s1 is: 30.
The lower bound of the element with a key of 20 in the set s1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The set s1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>消去

セット内の要素または要素の範囲を指定した位置から削除するか、または指定したキーと一致する要素を削除します。

```cpp
iterator erase(
    const_iterator Where);

iterator erase(
    const_iterator First,
    const_iterator Last);

size_type erase(
    const key_type& Key);
```

### <a name="parameters"></a>パラメーター

*@No__t_1*
削除される要素の位置。

*最初*の \
削除される最初の要素の位置。

*最後*の \
削除される最後の要素の次の位置。

*キー* \
削除される要素のキー値。

### <a name="return-value"></a>戻り値

最初の 2 つのメンバー関数の場合は、削除された要素の後の最初の残存要素、またはセットの最後の要素 (このような要素が存在しない場合) を指定する双方向反復子。

3 番目のメンバー関数の場合は、セットから削除された要素の数を返します。

### <a name="example"></a>例

```cpp
// set_erase.cpp
// compile with: /EHsc
#include <set>
#include <string>
#include <iostream>
#include <iterator> // next() and prev() helper functions

using namespace std;

using myset = set<string>;

void printset(const myset& s) {
    for (const auto& iter : s) {
        cout << " [" << iter << "]";
    }
    cout << endl << "size() == " << s.size() << endl << endl;
}

int main()
{
    myset s1;

    // Fill in some data to test with, one at a time
    s1.insert("Bob");
    s1.insert("Robert");
    s1.insert("Bert");
    s1.insert("Rob");
    s1.insert("Bobby");

    cout << "Starting data of set s1 is:" << endl;
    printset(s1);
    // The 1st member function removes an element at a given position
    s1.erase(next(s1.begin()));
    cout << "After the 2nd element is deleted, the set s1 is:" << endl;
    printset(s1);

    // Fill in some data to test with, one at a time, using an initializer list
    myset s2{ "meow", "hiss", "purr", "growl", "yowl" };

    cout << "Starting data of set s2 is:" << endl;
    printset(s2);
    // The 2nd member function removes elements
    // in the range [First, Last)
    s2.erase(next(s2.begin()), prev(s2.end()));
    cout << "After the middle elements are deleted, the set s2 is:" << endl;
    printset(s2);

    myset s3;

    // Fill in some data to test with, one at a time, using emplace
    s3.emplace("C");
    s3.emplace("C#");
    s3.emplace("D");
    s3.emplace("D#");
    s3.emplace("E");
    s3.emplace("E#");
    s3.emplace("F");
    s3.emplace("F#");
    s3.emplace("G");
    s3.emplace("G#");
    s3.emplace("A");
    s3.emplace("A#");
    s3.emplace("B");

    cout << "Starting data of set s3 is:" << endl;
    printset(s3);
    // The 3rd member function removes elements with a given Key
    myset::size_type count = s3.erase("E#");
    // The 3rd member function also returns the number of elements removed
    cout << "The number of elements removed from s3 is: " << count << "." << endl;
    cout << "After the element with a key of \"E#\" is deleted, the set s3 is:" << endl;
    printset(s3);
}
```

## <a name="find"></a>探す

指定したキーと等価のキーを持つ、set 内の要素の位置を参照する反復子を返します。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の set 内の要素の並べ替えキーと照合するキー値。

### <a name="return-value"></a>戻り値

指定したキーを持つ要素の位置を参照する反復子。キーの一致が検出されない場合は、set 内の最後の要素の次の位置 (`set::end()`)。

### <a name="remarks"></a>Remarks

このメンバー関数は、小なり比較関係に基づいて順序を誘発する二項述語の下で、キーが引数*キー*と等価である set 内の要素を参照する反復子を返します。

@No__t_0 の戻り値が `const_iterator` に割り当てられている場合、set オブジェクトは変更できません。 @No__t_0 の戻り値が `iterator` に割り当てられている場合は、set オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// compile with: /EHsc /W4 /MTd
#include <set>
#include <iostream>
#include <vector>
#include <string>

using namespace std;

template <typename T> void print_elem(const T& t) {
    cout << "(" << t << ") ";
}

template <typename T> void print_collection(const T& t) {
    cout << t.size() << " elements: ";

    for (const auto& p : t) {
        print_elem(p);
    }
    cout << endl;
}

template <typename C, class T> void findit(const C& c, T val) {
    cout << "Trying find() on value " << val << endl;
    auto result = c.find(val);
    if (result != c.end()) {
        cout << "Element found: "; print_elem(*result); cout << endl;
    } else {
        cout << "Element not found." << endl;
    }
}

int main()
{
    set<int> s1({ 40, 45 });
    cout << "The starting set s1 is: " << endl;
    print_collection(s1);

    vector<int> v;
    v.push_back(43);
    v.push_back(41);
    v.push_back(46);
    v.push_back(42);
    v.push_back(44);
    v.push_back(44); // attempt a duplicate

    cout << "Inserting the following vector data into s1: " << endl;
    print_collection(v);

    s1.insert(v.begin(), v.end());

    cout << "The modified set s1 is: " << endl;
    print_collection(s1);
    cout << endl;
    findit(s1, 45);
    findit(s1, 6);
}
```

## <a name="get_allocator"></a>get_allocator

set の構築に使用されるアロケーター オブジェクトのコピーを返します。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>戻り値

set がメモリの管理に使用するアロケーターである、テンプレート パラメーター `Allocator`。

`Allocator` の詳細については、[set クラス](../standard-library/set-class.md)のトピックのコメントに関するセクションを参照してください。

### <a name="remarks"></a>Remarks

set クラスのアロケーターは、クラスがどのようにストレージを管理するかを指定します。 C++ 標準ライブラリ コンテナー クラスで提供される既定のアロケーターは、ほとんどのプログラミング要件に対応しています。 独自のアロケーター クラスを作成して使用することは、C++ における高度な作業の 1 つです。

### <a name="example"></a>例

```cpp
// set_get_allocator.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int>::allocator_type s1_Alloc;
   set <int>::allocator_type s2_Alloc;
   set <double>::allocator_type s3_Alloc;
   set <int>::allocator_type s4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   set <int> s1;
   set <int, allocator<int> > s2;
   set <double, allocator<double> > s3;

   s1_Alloc = s1.get_allocator( );
   s2_Alloc = s2.get_allocator( );
   s3_Alloc = s3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << s2.max_size( ) << "." << endl;

   cout << "\nThe number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << s3.max_size( ) <<  "." << endl;

   // The following line creates a set s4
   // with the allocator of multiset s1.
   set <int> s4( less<int>( ), s1_Alloc );

   s4_Alloc = s4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( s1_Alloc == s4_Alloc )
   {
      cout << "\nThe allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "\nThe allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a>insert

set に要素または要素範囲を挿入します。

```cpp
// (1) single element
pair<iterator, bool> insert(
    const value_type& Val);

// (2) single element, perfect forwarded
template <class ValTy>
pair<iterator, bool>
insert(
    ValTy&& Val);

// (3) single element with hint
iterator insert(
    const_iterator Where,
    const value_type& Val);

// (4) single element, perfect forwarded, with hint
template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);

// (5) range
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

// (6) initializer list
void insert(
    initializer_list<value_type>
IList);
```

### <a name="parameters"></a>パラメーター

*Val* \
値が同じ順序付けになる要素が set にまだ含まれていない場合に、set に挿入される要素の値。

*@No__t_1*
正しい挿入ポイントの検索を開始する場所 (その位置がの直前にある*場合、挿入*は、対数時間ではなく償却定数時間で実行できます)。

*Valty* \
Set が[value_type](../standard-library/map-class.md#value_type)の要素を構築するために使用できる引数の型を指定し、引数として*Val*を完全に転送するテンプレートパラメーター。

*最初*の \
コピーされる最初の要素の位置。

*最後*の \
コピーされる最後の要素の次の位置。

*InputIterator* \
[入力反復子](../standard-library/input-iterator-tag-struct.md)の要件を満たすテンプレート関数の引数。この反復子は、[value_type](../standard-library/map-class.md#value_type) オブジェクトの構築に使用できる型の要素を指し示します。

*IList* \
要素のコピー元の [initializer_list](../standard-library/initializer-list.md)。

### <a name="return-value"></a>戻り値

単一要素のメンバー関数 (1) と (2) は、ペアを返します。この[ペア](../standard-library/pair-structure.md)の**bool**コンポーネントは、挿入が行われた場合は true になり、順序に等しい値の要素がセットに既に含まれている場合は false になります。 戻り値のペアの反復子コンポーネントは、 **bool**コンポーネントが true の場合は新しく挿入された要素を指し、 **bool**コンポーネントが false の場合は既存の要素を指します。

単一要素の with-hint メンバー関数 (3) および (4) は、set に挿入された新しい要素の位置を指す反復子を返します。ただし、同じキーを持つ要素が既に存在する場合、この反復子は既存の要素を指します。

### <a name="remarks"></a>Remarks

この関数では、反復子、ポインター、参照は無効になりません。

要素を 1 つだけ挿入するとき、例外がスローされるとコンテナーの状態は変更されません。 複数の要素を挿入するときに例外がスローされた場合、コンテナーの状態は未指定ですが、有効な状態になっています。

単一要素のメンバー関数によって返される `pair` `pr` の反復子コンポーネントにアクセスするには、`pr.first` を使用します。返されるペアに含まれる反復子を逆参照するには、要素を指定して、`*pr.first` を使用します。 **Bool**コンポーネントにアクセスするには、`pr.second` を使用します。 例については、この記事で後ほど説明するサンプル コードを参照してください。

コンテナーの [value_type](../standard-library/map-class.md#value_type) はそのコンテナーに属する typedef であり、set の場合、`set<V>::value_type` は `const V` 型です。

範囲を指定したメンバー関数 (5) は、範囲 `[First, Last)` の反復子によってアドレス指定された各要素に対応する set に要素値のシーケンスを挿入します。したがって、`Last` は挿入されません。 コンテナーのメンバー関数 `end()` は、コンテナー内にある最後の要素の直後の位置を参照します。たとえば、ステートメント `s.insert(v.begin(), v.end());` は、`v` のすべての要素を `s` に挿入しようとします。 範囲内で一意の値を持つ要素だけが挿入されますが、値が重複する要素は無視されます。 拒否される要素を確認するには、1 つの要素が指定された `insert` を使用します。

初期化子リストのメンバー関数 (6) は [initializer_list](../standard-library/initializer-list.md) を使用して、set に要素をコピーします。

インプレースで構築された (つまり、コピーまたは移動操作が実行されない) 要素の挿入については、「[set::emplace](#emplace)」および「[set::emplace_hint](#emplace_hint)」を参照してください。

### <a name="example"></a>例

```cpp
// set_insert.cpp
// compile with: /EHsc
#include <set>
#include <iostream>
#include <string>
#include <vector>

using namespace std;

template <typename S> void print(const S& s) {
    cout << s.size() << " elements: ";

    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    set<int> s1;
    // call insert(const value_type&) version
    s1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    s1.insert(20);

    cout << "The original set values of s1 are:" << endl;
    print(s1);

    // intentionally attempt a duplicate, single element
    auto ret = s1.insert(1);
    if (!ret.second){
        auto elem = *ret.first;
        cout << "Insert failed, element with value 1 already exists."
            << endl << "  The existing element is (" << elem << ")"
            << endl;
    }
    else{
        cout << "The modified set values of s1 are:" << endl;
        print(s1);
    }
    cout << endl;

    // single element, with hint
    s1.insert(s1.end(), 30);
    cout << "The modified set values of s1 are:" << endl;
    print(s1);
    cout << endl;

    // The templatized version inserting a jumbled range
    set<int> s2;
    vector<int> v;
    v.push_back(43);
    v.push_back(294);
    v.push_back(41);
    v.push_back(330);
    v.push_back(42);
    v.push_back(45);

    cout << "Inserting the following vector data into s2:" << endl;
    print(v);

    s2.insert(v.begin(), v.end());

    cout << "The modified set values of s2 are:" << endl;
    print(s2);
    cout << endl;

    // The templatized versions move-constructing elements
    set<string>  s3;
    string str1("blue"), str2("green");

    // single element
    s3.insert(move(str1));
    cout << "After the first move insertion, s3 contains:" << endl;
    print(s3);

    // single element with hint
    s3.insert(s3.end(), move(str2));
    cout << "After the second move insertion, s3 contains:" << endl;
    print(s3);
    cout << endl;

    set<int> s4;
    // Insert the elements from an initializer_list
    s4.insert({ 4, 44, 2, 22, 3, 33, 1, 11, 5, 55 });
    cout << "After initializer_list insertion, s4 contains:" << endl;
    print(s4);
    cout << endl;
}
```

## <a name="iterator"></a>反

セット内の任意の要素を読み取れる、定数の[双方向反復子](../standard-library/bidirectional-iterator-tag-struct.md)を提供する型。

```cpp
typedef implementation-defined iterator;
```

### <a name="example"></a>例

@No__t_1 の宣言方法や使用方法の例については、 [begin](#begin)の例を参照してください。

## <a name="key_comp"></a>key_comp

set 内のキーを並べ替えるために使用される比較オブジェクトのコピーを取得します。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>戻り値

set が要素の並べ替えに使用する関数オブジェクトである、テンプレート パラメーター `Traits` を返します。

`Traits`の詳細については、[set クラス](../standard-library/set-class.md)のトピックのコメントに関するセクションを参照してください。

### <a name="remarks"></a>Remarks

格納されているオブジェクトはメンバー関数を定義します。

**bool operator ()** (**const キー &** `_xVal`、 **const キー &** `_yVal`);

これは、並べ替え順で `_xVal` が `_yVal` に先行しかつ等しくない場合に **true** を返します。

[key_compare](#key_compare) および [value_compare](#value_compare) は両方ともテンプレート パラメーター `Traits` のシノニムです。 どちらも set および multiset クラスで使用でき、そこでは同一ですが、map および multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

```cpp
// set_key_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set<int, less<int> >::key_compare kc1 = s1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::key_compare kc2 = s2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of s2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of s1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of s2.
```

## <a name="key_compare"></a>key_compare

2 つの並べ替えキーを比較して、set 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Remarks

`key_compare` はテンプレート パラメーター `Traits` のシノニムです。

`Traits`の詳細については、[set クラス](../standard-library/set-class.md)のトピックのコメントに関するセクションを参照してください。

@No__t_0 と[value_compare](#value_compare)の両方がテンプレートパラメーター `Traits` のシノニムであることに注意してください。 どちらも set および multiset クラスで使用でき、そこでは同一ですが、map および multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

`key_compare` の宣言方法や使用方法の例については、[key_comp](#key_comp) の例をご覧ください。

## <a name="key_type"></a>key_type

並べ替えキーとしてキャパシティ内に set の要素として格納されるオブジェクトを表す型。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Remarks

`key_type` はテンプレート パラメーター `Key` のシノニムです。

`Key` の詳細については、[set クラス](../standard-library/set-class.md)のトピックのコメントに関するセクションを参照してください。

@No__t_0 と[value_type](#value_type)の両方がテンプレートパラメーター `Key` のシノニムであることに注意してください。 どちらも set および multiset クラスで使用でき、そこでは同一ですが、map および multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

`key_type` の宣言方法や使用方法の例については、[value_type](#value_type) の例をご覧ください。

## <a name="lower_bound"></a>lower_bound

指定したキー以上のキーを持つ、set 内の最初の要素を指す反復子を返します。

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の set 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

引数キー以上のキーを持つ set 内の要素の位置を指す、または、キーの一致が検出されない場合は set 内の最後の要素の次の位置を指す反復子または `const_iterator`。

### <a name="example"></a>例

```cpp
// set_lower_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.lower_bound( 20 );
   cout << "The element of set s1 with a key of 20 is: "
        << *s1_RcIter << "." << endl;

   s1_RcIter = s1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of set s1 with a key of 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator that addresses the location
   s1_AcIter = s1.end( );
   s1_AcIter--;
   s1_RcIter = s1.lower_bound( *s1_AcIter );
   cout << "The element of s1 with a key matching "
        << "that of the last element is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The element of set s1 with a key of 20 is: 20.
The set s1 doesn't have an element with a key of 40.
The element of s1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a>max_size

set の最大長を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

set の可能な最大長。

### <a name="example"></a>例

```cpp
// set_max_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::size_type i;

   i = s1.max_size( );
   cout << "The maximum possible length "
        << "of the set is " << i << "." << endl;
}
```

## <a name="op_eq"></a>operator =

この `set` の要素を、別の `set` の要素を使って置き換えます。

```cpp
set& operator=(const set& right);

set& operator=(set&& right);
```

### <a name="parameters"></a>パラメーター

*右*\
この `set` に割り当てられる新しい要素を提供する `set`。

### <a name="remarks"></a>Remarks

最初のバージョンの `operator=` では、*右側*の[左辺値参照](../cpp/lvalue-reference-declarator-amp.md)を使用して、要素を*右*からこの `set` にコピーします。

2 番目のバージョンは、right への[右辺値参照](../cpp/rvalue-reference-declarator-amp-amp.md)を使用します。 要素は*右*からこの `set` に移動します。

これらの演算子関数の実行前にこの `set` 内に含まれていた要素はすべて破棄されます。

### <a name="example"></a>例

```cpp
// set_operator_as.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
   {
   using namespace std;
   set<int> v1, v2, v3;
   set<int>::iterator iter;

   v1.insert(10);

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

set 内の要素へのポインターを提供する型。

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Remarks

**pointer** 型を使って要素の値を変更することができます。

ほとんどの場合、set オブジェクト内の要素にアクセスするには、[iterator](#iterator) を使用する必要があります。

## <a name="rbegin"></a>rbegin

反転された set 内の最初の要素を指す反復子を返します。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>戻り値

反転された set 内の最初の要素を示す、または反転されていない set 内の最後の要素だったものを示す反転双方向反復子。

### <a name="remarks"></a>Remarks

`rbegin` は、[begin](#begin) が set で使用されるように、逆順の set で使用されます。

`rbegin` の戻り値が `const_reverse_iterator`に割り当てられる場合は、set オブジェクトを変更できません。 `rbegin` の戻り値が `reverse_iterator` に割り当てられる場合は、set オブジェクトを変更できます。

`rbegin` を使用して、set 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// set_rbegin.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rbegin( );
   cout << "The first element in the reversed set is "
        << *s1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a set in a forward order
   cout << "The set is:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout << endl;

   // rbegin can be used to start an iteration
   // through a set in a reverse order
   cout << "The reversed set is:";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << " " << *s1_rIter;
   cout << endl;

   // A set element can be erased by dereferencing to its key
   s1_rIter = s1.rbegin( );
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed set is "<< *s1_rIter << "." << endl;
}
```

```Output
The first element in the reversed set is 30.
The set is: 10 20 30
The reversed set is: 30 20 10
After the erasure, the first element in the reversed set is 20.
```

## <a name="reference"></a>「

set に格納されている要素への参照を提供する型。

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>例

```cpp
// set_reference.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;

   s1.insert( 10 );
   s1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   const int &Ref1 = *s1.begin( );

   cout << "The first element in the set is "
        << Ref1 << "." << endl;
}
```

```Output
The first element in the set is 10.
```

## <a name="rend"></a>rend

反転された set 内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>戻り値

逆順の set 内の最後の要素の次の場所 (通常の順序の set 内の最初の要素の前の場所) を指す逆順双方向反復子。

### <a name="remarks"></a>Remarks

`rend` は、[end](#end) が set で使用されるように、逆順の set で使用されます。

`rend` の戻り値が `const_reverse_iterator`に割り当てられる場合は、set オブジェクトを変更できません。 `rend` の戻り値が `reverse_iterator` に割り当てられる場合は、set オブジェクトを変更できます。 `rend` によって返された値は逆参照しないでください。

`rend` を使用して、逆順反復子が set の末尾に達したかどうかをテストできます。

### <a name="example"></a>例

```cpp
// set_rend.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main() {
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;
   set <int>::reverse_iterator s1_rIter;
   set <int>::const_reverse_iterator s1_crIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_rIter = s1.rend( );
   s1_rIter--;
   cout << "The last element in the reversed set is "
        << *s1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a set in a forward order
   cout << "The set is: ";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++ )
      cout << *s1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a set in a reverse order
   cout << "The reversed set is: ";
   for ( s1_rIter = s1.rbegin( ) ; s1_rIter != s1.rend( ); s1_rIter++ )
      cout << *s1_rIter << " ";
   cout << "." << endl;

   s1_rIter = s1.rend( );
   s1_rIter--;
   s1.erase ( *s1_rIter );

   s1_rIter = s1.rend( );
   --s1_rIter;
   cout << "After the erasure, the last element in the "
        << "reversed set is " << *s1_rIter << "." << endl;
}
```

## <a name="reverse_iterator"></a>reverse_iterator

反転された set 内の 1 つの要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Remarks

型 `reverse_iterator` は、逆の順序で set を反復処理するために使用します。

### <a name="example"></a>例

`reverse_iterator` の宣言方法や使用方法の例については、[rbegin](#rbegin) の例を参照してください。

## <a name="set"></a>一連

空の set を構築するか、他の set の全体または一部のコピーである set を構築します。

```cpp
set();

explicit set(
    const Traits& Comp);

set(
    const Traits& Comp,
    const Allocator& Al);

set(
    const set& Right);

set(
    set&& Right);

set(
    initializer_list<Type> IList);

set(
    initializer_list<Type> IList,
    const Compare& Comp);

set(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>パラメーター

*Al* \
この set オブジェクトに使用するストレージアロケータークラス。既定では `Allocator` になります。

*Comp* \
set 内の要素の並べ替えに使用される、`const Traits` 型の比較関数。既定では `Compare` です。

*Rght* \
構築される set のコピー元となる set。

*最初*の \
コピーする要素範囲内の最初の要素の位置。

*最後*の \
コピーする要素範囲を超える最初の要素の位置。

*IList* \
要素のコピー元の initializer_list。

### <a name="remarks"></a>Remarks

すべてのコンストラクターは、アロケーター オブジェクトの型を格納します。このオブジェクトは set のメモリ ストレージを管理し、後で [get_allocator](#get_allocator) を呼び出して取得することができます。 代替アロケーターの代わりに使用されるクラス宣言やプリプロセス マクロでは、アロケーターのパラメーターが省略される場合があります。

すべてのコンストラクターは、それぞれの set を初期化します。

すべてのコンストラクターは `Traits` 型の関数オブジェクトを格納します。このオブジェクトは、セットのキーの順序を確立するために使用され、後で[key_comp](#key_comp)を呼び出すことによって取得することができます。

最初の 3 つのコンストラクターは、空の初期 set を指定します。2 番目のコンストラクターは要素の順序を確立するために使用する比較関数の型 (`comp`) を指定し、3 番目のコンストラクターは使用するアロケーターの型 (`al`) を明示的に指定します。 キーワード **explicit** は、特定の種類の自動型変換が実行されないようにします。

4 番目のコンストラクターは、set `right` のコピーを指定します。

次の 3 つのコンストラクターは、initializer_list を使用して要素を指定します。

次の3つのコンストラクターは、セットの範囲 [`first`、`last`) をコピーします。このとき、下では、クラス `Traits` および**アロケーター**の比較関数の型を指定します。

8 番目のコンストラクターは、`right` を移動することによって、set のコピーを指定します。

### <a name="example"></a>例

```cpp
// set_set.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main()
{
    using namespace std;

    // Create an empty set s0 of key type integer
    set <int> s0;

    // Create an empty set s1 with the key comparison
    // function of less than, then insert 4 elements
    set <int, less<int> > s1;
    s1.insert(10);
    s1.insert(20);
    s1.insert(30);
    s1.insert(40);

    // Create an empty set s2 with the key comparison
    // function of less than, then insert 2 elements
    set <int, less<int> > s2;
    s2.insert(10);
    s2.insert(20);

    // Create a set s3 with the
    // allocator of set s1
    set <int>::allocator_type s1_Alloc;
    s1_Alloc = s1.get_allocator();
    set <int> s3(less<int>(), s1_Alloc);
    s3.insert(30);

    // Create a copy, set s4, of set s1
    set <int> s4(s1);

    // Create a set s5 by copying the range s1[ first,  last)
    set <int>::const_iterator s1_bcIter, s1_ecIter;
    s1_bcIter = s1.begin();
    s1_ecIter = s1.begin();
    s1_ecIter++;
    s1_ecIter++;
    set <int> s5(s1_bcIter, s1_ecIter);

    // Create a set s6 by copying the range s4[ first,  last)
    // and with the allocator of set s2
    set <int>::allocator_type s2_Alloc;
    s2_Alloc = s2.get_allocator();
    set <int> s6(s4.begin(), ++s4.begin(), less<int>(), s2_Alloc);

    cout << "s1 =";
    for (auto i : s1)
        cout << " " << i;
    cout << endl;

    cout << "s2 = " << *s2.begin() << " " << *++s2.begin() << endl;

    cout << "s3 =";
    for (auto i : s3)
        cout << " " << i;
    cout << endl;

    cout << "s4 =";
    for (auto i : s4)
        cout << " " << i;
    cout << endl;

    cout << "s5 =";
    for (auto i : s5)
        cout << " " << i;
    cout << endl;

    cout << "s6 =";
    for (auto i : s6)
        cout << " " << i;
    cout << endl;

    // Create a set by moving s5
    set<int> s7(move(s5));
    cout << "s7 =";
    for (auto i : s7)
        cout << " " << i;
    cout << endl;

    // Create a set with an initializer_list
    cout << "s8 =";
    set<int> s8{ { 1, 2, 3, 4 } };
    for (auto i : s8)
        cout << " " << i;
    cout << endl;

    cout << "s9 =";
    set<int> s9{ { 5, 6, 7, 8 }, less<int>() };
    for (auto i : s9)
        cout << " " << i;
    cout << endl;

    cout << "s10 =";
    set<int> s10{ { 10, 20, 30, 40 }, less<int>(), s9.get_allocator() };
    for (auto i : s10)
        cout << " " << i;
    cout << endl;
}
```

```Output
s1 = 10 20 30 40s2 = 10 20s3 = 30s4 = 10 20 30 40s5 = 10 20s6 = 10s7 = 10 20s8 = 1 2 3 4s9 = 5 6 7 8s10 = 10 20 30 40
```

## <a name="size"></a>幅

セット内の要素数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

set の現在の長さ。

### <a name="example"></a>例

```cpp
// set_size.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: size_type i;

   s1.insert( 1 );
   i = s1.size( );
   cout << "The set length is " << i << "." << endl;

   s1.insert( 2 );
   i = s1.size( );
   cout << "The set length is now " << i << "." << endl;
}
```

```Output
The set length is 1.
The set length is now 2.
```

## <a name="size_type"></a>size_type

set 内の要素の数を表すことができる符号なし整数型。

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>例

`size_type` の宣言方法や使用方法の例については、[size](#size) の例をご覧ください。

## <a name="swap"></a>フォト

2 つの set の要素を交換します。

```cpp
void swap(
    set<Key, Traits, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*右*\
ターゲットの set と交換する要素を提供する引数の set。

### <a name="remarks"></a>Remarks

このメンバー関数が、要素を交換する 2 つの set において要素を指定している参照、ポインター、反復子を無効化することはありません。

### <a name="example"></a>例

```cpp
// set_swap.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1, s2, s3;
   set <int>::iterator s1_Iter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );
   s2.insert( 100 );
   s2.insert( 200 );
   s3.insert( 300 );

   cout << "The original set s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   s1.swap( s2 );

   cout << "After swapping with s2, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( s1, s3 );

   cout << "After swapping with s3, list s1 is:";
   for ( s1_Iter = s1.begin( ); s1_Iter != s1.end( ); s1_Iter++ )
      cout << " " << *s1_Iter;
   cout   << "." << endl;
}
```

```Output
The original set s1 is: 10 20 30.
After swapping with s2, list s1 is: 100 200.
After swapping with s3, list s1 is: 300.
```

## <a name="upper_bound"></a>upper_bound

指定したキーよりも大きいキーを持つ、set 内の最初の要素を指す反復子を返します。

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の set 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

引数キーより大きいキーを持つ set 内の要素の位置を指す、またはキーの一致が検出されない場合は、set 内の最後の要素の次の位置を指す、`iterator` または `const_iterator`。

### <a name="example"></a>例

```cpp
// set_upper_bound.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int> :: const_iterator s1_AcIter, s1_RcIter;

   s1.insert( 10 );
   s1.insert( 20 );
   s1.insert( 30 );

   s1_RcIter = s1.upper_bound( 20 );
   cout << "The first element of set s1 with a key greater "
        << "than 20 is: " << *s1_RcIter << "." << endl;

   s1_RcIter = s1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( s1_RcIter == s1.end( ) )
      cout << "The set s1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of set s1 with a key > 40 is: "
           << *s1_RcIter << "." << endl;

   // The element at a specific location in the set can be found
   // by using a dereferenced iterator addressing the location
   s1_AcIter = s1.begin( );
   s1_RcIter = s1.upper_bound( *s1_AcIter );
   cout << "The first element of s1 with a key greater than"
        << endl << "that of the initial element of s1 is: "
        << *s1_RcIter << "." << endl;
}
```

```Output
The first element of set s1 with a key greater than 20 is: 30.
The set s1 doesn't have an element with a key greater than 30.
The first element of s1 with a key greater than
that of the initial element of s1 is: 20.
```

## <a name="value_comp"></a>value_comp

set 内の要素の値を並べ替えるために使用される比較オブジェクトのコピーを取得します。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>戻り値

set が要素の並べ替えに使用する関数オブジェクトである、テンプレート パラメーター `Traits` を返します。

`Traits`の詳細については、[set クラス](../standard-library/set-class.md)のトピックのコメントに関するセクションを参照してください。

### <a name="remarks"></a>Remarks

格納されているオブジェクトはメンバー関数を定義します。

**bool operator**(**const key &** `_xVal`、 **const key &** `_yVal`);

これは、並べ替え順で `_xVal` が `_yVal` に先行しかつ等しくない場合に **true** を返します。

[value_compare](#value_compare) および [key_compare](#key_compare) は両方ともテンプレート パラメーター `Traits` のシノニムです。 どちらも set および multiset クラスで使用でき、そこでは同一ですが、map および multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

```cpp
// set_value_comp.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;

   set <int, less<int> > s1;
   set <int, less<int> >::value_compare vc1 = s1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of s1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of s1."
           << endl;
   }

   set <int, greater<int> > s2;
   set<int, greater<int> >::value_compare vc2 = s2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of s2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of s2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of s1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of s2.
```

## <a name="value_compare"></a>value_compare

2 つの要素の値を比較して、set 内の要素の相対順序を決定できる関数オブジェクトを提供する型。

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Remarks

`value_compare` はテンプレート パラメーター `Traits` のシノニムです。

`Traits`の詳細については、[set クラス](../standard-library/set-class.md)のトピックのコメントに関するセクションを参照してください。

[Key_compare](#key_compare)と `value_compare` の両方がテンプレートパラメーター `Traits` のシノニムであることに注意してください。 どちらも set および multiset クラスで使用でき、そこでは同一ですが、map および multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

`value_compare` の宣言方法や使用方法の例については、[value_comp](#value_comp) の例をご覧ください。

## <a name="value_type"></a>value_type

値として、キャパシティ内で set の要素として格納されるオブジェクトを表す型です。

```cpp
typedef Key value_type;
```

### <a name="remarks"></a>Remarks

`value_type` はテンプレート パラメーター `Key` のシノニムです。

`Key` の詳細については、[set クラス](../standard-library/set-class.md)のトピックのコメントに関するセクションを参照してください。

[Key_type](#key_type)と `value_type` の両方がテンプレートパラメーター `Key` のシノニムであることに注意してください。 どちらも set および multiset クラスで使用でき、そこでは同一ですが、map および multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

```cpp
// set_value_type.cpp
// compile with: /EHsc
#include <set>
#include <iostream>

int main( )
{
   using namespace std;
   set <int> s1;
   set <int>::iterator s1_Iter;

   set <int>::value_type svt_Int;   // Declare value_type
   svt_Int = 10;            // Initialize value_type

   set <int> :: key_type skt_Int;   // Declare key_type
   skt_Int = 20;             // Initialize key_type

   s1.insert( svt_Int );         // Insert value into s1
   s1.insert( skt_Int );         // Insert key into s1

   // A set accepts key_types or value_types as elements
   cout << "The set has elements:";
   for ( s1_Iter = s1.begin( ) ; s1_Iter != s1.end( ); s1_Iter++)
      cout << " " << *s1_Iter;
   cout << "." << endl;
}
```

```Output
The set has elements: 10 20.
```
