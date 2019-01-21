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
ms.openlocfilehash: 93ef654bb71a342a6215ce5cd60786f36cadedf7
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657553"
---
# <a name="array-class"></a>array クラス

データをアクセラレータに移動するために使用するデータ コンテナーを表します。

## <a name="syntax"></a>構文

```
template <typename value_type, int _Rank>
friend class array;
```

#### <a name="parameters"></a>パラメーター

*value_type*<br/>
データの要素型。

*_Rank*<br/>
配列のランク。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[array コンス トラクター](#ctor)|`array` クラスの新しいインスタンスを初期化します。|
|[~ array デストラクター](#dtor)|`array` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[copy_to](#copy_to)|array の内容を別の array にコピーします。|
|[data](#data)|配列の生データへのポインターを返します。|
|[get_accelerator_view](#get_accelerator_view)|返します、 [accelerator_view](accelerator-view-class.md)配列が割り当てられている場所を表すオブジェクト。 このプロパティは CPU 上でのみアクセスできます。|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|2 つ目の取得[accelerator_view](accelerator-view-class.md)オブジェクトをインスタンス化するステージング コンス トラクターが呼び出されたときに、パラメーターとして渡される、`array`オブジェクト。|
|[get_cpu_access_type](#get_cpu_access_type)|返します、 [access_type](concurrency-namespace-enums-amp.md#access_type)の配列。 このメソッドは CPU 上でのみアクセスできます。|
|[get_extent](#get_extent)|返します、[エクステント](extent-class.md)オブジェクトの配列。|
|[reinterpret_as](#reinterpret_as)|`array` オブジェクトのすべての要素を含む 1 次元配列を返します。|
|[section](#section)|指定された原点にある `array` オブジェクトのサブセクションを返し、これは必要に応じて範囲が指定されます。|
|[view_as](#view_as)|返します、 [array_view](array-view-class.md)から構築されたオブジェクトを`array`オブジェクト。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[operator std::vector&lt;value_type&gt;](#operator_vec)|使用して`copy(*this, vector)`へ暗黙的に変換、配列、std::[ベクター](../../../standard-library/vector-class.md)オブジェクト。|
|[演算子 ()](#operator_call)|パラメーターによって指定された要素の値を返します。|
|[operator\[\]](#operator_at)|指定したインデックス位置にある要素を返します。|
|[operator=](#operator_eq)|指定された `array` オブジェクトの内容をこのオブジェクトにコピーします。|

### <a name="public-constants"></a>パブリック定数

|名前|説明|
|----------|-----------------|
|[rank 定数](#rank)|配列のランクを格納します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[accelerator_view](#accelerator_view)|取得、 [accelerator_view](accelerator-view-class.md)配列が割り当てられている場所を表すオブジェクト。 このプロパティは CPU 上でのみアクセスできます。|
|[associated_accelerator_view](#associated_accelerator_view)|2 つ目の取得[accelerator_view](accelerator-view-class.md)オブジェクトをインスタンス化するステージング コンス トラクターが呼び出されたときに、パラメーターとして渡される、`array`オブジェクト。|
|[cpu_access_type](#cpu_access_type)|取得、 [access_type](concurrency-namespace-enums-amp.md#access_type) CPU が配列の記憶域にアクセスする方法を表します。|
|[extent](#extent)|配列の図形を定義する範囲を取得します。|

## <a name="remarks"></a>Remarks

型`array<T,N>`、密で正規表現を表します (ギザギザにならず) *N*-は、アクセラレータや CPU などの特定の場所にある次元の配列。 配列の要素のデータ型は `T` で、ターゲット アクセラレータと互換性のある型である必要があります。 ランクは `N` であり、配列のランクは静的に決定され、型の一部です。配列の範囲は、ランタイムによって決定され、`extent<N>` クラスを使用して表されます。

いくつかの機能は、ランク 1、2、および 3 で `array` オブジェクトに特化していますが、配列はどの次元数も指定できます。 次元の引数を省略すると、既定値は 1 です。

配列データはメモリ内に連続して配置されます。 最下位の次元で "1" 異なる要素はメモリでは隣接しています。

配列が別の配列にコピーされる場合は詳細コピーが実行されるため、配列は論理的に値型であると見なされます。 2 つの配列が同じデータを指すことはありません。

`array<T,N>` 型はいくつかのシナリオで使用されます。

- アクセラレータの計算で使用できるデータ コンテナーとして。

- ホスト CPU にメモリを保持するデータ コンテナーとして (他の配列との間でコピーするために使用できます)。

- ホストとデバイス間のコピーの高速の仲介役として機能するステージング オブジェクトとして。

## <a name="inheritance-hierarchy"></a>継承階層

`array`

## <a name="requirements"></a>必要条件

**ヘッダー:** amp.h

**Namespace:** コンカレンシー

##  <a name="dtor"></a> ~ 配列

`array` オブジェクトを破棄します。

```
~array() restrict(cpu);
```

##  <a name="accelerator_view"></a> accelerator_view

取得、 [accelerator_view](accelerator-view-class.md)配列が割り当てられている場所を表すオブジェクト。 このプロパティは CPU 上でのみアクセスできます。

```
__declspec(property(get= get_accelerator_view)) Concurrency::accelerator_view accelerator_view;
```

##  <a name="ctor"></a> 配列

新しいインスタンスを初期化、 [array クラス](array-class.md)します。 `array<T,N>` の既定のコンストラクターがありません。 すべてのコンストラクターは CPU でのみ実行されます。 これらは、Direct3D ターゲットで実行することはできません。

```
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
[Accelerator_view](accelerator-view-class.md)オブジェクト、配列の位置を指定します。

*_Cpu_access_type*<br/>
必要な[access_type](concurrency-namespace-enums-amp.md#access_type) CPU 上の配列。 このパラメーターには、CPU の `access_type_auto` 決定をランタイムに任せる `access_type` の既定値があります。 配列の実際の CPU `access_type` は `get_cpu_access_type` メソッドを使用してクエリを実行できます。

*_Extent*<br/>
配列の各次元の範囲。

*_E0*<br/>
このセクションの範囲の最上位のコンポーネント。

*_E1*<br/>
このセクションの範囲の最上位の次のコンポーネント。

*_E2*<br/>
このセクションの範囲の最下位のコンポーネント。

*_InputIterator*<br/>
入力列挙子の型。

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

##  <a name="associated_accelerator_view"></a> associated_accelerator_view

2 つ目の取得[accelerator_view](accelerator-view-class.md)オブジェクトをインスタンス化するステージング コンス トラクターが呼び出されたときに、パラメーターとして渡される、`array`オブジェクト。

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to

内容をコピー、`array`間`array`します。

```
void copy_to(
    array<value_type, _Rank>& _Dest) const ;

void copy_to(
    array_view<value_type, _Rank>& _Dest) const ;
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
[Array_view](array-view-class.md)オブジェクトにコピーします。

##  <a name="cpu_access_type"></a> cpu_access_type

この配列に許可されている CPU access_type を取得します。

```
__declspec(property(get= get_cpu_access_type)) access_type cpu_access_type;
```

##  <a name="data"></a> データ

`array` の生データへのポインターを返します。

```
value_type* data() restrict(amp, cpu);

const value_type* data() const restrict(amp, cpu);
```

### <a name="return-value"></a>戻り値

配列の生データへのポインター。

##  <a name="extent"></a> エクステント

取得、[エクステント](extent-class.md)の形状を定義するオブジェクト、`array`します。

```
__declspec(property(get= get_extent)) Concurrency::extent<_Rank> extent;
```

##  <a name="get_accelerator_view"></a> get_accelerator_view

返します、 [accelerator_view](accelerator-view-class.md)位置を表すオブジェクトを`array`オブジェクトが割り当てられます。 このプロパティは CPU 上でのみアクセスできます。

```
Concurrency::accelerator_view get_accelerator_view() const;
```

### <a name="return-value"></a>戻り値

`accelerator_view`位置を表すオブジェクトを`array`オブジェクトが割り当てられます。

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

2 つ目の取得[accelerator_view](accelerator-view-class.md)オブジェクトをインスタンス化するステージング コンス トラクターが呼び出されたときに、パラメーターとして渡される、`array`オブジェクト。

```
Concurrency::accelerator_view get_associated_accelerator_view() const ;
```

### <a name="return-value"></a>戻り値

2 番目の[accelerator_view](accelerator-view-class.md)ステージング コンス トラクターに渡されるオブジェクト。

##  <a name="get_cpu_access_type"></a> get_cpu_access_type

この配列に対して許可される CPU access_type を返します。

```
access_type get_cpu_access_type() const restrict(cpu);
```

### <a name="return-value"></a>戻り値

##  <a name="get_extent"></a> get_extent

返します、[エクステント](extent-class.md)のオブジェクト、`array`します。

```
Concurrency::extent<_Rank> get_extent() const restrict(amp,cpu);
```

### <a name="return-value"></a>戻り値

`extent`のオブジェクト、`array`します。

##  <a name="operator_vec"></a> operator std::vector&lt;value_type&gt;

使用して`copy(*this, vector)`std::vector オブジェクトに配列を暗黙的に変換します。

```
operator std::vector<value_type>() const restrict(cpu);
```

### <a name="parameters"></a>パラメーター

*value_type*<br/>
ベクターの要素のデータ型。

### <a name="return-value"></a>戻り値

配列に含まれるデータのコピーを含む型 `vector<T>` のオブジェクト。

##  <a name="operator_call"></a> operator()

パラメーターによって指定された要素の値を返します。

```
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

##  <a name="operator_at"></a> operator[]

指定したインデックス位置にある要素を返します。

```
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

##  <a name="operator_eq"></a> 演算子 =

指定した内容をコピー`array`オブジェクト。

```
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

##  <a name="rank"></a> ランク

ランクを格納、`array`します。

```
static const int rank = _Rank;
```

## <a name="reinterpret_as"></a> reinterpret_as

必要に応じてソース配列の別の値型である可能性がありますが、1 次元 array_view を配列として再解釈します。

### <a name="syntax"></a>構文

```
template <typename _Value_type2>
array_view<_Value_type2,1> reinterpret_as() restrict(amp,cpu);

template <typename _Value_type2>
array_view<const _Value_type2, 1> reinterpret_as() const restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Value_type2*<br/>
返されたデータのデータ型。

### <a name="return-value"></a>戻り値

Array_view または要素型とランク N から 1 に削減する T から解釈要素型で、配列に基づいている const の array_view オブジェクトの場合は。

### <a name="remarks"></a>Remarks

ソース配列とは異なる値型が通常含まれている、線形の、1 次元配列のように、多次元配列を表示すると都合のよい場合があります。 これを実現するには、このメソッドを使用できます。
**注意**安全でない可能性のある操作は、別の値の型を使用して配列オブジェクトを変換」ダイアログします。 この機能を慎重に使用することをお勧めします。

次にコード例を示します。

```cpp
struct RGB { float r; float g; float b; };

array<RGB,3>  a = ...;
array_view<float,1> v = a.reinterpret_as<float>();

assert(v.extent == 3*a.extent);
```

##  <a name="section"></a> セクション

指定された原点にある `array` オブジェクトのサブセクションを返し、これは必要に応じて範囲が指定されます。

```
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

*value_type*<br/>
コピーされた要素のデータ型。

### <a name="return-value"></a>戻り値

指定された原点にある `array` オブジェクトのサブセクションを返し、これは必要に応じて範囲が指定されます。 `index` オブジェクトのみを指定すると、サブセクションには `index` オブジェクトの要素のインデックスより大きなインデックスを持つ関連するグリッドのすべての要素が含まれます。

##  <a name="view_as"></a> view_as

この配列として再解釈、 [array_view](array-view-class.md)異なるランクの。

```
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
新しいを作成するために使用する範囲[array_view](array-view-class.md)オブジェクト。

*value_type*<br/>
元の両方の要素のデータ型`array`オブジェクトおよび返された`array_view`オブジェクト。

### <a name="return-value"></a>戻り値

[Array_view](array-view-class.md)構築されたオブジェクト。

## <a name="see-also"></a>関連項目

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
