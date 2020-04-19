---
title: CMFCDropDownToolBar クラス
ms.date: 11/19/2018
f1_keywords:
- CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::AllowShowOnPaneMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadBitmap
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::LoadToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnLButtonUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnMouseMove
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnSendCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolBar::OnUpdateCmdUI
helpviewer_keywords:
- CMFCDropDownToolBar [MFC], AllowShowOnPaneMenu
- CMFCDropDownToolBar [MFC], LoadBitmap
- CMFCDropDownToolBar [MFC], LoadToolBar
- CMFCDropDownToolBar [MFC], OnLButtonUp
- CMFCDropDownToolBar [MFC], OnMouseMove
- CMFCDropDownToolBar [MFC], OnSendCommand
- CMFCDropDownToolBar [MFC], OnUpdateCmdUI
ms.assetid: 78818ec5-83ce-42fa-a0d4-2d9d5ecc8770
ms.openlocfilehash: f2c4135d2a27928dbde4299fa1f8eda42237d893
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62238074"
---
# <a name="cmfcdropdowntoolbar-class"></a>CMFCDropDownToolBar クラス

ユーザーがトップレベルのツール バー ボタンを押し続けたときに表示されるツール バーです。

   詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。
## <a name="syntax"></a>構文

```
class CMFCDropDownToolBar : public CMFCToolBar
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCDropDownToolBar::AllowShowOnPaneMenu](#allowshowonpanemenu)|( `CPane::AllowShowOnPaneMenu`をオーバーライドします)。|
|[CMFCDropDownToolBar::LoadBitmap](#loadbitmap)|(上書き[CMFCToolBar::LoadBitmap](../../mfc/reference/cmfctoolbar-class.md#loadbitmap))。|
|[CMFCDropDownToolBar::LoadToolBar](#loadtoolbar)|(上書き[CMFCToolBar::LoadToolBar](../../mfc/reference/cmfctoolbar-class.md#loadtoolbar))。|
|[CMFCDropDownToolBar::OnLButtonUp](#onlbuttonup)||
|[CMFCDropDownToolBar::OnMouseMove](#onmousemove)||
|[CMFCDropDownToolBar::OnSendCommand](#onsendcommand)|( `CMFCToolBar::OnSendCommand`をオーバーライドします)。|
|[CMFCDropDownToolBar::OnUpdateCmdUI](#onupdatecmdui)|(上書き[CMFCToolBar::OnUpdateCmdUI](cmfctoolbar-class.md)します。|

### <a name="remarks"></a>Remarks

A`CMFCDropDownToolBar`オブジェクトは、ポップアップ メニューの動作では、ツールバーの外観を結合します。 ユーザーが押すし、ドロップダウン ツール バー ボタンを保持 (を参照してください[CMFCDropDownToolbarButton クラス](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md))、ドロップダウン ツールバーが表示され、ユーザーはまでスクロールし、マウスを解放してドロップダウン ツール バーからボタンを選択することができますボタンをクリックします。 ドロップダウン ツールバー ボタンを選択すると、そのボタンが最上位レベルのツールバーの現在のボタンとして表示されます。

ドロップダウン ツールバーのカスタマイズや、ドッキングされていることはできませんし、ティアオフ状態はありません。

次の図は、`CMFCDropDownToolBar`オブジェクト。

![CMFCDropDownToolbar の例](../../mfc/reference/media/cmfcdropdown.png "CMFCDropDownToolbar の例")

作成する、`CMFCDropDownToolBar`オブジェクトの通常のツールバーを作成すると同じ方法 (を参照してください[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md))。

親ツールバーのドロップダウン ツール バーを挿入します。

1. 親ツール バー リソースでボタンのダミー リソース ID を予約します。

2. 作成、`CMFCDropDownToolBarButton`ドロップダウン ツール バーを格納しているオブジェクト (詳細については、次を参照してください。 [CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md#cmfcdropdowntoolbarbutton))。

3. ダミー ボタンに置き換える、`CMFCDropDownToolBarButton`オブジェクトを使用して[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)します。

ツール バー ボタンの詳細については、次を参照してください。[チュートリアル。コントロールのツールバーに追加](../../mfc/walkthrough-putting-controls-on-toolbars.md)します。 ドロップダウン ツール バーの例は、サンプル プロジェクト VisualStudioDemo を参照してください。

## <a name="example"></a>例

次の例では、使用する方法、`Create`メソッドで、`CMFCDropDownToolBar`クラス。 このコード スニペットの一部、 [Visual Studio のデモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_VisualStudioDemo#29](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#30](../../mfc/codesnippet/cpp/cmfcdropdowntoolbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCDropDownToolBar](../../mfc/reference/cmfcdropdowntoolbar-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdropdowntoolbar.h

##  <a name="allowshowonpanemenu"></a>  CMFCDropDownToolBar::AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="loadbitmap"></a>  CMFCDropDownToolBar::LoadBitmap

アプリケーション リソースからツール バー イメージを読み込みます。

```
virtual BOOL LoadBitmap(
    UINT uiResID,
    UINT uiColdResID=0,
    UINT uiMenuResID=0,
    BOOL bLocked=FALSE,
    UINT uiDisabledResID=0,
    UINT uiMenuDisabledResID=0);
```

### <a name="parameters"></a>パラメーター

*uiResID*<br/>
[in]ツールバーのホット イメージを参照するビットマップのリソース ID。

*uiColdResID*<br/>
[in]ツールバーのコールド イメージを参照するビットマップのリソース ID。

*uiMenuResID*<br/>
[in]通常のメニュー画像を参照するビットマップのリソース ID。

*bLocked*<br/>
[in]ツールバーをロックする場合は TRUEそれ以外の場合は FALSE です。

*uiDisabledResID*<br/>
[in]ツールバーの無効イメージを参照するビットマップのリソース ID。

*uiMenuDisabledResID*<br/>
[in]メニューの無効イメージを参照するビットマップのリソース ID。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は 0 以外。それ以外の場合は 0。

### <a name="remarks"></a>Remarks

[CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex) メソッドはこのメソッドを呼び出して、ツール バーに関連付けられたイメージを読み込みます。 このメソッドをオーバーライドして、イメージ リソースのカスタムの読み込みを実行します。

ツール バーの作成後に、 `LoadBitmapEx` メソッドを呼び出して追加のイメージを読み込みます。

##  <a name="loadtoolbar"></a>  CMFCDropDownToolBar::LoadToolBar

```
virtual BOOL LoadToolBar(
    UINT uiResID,
    UINT uiColdResID = 0,
    UINT uiMenuResID = 0,
    BOOL = FALSE,
    UINT uiDisabledResID = 0,
    UINT uiMenuDisabledResID = 0,
    UINT uiHotResID = 0);
```

### <a name="parameters"></a>パラメーター

[in]*uiResID*<br/>

[in] *uiColdResID*<br/>

[in]*uiMenuResID*<br/>

[in]*BOOL*<br/>

[in] *uiDisabledResID*<br/>

[in] *uiMenuDisabledResID*<br/>

[in] *uiHotResID*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="onlbuttonup"></a>  CMFCDropDownToolBar::OnLButtonUp

```
afx_msg void OnLButtonUp(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

[in]*nFlags*<br/>

[in]*ポイント*<br/>

### <a name="remarks"></a>Remarks

##  <a name="onmousemove"></a>  CMFCDropDownToolBar::OnMouseMove

```
afx_msg void OnMouseMove(
    UINT nFlags,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

[in]*nFlags*<br/>

[in]*ポイント*<br/>

### <a name="remarks"></a>Remarks

##  <a name="onsendcommand"></a>  CMFCDropDownToolBar::OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>パラメーター

[in]*pButton*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="onupdatecmdui"></a>  CMFCDropDownToolBar::OnUpdateCmdUI

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>パラメーター

[in]*pTarget*<br/>

[in]*持たず*<br/>

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBar::Create](../../mfc/reference/cmfctoolbar-class.md#create)<br/>
[CMFCToolBar::ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[CMFCDropDownToolbarButton クラス](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)<br/>
[チュートリアル: ツール バーへのコントロールの追加](../../mfc/walkthrough-putting-controls-on-toolbars.md)
