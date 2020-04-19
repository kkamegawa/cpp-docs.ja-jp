---
title: concurrent_queue クラス
ms.date: 11/04/2016
f1_keywords:
- concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::concurrent_queue
- CONCURRENT_QUEUE/concurrency::concurrent_queue::clear
- CONCURRENT_QUEUE/concurrency::concurrent_queue::empty
- CONCURRENT_QUEUE/concurrency::concurrent_queue::get_allocator
- CONCURRENT_QUEUE/concurrency::concurrent_queue::push
- CONCURRENT_QUEUE/concurrency::concurrent_queue::try_pop
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_begin
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_end
- CONCURRENT_QUEUE/concurrency::concurrent_queue::unsafe_size
helpviewer_keywords:
- concurrent_queue class
ms.assetid: c2218996-d0ea-40e9-b002-e9a15b085f51
ms.openlocfilehash: 4e913af40b2218da5699da2659ec2e9189e32994
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143199"
---
# <a name="concurrent_queue-class"></a>concurrent_queue クラス

`concurrent_queue` クラスは、キューの要素に先入れ先出し方式でアクセスできるようにするシーケンス コンテナー クラスです。 これを使用すると、`push`、`try_pop` などの特定のコンカレンシー セーフな操作を実行できます。 ここでは、同時実行セーフとは、ポインターまたは反復子が常に有効であることを意味します。 これは、要素の初期化、または特定のトラバーサルの順序の保証ではありません。

## <a name="syntax"></a>構文

```cpp
template<typename T, class _Ax>
class concurrent_queue: public ::Concurrency::details::_Concurrent_queue_base_v4;
```

### <a name="parameters"></a>パラメーター

*T*<br/>
キューに格納される要素のデータ型。

*_Ax*<br/>
この同時実行キューのメモリの割り当てと解放に関する詳細をカプセル化する、格納されているアロケーターオブジェクトを表す型。 この引数は省略可能であり、既定値は `allocator<T>` です。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

|Name|説明|
|----------|-----------------|
|`allocator_type`|同時実行キューのアロケータークラスを表す型。|
|`const_iterator`|同時実行キュー内の要素に対する非スレッドセーフ `const` 反復子を表す型。|
|`const_reference`|`const` 操作の読み取りと実行のために、同時実行キューに格納されている `const` 要素への参照を提供する型。|
|`difference_type`|同時実行キュー内の2つの要素間の符号付き距離を提供する型。|
|`iterator`|同時実行キュー内の要素に対するスレッドセーフではない反復子を表す型。|
|`reference`|同時実行キューに格納されている要素への参照を提供する型。|
|`size_type`|同時実行キュー内の要素の数をカウントする型。|
|`value_type`|同時実行キューに格納されているデータ型を表す型。|

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[concurrent_queue](#ctor)|オーバーロードされます。 同時実行キューを構築します。|
|[~ concurrent_queue デストラクター](#dtor)|同時実行キューを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[オフ](#clear)|同時実行キューをクリアし、現在エンキューされている要素を破棄します。 このメソッドはコンカレンシー セーフではありません。|
|[empty](#empty)|このメソッドが呼び出された時点で同時実行キューが空かどうかをテストします。 このメソッドはコンカレンシー セーフです。|
|[get_allocator](#get_allocator)|同時実行キューの構築に使用されるアロケーターのコピーを返します。 このメソッドはコンカレンシー セーフです。|
|[push](#push)|オーバーロードされます。 同時実行キューの末尾に項目をエンキューします。 このメソッドはコンカレンシー セーフです。|
|[try_pop](#try_pop)|デキューが使用可能な場合は、キューから項目を取得します。 このメソッドはコンカレンシー セーフです。|
|[unsafe_begin](#unsafe_begin)|オーバーロードされます。 同時実行キューの先頭に `iterator` または `const_iterator` 型の反復子を返します。 このメソッドはコンカレンシー セーフではありません。|
|[unsafe_end](#unsafe_end)|オーバーロードされます。 同時実行キューの末尾に `iterator` または `const_iterator` 型の反復子を返します。 このメソッドはコンカレンシー セーフではありません。|
|[unsafe_size](#unsafe_size)|キュー内の項目の数を返します。 このメソッドはコンカレンシー セーフではありません。|

## <a name="remarks"></a>コメント

詳細については、「[並列コンテナーとオブジェクト](../../../parallel/concrt/parallel-containers-and-objects.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`concurrent_queue`

## <a name="requirements"></a>要件

**ヘッダー:** concurrent_queue

**名前空間:** concurrency

## <a name="clear"></a>クリア

同時実行キューをクリアし、現在エンキューされている要素を破棄します。 このメソッドはコンカレンシー セーフではありません。

```cpp
void clear();
```

## <a name="ctor"></a>concurrent_queue

同時実行キューを構築します。

```cpp
explicit concurrent_queue(
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    const concurrent_queue& _OtherQ,
    const allocator_type& _Al = allocator_type());

concurrent_queue(
    concurrent_queue&& _OtherQ,
    const allocator_type& _Al = allocator_type());

template<typename _InputIterator>
concurrent_queue(_InputIterator _Begin,
    _InputIterator _End);
```

### <a name="parameters"></a>パラメーター

*_InputIterator*<br/>
値の範囲を指定する入力反復子の型。

*_Al*<br/>
このオブジェクトに対して使用するアロケーター クラス。

*_OtherQ*<br/>
要素のコピー元または移動元の `concurrent_queue` オブジェクト。

*_Begin*<br/>
コピーする要素範囲内の最初の要素の位置。

*_End*<br/>
コピーする要素範囲を超える最初の要素の位置。

### <a name="remarks"></a>コメント

すべてのコンストラクターは、アロケーターオブジェクト `_Al` を格納し、キューを初期化します。

最初のコンストラクターは、空の初期キューを指定し、使用するアロケーターの型を明示的に指定します。

2番目のコンストラクターは `_OtherQ`同時実行キューのコピーを指定します。

3番目のコンストラクターは `_OtherQ`同時実行キューの移動を指定します。

4番目のコンストラクターは、反復子の範囲 [`_Begin`、`_End`) によって指定された値を指定します。

## <a name="dtor"></a>~ concurrent_queue

同時実行キューを破棄します。

```cpp
~concurrent_queue();
```

## <a name="empty"></a>指定

このメソッドが呼び出された時点で同時実行キューが空かどうかをテストします。 このメソッドはコンカレンシー セーフです。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

先ほど見た時点で、同時実行キューが空だった場合は**true** 、それ以外の場合は**false** 。

### <a name="remarks"></a>コメント

このメソッドは `push`、`try_pop`、および `empty`メソッドの呼び出しに関しては同時実行セーフですが、呼び出し元のスレッドによって検査されたときに返される値が間違っている可能性があります。

## <a name="get_allocator"></a>get_allocator

同時実行キューの構築に使用されるアロケーターのコピーを返します。 このメソッドはコンカレンシー セーフです。

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>戻り値

同時実行キューを構築するために使用されるアロケーターのコピー。

## <a name="push"></a>押し付け

同時実行キューの末尾に項目をエンキューします。 このメソッドはコンカレンシー セーフです。

```cpp
void push(const T& _Src);

void push(T&& _Src);
```

### <a name="parameters"></a>パラメーター

*_Src*<br/>
キューに追加する項目。

### <a name="remarks"></a>コメント

`push` は、`push`、`try_pop`、および `empty`メソッドの呼び出しに関して、同時実行セーフです。

## <a name="try_pop"></a>try_pop

デキューが使用可能な場合は、キューから項目を取得します。 このメソッドはコンカレンシー セーフです。

```cpp
bool try_pop(T& _Dest);
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
デキューされた項目を格納する場所への参照。

### <a name="return-value"></a>戻り値

項目が正常にデキューされた場合は**true** 。それ以外の場合は**false** 。

### <a name="remarks"></a>コメント

項目が正常にデキューされた場合、パラメーター `_Dest` はデキューされた値を受け取り、キューに保持されている元の値は破棄され、この関数は**true**を返します。 デキューする項目がなかった場合、この関数はブロックせずに `false` を返し、`_Dest` パラメーターの内容は未定義になります。

`try_pop` は、`push`、`try_pop`、および `empty`メソッドの呼び出しに関して、同時実行セーフです。

## <a name="unsafe_begin"></a>unsafe_begin

同時実行キューの先頭に `iterator` または `const_iterator` 型の反復子を返します。 このメソッドはコンカレンシー セーフではありません。

```cpp
iterator unsafe_begin();

const_iterator unsafe_begin() const;
```

### <a name="return-value"></a>戻り値

同時実行キューオブジェクトの先頭に `iterator` または `const_iterator` 型の反復子。

### <a name="remarks"></a>コメント

`concurrent_queue` クラスの反復子は、低速であるため、主にデバッグを目的としています。反復は、他のキュー操作に対する同時実行セーフではありません。

## <a name="unsafe_end"></a>unsafe_end

同時実行キューの末尾に `iterator` または `const_iterator` 型の反復子を返します。 このメソッドはコンカレンシー セーフではありません。

```cpp
iterator unsafe_end();

const_iterator unsafe_end() const;
```

### <a name="return-value"></a>戻り値

同時実行キューの末尾に `iterator` または `const_iterator` 型の反復子。

### <a name="remarks"></a>コメント

`concurrent_queue` クラスの反復子は、低速であるため、主にデバッグを目的としています。反復は、他のキュー操作に対する同時実行セーフではありません。

## <a name="unsafe_size"></a>unsafe_size

キュー内の項目の数を返します。 このメソッドはコンカレンシー セーフではありません。

```cpp
size_type unsafe_size() const;
```

### <a name="return-value"></a>戻り値

同時実行キューのサイズ。

### <a name="remarks"></a>コメント

`unsafe_size` は同時実行セーフではなく、メソッド `push`、`try_pop`、および `empty`の呼び出しと同時に呼び出された場合、正しくない結果が生成される可能性があります。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)
