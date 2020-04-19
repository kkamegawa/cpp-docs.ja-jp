---
title: writeonly_texture_view クラス
ms.date: 11/04/2016
f1_keywords:
- writeonly_texture_view
- AMP_GRAPHICS/writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view
- AMP_GRAPHICS/Concurrency::graphics::writeonly_texture_view::set
- AMP_GRAPHICS/Concurrency::graphics::rank Constant
ms.assetid: 8d117ad3-0a1c-41ae-b29c-7c95fdd4d04d
ms.openlocfilehash: 8978a548ed246c59d7e7f007f1180685c7343a14
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126241"
---
# <a name="writeonly_texture_view-class"></a>writeonly_texture_view クラス

テクスチャへの書き込み専用アクセスを提供します。

## <a name="syntax"></a>構文

```cpp
template <
    typename value_type,
    int _Rank
>
class writeonly_texture_view;

template <
    typename value_type,
    int _Rank
>
class writeonly_texture_view<value_type, _Rank> : public details::_Texture_base<value_type, _Rank>;
```

### <a name="parameters"></a>パラメーター

*value_type*<br/>
テクスチャの要素の型。

*_Rank*<br/>
テクスチャのランク。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

|Name|説明|
|----------|-----------------|
|`scalar_type`||
|`value_type`|テクスチャの要素の型。|

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[writeonly_texture_view コンストラクター](#ctor)|`writeonly_texture_view` クラスの新しいインスタンスを初期化します。|
|[~ writeonly_texture_view デストラクター](#ctor)|`writeonly_texture_view` オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[set](#set)|指定されたインデックス位置にある要素の値を設定します。|

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|[operator=](#operator_eq)|指定した `writeonly_texture_view` オブジェクトをこのオブジェクトにコピーします。|

### <a name="public-constants"></a>パブリック定数

|Name|説明|
|----------|-----------------|
|[rank 定数](#rank)|`writeonly_texture_view` オブジェクトのランクを取得します。|

## <a name="inheritance-hierarchy"></a>継承階層

`_Texture_base`

`writeonly_texture_view`

## <a name="requirements"></a>要件

**ヘッダー:** amp_graphics

**名前空間:** Concurrency:: graphics

## <a name="dtor"></a>~ writeonly_texture_view

`writeonly_texture_view` オブジェクトを破棄します。

```cpp
~writeonly_texture_view() restrict(amp,cpu);
```

## <a name="operator_eq"></a>operator =

指定した `writeonly_texture_view` オブジェクトをこのオブジェクトにコピーします。

```cpp
writeonly_texture_view<value_type, _Rank>& operator= (
    const writeonly_texture_view<value_type, _Rank>& _Other) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Other*<br/>
コピー元の `writeonly_texture_view` オブジェクト。

### <a name="return-value"></a>戻り値

この `writeonly_texture_view` オブジェクトへの参照。

## <a name="rank"></a>ランク

`writeonly_texture_view` オブジェクトのランクを取得します。

```cpp
static const int rank = _Rank;
```

## <a name="set"></a>一連

指定されたインデックス位置にある要素の値を設定します。

```cpp
void set(
    const index<_Rank>& _Index,
    const value_type& value) const restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
要素のインデックス。

*value*<br/>
要素の新しい値。

## <a name="ctor"></a>writeonly_texture_view

`writeonly_texture_view` クラスの新しいインスタンスを初期化します。

```cpp
writeonly_texture_view(
    texture<value_type,
    _Rank>& _Src) restrict(amp);

writeonly_texture_view(
    const writeonly_texture_view<value_type,
    _Rank>& _Src) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Rank*<br/>
テクスチャのランク。

*value_type*<br/>
テクスチャの要素の型。

*_Src*<br/>
`writeonly_texture_view`の作成に使用されるテクスチャ。

## <a name="see-also"></a>参照

[Concurrency::graphics 名前空間](concurrency-graphics-namespace.md)
