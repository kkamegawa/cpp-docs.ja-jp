---
title: hash_multimap クラス
ms.date: 10/18/2018
f1_keywords:
- hash_map/stdext::hash_multimap
- hash_map/stdext::hash_multimap::allocator_type
- hash_map/stdext::hash_multimap::const_iterator
- hash_map/stdext::hash_multimap::const_pointer
- hash_map/stdext::hash_multimap::const_reference
- hash_map/stdext::hash_multimap::const_reverse_iterator
- hash_map/stdext::hash_multimap::difference_type
- hash_map/stdext::hash_multimap::iterator
- hash_map/stdext::hash_multimap::key_compare
- hash_map/stdext::hash_multimap::key_type
- hash_map/stdext::hash_multimap::mapped_type
- hash_map/stdext::hash_multimap::pointer
- hash_map/stdext::hash_multimap::reference
- hash_map/stdext::hash_multimap::reverse_iterator
- hash_map/stdext::hash_multimap::size_type
- hash_map/stdext::hash_multimap::value_type
- hash_map/stdext::hash_multimap::begin
- hash_map/stdext::hash_multimap::cbegin
- hash_map/stdext::hash_multimap::cend
- hash_map/stdext::hash_multimap::clear
- hash_map/stdext::hash_multimap::count
- hash_map/stdext::hash_multimap::crbegin
- hash_map/stdext::hash_multimap::crend
- hash_map/stdext::hash_multimap::emplace
- hash_map/stdext::hash_multimap::emplace_hint
- hash_map/stdext::hash_multimap::empty
- hash_map/stdext::hash_multimap::end
- hash_map/stdext::hash_multimap::equal_range
- hash_map/stdext::hash_multimap::erase
- hash_map/stdext::hash_multimap::find
- hash_map/stdext::hash_multimap::get_allocator
- hash_map/stdext::hash_multimap::insert
- hash_map/stdext::hash_multimap::key_comp
- hash_map/stdext::hash_multimap::lower_bound
- hash_map/stdext::hash_multimap::max_size
- hash_map/stdext::hash_multimap::rbegin
- hash_map/stdext::hash_multimap::rend
- hash_map/stdext::hash_multimap::size
- hash_map/stdext::hash_multimap::swap
- hash_map/stdext::hash_multimap::upper_bound
- hash_map/stdext::hash_multimap::value_comp
helpviewer_keywords:
- stdext::hash_multimap
- stdext::hash_multimap::allocator_type
- stdext::hash_multimap::const_iterator
- stdext::hash_multimap::const_pointer
- stdext::hash_multimap::const_reference
- stdext::hash_multimap::const_reverse_iterator
- stdext::hash_multimap::difference_type
- stdext::hash_multimap::iterator
- stdext::hash_multimap::key_compare
- stdext::hash_multimap::key_type
- stdext::hash_multimap::mapped_type
- stdext::hash_multimap::pointer
- stdext::hash_multimap::reference
- stdext::hash_multimap::reverse_iterator
- stdext::hash_multimap::size_type
- stdext::hash_multimap::value_type
- stdext::hash_multimap::begin
- stdext::hash_multimap::cbegin
- stdext::hash_multimap::cend
- stdext::hash_multimap::clear
- stdext::hash_multimap::count
- stdext::hash_multimap::crbegin
- stdext::hash_multimap::crend
- stdext::hash_multimap::emplace
- stdext::hash_multimap::emplace_hint
- stdext::hash_multimap::empty
- stdext::hash_multimap::end
- stdext::hash_multimap::equal_range
- stdext::hash_multimap::erase
- stdext::hash_multimap::find
- stdext::hash_multimap::get_allocator
- stdext::hash_multimap::insert
- stdext::hash_multimap::key_comp
- stdext::hash_multimap::lower_bound
- stdext::hash_multimap::max_size
- stdext::hash_multimap::rbegin
- stdext::hash_multimap::rend
- stdext::hash_multimap::size
- stdext::hash_multimap::swap
- stdext::hash_multimap::upper_bound
- stdext::hash_multimap::value_comp
ms.assetid: f41a6db9-67aa-43a3-a3c5-dbfe9ec3ae7d
ms.openlocfilehash: b42dd5ba4aa3df12e3ef1aba930b2214dde19756
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687973"
---
# <a name="hash_multimap-class"></a>hash_multimap クラス

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

コンテナー クラスの hash_multimap は、C++ 標準ライブラリの拡張機能であり、並べ替えキーとデータ値のペアを要素として持つコレクションのデータを格納したり迅速に取得したりするために使用されます。キーの値は、一意である必要も関連するデータ値である必要もありません。

## <a name="syntax"></a>構文

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare <Key, less <Key>>,
    class Allocator=allocator <pair  <const Key, Type>>>
class hash_multimap
```

### <a name="parameters"></a>パラメーター

*キー* \
hash_multimap に格納されるキーのデータ型。

*型*\
hash_multimap に格納される要素のデータ型。

*特徴*\
2つの関数オブジェクトを含む型。2つの要素の値を並べ替えキーとして比較してその相対順序を決定できるクラスの*特徴*の1つであり、要素のキー値を符号なし整数にマッピングする単項述語であるハッシュ関数です。「`size_t`」と入力します。 この引数は省略可能であり、既定値は `hash_compare<Key, less<Key>>` です。

*アロケーター* \
メモリの hash_multimap の割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクトを表す型。 この引数は省略可能であり、既定値は `allocator<pair <const Key, Type>>` です。

## <a name="remarks"></a>Remarks

hash_multimap の特徴を次に示します。

- hash_map は連想コンテナーであり、関連付けられたキー値に基づいて要素の値を効率的に取得できるようにする可変サイズのコンテナーとして機能します。

- 反転することができます。これは、hash_map には、要素にアクセスするための双方向反復子が用意されているためです。

- ハッシュされます。これは、要素のキー値に適用されたハッシュ関数の値に基づいて、要素がバケットにグループ化されるためです。

- 複数対応です。要素は一意のキーを持つ必要がないので、関連する多くの要素データ値を 1 つのキー値が持つことができるためです。

- ペアを保持する連想コンテナーです。これは、要素値とキー値が分かれているためです。

- クラステンプレート。提供される機能はジェネリックであり、要素またはキーとして含まれる特定のデータ型には依存しません。 要素やキーに使用されているデータ型は、クラス テンプレートで比較関数やアロケーターと共にパラメーターとして指定されます。

並べ替えでのハッシュの主な利点は、効率に優れていることです。コンテナー内にある要素を並べ替えるとき、その時間は要素の数の対数に比例しますが、適切なハッシュを実行すると、挿入、削除、検索にかかる平均時間は一定しています。 hash_multimap の要素の値 (関連するキー値ではありません) は、直接変更できます。 この場合、変更前の要素に関連付けられていたキー値を削除し、新しい要素に関連付けられる新しいキー値を挿入する必要があります。

一般的に、コンテナー型の選択は、アプリケーションにおいて必要な検索および挿入の種類に基づいている必要があります。 ハッシュされた連想コンテナーは、検索、挿入、削除の各操作用に最適化されています。 これらの操作を明示的にサポートするメンバー関数は、適切に記述されたハッシュ関数と共に使用すると、効率的に機能します。検索、挿入、削除の操作にかかる実行時間は、平均で一定しており、コンテナー内の要素の数による影響を受けません。 適切に記述されたハッシュ関数によって、ハッシュ値の一様分布が生成され、競合の数を最小限に抑えることができます (競合は、異なるキー値が同じハッシュ値にマップされたときに発生する可能性があります)。 最悪のケースは、不適切に記述されたハッシュ関数が使用される場合です。演算の回数は、シーケンス内の要素数に比例して増えることになります (線形時間)。

hash_multimap は、値とキーを関連付ける条件をアプリケーションが満たしている場合、最適な連想コンテナーです。 この種類の構造体のモデルとなるのは、キー ワードとそれに関連する文字列値 (たとえば定義) の順序付きリストです。キー ワードは常に一意に定義されるわけではありません。 そうでなくて、キー ワードが一意に定義され、キーが一意になる場合は、hash_map が最適なコンテナーです。 また、キーワードのリストだけが格納される場合は、hash_set が適切なコンテナーとなります。 キーワードを複数設定できる場合は、hash_multiset が適切なコンテナー構造体となります。

hash_multimap は、格納されているハッシュ `Traits` オブジェクト ([value_compare](../standard-library/value-compare-class.md) 型) を呼び出すことによって、制御するシーケンスを並べ替えます。 格納されているこのオブジェクトには、メンバー関数 [key_comp](../standard-library/hash-map-class.md#key_comp) を呼び出すことによってアクセスできます。 このような関数オブジェクトは、[hash_compare](../standard-library/hash-compare-class.md)`<Key, less<Key>>` クラスのオブジェクトと同様に動作する必要があります。 具体的には、`Key` 型のすべての `Key` の値に対して、`Traits (Key)` を呼び出すことにより、`size_t` 型の値を配布します。

通常、要素は、この順序を確立するために小なり比較だけを実行できる必要があります。これにより、2 つの要素が指定されたときに、それらの要素が等しいか (どちらか一方が小さくはない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 テクニカル ノートでは、比較関数は、数学上の標準的な意味で厳密弱順序を発生させる二項述語であると示されています。 二項述語 f (x, y) は、2つの引数オブジェクト `x` および `y` と、戻り値 ( **true**または**false**) を持つ関数オブジェクトです。 Hash_multimap に適用される順序付けは、二項述語が反対称、、および推移的であり、等価性が推移的である場合 (2 つの `x` オブジェクトと `y` が f (x, y) と f (y) の両方で等価になるように定義されている場合) に厳密弱順序です。, x) が**false**です。 2 つのキーの等値に関する条件が等価性の条件よりも厳しく、優先される場合、順序付けは完全な順序付け (すべての要素が相互の値に基づいて並べ替えられる) となり、一致するそれぞれのキーを識別するのが難しくなります。

被制御シーケンスにおける要素の実際の順序は、ハッシュ関数、順序関数、コンテナー オブジェクトに格納されるハッシュ テーブルの現在のサイズによって異なります。 ハッシュ テーブルの現在のサイズは特定できないため、通常は、被制御シーケンス内の要素の順序を予測することはできません。 要素を挿入しても反復子の有効性は失われません。また、要素を削除した場合は、削除された要素を具体的に指す反復子だけが無効化されます。

hash_multimap クラスに用意されている反復子は双方向反復子ですが、クラス メンバー関数 [insert](#insert) と [hash_multimap](#hash_multimap) には、弱い入力反復子をテンプレート パラメーターとして取得するバージョンがあります。この反復子の機能に関する要件は、双方向反復子のクラスで保証されている要件よりも低くなっています。 これらの反復子の機能に差異があるのは、反復子の概念が異なっているためです。 反復子の各概念には、反復子独自の要件の hash_multimap が含まれています。また、それらの要件を使用するアルゴリズムでは、反復子の種類ごとに指定されている要件で前提を絞り込む必要があります。 たとえば、一部のオブジェクトを参照するために入力反復子が逆参照される可能性があることを前提とする場合があります。さらに、シーケンス内にある次の反復子に対して逆参照が増加する可能性があることを前提とする場合もあります。 このことは、機能の最小限の hash_multimap ですが、メンバー関数のコンテキストに含まれる反復子の範囲 `[First, Last)` について明確にするには十分です。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[hash_multimap](#hash_multimap)|特定のサイズのリスト、特定の値の要素を持つリスト、または特定の `allocator` を持つリストを構築します。あるいは他の `hash_multimap` のコピーとして構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[allocator_type](#allocator_type)|`allocator` オブジェクトの `hash_multimap` クラスを表す型。|
|[const_iterator](#const_iterator)|`const` 内の 1 つの `hash_multimap` 要素を読み取ることができる双方向反復子を提供する型。|
|[const_pointer](#const_pointer)|@No__t_1 内の**const**要素へのポインターを提供する型。|
|[const_reference](#const_reference)|読み取りと**const**操作の実行のために `hash_multimap` に格納されている**const**要素への参照を提供する型。|
|[const_reverse_iterator](#const_reverse_iterator)|@No__t_1 内の任意の**const**要素を読み取ることができる双方向反復子を提供する型。|
|[difference_type](#difference_type)|`hash_multimap` の要素の数を、反復子が指す要素の範囲に基づいて表すために使用できる符号付き整数型。|
|[Iterator](#iterator)|`hash_multimap` 内の任意の要素を読み取り、または変更できる双方向反復子を提供する型。|
|[key_compare](#key_compare)|2 つの並べ替えキーを比較して、`hash_multimap` 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。|
|[key_type](#key_type)|`hash_multimap` の各要素の一部である並べ替えキー オブジェクトを表す型。|
|[mapped_type](#mapped_type)|`hash_multimap` に格納されているデータ型を表す型。|
|[pointer](#pointer)|`hash_multimap` 内の要素へのポインターを提供する型。|
|[reference](#reference)|`hash_multimap` に格納されている要素への参照を提供する型。|
|[reverse_iterator](#reverse_iterator)|反転された `hash_multimap` 内の 1 つの要素を読み取り、または変更できる双方向反復子を提供する型。|
|[size_type](#size_type)|`hash_multimap` 内の要素の数を表すことができる符号なし整数型。|
|[value_type](#value_type)|2 つの要素を並べ替えキーとして比較して、`hash_multimap` 内の要素の相対順序を決定できる関数オブジェクトを提供する型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[begin](#begin)|`hash_multimap` 内の最初の要素を指す反復子を返します。|
|[cbegin](#cbegin)|`hash_multimap` 内の最初の要素を指す定数反復子を返します。|
|[cend](#cend)|`hash_multimap` 内の最後の要素の次の位置を指す定数反復子を返します。|
|[clear](#clear)|`hash_multimap` のすべての要素を消去します。|
|[count](#count)|パラメーター指定したキーに一致するキーを持つ、`hash_multimap` 内の要素の数を返します。|
|[crbegin](#crbegin)|反転された `hash_multimap` 内の最初の要素を指す定数反復子を返します。|
|[crend](#crend)|反転された `hash_multimap` 内の最後の要素の次の位置を指す定数反復子を返します。|
|[emplace](#emplace)|インプレースで構築された要素を `hash_multimap` に挿入します。|
|[emplace_hint](#emplace_hint)|インプレースで構築された要素を、配置ヒントと共に `hash_multimap` に挿入します。|
|[empty](#empty)|`hash_multimap` が空かどうかをテストします。|
|[end](#end)|`hash_multimap` 内の最後の要素の次の位置を指す反復子を返します。|
|[equal_range](#equal_range)|`hash_multimap` 内の最後の要素の次の位置を指す反復子を返します。|
|[erase](#erase)|指定した位置から `hash_multimap` 内の要素または要素範囲を削除します。|
|[find](#find)|指定したキーと同じキーを持つ、`hash_multimap` 内の要素の位置を指す反復子を返します。|
|[get_allocator](#get_allocator)|`allocator` の構築に使用される `hash_multimap` オブジェクトのコピーを返します。|
|[insert](#insert)|指定した位置において、`hash_multimap` に単一の要素または要素の範囲を挿入します。|
|[key_comp](#key_comp)|`hash_multimap` 内のキーを並べ替えるために使用される比較オブジェクトのコピーを取得します。|
|[lower_bound](#lower_bound)|指定したキー以上のキー値を持つ、`hash_multimap` 内の最初の要素を指す反復子を返します。|
|[max_size](#max_size)|`hash_multimap` の最大長を返します。|
|[rbegin](#rbegin)|反転された `hash_multimap` 内の最初の要素を指す反復子を返します。|
|[rend](#rend)|反転された `hash_multimap` 内の最後の要素の次の位置を指す反復子を返します。|
|[size](#size)|`hash_multimap` の新しいサイズを指定します。|
|[swap](#swap)|2 つの `hash_multimap` の要素を交換します。|
|[upper_bound](#upper_bound)|指定したキーよりも大きいキー値を持つ、`hash_multimap` 内の最初の要素を指す反復子を返します。|
|[value_comp](#value_comp)|`hash_multimap` 内の要素の値を並べ替えるために使用される比較オブジェクトのコピーを取得します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[hash_multimap::operator=](#op_eq)|別の `hash_multimap` のコピーで `hash_multimap` の要素を置き換えます。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<hash_map>

**名前空間:** stdext

## <a name="allocator_type"></a>  hash_multimap::allocator_type

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap オブジェクトのアロケーター クラスを表す型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="remarks"></a>Remarks

`allocator_type` はテンプレート パラメーター `Allocator` のシノニムです。

`Allocator` の詳細については、[hash_multimap クラス](../standard-library/hash-multimap-class.md)のトピックのコメントに関するセクションをご覧ください。

### <a name="example"></a>例

`allocator_type` の使用例については、[get_allocator](#get_allocator) の例をご覧ください。

## <a name="begin"></a>hash_multimap::begin

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap の 1 つ目の要素を示す反復子を返します。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>戻り値

hash_multimap 内の最初の要素、または空の hash_multimap の次の位置を指す双方向反復子。

### <a name="remarks"></a>Remarks

@No__t_0 の戻り値が `const_iterator` に割り当てられている場合、hash_multimap オブジェクト内の要素は変更できません。 @No__t_0 の戻り値が `iterator` に割り当てられている場合は、hash_multimap オブジェクトの要素を変更できます。

### <a name="example"></a>例

```cpp
// hash_multimap_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is " << hm1_cIter -> first
        << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now " << hm1_cIter -> first
        << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="cbegin"></a>  hash_multimap::cbegin

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap の 1 つ目の要素を示す定数反復子を返します。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

[hash_multimap](../standard-library/hash-multimap-class.md) 内の最初の要素、または空の `hash_multimap` の次の位置を指す定数双方向反復子。

### <a name="example"></a>例

```cpp
// hash_multimap_cbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.cbegin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;
   }
```

```Output
The first element of hm1 is 2.
```

## <a name="cend"></a>  hash_multimap::cend

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap 内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>戻り値

[hash_multimap](../standard-library/hash-multimap-class.md) リスト内の最後の要素の次の位置を指す定数双方向反復子。 `hash_multimap` が空の場合は、`hash_multimap::cend == hash_multimap::begin`。

### <a name="remarks"></a>Remarks

`cend` は、反復子が hash_multimap の末尾に達したかどうかをテストするために使用します。

`cend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// hash_multimap_cend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.cend( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;
   }
```

```Output
The value of last element of hm1 is 30.
```

## <a name="clear"></a>  hash_multimap::clear

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap のすべての要素を消去します。

```cpp
void clear();
```

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

hash_multimap::clear メンバー関数の使用例を次に示します。

```cpp
// hash_multimap_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_multimap is initially "
         << i  << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_multimap after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_multimap is initially 2.
The size of the hash_multimap after clearing is 0.
```

## <a name="const_iterator"></a>  hash_multimap::const_iterator

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap の 1 つの **const** 要素を読み取ることができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Remarks

`const_iterator` 型で要素の値を変更することはできません。

Hash_multimap によって定義された `const_iterator` は、`pair<const Key, Type>` 型の[value_type](#value_type)のオブジェクトを指します。 キーの値はペアの 1 番目のメンバー、マップされた要素の値はペアの 2 番目のメンバーを介して取得できます。

Hash_multimap 内の要素を指す `const_iterator` `cIter` を逆参照するには、`->` 演算子を使用します。

要素のキーの値にアクセスするには、`cIter->first` を使用します。これは `(*cIter).first` と同じです。 要素のマップされた datum の値にアクセスするには、`cIter->second` を使用します。これは `(*cIter).second` と同じです。

### <a name="example"></a>例

`const_iterator` の使用例については、[begin](#begin) の例をご覧ください。

## <a name="const_pointer"></a>  hash_multimap::const_pointer

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap 内の **const** 要素へのポインターを提供する型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Remarks

`const_pointer` 型で要素の値を変更することはできません。

ほとんどの場合、hash_multimap オブジェクト内の要素にアクセスするには、[反復子](#iterator)を使用する必要があります。

## <a name="const_reference"></a>  hash_multimap::const_reference

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

読み取りと **const** 操作の実行のために hash_multimap に格納された **const** 要素への参照を提供する型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_multimap_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin() -> second );

   cout << "The data value of 1st element in the hash_multimap is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of 1st element in the hash_multimap is 10.
```

## <a name="const_reverse_iterator"></a>  hash_multimap::const_reverse_iterator

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap の任意の **const** 要素を読み取ることができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse_iterator const_reverse_iterator;
```

### <a name="remarks"></a>Remarks

`const_reverse_iterator` 型は要素の値を変更できず、逆の順序で hash_multimap を反復処理するために使用します。

Hash_multimap によって定義された `const_reverse_iterator` は、 [value_type](#value_type)のオブジェクトを指します。これは、最初のメンバーが要素のキーであり、2番目 `pair<const Key, Type>` のメンバーが要素に保持されているマップされた datum であることを示します。

Hash_multimap 内の要素を指す `const_reverse_iterator` `crIter` を逆参照するには、`->` 演算子を使用します。

要素のキーの値にアクセスするには、`crIter->first` を使用します。これは `(*crIter).first` と同じです。 要素のマップされた datum の値にアクセスするには、`crIter->second` を使用します。これは `(*crIter).second` と同じです。

### <a name="example"></a>例

`const_reverse_iterator` の宣言方法や使用方法の例については、[rend](#rend) の例をご覧ください。

## <a name="count"></a>  hash_multimap::count

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

パラメーター指定したキーと一致するキーを持つ、hash_multimap 内の要素の数を返します。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
照合される hash_multimap の要素のキー。

### <a name="return-value"></a>戻り値

hash_multimap に、並べ替えキーがパラメーター キーと一致する要素が含まれている場合は 1。hash_multimap に、キーが一致する要素が含まれていない場合は 0。

### <a name="remarks"></a>Remarks

メンバー関数は、

**[lower_bound (** `key` **), upper_bound (** `key` **) )**

キー値*キー*を持つ。

### <a name="example"></a>例

hash_multimap::count メンバー関数の使用例を次に示します。

```cpp
// hash_multimap_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 1));
    hm1.insert(Int_Pair(1, 4));
    hm1.insert(Int_Pair(2, 1));

    // Elements do not need to have unique keys in hash_multimap,
    // so duplicates are allowed and counted
    i = hm1.count(1);
    cout << "The number of elements in hm1 with a sort key of 1 is: "
         << i << "." << endl;

    i = hm1.count(2);
    cout << "The number of elements in hm1 with a sort key of 2 is: "
         << i << "." << endl;

    i = hm1.count(3);
    cout << "The number of elements in hm1 with a sort key of 3 is: "
         << i << "." << endl;
}
```

```Output
The number of elements in hm1 with a sort key of 1 is: 2.
The number of elements in hm1 with a sort key of 2 is: 2.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  hash_multimap::crbegin

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

反転された hash_multimap 内の最初の要素を指す定数反復子を返します。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>戻り値

反転された [hash_multimap](../standard-library/hash-multimap-class.md) 内の最初の要素を示す、または反転されていない `hash_multimap` 内の最後の要素だったものを示す定数逆順双方向反復子。

### <a name="remarks"></a>Remarks

`crbegin` は、[hash_multimap::begin](#begin) が `hash_multimap` で使用されるように、逆順の hash_multimap で使用されます。

戻り値が `crbegin` の場合、`hash_multimap` オブジェクトは変更できません。

`crbegin` を使用して、`hash_multimap` 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// hash_multimap_crbegin.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
```

## <a name="crend"></a>  hash_multimap::crend

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

反転された hash_multimap 内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>戻り値

逆順の [hash_multimap](../standard-library/hash-multimap-class.md) 内の最後の要素の次の場所 (通常の順序の `hash_multimap` 内の最初の要素の前の場所) を指す定数逆順双方向反復子。

### <a name="remarks"></a>Remarks

`crend` は、[hash_multimap::end](#end) が hash_multimap で使用されるように、逆順の hash_multimap で使用されます。

戻り値が `crend` の場合、`hash_multimap` オブジェクトは変更できません。

`crend` を使用して、逆順反復子が hash_multimap の末尾に達したかどうかをテストできます。

`crend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// hash_multimap_crend.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 3.
```

## <a name="difference_type"></a>  hash_multimap::difference_type

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap の要素の数を、反復子が指す要素の範囲に基づいて表すために使用できる符号付き整数型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="remarks"></a>Remarks

`difference_type` は、コンテナーの反復子を減算またはインクリメントするときに返される型です。 通常 `difference_type` は、 *[ first,  last)* の範囲内で、反復子 `first` と `last` の間にある要素の数を表すために使用され、`first` が指す要素と、`last` が指す要素の 1 つ前までの範囲の要素を含みます。

`difference_type` は、入力反復子の要件を満たすすべての反復子 (set などの反転可能なコンテナーによってサポートされる双方向反復子のクラスを含む) に対して使用できますが、反復子間の減算は、vector などのランダム アクセス コンテナーによって提供される、ランダム アクセス反復子によってのみサポートされます。

### <a name="example"></a>例

```cpp
// hash_multimap_difference_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(3, 20));

    // The following will insert, because map keys
    // do not need to be unique
    hm1.insert(Int_Pair(2, 30));

    hash_multimap<int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
    hm1_bIter = hm1.begin();
    hm1_eIter = hm1.end();

    // Count the number of elements in a hash_multimap
    hash_multimap<int, int>::difference_type df_count = 0;
    hm1_Iter = hm1.begin();
    while (hm1_Iter != hm1_eIter)
    {
        df_count++;
        hm1_Iter++;
    }

    cout << "The number of elements in the hash_multimap hm1 is: "
         << df_count << "." << endl;

    cout << "The keys of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> first;
    cout << "." << endl;

    cout << "The values of the mapped elements are:";
    for (hm1_Iter= hm1.begin() ; hm1_Iter!= hm1.end();
        hm1_Iter++)
        cout << " " << hm1_Iter-> second;
    cout << "." << endl;
}
```

```Output
The number of elements in the hash_multimap hm1 is: 4.
The keys of the mapped elements are: 1 2 2 3.
The values of the mapped elements are: 10 20 30 20.
```

## <a name="emplace"></a>  hash_multimap::emplace

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

インプレースで構築された要素を hash_multimap に挿入します。

```cpp
template <class ValTy>
iterator emplace(ValTy&& val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*val*|[hash_multimap](../standard-library/hash-multimap-class.md) に挿入される要素の移動コンストラクトに使用する値。|

### <a name="return-value"></a>戻り値

`emplace` メンバー関数は、新しい要素が挿入された位置を指す反復子を返します。

### <a name="remarks"></a>Remarks

要素の [hash_multimap::value_type](#value_type) はペアを表します。これにより、要素の値は順序付けされたペアになり、このペアの最初のコンポーネントはキー値と同じで、2 番目のコンポーネントは要素のデータ値と同じになります。

### <a name="example"></a>例

```cpp
// hash_multimap_emplace.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
    cout << "After the emplace, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="emplace_hint"></a>  hash_multimap::emplace_hint

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

インプレースで構築された要素を、配置ヒントと共に hash_multimap に挿入します。

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*val*|挿入される要素 (一般的には、キーが同じ順序付けになる要素) が `hash_multimap` にまだ含まれていない場合に、[hash_multimap](../standard-library/hash-multimap-class.md) に挿入される要素の移動コンストラクトに使用する値。|
|*場所 (_s)*|正しい挿入ポイントの検索を開始する場所に関するヒント。|

### <a name="return-value"></a>戻り値

[hash_multimap::emplace](#emplace) メンバー関数は、`hash_multimap` に新しい要素が挿入された位置を指す反復子を返します。

### <a name="remarks"></a>Remarks

要素の [hash_multimap::value_type](#value_type) はペアを表します。これにより、要素の値は順序付けされたペアになり、このペアの最初のコンポーネントはキー値と同じで、2 番目のコンポーネントは要素のデータ値と同じになります。

挿入ポイントが *(Where)* の直後にある場合、挿入は対数時間ではなく、償却定数時間で実行できます。

### <a name="example"></a>例

```cpp
// hash_multimap_emplace_hint.cpp
// compile with: /EHsc
#include<hash_multimap>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
    cout << "After the emplace insertion, hm1 contains:" << endl
      << " " << hm1.begin()->first
      << " => " << hm1.begin()->second
      << endl;
}
```

```Output
After the emplace insertion, hm1 contains:
1 => a
```

## <a name="empty"></a>  hash_multimap::empty

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap が空かどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

hash_multimap が空の場合は **true**。hash_multimap が空ではない場合は **false**。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_multimap_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_multimap hm1 is empty." << endl;
   else
      cout << "The hash_multimap hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_multimap hm2 is empty." << endl;
   else
      cout << "The hash_multimap hm2 is not empty." << endl;
}
```

```Output
The hash_multimap hm1 is not empty.
The hash_multimap hm2 is empty.
```

## <a name="end"></a>  hash_multimap::end

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap 内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>戻り値

hash_multimap リスト内の最後の要素の次の位置を指す双方向反復子。 hash_multimap が空の場合は、hash_multimap::end == hash_multimap::begin。

### <a name="remarks"></a>Remarks

`end` は、反復子が hash_multimap の末尾に達したかどうかをテストするために使用します。

`end` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// hash_multimap_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is "
        << hm1_cIter -> second << "." << endl;

   hm1_Iter = hm1.end( );
   hm1_Iter--;
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.end ( );
   // hm1_cIter--;
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.end( );
   hm1_cIter--;
   cout << "The value of last element of hm1 is now "
        << hm1_cIter -> second << "." << endl;
}
```

```Output
The value of last element of hm1 is 30.
The value of last element of hm1 is now 20.
```

## <a name="equal_range"></a>  hash_multimap::equal_range

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

指定したキーよりも大きいキーを持つ、hash_multimap 内の最初の要素を指す反復子と、そのキー以上のキーを持つ、hash_multimap 内の最初の要素を指す反復子のペアを返します。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の hash_multimap 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

1 番目がそのキーの [lower_bound](#lower_bound)、2 番目がそのキーの [upper_bound](#upper_bound) である、反復子のペア。

メンバー関数によって返されるペア `pr` 最初の反復子にアクセスするには、`pr` を使用します。 **最初**に、下限の反復子を逆参照するには、\* (`pr` を使用します。 **最初**)。 メンバー関数によって返さ `pr` ペアの2番目の反復子にアクセスするには、`pr` を使用します。 **次**に、上限の反復子を逆参照するには、\* (`pr` を使用します。 **2 番目**)。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_multimap_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_multimap <int, int> IntMMap;
   IntMMap hm1;
   hash_multimap <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMMap::const_iterator, IntMMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with a key of 2\n"
        << "in the hash_multimap hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with a key of 2\n"
        << "in the hash_multimap hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair "
        << "returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key less than 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2
in the hash_multimap hm1 is: 20.
The upper bound of the element with a key of 2
in the hash_multimap hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_multimap hm1 doesn't have an element with a key less than 4.
```

## <a name="erase"></a>  hash_multimap::erase

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap 内の要素または要素の範囲を指定した位置から削除するか、または指定したキーと一致する要素を削除します。

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>パラメーター

@No__t_1 の*場所 (_c)*
hash_multimap から削除する要素の位置。

*最初*の \
hash_multimap から削除する最初の要素の位置。

*最後*の \
hash_multimap から削除する最後の要素の次の位置。

*キー* \
hash_multimap から削除する要素のキー。

### <a name="return-value"></a>戻り値

最初の 2 つのメンバー関数の場合は、削除された要素の後に残った最初の要素、またはそのような要素が存在しない場合は hash_multimap の末尾へのポインターを指定する、双方向反復子。

3 番目のメンバー関数の場合は、hash_multimap から削除された要素の数を返します。

### <a name="remarks"></a>Remarks

メンバー関数が例外をスローすることはありません。

### <a name="example"></a>例

hash_multimap::erase メンバー関数の使用例を次に示します。

```cpp
// hash_multimap_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2, hm3;
    hash_multimap<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_multimap<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i) );
        hm2.insert(Int_Pair (i, i*i) );
        hm3.insert(Int_Pair (i, i-1) );
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, "
         << "the hash_multimap hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_multimap hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    hm3.insert(Int_Pair (2, 5));
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that of the"
         << endl;
    cout  << "2nd element is deleted, "
          << "the hash_multimap hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_multimap hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_multimap hm2 is: 1 16.
After the element with a key of 2 is deleted,
the hash_multimap hm3 is: 0 2 3.
The number of elements removed from hm3 is: 2.
After another element with a key equal to that of the
2nd element is deleted, the hash_multimap hm3 is: 0 3.
```

## <a name="find"></a>  hash_multimap::find

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

指定したキーと同じキーを持つ、hash_multimap 内の要素の最初の位置を指す反復子を返します。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の hash_multimap 内の要素の並べ替えキーによって照合されるキー。

### <a name="return-value"></a>戻り値

指定したキーを持つ要素の最初の位置を指す反復子。キーの一致が検出されない場合は、hash_multimap 内の最後の要素の次の位置。

### <a name="remarks"></a>Remarks

このメンバー関数は、hash_multimap 内の要素をアドレス指定する反復子を返します。この要素は、並べ替えキーが、小なり比較関係に基づいて順序を誘発する二項述語の下にある引数キーに `equivalent` されます。

`find` の戻り値が `const_iterator` に割り当てられている場合、hash_multimap オブジェクトは変更できません。 @No__t_0 の戻り値が `iterator` に割り当てられている場合は、hash_multimap オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// hash_multimap_find.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1;
    hash_multimap<int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 20));
    hm1.insert(Int_Pair(3, 30));

    hm1_RcIter = hm1.find(2);
    cout << "The element of hash_multimap hm1 with a key of 2 is: "
          << hm1_RcIter -> second << "." << endl;

    hm1_RcIter = hm1.find(3);
    cout << "The first element of hash_multimap hm1 with a key of 3 is: "
          << hm1_RcIter -> second << "." << endl;

    // If no match is found for the key, end() is returned
    hm1_RcIter = hm1.find(4);

    if (hm1_RcIter == hm1.end())
        cout << "The hash_multimap hm1 doesn't have an element "
             << "with a key of 4." << endl;
    else
        cout << "The element of hash_multimap hm1 with a key of 4 is: "
             << hm1_RcIter -> second << "." << endl;

    // The element at a specific location in the hash_multimap can be
    // found using a dereferenced iterator addressing the location
    hm1_AcIter = hm1.end();
    hm1_AcIter--;
    hm1_RcIter = hm1.find(hm1_AcIter -> first);
    cout << "The first element of hm1 with a key matching"
         << endl << "that of the last element is: "
         << hm1_RcIter -> second << "." << endl;

    // Note that the first element with a key equal to
    // the key of the last element is not the last element
    if (hm1_RcIter == --hm1.end())
        cout << "This is the last element of hash_multimap hm1."
             << endl;
    else
        cout << "This is not the last element of hash_multimap hm1."
             << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="get_allocator"></a>  hash_multimap::get_allocator

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap の構築に使用されるアロケーター オブジェクトのコピーを返します。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>戻り値

hash_multimap で使用されるアロケーター。

### <a name="remarks"></a>Remarks

hash_multimap クラスのアロケーターは、クラスがどのようにストレージを管理するかを指定します。 C++ 標準ライブラリ コンテナー クラスで提供される既定のアロケーターは、ほとんどのプログラミング要件に対応しています。 独自のアロケーター クラスを作成して使用することは、C++ における高度な作業の 1 つです。

### <a name="example"></a>例

```cpp
// hash_multimap_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int>::allocator_type hm1_Alloc;
   hash_multimap <int, int>::allocator_type hm2_Alloc;
   hash_multimap <int, double>::allocator_type hm3_Alloc;
   hash_multimap <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> hm2;
   hash_multimap <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << " before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_multimap hm4
   // with the allocator of hash_multimap hm1.
   hash_multimap <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated by the other
   if( hm1_Alloc == hm4_Alloc )
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

## <a name="hash_multimap"></a>  hash_multimap::hash_multimap

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

空の hash_multimap を構築するか、他の hash_multimap の全体または一部のコピーである hash_multimap を構築します。

```cpp
hash_multimap();

explicit hash_multimap(
    const Compare& Comp);

hash_multimap(
    const Compare& Comp,
    const Allocator& Al);

hash_multimap(
    const hash_multimap& Right);

hash_multimap(
    hash_multimap&& Right);

hash_multimap(
    initializer_list<Type> IList);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp);

hash_multimap(
    initializer_list<Type> IList,
    const Compare& Comp,
    const Allocator& Al);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last,
    const Compare& Comp);

template <class InputIterator>
hash_multimap(
    InputIterator First,
    InputIterator Last,
    const Compare& Comp,
    const Allocator& Al);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*ウムアルクラ*|この hash_multimap オブジェクトに使用するストレージ アロケーター クラス。既定では、`Allocator` です。|
|*コンペティション*|マップ内の要素の並べ替えに使用される、型 `const Traits` の比較関数。既定では `Traits` です。|
|*右*|構築される map のコピー元となる map。|
|*まずは*|コピーする要素範囲内の最初の要素の位置。|
|*前の*|コピーする要素範囲を超える最初の要素の位置。|
|*IList*|コピー元の initializer_list。|

### <a name="remarks"></a>Remarks

すべてのコンストラクターは、アロケーター オブジェクトの型を格納します。このオブジェクトは hash_multimap のメモリ ストレージを管理し、後で [get_allocator](#get_allocator) を呼び出して取得することができます。 代替アロケーターの代わりに使用されるクラス宣言やプリプロセス マクロでは、アロケーターのパラメーターが省略される場合があります。

すべてのコンストラクターは、それぞれの hash_multimap を初期化します。

すべてのコンストラクターは、`Traits` 型の関数オブジェクトを格納します。このオブジェクトは hash_multimap のキーの順序を確立するために使用され、後で [key_comp](#key_comp) を呼び出して取得することができます。

最初の3つのコンストラクターは、空の初期 hash_multimap を指定します。2番目の関数は、要素の順序を確立するために使用する比較関数 (*Comp*) の種類を指定し、3番目の関数は、使用するアロケーターの型 (`_Al`) を明示的に指定します。 キーワード `explicit` は、特定の種類の自動型変換が実行されないようにします。

4 番目のコンストラクターは、hash_multimap `Right` のコピーを指定します。

次の 3 つのコンストラクターは、map の範囲 `First, Last)` をコピーします。下のコンストラクターになるほど、より明確に `Traits` クラスの比較関数と Allocator の型が指定されています。

8 番目のコンストラクターは、hash_multimap `Right` を移動します。

最後の 3 つのコンストラクターは、initializer_list を使用します。

## <a name="insert"></a>  hash_multimap::insert

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap に要素や要素範囲を挿入します。

```cpp
iterator insert(
    const value_type& Val);

iterator insert(
    const_iterator Where,
    const value_type& Val);void insert(
    initializer_list<value_type> IList);

template <class InputIterator>
void insert(
    InputIterator First,
    InputIterator Last);

template <class ValTy>
iterator insert(
    ValTy&& Val);

template <class ValTy>
iterator insert(
    const_iterator Where,
    ValTy&& Val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*Val*|挿入される要素が hash_multimap にまだ含まれていない場合、より一般的には、キーが同じ順序付けになる要素がまだ含まれていない場合に、hash_multimap に挿入される要素の値。|
|*Where*|正しい挿入ポイントの検索を開始する場所に関するヒント。|
|*まずは*|マップからコピーされる最初の要素の位置。|
|*前の*|マップからコピーされる最後の要素の次の位置。|

### <a name="return-value"></a>戻り値

最初の 2 つの `insert` メンバー関数は、新しい要素が挿入された位置を指す反復子を返します。

3 番目のメンバー関数は、挿入する要素の initializer_list を使用します。

4 番目のメンバー関数は、指定されたセットの範囲 `[First, Last)` 内の反復子によってアドレス指定されている各要素に対応するマップに、要素値のシーケンスを挿入します。

最後の 2 つの `insert` メンバー関数は、先頭の 2 つのメンバー関数と同じように動作しますが、挿入値を移動構築する点が異なります。

### <a name="remarks"></a>Remarks

要素の [value_type](#value_type) はペアを表します。これにより、要素の値は順序付けされたペアになり、このペアの最初のコンポーネントはキー値と同じで、2 番目のコンポーネントは要素のデータ値と同じになります。

挿入ポイントが*位置*の直後にある場合は、対数時間ではなく、`insert` のヒントバージョンに対して、償却定数時間で挿入することができます。

## <a name="iterator"></a>  hash_multimap::iterator

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap 内の任意の要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Remarks

Hash_multimap によって定義される `iterator` は、 [value_type](#value_type)のオブジェクトを指します。このオブジェクトの最初のメンバーは要素のキーで、2番目 **> \< `pair`** のメンバーは要素が保持するマップされた datum です。

Hash_multimap 内の要素を指す**反復子**`Iter` を逆参照するには、`->` 演算子を使用します。

要素のキーの値にアクセスするには、**最初**に  ->  `Iter` を使用します。これは、(\* `Iter`) に相当します。 **最初**に。 要素のマップされた datum の値にアクセスするには、`Iter`  -> **second**を使用します。これは、(\* `Iter`) に相当します。 **最初**に。

@No__t_0 型を使用して、要素の値を変更できます。

### <a name="example"></a>例

`iterator` の宣言方法や使用方法の例については、[begin](#begin) の例をご覧ください。

## <a name="key_comp"></a>  hash_multimap::key_comp

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap 内のキーを並べ替えるために使用される比較オブジェクトのコピーを取得します。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>戻り値

hash_multimap が要素の並べ替えに使用する関数オブジェクトを返します。

### <a name="remarks"></a>Remarks

格納されているオブジェクトは以下のメンバー関数を定義します。

**bool operator(const Key&** `left` **, const Key&** `right` **);**

これは、並べ替え順で `left` が `right` に先行しかつ等しくない場合に **true** を返します。

### <a name="example"></a>例

```cpp
// hash_multimap_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::key_compare kc1 = hm1.key_comp( ) ;
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false,\n"
           << "where kc1 is the function object of hm1.\n"
           << endl;
   }

   hash_multimap <int, int, hash_compare<int, greater<int>>> hm2;
   hash_multimap <int, int, hash_compare<int, greater<int>>
      >::key_compare kc2 = hm2.key_comp( );
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,\n"
           << "where kc2 is the function object of hm2."
           << endl;
   }
}
```

## <a name="key_compare"></a>  hash_multimap::key_compare

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

2 つの並べ替えキーを比較して、hash_multimap 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Remarks

`key_compare` は、テンプレートパラメーターの*特徴*のシノニムです。

*特徴*の詳細については、 [hash_multimap クラス](../standard-library/hash-multimap-class.md)のトピックを参照してください。

### <a name="example"></a>例

`key_compare` の宣言方法や使用方法の例については、[key_comp](#key_comp) の例をご覧ください。

## <a name="key_type"></a>  hash_multimap::key_type

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap の各要素の一部である並べ替えキー オブジェクトを表す型。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Remarks

`key_type` は、テンプレートパラメーター*キー*のシノニムです。

*キー*の詳細については、 [hash_multimap クラス](../standard-library/hash-multimap-class.md)のトピックの「解説」を参照してください。

### <a name="example"></a>例

`key_compare` の宣言方法や使用方法の例については、[value_type](#value_type) の例をご覧ください。

## <a name="lower_bound"></a>  hash_multimap::lower_bound

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

指定したキー以上のキーを持つ、hash_multimap 内の最初の要素を指す反復子を返します。

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の hash_multimap 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

引数キー以上のキーを持つ hash_multimap 内の要素の位置を指す、または、キーの一致が検出されない場合は hash_multimap 内の最後の要素の次の位置を指す、[反復子](#iterator)または [const_iterator](#const_iterator)。

`lower_bound` の戻り値が `const_iterator` に割り当てられている場合、hash_multimap オブジェクトは変更できません。 @No__t_0 の戻り値が `iterator` に割り当てられている場合は、hash_multimap オブジェクトを変更できます。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_multimap_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter,
      hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The element of hash_multimap hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.lower_bound( 3 );
   cout << "The first element of hash_multimap hm1 with a key of 3 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.lower_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key matching"
        << endl << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;

   // Note that the first element with a key equal to
   // the key of the last element is not the last element
   if ( hm1_RcIter == --hm1.end( ) )
      cout << "This is the last element of hash_multimap hm1."
           << endl;
   else
      cout << "This is not the last element of hash_multimap hm1."
           << endl;
}
```

```Output
The element of hash_multimap hm1 with a key of 2 is: 20.
The first element of hash_multimap hm1 with a key of 3 is: 20.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key matching
that of the last element is: 20.
This is not the last element of hash_multimap hm1.
```

## <a name="mapped_type"></a>  hash_multimap::mapped_type

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap 内に格納されているデータ型を表す型。

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Remarks

`mapped_type` は、テンプレート パラメーター *Type* のシノニムです。

*型*の詳細については、 [hash_multimap クラス](../standard-library/hash-multimap-class.md)のトピックを参照してください。

### <a name="example"></a>例

`key_type` の宣言方法や使用方法の例については、[value_type](#value_type) の例をご覧ください。

## <a name="max_size"></a>  hash_multimap::max_size

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap の最大長を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

hash_multimap の可能な最大長。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_multimap_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_multimap is " << i << "." << endl;
}
```

## <a name="op_eq"></a>  hash_multimap::operator=

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap の要素を、別の hash_multimap のコピーで置き換えます。

```cpp
hash_multimap& operator=(const hash_multimap& right);

hash_multimap& operator=(hash_multimap&& right);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*right*|`hash_multimap` にコピーする [hash_multimap](../standard-library/hash-multimap-class.md)。|

### <a name="remarks"></a>Remarks

@No__t_0 内の既存の要素を消去した後、 *`operator=` の内容*を `hash_multimap` にコピーまたは移動します。

### <a name="example"></a>例

```cpp
// hash_multimap_operator_as.cpp
// compile with: /EHsc
#include <hash_multimap>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap<int, int> v1, v2, v3;
   hash_multimap<int, int>::iterator iter;

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

## <a name="pointer"></a>  hash_multimap::pointer

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap 内の要素へのポインターを提供する型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Remarks

@No__t_0 型を使用して、要素の値を変更できます。

ほとんどの場合、hash_multimap オブジェクト内の要素にアクセスするには、[反復子](#iterator)を使用する必要があります。

## <a name="rbegin"></a>  hash_multimap::rbegin

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

反転された hash_multimap 内の最初の要素を指す反復子を返します。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>戻り値

反転された hash_multimap 内の最初の要素を示す、または反転されていない hash_multimap 内の最後の要素だったものを示す逆順双方向反復子。

### <a name="remarks"></a>Remarks

`rbegin` は、[begin](#begin) が hash_multimap で使用されるように、逆順の hash_multimap で使用されます。

`rbegin` の戻り値が `const_reverse_iterator` に割り当てられている場合、hash_multimap オブジェクトは変更できません。 `rbegin` の戻り値が `reverse_iterator` に割り当てられている場合、hash_multimap オブジェクトは変更できます。

`rbegin` を使用して、hash_multimap 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// hash_multimap_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element\n"
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_multimap hm1 is 3.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the first element
in the reversed hash_multimap is 2.
```

## <a name="reference"></a>  hash_multimap::reference

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap に格納されている要素への参照を提供する型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_multimap_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_multimap is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_multimap is "
        << Ref2 << "." << endl;

   //The non-const_reference can be used to modify the
   //data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  hash_multimap::rend

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

反転された hash_multimap 内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>戻り値

逆順の hash_multimap 内の最後の要素の次の場所 (通常の順序の hash_multimap 内の最初の要素の前の場所) を指す逆順双方向反復子。

### <a name="remarks"></a>Remarks

`rend` は、[end](#end) が hash_multimap で使用されるように、逆順の hash_multimap で使用されます。

`rend` の戻り値が [const_reverse_iterator](#const_reverse_iterator) に割り当てられている場合、hash_multimap オブジェクトは変更できません。 `rend` の戻り値が [reverse_iterator](#reverse_iterator) に割り当てられている場合、hash_multimap オブジェクトは変更できます。

`rend` を使用して、逆順反復子が hash_multimap の末尾に達したかどうかをテストできます。

`rend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// hash_multimap_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;

   hash_multimap <int, int> :: iterator hm1_Iter;
   hash_multimap <int, int> :: reverse_iterator hm1_rIter;
   hash_multimap <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_multimap hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_multimap in a forward order
   cout << "The hash_multimap is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_multimap in a reverse order
   cout << "The reversed hash_multimap is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_multimap element can be erased by dereferencing its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_multimap is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_multimap hm1 is 1.
The hash_multimap is: 1 2 3 .
The reversed hash_multimap is: 3 2 1 .
After the erasure, the last element in the reversed hash_multimap is 2.
```

## <a name="reverse_iterator"></a>  hash_multimap::reverse_iterator

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

反転された hash_multimap 内の 1 つの要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Remarks

型 `reverse_iterator` は、逆の順序で hash_multimap を反復処理するために使用します。

hash_multimap によって定義される `reverse_iterator` は、[value_type](#value_type) のオブジェクトを指します。これは `pair`\< **const Key, Type**> 型です。 キーの値はペアの 1 番目のメンバー、マップされた要素の値はペアの 2 番目のメンバーを介して取得できます。

### <a name="example"></a>例

`reverse_iterator` の宣言方法や使用方法の例については、[rbegin](#rbegin) の例を参照してください。

## <a name="size"></a>  hash_multimap::size

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap 内の要素の数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

hash_multimap の現在の長さ。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

hash_multimap::size メンバー関数の使用例を次に示します。

```cpp
// hash_multimap_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_multimap<int, int> hm1, hm2;
    hash_multimap<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_multimap length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_multimap length is now " << i << "." << endl;
}
```

```Output
The hash_multimap length is 1.
The hash_multimap length is now 2.
```

## <a name="size_type"></a>  hash_multimap::size_type

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap 内の要素の数をカウントする符号なし整数型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

`size_type` の宣言方法や使用方法の例については、[size](#size) の例をご覧ください。

## <a name="swap"></a>  hash_multimap::swap

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

2 つの hash_multimap の要素を交換します。

```cpp
void swap(hash_multimap& right);
```

### <a name="parameters"></a>パラメーター

*右*\
交換する要素を提供する hash_multimap (hash_multimap の要素と要素を交換する hash_multimap)。

### <a name="remarks"></a>Remarks

メンバー関数は、要素を交換する 2 つの hash_multimap において要素を指定している参照、ポインター、反復子を無効にすることはありません。

### <a name="example"></a>例

```cpp
// hash_multimap_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1, hm2, hm3;
   hash_multimap <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_multimap hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_multimap hm1 is: 10 20 30.
After swapping with hm2, hash_multimap hm1 is: 100 200.
After swapping with hm3, hash_multimap hm1 is: 300.
```

## <a name="upper_bound"></a>  hash_multimap::upper_bound

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

指定したキーよりも大きいキーを持つ、hash_multimap 内の最初の要素を指す反復子を返します。

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の hash_multimap 内の要素の並べ替えキーと比較される引数キー。

### <a name="return-value"></a>戻り値

引数キーより大きいキーを持つ hash_multimap 内の要素の位置を指す、または、キーの一致が検出されない場合は hash_multimap 内の最後の要素の次の位置を指す、[反復子](#iterator)または [const_iterator](#const_iterator)。

`upper_bound` の戻り値が `const_iterator` に割り当てられている場合、hash_multimap オブジェクトは変更できません。 @No__t_0 の戻り値が `iterator` に割り当てられている場合は、hash_multimap オブジェクトを変更できます。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_multimap_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm1.insert ( Int_Pair ( 3, 40 ) );

   hm1_RcIter = hm1.upper_bound( 1 );
   cout << "The 1st element of hash_multimap hm1 with "
        << "a key greater than 1 is: "
        << hm1_RcIter -> second << "." << endl;

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_multimap hm1\n"
        << "with a key greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.lower_bound( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_multimap hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_multimap hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_multimap can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1.upper_bound( hm1_AcIter -> first );
   cout << "The first element of hm1 with a key greater than"
        << endl << "that of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The 1st element of hash_multimap hm1 with a key greater than 1 is: 20.
The first element of hash_multimap hm1
with a key  greater than 2 is: 30.
The hash_multimap hm1 doesn't have an element with a key of 4.
The first element of hm1 with a key greater than
that of the initial element of hm1 is: 20.
```

## <a name="value_comp"></a>  hash_multimap::value_comp

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

このメンバー関数は、キー値の比較によって hash_multimap の要素の順序を決定する関数オブジェクトを返します。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>戻り値

hash_multimap が要素の並べ替えに使用する比較関数オブジェクトを返します。

### <a name="remarks"></a>Remarks

Hash_multimap *m*の場合、2つの*要素 e1* (*k1*, *d1*) と*e2*(*k2*, *d2*) が[value_type](#value_type)型のオブジェクトである場合、 *k1*と*k2*は[key_type](#key_type)型のキーで、*d1*と*d2*は[mapped_type](#mapped_type)型のデータであり、4 は 5 に相当します。 格納されているオブジェクトは以下のメンバー関数を定義します。

`bool operator( value_type& left, value_type& right);`

これは、並べ替え順で `left` のキー値が `right` のキー値に先行しかつ等しくない場合に、**true** を返します。

### <a name="example"></a>例

```cpp
// hash_multimap_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_multimap <int, int, hash_compare<int, less<int>>> hm1;
   hash_multimap <int, int, hash_compare<int, less<int>>
      >::value_compare vc1 = hm1.value_comp( );
   hash_multimap <int,int>::iterator Iter1, Iter2;

   Iter1= hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );
   Iter2= hm1.insert ( hash_multimap <int, int> :: value_type ( 2, 5 ) );

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

## <a name="value_type"></a>  hash_multimap::value_type

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、 [unordered_multimap Class](../standard-library/unordered-multimap-class.md)をご使用ください。

hash_multimap 内に格納されているオブジェクトの型を表す型。

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Remarks

`value_type` は、非定数 iterator または reference を使用して連想コンテナーのキーが変更されない可能性があるため、ペア \<const [key_type](#key_type)、 [mapped_type](#mapped_type)> \<key_type、および mapped_type > として宣言されています。

### <a name="example"></a>例

```cpp
// hash_multimap_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_multimap <int, int> hm1;
   hash_multimap <int, int> :: key_type key1;
   hash_multimap <int, int> :: mapped_type mapped1;
   hash_multimap <int, int> :: value_type value1;
   hash_multimap <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   hm1.insert ( hash_multimap <int, int> :: value_type ( 1, 10 ) );

   // Compare another way to insert objects into a hash_multimap
   hm1.insert ( cInt2Int ( 2, 20 ) );

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_multimap is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_multimap is "
        << mapped1 << "." << endl;

   // The following line would cause an error because
   // the value_type is not assignable
   // value1 = cInt2Int ( 4, 40 );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;
}
```

```Output
The key of first element in the hash_multimap is 1.
The data value of first element in the hash_multimap is 10.
The keys of the mapped elements are: 1 2.
The values of the mapped elements are: 10 20.
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
