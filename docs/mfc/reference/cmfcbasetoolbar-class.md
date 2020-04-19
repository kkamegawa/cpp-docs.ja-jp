---
title: CMFCBaseToolBar クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar
- AFXBASETOOLBAR/CMFCBaseToolBar::GetDockingMode
- AFXBASETOOLBAR/CMFCBaseToolBar::GetMinSize
- AFXBASETOOLBAR/CMFCBaseToolBar::OnAfterChangeParent
helpviewer_keywords:
- CMFCBaseToolBar [MFC], GetDockingMode
- CMFCBaseToolBar [MFC], GetMinSize
- CMFCBaseToolBar [MFC], OnAfterChangeParent
ms.assetid: 5d79206d-55e4-46f8-b1b8-042e34d7f9da
ms.openlocfilehash: 7a6ccdaf3d78b9973505dd4e90ca76f671fce889
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403868"
---
# <a name="cmfcbasetoolbar-class"></a>CMFCBaseToolBar クラス

ツールバーの基本クラス。

## <a name="syntax"></a>構文

```
class CMFCBaseToolBar : public CPane
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCBaseToolBar::CMFCBaseToolBar`|既定のコンストラクターです。|
|`CMFCBaseToolBar::~CMFCBaseToolBar`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|`CMFCBaseToolBar::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|[CMFCBaseToolBar::GetDockingMode](#getdockingmode)|ドッキングのモードを返します。 (上書き[cbasepane::getdockingmode](../../mfc/reference/cbasepane-class.md#getdockingmode))。|
|[CMFCBaseToolBar::GetMinSize](#getminsize)|ツールバーの最小サイズを返します。 (上書き[CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize))。|
|[CMFCBaseToolBar::OnAfterChangeParent](#onafterchangeparent)|ウィンドウの親が変更された後、フレームワークによって呼び出されます。 (上書き[CBasePane::OnAfterChangeParent](../../mfc/reference/cbasepane-class.md#onafterchangeparent))。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxbasetoolbar.h

##  <a name="getdockingmode"></a>  CMFCBaseToolBar::GetDockingMode

ドッキングのモードを返します。

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>戻り値

ドッキングのモード。

##  <a name="getminsize"></a>  CMFCBaseToolBar::GetMinSize

ツールバーの最小サイズを返します。

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>パラメーター

*size*<br/>
[out]ツールバーの最小サイズ。

##  <a name="onafterchangeparent"></a>  CMFCBaseToolBar::OnAfterChangeParent

ウィンドウの親が変更された後、フレームワークによって呼び出されます。

```
virtual void OnAfterChangeParent(CWnd* pWndOldParent);
```

### <a name="parameters"></a>パラメーター

*pWndOldParent*<br/>
[in]前の親ウィンドウへのポインター。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
