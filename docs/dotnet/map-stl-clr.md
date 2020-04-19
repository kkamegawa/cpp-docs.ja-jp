---
title: map (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::map
- cliext::map::begin
- cliext::map::clear
- cliext::map::const_iterator
- cliext::map::const_reference
- cliext::map::const_reverse_iterator
- cliext::map::count
- cliext::map::difference_type
- cliext::map::empty
- cliext::map::end
- cliext::map::equal_range
- cliext::map::erase
- cliext::map::find
- cliext::map::generic_container
- cliext::map::generic_iterator
- cliext::map::generic_reverse_iterator
- cliext::map::generic_value
- cliext::map::insert
- cliext::map::iterator
- cliext::map::key_comp
- cliext::map::key_compare
- cliext::map::key_type
- cliext::map::lower_bound
- cliext::map::make_value
- cliext::map::map
- cliext::map::mapped_type
- cliext::map::operator=
- cliext::map::operator
- cliext::map::rbegin
- cliext::map::reference
- cliext::map::rend
- cliext::map::reverse_iterator
- cliext::map::size
- cliext::map::size_type
- cliext::map::swap
- cliext::map::to_array
- cliext::map::upper_bound
- cliext::map::value_comp
- cliext::map::value_compare
- cliext::map::value_type
- cliext::operator!= (map)
- cliext::operator< (map)
- cliext::operator<= (map)
- cliext::operator== (map)
- cliext::operator> (map)
- cliext::operator>= (map)
helpviewer_keywords:
- <map> header [STL/CLR]
- map class [STL/CLR]
- <cliext/map> header [STL/CLR]
- begin member [STL/CLR]
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
- insert member [STL/CLR]
- iterator member [STL/CLR]
- key_comp member [STL/CLR]
- key_compare member [STL/CLR]
- key_type member [STL/CLR]
- lower_bound member [STL/CLR]
- make_value member [STL/CLR]
- map member [STL/CLR]
- mapped_type member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
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
- operator!= (map) member [STL/CLR]
- operator< (map) member [STL/CLR]
- operator<= (map) member [STL/CLR]
- operator== (map) member [STL/CLR]
- operator> (map) member [STL/CLR]
- operator>= (map) member [STL/CLR]
ms.assetid: 8b0a7764-b5e4-4175-a802-82b72eb8662a
ms.openlocfilehash: 9150d603f67051df4a6f182366623935e59fe9ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393715"
---
# <a name="map-stlclr"></a>map (STL/CLR)

テンプレート クラスは、双方向のアクセス権を持つ要素の可変長シーケンスを制御するオブジェクトについて説明します。 コンテナーを使用する`map`1 つの要素を格納する各ノードの場合は、バランスの取れた (ほぼ) 順序付けられたツリーとしての要素のシーケンスを管理します。 要素は、シーケンスと使いこなせるようになりますが、マップされた値を管理するためのキーで構成されます。

下記の説明で`GValue`と同じです。

`Microsoft::VisualC::StlClr::GenericPair<GKey, GMapped>`

それぞれの文字について以下に説明します。

`GKey` 同じ*キー*しない限り、後者の場合は、ref 型である場合は `Key^`

`GMapped` 同じ*マップ済み*しない限り、後者の場合は、ref 型である場合は `Mapped^`

## <a name="syntax"></a>構文

```cpp
template<typename Key,
    typename Mapped>
    ref class map
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        System::Collections::Generic::IDictionary<Gkey, GMapped>,
        Microsoft::VisualC::StlClr::ITree<Gkey, GValue>
    { ..... };
```

### <a name="parameters"></a>パラメーター

*Key*<br/>
被制御シーケンス内の要素の主要なコンポーネントの型。

*マップ*<br/>
被制御シーケンス内の要素の追加のコンポーネントの型。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<cliext マップ/>

**Namespace:** cliext

## <a name="declarations"></a>宣言

|型定義|説明|
|---------------------|-----------------|
|[map::const_iterator (STL/CLR)](#const_iterator)|被制御シーケンスの定数反復子の型です。|
|[map::const_reference (STL/CLR)](#const_reference)|要素への定数参照の型です。|
|[map::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|被制御シーケンスの定数反転反復子の型です。|
|[map::difference_type (STL/CLR)](#difference_type)|2 つの要素間の距離を (場合によっては符号付き) の型。|
|[map::generic_container (STL/CLR)](#generic_container)|コンテナーのジェネリック インターフェイスの型。|
|[map::generic_iterator (STL/CLR)](#generic_iterator)|コンテナーのジェネリック インターフェイスの反復子の型。|
|[map::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|コンテナーのジェネリック インターフェイスの反転反復子の型。|
|[map::generic_value (STL/CLR)](#generic_value)|コンテナーのジェネリック インターフェイスの要素の型。|
|[map::iterator (STL/CLR)](#iterator)|被制御シーケンスの反復子の型です。|
|[map::key_compare (STL/CLR)](#key_compare)|2 つのキーの順序付けデリゲート。|
|[map::key_type (STL/CLR)](#key_type)|順序付けキーの型です。|
|[map::mapped_type (STL/CLR)](#mapped_type)|各キーに関連付けられたマップされた値の型。|
|[map::reference (STL/CLR)](#reference)|要素への参照の型です。|
|[map::reverse_iterator (STL/CLR)](#reverse_iterator)|被制御シーケンスの反転反復子の型です。|
|[map::size_type (STL/CLR)](#size_type)|(負ではない) 距離は 2 つの要素の型。|
|[map::value_compare (STL/CLR)](#value_compare)|2 つの要素の値の順序付けデリゲート。|
|[map::value_type (STL/CLR)](#value_type)|要素の型。|

|メンバー関数|説明|
|---------------------|-----------------|
|[map::begin (STL/CLR)](#begin)|被制御シーケンスの先頭を指定します。|
|[map::clear (STL/CLR)](#clear)|すべての要素を削除します。|
|[map::count (STL/CLR)](#count)|指定したキーに一致する要素をカウントします。|
|[map::empty (STL/CLR)](#empty)|要素が存在しないかどうかをテストします。|
|[map::end (STL/CLR)](#end)|被制御シーケンスの末尾を指定します。|
|[map::equal_range (STL/CLR)](#equal_range)|指定したキーに一致する範囲を検索します。|
|[map::erase (STL/CLR)](#erase)|指定した位置にある要素を削除します。|
|[map::find (STL/CLR)](#find)|指定したキーに一致する要素を検索します。|
|[map::insert (STL/CLR)](#insert)|要素を追加します。|
|[map::key_comp (STL/CLR)](#key_comp)|2 つのキーの順序付けデリゲートをコピーします。|
|[map::lower_bound (STL/CLR)](#lower_bound)|指定したキーに一致する範囲の先頭を検出します。|
|[map::make_value (STL/CLR)](#make_value)|値オブジェクトを構築します。|
|[map::map (STL/CLR)](#map)|コンテナー オブジェクトを構築します。|
|[map::rbegin (STL/CLR)](#rbegin)|反転被制御シーケンスの先頭を指定します。|
|[map::rend (STL/CLR)](#rend)|反転被制御シーケンスの末尾を指定します。|
|[map::size (STL/CLR)](#size)|要素の数をカウントします。|
|[map::swap (STL/CLR)](#swap)|2 つのコンテナーのコンテンツを交換します。|
|[map::to_array (STL/CLR)](#to_array)|被制御シーケンスを新しい配列にコピーします。|
|[map::upper_bound (STL/CLR)](#upper_bound)|指定したキーに一致する範囲の末尾を検索します。|
|[map::value_comp (STL/CLR)](#value_comp)|2 つの要素の値の順序付けデリゲートをコピーします。|

|演算子|説明|
|--------------|-----------------|
|[map::operator= (STL/CLR)](#op_as)|被制御シーケンスを置き換えます。|
|[map::operator(STL/CLR)](#op)|関連するマップされた値をキーにマップします。|
|[operator!= (map) (STL/CLR)](#op_neq)|かどうかを`map`オブジェクトが等しく別`map`オブジェクト。|
|[operator< (map) (STL/CLR)](#op_lt)|かどうかを`map`オブジェクトが他よりも小さい`map`オブジェクト。|
|[operator<= (map) (STL/CLR)](#op_lteq)|かどうかを`map`オブジェクトが別に小さい`map`オブジェクト。|
|[operator== (map) (STL/CLR)](#op_eq)|かどうかを`map`オブジェクトが相互に等しい`map`オブジェクト。|
|[operator> (map) (STL/CLR)](#op_gt)|かどうかを`map`オブジェクトが他よりも大きい`map`オブジェクト。|
|[operator>= (map) (STL/CLR)](#op_gteq)|かどうかを`map`オブジェクトより大きいまたは相互に等しい`map`オブジェクト。|

## <a name="interfaces"></a>インターフェイス

|Interface|説明|
|---------------|-----------------|
|<xref:System.ICloneable>|オブジェクトが重複しています。|
|<xref:System.Collections.IEnumerable>|要素をシーケンス処理します。|
|<xref:System.Collections.ICollection>|要素のグループを管理します。|
|<xref:System.Collections.Generic.IEnumerable%601>|型指定された要素をシーケンス処理します。|
|<xref:System.Collections.Generic.ICollection%601>|型指定された要素のグループを管理します。|
|<xref:System.Collections.Generic.IDictionary%602>|{0} キー、値} のグループの管理のペア。|
|ITree < Key, 値 >|ジェネリックなコンテナーを管理します。|

## <a name="remarks"></a>Remarks

オブジェクトは、割り当て、個々 のノードとして、制御するシーケンスの記憶域を解放します。 別の 1 つのノードの内容のコピーからではなく、ノード間のリンクを変更することで順序付けられた保持する (ほぼ) バランスの取れたツリーに要素を挿入します。 つまり、挿入し、残りの要素を中断することがなく自由に要素を削除することができます。

オブジェクトがストアド デリゲート型のオブジェクトを呼び出すことによって、制御するシーケンスを並べ替えます[map::key_compare (STL/CLR)](../dotnet/map-key-compare-stl-clr.md)します。 マップを構築する際に、ストアド デリゲート オブジェクトを指定できます。既定値は、比較でデリゲート オブジェクトを指定しない場合`operator<(key_type, key_type)`します。 メンバー関数を呼び出すことによって格納されているこのオブジェクトにアクセスする[map::key_comp (STL/CLR)](../dotnet/map-key-comp-stl-clr.md)`()`します。

このようなデリゲート オブジェクトは、厳密弱順序の種類のキーを課す必要があります[map::key_type (STL/CLR)](../dotnet/map-key-type-stl-clr.md)します。 任意の 2 つのキーのつまり`X`と`Y`:

`key_comp()(X, Y)` 呼び出しごとに、同じブール型の結果を返します。

場合`key_comp()(X, Y)`が true の場合、 `key_comp()(Y, X)` false である必要があります。

場合`key_comp()(X, Y)`が true の場合、`X`前に順序付けすると言います`Y`します。

場合`!key_comp()(X, Y) && !key_comp()(Y, X)`が true の場合、`X`と`Y`同等の順序を持つと言います。

任意の要素に対して`X`前になる`Y`で、被制御シーケンスの`key_comp()(Y, X)`は false です。 (既定のデリゲート オブジェクトのキーしない値が減少します。)テンプレート クラスとは異なり[マップ](../dotnet/map-stl-clr.md)、テンプレート クラスのオブジェクト`map`はすべての要素のキーが一意である必要ありません。 (2 つ以上のキーと同じ順序付けします。)

各要素には、個別のキーと、マップされた値が含まれています。 シーケンスは、シーケンス (対数時間) 内の参照、挿入、および要素の数の対数に比例して操作の数が、任意の要素の削除を許可するように表されます。 要素を挿入しても反復子の有効性は失われません。また、要素を削除した場合は、削除された要素を指す反復子だけが無効化されます。

マップは、隣接する要素を被制御シーケンス内の要素を指定する反復子を指定する手順は、双方向反復子をサポートします。 特別なヘッド ノードによって返される反復子に対応[map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`します。 存在する場合は、被制御シーケンスの最後の要素に到達するこの反復子をデクリメントできます。 ヘッド ノードに到達するマップの反復子をインクリメントして等しく比較がし`end()`します。 によって返される反復子を逆参照することはできませんが、`end()`します。

その位置を表す数値を直接指定されたマップ要素を参照することはできないことに注意してください。--ランダム アクセス反復子が必要です。

マップの反復子は、それに関連付けられているコンテナーを識別するハンドルを格納するマップが関連付けられているノードを識別するハンドルを格納します。 関連付けられているコンテナー オブジェクトでのみ、反復子を使用することができます。 マップの反復子は、関連付けられているマップ ノードがいくつかのマップに関連付けられている限り有効です。 さらに、有効な反復子は dereferencable--へのアクセスまたは--指定する要素の値を変更すると等しくない限り、使用する`end()`します。

消去、または要素を削除する、格納されている値のデストラクターを呼び出します。 コンテナーを破棄するには、すべての要素が消去されます。 したがって、要素型を持つ ref クラスは、コンテナーによりする要素よりも長く保持しないコンテナーです。 ただし、ハンドルのコンテナーは*いない*その要素を破棄します。

## <a name="members"></a>メンバー

## <a name="begin"></a> map::begin (STL/CLR)

被制御シーケンスの先頭を指定します。

### <a name="syntax"></a>構文

```cpp
iterator begin();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンス、または空のシーケンスの末尾を越えた最初の要素を指定する双方向反復子を返します。 指定する反復子を取得するために使用、`current`被制御シーケンスの長さが変更された場合、被制御シーケンスが、そのステータスの先頭を変更できます。

### <a name="example"></a>例

```cpp
// cliext_map_begin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items
    Mymap::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*++begin() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*begin() = [a 1]
*++begin() = [b 2]
```

## <a name="clear"></a> map::clear (STL/CLR)

すべての要素を削除します。

### <a name="syntax"></a>構文

```cpp
void clear();
```

### <a name="remarks"></a>Remarks

メンバー関数は、効果的に呼び出す[map::erase (STL/CLR)](../dotnet/map-erase-stl-clr.md) `(` [map::begin (STL/CLR)](../dotnet/map-begin-stl-clr.md) `(),` [map::end (STL/CLR)](../dotnet/map-end-stl-clr.md) `())`. これを使用するには、被制御シーケンスが空であることを確認します。

### <a name="example"></a>例

```cpp
// cliext_map_clear.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));

    // display contents " [a 1] [b 2]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0
[a 1] [b 2]
size() = 0
```

## <a name="const_iterator"></a> map::const_iterator (STL/CLR)

被制御シーケンスの定数反復子の型です。

### <a name="syntax"></a>構文

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Remarks

この型が指定されていない型のオブジェクトを表します`T2`被制御シーケンスの定数双方向反復子として機能することができます。

### <a name="example"></a>例

```cpp
// cliext_map_const_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("[{0} {1}] ", cit->first, cit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="const_reference"></a> map::const_reference (STL/CLR)

要素への定数参照の型です。

### <a name="syntax"></a>構文

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Remarks

この型は、要素への定数参照を表します。

### <a name="example"></a>例

```cpp
// cliext_map_const_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        Mymap::const_reference cref = *cit;
        System::Console::Write("[{0} {1}] ", cref->first, cref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="const_reverse_iterator"></a> map::const_reverse_iterator (STL/CLR)

被制御シーケンスの定数反転反復子の種類.

### <a name="syntax"></a>構文

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Remarks

この型が指定されていない型のオブジェクトを表します`T4`被制御シーケンスの定数反転反復子として機能することができます。

### <a name="example"></a>例

```cpp
// cliext_map_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymap::const_reverse_iterator crit = c1.rbegin();
    for (; crit != c1.rend(); ++crit)
        System::Console::Write("[{0} {1}] ", crit->first, crit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="count"></a> map::count (STL/CLR)

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
// cliext_map_count.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("count(L'A') = {0}", c1.count(L'A'));
    System::Console::WriteLine("count(L'b') = {0}", c1.count(L'b'));
    System::Console::WriteLine("count(L'C') = {0}", c1.count(L'C'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
count(L'A') = 0
count(L'b') = 1
count(L'C') = 0
```

## <a name="difference_type"></a> map::difference_type (STL/CLR)

2 つの要素間の距離を符号付きの型。

### <a name="syntax"></a>構文

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Remarks

この型は、場合によって負の値の要素の数を表します。

### <a name="example"></a>例

```cpp
// cliext_map_difference_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymap::difference_type diff = 0;
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

    // compute negative difference
    diff = 0;
    for (Mymap::iterator it = c1.end(); it != c1.begin(); --it)
        --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
begin()-end() = -3
```

## <a name="empty"></a> map::empty (STL/CLR)

要素が存在しないかどうかをテストします。

### <a name="syntax"></a>構文

```cpp
bool empty();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスが空の場合に true を返します。 同じになります[map::size (STL/CLR)](../dotnet/map-size-stl-clr.md)`() == 0`します。 これを使用するには、map が空かどうかをテストします。

### <a name="example"></a>例

```cpp
// cliext_map_empty.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
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
[a 1] [b 2] [c 3]
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="end"></a> map::end (STL/CLR)

被制御シーケンスの末尾を指定します。

### <a name="syntax"></a>構文

```cpp
iterator end();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンスの最後の位置を指し示す双方向反復子を返します。 被制御シーケンスの末尾を指定する反復子を取得するのにために使用します。そのステータスは被制御シーケンスの長さが変更された場合は変更されません。

### <a name="example"></a>例

```cpp
// cliext_map_end.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect last two items
    Mymap::iterator it = c1.end();
    --it;
    --it;
    System::Console::WriteLine("*-- --end() = [{0} {1}]",
        it->first, it->second);
    ++it;
    System::Console::WriteLine("*--end() = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

## <a name="equal_range"></a> map::equal_range (STL/CLR)

指定したキーに一致する範囲を検索します。

### <a name="syntax"></a>構文

```cpp
cliext::pair<iterator, iterator> equal_range(key_type key);
```

#### <a name="parameters"></a>パラメーター

*key*<br/>
検索対象のキー値。

### <a name="remarks"></a>Remarks

メンバー関数は、反復子のペアを返します。 `cliext::pair<iterator, iterator>(` [map::lower_bound (STL/CLR)](../dotnet/map-lower-bound-stl-clr.md) `(key),` [map::upper_bound (STL/CLR)](../dotnet/map-upper-bound-stl-clr.md)`(key))`します。 指定したキーに一致する要素を被制御シーケンスの現在の範囲を決定するのに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_map_equal_range.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef Mymap::pair_iter_iter Pairii;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display results of failed search
    Pairii pair1 = c1.equal_range(L'x');
    System::Console::WriteLine("equal_range(L'x') empty = {0}",
        pair1.first == pair1.second);

    // display results of successful search
    pair1 = c1.equal_range(L'b');
    for (; pair1.first != pair1.second; ++pair1.first)
        System::Console::Write("[{0} {1}] ",
            pair1.first->first, pair1.first->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
equal_range(L'x') empty = True
[b 2]
```

## <a name="erase"></a> map::erase (STL/CLR)

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

最初のメンバー関数が指す被制御シーケンスの要素を削除する*場所*、および削除するには、要素の後に残る最初の要素を指定する反復子を返しますまたは[map::end (STL/CLR)](../dotnet/map-end-stl-clr.md) `()`そのような要素が存在しない場合。 これを使用するには 1 つの要素を削除します。

2 番目のメンバー関数は、範囲の被制御シーケンスの要素を削除する [`first`、 `last`)、し、削除された要素の後に残る最初の要素を指定する反復子を返しますまたは`end()`場合、このような要素がないです。存在する. これを使用するには 0 個以上の連続する要素を削除します。

3 番目のメンバー関数は、キーを持つと同じ順序付けの被制御シーケンスの任意の要素を削除します。 を*キー*、削除された要素の数のカウントを返します。 削除や、指定したキーと一致するすべての要素のカウントを使用するとします。

各要素のデータ消去では、被制御シーケンス内の要素の数の対数に比例して時間がかかります。

### <a name="example"></a>例

```cpp
// cliext_map_erase.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    cliext::map<wchar_t, int> c1;
    c1.insert(cliext::map<wchar_t, int>::make_value(L'a', 1));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'b', 2));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (cliext::map<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase an element and reinspect
    cliext::map<wchar_t, int>::iterator it =
        c1.erase(c1.begin());
    System::Console::WriteLine("erase(begin()) = [{0} {1}]",
        it->first, it->second);

    // add elements and display " b c d e"
    c1.insert(cliext::map<wchar_t, int>::make_value(L'd', 4));
    c1.insert(cliext::map<wchar_t, int>::make_value(L'e', 5));
    for each (cliext::map<wchar_t, int>::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // erase all but end
    it = c1.end();
    it = c1.erase(c1.begin(), --it);
    System::Console::WriteLine("erase(begin(), end()-1) = [{0} {1}]",
        it->first, it->second);
    System::Console::WriteLine("size() = {0}", c1.size());

    // erase end
    System::Console::WriteLine("erase(L'x') = {0}", c1.erase(L'x'));
    System::Console::WriteLine("erase(L'e') = {0}", c1.erase(L'e'));
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
erase(begin()) = [b 2]
[b 2] [c 3] [d 4] [e 5]
erase(begin(), end()-1) = [e 5]
size() = 1
erase(L'x') = 0
erase(L'e') = 1
```

## <a name="find"></a> map::find (STL/CLR)

指定したキーに一致する要素を検索します。

### <a name="syntax"></a>構文

```cpp
iterator find(key_type key);
```

#### <a name="parameters"></a>パラメーター

*key*<br/>
検索対象のキー値。

### <a name="remarks"></a>Remarks

被制御シーケンス内の少なくとも 1 つの要素があるのと同じ順序付け場合*キー*、メンバー関数は、それらの要素のいずれかを指定する反復子を返しますそれ以外の場合を返します[map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`。 指定したキーに一致する制御シーケンス内の要素を検索に使用します。

### <a name="example"></a>例

```cpp
// cliext_map_find.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("find {0} = {1}",
        L'A', c1.find(L'A') != c1.end());

    Mymap::iterator it = c1.find(L'b');
    System::Console::WriteLine("find {0} = [{1} {2}]",
        L'b', it->first, it->second);

    System::Console::WriteLine("find {0} = {1}",
        L'C', c1.find(L'C') != c1.end());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
find A = False
find b = [b 2]
find C = False
```

## <a name="generic_container"></a> map::generic_container (STL/CLR)

コンテナーのジェネリック インターフェイスの型。

### <a name="syntax"></a>構文

```cpp
typedef Microsoft::VisualC::StlClr::
    ITree<GKey, GValue>
    generic_container;
```

### <a name="remarks"></a>Remarks

この型は、このテンプレートのコンテナー クラスのジェネリック インターフェイスを表します。

### <a name="example"></a>例

```cpp
// cliext_map_generic_container.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify generic and display original
    gc1->insert(Mymap::make_value(L'd', 4));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // modify original and display generic
    c1.insert(Mymap::make_value(L'e', 5));
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3] [d 4] [e 5]
```

## <a name="generic_iterator"></a> map::generic_iterator (STL/CLR)

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
// cliext_map_generic_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_iterator gcit = gc1->begin();
    Mymap::generic_value gcval = *gcit;
    System::Console::Write("[{0} {1}] ", gcval->first, gcval->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="generic_reverse_iterator"></a> map::generic_reverse_iterator (STL/CLR)

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
// cliext_map_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_reverse_iterator gcit = gc1->rbegin();
    Mymap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[c 3]
```

## <a name="generic_value"></a> map::generic_value (STL/CLR)

コンテナーのジェネリック インターフェイスを使用するための要素の型。

### <a name="syntax"></a>構文

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Remarks

この型は、型のオブジェクトを表します。`GValue`ストアド要素の値をこのテンプレートのコンテナー クラスのジェネリック インターフェイスを使用するについて説明します。

### <a name="example"></a>例

```cpp
// cliext_map_generic_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct a generic container
    Mymap::generic_container^ gc1 = %c1;
    for each (Mymap::value_type elem in gc1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // get an element and display it
    Mymap::generic_iterator gcit = gc1->begin();
    Mymap::generic_value gcval = *gcit;
    System::Console::WriteLine("[{0} {1}] ", gcval->first, gcval->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
[a 1]
```

## <a name="insert"></a> map::insert (STL/CLR)

要素を追加します。

### <a name="syntax"></a>構文

```cpp
cliext::pair<iterator, bool> insert(value_type val);
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

最初のメンバー関数が値を持つ要素を挿入しようと*val*、値のペアを返しますと`X`します。 場合`X.second`が true の場合`X.first`新しく挿入される要素を指定します。 それ以外の`X.first`と同等の要素を指定既に順序付けが存在し、新しい要素は挿入されません。 これを使用して、1 つの要素を挿入します。

2 番目のメンバー関数は、値を持つ要素を挿入する*val*を使用して、*場所*(パフォーマンスを向上させる) をヒントとしてし、新しく挿入された要素を指定する反復子を返します。 これを使用するにはわかって要素に隣接する可能性のある 1 つの要素を挿入します。

3 番目のメンバー関数は、シーケンスを挿入します。 [`first`、 `last`)。 これを使用して、別のシーケンスからコピーした 0 個以上の要素を挿入します。

4 番目のメンバー関数で指定されたシーケンスを挿入する、*右*します。 これを使用して、列挙子によって説明されているシーケンスを挿入します。

各要素の挿入では、被制御シーケンス内の要素の数の対数に比例して時間がかかります。 挿入は発生償却定数時間でただし、カーソル位置に隣接する要素を指定するヒントを指定します。

### <a name="example"></a>例

```cpp
// cliext_map_insert.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
typedef Mymap::pair_iter_bool Pairib;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value, unique and duplicate
// insert a single value, success and failure
    Pairib pair1 = c1.insert(Mymap::make_value(L'x', 24));
    System::Console::WriteLine("insert([L'x' 24]) = [[{0} {1}] {2}]",
        pair1.first->first, pair1.first->second, pair1.second);

    pair1 = c1.insert(Mymap::make_value(L'b', 2));
    System::Console::WriteLine("insert([L'b' 2]) = [[{0} {1}] {2}]",
        pair1.first->first, pair1.first->second, pair1.second);

    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert a single value with hint
    Mymap::iterator it =
        c1.insert(c1.begin(), Mymap::make_value(L'y', 25));
    System::Console::WriteLine("insert(begin(), [L'y' 25]) = [{0} {1}]",
        it->first, it->second);
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an iterator range
    Mymap c2;
    it = c1.end();
    c2.insert(c1.begin(), --it);
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // insert an enumeration
    Mymap c3;
    c3.insert(   // NOTE: cast is not needed
        (System::Collections::Generic::
            IEnumerable<Mymap::value_type>^)%c1);
    for each (Mymap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
insert([L'x' 24]) = [[x 24] True]
insert([L'b' 2]) = [[b 2] False]
[a 1] [b 2] [c 3] [x 24]
insert(begin(), [L'y' 25]) = [y 25]
[a 1] [b 2] [c 3] [x 24] [y 25]
[a 1] [b 2] [c 3] [x 24]
[a 1] [b 2] [c 3] [x 24] [y 25]
```

## <a name="iterator"></a> map::iterator (STL/CLR)

被制御シーケンスの反復子の型です。

### <a name="syntax"></a>構文

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Remarks

この型が指定されていない型のオブジェクトを表します`T1`被制御シーケンスの双方向反復子として機能することができます。

### <a name="example"></a>例

```cpp
// cliext_map_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("[{0} {1}] ", it->first, it->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="key_comp"></a> map::key_comp (STL/CLR)

2 つのキーの順序付けデリゲートをコピーします。

### <a name="syntax"></a>構文

```cpp
key_compare^key_comp();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスの並べ替えに使用される順序付けデリゲートを返します。 2 つのキーの比較に使用するとします。

### <a name="example"></a>例

```cpp
// cliext_map_key_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymap c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="key_compare"></a> map::key_compare (STL/CLR)

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
// cliext_map_key_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::key_compare^ kcomp = c1.key_comp();

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();

    // test a different ordering rule
    Mymap c2 = cliext::greater<wchar_t>();
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
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False

compare(L'a', L'a') = False
compare(L'a', L'b') = False
compare(L'b', L'a') = True
```

## <a name="key_type"></a> map::key_type (STL/CLR)

順序付けキーの型です。

### <a name="syntax"></a>構文

```cpp
typedef Key key_type;
```

### <a name="remarks"></a>Remarks

型はテンプレート パラメーターのシノニム*キー*します。

### <a name="example"></a>例

```cpp
// cliext_map_key_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using key_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in key_type object
        Mymap::key_type val = it->first;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="lower_bound"></a> map::lower_bound (STL/CLR)

指定したキーに一致する範囲の先頭を検出します。

### <a name="syntax"></a>構文

```cpp
iterator lower_bound(key_type key);
```

#### <a name="parameters"></a>パラメーター

*key*<br/>
検索対象のキー値。

### <a name="remarks"></a>Remarks

メンバー関数は、最初の要素を決定する`X`と同等の順序を持つ被制御シーケンス内*キー*します。 このような要素が存在しないかどうか、それを返します[map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`; 指定する反復子を返します`X`します。 指定したキーと一致する、被制御シーケンス内で要素のシーケンスの先頭を現在検索を使用するとします。

### <a name="example"></a>例

```cpp
// cliext_map_lower_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("lower_bound(L'x')==end() = {0}",
        c1.lower_bound(L'x') == c1.end());

    Mymap::iterator it = c1.lower_bound(L'a');
    System::Console::WriteLine("*lower_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.lower_bound(L'b');
    System::Console::WriteLine("*lower_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
lower_bound(L'x')==end() = True
*lower_bound(L'a') = [a 1]
*lower_bound(L'b') = [b 2]
```

## <a name="make_value"></a> map::make_value (STL/CLR)

値オブジェクトを構築します。

### <a name="syntax"></a>構文

```cpp
static value_type make_value(key_type key, mapped_type mapped);
```

#### <a name="parameters"></a>パラメーター

*key*<br/>
使用するキー値。

*mapped*<br/>
検索する値をマップします。

### <a name="remarks"></a>Remarks

メンバー関数を返します、`value_type`オブジェクト キーを持つ*キー*し、マップされた値が*マップ*します。 その他のいくつかのメンバー関数で使用するための適切なオブジェクトの作成に使用するとします。

### <a name="example"></a>例

```cpp
// cliext_map_make_value.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="map"></a> map::map (STL/CLR)

コンテナー オブジェクトを構築します。

### <a name="syntax"></a>構文

```cpp
map();
explicit map(key_compare^ pred);
map(map<Key, Mapped>% right);
map(map<Key, Mapped>^ right);
template<typename InIter>
    mapmap(InIter first, InIter last);
template<typename InIter>
    map(InIter first, InIter last,
        key_compare^ pred);
map(System::Collections::Generic::IEnumerable<GValue>^ right);
map(System::Collections::Generic::IEnumerable<GValue>^ right,
    key_compare^ pred);
```

#### <a name="parameters"></a>パラメーター

*first*<br/>
挿入する範囲の先頭。

*last*<br/>
挿入する範囲の終了。

*Pred*<br/>
被制御シーケンスの述語を順序付けします。

*right*<br/>
挿入するオブジェクトまたは範囲。

### <a name="remarks"></a>Remarks

コンス トラクター。

`map();`

既定の順序の述語を使用して要素のない、被制御シーケンスを初期化`key_compare()`します。 これを使用するには、既定の順序の述語を持つ、空の初期被制御シーケンスを指定します。

コンス トラクター。

`explicit map(key_compare^ pred);`

順序付け述語で、要素のない、被制御シーケンスを初期化します*pred*します。 指定した順序付け述語を持つ、空の初期被制御シーケンスを指定するのに使用するとします。

コンス トラクター。

`map(map<Key, Mapped>% right);`

シーケンスが被制御シーケンスを初期化します [`right.begin()`、 `right.end()`)、既定の順序の述語とします。 マップ オブジェクトによって制御されるシーケンスのコピーである初期被制御シーケンスを指定するために使用*右*既定の順序の述語とします。

コンス トラクター。

`map(map<Key, Mapped>^ right);`

シーケンスが被制御シーケンスを初期化します [`right->begin()`、 `right->end()`)、既定の順序の述語とします。 マップ オブジェクトによって制御されるシーケンスのコピーである初期被制御シーケンスを指定するために使用*右*既定の順序の述語とします。

コンス トラクター。

`template<typename InIter> map(InIter first, InIter last);`

シーケンスが被制御シーケンスを初期化します [`first`、 `last`)、既定の順序の述語とします。 それを使用するには、述語を順序付け、既定値は、被制御シーケンスの別のシーケンスをコピーを作成します。

コンス トラクター。

`template<typename InIter> map(InIter first, InIter last, key_compare^ pred);`

シーケンスが被制御シーケンスを初期化します [`first`、 `last`)、順序付け述語で*pred*します。 これを使用するには、被制御シーケンスの順序付け述語の指定したもう 1 つのシーケンスのコピーを作成します。

コンス トラクター。

`map(System::Collections::Generic::IEnumerable<Key>^ right);`

列挙子によって指定されたシーケンスの被制御シーケンスを初期化します*右*既定の順序の述語とします。 これを使用するには、被制御シーケンスの既定の順序の述語で、列挙子によって説明されているもう 1 つのシーケンスのコピーを作成します。

コンス トラクター。

`map(System::Collections::Generic::IEnumerable<Key>^ right, key_compare^ pred);`

列挙子によって指定されたシーケンスの被制御シーケンスを初期化します*右*、順序付け述語で*pred*します。 これを使用するには、被制御シーケンスの順序付け述語の指定の列挙子によって説明されているもう 1 つのシーケンスのコピーを作成します。

### <a name="example"></a>例

```cpp
// cliext_map_construct.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
// construct an empty container
    Mymap c1;
    System::Console::WriteLine("size() = {0}", c1.size());

    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an ordering rule
    Mymap c2 = cliext::greater_equal<wchar_t>();
    System::Console::WriteLine("size() = {0}", c2.size());

    c2.insert(c1.begin(), c1.end());
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range
    Mymap c3(c1.begin(), c1.end());
    for each (Mymap::value_type elem in c3)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an iterator range and an ordering rule
    Mymap c4(c1.begin(), c1.end(),
        cliext::greater_equal<wchar_t>());
    for each (Mymap::value_type elem in c4)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration
    Mymap c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymap::value_type>^)%c3);
    for each (Mymap::value_type elem in c5)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct with an enumeration and an ordering rule
    Mymap c6(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<
            Mymap::value_type>^)%c3,
                cliext::greater_equal<wchar_t>());
    for each (Mymap::value_type elem in c6)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying another container
    Mymap c7(c4);
    for each (Mymap::value_type elem in c7)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct by copying a container handle
    Mymap c8(%c3);
    for each (Mymap::value_type elem in c8)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
[a 1] [b 2] [c 3]
size() = 0
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
[c 3] [b 2] [a 1]
[c 3] [b 2] [a 1]
[a 1] [b 2] [c 3]
```

## <a name="mapped_type"></a> map::mapped_type (STL/CLR)

各キーに関連付けられた、マップされた値の型です。

### <a name="syntax"></a>構文

```cpp
typedef Mapped mapped_type;
```

### <a name="remarks"></a>Remarks

型はテンプレート パラメーターのシノニム*マップ済み*します。

### <a name="example"></a>例

```cpp
// cliext_map_mapped_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using mapped_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in mapped_type object
        Mymap::mapped_type val = it->second;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
1 2 3
```

## <a name="op_as"></a> map: = (STL/CLR)

被制御シーケンスを置き換えます。

### <a name="syntax"></a>構文

```cpp
map<Key, Mapped>% operator=(map<Key, Mapped>% right);
```

#### <a name="parameters"></a>パラメーター

*right*<br/>
コピーするコンテナー。

### <a name="remarks"></a>Remarks

メンバー演算子コピー*右*、オブジェクトを返します`*this`します。 使用して、被制御シーケンス内のコピーを持つ、被制御シーケンスを置換する*右*します。

### <a name="example"></a>例

```cpp
// cliext_map_operator_as.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2 = c1;
    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [c 3]
```

## <a name="op"></a> map::operator(STL/CLR)

関連するマップされた値をキーにマップします。

### <a name="syntax"></a>構文

```cpp
mapped_type operator[](key_type key);
```

#### <a name="parameters"></a>パラメーター

*key*<br/>
検索対象のキー値。

### <a name="remarks"></a>Remarks

メンバー関数と同等の順序を持つ要素を検索する試み*キー*します。 関連するマップされた値が返されます 1 つが見つかると、それ以外の場合、挿入`value_type(key, mapped_type())`し、関連付けられているを返します (既定値) の値をマップします。 これを使用して関連付けられたキーを指定されたマップされた値を検索する、または何も見つからない場合は、キーのエントリが存在することを確認します。

### <a name="example"></a>例

```cpp
// cliext_map_operator_sub.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("c1[{0}] = {1}",
        L'A', c1[L'A']);
    System::Console::WriteLine("c1[{0}] = {1}",
        L'b', c1[L'b']);

    // redisplay altered contents
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // alter mapped values and redisplay
    c1[L'A'] = 10;
    c1[L'c'] = 13;
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
c1[A] = 0
c1[b] = 2
[A 0] [a 1] [b 2] [c 3]
[A 10] [a 1] [b 2] [c 13]
```

## <a name="rbegin"></a> map::rbegin (STL/CLR)

反転被制御シーケンスの先頭を指定します。

### <a name="syntax"></a>構文

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、または空のシーケンスの先頭を越えた、被制御シーケンスの最後の要素を指定する反転反復子を返します。 したがって、指定、`beginning`反転シーケンスの。 指定する反復子を取得するために使用、`current`被制御シーケンスの長さが変更された場合、逆の順序で見た被制御シーケンスが、そのステータスの先頭は変更できます。

### <a name="example"></a>例

```cpp
// cliext_map_rbegin.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymap::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*++rbegin() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*rbegin() = [c 3]
*++rbegin() = [b 2]
```

## <a name="reference"></a> map::reference (STL/CLR)

要素への参照の型です。

### <a name="syntax"></a>構文

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Remarks

この型は、要素への参照を表します。

### <a name="example"></a>例

```cpp
// cliext_map_reference.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    Mymap::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        Mymap::reference ref = *it;
        System::Console::Write("[{0} {1}] ", ref->first, ref->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="rend"></a> map::rend (STL/CLR)

反転被制御シーケンスの末尾を指定します。

### <a name="syntax"></a>構文

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンスの先頭を越えたを指す、逆順反復子を返します。 したがって、指定、`end`反転シーケンスの。 指定する反復子を取得するために使用、`current`被制御シーケンスの長さが変更された場合、逆の順序で見た被制御シーケンスが、そのステータスの末尾は変更できます。

### <a name="example"></a>例

```cpp
// cliext_map_rend.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // inspect first two items in reversed sequence
    Mymap::reverse_iterator rit = c1.rend();
    --rit;
    --rit;
    System::Console::WriteLine("*-- --rend() = [{0} {1}]",
        rit->first, rit->second);
    ++rit;
    System::Console::WriteLine("*--rend() = [{0} {1}]",
        rit->first, rit->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
*-- --rend() = [b 2]
*--rend() = [a 1]
```

## <a name="reverse_iterator"></a> map::reverse_iterator (STL/CLR)

被制御シーケンスの反転反復子の型です。

### <a name="syntax"></a>構文

```
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Remarks

この型が指定されていない型のオブジェクトを表します`T3`被制御シーケンスの反転反復子として機能することができます。

### <a name="example"></a>例

```cpp
// cliext_map_reverse_iterator.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" reversed
    Mymap::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("[{0} {1}] ", rit->first, rit->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[c 3] [b 2] [a 1]
```

## <a name="size"></a> map::size (STL/CLR)

要素の数をカウントします。

### <a name="syntax"></a>構文

```cpp
size_type size();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスの長さを返します。 それを使用するには、被制御シーケンス内の現在の要素の数を決定します。 シーケンスを参照してください、0 以外のサイズがかどうかが関心のあるすべての場合[map::empty (STL/CLR)](../dotnet/map-empty-stl-clr.md)`()`します。

### <a name="example"></a>例

```cpp
// cliext_map_size.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

    // add elements and clear again
    c1.insert(Mymap::make_value(L'd', 4));
    c1.insert(Mymap::make_value(L'e', 5));
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
size() = 0 after clearing
size() = 2 after adding 2
```

## <a name="size_type"></a> map::size_type (STL/CLR)

2 つの要素の間の距離を符号付きの型。

### <a name="syntax"></a>構文

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Remarks

この型は、負でない要素の数を表します。

### <a name="example"></a>例

```cpp
// cliext_map_size_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // compute positive difference
    Mymap::size_type diff = 0;
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
end()-begin() = 3
```

## <a name="swap"></a> map::swap (STL/CLR)

2 つのコンテナーのコンテンツを交換します。

### <a name="syntax"></a>構文

```cpp
void swap(map<Key, Mapped>% right);
```

#### <a name="parameters"></a>パラメーター

*right*<br/>
コンテンツを交換するコンテナー。

### <a name="remarks"></a>Remarks

メンバー関数は、交換の間で被制御シーケンス`this`と*右*します。 これは一定の時間内と、例外をスローしません。 2 つのコンテナーの内容を交換する簡単な方法として使用するとします。

### <a name="example"></a>例

```cpp
// cliext_map_swap.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // construct another container with repetition of values
    Mymap c2;
    c2.insert(Mymap::make_value(L'd', 4));
    c2.insert(Mymap::make_value(L'e', 5));
    c2.insert(Mymap::make_value(L'f', 6));
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // swap and redisplay
    c1.swap(c2);
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[d 4] [e 5] [f 6]
[d 4] [e 5] [f 6]
[a 1] [b 2] [c 3]
```

## <a name="to_array"></a> map::to_array (STL/CLR)

被制御シーケンスを新しい配列にコピーします。

### <a name="syntax"></a>構文

```cpp
cli::array<value_type>^ to_array();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンスを含む配列を返します。 配列の形式で被制御シーケンスのコピーを取得して使用するとします。

### <a name="example"></a>例

```cpp
// cliext_map_to_array.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // copy the container and modify it
    cli::array<Mymap::value_type>^ a1 = c1.to_array();

    c1.insert(Mymap::make_value(L'd', 4));
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // display the earlier array copy
    for each (Mymap::value_type elem in a1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3] [d 4]
[a 1] [b 2] [c 3]
```

## <a name="upper_bound"></a> map::upper_bound (STL/CLR)

指定したキーに一致する範囲の末尾を検索します。

### <a name="syntax"></a>構文

```cpp
iterator upper_bound(key_type key);
```

#### <a name="parameters"></a>パラメーター

*key*<br/>
検索対象のキー値。

### <a name="remarks"></a>Remarks

メンバー関数は、最後の要素を決定する`X`と同等の順序を持つ被制御シーケンス内*キー*します。 このような要素が存在しない場合、または場合`X`、被制御シーケンスの最後の要素では返します[map::end (STL/CLR)](../dotnet/map-end-stl-clr.md)`()`;を超える最初の要素を指定する反復子を返します`X`. 指定したキーと一致する、被制御シーケンス内で要素のシーケンスの末尾を現在検索を使用するとします。

### <a name="example"></a>例

```cpp
// cliext_map_upper_bound.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("upper_bound(L'x')==end() = {0}",
        c1.upper_bound(L'x') == c1.end());

    Mymap::iterator it = c1.upper_bound(L'a');
    System::Console::WriteLine("*upper_bound(L'a') = [{0} {1}]",
        it->first, it->second);
    it = c1.upper_bound(L'b');
    System::Console::WriteLine("*upper_bound(L'b') = [{0} {1}]",
        it->first, it->second);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
upper_bound(L'x')==end() = True
*upper_bound(L'a') = [b 2]
*upper_bound(L'b') = [c 3]
```

## <a name="value_comp"></a> map::value_comp (STL/CLR)

2 つの要素の値の順序付けデリゲートをコピーします。

### <a name="syntax"></a>構文

```cpp
value_compare^ value_comp();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスの並べ替えに使用される順序付けデリゲートを返します。 これを使用するには 2 つの要素の値を比較します。

### <a name="example"></a>例

```cpp
// cliext_map_value_comp.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'b', 2),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="value_compare"></a> map::value_compare (STL/CLR)

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
// cliext_map_value_compare.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    Mymap::value_compare^ kcomp = c1.value_comp();

    System::Console::WriteLine("compare([L'a', 1], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine("compare([L'a', 1], [L'b', 2]) = {0}",
        kcomp(Mymap::make_value(L'a', 1),
            Mymap::make_value(L'b', 2)));
    System::Console::WriteLine("compare([L'b', 2], [L'a', 1]) = {0}",
        kcomp(Mymap::make_value(L'b', 2),
            Mymap::make_value(L'a', 1)));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare([L'a', 1], [L'a', 1]) = False
compare([L'a', 1], [L'b', 2]) = True
compare([L'b', 2], [L'a', 1]) = False
```

## <a name="value_type"></a> map::value_type (STL/CLR)

要素の型。

### <a name="syntax"></a>構文

```cpp
typedef generic_value value_type;
```

### <a name="remarks"></a>Remarks

この型は `generic_value` の同意語です。

### <a name="example"></a>例

```cpp
// cliext_map_value_type.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]" using value_type
    for (Mymap::iterator it = c1.begin(); it != c1.end(); ++it)
        {   // store element in value_type object
        Mymap::value_type val = *it;
        System::Console::Write("[{0} {1}] ", val->first, val->second);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
```

## <a name="op_neq"></a> 演算子! = (map) (STL/CLR)

非等値比較を一覧表示します。

### <a name="syntax"></a>構文

```cpp
template<typename Key,
    typename Mapped>
    bool operator!=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します`!(left == right)`します。 テストに使用するかどうか*左*順序付けされていないと同じ*右*2 つのマップが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_map_operator_ne.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="op_lt"></a> 演算子&lt;(map) (STL/CLR)

リストが比較未満です。

### <a name="syntax"></a>構文

```cpp
template<typename Key,
    typename Mapped>
    bool operator<(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します。 場合は true、最下位の位置の`i`を`!(right[i] < left[i])`も真であることをお勧め`left[i] < right[i]`します。 返しますそれ以外の場合、`left->size() < right->size()`テストに使用するかどうか*左*前に順序付けは*右*2 つのマップが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_map_operator_lt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="op_lteq"></a> 演算子&lt;= (map) (STL/CLR)

以下の一覧を表示の比較。

### <a name="syntax"></a>構文

```cpp
template<typename Key,
    typename Mapped>
    bool operator<=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します`!(right < left)`します。 テストに使用するかどうか*左*後に順序付けされていない*右*2 つのマップが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_map_operator_le.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="op_eq"></a> operator = (map) (STL/CLR)

比較を一覧表示します。

### <a name="syntax"></a>構文

```cpp
template<typename Key,
    typename Mapped>
    bool operator==(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子の関数によって制御されるシーケンスの場合にのみ true を返します*左*と*右*同じ長さであると、各位置`i`、 `left[i] ==` `right[i]`します。 テストに使用するかどうか*左*が同じ順序付け*右*2 つのマップが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_map_operator_eq.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="op_gt"></a> 演算子&gt;(map) (STL/CLR)

比較よりも大きい値の一覧を表示します。

### <a name="syntax"></a>構文

```cpp
template<typename Key,
    typename Mapped>
    bool operator>(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します`right` `<` `left`します。 テストに使用するかどうか*左*が後に順序付け*右*2 つのマップが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_map_operator_gt.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="op_gteq"></a> 演算子&gt;= (map) (STL/CLR)

リストよりも大きいまたは等しい比較します。

### <a name="syntax"></a>構文

```cpp
template<typename Key,
    typename Mapped>
    bool operator>=(map<Key, Mapped>% left,
        map<Key, Mapped>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します`!(left` `<` `right)`します。 テストに使用するかどうか*左*する前に順序付けされていない*右*2 つのマップが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_map_operator_ge.cpp
// compile with: /clr
#include <cliext/map>

typedef cliext::map<wchar_t, int> Mymap;
int main()
    {
    Mymap c1;
    c1.insert(Mymap::make_value(L'a', 1));
    c1.insert(Mymap::make_value(L'b', 2));
    c1.insert(Mymap::make_value(L'c', 3));

    // display contents " [a 1] [b 2] [c 3]"
    for each (Mymap::value_type elem in c1)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    // assign to a new container
    Mymap c2;
    c2.insert(Mymap::make_value(L'a', 1));
    c2.insert(Mymap::make_value(L'b', 2));
    c2.insert(Mymap::make_value(L'd', 4));

    // display contents " [a 1] [b 2] [d 4]"
    for each (Mymap::value_type elem in c2)
        System::Console::Write("[{0} {1}] ", elem->first, elem->second);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
[a 1] [b 2] [c 3]
[a 1] [b 2] [d 4]
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```