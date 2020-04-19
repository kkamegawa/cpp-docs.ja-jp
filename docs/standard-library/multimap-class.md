---
title: multimap クラス
ms.date: 10/18/2018
f1_keywords:
- map/std::multimap
- map/std::multimap::allocator_type
- map/std::multimap::const_iterator
- map/std::multimap::const_pointer
- map/std::multimap::const_reference
- map/std::multimap::const_reverse_iterator
- map/std::multimap::difference_type
- map/std::multimap::iterator
- map/std::multimap::key_compare
- map/std::multimap::key_type
- map/std::multimap::mapped_type
- map/std::multimap::pointer
- map/std::multimap::reference
- map/std::multimap::reverse_iterator
- map/std::multimap::size_type
- map/std::multimap::value_type
- map/std::multimap::begin
- map/std::multimap::cbegin
- map/std::multimap::cend
- map/std::multimap::clear
- map/std::multimap::count
- map/std::multimap::crbegin
- map/std::multimap::crend
- map/std::multimap::emplace
- map/std::multimap::emplace_hint
- map/std::multimap::empty
- map/std::multimap::end
- map/std::multimap::equal_range
- map/std::multimap::erase
- map/std::multimap::find
- map/std::multimap::get_allocator
- map/std::multimap::insert
- map/std::multimap::key_comp
- map/std::multimap::lower_bound
- map/std::multimap::max_size
- map/std::multimap::rbegin
- map/std::multimap::rend
- map/std::multimap::size
- map/std::multimap::swap
- map/std::multimap::upper_bound
- map/std::multimap::value_comp
helpviewer_keywords:
- std::multimap [C++]
- std::multimap [C++], allocator_type
- std::multimap [C++], const_iterator
- std::multimap [C++], const_pointer
- std::multimap [C++], const_reference
- std::multimap [C++], const_reverse_iterator
- std::multimap [C++], difference_type
- std::multimap [C++], iterator
- std::multimap [C++], key_compare
- std::multimap [C++], key_type
- std::multimap [C++], mapped_type
- std::multimap [C++], pointer
- std::multimap [C++], reference
- std::multimap [C++], reverse_iterator
- std::multimap [C++], size_type
- std::multimap [C++], value_type
- std::multimap [C++], begin
- std::multimap [C++], cbegin
- std::multimap [C++], cend
- std::multimap [C++], clear
- std::multimap [C++], count
- std::multimap [C++], crbegin
- std::multimap [C++], crend
- std::multimap [C++], emplace
- std::multimap [C++], emplace_hint
- std::multimap [C++], empty
- std::multimap [C++], end
- std::multimap [C++], equal_range
- std::multimap [C++], erase
- std::multimap [C++], find
- std::multimap [C++], get_allocator
- std::multimap [C++], insert
- std::multimap [C++], key_comp
- std::multimap [C++], lower_bound
- std::multimap [C++], max_size
- std::multimap [C++], rbegin
- std::multimap [C++], rend
- std::multimap [C++], size
- std::multimap [C++], swap
- std::multimap [C++], upper_bound
- std::multimap [C++], value_comp
ms.assetid: 8796ae05-37c4-475a-9e61-75fde9d4a463
ms.openlocfilehash: a4b066bf1620f8aaca1b0fc581348c73d5255591
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687648"
---
# <a name="multimap-class"></a>multimap クラス

C++ 標準ライブラリの multimap クラスは、各要素がデータ値と並べ替えキーのペアであるコレクションのデータを格納および取得するために使用されます。 キーの値は一意である必要がなく、データを自動的に並べ替えるために使用されます。 multimap の要素の値 (関連するキー値ではありません) は、直接変更できます。 この場合、変更前の要素に関連付けられていたキー値を削除し、新しい要素に関連付けられる新しいキー値を挿入する必要があります。

## <a name="syntax"></a>構文

```cpp
template <class Key,
    class Type,
    class Traits=less <Key>,
    class Allocator=allocator <pair  <const Key, Type>>>
class multimap;
```

### <a name="parameters"></a>パラメーター

*キー* \
multimap に格納されるキーのデータ型。

*型*\
multimap に格納される要素のデータ型。

*特徴*\
2 つの要素の値を並べ替えキーとして比較して、multimap 内の要素の相対順序を決定できる関数オブジェクトを提供する型。 二項述語 `less<Key>` が既定値です。

C++ 14 では、型パラメーターを使用せずに `std::less<>` 述語または `std::greater<>` 述語を指定することで、異種ルックアップを有効にすることができます。 詳細については、「[連想コンテナーの異種ルックアップ](../standard-library/stl-containers.md#heterogeneous-lookup-in-associative-containers-c14)」をご覧ください。

*アロケーター* \
メモリの map の割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクトを表す型。 この引数は省略可能であり、既定値は `allocator<pair <const Key, Type> >` です。

## <a name="remarks"></a>Remarks

C++ 標準ライブラリ multimap クラスには下記の特徴があります。

- hash_map は連想コンテナーであり、関連付けられたキー値に基づいて要素の値を効率的に取得できるようにする可変サイズのコンテナーとして機能します。

- 反転することができます。これは、要素にアクセスするための双方向反復子が用意されているためです。

- 並べ替えが実行されます。これは、指定した比較関数に従ってコンテナー内のキー値によって要素に順序が設定されるためです。

- 複数対応です。要素は一意のキーを持つ必要がないので、関連する多くの要素データ値を 1 つのキー値が持つことができるためです。

- ペアを保持する連想コンテナーです。これは、要素のデータ値とキー値が分かれているためです。

- クラステンプレート。提供される機能はジェネリックであり、要素またはキーとして含まれる特定のデータ型には依存しません。 要素やキーに使用されているデータ型は、クラス テンプレートで比較関数やアロケーターと共にパラメーターとして指定されます。

map クラスに用意されている反復子は双方向反復子ですが、クラス メンバー関数 [insert](#insert) と [multimap](#multimap) には、弱い入力反復子をテンプレート パラメーターとして取得するバージョンがあります。この反復子の機能に関する要件は、双方向反復子のクラスで保証されている要件よりも低くなっています。 これらの反復子の機能に差異があるのは、反復子の概念が異なっているためです。 反復子の各概念には、反復子独自の一連の要件が含まれています。また、それらの要件を使用するアルゴリズムでは、反復子の種類ごとに指定されている要件に対して、前提を絞り込む必要があります。 たとえば、一部のオブジェクトを参照するために入力反復子が逆参照される可能性があることを前提とする場合があります。さらに、シーケンス内にある次の反復子に対して逆参照が増加する可能性があることを前提とする場合もあります。 このことは、最小限実施することですが、クラスのメンバー関数のコンテキストに含まれる反復子の範囲 `[First, Last)` について明確にすることも重要です。

一般的に、コンテナー型の選択は、アプリケーションにおいて必要な検索および挿入の種類に基づいている必要があります。 連想コンテナーは、検索、挿入、削除の各操作用に最適化されています。 これらの操作を明示的にサポートするメンバー関数は効率的であり、処理時間は平均的にコンテナー内にある要素の数の対数に比例します。 要素を挿入しても反復子の有効性は失われません。また、要素を削除した場合は、削除された要素を具体的に指す反復子だけが無効化されます。

multimap は、値とキーを関連付ける条件をアプリケーションが満たしている場合、最適な連想コンテナーです。 この種類の構造体のモデルとなるのは、キー ワードとそれに関連する文字列値 (たとえば定義) の順序付きリストです。キー ワードは常に一意に定義されるわけではありません。 そうではなくて、キーワードが一意に定義され、キーが一意になる場合は、map が最適なコンテナーです。 また、キーワードのリストだけが格納される場合は、set が適切なコンテナーとなります。 キーワードを複数設定できる場合は、multiset が適切なコンテナー構造体となります。

multimap では、[key_compare](#key_compare) 型の格納されている関数オブジェクトを呼び出すことによって、multimap が制御するシーケンスを並べ替えます。 この格納されているオブジェクトは比較関数であり、メンバー関数 [key_comp](#key_comp) を呼び出すことによってアクセスできます。 通常、要素は、この順序を確立するために小なり比較だけを実行できる必要があります。これにより、2 つの要素が指定されたときに、それらの要素が等しいか (どちらか一方が小さくはない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 テクニカル ノートでは、比較関数は、数学上の標準的な意味で厳密弱順序を発生させる二項述語であると示されています。 二項述語 `f(x,y)` は、2 つの引数オブジェクト (`x` および `y`) と戻り値 (true または false) を持つ関数オブジェクトです。 set に適用される順序付けは、二項述語が非再帰、反対称、推移的であり、等価性が推移的である (2 つのオブジェクト `x` と `y` が、`f(x,y)` と `f(y,x)` の両方が false の場合に等価になるように定義されている) 場合、厳密弱順序になります。 2 つのキーの等値に関する条件が等価性の条件よりも厳しく、優先される場合、順序付けは完全な順序付け (すべての要素が相互の値に基づいて並べ替えられる) となり、一致するそれぞれのキーを識別するのが難しくなります。

C++ 14 では、型パラメーターを使用せずに `std::less<>` 述語または `std::greater<>` 述語を指定することで、異種ルックアップを有効にすることができます。 詳細については、「[連想コンテナーの異種ルックアップ](../standard-library/stl-containers.md#sequence_containers)」をご覧ください。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[multimap](#multimap)|空の `multimap`、または他の `multimap` の全体または一部のコピーである hash_multiset を構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[allocator_type](#allocator_type)|`allocator` オブジェクトの `multimap` クラスを表す型。|
|[const_iterator](#const_iterator)|@No__t_1 内の**const**要素を読み取ることができる双方向反復子を提供する型。|
|[const_pointer](#const_pointer)|@No__t_1 内の**const**要素へのポインターを提供する型。|
|[const_reference](#const_reference)|読み取りと**const**操作の実行のために `multimap` に格納されている**const**要素への参照を提供する型。|
|[const_reverse_iterator](#const_reverse_iterator)|@No__t_1 内の任意の**const**要素を読み取ることができる双方向反復子を提供する型。|
|[difference_type](#difference_type)|`multimap` の要素の数を、反復子が指す要素の範囲に基づいて表すために使用できる符号付き整数型。|
|[Iterator](#iterator)|同じ `multimap` 内の要素を参照する 2 つの反復子の違いを提供する型。|
|[key_compare](#key_compare)|2 つの並べ替えキーを比較して、`multimap` 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。|
|[key_type](#key_type)|`multimap` の各要素の一部である並べ替えキー オブジェクトを表す型。|
|[mapped_type](#mapped_type)|`multimap` に格納されているデータ型を表す型。|
|[pointer](#pointer)|@No__t_1 内の**const**要素へのポインターを提供する型。|
|[reference](#reference)|`multimap` に格納されている要素への参照を提供する型。|
|[reverse_iterator](#reverse_iterator)|反転された `multimap` 内の 1 つの要素を読み取り、または変更できる双方向反復子を提供する型。|
|[size_type](#size_type)|@No__t_1 内の**const**要素へのポインターを提供する符号なし整数型。|
|[value_type](#value_type)|2 つの要素を並べ替えキーとして比較して、`multimap` 内の要素の相対順序を決定できる関数オブジェクトを提供する型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[begin](#begin)|`multimap` 内の最初の要素を指す反復子を返します。|
|[cbegin](#cbegin)|`multimap` 内の最初の要素を指す定数反復子を返します。|
|[cend](#cend)|`multimap` 内の最後の要素の次の位置を指す定数反復子を返します。|
|[clear](#clear)|`multimap` のすべての要素を消去します。|
|[count](#count)|パラメーター指定したキーに一致するキーを持つ、`multimap` 内の要素の数を返します。|
|[crbegin](#crbegin)|反転された `multimap` 内の最初の要素を指す定数反復子を返します。|
|[crend](#crend)|反転された `multimap` 内の最後の要素の次の位置を指す定数反復子を返します。|
|[emplace](#emplace)|インプレースで構築された要素を `multimap` に挿入します。|
|[emplace_hint](#emplace_hint)|インプレースで構築された要素を、配置ヒントと共に `multimap` に挿入します。|
|[empty](#empty)|`multimap` が空かどうかをテストします。|
|[end](#end)|`multimap` 内の最後の要素の次の位置を指す反復子を返します。|
|[equal_range](#equal_range)|要素のキーが指定された値と一致する要素の範囲を検索します。|
|[erase](#erase)|`multimap` 内の要素または要素の範囲を指定した位置から削除するか、または指定したキーと一致する要素を削除します。|
|[find](#find)|指定したキーと同じキーを持つ、`multimap` 内の要素の最初の位置を指す反復子を返します。|
|[get_allocator](#get_allocator)|`allocator` の構築に使用される `multimap` オブジェクトのコピーを返します。|
|[insert](#insert)|`multimap` に要素または要素範囲を挿入します。|
|[key_comp](#key_comp)|`multimap` 内のキーを並べ替えるために使用される比較オブジェクトのコピーを取得します。|
|[lower_bound](#lower_bound)|指定したキー以上のキーを持つ、`multimap` 内の最初の要素を指す反復子を返します。|
|[max_size](#max_size)|`multimap` の最大長を返します。|
|[rbegin](#rbegin)|反転された `multimap` 内の最初の要素を指す反復子を返します。|
|[rend](#rend)|反転された `multimap` 内の最後の要素の次の位置を指す反復子を返します。|
|[size](#size)|`multimap` 内の要素数を返します。|
|[swap](#swap)|2 つの `multimap` の要素を交換します。|
|[upper_bound](#upper_bound)|指定したキーよりも大きいキーを持つ、`multimap` 内の最初の要素を指す反復子を返します。|
|[value_comp](#value_comp)|このメンバー関数は、キー値の比較によって `multimap` の要素の順序を決定する関数オブジェクトを返します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator=](#op_eq)|別の `multimap` のコピーで `multimap` の要素を置き換えます。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<map>

**名前空間:** std

(**key**, **value**) のペアは、`pair` 型のオブジェクトとして multimap に格納されます。 この pair クラスはヘッダー \<utility> を必要としますが、これは \<map> によって自動的にインクルードされます。

## <a name="allocator_type"></a>  multimap::allocator_type

multimap オブジェクトのアロケーター クラスを表す型。

```cpp
typedef Allocator allocator_type;
```

### <a name="example"></a>例

`allocator_type` の使用例については、[get_allocator](#get_allocator) の例をご覧ください。

## <a name="begin"></a>  multimap::begin

multimap の 1 つ目の要素を指す反復子を返します。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>戻り値

multimap 内の最初の要素、または空の multimap の次の位置を指す、双方向反復子。

### <a name="example"></a>例

```cpp
// multimap_begin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: const_iterator m1_cIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 0, 0 ) );
   m1.insert ( Int_Pair ( 1, 1 ) );
   m1.insert ( Int_Pair ( 2, 4 ) );

   m1_cIter = m1.begin ( );
   cout << "The first element of m1 is " << m1_cIter -> first << endl;

   m1_Iter = m1.begin ( );
   m1.erase ( m1_Iter );

   // The following 2 lines would err as the iterator is const
   // m1_cIter = m1.begin ( );
   // m1.erase ( m1_cIter );

   m1_cIter = m1.begin( );
   cout << "First element of m1 is now " << m1_cIter -> first << endl;
}
```

```Output
The first element of m1 is 0
First element of m1 is now 1
```

## <a name="cbegin"></a>  multimap::cbegin

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

## <a name="cend"></a>  multimap::cend

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

## <a name="clear"></a>  multimap::clear

multimap のすべての要素を消去します。

```cpp
void clear();
```

### <a name="example"></a>例

multimap::clear メンバー関数の使用例を次に示します。

```cpp
// multimap_clear.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap<int, int> m1;
   multimap<int, int>::size_type i;
   typedef pair<int, int> Int_Pair;

   m1.insert(Int_Pair(1, 1));
   m1.insert(Int_Pair(2, 4));

   i = m1.size();
   cout << "The size of the multimap is initially "
        << i << "." << endl;

   m1.clear();
   i = m1.size();
   cout << "The size of the multimap after clearing is "
        << i << "." << endl;
}
```

```Output
The size of the multimap is initially 2.
The size of the multimap after clearing is 0.
```

## <a name="const_iterator"></a>  multimap::const_iterator

multimap 内の **const** 要素を読み取ることができる双方向反復子を提供する型。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Remarks

`const_iterator` 型で要素の値を変更することはできません。

Multimap によって定義された `const_iterator` は、`pair<const Key, Type>` 型の[value_type](#value_type)のオブジェクトを指します。 キーの値はペアの 1 番目のメンバー、マップされた要素の値はペアの 2 番目のメンバーを介して取得できます。

Multimap 内の要素を指す `const_iterator` *cIter*を逆参照するには、 **->** 演算子を使用します。

要素のキーの値にアクセスするには、`cIter->first` を使用します。これは `(*cIter).first` と同じです。 要素のマップされた datum の値にアクセスするには、`cIter->second` を使用します。これは `(*cIter).second` と同じです。

### <a name="example"></a>例

`const_iterator` の使用例については、[begin](#begin) の例をご覧ください。

## <a name="const_pointer"></a>  multimap::const_pointer

multimap 内の **const** 要素へのポインターを提供する型。

```cpp
typedef typename allocator_type::const_pointer const_pointer;
```

### <a name="remarks"></a>Remarks

`const_pointer` 型で要素の値を変更することはできません。

ほとんどの場合、multimap オブジェクト内の要素にアクセスするには[反復子](#iterator)を使用する必要があります。

## <a name="const_reference"></a>  multimap::const_reference

**const** 操作の読み取りと実行のために、multimap に格納された **const** 要素への参照を提供する型。

```cpp
typedef typename allocator_type::const_reference const_reference;
```

### <a name="example"></a>例

```cpp
// multimap_const_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of the first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of the first element in the multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the multimap is 1.
The data value of the first element in the multimap is 10.
```

## <a name="const_reverse_iterator"></a>  multimap::const_reverse_iterator

multimap 内の任意の **const** 要素を読み取ることができる双方向反復子を提供する型。

```cpp
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;
```

### <a name="remarks"></a>Remarks

`const_reverse_iterator` 型は要素の値を変更できず、逆の順序で multimap を反復処理するために使用します。

Multimap によって定義された `const_reverse_iterator` は、`pair<const Key, Type>` 型の[value_type](#value_type)のオブジェクトを指します。 キーの値はペアの 1 番目のメンバー、マップされた要素の値はペアの 2 番目のメンバーを介して取得できます。

Multimap 内の要素を指す `const_reverse_iterator` *crIter*を逆参照するには、 **->** 演算子を使用します。

要素のキーの値にアクセスするには、`crIter->first` を使用します。これは `(*crIter).first` と同じです。 要素のマップされた datum の値にアクセスするには、`crIter->second` を使用します。これは `(*crIter).first` と同じです。

### <a name="example"></a>例

`const_reverse_iterator` の宣言方法や使用方法の例については、[rend](#rend) の例をご覧ください。

## <a name="count"></a>  multimap::count

パラメーター指定されたキーと一致するキーを持つ multimap 内の要素の数を返します。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
照合される multimap の要素のキー。

### <a name="return-value"></a>戻り値

パラメーター キーと一致する並べ替えキーを持つ要素の数。一致するキーを持つ要素が multimap に含まれていない場合は 0 です。

### <a name="remarks"></a>Remarks

メンバー関数は、

\[ lower_bound (*キー*)、upper_bound (*キー*))

キー値*キー*を持つ。

### <a name="example"></a>例

multimap::count メンバー関数の使用例を次に示します。

```cpp
// multimap_count.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
    using namespace std;
    multimap<int, int> m1;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    m1.insert(Int_Pair(2, 1));
    m1.insert(Int_Pair(1, 4));
    m1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in multimap,
    // so duplicates are allowed and counted
    i = m1.count(1);
    cout << "The number of elements in m1 with a sort key of 1 is: "
         << i << "." << endl;

    i = m1.count(2);
    cout << "The number of elements in m1 with a sort key of 2 is: "
         << i << "." << endl;

    i = m1.count(3);
    cout << "The number of elements in m1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in m1 with a sort key of 1 is: 2.
The number of elements in m1 with a sort key of 2 is: 2.
The number of elements in m1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  multimap::crbegin

反転された multimap 内の最初の要素を指す定数反復子を返します。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>戻り値

反転された [multimap](../standard-library/multimap-class.md) 内の最初の要素を示す、または反転されていない `multimap` 内の最後の要素だったものを示す定数逆順双方向反復子。

### <a name="remarks"></a>Remarks

`crbegin` は、[begin](#begin) が `multimap` で使用されるのと同様に、反転された `multimap` で使用されます。

戻り値が `crbegin` の場合、`multimap` オブジェクトは変更できません。

`crbegin` を使用して、`multimap` 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// multimap_crbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
```

## <a name="crend"></a>  multimap::crend

反転された multimap 内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>戻り値

反転された [multimap](../standard-library/multimap-class.md) 内の最後の要素の次の場所 (反転されていない `multimap` 内の最初の要素の前の場所) を指す定数逆順双方向反復子。

### <a name="remarks"></a>Remarks

`crend` は、[multimap::end](#end) が `multimap` で使用されるのと同様に、反転された `multimap` で使用されます。

戻り値が `crend` の場合、`multimap` オブジェクトは変更できません。

`crend` を使用して、逆順反復子が `multimap` の末尾に達したかどうかをテストできます。

`crend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// multimap_crend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_crIter = m1.crend( );
   m1_crIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
```

## <a name="difference_type"></a>  multimap::difference_type

反復子が指す要素の範囲内にある multimap の要素の数を表すのに使用できる符号付き整数型。

```cpp
typedef typename allocator_type::difference_type difference_type;
```

### <a name="remarks"></a>Remarks

`difference_type` は、コンテナーの反復子を減算またはインクリメントするときに返される型です。 @No__t_0 は、通常、反復子 `first` と `last` 間の [*first*, *last*) の範囲内の要素の数を表すために使用されます。には、`first` が指す要素との要素の範囲が含まれます。`last` によってポイントされる要素。

`difference_type` は、入力反復子の要件を満たすすべての反復子 (set などの反転可能なコンテナーによってサポートされる双方向反復子のクラスを含む) に対して使用できますが、反復子間の減算は、vector などのランダム アクセス コンテナーによって提供される、ランダム アクセス反復子によってのみサポートされます。

### <a name="example"></a>例

```cpp
// multimap_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <map>
#include <algorithm>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );

   // The following will insert as multimap keys are not unique
   m1.insert ( Int_Pair ( 2, 30 ) );

   multimap <int, int>::iterator m1_Iter, m1_bIter, m1_eIter;
   m1_bIter = m1.begin( );
   m1_eIter = m1.end( );

   // Count the number of elements in a multimap
   multimap <int, int>::difference_type  df_count = 0;
   m1_Iter = m1.begin( );
   while ( m1_Iter != m1_eIter )
   {
      df_count++;
      m1_Iter++;
   }

   cout << "The number of elements in the multimap m1 is: "
        << df_count << "." << endl;
}
```

```Output
The number of elements in the multimap m1 is: 4.
```

## <a name="emplace"></a>  multimap::emplace

インプレースで構築された (コピーまたは移動操作が実行されない) 要素を挿入します。

```cpp
template <class... Args>
iterator emplace(Args&&... args);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*value*|multimap に挿入される要素を構築するために転送される引数。|

### <a name="return-value"></a>戻り値

新しく挿入される要素を指す反復子。

### <a name="remarks"></a>Remarks

この関数では、コンテナー要素を指す参照は無効になりません。ただし、コンテナーを指すすべての反復子が無効になる場合があります。

挿入時に例外がスローされた場合、コンテナーは変更されず、再度例外がスローされます。

要素の [value_type](../standard-library/map-class.md#value_type) はペアです。最初のコンポーネントがキー値と等しく、2 番目のコンポーネントが要素のデータ値と等しくなるよう、要素の値が順序付けされたペアになります。

### <a name="example"></a>例

```cpp
// multimap_emplace.cpp
// compile with: /EHsc
#include <map>
#include <string>
#include <iostream>

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: " << endl;

    for (const auto& p : m) {
        cout << "(" << p.first <<  "," << p.second << ") ";
    }

    cout << endl;
}

int main()
{
    multimap<string, string> m1;

    m1.emplace("Anna", "Accounting");
    m1.emplace("Bob", "Accounting");
    m1.emplace("Carmine", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;

    m1.emplace("Bob", "Engineering");

    cout << "multimap modified, now contains ";
    print(m1);
    cout << endl;
}
```

## <a name="emplace_hint"></a>  multimap::emplace_hint

インプレースで構築された (コピーまたは移動操作が実行されない) 要素を、配置ヒントと一緒に挿入します。

```cpp
template <class... Args>
iterator emplace_hint(
    const_iterator where,
    Args&&... args);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*value*|multimap に挿入される要素を構築するために転送される引数。|
|*where*|正しい挿入ポイントの検索を開始する場所 (その位置がの直前にある*場合、挿入*は、対数時間ではなく償却定数時間で実行できます)。|

### <a name="return-value"></a>戻り値

新しく挿入される要素を指す反復子。

### <a name="remarks"></a>Remarks

この関数では、コンテナー要素を指す参照は無効になりません。ただし、コンテナーを指すすべての反復子が無効になる場合があります。

配置の実行中、例外がスローされるとコンテナーの状態は変更されません。

要素の [value_type](../standard-library/map-class.md#value_type) はペアです。最初のコンポーネントがキー値と等しく、2 番目のコンポーネントが要素のデータ値と等しくなるよう、要素の値が順序付けされたペアになります。

コード例については、「[map::emplace_hint](../standard-library/map-class.md#emplace_hint)」をご覧ください。

## <a name="empty"></a>  multimap::empty

multimap が空かどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

multimap が空の場合は **true**、multimap が空ではない場合は **false**。

### <a name="example"></a>例

```cpp
// multimap_empty.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2;

   typedef pair <int, int> Int_Pair;
   m1.insert ( Int_Pair ( 1, 1 ) );

   if ( m1.empty( ) )
      cout << "The multimap m1 is empty." << endl;
   else
      cout << "The multimap m1 is not empty." << endl;

   if ( m2.empty( ) )
      cout << "The multimap m2 is empty." << endl;
   else
      cout << "The multimap m2 is not empty." << endl;
}
```

```Output
The multimap m1 is not empty.
The multimap m2 is empty.
```

## <a name="end"></a>  multimap::end

末尾超え反復子を返します。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>戻り値

末尾超え反復子。 multimap が空の場合は、`multimap::end() == multimap::begin()`。

### <a name="remarks"></a>Remarks

**end** は、反復子が multimap の末尾を超えたかどうかをテストするために使用します。

**end** によって返された値は逆参照しないでください。

コード例については、「[multimap::find](#find)」をご覧ください。

## <a name="equal_range"></a>  multimap::equal_range

要素のキーが指定された値と一致する要素の範囲を検索します。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の multimap 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

1 番目がそのキーの [lower_bound](#lower_bound)、2 番目がそのキーの [upper_bound](#upper_bound) である、反復子のペア。

メンバー関数によって返されるペア `pr` 最初の反復子にアクセスするには、`pr` を使用します。 **最初**に、下限の反復子を逆参照するには、\* (`pr` を使用します。 **最初**)。 メンバー関数によって返さ `pr` ペアの2番目の反復子にアクセスするには、`pr` を使用します。 **次**に、上限の反復子を逆参照するには、\* (`pr` を使用します。 **2 番目**)。

### <a name="example"></a>例

```cpp
// multimap_equal_range.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef multimap <int, int, less<int> > IntMMap;
   IntMMap m1;
   multimap <int, int> :: const_iterator m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = m1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the multimap m1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   m1_RcIter = m1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << m1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

   p2 = m1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == m1.end( ) ) && ( p2.second == m1.end( ) ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of multimap m1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the multimap m1 is: 20.
The upper bound of the element with a key of 2 in the multimap m1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The multimap m1 doesn't have an element with a key less than 4.
```

## <a name="erase"></a>  multimap::erase

マルチマップ内の要素または要素の範囲を指定した位置から削除するか、または指定したキーと一致する要素を削除します。

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
削除する要素のキー。

### <a name="return-value"></a>戻り値

最初の 2 つのメンバー関数の場合は、削除された要素の後の最初の残存要素、またはマップの最後の要素 (このような要素が存在しない場合) を指定する双方向反復子。

3 番目のメンバー関数の場合は、マルチマップから削除された要素の数を返します。

### <a name="remarks"></a>Remarks

コード例については、「[map::erase](../standard-library/map-class.md#erase)」をご覧ください。

## <a name="find"></a>  multimap::find

指定したキーと等価のキーを持つ、multimap 内の要素の最初の位置を参照する反復子を返します。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の multimap 内の要素の並べ替えキーによって照合されるキー値。

### <a name="return-value"></a>戻り値

指定したキーを持つ要素の位置を参照する反復子。キーの一致が検出されない場合は、multimap 内の最後の要素の次の位置 (`multimap::end()`)。

### <a name="remarks"></a>Remarks

このメンバー関数は、小なり比較関係に基づいて順序を推論する二項述語に即して、並べ替えキーが引数キーと等価である multimap 内の要素を参照する反復子を返します。

`find` の戻り値が `const_iterator` に割り当てられている場合、multimap オブジェクトは変更できません。 @No__t_0 の戻り値が `iterator` に割り当てられている場合は、multimap オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// compile with: /EHsc /W4 /MTd
#include <map>
#include <iostream>
#include <vector>
#include <string>
#include <utility>  // make_pair()

using namespace std;

template <typename A, typename B> void print_elem(const pair<A, B>& p) {
    cout << "(" << p.first << ", " << p.second << ") ";
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
    multimap<int, string> m1({ { 40, "Zr" }, { 45, "Rh" } });
    cout << "The starting multimap m1 is (key, value):" << endl;
    print_collection(m1);

    vector<pair<int, string>> v;
    v.push_back(make_pair(43, "Tc"));
    v.push_back(make_pair(41, "Nb"));
    v.push_back(make_pair(46, "Pd"));
    v.push_back(make_pair(42, "Mo"));
    v.push_back(make_pair(44, "Ru"));
    v.push_back(make_pair(44, "Ru")); // attempt a duplicate

    cout << "Inserting the following vector data into m1:" << endl;
    print_collection(v);

    m1.insert(v.begin(), v.end());

    cout << "The modified multimap m1 is (key, value):" << endl;
    print_collection(m1);
    cout << endl;
    findit(m1, 45);
    findit(m1, 6);
}
```

## <a name="get_allocator"></a>  multimap::get_allocator

multimap の構築に使用されるアロケーター オブジェクトのコピーを返します。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>戻り値

multimap で使用されるアロケーター。

### <a name="remarks"></a>Remarks

multimap クラスのアロケーターは、クラスがどのようにストレージを管理するかを指定します。 C++ 標準ライブラリ コンテナー クラスで提供される既定のアロケーターは、ほとんどのプログラミング要件に対応しています。 独自のアロケーター クラスを作成して使用することは、C++ における高度な作業の 1 つです。

### <a name="example"></a>例

```cpp
// multimap_get_allocator.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int>::allocator_type m1_Alloc;
   multimap <int, int>::allocator_type m2_Alloc;
   multimap <int, double>::allocator_type m3_Alloc;
   multimap <int, int>::allocator_type m4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   multimap <int, int> m1;
   multimap <int, int, allocator<int> > m2;
   multimap <int, double, allocator<double> > m3;

   m1_Alloc = m1.get_allocator( );
   m2_Alloc = m2.get_allocator( );
   m3_Alloc = m3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << m2.max_size( ) << ".\n" << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << m3.max_size( ) <<  ".\n" << endl;

   // The following line creates a multimap m4
   // with the allocator of multimap m1.
   map <int, int> m4( less<int>( ), m1_Alloc );

   m4_Alloc = m4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated via the other
   if( m1_Alloc == m4_Alloc )
   {
      cout << "The allocators are interchangeable."
           << endl;
   }
   else
   {
      cout << "The allocators are not interchangeable."
           << endl;
   }
}
```

## <a name="insert"></a>  multimap::insert

multimap に要素または要素範囲を挿入します。

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

|パラメーター|説明|
|-|-|
|*Val*|multimap に挿入される要素の値。|
|*Where*|正しい挿入ポイントの検索を開始する場所 (その位置がの直前にある*場合、挿入*は、対数時間ではなく償却定数時間で実行できます)。|
|*ValTy*|Map が[value_type](../standard-library/map-class.md#value_type)の要素を構築するために使用できる引数の型を指定し、引数として*Val*を完全に転送するテンプレートパラメーター。|
|*まずは*|コピーされる最初の要素の位置。|
|*前の*|コピーされる最後の要素の次の位置。|
|*InputIterator*|[入力反復子](../standard-library/input-iterator-tag-struct.md)の要件を満たすテンプレート関数の引数。この反復子は、[value_type](../standard-library/map-class.md#value_type) オブジェクトの構築に使用できる型の要素を指し示します。|
|*IList*|要素のコピー元の [initializer_list](../standard-library/initializer-list.md)。|

### <a name="return-value"></a>戻り値

単一要素の insert メンバー関数 (1) と (2) は、新しい要素が multimap に挿入された位置を指す反復子を返します。

単一要素とヒントのメンバー関数 (3) と (4) は、新しい要素が multimap に挿入された位置を指す反復子を返します。

### <a name="remarks"></a>Remarks

この関数では、ポインターや参照は無効になりません。ただし、コンテナーを指すすべての反復子が無効になる場合があります。

要素を 1 つだけ挿入するとき、例外がスローされるとコンテナーの状態は変更されません。 複数の要素を挿入するときに例外がスローされた場合、コンテナーの状態は未指定ですが、有効な状態になっています。

コンテナーの [value_type](../standard-library/map-class.md#value_type) はそのコンテナーに属する typedef であり、map の場合、`multimap<K, V>::value_type` は `pair<const K, V>` になります。 要素の値は順序付けされたペアになり、このペアの最初のコンポーネントはキー値と同じで、2 番目のコンポーネントは要素のデータ値と同じになります。

範囲のメンバー関数 (5) は、multimap に要素値のシーケンスを挿入します。このシーケンスは、`[First, Last)` の範囲の反復子によってアドレス指定された各要素に対応します。したがって、 *Last*は挿入されません。 コンテナーのメンバー関数 `end()` は、コンテナー内にある最後の要素の直後の位置を参照します。たとえば、ステートメント `m.insert(v.begin(), v.end());` は、`v` のすべての要素を `m` に挿入します。

初期化子リストのメンバー関数 (6) は、[initializer_list](../standard-library/initializer-list.md) を使用して map に要素をコピーします。

インプレースで構築された (つまり、コピーまたは移動操作が実行されない) 要素の挿入については、「[multimap::emplace](#emplace)」および「[multimap::emplace_hint](#emplace_hint)」をご覧ください。

### <a name="example"></a>例

```cpp
// multimap_insert.cpp
// compile with: /EHsc
#include <map>
#include <iostream>
#include <string>
#include <vector>
#include <utility>  // make_pair()

using namespace std;

template <typename M> void print(const M& m) {
    cout << m.size() << " elements: ";

    for (const auto& p : m) {
        cout << "(" << p.first << ", " << p.second << ") ";
    }

    cout << endl;
}

int main()
{

    // insert single values
    multimap<int, int> m1;
    // call insert(const value_type&) version
    m1.insert({ 1, 10 });
    // call insert(ValTy&&) version
    m1.insert(make_pair(2, 20));

    cout << "The original key and mapped values of m1 are:" << endl;
    print(m1);

    // intentionally attempt a duplicate, single element
    m1.insert(make_pair(1, 111));

    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);

    // single element, with hint
    m1.insert(m1.end(), make_pair(3, 30));
    cout << "The modified key and mapped values of m1 are:" << endl;
    print(m1);
    cout << endl;

    // The templatized version inserting a jumbled range
    multimap<int, int> m2;
    vector<pair<int, int>> v;
    v.push_back(make_pair(43, 294));
    v.push_back(make_pair(41, 262));
    v.push_back(make_pair(45, 330));
    v.push_back(make_pair(42, 277));
    v.push_back(make_pair(44, 311));

    cout << "Inserting the following vector data into m2:" << endl;
    print(v);

    m2.insert(v.begin(), v.end());

    cout << "The modified key and mapped values of m2 are:" << endl;
    print(m2);
    cout << endl;

    // The templatized versions move-constructing elements
    multimap<int, string>  m3;
    pair<int, string> ip1(475, "blue"), ip2(510, "green");

    // single element
    m3.insert(move(ip1));
    cout << "After the first move insertion, m3 contains:" << endl;
    print(m3);

    // single element with hint
    m3.insert(m3.end(), move(ip2));
    cout << "After the second move insertion, m3 contains:" << endl;
    print(m3);
    cout << endl;

    multimap<int, int> m4;
    // Insert the elements from an initializer_list
    m4.insert({ { 4, 44 }, { 2, 22 }, { 3, 33 }, { 1, 11 }, { 5, 55 } });
    cout << "After initializer_list insertion, m4 contains:" << endl;
    print(m4);
    cout << endl;
}
```

## <a name="iterator"></a>  multimap::iterator

multimap 内の任意の要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Remarks

Multimap によって定義された `iterator` は、`pair<const Key, Type>` 型の[value_type](#value_type)のオブジェクトを指します。 キーの値はペアの 1 番目のメンバー、マップされた要素の値はペアの 2 番目のメンバーを介して取得できます。

Multimap 内の要素を指す `iterator` *Iter*を逆参照するには、 **->** 演算子を使用します。

要素のキーの値にアクセスするには、`Iter->first` を使用します。これは `(*Iter).first` と同じです。 要素のマップされた datum の値にアクセスするには、`Iter->second` を使用します。これは `(*Iter).second` と同じです。

@No__t_0 型を使用して、要素の値を変更できます。

### <a name="example"></a>例

`iterator` の宣言方法や使用方法の例については、[begin](#begin) の例をご覧ください。

## <a name="key_comp"></a>  multimap::key_comp

multimap 内のキーの並べ替えに使用する比較オブジェクトのコピーを取得します。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>戻り値

multimap が要素の並べ替えに使用する関数オブジェクトを返します。

### <a name="remarks"></a>Remarks

格納されているオブジェクトは以下のメンバー関数を定義します。

`bool operator( const Key& x, const Key& y);`

これは、並べ替え順で *x* が厳密に *y* に先行する場合に true を返します。

### <a name="example"></a>例

```cpp
// multimap_key_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::key_compare kc1 = m1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of m1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of m1."
           << endl;
   }

   multimap <int, int, greater<int> > m2;
   multimap <int, int, greater<int> >::key_compare kc2 = m2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of m2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of m2."
           << endl;
   }
}
```

```Output
kc1( 2,3 ) returns value of true, where kc1 is the function object of m1.
kc2( 2,3 ) returns value of false, where kc2 is the function object of m2.
```

## <a name="key_compare"></a>  multimap::key_compare

2 つの並べ替えキーを比較して、multimap 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Remarks

`key_compare` はテンプレート パラメーター `Traits` のシノニムです。

`Traits` の詳細については、[multimap クラス](../standard-library/multimap-class.md)のトピックをご覧ください。

### <a name="example"></a>例

`key_compare` の宣言方法や使用方法の例については、[key_comp](#key_comp) の例をご覧ください。

## <a name="key_type"></a>  multimap::key_type

multimap の各要素の一部である並べ替えキー オブジェクトを表す型。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Remarks

`key_type` はテンプレート パラメーター `Key` のシノニムです。

`Key` の詳細については、[multimap クラス](../standard-library/multimap-class.md)のトピックのコメントのセクションをご覧ください。

### <a name="example"></a>例

`key_type` の宣言方法や使用方法の例については、[value_type](#value_type) の例をご覧ください。

## <a name="lower_bound"></a>  multimap::lower_bound

指定したキー以上のキーを持つ、multimap 内の最初の要素を指す反復子を返します。

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の multimap 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

引数キー以上のキーを持つ multimap 内の要素の位置を指す、または、キーの一致が検出されない場合は multimap 内の最後の要素の次の位置を指す、反復子または `const_iterator`。

`lower_bound` の戻り値が `const_iterator` に割り当てられている場合、multimap オブジェクトは変更できません。 `lower_bound` の戻り値が**反復子**に割り当てられている場合、multimap オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// multimap_lower_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_RcIter = m1.lower_bound( 2 );
   cout << "The element of multimap m1 with a key of 2 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.lower_bound( 3 );
   cout << "The first element of multimap m1 with a key of 3 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
              << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
                << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.end( );
   m1_AcIter--;
   m1_RcIter = m1.lower_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key matching\n"
        << "that of the last element is: "
        << m1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( m1_RcIter == --m1.end( ) )
      cout << "This is the last element of multimap m1."
           << endl;
   else
      cout << "This is not the last element of multimap m1."
           << endl;
}
```

```Output
The element of multimap m1 with a key of 2 is: 20.
The first element of multimap m1 with a key of 3 is: 20.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key matching
that of the last element is: 20.
This is not the last element of multimap m1.
```

## <a name="mapped_type"></a>  multimap::mapped_type

multimap 内に格納されているデータ型を表す型。

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Remarks

`mapped_type` はテンプレート パラメーター `Type` のシノニムです。

`Type` の詳細については、[multimap クラス](../standard-library/multimap-class.md)のトピックをご覧ください。

### <a name="example"></a>例

`key_type` の宣言方法や使用方法の例については、[value_type](#value_type) の例をご覧ください。

## <a name="max_size"></a>  multimap::max_size

multimap の最大長を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

multimap の可能な最大長。

### <a name="example"></a>例

```cpp
// multimap_max_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: size_type i;

   i = m1.max_size( );
   cout << "The maximum possible length "
        << "of the multimap is " << i << "." << endl;
}
```

## <a name="multimap"></a>  multimap::multimap

空の multimap、または他の multimap の全体または一部のコピーである multimap を構築します。

```cpp
multimap();

explicit multimap(
    const Traits& Comp);

multimap(
    const Traits& Comp,
    const Allocator& Al);

map(
    const multimap& Right);

multimap(
    multimap&& Right);

multimap(
    initializer_list<value_type> IList);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp);

multimap(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
multimap(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*ウムアルクラ*|この multimap オブジェクトに使用するストレージ アロケーター クラス。既定では、Allocator です。|
|*コンペティション*|マップ内の要素の並べ替えに使用される、型 `constTraits` の比較関数。既定では `Traits` です。|
|*右*|構築される map のコピー元となる map。|
|*まずは*|コピーする要素範囲内の最初の要素の位置。|
|*前の*|コピーする要素範囲を超える最初の要素の位置。|
|*IList*|要素のコピー元の initializer_list。|

### <a name="remarks"></a>Remarks

すべてのコンストラクターは、アロケーター オブジェクトの型を格納します。このオブジェクトは multimap のメモリ ストレージを管理し、後で [get_allocator](#get_allocator) を呼び出して取得することができます。 代替アロケーターの代わりに使用されるクラス宣言やプリプロセス マクロでは、アロケーターのパラメーターが省略される場合があります。

すべてのコンストラクターは、それぞれの multimap を初期化します。

すべてのコンストラクターは、`Traits` 型の関数オブジェクトを格納します。このオブジェクトは multimap のキーの順序を確立するために使用され、後で [key_comp](#key_comp) を呼び出して取得することができます。

最初の3つのコンストラクターは、空の初期 multimap を指定します。2番目のコンストラクターは、要素の順序を確立するために使用する比較関数の型 (*Comp*) を指定し、3番目のコンストラクターはアロケーターの型 (*Al*) を明示的に指定します。用い. キーワード**explicit**では、特定の種類の自動型変換が抑制されます。

4番目のコンストラクターは、multimap*権限*のコピーを指定します。

5番目のコンストラクターは、*右*に移動して multimap のコピーを指定します。

6 番目、7 番目、8 番目のコンストラクターは、initializer_list のメンバーをコピーします。

次の 3 つのコンストラクターは、map の範囲 `[First, Last)` をコピーします。下のコンストラクターになるほど、より明確に `Traits` クラスの比較関数と Allocator の型が指定されています。

### <a name="example"></a>例

```cpp
// multimap_ctor.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    typedef pair <int, int> Int_Pair;

    // Create an empty multimap m0 of key type integer
    multimap <int, int> m0;

    // Create an empty multimap m1 with the key comparison
    // function of less than, then insert 4 elements
    multimap <int, int, less<int> > m1;
    m1.insert(Int_Pair(1, 10));
    m1.insert(Int_Pair(2, 20));
    m1.insert(Int_Pair(3, 30));
    m1.insert(Int_Pair(4, 40));

    // Create an empty multimap m2 with the key comparison
    // function of greater than, then insert 2 elements
    multimap <int, int, less<int> > m2;
    m2.insert(Int_Pair(1, 10));
    m2.insert(Int_Pair(2, 20));

    // Create a multimap m3 with the
    // allocator of multimap m1
    multimap <int, int>::allocator_type m1_Alloc;
    m1_Alloc = m1.get_allocator();
    multimap <int, int> m3(less<int>(), m1_Alloc);
    m3.insert(Int_Pair(3, 30));

    // Create a copy, multimap m4, of multimap m1
    multimap <int, int> m4(m1);

    // Create a multimap m5 by copying the range m1[ first,  last)
    multimap <int, int>::const_iterator m1_bcIter, m1_ecIter;
    m1_bcIter = m1.begin();
    m1_ecIter = m1.begin();
    m1_ecIter++;
    m1_ecIter++;
    multimap <int, int> m5(m1_bcIter, m1_ecIter);

    // Create a multimap m6 by copying the range m4[ first,  last)
    // and with the allocator of multimap m2
    multimap <int, int>::allocator_type m2_Alloc;
    m2_Alloc = m2.get_allocator();
    multimap <int, int> m6(m4.begin(), ++m4.begin(), less<int>(), m2_Alloc);

    cout << "m1 =";
    for (auto i : m1)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m2 =";
    for (auto i : m2)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m3 =";
    for (auto i : m3)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m4 =";
    for (auto i : m4)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m5 =";
    for (auto i : m5)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    cout << "m6 =";
    for (auto i : m6)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m8 by copying in an initializer_list
    multimap<int, int> m8{ { { 1, 1 }, { 2, 2 }, { 3, 3 }, { 4, 4 } } };
    cout << "m8: = ";
    for (auto i : m8)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m9 with an initializer_list and a comparator
    multimap<int, int> m9({ { 5, 5 }, { 6, 6 }, { 7, 7 }, { 8, 8 } }, less<int>());
    cout << "m9: = ";
    for (auto i : m9)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

    // Create a multimap m10 with an initializer_list, a comparator, and an allocator
    multimap<int, int> m10({ { 9, 9 }, { 10, 10 }, { 11, 11 }, { 12, 12 } }, less<int>(), m9.get_allocator());
    cout << "m10: = ";
    for (auto i : m10)
        cout << i.first << " " << i.second << ", ";
    cout << endl;

}
```

## <a name="op_eq"></a>  multimap::operator=

multimap の要素を、別の multimap のコピーで置き換えます。

```cpp
multimap& operator=(const multimap& right);

multimap& operator=(multimap&& right);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*right*|`multimap` にコピーされる [multimap](../standard-library/multimap-class.md)。|

### <a name="remarks"></a>Remarks

@No__t_0 内の既存の要素を消去した後、 *`operator=` の内容*を `multimap` にコピーまたは移動します。

### <a name="example"></a>例

```cpp
// multimap_operator_as.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
   {
   using namespace std;
   multimap<int, int> v1, v2, v3;
   multimap<int, int>::iterator iter;

   v1.insert(pair<int, int>(1, 10));

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter->second << " ";
   cout << endl;
   }
```

## <a name="pointer"></a>  multimap::pointer

multimap 内の要素へのポインターを提供する型。

```cpp
typedef typename allocator_type::pointer pointer;
```

### <a name="remarks"></a>Remarks

@No__t_0 型を使用して、要素の値を変更できます。

ほとんどの場合、multimap オブジェクト内の要素にアクセスするには[反復子](#iterator)を使用する必要があります。

## <a name="rbegin"></a>  multimap::rbegin

反転された multimap 内の最初の要素を指す反復子を返します。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>戻り値

反転された multimap 内の最初の要素を指す、または反転されていない multimap 内の最後の要素だったものを指す、逆順双方向反復子。

### <a name="remarks"></a>Remarks

`rbegin` は、[begin](#begin) が multimap で 使用されるのと同様に、反転された multimap で使用されます。

`rbegin` の戻り値が `const_reverse_iterator` に割り当てられている場合、multimap オブジェクトは変更できません。 `rbegin` の戻り値が `reverse_iterator` に割り当てられている場合は、multimap オブジェクトを変更できます。

`rbegin` を使用して、multimap 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// multimap_rbegin.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rbegin( );
   cout << "The first element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing its key
   m1_rIter = m1.rbegin( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed multimap m1 is 3.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the first element in the reversed multimap is 2.
```

## <a name="reference"></a>  multimap::reference

multimap に格納されている要素への参照を提供する型。

```cpp
typedef typename allocator_type::reference reference;
```

### <a name="example"></a>例

```cpp
// multimap_ref.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( m1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( m1.begin( ) -> first );

   cout << "The key of first element in the multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( m1.begin( ) -> second );

   cout << "The data value of first element in the multimap is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  multimap::rend

反転された multimap 内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>戻り値

反転された multimap 内の最後の要素の次の場所 (反転されていない multimap 内の最初の要素の前の場所) を指す逆順双方向反復子。

### <a name="remarks"></a>Remarks

`rend` は、[end](../standard-library/map-class.md#end) が multimap で使用されるのと同様に、反転された multimap で使用されます。

`rend` の戻り値が `const_reverse_iterator` に割り当てられている場合、multimap オブジェクトは変更できません。 `rend` の戻り値が `reverse_iterator` に割り当てられている場合は、multimap オブジェクトを変更できます。

`rend` を使用して、逆順反復子が multimap の末尾に達したかどうかをテストできます。

`rend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// multimap_rend.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;

   multimap <int, int> :: iterator m1_Iter;
   multimap <int, int> :: reverse_iterator m1_rIter;
   multimap <int, int> :: const_reverse_iterator m1_crIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "The last element of the reversed multimap m1 is "
        << m1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a multimap in a forward order
   cout << "The multimap is: ";
   for ( m1_Iter = m1.begin( ) ; m1_Iter != m1.end( ); m1_Iter++)
      cout << m1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a multimap in a reverse order
   cout << "The reversed multimap is: ";
   for ( m1_rIter = m1.rbegin( ) ; m1_rIter != m1.rend( ); m1_rIter++)
      cout << m1_rIter -> first << " ";
      cout << "." << endl;

   // A multimap element can be erased by dereferencing to its key
   m1_rIter = --m1.rend( );
   m1.erase ( m1_rIter -> first );

   m1_rIter = m1.rend( );
   m1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed multimap is "
        << m1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed multimap m1 is 1.
The multimap is: 1 2 3 .
The reversed multimap is: 3 2 1 .
After the erasure, the last element in the reversed multimap is 2.
```

## <a name="reverse_iterator"></a>  multimap::reverse_iterator

反転された multimap 内の 1 つの要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef std::reverse_iterator<iterator> reverse_iterator;
```

### <a name="remarks"></a>Remarks

`reverse_iterator` 型は、逆の順序で multimap を反復処理するために使用します。

Multimap によって定義された `reverse_iterator` は、`pair<const Key, Type>` 型の[value_type](#value_type)のオブジェクトを指します。 キーの値はペアの 1 番目のメンバー、マップされた要素の値はペアの 2 番目のメンバーを介して取得できます。

Multimap 内の要素を指す `reverse_iterator` *rIter*を逆参照するには、 **->** 演算子を使用します。

要素のキーの値にアクセスするには、`rIter->first` を使用します。これは `(*rIter).first` と同じです。 要素のマップされた datum の値にアクセスするには、`rIter->second` を使用します。これは `(*rIter).second` と同じです。

### <a name="example"></a>例

`reverse_iterator` の宣言方法や使用方法の例については、[rbegin](#rbegin) の例を参照してください。

## <a name="size"></a>  multimap::size

multimap 内の要素の数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

multimap の現在の長さ。

### <a name="example"></a>例

multimap::size メンバー関数の使用例を次に示します。

```cpp
// multimap_size.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main()
{
    using namespace std;
    multimap<int, int> m1, m2;
    multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    m1.insert(Int_Pair(1, 1));
    i = m1.size();
    cout << "The multimap length is " << i << "." << endl;

    m1.insert(Int_Pair(2, 4));
    i = m1.size();
    cout << "The multimap length is now " << i << "." << endl;
}
```

```Output
The multimap length is 1.
The multimap length is now 2.
```

## <a name="size_type"></a>  multimap::size_type

multimap 内の要素の数をカウントする符号なし整数型。

```cpp
typedef typename allocator_type::size_type size_type;
```

### <a name="example"></a>例

`size_type` の宣言方法や使用方法の例については、[size](#size) の例をご覧ください。

## <a name="swap"></a>  multimap::swap

2 つの multimap の要素を交換します。

```cpp
void swap(
    multimap<Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*右*\
交換する要素を提供する multimap (multimap `left` と要素を交換する multimap)。

### <a name="remarks"></a>Remarks

メンバー関数は、要素を交換する 2 つの multimap において要素を指定している参照、ポインター、反復子を無効化することはありません。

### <a name="example"></a>例

```cpp
// multimap_swap.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1, m2, m3;
   multimap <int, int>::iterator m1_Iter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m2.insert ( Int_Pair ( 10, 100 ) );
   m2.insert ( Int_Pair ( 20, 200 ) );
   m3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   m1.swap( m2 );

   cout << "After swapping with m2, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( m1, m3 );

   cout << "After swapping with m3, multimap m1 is:";
   for ( m1_Iter = m1.begin( ); m1_Iter != m1.end( ); m1_Iter++ )
      cout << " " << m1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original multimap m1 is: 10 20 30.
After swapping with m2, multimap m1 is: 100 200.
After swapping with m3, multimap m1 is: 300.
```

## <a name="upper_bound"></a>  multimap::upper_bound

指定したキーよりも大きいキーを持つ、multimap 内の最初の要素を指す反復子を返します。

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の multimap 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

引数キーより大きいキーを持つ multimap 内の要素の位置を指す、または、キーの一致が検出されない場合は multimap 内の最後の要素の次の位置を指す、反復子または `const_iterator`。

戻り値が `const_iterator` に割り当てられている場合、multimap オブジェクトは変更できません。 戻り値が `iterator` に割り当てられている場合は、multimap オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// multimap_upper_bound.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   multimap <int, int> m1;
   multimap <int, int> :: const_iterator m1_AcIter, m1_RcIter;
   typedef pair <int, int> Int_Pair;

   m1.insert ( Int_Pair ( 1, 10 ) );
   m1.insert ( Int_Pair ( 2, 20 ) );
   m1.insert ( Int_Pair ( 3, 30 ) );
   m1.insert ( Int_Pair ( 3, 40 ) );

   m1_RcIter = m1.upper_bound( 1 );
   cout << "The 1st element of multimap m1 with "
        << "a key greater than 1 is: "
        << m1_RcIter -> second << "." << endl;

   m1_RcIter = m1.upper_bound( 2 );
   cout << "The first element of multimap m1 with a key "
        << " greater than 2 is: "
        << m1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   m1_RcIter = m1.lower_bound( 4 );

   if ( m1_RcIter == m1.end( ) )
      cout << "The multimap m1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of multimap m1 with a key of 4 is: "
           << m1_RcIter -> second << "." << endl;

   // The element at a specific location in the multimap can be
   // found using a dereferenced iterator addressing the location
   m1_AcIter = m1.begin( );
   m1_RcIter = m1.upper_bound( m1_AcIter -> first );
   cout << "The first element of m1 with a key greater than\n"
        << "that of the initial element of m1 is: "
        << m1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of multimap m1 with a key greater than 1 is: 20.
The first element of multimap m1 with a key  greater than 2 is: 30.
The multimap m1 doesn't have an element with a key of 4.
The first element of m1 with a key greater than
that of the initial element of m1 is: 20.
```

## <a name="value_comp"></a>  multimap::value_comp

このメンバー関数は、キー値の比較によって multimap の要素の順序を決定する関数オブジェクトを返します。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>戻り値

multimap が要素の並べ替えに使用する比較関数オブジェクトを返します。

### <a name="remarks"></a>Remarks

Multimap *m*の場合、2つの*要素 e1*(*k1*、 *d1*) と*e2*(*k2*、 *d2*) は `value_type` 型のオブジェクトです。ここで、 *k1*と*k2*は 0 型のキーであり、 *d1*および*d2*です。3 型のデータであり、4 は 5 に相当します。

### <a name="example"></a>例

```cpp
// multimap_value_comp.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;

   multimap <int, int, less<int> > m1;
   multimap <int, int, less<int> >::value_compare vc1 = m1.value_comp( );
   multimap<int,int>::iterator Iter1, Iter2;

   Iter1= m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= m1.insert ( multimap <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *Iter1, *Iter2 ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does "
           << "not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1( *Iter2, *Iter1 ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does "
           << "not precede the element ( 1,10 )."
           << endl;
   }
}
```

```Output
The element ( 1,10 ) precedes the element ( 2,5 ).
The element ( 2,5 ) does not precede the element ( 1,10 ).
```

## <a name="value_type"></a>  multimap::value_type

map 内に要素として格納されるオブジェクトの型を表す型。

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="example"></a>例

```cpp
// multimap_value_type.cpp
// compile with: /EHsc
#include <map>
#include <iostream>

int main( )
{
   using namespace std;
   typedef pair <const int, int> cInt2Int;
   multimap <int, int> m1;
   multimap <int, int> :: key_type key1;
   multimap <int, int> :: mapped_type mapped1;
   multimap <int, int> :: value_type value1;
   multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   m1.insert ( multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   m1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( m1.begin( ) -> first );
   mapped1 = ( m1.begin( ) -> second );

   cout << "The key of first element in the multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = m1.begin( ) ; pIter != m1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the multimap is 1.
The data value of first element in the multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>関連項目

[コンテナー](../cpp/containers-modern-cpp.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
