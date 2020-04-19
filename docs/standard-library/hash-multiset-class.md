---
title: hash_multiset クラス
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_multiset
- hash_set/stdext::hash_multiset::allocator_type
- hash_set/stdext::hash_multiset::const_iterator
- hash_set/stdext::hash_multiset::const_pointer
- hash_set/stdext::hash_multiset::const_reference
- hash_set/stdext::hash_multiset::const_reverse_iterator
- hash_set/stdext::hash_multiset::difference_type
- hash_set/stdext::hash_multiset::iterator
- hash_set/stdext::hash_multiset::key_compare
- hash_set/stdext::hash_multiset::key_type
- hash_set/stdext::hash_multiset::pointer
- hash_set/stdext::hash_multiset::reference
- hash_set/stdext::hash_multiset::reverse_iterator
- hash_set/stdext::hash_multiset::size_type
- hash_set/stdext::hash_multiset::value_compare
- hash_set/stdext::hash_multiset::value_type
- hash_set/stdext::hash_multiset::begin
- hash_set/stdext::hash_multiset::cbegin
- hash_set/stdext::hash_multiset::cend
- hash_set/stdext::hash_multiset::clear
- hash_set/stdext::hash_multiset::count
- hash_set/stdext::hash_multiset::crbegin
- hash_set/stdext::hash_multiset::crend
- hash_set/stdext::hash_multiset::emplace
- hash_set/stdext::hash_multiset::emplace_hint
- hash_set/stdext::hash_multiset::empty
- hash_set/stdext::hash_multiset::end
- hash_set/stdext::hash_multiset::equal_range
- hash_set/stdext::hash_multiset::erase
- hash_set/stdext::hash_multiset::find
- hash_set/stdext::hash_multiset::get_allocator
- hash_set/stdext::hash_multiset::insert
- hash_set/stdext::hash_multiset::key_comp
- hash_set/stdext::hash_multiset::lower_bound
- hash_set/stdext::hash_multiset::max_size
- hash_set/stdext::hash_multiset::rbegin
- hash_set/stdext::hash_multiset::rend
- hash_set/stdext::hash_multiset::size
- hash_set/stdext::hash_multiset::swap
- hash_set/stdext::hash_multiset::upper_bound
- hash_set/stdext::hash_multiset::value_comp
helpviewer_keywords:
- stdext::hash_multiset
- stdext::hash_multiset::allocator_type
- stdext::hash_multiset::const_iterator
- stdext::hash_multiset::const_pointer
- stdext::hash_multiset::const_reference
- stdext::hash_multiset::const_reverse_iterator
- stdext::hash_multiset::difference_type
- stdext::hash_multiset::iterator
- stdext::hash_multiset::key_compare
- stdext::hash_multiset::key_type
- stdext::hash_multiset::pointer
- stdext::hash_multiset::reference
- stdext::hash_multiset::reverse_iterator
- stdext::hash_multiset::size_type
- stdext::hash_multiset::value_compare
- stdext::hash_multiset::value_type
- stdext::hash_multiset::begin
- stdext::hash_multiset::cbegin
- stdext::hash_multiset::cend
- stdext::hash_multiset::clear
- stdext::hash_multiset::count
- stdext::hash_multiset::crbegin
- stdext::hash_multiset::crend
- stdext::hash_multiset::emplace
- stdext::hash_multiset::emplace_hint
- stdext::hash_multiset::empty
- stdext::hash_multiset::end
- stdext::hash_multiset::equal_range
- stdext::hash_multiset::erase
- stdext::hash_multiset::find
- stdext::hash_multiset::get_allocator
- stdext::hash_multiset::insert
- stdext::hash_multiset::key_comp
- stdext::hash_multiset::lower_bound
- stdext::hash_multiset::max_size
- stdext::hash_multiset::rbegin
- stdext::hash_multiset::rend
- stdext::hash_multiset::size
- stdext::hash_multiset::swap
- stdext::hash_multiset::upper_bound
- stdext::hash_multiset::value_comp
ms.assetid: 0580397a-a76e-40ad-aea2-5c6f3a9d0a21
ms.openlocfilehash: 7881b1d6775206fbea40c3ba4b15572a6d4b3580
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865138"
---
# <a name="hash_multiset-class"></a>hash_multiset クラス

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

コンテナー クラスの hash_multiset は、C++ 標準ライブラリの拡張機能であり、コレクションのデータを格納および迅速に取得するために使用されます。コレクションに含まれる要素の値は、キー値として機能し、一意である必要はありません。

## <a name="syntax"></a>構文

```cpp
template <class Key, class Traits =hash_compare<Key, less <Key>>, class Allocator =allocator <Key>>
class hash_multiset
```

### <a name="parameters"></a>パラメーター

*キー*\
hash_multiset に格納する要素のデータ型。

*特徴*\
2つの関数オブジェクトを含む型。2つの要素の値を並べ替えキーとして比較してその相対順序を決定できる二項述語と、要素のキー値を `size_t`型の符号なし整数にマッピングする単項述語であるハッシュ関数の2つの関数オブジェクトが含まれます。 この引数は省略可能であり、既定値は `hash_compare<Key, less<Key> >` です。

*アロケーター*\
hash_multiset のメモリの割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクトを表す型。 この引数は省略可能であり、既定値は `allocator<Key>` です。

## <a name="remarks"></a>解説

hash_multiset は次のとおりです。

- hash_map は連想コンテナーであり、関連付けられたキー値に基づいて要素の値を効率的に取得できるようにする可変サイズのコンテナーとして機能します。 さらに、単純な連想コンテナーです。これは、要素値がキー値であるためです。

- 反転することができます。これは、hash_map には、要素にアクセスするための双方向反復子が用意されているためです。

- ハッシュされます。これは、要素のキー値に適用されたハッシュ関数の値に基づいて、要素がバケットにグループ化されるためです。

- 一意のクラスです。これは、各要素が一意のキーを持つ必要があるためです。 hash_multiset は単純な連想コンテナーでもあるため、要素も一意です。

- クラステンプレートは、提供される機能がジェネリックであり、要素またはキーとして含まれる特定のデータ型に依存しないためです。 要素やキーに使用されているデータ型は、クラス テンプレートで比較関数やアロケーターと共にパラメーターとして指定されます。

並べ替えに対するハッシュの主な利点は、効率に優れていることです。コンテナー内にある要素を並べ替えるとき、その時間は要素の数の対数に比例しますが、適切なハッシュを実行すると、挿入、削除、検索にかかる平均時間は一定になります。 set 内の要素の値は直接変更できません。 代わりに、以前の値を削除し、新しい値の要素を挿入する必要があります。

一般的に、コンテナー型の選択は、アプリケーションにおいて必要な検索および挿入の種類に基づいている必要があります。 ハッシュされた連想コンテナーは、検索、挿入、削除の各操作用に最適化されています。 これらの操作を明示的にサポートするメンバー関数は、適切に記述されたハッシュ関数と共に使用すると、効率的に機能します。検索、挿入、削除の操作にかかる実行時間は、平均で一定しており、コンテナー内の要素の数による影響を受けません。 適切に記述されたハッシュ関数によって、ハッシュ値の一様分布が生成され、競合の数を最小限に抑えることができます (競合は、異なるキー値が同じハッシュ値にマップされたときに発生する可能性があります)。 最悪のケースは、不適切に記述されたハッシュ関数が使用される場合です。演算の回数は、シーケンス内の要素数に比例して増えることになります (線形時間)。

値とキーを関連付ける条件をアプリケーションが満たしている場合、hash_multiset は最適な連想コンテナーとなっている必要があります。 hash_multiset の要素は複数の場合があり、それ自体の並べ替えキーとして機能する場合があるため、キーは一意ではありません。 この種類の構造体のモデルは、単語が複数回出現する可能性がある単語の順序付きのリストです。 単語が複数回出現することが許可されていない場合は、hash_set が適切なコンテナー構造体です。 一意の定義が値として一意のキーワードのリストにアタッチされている場合は、hash_map がこのデータを格納するのに適切な構造体です。 定義が一意でない場合は、hash_multimap が最適なコンテナーです。

hash_multimap は、格納されているハッシュ特徴 (traits) オブジェクト ([value_compare 型](#value_compare)) を呼び出すことによって、制御するシーケンスを並べ替えます。 格納されているこのオブジェクトには、メンバー関数 [key_comp](#key_comp) を呼び出すことによってアクセスできます。 このような関数オブジェクトは、`hash_compare<Key, less<Key> >`クラスのオブジェクトと同じように動作する必要があります。 具体的には、`Key`型のすべての値の*キー*について、`Trait(Key)` 呼び出しは `size_t`型の値の分布を生成します。

通常、要素は、この順序を確立するために小なり比較だけを実行できる必要があります。これにより、2 つの要素が指定されたときに、それらの要素が等しいか (どちらか一方が小さくはない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 テクニカル ノートでは、比較関数は、数学上の標準的な意味で厳密弱順序を発生させる二項述語であると示されています。 二項述語 *f*( *x*, *y*) は、2 つの引数オブジェクト (x および y) と戻り値 (true または false) を持つ関数オブジェクトです。 hash_multiset に適用される順序付けは、二項述語が非再帰、反対称、推移的であり、等価性が推移的である (2 つのオブジェクト (x と y) が、*f*( *x*,*y*) と *f*( *y*, *x*) の両方が false の場合に等価になるように定義されている) 場合、厳密弱順序になります。 2 つのキーの等値に関する条件が等価性の条件よりも厳しく、優先される場合、順序付けは完全な順序付け (すべての要素が相互の値に基づいて並べ替えられる) となり、一致するそれぞれのキーを識別するのが難しくなります。

被制御シーケンスにおける要素の実際の順序は、ハッシュ関数、順序関数、コンテナー オブジェクトに格納されるハッシュ テーブルの現在のサイズによって異なります。 ハッシュ テーブルの現在のサイズは特定できないため、通常は、被制御シーケンス内の要素の順序を予測することはできません。 要素を挿入しても反復子の有効性は失われません。また、要素を削除した場合は、削除された要素を具体的に指す反復子だけが無効化されます。

hash_multiset クラスに用意されている反復子は双方向反復子ですが、クラス メンバー関数 insert と hash_multiset には、弱い入力反復子をテンプレート パラメーターとして取得するバージョンがあります。この反復子の機能に関する要件は、双方向反復子のクラスで保証されている要件よりも低くなっています。 これらの反復子の機能に差異があるのは、反復子の概念が異なっているためです。 反復子の各概念には、反復子独自の要件の hash_multiset が含まれています。また、それらの要件を使用するアルゴリズムでは、反復子の種類ごとに指定されている要件で前提を絞り込む必要があります。 たとえば、一部のオブジェクトを参照するために入力反復子が逆参照される可能性があることを前提とする場合があります。さらに、シーケンス内にある次の反復子に対して逆参照が増加する可能性があることを前提とする場合もあります。 これは hash_multiset の最低限の機能ですが、クラス メンバー関数のコンテキストでの反復子の範囲 [ `first`, `last`) について明確にすることも重要です。

### <a name="constructors"></a>コンストラクター

|Constructor|Description|
|-|-|
|[hash_multiset](#hash_multiset)|空の `hash_multiset`、または他の `hash_multiset` の全体または一部のコピーである hash_multiset を構築します。|

### <a name="typedefs"></a>Typedefs

|種類の名前。|Description|
|-|-|
|[allocator_type](#allocator_type)|`allocator` オブジェクトの `hash_multiset` クラスを表す型。|
|[const_iterator](#const_iterator)|`hash_multiset`内の**const**要素を読み取ることができる双方向反復子を提供する型。|
|[const_pointer](#const_pointer)|`hash_multiset`内の**const**要素へのポインターを提供する型。|
|[const_reference](#const_reference)|読み取りと**const**操作の実行のために `hash_multiset` に格納されている**const**要素への参照を提供する型。|
|[const_reverse_iterator](#const_reverse_iterator)|`hash_multiset`内の任意の**const**要素を読み取ることができる双方向反復子を提供する型。|
|[difference_type](#difference_type)|同じ `hash_multiset` 内の要素をアドレス指定する 2 つの反復子の差を提供する符号付き整数型|
|[Iterator](#iterator)|`hash_multiset` 内の任意の要素を読み取り、または変更できる双方向反復子を提供する型。|
|[key_compare](#key_compare)|2 つの並べ替えキーを比較して、`hash_multiset` 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。|
|[key_type](#key_type)|並べ替えキーとしてキャパシティ内に `hash_set` の要素として格納されるオブジェクトを表す型。|
|[pointer](#pointer)|`hash_multiset` 内の要素へのポインターを提供する型。|
|[reference](#reference)|`hash_multiset` に格納されている要素への参照を提供する型。|
|[reverse_iterator](#reverse_iterator)|反転された `hash_multiset` 内の 1 つの要素を読み取り、または変更できる双方向反復子を提供する型。|
|[size_type](#size_type)|`hash_multiset` 内の要素の数を表すことができる符号なし整数型。|
|[value_compare](#value_compare)|2 つの関数オブジェクト、すなわち、`hash_multiset` の 2 つの要素の値を比較してその相対順序を判断できるクラス比較の二項述語と、要素のハッシュを計算する単項述語を提供する型です。|
|[value_type](#value_type)|値としてキャパシティ内に `hash_multiset` の要素として格納されるオブジェクトを表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|Description|
|-|-|
|[begin](#begin)|`hash_multiset` 内の最初の要素を指す反復子を返します。|
|[cbegin](#cbegin)|`hash_multiset` 内の最初の要素を指す定数反復子を返します。|
|[cend](#cend)|`hash_multiset` 内の最後の要素の次の位置を指す定数反復子を返します。|
|[オフ](#clear)|`hash_multiset` のすべての要素を消去します。|
|[count](#count)|パラメーター指定したキーに一致するキーを持つ、`hash_multiset` 内の要素の数を返します。|
|[crbegin](#crbegin)|反転された `hash_multiset` 内の最初の要素を指す定数反復子を返します。|
|[crend](#crend)|反転された `hash_multiset` 内の最後の要素の次の位置を指す定数反復子を返します。|
|[emplace](#emplace)|インプレースで構築された要素を `hash_multiset` に挿入します。|
|[emplace_hint](#emplace_hint)|インプレースで構築された要素を、配置ヒントと共に `hash_multiset` に挿入します。|
|[empty](#empty)|`hash_multiset` が空かどうかをテストします。|
|[end](#end)|`hash_multiset` 内の最後の要素の次の位置を指す反復子を返します。|
|[equal_range](#equal_range)|指定したキーよりも大きいキーを持つ、`hash_multiset` 内の最初の要素を指す反復子と、およびそのキー以上のキーを持つ、`hash_multiset` 内の最初の要素を指す反復子のペアを返します。|
|[erase](#erase)|`hash_multiset` 内の要素または要素の範囲を指定した位置から削除するか、または指定したキーと一致する要素を削除します。|
|[find](#find)|指定したキーと同じキーを持つ、`hash_multiset` 内の要素の位置を指す反復子を返します。|
|[get_allocator](#get_allocator)|`allocator` の構築に使用される `hash_multiset` オブジェクトのコピーを返します。|
|[insert](#insert)|`hash_multiset` に要素または要素範囲を挿入します。|
|[key_comp](#key_compare)|`hash_multiset` 内のキーを並べ替えるために使用される比較オブジェクトのコピーを取得します。|
|[lower_bound](#lower_bound)|指定したキー以上のキーを持つ、`hash_multiset` 内の最初の要素を指す反復子を返します。|
|[max_size](#max_size)|`hash_multiset` の最大長を返します。|
|[rbegin](#rbegin)|反転された `hash_multiset` 内の最初の要素を指す反復子を返します。|
|[rend](#rend)|反転された `hash_multiset` 内の最後の要素の次の位置を指す反復子を返します。|
|[size](#size)|`hash_multiset` 内の要素数を返します。|
|[スワップ](#swap)|2 つの `hash_multiset` の要素を交換します。|
|[upper_bound](#upper_bound)|指定したキー以上のキーを持つ、`hash_multiset` 内の最初の要素を指す反復子を返します。|
|[value_comp](#value_comp)|`hash_multiset` の要素キー値をハッシュおよび順序付けするために使用するハッシュ特性オブジェクトのコピーを取得します。|

### <a name="operators"></a>オペレーター

|演算子|Description|
|-|-|
|[hash_multiset::operator=](#op_eq)|hash_multiset の要素を、別の hash_multiset のコピーで置き換えます。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<hash_set >

**名前空間:** stdext

## <a name="allocator_type"></a>  hash_multiset::allocator_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset オブジェクトのアロケーター クラスを表す型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>例

[ の使用例については、](#get_allocator)get_allocator`allocator_type` の例をご覧ください。

## <a name="begin"></a>  hash_multiset::begin

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset 内の最初の要素を指す反復子を返します。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>戻り値

hash_multiset 内の最初の要素、または空の hash_multiset の次の位置を指す双方向反復子。

### <a name="remarks"></a>解説

`begin` の戻り値が `const_iterator`に割り当てられている場合、hash_multiset オブジェクト内の要素は変更できません。 `begin` の戻り値が `iterator`に割り当てられている場合は、hash_multiset オブジェクト内の要素を変更できます。

### <a name="example"></a>例

```cpp
// hash_multiset_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.begin( );
   cout << "The first element of hms1 is " << *hms1_Iter << endl;

   hms1_Iter = hms1.begin( );
   hms1.erase( hms1_Iter );

   // The following 2 lines would err because the iterator is const
   // hms1_cIter = hms1.begin( );
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.begin( );
   cout << "The first element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The first element of hms1 is 1
The first element of hms1 is now 2
```

## <a name="cbegin"></a>  hash_multiset::cbegin

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset 内の最初の要素を指す定数反復子を返します。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

[hash_multiset](../standard-library/hash-multiset-class.md) 内の最初の要素、または空の `hash_multiset` の次の位置を指す定数双方向反復子。

### <a name="remarks"></a>解説

`cbegin` の戻り値で `hash_multiset` オブジェクト内の要素を変更することはできません。

### <a name="example"></a>例

```cpp
// hash_multiset_cbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cbegin( );
   cout << "The first element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
```

## <a name="cend"></a>  hash_multiset::cend

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset 内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>戻り値

[hash_multiset](../standard-library/hash-multiset-class.md) リスト内の最後の要素の次の位置を指す定数双方向反復子。 `hash_multiset` が空の場合は、`hash_multiset::cend == hash_multiset::begin`。

### <a name="remarks"></a>解説

`cend` は、反復子が `hash_multiset` の末尾に達したかどうかをテストするために使用します。 `cend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// hash_multiset_cend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_cIter = hs1.cend( );
   hs1_cIter--;
   cout << "The last element of hs1 is " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
```

## <a name="clear"></a>  hash_multiset::clear

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset のすべての要素を消去します。

```cpp
void clear();
```

### <a name="remarks"></a>解説

### <a name="example"></a>例

```cpp
// hash_multiset_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 1 );
   hms1.insert( 2 );

   cout << "The size of the hash_multiset is initially " << hms1.size( )
        << "." << endl;

   hms1.clear( );
   cout << "The size of the hash_multiset after clearing is "
        << hms1.size( ) << "." << endl;
}
```

```Output
The size of the hash_multiset is initially 2.
The size of the hash_multiset after clearing is 0.
```

## <a name="const_iterator"></a>  hash_multiset::const_iterator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset の 1 つの **const** 要素を読み取ることができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>解説

`const_iterator` 型で要素の値を変更することはできません。

### <a name="example"></a>例

[ の使用例については、](#begin)begin`const_iterator` の例をご覧ください。

## <a name="const_pointer"></a>  hash_multiset::const_pointer

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset 内の **const** 要素へのポインターを提供する型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>解説

`const_pointer` 型で要素の値を変更することはできません。

ほとんどの場合、[const](#const_iterator) hash_multiset オブジェクト内の要素にアクセスするには、**const_iterator** を使用する必要があります。

## <a name="const_reference"></a>  hash_multiset::const_reference

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

読み取りと **const** 操作の実行のために hash_multiset に格納された **const** 要素への参照を提供する型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>解説

### <a name="example"></a>例

```cpp
// hash_multiset_const_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_multiset
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_multiset is 10.
```

## <a name="const_reverse_iterator"></a>  hash_multiset::const_reverse_iterator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset の任意の **const** 要素を読み取ることができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>解説

`const_reverse_iterator` 型は要素の値を変更できず、逆の順序で hash_multiset を反復処理するために使用します。

### <a name="example"></a>例

[ の宣言方法や使用方法の例については、](#rend)rend`const_reverse_iterator` の例をご覧ください。

## <a name="count"></a>  hash_multiset::count

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

パラメーター指定したキーと一致するキーを持つ、hash_multiset 内の要素の数を返します。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー*\
照合される hash_multiset の要素のキー。

### <a name="return-value"></a>戻り値

パラメーター指定したキーを持つ、hash_multiset 内の要素の数。

### <a name="remarks"></a>解説

メンバー関数は、次の範囲内の要素の数を返します。

\[ lower_bound (*キー*)、upper_bound (*キー*))。

### <a name="example"></a>例

hash_multiset::count メンバー関数の使用例を次に示します。

```cpp
// hash_multiset_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1;
    hash_multiset<int>::size_type i;

    hms1.insert(1);
    hms1.insert(1);

    // Keys do not need to be unique in hash_multiset,
    // so duplicates may exist.
    i = hms1.count(1);
    cout << "The number of elements in hms1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hms1.count(2);
    cout << "The number of elements in hms1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hms1 with a sort key of 1 is: 2.
The number of elements in hms1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>  hash_multiset::crbegin

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

反転された hash_multiset 内の最初の要素を指す定数反復子を返します。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>戻り値

反転された [hash_multiset](../standard-library/hash-multiset-class.md) 内の最初の要素を示す、または反転されていない `hash_multiset` 内の最後の要素だったものを示す定数逆順双方向反復子。

### <a name="remarks"></a>解説

`crbegin` は、`hash_multiset`hash_multiset::begin[ が ](#begin) で使用されるのと同様に、反転された `hash_multiset` で使用されます。

戻り値が `crbegin` の場合、`hash_multiset` オブジェクトは変更できません。

`crbegin` を使用して、`hash_multiset` 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// hash_multiset_crbegin.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
```

## <a name="crend"></a>  hash_multiset::crend

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

反転された hash_multiset 内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>戻り値

逆順の [hash_multiset](../standard-library/hash-multiset-class.md) 内の最後の要素の次の場所 (通常の順序の `hash_multiset` 内の最初の要素の前の場所) を指す定数逆順双方向反復子。

### <a name="remarks"></a>解説

`crend` は、`hash_multiset`hash_multiset::end[ が ](#end) で使用されるのと同様に、反転された `hash_multiset` で使用されます。

戻り値が `crend` の場合、`hash_multiset` オブジェクトは変更できません。

`crend` を使用して、逆順反復子が hash_multiset の末尾に達したかどうかをテストできます。

### <a name="example"></a>例

```cpp
// hash_multiset_crend.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hs1;
   hash_multiset <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
```

## <a name="difference_type"></a>  hash_multiset::difference_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

同じ hash_multiset 内の要素をアドレス指定する 2 つの反復子の差を提供する符号付き整数型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>解説

`difference_type` は、コンテナーの反復子を減算またはインクリメントするときに返される型です。 通常、`difference_type` は、[ `first`, `last`) の範囲内で、反復子 `first` と `last` の間にある要素の数を表すために使用され、`first` が指す要素と、`last` が指す要素の 1 つ前までの範囲の要素を含みます。

`difference_type` は、入力反復子の要件を満たすすべての反復子に使用できますが、set などの反転可能なコンテナーによってサポートされる双方向反復子のクラスが含まれていることに注意してください。 反復子間の減算は、vector や deque などのランダムアクセスコンテナーによって提供されるランダムアクセス反復子によってのみサポートされます。

### <a name="example"></a>例

```cpp
// hash_multiset_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter, hms1_bIter, hms1_eIter;

   hms1.insert( 20 );
   hms1.insert( 10 );

   // hash_multiset elements need not be unique
   hms1.insert( 20 );

   hms1_bIter = hms1.begin( );
   hms1_eIter = hms1.end( );

   hash_multiset <int>::difference_type   df_typ5, df_typ10,
        df_typ20;

   df_typ5 = count( hms1_bIter, hms1_eIter, 5 );
   df_typ10 = count( hms1_bIter, hms1_eIter, 10 );
   df_typ20 = count( hms1_bIter, hms1_eIter, 20 );

   // The keys & hence the elements of a hash_multiset
   // need not be unique and may occur multiple times
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_multiset hms1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_multiset hms1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_multiset hms1.\n";

   // Count the number of elements in a hash_multiset
   hash_multiset <int>::difference_type  df_count = 0;
   hms1_Iter = hms1.begin( );
   while ( hms1_Iter != hms1_eIter)
   {
      df_count++;
      hms1_Iter++;
   }

   cout << "The number of elements in the hash_multiset hms1 is "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_multiset hms1.
The number '10' occurs 1 times in hash_multiset hms1.
The number '20' occurs 2 times in hash_multiset hms1.
The number of elements in the hash_multiset hms1 is 3.
```

## <a name="emplace"></a>  hash_multiset::emplace

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

インプレースで構築された要素を hash_multiset に挿入します。

```cpp
template <class ValTy>
iterator insert(ValTy&& val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|Description|
|-|-|
|*val*|挿入される要素が [ にまだ含まれていない場合、より一般的には、キーが同じ順序付けになる要素がまだ含まれていない場合に、](../standard-library/hash-multiset-class.md)hash_multiset`hash_multiset` に挿入される要素の値。|

### <a name="return-value"></a>戻り値

`emplace` メンバー関数は、新しい要素が挿入された位置を指す反復子を返します。

### <a name="remarks"></a>解説

### <a name="example"></a>例

```cpp
// hash_multiset_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms3;
   string str1("a");

   hms3.emplace(move(str1));
   cout << "After the emplace insertion, hms3 contains "
      << *hms3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms3 contains a.
```

## <a name="emplace_hint"></a>  hash_multiset::emplace_hint

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

インプレースで構築された要素を、配置ヒントと共に hash_multiset に挿入します。

```cpp
template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& val);
```

### <a name="parameters"></a>パラメーター

*val*\
挿入される要素が [ にまだ含まれていない場合、より一般的には、キーが同じ順序付けになる要素がまだ含まれていない場合に、](../standard-library/hash-multiset-class.md)hash_multiset`hash_multiset` に挿入される要素の値。

*\*
正しい挿入ポイントの検索を開始する場所 (挿入ポイントが*where*の直後にある場合、挿入は、対数時間ではなく償却定数時間で行うことができます)。

### <a name="return-value"></a>戻り値

[hash_multiset::emplace](#emplace) メンバー関数は、`hash_multiset` に新しい要素が挿入された位置を指す反復子を返します。

### <a name="remarks"></a>解説

挿入ポイントが*位置*の直後にある場合、挿入は対数時間ではなく、償却定数時間で実行できます。

### <a name="example"></a>例

```cpp
// hash_multiset_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<string> hms1;
   string str1("a");

   hms1.insert(hms1.begin(), move(str1));
   cout << "After the emplace insertion, hms1 contains "
      << *hms1.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hms1 contains a.
```

## <a name="empty"></a>  hash_multiset::empty

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset が空かどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

hash_multiset が空の場合は **true**。hash_multiset が空ではない場合は **false**。

### <a name="remarks"></a>解説

### <a name="example"></a>例

```cpp
// hash_multiset_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2;
   hms1.insert ( 1 );

   if ( hms1.empty( ) )
      cout << "The hash_multiset hms1 is empty." << endl;
   else
      cout << "The hash_multiset hms1 is not empty." << endl;

   if ( hms2.empty( ) )
      cout << "The hash_multiset hms2 is empty." << endl;
   else
      cout << "The hash_multiset hms2 is not empty." << endl;
}
```

```Output
The hash_multiset hms1 is not empty.
The hash_multiset hms2 is empty.
```

## <a name="end"></a>  hash_multiset::end

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset 内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>戻り値

hash_multiset リスト内の最後の要素の次の位置を指す双方向反復子。 hash_multiset が空の場合は、hash_multiset::end == hash_multiset::begin。

### <a name="remarks"></a>解説

`end` は、反復子が hash_multiset の末尾に達したかどうかをテストするために使用されます。 `end` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// hash_multiset_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: iterator hms1_Iter;
   hash_multiset <int> :: const_iterator hms1_cIter;

   hms1.insert( 1 );
   hms1.insert( 2 );
   hms1.insert( 3 );

   hms1_Iter = hms1.end( );
   hms1_Iter--;
   cout << "The last element of hms1 is " << *hms1_Iter << endl;

   hms1.erase( hms1_Iter );

   // The following 3 lines would err because the iterator is const
   // hms1_cIter = hms1.end( );
   // hms1_cIter--;
   // hms1.erase( hms1_cIter );

   hms1_cIter = hms1.end( );
   hms1_cIter--;
   cout << "The last element of hms1 is now " << *hms1_cIter << endl;
}
```

```Output
The last element of hms1 is 3
The last element of hms1 is now 2
```

## <a name="equal_range"></a>  hash_multiset::equal_range

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

指定したキーよりも大きいキーを持つ、hash_multiset 内の最初の要素を指す反復子と、そのキー以上のキーを持つ、hash_multiset 内の最初の要素を指す反復子のペアを返します。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>パラメーター

*キー*\
検索対象の hash_multiset 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

1 番目がそのキーの [lower_bound](#lower_bound)、2 番目がそのキーの [upper_bound](#upper_bound) である、反復子のペア。

メンバー関数によって返されるペア `pr` 最初の反復子にアクセスするには、`pr`を使用します。 **最初**に、下限の反復子を逆参照するには、\*(`pr`を使用します。 **最初**)。 メンバー関数によって返さ `pr` ペアの2番目の反復子にアクセスするには、`pr`を使用します。 **次**に、上限の反復子を逆参照するには、\*(`pr`を使用します。 **2 番目**)。

### <a name="example"></a>例

```cpp
// hash_multiset_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multiset<int> IntHSet;
   IntHSet hms1;
   hash_multiset <int> :: const_iterator hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hms1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20\nin the hash_multiset hms1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hms1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hms1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hms1.end( ) )
      && ( p2.second == hms1.end( ) ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key less than 40." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20
in the hash_multiset hms1 is: 30.
The lower bound of the element with a key of 20
in the hash_multiset hms1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_multiset hms1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  hash_multiset::erase

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset 内の要素または要素範囲を指定した位置から削除するか、指定したキーと一致する要素を削除します。

```cpp
iterator erase(iterator where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>パラメーター

*\*
hash_multiset から削除する要素の位置。

*最初*の\
hash_multiset から削除する最初の要素の位置。

*最後*の\
hash_multiset から削除する最後の要素の次の位置。

*キー*\
hash_multiset から削除する要素のキー。

### <a name="return-value"></a>戻り値

最初の 2 つのメンバー関数の場合は、削除された要素の後の最初の残存要素、またはそのような要素が存在しない場合は hash_multiset の最後へのポインターを指定する、双方向反復子。 3 つ目のメンバー関数の場合は、hash_multiset から削除された要素の数。

### <a name="remarks"></a>解説

メンバー関数が例外をスローすることはありません。

### <a name="example"></a>例

hash_multiset::erase メンバー関数の使用例を次に示します。

```cpp
// hash_multiset_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multiset<int> hms1, hms2, hms3;
    hash_multiset<int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multiset<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hms1.insert(i);
        hms2.insert(i * i);
        hms3.insert(i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hms1.begin();
    hms1.erase(Iter1);

    cout << "After the 2nd element is deleted,\n"
         << "the hash_multiset hms1 is:" ;
    for (pIter = hms1.begin(); pIter != hms1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hms2.begin();
    Iter2 = --hms2.end();
    hms2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted,\n"
         << "the hash_multiset hms2 is:" ;
    for (pIter = hms2.begin(); pIter != hms2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hms3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hms3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hms3.begin();
    hms3.erase(Iter1);

    cout << "After another element with a key "
         << "equal to that of the 2nd element\n"
         << "is deleted, the hash_multiset hms3 is:" ;
    for (pIter = hms3.begin(); pIter != hms3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted,
the hash_multiset hms1 is: 1 3 4.
After the middle two elements are deleted,
the hash_multiset hms2 is: 16 4.
After the element with a key of 2 is deleted,
the hash_multiset hms3 is: 0 1 3.
The number of elements removed from hms3 is: 1.
After another element with a key equal to that of the 2nd element
is deleted, the hash_multiset hms3 is: 0 3.
```

## <a name="find"></a>  hash_multiset::find

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

指定したキーと同じキーを持つ、hash_multiset 内の要素の位置を指す反復子を返します。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー*\
検索対象の hash_multiset 内の要素の並べ替えキーによって照合される引数キー。

### <a name="return-value"></a>戻り値

指定したキーと等しい要素の位置を指す、またはキーの一致が検出されない場合は hash_multiset 内の最後の要素の次の位置を指す、[反復子](#iterator)または [const_iterator](#const_iterator)。

### <a name="remarks"></a>解説

このメンバー関数は、小なり比較関係に基づいて順序を誘発する二項述語の下で、並べ替えキーが引数キーに `equivalent` される hash_multiset 内の要素を指す反復子を返します。

`find` の戻り値が `const_iterator`に割り当てられている場合、hash_multiset オブジェクトを変更することはできません。 `find` の戻り値が `iterator`に割り当てられている場合は、hash_multiset オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// hash_multiset_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.find( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // The element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.find( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The element of hash_multiset hms1 with a key of 20 is: 20.
The hash_multiset hms1 doesn't have an element with a key of 40.
The element of hms1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>  hash_multiset::get_allocator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset の構築に使用されるアロケーター オブジェクトのコピーを返します。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>戻り値

hash_multiset がメモリの管理に使用するアロケーターである、このクラスのテンプレート パラメーター `Allocator`。

`Allocator` の詳細については、[hash_multiset クラス](../standard-library/hash-multiset-class.md)のトピックのコメントに関するセクションをご覧ください。

### <a name="remarks"></a>解説

hash_multiset クラスのアロケーターは、クラスがどのようにストレージを管理するかを指定します。 C++ 標準ライブラリ コンテナー クラスで提供される既定のアロケーターは、ほとんどのプログラミング要件に対応しています。 独自のアロケーター クラスを作成して使用することは、C++ における高度な作業の 1 つです。

### <a name="example"></a>例

```cpp
// hash_multiset_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_multiset <int, hash_compare <int, less<int> > > hms1;
   hash_multiset <int, hash_compare <int, greater<int> > > hms2;
   hash_multiset <double, hash_compare <double,
      less<double> >, allocator<double> > hms3;

   hash_multiset <int, hash_compare <int,
      greater<int> > >::allocator_type hms2_Alloc;
   hash_multiset <double>::allocator_type hms3_Alloc;
   hms2_Alloc = hms2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hms3.max_size( ) <<  "." << endl;

   // The following lines create a hash_multiset hms4
   // with the allocator of hash_multiset hms1.
   hash_multiset <int>::allocator_type hms4_Alloc;
   hash_multiset <int> hms4;
   hms4_Alloc = hms2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hms2_Alloc == hms4_Alloc )
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

## <a name="hash_multiset"></a>  hash_multiset::hash_multiset

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

空の `hash_multiset`、または他の `hash_multiset` の全体または一部のコピーである hash_multiset を構築します。

```cpp
hash_multiset();

explicit hash_multiset(
    const Traits& Comp);

hash_multiset(
    const Traits& Comp,
    const Allocator& Al);

hash_multiset(
    const hash_multiset<Key, Traits, Allocator>& Right);

hash_multiset(
    hash_multiset&& Right
};
hash_multiset (initializer_list<Type> IList);

hash_multiset(
    initializer_list<Tu[e> IList, const Compare& Comp):
hash_multiset(
    initializer_list<Type> IList, const Compare& Comp, const Allocator& Al);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last,
    const Traits& Comp);

template <class InputIterator>
hash_multiset(
    InputIterator first,
    InputIterator last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>パラメーター

*Al*\
この `hash_multiset` オブジェクトに使用するストレージ アロケーター クラス。既定では、`Allocator` です。

*Comp*\
`const Traits` 内の要素の並べ替えに使用される、`hash_multiset` 型の比較関数。既定では `hash_compare` です。

*右*\
構築された `hash_multiset` のコピー元となる `hash_multiset`。

*最初*の\
コピーする要素範囲内の最初の要素の位置。

*最後*の\
コピーする要素範囲を超える最初の要素の位置。

*IList*\
コピーされる要素を含む initializer_list。

### <a name="remarks"></a>解説

すべてのコンストラクターは、アロケーター オブジェクトの型を格納します。このオブジェクトは `hash_multiset` のメモリ ストレージを管理し、後で [hash_multiset::get_allocator](#get_allocator) を呼び出して取得することができます。 代替アロケーターの代わりに使用されるクラス宣言やプリプロセス マクロでは、アロケーターのパラメーターが省略される場合があります。

すべてのコンストラクターは、それぞれの hash_multisets を初期化します。

すべてのコンストラクターは、`Traits` 型の関数オブジェクトを格納します。このオブジェクトは `hash_multiset` のキーの順序を確立するために使用され、後で [hash_multiset::key_comp](#key_comp) を呼び出して取得することができます。 `Traits` の詳細については、[hash_multiset クラス](../standard-library/hash-multiset-class.md)のトピックをご覧ください。

最初の3つのコンストラクターは、空の初期 `hash_multiset`を指定し、2番目のコンストラクターは要素の順序を確立するために使用する比較関数の型 (*Comp*) を指定し、3番目のコンストラクターは使用するアロケーターの型 (*Al*) を明示的に指定します。 キーワード **explicit** は、特定の種類の自動型変換が実行されないようにします。

4番目のコンストラクターは、`hash_multiset` `Right`を移動します。

5 番目、6 番目、7 番目のコンストラクターは initializer_list を使用します。

最後の 3 つのコンストラクターは、`first` の範囲 [ `last`, `hash_multiset`) をコピーします。下のコンストラクターになるほど、より明確に Compare クラスの比較関数とアロケーターの型が指定されています。

ハッシュされた設定コンテナー内にある要素の実際の順序は、ハッシュ関数、順序関数、ハッシュ テーブルの現在のサイズに応じて異なります。通常、順序関数のみによって要素の順序が決定される場合、設定コンテナーでの要素の順序を予測することはできません。

## <a name="insert"></a>  hash_multiset::insert

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset に要素や要素範囲を挿入します。

```cpp
iterator insert(
    const Type& value);

iterator insert(
    iterator where,
    const Type& Al);

void insert(
    initializer_list<Type> IList);

iterator insert(
    const Type& value);

iterator insert(
    Iterator where,
    const Type& value);

template <class InputIterator>
void insert(
    InputIterator first,
    InputIterator last);

template <class ValTy>
iterator insert(
    ValTy&& value);

template <class ValTy>
iterator insert(
    const_iterator where,
    ValTy&& value);
```

### <a name="parameters"></a>パラメーター

*value*\
挿入される要素が hash_multiset にまだ含まれていない場合、一般的には、キーが同じ順序付けになる要素が hash_multiset にまだ含まれていない場合に、hash_multiset に挿入される要素の値。

*\*
正しい挿入ポイントの検索を開始する場所 (挿入ポイントが*where*の直後にある場合、挿入は、対数時間ではなく償却定数時間で行うことができます)。

*最初*の\
hash_multiset からコピーされる最初の要素の位置。

*最後*の\
hash_multiset からコピーされる最後の要素の次の位置。

*IList*\
コピーする要素を含む initializer_list。

### <a name="return-value"></a>戻り値

最初の 2 つの insert メンバー関数は、新しい要素が挿入された位置を指す反復子を返します。

次の 3 つのメンバー関数は initializer_list を使用します。

3 番目のメンバー関数は、指定した hash_multiset の範囲 (`first`、`last`) 内の反復子が指す各要素に対応する hash_multiset に要素値のシーケンスを挿入します。

### <a name="remarks"></a>解説

挿入ポイントが*位置*の直後にある場合、挿入は、対数時間ではなく、insert のヒントバージョンに対して償却定数時間で実行できます。

## <a name="iterator"></a>  hash_multiset::iterator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset 内の任意の要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>解説

`iterator` 型を使用して、要素の値を変更できます。

### <a name="example"></a>例

`iterator`の宣言方法や使用方法の例については、 [begin](#begin)の例を参照してください。

## <a name="key_comp"></a>  hash_multiset::key_comp

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset 内のキーを並べ替えるために使用される比較オブジェクトのコピーを取得します。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>戻り値

コンテナーの要素のハッシュと順序付けに使用される関数オブジェクトを含む、hash_multiset テンプレートパラメーターの*特徴*を返します。

*特徴*の詳細については、 [hash_multiset クラス](../standard-library/hash-multiset-class.md)に関するトピックを参照してください。

### <a name="remarks"></a>解説

格納されているオブジェクトは以下のメンバー関数を定義します。

`bool operator<(const Key& _xVal, const Key& _yVal);`

これは、並べ替え順で **が** に先行しかつ等しくない場合に `_xVal`true`_yVal` を返します。

[key_compare](#key_compare) および [value_compare](#value_compare) は両方ともテンプレート パラメーター *Traits* のシノニムです。 どちらも hash_multiset および hash_multiset クラスで使用でき、そこでは同一ですが、hash_map および hash_multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

```cpp
// hash_multiset_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > >hms1;
   hash_multiset<int, hash_compare < int, less<int> > >::key_compare kc1
          = hms1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hms1."
        << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hms2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hms2."
           << endl;
   }
}
```

## <a name="key_compare"></a>  hash_multiset::key_compare

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

2 つの関数オブジェクト、すなわち、hash_multiset の 2 つの要素の値を比較してその相対順序を判断できるクラス比較の二項述語と、要素のハッシュを計算する単項述語を提供する型です。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>解説

`key_compare` は、テンプレートパラメーターの*特徴*のシノニムです。

*特徴*の詳細については、 [hash_multiset クラス](../standard-library/hash-multiset-class.md)に関するトピックを参照してください。

`key_compare` および value_compare は両方ともテンプレート パラメーター *Traits* のシノニムです。 どちらも hash_set および hash_multiset クラスで使用でき、そこでは同一ですが、hash_map および hash_multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

[ の宣言方法や使用方法の例については、](#key_comp)key_comp`key_compare` の例をご覧ください。

## <a name="key_type"></a>  hash_multiset::key_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

並べ替えキーを比較して、hash_multiset 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>解説

`key_type` は、テンプレートパラメーター*キー*のシノニムです。

`key_type` および [value_type](../standard-library/hash-set-class.md#value_type) は両方ともテンプレート パラメーター *Key* のシノニムです。 これらの型は map クラスおよび multimap クラスでは異なるものになるため、互換性を保つためにこれらが同一のものである set クラスと multiset クラスでも使用できるようになっています。

*キー*の詳細については、 [hash_multiset クラス](../standard-library/hash-multiset-class.md)のトピックの「解説」を参照してください。

### <a name="example"></a>例

[ の宣言方法や使用方法の例については、](#value_type)value_type`key_type` の例をご覧ください。

## <a name="lower_bound"></a>  hash_multiset::lower_bound

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

指定したキー以上のキーを持つ、hash_multiset 内の最初の要素を指す反復子を返します。

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>パラメーター

*キー*\
検索対象の hash_multiset 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

引数キー以上のキーを持つ hash_multiset 内の最初の要素の位置を指す、または、キーの一致が検出されない場合は hash_multiset 内の最後の要素の次の位置を指す、[反復子](#iterator)または [const_iterator](#const_iterator)。

### <a name="remarks"></a>解説

### <a name="example"></a>例

```cpp
// hash_multiset_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main() {
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.lower_bound( 20 );
   cout << "The element of hash_multiset hms1 with a key of 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_multiset hms1 with a key of 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be found
   // by using a dereferenced iterator that addresses the location
   hms1_AcIter = hms1.end( );
   hms1_AcIter--;
   hms1_RcIter = hms1.lower_bound( *hms1_AcIter );
   cout << "The element of hms1 with a key matching "
        << "that of the last element is: "
        << *hms1_RcIter << "." << endl;
}
```

## <a name="max_size"></a>  hash_multiset::max_size

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset の最大長を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

hash_multiset の可能な最大長。

### <a name="remarks"></a>解説

### <a name="example"></a>例

```cpp
// hash_multiset_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::size_type i;

   i = hms1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multiset is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  hash_multiset::operator=

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset の要素を、別の hash_multiset のコピーで置き換えます。

```cpp
hash_multiset& operator=(const hash_multiset& right);

hash_multiset& operator=(hash_multiset&& right);
```

### <a name="parameters"></a>パラメーター

|パラメーター|Description|
|-|-|
|*right*|[ にコピーする ](../standard-library/hash-multiset-class.md)hash_multiset`hash_multiset`。|

### <a name="remarks"></a>解説

`hash_multiset`内の既存の要素を消去した後、 *`operator=` の内容*を `hash_multiset`にコピーまたは移動します。

### <a name="example"></a>例

```cpp
// hash_multiset_operator_as.cpp
// compile with: /EHsc
#include <hash_multiset>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset<int> v1, v2, v3;
   hash_multiset<int>::iterator iter;

   v1.insert(10);

   cout << "v1 = " ;
   for (iter = v1.begin(); iter != v1.end(); iter++)
      cout << iter << " ";
   cout << endl;

   v2 = v1;
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;

// move v1 into v2
   v2.clear();
   v2 = move(v1);
   cout << "v2 = ";
   for (iter = v2.begin(); iter != v2.end(); iter++)
      cout << iter << " ";
   cout << endl;
}
```

## <a name="pointer"></a>  hash_multiset::pointer

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset 内の要素へのポインターを提供する型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>解説

`pointer` 型を使用して、要素の値を変更できます。

ほとんどの場合、multiset オブジェクト内の要素にアクセスするには[反復子](#iterator)を使用する必要があります。

## <a name="rbegin"></a>  hash_multiset::rbegin

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

反転された hash_multiset 内の最初の要素を指す反復子を返します。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>戻り値

反転された hash_multiset 内の最初の要素を示す、または反転されていない hash_multiset 内の最後の要素だったものを示す逆順双方向反復子。

### <a name="remarks"></a>解説

`rbegin` は、[begin](#begin) が hash_multiset で使用されるように、逆順の hash_multiset で使用されます。

`rbegin` の戻り値が `const_reverse_iterator` に割り当てられる場合は、hash_multiset オブジェクトを変更できません。 `rbegin` の戻り値が `reverse_iterator` に割り当てられる場合は、hash_multiset オブジェクトを変更できます。

`rbegin` を使用して、hash_multiset 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// hash_multiset_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rbegin( );
   cout << "The first element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << endl;

   // A hash_multiset element can be erased by dereferencing to its key
   hms1_rIter = hms1.rbegin( );
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_multiset is "<< *hms1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_multiset is 30.
The hash_multiset is: 10 20 30
The reversed hash_multiset is: 30 20 10
After the erasure, the first element in the reversed hash_multiset is 20.
```

## <a name="reference"></a>  hash_multiset::reference

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset に格納されている要素への参照を提供する型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>解説

### <a name="example"></a>例

```cpp
// hash_multiset_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;

   hms1.insert( 10 );
   hms1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hms1.begin( );

   cout << "The first element in the hash_multiset is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_multiset can be
   // changed by operating on its (non const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_multiset is now "
        << *hms1.begin() << "." << endl;
}
```

```Output
The first element in the hash_multiset is 10.
The first element in the hash_multiset is now 15.
```

## <a name="rend"></a>  hash_multiset::rend

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

反転された hash_multiset 内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>戻り値

逆順の hash_multiset 内の最後の要素の次の場所 (通常の順序の hash_multiset 内の最初の要素の前の場所) を指す逆順双方向反復子。

### <a name="remarks"></a>解説

`rend` は、[end](#end) が hash_multiset で使用されるように、逆順の hash_multiset で使用されます。

`rend` の戻り値が `const_reverse_iterator` に割り当てられる場合は、hash_multiset オブジェクトを変更できません。 `rend` の戻り値が `reverse_iterator` に割り当てられる場合は、hash_multiset オブジェクトを変更できます。 `rend` によって返された値は逆参照しないでください。

`rend` を使用して、逆順反復子が hash_multiset の末尾に達したかどうかをテストできます。

### <a name="example"></a>例

```cpp
// hash_multiset_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;
   hash_multiset <int>::reverse_iterator hms1_rIter;
   hash_multiset <int>::const_reverse_iterator hms1_crIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "The last element in the reversed hash_multiset is "
        << *hms1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_multiset in a forward order
   cout << "The hash_multiset is: ";
   for ( hms1_Iter = hms1.begin( ) ; hms1_Iter != hms1.end( );
         hms1_Iter++ )
      cout << *hms1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_multiset in a reverse order
   cout << "The reversed hash_multiset is: ";
   for ( hms1_rIter = hms1.rbegin( ) ; hms1_rIter != hms1.rend( );
         hms1_rIter++ )
      cout << *hms1_rIter << " ";
   cout << "." << endl;

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   hms1.erase ( *hms1_rIter );

   hms1_rIter = hms1.rend( );
   hms1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_multiset is " << *hms1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_multiset is 10.
The hash_multiset is: 10 20 30 .
The reversed hash_multiset is: 30 20 10 .
After the erasure, the last element in the reversed hash_multiset is 20.
```

## <a name="reverse_iterator"></a>  hash_multiset::reverse_iterator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

反転された hash_multiset 内の 1 つの要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>解説

型 `reverse_iterator` は、逆の順序で hash_multiset を反復処理するために使用します。

### <a name="example"></a>例

[ の宣言方法や使用方法の例については、](#rbegin)rbegin`reverse_iterator` の例をご覧ください。

## <a name="size"></a>  hash_multiset::size

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset 内の要素の数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

hash_multiset の現在の長さ。

### <a name="remarks"></a>解説

### <a name="example"></a>例

```cpp
// hash_multiset_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: size_type i;

   hms1.insert( 1 );
   i = hms1.size( );
   cout << "The hash_multiset length is " << i << "." << endl;

   hms1.insert( 2 );
   i = hms1.size( );
   cout << "The hash_multiset length is now " << i << "." << endl;
}
```

```Output
The hash_multiset length is 1.
The hash_multiset length is now 2.
```

## <a name="size_type"></a>  hash_multiset::size_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset 内の要素の数を表すことができる符号なし整数型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>解説

### <a name="example"></a>例

[ の宣言方法や使用方法の例については、](#size)size`size_type` の例をご覧ください。

## <a name="swap"></a>  hash_multiset::swap

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

2 つの hash_multiset の要素を交換します。

```cpp
void swap(hash_multiset& right);
```

### <a name="parameters"></a>パラメーター

*右*\
ターゲットの hash_multiset と交換する要素を提供する引数の hash_multiset。

### <a name="remarks"></a>解説

メンバー関数は、要素を交換する 2 つの hash_multiset において要素を指定している参照、ポインター、反復子を無効にすることはありません。

### <a name="example"></a>例

```cpp
// hash_multiset_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1, hms2, hms3;
   hash_multiset <int>::iterator hms1_Iter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );
   hms2.insert( 100 );
   hms2.insert( 200 );
   hms3.insert( 300 );

   cout << "The original hash_multiset hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hms1.swap( hms2 );

   cout << "After swapping with hms2, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hms1, hms3 );

   cout << "After swapping with hms3, list hms1 is:";
   for ( hms1_Iter = hms1.begin( ); hms1_Iter != hms1.end( );
         hms1_Iter++ )
         cout << " " << *hms1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_multiset hms1 is: 10 20 30.
After swapping with hms2, list hms1 is: 200 100.
After swapping with hms3, list hms1 is: 300.
```

## <a name="upper_bound"></a>  hash_multiset::upper_bound

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

指定したキーよりも大きいキーを持つ、hash_multiset 内の最初の要素を指す反復子を返します。

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>パラメーター

*キー*\
検索対象の hash_multiset 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

引数キーより大きいキーを持つ hash_multiset 内の最初の要素の位置を指す、または、キーの一致が検出されない場合は hash_multiset 内の最後の要素の次の位置を指す、[反復子](#iterator)または [const_iterator](#const_iterator)。

### <a name="remarks"></a>解説

### <a name="example"></a>例

```cpp
// hash_multiset_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int> :: const_iterator hms1_AcIter, hms1_RcIter;

   hms1.insert( 10 );
   hms1.insert( 20 );
   hms1.insert( 30 );

   hms1_RcIter = hms1.upper_bound( 20 );
   cout << "The first element of hash_multiset hms1" << endl
        << "with a key greater than 20 is: "
        << *hms1_RcIter << "." << endl;

   hms1_RcIter = hms1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hms1_RcIter == hms1.end( ) )
      cout << "The hash_multiset hms1 doesn't have an element\n"
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_multiset hms1"
           << "with a key > 40 is: "
           << *hms1_RcIter << "." << endl;

   // An element at a specific location in the hash_multiset can be
   // found by using a dereferenced iterator addressing the location
   hms1_AcIter = hms1.begin( );
   hms1_RcIter = hms1.upper_bound( *hms1_AcIter );
   cout << "The first element of hms1 with a key greater than "
        << endl << "that of the initial element of hms1 is: "
        << *hms1_RcIter << "." << endl;
}
```

```Output
The first element of hash_multiset hms1
with a key greater than 20 is: 30.
The hash_multiset hms1 doesn't have an element
with a key greater than 30.
The first element of hms1 with a key greater than
that of the initial element of hms1 is: 20.
```

## <a name="value_comp"></a>  hash_multiset::value_comp

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

hash_multiset 内の要素の値を並べ替えるために使用される比較オブジェクトのコピーを取得します。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>戻り値

コンテナーの要素をハッシュおよび順序付けするために使用される関数オブジェクトを含む、hash_multiset テンプレートパラメーターの*特徴*を返します。

*特徴*の詳細については、 [hash_multiset クラス](../standard-library/hash-multiset-class.md)に関するトピックを参照してください。

### <a name="remarks"></a>解説

格納されているオブジェクトは以下のメンバー関数を定義します。

**bool 演算子**( **&** `_xVal`、 **const キー &** *_yVal*);

これは、並べ替え順で **が** に先行しかつ等しくない場合に `_xVal`true`_yVal` を返します。

[key_compare](#key_compare) および [value_compare](#value_compare) は両方ともテンプレート パラメーター *Traits* のシノニムです。 どちらも hash_multiset および hash_multiset クラスで使用でき、そこでは同一ですが、hash_map および hash_multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

```cpp
// hash_multiset_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multiset <int, hash_compare < int, less<int> > > hms1;
   hash_multiset <int, hash_compare < int, less<int> > >::value_compare
      vc1 = hms1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hms1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hms1."
           << endl;
   }

   hash_multiset <int, hash_compare < int, greater<int> > > hms2;
   hash_multiset<int, hash_compare < int, greater<int> > >::
           value_compare vc2 = hms2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hms2."
           << endl;
   }
}
```

```Output
vc1( 2,3 ) returns value of true, where vc1 is the function object of hms1.
vc2( 2,3 ) returns value of false, where vc2 is the function object of hms2.
```

## <a name="value_compare"></a>  hash_multiset::value_compare

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

2 つの関数オブジェクト、すなわち、hash_multiset の 2 つの要素の値を比較してその相対順序を判断できるクラス比較の二項述語と、要素のハッシュを計算する単項述語を提供する型です。

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>解説

`value_compare` は、テンプレートパラメーターの*特徴*のシノニムです。

*特徴*の詳細については、 [hash_multiset クラス](../standard-library/hash-multiset-class.md)に関するトピックを参照してください。

[Key_compare](#key_compare)と `value_compare` は両方ともテンプレートパラメーターの*特徴*のシノニムです。 どちらもクラス set および multiset で使用でき、そこでは同一ですが、クラス map および multimap では異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

[ の宣言方法や使用方法の例については、](#value_comp)value_comp`value_compare`の例を参照してください。

## <a name="value_type"></a>  hash_multiset::value_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_multiset クラス](../standard-library/unordered-multiset-class.md)を使用してください。

値としてキャパシティ内に hash_multiset の要素として格納されるオブジェクトを表す型。

```cpp
typedef Key value_type;
```

### <a name="example"></a>例

```cpp
// hash_multiset_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multiset <int> hms1;
   hash_multiset <int>::iterator hms1_Iter;

   // Declare value_type
   hash_multiset <int> :: value_type hmsvt_Int;

   hmsvt_Int = 10;   // Initialize value_type

   // Declare key_type
   hash_multiset <int> :: key_type hmskt_Int;
   hmskt_Int = 20;             // Initialize key_type

   hms1.insert( hmsvt_Int );         // Insert value into s1
   hms1.insert( hmskt_Int );         // Insert key into s1

   // A hash_multiset accepts key_types or value_types as elements
   cout << "The hash_multiset has elements:";
   for ( hms1_Iter = hms1.begin() ; hms1_Iter != hms1.end( );
         hms1_Iter++)
      cout << " " << *hms1_Iter;
      cout << "." << endl;
}
```

```Output
The hash_multiset has elements: 10 20.
```

## <a name="see-also"></a>参照

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
