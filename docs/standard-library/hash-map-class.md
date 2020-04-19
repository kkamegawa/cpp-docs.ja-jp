---
title: hash_map クラス
ms.date: 11/04/2016
f1_keywords:
- hash_map/stdext::hash_map
- hash_map/stdext::hash_map::allocator_type
- hash_map/stdext::hash_map::const_iterator
- hash_map/stdext::hash_map::const_pointer
- hash_map/stdext::hash_map::const_reference
- hash_map/stdext::hash_map::const_reverse_iterator
- hash_map/stdext::hash_map::difference_type
- hash_map/stdext::hash_map::iterator
- hash_map/stdext::hash_map::key_compare
- hash_map/stdext::hash_map::key_type
- hash_map/stdext::hash_map::mapped_type
- hash_map/stdext::hash_map::pointer
- hash_map/stdext::hash_map::reference
- hash_map/stdext::hash_map::reverse_iterator
- hash_map/stdext::hash_map::size_type
- hash_map/stdext::hash_map::value_type
- hash_map/stdext::hash_map::at
- hash_map/stdext::hash_map::begin
- hash_map/stdext::hash_map::cbegin
- hash_map/stdext::hash_map::cend
- hash_map/stdext::hash_map::clear
- hash_map/stdext::hash_map::count
- hash_map/stdext::hash_map::crbegin
- hash_map/stdext::hash_map::crend
- hash_map/stdext::hash_map::emplace
- hash_map/stdext::hash_map::emplace_hint
- hash_map/stdext::hash_map::empty
- hash_map/stdext::hash_map::end
- hash_map/stdext::hash_map::equal_range
- hash_map/stdext::hash_map::erase
- hash_map/stdext::hash_map::find
- hash_map/stdext::hash_map::get_allocator
- hash_map/stdext::hash_map::insert
- hash_map/stdext::hash_map::key_comp
- hash_map/stdext::hash_map::lower_bound
- hash_map/stdext::hash_map::max_size
- hash_map/stdext::hash_map::rbegin
- hash_map/stdext::hash_map::rend
- hash_map/stdext::hash_map::size
- hash_map/stdext::hash_map::swap
- hash_map/stdext::hash_map::upper_bound
- hash_map/stdext::hash_map::value_comp
helpviewer_keywords:
- stdext::hash_map
- stdext::hash_map::allocator_type
- stdext::hash_map::const_iterator
- stdext::hash_map::const_pointer
- stdext::hash_map::const_reference
- stdext::hash_map::const_reverse_iterator
- stdext::hash_map::difference_type
- stdext::hash_map::iterator
- stdext::hash_map::key_compare
- stdext::hash_map::key_type
- stdext::hash_map::mapped_type
- stdext::hash_map::pointer
- stdext::hash_map::reference
- stdext::hash_map::reverse_iterator
- stdext::hash_map::size_type
- stdext::hash_map::value_type
- stdext::hash_map::at
- stdext::hash_map::begin
- stdext::hash_map::cbegin
- stdext::hash_map::cend
- stdext::hash_map::clear
- stdext::hash_map::count
- stdext::hash_map::crbegin
- stdext::hash_map::crend
- stdext::hash_map::emplace
- stdext::hash_map::emplace_hint
- stdext::hash_map::empty
- stdext::hash_map::end
- stdext::hash_map::equal_range
- stdext::hash_map::erase
- stdext::hash_map::find
- stdext::hash_map::get_allocator
- stdext::hash_map::insert
- stdext::hash_map::key_comp
- stdext::hash_map::lower_bound
- stdext::hash_map::max_size
- stdext::hash_map::rbegin
- stdext::hash_map::rend
- stdext::hash_map::size
- stdext::hash_map::swap
- stdext::hash_map::upper_bound
- stdext::hash_map::value_comp
ms.assetid: 40879dfc-51ba-4a59-9f9e-26208de568a8
ms.openlocfilehash: e993b694e03c83ef2b2bc96ecefc2d37e48f7747
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687981"
---
# <a name="hash_map-class"></a>hash_map クラス

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

各要素がペアになっているコレクションからデータをすばやく格納および取得します。このペアには並べ替えキーが含まれていて、その値は一意であり、データ値が関連付けられています。

## <a name="syntax"></a>構文

```cpp
template <class Key,
    class Type,
    class Traits=hash_compare<Key, less<Key>>,
    class Allocator=allocator<pair <const Key, Type>>>
class hash_map
```

### <a name="parameters"></a>パラメーター

*キー* \
hash_map に格納されるキーのデータ型。

*型*\
hash_map に格納される要素のデータ型。

*特徴*\
2 つの関数オブジェクトを含む型。2 つの要素の値を並べ替えキーとして比較し、要素の相対順序を決定できるクラス比較、または要素のキー値を `size_t` 型の符号なし整数にマップする単項述語であるハッシュ関数のいずれかを使用できます。 この引数は省略可能であり、hash_compare < `Key`、より少ない < `Key` > > が既定値です。

*アロケーター* \
メモリの hash_map の割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクトを表す型。 この引数は省略可能であり、既定値は allocator<pair <const `Key`, `Type`>> です。

## <a name="remarks"></a>Remarks

hash_map の特徴を次に示します。

- hash_map は連想コンテナーであり、関連付けられたキー値に基づいて要素の値を効率的に取得できるようにする可変サイズのコンテナーとして機能します。

- 反転することができます。これは、hash_map には、要素にアクセスするための双方向反復子が用意されているためです。

- ハッシュされます。これは、要素のキー値に適用されたハッシュ関数の値に基づいて、要素がバケットにグループ化されるためです。

- 一意のクラスです。これは、各要素が一意のキーを持つ必要があるためです。

- ペアを保持する連想コンテナーです。これは、要素のデータ値とキー値が分かれているためです。

- クラステンプレート。提供される機能はジェネリックであり、要素またはキーとして含まれる特定のデータ型には依存しません。 要素やキーに使用されているデータ型は、クラス テンプレートで比較関数やアロケーターと共にパラメーターとして指定されます。

並べ替えでのハッシュの主な利点は、効率に優れていることです。コンテナー内にある要素を並べ替えるとき、その時間は要素の数の対数に比例しますが、適切なハッシュを実行すると、挿入、削除、検索にかかる平均時間は一定しています。 hash_map の要素の値 (関連するキー値ではありません) は、直接変更される場合があります。 この場合、変更前の要素に関連付けられていたキー値を削除し、新しい要素に関連付けられる新しいキー値を挿入する必要があります。

一般的に、コンテナー型の選択は、アプリケーションにおいて必要な検索および挿入の種類に基づいている必要があります。 ハッシュされた連想コンテナーは、検索、挿入、削除の各操作用に最適化されています。 これらの操作を明示的にサポートするメンバー関数は、適切に記述されたハッシュ関数と共に使用すると、効率的に機能します。検索、挿入、削除の操作にかかる実行時間は、平均で一定しており、コンテナー内の要素の数による影響を受けません。 適切に記述されたハッシュ関数によって、ハッシュ値の一様分布が生成され、競合の数を最小限に抑えることができます (競合は、異なるキー値が同じハッシュ値にマップされたときに発生する可能性があります)。 最悪のケースは、不適切に記述されたハッシュ関数が使用される場合です。演算の回数は、シーケンス内の要素数に比例して増えることになります (線形時間)。

値とキーを関連付ける条件をアプリケーションが満たしている場合、hash_map は最適な連想コンテナーとなっている必要があります。 この種類の構造体のモデルとなるのは、一意に発生するキーワードおよび関連する文字列値 (キーワードの定義を指定) が順番に格納されたリストです。 ただし、キーワードには正しい定義が複数あり、そのためにキーが一意ではなくなる場合は、hash_multimap が適切なコンテナーとなります。 また、キーワードのリストだけが格納される場合は、hash_set が適切なコンテナーとなります。 キーワードを複数設定できる場合は、hash_multiset が適切なコンテナー構造体となります。

Hash_map は、 [value_compare](../standard-library/value-compare-class.md)クラスの格納されたハッシュ*特性*オブジェクトを呼び出すことによって、制御するシーケンスを並べ替えます。 格納されているこのオブジェクトには、メンバー関数 [key_comp](#key_comp) を呼び出すことによってアクセスできます。 このような関数オブジェクトは、[hash_compare](../standard-library/hash-compare-class.md)<Key, less\<Key>> クラスのオブジェクトと同様に動作する必要があります。 具体的には、 *key*型のすべての値*キー*に対して `Traits` (`Key`) を呼び出すと、`size_t` 型の値の分布が生成されます。

通常、要素は、この順序を確立するために小なり比較だけを実行できる必要があります。これにより、2 つの要素が指定されたときに、それらの要素が等しいか (どちらか一方が小さくはない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 テクニカル ノートでは、比較関数は、数学上の標準的な意味で厳密弱順序を発生させる二項述語であると示されています。 二項述語 f (x y) は、2つの引数オブジェクト `x` および `y` と、戻り値 ( **true**または**false**) を持つ関数オブジェクトです。 hash_map に適用される順序付けは、二項述語が非再帰、反対称、推移的であり、等価性が推移的である (2 つオブジェクト (x と y) が、f(x, y) と f(y, x) の両方が false の場合に等価になるように定義されている) 場合、厳密弱順序になります。 2 つのキーの等値に関する条件が等価性の条件よりも厳しく、優先される場合、順序付けは完全な順序付け (すべての要素が相互の値に基づいて並べ替えられる) となり、一致するそれぞれのキーを識別するのが難しくなります。

被制御シーケンスにおける要素の実際の順序は、ハッシュ関数、順序関数、コンテナー オブジェクトに格納されるハッシュ テーブルの現在のサイズによって異なります。 ハッシュ テーブルの現在のサイズは特定できないため、通常は、被制御シーケンス内の要素の順序を予測することはできません。 要素を挿入しても反復子の有効性は失われません。また、要素を削除した場合は、削除された要素を具体的に指す反復子だけが無効化されます。

hash_map クラスに用意されている反復子は双方向反復子ですが、クラス メンバー関数 [insert](#insert) と [hash_map](#hash_map) には、弱い入力反復子をテンプレート パラメーターとして取得するバージョンがあります。この反復子の機能に関する要件は、双方向反復子のクラスで保証されている要件よりも低くなっています。 これらの反復子の機能に差異があるのは、反復子の概念が異なっているためです。 反復子の各概念には、反復子独自の一連の要件が含まれています。また、それらの要件を使用するアルゴリズムでは、反復子の種類ごとに指定されている要件に対して、前提を絞り込む必要があります。 たとえば、一部のオブジェクトを参照するために入力反復子が逆参照される可能性があることを前提とする場合があります。さらに、シーケンス内にある次の反復子に対して逆参照が増加する可能性があることを前提とする場合もあります。 このことは、最小限実施することですが、クラス メンバー関数のコンテキストに含まれる反復子の範囲 `[First, Last)` について明確にすることも重要です。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[hash_map](#hash_map)|空の `hash_map`、または他の `hash_map` の全体または一部のコピーである hash_multiset を構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[allocator_type](#allocator_type)|`allocator` オブジェクトの `hash_map` クラスを表す型。|
|[const_iterator](#const_iterator)|`const` 内の 1 つの `hash_map` 要素を読み取ることができる双方向反復子を提供する型。|
|[const_pointer](#const_pointer)|@No__t_1 内の**const**要素へのポインターを提供する型。|
|[const_reference](#const_reference)|読み取りと**const**操作の実行のために `hash_map` に格納されている**const**要素への参照を提供する型。|
|[const_reverse_iterator](#const_reverse_iterator)|@No__t_1 内の任意の**const**要素を読み取ることができる双方向反復子を提供する型。|
|[difference_type](#difference_type)|`hash_map` の要素の数を、反復子が指す要素の範囲に基づいて表すために使用できる符号付き整数型。|
|[Iterator](#iterator)|`hash_map` 内の任意の要素を読み取り、または変更できる双方向反復子を提供する型。|
|[key_compare](#key_compare)|2 つの並べ替えキーを比較して、`hash_map` 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。|
|[key_type](#key_type)|`hash_map` の各要素の一部である並べ替えキー オブジェクトを表す型。|
|[mapped_type](#mapped_type)|`hash_map` に格納されているデータ型を表す型。|
|[pointer](#pointer)|`hash_map` 内の要素へのポインターを提供する型。|
|[reference](#reference)|`hash_map` に格納されている要素への参照を提供する型。|
|[reverse_iterator](#reverse_iterator)|反転された `hash_map` 内の 1 つの要素を読み取り、または変更できる双方向反復子を提供する型。|
|[size_type](#size_type)|`hash_map` 内の要素の数を表すことができる符号なし整数型。|
|[value_type](#value_type)|2 つの要素を並べ替えキーとして比較して、`hash_map` 内の要素の相対順序を決定できる関数オブジェクトを提供する型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[at](#at)|指定したキー値を持つ、`hash_map` 内の要素を検索します。|
|[begin](#begin)|`hash_map` 内の最初の要素を指す反復子を返します。|
|[cbegin](#cbegin)|`hash_map` 内の最初の要素を指す定数反復子を返します。|
|[cend](#cend)|`hash_map` 内の最後の要素の次の位置を指す定数反復子を返します。|
|[clear](#clear)|`hash_map` のすべての要素を消去します。|
|[count](#count)|パラメーター指定したキーに一致するキーを持つ、`hash_map` 内の要素の数を返します。|
|[crbegin](#crbegin)|反転された `hash_map` 内の最初の要素を指す定数反復子を返します。|
|[crend](#crend)|反転された `hash_map` 内の最後の要素の次の位置を指す定数反復子を返します。|
|[emplace](#emplace)|インプレースで構築された要素を `hash_map` に挿入します。|
|[emplace_hint](#emplace_hint)|インプレースで構築された要素を、配置ヒントと共に `hash_map` に挿入します。|
|[empty](#empty)|`hash_map` が空かどうかをテストします。|
|[end](#end)|`hash_map` 内の最後の要素の次の位置を指す反復子を返します。|
|[equal_range](#equal_range)|指定したキーよりも大きいキーを持つ、`hash_map` 内の最初の要素を指す反復子のペア、およびそのキー以上のキーを持つ、`hash_map` 内の最初の要素を指す反復子のペアを返します。|
|[erase](#erase)|指定した位置から `hash_map` 内の要素または要素範囲を削除します。|
|[find](#find)|指定したキーと同じキーを持つ、`hash_map` 内の要素の位置を指す反復子を返します。|
|[get_allocator](#get_allocator)|`allocator` の構築に使用される `hash_map` オブジェクトのコピーを返します。|
|[insert](#insert)|`hash_map` に要素または要素範囲を挿入します。|
|[key_comp](#key_comp)|指定したキー以上のキー値を持つ、`hash_map` 内の最初の要素を指す反復子を返します。|
|[lower_bound](#lower_bound)|指定したキー以上のキー値を持つ、`hash_map` 内の最初の要素を指す反復子を返します。|
|[max_size](#max_size)|`hash_map` の最大長を返します。|
|[rbegin](#rbegin)|反転された `hash_map` 内の最初の要素を指す反復子を返します。|
|[rend](#rend)|反転された `hash_map` 内の最後の要素の次の位置を指す反復子を返します。|
|[size](#size)|`hash_map` 内の要素数を返します。|
|[swap](#swap)|2 つの `hash_map` の要素を交換します。|
|[upper_bound](#upper_bound)|指定したキーよりも大きいキー値を持つ、`hash_map` 内の最初の要素を指す反復子を返します。|
|[value_comp](#value_comp)|`hash_map` 内の要素の値を並べ替えるために使用される比較オブジェクトのコピーを取得します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator&#91;&#93;](#op_at)|`hash_map` に、指定したキー値を持つ要素を挿入します。|
|[hash_map::operator=](#op_eq)|別の `hash_map` のコピーで `hash_map` の要素を置き換えます。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<hash_map>

**名前空間:** stdext

## <a name="allocator_type"></a>  hash_map::allocator_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map オブジェクトのアロケーター クラスを表す型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::allocator_type allocator_type;
```

### <a name="example"></a>例

`allocator_type` の使用例については、[get_allocator](#get_allocator) の例をご覧ください。

## <a name="at"></a>  hash_map::at

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

指定したキー値を持つ、hash_map 内の要素を検索します。

```cpp
Type& at(const Key& key);

const Type& at(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*key*|検索する要素のキー値。|

### <a name="return-value"></a>戻り値

見つかった要素のデータ値への参照。

### <a name="remarks"></a>Remarks

引数のキー値が見つからない場合、この関数は、[out_of_range クラス](../standard-library/out-of-range-class.md) のオブジェクトをスローします。

### <a name="example"></a>例

```cpp
// hash_map_at.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;

   // Insert data values
   hm1.insert ( cInt2Int ( 1, 10 ) );
   hm1.insert ( cInt2Int ( 2, 20 ) );
   hm1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The values of the mapped elements are:";
   for ( int i = 1 ; i <= hm1.size() ; i++ )
      cout << " " << hm1.at(i);
   cout << "." << endl;
}
```

## <a name="begin"></a>  hash_map::begin

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内の最初の要素を指す反復子を返します。

```cpp
const_iterator begin() const;

iterator begin();
```

### <a name="return-value"></a>戻り値

hash_map 内の最初の要素、または空の hash_map の次の位置を指す双方向反復子。

### <a name="example"></a>例

```cpp
// hash_map_begin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: const_iterator hm1_cIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 0, 0 ) );
   hm1.insert ( Int_Pair ( 1, 1 ) );
   hm1.insert ( Int_Pair ( 2, 4 ) );

   hm1_cIter = hm1.begin ( );
   cout << "The first element of hm1 is "
        << hm1_cIter -> first << "." << endl;

   hm1_Iter = hm1.begin ( );
   hm1.erase ( hm1_Iter );

   // The following 2 lines would err because the iterator is const
   // hm1_cIter = hm1.begin ( );
   // hm1.erase ( hm1_cIter );

   hm1_cIter = hm1.begin( );
   cout << "The first element of hm1 is now "
        << hm1_cIter -> first << "." << endl;
}
```

```Output
The first element of hm1 is 0.
The first element of hm1 is now 1.
```

## <a name="cbegin"></a>  hash_map::cbegin

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内の最初の要素を示す定数反復子を返します。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

[hash_map](../standard-library/hash-map-class.md) 内の最初の要素、または空の `hash_map` の次の位置を指す定数双方向反復子。

### <a name="example"></a>例

```cpp
// hash_map_cbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_iterator hm1_cIter;
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

## <a name="cend"></a>  hash_map::cend

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>戻り値

[hash_map](../standard-library/hash-map-class.md) 内の最後の要素の次の位置を指す定数双方向反復子。 `hash_map` が空の場合は、`hash_map::cend == hash_map::begin`。

### <a name="remarks"></a>Remarks

`cend` は、反復子が `hash_map` の末尾に達したかどうかをテストするために使用します。

`cend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// hash_map_cend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_iterator hm1_cIter;
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

## <a name="clear"></a>  hash_map::clear

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map のすべての要素を消去します。

```cpp
void clear();
```

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

hash_map::clear メンバー関数の使用例を次に示します。

```cpp
// hash_map_clear.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    hm1.insert(Int_Pair(2, 4));

    i = hm1.size();
    cout << "The size of the hash_map is initially "
         << i << "." << endl;

    hm1.clear();
    i = hm1.size();
    cout << "The size of the hash_map after clearing is "
         << i << "." << endl;
}
```

```Output
The size of the hash_map is initially 2.
The size of the hash_map after clearing is 0.
```

## <a name="const_iterator"></a>  hash_map::const_iterator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内の 1 つの **const** 要素を読み取ることができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_iterator const_iterator;
```

### <a name="remarks"></a>Remarks

`const_iterator` 型で要素の値を変更することはできません。

Hash_map によって定義される `const_iterator` は、 [value_type](#value_type)のオブジェクトである要素を指します。これは、最初のメンバーが要素のキーであり、2番目 `pair< const Key, Type >` のメンバーが要素に保持されているマップされた datum であることを示します。

Hash_map 内の要素を指す `const_iterator` `cIter` を逆参照するには、`->` 演算子を使用します。

要素のキーの値にアクセスするには、`cIter->first` を使用します。これは `(*cIter).first` と同じです。 要素のマップされた datum の値にアクセスするには、`cIter->second` を使用します。これは `(*cIter).second` と同じです。

### <a name="example"></a>例

`const_iterator` の使用例については、[begin](#begin) の例をご覧ください。

## <a name="const_pointer"></a>  hash_map::const_pointer

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内の **const** 要素へのポインターを提供する型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_pointer const_pointer;
```

### <a name="remarks"></a>Remarks

`const_pointer` 型で要素の値を変更することはできません。

ほとんどの場合、hash_map オブジェクト内の要素にアクセスするには、[反復子](#iterator)を使用する必要があります。

## <a name="const_reference"></a>  hash_map::const_reference

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

**const** 操作の読み取りと実行のために、hash_map に格納された **const** 要素への参照を提供する型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::const_reference const_reference;
```

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_map_const_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map<int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error because the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of the first element in the hash_map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of the first element in the hash_map is "
        << Ref2 << "." << endl;
}
```

```Output
The key of the first element in the hash_map is 1.
The data value of the first element in the hash_map is 10.
```

## <a name="const_reverse_iterator"></a>  hash_map::const_reverse_iterator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map の 任意の **const** 要素を読み取ることができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::const_reverse)iterator const_reverse_iterator;
```

### <a name="remarks"></a>Remarks

`const_reverse_iterator` 型は要素の値を変更できず、逆の順序で hash_map を反復処理するために使用します。

hash_map によって定義される `const_reverse_iterator` は、[value_type](#value_type) のオブジェクトである要素を指します。これは`pair`\< **const Key, Type**> 型で、その最初のメンバーは要素へのキーであり、2 番目のメンバーは要素が保持するマップされたデータです。

Hash_map 内の要素を指す `const_reverse_iterator` `crIter` を逆参照するには、 **->** 演算子を使用します。

要素のキーの値にアクセスするには `crIter` -> **first** を使用しますが、これは (\* `crIter`) **.first** と同等です。 要素のマップされた datum の値にアクセスするには、`crIter`  -> **second**を使用します。これは、(\* `crIter`) に相当します。 **最初**に。

### <a name="example"></a>例

`const_reverse_iterator` の宣言方法や使用方法の例については、[rend](#rend) の例をご覧ください。

## <a name="count"></a>  hash_map::count

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

キーがパラメーター指定したキーと一致する hash_map の要素数を返します。

```cpp
size_type count(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
hash_map と照合する要素のキー値。

### <a name="return-value"></a>戻り値

hash_map に、並べ替えキーがパラメーター キーと一致する要素が含まれている場合は 1。hash_map に、キーが一致する要素が含まれていない場合は 0。

### <a name="remarks"></a>Remarks

メンバー関数は、次の範囲内の要素 *x* の数を返します。

\[ lower_bound (*キー*)、upper_bound (*キー*))

一意の連想コンテナーである hash_map の場合、これは 0 または 1 です。

### <a name="example"></a>例

hash_map::count メンバー関数の使用例を次に示します。

```cpp
// hash_map_count.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair (1, 1));
    hm1.insert(Int_Pair (2, 1));
    hm1.insert(Int_Pair (1, 4));
    hm1.insert(Int_Pair (2, 1));

    // Keys must be unique in hash_map, so duplicates are ignored
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
The number of elements in hm1 with a sort key of 1 is: 1.
The number of elements in hm1 with a sort key of 2 is: 1.
The number of elements in hm1 with a sort key of 3 is: 0.
```

## <a name="crbegin"></a>  hash_map::crbegin

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

反転された hash_map 内の最初の要素を指す定数反復子を返します。

```cpp
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>戻り値

反転された [hash_map](../standard-library/hash-map-class.md) 内の最初の要素を示す、または反転されていない `hash_map` 内の最後の要素だったものを示す定数逆順双方向反復子。

### <a name="remarks"></a>Remarks

`crbegin` は、[begin](#begin) が `hash_map` で使用されるのと同様に、反転された hash_map で使用されます。

戻り値が `crbegin` の場合、`hash_map` オブジェクトは変更できません。

`crbegin` を使用して、`hash_map` 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// hash_map_crbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crbegin( );
   cout << "The first element of the reversed hash_map hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_map hm1 is 3.
```

## <a name="crend"></a>  hash_map::crend

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

反転された hash_map 内の最後の要素の次の位置を指す定数反復子を返します。

```cpp
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>戻り値

反転された [hash_map](../standard-library/hash-map-class.md) 内の最後の要素の次の場所 (反転されていない `hash_map` 内の最初の要素の前の場所) を指す定数逆順双方向反復子。

### <a name="remarks"></a>Remarks

`crend` は、 [hash_map::end](#end) が `hash_map` で使用されるのと同様に、反転された `hash_map` で使用されます。

戻り値が `crend` の場合、`hash_map` オブジェクトは変更できません。

`crend` を使用して、逆順反復子が `hash_map` の末尾に達したかどうかをテストできます。

`crend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// hash_map_crend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_crIter = hm1.crend( );
   hm1_crIter--;
   cout << "The last element of the reversed hash_map hm1 is "
        << hm1_crIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_map hm1 is 3.
```

## <a name="difference_type"></a>  hash_map::difference_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

反復子が指す要素の範囲内にある hash_map の要素の数を表すのに使用できる符号付き整数型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::difference_type difference_type;
```

### <a name="example"></a>例

```cpp
// hash_map_diff_type.cpp
// compile with: /EHsc
#include <iostream>
#include <hash_map>
#include <algorithm>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 3, 20 ) );

   // The following won't insert, because map keys are unique
   hm1.insert ( Int_Pair ( 2, 30 ) );

   hash_map <int, int>::iterator hm1_Iter, hm1_bIter, hm1_eIter;
   hm1_bIter = hm1.begin( );
   hm1_eIter = hm1.end( );

   // Count the number of elements in a hash_map
   hash_map <int, int>::difference_type  df_count = 0;
   hm1_Iter = hm1.begin( );
   while ( hm1_Iter != hm1_eIter)
   {
      df_count++;
      hm1_Iter++;
   }

   cout << "The number of elements in the hash_map hm1 is: "
        << df_count << "." << endl;

   cout  << "The keys of the mapped elements are:";
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;
         hm1_Iter++)
      cout << " " << hm1_Iter-> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( hm1_Iter= hm1.begin( ) ; hm1_Iter!= hm1.end( ) ;
         hm1_Iter++)
      cout << " " << hm1_Iter-> second;
   cout << "." << endl;
}
```

```Output
The number of elements in the hash_map hm1 is: 3.
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 20.
```

## <a name="emplace"></a>  hash_map::emplace

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

インプレースで構築された要素を hash_map に挿入します。

```cpp
template <class ValTy>
pair <iterator, bool>
emplace(
    ValTy&& val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*val*|挿入される要素 (一般的には、キーが同じ順序付けになる要素) が `hash_map` にまだ含まれていない場合に、[hash_map](../standard-library/hash-map-class.md) に挿入される要素の移動コンストラクトに使用する値。|

### <a name="return-value"></a>戻り値

`emplace` メンバー関数はペアを返しますが、その bool コンポーネントは、挿入が行われた場合は true を返し、`hash_map` に既に順序の値が等しいキーの要素が含まれている場合は、false を返します。また、その反復子コンポーネントは、新しい要素が挿入されたか要素が既に存在しているアドレスを返します。

このメンバー関数によって返されたペア `pr` の反復子コンポーネントにアクセスするには `pr.first` を使用し、この反復子を逆参照するには `*(pr.first)` を使用します。 このメンバー関数によって返される `pr` ペアの**bool**要素にアクセスするには、`pr.second` を使用し、逆参照するには `*(pr.second)` を使用します。

### <a name="remarks"></a>Remarks

要素の [hash_map::value_type](#value_type) はペアです。最初のコンポーネントがキー値と等しく、2 番目のコンポーネントが要素のデータ値と等しくなるよう、要素の値が順序付けされたペアになります。

### <a name="example"></a>例

```cpp
// hash_map_emplace.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(move(is1));
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

## <a name="emplace_hint"></a>  hash_map::emplace_hint

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

インプレースで構築された要素を、配置ヒントと共に hash_map に挿入します。

```cpp
template <class ValTy>
iterator emplace_hint(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*val*|挿入される要素 (一般的には、キーが同じ順序付けになる要素) が `hash_map` にまだ含まれていない場合に、[hash_map](../standard-library/hash-map-class.md) に挿入される要素の移動コンストラクトに使用する値。|
|*場所 (_s)*|正しい挿入ポイントの検索を開始する場所に関するヒント。|

### <a name="return-value"></a>戻り値

[hash_multimap::emplace](../standard-library/hash-multimap-class.md#emplace) メンバー関数は、`hash_map` に新しい要素が挿入された位置、または、同等の順序での既存の要素が存在する位置を指す反復子を返します。

### <a name="remarks"></a>Remarks

要素の [hash_map::value_type](#value_type) はペアです。最初のコンポーネントがキー値と等しく、2 番目のコンポーネントが要素のデータ値と等しくなるよう、要素の値が順序付けされたペアになります。

挿入ポイントが *(Where)* の直後にある場合、挿入は対数時間ではなく、償却定数時間で実行できます。

### <a name="example"></a>例

```cpp
// hash_map_emplace_hint.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, string> hm1;
    typedef pair<int, string> is1(1, "a");

    hm1.emplace(hm1.begin(), move(is1));
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

## <a name="empty"></a>  hash_map::empty

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map が空かどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

hash_map が空の場合は **true**、hash_map が空ではない場合は **false**。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_map_empty.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2;

   typedef pair <int, int> Int_Pair;
   hm1.insert ( Int_Pair ( 1, 1 ) );

   if ( hm1.empty( ) )
      cout << "The hash_map hm1 is empty." << endl;
   else
      cout << "The hash_map hm1 is not empty." << endl;

   if ( hm2.empty( ) )
      cout << "The hash_map hm2 is empty." << endl;
   else
      cout << "The hash_map hm2 is not empty." << endl;
}
```

```Output
The hash_map hm1 is not empty.
The hash_map hm2 is empty.
```

## <a name="end"></a>  hash_map::end

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_iterator end() const;

iterator end();
```

### <a name="return-value"></a>戻り値

hash_map 内の最後の要素の次の位置を指す双方向反復子。 hash_map が空の場合、hash_map::end == hash_map::begin です。

### <a name="remarks"></a>Remarks

`end` は、反復子が hash_map の末尾に達したかどうかをテストするために使用されます。

`end` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// hash_map_end.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: const_iterator hm1_cIter;
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

## <a name="equal_range"></a>  hash_map::equal_range

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

指定したキーよりも大きいキーを持つ hash_map 内の最初の要素を指す反復子と、そのキー以上のキーを持つ hash_map 内の最初の要素を指す反復子、のペアを返します。

```cpp
pair <const_iterator, const_iterator> equal_range (const Key& key) const;

pair <iterator, iterator> equal_range (const Key& key);
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の hash_map 内の要素の並べ替えキーと比較される引数キー値。

### <a name="return-value"></a>戻り値

1 番目がそのキーの [lower_bound](#lower_bound)、2 番目がそのキーの [upper_bound](#upper_bound) である、反復子のペア。

メンバー関数によって返されるペア `pr` 最初の反復子にアクセスするには、`pr` を使用します。 **最初**に、下限の反復子を逆参照するには、\* (`pr` を使用します。 **最初**)。 メンバー関数によって返さ `pr` ペアの2番目の反復子にアクセスするには、`pr` を使用します。 **次**に、上限の反復子を逆参照するには、\* (`pr` を使用します。 **2 番目**)。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_map_equal_range.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef hash_map <int, int> IntMap;
   IntMap hm1;
   hash_map <int, int> :: const_iterator hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   pair <IntMap::const_iterator, IntMap::const_iterator> p1, p2;
   p1 = hm1.equal_range( 2 );

   cout << "The lower bound of the element with "
        << "a key of 2 in the hash_map hm1 is: "
        << p1.first -> second << "." << endl;

   cout << "The upper bound of the element with "
        << "a key of 2 in the hash_map hm1 is: "
        << p1.second -> second << "." << endl;

   // Compare the upper_bound called directly
   hm1_RcIter = hm1.upper_bound( 2 );

   cout << "A direct call of upper_bound( 2 ) gives "
        << hm1_RcIter -> second << "," << endl
        << "matching the 2nd element of the pair"
        << " returned by equal_range( 2 )." << endl;

   p2 = hm1.equal_range( 4 );

   // If no match is found for the key,
   // both elements of the pair return end( )
   if ( ( p2.first == hm1.end( ) ) && ( p2.second == hm1.end( ) ) )
      cout << "The hash_map hm1 doesn't have an element "
             << "with a key less than 40." << endl;
   else
      cout << "The element of hash_map hm1 with a key >= 40 is: "
           << p1.first -> first << "." << endl;
}
```

```Output
The lower bound of the element with a key of 2 in the hash_map hm1 is: 20.
The upper bound of the element with a key of 2 in the hash_map hm1 is: 30.
A direct call of upper_bound( 2 ) gives 30,
matching the 2nd element of the pair returned by equal_range( 2 ).
The hash_map hm1 doesn't have an element with a key less than 40.
```

## <a name="erase"></a>  hash_map::erase

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内の要素または要素の範囲を指定した位置から削除するか、または指定したキーと一致する要素を削除します。

```cpp
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);

size_type erase(const key_type& key);
```

### <a name="parameters"></a>パラメーター

@No__t_1 の*場所 (_c)*
hash_map から削除する要素の位置。

*最初*の \
hash_map から削除する最初の要素の位置。

*最後*の \
hash_map から削除する最後の要素の次の位置。

*キー* \
hash_map から削除する要素のキー値。

### <a name="return-value"></a>戻り値

最初の 2 つのメンバー関数の場合は、削除された要素の後の最初の残存要素を指定する双方向反復子、または hash_map の末尾へのポインター (残存要素が存在しない場合)。

3 番目のメンバー関数の場合は、hash_map から削除された要素の数を返します。

### <a name="remarks"></a>Remarks

メンバー関数が例外をスローすることはありません。

### <a name="example"></a>例

hash_map::erase メンバー関数の使用例を次に示します。

```cpp
// hash_map_erase.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1, hm2, hm3;
    hash_map<int, int> :: iterator pIter, Iter1, Iter2;
    int i;
    hash_map<int, int>::size_type n;
    typedef pair<int, int> Int_Pair;

    for (i = 1; i < 5; i++)
    {
        hm1.insert(Int_Pair (i, i));
        hm2.insert(Int_Pair (i, i*i));
        hm3.insert(Int_Pair (i, i-1));
    }

    // The 1st member function removes an element at a given position
    Iter1 = ++hm1.begin();
    hm1.erase(Iter1);

    cout << "After the 2nd element is deleted, the hash_map hm1 is:";
    for (pIter = hm1.begin(); pIter != hm1.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 2nd member function removes elements
    // in the range [ first,  last)
    Iter1 = ++hm2.begin();
    Iter2 = --hm2.end();
    hm2.erase(Iter1, Iter2);

    cout << "After the middle two elements are deleted, "
         << "the hash_map hm2 is:";
    for (pIter = hm2.begin(); pIter != hm2.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function removes elements with a given  key
    n = hm3.erase(2);

    cout << "After the element with a key of 2 is deleted,\n"
         << "the hash_map hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;

    // The 3rd member function returns the number of elements removed
    cout << "The number of elements removed from hm3 is: "
         << n << "." << endl;

    // The dereferenced iterator can also be used to specify a key
    Iter1 = ++hm3.begin();
    hm3.erase(Iter1);

    cout << "After another element with a key equal to that"
         << endl;
    cout  << "of the 2nd element is deleted, "
          << "the hash_map hm3 is:";
    for (pIter = hm3.begin(); pIter != hm3.end(); pIter++)
        cout << " " << pIter -> second;
    cout << "." << endl;
}
```

```Output
After the 2nd element is deleted, the hash_map hm1 is: 1 3 4.
After the middle two elements are deleted, the hash_map hm2 is: 1 16.
After the element with a key of 2 is deleted,
the hash_map hm3 is: 0 2 3.
The number of elements removed from hm3 is: 1.
After another element with a key equal to that
of the 2nd element is deleted, the hash_map hm3 is: 0 3.
```

## <a name="find"></a>  hash_map::find

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

指定したキーと同じキーを持つ、hash_map 内の要素の位置を指す反復子を返します。

```cpp
iterator find(const Key& key);

const_iterator find(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の hash_map 内の要素の並べ替えキーによって照合されるキー値。

### <a name="return-value"></a>戻り値

指定したキーを持つ要素の位置を指す反復子。キーの一致が検出されない場合は、hash_map 内の最後の要素の次の位置。

### <a name="remarks"></a>Remarks

`find` は、小なり比較関係に基づいて順序を誘発する二項述語の下で、並べ替えキーが引数キーと等価である hash_map 内の要素をアドレス指定する反復子を返します。

@No__t_0 の戻り値が[const_iterator](#const_iterator)に割り当てられている場合、hash_map オブジェクトを変更することはできません。 @No__t_0 の戻り値が[反復子](#iterator)に割り当てられている場合は、hash_map オブジェクトを変更できます。

### <a name="example"></a>例

```cpp
// hash_map_find.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.find( 2 );
   cout << "The element of hash_map hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1.find( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_map can be found
   // using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1.find( hm1_AcIter -> first );
   cout << "The element of hm1 with a key matching "
        << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The element of hash_map hm1 with a key of 2 is: 20.
The hash_map hm1 doesn't have an element with a key of 4.
The element of hm1 with a key matching that of the last element is: 30.
```

## <a name="get_allocator"></a>  hash_map::get_allocator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map の構築に使用されるアロケーター オブジェクトのコピーを返します。

```cpp
Allocator get_allocator() const;
```

### <a name="return-value"></a>戻り値

hash_map で使用されるアロケーター。

### <a name="remarks"></a>Remarks

hash_map クラスのアロケーターは、クラスがどのようにストレージを管理するかを指定します。 C++ 標準ライブラリ コンテナー クラスで提供される既定のアロケーターは、ほとんどのプログラミング要件に対応しています。 独自のアロケーター クラスを作成して使用することは、C++ における高度な作業の 1 つです。

### <a name="example"></a>例

```cpp
// hash_map_get_allocator.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int>::allocator_type hm1_Alloc;
   hash_map <int, int>::allocator_type hm2_Alloc;
   hash_map <int, double>::allocator_type hm3_Alloc;
   hash_map <int, int>::allocator_type hm4_Alloc;

   // The following lines declare objects
   // that use the default allocator.
   hash_map <int, int> hm1;
   hash_map <int, int> hm2;
   hash_map <int, double> hm3;

   hm1_Alloc = hm1.get_allocator( );
   hm2_Alloc = hm2.get_allocator( );
   hm3_Alloc = hm3.get_allocator( );

   cout << "The number of integers that can be allocated"
        << endl << "before free memory is exhausted: "
        << hm2.max_size( ) << "." << endl;

   cout << "The number of doubles that can be allocated"
        << endl << "before free memory is exhausted: "
        << hm3.max_size( ) <<  "." << endl;

   // The following line creates a hash_map hm4
   // with the allocator of hash_map hm1.
   hash_map <int, int> hm4( less<int>( ), hm1_Alloc );

   hm4_Alloc = hm4.get_allocator( );

   // Two allocators are interchangeable if
   // storage allocated from each can be
   // deallocated with the other
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

## <a name="hash_map"></a>  hash_map::hash_map

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

空の hash_map を構築するか、他の hash_map の全体または一部のコピーである hash_map を構築します。

```cpp
hash_map();

explicit hash_map(
    const Traits& Comp);

hash_map(
    const Traits& Comp,
    const Allocator& Al);

hash_map(
    const hash_map& Right);

hash_map(
    hash_map&& Right);

hash_map(
    initializer_list<Type> IList);hash_map(initializer_list<Type> IList,
    const key_compare& Comp);

hash_map(
    initializer_list<Type> IList,
    const key_compare& Comp,
    const allocator_type& Al);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp);

template <class InputIterator>
hash_map(
    InputIterator First,
    InputIterator Last,
    const Traits& Comp,
    const Allocator& Al
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*ウムアルクラ*|この hash_map オブジェクトに使用するストレージアロケータークラス。既定では `Allocator` になります。|
|*コンペティション*|hash_map 内の要素の並べ替えに使用される、型 const `Traits` の比較関数。既定では `hash_compare` です。|
|*右*|構築されたマップがコピーになる元の hash_map。|
|*まずは*|コピーする要素範囲内の最初の要素の位置。|
|*前の*|コピーする要素範囲を超える最初の要素の位置。|
|*IList*|initializer_list|

### <a name="remarks"></a>Remarks

すべてのコンストラクターは、アロケーター オブジェクトの型を格納します。このオブジェクトは hash_map のメモリ ストレージを管理し、後で [get_allocator](#get_allocator) を呼び出して取得することができます。 代替アロケーターの代わりに使用されるクラス宣言やプリプロセス マクロでは、アロケーターのパラメーターが省略される場合があります。

すべてのコンストラクターは、それぞれの hash_map を初期化します。

すべてのコンストラクターは、`Traits` 型の関数オブジェクトを格納します。このオブジェクトは hash_map のキーの順序を確立するために使用され、後で [key_comp](#key_comp) を呼び出して取得することができます。

最初の3つのコンストラクターは、空の初期 hash_map を指定します。さらに、2番目のコンストラクターは要素の順序を確立するために使用する比較関数 (*Comp*) の種類を指定し、3番目のコンストラクターはアロケーターの型 (Al) を明示的に指定します。) を使用します。 キーワード **explicit** は、特定の種類の自動型変換が実行されないようにします。

4番目のコンストラクターは、hash_map*権限*のコピーを指定します。

次の 3 つのコンストラクターは、hash_map の範囲 `[First, Last)` をコピーします。下のコンストラクターになるほど、より明確に比較関数の型のクラス `Traits` とアロケーターの型を指定します。

最後のコンストラクターは、hash_map*権限*を移動します。

## <a name="insert"></a>  hash_map::insert

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map に要素や要素範囲を挿入します。

```cpp
pair <iterator, bool> insert(
    const value_type& val);

iterator insert(
    const_iterator _Where,
    const value_type& val);

template <class InputIterator>
void insert(
    InputIterator first,
    InputIterator last);

template <class ValTy>
pair <iterator, bool>
insert(
    ValTy&& val);

template <class ValTy>
iterator insert(
    const_iterator _Where,
    ValTy&& val);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*val*|挿入される要素が hash_map にまだ含まれていない場合 (一般的には、キーが同じ順序付けになる要素がまだ含まれていない場合) に、hash_map に挿入される要素の値。|
|*場所 (_s)*|正しい挿入ポイントの検索を開始する場所に関するヒント。|
|*まずは*|hash_map からコピーされる最初の要素の位置。|
|*前の*|hash_map からコピーされる最後の要素の次の位置。|

### <a name="return-value"></a>戻り値

最初の `insert` メンバー関数は、挿入が行われた場合に true を返すブール値のペアを返します。また、順序の値が同じキーを持つ要素が hash_map に既に含まれていて、その反復子コンポーネントがアドレスを返した場合は false を返します。新しい要素が挿入された場所、または要素が既に存在していた場所。

このメンバー関数によって返されるペア `pr` の反復子コンポーネントにアクセスするには、`pr` を使用します。 **まず**、\* (`pr` を使用します。 **最初**)。 このメンバー関数によって返されるペア `pr` の**bool**コンポーネントにアクセスするには、`pr` を使用します。 **次**に、\* (`pr` を使用します。 **2 番目**)。

2番目の `insert` メンバー関数 (ヒントバージョン) は、新しい要素が hash_map に挿入された位置を指す反復子を返します。

最後の2つの `insert` メンバー関数は、最初の2つのメンバー関数と同じように動作しますが、挿入された値がコンストラクトによって移動される点が異なります。

### <a name="remarks"></a>Remarks

要素の [value_type](../standard-library/map-class.md#value_type) はペアです。最初のコンポーネントがキー値と等しく、2 番目のコンポーネントが要素のデータ値と等しくなるよう、要素の値が順序付けされたペアになります。

挿入ポイント*が位置の*直後にある場合は、挿入ポイントが対数時間ではなく insert のヒントバージョンに対して、償却定数時間で挿入されることがあります。

3 番目のメンバー関数は、指定したセットの範囲 *[First, Last)* の反復子が指す各要素に対応する hash_map に要素値のシーケンスを挿入します。

### <a name="example"></a>例

```cpp
// hash_map_insert.cpp
// compile with: /EHsc
#include<hash_map>
#include<iostream>
#include <string>

int main()
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int>::iterator hm1_pIter, hm2_pIter;

    hash_map<int, int> hm1, hm2;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 10));
    hm1.insert(Int_Pair(2, 20));
    hm1.insert(Int_Pair(3, 30));
    hm1.insert(Int_Pair(4, 40));

    cout << "The original elements (Key => Value) of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << " " << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    pair< hash_map<int,int>::iterator, bool > pr;
    pr = hm1.insert(Int_Pair(1, 10));

    if (pr.second == true)
    {
        cout << "The element 10 was inserted in hm1 successfully."
            << endl;
    }
    else
    {
        cout << "The element 10 already exists in hm1\n"
            << "with a key value of "
            << "((pr.first) -> first) = " << (pr.first)->first
            << "." << endl;
    }

    // The hint version of insert
    hm1.insert(--hm1.end(), Int_Pair(5, 50));

    cout << "After the insertions, the elements of hm1 are:";
    for (hm1_pIter = hm1.begin(); hm1_pIter != hm1.end(); hm1_pIter++)
        cout << endl << hm1_pIter -> first << " => "
             << hm1_pIter->second;
    cout << endl;

    hm2.insert(Int_Pair(10, 100));

    // The templatized version inserting a range
    hm2.insert( ++hm1.begin(), --hm1.end() );

    cout << "After the insertions, the elements of hm2 are:";
    for (hm2_pIter = hm2.begin(); hm2_pIter != hm2.end(); hm2_pIter++)
        cout << endl << hm2_pIter -> first << " => "
             << hm2_pIter->second;
    cout << endl;

    // The templatized versions move constructing elements
    hash_map<int, string> hm3, hm4;
    pair<int, string> is1(1, "a"), is2(2, "b");

    hm3.insert(move(is1));
    cout << "After the move insertion, hm3 contains:" << endl
      << hm3.begin()->first
      << " => " << hm3.begin()->second
      << endl;

    hm4.insert(hm4.begin(), move(is2));
    cout << "After the move insertion, hm4 contains:" << endl
      << hm4.begin()->first
      << " => " << hm4.begin()->second
      << endl;
}
```

```Output
The original elements (Key => Value) of hm1 are:
1 => 10
2 => 20
3 => 30
4 => 40
The element 10 already exists in hm1
with a key value of ((pr.first) -> first) = 1.
After the insertions, the elements of hm1 are:
1 => 10
2 => 20
3 => 30
4 => 40
5 => 50
After the insertions, the elements of hm2 are:
2 => 20
10 => 100
3 => 30
4 => 40
After the move insertion, hm3 contains:
1 => a
After the move insertion, hm4 contains:
2 => b
```

## <a name="iterator"></a>  hash_map::iterator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内の任意の要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::iterator iterator;
```

### <a name="remarks"></a>Remarks

Hash_map によって定義される `iterator` は、 [value_type](#value_type)のオブジェクトである要素を指します。これは、最初 \<const のメンバーが要素のキーであり、2番目のメンバーが要素によって保持されているマップされた datum である、**型 >** です。

Multimap 内の要素を指す**反復子**`Iter` を逆参照するには、`->` 演算子を使用します。

要素のキーの値にアクセスするには、**最初**に  ->  `Iter` を使用します。これは、(\* `Iter`) に相当します。 **最初**に。 要素のマップされた datum の値にアクセスするには、`Iter`  -> **second**を使用します。これは、(\* `Iter`) に相当します。 **second** に初期化します。

@No__t_0 型を使用して、要素の値を変更できます。

### <a name="example"></a>例

@No__t_1 の宣言方法や使用方法の例については、 [begin](#begin)の例を参照してください。

## <a name="key_comp"></a>  hash_map::key_comp

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内のキーの並べ替えに使用する比較オブジェクトのコピーを取得します。

```cpp
key_compare key_comp() const;
```

### <a name="return-value"></a>戻り値

hash_map が要素の並べ替えに使用する関数オブジェクトを返します。

### <a name="remarks"></a>Remarks

格納されているオブジェクトは以下のメンバー関数を定義します。

**bool operator**( **const Key&** `left` **, const Key&** `right`);

これは、並べ替え順で `left` が `right` に先行しかつ等しくない場合に **true** を返します。

### <a name="example"></a>例

```cpp
// hash_map_key_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_map <int, int, hash_compare<int, less<int> > > hm1;
   hash_map <int, int, hash_compare<int, less<int> > >::key_compare
      kc1 = hm1.key_comp( ) ;

   // Operator stored in kc1 tests order & returns bool value
   bool result1 = kc1( 2, 3 ) ;
   if( result1 == true )
   {
      cout << "kc1( 2,3 ) returns value of true,"
           << "\n where kc1 is the function object of hm1"
           << " of type key_compare." << endl;
   }
   else
   {
      cout << "kc1( 2,3 ) returns value of false"
           << "\n where kc1 is the function object of hm1"
           << " of type key_compare." << endl;
   }

   hash_map <int, int, hash_compare<int, greater<int> > > hm2;
   hash_map <int, int, hash_compare<int, greater<int> > >
      ::key_compare kc2 = hm2.key_comp( );

   // Operator stored in kc2 tests order & returns bool value
   bool result2 = kc2( 2, 3 ) ;
   if( result2 == true )
   {
      cout << "kc2( 2,3 ) returns value of true,"
           << "\n where kc2 is the function object of hm2"
           << " of type key_compare." << endl;
   }
   else
   {
      cout << "kc2( 2,3 ) returns value of false,"
           << "\n where kc2 is the function object of hm2"
           << " of type key_compare." << endl;
   }
}
```

## <a name="key_compare"></a>  hash_map::key_compare

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

2 つの並べ替えキーを比較して、map 内の 2 つの要素の相対順序を決定できる関数オブジェクトを提供する型。

```cpp
typedef Traits key_compare;
```

### <a name="remarks"></a>Remarks

`key_compare` はテンプレート パラメーター `Traits` のシノニムです。

`Traits` の詳細については、[hash_map クラス](../standard-library/hash-map-class.md)のトピックをご覧ください。

### <a name="example"></a>例

`key_compare` の宣言方法や使用方法の例については、[key_comp](#key_comp) の例をご覧ください。

## <a name="key_type"></a>  hash_map::key_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map の各要素の一部である並べ替えキー オブジェクトを表す型。

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Remarks

`key_type` はテンプレート パラメーター `Key` のシノニムです。

`Key` の詳細については、[hash_map クラス](../standard-library/hash-map-class.md)のトピックのコメントのセクションをご覧ください。

### <a name="example"></a>例

`key_type` の宣言方法や使用方法の例については、[value_type](#value_type) の例をご覧ください。

## <a name="lower_bound"></a>  hash_map::lower_bound

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

指定したキー値以上のキー値を持つ、hash_map 内の最初の要素を指す反復子を返します。

```cpp
iterator lower_bound(const Key& key);

const_iterator lower_bound(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の hash_map 内の要素の並べ替えキーと比較される引数キー値。

### <a name="return-value"></a>戻り値

引数キー以上のキーを持つ hash_map 内の要素の位置を指す、または、キーの一致が検出されない場合は hash_map 内の最後の要素の次の位置を指す、[反復子](#iterator)または [const_iterator](#const_iterator)。

`lower_bound` の戻り値が `const_iterator` に割り当てられている場合、hash_map オブジェクトは変更できません。 @No__t_0 の戻り値が `iterator` に割り当てられている場合は、hash_map オブジェクトを変更できます。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_map_lower_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.lower_bound( 2 );
   cout << "The first element of hash_map hm1 with a key of 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end( ) is returned
   hm1_RcIter = hm1. lower_bound ( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key of 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key of 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // An element at a specific location in the hash_map can be
   // found using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.end( );
   hm1_AcIter--;
   hm1_RcIter = hm1. lower_bound ( hm1_AcIter -> first );
   cout << "The element of hm1 with a key matching "
        << "that of the last element is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key of 2 is: 20.
The hash_map hm1 doesn't have an element with a key of 4.
The element of hm1 with a key matching that of the last element is: 30.
```

## <a name="mapped_type"></a>  hash_map::mapped_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内に格納されているデータ型を表す型。

```cpp
typedef Type mapped_type;
```

### <a name="remarks"></a>Remarks

`mapped_type` 型は、テンプレート パラメーター `Type` のシノニムです。

`Type` の詳細については、[hash_map クラス](../standard-library/hash-map-class.md)のトピックをご覧ください。

### <a name="example"></a>例

`key_type` の宣言方法や使用方法の例については、[value_type](#value_type) の例をご覧ください。

## <a name="max_size"></a>  hash_map::max_size

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map の最大長を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

hash_map の可能な最大長。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_map_max_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: size_type i;

   i = hm1.max_size( );
   cout << "The maximum possible length "
        << "of the hash_map is " << i << "."
        << endl << "(Magnitude is machine specific.)";
}
```

## <a name="op_at"></a>  hash_map::operator[]

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

`hash_map` に、指定したキー値を持つ要素を挿入します。

```cpp
Type& operator[](const Key& key);

Type& operator[](Key&& key);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*key*|挿入する要素のキー値。|

### <a name="return-value"></a>戻り値

挿入される要素のデータ値への参照。

### <a name="remarks"></a>Remarks

引数のキー値が見つからない場合は、データ型の既定値と一緒に挿入されます。

`operator[]` は、下記を用いて、`hash_map m` への要素の挿入に使用されることがあります。

`m[ key] = DataValue`;

ここで、DataValue は key のキー値を持つ要素の `mapped_type` の値*です。*

`operator[]` を使用して要素を挿入した場合、返される参照では、挿入によって既存の要素が変更されるのか、または新しい要素が作成されるのかは、示されません。 メンバー関数 [find](../standard-library/map-class.md#find) および [insert](../standard-library/map-class.md#insert) を使用して、挿入前に指定のキーを持つ要素が既に存在するかどうかを確認することができます。

### <a name="example"></a>例

```cpp
// hash_map_op_ref.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;
   hash_map <int, int> :: iterator pIter;

   // Insert a data value of 10 with a key of 1
   // into a hash_map using the operator[] member function
   hm1[ 1 ] = 10;

   // Compare other ways to insert objects into a hash_map
   hm1.insert ( hash_map <int, int> :: value_type ( 2, 20 ) );
   hm1.insert ( cInt2Int ( 3, 30 ) );

   cout  << "The keys of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // If the key already exists, operator[]
   // changes the value of the datum in the element
   hm1[ 2 ] = 40;

   // operator[] will also insert the value of the data
   // type's default constructor if the value is unspecified
   hm1[5];

   cout  << "The keys of the mapped elements are now:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> first;
   cout << "." << endl;

   cout  << "The values of the mapped elements are now:";
   for ( pIter = hm1.begin( ) ; pIter != hm1.end( ) ; pIter++ )
      cout << " " << pIter -> second;
   cout << "." << endl;

   // operator[] will also insert by moving a key
   hash_map <string, int> hm2;
   string str("a");
   hm2[move(str)] = 1;
   cout << "The moved key is " << hm2.begin()->first
      << ", with value " << hm2.begin()->second << endl;
}
```

## <a name="op_eq"></a>  hash_map::operator=

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map の要素を、別の hash_map のコピーで置き換えます。

```cpp
hash_map& operator=(const hash_map& right);

hash_map& operator=(hash_map&& right);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-|-|
|*right*|`hash_map` にコピーされる [hash_map クラス](../standard-library/hash-map-class.md)。|

### <a name="remarks"></a>Remarks

@No__t_0 内の既存の要素を消去した後、 *`operator=` の内容*を `hash_map` にコピーまたは移動します。

### <a name="example"></a>例

```cpp
// hash_map_operator_as.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map<int, int> v1, v2, v3;
   hash_map<int, int>::iterator iter;

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

## <a name="pointer"></a>  hash_map::pointer

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内の要素へのポインターを提供する型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::pointer pointer;
```

### <a name="remarks"></a>Remarks

@No__t_0 型を使用して、要素の値を変更できます。

ほとんどの場合、hash_map オブジェクト内の要素にアクセスするには、[反復子](#iterator)を使用する必要があります。

## <a name="rbegin"></a>  hash_map::rbegin

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

反転された hash_map 内の最初の要素を指す反復子を返します。

```cpp
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```

### <a name="return-value"></a>戻り値

反転された hash_map 内の最初の要素を示す、または反転されていない hash_map 内の最後の要素だったものを示す、逆順双方向反復子。

### <a name="remarks"></a>Remarks

`rbegin` は、[begin](#begin) が hash_map で使用されるのと同様に、反転された hash_map で使用されます。

`rbegin` の戻り値が [const_reverse_iterator](#const_reverse_iterator) に割り当てられている場合、hash_map オブジェクトは変更できません。 `rbegin` の戻り値が [reverse_iterator](#reverse_iterator) に割り当てられている場合、hash_map オブジェクトを変更できます。

`rbegin` を使用して、hash_map 内を後方に向かって反復処理できます。

### <a name="example"></a>例

```cpp
// hash_map_rbegin.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: reverse_iterator hm1_rIter;
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rbegin( );
   cout << "The first element of the reversed hash_map hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_map in a forward order
   cout << "The hash_map is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( ); hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_map in a reverse order
   cout << "The reversed hash_map is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( ); hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_map element can be erased by dereferencing to its key
   hm1_rIter = hm1.rbegin( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rbegin( );
   cout << "After the erasure, the first element "
        << "in the reversed hash_map is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The first element of the reversed hash_map hm1 is 3.
The hash_map is: 1 2 3 .
The reversed hash_map is: 3 2 1 .
After the erasure, the first element in the reversed hash_map is 2.
```

## <a name="reference"></a>  hash_map::reference

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map に格納されている要素への参照を提供する型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::reference reference;
```

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_map_reference.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );

   // Declare and initialize a const_reference &Ref1
   // to the key of the first element
   const int &Ref1 = ( hm1.begin( ) -> first );

   // The following line would cause an error as the
   // non-const_reference cannot be used to access the key
   // int &Ref1 = ( hm1.begin( ) -> first );

   cout << "The key of first element in the hash_map is "
        << Ref1 << "." << endl;

   // Declare and initialize a reference &Ref2
   // to the data value of the first element
   int &Ref2 = ( hm1.begin( ) -> second );

   cout << "The data value of first element in the hash_map is "
        << Ref2 << "." << endl;

   // The non-const_reference can be used to modify the
   // data value of the first element
   Ref2 = Ref2 + 5;
   cout << "The modified data value of first element is "
        << Ref2 << "." << endl;
}
```

```Output
The key of first element in the hash_map is 1.
The data value of first element in the hash_map is 10.
The modified data value of first element is 15.
```

## <a name="rend"></a>  hash_map::rend

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

反転された hash_map 内の最後の要素の次の位置を指す反復子を返します。

```cpp
const_reverse_iterator rend() const;

reverse_iterator rend();
```

### <a name="return-value"></a>戻り値

反転された hash_map 内の最後の要素の次の場所 (反転されていない hash_map 内の最初の要素の前の場所) を指す逆順双方向反復子。

### <a name="remarks"></a>Remarks

`rend` は、[end](#end) が hash_map で使用されるのと同様に、反転された hash_map で使用されます。

`rend` の戻り値が [const_reverse_iterator](#const_reverse_iterator) に割り当てられている場合、hash_map オブジェクトは変更できません。 `rend` の戻り値が [reverse_iterator](#reverse_iterator) に割り当てられている場合、hash_map オブジェクトを変更できます。

`rend` を使用して、逆順反復子が hash_map の末尾に達したかどうかをテストできます。

`rend` によって返された値は逆参照しないでください。

### <a name="example"></a>例

```cpp
// hash_map_rend.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;

   hash_map <int, int> :: iterator hm1_Iter;
   hash_map <int, int> :: reverse_iterator hm1_rIter;
   hash_map <int, int> :: const_reverse_iterator hm1_crIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "The last element of the reversed hash_map hm1 is "
        << hm1_rIter -> first << "." << endl;

   // begin can be used to start an iteration
   // through a hash_map in a forward order
   cout << "The hash_map is: ";
   for ( hm1_Iter = hm1.begin( ) ; hm1_Iter != hm1.end( );
   hm1_Iter++)
      cout << hm1_Iter -> first << " ";
      cout << "." << endl;

   // rbegin can be used to start an iteration
   // through a hash_map in a reverse order
   cout << "The reversed hash_map is: ";
   for ( hm1_rIter = hm1.rbegin( ) ; hm1_rIter != hm1.rend( );
      hm1_rIter++)
      cout << hm1_rIter -> first << " ";
      cout << "." << endl;

   // A hash_map element can be erased by dereferencing to its key
   hm1_rIter = --hm1.rend( );
   hm1.erase ( hm1_rIter -> first );

   hm1_rIter = hm1.rend( );
   hm1_rIter--;
   cout << "After the erasure, the last element "
        << "in the reversed hash_map is "
        << hm1_rIter -> first << "." << endl;
}
```

```Output
The last element of the reversed hash_map hm1 is 1.
The hash_map is: 1 2 3 .
The reversed hash_map is: 3 2 1 .
After the erasure, the last element in the reversed hash_map is 2.
```

## <a name="reverse_iterator"></a>  hash_map::reverse_iterator

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

反転された hash_map 内の 1 つの要素の読み取りまたは変更ができる双方向反復子を提供する型。

```cpp
typedef list<typename Traits::value_type, typename Traits::allocator_type>::reverse_iterator reverse_iterator;
```

### <a name="remarks"></a>Remarks

`reverse_iterator` 型は要素の値を変更できず、逆の順序で hash_map を反復処理するために使用します。

hash_map によって定義される `reverse_iterator` は [value_type](#value_type) のオブジェクトである要素を指します。これは **pair\<const Key, Type>** 型で、その最初のメンバーは要素へのキーであり、2 番目のメンバーは要素が保持するマップされたデータです。

Hash_map 内の要素を指す `reverse_iterator` `rIter` を逆参照するには、-> 演算子を使用します。

要素のキーの値にアクセスするには、**最初**に  ->  `rIter` を使用します。これは、(\* `rIter`) に相当します。 **最初**に。 要素のマップされた datum の値にアクセスするには、`rIter`  -> **second**を使用します。これは、(\* `rIter`) に相当します。 **最初**に。

### <a name="example"></a>例

`reverse_iterator` の宣言方法や使用方法の例については、[rbegin](#rbegin) の例をご覧ください。

## <a name="size"></a>  hash_map::size

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内の要素の数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

hash_map の現在の長さ。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

hash_map::size メンバー関数の使用例を次に示します。

```cpp
// hash_map_size.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
    using namespace std;
    using namespace stdext;
    hash_map<int, int> hm1, hm2;
    hash_map<int, int>::size_type i;
    typedef pair<int, int> Int_Pair;

    hm1.insert(Int_Pair(1, 1));
    i = hm1.size();
    cout << "The hash_map length is " << i << "." << endl;

    hm1.insert(Int_Pair(2, 4));
    i = hm1.size();
    cout << "The hash_map length is now " << i << "." << endl;
}
```

```Output
The hash_map length is 1.
The hash_map length is now 2.
```

## <a name="size_type"></a>  hash_map::size_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内の要素の数を表すことができる符号なし整数型。

```cpp
typedef list<typename _Traits::value_type, typename _Traits::allocator_type>::size_type size_type;
```

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

`size_type` の宣言方法や使用方法の例については、[size](#size) の例をご覧ください。

## <a name="swap"></a>  hash_map::swap

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

2 つの hash_map の要素を交換します。

```cpp
void swap(hash_map& right);
```

### <a name="parameters"></a>パラメーター

*右*\
ターゲットの hash_map と交換する要素を提供する引数の hash_map。

### <a name="remarks"></a>Remarks

メンバー関数は、要素を交換する 2 つの hash_map において要素を指定している参照、ポインター、反復子を無効化することはありません。

### <a name="example"></a>例

```cpp
// hash_map_swap.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1, hm2, hm3;
   hash_map <int, int>::iterator hm1_Iter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );
   hm2.insert ( Int_Pair ( 10, 100 ) );
   hm2.insert ( Int_Pair ( 20, 200 ) );
   hm3.insert ( Int_Pair ( 30, 300 ) );

   cout << "The original hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;

   // This is the member function version of swap
   // hm2 is said to be the argument hash_map;
   // hm1 is said to be the target hash_map
   hm1.swap( hm2 );

   cout << "After swapping with hm2, hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout  << "." << endl;

   // This is the specialized template version of swap
   swap( hm1, hm3 );

   cout << "After swapping with hm3, hash_map hm1 is:";
   for ( hm1_Iter = hm1.begin( ); hm1_Iter != hm1.end( ); hm1_Iter++ )
      cout << " " << hm1_Iter -> second;
   cout   << "." << endl;
}
```

```Output
The original hash_map hm1 is: 10 20 30.
After swapping with hm2, hash_map hm1 is: 100 200.
After swapping with hm3, hash_map hm1 is: 300.
```

## <a name="upper_bound"></a>  hash_map::upper_bound

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

指定したキーよりも大きいキー値を持つ hash_map 内の最初の要素を指す反復子を返します。

```cpp
iterator upper_bound(const Key& key);

const_iterator upper_bound(const Key& key) const;
```

### <a name="parameters"></a>パラメーター

*キー* \
検索対象の hash_map 内の要素の並べ替えキー値と比較される引数キー値。

### <a name="return-value"></a>戻り値

[反復子](#iterator)または [const_iterator](#const_iterator)。引数キーより大きいキーを持つ hash_map 内の要素の位置を指します。または、キーが一致しない場合は hash_map 内の最後の要素の次の位置を指します。

戻り値が `const_iterator` に割り当てられている場合、hash_map オブジェクトは変更できません。 戻り値が `iterator` に割り当てられている場合は、hash_map オブジェクトを変更できます。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

```cpp
// hash_map_upper_bound.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   hash_map <int, int> hm1;
   hash_map <int, int> :: const_iterator hm1_AcIter, hm1_RcIter;
   typedef pair <int, int> Int_Pair;

   hm1.insert ( Int_Pair ( 1, 10 ) );
   hm1.insert ( Int_Pair ( 2, 20 ) );
   hm1.insert ( Int_Pair ( 3, 30 ) );

   hm1_RcIter = hm1.upper_bound( 2 );
   cout << "The first element of hash_map hm1 with a key "
        << "greater than 2 is: "
        << hm1_RcIter -> second << "." << endl;

   // If no match is found for the key, end is returned
   hm1_RcIter = hm1. upper_bound ( 4 );

   if ( hm1_RcIter == hm1.end( ) )
      cout << "The hash_map hm1 doesn't have an element "
           << "with a key greater than 4." << endl;
   else
      cout << "The element of hash_map hm1 with a key > 4 is: "
           << hm1_RcIter -> second << "." << endl;

   // The element at a specific location in the hash_map can be found
   // using a dereferenced iterator addressing the location
   hm1_AcIter = hm1.begin( );
   hm1_RcIter = hm1. upper_bound ( hm1_AcIter -> first );
   cout << "The 1st element of hm1 with a key greater than that\n"
        << "of the initial element of hm1 is: "
        << hm1_RcIter -> second << "." << endl;
}
```

```Output
The first element of hash_map hm1 with a key greater than 2 is: 30.
The hash_map hm1 doesn't have an element with a key greater than 4.
The 1st element of hm1 with a key greater than that
of the initial element of hm1 is: 20.
```

## <a name="value_comp"></a>  hash_map::value_comp

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

キー値の比較によって hash_map の要素の順序を決定する関数オブジェクトを返します。

```cpp
value_compare value_comp() const;
```

### <a name="return-value"></a>戻り値

hash_map が要素の並べ替えに使用する比較関数オブジェクトを返します。

### <a name="remarks"></a>Remarks

Hash_map *m*の場合、2つの*要素 e1* (*k1*, *d1*) と*e2* (*k2*, *d2*) が[value_type](#value_type)型のオブジェクトである場合、 *k1*と*k2*は[key_type](#key_type)と d1 型のキーです。および*d2*は[mapped_type](#mapped_type)型のデータであり、4 は 5 に相当します。 格納されているオブジェクトは以下のメンバー関数を定義します。

`bool operator(value_type& left, value_type& right);`

これは、並べ替え順で `left` のキー値が `right` のキー値に先行しかつ等しくない場合に、**true** を返します。

### <a name="example"></a>例

```cpp
// hash_map_value_comp.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;

   hash_map <int, int, hash_compare<int, less<int> > > hm1;
   hash_map <int, int, hash_compare<int, less<int> > >
   ::value_compare vc1 = hm1.value_comp( );
   pair< hash_map<int,int>::iterator, bool > pr1, pr2;

   pr1= hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );
   pr2= hm1.insert ( hash_map <int, int> :: value_type ( 2, 5 ) );

   if( vc1( *pr1.first, *pr2.first ) == true )
   {
      cout << "The element ( 1,10 ) precedes the element ( 2,5 )."
           << endl;
   }
   else
   {
      cout << "The element ( 1,10 ) does not precede the element ( 2,5 )."
           << endl;
   }

   if( vc1 ( *pr2.first, *pr1.first ) == true )
   {
      cout << "The element ( 2,5 ) precedes the element ( 1,10 )."
           << endl;
   }
   else
   {
      cout << "The element ( 2,5 ) does not precede the element ( 1,10 )."
           << endl;
   }
}
```

## <a name="value_type"></a>  hash_map::value_type

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

hash_map 内に格納されているオブジェクトの型を表す型。

```cpp
typedef pair<const Key, Type> value_type;
```

### <a name="remarks"></a>Remarks

`value_type` は `pair<const key_type, mapped_type>` するように宣言されています。また、非定数 iterator または reference を使用して連想コンテナーのキーが変更されない可能性があるため、`pair<key_type, mapped_type>` ません。

### <a name="example"></a>例

```cpp
// hash_map_value_type.cpp
// compile with: /EHsc
#include <hash_map>
#include <iostream>

int main( )
{
   using namespace std;
   using namespace stdext;
   typedef pair <const int, int> cInt2Int;
   hash_map <int, int> hm1;
   hash_map <int, int> :: key_type key1;
   hash_map <int, int> :: mapped_type mapped1;
   hash_map <int, int> :: value_type value1;
   hash_map <int, int> :: iterator pIter;

   // value_type can be used to pass the correct type
   // explicitly to avoid implicit type conversion
   hm1.insert ( hash_map <int, int> :: value_type ( 1, 10 ) );

   // Compare other ways to insert objects into a hash_map
   hm1.insert ( cInt2Int ( 2, 20 ) );
   hm1[ 3 ] = 30;

   // Initializing key1 and mapped1
   key1 = ( hm1.begin( ) -> first );
   mapped1 = ( hm1.begin( ) -> second );

   cout << "The key of first element in the hash_map is "
        << key1 << "." << endl;

   cout << "The data value of first element in the hash_map is "
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
The key of first element in the hash_map is 1.
The data value of first element in the hash_map is 10.
The keys of the mapped elements are: 1 2 3.
The values of the mapped elements are: 10 20 30.
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
