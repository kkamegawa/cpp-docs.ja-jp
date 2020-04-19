---
title: CDCRenderTarget クラス
ms.date: 11/04/2016
f1_keywords:
- CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::CDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::Attach
- AFXRENDERTARGET/CDCRenderTarget::BindDC
- AFXRENDERTARGET/CDCRenderTarget::Create
- AFXRENDERTARGET/CDCRenderTarget::Detach
- AFXRENDERTARGET/CDCRenderTarget::GetDCRenderTarget
- AFXRENDERTARGET/CDCRenderTarget::m_pDCRenderTarget
helpviewer_keywords:
- CDCRenderTarget [MFC], CDCRenderTarget
- CDCRenderTarget [MFC], Attach
- CDCRenderTarget [MFC], BindDC
- CDCRenderTarget [MFC], Create
- CDCRenderTarget [MFC], Detach
- CDCRenderTarget [MFC], GetDCRenderTarget
- CDCRenderTarget [MFC], m_pDCRenderTarget
ms.assetid: aa8059c9-08e6-49e4-9b8c-00fa54077a61
ms.openlocfilehash: 70169d2b89d9ea657898f7a96dea27556023d4e2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62168174"
---
# <a name="cdcrendertarget-class"></a>CDCRenderTarget クラス

ID2D1DCRenderTarget のラッパーです。

## <a name="syntax"></a>構文

```
class CDCRenderTarget : public CRenderTarget;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDCRenderTarget::CDCRenderTarget](#cdcrendertarget)|CDCRenderTarget オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDCRenderTarget::Attach](#attach)|既存の接続は、ターゲット オブジェクトのインターフェイスを表示します。|
|[CDCRenderTarget::BindDC](#binddc)|描画コマンドを発行先デバイス コンテキストにレンダー ターゲットをバインドします。|
|[CDCRenderTarget::Create](#create)|CDCRenderTarget を作成します。|
|[CDCRenderTarget::Detach](#detach)|オブジェクトからのレンダー ターゲットのインターフェイスをデタッチします。|
|[CDCRenderTarget::GetDCRenderTarget](#getdcrendertarget)|返します ID2D1DCRenderTarget インターフェイス|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CDCRenderTarget::operator ID2D1DCRenderTarget*](#operator_id2d1dcrendertarget_star)|返します ID2D1DCRenderTarget インターフェイス|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CDCRenderTarget::m_pDCRenderTarget](#m_pdcrendertarget)|ID2D1DCRenderTarget オブジェクトへのポインター。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CDCRenderTarget](../../mfc/reference/cdcrendertarget-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="attach"></a>  CDCRenderTarget::Attach

既存の接続は、ターゲット オブジェクトのインターフェイスを表示します。

```
void Attach(ID2D1DCRenderTarget* pTarget);
```

### <a name="parameters"></a>パラメーター

*pTarget*<br/>
既存のレンダー ターゲットのインターフェイスです。 NULL にすることはできません。

##  <a name="binddc"></a>  CDCRenderTarget::BindDC

描画コマンドを発行先デバイス コンテキストにレンダー ターゲットをバインドします。

```
BOOL BindDC(
    const CDC& dc,
    const CRect& rect);
```

### <a name="parameters"></a>パラメーター

*dc*<br/>
デバイス コンテキスト レンダー ターゲットが描画コマンドを発行するには

*rect*<br/>
レンダー ターゲットがバインドされているデバイス コンテキスト (HDC) へのハンドルのサイズ

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="cdcrendertarget"></a>  CDCRenderTarget::CDCRenderTarget

CDCRenderTarget オブジェクトを構築します。

```
CDCRenderTarget();
```

##  <a name="create"></a>  CDCRenderTarget::Create

CDCRenderTarget を作成します。

```
BOOL Create(const D2D1_RENDER_TARGET_PROPERTIES& props);
```

### <a name="parameters"></a>パラメーター

*プロパティ*<br/>
レンダリング モード、ピクセル形式、リモート処理オプション、DPI 情報、およびハードウェアのレンダリングに必要な最小の DirectX サポートします。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="detach"></a>  CDCRenderTarget::Detach

オブジェクトからのレンダー ターゲットのインターフェイスをデタッチします。

```
ID2D1DCRenderTarget* Detach();
```

### <a name="return-value"></a>戻り値

デタッチされたへのポインターは、ターゲットのインターフェイスをレンダリングします。

##  <a name="getdcrendertarget"></a>  CDCRenderTarget::GetDCRenderTarget

返します ID2D1DCRenderTarget インターフェイス

```
ID2D1DCRenderTarget* GetDCRenderTarget();
```

### <a name="return-value"></a>戻り値

ID2D1DCRenderTarget インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="m_pdcrendertarget"></a>  CDCRenderTarget::m_pDCRenderTarget

ID2D1DCRenderTarget オブジェクトへのポインター。

```
ID2D1DCRenderTarget* m_pDCRenderTarget;
```

##  <a name="operator_id2d1dcrendertarget_star"></a>  CDCRenderTarget::operator ID2D1DCRenderTarget*

返します ID2D1DCRenderTarget インターフェイス

```
operator ID2D1DCRenderTarget*();
```

### <a name="return-value"></a>戻り値

ID2D1DCRenderTarget インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
