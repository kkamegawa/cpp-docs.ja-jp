---
title: Concurrency::graphics::direct3d 名前空間
ms.date: 11/04/2016
f1_keywords:
- amp_graphics/Concurrency::graphics::direct3d
- amp_short_vectors/Concurrency::graphics::direct3d
ms.assetid: be283331-07cf-46e4-91a1-e8aa85d4ec8e
ms.openlocfilehash: 4911787fd17877769eb723cf1e61e29fe626a783
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139439"
---
# <a name="concurrencygraphicsdirect3d-namespace"></a>Concurrency::graphics::direct3d 名前空間

[Get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)メソッドと[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)メソッドを提供します。

## <a name="syntax"></a>構文

```cpp
namespace direct3d;
```

## <a name="members"></a>メンバー

### <a name="functions"></a>関数

|Name<br /><br /> 説明|
|--------------------------|
|[get_sampler](concurrency-graphics-direct3d-namespace-functions.md#get_sampler)<br /><br /> 指定されたサンプラー オブジェクトを表す特定のアクセラレータ ビューについて、Direct3D サンプラーの状態インターフェイスを取得します。|
|[get_texture](concurrency-graphics-direct3d-namespace-functions.md#get_texture)<br /><br /> 指定された[テクスチャ](texture-class.md)オブジェクトの基になる Direct3D テクスチャインターフェイスを取得します。|
|[make_sampler](concurrency-graphics-direct3d-namespace-functions.md#make_sampler)<br /><br /> Direct3D サンプラーの状態インターフェイス ポインターからサンプラーを作成します。|
|[make_texture](concurrency-graphics-direct3d-namespace-functions.md#make_texture)<br /><br /> 指定されたパラメーターを使用して、[テクスチャ](texture-class.md)オブジェクトを作成します。|
|[msad4](concurrency-graphics-direct3d-namespace-functions.md#msad4)<br /><br /> 4 バイトの参照値と 8 バイトのソース値を比較し、4 個の合計値のベクターを累積します。|

## <a name="requirements"></a>［要件］

**ヘッダー:** amp_graphics

**名前空間:** Concurrency:: graphics

## <a name="see-also"></a>参照

[Concurrency::graphics 名前空間](concurrency-graphics-namespace.md)
