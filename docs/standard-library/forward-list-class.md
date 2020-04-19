---
title: forward_list クラス
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::forward_list
- forward_list/std::forward_list::allocator_type
- forward_list/std::forward_list::const_iterator
- forward_list/std::forward_list::const_pointer
- forward_list/std::forward_list::const_reference
- forward_list/std::forward_list::difference_type
- forward_list/std::forward_list::iterator
- forward_list/std::forward_list::pointer
- forward_list/std::forward_list::reference
- forward_list/std::forward_list::size_type
- forward_list/std::forward_list::value_type
- forward_list/std::forward_list::assign
- forward_list/std::forward_list::before_begin
- forward_list/std::forward_list::begin
- forward_list/std::forward_list::cbefore_begin
- forward_list/std::forward_list::cbegin
- forward_list/std::forward_list::cend
- forward_list/std::forward_list::clear
- forward_list/std::forward_list::emplace_after
- forward_list/std::forward_list::emplace_front
- forward_list/std::forward_list::empty
- forward_list/std::forward_list::end
- forward_list/std::forward_list::erase_after
- forward_list/std::forward_list::front
- forward_list/std::forward_list::get_allocator
- forward_list/std::forward_list::insert_after
- forward_list/std::forward_list::max_size
- forward_list/std::forward_list::merge
- forward_list/std::forward_list::pop_front
- forward_list/std::forward_list::push_front
- forward_list/std::forward_list::remove
- forward_list/std::forward_list::remove_if
- forward_list/std::forward_list::resize
- forward_list/std::forward_list::reverse
- forward_list/std::forward_list::sort
- forward_list/std::forward_list::splice_after
- forward_list/std::forward_list::swap
- forward_list/std::forward_list::unique
helpviewer_keywords:
- std::forward_list
- std::forward_list::allocator_type
- std::forward_list::const_iterator
- std::forward_list::const_pointer
- std::forward_list::const_reference
- std::forward_list::difference_type
- std::forward_list::iterator
- std::forward_list::pointer
- std::forward_list::reference
- std::forward_list::size_type
- std::forward_list::value_type
- std::forward_list::assign
- std::forward_list::before_begin
- std::forward_list::begin
- std::forward_list::cbefore_begin
- std::forward_list::cbegin
- std::forward_list::cend
- std::forward_list::clear
- std::forward_list::emplace_after
- std::forward_list::emplace_front
- std::forward_list::empty
- std::forward_list::end
- std::forward_list::erase_after
- std::forward_list::front
- std::forward_list::get_allocator
- std::forward_list::insert_after
- std::forward_list::max_size
- std::forward_list::merge
- std::forward_list::pop_front
- std::forward_list::push_front
- std::forward_list::remove
- std::forward_list::remove_if
- std::forward_list::resize
- std::forward_list::reverse
- std::forward_list::sort
- std::forward_list::splice_after
- std::forward_list::swap
- std::forward_list::unique
ms.openlocfilehash: e13242aa41cc99cdd01a6f16b607ef568195d659
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890200"
---
# <a name="forward_list-class"></a>forward_list クラス

要素の可変長シーケンスを制御するオブジェクトを表します。 シーケンスはノードのシングル リンク リストとして格納され、各ノードには型 `Type` のメンバーが含まれます。

## <a name="syntax"></a>構文

```cpp
template <class Type,
    class Allocator = allocator<Type>>
class forward_list
```

### <a name="parameters"></a>パラメーター

「* \」と入力します。
forward_list に格納される要素のデータ型。

*アロケーター* \
forward_list によるメモリの割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクト。 このパラメーターは省略できます。 既定値は allocator<`Type`> です。

## <a name="remarks"></a>Remarks

`forward_list` オブジェクトは、[アロケータークラス](../standard-library/allocator-class.md)(`std::allocator)`と呼ばれる) に基づくクラス*アロケーター*の格納されたオブジェクトによって制御されるシーケンスのストレージを割り当て、解放します。 詳細については、「[アロケーター](../standard-library/allocators.md)」をご覧ください。 アロケーターオブジェクトは、`allocator` 型のオブジェクトと同じ外部インターフェイスを持っている必要があります。

> [!NOTE]
> コンテナー オブジェクトを代入しても、格納されているアロケーター オブジェクトはコピーされません。

反復子、ポインター、および参照は、それらの被制御シーケンスの要素が `forward_list` を通じて消去された場合、無効になる可能性があります。 `forward_list` を通じて被制御シーケンスに対して行われた挿入およびスプライスによって反復子が無効になることはありません。

[forward_list::insert_after](#insert_after) の呼び出しによって、被制御シーケンスへの追加が発生する場合があります。この関数は、コンストラクター `Type(const  T&)` を呼び出す唯一のメンバー関数です。 `forward_list` は、移動コンストラクターも呼び出す場合があります。 このような式が例外をスローした場合、コンテナー オブジェクトは新しい要素を挿入せず、例外を再スローします。 このため、このような例外が発生した場合は、`forward_list` 型のオブジェクトが既知の状態のままになります。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[forward_list](#forward_list)|`forward_list` 型のオブジェクトを構築します。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[allocator_type](#allocator_type)|前方リスト オブジェクトのアロケーター クラスを表す型。|
|[const_iterator](#const_iterator)|前方リストに定数反復子を提供する型。|
|[const_pointer](#const_pointer)|前方リスト内の**const**要素へのポインターを提供する型。|
|[const_reference](#const_reference)|前方リスト内の要素への定数参照を提供する型。|
|[difference_type](#difference_type)|前方リストの要素の数を、反復子が指す要素の範囲に基づいて表すために使用できる符号付き整数型。|
|[Iterator](#iterator)|前方リストの反復子を提供する型。|
|[pointer](#pointer)|前方リスト内の要素へのポインターを提供する型。|
|[reference](#reference)|前方リスト内の要素への参照を提供する型。|
|[size_type](#size_type)|2 つの要素間の距離を表す、符号なしの型。|
|[value_type](#value_type)|前方リストに格納された要素の型を表す型。|

### <a name="functions"></a>関数

|||
|-|-|
|[assign](#assign)|前方リストから要素を消去し、対象の前方リストに新しい要素のセットをコピーします。|
|[before_begin](#before_begin)|前方リスト内の先頭要素の前の位置を示す反復子を返します。|
|[begin](#begin)|前方リスト内の最初の要素を指す反復子を返します。|
|[cbefore_begin](#cbefore_begin)|前方リスト内の先頭要素の前の位置を示す定数反復子を返します。|
|[cbegin](#cbegin)|前方リスト内の最初の要素を指す定数反復子を返します。|
|[cend](#cend)|前方リスト内の最後の要素の次の場所を指す定数反復子を返します。|
|[clear](#clear)|前方リストのすべての要素を消去します。|
|[emplace_after](#emplace_after)|指定された位置の後に新しい要素を構築します。|
|[emplace_front](#emplace_front)|イン プレースで構築された要素をリストの先頭に追加します。|
|[empty](#empty)|前方リストが空であるかどうかをテストします。|
|[end](#end)|前方リスト内の最後の要素の次の場所を指す反復子を返します。|
|[erase_after](#erase_after)|前方リストから指定された位置の後の要素を削除します。|
|[front](#front)|前方リスト内の最初の要素への参照を返します。|
|[get_allocator](#get_allocator)|前方リストの構築に使用されるアロケーター オブジェクトのコピーを返します。|
|[insert_after](#insert_after)|前方リストの指定された位置の後に要素を追加します。|
|[max_size](#max_size)|前方リストの最大長を返します。|
|[merge](#merge)|引数リストから要素を削除し、それをターゲットの前方リストに挿入して、新たに組み合わされたセットの要素を昇順またはその他の指定された順序で並べ替えます。|
|[pop_front](#pop_front)|前方リストの先頭から要素を削除します。|
|[push_front](#push_front)|前方リストの先頭に要素を追加します。|
|[remove](#remove)|指定された値と一致する前方リスト内の要素を消去します。|
|[remove_if](#remove_if)|指定された述語を満たす前方リスト内の要素を消去します。|
|[resize](#resize)|前方リストの新しいサイズを指定します。|
|[reverse](#reverse)|前方リスト内で要素が出現する順序を反転させます。|
|[sort](#sort)|要素を昇順または述語によって指定された順序で配置します。|
|[splice_after](#splice_after)|ノード間のリンクを再接合します。|
|[swap](#swap)|2 つの前方リストの要素を交換します。|
|[unique](#unique)|指定されたテストに合格した隣接する要素を削除します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](#op_eq)|別の前方リストのコピーで前方リストの要素を置き換えます。|

## <a name="allocator_type"></a>allocator_type

前方リスト オブジェクトのアロケーター クラスを表す型。

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Remarks

`allocator_type` は、テンプレート パラメーター Allocator のシノニムです。

## <a name="assign"></a>割り当てる

前方リストから要素を消去し、対象の前方リストに新しい要素のセットをコピーします。

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign(
    initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>パラメーター

*最初*の \
置換範囲の先頭。

*最後*の \
置換範囲の末尾。

*カウント*\
割り当てる要素の数。

*val* \
各要素に割り当てる値。

*型*\
値の型。

*IList* \
コピーする initializer_list。

### <a name="remarks"></a>Remarks

forward_list が整数型の場合、1 つ目のメンバー関数は `assign((size_type)First, (Type)Last)` と同様に動作します。 それ以外の場合、1 つ目のメンバー関数は、`*this` によって制御されているシーケンスをシーケンス [ `First, Last)` に置換します。このシーケンスは、初期状態の被制御シーケンスと重なってはなりません。

2 つ目のメンバー関数は、`*this` によって制御されているシーケンスを、値 `Count` の `Val` 個の要素の繰り返しで置き換えます。

3 つ目のメンバー関数は、initializer_list の要素を forward_list にコピーします。

## <a name="before_begin"></a>before_begin

前方リスト内の先頭要素の前の位置を示す反復子を返します。

```cpp
const_iterator before_begin() const;
iterator before_begin();
```

### <a name="return-value"></a>戻り値

シーケンスの最初の要素の直前 (または末尾の空のシーケンスの直前) の位置を示す前方反復子。

### <a name="remarks"></a>Remarks

## <a name="begin"></a>初め

前方リスト内の最初の要素を指す反復子を返します。

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>戻り値

シーケンスの最初の要素 (または空のシーケンスの末尾の次の位置) を示す前方反復子。

### <a name="remarks"></a>Remarks

## <a name="cbefore_begin"></a>cbefore_begin

前方リスト内の先頭要素の前の位置を示す定数反復子を返します。

```cpp
const_iterator cbefore_begin() const;
```

### <a name="return-value"></a>戻り値

シーケンスの最初の要素の直前 (または末尾の空のシーケンスの直前) の位置を示す前方反復子。

### <a name="remarks"></a>Remarks

## <a name="cbegin"></a>cbegin

範囲内の最初の要素を指す**定数**反復子を返します。

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

範囲の最初の要素、または空の範囲の末尾の次の位置 (空の範囲の場合は `cbegin() == cend()`) を指す、**定数**前方アクセス反復子。

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

範囲の末尾の次の位置を指し示す前方アクセス反復子。

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

前方リストのすべての要素を消去します。

```cpp
void clear();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、`erase_after(before_begin(), end()).` を呼び出します。

## <a name="const_iterator"></a>const_iterator

前方リストに定数反復子を提供する型。

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Remarks

`const_iterator` は、被制御シーケンスの定数前方反復子として使用できるオブジェクトを表します。 ここでは、実装定義型のシノニムとして記述されています。

## <a name="const_pointer"></a>const_pointer

前方リスト内の**const**要素へのポインターを提供する型。

```cpp
typedef typename Allocator::const_pointer
    const_pointer;
```

### <a name="remarks"></a>Remarks

## <a name="const_reference"></a>const_reference

前方リスト内の要素への定数参照を提供する型。

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Remarks

## <a name="difference_type"></a>difference_type

前方リストの要素の数を、反復子が指す要素の範囲に基づいて表すために使用できる符号付き整数型。

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Remarks

`difference_type` は、被制御シーケンス内にある任意の 2 つの要素のアドレスの違いを表現できるオブジェクトを記述します。

## <a name="emplace_after"></a>emplace_after

指定された位置の後に新しい要素を構築します。

```cpp
template <class T>
iterator emplace_after(const_iterator Where, Type&& val);
```

### <a name="parameters"></a>パラメーター

*\*
新しい要素が構築された、ターゲット前方リスト内の位置。

*val* \
コンストラクターの引数。

### <a name="return-value"></a>戻り値

新しく挿入される要素を指定する反復子。

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンス内の*位置*が指す要素の直後に、コンストラクター引数*val*を持つ要素を挿入します。 それ以外は、[forward_list::insert_after](#insert_after) と同じ動作をします。

## <a name="emplace_front"></a>emplace_front

イン プレースで構築された要素をリストの先頭に追加します。

```cpp
template <class Type>
    void emplace_front(Type&& val);
```

### <a name="parameters"></a>パラメーター

*val* \
前方リストの先頭に追加する要素。

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスの末尾に、コンストラクター引数 `_ val` を持つ要素を挿入します。

例外がスローされた場合、コンテナーは変更されず、例外が再度スローされます。

## <a name="empty"></a>指定

前方リストが空であるかどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

前方リストが空の場合は**true** 。それ以外の場合は**false**。

## <a name="end"></a>終わり

前方リスト内の最後の要素の次の場所を指す反復子を返します。

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>戻り値

シーケンスの末尾の次の位置を指す前方反復子。

## <a name="erase_after"></a>erase_after

前方リストから指定された位置の後の要素を削除します。

```cpp
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```

### <a name="parameters"></a>パラメーター

*\*
要素が削除される、ターゲット前方リスト内の位置。

*最初*の \
削除する範囲の先頭。

*最後*の \
削除する範囲の最後。

### <a name="return-value"></a>戻り値

削除した要素の後に残る最初の要素を指定する反復子。このような要素が存在しない場合は、[forward_list::end](#end)。

### <a name="remarks"></a>Remarks

最初のメンバー関数は、被制御シーケンスの要素を、 *Where*の直後に削除します。

2 番目のメンバー関数は、範囲 `( first,  last)` (両端は含まない) の被制御シーケンスの要素を削除します。

`N` 個の要素を削除すると、デストラクターが `N` 回呼び出されます。 [再割り当て](../standard-library/forward-list-class.md)が発生するため、反復子と参照は、消去された要素に対して無効になります。

メンバー関数が例外をスローすることはありません。

## <a name="forward_list"></a>forward_list

`forward_list` 型のオブジェクトを構築します。

```cpp
forward_list();
explicit forward_list(const Allocator& Al);
explicit forward_list(size_type Count);
forward_list(size_type Count, const Type& Val);
forward_list(size_type Count, const Type& Val, const Allocator& Al);
forward_list(const forward_list& Right);
forward_list(const forward_list& Right, const Allocator& Al);
forward_list(forward_list&& Right);
forward_list(forward_list&& Right, const Allocator& Al);
forward_list(initializer_list<Type> IList, const Alloc& Al);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>パラメーター

*Al* \
このオブジェクトに対して使用するアロケーター クラス。

*カウント*\
構築されたリスト内の要素の数。

*Val* \
構築されたリストの要素の値。

*右*\
構築されたリストがコピーになる元のリスト。

*最初*の \
コピーする要素範囲内の最初の要素の位置。

*最後*の \
コピーする要素範囲を超える最初の要素の位置。

*IList* \
コピーする initializer_list。

### <a name="remarks"></a>Remarks

すべてのコンストラクターは[アロケーター](../standard-library/allocator-class.md)を格納し、被制御シーケンスを初期化します。 アロケーターオブジェクトは、引数*Al*(存在する場合) です。 コピー コンストラクターの場合は、` right.get_allocator()` です。 それ以外の場合は `Allocator()` です。

最初の 2 つのコンストラクターは、空の初期被制御シーケンスを指定します。

3番目のコンストラクターは、`Type()` 値の*Count*要素の繰り返しを指定します。

4番目と5番目のコンストラクターは、値*Val*の*Count*要素の繰り返しを指定します。

6番目のコンストラクターは、 *Right*によって制御されるシーケンスのコピーを指定します。 `InputIterator` が整数型の場合、次の 2 つのコンストラクターは、値 `(size_type)First` の `(Type)Last` 個の要素の繰り返しを指定します。 それ以外の場合、次の 2 つのコンストラクターは、シーケンス `[First, Last)` を指定します。

9 番目と 10 番目のコンストラクターは 6 番目と同じですが、[rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) 参照があります。

最後のコンストラクターは、クラス `initializer_list<Type>` のオブジェクトによる初期被制御シーケンスを指定します。

## <a name="front"></a>外側

前方リスト内の最初の要素への参照を返します。

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>戻り値

被制御シーケンスの最初の要素への参照。被制御シーケンスを空にすることはできません。

## <a name="get_allocator"></a>get_allocator

前方リストの構築に使用されるアロケーター オブジェクトのコピーを返します。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>戻り値

格納されている[アロケーター](../standard-library/allocator-class.md) オブジェクトを取得します。

## <a name="insert_after"></a>insert_after

前方リストの指定された位置の後に要素を追加します。

```cpp
iterator insert_after(const_iterator Where, const Type& Val);
void insert_after(const_iterator Where, size_type Count, const Type& Val);
void insert_after(const iterator Where, initializer_list<Type> IList);
iterator insert_after(const_iterator Where, Type&& Val);
template <class InputIterator>
    void insert_after(const_iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>パラメーター

*\*
最初の要素が挿入される、ターゲット前方リスト内の位置。

*カウント*\
挿入する要素の数。

*最初*の \
挿入範囲の先頭。

*最後*の \
挿入範囲の末尾。

*Val* \
前方リストに追加する要素。

*IList* \
挿入する initializer_list。

### <a name="return-value"></a>戻り値

新しく挿入される要素を指定する反復子 (最初と最後のメンバー関数のみ)。

### <a name="remarks"></a>Remarks

各メンバー関数は、被制御シーケンス内の*位置*を指す要素の直後に、残りのオペランドによって指定されたシーケンスを挿入します。

1つ目のメンバー関数は、値*Val*を持つ要素を挿入し、新しく挿入された要素を指定する反復子を返します。

2番目のメンバー関数は、値*Val*の*Count*要素の繰り返しを挿入します。

`InputIterator` が整数型である場合、3 番目のメンバー関数は `insert(it, (size_type)First, (Type)Last)` と同じように動作します。 それ以外の場合は、シーケンス `[First, Last)` を挿入します。このシーケンスは、最初の被制御シーケンスと重複しないようにする必要があります。

4 番目のメンバー関数は、クラス `initializer_list<Type>` のオブジェクトによって指定されたシーケンスを挿入します。

最後のメンバー関数は 1 番目の関数と同じですが、[rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) 参照を受け取ります。

`N` 個の要素を挿入すると、コンストラクターが `N` 回呼び出されます。 [再割り当て](../standard-library/forward-list-class.md)が実行されますが、反復子または参照は無効になりません。

1 つまたは複数の要素の挿入時に例外がスローされた場合、コンテナーは変更されず、再度例外がスローされます。

## <a name="iterator"></a>反

前方リストの反復子を提供する型。

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Remarks

`iterator` は、被制御シーケンスの前方反復子として使用できるオブジェクトを表します。 ここでは、実装定義型のシノニムとして記述されています。

## <a name="max_size"></a>max_size

前方リストの最大長を返します。

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

オブジェクトが制御できる最も長いシーケンスの長さ。

### <a name="remarks"></a>Remarks

## <a name="merge"></a>マージ

2 つの並べ替えシーケンスを結合し、線形時間で 1 つの並べ替えシーケンスとします。 引数リストから要素を削除し、それをこの `forward_list` に挿入します。 `merge` を呼び出す前に、2 つのリストを同じ比較関数オブジェクトによって並べ替える必要があります。 結合されたリストは、その比較関数オブジェクトによって並び替えられます。

```cpp
void merge(forward_list& right);
template <class Predicate>
    void merge(forward_list& right, Predicate comp);
```

### <a name="parameters"></a>パラメーター

*右*\
マージする前方リスト。

*comp* \
要素を並べ替えるために使用される比較関数オブジェクト。

### <a name="remarks"></a>Remarks

`forward_list::merge` によって `forward_list` `right`から要素が削除され、この `forward_list`に挿入されます。 以下に示すように、両方のシーケンスを同じ述語に基づいて順序付けする必要があります。 結合されたシーケンスも、その比較関数オブジェクトに基づいて順序付けされます。

`i` および `j` の位置にある要素を指定する反復子 `Pi` および `Pj` がある場合、最初のメンバー関数は、`i < j` のたびに、順序 `!(*Pj < *Pi)` を設定します。 (要素は `ascending` 順に並べ替えられます)。2番目のメンバー関数は、`i < j` たびに順序を `! comp(*Pj, *Pi)` します。

元の被制御シーケンス内の要素ペアは、結果として得られた被制御シーケンス内で順序が反転されることはありません。 結果として得られた被制御シーケンス内の要素ペアが等価である場合 (`!(*Pi < *Pj) && !(*Pj < *Pi)`)、元の被制御シーケンスからの要素は、`right` によって制御されるシーケンスからの要素の前に置かれます。

例外は、`comp` が例外をスローした場合にのみ発生します。 その場合、被制御シーケンスは順序が指定されないままとされ、例外が再スローされます。

## <a name="op_eq"></a>operator =

別の前方リストのコピーで前方リストの要素を置き換えます。

```cpp
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```

### <a name="parameters"></a>パラメーター

*右*\
前方リストにコピーする前方リスト。

*IList* \
型 `Type` の要素のシーケンスと同じように動作する中かっこで囲まれた初期化子リスト。

### <a name="remarks"></a>Remarks

最初のメンバー演算子は、被制御シーケンスを*right*によって制御されるシーケンスのコピーで置き換えます。

2 番目のメンバー演算子は、クラス `initializer_list<Type>` オブジェクトからの被制御シーケンスを置き換えます。

3 番目のメンバー演算子は最初のものと同じですが、[rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) を使用します。

## <a name="pointer"></a>pointer

前方リスト内の要素へのポインターを提供する型。

```cpp
typedef typename Allocator::pointer pointer;
```

## <a name="pop_front"></a>pop_front

前方リストの先頭から要素を削除します。

```cpp
void pop_front();
```

### <a name="remarks"></a>Remarks

前方リストの最初の要素は、空にすることができません。

メンバー関数が例外をスローすることはありません。

## <a name="push_front"></a>push_front

前方リストの先頭に要素を追加します。

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>パラメーター

*val* \
前方リストの先頭に追加する要素。

### <a name="remarks"></a>Remarks

例外がスローされた場合、コンテナーは変更されず、例外が再度スローされます。

## <a name="reference"></a>「

前方リスト内の要素への参照を提供する型。

```cpp
typedef typename Allocator::reference reference;
```

## <a name="remove"></a>から

指定された値と一致する前方リスト内の要素を消去します。

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>パラメーター

*val* \
要素によって保持されている場合、リストからその要素が削除される原因となる値。

### <a name="remarks"></a>Remarks

メンバー関数は、反復子 `P` で指定されたすべての要素を被制御シーケンスから削除します (`*P ==  val`)。

メンバー関数が例外をスローすることはありません。

## <a name="remove_if"></a>remove_if

指定された述語を満たす前方リスト内の要素を消去します。

```cpp
template <class Predicate>
    void remove_if(Predicate pred);
```

### <a name="parameters"></a>パラメーター

*pred* \
要素によって満たされる場合、単項述語は結果的にリストからその要素を削除します。

### <a name="remarks"></a>Remarks

メンバー関数は、反復子 `P` で指定されたすべての要素を被制御シーケンスから削除します (` pred(*P)` は true)。

例外は、 *pred*が例外をスローした場合にのみ発生します。 その場合、被制御シーケンスは状態が未指定のままとなり、例外が再スローされます。

## <a name="resize"></a>サイズ

前方リストの新しいサイズを指定します。

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```

### <a name="parameters"></a>パラメーター

*Newsize\ (_c)*
サイズ指定された前方リストの要素の数。

*val* \
埋め込みで使用する値。

### <a name="remarks"></a>Remarks

メンバー関数はどちらも、リストその後内の要素の数が*Newsize*であることを確認します。 被制御シーケンスを長くする必要がある場合、最初のメンバー関数は値 `Type()` を持つ要素を追加し、2番目のメンバー関数は値*val*を持つ要素を追加します。 被制御シーケンスを短くするには、両方のメンバー関数とも `erase_after(begin() + _Newsize - 1, end())` を効果的に呼び出します。

## <a name="reverse"></a>後ろ向き

前方リスト内で要素が出現する順序を反転させます。

```cpp
void reverse();
```

## <a name="size_type"></a>size_type

2 つの要素間の距離を表す、符号なしの型。

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="remarks"></a>Remarks

符号なし整数型は、被制御シーケンスの長さを表すことができるオブジェクトを表します。

## <a name="sort"></a>基づく

要素を昇順または述語によって指定された順序で配置します。

```cpp
void sort();
template <class Predicate>
void sort(Predicate pred);
```

### <a name="parameters"></a>パラメーター

*pred* \
順序付け述語。

### <a name="remarks"></a>Remarks

両方のメンバー関数は、次に説明するように、述語に基づいて被制御シーケンス内の要素を順序付けします。

`i` および `j` の位置にある要素を指定する反復子 `Pi` および `Pj` がある場合、最初のメンバー関数は、`i < j` のたびに、順序 `!(*Pj < *Pi)` を設定します。 (要素は `ascending` 順に並べ替えられます)。メンバーテンプレート関数は、`i < j` たびに注文 `! pred(*Pj, *Pi)` を行います。 元の被制御シーケンス内の順序付けされた要素ペアは、結果として得られた被制御シーケンス内で順序が反転されることはありません。 (並べ替えは安定しています)。

例外は、 *pred*が例外をスローした場合にのみ発生します。 その場合、被制御シーケンスは順序が指定されないままとされ、例外が再スローされます。

## <a name="splice_after"></a>splice_after

ソースの forward_list から要素を削除して、ターゲットの forward_list に挿入します。

```cpp
// insert the entire source forward_list
void splice_after(const_iterator Where, forward_list& Source);
void splice_after(const_iterator Where, forward_list&& Source);

// insert one element of the source forward_list
void splice_after(const_iterator Where, forward_list& Source, const_iterator Iter);
void splice_after(const_iterator Where, forward_list&& Source, const_iterator Iter);

// insert a range of elements from the source forward_list
void splice_after(
    const_iterator Where,
    forward_list& Source,
    const_iterator First,
    const_iterator Last);

void splice_after(
    const_iterator Where,
    forward_list&& Source,
    const_iterator First,
    const_iterator Last);
```

### <a name="parameters"></a>パラメーター

*\*
ターゲットの forward_list 内の挿入位置の直前の位置。

*Source*\
ターゲットの forward_list に挿入されるソースの forward_list。

*Iter* \
ソースの forward_list リストから挿入される要素。

*最初*の \
ソースの forward_list リストから挿入される範囲内の最初の要素。

*最後*の \
ソースの forward_list リストから挿入される範囲を超える最初の位置。

### <a name="remarks"></a>Remarks

メンバー関数の最初のペアは、*ソース*によって制御されるシーケンスを、 *Where*でポイントされた被制御シーケンス内の要素の直後に挿入します。 また、*ソース*からすべての要素が削除されます。 (`&Source` は**this**と等しくない必要があります)。

メンバー関数の2番目のペアは、*ソース*によって制御されるシーケンス内の*Iter*の直後にある要素を削除し、 *Where*によってポイントされた被制御シーケンス内の要素の直後に挿入します。 (`Where == Iter || Where == ++Iter` の場合は、何も変わりません)。

3番目のメンバー関数 (範囲指定されたスプライス) は、`(First, Last)` によって指定されたサブ範囲を、 *Where*でポイントされた被制御シーケンス内の要素の直後に、*ソース*によって制御されるシーケンスから挿入します。 また、*ソース*によって制御されるシーケンスから元のサブ範囲も削除されます。 (`&Source == this`場合、範囲 `(First, Last)` には、 *Where*でポイントする要素を含めることはできません)。

範囲指定されたスプライスで `N` 個の要素が挿入され、さらに `&Source != this` の場合、クラス [iterator](#iterator) のオブジェクトは `N` 回インクリメントされます。

スプライスされた要素を指定している反復子、ポインター、参照は、いずれも無効になりません。

### <a name="example"></a>例

```cpp
// forward_list_splice_after.cpp
// compile with: /EHsc /W4
#include <forward_list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    forward_list<int> c1{ 10, 11 };
    forward_list<int> c2{ 20, 21, 22 };
    forward_list<int> c3{ 30, 31 };
    forward_list<int> c4{ 40, 41, 42, 43 };

    forward_list<int>::iterator where_iter;
    forward_list<int>::iterator first_iter;
    forward_list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice_after(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice_after(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    c2.splice_after(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = (10) (11)c2 = (20) (21) (22)c3 = (30) (31)c4 = (40) (41) (42) (43)After splicing c1 into c2:c1 =c2 = (20) (21) (10) (11) (22)After splicing the first element of c3 into c2:c3 = (30)c2 = (20) (21) (31) (10) (11) (22)After splicing a range of c4 into c2:c4 = (40) (41)c2 = (20) (21) (42) (43) (31) (10) (11) (22)
```

## <a name="swap"></a>フォト

2 つの前方リストの要素を交換します。

```cpp
void swap(forward_list& right);
```

### <a name="parameters"></a>パラメーター

*右*\
交換する要素を指定する前方リスト。

### <a name="remarks"></a>Remarks

このメンバー関数は、`*this` と*right*の間で被制御シーケンスを交換します。 `get_allocator() ==  right.get_allocator()` の場合、この処理は一定時間に実行されます。例外がスローされることはなく、参照や、ポインター、2 つの被制御シーケンス内の要素を指定する反復子が無効にされることもありません。 それ以外の場合、2 つの被制御シーケンス内の要素数に比例した回数、要素の割り当てとコンストラクター呼び出しが実行されます。

## <a name="unique"></a>固有

等値要素内の連続するグループのそれぞれから、最初の要素を除くすべてを削除します。

```cpp
void unique();
template <class BinaryPredicate>
void unique(BinaryPredicate comp);
```

### <a name="parameters"></a>パラメーター

*comp* \
一連の要素の比較に使用する二項述語。

### <a name="remarks"></a>Remarks

各一意の要素の最初のオブジェクトを保持し、残りは削除します。 値の等しい要素がリスト内で隣接するように、要素を並べ替える必要があります。

最初のメンバー関数は、直前の要素に一致するすべての要素を被制御シーケンスから削除します。 `i` および `j` の位置にある要素を指定する反復子 `Pi` および `Pj` がある場合、2 番目のメンバー関数は、`i + 1 == j &&  comp(*Pi, *Pj)` の条件を満たすすべての要素を削除します。

被制御シーケンスの長さが `N` (> 0) である場合、述語 ` comp(*Pi, *Pj)` は評価される時間 `N - 1` となります。

例外は、`comp` が例外をスローした場合にのみ発生します。 その場合、被制御シーケンスは状態が未指定のままとなり、例外が再スローされます。

## <a name="value_type"></a>value_type

前方リストに格納された要素の型を表す型。

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `Type` のシノニムです。
