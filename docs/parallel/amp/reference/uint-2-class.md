---
title: uint_2 クラス
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::uint_2::set_xy
- amp_short_vectors/Concurrency::graphics::uint_2::y
- amp_short_vectors/Concurrency::graphics::uint_2::gr
- amp_short_vectors/Concurrency::graphics::uint_2::operator-
- amp_short_vectors/Concurrency::graphics::uint_2::get_x
- amp_short_vectors/Concurrency::graphics::uint_2::operator-=
- amp_short_vectors/Concurrency::graphics::uint_2::r
- amp_short_vectors/Concurrency::graphics::uint_2::yx
- amp_short_vectors/Concurrency::graphics::uint_2::operator--
- amp_short_vectors/Concurrency::graphics::uint_2::set_yx
- amp_short_vectors/Concurrency::graphics::uint_2::operator=
- amp_short_vectors/Concurrency::graphics::uint_2::set_x
- amp_short_vectors/Concurrency::graphics::uint_2::operator+=
- amp_short_vectors/Concurrency::graphics::uint_2::get_y
- amp_short_vectors/Concurrency::graphics::uint_2::xy
- amp_short_vectors/Concurrency::graphics::uint_2::x
- amp_short_vectors/Concurrency::graphics::uint_2::get_xy
- amp_short_vectors/Concurrency::graphics::uint_2::set_y
- amp_short_vectors/Concurrency::graphics::uint_2
- amp_short_vectors/Concurrency::graphics::uint_2::operator*=
- amp_short_vectors/Concurrency::graphics::uint_2::get_yx
- amp_short_vectors/Concurrency::graphics::uint_2::operator/=
- amp_short_vectors/Concurrency::graphics::uint_2::g
- amp_short_vectors/Concurrency::graphics::uint_2::operator++
- amp_short_vectors/Concurrency::graphics::uint_2::rg
ms.assetid: 9fcc9129-72b1-4da7-9012-4d3be15f1c52
ms.openlocfilehash: 5f01e4d50dc3fab8d7cb909d1ea2f3d1801f0db0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126211"
---
# <a name="uint_2-class"></a>uint_2 クラス

2 個の符号なし整数の short ベクターを表します。

## <a name="syntax"></a>構文

```cpp
class uint_2;
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

|Name|説明|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[uint_2 コンストラクター](#ctor)|オーバーロードされます。 既定のコンストラクター。すべての要素を 0 で初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|uint_2::get_x||
|uint_2::get_xy||
|uint_2::get_y||
|uint_2::get_yx||
|uint_2::ref_g メソッド||
|uint_2::ref_r メソッド||
|uint_2::ref_x メソッド||
|uint_2::ref_y メソッド||
|uint_2::set_x||
|uint_2::set_xy||
|uint_2::set_y||
|uint_2::set_yx||

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|uint_2::operator--||
|uint_2::operator%=||
|uint_2::operator&=||
|uint_2::operator*=||
|uint_2::operator/=||
|uint_2::operator^=||
|uint_2::operator&#124;=||
|uint_2::operator~||
|uint_2::operator++||
|uint_2::operator+=||
|uint_2:: operator <\<=||
|uint_2::operator=||
|uint_2::operator-=||
|uint_2::operator>>=||

### <a name="public-constants"></a>パブリック定数

|Name|説明|
|----------|-----------------|
|[サイズ定数](#uint_2__size)||

### <a name="public-data-members"></a>パブリック データ メンバー

|Name|説明|
|----------|-----------------|
|uint_2::g||
|uint_2::gr||
|uint_2::r||
|uint_2::rg||
|uint_2::x||
|uint_2::xy||
|uint_2::y||
|uint_2:: yx||

## <a name="inheritance-hierarchy"></a>継承階層

`uint_2`

## <a name="requirements"></a>要件

**ヘッダー:** amp_short_vectors

**名前空間:** Concurrency:: graphics

## <a name="ctor"></a>uint_2

既定のコンストラクター。すべての要素を 0 で初期化します。

```cpp
uint_2() restrict(amp,
    cpu);

uint_2(
    unsigned int _V0,
    unsigned int _V1) restrict(amp,
    cpu);

uint_2(
    unsigned int _V) restrict(amp,
    cpu);

uint_2(
    const uint_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const int_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const float_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const unorm_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
    const norm_2& _Other) restrict(amp,
    cpu);

explicit inline uint_2(
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

## <a name="uint_2__size"></a>幅

```cpp
static const int size = 2;
```

## <a name="see-also"></a>参照

[Concurrency::graphics 名前空間](concurrency-graphics-namespace.md)
