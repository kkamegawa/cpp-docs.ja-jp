---
title: concurrent_unordered_map クラス
ms.date: 11/04/2016
f1_keywords:
- concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::concurrent_unordered_map
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::at
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::hash_function
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::insert
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::key_eq
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::swap
- CONCURRENT_UNORDERED_MAP/concurrency::concurrent_unordered_map::unsafe_erase
helpviewer_keywords:
- concurrent_unordered_map class
ms.assetid: b2d879dd-87ef-4af9-a266-a5443fd538b8
ms.openlocfilehash: 50868d020224e7bade9766f7307bfcc46ce4be47
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657592"
---
# <a name="concurrentunorderedmap-class"></a>concurrent_unordered_map クラス

`concurrent_unordered_map` クラスは、`std::pair<const K, _Element_type>` 型要素の可変長シーケンスを制御する同時実行セーフなコンテナーです。 このシーケンスは、同時実行セーフな追加、要素アクセス、反復子アクセス、反復子走査の各操作を実行できるように表されます。

## <a name="syntax"></a>構文

```
template <typename K,
    typename _Element_type,
    typename _Hasher = std::hash<K>,
    typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>
>,
typename key_equality = std::equal_to<K>,
    typename _Allocator_type = std::allocator<std::pair<const K,
    _Element_type>>> class concurrent_unordered_map : public details::_Concurrent_hash<details::_Concurrent_unordered_map_traits<K,
    _Element_type,
details::_Hash_compare<K,
    _Hasher,
key_equality>,
    _Allocator_type,
false>>;
```

#### <a name="parameters"></a>パラメーター

*K*<br/>
キーの型。

*_Element_type*<br/>
マップされた型。

*_Hasher*<br/>
ハッシュ関数のオブジェクト型。 この引数は省略可能であり、既定値は `std::hash<K>` です。

*key_equality*<br/>
等価比較関数のオブジェクト型。 この引数は省略可能であり、既定値は `std::equal_to<K>` です。

*_Allocator_type*<br/>
同時実行順序なしのマップのメモリの割り当てと解放に関する詳細をカプセル化する、格納されたアロケーター オブジェクトを表す型。 この引数は省略可能、既定値は`std::allocator<std::pair<K`、`_Element_type>>`します。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|`allocator_type`|ストレージを管理するためのアロケーターの型です。|
|`const_iterator`|被制御シーケンスの定数反復子の型です。|
|`const_local_iterator`|被制御シーケンスの定数バケット反復子の型です。|
|`const_pointer`|要素への定数ポインターの型です。|
|`const_reference`|要素への定数参照の型です。|
|`difference_type`|2 つの要素間の距離を表す、符号付きの型です。|
|`hasher`|ハッシュ関数の型です。|
|`iterator`|被制御シーケンスの反復子の型です。|
|`key_equal`|比較関数の型です。|
|`key_type`|順序付けキーの型です。|
|`local_iterator`|被制御シーケンスのバケット反復子の型です。|
|`mapped_type`|各キーに関連付けられた、マップされた値の型です。|
|`pointer`|要素へのポインターの型です。|
|`reference`|要素への参照の型です。|
|`size_type`|2 つの要素間の距離を表す、符号なしの型です。|
|`value_type`|要素の型。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[concurrent_unordered_map](#ctor)|オーバーロードされます。 同時実行順序なしのマップを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[at](#at)|オーバーロードされます。 `concurrent_unordered_map` 内の指定されたキー値を持つ要素を検索します。 このメソッドはコンカレンシー セーフです。|
|[hash_function](#hash_function)|格納されているハッシュ関数オブジェクトを取得します。|
|[insert](#insert)|オーバーロードされます。 要素を `concurrent_unordered_map` オブジェクトに追加します。|
|[key_eq](#key_eq)|格納された等価比較関数のオブジェクトを取得します。|
|[swap](#swap)|2 つの `concurrent_unordered_map` オブジェクトのコンテンツを交換します。 このメソッドはコンカレンシー セーフではありません。|
|[unsafe_erase](#unsafe_erase)|オーバーロードされます。 `concurrent_unordered_map` から指定した位置にある要素を削除します。 このメソッドはコンカレンシー セーフではありません。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[operator\[\]](#operator_at)|オーバーロードされます。 指定したキーを持つ要素を検索または挿入します。 このメソッドはコンカレンシー セーフです。|
|[operator=](#operator_eq)|オーバーロードされます。 別の `concurrent_unordered_map` オブジェクトの内容をこのオブジェクトに割り当てます。 このメソッドはコンカレンシー セーフではありません。|

## <a name="remarks"></a>Remarks

詳細については、`concurrent_unordered_map`クラスを参照してください[並列コンテナーとオブジェクト](../../../parallel/concrt/parallel-containers-and-objects.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`_Traits`

`_Concurrent_hash`

`concurrent_unordered_map`

## <a name="requirements"></a>必要条件

**ヘッダー:** concurrent_unordered_map.h

**名前空間:** concurrency

##  <a name="at"></a> で

`concurrent_unordered_map` 内の指定されたキー値を持つ要素を検索します。 このメソッドはコンカレンシー セーフです。

```
mapped_type& at(const key_type& KVal);

const mapped_type& at(const key_type& KVal) const;
```

### <a name="parameters"></a>パラメーター

*KVal*<br/>
検索するキー値。

### <a name="return-value"></a>戻り値

見つかった要素のデータ値への参照。

### <a name="remarks"></a>Remarks

引数のキー値が見つからない場合、この関数は、`out_of_range` クラスのオブジェクトをスローします。

##  <a name="begin"></a> 開始

同時実行コンテナーの最初の要素を指す反復子を返します。 このメソッドはコンカレンシー セーフです。

```
iterator begin();

const_iterator begin() const;
```

### <a name="return-value"></a>戻り値

同時実行コンテナーの最初の要素の反復子。

##  <a name="cbegin"></a> cbegin

同時実行コンテナーの最初の要素を指す定数反復子を返します。 このメソッドはコンカレンシー セーフです。

```
const_iterator cbegin() const;
```

### <a name="return-value"></a>戻り値

同時実行コンテナーの最初の要素に定数反復子。

##  <a name="cend"></a> cend

同時実行コンテナーの最後の要素の次の位置を指す定数反復子を返します。 このメソッドはコンカレンシー セーフです。

```
const_iterator cend() const;
```

### <a name="return-value"></a>戻り値

位置を同時実行コンテナーの最後の要素を指す定数反復子。

##  <a name="clear"></a> オフ

同時実行コンテナー内のすべての要素を消去します。 この関数は、同時実行セーフではありません。

```
void clear();
```

##  <a name="ctor"></a> concurrent_unordered_map

同時実行順序なしのマップを構築します。

```
explicit concurrent_unordered_map(
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const allocator_type& _Allocator);

template <typename _Iterator>
concurrent_unordered_map(_Iterator _Begin,
    _Iterator _End,
    size_type _Number_of_buckets = 8,
    const hasher& _Hasher = hasher(),
    const key_equal& key_equality = key_equal(),
    const allocator_type& _Allocator = allocator_type());

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap);

concurrent_unordered_map(
    const concurrent_unordered_map& _Umap,
    const allocator_type& _Allocator);

concurrent_unordered_map(
    concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>パラメーター

*_Iterator*<br/>
入力反復子の型。

*_Number_of_buckets*<br/>
この順序付けられていないマップ バケットの初期数。

*_Hasher*<br/>
この順序なしのマップのハッシュ関数。

*key_equality*<br/>
この順序付けられていないマップの等値比較関数。

*_Allocator*<br/>
この順序付けられていないマップのアロケーター。

*開始 (_b)*<br/>
コピーする要素範囲内の最初の要素の位置。

*(_E)*<br/>
コピーする要素範囲を超える最初の要素の位置。

*_Umap*<br/>
要素のコピー元または移動元の `concurrent_unordered_map` オブジェクト。

### <a name="remarks"></a>Remarks

すべてのコンス トラクターは、アロケーター オブジェクトを格納`_Allocator`と順序付けられていないマップを初期化します。

最初のコンス トラクター空の初期マップを指定しますを明示的に指定します、バケット数ハッシュ関数、等しいかどうかの関数とアロケーターの型を使用します。

2 番目のコンス トラクターでは、順序なしのマップのアロケーターを指定します。

3 番目のコンス トラクターは、反復子の範囲で指定された値を指定する [ `_Begin`、 `_End`)。

4 番目と 5 番目のコンス トラクターは、同時実行の順序なしのマップのコピーを指定します。`_Umap`します。

最後のコンス トラクターは、同時実行の順序なしのマップの移動を指定`_Umap`します。

##  <a name="count"></a> カウント

指定したキーに一致する要素の数をカウントします。 この関数は、同時実行セーフです。

```
size_type count(const key_type& KVal) const;
```

### <a name="parameters"></a>パラメーター

*KVal*<br/>
検索対象のキー。

### <a name="return-value"></a>戻り値

コンテナーにキーが表示される回数の合計を回数します。

##  <a name="empty"></a> 空

要素が存在しないかどうかをテストします。 このメソッドはコンカレンシー セーフです。

```
bool empty() const;
```

### <a name="return-value"></a>戻り値

**true**同時実行コンテナーが空の場合**false**それ以外の場合。

### <a name="remarks"></a>Remarks

同時実行の挿入がある場合、同時実行コンテナーが空かどうかを戻り値は読み取り専用でも前に、この関数の呼び出し直後後変更可能性があります。

##  <a name="end"></a> 終わり

同時実行コンテナーの最後の要素の次の位置を指す反復子を返します。 このメソッドはコンカレンシー セーフです。

```
iterator end();

const_iterator end() const;
```

### <a name="return-value"></a>戻り値

同時実行コンテナーの最後の要素を指す反復子。

##  <a name="equal_range"></a> equal_range

指定したキーに一致する範囲を検索します。 この関数は、同時実行セーフです。

```
std::pair<iterator,
    iterator> equal_range(
    const key_type& KVal);

std::pair<const_iterator,
    const_iterator> equal_range(
    const key_type& KVal) const;
```

### <a name="parameters"></a>パラメーター

*KVal*<br/>
検索するキー値。

### <a name="return-value"></a>戻り値

A[ペア](../../../standard-library/pair-structure.md)最初の要素は、反復子を先頭に、2 番目の要素が、範囲の末尾に反復子です。

### <a name="remarks"></a>Remarks

同時実行の挿入を begin 反復子の後と終わりの反復子の前に挿入される追加のキーが発生することができます。

##  <a name="find"></a> 検索

指定したキーに一致する要素を検索します。 この関数は、同時実行セーフです。

```
iterator find(const key_type& KVal);

const_iterator find(const key_type& KVal) const;
```

### <a name="parameters"></a>パラメーター

*KVal*<br/>
検索するキー値。

### <a name="return-value"></a>戻り値

指定したキーに一致する最初の要素の位置を指す反復子または反復子`end()`そのような要素が存在しない場合。

##  <a name="get_allocator"></a> get_allocator

この同時実行コンテナーの格納されたアロケーター オブジェクトを返します。 このメソッドはコンカレンシー セーフです。

```
allocator_type get_allocator() const;
```

### <a name="return-value"></a>戻り値

この同時実行コンテナーの格納されたアロケーター オブジェクト。

##  <a name="hash_function"></a> hash_function

格納されているハッシュ関数オブジェクトを取得します。

```
hasher hash_function() const;
```

### <a name="return-value"></a>戻り値

格納されているハッシュ関数オブジェクト。

##  <a name="insert"></a> 挿入します。

要素を `concurrent_unordered_map` オブジェクトに追加します。

```
std::pair<iterator,
    bool> insert(
    const value_type& value);

iterator insert(
    const_iterator _Where,
    const value_type& value);

template<class _Iterator>
void insert(_Iterator first,
    _Iterator last);

template<class V>
std::pair<iterator,
    bool> insert(
    V&& value);

template<class V>
typename std::enable_if<!std::is_same<const_iterator,
    typename std::remove_reference<V>::type>::value,
    iterator>::type insert(
    const_iterator _Where,
    V&& value);
```

### <a name="parameters"></a>パラメーター

*_Iterator*<br/>
反復子の型を挿入するために使用します。

*V*<br/>
マップに挿入された値の型。

*value*<br/>
挿入する値。

*_Where*<br/>
挿入ポイントを検索する開始位置。

*first*<br/>
挿入する範囲の先頭。

*last*<br/>
挿入する範囲の終了。

### <a name="return-value"></a>戻り値

反復子とブール値を含むペア。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

最初のメンバー関数は、要素 X がのと同じ順序付けキーを持つが、シーケンス内に存在するかどうかを決定します。`value`します。 場合は、このような要素 X を作成して初期化で`value`します。 関数は、反復子を決定し、 `where` X を指定します。挿入が発生したかどうか、関数を返します`std::pair(where, true)`します。 返しますそれ以外の場合、`std::pair(where, false)`します。

2 番目のメンバー関数は、挿入を返します ( `value`) を使用して、`_Where`として挿入ポイントを検索する被制御シーケンス内の開始場所。

3 番目のメンバー関数は、範囲からの要素の値のシーケンスを挿入 [ `first`、 `last`)。

最後の 2 つのメンバー関数の動作は同じことを除いて、最初の 2 つ`value`挿入された値を構築するために使用します。

##  <a name="key_eq"></a> key_eq

格納された等価比較関数のオブジェクトを取得します。

```
key_equal key_eq() const;
```

### <a name="return-value"></a>戻り値

格納された等価比較関数のオブジェクト。

##  <a name="load_factor"></a> load_factor

計算し、コンテナーの現在のテーブル占有率を返します。 占有率は、バケットの数で割った値コンテナー内の要素の数です。

```
float load_factor() const;
```

### <a name="return-value"></a>戻り値

コンテナーのテーブル占有率。

##  <a name="max_load_factor"></a> max_load_factor

取得またはコンテナーの最大テーブル占有率を設定します。 最大テーブル占有率は要素の最大数、コンテナーの内部テーブルを拡張する前に、バケットにすることができます。

```
float max_load_factor() const;

void max_load_factor(float _Newmax);
```

### <a name="parameters"></a>パラメーター

`_Newmax`

### <a name="return-value"></a>戻り値

1 つ目のメンバー関数は、格納されている最大テーブル占有率を返します。 2 番目のメンバー関数は、値は返されませんがスローされます、 [out_of_range](../../../standard-library/out-of-range-class.md)指定したテーブル占有率が有効でない場合は例外.

##  <a name="max_size"></a> max_size

アロケーターによって決定される、同時実行コンテナーの最大サイズを返します。 このメソッドはコンカレンシー セーフです。

```
size_type max_size() const;
```

### <a name="return-value"></a>戻り値

この同時実行コンテナーに挿入できる要素の最大数。

### <a name="remarks"></a>Remarks

この上限値実際にどのようなコンテナー実際に保持できるよりも高い場合があります。

##  <a name="operator_at"></a> operator[]

指定したキーを持つ要素を検索または挿入します。 このメソッドはコンカレンシー セーフです。

```
mapped_type& operator[](const key_type& kval);

mapped_type& operator[](key_type&& kval);
```

### <a name="parameters"></a>パラメーター

*KVal*<br/>
キーの値

検索または挿入します。

### <a name="return-value"></a>戻り値

見つからないか、または挿入された要素のデータ値への参照。

### <a name="remarks"></a>Remarks

引数のキー値が見つからない場合は、データ型の既定値と一緒に挿入されます。

`operator[]` マップに要素を挿入に使用することがあります`m`を使用して`m[key] = DataValue;`ここで、`DataValue`の値である、`mapped_type`のキーの値を持つ要素の`key`します。

`operator[]` を使用して要素を挿入した場合、返される参照では、挿入によって既存の要素が変更される、または新しい要素が作成されるかどうかは指示されません。 メンバー関数は、`find`と[挿入](#insert)指定したキーを持つ要素が既に、挿入前に存在するかどうかを判断するために使用できます。

##  <a name="operator_eq"></a> 演算子 =

別の `concurrent_unordered_map` オブジェクトの内容をこのオブジェクトに割り当てます。 このメソッドはコンカレンシー セーフではありません。

```
concurrent_unordered_map& operator= (const concurrent_unordered_map& _Umap);

concurrent_unordered_map& operator= (concurrent_unordered_map&& _Umap);
```

### <a name="parameters"></a>パラメーター

*_Umap*<br/>
ソース `concurrent_unordered_map` オブジェクト。

### <a name="return-value"></a>戻り値

この `concurrent_unordered_map` オブジェクトへの参照。

### <a name="remarks"></a>Remarks

同時実行ベクターの場合は、既存の要素を消去した後`operator=`の内容を移動またはコピー`_Umap`同時実行ベクターにします。

##  <a name="rehash"></a> 流用しています

ハッシュ テーブルをリビルドします。

```
void rehash(size_type _Buckets);
```

### <a name="parameters"></a>パラメーター

*_Buckets*<br/>
必要なバケット数。

### <a name="remarks"></a>Remarks

メンバー関数は、バケット数を `_Buckets` 以上に変更し、必要に応じて、ハッシュ テーブルをリビルドします。 バケット数は 2 の累乗である必要があります。 場合いない 2 の累乗で、2 の累乗に切り上げられますされます。

スローされます、 [out_of_range](../../../standard-library/out-of-range-class.md)例外のバケットの数が有効でない場合 (0 またはバケットの最大数より大きい)。

##  <a name="size"></a> サイズ

この同時実行コンテナーの要素の数を返します。 このメソッドはコンカレンシー セーフです。

```
size_type size() const;
```

### <a name="return-value"></a>戻り値

コンテナー内の項目の数。

### <a name="remarks"></a>Remarks

同時実行の挿入がある場合は、同時実行コンテナー内の要素の数は、戻り値は読み取り専用でも前に、この関数の呼び出し直後後変更できます。

##  <a name="swap"></a> スワップ

2 つの `concurrent_unordered_map` オブジェクトのコンテンツを交換します。 このメソッドはコンカレンシー セーフではありません。

```
void swap(concurrent_unordered_map& _Umap);
```

### <a name="parameters"></a>パラメーター

*_Umap*<br/>
`concurrent_unordered_map`交換するオブジェクト。

##  <a name="unsafe_begin"></a> unsafe_begin

特定のバケットのこのコンテナーの最初の要素に反復子を返します。

```
local_iterator unsafe_begin(size_type _Bucket);

const_local_iterator unsafe_begin(size_type _Bucket) const;
```

### <a name="parameters"></a>パラメーター

*_ バケット*<br/>
バケットのインデックス。

### <a name="return-value"></a>戻り値

バケットの先頭を指す反復子。

##  <a name="unsafe_bucket"></a> unsafe_bucket

このコンテナー内に特定のキーがマップされるバケットのインデックスを返します。

```
size_type unsafe_bucket(const key_type& KVal) const;
```

### <a name="parameters"></a>パラメーター

*KVal*<br/>
検索対象の要素のキー。

### <a name="return-value"></a>戻り値

このコンテナー内のキーのバケットのインデックス。

##  <a name="unsafe_bucket_count"></a> unsafe_bucket_count

このコンテナー内の現在のバケット数を返します。

```
size_type unsafe_bucket_count() const;
```

### <a name="return-value"></a>戻り値

このコンテナー内のバケットの現在数。

##  <a name="unsafe_bucket_size"></a> unsafe_bucket_size

このコンテナーの特定のバケット内の項目の数を返します。

```
size_type unsafe_bucket_size(size_type _Bucket);
```

### <a name="parameters"></a>パラメーター

*_ バケット*<br/>
検索するバケット。

### <a name="return-value"></a>戻り値

このコンテナー内のバケットの現在数。

##  <a name="unsafe_cbegin"></a> unsafe_cbegin

特定のバケットのこのコンテナーの最初の要素に反復子を返します。

```
const_local_iterator unsafe_cbegin(size_type _Bucket) const;
```

### <a name="parameters"></a>パラメーター

*_ バケット*<br/>
バケットのインデックス。

### <a name="return-value"></a>戻り値

バケットの先頭を指す反復子。

##  <a name="unsafe_cend"></a> unsafe_cend

位置を特定のバケット内の最後の要素を指す反復子を返します。

```
const_local_iterator unsafe_cend(size_type _Bucket) const;
```

### <a name="parameters"></a>パラメーター

*_ バケット*<br/>
バケットのインデックス。

### <a name="return-value"></a>戻り値

バケットの先頭を指す反復子。

##  <a name="unsafe_end"></a> unsafe_end

特定のバケットのこのコンテナーの最後の要素に反復子を返します。

```
local_iterator unsafe_end(size_type _Bucket);

const_local_iterator unsafe_end(size_type _Bucket) const;
```

### <a name="parameters"></a>パラメーター

*_ バケット*<br/>
バケットのインデックス。

### <a name="return-value"></a>戻り値

バケットの末尾を指す反復子。

##  <a name="unsafe_erase"></a> unsafe_erase

`concurrent_unordered_map` から指定した位置にある要素を削除します。 このメソッドはコンカレンシー セーフではありません。

```
iterator unsafe_erase(
    const_iterator _Where);

iterator unsafe_erase(
    const_iterator _Begin,
    const_iterator _End);

size_type unsafe_erase(
    const key_type& KVal);
```

### <a name="parameters"></a>パラメーター

*_Where*<br/>
消去する反復子の位置。

*開始 (_b)*<br/>
消去する要素の範囲の最初の要素の位置。

*(_E)*<br/>
消去する要素の範囲を超える先頭の要素の位置。

*KVal*<br/>
消去するキー値。

### <a name="return-value"></a>戻り値

最初の 2 つのメンバー関数は、削除された要素の後の最初の残存要素を指定する反復子を返します。このような要素が存在しない場合は、`concurrent_unordered_map::end`() が返されます。 3 つ目のメンバー関数は削除する要素の数を返します。

### <a name="remarks"></a>Remarks

最初のメンバー関数が指す被制御シーケンスの要素を削除する`_Where`します。 2 番目のメンバー関数は、範囲内の要素を削除する [ `_Begin`、 `_End`)。

3 番目のメンバー関数は、区切られた範囲内の要素を削除する`concurrent_unordered_map::equal_range`(KVal)。

##  <a name="unsafe_max_bucket_count"></a> unsafe_max_bucket_count

このコンテナー内のバケットの最大数を返します。

```
size_type unsafe_max_bucket_count() const;
```

### <a name="return-value"></a>戻り値

このコンテナー内のバケットの最大数。

## <a name="see-also"></a>関連項目

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[並列コンテナーと並列オブジェクト](../../../parallel/concrt/parallel-containers-and-objects.md)

