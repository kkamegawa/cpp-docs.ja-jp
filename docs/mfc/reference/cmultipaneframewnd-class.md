---
title: CMultiPaneFrameWnd クラス
ms.date: 11/04/2016
f1_keywords:
- CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AddRecentPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::AdjustPaneFrames
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CalcExpectedDockedRect
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeAttached
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CanBeDockedToPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CheckGripperVisibility
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::CloseMiniFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ConvertToTabbedDocument
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::DockRecentPaneToMainFrame
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetCaptionText
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneContainerManager
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetFirstVisiblePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetPaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::GetVisiblePaneCount
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::InsertPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::LoadState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnDockToRecentPos
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnKillRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnPaneRecalcLayout
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnSetRollUpTimer
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::OnShowPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::PaneFromPoint
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemoveNonValidPanes
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::RemovePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::ReplacePane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SaveState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::Serialize
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetLastFocusedPane
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::SetPreDockState
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentDockSiteInfo
- AFXMULTIPANEFRAMEWND/CMultiPaneFrameWnd::StoreRecentTabRelatedInfo
helpviewer_keywords:
- CMultiPaneFrameWnd [MFC], AddPane
- CMultiPaneFrameWnd [MFC], AddRecentPane
- CMultiPaneFrameWnd [MFC], AdjustLayout
- CMultiPaneFrameWnd [MFC], AdjustPaneFrames
- CMultiPaneFrameWnd [MFC], CalcExpectedDockedRect
- CMultiPaneFrameWnd [MFC], CanBeAttached
- CMultiPaneFrameWnd [MFC], CanBeDockedToPane
- CMultiPaneFrameWnd [MFC], CheckGripperVisibility
- CMultiPaneFrameWnd [MFC], CloseMiniFrame
- CMultiPaneFrameWnd [MFC], ConvertToTabbedDocument
- CMultiPaneFrameWnd [MFC], DockFrame
- CMultiPaneFrameWnd [MFC], DockPane
- CMultiPaneFrameWnd [MFC], DockRecentPaneToMainFrame
- CMultiPaneFrameWnd [MFC], GetCaptionText
- CMultiPaneFrameWnd [MFC], GetPaneContainerManager
- CMultiPaneFrameWnd [MFC], GetFirstVisiblePane
- CMultiPaneFrameWnd [MFC], GetPane
- CMultiPaneFrameWnd [MFC], GetPaneCount
- CMultiPaneFrameWnd [MFC], GetVisiblePaneCount
- CMultiPaneFrameWnd [MFC], InsertPane
- CMultiPaneFrameWnd [MFC], LoadState
- CMultiPaneFrameWnd [MFC], OnDockToRecentPos
- CMultiPaneFrameWnd [MFC], OnKillRollUpTimer
- CMultiPaneFrameWnd [MFC], OnPaneRecalcLayout
- CMultiPaneFrameWnd [MFC], OnSetRollUpTimer
- CMultiPaneFrameWnd [MFC], OnShowPane
- CMultiPaneFrameWnd [MFC], PaneFromPoint
- CMultiPaneFrameWnd [MFC], RemoveNonValidPanes
- CMultiPaneFrameWnd [MFC], RemovePane
- CMultiPaneFrameWnd [MFC], ReplacePane
- CMultiPaneFrameWnd [MFC], SaveState
- CMultiPaneFrameWnd [MFC], Serialize
- CMultiPaneFrameWnd [MFC], SetDockState
- CMultiPaneFrameWnd [MFC], SetLastFocusedPane
- CMultiPaneFrameWnd [MFC], SetPreDockState
- CMultiPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CMultiPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
ms.assetid: 989a548e-0d70-46b7-a513-8cf740e1be3e
ms.openlocfilehash: 9c23d76e8f3ea54fe34e7956ad5b4e7dc9780def
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366837"
---
# <a name="cmultipaneframewnd-class"></a>CMultiPaneFrameWnd クラス

`CMultiPaneFrameWnd`クラスは拡張[CPaneFrameWnd クラス](../../mfc/reference/cpaneframewnd-class.md)します。 複数のペインをサポートします。 コントロール バーへの単一の埋め込みハンドルではなく`CMultiPaneFrameWnd`が含まれています、 [CPaneContainerManager クラス](../../mfc/reference/cpanecontainermanager-class.md)により、1 つをドッキングするのには、ユーザー オブジェクト`CMultiPaneFrameWnd`別に、動的に作成する複数のフローティング、タブ付きwindows とします。

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

## <a name="syntax"></a>構文

```
class CMultiPaneFrameWnd : public CPaneFrameWnd
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMultiPaneFrameWnd::AddPane](#addpane)|ペインを追加します。 (上書き[CPaneFrameWnd::AddPane](../../mfc/reference/cpaneframewnd-class.md#addpane))。|
|[CMultiPaneFrameWnd::AddRecentPane](#addrecentpane)||
|[CMultiPaneFrameWnd::AdjustLayout](#adjustlayout)|ミニフレーム ウィンドウのレイアウトを調整します。 (上書き[CPaneFrameWnd::AdjustLayout](../../mfc/reference/cpaneframewnd-class.md#adjustlayout))。|
|[CMultiPaneFrameWnd::AdjustPaneFrames](#adjustpaneframes)|(上書き[CPaneFrameWnd::AdjustPaneFrames](../../mfc/reference/cpaneframewnd-class.md#adjustpaneframes))。|
|[CMultiPaneFrameWnd::CalcExpectedDockedRect](#calcexpecteddockedrect)|ドッキング ウィンドウの予想される四角形を計算します。 (上書き[CPaneFrameWnd::CalcExpectedDockedRect](../../mfc/reference/cpaneframewnd-class.md#calcexpecteddockedrect))。|
|[CMultiPaneFrameWnd::CanBeAttached](#canbeattached)|現在のウィンドウを別のウィンドウまたはフレーム ウィンドウにドッキングできるかどうかを判断します。 (上書き[CPaneFrameWnd::CanBeAttached](../../mfc/reference/cpaneframewnd-class.md#canbeattached))。|
|[CMultiPaneFrameWnd::CanBeDockedToPane](#canbedockedtopane)|ミニフレーム ウィンドウをペインにドッキングできるかどうかを判断します。 (上書き[CPaneFrameWnd::CanBeDockedToPane](../../mfc/reference/cpaneframewnd-class.md#canbedockedtopane))。|
|[CMultiPaneFrameWnd::CheckGripperVisibility](#checkgrippervisibility)|(上書き[CPaneFrameWnd::CheckGripperVisibility](../../mfc/reference/cpaneframewnd-class.md#checkgrippervisibility))。|
|[CMultiPaneFrameWnd::CloseMiniFrame](#closeminiframe)|( `CPaneFrameWnd::CloseMiniFrame`をオーバーライドします)。|
|[CMultiPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|ペインをタブ付きドキュメントに変換します。 (上書き[CPaneFrameWnd::ConvertToTabbedDocument](../../mfc/reference/cpaneframewnd-class.md#converttotabbeddocument))。|
|[CMultiPaneFrameWnd::DockFrame](#dockframe)||
|[CMultiPaneFrameWnd::DockPane](#dockpane)|ペインをドッキングします。 (上書き[CPaneFrameWnd::DockPane](../../mfc/reference/cpaneframewnd-class.md#dockpane))。|
|[CMultiPaneFrameWnd::DockRecentPaneToMainFrame](#dockrecentpanetomainframe)||
|[CMultiPaneFrameWnd::GetCaptionText](#getcaptiontext)|キャプション テキストを返します。 (上書き[CPaneFrameWnd::GetCaptionText](../../mfc/reference/cpaneframewnd-class.md#getcaptiontext))。|
|[CMultiPaneFrameWnd::GetPaneContainerManager](#getpanecontainermanager)|内部コンテナー マネージャー オブジェクトへの参照を返します。|
|[CMultiPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|ミニフレーム ウィンドウに含まれる最初の可視ペインを返します。 (上書き[CPaneFrameWnd::GetFirstVisiblePane](../../mfc/reference/cpaneframewnd-class.md#getfirstvisiblepane))。|
|[CMultiPaneFrameWnd::GetPane](#getpane)|ミニフレーム ウィンドウに含まれるペインを返します。 (上書き[CPaneFrameWnd::GetPane](../../mfc/reference/cpaneframewnd-class.md#getpane))。|
|[CMultiPaneFrameWnd::GetPaneCount](#getpanecount)|ミニフレーム ウィンドウに含まれるペインの数を返します。 (上書き[CPaneFrameWnd::GetPaneCount](../../mfc/reference/cpaneframewnd-class.md#getpanecount))。|
|[CMultiPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|ミニフレーム ウィンドウに含まれる可視ペインの数を返します。 (上書き[CPaneFrameWnd::GetVisiblePaneCount](../../mfc/reference/cpaneframewnd-class.md#getvisiblepanecount))。|
|[CMultiPaneFrameWnd::InsertPane](#insertpane)||
|[CMultiPaneFrameWnd::LoadState](#loadstate)|レジストリからペインの状態を読み込みます。 (上書き[CPaneFrameWnd::LoadState](../../mfc/reference/cpaneframewnd-class.md#loadstate))。|
|[CMultiPaneFrameWnd::OnDockToRecentPos](#ondocktorecentpos)|ミニフレーム ウィンドウを直前の位置にドッキングします。 (上書き[CPaneFrameWnd::OnDockToRecentPos](../../mfc/reference/cpaneframewnd-class.md#ondocktorecentpos))。|
|[CMultiPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|ロールアップ タイマーを停止します。 (上書き[CPaneFrameWnd::OnKillRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onkillrolluptimer))。|
|[CMultiPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|ミニフレーム ウィンドウ内のペインのレイアウトを調整します。 (上書き[CPaneFrameWnd::OnPaneRecalcLayout](../../mfc/reference/cpaneframewnd-class.md#onpanerecalclayout))。|
|[CMultiPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|ロールアップ タイマーを設定します。 (上書き[CPaneFrameWnd::OnSetRollUpTimer](../../mfc/reference/cpaneframewnd-class.md#onsetrolluptimer))。|
|[CMultiPaneFrameWnd::OnShowPane](#onshowpane)|ミニフレーム ウィンドウ内のペインが非表示になるとき、または表示されるときに、フレームワークによって呼び出されます。 (上書き[CPaneFrameWnd::OnShowPane](../../mfc/reference/cpaneframewnd-class.md#onshowpane))。|
|[CMultiPaneFrameWnd::PaneFromPoint](#panefrompoint)|ユーザーが指定した位置がミニフレーム ウィンドウ内のペインに含まれている場合、そのペインを返します。 (上書き[CPaneFrameWnd::PaneFromPoint](../../mfc/reference/cpaneframewnd-class.md#panefrompoint))。|
|[CMultiPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|有効でないウィンドウを削除するために、フレームワークによって呼び出されます。 (上書き[CPaneFrameWnd::RemoveNonValidPanes](../../mfc/reference/cpaneframewnd-class.md#removenonvalidpanes))。|
|[CMultiPaneFrameWnd::RemovePane](#removepane)|ミニフレーム ウィンドウから、ペインを削除します。 (上書き[CPaneFrameWnd::RemovePane](../../mfc/reference/cpaneframewnd-class.md#removepane))。|
|[CMultiPaneFrameWnd::ReplacePane](#replacepane)|ペインを別のペインに置き換えます。 (上書き[CPaneFrameWnd::ReplacePane](../../mfc/reference/cpaneframewnd-class.md#replacepane))。|
|[CMultiPaneFrameWnd::SaveState](#savestate)|レジストリにペインの状態を保存します。 (上書き[CPaneFrameWnd::SaveState](../../mfc/reference/cpaneframewnd-class.md#savestate))。|
|[CMultiPaneFrameWnd::Serialize](#serialize)|( `CPaneFrameWnd::Serialize`をオーバーライドします)。|
|[CMultiPaneFrameWnd::SetDockState](#setdockstate)|ドッキング状態を設定します。 (上書き[CPaneFrameWnd::SetDockState](../../mfc/reference/cpaneframewnd-class.md#setdockstate))。|
|[CMultiPaneFrameWnd::SetLastFocusedPane](#setlastfocusedpane)||
|[CMultiPaneFrameWnd::SetPreDockState](#setpredockstate)|ドッキング前の状態を設定します。 (上書き[CPaneFrameWnd::SetPreDockState](../../mfc/reference/cpaneframewnd-class.md#setpredockstate))。|
|[CMultiPaneFrameWnd::StoreRecentDockSiteInfo](#storerecentdocksiteinfo)|(上書き[CPaneFrameWnd::StoreRecentDockSiteInfo](../../mfc/reference/cpaneframewnd-class.md#storerecentdocksiteinfo))。|
|[CMultiPaneFrameWnd::StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)|(上書き[CPaneFrameWnd::StoreRecentTabRelatedInfo](../../mfc/reference/cpaneframewnd-class.md#storerecenttabrelatedinfo))。|

## <a name="remarks"></a>Remarks

このクラスのメソッドのほとんどのメソッドをオーバーライドする、 [CPaneFrameWnd クラス](../../mfc/reference/cpaneframewnd-class.md)クラス。

ペインが AFX_CBRS_AUTO_ROLLUP スタイルを使用し、ユーザーがマルチ ウィンドウ フレーム ウィンドウにそのウィンドウをドッキングする場合、ユーザーは、他のドッキング ペインのスタイル設定に関係なく、ウィンドウをロールアップできます。

フレームワークが自動的に作成、`CMultiPaneFrameWnd`ユーザー CBRS_FLOAT_MULTI スタイルを使用するウィンドウをフローティングするときにオブジェクト。

クラスを派生させる方法について、`CPaneFrameWnd`クラスし、動的に作成を参照してください[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)します。

## <a name="example"></a>例

次の例へのポインターを取得する方法を示します、`CMultiPaneFrameWnd`オブジェクト。 このコード スニペットの一部、[ウィンドウのサイズを設定サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_SetPaneSize#4](../../mfc/reference/codesnippet/cpp/cmultipaneframewnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)

[CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxMultiPaneFrameWnd.h

##  <a name="addpane"></a>  CMultiPaneFrameWnd::AddPane

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>パラメーター

[in]*我が物*<br/>

### <a name="remarks"></a>Remarks

##  <a name="addrecentpane"></a>  CMultiPaneFrameWnd::AddRecentPane

```
virtual BOOL AddRecentPane(CDockablePane* pBar);
```

### <a name="parameters"></a>パラメーター

[in]*pBar*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="adjustlayout"></a>  CMultiPaneFrameWnd::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Remarks

##  <a name="adjustpaneframes"></a>  CMultiPaneFrameWnd::AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Remarks

##  <a name="calcexpecteddockedrect"></a>  CMultiPaneFrameWnd::CalcExpectedDockedRect

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>パラメーター

[in]*pWndToDock*<br/>
[in]*ptMouse*<br/>
[in]*rectResult*<br/>
[in] *bDrawTab*<br/>
[in]*ppTargetBar*<br/>

### <a name="remarks"></a>Remarks

##  <a name="canbeattached"></a>  CMultiPaneFrameWnd::CanBeAttached

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="canbedockedtopane"></a>  CMultiPaneFrameWnd::CanBeDockedToPane

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>パラメーター

[in]*pDockingBar*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="checkgrippervisibility"></a>  CMultiPaneFrameWnd::CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>Remarks

##  <a name="closeminiframe"></a>  CMultiPaneFrameWnd::CloseMiniFrame

```
virtual void CloseMiniFrame();
```

### <a name="remarks"></a>Remarks

##  <a name="converttotabbeddocument"></a>  CMultiPaneFrameWnd::ConvertToTabbedDocument

```
virtual void ConvertToTabbedDocument();
```

### <a name="remarks"></a>Remarks

##  <a name="dockframe"></a>  CMultiPaneFrameWnd::DockFrame

```
virtual BOOL DockFrame(
    CPaneFrameWnd* pDockedFrame,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>パラメーター

[in]*pDockedFrame*<br/>
[in]*dockMethod*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="dockpane"></a>  CMultiPaneFrameWnd::DockPane

```
virtual BOOL DockPane(CDockablePane* pDockedBar);
```

### <a name="parameters"></a>パラメーター

[in] *pDockedBar*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="dockrecentpanetomainframe"></a>  CMultiPaneFrameWnd::DockRecentPaneToMainFrame

```
virtual void DockRecentPaneToMainFrame(CDockablePane* pBar);
```

### <a name="parameters"></a>パラメーター

[in]*pBar*<br/>

### <a name="remarks"></a>Remarks

##  <a name="getcaptiontext"></a>  CMultiPaneFrameWnd::GetCaptionText

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getfirstvisiblepane"></a>  CMultiPaneFrameWnd::GetFirstVisiblePane

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getpane"></a>  CMultiPaneFrameWnd::GetPane

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getpanecontainermanager"></a>  CMultiPaneFrameWnd::GetPaneContainerManager

内部コンテナー マネージャー オブジェクトへの参照を返します。

```
CPaneContainerManager& GetPaneContainerManager();
```

### <a name="return-value"></a>戻り値

内部コンテナー マネージャー オブジェクトへの参照。

### <a name="remarks"></a>Remarks

このメソッドは、内部へのアクセスに使用できます[CPaneContainerManager クラス](../../mfc/reference/cpanecontainermanager-class.md)オブジェクト。

##  <a name="getpanecount"></a>  CMultiPaneFrameWnd::GetPaneCount

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getvisiblepanecount"></a>  CMultiPaneFrameWnd::GetVisiblePaneCount

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="insertpane"></a>  CMultiPaneFrameWnd::InsertPane

```
virtual BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter);
```

### <a name="parameters"></a>パラメーター

[in]*pControlBar*<br/>
[in]*pTarget*<br/>
[in]*bAfter*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="loadstate"></a>  CMultiPaneFrameWnd::LoadState

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>パラメーター

[in] *lpszProfileName*<br/>
[in]*uiID*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="ondocktorecentpos"></a>  CMultiPaneFrameWnd::OnDockToRecentPos

```
virtual void OnDockToRecentPos();
```

### <a name="remarks"></a>Remarks

##  <a name="onkillrolluptimer"></a>  CMultiPaneFrameWnd::OnKillRollUpTimer

```
virtual void OnKillRollUpTimer();
```

### <a name="remarks"></a>Remarks

##  <a name="onpanerecalclayout"></a>  CMultiPaneFrameWnd::OnPaneRecalcLayout

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>Remarks

##  <a name="onsetrolluptimer"></a>  CMultiPaneFrameWnd::OnSetRollUpTimer

```
virtual void OnSetRollUpTimer();
```

### <a name="remarks"></a>Remarks

##  <a name="onshowpane"></a>  CMultiPaneFrameWnd::OnShowPane

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>パラメーター

[in]*pBar*<br/>
[in]*bShow*<br/>

### <a name="remarks"></a>Remarks

##  <a name="panefrompoint"></a>  CMultiPaneFrameWnd::PaneFromPoint

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>パラメーター

[in]*ポイント*<br/>
[in]*nSensitivity*<br/>
[in]*bCheckVisibility*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="removenonvalidpanes"></a>  CMultiPaneFrameWnd::RemoveNonValidPanes

```
virtual void RemoveNonValidPanes();
```

### <a name="remarks"></a>Remarks

##  <a name="removepane"></a>  CMultiPaneFrameWnd::RemovePane

```
virtual void RemovePane(
    CBasePane* pBar,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = TRUE);
```

### <a name="parameters"></a>パラメーター

[in]*pBar*<br/>
[in]*bDestroy*<br/>
[in]*bNoDelayedDestroy*<br/>

### <a name="remarks"></a>Remarks

##  <a name="replacepane"></a>  CMultiPaneFrameWnd::ReplacePane

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>パラメーター

[in] *pBarOrg*<br/>
[in]*pBarReplaceWith*<br/>

### <a name="remarks"></a>Remarks

##  <a name="savestate"></a>  CMultiPaneFrameWnd::SaveState

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>パラメーター

[in] *lpszProfileName*<br/>
[in]*uiID*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="serialize"></a>  CMultiPaneFrameWnd::Serialize

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>パラメーター

[in]*ar*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setdockstate"></a>  CMultiPaneFrameWnd::SetDockState

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>パラメーター

[in]*pDockManager*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setlastfocusedpane"></a>  CMultiPaneFrameWnd::SetLastFocusedPane

```
void SetLastFocusedPane(HWND hwnd);
```

### <a name="parameters"></a>パラメーター

[in]*hwnd*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setpredockstate"></a>  CMultiPaneFrameWnd::SetPreDockState

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>パラメーター

[in]*preDockState*<br/>
[in]*pBarToDock*<br/>
[in]*dockMethod*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="storerecentdocksiteinfo"></a>  CMultiPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>パラメーター

[in]*pBar*<br/>

### <a name="remarks"></a>Remarks

##  <a name="storerecenttabrelatedinfo"></a>  CMultiPaneFrameWnd::StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>パラメーター

[in]*pDockingBar*<br/>
[in] *pTabbedBar*<br/>

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd クラス](../../mfc/reference/cpaneframewnd-class.md)
