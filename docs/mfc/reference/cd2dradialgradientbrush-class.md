---
title: CD2DRadialGradientBrush クラス
ms.date: 11/04/2016
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
ms.openlocfilehash: 22029ebcf8cf519571e81e11c84de146c9d54b26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396328"
---
# <a name="cd2dradialgradientbrush-class"></a>CD2DRadialGradientBrush クラス

ID2D1RadialGradientBrush のラッパーです。

## <a name="syntax"></a>構文

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](#cd2dradialgradientbrush)|CD2DLinearGradientBrush オブジェクトを構築します。|
|[CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush](#_dtorcd2dradialgradientbrush)|デストラクターです。 D2D 放射状グラデーション ブラシ オブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DRadialGradientBrush::Attach](#attach)|既存のリソース インターフェイス オブジェクトにアタッチします|
|[CD2DRadialGradientBrush::Create](#create)|CD2DRadialGradientBrush を作成します。 (上書き[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create))。|
|[CD2DRadialGradientBrush::Destroy](#destroy)|CD2DRadialGradientBrush オブジェクトを破棄します。 (上書き[CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy))。|
|[CD2DRadialGradientBrush::Detach](#detach)|オブジェクトからリソースのインターフェイスをデタッチします。|
|[CD2DRadialGradientBrush::Get](#get)|返します ID2D1RadialGradientBrush インターフェイス|
|[CD2DRadialGradientBrush::GetCenter](#getcenter)|グラデーションの楕円の中心を取得します。|
|[CD2DRadialGradientBrush::GetGradientOriginOffset](#getgradientoriginoffset)|グラデーションの楕円の中心を基準としたグラデーションの原点のオフセットを取得します。|
|[CD2DRadialGradientBrush::GetRadiusX](#getradiusx)|グラデーションの楕円の x 半径を取得します。|
|[CD2DRadialGradientBrush::GetRadiusY](#getradiusy)|グラデーションの楕円の y 半径を取得します。|
|[CD2DRadialGradientBrush::SetCenter](#setcenter)|ブラシの座標空間でグラデーションの楕円の中心を指定します。|
|[CD2DRadialGradientBrush::SetGradientOriginOffset](#setgradientoriginoffset)|グラデーションの楕円の中心を基準としたグラデーションの原点のオフセットを指定します|
|[CD2DRadialGradientBrush::SetRadiusX](#setradiusx)|ブラシの座標空間でグラデーションの楕円の x 半径を指定します。|
|[CD2DRadialGradientBrush::SetRadiusY](#setradiusy)|ブラシの座標空間でグラデーションの楕円の y 半径を指定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush *](#operator_id2d1radialgradientbrush_star)|返します ID2D1RadialGradientBrush インターフェイス|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CD2DRadialGradientBrush::m_pRadialGradientBrush](#m_pradialgradientbrush)|ID2D1RadialGradientBrush へのポインター。|
|[CD2DRadialGradientBrush::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|Center、グラデーションの原点のオフセットと x 半径と y 半径ブラシのグラデーションのです。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="_dtorcd2dradialgradientbrush"></a>  CD2DRadialGradientBrush:: ~ CD2DRadialGradientBrush

デストラクターです。 D2D 放射状グラデーション ブラシ オブジェクトが破棄されるときに呼び出されます。

```
virtual ~CD2DRadialGradientBrush();
```

##  <a name="attach"></a>  CD2DRadialGradientBrush::Attach

既存のリソース インターフェイス オブジェクトにアタッチします

```
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>パラメーター

*pResource*<br/>
既存のリソース インターフェイスです。 NULL にすることはできません。

##  <a name="cd2dradialgradientbrush"></a>  CD2DRadialGradientBrush::CD2DRadialGradientBrush

CD2DLinearGradientBrush オブジェクトを構築します。

```
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>パラメーター

*pParentTarget*<br/>
レンダー ターゲットへのポインター。

*gradientStops*<br/>
D2D1_GRADIENT_STOP 構造体の配列へのポインター。

*gradientStopsCount*<br/>
GradientStops 配列内のグラデーションの分岐点の数を指定する 1 以上の値。

*RadialGradientBrushProperties*<br/>
Center、グラデーションの原点のオフセットと x 半径と y 半径ブラシのグラデーションのです。

*colorInterpolationGamma*<br/>
グラデーションの分岐点間の補間を実行する色で領域。

*extendMode*<br/>
[0, 1] の正規化された範囲外のグラデーションの動作です。

*pBrushProperties*<br/>
不透明度と、ブラシの変換へのポインター。

*bAutoDestroy*<br/>
所有者 (pParentTarget) によって、オブジェクトが破棄されることを示します。

##  <a name="create"></a>  CD2DRadialGradientBrush::Create

CD2DRadialGradientBrush を作成します。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>パラメーター

*pRenderTarget*<br/>
レンダー ターゲットへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功すると、S_OK を返します。 それ以外の場合、HRESULT エラー コードを返します。

##  <a name="destroy"></a>  CD2DRadialGradientBrush::Destroy

CD2DRadialGradientBrush オブジェクトを破棄します。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DRadialGradientBrush::Detach

オブジェクトからリソースのインターフェイスをデタッチします。

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>戻り値

インターフェイスのデタッチされたリソースへのポインター。

##  <a name="get"></a>  CD2DRadialGradientBrush::Get

返します ID2D1RadialGradientBrush インターフェイス

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>戻り値

ID2D1RadialGradientBrush インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="getcenter"></a>  CD2DRadialGradientBrush::GetCenter

グラデーションの楕円の中心を取得します。

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>戻り値

グラデーションの楕円の中心。 この値は、ブラシの座標空間で表されます

##  <a name="getgradientoriginoffset"></a>  CD2DRadialGradientBrush::GetGradientOriginOffset

グラデーションの楕円の中心を基準としたグラデーションの原点のオフセットを取得します。

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>戻り値

グラデーションの原点グラデーション楕円の中心からのオフセット。 この値は、ブラシの座標空間で表されます

##  <a name="getradiusx"></a>  CD2DRadialGradientBrush::GetRadiusX

グラデーションの楕円の x 半径を取得します。

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>戻り値

グラデーションの楕円の x 半径。 この値は、ブラシの座標空間で表されます

##  <a name="getradiusy"></a>  CD2DRadialGradientBrush::GetRadiusY

グラデーションの楕円の y 半径を取得します。

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>戻り値

グラデーションの楕円の y 半径。 この値は、ブラシの座標空間で表されます

##  <a name="m_pradialgradientbrush"></a>  CD2DRadialGradientBrush::m_pRadialGradientBrush

ID2D1RadialGradientBrush へのポインター。

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

##  <a name="m_radialgradientbrushproperties"></a>  CD2DRadialGradientBrush::m_RadialGradientBrushProperties

Center、グラデーションの原点のオフセットと x 半径と y 半径ブラシのグラデーションのです。

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

##  <a name="operator_id2d1radialgradientbrush_star"></a>  CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush*

返します ID2D1RadialGradientBrush インターフェイス

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>戻り値

ID2D1RadialGradientBrush インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="setcenter"></a>  CD2DRadialGradientBrush::SetCenter

ブラシの座標空間でグラデーションの楕円の中心を指定します。

```
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
ブラシの座標空間で、グラデーションの楕円の中心

##  <a name="setgradientoriginoffset"></a>  CD2DRadialGradientBrush::SetGradientOriginOffset

グラデーションの楕円の中心を基準としたグラデーションの原点のオフセットを指定します

```
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>パラメーター

*gradientOriginOffset*<br/>
グラデーションの原点グラデーション楕円の中心からのオフセット

##  <a name="setradiusx"></a>  CD2DRadialGradientBrush::SetRadiusX

ブラシの座標空間でグラデーションの楕円の x 半径を指定します。

```
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>パラメーター

*radiusX*<br/>
グラデーションの楕円の x 半径。 この値は、ブラシの座標空間で、します。

##  <a name="setradiusy"></a>  CD2DRadialGradientBrush::SetRadiusY

ブラシの座標空間でグラデーションの楕円の y 半径を指定します。

```
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>パラメーター

*radiusY*<br/>
グラデーションの楕円の y 半径。 この値は、ブラシの座標空間で、します。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
