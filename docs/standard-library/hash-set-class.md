---
title: hash_set クラス
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_set
- hash_set/stdext::hash_set::allocator_type
- hash_set/stdext::hash_set::const_iterator
- hash_set/stdext::hash_set::const_pointer
- hash_set/stdext::hash_set::const_reference
- hash_set/stdext::hash_set::const_reverse_iterator
- hash_set/stdext::hash_set::difference_type
- hash_set/stdext::hash_set::iterator
- hash_set/stdext::hash_set::key_compare
- hash_set/stdext::hash_set::key_type
- hash_set/stdext::hash_set::pointer
- hash_set/stdext::hash_set::reference
- hash_set/stdext::hash_set::reverse_iterator
- hash_set/stdext::hash_set::size_type
- hash_set/stdext::hash_set::value_compare
- hash_set/stdext::hash_set::value_type
- hash_set/stdext::hash_set::begin
- hash_set/stdext::hash_set::cbegin
- hash_set/stdext::hash_set::cend
- hash_set/stdext::hash_set::clear
- hash_set/stdext::hash_set::count
- hash_set/stdext::hash_set::crbegin
- hash_set/stdext::hash_set::crend
- hash_set/stdext::hash_set::emplace
- hash_set/stdext::hash_set::emplace_hint
- hash_set/stdext::hash_set::empty
- hash_set/stdext::hash_set::end
- hash_set/stdext::hash_set::equal_range
- hash_set/stdext::hash_set::erase
- hash_set/stdext::hash_set::find
- hash_set/stdext::hash_set::get_allocator
- hash_set/stdext::hash_set::insert
- hash_set/stdext::hash_set::key_comp
- hash_set/stdext::hash_set::lower_bound
- hash_set/stdext::hash_set::max_size
- hash_set/stdext::hash_set::rbegin
- hash_set/stdext::hash_set::rend
- hash_set/stdext::hash_set::size
- hash_set/stdext::hash_set::swap
- hash_set/stdext::hash_set::upper_bound
- hash_set/stdext::hash_set::value_comp
helpviewer_keywords:
- stdext::hash_set
- stdext::hash_set::allocator_type
- stdext::hash_set::const_iterator
- stdext::hash_set::const_pointer
- stdext::hash_set::const_reference
- stdext::hash_set::const_reverse_iterator
- stdext::hash_set::difference_type
- stdext::hash_set::iterator
- stdext::hash_set::key_compare
- stdext::hash_set::key_type
- stdext::hash_set::pointer
- stdext::hash_set::reference
- stdext::hash_set::reverse_iterator
- stdext::hash_set::size_type
- stdext::hash_set::value_compare
- stdext::hash_set::value_type
- stdext::hash_set::begin
- stdext::hash_set::cbegin
- stdext::hash_set::cend
- stdext::hash_set::clear
- stdext::hash_set::count
- stdext::hash_set::crbegin
- stdext::hash_set::crend
- stdext::hash_set::emplace
- stdext::hash_set::emplace_hint
- stdext::hash_set::empty
- stdext::hash_set::end
- stdext::hash_set::equal_range
- stdext::hash_set::erase
- stdext::hash_set::find
- stdext::hash_set::get_allocator
- stdext::hash_set::insert
- stdext::hash_set::key_comp
- stdext::hash_set::lower_bound
- stdext::hash_set::max_size
- stdext::hash_set::rbegin
- stdext::hash_set::rend
- stdext::hash_set::size
- stdext::hash_set::swap
- stdext::hash_set::upper_bound
- stdext::hash_set::value_comp
ms.assetid: c765c06e-cbb6-48c2-93ca-d15468eb28d7
ms.openlocfilehash: becf038678f4abbe285e719e4d1cc1f3f12de982
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689547"
---
# <a name="hash_set-class"></a>hash_set クラス

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

コンテナー クラス hash_set は、C++ 標準 ライブラリの拡張機能です。含まれる要素の値が一意で、キー値として機能するコレクションにおいて、データを格納したり迅速に取得したりするために使用されます。

## <a name="syntax"></a>構文

```cpp
template <class Key,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<Key>>
class hash_set
```

### <a name="parameters"></a>パラメーター

*キー* \
hash_set に格納される要素のデータ型。

*特徴*\
2つの関数オブジェクトを含む型。2つの要素の値を並べ替えキーとして比較してそれらの相対順序を決定できる二項述語と、要素のキー値を符号なしにマップする単項述語であるハッシュ関数の2つの関数オブジェクトが含まれます。`size_t` 型の整数。 この引数は省略可能であり、既定値は `hash_compare<Key, less<Key> >` です。

*アロケーター* \
メモリの hash_set の割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクトを表す型。 この引数は省略可能であり、既定値は `allocator<Key>` です。

## <a name="remarks"></a>Remarks

hash_set は次のようなものです。

- hash_map は連想コンテナーであり、関連付けられたキー値に基づいて要素の値を効率的に取得できるようにする可変サイズのコンテナーとして機能します。 さらに、単純な連想コンテナーです。これは、要素値がキー値であるためです。

- 反転することができます。これは、hash_map には、要素にアクセスするための双方向反復子が用意されているためです。

- ハッシュされます。これは、要素のキー値に適用されたハッシュ関数の値に基づいて、要素がバケットにグループ化されるためです。

- 一意のクラスです。これは、各要素が一意のキーを持つ必要があるためです。 hash_set は単純な連想コンテナーでもあるため、要素も一意です。

- クラステンプレートは、提供される機能がジェネリックであり、要素またはキーとして含まれる特定のデータ型に依存しないためです。 要素やキーに使用されているデータ型は、クラス テンプレートで比較関数やアロケーターと共にパラメーターとして指定されます。

並べ替えでのハッシュの主な利点は、効率に優れていることです。コンテナー内にある要素を並べ替えるとき、その時間は要素の数の対数に比例しますが、適切なハッシュを実行すると、挿入、削除、検索にかかる平均時間は一定しています。 set 内の要素の値は直接変更できません。 代わりに、以前の値を削除し、新しい値の要素を挿入する必要があります。

一般的に、コンテナー型の選択は、アプリケーションにおいて必要な検索および挿入の種類に基づいている必要があります。 ハッシュされた連想コンテナーは、検索、挿入、削除の各操作用に最適化されています。 これらの操作を明示的にサポートするメンバー関数は、適切に記述されたハッシュ関数と共に使用すると、効率的に機能します。検索、挿入、削除の操作にかかる実行時間は、平均で一定しており、コンテナー内の要素の数による影響を受けません。 適切に記述されたハッシュ関数によって、ハッシュ値の一様分布が生成され、競合の数を最小限に抑えることができます (競合は、異なるキー値が同じハッシュ値にマップされたときに発生する可能性があります)。 最悪のケースは、不適切に記述されたハッシュ関数が使用される場合です。演算の回数は、シーケンス内の要素数に比例して増えることになります (線形時間)。

値とキーを関連付ける条件をアプリケーションが満たしている場合、hash_set は最適な連想コンテナーとなっている必要があります。 hash_set の要素は一意であり、独自の並べ替えキーとして機能します。 この種類の構造体のモデルは、単語が 1 回だけ出現する可能性がある単語の順序付きのリストです。 キーワードを複数設定できる場合は、hash_multiset が適切なコンテナー構造体となります。 値が一意のキーワードのリストにアタッチされている必要がある場合、hash_map がこのデータを格納するのに適切な構造体です。 キーが一意でない場合は、hash_multimap が最適なコンテナーです。

Hash_set は、 [value_compare](#value_compare)型の格納されたハッシュ `Traits` オブジェクトを呼び出すことによって、制御するシーケンスを並べ替えます。 格納されているこのオブジェクトには、メンバー関数 [key_comp](#key_comp) を呼び出すことによってアクセスできます。 このような関数オブジェクトは、*hash_compare<Key, less\<Key> >* クラスのオブジェクトと同様に動作する必要があります。 具体的には、Key 型の `key` すべての値について、呼び出しの特徴 (`key`) は size_t 型の値の分布を生成します。

通常、要素は、この順序を確立するために小なり比較だけを実行できる必要があります。これにより、2 つの要素が指定されたときに、それらの要素が等しいか (どちらか一方が小さくはない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 テクニカル ノートでは、比較関数は、数学上の標準的な意味で厳密弱順序を発生させる二項述語であると示されています。 二項述語 *f*( *x*, *y*) は、2 つの引数オブジェクト (x および y) と戻り値 (true または false) を持つ関数オブジェクトです。 hash_set に適用される順序付けは、二項述語が非再帰、反対称、推移的であり、等価性が推移的である (2 つのオブジェクト (*x* と *y*) が、*f*( *x*, *y*) と *f*( *y*, *x*) の両方が false の場合に等価になるように定義されている) 場合、厳密弱順序になります。 2 つのキーの等値に関する条件が等価性の条件よりも厳しく、優先される場合、順序付けは完全な順序付け (すべての要素が相互の値に基づいて並べ替えられる) となり、一致するそれぞれのキーを識別するのが難しくなります。

被制御シーケンスにおける要素の実際の順序は、ハッシュ関数、順序関数、コンテナー オブジェクトに格納されるハッシュ テーブルの現在のサイズによって異なります。 ハッシュ テーブルの現在のサイズは特定できないため、通常は、被制御シーケンス内の要素の順序を予測することはできません。 要素を挿入しても反復子の有効性は失われません。また、要素を削除した場合は、削除された要素を具体的に指す反復子だけが無効化されます。

hash_set クラスに用意されている反復子は双方向反復子ですが、クラス メンバー関数 [insert](#insert) と [hash_set](#hash_set) には、弱い入力反復子をテンプレート パラメーターとして取得するバージョンがあります。この反復子の機能に関する要件は、双方向反復子のクラスで保証されている要件よりも低くなっています。 これらの反復子の機能に差異があるのは、反復子の概念が異なっているためです。 反復子の各概念には、反復子独自の一連の要件が含まれています。また、それらの要件を使用するアルゴリズムでは、反復子の種類ごとに指定されている要件に対して、前提を絞り込む必要があります。 たとえば、一部のオブジェクトを参照するために入力反復子が逆参照される可能性があることを前提とする場合があります。さらに、シーケンス内にある次の反復子に対して逆参照が増加する可能性があることを前提とする場合もあります。 このことは、最小限実施することですが、クラス メンバー関数のコンテキストに含まれる反復子の範囲 [ `first`, `last`) について明確にすることも重要です。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[hash_set](#hash_set)|空の `hash_set`、または他の `hash_set` の全体または一部のコピーである hash_multiset を構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[allocator_type](#allocator_type)|`allocator` オブジェクトの `hash_set` クラスを表す型。|
|[const_iterator](#const_iterator)|`const` 内の 1 つの `hash_set` 要素を読み取ることができる双方向反復子を提供する型。|
|[const_pointer](#const_pointer)|@No__t_1 内の**const**要素へのポインターを提供する型。|
|[const_reference](#const_reference)|読み取りと**const**操作の実行のために `hash_set` に格納されている**const**要素への参照を提供する型。|
|[const_reverse_iterator](#const_reverse_iterator)|@No__t_1 内の任意の**const**要素を読み取ることができる双方向反復子を提供する型。|
|[difference_type](#difference_type)|`hash_set` の要素の数を、反復子が指す要素の範囲に基づいて表すために使用できる符号付き整数型。|
|[Iterator](#iterator)|`hash_set` 内の任意の要素を読み取り、または変更できる双方向反復子を提供する型。|
|[key_compare](#key_compare)|2 つの並べ替えキーを比較して、`hash_set` 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。|
|[key_type](#key_type)|並べ替えキーとしてキャパシティ内に `hash_set` の要素として格納されるオブジェクトを表す型。|
|[pointer](#pointer)|`hash_set` 内の要素へのポインターを提供する型。|
|[reference](#reference)|`hash_set` に格納されている要素への参照を提供する型。|
|[reverse_iterator](#reverse_iterator)|反転された `hash_set` 内の 1 つの要素を読み取り、または変更できる双方向反復子を提供する型。|
|[size_type](#size_type)|`hash_set` 内の要素の数を表すことができる符号なし整数型。|
|[value_compare](#value_compare)|2 つの関数オブジェクト、すなわち、`hash_set` の 2 つの要素の値を比較してその相対順序を判断できるクラス比較の二項述語と、要素のハッシュを計算する単項述語を提供する型です。|
|[value_type](#value_type)|値としてキャパシティ内に `hash_set` の要素として格納されるオブジェクトを表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[begin](#begin)|`hash_set` 内の最初の要素を指す反復子を返します。|
|[cbegin](#cbegin)|`hash_set` 内の最初の要素を指す定数反復子を返します。|
|[cend](#cend)|`hash_set` 内の最後の要素の次の位置を指す定数反復子を返します。|
|[clear](#clear)|`hash_set` のすべての要素を消去します。|
|[count](#count)|パラメーター指定したキーに一致するキーを持つ、`hash_set` 内の要素の数を返します。|
|[crbegin](#crbegin)|反転された `hash_set` 内の最初の要素を指す定数反復子を返します。|
|[crend](#crend)|反転された `hash_set` 内の最後の要素の次の位置を指す定数反復子を返します。|
|[emplace](#emplace)|インプレースで構築された要素を `hash_set` に挿入します。|
|[emplace_hint](#emplace_hint)|インプレースで構築された要素を、配置ヒントと共に `hash_set` に挿入します。|
|[empty](#empty)|`hash_set` が空かどうかをテストします。|
|[end](#end)|`hash_set` 内の最後の要素の次の位置を指す反復子を返します。|
|[equal_range](#equal_range)|指定したキーよりも大きいキーを持つ、`hash_set` 内の最初の要素を指す反復子と、およびそのキー以上のキーを持つ、`hash_set` 内の最初の要素を指す反復子のペアを返します。|
|[erase](#erase)|`hash_set` 内の要素または要素の範囲を指定した位置から削除するか、または指定したキーと一致する要素を削除します。|
|[find](#find)|指定したキーと同じキーを持つ、`hash_set` 内の要素の位置を指す反復子を返します。|
|[get_allocator](#get_allocator)|`allocator` の構築に使用される `hash_set` オブジェクトのコピーを返します。|
|[insert](#insert)|`hash_set` に要素または要素範囲を挿入します。|
|[key_comp](#key_comp)|`hash_set` 内のキーを並べ替えるために使用される比較オブジェクトのコピーを取得します。|
|[lower_bound](#lower_bound)|指定したキー以上のキーを持つ、`hash_set` 内の最初の要素を指す反復子を返します。|
|[max_size](#max_size)|`hash_set` の最大長を返します。|
|[rbegin](#rbegin)|反転された `hash_set` 内の最初の要素を指す反復子を返します。|
|[rend](#rend)|反転された `hash_set` 内の最後の要素の次の位置を指す反復子を返します。|
|[size](#size)|`hash_set` 内の要素数を返します。|
|[swap](#swap)|2 つの `hash_set` の要素を交換します。|
|[upper_bound](#upper_bound)|指定したキー以上のキーを持つ、`hash_set` 内の最初の要素を指す反復子を返します。|
|[value_comp](#value_comp)|`hash_set` の要素キー値をハッシュおよび順序付けするために使用するハッシュ特性オブジェクトのコピーを取得します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[hash_set::operator=](#op_eq)|別の `hash_set` のコピーで `hash_set` の要素を置き換えます。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<hash_set>

**名前空間:** stdext

## <a name="allocator_type"></a>  hash_set::allocator_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set オブジェクトのアロケーター クラスを表す型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Remarks

`allocator_type` は、テンプレートパラメーター*アロケーター*のシノニムです。

*アロケーター*の詳細については、 [hash_set クラス](../standard-library/hash-set-class.md)のトピックの「解説」を参照してください。

### <a name="example"></a>例

`allocator_type` の使用例については、[get_allocator](#get_allocator) の例をご覧ください。

## <a name="begin"></a>  hash_set::begin

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set 内の最初の要素を指す反復子を返します。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>戻り値

hash_set 内の最初の要素、または空の hash_set の次の位置を指す双方向反復子。

### <a name="remarks"></a>Remarks

@No__t_0 の戻り値が `const_iterator` に割り当てられている場合、hash_set オブジェクト内の要素は変更できません。 @No__t_0 の戻り値が `iterator` に割り当てられている場合は、hash_set オブジェクトの要素を変更できます。

### <a name="example"></a>例

```cpp
// hash_set_begin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.begin( );
   cout << "The first element of hs1 is " << *hs1_Iter << endl;

   hs1_Iter = hs1.begin( );
   hs1.erase( hs1_Iter );

   // The following 2 lines would err because the iterator is const
   // hs1_cIter = hs1.begin( );
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.begin( );
   cout << "The first element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The first element of hs1 is 1
The first element of hs1 is now 2
```

## <a name="cbegin"></a>  hash_set::cbegin

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set 内の最初の要素を指す定数反復子を返します。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

[hash_set](../standard-library/hash-set-class.md) 内の最初の要素、または空の `hash_set` の次の位置を指す定数双方向反復子。

### <a name="remarks"></a>Remarks

`cbegin` の戻り値で `hash_set` オブジェクト内の要素を変更することはできません。

### <a name="example"></a>例

```cpp
// hash_set_cbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_iterator hs1_cIter;

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

## <a name="cend"></a>  hash_set::cend

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set 内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>戻り値

[hash_set](../standard-library/hash-set-class.md) リスト内の最後の要素の次の位置を指す定数双方向反復子。 `hash_set` が空の場合は、`hash_set::cend == hash_set::begin`。

### <a name="remarks"></a>Remarks

`cend` は、反復子が `hash_set` の末尾に達したかどうかをテストするために使用します。 `cend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// hash_set_cend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_cIter;

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

## <a name="clear"></a>  hash_set::clear

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set のすべての要素を消去します。

```cpp
void clear();
```

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_set_clear.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 1 );
   hs1.insert( 2 );

   cout << "The size of the hash_set is initially " << hs1.size( )
        << "." << endl;

   hs1.clear( );
   cout << "The size of the hash_set after clearing is "
        << hs1.size( ) << "." << endl;
}
```

```Output
The size of the hash_set is initially 2.
The size of the hash_set after clearing is 0.
```

## <a name="const_iterator"></a>  hash_set::const_iterator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set の 1 つの **const** 要素を読み取ることができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Remarks

`const_iterator` 型で要素の値を変更することはできません。

### <a name="example"></a>例

`const_iterator` の使用例については、[begin](#begin) の例をご覧ください。

## <a name="const_pointer"></a>  hash_set::const_pointer

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set 内の **const** 要素へのポインターを提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Remarks

`const_pointer` 型で要素の値を変更することはできません。

ほとんどの場合、**const** hash_set オブジェクト内の要素にアクセスするには、[const_iterator](#const_iterator) を使用する必要があります。

## <a name="const_reference"></a>  hash_set::const_reference

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

読み取りと **const** 操作の実行のために、hash_set に格納された **const** 要素への参照を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_set_const_ref.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a const_reference &Ref1
   // to the 1st element
   const int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The following line would cause an error because the
   // const_reference cannot be used to modify the hash_set
   // Ref1 = Ref1 + 5;
}
```

```Output
The first element in the hash_set is 10.
```

## <a name="const_reverse_iterator"></a>  hash_set::const_reverse_iterator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set の 任意の **const** 要素を読み取ることができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Remarks

`const_reverse_iterator` 型は要素の値を変更できず、逆の順序で hash_set を反復処理するために使用します。

### <a name="example"></a>例

`const_reverse_iterator` の宣言方法や使用方法の例については、[rend](#rend) の例をご覧ください。

## <a name="count"></a>  hash_set::count

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

パラメーター指定したキーに一致するキーを持つ、hash_set 内の要素の数を返します。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
照合される hash_set の要素のキー。

### <a name="return-value"></a>戻り値

並べ替えキーがパラメーター キーと一致する要素が hash_set に含まれている場合は 1。

hash_set に一致するキーを持つ要素が含まれていない場合は 0。

### <a name="remarks"></a>Remarks

メンバー関数は、次の範囲内の要素の数を返します。

\[ lower_bound (*キー*)、upper_bound (*キー*))。

### <a name="example"></a>例

hash_set::count メンバー関数の使用例を次に示します。

```cpp
// hash_set_count.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1;
    hash_set<int>::size_type i;

    hs1.insert(1);
    hs1.insert(1);

    // Keys must be unique in hash_set, so duplicates are ignored.
    i = hs1.count(1);
    cout << "The number of elements in hs1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hs1.count(2);
    cout << "The number of elements in hs1 with a sort key of 2 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hs1 with a sort key of 1 is: 1.
The number of elements in hs1 with a sort key of 2 is: 0.
```

## <a name="crbegin"></a>  hash_set::crbegin

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

反転された hash_set 内の最初の要素を指す定数反復子を返します。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>戻り値

反転された [hash_set](../standard-library/hash-set-class.md) 内の最初の要素を示す、または反転されていない `hash_set` 内の最後の要素だったものを示す定数逆順双方向反復子。

### <a name="remarks"></a>Remarks

hash_set で [hash_set::begin](#begin) が使用されるように、`crbegin` は、反転された hash_set で使用されます。

戻り値が `crbegin` の場合、`hash_set` オブジェクトは変更できません。

`crbegin` を使用して、`hash_set` 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// hash_set_crbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
```

## <a name="crend"></a>  hash_set::crend

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

反転された hash_set 内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>戻り値

逆順の [hash_set](../standard-library/hash-set-class.md) 内の最後の要素の次の場所 (通常の順序の `hash_set` 内の最初の要素の前の場所) を指す定数逆順双方向反復子。

### <a name="remarks"></a>Remarks

`crend` は、[hash_set::end](#end) が `hash_set` で使われるときと同様の方法で、反転された `hash_set` で使われます。

戻り値が `crend` の場合、`hash_set` オブジェクトは変更できません。

`crend` を使用して、逆順反復子が `hash_set` の末尾に達したかどうかをテストできます。

### <a name="example"></a>例

```cpp
// hash_set_crend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_crIter = hs1.crend( );
   hs1_crIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_crIter << "." << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
```

## <a name="difference_type"></a>  hash_set::difference_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set の要素の数を、反復子が指す要素の範囲に基づいて表すために使用できる符号付き整数型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Remarks

`difference_type` は、コンテナーの反復子を減算またはインクリメントするときに返される型です。 通常、`difference_type` は、[ `first`, `last`) の範囲内で、反復子 `first` と `last` の間にある要素の数を表すために使用され、`first` が指す要素と、`last` が指す要素の 1 つ前までの範囲の要素を含みます。

`difference_type` は、入力反復子の要件を満たすすべての反復子 (set などの反転可能なコンテナーによってサポートされる双方向反復子のクラスを含む) に対して使用できますが、反復子間の減算は、vector や deque などのランダム アクセス コンテナーによって提供される、ランダム アクセス反復子によってのみサポートされます。

### <a name="example"></a>例

```cpp
// hash_set_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_set>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter, hs1_bIter, hs1_eIter;

   hs1.insert( 20 );
   hs1.insert( 10 );
   hs1.insert( 20 );   // Won't insert as hash_set elements are unique

   hs1_bIter = hs1.begin( );
   hs1_eIter = hs1.end( );

   hash_set <int>::difference_type   df_typ5, df_typ10, df_typ20;

   df_typ5 = count( hs1_bIter, hs1_eIter, 5 );
   df_typ10 = count( hs1_bIter, hs1_eIter, 10 );
   df_typ20 = count( hs1_bIter, hs1_eIter, 20 );

   // The keys, and hence the elements, of a hash_set are unique,
   // so there is at most one of a given value
   cout << "The number '5' occurs " << df_typ5
        << " times in hash_set hs1.\n";
   cout << "The number '10' occurs " << df_typ10
        << " times in hash_set hs1.\n";
   cout << "The number '20' occurs " << df_typ20
        << " times in hash_set hs1.\n";

   // Count the number of elements in a hash_set
   hash_set <int>::difference_type  df_count = 0;
   hs1_Iter = hs1.begin( );
   while ( hs1_Iter != hs1_eIter)
   {
      df_count++;
      hs1_Iter++;
   }

   cout << "The number of elements in the hash_set hs1 is: "
        << df_count << "." << endl;
}
```

```Output
The number '5' occurs 0 times in hash_set hs1.
The number '10' occurs 1 times in hash_set hs1.
The number '20' occurs 1 times in hash_set hs1.
The number of elements in the hash_set hs1 is: 2.
```

## <a name="emplace"></a>  hash_set::emplace

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

インプレースで構築された要素を hash_set に挿入します。

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*val*|挿入される要素が `hash_set` にまだ含まれていない場合、より一般的には、キーが同じ順序付けになる要素がまだ含まれていない場合に、[hash_set](../standard-library/hash-set-class.md) に挿入される要素の値。|

### <a name="return-value"></a>戻り値

@No__t_0 メンバー関数は、挿入が行われた場合に**true**を返す**ブール**値のペアを返します。また、キー `hash_set` が順序で同じ値を持ち、その反復子を持つ要素が既に含まれている場合は**false**を返します。コンポーネントは、新しい要素が挿入されたアドレス、または要素が既に配置されているアドレスを返します。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_set_emplace.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.emplace(move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="emplace_hint"></a>  hash_set::emplace_hint

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

インプレースで構築された要素を hash_set に挿入します。

```cpp
template <class ValTy>
iterator emplace(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*val*|挿入される要素が `hash_set` にまだ含まれていない場合、より一般的には、キーが同じ順序付けになる要素がまだ含まれていない場合に、[hash_set](../standard-library/hash-set-class.md) に挿入される要素の値。|
|*場所 (_s)*|正しい挿入ポイントの検索を開始する場所 (挿入ポイントがの直後*にある場合*は、対数時間ではなく、償却定数時間で挿入できます)。|

### <a name="return-value"></a>戻り値

[hash_set::emplace](#emplace) メンバー関数は、`hash_set` に新しい要素が挿入された位置、または、同等の順序での既存の要素が存在する位置を指す反復子を返します。

### <a name="remarks"></a>Remarks

挿入ポイントが *(Where)* の直後にある場合、挿入は対数時間ではなく、償却定数時間で実行できます。

### <a name="example"></a>例

```cpp
// hash_set_emplace_hint.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<string> hs3;
   string str1("a");

   hs3.insert(hs3.begin(), move(str1));
   cout << "After the emplace insertion, hs3 contains "
      << *hs3.begin() << "." << endl;
}
```

```Output
After the emplace insertion, hs3 contains a.
```

## <a name="empty"></a>  hash_set::empty

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set が空かどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

hash_set が空の場合は **true**、hash_set が空ではない場合は **false**。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_set_empty.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2;
   hs1.insert ( 1 );

   if ( hs1.empty( ) )
      cout << "The hash_set hs1 is empty." << endl;
   else
      cout << "The hash_set hs1 is not empty." << endl;

   if ( hs2.empty( ) )
      cout << "The hash_set hs2 is empty." << endl;
   else
      cout << "The hash_set hs2 is not empty." << endl;
}
```

```Output
The hash_set hs1 is not empty.
The hash_set hs2 is empty.
```

## <a name="end"></a>  hash_set::end

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set 内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>戻り値

hash_set 内の最後の要素の次の位置を指す双方向反復子。 hash_set が空の場合は、hash_set::end == hash_set::begin。

### <a name="remarks"></a>Remarks

`end` は、反復子が hash_set の末尾に達したかどうかをテストするために使用されます。 `end` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// hash_set_end.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: iterator hs1_Iter;
   hash_set <int> :: const_iterator hs1_cIter;

   hs1.insert( 1 );
   hs1.insert( 2 );
   hs1.insert( 3 );

   hs1_Iter = hs1.end( );
   hs1_Iter--;
   cout << "The last element of hs1 is " << *hs1_Iter << endl;

   hs1.erase( hs1_Iter );

   // The following 3 lines would err because the iterator is const:
   // hs1_cIter = hs1.end( );
   // hs1_cIter--;
   // hs1.erase( hs1_cIter );

   hs1_cIter = hs1.end( );
   hs1_cIter--;
   cout << "The last element of hs1 is now " << *hs1_cIter << endl;
}
```

```Output
The last element of hs1 is 3
The last element of hs1 is now 2
```

## <a name="equal_range"></a>  hash_set::equal_range

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

指定したキーと同じキーを持つ、hash_set 内の最初の要素を指す反復子と、そのキーよりも大きいいキーを持つ、hash_set 内の最初の要素を指す反復子のペアを返します。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の hash_set 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

1 番目がそのキーの [lower_bound](../standard-library/set-class.md#lower_bound)、2 番目がそのキーの [upper_bound](../standard-library/set-class.md#upper_bound) である、反復子のペア。

メンバー関数によって返されたペア pr の最初の反復子にアクセスするには、`pr` を使用します。 **最初**に、下限の反復子を逆参照するには、\* (`pr` を使用します。 **最初**)。 メンバー関数によって返さ `pr` ペアの2番目の反復子にアクセスするには、`pr` を使用します。 **次**に、上限の反復子を逆参照するには、\* (`pr` を使用します。 **2 番目**)。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_set_equal_range.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_set<int> IntHSet;
   IntHSet hs1;
   hash_set <int> :: const_iterator hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   pair <IntHSet::const_iterator, IntHSet::const_iterator> p1, p2;
   p1 = hs1.equal_range( 20 );

   cout << "The upper bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.second) << "." << endl;

   cout << "The lower bound of the element with "
        << "a key of 20 in the hash_set hs1 is: "
        << *(p1.first) << "." << endl;

   // Compare the upper_bound called directly
   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "A direct call of upper_bound( 20 ) gives "
        << *hs1_RcIter << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 20 )." << endl;

   p2 = hs1.equal_range( 40 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hs1.end( ) ) && ( p2.second == hs1.end( ) ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than or equal to 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key >= 40 is: "
           << *(p1.first) << "." << endl;
}
```

```Output
The upper bound of the element with a key of 20 in the hash_set hs1 is: 30.
The lower bound of the element with a key of 20 in the hash_set hs1 is: 20.
A direct call of upper_bound( 20 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 20 ).
The hash_set hs1 doesn't have an element with a key greater than or equal to 40.
```

## <a name="erase"></a>  hash_set::erase

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set 内の要素または要素の範囲を指定した位置から削除するか、または指定したキーと一致する要素を削除します。

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>パラメーター

@No__t_1 の*場所 (_c)*
hash_set から削除する要素の位置。

*最初*の \
hash_set から削除する最初の要素の位置。

*最後*の \
hash_set から削除する最後の要素の次の位置。

*キー* \
hash_set から削除する要素のキー。

### <a name="return-value"></a>戻り値

最初の 2 つのメンバー関数の場合は、削除された要素の後の最初の残存要素を指定する双方向反復子、または hash_set の末尾へのポインター (残存要素が存在しない場合)。 3 番目のメンバー関数の場合は、hash_set から削除された要素の数。

### <a name="remarks"></a>Remarks

メンバー関数が例外をスローすることはありません。

### <a name="example"></a>例

hash_set::erase メンバー関数の使用例を次に示します。

```cpp
// hash_set_erase.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_set<int> hs1, hs2, hs3;
    hash_set<int>::iterator pIter, Iter1, Iter2;
    int i;
    hash_set<int>::size_type n;

    for (i = 1; i < 5; i++)
    {
        hs1.insert (i);
        hs2.insert (i * i);
        hs3.insert (i - 1);
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hs1.begin();
    hs1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_set hs1 is:";
    for (pIter = hs1.begin(); pIter != hs1.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hs2.begin();
    Iter2 = --hs2.end();
    hs2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_set hs2 is:";
    for (pIter = hs2.begin(); pIter != hs2.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hs3.erase(2);

    cout << "After the element with a key of 2 is deleted, "
         << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hs3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hs3.begin();
    hs3.erase(Iter1);

    cout << "After another element (unique for hash_set) with a key "
         << endl;
    cout  << "equal to that of the 2nd element is deleted, "
          << "the hash_set hs3 is:";
    for (pIter = hs3.begin(); pIter != hs3.end(); pIter++)
        cout << " " << *pIter;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_set hs1 is: 1 3 4.
After the middle two elements are deleted, the hash_set hs2 is: 16 4.
After the element with a key of 2 is deleted, the hash_set hs3 is: 0 1 3.
The number of elements removed from hs3 is: 1.
After another element (unique for hash_set) with a key
equal to that of the 2nd element is deleted, the hash_set hs3 is: 0 3.
```

## <a name="find"></a>  hash_set::find

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

指定したキーと同じキーを持つ、hash_set 内の要素の位置を指す反復子を返します。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の hash_set 内の要素の並べ替えキーによって照合される引数キー。

### <a name="return-value"></a>戻り値

指定したキーと等しい要素の位置を指す `iterator` または `const_iterator`。キーの一致が検出されない場合は、hash_set 内の最後の要素の次の位置を指す。

### <a name="remarks"></a>Remarks

このメンバー関数は、hash_set 内の要素をアドレス指定する反復子を返します。この要素は、並べ替えキーが、小なり比較関係に基づいて順序を誘発する二項述語の下にある引数キーに `equivalent` されます。

@No__t_0 の戻り値が `const_iterator` に割り当てられている場合、hash_set オブジェクトを変更することはできません。 @No__t_0 の戻り値が `iterator` に割り当てられている場合は、hash_set オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// hash_set_find.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.find( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.find( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // The element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.find( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>  hash_set::get_allocator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set の構築に使用されるアロケーター オブジェクトのコピーを返します。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>戻り値

テンプレートパラメーター*アロケーター*であるメモリを管理するために hash_set によって使用されるアロケーター。

*アロケーター*の詳細については、 [hash_set クラス](../standard-library/hash-set-class.md)のトピックの「解説」を参照してください。

### <a name="remarks"></a>Remarks

hash_set クラスのアロケーターは、クラスがどのようにストレージを管理するかを指定します。 C++ 標準ライブラリ コンテナー クラスで提供される既定のアロケーターは、ほとんどのプログラミング要件に対応しています。 独自のアロケーター クラスを作成して使用することは、C++ における高度な作業の 1 つです。

### <a name="example"></a>例

```cpp
// hash_set_get_allocator.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   // The following lines declare objects
   // that use the default allocator.
   hash_set <int, hash_compare <int, less<int> > > hs1;
   hash_set <int,  hash_compare <int, greater<int> > > hs2;
   hash_set <double, hash_compare <double,
      less<double> >, allocator<double> > hs3;

   hash_set <int, hash_compare <int,
      greater<int> > >::allocator_type hs2_Alloc;
   hash_set <double>::allocator_type hs3_Alloc;
   hs2_Alloc = hs2.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs1.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hs3.max_size( ) <<  "." << endl;

   // The following lines create a hash_set hs4
   // with the allocator of hash_set hs1.
   hash_set <int>::allocator_type hs4_Alloc;
   hash_set <int> hs4;
   hs4_Alloc = hs2.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hs2_Alloc == hs4_Alloc )
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

## <a name="hash_set"></a>  hash_set::hash_set

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

空の `hash_set`、または他の `hash_set` の全体または一部のコピーである hash_multiset を構築します。

```cpp
hash_set();

explicit hash_set(
    const Traits& Comp);

hash_set(
    const Traits& Comp,
    const Allocator& Al);

hash_set(
    const hash_set<Key, Traits, Allocator>& Right);

hash_set(
    hash_set&& Right);

hash_set(
    initializer_list<Type> IList);

hash_set(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_set(
    initializer_list<value_type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_set(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*ウムアルクラ*|この `hash_set` オブジェクトに使用するストレージ アロケーター クラス。既定では、`Allocator` です。|
|*コンペティション*|`const Traits` 内の要素の並べ替えに使用される、`hash_set` 型の比較関数。既定では `hash_compare` です。|
|*右*|構築された `hash_set` のコピー元となる `hash_set`。|
|*まずは*|コピーする要素範囲内の最初の要素の位置。|
|*前の*|コピーする要素範囲を超える最初の要素の位置。|

### <a name="remarks"></a>Remarks

すべてのコンストラクターは、アロケーター オブジェクトの型を格納します。このオブジェクトは `hash_set` のメモリ ストレージを管理し、後で [hash_set::get_allocator](#get_allocator) を呼び出して取得することができます。 代替アロケーターの代わりに使用されるクラス宣言やプリプロセス マクロでは、アロケーターのパラメーターが省略される場合があります。

すべてのコンストラクターは、それぞれの hash_sets を初期化します。

すべてのコンストラクターは、`Traits` 型の関数オブジェクトを格納します。このオブジェクトは `hash_set` のキーの順序を確立するために使用され、後で [hash_set::key_comp](#key_comp) を呼び出して取得することができます。 `Traits` の詳細については、[hash_set クラス](../standard-library/hash-set-class.md)のトピックをご覧ください。

1 番目のコンストラクターは、空の初期 `hash_set` を作成します。2 番目のコンストラクターは要素の順序を確立するために使用する比較関数の型 (`Comp`) を指定し、3 番目のコンストラクターは使用するアロケーターの型 (`Al`) を明示的に指定します。 キーワード `explicit` は、特定の種類の自動型変換が実行されないようにします。

4 番目と 5 番目のコンストラクターは、`hash_set` `Right` のコピーを指定します。

最後の 6 番目、7 番目、および 8 番目のコンストラクターは、要素の initializer_list を使用します。

最後のコンストラクターは、`hash_set` の範囲 [ `First`, `Last`) をコピーします。下のコンストラクターになるほど、より明確に比較関数の型の Traits クラスとアロケーターの型が指定されています。

8 番目のコンストラクターは、`hash_set` `Right` を移動します。

`hash_set` コンテナー内にある要素の実際の順序は、ハッシュ関数、順序関数、ハッシュ テーブルの現在のサイズに応じて異なります。順序関数のみによって要素の順序が決定されるセット コンテナーとは異なり、通常は要素の順序を予測できません。

## <a name="insert"></a>  hash_set::insert

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

`hash_set` に要素または要素範囲を挿入します。

```cpp
pair<iterator, bool> insert(
    const value_type& Val);

iterator insert(
    iterator Where,
    const value_type& Val);

void insert(
    initializer_list<value_type> IList)
template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*Val*|挿入される要素が `hash_set` にまだ含まれていない場合、より一般的には、キーが同じ順序付けになる要素がまだ含まれていない場合に、`hash_set` に挿入される要素の値。|
|*Where*|正しい挿入ポイントの検索を開始する場所 (挿入ポイントが `_Where` の直後にある場合、挿入処理は対数時間ではなく償却定数時間で実行できます)。|
|*まずは*|`hash_set` からコピーされる最初の要素の位置。|
|*前の*|`hash_set` からコピーされる最後の要素の次の位置。|
|*IList*|要素のコピー元の initializer_list。|

### <a name="return-value"></a>戻り値

最初の `insert` メンバー関数は、挿入が行われた場合に**true**を返す**ブール**値のペアを返します。また、キー `hash_set` が順序で同じ値を持ち、その反復子を持つ要素が既に含まれている場合は**false**を返します。コンポーネントは、新しい要素が挿入されたアドレス、または要素が既に配置されているアドレスを返します。

このメンバー関数によって返されたペア `pr` の反復子コンポーネントにアクセスするには `pr.first` を使用し、この反復子を逆参照するには `*(pr.first)` を使用します。 このメンバー関数によって返される `pr` ペアの**bool**要素にアクセスするには、`pr.second` を使用し、逆参照するには `*(pr.second)` を使用します。

2 番目の `insert` メンバー関数は、`hash_set` に新しい要素が挿入された位置を指す反復子を返します。

### <a name="remarks"></a>Remarks

3 番目のメンバー関数は initializer_list の要素を挿入します。

3 番目のメンバー関数は、指定した `hash_set` の範囲 [ `First`, `Last`) 内の反復子が指す各要素に対応する `hash_set` に要素値のシーケンスを挿入します。

## <a name="iterator"></a>  hash_set::iterator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set 内の任意の要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Remarks

@No__t_0 型を使用して、要素の値を変更できます。

### <a name="example"></a>例

`iterator` の宣言方法や使用方法の例については、[begin](#begin) の例をご覧ください。

## <a name="key_comp"></a>  hash_set::key_comp

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set の要素キー値をハッシュおよび順序付けするために使用するハッシュ特性オブジェクトのコピーを取得します。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>戻り値

Hash_set が要素の並べ替えに使用する関数オブジェクトを返します。これは、テンプレートパラメーターの*特徴*です。

*特徴*の詳細については、 [hash_set クラス](../standard-library/hash-set-class.md)のトピックを参照してください。

### <a name="remarks"></a>Remarks

格納されているオブジェクトはメンバー関数を定義します。

`bool operator( const Key& _xVal, const Key& _yVal );`

これは、並べ替え順で `_xVal` が `_yVal` に先行しかつ等しくない場合に **true** を返します。

[key_compare](#key_compare) および [value_compare](#value_compare) は両方ともテンプレート パラメーター *Traits* のシノニムです。 どちらも hash_set および hash_multiset クラスで使用でき、そこでは同一ですが、hash_map および hash_multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

```cpp
// hash_set_key_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > >hs1;
   hash_set<int, hash_compare < int, less<int> > >::key_compare kc1
          = hs1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true, "
           << "where kc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false "
           << "where kc1 is the function object of hs1."
        << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::key_compare
         kc2 = hs2.key_comp( ) ;
   bool result2 = kc2( 2, 3 ) ;
   if(result2 == true)
   {
      cout << "kc2( 2,3 ) returns value of true, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false, "
           << "where kc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="key_compare"></a>  hash_set::key_compare

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

2 つの並べ替えキーを比較して、hash_set 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Remarks

`key_compare` は、テンプレートパラメーターの*特徴*のシノニムです。

*特徴*の詳細については、 [hash_set クラス](../standard-library/hash-set-class.md)のトピックを参照してください。

`key_compare` および [value_compare](#value_compare) は両方ともテンプレート パラメーター *Traits* のシノニムです。 どちらも set および multiset クラスで使用でき、そこでは同一ですが、map および multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

`key_compare` の宣言方法や使用方法の例については、[key_comp](#key_comp) の例をご覧ください。

## <a name="key_type"></a>  hash_set::key_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

並べ替えキーとしてキャパシティ内に hash_set の要素として格納されるオブジェクトを表す型。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Remarks

`key_type` は、テンプレートパラメーター*キー*のシノニムです。

*キー*の詳細については、 [hash_set クラス](../standard-library/hash-set-class.md)のトピックの「解説」を参照してください。

`key_type` および [value_type](#value_type) は両方ともテンプレート パラメーター *Key* のシノニムです。 どちらも hash_set および hash_multiset クラスで使用でき、そこでは同一ですが、hash_map および hash_multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

`key_type` の宣言方法や使用方法の例については、[value_type](#value_type) の例をご覧ください。

## <a name="lower_bound"></a>  hash_set::lower_bound

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

指定したキー以上のキーを持つ、hash_set 内の最初の要素を指す反復子を返します。

```cpp
const_iterator lower_bound(const Key& key) const;

iterator lower_bound(const Key& key);
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の hash_set 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

引数キー以上のキーを持つ hash_set 内の要素の位置を指す、または、キーの一致が検出されない場合は hash_set 内の最後の要素の次の位置を指す、`iterator` または `const_iterator`。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_set_lower_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.lower_bound( 20 );
   cout << "The element of hash_set hs1 with a key of 20 is: "
        << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.lower_bound( 40 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key of 40." << endl;
   else
      cout << "The element of hash_set hs1 with a key of 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator that addresses the location
   hs1_AcIter = hs1.end( );
   hs1_AcIter--;
   hs1_RcIter = hs1.lower_bound( *hs1_AcIter );
   cout << "The element of hs1 with a key matching "
        << "that of the last element is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The element of hash_set hs1 with a key of 20 is: 20.
The hash_set hs1 doesn't have an element with a key of 40.
The element of hs1 with a key matching that of the last element is: 30.
```

## <a name="max_size"></a>  hash_set::max_size

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set の最大長を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

hash_set の可能な最大長。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_set_max_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::size_type i;

   i = hs1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_set is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  hash_set::operator=

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set の要素を、別の hash_set のコピーで置き換えます。

```cpp
hash_set& operator=(const hash_set& right);

hash_set& operator=(hash_set&& right);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*right*|`hash_set` にコピーする [hash_set](../standard-library/hash-set-class.md)。|

### <a name="remarks"></a>Remarks

@No__t_0 内の既存の要素を消去した後、 *`operator=` の内容*を `hash_set` にコピーまたは移動します。

### <a name="example"></a>例

```cpp
// hash_set_operator_as.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set<int> v1, v2, v3;
   hash_set<int>::iterator iter;

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

## <a name="pointer"></a>  hash_set::pointer

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set 内の要素へのポインターを提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Remarks

@No__t_0 型を使用して、要素の値を変更できます。

ほとんどの場合、hash_set オブジェクト内の要素にアクセスするには、[反復子](#iterator)を使用する必要があります。

## <a name="rbegin"></a>  hash_set::rbegin

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

反転された hash_set 内の最初の要素を指す反復子を返します。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>戻り値

反転された hash_set 内の最初の要素を示す、または反転されていない hash_set 内の最後の要素だったものを示す逆順双方向反復子。

### <a name="remarks"></a>Remarks

hash_set で [begin](#begin) が使用されるように、`rbegin` は、反転された hash_set で使用されます。

`rbegin` の戻り値が `const_reverse_iterator` に割り当てられる場合は、hash_set オブジェクトを変更できません。 `rbegin` の戻り値が `reverse_iterator` に割り当てられる場合は、hash_set オブジェクトを変更できます。

`rbegin` を使用して、hash_set 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// hash_set_rbegin.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rbegin( );
   cout << "The first element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // begin can be used to start an iteration
   // through a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << endl;

   // rbegin can be used to start an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << endl;

   // A hash_set element can be erased by dereferencing to its key
   hs1_rIter = hs1.rbegin( );
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_set is "<< *hs1_rIter << "."
        << endl;
}
```

```Output
The first element in the reversed hash_set is 30.
The hash_set is: 10 20 30
The reversed hash_set is: 30 20 10
After the erasure, the first element in the reversed hash_set is 20.
```

## <a name="reference"></a>  hash_set::reference

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set に格納されている要素への参照を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_set_reference.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;

   hs1.insert( 10 );
   hs1.insert( 20 );

   // Declare and initialize a reference &Ref1 to the 1st element
   int &Ref1 = *hs1.begin( );

   cout << "The first element in the hash_set is "
        << Ref1 << "." << endl;

   // The value of the 1st element of the hash_set can be changed
   // by operating on its (non-const) reference
   Ref1 = Ref1 + 5;

   cout << "The first element in the hash_set is now "
        << *hs1.begin() << "." << endl;
}
```

```Output
The first element in the hash_set is 10.
The first element in the hash_set is now 15.
```

## <a name="rend"></a>  hash_set::rend

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

反転された hash_set 内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>戻り値

逆順の hash_set 内の最後の要素の次の場所 (通常の順序の hash_set 内の最初の要素の前の場所) を指す逆順双方向反復子。

### <a name="remarks"></a>Remarks

hash_set で [end](#end) が使用されるように、`rend` は、反転された hash_set で使用されます。

`rend` の戻り値が `const_reverse_iterator` に割り当てられる場合は、hash_set オブジェクトを変更できません。 `rend` の戻り値が `reverse_iterator` に割り当てられる場合は、hash_set オブジェクトを変更できます。 `rend` によって返された値は逆参照しないでください。

`rend` を使用して、逆順反復子が hash_set の末尾に達したかどうかをテストできます。

### <a name="example"></a>例

```cpp
// hash_set_rend.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;
   hash_set <int>::reverse_iterator hs1_rIter;
   hash_set <int>::const_reverse_iterator hs1_crIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "The last element in the reversed hash_set is "
        << *hs1_rIter << "." << endl;

   // end can be used to terminate an iteration
   // through a hash_set in a forward order
   cout << "The hash_set is: ";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( );
         hs1_Iter++ )
      cout << *hs1_Iter << " ";
   cout << "." << endl;

   // rend can be used to terminate an iteration
   // through a hash_set in a reverse order
   cout << "The reversed hash_set is: ";
   for ( hs1_rIter = hs1.rbegin( ) ; hs1_rIter != hs1.rend( );
         hs1_rIter++ )
      cout << *hs1_rIter << " ";
   cout << "." << endl;

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   hs1.erase ( *hs1_rIter );

   hs1_rIter = hs1.rend( );
   hs1_rIter--;
   cout << "After the erasure, the last element in the "
        << "reversed hash_set is " << *hs1_rIter << "."
        << endl;
}
```

```Output
The last element in the reversed hash_set is 10.
The hash_set is: 10 20 30 .
The reversed hash_set is: 30 20 10 .
After the erasure, the last element in the reversed hash_set is 20.
```

## <a name="reverse_iterator"></a>  hash_set::reverse_iterator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

反転された hash_set 内の 1 つの要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Remarks

型 `reverse_iterator` は、逆の順序で hash_set を反復処理するために使用します。

### <a name="example"></a>例

`reverse_iterator` の宣言方法や使用方法の例については、[rbegin](#rbegin) の例を参照してください。

## <a name="size"></a>  hash_set::size

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set 内の要素の数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

hash_set の現在の長さ。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_set_size.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: size_type i;

   hs1.insert( 1 );
   i = hs1.size( );
   cout << "The hash_set length is " << i << "." << endl;

   hs1.insert( 2 );
   i = hs1.size( );
   cout << "The hash_set length is now " << i << "." << endl;
}
```

```Output
The hash_set length is 1.
The hash_set length is now 2.
```

## <a name="size_type"></a>  hash_set::size_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set 内の要素の数を表すことができる符号なし整数型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

`size_type` の宣言方法や使用方法の例については、[size](#size) の例をご覧ください。

## <a name="swap"></a>  hash_set::swap

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

2 つの hash_set の要素を交換します。

```cpp
void swap(hash_set& right);
```

### <a name="parameters"></a>パラメーター

*右*\
ターゲットの hash_set と交換する要素を提供する引数の hash_set。

### <a name="remarks"></a>Remarks

メンバー関数は、要素を交換する 2 つの hash_set において要素を指定している参照、ポインター、反復子を無効にすることはありません。

### <a name="example"></a>例

```cpp
// hash_set_swap.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1, hs2, hs3;
   hash_set <int>::iterator hs1_Iter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );
   hs2.insert( 100 );
   hs2.insert( 200 );
   hs3.insert( 300 );

   cout << "The original hash_set hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;

   // This is the member function version of swap
   hs1.swap( hs2 );

   cout << "After swapping with hs2, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hs1, hs3 );

   cout << "After swapping with hs3, list hs1 is:";
   for ( hs1_Iter = hs1.begin( ); hs1_Iter != hs1.end( );
         hs1_Iter++ )
         cout << " " << *hs1_Iter;
   cout   << "." << endl;
}
```

```Output
The original hash_set hs1 is: 10 20 30.
After swapping with hs2, list hs1 is: 200 100.
After swapping with hs3, list hs1 is: 300.
```

## <a name="upper_bound"></a>  hash_set::upper_bound

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

指定したキーよりも大きいキーを持つ、hash_set 内の最初の要素を指す反復子を返します。

```cpp
const_iterator upper_bound(const Key& key) const;

iterator upper_bound(const Key& key);
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の hash_set 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

引数キー以上のキーを持つ hash_set 内の要素の位置を指す、またはキーの一致が検出されない場合は hash_set 内の最後の要素の次の位置を指す、`iterator` または `const_iterator`。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_set_upper_bound.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int> :: const_iterator hs1_AcIter, hs1_RcIter;

   hs1.insert( 10 );
   hs1.insert( 20 );
   hs1.insert( 30 );

   hs1_RcIter = hs1.upper_bound( 20 );
   cout << "The first element of hash_set hs1 with a key greater "
        << "than 20 is: " << *hs1_RcIter << "." << endl;

   hs1_RcIter = hs1.upper_bound( 30 );

   // If no match is found for the key, end( ) is returned
   if ( hs1_RcIter == hs1.end( ) )
      cout << "The hash_set hs1 doesn't have an element "
           << "with a key greater than 30." << endl;
   else
      cout << "The element of hash_set hs1 with a key > 40 is: "
           << *hs1_RcIter << "." << endl;

   // An element at a specific location in the hash_set can be found
   // by using a dereferenced iterator addressing the location
   hs1_AcIter = hs1.begin( );
   hs1_RcIter = hs1.upper_bound( *hs1_AcIter );
   cout << "The first element of hs1 with a key greater than "
        << endl << "that of the initial element of hs1 is: "
        << *hs1_RcIter << "." << endl;
}
```

```Output
The first element of hash_set hs1 with a key greater than 20 is: 30.
The hash_set hs1 doesn't have an element with a key greater than 30.
The first element of hs1 with a key greater than
that of the initial element of hs1 is: 20.
```

## <a name="value_comp"></a>  hash_set::value_comp

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

hash_set 内の要素の値を並べ替えるために使用される比較オブジェクトのコピーを取得します。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>戻り値

Hash_set が要素の並べ替えに使用する関数オブジェクトを返します。これは、テンプレートパラメーターの*比較*です。

*比較*の詳細については、 [hash_set クラス](../standard-library/hash-set-class.md)のトピックの「解説」を参照してください。

### <a name="remarks"></a>Remarks

格納されているオブジェクトはメンバー関数を定義します。

`bool operator( const Key& _xVal, const Key& _yVal );`

これは、並べ替え順で `_xVal` が `_yVal` に先行しかつ等しくない場合に **true** を返します。

[Value_compare](../standard-library/set-class.md#value_compare)と[key_compare](../standard-library/set-class.md#key_compare)の両方がテンプレートパラメーター*比較*のシノニムであることに注意してください。 どちらも hash_set および hash_multiset クラスで使用でき、そこでは同一ですが、hash_map および hash_multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

```cpp
// hash_set_value_comp.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_set <int, hash_compare < int, less<int> > > hs1;
   hash_set <int, hash_compare < int, less<int> >  >::value_compare
      vc1 = hs1.value_comp( );
   bool result1 = vc1( 2, 3 );
   if( result1 == true )
   {
      cout << "vc1( 2,3 ) returns value of true, "
           << "where vc1 is the function object of hs1."
           << endl;
   }
   else
   {
      cout << "vc1( 2,3 ) returns value of false, "
           << "where vc1 is the function object of hs1."
           << endl;
   }

   hash_set <int, hash_compare < int, greater<int> > > hs2;
   hash_set<int, hash_compare < int, greater<int> > >::value_compare
      vc2 = hs2.value_comp( );
   bool result2 = vc2( 2, 3 );
   if( result2 == true )
   {
      cout << "vc2( 2,3 ) returns value of true, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
   else
   {
      cout << "vc2( 2,3 ) returns value of false, "
           << "where vc2 is the function object of hs2."
           << endl;
   }
}
```

## <a name="value_compare"></a>  hash_set::value_compare

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

2 つの関数オブジェクト、すなわち、hash_set の 2 つの要素の値を比較してその相対順序を判断できるクラス比較の二項述語と、要素のハッシュを計算する単項述語を提供する型です。

```cpp
typedef key_compare value_compare;
```

### <a name="remarks"></a>Remarks

`value_compare` は、テンプレートパラメーターの*特徴*のシノニムです。

*特徴*の詳細については、 [hash_set クラス](../standard-library/hash-set-class.md)のトピックを参照してください。

[Key_compare](#key_compare)と `value_compare` は両方ともテンプレートパラメーターの*特徴*のシノニムです。 どちらも hash_set および hash_multiset クラスで使用でき、そこでは同一ですが、hash_map および hash_multimap クラスでは異なるものなので互換性を保つようになっています。

### <a name="example"></a>例

`value_compare` の宣言方法や使用方法の例については、[value_comp](#value_comp) の例をご覧ください。

## <a name="value_type"></a>  hash_set::value_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_set クラス](../standard-library/unordered-set-class.md)を使用してください。

値としてキャパシティ内に hash_set の要素として格納されるオブジェクトを表す型。

```cpp
typedef Key value_type;
```

### <a name="example"></a>例

```cpp
// hash_set_value_type.cpp
// compile with: /EHsc
#include <hash_set>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_set <int> hs1;
   hash_set <int>::iterator hs1_Iter;

   hash_set <int> :: value_type hsvt_Int;   // Declare value_type
   hsvt_Int = 10;             // Initialize value_type

   hash_set <int> :: key_type hskt_Int;   // Declare key_type
   hskt_Int = 20;             // Initialize key_type

   hs1.insert( hsvt_Int );         // Insert value into hs1
   hs1.insert( hskt_Int );         // Insert key into hs1

   // A hash_set accepts key_types or value_types as elements
   cout << "The hash_set has elements:";
   for ( hs1_Iter = hs1.begin( ) ; hs1_Iter != hs1.end( ); hs1_Iter++)
      cout << " " << *hs1_Iter;
   cout << "." << endl;
}
```

```Output
The hash_set has elements: 10 20.
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
