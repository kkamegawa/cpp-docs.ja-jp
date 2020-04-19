---
title: unorm クラス
ms.date: 11/04/2016
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
ms.openlocfilehash: 7c9ec967be8be618e5f8ab3bad1bfd940bfeaef4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126306"
---
# <a name="unorm-class"></a>unorm クラス

Unorm 番号を表します。 各要素は、[0.0 f, 1.0 f] の範囲の浮動小数点数です。

## <a name="syntax"></a>構文

```cpp
class unorm;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[unorm コンストラクター](#ctor)|オーバーロードされます。 既定のコンストラクターです。 を 0.0 f に初期化します。|

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|unorm::operator--||
|unorm:: operator float|変換演算子。 Unorm 数値を浮動小数点値に変換します。|
|unorm:: operator * =||
|unorm:: operator/=||
|unorm:: operator + +||
|unorm::operator+=||
|unorm::operator=||
|unorm::operator-=||

## <a name="inheritance-hierarchy"></a>継承階層

`unorm`

## <a name="requirements"></a>［要件］

**ヘッダー:** amp_short_vectors

**名前空間:** Concurrency:: graphics

## <a name="ctor"></a>unorm

既定のコンストラクターです。 を 0.0 f に初期化します。

```cpp
unorm(
    void) restrict(amp,
    cpu);

explicit unorm(
    float _V) restrict(amp,
    cpu);

explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

explicit unorm(
    int _V) restrict(amp,
    cpu);

explicit unorm(
    double _V) restrict(amp,
    cpu);

unorm(
    const unorm& _Other) restrict(amp,
    cpu);

inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```

### <a name="parameters"></a>パラメーター

*_V*<br/>
の初期化に使用される値。

*_Other*<br/>
の初期化に使用される基準オブジェクト。

## <a name="see-also"></a>参照

[Concurrency::graphics 名前空間](concurrency-graphics-namespace.md)
