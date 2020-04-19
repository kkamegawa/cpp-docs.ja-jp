---
title: CD2DLinearGradientBrush クラス
ms.date: 11/04/2016
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
ms.openlocfilehash: d86235893d1f238f4cba9c927fad17f29060e591
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348628"
---
# <a name="cd2dlineargradientbrush-class"></a>CD2DLinearGradientBrush クラス

ID2D1LinearGradientBrush のラッパーです。

## <a name="syntax"></a>構文

```
class CD2DLinearGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](#cd2dlineargradientbrush)|CD2DLinearGradientBrush オブジェクトを構築します。|
|[CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush](#_dtorcd2dlineargradientbrush)|デストラクターです。 D2D 線状グラデーション ブラシ オブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DLinearGradientBrush::Attach](#attach)|既存のリソース インターフェイス オブジェクトにアタッチします|
|[CD2DLinearGradientBrush::Create](#create)|CD2DLinearGradientBrush を作成します。 (上書き[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create))。|
|[CD2DLinearGradientBrush::Destroy](#destroy)|CD2DLinearGradientBrush オブジェクトを破棄します。 (上書き[CD2DGradientBrush::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy))。|
|[CD2DLinearGradientBrush::Detach](#detach)|オブジェクトからリソースのインターフェイスをデタッチします。|
|[CD2DLinearGradientBrush::Get](#get)|返します ID2D1LinearGradientBrush インターフェイス|
|[CD2DLinearGradientBrush::GetEndPoint](#getendpoint)|線形グラデーションの終点の座標を取得します。|
|[CD2DLinearGradientBrush::GetStartPoint](#getstartpoint)|線形グラデーションの開始座標を取得します。|
|[CD2DLinearGradientBrush::SetEndPoint](#setendpoint)|ブラシの座標空間での線形グラデーションの終点の座標を設定します。|
|[CD2DLinearGradientBrush::SetStartPoint](#setstartpoint)|ブラシの座標空間で線状グラデーションの開始座標を設定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush*](#operator_id2d1lineargradientbrush_star)|返します ID2D1LinearGradientBrush インターフェイス|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CD2DLinearGradientBrush::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|開始およびグラデーションの始点と終点。|
|[CD2DLinearGradientBrush::m_pLinearGradientBrush](#m_plineargradientbrush)|ID2D1LinearGradientBrush へのポインター。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DLinearGradientBrush`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="_dtorcd2dlineargradientbrush"></a>  CD2DLinearGradientBrush:: ~ CD2DLinearGradientBrush

デストラクターです。 D2D 線状グラデーション ブラシ オブジェクトが破棄されるときに呼び出されます。

```
virtual ~CD2DLinearGradientBrush();
```

##  <a name="attach"></a>  CD2DLinearGradientBrush::Attach

既存のリソース インターフェイス オブジェクトにアタッチします

```
void Attach(ID2D1LinearGradientBrush* pResource);
```

### <a name="parameters"></a>パラメーター

*pResource*<br/>
既存のリソース インターフェイスです。 NULL にすることはできません。

##  <a name="cd2dlineargradientbrush"></a>  CD2DLinearGradientBrush::CD2DLinearGradientBrush

CD2DLinearGradientBrush オブジェクトを構築します。

```
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,
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

*LinearGradientBrushProperties*<br/>
開始およびグラデーションの始点と終点。

*colorInterpolationGamma*<br/>
グラデーションの分岐点間の補間を実行する色で領域。

*extendMode*<br/>
[0, 1] の正規化された範囲外のグラデーションの動作です。

*pBrushProperties*<br/>
不透明度と、ブラシの変換へのポインター。

*bAutoDestroy*<br/>
所有者 (pParentTarget) によって、オブジェクトが破棄されることを示します。

##  <a name="create"></a>  CD2DLinearGradientBrush::Create

CD2DLinearGradientBrush を作成します。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>パラメーター

*pRenderTarget*<br/>
レンダー ターゲットへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功すると、S_OK を返します。 それ以外の場合、HRESULT エラー コードを返します。

##  <a name="destroy"></a>  CD2DLinearGradientBrush::Destroy

CD2DLinearGradientBrush オブジェクトを破棄します。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DLinearGradientBrush::Detach

オブジェクトからリソースのインターフェイスをデタッチします。

```
ID2D1LinearGradientBrush* Detach();
```

### <a name="return-value"></a>戻り値

インターフェイスのデタッチされたリソースへのポインター。

##  <a name="get"></a>  CD2DLinearGradientBrush::Get

返します ID2D1LinearGradientBrush インターフェイス

```
ID2D1LinearGradientBrush* Get();
```

### <a name="return-value"></a>戻り値

ID2D1LinearGradientBrush インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="getendpoint"></a>  CD2DLinearGradientBrush::GetEndPoint

線形グラデーションの終点の座標を取得します。

```
CD2DPointF GetEndPoint() const;
```

### <a name="return-value"></a>戻り値

ブラシの座標空間での線形グラデーションの終了の 2 次元座標

##  <a name="getstartpoint"></a>  CD2DLinearGradientBrush::GetStartPoint

線形グラデーションの開始座標を取得します。

```
CD2DPointF GetStartPoint() const;
```

### <a name="return-value"></a>戻り値

ブラシの座標空間での線形グラデーションの開始の 2 次元座標

##  <a name="m_lineargradientbrushproperties"></a>  CD2DLinearGradientBrush::m_LinearGradientBrushProperties

開始およびグラデーションの始点と終点。

```
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;
```

##  <a name="m_plineargradientbrush"></a>  CD2DLinearGradientBrush::m_pLinearGradientBrush

ID2D1LinearGradientBrush へのポインター。

```
ID2D1LinearGradientBrush* m_pLinearGradientBrush;
```

##  <a name="operator_id2d1lineargradientbrush_star"></a>  CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush*

返します ID2D1LinearGradientBrush インターフェイス

```
operator ID2D1LinearGradientBrush*();
```

### <a name="return-value"></a>戻り値

ID2D1LinearGradientBrush インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="setendpoint"></a>  CD2DLinearGradientBrush::SetEndPoint

ブラシの座標空間での線形グラデーションの終点の座標を設定します。

```
void SetEndPoint(CD2DPointF point);
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
ブラシの座標空間での線形グラデーションの終了の 2 次元座標

##  <a name="setstartpoint"></a>  CD2DLinearGradientBrush::SetStartPoint

ブラシの座標空間で線状グラデーションの開始座標を設定します。

```
void SetStartPoint(CD2DPointF point);
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
ブラシの座標空間での線形グラデーションの開始の 2 次元座標

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
