---
title: CHwndRenderTarget クラス
ms.date: 11/04/2016
f1_keywords:
- CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::CHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::Attach
- AFXRENDERTARGET/CHwndRenderTarget::CheckWindowState
- AFXRENDERTARGET/CHwndRenderTarget::Create
- AFXRENDERTARGET/CHwndRenderTarget::Detach
- AFXRENDERTARGET/CHwndRenderTarget::GetHwnd
- AFXRENDERTARGET/CHwndRenderTarget::GetHwndRenderTarget
- AFXRENDERTARGET/CHwndRenderTarget::ReCreate
- AFXRENDERTARGET/CHwndRenderTarget::Resize
- AFXRENDERTARGET/CHwndRenderTarget::m_pHwndRenderTarget
helpviewer_keywords:
- CHwndRenderTarget [MFC], CHwndRenderTarget
- CHwndRenderTarget [MFC], Attach
- CHwndRenderTarget [MFC], CheckWindowState
- CHwndRenderTarget [MFC], Create
- CHwndRenderTarget [MFC], Detach
- CHwndRenderTarget [MFC], GetHwnd
- CHwndRenderTarget [MFC], GetHwndRenderTarget
- CHwndRenderTarget [MFC], ReCreate
- CHwndRenderTarget [MFC], Resize
- CHwndRenderTarget [MFC], m_pHwndRenderTarget
ms.assetid: aa65b69f-7202-46ea-af81-ef325da0b840
ms.openlocfilehash: bf446cdf1ea064943ff92d66ac89b0e4177e6910
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345787"
---
# <a name="chwndrendertarget-class"></a>CHwndRenderTarget クラス

ID2D1HwndRenderTarget のラッパーです。

## <a name="syntax"></a>構文

```
class CHwndRenderTarget : public CRenderTarget;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CHwndRenderTarget::CHwndRenderTarget](#chwndrendertarget)|HWND から CHwndRenderTarget オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CHwndRenderTarget::Attach](#attach)|既存の接続は、ターゲット オブジェクトのインターフェイスを表示します。|
|[CHwndRenderTarget::CheckWindowState](#checkwindowstate)|このレンダー ターゲットに関連付けられている HWND がオクルー ジョンかどうかを示します。|
|[CHwndRenderTarget::Create](#create)|ウィンドウに関連付けられているレンダー ターゲットを作成します。|
|[CHwndRenderTarget::Detach](#detach)|オブジェクトからのレンダー ターゲットのインターフェイスをデタッチします。|
|[CHwndRenderTarget::GetHwnd](#gethwnd)|レンダリング ターゲットをこれに関連付けられている HWND を返します。|
|[CHwndRenderTarget::GetHwndRenderTarget](#gethwndrendertarget)|ID2D1HwndRenderTarget インターフェイスを返します。|
|[CHwndRenderTarget::ReCreate](#recreate)|ウィンドウに関連付けられているレンダー ターゲットを再作成します。|
|[CHwndRenderTarget::Resize](#resize)|レンダー ターゲットのサイズを指定したピクセルのサイズに変更します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CHwndRenderTarget::operator ID2D1HwndRenderTarget*](#operator_id2d1hwndrendertarget_star)|ID2D1HwndRenderTarget インターフェイスを返します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CHwndRenderTarget::m_pHwndRenderTarget](#m_phwndrendertarget)|ID2D1HwndRenderTarget オブジェクトへのポインター。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

[CHwndRenderTarget](../../mfc/reference/chwndrendertarget-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="attach"></a>  CHwndRenderTarget::Attach

既存の接続は、ターゲット オブジェクトのインターフェイスを表示します。

```
void Attach(ID2D1HwndRenderTarget* pTarget);
```

### <a name="parameters"></a>パラメーター

*pTarget*<br/>
既存のレンダー ターゲットのインターフェイスです。 NULL にすることはできません。

##  <a name="checkwindowstate"></a>  CHwndRenderTarget::CheckWindowState

このレンダー ターゲットに関連付けられている HWND がオクルー ジョンかどうかを示します。

```
D2D1_WINDOW_STATE CheckWindowState() const;
```

### <a name="return-value"></a>戻り値

これに関連付けられている HWND がレンダー ターゲットであるかどうかを示す値が遮蔽されます。

##  <a name="chwndrendertarget"></a>  CHwndRenderTarget::CHwndRenderTarget

HWND から CHwndRenderTarget オブジェクトを構築します。

```
CHwndRenderTarget(HWND hwnd = NULL);
```

### <a name="parameters"></a>パラメーター

*hwnd*<br/>
これに関連付けられている HWND レンダー ターゲット

##  <a name="create"></a>  CHwndRenderTarget::Create

ウィンドウに関連付けられているレンダー ターゲットを作成します。

```
BOOL Create(HWND hWnd);
```

### <a name="parameters"></a>パラメーター

*hWnd*<br/>
これに関連付けられている HWND レンダー ターゲット

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE が返されます

##  <a name="detach"></a>  CHwndRenderTarget::Detach

オブジェクトからのレンダー ターゲットのインターフェイスをデタッチします。

```
ID2D1HwndRenderTarget* Detach();
```

### <a name="return-value"></a>戻り値

デタッチされたへのポインターは、ターゲットのインターフェイスをレンダリングします。

##  <a name="gethwnd"></a>  CHwndRenderTarget::GetHwnd

レンダリング ターゲットをこれに関連付けられている HWND を返します。

```
HWND GetHwnd() const;
```

### <a name="return-value"></a>戻り値

これに関連付けられている HWND はレンダー ターゲットです。

##  <a name="gethwndrendertarget"></a>  CHwndRenderTarget::GetHwndRenderTarget

ID2D1HwndRenderTarget インターフェイスを返します。

```
ID2D1HwndRenderTarget* GetHwndRenderTarget();
```

### <a name="return-value"></a>戻り値

ID2D1HwndRenderTarget インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="m_phwndrendertarget"></a>  CHwndRenderTarget::m_pHwndRenderTarget

ID2D1HwndRenderTarget オブジェクトへのポインター。

```
ID2D1HwndRenderTarget* m_pHwndRenderTarget;
```

##  <a name="operator_id2d1hwndrendertarget_star"></a>  CHwndRenderTarget::operator ID2D1HwndRenderTarget*

ID2D1HwndRenderTarget インターフェイスを返します。

```
operator ID2D1HwndRenderTarget*();
```

### <a name="return-value"></a>戻り値

ID2D1HwndRenderTarget インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="recreate"></a>  CHwndRenderTarget::ReCreate

ウィンドウに関連付けられているレンダー ターゲットを再作成します。

```
BOOL ReCreate(HWND hWnd);
```

### <a name="parameters"></a>パラメーター

*hWnd*<br/>
これに関連付けられている HWND レンダー ターゲット

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="resize"></a>  CHwndRenderTarget::Resize

レンダー ターゲットのサイズを指定したピクセルのサイズに変更します。

```
BOOL Resize(const CD2DSizeU& size);
```

### <a name="parameters"></a>パラメーター

*size*<br/>
デバイス ピクセル単位で、レンダー ターゲットの新しいサイズ

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
