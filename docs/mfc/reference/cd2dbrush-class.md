---
title: CD2DBrush クラス
ms.date: 11/04/2016
f1_keywords:
- CD2DBrush
- AFXRENDERTARGET/CD2DBrush
- AFXRENDERTARGET/CD2DBrush::CD2DBrush
- AFXRENDERTARGET/CD2DBrush::Attach
- AFXRENDERTARGET/CD2DBrush::Destroy
- AFXRENDERTARGET/CD2DBrush::Detach
- AFXRENDERTARGET/CD2DBrush::Get
- AFXRENDERTARGET/CD2DBrush::GetOpacity
- AFXRENDERTARGET/CD2DBrush::GetTransform
- AFXRENDERTARGET/CD2DBrush::IsValid
- AFXRENDERTARGET/CD2DBrush::SetOpacity
- AFXRENDERTARGET/CD2DBrush::SetTransform
- AFXRENDERTARGET/CD2DBrush::m_pBrush
- AFXRENDERTARGET/CD2DBrush::m_pBrushProperties
helpviewer_keywords:
- CD2DBrush [MFC], CD2DBrush
- CD2DBrush [MFC], Attach
- CD2DBrush [MFC], Destroy
- CD2DBrush [MFC], Detach
- CD2DBrush [MFC], Get
- CD2DBrush [MFC], GetOpacity
- CD2DBrush [MFC], GetTransform
- CD2DBrush [MFC], IsValid
- CD2DBrush [MFC], SetOpacity
- CD2DBrush [MFC], SetTransform
- CD2DBrush [MFC], m_pBrush
- CD2DBrush [MFC], m_pBrushProperties
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
ms.openlocfilehash: 1d079ec6c96f96919fde39b73297580ed2a0ac75
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391297"
---
# <a name="cd2dbrush-class"></a>CD2DBrush クラス

ID2D1Brush のラッパーです。

## <a name="syntax"></a>構文

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DBrush::CD2DBrush](#cd2dbrush)|CD2DBrush オブジェクトを構築します。|
|[CD2DBrush:: ~ CD2DBrush](#_dtorcd2dbrush)|デストラクターです。 D2D ブラシ オブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DBrush::Attach](#attach)|既存のリソース インターフェイス オブジェクトにアタッチします|
|[CD2DBrush::Destroy](#destroy)|CD2DBrush オブジェクトを破棄します。 (上書き[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy))。|
|[CD2DBrush::Detach](#detach)|オブジェクトからリソースのインターフェイスをデタッチします。|
|[CD2DBrush::Get](#get)|返します ID2D1Brush インターフェイス|
|[CD2DBrush::GetOpacity](#getopacity)|このブラシの不透明度を取得します。|
|[CD2DBrush::GetTransform](#gettransform)|レンダー ターゲットの現在の変換を取得します。|
|[CD2DBrush::IsValid](#isvalid)|リソースの有効性を確認します (上書き[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid))。|
|[CD2DBrush::SetOpacity](#setopacity)|このブラシの不透明度を設定します。|
|[CD2DBrush::SetTransform](#settransform)|既存の変換を置き換える、レンダー ターゲットに指定した変換を適用されます。 変換後のスペースですべての後続の描画操作が発生します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DBrush::operator ID2D1Brush *](#operator_id2d1brush_star)|返します ID2D1Brush インターフェイス|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CD2DBrush::m_pBrush](#m_pbrush)|ID2D1Brush オブジェクトへのポインターを格納します。|
|[CD2DBrush::m_pBrushProperties](#m_pbrushproperties)|ブラシのプロパティ。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="_dtorcd2dbrush"></a>  CD2DBrush:: ~ CD2DBrush

デストラクターです。 D2D ブラシ オブジェクトが破棄されるときに呼び出されます。

```
virtual ~CD2DBrush();
```

##  <a name="attach"></a>  CD2DBrush::Attach

既存のリソース インターフェイス オブジェクトにアタッチします。

```
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>パラメーター

*pResource*<br/>
既存のリソース インターフェイスです。 Nll は指定できません。

##  <a name="cd2dbrush"></a>  CD2DBrush::CD2DBrush

CD2DBrush オブジェクトを構築します。

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>パラメーター

*pParentTarget*<br/>
レンダー ターゲットへのポインター。

*pBrushProperties*<br/>
不透明度と、ブラシの変換へのポインター。

*bAutoDestroy*<br/>
所有者 (pParentTarget) によって、オブジェクトが破棄されることを示します。

##  <a name="destroy"></a>  CD2DBrush::Destroy

CD2DBrush オブジェクトを破棄します。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DBrush::Detach

オブジェクトからリソースのインターフェイスをデタッチします。

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>戻り値

インターフェイスのデタッチされたリソースへのポインター。

##  <a name="get"></a>  CD2DBrush::Get

返します ID2D1Brush インターフェイス

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>戻り値

ID2D1Brush インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="getopacity"></a>  CD2DBrush::GetOpacity

このブラシの不透明度を取得します。

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>戻り値

0 と、ブラシの不透明度を示す 1 の間の値。 この値は、定数の乗数、ブラシで塗りつぶされますすべてのピクセルのアルファ値を直線的にスケーリングします。 乗算は前に、不透明度の値は 0 ~ 1 の範囲にクランプされます。

##  <a name="gettransform"></a>  CD2DBrush::GetTransform

レンダー ターゲットの現在の変換を取得します。

```
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>パラメーター

*transform*<br/>
このエラーが返されるときに、レンダー ターゲットの現在の変換が含まれています。 このパラメーターは初期化せずに渡されます。

##  <a name="isvalid"></a>  CD2DBrush::IsValid

リソースの有効性のチェック

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>戻り値

リソースが有効な場合は TRUE。それ以外の場合は FALSE です。

##  <a name="m_pbrush"></a>  CD2DBrush::m_pBrush

ID2D1Brush オブジェクトへのポインターを格納します。

```
ID2D1Brush* m_pBrush;
```

##  <a name="m_pbrushproperties"></a>  CD2DBrush::m_pBrushProperties

ブラシのプロパティ。

```
CD2DBrushProperties* m_pBrushProperties;
```

##  <a name="operator_id2d1brush_star"></a>  CD2DBrush::operator ID2D1Brush*

返します ID2D1Brush インターフェイス

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>戻り値

ID2D1Brush インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="setopacity"></a>  CD2DBrush::SetOpacity

このブラシの不透明度を設定します。

```
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>パラメーター

*不透明度*<br/>
0 と、ブラシの不透明度を示す 1 の間の値。 この値は、定数の乗数、ブラシで塗りつぶされますすべてのピクセルのアルファ値を直線的にスケーリングします。 乗算は前に、不透明度の値は 0 ~ 1 の範囲にクランプされます。

##  <a name="settransform"></a>  CD2DBrush::SetTransform

既存の変換を置き換える、レンダー ターゲットに指定した変換を適用されます。 すべての後続の描画操作では、変換後の領域で発生します。

```
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>パラメーター

*transform*<br/>
レンダー ターゲットに適用する変換

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
