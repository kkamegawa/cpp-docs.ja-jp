---
title: vector (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::vector
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::vector::assign
- cliext::vector::at
- cliext::vector::back
- cliext::vector::back_item
- cliext::vector::begin
- cliext::vector::capacity
- cliext::vector::clear
- cliext::vector::const_iterator
- cliext::vector::const_reference
- cliext::vector::const_reverse_iterator
- cliext::vector::difference_type
- cliext::vector::empty
- cliext::vector::end
- cliext::vector::erase
- cliext::vector::front
- cliext::vector::front_item
- cliext::vector::generic_container
- cliext::vector::generic_iterator
- cliext::vector::generic_reverse_iterator
- cliext::vector::generic_value
- cliext::vector::insert
- cliext::vector::iterator
- cliext::vector::operator=
- cliext::vector::operator
- cliext::vector::pop_back
- cliext::vector::push_back
- cliext::vector::rbegin
- cliext::vector::reference
- cliext::vector::rend
- cliext::vector::reserve
- cliext::vector::resize
- cliext::vector::reverse_iterator
- cliext::vector::size
- cliext::vector::size_type
- cliext::vector::swap
- cliext::vector::to_array
- cliext::vector::value_type
- cliext::vector::vector
helpviewer_keywords:
- vector class [STL/CLR]
- <cliext/vector> header [STL/CLR]
- <vector> header [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> (vector) member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- at member [STL/CLR]
- back member [STL/CLR]
- back_item member [STL/CLR]
- begin member [STL/CLR]
- capacity member [STL/CLR]
- clear member [STL/CLR]
- const_iterator member [STL/CLR]
- const_reference member [STL/CLR]
- const_reverse_iterator member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- end member [STL/CLR]
- erase member [STL/CLR]
- front member [STL/CLR]
- front_item member [STL/CLR]
- generic_container member [STL/CLR]
- generic_iterator member [STL/CLR]
- generic_reverse_iterator member [STL/CLR]
- generic_value member [STL/CLR]
- insert member [STL/CLR]
- iterator member [STL/CLR]
- operator= member [STL/CLR]
- operator member [STL/CLR]
- pop_back member [STL/CLR]
- push_back member [STL/CLR]
- rbegin member [STL/CLR]
- reference member [STL/CLR]
- rend member [STL/CLR]
- reserve member [STL/CLR]
- resize member [STL/CLR]
- reverse_iterator member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- swap member [STL/CLR]
- to_array member [STL/CLR]
- value_type member [STL/CLR]
- vector member [STL/CLR]
ms.assetid: f90060d5-097a-4e9d-9a26-a634b5b9c6c2
ms.openlocfilehash: 09a0919cd47937960736c6cccf31343c5e12087d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384388"
---
# <a name="vector-stlclr"></a>vector (STL/CLR)

テンプレート クラスは、ランダムなアクセス権を持つ要素の可変長シーケンスを制御するオブジェクトについて説明します。 コンテナーを使用する`vector`ストレージの連続したブロックとして要素のシーケンスを管理します。 ブロックは、オンデマンドで拡大している配列として実装されます。

下記の説明で`GValue`と同じ*値*しない限り、後者の場合は、ref 型である場合は`Value^`します。

## <a name="syntax"></a>構文

```cpp
template<typename Value>
    ref class vector
        :   public
        System::ICloneable,
        System::Collections::IEnumerable,
        System::Collections::ICollection,
        System::Collections::Generic::IEnumerable<GValue>,
        System::Collections::Generic::ICollection<GValue>,
        System::Collections::Generic::IList<GValue>,
        Microsoft::VisualC::StlClr::IVector<GValue>
    { ..... };
```

### <a name="parameters"></a>パラメーター

*[値]*<br/>
被制御シーケンス内の要素の型。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<cliext/vector >

**Namespace:** cliext

## <a name="declarations"></a>宣言

|型定義|説明|
|---------------------|-----------------|
|[vector::const_iterator (STL/CLR)](#const_iterator)|被制御シーケンスの定数反復子の型です。|
|[vector::const_reference (STL/CLR)](#const_reference)|要素への定数参照の型です。|
|[vector::const_reverse_iterator (STL/CLR)](#const_reverse_iterator)|被制御シーケンスの定数反転反復子の型です。|
|[vector::difference_type (STL/CLR)](#difference_type)|2 つの要素間の距離を表す、符号付きの型です。|
|[vector::generic_container (STL/CLR)](#generic_container)|コンテナーのジェネリック インターフェイスの型。|
|[vector::generic_iterator (STL/CLR)](#generic_iterator)|コンテナーのジェネリック インターフェイスの反復子の型。|
|[vector::generic_reverse_iterator (STL/CLR)](#generic_reverse_iterator)|コンテナーのジェネリック インターフェイスの反転反復子の型。|
|[vector::generic_value (STL/CLR)](#generic_value)|コンテナーのジェネリック インターフェイスの要素の型。|
|[vector::iterator (STL/CLR)](#iterator)|被制御シーケンスの反復子の型です。|
|[vector::reference (STL/CLR)](#reference)|要素への参照の型です。|
|[vector::reverse_iterator (STL/CLR)](#reverse_iterator)|被制御シーケンスの反転反復子の型です。|
|[vector::size_type (STL/CLR)](#size_type)|2 つの要素間の距離を表す、符号付きの型です。|
|[vector::value_type (STL/CLR)](#value_type)|要素の型。|

|メンバー関数|説明|
|---------------------|-----------------|
|[vector::assign (STL/CLR)](#assign)|すべての要素を置換します。|
|[vector::at (STL/CLR)](#at)|指定した位置にある要素にアクセスします。|
|[vector::back (STL/CLR)](#back)|最後の要素にアクセスします。|
|[vector::begin (STL/CLR)](#begin)|被制御シーケンスの先頭を指定します。|
|[vector::capacity (STL/CLR)](#capacity)|コンテナーに割り当てられたストレージのサイズを報告します。|
|[vector::clear (STL/CLR)](#clear)|すべての要素を削除します。|
|[vector::empty (STL/CLR)](#empty)|要素が存在しないかどうかをテストします。|
|[vector::end (STL/CLR)](#end)|被制御シーケンスの末尾を指定します。|
|[vector::erase (STL/CLR)](#erase)|指定した位置にある要素を削除します。|
|[vector::front (STL/CLR)](#front)|最初の要素にアクセスします。|
|[vector::insert (STL/CLR)](#insert)|指定した位置にある要素を追加します。|
|[vector::pop_back (STL/CLR)](#pop_back)|最後の要素を削除します。|
|[vector::push_back (STL/CLR)](#push_back)|新しい最後の要素を追加します。|
|[vector::rbegin (STL/CLR)](#rbegin)|反転被制御シーケンスの先頭を指定します。|
|[vector::rend (STL/CLR)](#rend)|反転被制御シーケンスの末尾を指定します。|
|[vector::reserve (STL/CLR)](#reserve)|により、コンテナーの拡張最小容量。|
|[vector::resize (STL/CLR)](#resize)|要素の数を変更します。|
|[vector::size (STL/CLR)](#size)|要素の数をカウントします。|
|[vector::swap (STL/CLR)](#swap)|2 つのコンテナーのコンテンツを交換します。|
|[vector::to_array (STL/CLR)](#to_array)|被制御シーケンスを新しい配列にコピーします。|
|[vector::vector (STL/CLR)](#vector)|コンテナー オブジェクトを構築します。|

|プロパティ|説明|
|--------------|-----------------|
|[vector::back_item (STL/CLR)](#back_item)|最後の要素にアクセスします。|
|[vector::front_item (STL/CLR)](#front_item)|最初の要素にアクセスします。|

|演算子|説明|
|--------------|-----------------|
|[vector::operator= (STL/CLR)](#op_as)|被制御シーケンスを置き換えます。|
|[vector::operator(STL/CLR)](#op)|指定した位置にある要素にアクセスします。|
|[operator!= (vector) (STL/CLR)](#op_neq)|かどうかを`vector`オブジェクトが等しく別`vector`オブジェクト。|
|[operator< (vector) (STL/CLR)](#op_lt)|かどうかを`vector`オブジェクトが他よりも小さい`vector`オブジェクト。|
|[operator<= (vector) (STL/CLR)](#op_lteq)|かどうかを`vector`オブジェクトが別に小さい`vector`オブジェクト。|
|[operator== (vector) (STL/CLR)](#op_eq)|かどうかを`vector`オブジェクトが相互に等しい`vector`オブジェクト。|
|[operator> (vector) (STL/CLR)](#op_gt)|かどうかを`vector`オブジェクトが他よりも大きい`vector`オブジェクト。|
|[operator>= (vector) (STL/CLR)](#op_gteq)|かどうかを`vector`オブジェクトより大きいまたは相互に等しい`vector`オブジェクト。|

## <a name="interfaces"></a>インターフェイス

|Interface|説明|
|---------------|-----------------|
|<xref:System.ICloneable>|オブジェクトが重複しています。|
|<xref:System.Collections.IEnumerable>|要素をシーケンス処理します。|
|<xref:System.Collections.ICollection>|要素のグループを管理します。|
|<xref:System.Collections.Generic.IEnumerable%601>|型指定された要素をシーケンス処理します。|
|<xref:System.Collections.Generic.ICollection%601>|型指定された要素のグループを管理します。|
|<xref:System.Collections.Generic.IList%601>|型指定された要素の順序付きのグループを管理します。|
|IVector < 値\>|ジェネリックなコンテナーを管理します。|

## <a name="remarks"></a>Remarks

割り当ておよび解放の保存されている配列を通じて制御してシーケンスに対するストレージの*値*要素で、必要に応じて大きくなります。 新しい要素を追加のコストが償却定数時間であるような方法で拡張が発生します。 つまり、末尾に要素を追加のコストは増加しません、平均、被制御シーケンスを大きくの長さとして。 そのため、ベクトルとは、基になるコンテナー テンプレート クラスの有力候補[スタック (STL/CLR)](../dotnet/stack-stl-clr.md)します。

A`vector`に (前) の最初の要素の 0 からカウントの位置を直接指定された要素に参照できることを意味サポート ランダム アクセス反復子`size() - 1`(戻る) の最後の要素にします。 ベクターが基になるコンテナー テンプレート クラスに適した候補であることも意味[priority_queue (STL/CLR)](../dotnet/priority-queue-stl-clr.md)します。

ベクターの反復子は、要素の指定のバイアスとその関連のベクター オブジェクトを識別するハンドルを格納します。 関連付けられているコンテナー オブジェクトでのみ、反復子を使用することができます。 Vector 要素のバイアスは、位置の場合と同じです。

挿入または要素を消去するには、反復子によって指定された値を変更することも、指定された位置に格納されている要素の値を変更できます。 (コンテナーを要素にコピーまたはスケール ダウンまたは穴を消去した後に挿入する前に穴を作成する必要があります)。それにもかかわらず、ベクターの反復子は有効ですが範囲内にそのバイアス限り`[0, size()]`します。 さらに、有効な反復子は dereferencable--これを使用するにはアクセスまたはそのバイアスがない限り、--指定する要素の値を変更する`size()`します。

消去、または要素を削除する、格納されている値のデストラクターを呼び出します。 コンテナーを破棄するには、すべての要素が消去されます。 したがって、要素型を持つ ref クラスは、コンテナーによりする要素よりも長く保持しないコンテナーです。 ただし、ハンドルのコンテナーには、その要素は破棄されません。

## <a name="members"></a>メンバー

## <a name="assign"></a> vector::assign (STL/CLR)

すべての要素を置換します。

### <a name="syntax"></a>構文

```cpp
void assign(size_type count, value_type val);
template<typename InIt>
    void assign(InIt first, InIt last);
void assign(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>パラメーター

*count*<br/>
挿入する要素の数。

*first*<br/>
挿入する範囲の先頭。

*last*<br/>
挿入する範囲の終了。

*right*<br/>
挿入する列挙です。

*val*<br/>
挿入する要素の値。

### <a name="remarks"></a>Remarks

最初のメンバー関数は、被制御シーケンスの繰り返しを置き換えます*カウント*値の要素*val*します。 使用する要素をコンテナーと同じ値を持ちます。

場合`InIt`整数型の場合は、2 番目のメンバー関数の動作と同じ`assign((size_type)first, (value_type)last)`します。 それ以外の場合、被制御シーケンスのシーケンスを置き換えます [`first`、 `last`)。 使用することを被制御シーケンスのコピーを別のシーケンス。

3 番目のメンバー関数は、被制御シーケンスを列挙子によって指定されたシーケンスに置き換えます*右*します。 これを使用するには、被制御シーケンスの列挙子によって説明されているシーケンスのコピーを作成します。

### <a name="example"></a>例

```cpp
// cliext_vector_assign.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// assign a repetition of values
    cliext::vector<wchar_t> c2;
    c2.assign(6, L'x');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign an iterator range
    c2.assign(c1.begin(), c1.end() - 1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign an enumeration
    c2.assign(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
x x x x x x
a b
a b c
```

## <a name="at"></a> vector::at (STL/CLR)

指定した位置にある要素にアクセスします。

### <a name="syntax"></a>構文

```cpp
reference at(size_type pos);
```

#### <a name="parameters"></a>パラメーター

*pos*<br/>
アクセスする要素の位置。

### <a name="remarks"></a>Remarks

このメンバー関数は、位置にある、被制御シーケンスの要素への参照を返します*pos*します。読み取りまたは要素の位置を記述するために使用がわかっています。

### <a name="example"></a>例

```cpp
// cliext_vector_at.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using at
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// change an entry and redisplay
    c1.at(1) = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="back"></a> vector::back (STL/CLR)

最後の要素にアクセスします。

### <a name="syntax"></a>構文

```cpp
reference back();
```

### <a name="remarks"></a>Remarks

メンバー関数は、空でない必要があります、被制御シーケンスの最後の要素への参照を返します。 最後の要素へのアクセスが存在することがわかっている場合に使用するとします。

### <a name="example"></a>例

```cpp
// cliext_vector_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back() = {0}", c1.back());

// alter last item and reinspect
    c1.back() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back() = c
a b x
```

## <a name="back_item"></a> vector::back_item (STL/CLR)

最後の要素にアクセスします。

### <a name="syntax"></a>構文

```cpp
property value_type back_item;
```

### <a name="remarks"></a>Remarks

プロパティでは、空でない必要があります、被制御シーケンスの最後の要素にアクセスします。 存在することがわかっている場合、最後の要素の読み書きに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_vector_back_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("back_item = {0}", c1.back_item);

// alter last item and reinspect
    c1.back_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
back_item = c
a b x
```

## <a name="begin"></a> vector::begin (STL/CLR)

被制御シーケンスの先頭を指定します。

### <a name="syntax"></a>構文

```cpp
iterator begin();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンス、または空のシーケンスの末尾を越えた最初の要素を指定するランダム アクセス反復子を返します。 指定する反復子を取得するために使用、`current`被制御シーケンスの長さが変更された場合、被制御シーケンスが、そのステータスの先頭を変更できます。

### <a name="example"></a>例

```cpp
// cliext_vector_begin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("*begin() = {0}", *it);
    System::Console::WriteLine("*++begin() = {0}", *++it);

// alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*begin() = a
*++begin() = b
x y c
```

## <a name="capacity"></a> vector::capacity (STL/CLR)

コンテナーに割り当てられたストレージのサイズを報告します。

### <a name="syntax"></a>構文

```cpp
size_type capacity();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンスは少なくともと同じ大きさの値を保持するために現在割り当てられている記憶域を返します。 [vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`()`します。 使用する前に、被制御シーケンスの記憶域を再割り当てする必要がありますが、どの程度のコンテナーを拡張できるかを判断します。

### <a name="example"></a>例

```cpp
// cliext_vector_capacity.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="clear"></a> vector::clear (STL/CLR)

すべての要素を削除します。

### <a name="syntax"></a>構文

```cpp
void clear();
```

### <a name="remarks"></a>Remarks

メンバー関数は、効果的に呼び出す[vector::erase (STL/CLR)](../dotnet/vector-erase-stl-clr.md) `(` [vector::begin (STL/CLR)](../dotnet/vector-begin-stl-clr.md) `(),` [vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `())`. これを使用するには、被制御シーケンスが空であることを確認します。

### <a name="example"></a>例

```cpp
// cliext_vector_clear.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0}", c1.size());

// add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');

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

## <a name="const_iterator"></a> vector::const_iterator (STL/CLR)

被制御シーケンスの定数反復子の型です。

### <a name="syntax"></a>構文

```cpp
typedef T2 const_iterator;
```

### <a name="remarks"></a>Remarks

この型が指定されていない型のオブジェクトを表します`T2`被制御シーケンスの定数ランダム アクセス反復子として機能することができます。

### <a name="example"></a>例

```cpp
// cliext_vector_const_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        System::Console::Write("{0} ", *cit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reference"></a> vector::const_reference (STL/CLR)

要素への定数参照の型です。

### <a name="syntax"></a>構文

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Remarks

この型は、要素への定数参照を表します。

### <a name="example"></a>例

```cpp
// cliext_vector_const_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::const_iterator cit = c1.begin();
    for (; cit != c1.end(); ++cit)
        {   // get a const reference to an element
        cliext::vector<wchar_t>::const_reference cref = *cit;
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="const_reverse_iterator"></a> vector::const_reverse_iterator (STL/CLR)

被制御シーケンスの定数反転反復子の種類.

### <a name="syntax"></a>構文

```cpp
typedef T4 const_reverse_iterator;
```

### <a name="remarks"></a>Remarks

この型が指定されていない型のオブジェクトを表します`T4`被制御シーケンスの定数反転反復子として機能することができます。

### <a name="example"></a>例

```cpp
// cliext_vector_const_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::const_reverse_iterator crit = c1.rbegin();
    cliext::vector<wchar_t>::const_reverse_iterator crend = c1.rend();
    for (; crit != crend; ++crit)
        System::Console::Write("{0} ", *crit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="difference_type"></a> vector::difference_type (STL/CLR)

2 つの要素間の距離を符号付きの型。

### <a name="syntax"></a>構文

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Remarks

この型は、符号付きの要素の数を表します。

### <a name="example"></a>例

```cpp
// cliext_vector_difference_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::difference_type diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it) ++diff;
    System::Console::WriteLine("end()-begin() = {0}", diff);

// compute negative difference
    diff = 0;
    for (cliext::vector<wchar_t>::iterator it = c1.end();
        it != c1.begin(); --it) --diff;
    System::Console::WriteLine("begin()-end() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
begin()-end() = -3
```

## <a name="empty"></a> vector::empty (STL/CLR)

要素が存在しないかどうかをテストします。

### <a name="syntax"></a>構文

```cpp
bool empty();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスが空の場合に true を返します。 同じになります[vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md)`() == 0`します。 ベクターが空かどうかをテストに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_vector_empty.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

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

## <a name="end"></a> vector::end (STL/CLR)

被制御シーケンスの末尾を指定します。

### <a name="syntax"></a>構文

```cpp
iterator end();
```

### <a name="remarks"></a>Remarks

メンバー関数では、被制御シーケンスの最後の位置を指し示すランダム アクセス反復子を返します。 指定する反復子を取得するために使用、`current`被制御シーケンスの長さが変更された場合、被制御シーケンスが、そのステータスの末尾を変更できます。

### <a name="example"></a>例

```cpp
// cliext_vector_end.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last two items
    cliext::vector<wchar_t>::iterator it = c1.end();
    --it;
    System::Console::WriteLine("*-- --end() = {0}", *--it);
    System::Console::WriteLine("*--end() = {0}", *++it);

// alter first two items and reinspect
    *--it = L'x';
    *++it = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --end() = b
*--end() = c
a x y
```

## <a name="erase"></a> vector::erase (STL/CLR)

指定した位置にある要素を削除します。

### <a name="syntax"></a>構文

```cpp
iterator erase(iterator where);
iterator erase(iterator first, iterator last);
```

#### <a name="parameters"></a>パラメーター

*first*<br/>
消去する範囲の先頭。

*last*<br/>
消去する範囲の終了。

*where*<br/>
消去する要素。

### <a name="remarks"></a>Remarks

最初のメンバー関数が指す被制御シーケンスの要素を削除する*場所*します。 これを使用するには 1 つの要素を削除します。

2 番目のメンバー関数は、範囲 [`first`, `last`) の被制御シーケンスの要素を削除します。 これを使用するには 0 個以上の連続する要素を削除します。

両方のメンバー関数は、削除された要素の後に残る最初の要素を指定する反復子を返しますまたは[vector::end (STL/CLR)](../dotnet/vector-end-stl-clr.md) `()`そのような要素が存在しない場合。

要素を消去するときに要素のコピーの数が消去の末尾と、シーケンスの最も近い最後の要素の数に比例します。 (シーケンスのいずれかの側の 1 つまたは複数の要素を消去するときに要素のコピーは発生しません。)

### <a name="example"></a>例

```cpp
// cliext_vector_erase.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// erase an element and reinspect
    System::Console::WriteLine("erase(begin()) = {0}",
        *c1.erase(c1.begin()));

// add elements and display " b c d e"
    c1.push_back(L'd');
    c1.push_back(L'e');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// erase all but end
    cliext::vector<wchar_t>::iterator it = c1.end();
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

## <a name="front"></a> vector::front (STL/CLR)

最初の要素にアクセスします。

### <a name="syntax"></a>構文

```cpp
reference front();
```

### <a name="remarks"></a>Remarks

メンバー関数は、空でない必要があります、被制御シーケンスの最初の要素への参照を返します。 存在することがわかっている場合、最初の要素の読み書きに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_vector_front.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first item
    System::Console::WriteLine("front() = {0}", c1.front());

// alter first item and reinspect
    c1.front() = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front() = a
x b c
```

# <a name="front_item"></a> vector::front_item (STL/CLR)
最初の要素にアクセスします。

### <a name="syntax"></a>構文

```cpp
property value_type front_item;
```

### <a name="remarks"></a>Remarks

プロパティでは、空でない必要があります、被制御シーケンスの最初の要素にアクセスします。 存在することがわかっている場合、最初の要素の読み書きに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_vector_front_item.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first item
    System::Console::WriteLine("front_item = {0}", c1.front_item);

// alter first item and reinspect
    c1.front_item = L'x';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
front_item = a
x b c
```

# <a name="generic_container"></a> vector::generic_container (STL/CLR)
コンテナーのジェネリック インターフェイスの型。

### <a name="syntax"></a>構文

```cpp
typedef Microsoft::VisualC::StlClr::
    IVector<generic_value>
    generic_container;
```

### <a name="remarks"></a>Remarks

この型は、このテンプレートのコンテナー クラスのジェネリック インターフェイスを表します。

### <a name="example"></a>例

```cpp
// cliext_vector_generic_container.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    gc1->insert(gc1->end(), L'd');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify original and display generic
    c1.push_back(L'e');

    System::Collections::IEnumerator^ enum1 =
        gc1->GetEnumerator();
    while (enum1->MoveNext())
        System::Console::Write("{0} ", enum1->Current);
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

## <a name="generic_iterator"></a> vector::generic_iterator (STL/CLR)

コンテナーのジェネリック インターフェイスを使用するため、反復子の型。

### <a name="syntax"></a>構文

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ContainerRandomAccessIterator<generic_value>
    generic_iterator;
```

### <a name="remarks"></a>Remarks

この型は、このテンプレートのコンテナー クラスのジェネリック インターフェイスで使用できる汎用的な反復子を表します。

### <a name="example"></a>例

```cpp
// cliext_vector_generic_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

# <a name="generic_reverse_iterator"></a> vector::generic_reverse_iterator (STL/CLR)
コンテナーのジェネリック インターフェイスを使用する反転反復子の型。

### <a name="syntax"></a>構文

```cpp
typedef Microsoft::VisualC::StlClr::Generic::
    ReverseRandomAccessIterator<generic_value> generic_reverse_iterator;
```

### <a name="remarks"></a>Remarks

この型は、このテンプレートのコンテナー クラスのジェネリック インターフェイスで使用できる汎用の反転反復子を表します。

### <a name="example"></a>例

```cpp
// cliext_vector_generic_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_reverse_iterator gcit = gc1->rbegin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a c c
```

## <a name="generic_value"></a> vector::generic_value (STL/CLR)

コンテナーのジェネリック インターフェイスを使用するための要素の型。

### <a name="syntax"></a>構文

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Remarks

この型は、型のオブジェクトを表します。`GValue`ストアド要素の値をこのテンプレートのコンテナー クラスのジェネリック インターフェイスを使用するについて説明します。

### <a name="example"></a>例

```cpp
// cliext_vector_generic_value.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct a generic container
    cliext::vector<wchar_t>::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    cliext::vector<wchar_t>::generic_iterator gcit = gc1->begin();
    cliext::vector<wchar_t>::generic_value gcval = *gcit;
    *++gcit = gcval;
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a a c
```

## <a name="insert"></a> vector::insert (STL/CLR)

指定した位置にある要素を追加します。

### <a name="syntax"></a>構文

```cpp
iterator insert(iterator where, value_type val);
void insert(iterator where, size_type count, value_type val);
template<typename InIt>
    void insert(iterator where, InIt first, InIt last);
void insert(iterator where,
    System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>パラメーター

*count*<br/>
挿入する要素の数。

*first*<br/>
挿入する範囲の先頭。

*last*<br/>
挿入する範囲の終了。

*right*<br/>
挿入する列挙です。

*val*<br/>
挿入する要素の値。

*where*<br/>
前に挿入するコンテナー内の場所。

### <a name="remarks"></a>Remarks

メンバーの関数が指す要素の前に、挿入、*場所*で、被制御シーケンスのシーケンスは、残りのオペランドで指定します。

最初のメンバー関数は、値を持つ要素を挿入*val*し、新しく挿入された要素を指定する反復子を返します。 これを使用して、反復子によって指定された場所の前に 1 つの要素を挿入します。

2 番目のメンバー関数は、挿入の繰り返しを*カウント*値の要素*val*します。 同じ値のすべてのコピーである 0 個以上の連続する要素を挿入するのに使用するとします。

`InIt` が整数型である場合、3 番目のメンバー関数は `insert(where, (size_type)first, (value_type)last)` と同じように動作します。 シーケンスを挿入する場合は、[`first`、 `last`)。 これを使用するには 0 個以上の連続する要素を使用して、別のシーケンスからコピーを挿入します。

4 番目のメンバー関数で指定されたシーケンスを挿入する、*右*します。 これを使用して、列挙子によって説明されているシーケンスを挿入します。

1 つの要素を挿入するときに、要素のコピーの数を挿入ポイントと、シーケンスの最も近い最後の要素の数に比例します。 (一方の端のシーケンスの 1 つまたは複数の要素を挿入するときに要素のコピーは発生しません。)場合`InIt`、入力反復子は、3 番目のメンバー関数は、シーケンス内の各要素の 1 つの挿入を効果的に実行します。 それ以外の場合、挿入するときに`N`要素、要素のコピーの数が線形に`N`カーソルと最も近いシーケンスの最後の要素の数。

### <a name="example"></a>例

```cpp
// cliext_vector_insert.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a single value using iterator
    cliext::vector<wchar_t>::iterator it = c1.begin();
    System::Console::WriteLine("insert(begin()+1, L'x') = {0}",
        *c1.insert(++it, L'x'));
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert a repetition of values
    cliext::vector<wchar_t> c2;
    c2.insert(c2.begin(), 2, L'y');
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an iterator range
    it = c1.end();
    c2.insert(c2.end(), c1.begin(), --it);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// insert an enumeration
    c2.insert(c2.begin(),   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c1);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
insert(begin()+1, L'x') = x
a x b c
y y
y y a x b
a x b c y y a x b
```

## <a name="iterator"></a> vector::iterator (STL/CLR)

被制御シーケンスの反復子の型です。

### <a name="syntax"></a>構文

```cpp
typedef T1 iterator;
```

### <a name="remarks"></a>Remarks

この型が指定されていない型のオブジェクトを表します`T1`被制御シーケンスのランダム アクセス反復子として機能することができます。

### <a name="example"></a>例

```cpp
// cliext_vector_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();

// alter first element and redisplay
    it = c1.begin();
    *it = L'x';
    for (; it != c1.end(); ++it)
        System::Console::Write("{0} ", *it);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
x b c
```

## <a name="op_as"></a> vector::operator = (STL/CLR)

被制御シーケンスを置き換えます。

### <a name="syntax"></a>構文

```cpp
vector<Value>% operator=(vector<Value>% right);
```

#### <a name="parameters"></a>パラメーター

*right*<br/>
コピーするコンテナー。

### <a name="remarks"></a>Remarks

メンバー演算子コピー*右*、オブジェクトを返します`*this`します。 使用して、被制御シーケンス内のコピーを持つ、被制御シーケンスを置換する*右*します。

### <a name="example"></a>例

```cpp
// cliext_vector_operator_as.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2 = c1;
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="op"></a> vector::operator(STL/CLR)

指定した位置にある要素にアクセスします。

### <a name="syntax"></a>構文

```cpp
reference operator[](size_type pos);
```

#### <a name="parameters"></a>パラメーター

*pos*<br/>
アクセスする要素の位置。

### <a name="remarks"></a>Remarks

メンバー演算子は、位置にある要素を referene を返します*pos*します。要素がわかっている位置へのアクセスに使用します。

### <a name="example"></a>例

```cpp
// cliext_vector_operator_sub.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using subscripting
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();

// change an entry and redisplay
    c1[1] = L'x';
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1[i]);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a x c
```

## <a name="pop_back"></a> vector::pop_back (STL/CLR)

最後の要素を削除します。

### <a name="syntax"></a>構文

```cpp
void pop_back();
```

### <a name="remarks"></a>Remarks

メンバー関数は、空でない必要があります、被制御シーケンスの最後の要素を削除します。 後ろに 1 つの要素によって、ベクターを短縮するのに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_vector_pop_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// pop an element and redisplay
    c1.pop_back();
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b
```

## <a name="push_back"></a> vector::push_back (STL/CLR)

新しい最後の要素を追加します。

### <a name="syntax"></a>構文

```cpp
void push_back(value_type val);
```

### <a name="remarks"></a>Remarks

メンバー関数は、値を持つ要素を挿入する`val`被制御シーケンスの最後にします。 使用する別の要素をベクターに追加します。

### <a name="example"></a>例

```cpp
// cliext_vector_push_back.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="rbegin"></a> vector::rbegin (STL/CLR)

反転被制御シーケンスの先頭を指定します。

### <a name="syntax"></a>構文

```cpp
reverse_iterator rbegin();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、または空のシーケンスの先頭を越えた、被制御シーケンスの最後の要素を指定する反転反復子を返します。 したがって、指定、`beginning`反転シーケンスの。 指定する反復子を取得するために使用、`current`被制御シーケンスの長さが変更された場合、逆の順序で見た被制御シーケンスが、そのステータスの先頭は変更できます。

### <a name="example"></a>例

```cpp
// cliext_vector_rbegin.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items in reversed sequence
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
    System::Console::WriteLine("*rbegin() = {0}", *rit);
    System::Console::WriteLine("*++rbegin() = {0}", *++rit);

// alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*rbegin() = c
*++rbegin() = b
a y x
```

## <a name="reference"></a> vector::reference (STL/CLR)

要素への参照の型です。

### <a name="syntax"></a>構文

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Remarks

この型は、要素への参照を表します。

### <a name="example"></a>例

```cpp
// cliext_vector_reference.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    cliext::vector<wchar_t>::iterator it = c1.begin();
    for (; it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();

// modify contents " a b c"
    for (it = c1.begin(); it != c1.end(); ++it)
        {   // get a reference to an element
        cliext::vector<wchar_t>::reference ref = *it;

        ref += (wchar_t)(L'A' - L'a');
        System::Console::Write("{0} ", ref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
A B C
```

## <a name="rend"></a> vector::rend (STL/CLR)

反転被制御シーケンスの末尾を指定します。

### <a name="syntax"></a>構文

```cpp
reverse_iterator rend();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンスの先頭を越えたを指す、逆順反復子を返します。 したがって、指定、`end`反転シーケンスの。 指定する反復子を取得するために使用、`current`被制御シーケンスの長さが変更された場合、逆の順序で見た被制御シーケンスが、そのステータスの末尾は変更できます。

### <a name="example"></a>例

```cpp
// cliext_vector_rend.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect first two items
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rend();
    --rit;
    System::Console::WriteLine("*-- --rend() = {0}", *--rit);
    System::Console::WriteLine("*--rend() = {0}", *++rit);

// alter first two items and reinspect
    *--rit = L'x';
    *++rit = L'y';
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
*-- --rend() = b
*--rend() = a
y x c
```

## <a name="reserve"></a> vector::reserve (STL/CLR)

により、コンテナーの拡張最小容量。

### <a name="syntax"></a>構文

```cpp
void reserve(size_type count);
```

#### <a name="parameters"></a>パラメーター

*count*<br/>
コンテナーの新しい最小容量。

### <a name="remarks"></a>Remarks

メンバー関数は、確実`capacity()`少なくとも以下を返します*カウント*します。 あるコンテナー必要がありますが再配置被制御シーケンスに対するストレージの指定されたサイズが大きくなるまでを使用するとします。

### <a name="example"></a>例

```cpp
// cliext_vector_reserve.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for (int i = 0; i < c1.size(); ++i)
        System::Console::Write("{0} ", c1.at(i));
    System::Console::WriteLine();

// increase capacity
    cliext::vector<wchar_t>::size_type cap = c1.capacity();
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        cap, c1.size() <= cap);
    c1.reserve(cap + 5);
    System::Console::WriteLine("capacity() = {0}, ok = {1}",
        c1.capacity(), cap + 5 <= c1.capacity());
    return (0);
    }
```

```Output
a b c
capacity() = 4, ok = True
capacity() = 9, ok = True
```

## <a name="resize"></a> vector::resize (STL/CLR)

要素の数を変更します。

### <a name="syntax"></a>構文

```cpp
void resize(size_type new_size);
void resize(size_type new_size, value_type val);
```

#### <a name="parameters"></a>パラメーター

*new_size*<br/>
被制御シーケンスの新しいサイズ。

*val*<br/>
埋め込み要素の値。

### <a name="remarks"></a>Remarks

メンバー関数の両方が必ず[vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `()`以後返します*new_size*。 最初のメンバー関数が値で要素を追加する場合は、被制御シーケンスを長くするには、する必要があります、 `value_type()`2 番目のメンバー関数は、値を持つ要素を追加します。 一方、 *val*します。 被制御シーケンスを短くするために、両方のメンバー関数効果的に消去する最後の要素[vector::size (STL/CLR)](../dotnet/vector-size-stl-clr.md) `() -` `new_size`時間。 被制御シーケンスは、サイズを持つようにするために使用する*new_size*トリミングまたは現在の被制御シーケンス内のスペースでは、します。

### <a name="example"></a>例

```cpp
// cliext_vector_resize.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container and pad with default values
    cliext::vector<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());
    c1.resize(4);
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

// resize to empty
    c1.resize(0);
    System::Console::WriteLine("size() = {0}", c1.size());

// resize and pad
    c1.resize(5, L'x');
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
0 0 0 0
size() = 0
x x x x x
```

## <a name="reverse_iterator"></a> vector::reverse_iterator (STL/CLR)

被制御シーケンスの反転反復子の型です。

### <a name="syntax"></a>構文

```cpp
typedef T3 reverse_iterator;
```

### <a name="remarks"></a>Remarks

この型が指定されていない型のオブジェクトを表します`T3`被制御シーケンスの反転反復子として機能することができます。

### <a name="example"></a>例

```cpp
// cliext_vector_reverse_iterator.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" reversed
    cliext::vector<wchar_t>::reverse_iterator rit = c1.rbegin();
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();

// alter first element and redisplay
    rit = c1.rbegin();
    *rit = L'x';
    for (; rit != c1.rend(); ++rit)
        System::Console::Write("{0} ", *rit);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
x b a
```

## <a name="size"></a> vector::size (STL/CLR)

要素の数をカウントします。

### <a name="syntax"></a>構文

```cpp
size_type size();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスの長さを返します。 それを使用するには、被制御シーケンス内の現在の要素の数を決定します。 シーケンスを参照してください、0 以外のサイズがかどうかが関心のあるすべての場合[vector::empty (STL/CLR)](../dotnet/vector-empty-stl-clr.md)`()`します。

### <a name="example"></a>例

```cpp
// cliext_vector_size.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

// clear the container and reinspect
    c1.clear();
    System::Console::WriteLine("size() = {0} after clearing", c1.size());

// add elements and clear again
    c1.push_back(L'a');
    c1.push_back(L'b');
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

## <a name="size_type"></a> vector::size_type (STL/CLR)

2 つの要素間の距離を表す、符号付きの型です。

### <a name="syntax"></a>構文

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Remarks

この型は、負でない要素の数を表します。

### <a name="example"></a>例

```cpp
// cliext_vector_size_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    cliext::vector<wchar_t>::size_type diff = c1.end() - c1.begin();
    System::Console::WriteLine("end()-begin() = {0}", diff);
    return (0);
    }
```

```Output
a b c
end()-begin() = 3
```

## <a name="swap"></a> vector::swap (STL/CLR)

2 つのコンテナーのコンテンツを交換します。

### <a name="syntax"></a>構文

```cpp
void swap(vector<Value>% right);
```

#### <a name="parameters"></a>パラメーター

*right*<br/>
コンテンツを交換するコンテナー。

### <a name="remarks"></a>Remarks

メンバー関数は、交換の間で被制御シーケンス`*this`と*右*します。 これは一定の時間内と、例外をスローしません。 2 つのコンテナーの内容を交換する簡単な方法として使用するとします。

### <a name="example"></a>例

```cpp
// cliext_vector_swap.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct another container with repetition of values
    cliext::vector<wchar_t> c2(5, L'x');
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
x x x x x
x x x x x
a b c
```

## <a name="to_array"></a> vector::to_array (STL/CLR)

被制御シーケンスを新しい配列にコピーします。

### <a name="syntax"></a>構文

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンスを含む配列を返します。 配列の形式で被制御シーケンスのコピーを取得して使用するとします。

### <a name="example"></a>例

```cpp
// cliext_vector_to_array.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push_back(L'd');
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

## <a name="value_type"></a> vector::value_type (STL/CLR)

要素の型。

### <a name="syntax"></a>構文

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Remarks

型はテンプレート パラメーターのシノニム*値*します。

### <a name="example"></a>例

```cpp
// cliext_vector_value_type.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c" using value_type
    for (cliext::vector<wchar_t>::iterator it = c1.begin();
        it != c1.end(); ++it)
        {   // store element in value_type object
        cliext::vector<wchar_t>::value_type val = *it;

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="vector"></a> vector::vector (STL/CLR)

コンテナー オブジェクトを構築します。

### <a name="syntax"></a>構文

```cpp
vector();
vector(vector<Value>% right);
vector(vector<Value>^ right);
explicit vector(size_type count);
vector(size_type count, value_type val);
template<typename InIt>
    vector(InIt first, InIt last);
vector(System::Collections::Generic::IEnumerable<Value>^ right);
```

#### <a name="parameters"></a>パラメーター

*count*<br/>
挿入する要素の数。

*first*<br/>
挿入する範囲の先頭。

*last*<br/>
挿入する範囲の終了。

*right*<br/>
挿入するオブジェクトまたは範囲。

*val*<br/>
挿入する要素の値。

### <a name="remarks"></a>Remarks

コンス トラクター。

`vector();`

要素のない、被制御シーケンスを初期化します。 空の初期被制御シーケンスの指定に使用するとします。

コンス トラクター。

`vector(vector<Value>% right);`

シーケンスが被制御シーケンスを初期化します [`right.begin()`、 `right.end()`)。 使用すると、vector オブジェクトによって制御されるシーケンスのコピーである初期被制御シーケンスの指定を*右*します。

コンス トラクター。

`vector(vector<Value>^ right);`

シーケンスが被制御シーケンスを初期化します [`right->begin()`、 `right->end()`)。 ハンドルが、vector オブジェクトによって制御されるシーケンスのコピーである初期被制御シーケンスを指定するために使用*右*します。

コンス トラクター。

`explicit vector(size_type count);`

被制御シーケンスを初期化します*カウント*値を持つ要素各`value_type()`します。 使用する要素をコンテナーを格納するのに既定値を持ちます。

コンス トラクター。

`vector(size_type count, value_type val);`

被制御シーケンスを初期化します*カウント*値を持つ要素各*val*します。 使用する要素をコンテナーと同じ値を持ちます。

コンス トラクター。

`template<typename InIt>`

`vector(InIt first, InIt last);`

シーケンスが被制御シーケンスを初期化します [`first`、 `last`)。 これを使用するには、被制御シーケンスの別のシーケンスのコピーを作成します。

コンス トラクター。

`vector(System::Collections::Generic::IEnumerable<Value>^ right);`

列挙子によって指定されたシーケンスの被制御シーケンスを初期化します*右*します。 これを使用するには、被制御シーケンスの列挙子によって説明されているもう 1 つのシーケンスのコピーを作成します。

### <a name="example"></a>例

```cpp
// cliext_vector_construct.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
// construct an empty container
    cliext::vector<wchar_t> c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct with a repetition of default values
    cliext::vector<wchar_t> c2(3);
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", (int)elem);
    System::Console::WriteLine();

// construct with a repetition of values
    cliext::vector<wchar_t> c3(6, L'x');
    for each (wchar_t elem in c3)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an iterator range
    cliext::vector<wchar_t>::iterator it = c3.end();
    cliext::vector<wchar_t> c4(c3.begin(), --it);
    for each (wchar_t elem in c4)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct with an enumeration
    cliext::vector<wchar_t> c5(   // NOTE: cast is not needed
        (System::Collections::Generic::IEnumerable<wchar_t>^)%c3);
    for each (wchar_t elem in c5)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    cliext::vector<wchar_t> c7(c3);
    for each (wchar_t elem in c7)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying a container handle
    cliext::vector<wchar_t> c8(%c3);
    for each (wchar_t elem in c8)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    return (0);
    }
```

```Output
size() = 0
0 0 0
x x x x x x
x x x x x
x x x x x x
x x x x x x
x x x x x x
```

## <a name="op_neq"></a> 演算子! = (ベクター) (STL/CLR)

非等値比較をベクターします。

### <a name="syntax"></a>構文

```cpp
template<typename Value>
    bool operator!=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します`!(left == right)`します。 テストに使用するかどうか*左*順序付けされていないと同じ*右*2 つのベクトルが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_vector_operator_ne.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="op_lt"></a> 演算子&lt;(ベクター) (STL/CLR)

ベクターの比較よりも小さいです。

### <a name="syntax"></a>構文

```cpp
template<typename Value>
    bool operator<(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します。 場合は true、最下位の位置の`i`を`!(right[i] < left[i])`も真であることをお勧め`left[i] < right[i]`します。 返しますそれ以外の場合、`left->size() < right->size()`テストに使用するかどうか*左*前に順序付けは*右*2 つのベクトルが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_vector_operator_lt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="op_lteq"></a> 演算子&lt;= (ベクター) (STL/CLR)

以下のベクターの比較。

### <a name="syntax"></a>構文

```cpp
template<typename Value>
    bool operator<=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します`!(right < left)`します。 テストに使用するかどうか*左*後に順序付けされていない*右*2 つのベクトルが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_vector_operator_le.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="op_eq"></a> 演算子 (ベクター) (STL/CLR) = =

ベクター比較します。

### <a name="syntax"></a>構文

```cpp
template<typename Value>
    bool operator==(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子の関数によって制御されるシーケンスの場合にのみ true を返します*左*と*右*同じ長さであると、各位置`i`、 `left[i] ==` `right[i]`します。 テストに使用するかどうか*左*が同じ順序付け*右*2 つのベクトルが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_vector_operator_eq.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="op_gt"></a> 演算子&gt;(ベクター) (STL/CLR)

ベクターの比較よりも大きいです。

### <a name="syntax"></a>構文

```cpp
template<typename Value>
    bool operator>(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します`right` `<` `left`します。 テストに使用するかどうか*左*が後に順序付け*右*2 つのベクトルが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_vector_operator_gt.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="op_gteq"></a> 演算子&gt;= (ベクター) (STL/CLR)

Vector より大きいまたは等しい比較します。

### <a name="syntax"></a>構文

```cpp
template<typename Value>
    bool operator>=(vector<Value>% left,
        vector<Value>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します`!(left < right)`します。 テストに使用するかどうか*左*する前に順序付けされていない*右*2 つのベクトルが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_vector_operator_ge.cpp
// compile with: /clr
#include <cliext/vector>

int main()
    {
    cliext::vector<wchar_t> c1;
    c1.push_back(L'a');
    c1.push_back(L'b');
    c1.push_back(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    cliext::vector<wchar_t> c2;
    c2.push_back(L'a');
    c2.push_back(L'b');
    c2.push_back(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```