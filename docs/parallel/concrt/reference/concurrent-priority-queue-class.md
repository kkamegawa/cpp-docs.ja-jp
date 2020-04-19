---
title: concurrent_priority_queue クラス
ms.date: 11/04/2016
f1_keywords:
- concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::concurrent_priority_queue
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::clear
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::empty
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::get_allocator
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::push
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::size
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::swap
- CONCURRENT_PRIORITY_QUEUE/concurrency::concurrent_priority_queue::try_pop
helpviewer_keywords:
- concurrent_priority_queue class
ms.assetid: 3e740381-0f4e-41fc-8b66-ad0bb55f17a3
ms.openlocfilehash: 1d8651d1391ded2970a00a7429c36f341a438659
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143216"
---
# <a name="concurrent_priority_queue-class"></a>concurrent_priority_queue クラス

`concurrent_priority_queue` クラスは、複数のスレッドが項目を同時にプッシュおよびポップできるようにするコンテナーです。 項目は優先順位の順にポップされます。この優先順位は、テンプレート引数として指定されたファンクタによって決まります。

## <a name="syntax"></a>構文

```cpp
template <typename T,
    typename _Compare= std::less<T>,
    typename _Ax = std::allocator<T>
>,
    typename _Ax = std::allocator<T>> class concurrent_priority_queue;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
優先順位キューに格納される要素のデータ型。

*_Compare*<br/>
2つの要素の値を並べ替えキーとして比較して優先順位キュー内の相対順序を決定できる関数オブジェクトの型。 この引数は省略可能であり、既定値は二項述語 `less<T>` です。

*_Ax*<br/>
同時優先順位キューのメモリの割り当てと解放に関する詳細をカプセル化する、格納されているアロケーターオブジェクトを表す型。 この引数は省略可能であり、既定値は `allocator<T>` です。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

|Name|説明|
|----------|-----------------|
|`allocator_type`|同時優先順位キューのアロケータークラスを表す型。|
|`const_reference`|同時実行優先順位キューに格納されている型の要素への const 参照を表す型。|
|`reference`|同時実行優先順位キューに格納されている型の要素への参照を表す型。|
|`size_type`|同時実行優先順位キュー内の要素の数をカウントする型。|
|`value_type`|同時実行優先順位キューに格納されているデータ型を表す型。|

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[concurrent_priority_queue](#ctor)|オーバーロードされます。 同時優先順位キューを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[オフ](#clear)|同時実行優先度内のすべての要素を消去します。 このメソッドはコンカレンシー セーフではありません。|
|[empty](#empty)|このメソッドが呼び出されたときに、同時優先順位キューが空かどうかをテストします。 このメソッドはコンカレンシー セーフです。|
|[get_allocator](#get_allocator)|同時優先順位キューを構築するために使用されるアロケーターのコピーを返します。 このメソッドはコンカレンシー セーフです。|
|[push](#push)|オーバーロードされます。 同時優先順位キューに要素を追加します。 このメソッドはコンカレンシー セーフです。|
|[size](#size)|同時優先順位キュー内の要素の数を返します。 このメソッドはコンカレンシー セーフです。|
|[スワップ](#swap)|2つの同時優先順位キューの内容を交換します。 このメソッドはコンカレンシー セーフではありません。|
|[try_pop](#try_pop)|キューが空でない場合は、キューから最も優先順位の高い要素を削除して返します。 このメソッドはコンカレンシー セーフです。|

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|[operator=](#operator_eq)|オーバーロードされます。 別の `concurrent_priority_queue` オブジェクトの内容をこのオブジェクトに割り当てます。 このメソッドはコンカレンシー セーフではありません。|

## <a name="remarks"></a>コメント

`concurrent_priority_queue` クラスの詳細については、「[並列コンテナーとオブジェクト](../../../parallel/concrt/parallel-containers-and-objects.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`concurrent_priority_queue`

## <a name="requirements"></a>要件

**ヘッダー:** concurrent_priority_queue

**名前空間:** concurrency

## <a name="clear"></a>クリア

同時実行優先度内のすべての要素を消去します。 このメソッドはコンカレンシー セーフではありません。

```cpp
void clear();
```

### <a name="remarks"></a>コメント

`clear` は同時実行セーフではありません。 このメソッドを呼び出すときに、他のスレッドが同時優先順位キューに対してメソッドを呼び出していないことを確認する必要があります。 `clear` はメモリを解放しません。

## <a name="ctor"></a>concurrent_priority_queue

同時優先順位キューを構築します。

```cpp
explicit concurrent_priority_queue(
    const allocator_type& _Al = allocator_type());

explicit concurrent_priority_queue(
    size_type _Init_capacity,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_priority_queue(_InputIterator _Begin,
    _InputIterator _End,
    const allocator_type& _Al = allocator_type());

concurrent_priority_queue(
    const concurrent_priority_queue& _Src);

concurrent_priority_queue(
    const concurrent_priority_queue& _Src,
    const allocator_type& _Al);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src);

concurrent_priority_queue(
    concurrent_priority_queue&& _Src,
    const allocator_type& _Al);
```

### <a name="parameters"></a>パラメーター

*_InputIterator*<br/>
入力反復子の型。

*_Al*<br/>
このオブジェクトに対して使用するアロケーター クラス。

*_Init_capacity*<br/>
`concurrent_priority_queue` オブジェクトの初期容量。

*_Begin*<br/>
コピーする要素範囲内の最初の要素の位置。

*_End*<br/>
コピーする要素範囲を超える最初の要素の位置。

*_Src*<br/>
要素のコピー元または移動元の `concurrent_priority_queue` オブジェクト。

### <a name="remarks"></a>コメント

すべてのコンストラクターは、アロケーターオブジェクト `_Al` を格納し、優先順位キューを初期化します。

最初のコンストラクターは、空の初期優先順位キューを指定し、必要に応じてアロケーターを指定します。

2番目のコンストラクターは、初期容量 `_Init_capacity` の優先順位キューを指定し、必要に応じてアロケーターを指定します。

3番目のコンストラクターは、反復子の範囲 [`_Begin`、`_End`) によって指定された値を指定し、必要に応じてアロケーターを指定します。

4番目と5番目のコンストラクターは、優先順位キュー `_Src`のコピーを指定します。

6番目と7番目のコンストラクターは、優先順位キュー `_Src`の移動を指定します。

## <a name="empty"></a>指定

このメソッドが呼び出されたときに、同時優先順位キューが空かどうかをテストします。 このメソッドはコンカレンシー セーフです。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

関数が呼び出された時点で優先順位キューが空だった場合は**true** 、それ以外の場合は**false** 。

## <a name="get_allocator"></a>get_allocator

同時優先順位キューを構築するために使用されるアロケーターのコピーを返します。 このメソッドはコンカレンシー セーフです。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>戻り値

`concurrent_priority_queue` オブジェクトを構築するために使用されるアロケーターのコピー。

## <a name="operator_eq"></a>operator =

別の `concurrent_priority_queue` オブジェクトの内容をこのオブジェクトに割り当てます。 このメソッドはコンカレンシー セーフではありません。

```cpp
concurrent_priority_queue& operator= (const concurrent_priority_queue& _Src);

concurrent_priority_queue& operator= (concurrent_priority_queue&& _Src);
```

### <a name="parameters"></a>パラメーター

*_Src*<br/>
ソース `concurrent_priority_queue` オブジェクト。

### <a name="return-value"></a>戻り値

この `concurrent_priority_queue` オブジェクトへの参照。

## <a name="push"></a>押し付け

同時優先順位キューに要素を追加します。 このメソッドはコンカレンシー セーフです。

```cpp
void push(const value_type& _Elem);

void push(value_type&& _Elem);
```

### <a name="parameters"></a>パラメーター

*_Elem*<br/>
同時優先順位キューに追加する要素。

## <a name="size"></a>幅

同時優先順位キュー内の要素の数を返します。 このメソッドはコンカレンシー セーフです。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

この `concurrent_priority_queue` オブジェクト内の要素の数。

### <a name="remarks"></a>コメント

返されるサイズには、関数 `push`の呼び出しによって追加されたすべての要素が含まれることが保証されます。 ただし、保留中の同時操作の結果が反映されない場合があります。

## <a name="swap"></a>フォト

2つの同時優先順位キューの内容を交換します。 このメソッドはコンカレンシー セーフではありません。

```cpp
void swap(concurrent_priority_queue& _Queue);
```

### <a name="parameters"></a>パラメーター

*_Queue*<br/>
コンテンツの交換先の `concurrent_priority_queue` オブジェクト。

## <a name="try_pop"></a>try_pop

キューが空でない場合は、キューから最も優先順位の高い要素を削除して返します。 このメソッドはコンカレンシー セーフです。

```cpp
bool try_pop(reference _Elem);
```

### <a name="parameters"></a>パラメーター

*_Elem*<br/>
キューが空でない場合、最も優先度の高い要素が設定される変数への参照。

### <a name="return-value"></a>戻り値

値がポップされた場合は**true** 、それ以外の場合は**false** 。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[並列コンテナーと並列オブジェクト](../../../parallel/concrt/parallel-containers-and-objects.md)
