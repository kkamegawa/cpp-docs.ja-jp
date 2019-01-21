---
title: texture クラス
ms.date: 11/04/2016
f1_keywords:
- texture
- AMP_GRAPHICS/texture
- AMP_GRAPHICS/concurrency::graphics::texture::texture
- AMP_GRAPHICS/concurrency::graphics::texture::copy_to
- AMP_GRAPHICS/concurrency::graphics::texture::data
- AMP_GRAPHICS/concurrency::graphics::texture::get
- AMP_GRAPHICS/concurrency::graphics::texture::get_associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::get_depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::get_row_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::set
- AMP_GRAPHICS/concurrency::graphics::texture::rank
- AMP_GRAPHICS/concurrency::graphics::texture::associated_accelerator_view
- AMP_GRAPHICS/concurrency::graphics::texture::depth_pitch
- AMP_GRAPHICS/concurrency::graphics::texture::row_pitch
ms.assetid: 16e85d4d-e80a-474a-995d-8bf63fbdf34c
ms.openlocfilehash: 8e427206379f1e7d094362411f074ad9cafb43fd
ms.sourcegitcommit: 53f75afaf3c0b3ed481c5503357ed2b7b87aac6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2018
ms.locfileid: "53657540"
---
# <a name="texture-class"></a>texture クラス

テクスチャは範囲ドメイン内の `accelerator_view` についてのデータ集合体です。 これは、範囲ドメインの各要素に対して 1 つずつの変数のコレクションです。 各変数は C++ のプリミティブ型に対応する値を保持 ( `unsigned int`、 `int`、 `float`、 `double`)、スカラー型 ( `norm`、または`unorm`)、または short ベクター型。

## <a name="syntax"></a>構文

```
template <typename value_type,  int _Rank>
class texture;
```

#### <a name="parameters"></a>パラメーター

*value_type*<br/>
テクスチャの要素の型。

*_Rank*<br/>
テクスチャのランク。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|`scalar_type`|スカラー型。|
|`value_type`|値型。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[テクスチャのコンス トラクター](#ctor)|`texture` クラスの新しいインスタンスを初期化します。|
|[~ texture デストラクター](#ctor)|`texture` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[copy_to](#copy_to)|コピー、`texture`ディープ コピーを実行して、先のオブジェクト。|
|[data](#data)|このテクスチャの生データに CPU のポインターを返します。|
|[get](#get)|指定したインデックス位置に要素の値を返します。|
|[get_associated_accelerator_view](#get_associated_accelerator_view)|返します、 [accelerator_view](accelerator-view-class.md)にコピーするには、このテクスチャの優先ターゲットであります。|
|[get_depth_pitch](#get_depth_pitch)|CPU の 3D ステージング テクスチャの各深度スライス間のバイト数を返します。|
|[get_row_pitch](#get_row_pitch)|CPU の 2D または 3D ステージング テクスチャの各行間でバイト数を返します。|
|[set](#set)|指定されたインデックス位置にある要素の値を設定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[演算子 ()](#operator_call)|パラメーターによって指定された要素の値を返します。|
|[operator\[\]](#operator_at)|指定したインデックス位置にある要素を返します。|
|[operator=](#operator_eq)|指定したコピー[テクスチャ](texture-class.md)オブジェクトをこのオブジェクト。|

### <a name="public-constants"></a>パブリック定数

|名前|説明|
|----------|-----------------|
|[rank 定数](#rank)|`texture` オブジェクトのランクを取得します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[associated_accelerator_view](#associated_accelerator_view)|取得、 [accelerator_view](accelerator-view-class.md)にコピーするには、このテクスチャの優先ターゲットであります。|
|[depth_pitch](#depth_pitch)|CPU の 3D ステージング テクスチャの各深度スライス間のバイト数を取得します。|
|[row_pitch](#row_pitch)|CPU の 2D または 3D ステージング テクスチャの各行間のバイト数を取得します。|

## <a name="inheritance-hierarchy"></a>継承階層

`_Texture_base`

`texture`

## <a name="requirements"></a>必要条件

**ヘッダー:** amp_graphics.h

**Namespace:** Concurrency::graphics

##  <a name="dtor"></a> ~ テクスチャ

`texture` オブジェクトを破棄します。

```
~texture() restrict(cpu);
```

##  <a name="associated_accelerator_view"></a> associated_accelerator_view

取得、 [accelerator_view](accelerator-view-class.md)にコピーするには、このテクスチャの優先ターゲットであります。

```
__declspec(property(get= get_associated_accelerator_view)) Concurrency::accelerator_view associated_accelerator_view;
```

##  <a name="copy_to"></a> copy_to

コピー、`texture`ディープ コピーを実行して、先のオブジェクト。

```
void copy_to(texture& _Dest) const;
void copy_to(writeonly_texture_view<value_type, _Rank>& _Dest) const;
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
コピー先のオブジェクト。

*_Rank*<br/>
テクスチャのランク。

*value_type*<br/>
テクスチャの要素の型。

##  <a name="data"></a> データ

このテクスチャの生データに CPU のポインターを返します。

```
void* data() restrict(cpu);

const void* data() const restrict(cpu);
```

### <a name="return-value"></a>戻り値

テクスチャの生データへのポインター。

##  <a name="depth_pitch"></a> depth_pitch

CPU の 3D ステージング テクスチャの各深度スライス間のバイト数を取得します。

```
__declspec(property(get= get_depth_pitch)) unsigned int depth_pitch;
```

##  <a name="get"></a> 取得

指定したインデックス位置に要素の値を返します。

```
const value_type get(const index<_Rank>& _Index) const restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
要素のインデックス。

### <a name="return-value"></a>戻り値

指定されたインデックス位置にある要素の値。

##  <a name="get_associated_accelerator_view"></a> get_associated_accelerator_view

コピー先であるこのテクスチャの優先ターゲットである accelerator_view を返します。

```
Concurrency::accelerator_view get_associated_accelerator_view() const restrict(cpu);
```

### <a name="return-value"></a>戻り値

[Accelerator_view](accelerator-view-class.md)にコピーするには、このテクスチャの優先ターゲットであります。

##  <a name="get_depth_pitch"></a> get_depth_pitch

CPU の 3D ステージング テクスチャの各深度スライス間のバイト数を返します。

```
unsigned int get_depth_pitch() const restrict(cpu);
```

### <a name="return-value"></a>戻り値

CPU の 3D ステージング テクスチャの各深度スライス間のバイト数。

##  <a name="get_row_pitch"></a> get_row_pitch

2 次元ステージング テクスチャの各行間、または 3 次元ステージング テクスチャの深度スライスの各行間のバイト数を返します。

```
unsigned int get_row_pitch() const restrict(cpu);
```

### <a name="return-value"></a>戻り値

2 次元ステージング テクスチャの各行間、または 3 次元ステージング テクスチャの深度スライスの各行間のバイト数。

##  <a name="operator_call"></a> operator()

パラメーターによって指定された要素の値を返します。

```
const value_type operator() (
    const index<_Rank>& _Index) const restrict(amp);

const value_type operator() (
    int _I0) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1) const restrict(amp);

const value_type operator() (
    int _I0,
    int _I1,
    int _I2) const restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
インデックス。

*_I0*<br/>
インデックスの最上位のコンポーネント。

*_I1*<br/>
インデックスの最上位の次のコンポーネント。

*_I2*<br/>
インデックスの最下位のコンポーネント。

*_Rank*<br/>
インデックスのランク。

### <a name="return-value"></a>戻り値

パラメーターで指定された要素の値。

##  <a name="operator_at"></a> operator[]

指定したインデックス位置にある要素を返します。

```
const value_type operator[] (const index<_Rank>& _Index) const restrict(amp);

const value_type operator[] (int _I0) const restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
インデックス。

*_I0*<br/>
インデックス。

### <a name="return-value"></a>戻り値

指定したインデックス位置にある要素。

##  <a name="operator_eq"></a> 演算子 =

指定したコピー[テクスチャ](texture-class.md)オブジェクトをこのオブジェクト。

```
texture& operator= (
    const texture& _Other);

texture& operator= (
    texture<value_type, _Rank>&& _Other);
```

### <a name="parameters"></a>パラメーター

*_Other*<br/>
コピー元の `texture` オブジェクト。

### <a name="return-value"></a>戻り値

この `texture` オブジェクトへの参照。

##  <a name="rank"></a> ランク

`texture` オブジェクトのランクを取得します。

```
static const int rank = _Rank;
```

##  <a name="row_pitch"></a> row_pitch

CPU の 2D または 3D ステージング テクスチャの各行間のバイト数を取得します。

```
__declspec(property(get= get_row_pitch)) unsigned int row_pitch;
```

##  <a name="set"></a> 設定

指定されたインデックス位置にある要素の値を設定します。

```
void set(
    const index<_Rank>& _Index,
    const value_type& value) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
要素のインデックス。

*_Rank*<br/>
インデックスのランク。

*value*<br/>
要素の新しい値。

##  <a name="ctor"></a> テクスチャ

`texture` クラスの新しいインスタンスを初期化します。

```
texture(const Concurrency::extent<_Rank>& _Ext) restrict(cpu);

texture(int _E0) restrict(cpu);

texture(int _E0, int _E1) restrict(cpu);

texture(int _E0, int _E1, int _E2) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0, _Input_iterator _Src_first, _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last) restrict(cpu);

template<typename _Input_iterator>
texture(
    const Concurrency::extent<_Rank>& _Ext,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

template<typename _Input_iterator>
texture(
    int _E0,
    int _E1,
    int _E2,
    _Input_iterator _Src_first,
    _Input_iterator _Src_last,
    const Concurrency::accelerator_view& _Av) restrict(cpu))  ;

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    int _E1,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element) restrict(cpu);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av)  ;

texture(
    int _E0,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    int _E0,
    int _E1,
    int _E2,
    _In_ void* _Source,
    unsigned int _Src_byte_size,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av) restrict(cpu);

texture(
    const texture& _Src,
    const Concurrency::accelerator_view& _Acc_view);

texture(
    texture&& _Other);

texture(
    const Concurrency::extent<_Rank>& _Ext,
    unsigned int _Bits_per_scalar_element,
    const Concurrency::accelerator_view& _Av);

texture(
    const texture& _Src);
```

### <a name="parameters"></a>パラメーター

*_Acc_view*<br/>
[Accelerator_view](accelerator-view-class.md)テクスチャの場所を指定します。

*_Av*<br/>
[Accelerator_view](accelerator-view-class.md)テクスチャの場所を指定します。

*_Associated_av*<br/>
コピー先としてまたはこのテクスチャからの優先ターゲットを指定する accelerator_view。

*_Bits_per_scalar_element*<br/>
テクスチャの基になるスカラー型のスカラー要素ごとのビット数。 一般に、サポートされている値は 8、16、32、および 64 です。 0 を指定すると、ビット数は基になる scalar_type と同じです。 64 は、倍精度ベースのテクスチャに対してのみ有効です。

*展開*<br/>
テクスチャの各次元の範囲。

*_E0*<br/>
テクスチャの最上位のコンポーネント。

*_E1*<br/>
テクスチャの最上位の次のコンポーネント。

*_E2*<br/>
テクスチャの範囲の最下位のコンポーネント。

*_Input_iterator*<br/>
入力列挙子の型。

*_Mipmap_levels*<br/>
基になるテクスチャの MIPMAP レベルの数。 0 を指定すると、テクスチャには指定された範囲で可能な最小サイズにした MIPMAP レベルのすべての範囲が含まれます。

*_Rank*<br/>
範囲のランク。

*_Source*<br/>
ホスト バッファーへのポインター。

*_Src*<br/>
コピーするテクスチャ。

*_Src_byte_size*<br/>
ソース バッファーのバイト数。

*_Src_first*<br/>
ソース コンテナーへの先頭の反復子。

*_Src_last*<br/>
ソース コンテナーへの終了の反復子。

*_Other*<br/>
その他のデータ ソース。

*_Rank*<br/>
セクションのランク。

## <a name="see-also"></a>関連項目

[Concurrency::graphics 名前空間](concurrency-graphics-namespace.md)
