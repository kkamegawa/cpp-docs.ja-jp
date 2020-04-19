---
title: array クラス
ms.date: 11/04/2016
f1_keywords:
- array
- AMP/array
- AMP/Concurrency::array::array
- AMP/Concurrency::array::copy_to
- AMP/Concurrency::array::data
- AMP/Concurrency::array::get_accelerator_view
- AMP/Concurrency::array::get_associated_accelerator_view
- AMP/Concurrency::array::get_cpu_access_type
- AMP/Concurrency::array::get_extent
- AMP/Concurrency::array::reinterpret_as
- AMP/Concurrency::array::section
- AMP/Concurrency::array::view_as
- AMP/Concurrency::array::rank
- AMP/Concurrency::array::accelerator_view
- AMP/Concurrency::array::associated_accelerator_view
- AMP/Concurrency::array::cpu_access_type
- AMP/Concurrency::array::extent
helpviewer_keywords:
- array class
ms.assetid: 0832b6c1-40f0-421d-9104-6b1baa0c63a7
ms.openlocfilehash: efea8dabb69a48e69d68a86110fdf9bc7664948b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127113"
---
# <a name="array-class"></a>array クラス

データをアクセラレータに移動するために使用するデータ コンテナーを表します。

## <a name="syntax"></a>構文

```cpp
template <typename value_type, int _Rank>
friend class array;
```

### <a name="parameters"></a>パラメーター

*value_type*<br/>
データの要素型。

*_Rank*<br/>
配列のランク。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[配列コンストラクター](#ctor)|`array` クラスの新しいインスタンスを初期化します。|
|[~ array デストラクター](#dtor)|`array` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[copy_to](#copy_to)|array の内容を別の array にコピーします。|
|[data](#data)|配列の生データへのポインターを返します。|
|[get_accelerator_view](#get_accelerator_view)|配列が割り当てられている場所を表す[accelerator_view](accelerator-view-class.md)オブジェクトを返します。 このプロパティは CPU 上でのみアクセスできます。|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|ステージングコンストラクターが `array` オブジェクトをインスタンス化するために呼び出されたときにパラメーターとして渡される2番目の[accelerator_view](accelerator-view-class.md)オブジェクトを取得します。|
|[get_cpu_access_type](#get_cpu_access_type)|配列の[access_type](concurrency-namespace-enums-amp.md#access_type)を返します。 このメソッドは CPU 上でのみアクセスできます。|
|[get_extent](#get_extent)|配列の[extent](extent-class.md)オブジェクトを返します。|
|[reinterpret_as](#reinterpret_as)|`array` オブジェクトのすべての要素を含む 1 次元配列を返します。|
|[section](#section)|指定された原点にある `array` オブジェクトのサブセクションを返し、これは必要に応じて範囲が指定されます。|
|[view_as](#view_as)|`array` オブジェクトから構築された[array_view](array-view-class.md)オブジェクトを返します。|

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|[演算子 std:: vector&lt;value_type&gt;](#operator_vec)|`copy(*this, vector)` を使用して、配列を std::[vector](../../../standard-library/vector-class.md)オブジェクトに暗黙的に変換します。|
|[演算子 ()](#operator_call)|パラメーターによって指定された要素の値を返します。|
|[operator\[\]](#operator_at)|指定したインデックス位置にある要素を返します。|
|[operator=](#operator_eq)|指定された `array` オブジェクトの内容をこのオブジェクトにコピーします。|

### <a name="public-constants"></a>パブリック定数

|Name|説明|
|----------|-----------------|
|[rank 定数](#rank)|配列のランクを格納します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|Name|説明|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|配列が割り当てられている場所を表す[accelerator_view](accelerator-view-class.md)オブジェクトを取得します。 このプロパティは CPU 上でのみアクセスできます。|
|[associated_accelerator_view](#associated_accelerator_view)|ステージングコンストラクターが `array` オブジェクトをインスタンス化するために呼び出されたときにパラメーターとして渡される2番目の[accelerator_view](accelerator-view-class.md)オブジェクトを取得します。|
|[cpu_access_type](#cpu_access_type)|CPU が配列のストレージにアクセスする方法を表す[access_type](concurrency-namespace-enums-amp.md#access_type)を取得します。|
|[extent](#extent)|配列の図形を定義する範囲を取得します。|

## <a name="remarks"></a>コメント

`array<T,N>` 型は、アクセラレータや CPU など、特定の場所に配置されている高密度で標準の (ジャグ的ではない) *N*次元配列を表します。 配列の要素のデータ型は `T` で、ターゲット アクセラレータと互換性のある型である必要があります。 ランクは `N` であり、配列のランクは静的に決定され、型の一部です。配列の範囲は、ランタイムによって決定され、`extent<N>` クラスを使用して表されます。

いくつかの機能は、ランク 1、2、および 3 で `array` オブジェクトに特化していますが、配列はどの次元数も指定できます。 次元の引数を省略すると、既定値は 1 です。

配列データはメモリ内に連続して配置されます。 最下位の次元で "1" 異なる要素はメモリでは隣接しています。

配列が別の配列にコピーされる場合は詳細コピーが実行されるため、配列は論理的に値型であると見なされます。 2 つの配列が同じデータを指すことはありません。

`array<T,N>` 型はいくつかのシナリオで使用されます。

- アクセラレータの計算で使用できるデータ コンテナーとして。

- ホスト CPU にメモリを保持するデータ コンテナーとして (他の配列との間でコピーするために使用できます)。

- ホストとデバイス間のコピーの高速の仲介役として機能するステージング オブジェクトとして。

## <a name="inheritance-hierarchy"></a>継承階層

`array`

## <a name="requirements"></a>要件

**ヘッダー:** amp.h

**名前空間:** Concurrency

## <a name="dtor"></a>~ array

`array` オブジェクトを破棄します。

```cpp
~array() restrict(cpu);
```

## <a name="accelerator_view"></a>accelerator_view

配列が割り当てられている場所を表す[accelerator_view](accelerator-view-class.md)オブジェクトを取得します。 このプロパティは CPU 上でのみアクセスできます。

```cpp
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

## <a name="ctor"></a>配列

[配列クラス](array-class.md)の新しいインスタンスを初期化します。 `array<T,N>` の既定のコンストラクターがありません。 すべてのコンストラクターは CPU でのみ実行されます。 これらは、Direct3D ターゲットで実行することはできません。

```cpp
explicit array(
    const Concurrency::extent<_Rank>& _Extent) restrict(cpu);

explicit array(
    int _E0) restrict(cpu);

explicit array(
    int _E0,
    int _E1) restrict(cpu);

explicit array(
    int _E0,
    int _E1,
    int _E2) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const Concurrency::extent<_Rank>& _Extent,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

array(
    int _E0,
    int _E1,
    int _E2,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    const Concurrency::extent<_Rank>& _Extent,
    _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    _InputIterator _Src_first,
    _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first, _InputIterator _Src_last,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

template <typename _InputIterator>
array(
    int _E0,
    int _E1,
    int _E2, _InputIterator _Src_first,
    Concurrency::accelerator_view _Av,
    Concurrency::accelerator_view _Associated_Av) restrict(cpu);

explicit array(
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av
    access_type _Cpu_access_type = access_type_auto) restrict(cpu);

array(
    const array_view<const value_type, _Rank>& _Src,
    accelerator_view _Av,
    accelerator_view _Associated_Av) restrict(cpu);

array(const array& _Other) restrict(cpu);

array(array&& _Other) restrict(cpu);
```

### <a name="parameters"></a>パラメーター

*_Associated_Av*<br/>
配列の優先ターゲットの位置を指定する accelerator_view。

*_Av*<br/>
配列の位置を指定する[accelerator_view](accelerator-view-class.md)オブジェクト。

*_Cpu_access_type*<br/>
CPU 上の配列に必要な[access_type](concurrency-namespace-enums-amp.md#access_type) 。 このパラメーターには、CPU の `access_type_auto` 決定をランタイムに任せる `access_type` の既定値があります。 配列の実際の CPU `access_type` は `get_cpu_access_type` メソッドを使用してクエリを実行できます。

*_Extent*<br/>
配列の各次元の範囲。

*_E0*<br/>
このセクションの範囲の最上位のコンポーネント。

*_E1*<br/>
このセクションの範囲の最上位の次のコンポーネント。

*_E2*<br/>
このセクションの範囲の最下位のコンポーネント。

*_InputIterator*<br/>
入力反復子の型。

*_Src*<br/>
コピーするオブジェクト。

*_Src_first*<br/>
ソース コンテナーへの先頭の反復子。

*_Src_last*<br/>
ソース コンテナーへの終了の反復子。

*_Other*<br/>
その他のデータ ソース。

*_Rank*<br/>
セクションのランク。

*value_type*<br/>
コピーされた要素のデータ型。

## <a name="associated_accelerator_view"></a>associated_accelerator_view

ステージングコンストラクターが `array` オブジェクトをインスタンス化するために呼び出されたときにパラメーターとして渡される2番目の[accelerator_view](accelerator-view-class.md)オブジェクトを取得します。

```cpp
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

## <a name="copy_to"></a>copy_to

`array` の内容を別の `array`にコピーします。

```cpp
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
コピー先の[array_view](array-view-class.md)オブジェクト。

## <a name="cpu_access_type"></a>cpu_access_type

この配列に許可されている CPU access_type を取得します。

```cpp
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

## <a name="data"></a>データ

`array` の生データへのポインターを返します。

```cpp
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>戻り値

配列の生データへのポインター。

## <a name="extent"></a>エクステント

`array`の形状を定義する[extent](extent-class.md)オブジェクトを取得します。

```cpp
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

## <a name="get_accelerator_view"></a>get_accelerator_view

`array` オブジェクトが割り当てられている場所を表す[accelerator_view](accelerator-view-class.md)オブジェクトを返します。 このプロパティは CPU 上でのみアクセスできます。

```cpp
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>戻り値

`array` オブジェクトが割り当てられている場所を表す `accelerator_view` オブジェクト。

## <a name="get_associated_accelerator_view"></a>get_associated_accelerator_view

ステージングコンストラクターが `array` オブジェクトをインスタンス化するために呼び出されたときにパラメーターとして渡される2番目の[accelerator_view](accelerator-view-class.md)オブジェクトを取得します。

```cpp
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>戻り値

ステージングコンストラクターに渡される2番目の[accelerator_view](accelerator-view-class.md)オブジェクト。

## <a name="get_cpu_access_type"></a>get_cpu_access_type

この配列に対して許可される CPU access_type を返します。

```cpp
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>戻り値

## <a name="get_extent"></a>get_extent

`array`の[extent](extent-class.md)オブジェクトを返します。

```cpp
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>戻り値

`extent` の `array` オブジェクトです。

## <a name="operator_vec"></a>演算子 std:: vector&lt;value_type&gt;

`copy(*this, vector)` を使用して、配列を std:: vector オブジェクトに暗黙的に変換します。

```cpp
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>パラメーター

*value_type*<br/>
ベクターの要素のデータ型。

### <a name="return-value"></a>戻り値

配列に含まれるデータのコピーを含む型 `vector<T>` のオブジェクト。

## <a name="operator_call"></a>operator ()

パラメーターによって指定された要素の値を返します。

```cpp
value_type& operator() (const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator() (const index<_Rank>& _Index) cons  t restrict(amp,cpu);

value_type& operator() (int _I0, int _I1) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1) const restrict(amp,cpu)  ;

value_type& operator() (int _I0, int _I1, int _I2) restrict(amp,cpu);

const value_type& operator() (int _I0, int _I1, int _I2) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator()(int _I) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator()(int _I) const restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
要素の場所。

*_I0*<br/>
このセクションの原点の最上位のコンポーネント。

*_I1*<br/>
このセクションの原点の最上位の次のコンポーネント。

*_I2*<br/>
このセクションの原点の最下位のコンポーネント。

*_I*<br/>
要素の場所。

### <a name="return-value"></a>戻り値

パラメーターで指定される要素の値。

## <a name="operator_at"></a>演算子 []

指定したインデックス位置にある要素を返します。

```cpp
value_type& operator[](const index<_Rank>& _Index) restrict(amp,cpu);

const value_type& operator[]
    (const index<_Rank>& _Index) const restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Result_type operator[](int _i) restrict(amp,cpu);

typename details::_Projection_result_type<value_type,_Rank>::_Const_result_type operator[](int _i) const restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
インデックス。

*_I*<br/>
インデックス。

### <a name="return-value"></a>戻り値

指定したインデックス位置にある要素。

## <a name="operator_eq"></a>operator =

指定された `array` オブジェクトの内容をコピーします。

```cpp
array& operator= (const array& _Other) restrict(cpu);

array& operator= (array&& _Other) restrict(cpu);

array& operator= (
    const array_view<const value_type, _Rank>& _Src) restrict(cpu);
```

### <a name="parameters"></a>パラメーター

*_Other*<br/>
コピー元の `array` オブジェクト。

*_Src*<br/>
コピー元の `array` オブジェクト。

### <a name="return-value"></a>戻り値

この `array` オブジェクトへの参照。

## <a name="rank"></a>ランク

`array`のランクを格納します。

```cpp
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a>reinterpret_as

1次元の array_view で配列を再解釈します。必要に応じて、ソース配列とは異なる値型を使用できます。

### <a name="syntax"></a>構文

```cpp
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Value_type2*<br/>
返されたデータのデータ型。

### <a name="return-value"></a>戻り値

配列に基づいた array_view または const array_view オブジェクト。要素の型は T から ElementType に再解釈され、ランクは N から1に減少します。

### <a name="remarks"></a>コメント

ソース配列とは異なる値型が通常含まれている、線形の、1 次元配列のように、多次元配列を表示すると都合のよい場合があります。 これを実現するには、このメソッドを使用できます。
**注意**異なる値型を使用して配列オブジェクトを再解釈すると、安全でない可能性があります。 この機能を慎重に使用することをお勧めします。

コードの例は次のとおりです。

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

## <a name="section"></a>下

指定された原点にある `array` オブジェクトのサブセクションを返し、これは必要に応じて範囲が指定されます。

```cpp
array_view<value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::index<_Rank>& _Section_origin,
    const Concurrency::extent<_Rank>& _Section_extent) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const Concurrency::extent<_Rank>& _Ext) const restrict(amp,cpu);

array_view<value_type,_Rank> section(
    const index<_Rank>& _Idx) restrict(amp,cpu);

array_view<const value_type,_Rank> section(
    const index<_Rank>& _Idx) const restrict(amp,cpu);

array_view<value_type,1> section(
    int _I0,
    int _E0) restrict(amp,cpu);

array_view<const value_type,1> section(
    int _I0,
    int _E0) const restrict(amp,cpu);

array_view<value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) restrict(amp,cpu);

array_view<const value_type,2> section(
    int _I0,
    int _I1,
    int _E0,
    int _E1) const restrict(amp,cpu);

array_view<value_type,3> section(
    int _I0,
    int _I1,
    int _I2,
    int _E0,
    int _E1,
    int _E2) restrict(amp,cpu);

array_view<const value_type,3> section(
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

*_Ext*<br/>
セクションの範囲を指定する[extent](extent-class.md)オブジェクト。 原点は 0 です。

*_Idx*<br/>
Origin の位置を指定する[index](index-class.md)オブジェクトです。 サブセクションは残りの範囲です。

*_I0*<br/>
このセクションの原点の最上位のコンポーネント。

*_I1*<br/>
このセクションの原点の最上位の次のコンポーネント。

*_I2*<br/>
このセクションの原点の最下位のコンポーネント。

*_Rank*<br/>
セクションのランク。

*_Section_extent*<br/>
セクションの範囲を指定する[extent](extent-class.md)オブジェクト。

*_Section_origin*<br/>
Origin の位置を指定する[index](index-class.md)オブジェクトです。

*value_type*<br/>
コピーされた要素のデータ型。

### <a name="return-value"></a>戻り値

指定された原点にある `array` オブジェクトのサブセクションを返し、これは必要に応じて範囲が指定されます。 `index` オブジェクトのみを指定すると、サブセクションには `index` オブジェクトの要素のインデックスより大きなインデックスを持つ関連するグリッドのすべての要素が含まれます。

## <a name="view_as"></a>view_as

この配列を別のランクの[array_view](array-view-class.md)として再解釈します。

```cpp
template <int _New_rank>
array_view<value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) restrict(amp,cpu);

template <int _New_rank>
array_view<const value_type,_New_rank> view_as(
    const Concurrency::extent<_New_rank>& _View_extent) const restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_New_rank*<br/>
パラメーターとして渡された `extent` オブジェクトのランク。

*_View_extent*<br/>
新しい[array_view](array-view-class.md)オブジェクトを構築するために使用されるエクステント。

*value_type*<br/>
元の `array` オブジェクトと返された `array_view` オブジェクトの両方の要素のデータ型。

### <a name="return-value"></a>戻り値

構築される[array_view](array-view-class.md)オブジェクト。

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
