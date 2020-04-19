---
title: int_3 クラス
ms.date: 11/04/2016
f1_keywords:
- amp_short_vectors/Concurrency::graphics::int_3::get_x
- amp_short_vectors/Concurrency::graphics::int_3::operator-=
- amp_short_vectors/Concurrency::graphics::int_3::get_y
- amp_short_vectors/Concurrency::graphics::int_3::operator=
- amp_short_vectors/Concurrency::graphics::int_3::operator++
- amp_short_vectors/Concurrency::graphics::int_3::zyx
- amp_short_vectors/Concurrency::graphics::int_3::get_z
- amp_short_vectors/Concurrency::graphics::int_3::operator*=
- amp_short_vectors/Concurrency::graphics::int_3::grb
- amp_short_vectors/Concurrency::graphics::int_3::get_xz
- amp_short_vectors/Concurrency::graphics::int_3::br
- amp_short_vectors/Concurrency::graphics::int_3::operator--
- amp_short_vectors/Concurrency::graphics::int_3
- amp_short_vectors/Concurrency::graphics::int_3::set_yx
- amp_short_vectors/Concurrency::graphics::int_3::x
- amp_short_vectors/Concurrency::graphics::int_3::yxz
- amp_short_vectors/Concurrency::graphics::int_3::set_y
- amp_short_vectors/Concurrency::graphics::int_3::zy
- amp_short_vectors/Concurrency::graphics::int_3::z
- amp_short_vectors/Concurrency::graphics::int_3::get_zx
- amp_short_vectors/Concurrency::graphics::int_3::rb
- amp_short_vectors/Concurrency::graphics::int_3::yzx
- amp_short_vectors/Concurrency::graphics::int_3::gb
- amp_short_vectors/Concurrency::graphics::int_3::set_zxy
- amp_short_vectors/Concurrency::graphics::int_3::xy
- amp_short_vectors/Concurrency::graphics::int_3::set_zx
- amp_short_vectors/Concurrency::graphics::int_3::g
- amp_short_vectors/Concurrency::graphics::int_3::operator/=
- amp_short_vectors/Concurrency::graphics::int_3::get_zy
- amp_short_vectors/Concurrency::graphics::int_3::yx
- amp_short_vectors/Concurrency::graphics::int_3::xzy
- amp_short_vectors/Concurrency::graphics::int_3::set_x
- amp_short_vectors/Concurrency::graphics::int_3::set_xz
- amp_short_vectors/Concurrency::graphics::int_3::get_yzx
- amp_short_vectors/Concurrency::graphics::int_3::b
- amp_short_vectors/Concurrency::graphics::int_3::gbr
- amp_short_vectors/Concurrency::graphics::int_3::operator+=
- amp_short_vectors/Concurrency::graphics::int_3::gr
- amp_short_vectors/Concurrency::graphics::int_3::brg
- amp_short_vectors/Concurrency::graphics::int_3::bg
- amp_short_vectors/Concurrency::graphics::int_3::zx
- amp_short_vectors/Concurrency::graphics::int_3::get_xyz
- amp_short_vectors/Concurrency::graphics::int_3::set_zyx
- amp_short_vectors/Concurrency::graphics::int_3::set_yzx
- amp_short_vectors/Concurrency::graphics::int_3::y
- amp_short_vectors/Concurrency::graphics::int_3::set_z
- amp_short_vectors/Concurrency::graphics::int_3::r
- amp_short_vectors/Concurrency::graphics::int_3::set_xzy
- amp_short_vectors/Concurrency::graphics::int_3::rg
- amp_short_vectors/Concurrency::graphics::int_3::xyz
- amp_short_vectors/Concurrency::graphics::int_3::get_yz
- amp_short_vectors/Concurrency::graphics::int_3::operator-
- amp_short_vectors/Concurrency::graphics::int_3::set_xy
- amp_short_vectors/Concurrency::graphics::int_3::zxy
- amp_short_vectors/Concurrency::graphics::int_3::yz
- amp_short_vectors/Concurrency::graphics::int_3::set_zy
- amp_short_vectors/Concurrency::graphics::int_3::bgr
- amp_short_vectors/Concurrency::graphics::int_3::get_xzy
- amp_short_vectors/Concurrency::graphics::int_3::get_yx
- amp_short_vectors/Concurrency::graphics::int_3::rbg
- amp_short_vectors/Concurrency::graphics::int_3::get_zxy
- amp_short_vectors/Concurrency::graphics::int_3::set_yxz
- amp_short_vectors/Concurrency::graphics::int_3::rgb
- amp_short_vectors/Concurrency::graphics::int_3::get_xy
- amp_short_vectors/Concurrency::graphics::int_3::set_xyz
- amp_short_vectors/Concurrency::graphics::int_3::get_yxz
- amp_short_vectors/Concurrency::graphics::int_3::get_zyx
- amp_short_vectors/Concurrency::graphics::int_3::xz
- amp_short_vectors/Concurrency::graphics::int_3::set_yz
ms.assetid: d4af182f-30f1-455c-b16d-aa99cd314038
ms.openlocfilehash: bc35562466ee33585be03739695d24da043415c2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127817"
---
# <a name="int_3-class"></a>int_3 クラス

3 個の整数の short ベクターを表します。

## <a name="syntax"></a>構文

```cpp
class int_3;
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

|Name|説明|
|----------|-----------------|
|`value_type`||

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[int_3 コンストラクター](#ctor)|オーバーロードされます。 既定のコンストラクター。すべての要素を 0 で初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|int_3::get_x||
|int_3::get_xy||
|int_3::get_xyz||
|int_3::get_xz||
|int_3::get_xzy||
|int_3::get_y||
|int_3::get_yx||
|int_3::get_yxz||
|int_3::get_yz||
|int_3::get_yzx||
|int_3::get_z||
|int_3::get_zx||
|int_3::get_zxy||
|int_3::get_zy||
|int_3::get_zyx||
|int_3::ref_b||
|int_3::ref_g||
|int_3::ref_r||
|int_3::ref_x||
|int_3::ref_y||
|int_3::ref_z||
|int_3::set_x||
|int_3::set_xy||
|int_3::set_xyz||
|int_3::set_xz||
|int_3::set_xzy||
|int_3::set_y||
|int_3::set_yx||
|int_3::set_yxz||
|int_3::set_yz||
|int_3::set_yzx||
|int_3::set_z||
|int_3::set_zx||
|int_3::set_zxy||
|int_3::set_zy||
|int_3::set_zyx||

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|int_3::operator-||
|int_3::operator--||
|int_3::operator%=||
|int_3::operator&=||
|int_3::operator*=||
|int_3::operator/=||
|int_3::operator^=||
|int_3::operator&#124;=||
|int_3::operator~||
|int_3::operator++||
|int_3::operator+=||
|int_3:: operator <\<=||
|int_3::operator=||
|int_3::operator-=||
|int_3::operator>>=||

### <a name="public-constants"></a>パブリック定数

|Name|説明|
|----------|-----------------|
|[サイズ定数](#size)||

### <a name="public-data-members"></a>パブリック データ メンバー

|Name|説明|
|----------|-----------------|
|int_3::b||
|int_3::bg||
|int_3::bgr||
|int_3::br||
|int_3::brg||
|int_3::g||
|int_3::gb||
|int_3::gbr||
|int_3::gr||
|int_3::grb||
|int_3::r||
|int_3::rb||
|int_3::rbg||
|int_3::rg||
|int_3::rgb||
|int_3::x||
|int_3::xy||
|int_3::xyz||
|int_3::xz||
|int_3::xzy||
|int_3::y||
|int_3::yx||
|int_3::yxz||
|int_3::yz||
|int_3::yzx||
|int_3::z||
|int_3::zx||
|int_3::zxy||
|int_3::zy||
|int_3::zyx||

## <a name="inheritance-hierarchy"></a>継承階層

`int_3`

## <a name="requirements"></a>要件

**ヘッダー:** amp_short_vectors

**名前空間:** Concurrency:: graphics

## <a name="ctor"></a>int_3

既定のコンストラクター。すべての要素を 0 で初期化します。

### <a name="syntax"></a>構文

```cpp
int_3() restrict(amp,cpu);
int_3(
   int _V0,
   int _V1,
   int _V2
) restrict(amp,cpu);
int_3(
   int _V
) restrict(amp,cpu);
int_3(
   const int_3& _Other
) restrict(amp,cpu);
explicit inline int_3(
   const uint_3& _Other
) restrict(amp,cpu);
explicit inline int_3(
   const float_3& _Other
) restrict(amp,cpu);
explicit inline int_3(
   const unorm_3& _Other
) restrict(amp,cpu);
explicit inline int_3(
   const norm_3& _Other
) restrict(amp,cpu);
explicit inline int_3(
   const double_3& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_V0*<br/>
要素0を初期化する値。

*_V1*<br/>
要素1を初期化する値。

*_V2*<br/>
要素2を初期化する値。

*_V*<br/>
初期化の値。

*_Other*<br/>
の初期化に使用されるオブジェクト。

## <a name="size"></a>幅

### <a name="syntax"></a>構文

```cpp
static const int size = 3;
```

## <a name="see-also"></a>参照

[Concurrency::graphics 名前空間](concurrency-graphics-namespace.md)
