---
title: CD2DLayer クラス
ms.date: 11/04/2016
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
ms.openlocfilehash: 28ebe19b0f28692116a0b95721ff2e5490ad7e68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391232"
---
# <a name="cd2dlayer-class"></a>CD2DLayer クラス

ID2D1Layer のラッパーです。

## <a name="syntax"></a>構文

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DLayer::CD2DLayer](#cd2dlayer)|CD2DLayer オブジェクトを構築します。|
|[CD2DLayer:: ~ CD2DLayer](#_dtorcd2dlayer)|デストラクターです。 D2D レイヤー オブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DLayer::Attach](#attach)|既存のリソース インターフェイス オブジェクトにアタッチします|
|[CD2DLayer::Create](#create)|CD2DLayer を作成します。 (上書き[CD2DResource::Create](../../mfc/reference/cd2dresource-class.md#create))。|
|[CD2DLayer::Destroy](#destroy)|CD2DLayer オブジェクトを破棄します。 (上書き[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy))。|
|[CD2DLayer::Detach](#detach)|オブジェクトからリソースのインターフェイスをデタッチします。|
|[CD2DLayer::Get](#get)|返します ID2D1Layer インターフェイス|
|[CD2DLayer::GetSize](#getsize)|デバイス非依存ピクセルで、レンダー ターゲットのサイズを返します|
|[CD2DLayer::IsValid](#isvalid)|リソースの有効性を確認します (上書き[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid))。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DLayer::operator ID2D1Layer*](#operator_id2d1layer_star)|返します ID2D1Layer インターフェイス|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CD2DLayer::m_pLayer](#m_player)|ID2D1Layer オブジェクトへのポインターを格納します。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="_dtorcd2dlayer"></a>  CD2DLayer:: ~ CD2DLayer

デストラクターです。 D2D レイヤー オブジェクトが破棄されるときに呼び出されます。

```
virtual ~CD2DLayer();
```

##  <a name="attach"></a>  CD2DLayer::Attach

既存のリソース インターフェイス オブジェクトにアタッチします

```
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>パラメーター

*pResource*<br/>
既存のリソース インターフェイスです。 NULL にすることはできません。

##  <a name="cd2dlayer"></a>  CD2DLayer::CD2DLayer

CD2DLayer オブジェクトを構築します。

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>パラメーター

*pParentTarget*<br/>
レンダー ターゲットへのポインター。

*bAutoDestroy*<br/>
所有者 (pParentTarget) によって、オブジェクトが破棄されることを示します。

##  <a name="create"></a>  CD2DLayer::Create

CD2DLayer を作成します。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>パラメーター

*pRenderTarget*<br/>
レンダー ターゲットへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功すると、S_OK を返します。 それ以外の場合、HRESULT エラー コードを返します。

##  <a name="destroy"></a>  CD2DLayer::Destroy

CD2DLayer オブジェクトを破棄します。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DLayer::Detach

オブジェクトからリソースのインターフェイスをデタッチします。

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>戻り値

インターフェイスのデタッチされたリソースへのポインター。

##  <a name="get"></a>  CD2DLayer::Get

返します ID2D1Layer インターフェイス

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>戻り値

ID2D1Layer インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="getsize"></a>  CD2DLayer::GetSize

デバイス非依存ピクセルで、レンダー ターゲットのサイズを返します

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>戻り値

デバイス非依存ピクセルで、レンダー ターゲットの現在のサイズ

##  <a name="isvalid"></a>  CD2DLayer::IsValid

リソースの有効性のチェック

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>戻り値

リソースが有効な場合は TRUE。それ以外の場合は FALSE です。

##  <a name="m_player"></a>  CD2DLayer::m_pLayer

ID2D1Layer オブジェクトへのポインターを格納します。

```
ID2D1Layer* m_pLayer;
```

##  <a name="operator_id2d1layer_star"></a>  CD2DLayer::operator ID2D1Layer*

返します ID2D1Layer インターフェイス

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>戻り値

ID2D1Layer インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
