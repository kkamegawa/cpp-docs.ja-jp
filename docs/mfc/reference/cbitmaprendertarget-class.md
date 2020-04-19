---
title: CBitmapRenderTarget クラス
ms.date: 11/04/2016
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
ms.openlocfilehash: 8c110ec8f7c232180bf054e8e4ba90a18f1902c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388438"
---
# <a name="cbitmaprendertarget-class"></a>CBitmapRenderTarget クラス

ID2D1BitmapRenderTarget のラッパーです。

## <a name="syntax"></a>構文

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|CBitmapRenderTarget オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CBitmapRenderTarget::Attach](#attach)|既存の接続は、ターゲット オブジェクトのインターフェイスを表示します。|
|[CBitmapRenderTarget::Detach](#detach)|オブジェクトからのレンダー ターゲットのインターフェイスをデタッチします。|
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|このレンダー ターゲットのビットマップを取得します。 返されるビットマップは、描画操作に使用できます。|
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|返します ID2D1BitmapRenderTarget インターフェイス|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *](#operator_id2d1bitmaprendertarget_star)|返します ID2D1BitmapRenderTarget インターフェイス|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|ID2D1BitmapRenderTarget オブジェクトへのポインター。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="attach"></a>  CBitmapRenderTarget::Attach

既存の接続は、ターゲット オブジェクトのインターフェイスを表示します。

```
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>パラメーター

*pTarget*<br/>
既存のレンダー ターゲットのインターフェイスです。 NULL にすることはできません。

##  <a name="cbitmaprendertarget"></a>  CBitmapRenderTarget::CBitmapRenderTarget

CBitmapRenderTarget オブジェクトを構築します。

```
CBitmapRenderTarget();
```

##  <a name="detach"></a>  CBitmapRenderTarget::Detach

オブジェクトからのレンダー ターゲットのインターフェイスをデタッチします。

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>戻り値

デタッチされたへのポインターは、ターゲットのインターフェイスをレンダリングします。

##  <a name="getbitmap"></a>  CBitmapRenderTarget::GetBitmap

このレンダー ターゲットのビットマップを取得します。 返されるビットマップは、描画操作に使用できます。

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>パラメーター

*bitmap*<br/>
このメソッドが戻るときに、このレンダー ターゲットの有効なビットマップが含まれています。 このビットマップは、描画操作に使用できます。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="getbitmaprendertarget"></a>  CBitmapRenderTarget::GetBitmapRenderTarget

返します ID2D1BitmapRenderTarget インターフェイス

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>戻り値

ID2D1BitmapRenderTarget インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="m_pbitmaprendertarget"></a>  CBitmapRenderTarget::m_pBitmapRenderTarget

ID2D1BitmapRenderTarget オブジェクトへのポインター。

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

##  <a name="operator_id2d1bitmaprendertarget_star"></a>  CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *

返します ID2D1BitmapRenderTarget インターフェイス

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>戻り値

ID2D1BitmapRenderTarget インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
