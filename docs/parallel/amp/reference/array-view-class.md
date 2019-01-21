---
title: array_view クラス
ms.date: 11/04/2016
f1_keywords:
- array_view
- AMP/array_view
- AMP/Concurrency::array_view::array_view
- AMP/Concurrency::array_view::copy_to
- AMP/Concurrency::array_view::data
- AMP/Concurrency::array_view::discard_data
- AMP/Concurrency::array_view::get_extent
- AMP/Concurrency::array_view::get_ref
- AMP/Concurrency::array_view::get_source_accelerator_view
- AMP/Concurrency::array_view::refresh
- AMP/Concurrency::array_view::reinterpret_as
- AMP/Concurrency::array_view::section
- AMP/Concurrency::array_view::synchronize
- AMP/Concurrency::array_view::synchronize_async
- AMP/Concurrency::array_view::synchronize_to
- AMP/Concurrency::array_view::synchronize_to_async
- AMP/Concurrency::array_view::view_as
- AMP/Concurrency::array_view::rank
- AMP/Concurrency::array_view::extent
- AMP/Concurrency::array_view::source_accelerator_view
- AMP/Concurrency::array_view::value_type
helpviewer_keywords:
- array_view class
ms.assetid: 7e7ec9bc-05a2-4372-b05d-752b50006c5a
ms.openlocfilehash: d33c54e82e9bc228b97bff4802c9231a98f51033
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657488"
---
# <a name="arrayview-class"></a>array_view クラス

別のコンテナーに保持されるデータの N 次元のビューを表します。

## <a name="syntax"></a>構文

```
template <
    typename value_type,
    int _Rank = 1
>
class array_view : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;

template <
    typename value_type,
    int _Rank
>
class array_view<const value_type, _Rank> : public _Array_view_base<_Rank, sizeof(value_type)/sizeof(int)>;
```

#### <a name="parameters"></a>パラメーター

*value_type*<br/>
`array_view` オブジェクトの要素のデータ型。

*_Rank*<br/>
`array_view` オブジェクトのランク。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[array_view コンス トラクター](#ctor)|`array_view` クラスの新しいインスタンスを初期化します。 `array<T,N>` の既定のコンストラクターがありません。 すべてのコンストラクターは、CPU 上のみで実行されるように制限されており、Direct3D ターゲット上で実行することはできません。|
|[~ array_view デストラクター](#ctor)|`array_view` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[copy_to](#copy_to)|`array_view` を呼び出して `copy(*this, dest)` オブジェクトの内容を指定されたコピー先にコピーします。|
|[data](#data)|`array_view` の生データへのポインターを返します。|
|[discard_data](#discard_data)|このビューの基となる現在のデータを破棄します。|
|[get_extent](#get_extent)|array_view オブジェクトの範囲オブジェクトを返します。|
|[get_ref](#get_ref)|インデックス付けされた要素への参照を返します。|
|[get_source_accelerator_view](#get_source_accelerator_view)|返します、 [accelerator_view](accelerator-view-class.md)場所のデータ ソース、`array_view`が配置されています。|
|[refresh](#refresh)|バインドされたメモリが `array_view` インターフェイスの外部で変更されたことを `array_view` オブジェクトに通知します。 このメソッドの呼び出しによって、すべてのキャッシュされた情報が表示されます。|
|[reinterpret_as](#reinterpret_as)|`array_view` オブジェクトのすべての要素を含む 1 次元配列を返します。|
|[section](#section)|指定された原点に `array_view` オブジェクトのサブセクションを返し、これは必要に応じて範囲が指定されます。|
|[synchronize](#synchronize)|`array_view` オブジェクトへの変更をそのソース データに同期して戻します。|
|[synchronize_async](#synchronize_async)|非同期的に行われた変更を同期化、`array_view`そのソース データへのオブジェクト。|
|[synchronize_to](#synchronize_to)|加えられた変更と同期、`array_view`を指定したオブジェクト[accelerator_view](accelerator-view-class.md)します。|
|[synchronize_to_async](#synchronize_to_async)|非同期的に行われた変更を同期化、`array_view`を指定したオブジェクト[accelerator_view](accelerator-view-class.md)します。|
|[view_as](#view_as)|この `array_view` を使用して異なるランクの `array_view` オブジェクトを生成します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[演算子 ()](#operator_call)|パラメーターによって指定された要素の値を返します。|
|[operator\[\]](#operator_at)|パラメーターで指定された要素を返します。|
|[operator=](#operator_eq)|指定された `array_view` オブジェクトの内容をこのオブジェクトにコピーします。|

### <a name="public-constants"></a>パブリック定数

|名前|説明|
|----------|-----------------|
|[rank 定数](#rank)|`array_view` オブジェクトのランクを格納します。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[extent](#extent)|`extent` オブジェクトの形状を定義する `array_view` オブジェクトを取得します。|
|[source_accelerator_view](#source_accelerator_view)|取得、 [accelerator_view](accelerator-view-class.md)場所のデータ ソース、`array_view`が配置されています。|
|[value_type](#value_type)|`array_view` の値型およびバインド配列。|

## <a name="remarks"></a>Remarks

`array_view`クラスに含まれているデータにビューを表します、[配列](array-class.md)オブジェクトまたはのサブセクションを`array`オブジェクト。

ソース データが格納されている (ローカル)、または別のアクセラレータまたはコヒーレンス ドメイン (リモート) 上の、`array_view` オブジェクトにアクセスできます。 オブジェクトにリモートにアクセスすると、ビューは必要に応じてコピーされ、キャッシュされます。 自動キャッシュの効果を除いて、`array_view` オブジェクトには `array` オブジェクトと同様のパフォーマンス プロファイルがあります。 ビューを使用してデータにアクセスする場合、パフォーマンスがわずかに低下します。

リモートでの使用には次の 3 つの方法があります。

- ビューをシステム メモリのポインターが渡される、 [parallel_for_each](../../../parallel/concrt/reference/concurrency-namespace-functions.md#parallel_for_each)アクセラレータを呼び出すし、アクセラレータでアクセスします。

- アクセラレータにある配列へのビューは、別のアクセラレータへの `parallel_for_each` 呼び出しによって渡され、そこでアクセスされます。

- アクセラレータにある配列へのビューは CPU 上でアクセスされます。

これらのシナリオのいずれかで、参照されたビューは、リモートの場所へのランタイムによってコピーされ、`array_view` オブジェクトへの呼び出しによって変更される場合は、ローカルの場所へコピーして戻されます。 ランタイムは、変更をコピーして戻す処理を最適化する場合、変更された要素のみをコピーする場合、または変更されない部分もコピーする場合があります。 1 つのデータ ソースで `array_view` オブジェクトが重複すると、リモートの場所での参照整合性の維持が保証されません。

同じデータ ソースに対するマルチスレッド アクセスを同期する必要があります。

ランタイムは `array_view` オブジェクトのデータのキャッシュに関連して次の内容を保証します。

- プログラムの順序での `array` オブジェクトと `array_view` オブジェクトへのすべての完全同期アクセスは、逐次事前発生リレーションシップに従います。

- 単一の `array_view` オブジェクトの同じアクセラレータ上で重複する `array` オブジェクトへのすべての完全同期アクセスは、`array` オブジェクトを使用してエイリアス化されます。 これらは、プログラムの順序に従う合計事前発生リレーションシップを引き起こします。 キャッシュはありません。 `array_view` オブジェクトが異なるアクセラレータで実行されている場合、アクセスの順序は未定義で、競合状態を作成します。

システム メモリのポインターを使用して `array_view` オブジェクトを作成する場合、`array_view` ポインターのみを使用してビュー `array_view` オブジェクトを変更する必要があります。 また、`refresh()` オブジェクトを使用せずに、基になるネイティブ メモリが直接変更される場合は、システム ポインターに添付されている `array_view` オブジェクトの 1 つに `array_view` を呼び出す必要があります。

どちらの操作も、基になるネイティブ メモリが変更されていること、およびアクセラレータ内にあるコピーが古くなっていることを `array_view` オブジェクトに通知します。 これらのガイドラインに従う場合、ポインター ベースのビューはデータ並列配列のビューに提供されるビューと同じです。

## <a name="inheritance-hierarchy"></a>継承階層

`_Array_view_shape`

`_Array_view_base`

`array_view`

## <a name="requirements"></a>必要条件

**ヘッダー:** amp.h

**Namespace:** コンカレンシー

##  <a name="dtor"></a> ~ array_view

`array_view` オブジェクトを破棄します。

```
~array_view()restrict(amp,cpu);
```

##  <a name="ctor"></a> array_view

`array_view` クラスの新しいインスタンスを初期化します。

```
array_view(
    array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view& _Other)restrict(amp,cpu);

explicit array_view(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    _Container& _Src) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    int _E0,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    _Container& _Src) restrict(cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2) __CPU_ONLY;

template <
    typename _Container
>
explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _Container& _Src);

explicit array_view(
    int _E0,
    _In_ value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    _In_ value_type* _Src)restrict(amp,cpu);

explicit array_view(
    int _E0,
    int _E1,
    int _E2,
    _In_ value_type* _Src)restrict(amp,cpu);

array_view(
    const array<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<value_type, _Rank>& _Src)restrict(amp,cpu);

array_view(
    const array_view<const value_type, _Rank>& _Src)restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const _Container& _Src) restrict(cpu);

template <
    typename _Container
>
explicit array_view(
    const _Container& _Src,
    typename std::enable_if<details::_Is_container<_Container>::type::value, void **>::type = 0) restrict(cpu);

array_view(
    const Concurrency::extent<_Rank>& _Extent,
    const value_type* _Src)restrict(amp,cpu);

template <
    typename _Arr_type,
    int _Size
>
explicit array_view(
    const _In_ _Arr_type (& _Src) [_Size]) restrict(amp,cpu);

template <
    typename _Container
>
array_view(
    int _E0,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    const _Container& _Src);

template <
    typename _Container
>
array_view(
    int _E0,
    int _E1,
    int _E2,
    const _Container& _Src);

array_view(
    int _E0,
    const value_type* _Src)restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    const value_type* _Src) restrict(amp,cpu);

array_view(
    int _E0,
    int _E1,
    int _E2,
    const value_type* _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Arr_type*<br/>
データが提供される C スタイルの配列の要素型。

*_Container*<br/>
`data()` メンバーおよび `size()` メンバーをサポートする線形コンテナーを指定する必要があるテンプレート引数。

*_E0*<br/>
このセクションの範囲の最上位のコンポーネント。

*_E1*<br/>
このセクションの範囲の最上位の次のコンポーネント。

*_E2*<br/>
このセクションの範囲の最下位のコンポーネント。

*_Extent*<br/>
この `array_view` の各次元の範囲。

*_Other*<br/>
新しい `array_view<T,N>` の初期化に使用する `array_view` 型のオブジェクト。

*サイズ) (_s*<br/>
データが提供される C スタイルの配列のサイズ。

*_Src*<br/>
新しい配列にコピーされるソース データへのポインター。

##  <a name="copy_to"></a> copy_to

内容をコピー、`array_view`オブジェクトを呼び出すことによって指定したコピー先のオブジェクトに`copy(*this, dest)`します。

```
void copy_to(
    array<value_type, _Rank>& _Dest) const;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
コピー先のオブジェクト。

##  <a name="data"></a> データ

`array_view` の生データへのポインターを返します。

```
value_type* data() const restrict(amp,
    cpu);

const value_type* data() const restrict(amp,
    cpu);
```

### <a name="return-value"></a>戻り値

生データへのポインター、`array_view`します。

##  <a name="discard_data"></a> discard_data

このビューの基となる現在のデータを破棄します。 これは、ビューの現在の内容をアクセスしているターゲット `accelerator_view` にコピーしないようにするために使用するランタイムの最適化のためのヒントで、既存の内容が必要ではない場合に使用することをお勧めします。 restrict(amp) コンテキストで使用される場合、このメソッドは実行されません。

```
void discard_data() const restrict(cpu);
```

##  <a name="extent"></a> エクステント

`extent` オブジェクトの形状を定義する `array_view` オブジェクトを取得します。

```
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

##  <a name="get_extent"></a> get_extent

返します、[エクステント](extent-class.md)のオブジェクト、`array_view`オブジェクト。

```
Concurrency::extent<_Rank> get_extent() const restrict(cpu, amp);
```

### <a name="return-value"></a>戻り値

`extent`のオブジェクト、`array_view`オブジェクト

##  <a name="get_ref"></a> get_ref

_Index によってインデックス付けされた要素への参照を取得します。 CPU の array_view にアクセスするための他のインデックス作成演算子とは異なり、このメソッドは CPU にこの array_view の内容を暗黙的に同期しません。 リモートの場所で array_view にアクセスしたり、この array_view を含むコピー操作を実行したりした後は、このメソッドを呼び出す前に array_view を CPU に明示的に同期する必要があります。 これができない場合は、未定義の動作が発生します。

```
value_type& get_ref(
    const index<_Rank>& _Index) const restrict(amp, cpu);
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
インデックス。

### <a name="return-value"></a>戻り値

_Index によってインデックス付けされた要素への参照

##  <a name="get_source_accelerator_view"></a> get_source_accelerator_view

array_view のデータ ソースが存在する accelerator_view を返します。 array_view にデータ ソースがない場合、この API は runtime_exception をスローします

```
accelerator_view get_source_accelerator_view() const;
```

### <a name="return-value"></a>戻り値

##  <a name="operator_call"></a> operator()

パラメーターによって指定された要素の値を返します。

```
value_type& operator() (
    const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator() (
    int _I) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1) const restrict(amp,cpu);

value_type& operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator() (
    int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
要素の場所。

*_I0*<br/>
最初の次元のインデックス。

*_I1*<br/>
2 番目の次元のインデックス。

*_I2*<br/>
3 番目の次元のインデックス。

*_I*<br/>
要素の場所。

### <a name="return-value"></a>戻り値

パラメーターによって指定された要素の値。

##  <a name="operator_at"></a> operator[]

パラメーターで指定された要素を返します。

```
typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[] (
    int _I) const restrict(amp,cpu);

value_type& operator[] (
    const index<_Rank>& _Index) const restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
インデックス。

*_I*<br/>
インデックス。

### <a name="return-value"></a>戻り値

インデックスでの要素の値、または最上位の次元に投影される `array_view`。

##  <a name="operator_eq"></a> 演算子 =

指定された `array_view` オブジェクトの内容をこのオブジェクトにコピーします。

```
array_view& operator= (
    const array_view& _Other) restrict(amp,cpu);

array_view& operator= (
    const array_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Other*<br/>
コピー元の `array_view` オブジェクト。

### <a name="return-value"></a>戻り値

この `array_view` オブジェクトへの参照。

##  <a name="rank"></a> ランク

`array_view` オブジェクトのランクを格納します。

```
static const int rank = _Rank;
```

##  <a name="refresh"></a> 更新

バインドされたメモリが `array_view` インターフェイスの外部で変更されたことを `array_view` オブジェクトに通知します。 このメソッドの呼び出しによって、すべてのキャッシュされた情報が表示されます。

```
void refresh() const restrict(cpu);
```

## <a name="reinterpret_as"></a> reinterpret_as

オプションとして、ソースの array_view とは異なる値型を持つ可能性のある、1 次元 array_view を使用して array_view を再解釈します。

### <a name="syntax"></a>構文

```
template <
    typename _Value_type2
>
array_view< _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);

template <
    typename _Value_type2
>
array_view<const _Value_type2, _Rank> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Value_type2*<br/>
新しい `array_view` オブジェクトのデータ型。

### <a name="return-value"></a>戻り値

`array_view`オブジェクトまたは const`array_view`オブジェクトに基づくこの`array_view`から変換された要素の型を持つ`T`に`_Value_type2`から、ランクを引き下げられたと*N*を 1 にします。

### <a name="remarks"></a>Remarks

ソース配列とは異なる値型が含まれる可能性のある、線形の、1 次元配列として多次元配列を表示すると都合のよい場合があります。 このメソッドを使用して `array_view` でこれを実現できます。

**警告**Reinterpeting 別の値の型を使用して array_view オブジェクトは安全でない操作です。 この機能を使用するときは、十分に注意する必要があります。

次に例を示します。

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

##  <a name="section"></a> セクション

指定された原点に `array_view` オブジェクトのサブセクションを返し、これは必要に応じて範囲が指定されます。

```
array_view section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view section(
    const Concurrency::index<_Rank>& _Idx) const restrict(amp,cpu);

array_view section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) const restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_E0*<br/>
このセクションの範囲の最上位のコンポーネント。

*_E1*<br/>
このセクションの範囲の最上位の次のコンポーネント。

*_E2*<br/>
このセクションの範囲の最下位のコンポーネント。

*展開*<br/>
[エクステント](extent-class.md)セクションの範囲を指定するオブジェクト。 原点は 0 です。

*_Idx*<br/>
[インデックス](index-class.md)元の場所を指定するオブジェクト。 サブセクションは残りの範囲です。

*_I0*<br/>
このセクションの原点の最上位のコンポーネント。

*_I1*<br/>
このセクションの原点の最上位の次のコンポーネント。

*_I2*<br/>
このセクションの原点の最下位のコンポーネント。

*_Rank*<br/>
セクションのランク。

*_Section_extent*<br/>
[エクステント](extent-class.md)セクションの範囲を指定するオブジェクト。

*_Section_origin*<br/>
[インデックス](index-class.md)元の場所を指定するオブジェクト。

### <a name="return-value"></a>戻り値

指定された原点にある `array_view` オブジェクトのサブセクションで、これは必要に応じて範囲が指定されます。 `index` のオブジェクトのみを指定すると、サブセクションには `index` オブジェクトの要素のインデックスより大きなインデックスを持つ関連する範囲のすべての要素が含まれます。

##  <a name="source_accelerator_view"></a> source_accelerator_view

この array_view が関連付けられているソースの accelerator_view を取得します。

```
__declspec(property(get= get_source_accelerator_view)) accelerator_view source_accelerator_view;
```

##  <a name="synchronize"></a> 同期

`array_view` オブジェクトへの変更をそのソース データに同期して戻します。

```
void synchronize(access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize() const restrict(cpu);
```

### <a name="parameters"></a>パラメーター

*_Access_type*<br/>
目的の[access_type](concurrency-namespace-enums-amp.md#access_type)ターゲットで[accelerator_view](accelerator-view-class.md)します。 このパラメーターには `access_type_read` の既定値があります。

##  <a name="synchronize_async"></a> synchronize_async

非同期的に行われた変更を同期化、`array_view`そのソース データへのオブジェクト。

```
concurrency::completion_future synchronize_async(access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_async() const restrict(cpu);
```

### <a name="parameters"></a>パラメーター

*_Access_type*<br/>
目的の[access_type](concurrency-namespace-enums-amp.md#access_type)ターゲットで[accelerator_view](accelerator-view-class.md)します。 このパラメーターには `access_type_read` の既定値があります。

### <a name="return-value"></a>戻り値

操作の完了を待機する予定。

##  <a name="synchronize_to"></a> synchronize_to

この array_view に行われた変更を指定された accelerator_view と同期します。

```
void synchronize_to(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

void synchronize_to(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>パラメーター

*_Accl_view*<br/>
同期ターゲットの accelerator_view。

*_Access_type*<br/>
ターゲットの accelerator_view の必要な access_type。 このパラメーターには access_type_read の既定値があります。

##  <a name="synchronize_to_async"></a> synchronize_to_async

この array_view に行われた変更を指定された accelerator_view と非同期に同期します。

```
concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view,
    access_type _Access_type = access_type_read) const restrict(cpu);

concurrency::completion_future synchronize_to_async(
    const accelerator_view& _Accl_view) const restrict(cpu);
```

### <a name="parameters"></a>パラメーター

*_Accl_view*<br/>
同期ターゲットの accelerator_view。

*_Access_type*<br/>
ターゲットの accelerator_view の必要な access_type。 このパラメーターには access_type_read の既定値があります。

### <a name="return-value"></a>戻り値

操作の完了を待機する予定。

##  <a name="value_type"></a> value_type

array_view の値型およびバインド配列。

```
typedef typenamevalue_type value_type;
```

##  <a name="view_as"></a> view_as

異なるランクの `array_view` としてこの `array_view` を再解釈します。

```
template <
    int _New_rank
>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);

template <
    int _New_rank
>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank> _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_New_rank*<br/>
新しい `array_view` オブジェクトのランク。

*_View_extent*<br/>
変形を行う `extent`。

*value_type*<br/>
元の両方の要素のデータ型[配列](array-class.md)オブジェクトおよび返された`array_view`オブジェクト。

### <a name="return-value"></a>戻り値

`array_view`構築されたオブジェクト。

## <a name="see-also"></a>関連項目

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
