---
title: CPaneFrameWnd クラス
ms.date: 11/04/2016
f1_keywords:
- CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd
- AFXPANEFRAMEWND/CPaneFrameWnd::AddPane
- AFXPANEFRAMEWND/CPaneFrameWnd::AddRemovePaneFromGlobalList
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::AdjustPaneFrames
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcBorderSize
- AFXPANEFRAMEWND/CPaneFrameWnd::CalcExpectedDockedRect
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeAttached
- AFXPANEFRAMEWND/CPaneFrameWnd::CanBeDockedToPane
- AFXPANEFRAMEWND/CPaneFrameWnd::CheckGripperVisibility
- AFXPANEFRAMEWND/CPaneFrameWnd::ConvertToTabbedDocument
- AFXPANEFRAMEWND/CPaneFrameWnd::Create
- AFXPANEFRAMEWND/CPaneFrameWnd::CreateEx
- AFXPANEFRAMEWND/CPaneFrameWnd::DockPane
- AFXPANEFRAMEWND/CPaneFrameWnd::FindFloatingPaneByID
- AFXPANEFRAMEWND/CPaneFrameWnd::FrameFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionHeight
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetCaptionText
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::GetDockingMode
- AFXPANEFRAMEWND/CPaneFrameWnd::GetFirstVisiblePane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPane
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::GetParent
- AFXPANEFRAMEWND/CPaneFrameWnd::GetPinState
- AFXPANEFRAMEWND/CPaneFrameWnd::GetRecentFloatingRect
- AFXPANEFRAMEWND/CPaneFrameWnd::GetVisiblePaneCount
- AFXPANEFRAMEWND/CPaneFrameWnd::HitTest
- AFXPANEFRAMEWND/CPaneFrameWnd::IsCaptured
- AFXPANEFRAMEWND/CPaneFrameWnd::IsDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollDown
- AFXPANEFRAMEWND/CPaneFrameWnd::IsRollUp
- AFXPANEFRAMEWND/CPaneFrameWnd::KillDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::LoadState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnBeforeDock
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDockToRecentPos
- AFXPANEFRAMEWND/CPaneFrameWnd::OnKillRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnMovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::OnPaneRecalcLayout
- AFXPANEFRAMEWND/CPaneFrameWnd::OnSetRollUpTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::OnShowPane
- AFXPANEFRAMEWND/CPaneFrameWnd::PaneFromPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::Pin
- AFXPANEFRAMEWND/CPaneFrameWnd::RedrawAll
- AFXPANEFRAMEWND/CPaneFrameWnd::RemoveNonValidPanes
- AFXPANEFRAMEWND/CPaneFrameWnd::RemovePane
- AFXPANEFRAMEWND/CPaneFrameWnd::ReplacePane
- AFXPANEFRAMEWND/CPaneFrameWnd::SaveState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetCaptionButtons
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDelayShow
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingManager
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockingTimer
- AFXPANEFRAMEWND/CPaneFrameWnd::SetDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SetHotPoint
- AFXPANEFRAMEWND/CPaneFrameWnd::SetPreDockState
- AFXPANEFRAMEWND/CPaneFrameWnd::SizeToContent
- AFXPANEFRAMEWND/CPaneFrameWnd::StartTearOff
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentDockSiteInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::StoreRecentTabRelatedInfo
- AFXPANEFRAMEWND/CPaneFrameWnd::OnCheckRollState
- AFXPANEFRAMEWND/CPaneFrameWnd::OnDrawBorder
- AFXPANEFRAMEWND/CPaneFrameWnd::m_bUseSaveBits
helpviewer_keywords:
- CPaneFrameWnd [MFC], AddPane
- CPaneFrameWnd [MFC], AddRemovePaneFromGlobalList
- CPaneFrameWnd [MFC], AdjustLayout
- CPaneFrameWnd [MFC], AdjustPaneFrames
- CPaneFrameWnd [MFC], CalcBorderSize
- CPaneFrameWnd [MFC], CalcExpectedDockedRect
- CPaneFrameWnd [MFC], CanBeAttached
- CPaneFrameWnd [MFC], CanBeDockedToPane
- CPaneFrameWnd [MFC], CheckGripperVisibility
- CPaneFrameWnd [MFC], ConvertToTabbedDocument
- CPaneFrameWnd [MFC], Create
- CPaneFrameWnd [MFC], CreateEx
- CPaneFrameWnd [MFC], DockPane
- CPaneFrameWnd [MFC], FindFloatingPaneByID
- CPaneFrameWnd [MFC], FrameFromPoint
- CPaneFrameWnd [MFC], GetCaptionHeight
- CPaneFrameWnd [MFC], GetCaptionRect
- CPaneFrameWnd [MFC], GetCaptionText
- CPaneFrameWnd [MFC], GetDockingManager
- CPaneFrameWnd [MFC], GetDockingMode
- CPaneFrameWnd [MFC], GetFirstVisiblePane
- CPaneFrameWnd [MFC], GetHotPoint
- CPaneFrameWnd [MFC], GetPane
- CPaneFrameWnd [MFC], GetPaneCount
- CPaneFrameWnd [MFC], GetParent
- CPaneFrameWnd [MFC], GetPinState
- CPaneFrameWnd [MFC], GetRecentFloatingRect
- CPaneFrameWnd [MFC], GetVisiblePaneCount
- CPaneFrameWnd [MFC], HitTest
- CPaneFrameWnd [MFC], IsCaptured
- CPaneFrameWnd [MFC], IsDelayShow
- CPaneFrameWnd [MFC], IsRollDown
- CPaneFrameWnd [MFC], IsRollUp
- CPaneFrameWnd [MFC], KillDockingTimer
- CPaneFrameWnd [MFC], LoadState
- CPaneFrameWnd [MFC], OnBeforeDock
- CPaneFrameWnd [MFC], OnDockToRecentPos
- CPaneFrameWnd [MFC], OnKillRollUpTimer
- CPaneFrameWnd [MFC], OnMovePane
- CPaneFrameWnd [MFC], OnPaneRecalcLayout
- CPaneFrameWnd [MFC], OnSetRollUpTimer
- CPaneFrameWnd [MFC], OnShowPane
- CPaneFrameWnd [MFC], PaneFromPoint
- CPaneFrameWnd [MFC], Pin
- CPaneFrameWnd [MFC], RedrawAll
- CPaneFrameWnd [MFC], RemoveNonValidPanes
- CPaneFrameWnd [MFC], RemovePane
- CPaneFrameWnd [MFC], ReplacePane
- CPaneFrameWnd [MFC], SaveState
- CPaneFrameWnd [MFC], SetCaptionButtons
- CPaneFrameWnd [MFC], SetDelayShow
- CPaneFrameWnd [MFC], SetDockingManager
- CPaneFrameWnd [MFC], SetDockingTimer
- CPaneFrameWnd [MFC], SetDockState
- CPaneFrameWnd [MFC], SetHotPoint
- CPaneFrameWnd [MFC], SetPreDockState
- CPaneFrameWnd [MFC], SizeToContent
- CPaneFrameWnd [MFC], StartTearOff
- CPaneFrameWnd [MFC], StoreRecentDockSiteInfo
- CPaneFrameWnd [MFC], StoreRecentTabRelatedInfo
- CPaneFrameWnd [MFC], OnCheckRollState
- CPaneFrameWnd [MFC], OnDrawBorder
- CPaneFrameWnd [MFC], m_bUseSaveBits
ms.assetid: ea3423a3-2763-482e-b763-817036ded10d
ms.openlocfilehash: 37ab241219f28336e73ea459a4e32ff413de8964
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502974"
---
# <a name="cpaneframewnd-class"></a>CPaneFrameWnd クラス

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

1 つのペインを含むミニフレーム ウィンドウを実装します。 そのペインは、ウィンドウのクライアント領域になります。

## <a name="syntax"></a>構文

```
class CPaneFrameWnd : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CPaneFrameWnd:: AddPane](#addpane)|ペインを追加します。|
|[CPaneFrameWnd:: AddRemovePaneFromGlobalList](#addremovepanefromgloballist)|グローバル リストに対してペインを追加または削除します。|
|[CPaneFrameWnd:: AdjustLayout](#adjustlayout)|ミニフレーム ウィンドウのレイアウトを調整します。|
|[CPaneFrameWnd:: AdjustPaneFrames](#adjustpaneframes)||
|[CPaneFrameWnd:: CalcBorderSize](#calcbordersize)|ミニフレーム ウィンドウの境界線のサイズを計算します。|
|[CPaneFrameWnd:: CalcExpectedDockedRect](#calcexpecteddockedrect)|ドッキング ウィンドウの予想される四角形を計算します。|
|[CPaneFrameWnd:: CanBeAttached](#canbeattached)|現在のペインを別のペインまたはフレーム ウィンドウにドッキングできるかどうかを判定します。|
|[CPaneFrameWnd:: Canbedoc/Pane](#canbedockedtopane)|ミニフレーム ウィンドウをペインにドッキングできるかどうかを判定します。|
|[CPaneFrameWnd:: CheckGripperVisibility](#checkgrippervisibility)||
|[CPaneFrameWnd::ConvertToTabbedDocument](#converttotabbeddocument)|ペインをタブ付きドキュメントに変換します。|
|[CPaneFrameWnd::Create](#create)|ミニフレーム ウィンドウを作成し、`CPaneFrameWnd` オブジェクトにアタッチします。|
|[CPaneFrameWnd:: CreateEx](#createex)|ミニフレーム ウィンドウを作成し、`CPaneFrameWnd` オブジェクトにアタッチします。|
|[CPaneFrameWnd::D ockPane](#dockpane)|ペインをドッキングします。|
|[CPaneFrameWnd:: FindFloatingPaneByID](#findfloatingpanebyid)|フローティング ペインのグローバル リストで、指定したコントロール ID のペインを検索します。|
|[CPaneFrameWnd:: FrameFromPoint](#framefrompoint)|ユーザーが指定したポイントを含むミニフレーム ウィンドウを検索します。|
|[CPaneFrameWnd:: GetCaptionHeight](#getcaptionheight)|ミニフレーム ウィンドウのキャプションの高さを返します。|
|[CPaneFrameWnd:: GetCaptionRect](#getcaptionrect)|ミニフレーム ウィンドウのキャプションに外接する四角形を計算します。|
|[CPaneFrameWnd::GetCaptionText](#getcaptiontext)|キャプション テキストを返します。|
|[CPaneFrameWnd:: Getdoc王国マネージャー](#getdockingmanager)||
|[CPaneFrameWnd:: Getdoc モード](#getdockingmode)|ドッキングのモードを返します。|
|[CPaneFrameWnd::GetFirstVisiblePane](#getfirstvisiblepane)|ミニフレーム ウィンドウに含まれる最初の可視ペインを返します。|
|[CPaneFrameWnd:: GetHotPoint](#gethotpoint)||
|[CPaneFrameWnd::GetPane](#getpane)|ミニフレーム ウィンドウに含まれるペインを返します。|
|[CPaneFrameWnd::GetPaneCount](#getpanecount)|ミニフレーム ウィンドウに含まれるペインの数を返します。|
|[CPaneFrameWnd::GetParent](#getparent)||
|[CPaneFrameWnd::GetPinState](#getpinstate)||
|[CPaneFrameWnd:: GetRecentFloatingRect](#getrecentfloatingrect)||
|[CPaneFrameWnd::GetVisiblePaneCount](#getvisiblepanecount)|ミニフレーム ウィンドウに含まれる可視ペインの数を返します。|
|[CPaneFrameWnd::HitTest](#hittest)|特定のポイントに、ミニフレーム ウィンドウのどの部分があるか判定します。|
|[CPaneFrameWnd:: IsCaptured](#iscaptured)||
|[CPaneFrameWnd::IsDelayShow](#isdelayshow)||
|[CPaneFrameWnd::IsRollDown](#isrolldown)|ミニフレーム ウィンドウをロール ダウンするかどうかを判断します。|
|[CPaneFrameWnd:: IsRollUp](#isrollup)|ミニフレーム ウィンドウをロール アップするかどうかを判断します。|
|[CPaneFrameWnd::KillDockingTimer](#killdockingtimer)|ドッキング タイマーを停止します。|
|[CPaneFrameWnd::LoadState](#loadstate)|レジストリからペインの状態を読み込みます。|
|[CPaneFrameWnd::OnBeforeDock](#onbeforedock)|ドッキングが可能かどうかを判定します。|
|[CPaneFrameWnd:: OnDockToRecentPos](#ondocktorecentpos)|ミニフレーム ウィンドウを直前の位置にドッキングします。|
|[CPaneFrameWnd::OnKillRollUpTimer](#onkillrolluptimer)|ロールアップ タイマーを停止します。|
|[CPaneFrameWnd::OnMovePane](#onmovepane)|ミニフレーム ウィンドウを指定したオフセットだけ移動します。|
|[CPaneFrameWnd::OnPaneRecalcLayout](#onpanerecalclayout)|含まれているペインのレイアウトを調整します。|
|[CPaneFrameWnd::OnSetRollUpTimer](#onsetrolluptimer)|ロールアップ タイマーを設定します。|
|[CPaneFrameWnd:: OnShowPane](#onshowpane)|ミニフレーム ウィンドウ内のペインが非表示になるとき、または表示されるときに、フレームワークによって呼び出されます。|
|[CPaneFrameWnd::P aneFromPoint](#panefrompoint)|ユーザーが指定した位置がミニフレーム ウィンドウ内のペインに含まれている場合、そのペインを返します。|
|[CPaneFrameWnd::Pin](#pin)||
|`CPaneFrameWnd::PreTranslateMessage`|[TranslateMessage](../../mfc/reference/cwinapp-class.md) および [DispatchMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) の各 Windows 関数にディスパッチされる前に、ウィンドウ メッセージを変換するためにクラス [CWinApp](/windows/win32/api/winuser/nf-winuser-dispatchmessage) で使用されます。|
|[CPaneFrameWnd::RedrawAll](#redrawall)|すべてのミニフレーム ウィンドウを再描画します。|
|[CPaneFrameWnd::RemoveNonValidPanes](#removenonvalidpanes)|有効でないウィンドウを削除するために、フレームワークによって呼び出されます。|
|[CPaneFrameWnd::RemovePane](#removepane)|ミニフレーム ウィンドウから、ペインを削除します。|
|[CPaneFrameWnd::ReplacePane](#replacepane)|ペインを別のペインに置き換えます。|
|[CPaneFrameWnd:: SaveState](#savestate)|レジストリにペインの状態を保存します。|
|`CPaneFrameWnd::Serialize`|アーカイブに対して、このオブジェクトの読み取りまたは書き込みを行います。|
|[CPaneFrameWnd::SetCaptionButtons](#setcaptionbuttons)|キャプションのボタンを設定します。|
|[CPaneFrameWnd:: SetDelayShow](#setdelayshow)||
|[CPaneFrameWnd:: Setdoc王国マネージャー](#setdockingmanager)||
|[CPaneFrameWnd:: Setdoc Timer](#setdockingtimer)|ドッキング タイマーを設定します。|
|[CPaneFrameWnd:: SetDockState](#setdockstate)|ドッキング状態を設定します。|
|[CPaneFrameWnd:: SetHotPoint](#sethotpoint)||
|[CPaneFrameWnd:: SetPreDockState](#setpredockstate)|ドッキング前の状態を設定するために、フレームワークによって呼び出されます。|
|[CPaneFrameWnd:: SizeToContent](#sizetocontent)|含まれているペインとサイズを同じにするために、ミニフレーム ウィンドウのサイズを調整します。|
|[CPaneFrameWnd:: StartTearOff](#starttearoff)|メニューをティアオフします。|
|[CPaneFrameWnd:: StoreRecentDockSiteInfo](#storerecentdocksiteinfo)||
|[CPaneFrameWnd:: StoreRecentTabRelatedInfo](#storerecenttabrelatedinfo)||

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CPaneFrameWnd:: OnCheckRollState](#oncheckrollstate)|ミニフレーム ウィンドウをロール アップまたはロール ダウンするかどうかを判断します。|
|[CPaneFrameWnd::OnDrawBorder](#ondrawborder)|ミニフレーム ウィンドウの境界線を描画します。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CPaneFrameWnd:: m_bUseSaveBits](#m_busesavebits)|ウィンドウクラスを CS_SAVEBITS クラススタイルで登録するかどうかを指定します。|

## <a name="remarks"></a>Remarks

ペインがドッキング状態からフローティング状態に切り替わるときに、フレームワークは自動的に `CPaneFrameWnd` オブジェクトを作成します。

ミニフレーム ウィンドウは内容を表示した状態でドラッグ (直接ドッキング) するか、ドラッグ四角形を使用してドラッグ (標準ドッキング) することができます。 ミニフレームのコンテナー ペインのドッキング モードにより、ミニフレームのドラッグ動作が決まります。 詳細については、「 [Cbasepane:: Getdocによるモード](../../mfc/reference/cbasepane-class.md#getdockingmode)」を参照してください。

ミニフレーム ウィンドウには、含まれているペインのスタイルに従って、キャプションのボタンが表示されます。 ウィンドウを閉じることができる場合は ( [Cbasepane:: can、Losed](../../mfc/reference/cbasepane-class.md#canbeclosed))、[閉じる] ボタンが表示されます。 ウィンドウに AFX_CBRS_AUTO_ROLLUP スタイルがある場合は、pin が表示されます。

`CPaneFrameWnd` からクラスを派生させる場合は、フレームワークで作成方法を定義する必要があります。 [CPane:: createdefaultminiframe フレーム](../../mfc/reference/cpane-class.md#createdefaultminiframe)をオーバーライドしてクラスを作成するか`CPane::m_pMiniFrameRTC` 、クラスのランタイムクラス情報を指すようにメンバーを設定します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CPaneFrameWnd`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxPaneFrameWnd

##  <a name="addpane"></a>  CPaneFrameWnd::AddPane

ペインを追加します。

```
virtual void AddPane(CBasePane* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
から追加するペイン。

##  <a name="addremovepanefromgloballist"></a>CPaneFrameWnd:: AddRemovePaneFromGlobalList

グローバル リストに対してペインを追加または削除します。

```
static BOOL __stdcall AddRemovePaneFromGlobalList(
    CBasePane* pWnd,
    BOOL bAdd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
から追加または削除するペイン。

*bAdd*<br/>
から0以外の場合は、ペインを追加します。 0の場合は、ペインを削除します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は0以外の。それ以外の場合は0です。

##  <a name="adjustlayout"></a>  CPaneFrameWnd::AdjustLayout

ミニフレーム ウィンドウのレイアウトを調整します。

```
virtual void AdjustLayout();
```

##  <a name="adjustpaneframes"></a>CPaneFrameWnd:: AdjustPaneFrames

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Remarks

##  <a name="calcbordersize"></a>CPaneFrameWnd:: CalcBorderSize

ミニフレームウィンドウの境界線のサイズを計算します。

```
virtual void CalcBorderSize(CRect& rectBorderSize) const;
```

### <a name="parameters"></a>パラメーター

*rectBorderSize*<br/>
入出力ミニフレームウィンドウの境界線のサイズをピクセル単位で格納します。

### <a name="remarks"></a>Remarks

このメソッドは、ミニフレームウィンドウの境界線のサイズを計算するためにフレームワークによって呼び出されます。 返されるサイズは、ミニフレームウィンドウにツールバーまたは[CDockablePane](../../mfc/reference/cdockablepane-class.md)が含まれているかどうかによって異なります。

##  <a name="calcexpecteddockedrect"></a>CPaneFrameWnd:: CalcExpectedDockedRect

ドッキング ウィンドウの予想される四角形を計算します。

```
virtual void CalcExpectedDockedRect(
    CWnd* pWndToDock,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>パラメーター

*pWndToDock*<br/>
からドッキングするウィンドウへのポインター。

*ptMouse*<br/>
からマウスの位置。

*rectResult*<br/>
入出力計算された四角形。

*bDrawTab タブ*<br/>
入出力TRUE の場合は、タブを描画します。FALSE の場合は、タブを描画しません。

*ppTargetBar*<br/>
入出力ターゲットペインへのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、ユーザーがウィンドウを*Ptmouse*によって指定されたポイントにドラッグし、そこにドッキングした場合に、ウィンドウが占める四角形を計算します。

##  <a name="canbeattached"></a>CPaneFrameWnd:: CanBeAttached

現在のペインを別のペインまたはフレーム ウィンドウにドッキングできるかどうかを判定します。

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>戻り値

ペインを別のペインまたはフレームウィンドウにドッキングできる場合は TRUE。それ以外の場合は FALSE。

##  <a name="canbedockedtopane"></a>CPaneFrameWnd:: Canbedoc/Pane

ミニフレーム ウィンドウをペインにドッキングできるかどうかを判定します。

```
virtual BOOL CanBeDockedToPane(const CDockablePane* pDockingBar) const;
```

### <a name="parameters"></a>パラメーター

*Pdocのボタン*<br/>
からペイン。

### <a name="return-value"></a>戻り値

ミニフレームを*Pdocの枠線*にドッキングできる場合は0以外の場合は。それ以外の場合は0です。

##  <a name="checkgrippervisibility"></a>CPaneFrameWnd:: CheckGripperVisibility

```
virtual void CheckGripperVisibility();
```

### <a name="remarks"></a>Remarks

##  <a name="converttotabbeddocument"></a>  CPaneFrameWnd::ConvertToTabbedDocument

ペインをタブ付きドキュメントに変換します。

```
virtual void ConvertToTabbedDocument();
```

##  <a name="create"></a>CPaneFrameWnd:: Create

ミニフレームウィンドウを作成し、 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)オブジェクトにアタッチします。

```
virtual BOOL Create(
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszWindowName*<br/>
からミニフレームウィンドウに表示するテキストを指定します。

*dwStyle*<br/>
からウィンドウスタイルを指定します。 詳細については、「[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)」を参照してください。

*rect*<br/>
からミニフレームウィンドウの初期サイズと位置を指定します。

*pParentWnd*<br/>
[入力、出力]ミニフレームウィンドウの親フレームを指定します。 この値を NULL にすることはできません。

*pContext*<br/>
[入力、出力]ユーザー定義のコンテキストを指定します。

### <a name="return-value"></a>戻り値

ウィンドウが正常に作成された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ミニフレームウィンドウは、2つの手順で作成されます。 最初に、フレームワークによっ`CPaneFrameWnd`てオブジェクトが作成されます。 次に、を`Create`呼び出して Windows ミニフレームウィンドウを作成し、それ`CPaneFrameWnd`をオブジェクトにアタッチします。

##  <a name="createex"></a>CPaneFrameWnd:: CreateEx

ミニフレームウィンドウを作成し、 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)オブジェクトにアタッチします。

```
virtual BOOL CreateEx(
    DWORD dwStyleEx,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>パラメーター

*Dwスタイル Ex*<br/>
から拡張ウィンドウスタイルを指定します。 詳細については、「[拡張ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)」を参照してください。

*lpszWindowName*<br/>
からミニフレームウィンドウに表示するテキストを指定します。

*dwStyle*<br/>
からウィンドウスタイルを指定します。 詳細については、「[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)」を参照してください。

*rect*<br/>
からミニフレームウィンドウの初期サイズと位置を指定します。

*pParentWnd*<br/>
[入力、出力]ミニフレームウィンドウの親フレームを指定します。 この値を NULL にすることはできません。

*pContext*<br/>
[入力、出力]ユーザー定義のコンテキストを指定します。

### <a name="return-value"></a>戻り値

ウィンドウが正常に作成された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ミニフレームウィンドウは、2つの手順で作成されます。 最初に、フレームワークによっ`CPaneFrameWnd`てオブジェクトが作成されます。 次に、を`Create`呼び出して Windows ミニフレームウィンドウを作成し、それ`CPaneFrameWnd`をオブジェクトにアタッチします。

##  <a name="dockpane"></a>CPaneFrameWnd::D ockPane

ペインをドッキングします。

```
virtual CDockablePane* DockPane(BOOL& bWasDocked);
```

### <a name="parameters"></a>パラメーター

*Bベアドッキング*<br/>
入出力ペインが既にドッキングされている場合は TRUE。それ以外の場合は FALSE。

### <a name="return-value"></a>戻り値

操作が成功した場合は`CDockablePane` 、ペインがドッキングされた。それ以外の場合は NULL。

##  <a name="findfloatingpanebyid"></a>CPaneFrameWnd:: FindFloatingPaneByID

フローティング ペインのグローバル リストで、指定したコントロール ID のペインを検索します。

```
static CBasePane* FindFloatingPaneByID(UINT nID);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
から検索するペインのコントロール ID を表します。

### <a name="return-value"></a>戻り値

指定されたコントロール ID を持つペイン。それ以外の場合は、指定されたコントロール ID を持つペインがない場合は NULL になります。

##  <a name="framefrompoint"></a>CPaneFrameWnd:: FrameFromPoint

指定したポイントを含むミニフレームウィンドウを検索します。

```
static CPaneFrameWnd* __stdcall FrameFromPoint(
    CPoint pt,
    int nSensitivity,
    CPaneFrameWnd* pFrameToExclude = NULL,
    BOOL bFloatMultiOnly = FALSE);
```

### <a name="parameters"></a>パラメーター

*未満*<br/>
から画面座標で表される点。

*nSensitivity*<br/>
からミニフレームウィンドウの検索領域をこのサイズで増やします。 指定されたポイントが増加した領域にある場合、ミニフレームウィンドウは検索条件を満たします。

*Pフレームの除外*<br/>
から検索から除外するミニフレームウィンドウを指定します。

*bFloatMultiOnly*<br/>
からTRUE の場合は、CBRS_FLOAT_MULTI スタイルを持つミニフレームウィンドウのみを検索します。 FALSE の場合は、すべてのミニフレームウィンドウを検索します。

### <a name="return-value"></a>戻り値

*Pt*を含むミニフレームウィンドウへのポインター。それ以外の場合は NULL。

##  <a name="getcaptionheight"></a>CPaneFrameWnd:: GetCaptionHeight

ミニフレーム ウィンドウのキャプションの高さを返します。

```
virtual int GetCaptionHeight() const;
```

### <a name="return-value"></a>戻り値

ミニフレームウィンドウの高さ (ピクセル単位)。

### <a name="remarks"></a>Remarks

ミニフレームウィンドウの高さを決定するには、このメソッドを呼び出します。 既定では、高さは SM_CYSMCAPTION に設定されています。 詳細については、「 [GetSystemMetrics 関数](/windows/win32/api/winuser/nf-winuser-getsystemmetrics)」を参照してください。

##  <a name="getcaptionrect"></a>CPaneFrameWnd:: GetCaptionRect

ミニフレーム ウィンドウのキャプションに外接する四角形を計算します。

```
virtual void GetCaptionRect(CRect& rectCaption) const;
```

### <a name="parameters"></a>パラメーター

*rectCaption*<br/>
入出力ミニフレームウィンドウキャプションのサイズと位置を画面座標で格納します。

### <a name="remarks"></a>Remarks

このメソッドは、ミニフレームウィンドウのキャプションの外接する四角形を計算するためにフレームワークによって呼び出されます。

##  <a name="getcaptiontext"></a>  CPaneFrameWnd::GetCaptionText

キャプション テキストを返します。

```
virtual CString GetCaptionText();
```

### <a name="return-value"></a>戻り値

ミニフレームウィンドウのキャプションテキスト。

### <a name="remarks"></a>Remarks

このメソッドは、キャプションテキストを表示するときにフレームワークによって呼び出されます。

##  <a name="getdockingmanager"></a>CPaneFrameWnd:: Getdoc王国マネージャー

```
CDockingManager* GetDockingManager() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getdockingmode"></a>  CPaneFrameWnd::GetDockingMode

ドッキングのモードを返します。

```
virtual AFX_DOCK_TYPE GetDockingMode() const;
```

### <a name="return-value"></a>戻り値

ドッキングモード。 次のいずれかの値です。

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

##  <a name="getfirstvisiblepane"></a>CPaneFrameWnd:: GetFirstVisiblePane

ミニフレーム ウィンドウに含まれる最初の可視ペインを返します。

```
virtual CWnd* GetFirstVisiblePane() const;
```

### <a name="return-value"></a>戻り値

ミニフレームウィンドウの最初のペイン。ミニフレームウィンドウにペインが含まれていない場合は NULL。

##  <a name="gethotpoint"></a>CPaneFrameWnd:: GetHotPoint

```
CPoint GetHotPoint() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getpane"></a>  CPaneFrameWnd::GetPane

ミニフレーム ウィンドウに含まれるペインを返します。

```
virtual CWnd* GetPane() const;
```

### <a name="return-value"></a>戻り値

ミニフレームに含まれるペイン。ミニフレームウィンドウにペインが含まれていない場合は NULL。

### <a name="remarks"></a>Remarks

##  <a name="getpanecount"></a>  CPaneFrameWnd::GetPaneCount

ミニフレーム ウィンドウに含まれるペインの数を返します。

```
virtual int GetPaneCount() const;
```

### <a name="return-value"></a>戻り値

ミニフレームウィンドウ内のペインの数。 この値は0にすることができます。

### <a name="remarks"></a>Remarks

##  <a name="getparent"></a>  CPaneFrameWnd::GetParent

```
CWnd* GetParent();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getpinstate"></a>  CPaneFrameWnd::GetPinState

```
BOOL GetPinState() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getrecentfloatingrect"></a>CPaneFrameWnd:: GetRecentFloatingRect

```
CRect GetRecentFloatingRect() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getvisiblepanecount"></a>  CPaneFrameWnd::GetVisiblePaneCount

ミニフレーム ウィンドウに含まれる可視ペインの数を返します。

```
virtual int GetVisiblePaneCount() const;
```

### <a name="return-value"></a>戻り値

表示されるペインの数。

### <a name="remarks"></a>Remarks

##  <a name="hittest"></a>  CPaneFrameWnd::HitTest

特定のポイントに、ミニフレーム ウィンドウのどの部分があるか判定します。

```
virtual LRESULT HitTest(
    CPoint point,
    BOOL bDetectCaption);
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
からテストするポイント。

*B検出キャプション*<br/>
からTRUE の場合は、キャプションに対するポイントを確認します。 FALSE の場合は、キャプションを無視します。

### <a name="return-value"></a>戻り値

次のいずれかの値です。

|[値]|説明|
|-----------|-------------|
|HTNOWHERE|ポイントがミニフレームウィンドウの外側にあります。|
|HTCLIENT|ポイントはクライアント領域にあります。|
|HTCAPTION|ポイントはキャプション上にあります。|
|HTTOP|ポイントが一番上にあります。|
|HTTOPLEFT|ポイントが左上にあります。|
|HTTOPRIGHT|ポイントは右上にあります。|
|HTLEFT|ポイントが左側にあります。|
|HTRIGHT|ポイントが右側にあります。|
|HTBOTTOM|点は下部にあります。|
|左から左|ポイントは左下にあります。|
|HTRIGHT|ポイントが右下にあります。|

##  <a name="iscaptured"></a>CPaneFrameWnd:: IsCaptured

```
BOOL IsCaptured() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isdelayshow"></a>  CPaneFrameWnd::IsDelayShow

```
BOOL IsDelayShow() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isrolldown"></a>  CPaneFrameWnd::IsRollDown

ミニフレーム ウィンドウをロール ダウンするかどうかを判断します。

```
virtual BOOL IsRollDown() const;
```

### <a name="return-value"></a>戻り値

ミニフレームウィンドウをロールダウンする必要がある場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ミニフレームウィンドウをロールダウンする必要があるかどうかを判断するために、フレームワークによって呼び出されます。 AFX_CBRS_AUTO_ROLLUP フラグを持つペインが少なくとも1つ含まれている場合は、ミニフレームウィンドウに対して rollup/rolldown 機能が有効になります。 このフラグは、ペインが作成されるときに設定されます。 詳細については、「 [Cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)」を参照してください。

既定では、フレームワークは、ウィンドウをロールダウンする必要があるかどうかを判断するために、マウスポインターがミニフレームウィンドウの外接する四角形の内側にあるかどうかを確認します。 派生クラスでは、この動作をオーバーライドできます。

##  <a name="isrollup"></a>CPaneFrameWnd:: IsRollUp

ミニフレーム ウィンドウをロール アップするかどうかを判断します。

```
virtual BOOL IsRollUp() const;
```

### <a name="return-value"></a>戻り値

ミニフレームウィンドウをロールアップする必要がある場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ミニフレームウィンドウをロールアップする必要があるかどうかを判断するために、フレームワークによって呼び出されます。 AFX_CBRS_AUTO_ROLLUP フラグを持つペインが少なくとも1つ含まれている場合は、ミニフレームウィンドウに対して rollup/rolldown 機能が有効になります。 このフラグは、ペインが作成されるときに設定されます。 詳細については、「 [Cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)」を参照してください。

既定では、フレームワークは、ウィンドウをロールアップする必要があるかどうかを判断するために、マウスポインターがミニフレームウィンドウの外接する四角形の内側にあるかどうかを確認します。 派生クラスでは、この動作をオーバーライドできます。

##  <a name="killdockingtimer"></a>  CPaneFrameWnd::KillDockingTimer

ドッキング タイマーを停止します。

```
void KillDockingTimer();
```

##  <a name="loadstate"></a>  CPaneFrameWnd::LoadState

レジストリからペインの状態を読み込みます。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
からプロファイル名。

*uiID*<br/>
からペイン ID。

### <a name="return-value"></a>戻り値

ペインの状態が正常に読み込まれた場合は TRUE。それ以外の場合は FALSE。

##  <a name="m_busesavebits"></a>CPaneFrameWnd:: m_bUseSaveBits

CS_SAVEBITS クラススタイルを持つウィンドウクラスを登録するかどうかを指定します。

```
AFX_IMPORT_DATA static BOOL m_bUseSaveBits;
```

### <a name="remarks"></a>Remarks

CS_SAVEBITS スタイルを持つミニフレームウィンドウクラスを登録するには、この静的メンバーを TRUE に設定します。 これは、ユーザーがミニフレームウィンドウをドラッグしたときのちらつきを軽減するのに役立ちます。

##  <a name="onbeforedock"></a>  CPaneFrameWnd::OnBeforeDock

ドッキングが可能かどうかを判定します。

```
virtual BOOL OnBeforeDock();
```

### <a name="return-value"></a>戻り値

ドッキングできる場合は TRUE。それ以外の場合は FALSE。

##  <a name="oncheckrollstate"></a>CPaneFrameWnd:: OnCheckRollState

ミニフレーム ウィンドウをロール アップまたはロール ダウンするかどうかを判断します。

```
virtual void OnCheckRollState();
```

### <a name="remarks"></a>Remarks

このメソッドは、ミニフレームウィンドウをロールアップまたはダウンする必要があるかどうかを判断するために、フレームワークによって呼び出されます。

既定では、フレームワークは[CPaneFrameWnd:: IsRollUp](#isrollup)と[CPaneFrameWnd:: IsRollDown](#isrolldown)を呼び出し、ミニフレームウィンドウを拡大または復元します。 派生クラスでこのメソッドをオーバーライドして、別の視覚効果を使用することができます。

##  <a name="ondocktorecentpos"></a>CPaneFrameWnd:: OnDockToRecentPos

ミニフレーム ウィンドウを直前の位置にドッキングします。

```
virtual void OnDockToRecentPos();
```

##  <a name="ondrawborder"></a>  CPaneFrameWnd::OnDrawBorder

ミニフレーム ウィンドウの境界線を描画します。

```
virtual void OnDrawBorder(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
から境界線の描画に使用するデバイスコンテキスト。

### <a name="remarks"></a>Remarks

このメソッドは、ミニフレームウィンドウの境界線を描画するためにフレームワークによって呼び出されます。

##  <a name="onkillrolluptimer"></a>CPaneFrameWnd:: OnKillRollUpTimer

ロールアップ タイマーを停止します。

```
virtual void OnKillRollUpTimer();
```

##  <a name="onmovepane"></a>  CPaneFrameWnd::OnMovePane

ミニフレーム ウィンドウを指定したオフセットだけ移動します。

```
virtual void OnMovePane(
    CPane* pBar,
    CPoint ptOffset);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
からペインへのポインター (無視)。

*ptOffset*<br/>
からペインの移動に使用するオフセット。

##  <a name="onpanerecalclayout"></a>  CPaneFrameWnd::OnPaneRecalcLayout

ミニフレームウィンドウ内のペインのレイアウトを調整します。

```
virtual void OnPaneRecalcLayout();
```

### <a name="remarks"></a>Remarks

フレームワークは、ミニフレームウィンドウ内のペインのレイアウトを調整する必要がある場合に、このメソッドを呼び出します。

既定では、ウィンドウはミニフレームウィンドウのクライアント領域全体をカバーするように配置されています。

##  <a name="onsetrolluptimer"></a>CPaneFrameWnd:: OnSetRollUpTimer

ロールアップ タイマーを設定します。

```
virtual void OnSetRollUpTimer();
```

##  <a name="onshowpane"></a>  CPaneFrameWnd::OnShowPane

ミニフレーム ウィンドウ内のペインが非表示になるとき、または表示されるときに、フレームワークによって呼び出されます。

```
virtual void OnShowPane(
    CDockablePane* pBar,
    BOOL bShow);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
から表示または非表示になっているペイン。

*bShow*<br/>
からペインが表示されている場合は TRUE。ペインが非表示になっている場合は FALSE。

### <a name="remarks"></a>Remarks

ミニフレームウィンドウのペインが表示または非表示にされたときに、フレームワークによって呼び出されます。 既定の実装では、何も行われません。

##  <a name="pin"></a>  CPaneFrameWnd::Pin

```
void Pin(BOOL bPin = TRUE);
```

### <a name="parameters"></a>パラメーター

から*Bpin*<br/>

### <a name="remarks"></a>Remarks

##  <a name="panefrompoint"></a>CPaneFrameWnd::P aneFromPoint

ユーザーが指定した位置がミニフレーム ウィンドウ内のペインに含まれている場合、そのペインを返します。

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    BOOL bCheckVisibility);
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
からユーザーがクリックしたポイント (画面座標)。

*nSensitivity*<br/>
からこのパラメーターは使用されません。

*bCheckVisibility*<br/>
から表示されるペインのみを返すように指定する場合は TRUE。それ以外の場合は FALSE。

### <a name="return-value"></a>戻り値

ユーザーがクリックしたペイン。その場所にペインが存在しない場合は NULL。

### <a name="remarks"></a>Remarks

指定されたポイントを含むペインを取得するには、このメソッドを呼び出します。

##  <a name="redrawall"></a>  CPaneFrameWnd::RedrawAll

すべてのミニフレーム ウィンドウを再描画します。

```
static void RedrawAll();
```

### <a name="remarks"></a>Remarks

このメソッドは、ウィンドウごとに[CWnd:: RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow)を呼び出すことによって、すべてのミニフレームウィンドウを更新します。

##  <a name="removenonvalidpanes"></a>  CPaneFrameWnd::RemoveNonValidPanes

有効でないウィンドウを削除するために、フレームワークによって呼び出されます。

```
virtual void RemoveNonValidPanes();
```

##  <a name="removepane"></a>  CPaneFrameWnd::RemovePane

ミニフレーム ウィンドウから、ペインを削除します。

```
virtual void RemovePane(
    CBasePane* pWnd,
    BOOL bDestroy = FALSE,
    BOOL bNoDelayedDestroy = FALSE);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
から削除するペインへのポインター。

*bDestroy*<br/>
からミニフレームウィンドウの動作を指定します。 *Bdestroy*が TRUE の場合、このメソッドはミニフレームウィンドウを直ちに破棄します。 FALSE の場合、このメソッドは、特定の遅延の後にミニフレームウィンドウを破棄します。

*bNoDelayedDestroy*<br/>
からTRUE の場合、遅延破棄は無効になります。 FALSE の場合、遅延破棄が有効になります。

### <a name="remarks"></a>Remarks

フレームワークは、ミニフレームウィンドウを直ちに、または特定の遅延の後に破棄できます。 ミニフレームウィンドウの破棄を遅延する場合は、 *Bnodelayeddestroy*パラメーターに FALSE を渡します。 遅延破棄は、フレームワークが AFX_WM_CHECKEMPTYMINIFRAME メッセージを処理するときに発生します。

##  <a name="replacepane"></a>  CPaneFrameWnd::ReplacePane

ペインを別のペインに置き換えます。

```
virtual void ReplacePane(
    CBasePane* pBarOrg,
    CBasePane* pBarReplaceWith);
```

### <a name="parameters"></a>パラメーター

*pBarOrg*<br/>
から元のペインへのポインター。

*pBarReplaceWith*<br/>
から元のペインを置き換えるペインへのポインター。

##  <a name="savestate"></a>CPaneFrameWnd:: SaveState

レジストリにペインの状態を保存します。

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
からプロファイル名。

*uiID*<br/>
からペイン ID。

### <a name="return-value"></a>戻り値

ペインの状態が正常に保存された場合は TRUE。それ以外の場合は FALSE。

##  <a name="setcaptionbuttons"></a>  CPaneFrameWnd::SetCaptionButtons

キャプションのボタンを設定します。

```
virtual void SetCaptionButtons(DWORD dwButtons);
```

### <a name="parameters"></a>パラメーター

*dwButtons*<br/>
から次の値のビットごとの or の組み合わせ。

- AFX_CAPTION_BTN_CLOSE

- AFX_CAPTION_BTN_PIN

- AFX_CAPTION_BTN_MENU

- AFX_CAPTION_BTN_CUSTOMIZE

##  <a name="setdelayshow"></a>  CPaneFrameWnd::SetDelayShow

```
void SetDelayShow(BOOL bDelayShow);
```

### <a name="parameters"></a>パラメーター

から*Bdelayshow*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setdockingmanager"></a>CPaneFrameWnd:: Setdoc王国マネージャー

```
void SetDockingManager(CDockingManager* pManager);
```

### <a name="parameters"></a>パラメーター

から*Pmanager*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setdockingtimer"></a>  CPaneFrameWnd::SetDockingTimer

ドッキング タイマーを設定します。

```
void SetDockingTimer(UINT nTimeOut);
```

### <a name="parameters"></a>パラメーター

*nTimeOut*<br/>
からタイムアウト値 (ミリ秒単位)。

##  <a name="setdockstate"></a>CPaneFrameWnd:: SetDockState

ドッキング状態を設定します。

```
virtual void SetDockState(CDockingManager* pDockManager);
```

### <a name="parameters"></a>パラメーター

*pDockManager*<br/>
からドッキングマネージャーへのポインター。

##  <a name="sethotpoint"></a>CPaneFrameWnd:: SetHotPoint

```
void SetHotPoint(CPoint& ptNew);
```

### <a name="parameters"></a>パラメーター

から*Ptnew*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setpredockstate"></a>CPaneFrameWnd:: SetPreDockState

ドッキング前の状態を設定するために、フレームワークによって呼び出されます。

```
virtual BOOL SetPreDockState(
    AFX_PREDOCK_STATE preDockState,
    CBasePane* pBarToDock = NULL,
    AFX_DOCK_METHOD dockMethod = DM_MOUSE);
```

### <a name="parameters"></a>パラメーター

*preDockState*<br/>
から使用可能な値:

- PDS_NOTHING,

- PDS_DOCK_REGULAR,

- PDS_DOCK_TO_TAB

*pBarToDock*<br/>
からドッキングするペインへのポインター。

*dockMethod*<br/>
からドッキングメソッド。 (このパラメーターは無視されます)。

### <a name="return-value"></a>戻り値

ミニフレームウィンドウがドッキング解除されている場合は TRUE。ドッキングされている場合は FALSE。

##  <a name="sizetocontent"></a>CPaneFrameWnd:: SizeToContent

格納されているペインと同じになるように、ミニフレームウィンドウのサイズを調整します。

```
virtual void SizeToContent();
```

### <a name="remarks"></a>Remarks

このメソッドを呼び出して、ミニフレームウィンドウのサイズを、含まれているペインのサイズに調整します。

##  <a name="starttearoff"></a>CPaneFrameWnd:: StartTearOff

メニューをティアオフします。

```
BOOL StartTearOff(CMFCPopu* pMenu);
```

### <a name="parameters"></a>パラメーター

*pMenu*<br/>
からメニューへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

##  <a name="storerecentdocksiteinfo"></a>  CPaneFrameWnd::StoreRecentDockSiteInfo

```
virtual void StoreRecentDockSiteInfo(CPane* pBar);
```

### <a name="parameters"></a>パラメーター

から*Pbar*<br/>

### <a name="remarks"></a>Remarks

##  <a name="storerecenttabrelatedinfo"></a>CPaneFrameWnd:: StoreRecentTabRelatedInfo

```
virtual void StoreRecentTabRelatedInfo(
    CDockablePane* pDockingBar,
    CDockablePane* pTabbedBar);
```

### <a name="parameters"></a>パラメーター

から*Pdocのボタン*<br/>
から*pTabbedBar*<br/>

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)
