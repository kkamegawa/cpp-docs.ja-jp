---
title: concurrent_vector クラス
ms.date: 11/04/2016
f1_keywords:
- concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::concurrent_vector
- CONCURRENT_VECTOR/concurrency::concurrent_vector::assign
- CONCURRENT_VECTOR/concurrency::concurrent_vector::at
- CONCURRENT_VECTOR/concurrency::concurrent_vector::back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::begin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::capacity
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::cend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::clear
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::crend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::empty
- CONCURRENT_VECTOR/concurrency::concurrent_vector::end
- CONCURRENT_VECTOR/concurrency::concurrent_vector::front
- CONCURRENT_VECTOR/concurrency::concurrent_vector::get_allocator
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_by
- CONCURRENT_VECTOR/concurrency::concurrent_vector::grow_to_at_least
- CONCURRENT_VECTOR/concurrency::concurrent_vector::max_size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::push_back
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rbegin
- CONCURRENT_VECTOR/concurrency::concurrent_vector::rend
- CONCURRENT_VECTOR/concurrency::concurrent_vector::reserve
- CONCURRENT_VECTOR/concurrency::concurrent_vector::resize
- CONCURRENT_VECTOR/concurrency::concurrent_vector::shrink_to_fit
- CONCURRENT_VECTOR/concurrency::concurrent_vector::size
- CONCURRENT_VECTOR/concurrency::concurrent_vector::swap
helpviewer_keywords:
- concurrent_vector class
ms.assetid: a217b4ac-af2b-4d41-94eb-09a75ee28622
ms.openlocfilehash: e8036b0942600e5d47254583e2675c525010a5c1
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657566"
---
# <a name="concurrentvector-class"></a>concurrent_vector クラス

`concurrent_vector` クラスは、任意の要素にランダムにアクセスできるようにするシーケンス コンテナー クラスです。 これを使用すると、同時実行セーフな追加、要素アクセス、反復子アクセス、および反復子走査の各操作を実行できます。

## <a name="syntax"></a>構文

```
template<typename T, class _Ax>
class concurrent_vector: protected details::_Allocator_base<T,
    _Ax>,
private details::_Concurrent_vector_base_v4;
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
ベクターに格納される要素のデータ型。

*_Ax*<br/>
同時実行ベクターのメモリの割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクトを表す型。 この引数は省略可能であり、既定値は `allocator<T>` です。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|`allocator_type`|同時実行ベクターのアロケーター クラスを表す型。|
|`const_iterator`|読み取ることができるランダム アクセス反復子を提供する型、`const`同時実行ベクター内の要素。|
|`const_pointer`|ポインターを提供する型、`const`同時実行ベクター内の要素。|
|`const_reference`|参照を提供する型、`const`要素の読み取りと実行のための同時実行ベクターに格納されている`const`操作。|
|`const_reverse_iterator`|いずれかを読み取ることができるランダム アクセス反復子を提供する型`const`同時実行ベクター内の要素。|
|`difference_type`|同時実行ベクターの 2 つの要素間の符号付きの距離を提供する型。|
|`iterator`|同時実行ベクター内の要素を読み取ることができるランダム アクセス反復子を提供する型。 反復子を使用して要素の変更は、同時実行セーフではありません。|
|`pointer`|同時実行ベクター内の要素へのポインターを提供する型。|
|`reference`|同時実行ベクターに格納されている要素への参照を提供する型。|
|`reverse_iterator`|反転された同時実行ベクター内の任意の要素を読み取ることができるランダム アクセス反復子を提供する型。 反復子を使用して要素の変更は、同時実行セーフではありません。|
|`size_type`|同時実行ベクター内の要素の数をカウントする型。|
|`value_type`|同時実行ベクターに格納されているデータ型を表す型。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[concurrent_vector](#ctor)|オーバーロードされます。 同時実行ベクターを構築します。|
|[~ concurrent_vector デストラクター](#dtor)|すべての要素を消去し、この同時実行ベクターを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[assign](#assign)|オーバーロードされます。 同時実行ベクターの要素を消去し、いずれかを割り当てる`_N`のコピー `_Item`、反復子の範囲で指定された値、または [ `_Begin`、 `_End`)。 このメソッドはコンカレンシー セーフではありません。|
|[at](#at)|オーバーロードされます。 同時実行ベクターで指定したインデックス位置にある要素へのアクセスを提供します。 このメソッドは、同時実行セーフ読み取り操作と、値を確認をしている限り、ベクトルを増加しているときにも`_Index`が、同時実行ベクターのサイズより小さい。|
|[back](#back)|オーバーロードされます。 または、参照を返します`const`最後に、同時実行ベクター内の要素を参照します。 同時実行ベクターが空の場合、戻り値が定義されていません。 このメソッドはコンカレンシー セーフです。|
|[begin](#begin)|オーバーロードされます。 型の反復子を返します`iterator`または`const_iterator`同時実行ベクターの先頭にします。 このメソッドはコンカレンシー セーフです。|
|[capacity](#capacity)|同時実行ベクターがより多くのメモリを割り当てることがなく拡張できる最大サイズを返します。 このメソッドはコンカレンシー セーフです。|
|[cbegin](#cbegin)|型の反復子を返します`const_iterator`同時実行ベクターの先頭にします。 このメソッドはコンカレンシー セーフです。|
|[cend](#cend)|型の反復子を返します`const_iterator`同時実行ベクターの末尾にします。 このメソッドはコンカレンシー セーフです。|
|[clear](#clear)|同時実行のベクトル内のすべての要素を消去します。 このメソッドはコンカレンシー セーフではありません。|
|[crbegin](#crbegin)|型の反復子を返します`const_reverse_iterator`同時実行ベクターの先頭にします。 このメソッドはコンカレンシー セーフです。|
|[crend](#crend)|型の反復子を返します`const_reverse_iterator`同時実行ベクターの末尾にします。 このメソッドはコンカレンシー セーフです。|
|[empty](#empty)|テスト時に、同時実行ベクターが空の場合、このメソッドが呼び出されます。 このメソッドはコンカレンシー セーフです。|
|[end](#end)|オーバーロードされます。 型の反復子を返します`iterator`または`const_iterator`同時実行ベクターの末尾にします。 このメソッドはコンカレンシー セーフです。|
|[front](#front)|オーバーロードされます。 または、参照を返します`const`同時実行ベクターの最初の要素への参照。 同時実行ベクターが空の場合、戻り値が定義されていません。 このメソッドはコンカレンシー セーフです。|
|[get_allocator](#get_allocator)|同時実行ベクターを構築するために使用するアロケーターのコピーを返します。 このメソッドはコンカレンシー セーフです。|
|[grow_by](#grow_by)|オーバーロードされます。 この同時実行ベクターで`_Delta`要素。 このメソッドはコンカレンシー セーフです。|
|[grow_to_at_least](#grow_to_at_least)|この同時実行ベクターになるまで、少なくとも拡張`_N`要素。 このメソッドはコンカレンシー セーフです。|
|[max_size](#max_size)|同時実行ベクターが保持できる要素の最大数を返します。 このメソッドはコンカレンシー セーフです。|
|[push_back](#push_back)|オーバーロードされます。 同時実行ベクターの末尾に指定したアイテムを追加します。 このメソッドはコンカレンシー セーフです。|
|[rbegin](#rbegin)|オーバーロードされます。 型の反復子を返します`reverse_iterator`または`const_reverse_iterator`同時実行ベクターの先頭にします。 このメソッドはコンカレンシー セーフです。|
|[rend](#rend)|オーバーロードされます。 型の反復子を返します`reverse_iterator`または`const_reverse_iterator`同時実行ベクターの末尾にします。 このメソッドはコンカレンシー セーフです。|
|[reserve](#reserve)|サイズに、同時実行ベクターを拡張するための十分な領域を割り当てます`_N`を後でより多くのメモリを割り当てる必要はありません。 このメソッドはコンカレンシー セーフではありません。|
|[resize](#resize)|オーバーロードされます。 要求されたサイズ、削除、または必要に応じて要素を追加するには、同時実行ベクターのサイズを変更します。 このメソッドはコンカレンシー セーフではありません。|
|[shrink_to_fit](#shrink_to_fit)|断片化を削減し、メモリ使用量を最適化する同時実行ベクターの内部表現が圧縮されます。 このメソッドはコンカレンシー セーフではありません。|
|[size](#size)|同時実行ベクターの要素の数を返します。 このメソッドはコンカレンシー セーフです。|
|[swap](#swap)|2 つの同時実行ベクターの内容を交換します。 このメソッドはコンカレンシー セーフではありません。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[operator\[\]](#operator_at)|オーバーロードされます。 同時実行ベクターで指定したインデックス位置にある要素へのアクセスを提供します。 このメソッドは、同時実行セーフ読み取り操作とすることを確認する値として、ベクトルを増加しているときにも`_Index`が、同時実行ベクターのサイズより小さい。|
|[operator=](#operator_eq)|オーバーロードされます。 別の `concurrent_vector` オブジェクトの内容をこのオブジェクトに割り当てます。 このメソッドはコンカレンシー セーフではありません。|

## <a name="remarks"></a>Remarks

詳細については、`concurrent_vector`クラスを参照してください[並列コンテナーとオブジェクト](../../../parallel/concrt/parallel-containers-and-objects.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`_Concurrent_vector_base_v4`

`_Allocator_base`

`concurrent_vector`

## <a name="requirements"></a>必要条件

**ヘッダー:** concurrent_vector.h

**名前空間:** concurrency

##  <a name="assign"></a> 割り当てる

同時実行ベクターの要素を消去し、いずれかを割り当てる`_N`のコピー `_Item`、反復子の範囲で指定された値、または [ `_Begin`、 `_End`)。 このメソッドはコンカレンシー セーフではありません。

```
void assign(
    size_type _N,
    const_reference _Item);

template<class _InputIterator>
void assign(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>パラメーター

*_InputIterator*<br/>
指定した反復子の型。

*_N*<br/>
同時実行ベクターにコピーする項目の数。

*(_I)*<br/>
同時実行ベクターの塗りつぶしに使用される値への参照。

*開始 (_b)*<br/>
ソース範囲の最初の要素の反復子。

*(_E)*<br/>
1 つ後ろのソース範囲の最後の要素を反復子。

### <a name="remarks"></a>Remarks

`assign` 同時実行セーフではありません。 他のスレッド メソッドを呼び出していない、同時実行ベクターをこのメソッドを呼び出すときにすることを確認する必要があります。

##  <a name="at"></a> で

同時実行ベクターで指定したインデックス位置にある要素へのアクセスを提供します。 このメソッドは、同時実行セーフ読み取り操作と、値を確認をしている限り、ベクトルを増加しているときにも`_Index`が、同時実行ベクターのサイズより小さい。

```
reference at(size_type _Index);

const_reference at(size_type _Index) const;
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
取得する要素のインデックス。

### <a name="return-value"></a>戻り値

指定したインデックス位置にある項目への参照。

### <a name="remarks"></a>Remarks

関数のバージョン`at`以外を返す`const`の参照を使用して同時に別のスレッドから要素を書き込むことはできません。 さまざまな同期オブジェクトは、同時読み取りを同期し、同じデータ要素への書き込み操作を使用してください。

メソッドはスロー`out_of_range`場合`_Index`が同時実行のベクターのサイズ以上と`range_error`ベクターの破損部分のインデックスが含まれる場合。 ベクターが維持される方法について詳しくは、次を参照してください。[並列コンテナーとオブジェクト](../../../parallel/concrt/parallel-containers-and-objects.md)します。

##  <a name="back"></a> 戻る

または、参照を返します`const`最後に、同時実行ベクター内の要素を参照します。 同時実行ベクターが空の場合、戻り値が定義されていません。 このメソッドはコンカレンシー セーフです。

```
reference back();

const_reference back() const;
```

### <a name="return-value"></a>戻り値

参照または`const`最後に、同時実行ベクター内の要素を参照します。

##  <a name="begin"></a> 開始

型の反復子を返します`iterator`または`const_iterator`同時実行ベクターの先頭にします。 このメソッドはコンカレンシー セーフです。

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>戻り値

型の反復子`iterator`または`const_iterator`同時実行ベクターの先頭にします。

##  <a name="capacity"></a> 容量

同時実行ベクターがより多くのメモリを割り当てることがなく拡張できる最大サイズを返します。 このメソッドはコンカレンシー セーフです。

```
size_type capacity() const;
```

### <a name="return-value"></a>戻り値

最大サイズを同時実行ベクターがより多くのメモリを割り当てることがなく拡張できます。

### <a name="remarks"></a>Remarks

C++ 標準ライブラリとは異なり`vector`、`concurrent_vector`より多くのメモリを割り当てる場合は、オブジェクトが既存の要素を移動しません。

##  <a name="cbegin"></a> cbegin

型の反復子を返します`const_iterator`同時実行ベクターの先頭にします。 このメソッドはコンカレンシー セーフです。

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

型の反復子`const_iterator`同時実行ベクターの先頭にします。

##  <a name="cend"></a> cend

型の反復子を返します`const_iterator`同時実行ベクターの末尾にします。 このメソッドはコンカレンシー セーフです。

```
const_iterator cend() const;
```

### <a name="return-value"></a>戻り値

型の反復子`const_iterator`同時実行ベクターの末尾にします。

##  <a name="clear"></a> オフ

同時実行のベクトル内のすべての要素を消去します。 このメソッドはコンカレンシー セーフではありません。

```
void clear();
```

### <a name="remarks"></a>Remarks

`clear` 同時実行セーフではありません。 他のスレッド メソッドを呼び出していない、同時実行ベクターをこのメソッドを呼び出すときにすることを確認する必要があります。 `clear` 内部配列を解放しません。 内部配列を解放するには、関数を呼び出す`shrink_to_fit`後`clear`します。

##  <a name="ctor"></a> concurrent_vector

同時実行ベクターを構築します。

```
explicit concurrent_vector(
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector(
    const concurrent_vector<T,
    M>& _Vector,
    const allocator_type& _Al = allocator_type());

concurrent_vector(
    concurrent_vector&& _Vector);

explicit concurrent_vector(
    size_type _N);

concurrent_vector(
    size_type _N,
    const_reference _Item,
    const allocator_type& _Al = allocator_type());

template<class _InputIterator>
concurrent_vector(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());
```

### <a name="parameters"></a>パラメーター

*M*<br/>
ソース ベクターのアロケーターの型。

*_InputIterator*<br/>
入力反復子の型。

*_Al*<br/>
このオブジェクトに対して使用するアロケーター クラス。

*_Vector*<br/>
要素のコピー元または移動元の `concurrent_vector` オブジェクト。

*_N*<br/>
`concurrent_vector` オブジェクトの初期容量。

*(_I)*<br/>
構築されたオブジェクトの要素の値。

*開始 (_b)*<br/>
コピーする要素範囲内の最初の要素の位置。

*(_E)*<br/>
コピーする要素範囲を超える最初の要素の位置。

### <a name="remarks"></a>Remarks

すべてのコンストラクターは、アロケーター オブジェクト `_Al` を格納し、ベクターを初期化します。

最初のコンス トラクターは、空の初期ベクターを指定し、アロケーターの型を明示的に指定します。 使用します。

2 つ目および 3 つ目のコンストラクターは、同時実行ベクター `_Vector` のコピーを指定します。

4 番目のコンストラクターは、同時実行ベクター `_Vector` の移動を指定します。

5 番目のコンス トラクターを指定された数の繰り返しを指定します ( `_N`) クラスの既定値の要素の`T`します。

6 番目のコンス トラクターの繰り返しを指定します ( `_N`) の値の要素`_Item`します。

最後のコンス トラクターは、反復子の範囲で指定された値を指定します。 [ `_Begin`、 `_End`)。

##  <a name="dtor"></a> ~concurrent_vector

すべての要素を消去し、この同時実行ベクターを破棄します。

```
~concurrent_vector();
```

##  <a name="crbegin"></a> crbegin

型の反復子を返します`const_reverse_iterator`同時実行ベクターの先頭にします。 このメソッドはコンカレンシー セーフです。

```
const_reverse_iterator crbegin() const;
```

### <a name="return-value"></a>戻り値

型の反復子`const_reverse_iterator`同時実行ベクターの先頭にします。

##  <a name="crend"></a> crend

型の反復子を返します`const_reverse_iterator`同時実行ベクターの末尾にします。 このメソッドはコンカレンシー セーフです。

```
const_reverse_iterator crend() const;
```

### <a name="return-value"></a>戻り値

型の反復子`const_reverse_iterator`同時実行ベクターの末尾にします。

##  <a name="empty"></a> 空

テスト時に、同時実行ベクターが空の場合、このメソッドが呼び出されます。 このメソッドはコンカレンシー セーフです。

```
bool empty() const;
```

### <a name="return-value"></a>戻り値

**true**場合は、関数が呼び出された時点で、ベクターが空**false**それ以外の場合。

##  <a name="end"></a> 終わり

型の反復子を返します`iterator`または`const_iterator`同時実行ベクターの末尾にします。 このメソッドはコンカレンシー セーフです。

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>戻り値

型の反復子`iterator`または`const_iterator`同時実行ベクターの末尾にします。

##  <a name="front"></a> 前面

または、参照を返します`const`同時実行ベクターの最初の要素への参照。 同時実行ベクターが空の場合、戻り値が定義されていません。 このメソッドはコンカレンシー セーフです。

```
reference front();

const_reference front() const;
```

### <a name="return-value"></a>戻り値

参照または`const`同時実行ベクターの最初の要素への参照。

##  <a name="get_allocator"></a> get_allocator

同時実行ベクターを構築するために使用するアロケーターのコピーを返します。 このメソッドはコンカレンシー セーフです。

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>戻り値

構築に使用するアロケーターのコピー、`concurrent_vector`オブジェクト。

##  <a name="grow_by"></a> grow_by

この同時実行ベクターで`_Delta`要素。 このメソッドはコンカレンシー セーフです。

```
iterator grow_by(
    size_type _Delta);

iterator grow_by(
    size_type _Delta,
    const_reference _Item);
```

### <a name="parameters"></a>パラメーター

*_Delta*<br/>
オブジェクトに追加する要素の数。

*(_I)*<br/>
新しい要素を初期化する値。

### <a name="return-value"></a>戻り値

最初の項目への反復が追加されます。

### <a name="remarks"></a>Remarks

場合`_Item`が指定されていない、新しい要素が既定で構築します。

##  <a name="grow_to_at_least"></a> grow_to_at_least

この同時実行ベクターになるまで、少なくとも拡張`_N`要素。 このメソッドはコンカレンシー セーフです。

```
iterator grow_to_at_least(size_type _N);
```

### <a name="parameters"></a>パラメーター

*_N*<br/>
新しい最小サイズ、`concurrent_vector`オブジェクト。

### <a name="return-value"></a>戻り値

インデックス位置にある要素に追加されたシーケンスの先頭を指す反復子`_N`場合、要素は追加されません。

##  <a name="max_size"></a> max_size

同時実行ベクターが保持できる要素の最大数を返します。 このメソッドはコンカレンシー セーフです。

```
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

要素の最大数、`concurrent_vector`オブジェクトを保持できます。

##  <a name="operator_eq"></a> 演算子 =

別の `concurrent_vector` オブジェクトの内容をこのオブジェクトに割り当てます。 このメソッドはコンカレンシー セーフではありません。

```
concurrent_vector& operator= (
    const concurrent_vector& _Vector);

template<class M>
concurrent_vector& operator= (
    const concurrent_vector<T, M>& _Vector);

concurrent_vector& operator= (
    concurrent_vector&& _Vector);
```

### <a name="parameters"></a>パラメーター

*M*<br/>
ソース ベクターのアロケーターの型。

*_Vector*<br/>
ソース `concurrent_vector` オブジェクト。

### <a name="return-value"></a>戻り値

この `concurrent_vector` オブジェクトへの参照。

##  <a name="operator_at"></a> operator[]

同時実行ベクターで指定したインデックス位置にある要素へのアクセスを提供します。 このメソッドは、同時実行セーフ読み取り操作とすることを確認する値として、ベクトルを増加しているときにも`_Index`が、同時実行ベクターのサイズより小さい。

```
reference operator[](size_type _index);

const_reference operator[](size_type _index) const;
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
取得する要素のインデックス。

### <a name="return-value"></a>戻り値

指定したインデックス位置にある項目への参照。

### <a name="remarks"></a>Remarks

バージョンの`operator []`以外を返す`const`の参照を使用して同時に別のスレッドから要素を書き込むことはできません。 さまざまな同期オブジェクトは、同時読み取りを同期し、同じデータ要素への書き込み操作を使用してください。

チェックを実行することがない境界`_Index`は同時実行ベクターに有効なインデックスです。

##  <a name="push_back"></a> push_back

同時実行ベクターの末尾に指定したアイテムを追加します。 このメソッドはコンカレンシー セーフです。

```
iterator push_back(const_reference _Item);

iterator push_back(T&& _Item);
```

### <a name="parameters"></a>パラメーター

*(_I)*<br/>
追加する値。

### <a name="return-value"></a>戻り値

項目の反復子が追加されます。

##  <a name="rbegin"></a> rbegin

型の反復子を返します`reverse_iterator`または`const_reverse_iterator`同時実行ベクターの先頭にします。 このメソッドはコンカレンシー セーフです。

```
reverse_iterator rbegin();

const_reverse_iterator rbegin() const;
```

### <a name="return-value"></a>戻り値

型の反復子`reverse_iterator`または`const_reverse_iterator`同時実行ベクターの先頭にします。

##  <a name="rend"></a> rend

型の反復子を返します`reverse_iterator`または`const_reverse_iterator`同時実行ベクターの末尾にします。 このメソッドはコンカレンシー セーフです。

```
reverse_iterator rend();

const_reverse_iterator rend() const;
```

### <a name="return-value"></a>戻り値

型の反復子`reverse_iterator`または`const_reverse_iterator`同時実行ベクターの末尾にします。

##  <a name="reserve"></a> 予約

サイズに、同時実行ベクターを拡張するための十分な領域を割り当てます`_N`を後でより多くのメモリを割り当てる必要はありません。 このメソッドはコンカレンシー セーフではありません。

```
void reserve(size_type _N);
```

### <a name="parameters"></a>パラメーター

*_N*<br/>
領域を予約する要素の数。

### <a name="remarks"></a>Remarks

`reserve` 同時実行セーフではありません。 他のスレッド メソッドを呼び出していない、同時実行ベクターをこのメソッドを呼び出すときにすることを確認する必要があります。 メソッドが返された後に、同時実行ベクターの容量は、要求された予約よりも大きい可能性があります。

##  <a name="resize"></a> サイズ変更

要求されたサイズ、削除、または必要に応じて要素を追加するには、同時実行ベクターのサイズを変更します。 このメソッドはコンカレンシー セーフではありません。

```
void resize(
    size_type _N);

void resize(
    size_type _N,
    const T& val);
```

### <a name="parameters"></a>パラメーター

*_N*<br/>
Concurrent_vector の新しいサイズ。

*val*<br/>
新しい要素の値は、新しいサイズが元のサイズより大きいかどうか、ベクターに追加されます。 値を省略すると、新しいオブジェクトには、その型の既定値は割り当てられます。

### <a name="remarks"></a>Remarks

コンテナーのサイズが要求されたサイズより小さい場合は、要素は、要求されたサイズに達するまで、ベクターに追加されます。 コンテナーのサイズに到達するまでに、コンテナーの末尾に近い要素が削除されたコンテナーのサイズが要求されたサイズより大きい場合は、`_N`します。 コンテナーの現在のサイズが要求されたサイズと同じ場合は、何も実行されません。

`resize` 同時実行セーフです。 他のスレッド メソッドを呼び出していない、同時実行ベクターをこのメソッドを呼び出すときにすることを確認する必要があります。

##  <a name="shrink_to_fit"></a> shrink_to_fit

断片化を削減し、メモリ使用量を最適化する同時実行ベクターの内部表現が圧縮されます。 このメソッドはコンカレンシー セーフではありません。

```
void shrink_to_fit();
```

### <a name="remarks"></a>Remarks

このメソッドは内部的に再割り当て、メモリ移動要素すべての反復子を無効にします。 `shrink_to_fit` 同時実行セーフではありません。 他のスレッド メソッドを呼び出していない、同時実行ベクターをこの関数を呼び出すときにすることを確認する必要があります。

##  <a name="size"></a> サイズ

同時実行ベクターの要素の数を返します。 このメソッドはコンカレンシー セーフです。

```
size_type size() const;
```

### <a name="return-value"></a>戻り値

この要素の数`concurrent_vector`オブジェクト。

### <a name="remarks"></a>Remarks

返されるサイズ、関数の呼び出しにより追加されたすべての要素を含めることが保証されます`push_back`、またはこのメソッドを呼び出す前に完了した操作を拡大します。 ただし、割り当てられている要素を含める場合も、同時呼び出し数増加メソッドのいずれかにして構築中。

##  <a name="swap"></a> スワップ

2 つの同時実行ベクターの内容を交換します。 このメソッドはコンカレンシー セーフではありません。

```
void swap(concurrent_vector& _Vector);
```

### <a name="parameters"></a>パラメーター

*_Vector*<br/>
`concurrent_vector`コンテンツを交換するオブジェクト。

## <a name="see-also"></a>関連項目

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[並列コンテナーと並列オブジェクト](../../../parallel/concrt/parallel-containers-and-objects.md)

