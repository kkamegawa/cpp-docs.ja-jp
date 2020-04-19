---
title: norm クラス
ms.date: 11/04/2016
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: 272ac3685539eb03f773c8bc60d5938ed6c53876
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126514"
---
# <a name="norm-class"></a>norm クラス

標準数値を表します。 各要素は、[-1.0 f, 1.0 f] の範囲の浮動小数点数です。

## <a name="syntax"></a>構文

```cpp
class norm;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[標準コンストラクター](#ctor)|オーバーロードされます。 既定のコンストラクターです。 を 0.0 f に初期化します。|

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|基準:: operator-||
|norm::operator--||
|基準:: operator float|変換演算子。 標準数を浮動小数点値に変換します。|
|norm::operator*=||
|norm::operator/=||
|基準:: operator + +||
|norm::operator+=||
|norm::operator=||
|norm::operator-=||

## <a name="inheritance-hierarchy"></a>継承階層

`norm`

## <a name="requirements"></a>要件

**ヘッダー:** amp_short_vectors

**名前空間:** Concurrency:: graphics

## <a name="ctor"></a>満た

既定のコンストラクターです。 を 0.0 f に初期化します。

```cpp
norm(
    void) restrict(amp,
    cpu);

explicit norm(
    float _V) restrict(amp,
    cpu);

explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

explicit norm(
    int _V) restrict(amp,
    cpu);

explicit norm(
    double _V) restrict(amp,
    cpu);

norm(
    const norm& _Other) restrict(amp,
    cpu);

norm(
    const unorm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>パラメーター

*_V*<br/>
の初期化に使用される値。

*_Other*<br/>
の初期化に使用されるオブジェクト。

## <a name="see-also"></a>参照

[Concurrency::graphics 名前空間](concurrency-graphics-namespace.md)
