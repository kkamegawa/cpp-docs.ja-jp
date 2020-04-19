---
title: float_2 クラス
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::float_2::yx
- amp_short_vectors/Concurrency::graphics::float_2::operator-=
- amp_short_vectors/Concurrency::graphics::float_2::operator++
- amp_short_vectors/Concurrency::graphics::float_2::operator-
- amp_short_vectors/Concurrency::graphics::float_2::r
- amp_short_vectors/Concurrency::graphics::float_2::get_yx
- amp_short_vectors/Concurrency::graphics::float_2::get_xy
- amp_short_vectors/Concurrency::graphics::float_2::operator/=
- amp_short_vectors/Concurrency::graphics::float_2::set_yx
- amp_short_vectors/Concurrency::graphics::float_2::x
- amp_short_vectors/Concurrency::graphics::float_2::get_y
- amp_short_vectors/Concurrency::graphics::float_2::operator+=
- amp_short_vectors/Concurrency::graphics::float_2::gr
- amp_short_vectors/Concurrency::graphics::float_2::operator=
- amp_short_vectors/Concurrency::graphics::float_2::set_x
- amp_short_vectors/Concurrency::graphics::float_2::operator--
- amp_short_vectors/Concurrency::graphics::float_2::get_x
- amp_short_vectors/Concurrency::graphics::float_2::operator*=
- amp_short_vectors/Concurrency::graphics::float_2::rg
- amp_short_vectors/Concurrency::graphics::float_2::set_xy
- amp_short_vectors/Concurrency::graphics::float_2::xy
- amp_short_vectors/Concurrency::graphics::float_2
- amp_short_vectors/Concurrency::graphics::float_2::set_y
- amp_short_vectors/Concurrency::graphics::float_2::y
- amp_short_vectors/Concurrency::graphics::float_2::g
ms.assetid: b3ebd48e-f8c8-4f00-a640-357f702f0cae
ms.openlocfilehash: af5116118c9821f5c1801789bff13f3de8d4026a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126657"
---
# <a name="float_2-class"></a>float_2 クラス

2 個の浮動小数点数の short ベクターを表します。

## <a name="syntax"></a>構文

```cpp
class float_2;
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|Name|説明|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[float_2 コンストラクター](#ctor)|オーバーロードされます。 既定のコンストラクター。すべての要素を 0 で初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|float_2:: get_x||
|float_2:: get_xy||
|float_2:: get_y||
|float_2::get_yx||
|float_2::ref_g||
|float_2::ref_r||
|float_2::ref_x||
|float_2::ref_y||
|float_2::set_x||
|float_2::set_xy||
|float_2:: set_y||
|float_2::set_yx||

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|float_2:: operator-||
|float_2::operator--||
|float_2::operator*=||
|float_2::operator/=||
|float_2:: operator + +||
|float_2::operator+=||
|float_2::operator=||
|float_2::operator-=||

### <a name="public-constants"></a>パブリック定数

|Name|説明|
|----------|-----------------|
|[サイズ定数](#float_2__size)||

### <a name="public-data-members"></a>パブリック データ メンバー

|Name|説明|
|----------|-----------------|
|float_2:: g||
|float_2:: gr||
|float_2::r||
|float_2::rg||
|float_2::x||
|float_2::xy||
|float_2:: y||
|float_2:: yx||

## <a name="inheritance-hierarchy"></a>継承階層

`float_2`

## <a name="requirements"></a>［要件］

**ヘッダー:** amp_short_vectors

**名前空間:** Concurrency:: graphics

## <a name="ctor"></a>float_2

既定のコンストラクター。すべての要素を 0 で初期化します。

```cpp
float_2() restrict(amp,
    cpu);

float_2(
    float _V0,
    float _V1) restrict(amp,
    cpu);

float_2(
    float _V) restrict(amp,
    cpu);

float_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline float_2(
    const double_2& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>パラメーター

*_V0*<br/>
要素0を初期化する値。

*_V1*<br/>
要素1を初期化する値。

*_V*<br/>
初期化の値。

*_Other*<br/>
の初期化に使用されるオブジェクト。

## <a name="float_2__size"></a>幅

```cpp
static const int size = 2;
```

## <a name="see-also"></a>参照

[Concurrency::graphics 名前空間](concurrency-graphics-namespace.md)
