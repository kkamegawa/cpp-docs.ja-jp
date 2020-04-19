---
title: hash_multiset (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::hash_multiset
- cliext::hash_multiset::begin
- cliext::hash_multiset::bucket_count
- cliext::hash_multiset::clear
- cliext::hash_multiset::const_iterator
- cliext::hash_multiset::const_reference
- cliext::hash_multiset::const_reverse_iterator
- cliext::hash_multiset::count
- cliext::hash_multiset::difference_type
- cliext::hash_multiset::empty
- cliext::hash_multiset::end
- cliext::hash_multiset::equal_range
- cliext::hash_multiset::erase
- cliext::hash_multiset::find
- cliext::hash_multiset::generic_container
- cliext::hash_multiset::generic_iterator
- cliext::hash_multiset::generic_reverse_iterator
- cliext::hash_multiset::generic_value
- cliext::hash_multiset::hash_delegate
- cliext::hash_multiset::hash_multiset
- cliext::hash_multiset::hasher
- cliext::hash_multiset::insert
- cliext::hash_multiset::iterator
- cliext::hash_multiset::key_comp
- cliext::hash_multiset::key_compare
- cliext::hash_multiset::key_type
- cliext::hash_multiset::load_factor
- cliext::hash_multiset::lower_bound
- cliext::hash_multiset::make_value
- cliext::hash_multiset::max_load_factor
- cliext::hash_multiset::operator=
- cliext::hash_multiset::rbegin
- cliext::hash_multiset::reference
- cliext::hash_multiset::rehash
- cliext::hash_multiset::rend
- cliext::hash_multiset::reverse_iterator
- cliext::hash_multiset::size
- cliext::hash_multiset::size_type
- cliext::hash_multiset::swap
- cliext::hash_multiset::to_array
- cliext::hash_multiset::upper_bound
- cliext::hash_multiset::value_comp
- cliext::hash_multiset::value_compare
- cliext::hash_multiset::value_type
helpviewer_keywords:
- <cliext/hash_set> header [STL/CLR]
- hash_multiset class [STL/CLR]
- <hash_set> header [STL/CLR]
- begin member [STL/CLR]
- bucket_count member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- count member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- equal_range member [STL/CLR]
- erase member [STL/CLR]
- find member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- hash_delegate member [STL/CLR]
- hash_multiset member [STL/CLR]
- hasher member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- load_factor member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- max_load_factor member [STL/CLR]
- operator= member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rehash member [STL/CLR]
- rend member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- upper_bound member [STL/CLR]
- value_comp member [STL/CLR]
- value_compare member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 8462bd21-6829-4dd3-ac81-c42d6fdf92f0
ms.openlocfilehash: 8d8e7ab9bcbaf9ea8ce95558c53d5936473f9c8f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222976"
---
# <a name="hashmultiset-stlclr"></a>hash_multiset (STL/CLR)

テンプレート クラスは、双方向のアクセス権を持つ要素の可変長シーケンスを制御するオブジェクトについて説明します。 コンテナーを使用する`hash_multiset`双方向を格納するテーブルの各エントリをハッシュ テーブルとして要素のシーケンスを管理するには、ノード、および 1 つの要素を格納する各ノードの一覧がリンクされています。 各要素の値は、シーケンスを順序付けをキーとして使用されます。

下記の説明で`GValue`と同じです`GKey`、さらには同じ*キー*しない限り、後者の場合は、ref 型である場合は`Key^`します。

## <a name="syntax"></a>構文

```cpp
template<typename Key>
    ref class hash_multiset
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IHash<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>パラメーター

*Key*<br/>
被制御シーケンス内の要素の主要なコンポーネントの型。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<cliext/hash_set >

**Namespace:** cliext

## <a name="declarations"></a>宣言

|型定義|説明|
|---------------------|-----------------|
|[hash_multiset::const_iterator (STL/CLR)](#const_iterator)|被制御シーケンスの定数反復子の型です。|
|[hash_multiset::const_reference (STL/CLR)](#const_reference)|要素への定数参照の型です。|
|[hash_multiset::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|被制御シーケンスの定数反転反復子の型です。|
|[hash_multiset::difference_type (STL/CLR)](#difference_type)|2 つの要素間の距離を (場合によっては符号付き) の型。|
|[hash_multiset::generic_container (STL/CLR)](#generic_container)|コンテナーのジェネリック インターフェイスの型。|
|[hash_multiset::generic_iterator (STL/CLR)](#generic_iterator)|コンテナーのジェネリック インターフェイスの反復子の型。|
|[hash_multiset::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|コンテナーのジェネリック インターフェイスの反転反復子の型。|
|[hash_multiset::generic_value (STL/CLR)](#generic_value)|コンテナーのジェネリック インターフェイスの要素の型。|
|[hash_multiset::hasher (STL/CLR)](#hasher)|キーのハッシュのデリゲート。|
|[hash_multiset::iterator (STL/CLR)](#iterator)|被制御シーケンスの反復子の型です。|
|[hash_multiset::key_compare (STL/CLR)](#key_compare)|2 つのキーの順序付けデリゲート。|
|[hash_multiset::key_type (STL/CLR)](#key_type)|順序付けキーの型です。|
|[hash_multiset::reference (STL/CLR)](#reference)|要素への参照の型です。|
|[hash_multiset::reverse_iterator (STL/CLR)](#reverse_iterator)|被制御シーケンスの反転反復子の型です。|
|[hash_multiset::size_type (STL/CLR)](#size_type)|(負ではない) 距離は 2 つの要素の型。|
|[hash_multiset::value_compare (STL/CLR)](#value_compare)|2 つの要素の値の順序付けデリゲート。|
|[hash_multiset::value_type (STL/CLR)](#value_type)|要素の型。|

|メンバー関数|説明|
|---------------------|-----------------|
|[hash_multiset::begin (STL/CLR)](#begin)|被制御シーケンスの先頭を指定します。|
|[hash_multiset::bucket_count (STL/CLR)](#bucket_count)|バケットの数をカウントします。|
|[hash_multiset::clear (STL/CLR)](#clear)|すべての要素を削除します。|
|[hash_multiset::count (STL/CLR)](#count)|指定したキーに一致する要素をカウントします。|
|[hash_multiset::empty (STL/CLR)](#empty)|要素が存在しないかどうかをテストします。|
|[hash_multiset::end (STL/CLR)](#end)|被制御シーケンスの末尾を指定します。|
|[hash_multiset::equal_range (STL/CLR)](#equal_range)|指定したキーに一致する範囲を検索します。|
|[hash_multiset::erase (STL/CLR)](#erase)|指定した位置にある要素を削除します。|
|[hash_multiset::find (STL/CLR)](#find)|指定したキーに一致する要素を検索します。|
|[hash_multiset::hash_delegate (STL/CLR)](#hash_delegate)|キーのハッシュのデリゲートをコピーします。|
|[hash_multiset::hash_multiset (STL/CLR)](#hash_multiset)|コンテナー オブジェクトを構築します。|
|[hash_multiset::insert (STL/CLR)](#insert)|要素を追加します。|
|[hash_multiset::key_comp (STL/CLR)](#key_comp)|2 つのキーの順序付けデリゲートをコピーします。|
|[hash_multiset::load_factor (STL/CLR)](#load_factor)|バケットごとの平均要素数をカウントします。|
|[hash_multiset::lower_bound (STL/CLR)](#lower_bound)|指定したキーに一致する範囲の先頭を検出します。|
|[hash_multiset::make_value (STL/CLR)](#make_value)|値オブジェクトを構築します。|
|[hash_multiset::max_load_factor (STL/CLR)](#max_load_factor)|バケットあたりの最大要素数を取得または設定します。|
|[hash_multiset::rbegin (STL/CLR)](#rbegin)|反転被制御シーケンスの先頭を指定します。|
|[hash_multiset::rehash (STL/CLR)](#rehash)|ハッシュ テーブルをリビルドします。|
|[hash_multiset::rend (STL/CLR)](#rend)|反転被制御シーケンスの末尾を指定します。|
|[hash_multiset::size (STL/CLR)](#size)|要素の数をカウントします。|
|[hash_multiset::swap (STL/CLR)](#swap)|2 つのコンテナーのコンテンツを交換します。|
|[hash_multiset::to_array (STL/CLR)](#to_array)|被制御シーケンスを新しい配列にコピーします。|
|[hash_multiset::upper_bound (STL/CLR)](#upper_bound)|指定したキーに一致する範囲の末尾を検索します。|
|[hash_multiset::value_comp (STL/CLR)](#value_comp)|2 つの要素の値の順序付けデリゲートをコピーします。|

|演算子|説明|
|--------------|-----------------|
|[hash_multiset::operator= (STL/CLR)](#op)|被制御シーケンスを置き換えます。|

## <a name="interfaces"></a>インターフェイス

|Interface|説明|
|---------------|-----------------|
|<xref:System.ICloneable>|オブジェクトが重複しています。|
|<xref:System.Collections.IEnumerable>|要素をシーケンス処理します。|
|<xref:System.Collections.ICollection>|要素のグループを管理します。|
|<xref:System.Collections.Generic.IEnumerable%601>|型指定された要素をシーケンス処理します。|
|<xref:System.Collections.Generic.ICollection%601>|型指定された要素のグループを管理します。|
|IHash\<キーの値 >|ジェネリックなコンテナーを管理します。|

## <a name="remarks"></a>Remarks

オブジェクトでは、割り当ておよび双方向リンク リスト内の個々 のノードとして、制御するシーケンスの記憶域を解放します。 アクセスを高速化、オブジェクトもサブリストのシーケンスとしてリスト全体を効果的に管理する (ハッシュ テーブル) の一覧へのポインターの可変長配列を保持するか、バケットします。 別の 1 つのノードの内容のコピーからではなく、ノード間のリンクを変更することで順序付けられた保持するバケットに要素を挿入します。 つまり、挿入し、残りの要素を中断することがなく自由に要素を削除することができます。

オブジェクトは、各バケット ストアド デリゲート型のオブジェクトを呼び出すことによって、制御を注文[hash_set::key_compare (STL/CLR)](../dotnet/hash-set-key-compare-stl-clr.md)します。 Hash_set; を作成する場合は、ストアド デリゲート オブジェクトを指定できます。既定値は、比較でデリゲート オブジェクトを指定しない場合`operator<=(key_type, key_type)`します。

メンバー関数を呼び出すことによって、ストアド デリゲート オブジェクトにアクセスする[hash_set::key_comp (STL/CLR)](../dotnet/hash-set-key-comp-stl-clr.md)`()`します。 このようなデリゲート オブジェクトがキー型の間の同等の順序を定義する必要があります[hash_set::key_type (STL/CLR)](../dotnet/hash-set-key-type-stl-clr.md)します。 任意の 2 つのキーのつまり`X`と`Y`:

`key_comp()(X, Y)` 呼び出しごとに、同じブール型の結果を返します。

場合`key_comp()(X, Y) && key_comp()(Y, X)`が true の場合、`X`と`Y`同等の順序を持つと言います。

ように動作する任意の順序付けルール`operator<=(key_type, key_type)`、`operator>=(key_type, key_type)`または`operator==(key_type, key_type)`eqivalent の順序を定義します。

コンテナーにより要素キーを持つは、同等の順序がある (および同じ整数値にハッシュ) が、バケット内の隣接するのみことに注意してください。 テンプレート クラスとは異なり[hash_set (STL/CLR)](../dotnet/hash-set-stl-clr.md)、テンプレート クラスのオブジェクト`hash_multiset`はすべての要素のキーが一意である必要ありません。 (2 つ以上のキーと同じ順序付けします。)

オブジェクトを決定するバケット ストアド デリゲート型のオブジェクトを呼び出すことによって特定の順序付けキーを含める必要があります[hash_set::hasher (STL/CLR)](../dotnet/hash-set-hasher-stl-clr.md)します。 メンバー関数を呼び出すことによって格納されているこのオブジェクトにアクセスする[hash_set::hash_delegate (STL/CLR)](../dotnet/hash-set-hash-delegate-stl-clr.md) `()`キーの値に依存する整数値を取得します。 Hash_set; を作成する場合は、ストアド デリゲート オブジェクトを指定できます。既定値は、関数でデリゲート オブジェクトを指定しない場合`System::Object::hash_value(key_type)`します。 任意のキー、つまり`X`と`Y`:

`hash_delegate()(X)` すべての呼び出しで同じ結果の整数値を返します。

場合`X`と`Y`と同じ順序付け、し`hash_delegate()(X)`として同じ整数の結果を返す必要があります`hash_delegate()(Y)`します。

各要素は、キーと値の両方として機能します。 シーケンスは、検索、挿入、および内にある (定数時間) - シーケンス内の要素の数の独立した少なくともケースの最適な操作の数と、任意の要素の削除を許可するように表されます。 要素を挿入しても反復子の有効性は失われません。また、要素を削除した場合は、削除された要素を指す反復子だけが無効化されます。

ハッシュされた値が均等に分散していない場合、ハッシュ テーブルは逆ことができます。 ハッシュ関数を常に、同じ値を返す--極度の検索、挿入、削除は、シーケンス (線形時間) 内の要素の数に比例します。 コンテナーは、適切なハッシュ関数、mean のバケットのサイズを選択するしますが、ハッシュ テーブルのサイズ (バケットの合計数) は、これらの選択肢の一部またはすべてをオーバーライドできます。 、たとえば、関数を参照してください[hash_set::max_load_factor (STL/CLR)](../dotnet/hash-set-max-load-factor-stl-clr.md)と[hash_set::rehash (STL/CLR)](../dotnet/hash-set-rehash-stl-clr.md)します。

Hash_multiset は、隣接する要素を被制御シーケンス内の要素を指定する反復子を指定する手順は、双方向反復子をサポートします。 特別なヘッド ノードによって返される反復子に対応[hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`します。 存在する場合は、被制御シーケンスの最後の要素に到達するこの反復子をデクリメントできます。 ヘッド ノードに到達する hash_multiset の反復子をインクリメントして等しく比較がし`end()`します。 によって返される反復子を逆参照することはできませんが、`end()`します。

その位置を表す数値を直接指定した hash_multiset の要素を参照することはできないことに注意してください。--ランダム アクセス反復子が必要です。

Hash_multiset の反復子は、それに関連付けられているコンテナーを識別するハンドルを格納する hash_multiset が関連付けられているノードを識別するハンドルを格納します。 関連付けられているコンテナー オブジェクトでのみ、反復子を使用することができます。 Hash_multiset の反復子は、関連付けられている hash_multiset ノードがいくつかの hash_multiset に関連付けられている限り有効です。 さらに、有効な反復子は dereferencable--へのアクセスまたは--指定する要素の値を変更すると等しくない限り、使用する`end()`します。

消去、または要素を削除する、格納されている値のデストラクターを呼び出します。 コンテナーを破棄するには、すべての要素が消去されます。 したがって、要素型を持つ ref クラスは、コンテナーによりする要素よりも長く保持しないコンテナーです。 ただし、ハンドルのコンテナーは*いない*その要素を破棄します。

## <a name="members"></a>メンバー

## <a name="begin"></a> hash_multiset::begin (STL/CLR)

被制御シーケンスの先頭を指定します。

### <a name="syntax"></a>構文

```cpp
iterator begin();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンス、または空のシーケンスの末尾を越えた最初の要素を指定する双方向反復子を返します。 指定する反復子を取得するために使用、`current`被制御シーケンスの長さが変更された場合、被制御シーケンスが、そのステータスの先頭を変更できます。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_begin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_multiset::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
```

## <a name="bucket_count"></a> hash_multiset::bucket_count (STL/CLR)

バケットの数をカウントします。

### <a name="syntax"></a>構文

```cpp
int bucket_count();
```

### <a name="remarks"></a>Remarks

メンバー関数は、現在のバケット数を返します。 これを使用するにはハッシュ テーブルのサイズを決定します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_bucket_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="clear"></a> hash_multiset::clear (STL/CLR)

すべての要素を削除します。

### <a name="syntax"></a>構文

```cpp
void clear();
```

### <a name="remarks"></a>Remarks

メンバー関数は、効果的に呼び出す[hash_multiset::erase (STL/CLR)](../dotnet/hash-multiset-erase-stl-clr.md) `(` [hash_multiset::begin (STL/CLR)](../dotnet/hash-multiset-begin-stl-clr.md) `(),` [hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`())`. これを使用するには、被制御シーケンスが空であることを確認します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_clear.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 0
a b
size() = 0
```

## <a name="const_iterator"></a> hash_multiset::const_iterator (STL/CLR)

被制御シーケンスの定数反復子の型です。

### <a name="syntax"></a>構文

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Remarks

この型が指定されていない型のオブジェクトを表します`T2`被制御シーケンスの定数双方向反復子として機能することができます。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_const_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_multiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reference"></a> hash_multiset::const_reference (STL/CLR)

要素への定数参照の型です。

### <a name="syntax"></a>構文

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Remarks

この型は、要素への定数参照を表します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_const_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_multiset::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Myhash_multiset::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reverse_iterator"></a> hash_multiset::const_reverse_iterator (STL/CLR)

被制御シーケンスの定数反転反復子の種類.

### <a name="syntax"></a>構文

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Remarks

この型が指定されていない型のオブジェクトを表します`T4`被制御シーケンスの定数反転反復子として機能することができます。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_multiset::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="count"></a> hash_multiset::count (STL/CLR)

指定したキーに一致する要素の数を検索します。

### <a name="syntax"></a>構文

```cpp
size_type count(key_type key);
```

#### <a name="parameters"></a>パラメーター

*key*<br/>
検索対象のキー値。

### <a name="remarks"></a>Remarks

メンバー関数と同等の順序を持つ被制御シーケンス内の要素の数を返します*キー*します。 指定したキーと一致する、被制御シーケンスの現在の要素の数を決定するのに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_count.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
a b c
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="difference_type"></a> hash_multiset::difference_type (STL/CLR)

2 つの要素間の距離を符号付きの型。

### <a name="syntax"></a>構文

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Remarks

この型は、場合によって負の値の要素の数を表します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_difference_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_multiset::difference_type diff = 0;
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Myhash_multiset::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="empty"></a> hash_multiset::empty (STL/CLR)

要素が存在しないかどうかをテストします。

### <a name="syntax"></a>構文

```cpp
bool empty();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスが空の場合に true を返します。 同じになります[hash_multiset::size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md)`() == 0`します。 Hash_multiset が空かどうかをテストに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_empty.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="end"></a> hash_multiset::end (STL/CLR)

被制御シーケンスの末尾を指定します。

### <a name="syntax"></a>構文

```cpp
iterator end();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンスの最後の位置を指し示す双方向反復子を返します。 被制御シーケンスの末尾を指定する反復子を取得するのにために使用します。そのステータスは被制御シーケンスの長さが変更された場合は変更されません。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_end.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect last two items
    Myhash_multiset::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
```

## <a name="equal_range"></a> hash_multiset::equal_range (STL/CLR)

指定したキーに一致する範囲を検索します。

### <a name="syntax"></a>構文

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>パラメーター

*key*<br/>
検索対象のキー値。

### <a name="remarks"></a>Remarks

メンバー関数は、反復子のペアを返します。 `cliext::pair<iterator, iterator>(` [hash_multiset::lower_bound (STL/CLR)](../dotnet/hash-multiset-lower-bound-stl-clr.md) `(key),` [hash_multiset::upper_bound (STL/CLR)](../dotnet/hash-multiset-upper-bound-stl-clr.md)`(key))`します。 指定したキーに一致する要素を被制御シーケンスの現在の範囲を決定するのに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_equal_range.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
typedef Myhash_multiset::pair_iter_iter Pairii;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("{0} ", *pair1.first);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
equal_range(L'x') empty = True
b
```

## <a name="erase"></a> hash_multiset::erase (STL/CLR)

指定した位置にある要素を削除します。

### <a name="syntax"></a>構文

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
bool erase(key_type key)
```

#### <a name="parameters"></a>パラメーター

*first*<br/>
消去する範囲の先頭。

*key*<br/>
消去するキー値。

*last*<br/>
消去する範囲の終了。

*where*<br/>
消去する要素。

### <a name="remarks"></a>Remarks

最初のメンバー関数が指す被制御シーケンスの要素を削除する*場所*、および削除するには、要素の後に残る最初の要素を指定する反復子を返しますまたは[hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md) `()`そのような要素が存在しない場合。 これを使用するには 1 つの要素を削除します。

2 番目のメンバー関数は、範囲の被制御シーケンスの要素を削除する [`first`、 `last`)、し、削除された要素の後に残る最初の要素を指定する反復子を返しますまたは`end()`場合、このような要素がないです。存在する. これを使用するには 0 個以上の連続する要素を削除します。

3 番目のメンバー関数は、キーを持つと同じ順序付けの被制御シーケンスの任意の要素を削除します。 を*キー*、削除された要素の数のカウントを返します。 削除や、指定したキーと一致するすべての要素のカウントを使用するとします。

各要素のデータ消去では、被制御シーケンス内の要素の数の対数に比例して時間がかかります。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_erase.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

    // add elements and display " b c d e"
    c1.insert(L'd');
    c1.insert(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // erase all but end
    Myhash_multiset::iterator it = c1.end();
    System::Console::WriteLine("erase(begin(), end()-1) = {0}",
        *c1.erase(c1.begin(), --it));
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
a b c
erase(begin()) = b
b c d e
erase(begin(), end()-1) = e
size() = 1
```

## <a name="find"></a> hash_multiset::find (STL/CLR)

指定したキーに一致する要素を検索します。

### <a name="syntax"></a>構文

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>パラメーター

*key*<br/>
検索対象のキー値。

### <a name="remarks"></a>Remarks

被制御シーケンス内の少なくとも 1 つの要素があるのと同じ順序付け場合*キー*、メンバー関数は、それらの要素のいずれかを指定する反復子を返しますそれ以外の場合を返します[hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`。 指定したキーに一致する制御シーケンス内の要素を検索に使用します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_find.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());
    System::Console::WriteLine("find {0} = {1}",
        L'b', *c1.find(L'b'));
    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
a b c
find A = False
find b = b
find C = False
```

## <a name="generic_container"></a> hash_multiset::generic_container (STL/CLR)

コンテナーのジェネリック インターフェイスの型。

### <a name="syntax"></a>構文

```cpp
typedef Microsoft::VisualC::StlClr::
    IHash<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Remarks

この型は、このテンプレートのコンテナー クラスのジェネリック インターフェイスを表します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_generic_container.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(L'e');
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c d
a b c d e
```

## <a name="generic_iterator"></a> hash_multiset::generic_iterator (STL/CLR)

コンテナーのジェネリック インターフェイスを使用するため、反復子の型。

### <a name="syntax"></a>構文

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerBidirectionalIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Remarks

この型は、このテンプレートのコンテナー クラスのジェネリック インターフェイスで使用できる汎用的な反復子を表します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_generic_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_iterator gcit = gc1->begin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="generic_reverse_iterator"></a> hash_multiset::generic_reverse_iterator (STL/CLR)

コンテナーのジェネリック インターフェイスを使用する反転反復子の型。

### <a name="syntax"></a>構文

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value>
    generic_reverse_iterator;
```

### <a name="remarks"></a>Remarks

この型は、このテンプレートのコンテナー クラスのジェネリック インターフェイスで使用できる汎用の反転反復子を表します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_reverse_iterator gcit = gc1->rbegin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
c
```

## <a name="generic_value"></a> hash_multiset::generic_value (STL/CLR)

コンテナーのジェネリック インターフェイスを使用するための要素の型。

### <a name="syntax"></a>構文

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Remarks

この型は、型のオブジェクトを表します。`GValue`ストアド要素の値をこのテンプレートのコンテナー クラスのジェネリック インターフェイスを使用するについて説明します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_generic_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct a generic container
    Myhash_multiset::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // get an element and display it
    Myhash_multiset::generic_iterator gcit = gc1->begin();
    Myhash_multiset::generic_value gcval = *gcit;
    System::Console::WriteLine("{0} ", gcval);
    return (0);
    }
```

```Output
a b c
a b c
a
```

## <a name="hash_delegate"></a> hash_multiset::hash_delegate (STL/CLR)

指定したキーに一致する要素を検索します。

### <a name="syntax"></a>構文

```cpp
hasher^ hash_delegate();
```

### <a name="remarks"></a>Remarks

メンバー関数では、キーの値を整数に変換するために使用するデリゲートを返します。 キーのハッシュに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_hash_delegate.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="hash_multiset"></a> hash_multiset::hash_multiset (STL/CLR)

コンテナー オブジェクトを構築します。

### <a name="syntax"></a>構文

```cpp
hash_multiset();
explicit hash_multiset(key_compare^ pred);
hash_multiset(key_compare^ pred, hasher^ hashfn);
hash_multiset(hash_multiset<Key>% right);
hash_multiset(hash_multiset<Key>^ right);
template<typename InIter>
    hash_multiset(InIter first, InIter last);
template<typename InIter>
    hash_multiset(InIter first, InIter last,
        key_compare^ pred);
template<typename InIter>
    hash_multiset(InIter first, InIter last,
        key_compare^ pred, hasher^ hashfn);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
hash_multiset(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred, hasher^ hashfn);
```

#### <a name="parameters"></a>パラメーター

*first*<br/>
挿入する範囲の先頭。

*hashfn*<br/>
ハッシュ バケットにマッピングのキーの関数。

*last*<br/>
挿入する範囲の終了。

*Pred*<br/>
被制御シーケンスの述語を順序付けします。

*right*<br/>
挿入するオブジェクトまたは範囲。

### <a name="remarks"></a>Remarks

コンス トラクター。

`hash_multiset();`

既定の順序の述語を使用して要素のない、被制御シーケンスを初期化`key_compare()`、および既定のハッシュ関数を使用します。 これを使用するには、既定の順序の述語とハッシュ関数を持つ、空の初期被制御シーケンスを指定します。

コンス トラクター。

`explicit hash_multiset(key_compare^ pred);`

順序付け述語で、要素のない、被制御シーケンスを初期化します*pred*、および既定のハッシュ関数を使用します。 指定した順序付け述語および既定のハッシュ関数を持つ、空の初期被制御シーケンスを指定して使用します。

コンス トラクター。

`hash_multiset(key_compare^ pred, hasher^ hashfn);`

順序付け述語で、要素のない、被制御シーケンスを初期化します*pred*、ハッシュ関数を使用して*hashfn*します。 これを使用して、順序指定された述語とハッシュ関数を持つ、空の初期被制御シーケンスを指定します。

コンス トラクター。

`hash_multiset(hash_multiset<Key>% right);`

シーケンスが被制御シーケンスを初期化します [`right.begin()`、 `right.end()`)、既定の順序の述語、および既定のハッシュ関数。 Hash_multiset オブジェクトによって制御されるシーケンスのコピーである初期被制御シーケンスを指定するために使用*右*既定の順序付け述語およびハッシュ関数を使用します。

コンス トラクター。

`hash_multiset(hash_multiset<Key>^ right);`

シーケンスが被制御シーケンスを初期化します [`right->begin()`、 `right->end()`)、既定の順序の述語、および既定のハッシュ関数。 Hash_multiset オブジェクトによって制御されるシーケンスのコピーである初期被制御シーケンスを指定するために使用*右*既定の順序付け述語およびハッシュ関数を使用します。

コンス トラクター。

`template<typename InIter> hash_multiset(InIter first, InIter last);`

シーケンスが被制御シーケンスを初期化します [`first`、 `last`)、既定の順序の述語、および既定のハッシュ関数。 これを使用するには述語とハッシュ関数を順序付け、既定値は、被制御シーケンスの別のシーケンスをコピーを作成します。

コンス トラクター。

`template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred);`

シーケンスが被制御シーケンスを初期化します [`first`、 `last`)、順序付け述語で*pred*と既定のハッシュ関数を使用します。 これを使用するには、被制御シーケンスの別のシーケンスを指定した順序付け述語と既定のハッシュ関数のコピーを作成します。

コンス トラクター。

`template<typename InIter> hash_multiset(InIter first, InIter last, key_compare^ pred, hasher^ hashfn);`

シーケンスが被制御シーケンスを初期化します [`first`、 `last`)、順序付け述語で*pred*、ハッシュ関数を使用して*hashfn*します。 これを使用するには、被制御シーケンスの順序指定された述語とハッシュ関数で、もう 1 つのシーケンスのコピーを作成します。

コンス トラクター。

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right);`

列挙子によって指定されたシーケンスの被制御シーケンスを初期化します*右*既定の順序の述語、および既定のハッシュ関数。 これを使用するには、被制御シーケンスの既定の順序の述語とハッシュ関数で、列挙子によって説明されているもう 1 つのシーケンスのコピーを作成します。

コンス トラクター。

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

列挙子によって指定されたシーケンスの被制御シーケンスを初期化します*右*、順序付け述語で*pred*と既定のハッシュ関数を使用します。 これを使用するには、被制御シーケンスの指定した順序付け述語と既定ハッシュ関数を使用した、列挙子によって説明されているもう 1 つのシーケンスのコピーを作成します。

コンス トラクター。

`hash_multiset(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred, hasher^ hashfn);`

列挙子によって指定されたシーケンスの被制御シーケンスを初期化します*右*、順序付け述語で*pred*、ハッシュ関数を使用して*hashfn*します。 これを使用するには、被制御シーケンスの順序指定された述語とハッシュ関数で、列挙子によって説明されているもう 1 つのシーケンスのコピーを作成します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_construct.cpp
// compile with: /clr
#include <cliext/hash_set>

int myfun(wchar_t key)
    { // hash a key
    return (key ^ 0xdeadbeef);
    }

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
// construct an empty container
    Myhash_multiset c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule
    Myhash_multiset c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an ordering rule and hash function
    Myhash_multiset c2h(cliext::greater_equal<wchar_t>(),
        gcnew Myhash_multiset::hasher(&myfun));
    System::Console::WriteLine("size() = {0}", c2h.size());

    c2h.insert(c1.begin(), c1.end());
    for each (wchar_t elem in c2h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an iterator range
    Myhash_multiset c3(c1.begin(), c1.end());
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Myhash_multiset c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule and hash function
    Myhash_multiset c4h(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>(),
        gcnew Myhash_multiset::hasher(&myfun));
    for each (wchar_t elem in c4h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct with an enumeration
    Myhash_multiset c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Myhash_multiset c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>());
    for each (wchar_t elem in c6)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule and hash function
    Myhash_multiset c6h(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3,
            cliext::greater_equal<wchar_t>(),
                gcnew Myhash_multiset::hasher(&myfun));
    for each (wchar_t elem in c6h)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine();

    // construct from a generic container
    Myhash_multiset c7(c4);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct by copying another container
    Myhash_multiset c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
a b c
size() = 0
a b c
size() = 0
c b a

a b c
a b c
c b a

a b c
a b c
c b a

a b c
a b c
```

## <a name="hasher"></a> hash_multiset::hasher (STL/CLR)

キーのハッシュのデリゲート。

### <a name="syntax"></a>構文

```cpp
Microsoft::VisualC::StlClr::UnaryDelegate<GKey, int>
    hasher;
```

### <a name="remarks"></a>Remarks

この型は、キーの値を整数に変換するデリゲートを表します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_hasher.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::hasher^ myhash = c1.hash_delegate();

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 1616896120
hash(L'b') = 570892832
```

## <a name="insert"></a> hash_multiset::insert (STL/CLR)

要素を追加します。

### <a name="syntax"></a>構文

```cpp
iterator insert(value_type val);
iterator insert(iterator where, value_type val);
template<typename InIter>
    void insert(InIter first, InIter last);
void insert(System::Collections::Generic::IEnumerable<value_type>^ right);
```

#### <a name="parameters"></a>パラメーター

*first*<br/>
挿入する範囲の先頭。

*last*<br/>
挿入する範囲の終了。

*right*<br/>
挿入する列挙です。

*val*<br/>
挿入するキー値。

*where*<br/>
(ヒントのみ) を挿入するコンテナー内の場所。

### <a name="remarks"></a>Remarks

各メンバー関数は、残りのオペランドで指定されたシーケンスを挿入します。

最初のメンバー関数は、値を持つ要素を挿入*val*、し、新しく挿入された要素を指定する反復子を返します。 これを使用して、1 つの要素を挿入します。

2 番目のメンバー関数は、値を持つ要素を挿入する*val*を使用して、*場所*(パフォーマンスを向上させる) をヒントとしてし、新しく挿入された要素を指定する反復子を返します。 これを使用するにはわかって要素に隣接する可能性のある 1 つの要素を挿入します。

3 番目のメンバー関数は、シーケンスを挿入します。 [`first`、 `last`)。 これを使用して、別のシーケンスからコピーした 0 個以上の要素を挿入します。

4 番目のメンバー関数で指定されたシーケンスを挿入する、*右*します。 これを使用して、列挙子によって説明されているシーケンスを挿入します。

各要素の挿入では、被制御シーケンス内の要素の数の対数に比例して時間がかかります。 挿入は発生償却定数時間でただし、カーソル位置に隣接する要素を指定するヒントを指定します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_insert.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
    System::Console::WriteLine("insert(L'x') = {0}",
        *c1.insert(L'x'));

    System::Console::WriteLine("insert(L'b') = {0}",
        *c1.insert(L'b'));

    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert a single value with hint
    System::Console::WriteLine("insert(begin(), L'y') = {0}",
        *c1.insert(c1.begin(), L'y'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an iterator range
    Myhash_multiset c2;
    Myhash_multiset::iterator it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // insert an enumeration
    Myhash_multiset c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(L'x') = x
insert(L'b') = b
a b b c x
insert(begin(), L'y') = y
a b b c x y
a b b c x
a b b c x y
```

## <a name="iterator"></a> hash_multiset::iterator (STL/CLR)

被制御シーケンスの反復子の型です。

### <a name="syntax"></a>構文

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Remarks

この型が指定されていない型のオブジェクトを表します`T1`被制御シーケンスの双方向反復子として機能することができます。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    Myhash_multiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="key_comp"></a> hash_multiset::key_comp (STL/CLR)

2 つのキーの順序付けデリゲートをコピーします。

### <a name="syntax"></a>構文

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスの並べ替えに使用される順序付けデリゲートを返します。 2 つのキーの比較に使用するとします。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_key_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_multiset c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="key_compare"></a> hash_multiset::key_compare (STL/CLR)

2 つのキーの順序付けデリゲート。

### <a name="syntax"></a>構文

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<GKey, GKey, bool>
    key_compare;
```

### <a name="remarks"></a>Remarks

型は、そのキーの引数の順序を決定するデリゲートのシノニムです。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_key_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Myhash_multiset c2 = cliext::greater<wchar_t>();
    kcomp = c2.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="key_type"></a> hash_multiset::key_type (STL/CLR)

順序付けキーの型です。

### <a name="syntax"></a>構文

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Remarks

型はテンプレート パラメーターのシノニム*キー*します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_key_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using key_type
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Myhash_multiset::key_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="load_factor"></a> hash_multiset::load_factor (STL/CLR)

バケットごとの平均要素数をカウントします。

### <a name="syntax"></a>構文

```cpp
float load_factor();
```

### <a name="remarks"></a>Remarks

メンバー関数を返します`(float)` [hash_multiset::size (STL/CLR)](../dotnet/hash-multiset-size-stl-clr.md) `() /` [hash_multiset::bucket_count (STL/CLR)](../dotnet/hash-multiset-bucket-count-stl-clr.md)`()`します。 これを使用して、バケットの平均サイズを決定します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="lower_bound"></a> hash_multiset::lower_bound (STL/CLR)

指定したキーに一致する範囲の先頭を検出します。

### <a name="syntax"></a>構文

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>パラメーター

*key*<br/>
検索対象のキー値。

### <a name="remarks"></a>Remarks

メンバー関数は、最初の要素を決定する`X`として同じバケットにハッシュを被制御シーケンス内*キー*と同等の順序あり*キー*します。 このような要素が存在しないかどうか、それを返します[hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; 指定する反復子を返します`X`します。 指定したキーと一致する、被制御シーケンス内で要素のシーケンスの先頭を現在検索を使用するとします。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_lower_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    System::Console::WriteLine("*lower_bound(L'a') = {0}",
        *c1.lower_bound(L'a'));
    System::Console::WriteLine("*lower_bound(L'b') = {0}",
        *c1.lower_bound(L'b'));
    return (0);
    }
```

```Output
a b c
lower_bound(L'x')==end() = True
*lower_bound(L'a') = a
*lower_bound(L'b') = b
```

## <a name="make_value"></a> hash_multiset::make_value (STL/CLR)

値オブジェクトを構築します。

### <a name="syntax"></a>構文

```cpp
static value_type make_value(key_type key);
```

#### <a name="parameters"></a>パラメーター

*key*<br/>
使用するキー値。

### <a name="remarks"></a>Remarks

メンバー関数を返します、`value_type`オブジェクト キーを持つ*キー*します。 その他のいくつかのメンバー関数で使用するための適切なオブジェクトの作成に使用するとします。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_make_value.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(Myhash_multiset::make_value(L'a'));
    c1.insert(Myhash_multiset::make_value(L'b'));
    c1.insert(Myhash_multiset::make_value(L'c'));

    // display contents " a b c"
    for each (Myhash_multiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="max_load_factor"></a> hash_multiset::max_load_factor (STL/CLR)

バケットあたりの最大要素数を取得または設定します。

### <a name="syntax"></a>構文

```cpp
float max_load_factor();
void max_load_factor(float new_factor);
```

#### <a name="parameters"></a>パラメーター

*new_factor*<br/>
新しい最大値を格納する要素を読み込みます。

### <a name="remarks"></a>Remarks

最初のメンバー関数は、現在格納されている最大テーブル要素を返します。 これを使用するには最大バケットの平均サイズを決定します。

2 番目のメンバー関数は、ストアの最大テーブル占有率を*new_factor*します。 自動再ハッシュは行われませんまで後続の挿入します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_max_load_factor.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="op"></a> hash_multiset::operator = (STL/CLR)

被制御シーケンスを置き換えます。

### <a name="syntax"></a>構文

```cpp
hash_multiset<Key>% operator=(hash_multiset<Key>% right);
```

#### <a name="parameters"></a>パラメーター

*right*<br/>
コピーするコンテナー。

### <a name="remarks"></a>Remarks

メンバー演算子コピー*右*、オブジェクトを返します`*this`します。 使用して、被制御シーケンス内のコピーを持つ、被制御シーケンスを置換する*右*します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_operator_as.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c"
    for each (Myhash_multiset::value_type elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // assign to a new container
    Myhash_multiset c2;
    c2 = c1;
// display contents " a b c"
    for each (Myhash_multiset::value_type elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="rbegin"></a> hash_multiset::rbegin (STL/CLR)

反転被制御シーケンスの先頭を指定します。

### <a name="syntax"></a>構文

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、または空のシーケンスの先頭を越えた、被制御シーケンスの最後の要素を指定する反転反復子を返します。 したがって、指定、`beginning`反転シーケンスの。 指定する反復子を取得するために使用、`current`被制御シーケンスの長さが変更された場合、逆の順序で見た被制御シーケンスが、そのステータスの先頭は変更できます。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_rbegin.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Myhash_multiset::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
```

## <a name="reference"></a> hash_multiset::reference (STL/CLR)

要素への参照の型です。

### <a name="syntax"></a>構文

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Remarks

この型は、要素への参照を表します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_reference.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    Myhash_multiset::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Myhash_multiset::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="rehash"></a> hash_multiset::rehash (STL/CLR)

ハッシュ テーブルをリビルドします。

### <a name="syntax"></a>構文

```cpp
void rehash();
```

### <a name="remarks"></a>Remarks

メンバー関数は、ことを確認するハッシュ テーブルを再構築[hash_multiset::load_factor (STL/CLR)](../dotnet/hash-multiset-load-factor-stl-clr.md) `() <=` [hash_multiset::max_load_factor (STL/CLR)](../dotnet/hash-multiset-max-load-factor-stl-clr.md)します。 それ以外の場合、挿入後に必要な場合にのみ、ハッシュ テーブルはサイズで増加します。 (が自動的にサイズは小さくなります。)これを使用して、ハッシュ テーブルのサイズを調整します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_rehash.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect current parameters
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // change max_load_factor and redisplay
    c1.max_load_factor(0.25f);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    System::Console::WriteLine();

    // rehash and redisplay
    c1.rehash(100);
    System::Console::WriteLine("bucket_count() = {0}", c1.bucket_count());
    System::Console::WriteLine("load_factor() = {0}", c1.load_factor());
    System::Console::WriteLine("max_load_factor() = {0}",
        c1.max_load_factor());
    return (0);
    }
```

```Output
a b c
bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 4

bucket_count() = 16
load_factor() = 0.1875
max_load_factor() = 0.25

bucket_count() = 128
load_factor() = 0.0234375
max_load_factor() = 0.25
```

## <a name="rend"></a> hash_multiset::rend (STL/CLR)

反転被制御シーケンスの末尾を指定します。

### <a name="syntax"></a>構文

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンスの先頭を越えたを指す、逆順反復子を返します。 したがって、指定、`end`反転シーケンスの。 指定する反復子を取得するために使用、`current`被制御シーケンスの長さが変更された場合、逆の順序で見た被制御シーケンスが、そのステータスの末尾は変更できます。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_rend.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // inspect first two items
    Myhash_multiset::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
```

## <a name="reverse_iterator"></a> hash_multiset::reverse_iterator (STL/CLR)

被制御シーケンスの反転反復子の型です。

### <a name="syntax"></a>構文

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Remarks

この型が指定されていない型のオブジェクトを表します`T3`被制御シーケンスの反転反復子として機能することができます。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_reverse_iterator.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" reversed
    Myhash_multiset::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="size"></a> hash_multiset::size (STL/CLR)

要素の数をカウントします。

### <a name="syntax"></a>構文

```cpp
size_type size();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスの長さを返します。 それを使用するには、被制御シーケンス内の現在の要素の数を決定します。 シーケンスを参照してください、0 以外のサイズがかどうかが関心のあるすべての場合[hash_multiset::empty (STL/CLR)](../dotnet/hash-multiset-empty-stl-clr.md)`()`します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_size.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(L'a');
    c1.insert(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 3 starting with 3
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="size_type"></a> hash_multiset::size_type (STL/CLR)

2 つの要素の間の距離を符号付きの型。

### <a name="syntax"></a>構文

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Remarks

この型は、負でない要素の数を表します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_size_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // compute positive difference
    Myhash_multiset::size_type diff = 0;
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="swap"></a> hash_multiset::swap (STL/CLR)

2 つのコンテナーのコンテンツを交換します。

### <a name="syntax"></a>構文

```cpp
void swap(hash_multiset<Key>% right);
```

#### <a name="parameters"></a>パラメーター

*right*<br/>
コンテンツを交換するコンテナー。

### <a name="remarks"></a>Remarks

メンバー関数は、交換の間で被制御シーケンス`this`と*右*します。 これは一定の時間内と、例外をスローしません。 2 つのコンテナーの内容を交換する簡単な方法として使用するとします。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_swap.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Myhash_multiset c2;
    c2.insert(L'd');
    c2.insert(L'e');
    c2.insert(L'f');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
d e f
d e f
a b c
```

## <a name="to_array"></a> hash_multiset::to_array (STL/CLR)

被制御シーケンスを新しい配列にコピーします。

### <a name="syntax"></a>構文

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンスを含む配列を返します。 配列の形式で被制御シーケンスのコピーを取得して使用するとします。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_to_array.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.insert(L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c d
a b c
```

## <a name="upper_bound"></a> hash_multiset::upper_bound (STL/CLR)

指定したキーに一致する範囲の末尾を検索します。

### <a name="syntax"></a>構文

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>パラメーター

*key*<br/>
検索対象のキー値。

### <a name="remarks"></a>Remarks

メンバー関数は、最後の要素を決定する`X`として同じバケットにハッシュを被制御シーケンス内*キー*と同等の順序あり*キー*します。 このような要素が存在しない場合、または場合`X`、被制御シーケンスの最後の要素では返します[hash_multiset::end (STL/CLR)](../dotnet/hash-multiset-end-stl-clr.md)`()`; を超える先頭の要素を指定する反復子を返します`X`. 指定したキーと一致する、被制御シーケンス内で要素のシーケンスの末尾を現在検索を使用するとします。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_upper_bound.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    System::Console::WriteLine("*upper_bound(L'a') = {0}",
        *c1.upper_bound(L'a'));
    System::Console::WriteLine("*upper_bound(L'b') = {0}",
        *c1.upper_bound(L'b'));
    return (0);
    }
```

```Output
a b c
upper_bound(L'x')==end() = True
*upper_bound(L'a') = b
*upper_bound(L'b') = c
```

## <a name="value_comp"></a> hash_multiset::value_comp (STL/CLR)

2 つの要素の値の順序付けデリゲートをコピーします。

### <a name="syntax"></a>構文

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスの並べ替えに使用される順序付けデリゲートを返します。 これを使用するには 2 つの要素の値を比較します。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_value_comp.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="value_compare"></a> hash_multiset::value_compare (STL/CLR)

2 つの要素の値の順序付けデリゲート。

### <a name="syntax"></a>構文

```cpp
Microsoft::VisualC::StlClr::BinaryDelegate<generic_value, generic_value, bool>
    value_compare;
```

### <a name="remarks"></a>Remarks

型は、その値の引数の順序を決定するデリゲートのシノニムです。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_value_compare.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    Myhash_multiset::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = True
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="value_type"></a> hash_multiset::value_type (STL/CLR)

要素の型。

### <a name="syntax"></a>構文

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Remarks

この型は `generic_value` の同意語です。

### <a name="example"></a>例

```cpp
// cliext_hash_multiset_value_type.cpp
// compile with: /clr
#include <cliext/hash_set>

typedef cliext::hash_multiset<wchar_t> Myhash_multiset;
int main()
    {
    Myhash_multiset c1;
    c1.insert(L'a');
    c1.insert(L'b');
    c1.insert(L'c');

    // display contents " a b c" using value_type
    for (Myhash_multiset::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Myhash_multiset::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```