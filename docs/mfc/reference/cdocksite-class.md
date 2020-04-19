---
title: CDockSite Class
ms.date: 10/18/2018
f1_keywords:
- CDockSite
- AFXDOCKSITE/CDockSite
- AFXDOCKSITE/CDockSite::AddRow
- AFXDOCKSITE/CDockSite::AdjustDockingLayout
- AFXDOCKSITE/CDockSite::AdjustLayout
- AFXDOCKSITE/CDockSite::AlignDockSite
- AFXDOCKSITE/CDockSite::CalcFixedLayout
- AFXDOCKSITE/CDockSite::CanAcceptPane
- AFXDOCKSITE/CDockSite::CreateEx
- AFXDOCKSITE/CDockSite::CreateRow
- AFXDOCKSITE/CDockSite::DockPane
- AFXDOCKSITE/CDockSite::DoesAllowDynInsertBefore
- AFXDOCKSITE/CDockSite::FindRowIndex
- AFXDOCKSITE/CDockSite::FixupVirtualRects
- AFXDOCKSITE/CDockSite::GetDockSiteID
- AFXDOCKSITE/CDockSite::GetDockSiteRowsList
- AFXDOCKSITE/CDockSite::IsAccessibilityCompatible
- AFXDOCKSITE/CDockSite::IsDragMode
- AFXDOCKSITE/CDockSite::IsLastRow
- AFXDOCKSITE/CDockSite::IsRectWithinDockSite
- AFXDOCKSITE/CDockSite::IsResizable
- AFXDOCKSITE/CDockSite::MovePane
- AFXDOCKSITE/CDockSite::OnInsertRow
- AFXDOCKSITE/CDockSite::OnRemoveRow
- AFXDOCKSITE/CDockSite::OnResizeRow
- AFXDOCKSITE/CDockSite::OnSetWindowPos
- AFXDOCKSITE/CDockSite::OnShowRow
- AFXDOCKSITE/CDockSite::OnSizeParent
- AFXDOCKSITE/CDockSite::PaneFromPoint
- AFXDOCKSITE/CDockSite::DockPaneLeftOf
- AFXDOCKSITE/CDockSite::FindPaneByID
- AFXDOCKSITE/CDockSite::GetPaneList
- AFXDOCKSITE/CDockSite::RectSideFromPoint
- AFXDOCKSITE/CDockSite::RemovePane
- AFXDOCKSITE/CDockSite::RemoveRow
- AFXDOCKSITE/CDockSite::ReplacePane
- AFXDOCKSITE/CDockSite::RepositionPanes
- AFXDOCKSITE/CDockSite::ResizeDockSite
- AFXDOCKSITE/CDockSite::ResizeRow
- AFXDOCKSITE/CDockSite::ShowPane
- AFXDOCKSITE/CDockSite::ShowRow
- AFXDOCKSITE/CDockSite::SwapRows
helpviewer_keywords:
- CDockSite [MFC], AddRow
- CDockSite [MFC], AdjustDockingLayout
- CDockSite [MFC], AdjustLayout
- CDockSite [MFC], AlignDockSite
- CDockSite [MFC], CalcFixedLayout
- CDockSite [MFC], CanAcceptPane
- CDockSite [MFC], CreateEx
- CDockSite [MFC], CreateRow
- CDockSite [MFC], DockPane
- CDockSite [MFC], DoesAllowDynInsertBefore
- CDockSite [MFC], FindRowIndex
- CDockSite [MFC], FixupVirtualRects
- CDockSite [MFC], GetDockSiteID
- CDockSite [MFC], GetDockSiteRowsList
- CDockSite [MFC], IsAccessibilityCompatible
- CDockSite [MFC], IsDragMode
- CDockSite [MFC], IsLastRow
- CDockSite [MFC], IsRectWithinDockSite
- CDockSite [MFC], IsResizable
- CDockSite [MFC], MovePane
- CDockSite [MFC], OnInsertRow
- CDockSite [MFC], OnRemoveRow
- CDockSite [MFC], OnResizeRow
- CDockSite [MFC], OnSetWindowPos
- CDockSite [MFC], OnShowRow
- CDockSite [MFC], OnSizeParent
- CDockSite [MFC], PaneFromPoint
- CDockSite [MFC], DockPaneLeftOf
- CDockSite [MFC], FindPaneByID
- CDockSite [MFC], GetPaneList
- CDockSite [MFC], RectSideFromPoint
- CDockSite [MFC], RemovePane
- CDockSite [MFC], RemoveRow
- CDockSite [MFC], ReplacePane
- CDockSite [MFC], RepositionPanes
- CDockSite [MFC], ResizeDockSite
- CDockSite [MFC], ResizeRow
- CDockSite [MFC], ShowPane
- CDockSite [MFC], ShowRow
- CDockSite [MFC], SwapRows
ms.assetid: 0fcfff79-5f50-4281-b2de-a55653bbea40
ms.openlocfilehash: 9c154fe621fb88a6dc96a9835fae95c4b86763de
ms.sourcegitcommit: bd7ddc044f9083246614b602ef6a758775313214
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68866191"
---
# <a name="cdocksite-class"></a>CDockSite Class

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

[CPane Class](../../mfc/reference/cpane-class.md) から派生したペインを一連の行に配置する機能を提供します。

## <a name="syntax"></a>構文

```
class CDockSite: public CBasePane
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDockSite::AddRow](#addrow)||
|[CDockSite:: AdjustDockingLayout](#adjustdockinglayout)|( [Cbasepane:: AdjustDockingLayout](../../mfc/reference/cbasepane-class.md#adjustdockinglayout)をオーバーライドします)。|
|[CDockSite:: AdjustLayout](#adjustlayout)|( [Cbasepane:: AdjustLayout](../../mfc/reference/cbasepane-class.md#adjustlayout)をオーバーライドします)。|
|[CDockSite:: AlignDockSite](#aligndocksite)||
|[CDockSite:: CalcFixedLayout](#calcfixedlayout)|( [Cbasepane:: CalcFixedLayout](../../mfc/reference/cbasepane-class.md#calcfixedlayout)をオーバーライドします)。|
|[CDockSite:: CanAcceptPane](#canacceptpane)|( [Cbasepane:: CanAcceptPane](../../mfc/reference/cbasepane-class.md#canacceptpane)をオーバーライドします)。|
|[CDockSite:: CreateEx](#createex)|( [Cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)をオーバーライドします)。|
|[CDockSite:: CreateRow](#createrow)||
|[CDockSite::D ockPane](#dockpane)|( [Cbasepane::D ockPane](../../mfc/reference/cbasepane-class.md#dockpane)をオーバーライドします)。|
|[CDockSite::D oesAllowDynInsertBefore](#doesallowdyninsertbefore)|( [Cbasepane::D oesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)をオーバーライドします)。|
|[CDockSite::FindRowIndex](#findrowindex)||
|[CDockSite:: FixupVirtualRects](#fixupvirtualrects)||
|[CDockSite:: GetDockSiteID](#getdocksiteid)||
|[CDockSite:: GetDockSiteRowsList](#getdocksiterowslist)||
|[CDockSite:: IsAccessibilityCompatible](#isaccessibilitycompatible)|( `CBasePane::IsAccessibilityCompatible`をオーバーライドします)。|
|[CDockSite:: IsDragMode](#isdragmode)||
|[CDockSite:: IsLastRow](#islastrow)||
|[CDockSite:: IsRectWithinDockSite](#isrectwithindocksite)||
|[CDockSite:: IsResizable 変更可能](#isresizable)|( [Cbasepane:: isresizable サイズを変更](../../mfc/reference/cbasepane-class.md#isresizable)できます)。|
|[CDockSite:: MovePane](#movepane)||
|[CDockSite:: OnInsertRow](#oninsertrow)||
|[CDockSite:: OnRemoveRow](#onremoverow)||
|[CDockSite:: OnResizeRow](#onresizerow)||
|[CDockSite:: OnSetWindowPos](#onsetwindowpos)||
|[CDockSite:: OnShowRow](#onshowrow)||
|[CDockSite:: OnSizeParent](#onsizeparent)||
|[CDockSite::P aneFromPoint](#panefrompoint)|パラメーターによって指定された点にあるドッキング サイトにドッキングされているペインを返します。|
|[CDockSite::D ockPaneLeftOf](#dockpaneleftof)|ペインを別のペインの左側にドッキングします。|
|[CDockSite:: FindPaneByID](#findpanebyid)|指定された ID によって識別されるペインを返します。|
|[CDockSite:: Get List](#getpanelist)|ドッキング サイトにドッキングされているペインの一覧を返します。|
|[CDockSite:: RectSideFromPoint](#rectsidefrompoint)||
|[CDockSite:: RemovePane](#removepane)||
|[CDockSite::RemoveRow](#removerow)||
|[CDockSite:: ReplacePane](#replacepane)||
|[CDockSite:: RepositionPanes](#repositionpanes)||
|[CDockSite:: ResizeDockSite](#resizedocksite)||
|[CDockSite:: ResizeRow](#resizerow)||
|[CDockSite:: ShowPane](#showpane)|ペインを表示します。|
|[CDockSite:: ShowRow](#showrow)||
|[CDockSite:: SwapRows](#swaprows)||

## <a name="remarks"></a>Remarks

`CDockSite` [CFrameWndEx:: EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking)を呼び出すと、フレームワークによってオブジェクトが自動的に作成されます。 ドッキング サイト ウィンドウは、メイン フレーム ウィンドウ上のクライアント領域の端に配置されます。

[CFrameWndEx クラス](../../mfc/reference/cframewndex-class.md)はこれらのサービスを処理するため、通常、dock サイトによって提供されるサービスを呼び出す必要はありません。

## <a name="example"></a>例

次の例では、`CDockSite` クラスのオブジェクトを作成する方法を示します。

[!code-cpp[NVC_MFC_RibbonApp#27](../../mfc/reference/codesnippet/cpp/cdocksite-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)\
└&nbsp;[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CWnd](../../mfc/reference/cwnd-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[Cbasepane](../../mfc/reference/cbasepane-class.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;└&nbsp;[CDockSite](../../mfc/reference/cdocksite-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxDockSite

##  <a name="addrow"></a>  CDockSite::AddRow

```
CDockingPanesRow* AddRow(
    POSITION pos,
    int nHeight);
```

### <a name="parameters"></a>パラメーター

から*pos*<br/>

から*nHeight*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="adjustdockinglayout"></a>  CDockSite::AdjustDockingLayout

```
virtual void AdjustDockingLayout();
```

### <a name="remarks"></a>Remarks

##  <a name="adjustlayout"></a>  CDockSite::AdjustLayout

```
virtual void AdjustLayout();
```

### <a name="remarks"></a>Remarks

##  <a name="aligndocksite"></a>  CDockSite::AlignDockSite

```
void AlignDockSite(
    const CRect& rectToAlignBy,
    CRect& rectResult,
    BOOL bMoveImmediately);
```

### <a name="parameters"></a>パラメーター

から*rectToAlignBy*<br/>

から*rectResult*<br/>

から*Bmoveimmediately ちに*<br/>

### <a name="remarks"></a>Remarks

##  <a name="calcfixedlayout"></a>  CDockSite::CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>パラメーター

から*Bstretch*<br/>

から*bHorz*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="canacceptpane"></a>CDockSite:: CanAcceptPane

```
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>パラメーター

から*Pbar*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="createex"></a>CDockSite:: CreateEx

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    DWORD dwControlBarStyle,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>パラメーター

から*Dwスタイル ex*<br/>

から*dwStyle*<br/>

から*rect*<br/>

から*pParentWnd*<br/>

から*Dwcontrolbarstyle*<br/>

から*pContext*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="createrow"></a>  CDockSite::CreateRow

```
virtual CDockingPanesRow* CreateRow(
    CDockSite* pParentDockBar,
    int nOffset,
    int nRowHeight);
```

### <a name="parameters"></a>パラメーター

から*pParentDockBar*<br/>

から*Noffset*<br/>

から*nRowHeight*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="dockpane"></a>CDockSite::D ockPane

```
virtual void DockPane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>パラメーター

から*pWnd*<br/>

から*dockMethod*<br/>

から*lpRect*<br/>

### <a name="remarks"></a>Remarks

##  <a name="dockpaneleftof"></a>CDockSite::D ockPaneLeftOf

ペインを別のペインの左側にドッキングします。

```
virtual BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>パラメーター

*pBarToDock*<br/>
[入力、出力]*Ptargetbar*の左側にドッキングするペインへのポインター。

*pTargetBar*<br/>
[入力、出力]ターゲットペインへのポインター。

### <a name="return-value"></a>戻り値

ペインが正常にドッキングされている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="doesallowdyninsertbefore"></a>  CDockSite::DoesAllowDynInsertBefore

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="findpanebyid"></a>CDockSite:: FindPaneByID

指定された ID を持つペインを返します。

```
CPane* FindPaneByID(UINT nID);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
から検索するペインのコマンド ID。

### <a name="return-value"></a>戻り値

指定したコマンド ID を持つペインへのポインター。ペインが見つからない場合は NULL。

### <a name="remarks"></a>Remarks

##  <a name="findrowindex"></a>  CDockSite::FindRowIndex

```
int FindRowIndex(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>パラメーター

から*Prow*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="fixupvirtualrects"></a>  CDockSite::FixupVirtualRects

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Remarks

##  <a name="getdocksiteid"></a>  CDockSite::GetDockSiteID

```
virtual UINT GetDockSiteID() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getdocksiterowslist"></a>  CDockSite::GetDockSiteRowsList

```
const CObList& GetDockSiteRowsList() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getpanelist"></a>  CDockSite::GetPaneList

ドッキングサイトにドッキングされているペインの一覧を返します。

```
const CObList& GetPaneList() const;
```

### <a name="return-value"></a>戻り値

ドッキングバーに現在ドッキングされているペインのリストへの読み取り専用の参照。

##  <a name="isaccessibilitycompatible"></a>  CDockSite::IsAccessibilityCompatible

```
virtual BOOL IsAccessibilityCompatible();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isdragmode"></a>CDockSite:: IsDragMode

```
virtual BOOL IsDragMode() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="islastrow"></a>  CDockSite::IsLastRow

```
bool IsLastRow(CDockingPanesRow* pRow) const;
```

### <a name="parameters"></a>パラメーター

から*Prow*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isrectwithindocksite"></a>  CDockSite::IsRectWithinDockSite

```
BOOL IsRectWithinDockSite(
    CRect rect,
    CPoint& ptDelta);
```

### <a name="parameters"></a>パラメーター

から*rect*<br/>

から*Ptdelta*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isresizable"></a>CDockSite:: IsResizable 変更可能

```
virtual BOOL IsResizable() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="movepane"></a>CDockSite:: MovePane

```
virtual BOOL MovePane(
    CPane* pWnd,
    UINT nFlags,
    CPoint ptOffset);
```

### <a name="parameters"></a>パラメーター

から*pWnd*<br/>

から*nFlags*<br/>

から*ptOffset*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="oninsertrow"></a>  CDockSite::OnInsertRow

```
virtual void OnInsertRow(POSITION pos);
```

### <a name="parameters"></a>パラメーター

から*pos*<br/>

### <a name="remarks"></a>Remarks

##  <a name="onremoverow"></a>  CDockSite::OnRemoveRow

```
virtual void OnRemoveRow(
    POSITION pos,
    BOOL bByShow = FALSE);
```

### <a name="parameters"></a>パラメーター

から*pos*<br/>

から*Bbyshow*<br/>

### <a name="remarks"></a>Remarks

##  <a name="onresizerow"></a>CDockSite:: OnResizeRow

```
virtual int OnResizeRow(
    CDockingPanesRow* pRowToResize,
    int nOffset);
```

### <a name="parameters"></a>パラメーター

から*pRowToResize*<br/>

から*Noffset*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="onsizeparent"></a>CDockSite:: OnSizeParent

```
virtual void OnSizeParent(
    CRect& rectAvailable,
    UINT nSide,
    BOOL bExpand,
    int nOffset);
```

### <a name="parameters"></a>パラメーター

から*rectAvailable*<br/>

から*Nside*<br/>

から*Bexpand*<br/>

から*Noffset*<br/>

### <a name="remarks"></a>Remarks

##  <a name="onsetwindowpos"></a>CDockSite:: OnSetWindowPos

```
virtual BOOL OnSetWindowPos(
    const CWnd* pWndInsertAfter,
    const CRect& rectWnd,
    UINT nFlags);
```

### <a name="parameters"></a>パラメーター

から*pWndInsertAfter*<br/>

から*Rectwnd*<br/>

から*nFlags*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="onshowrow"></a>  CDockSite::OnShowRow

```
virtual void OnShowRow(
    POSITION pos,
    BOOL bShow);
```

### <a name="parameters"></a>パラメーター

から*pos*<br/>

から*bShow*<br/>

### <a name="remarks"></a>Remarks

##  <a name="panefrompoint"></a>CDockSite::P aneFromPoint

パラメーターによって指定された点にあるドッキング サイトにドッキングされているペインを返します。

```
virtual CPane* PaneFromPoint(CPoint pt);
```

### <a name="parameters"></a>パラメーター

*未満*<br/>
から取得するペインのポイント (画面座標)。

### <a name="return-value"></a>戻り値

指定したポイントにあるペインへのポインター。指定したポイントにペインが存在しない場合は NULL。

### <a name="remarks"></a>Remarks

##  <a name="rectsidefrompoint"></a>  CDockSite::RectSideFromPoint

```
static int __stdcall RectSideFromPoint(
    const CRect& rect,
    const CPoint& point);
```

### <a name="parameters"></a>パラメーター

から*rect*<br/>

から*ポイント*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="removepane"></a>  CDockSite::RemovePane

```
virtual void RemovePane(
    CPane* pWnd,
    AFX_DOCK_METHOD dockMethod);
```

### <a name="parameters"></a>パラメーター

から*pWnd*<br/>

から*dockMethod*<br/>

### <a name="remarks"></a>Remarks

##  <a name="removerow"></a>  CDockSite::RemoveRow

```
void RemoveRow(CDockingPanesRow* pRow);
```

### <a name="parameters"></a>パラメーター

から*Prow*<br/>

### <a name="remarks"></a>Remarks

##  <a name="replacepane"></a>  CDockSite::ReplacePane

```
BOOL ReplacePane(
    CPane* pOldBar,
    CPane* pNewBar);
```

### <a name="parameters"></a>パラメーター

[in] *pOldBar*<br/>

から*Pnewbar*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="repositionpanes"></a>CDockSite:: RepositionPanes

```
virtual void RepositionPanes(CRect& rectNewClientArea);
```

### <a name="parameters"></a>パラメーター

から*rectNewClientArea*<br/>

### <a name="remarks"></a>Remarks

##  <a name="resizedocksite"></a>  CDockSite::ResizeDockSite

```
void ResizeDockSite(
    int nNewWidth,
    int nNewHeight);
```

### <a name="parameters"></a>パラメーター

[in] *nNewWidth*<br/>

から*nNewHeight*<br/>

### <a name="remarks"></a>Remarks

##  <a name="resizerow"></a>  CDockSite::ResizeRow

```
int ResizeRow(
    CDockingPanesRow* pRow,
    int nNewSize,
    BOOL bAdjustLayout = TRUE);
```

### <a name="parameters"></a>パラメーター

から*Prow*<br/>

から*Nnewsize*<br/>

から*bAdjustLayout*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="showpane"></a>CDockSite:: ShowPane

ペインを表示します。

```
virtual BOOL ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
[入力、出力]表示または非表示にするペインへのポインター。

*bShow*<br/>
からペインを表示するように指定する場合は TRUE。ペインを非表示にすることを指定する場合は FALSE。

*bDelay*<br/>
からペインが表示されるまで、ペインのレイアウトを遅延させることを指定する場合は TRUE。それ以外の場合は FALSE。

*bActivate*<br/>
からこのパラメーターは使用されません。

### <a name="return-value"></a>戻り値

ペインが正常に表示または非表示にされた場合は TRUE。 指定したペインがこのドックサイトに属していない場合は FALSE。

### <a name="remarks"></a>Remarks

ドッキングされたペインの表示と非表示を切り替えるには、このメソッドを呼び出します。 通常、を直接呼び出す`CDockSite::ShowPane`必要はありません。これは、親フレームウィンドウまたは基本ペインによって呼び出されるためです。

##  <a name="showrow"></a>  CDockSite::ShowRow

```
void ShowRow(
    CDockingPanesRow* pRow,
    BOOL bShow,
    BOOL bAdjustLayout);
```

### <a name="parameters"></a>パラメーター

から*Prow*<br/>

から*bShow*<br/>

から*bAdjustLayout*<br/>

### <a name="remarks"></a>Remarks

##  <a name="swaprows"></a>  CDockSite::SwapRows

```
void SwapRows(
    CDockingPanesRow* pFirstRow,
    CDockingPanesRow* pSecondRow);
```

### <a name="parameters"></a>パラメーター

から*Pfirstrow*<br/>

[in] *pSecondRow*<br/>

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CBasePane クラス](../../mfc/reference/cbasepane-class.md)
