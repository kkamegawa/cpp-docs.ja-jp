---
title: CMDIChildWndEx クラス
ms.date: 10/18/2018
f1_keywords:
- CMDIChildWndEx
- AFXMDICHILDWNDEX/CMDIChildWndEx
- AFXMDICHILDWNDEX/CMDIChildWndEx::ActivateTopLevelFrame
- AFXMDICHILDWNDEX/CMDIChildWndEx::AddPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::AddTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::AdjustDockingLayout
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnMDITabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnTaskBarTabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::CanShowOnWindowsList
- AFXMDICHILDWNDEX/CMDIChildWndEx::DockPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::DockPaneLeftOf
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableAutoHidePanes
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableDocking
- AFXMDICHILDWNDEX/CMDIChildWndEx::EnableTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetDockingManager
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetDocumentName
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetFrameIcon
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetFrameText
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetRelatedTabGroup
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTabProxyWnd
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTaskbarPreviewWnd
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::GetToolbarButtonToolTipText
- AFXMDICHILDWNDEX/CMDIChildWndEx::InsertPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::InvalidateIconicBitmaps
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsPointNearDockSite
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsReadOnly
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsRegisteredWithTaskbarTabs
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTabbedPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTaskbarTabsSupportEnabled
- AFXMDICHILDWNDEX/CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled
- AFXMDICHILDWNDEX/CMDIChildWndEx::m_dwDefaultTaskbarTabPropertyFlags
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnGetIconicLivePreviewBitmap
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnGetIconicThumbnail
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnMoveMiniFrame
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnSetPreviewMode
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailActivate
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailMouseActivate
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnTaskbarTabThumbnailStretch
- AFXMDICHILDWNDEX/CMDIChildWndEx::OnUpdateFrameTitle
- AFXMDICHILDWNDEX/CMDIChildWndEx::PaneFromPoint
- AFXMDICHILDWNDEX/CMDIChildWndEx::RecalcLayout
- AFXMDICHILDWNDEX/CMDIChildWndEx::RegisterTaskbarTab
- AFXMDICHILDWNDEX/CMDIChildWndEx::RemovePaneFromDockManager
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetRelatedTabGroup
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabActive
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabOrder
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarTabProperties
- AFXMDICHILDWNDEX/CMDIChildWndEx::SetTaskbarThumbnailClipRect
- AFXMDICHILDWNDEX/CMDIChildWndEx::ShowPane
- AFXMDICHILDWNDEX/CMDIChildWndEx::UnregisterTaskbarTab
- AFXMDICHILDWNDEX/CMDIChildWndEx::UpdateTaskbarTabIcon
helpviewer_keywords:
- CMDIChildWndEx [MFC], ActivateTopLevelFrame
- CMDIChildWndEx [MFC], AddPane
- CMDIChildWndEx [MFC], AddTabbedPane
- CMDIChildWndEx [MFC], AdjustDockingLayout
- CMDIChildWndEx [MFC], CanShowOnMDITabs
- CMDIChildWndEx [MFC], CanShowOnTaskBarTabs
- CMDIChildWndEx [MFC], CanShowOnWindowsList
- CMDIChildWndEx [MFC], DockPane
- CMDIChildWndEx [MFC], DockPaneLeftOf
- CMDIChildWndEx [MFC], EnableAutoHidePanes
- CMDIChildWndEx [MFC], EnableDocking
- CMDIChildWndEx [MFC], EnableTaskbarThumbnailClipRect
- CMDIChildWndEx [MFC], GetDockingManager
- CMDIChildWndEx [MFC], GetDocumentName
- CMDIChildWndEx [MFC], GetFrameIcon
- CMDIChildWndEx [MFC], GetFrameText
- CMDIChildWndEx [MFC], GetPane
- CMDIChildWndEx [MFC], GetRelatedTabGroup
- CMDIChildWndEx [MFC], GetTabbedPane
- CMDIChildWndEx [MFC], GetTabProxyWnd
- CMDIChildWndEx [MFC], GetTaskbarPreviewWnd
- CMDIChildWndEx [MFC], GetTaskbarThumbnailClipRect
- CMDIChildWndEx [MFC], GetToolbarButtonToolTipText
- CMDIChildWndEx [MFC], InsertPane
- CMDIChildWndEx [MFC], InvalidateIconicBitmaps
- CMDIChildWndEx [MFC], IsPointNearDockSite
- CMDIChildWndEx [MFC], IsReadOnly
- CMDIChildWndEx [MFC], IsRegisteredWithTaskbarTabs
- CMDIChildWndEx [MFC], IsTabbedPane
- CMDIChildWndEx [MFC], IsTaskbarTabsSupportEnabled
- CMDIChildWndEx [MFC], IsTaskbarThumbnailClipRectEnabled
- CMDIChildWndEx [MFC], m_dwDefaultTaskbarTabPropertyFlags
- CMDIChildWndEx [MFC], OnGetIconicLivePreviewBitmap
- CMDIChildWndEx [MFC], OnGetIconicThumbnail
- CMDIChildWndEx [MFC], OnMoveMiniFrame
- CMDIChildWndEx [MFC], OnPressTaskbarThmbnailCloseButton
- CMDIChildWndEx [MFC], OnSetPreviewMode
- CMDIChildWndEx [MFC], OnTaskbarTabThumbnailActivate
- CMDIChildWndEx [MFC], OnTaskbarTabThumbnailMouseActivate
- CMDIChildWndEx [MFC], OnTaskbarTabThumbnailStretch
- CMDIChildWndEx [MFC], OnUpdateFrameTitle
- CMDIChildWndEx [MFC], PaneFromPoint
- CMDIChildWndEx [MFC], RecalcLayout
- CMDIChildWndEx [MFC], RegisterTaskbarTab
- CMDIChildWndEx [MFC], RemovePaneFromDockManager
- CMDIChildWndEx [MFC], SetRelatedTabGroup
- CMDIChildWndEx [MFC], SetTaskbarTabActive
- CMDIChildWndEx [MFC], SetTaskbarTabOrder
- CMDIChildWndEx [MFC], SetTaskbarTabProperties
- CMDIChildWndEx [MFC], SetTaskbarThumbnailClipRect
- CMDIChildWndEx [MFC], ShowPane
- CMDIChildWndEx [MFC], UnregisterTaskbarTab
- CMDIChildWndEx [MFC], UpdateTaskbarTabIcon
ms.assetid: d39fec06-0bd6-4271-917d-35aae3b24d8e
ms.openlocfilehash: 9bb033b7ba366d233c8a0a81f36251d8b3f62808
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505563"
---
# <a name="cmdichildwndex-class"></a>CMDIChildWndEx クラス

クラス`CMDIChildWndEx`は、Windows のマルチドキュメントインターフェイス (MDI) 子ウィンドウの機能を提供します。 [CMDIChildWnd クラス](../../mfc/reference/cmdichildwnd-class.md)の機能が拡張されます。 ある特定の MFC クラスを MDI アプリケーションで使用するときは、フレームワークにこのクラスが必要です。

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

## <a name="syntax"></a>構文

```
class CMDIChildWndEx : public CMDIChildWnd
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMDIChildWndEx:: ActivateTopLevelFrame](#activatetoplevelframe)|アプリケーションをタスクバータブからアクティブ化する必要がある場合に、最上位レベルのフレームをアクティブ化するために、フレームワークによって内部的に呼び出されます。|
|`CMDIChildWndEx::AddDockSite`|このメソッドは使用されていないか、実装されていません。|
|[CMDIChildWndEx:: AddPane](#addpane)|ペインを追加します。|
|[CMDIChildWndEx:: AddTabbedPane](#addtabbedpane)|タブ付きペインを追加します。|
|[CMDIChildWndEx:: AdjustDockingLayout](#adjustdockinglayout)|ドッキングレイアウトを調整します。|
|[CMDIChildWndEx:: CanShowOnMDITabs](#canshowonmditabs)||
|[CMDIChildWndEx:: CanShowOnTaskBarTabs](#canshowontaskbartabs)|この MDI 子が Windows 7 のタスクバータブに表示されるかどうかをフレームワークに指示します。|
|[CMDIChildWndEx::CanShowOnWindowsList](#canshowonwindowslist)|[Cmfcwindowsmanagerdialog クラス](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)ダイアログボックスに MDI 子ウィンドウ名を表示できる場合は TRUE を返します。 それ以外の場合は FALSE を返します。|
|`CMDIChildWndEx::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークによって呼び出されます。|
|[CMDIChildWndEx::D ockPane](#dockpane)|ペインをドッキングします。|
|[CMDIChildWndEx::D ockPaneLeftOf](#dockpaneleftof)|ウィンドウを別のウィンドウの左側にドッキングします。|
|[CMDIChildWndEx:: EnableAutoHidePanes](#enableautohidepanes)|ウィンドウの指定した辺にドッキングされている場合、ウィンドウの自動非表示モードを有効にします。|
|[CMDIChildWndEx:: EnableDocking](#enabledocking)|子ウィンドウをメインフレームにドッキングできるようにします。|
|[CMDIChildWndEx::EnableTaskbarThumbnailClipRect](#enabletaskbarthumbnailcliprect)|ウィンドウのクライアント領域の一部の自動選択を有効または無効にして、そのウィンドウのサムネイルとしてタスクバーに表示します。|
|[CMDIChildWndEx:: Getdoc王国マネージャー](#getdockingmanager)||
|[CMDIChildWndEx:: GetDocumentName](#getdocumentname)|MDI 子ウィンドウに表示されるドキュメントの名前を返します。|
|[CMDIChildWndEx:: Getフレームアイコン](#getframeicon)|MDI 子ウィンドウアイコンを取得するためにフレームワークによって呼び出されます。|
|[CMDIChildWndEx:: Getフレームテキスト](#getframetext)|MDI 子ウィンドウのテキストを取得するためにフレームワークによって呼び出されます。|
|[CMDIChildWndEx:: GetPane](#getpane)|指定されたコントロール ID でペインを検索します。|
|[CMDIChildWndEx:: Get Tabgroup](#getrelatedtabgroup)||
|[CMDIChildWndEx:: GetTabbedPane](#gettabbedpane)|タブ付きドキュメントに変換された埋め込みドッキングペインへのポインターを返します。|
|[CMDIChildWndEx:: GetTabProxyWnd](#gettabproxywnd)|Windows 7 のタスクバータブに実際に登録されているタブプロキシウィンドウを返します。|
|[CMDIChildWndEx::GetTaskbarPreviewWnd](#gettaskbarpreviewwnd)|Windows 7 のタスクバーのタブサムネイルに表示される子ウィンドウ (通常はビューまたは分割ウィンドウ) を取得する必要があるときにフレームワークによって呼び出されます。|
|[CMDIChildWndEx:: GetTaskbarThumbnailClipRect](#gettaskbarthumbnailcliprect)|ウィンドウのクライアント領域の一部を選択して、そのウィンドウのサムネイルとしてタスクバーに表示する必要がある場合に、フレームワークによって呼び出されます。|
|`CMDIChildWndEx::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって呼び出されます。|
|[CMDIChildWndEx:: GetToolbarButtonToolTipText](#gettoolbarbuttontooltiptext)|ツールバーボタンのツールヒントを取得するために、フレームワークによって呼び出されます。|
|[CMDIChildWndEx:: InsertPane](#insertpane)|指定したペインをドッキングマネージャーに登録します。|
|[CMDIChildWndEx:: InvalidateIconicBitmaps](#invalidateiconicbitmaps)|MDI 子のアイコンビットマップ表現を無効にします。|
|[CMDIChildWndEx:: IsPointNearDockSite](#ispointneardocksite)|指定したポイントがドッキングサイトの近くにあるかどうかを判断します。|
|[CMDIChildWndEx:: IsReadOnly](#isreadonly)|子ウィンドウに表示されているドキュメントが読み取り専用の場合に TRUE を返します。 それ以外の場合は FALSE を返します。|
|[CMDIChildWndEx:: IsRegisteredWithTaskbarTabs](#isregisteredwithtaskbartabs)|MDI 子が Windows 7 のタスクバータブに正常に登録された場合に TRUE を返します。|
|[CMDIChildWndEx:: IsTabbedPane](#istabbedpane)|MDI 子ウィンドウにドッキングペインが含まれている場合に TRUE を返します。 それ以外の場合は FALSE を返します。|
|[CMDIChildWndEx:: IsTaskbarTabsSupportEnabled](#istaskbartabssupportenabled)|MDI 子要素が Windows 7 のタスクバータブに表示されるかどうかを示します。|
|[CMDIChildWndEx::IsTaskbarThumbnailClipRectEnabled](#istaskbarthumbnailcliprectenabled)|ウィンドウのクライアント領域の一部を自動的に選択して、タスクバーのウィンドウのサムネイルとして表示するかどうかを指定します。|
|[CMDIChildWndEx:: m_dwDefaultTaskbarTabPropertyFlags](#m_dwdefaulttaskbartabpropertyflags)|タブ (MDI 子) が Windows 7 のタスクバータブに登録されている場合に、フレームワークによって SetTaskbarTabProperties メソッドに渡されるフラグの組み合わせ。 既定の組み合わせは STPF_USEAPPTHUMBNAILWHENACTIVE &#124; STPF_USEAPPPEEKWHENACTIVE です。|
|[CMDIChildWndEx:: OnGetIconicLivePreviewBitmap](#ongeticoniclivepreviewbitmap)|MDI 子のライブプレビューのビットマップを取得する必要がある場合に、フレームワークによって呼び出されます。|
|[CMDIChildWndEx:: Onge Onicthumbnail](#ongeticonicthumbnail)|MDI 子のアイコンのサムネイルのビットマップを取得する必要があるときに、フレームワークによって呼び出されます。|
|[CMDIChildWndEx::OnMoveMiniFrame](#onmoveminiframe)|ミニフレームウィンドウを移動するためにフレームワークによって呼び出されます。|
|[CMDIChildWndEx::OnPressTaskbarThmbnailCloseButton](#onpresstaskbarthmbnailclosebutton)|ユーザーがタスクバーのタブのサムネイルで [閉じる] ボタンを押したときに、フレームワークによって呼び出されます。|
|[CMDIChildWndEx::OnSetPreviewMode](#onsetpreviewmode)|印刷プレビューモードを開始または終了するために、フレームワークによって呼び出されます。|
|[CMDIChildWndEx:: OnTaskbarTabThumbnailActivate](#ontaskbartabthumbnailactivate)|タスクバーのタブサムネイルで WM_ACTIVATE メッセージを処理する必要があるときに、フレームワークによって呼び出されます。|
|[CMDIChildWndEx:: OnTaskbarTabThumbnailMouseActivate](#ontaskbartabthumbnailmouseactivate)|タスクバーのタブサムネイルで WM_MOUSEACTIVATE メッセージを処理する必要があるときに、フレームワークによって呼び出されます。|
|[CMDIChildWndEx::OnTaskbarTabThumbnailStretch](#ontaskbartabthumbnailstretch)|MDI 子の Windows 7 タスクバーのサムネイルプレビュー用にビットマップを拡張する必要があるときに、フレームワークによって呼び出されます。|
|[CMDIChildWndEx::OnUpdateFrameTitle](#onupdateframetitle)|フレームタイトルを更新するためにフレームワークによって呼び出されます。 ( `CMDIChildWnd::OnUpdateFrameTitle`をオーバーライドします)。|
|[CMDIChildWndEx::P aneFromPoint](#panefrompoint)|指定されたポイントを含むペインを返します。|
|`CMDIChildWndEx::PreTranslateMessage`|[TranslateMessage](../../mfc/reference/cwinapp-class.md) および [DispatchMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) の各 Windows 関数にディスパッチされる前に、ウィンドウ メッセージを変換するためにクラス [CWinApp](/windows/win32/api/winuser/nf-winuser-dispatchmessage) で使用されます。 ( [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)をオーバーライドします)。|
|[CMDIChildWndEx:: RecalcLayout](#recalclayout)|ウィンドウのレイアウトを再計算します。|
|[CMDIChildWndEx:: RegisterTaskbarTab](#registertaskbartab)|MDI 子を Windows 7 のタスクバータブに登録します。|
|[CMDIChildWndEx:: RemovePaneFromDockManager](#removepanefromdockmanager)|ドッキングマネージャーからペインを削除します。|
|[CMDIChildWndEx:: Set Tabgroup](#setrelatedtabgroup)||
|[CMDIChildWndEx:: SetTaskbarTabActive](#settaskbartabactive)|対応する Windows 7 タスクバータブをアクティブにします。|
|[CMDIChildWndEx:: SetTaskbarTabOrder](#settaskbartaborder)|Windows 7 のタスクバータブで、指定したウィンドウの前に MDI 子を挿入します。|
|[CMDIChildWndEx:: SetTaskbarTabProperties](#settaskbartabproperties)|Windows 7 のタスクバー タブのプロパティを設定します。|
|[CMDIChildWndEx:: SetTaskbarThumbnailClipRect](#settaskbarthumbnailcliprect)|ウィンドウのクライアント領域の一部を選択してウィンドウのサムネイルとしてタスクバーに表示するために、フレームワークによって内部的に呼び出されます。|
|[CMDIChildWndEx:: ShowPane](#showpane)||
|[CMDIChildWndEx:: UnregisterTaskbarTab](#unregistertaskbartab)|Windows 7 のタスクバータブから MDI 子を削除します。|
|[CMDIChildWndEx:: UpdateTaskbarTabIcon](#updatetaskbartabicon)|Windows 7 のタスクバータブのアイコンを更新します。|

## <a name="remarks"></a>Remarks

Mdi アプリケーションで拡張されたドッキング機能を利用するには、 `CMDIChildWndEx` [CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)ではなく、アプリケーションの mdi 子ウィンドウクラスを派生させます。

## <a name="example"></a>例

次の例では、から`CMDIChildWndEx`クラスを派生させることができます。 このコードスニペットは、VisualStudioDemo [サンプルから抜粋したものです。MFC Visual Studio アプリケーション](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#3](../../mfc/codesnippet/cpp/cmdichildwndex-class_1.h)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CFrameWnd](../../mfc/reference/cframewnd-class.md)

[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)

[CMDIChildWndEx](../../mfc/reference/cmdichildwndex-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxMDIChildWndEx

##  <a name="addpane"></a>CMDIChildWndEx:: AddPane

ペインを追加します。

```
BOOL AddPane(
    CBasePane* pControlBar,
    BOOL bTail = TRUE);
```

### <a name="parameters"></a>パラメーター

*pControlBar*<br/>
からペインへのポインター。

*bTail*<br/>
からドッキングマネージャーのペインの一覧の末尾にペインを追加する場合は TRUE。それ以外の場合は FALSE。

### <a name="return-value"></a>戻り値

ペインがドッキングマネージャーに正常に登録された場合は TRUE。それ以外の場合は FALSE。

##  <a name="addtabbedpane"></a>  CMDIChildWndEx::AddTabbedPane

タブ付きペインを追加します。

```
void AddTabbedPane(CDockablePane* pControlBar);
```

### <a name="parameters"></a>パラメーター

*pControlBar*<br/>
からペインへのポインター。

##  <a name="adjustdockinglayout"></a>CMDIChildWndEx:: AdjustDockingLayout

ドッキングレイアウトを調整します。

```
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```

### <a name="parameters"></a>パラメーター

*hdwp*<br/>
から遅延ウィンドウ位置の構造体を処理します。

##  <a name="canshowonmditabs"></a>CMDIChildWndEx:: CanShowOnMDITabs

```
virtual BOOL CanShowOnMDITabs();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="canshowonwindowslist"></a>CMDIChildWndEx:: CanShowOnWindowsList

[ [Cmfcwindowsmanagerdialog クラス](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)] ダイアログボックスに MDI 子ウィンドウ名を表示できるかどうかを指定します。

```
virtual BOOL CanShowOnWindowsList();
```

### <a name="return-value"></a>戻り値

ウィンドウを**Windows**のダイアログボックスに表示できる場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ウィンドウが**Windows**ダイアログボックスに表示されない場合は、派生クラスでこのメソッドをオーバーライドし、FALSE を返します。 この関数は、から`CMFCWindowsManagerDialog`呼び出されます。

##  <a name="dockpane"></a>CMDIChildWndEx::D ockPane

ペインをドッキングします。

```
void DockPane(
    CBasePane* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
からペインへのポインター。

*nDockBarID*<br/>
からペインの ID。

*lpRect*<br/>
から四角形へのポインター。

### <a name="remarks"></a>Remarks

*LpRect*パラメーターは使用されません。

##  <a name="dockpaneleftof"></a>CMDIChildWndEx::D ockPaneLeftOf

ウィンドウを別のウィンドウの左側にドッキングします。

```
BOOL DockPaneLeftOf(
    CPane* pBar,
    CPane* pLeftOf);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
ドッキングするペインへのポインター。

*自分の*<br/>
参照ポイントとして機能するペインへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、 *Pbar*によって指定されたペインを取得し、で指定したペインの左側にドッキングします。

定義済みの順序で複数のペインをドッキングする場合は、このメソッドを呼び出します。

##  <a name="enableautohidepanes"></a>CMDIChildWndEx:: EnableAutoHidePanes

ウィンドウの指定した辺にドッキングされている場合、ウィンドウの自動非表示モードを有効にします。

```
BOOL EnableAutoHidePanes(DWORD dwDockStyle);
```

### <a name="parameters"></a>パラメーター

*dwDockStyle*<br/>
から有効になっているメインフレームウィンドウの辺を指定します。 次のフラグの1つまたは複数を使用します。

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

##  <a name="enabledocking"></a>CMDIChildWndEx:: EnableDocking

子ウィンドウをメインフレームにドッキングできるようにします。

```
BOOL EnableDocking(DWORD dwDockStyle);
```

### <a name="parameters"></a>パラメーター

*dwDockStyle*<br/>
から有効にするドッキングの配置を指定します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドを呼び出して、メインフレームへのドッキングの配置を有効にします。 CBRS_ALIGN_ フラグの組み合わせを渡すことができます (詳細については、「 [CControlBar:: EnableDocking](../../mfc/reference/ccontrolbar-class.md#enabledocking)」を参照してください)。

##  <a name="getdockingmanager"></a>CMDIChildWndEx:: Getdoc王国マネージャー

```
CDockingManager* GetDockingManager();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getdocumentname"></a>  CMDIChildWndEx::GetDocumentName

MDI 子ウィンドウに表示されるドキュメントの名前を返します。

```
virtual LPCTSTR GetDocumentName(CObject** pObj);
```

### <a name="return-value"></a>戻り値

ドキュメントの名前を格納している文字列へのポインター。

### <a name="remarks"></a>Remarks

ドキュメントは、MDI 子ウィンドウで表示されるものです。 通常、ウィンドウには、ファイルから読み込まれたデータまたはファイルに保存されたデータが表示されます。 したがって、ドキュメントの名前はファイルの名前になります。 の既定の`GetDocumentName`実装では、から`CDocument::GetPathName`取得した文字列が返されます。

ファイルから読み込まれていないドキュメントがウィンドウに表示されている場合は、派生クラスでこのメソッドをオーバーライドし、一意のドキュメント識別子を返します。

`GetDocumentName`は、開いているすべてのドキュメントの状態を保存するときに、フレームワークによって呼び出されます。 返された文字列はレジストリに書き込まれます。

フレームワークが後で状態を復元している場合は、ドキュメント名がレジストリから読み取られ、 [CMDIFrameWndEx:: CreateDocumentWindow](../../mfc/reference/cmdiframewndex-class.md#createdocumentwindow)に渡されます。 [CMDIFrameWndEx](../../mfc/reference/cmdiframewndex-class.md)派生クラスでこのメソッドをオーバーライドし、この名前を持つドキュメントを作成するか開いて、この名前を持つファイルを読み取ります。 ドキュメントがファイルに基づいていない場合は、ドキュメント識別子自体に基づいてドキュメントを作成します。 上記の操作は、ドキュメントを保存して復元する場合にのみ実行してください。

### <a name="example"></a>例

`GetDocumentName` メソッドの使用例を次に示します。 このコードスニペットは、VisualStudioDemo [サンプルから抜粋したものです。MFC Visual Studio アプリケーション](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#17](../../mfc/codesnippet/cpp/cmdichildwndex-class_2.cpp)]

##  <a name="getframeicon"></a>CMDIChildWndEx:: Getフレームアイコン

MDI 子ウィンドウのアイコンを取得するためにフレームワークによって呼び出されます。

```
virtual HICON GetFrameIcon() const;
```

### <a name="return-value"></a>戻り値

ウィンドウアイコンへのハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、MDI 子フレームウィンドウを含む [MDI] タブに表示するアイコンを決定するために、フレームワークによって呼び出されます。

既定では、このメソッドはウィンドウアイコンを返します。 この`GetFrameIcon`動作を`CMDIChildWndEx`カスタマイズするには、派生クラスでをオーバーライドします。

##  <a name="getframetext"></a>  CMDIChildWndEx::GetFrameText

MDI 子ウィンドウのテキストを取得するためにフレームワークによって呼び出されます。

```
virtual CString GetFrameText() const;
```

### <a name="return-value"></a>戻り値

フレームウィンドウテキストを格納している文字列。

### <a name="remarks"></a>Remarks

このメソッドは、MDI 子フレームウィンドウを含む MDI タブに表示するテキストを決定するために、フレームワークによって呼び出されます。

既定では、このメソッドはウィンドウテキストを返します。 この`GetFrameText`動作を`CMDIChildWndEx`カスタマイズするには、派生クラスでをオーバーライドします。

##  <a name="getpane"></a>CMDIChildWndEx:: GetPane

指定されたコントロール ID でペインを検索します。

```
CBasePane* GetPane(UINT nID);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
から検索するペインのコントロール ID。

### <a name="return-value"></a>戻り値

見つかった場合はペインへのポインター。それ以外の場合は NULL。

##  <a name="getrelatedtabgroup"></a>  CMDIChildWndEx::GetRelatedTabGroup

```
CMFCTabCtrl* GetRelatedTabGroup();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="gettabbedpane"></a>CMDIChildWndEx:: GetTabbedPane

MDI タブ付きドキュメントのグループの一部であるドッキングペインへのポインターを返します。

```
CDockablePane* GetTabbedPane() const;
```

### <a name="return-value"></a>戻り値

MDI タブ付きドキュメントのグループの一部であるドッキングペインへのポインター。

##  <a name="gettoolbarbuttontooltiptext"></a>CMDIChildWndEx:: GetToolbarButtonToolTipText

ツールバーボタンのツールヒントを取得するために、フレームワークによって呼び出されます。

```
virtual BOOL GetToolbarButtonToolTipText(
    CMFCToolBarButton*,
    CString&);
```

### <a name="return-value"></a>戻り値

ツールヒントが表示されている場合は TRUE。 既定の実装では、FALSE が返されます。

### <a name="remarks"></a>Remarks

ツールバーボタンのカスタムツールヒントを表示する場合は、このメソッドをオーバーライドします。

##  <a name="insertpane"></a>CMDIChildWndEx:: InsertPane

指定したペインをドッキングマネージャーに登録します。

```
BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter = TRUE);
```

### <a name="parameters"></a>パラメーター

*pControlBar*<br/>
から挿入するペインへのポインター。

*pTarget*<br/>
から隣接するペインへのポインター。

*bAfter*<br/>
からTRUE の場合、 *Ptarget*の後に*pControlBar*が挿入されます。 FALSE の場合、 *Ptarget*の前に*pControlBar*が挿入されます。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE、それ以外の場合は FALSE。

##  <a name="ispointneardocksite"></a>CMDIChildWndEx:: IsPointNearDockSite

指定したポイントがドッキングサイトの近くにあるかどうかを判断します。

```
BOOL IsPointNearDockSite(
    CPoint point,
    DWORD& dwBarAlignment,
    BOOL& bOuterEdge) const;
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
から指定されたポイント。

*dwBarAlignment*<br/>
からポイントが近づいている端を指定します。 指定できる値は、CBRS_ALIGN_LEFT、CBRS_ALIGN_RIGHT、CBRS_ALIGN_TOP、および CBRS_ALIGN_BOTTOM です。

*bOuterEdge*<br/>
からポイントがドッキングサイトの外側の境界の近くにある場合は TRUE。それ以外の場合は FALSE。

### <a name="return-value"></a>戻り値

ポイントがドッキングサイトの近くにある場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ドッキングマネージャーの感度セット内にあるポイントは、ドッキングサイトの近くにあります。 既定の感度は15ピクセルです。

##  <a name="isreadonly"></a>CMDIChildWndEx:: IsReadOnly

子ウィンドウに表示されるドキュメントを読み取り専用にするかどうかを指定します。

```
virtual BOOL IsReadOnly();
```

### <a name="return-value"></a>戻り値

ドキュメントが読み取り専用の場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

この関数は、読み取り専用のドキュメントが保存されないようにするために使用します。

### <a name="example"></a>例

メソッドを`IsReadOnly`オーバーライドする例を次に示します。 このコードスニペットは、VisualStudioDemo [サンプルから抜粋したものです。MFC Visual Studio アプリケーション](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#2](../../mfc/codesnippet/cpp/cmdichildwndex-class_3.cpp)]

##  <a name="istabbedpane"></a>CMDIChildWndEx:: IsTabbedPane

MDI 子ウィンドウにドッキングペインを表示するかどうかを指定します。

```
BOOL IsTabbedPane() const;
```

### <a name="return-value"></a>戻り値

MDI 子ウィンドウに、タブ付きドキュメントに変換されたドッキングペインが含まれている場合は TRUE。それ以外の場合は FALSE。

##  <a name="onmoveminiframe"></a>  CMDIChildWndEx::OnMoveMiniFrame

ミニフレームウィンドウを移動するためにフレームワークによって呼び出されます。

```
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```

### <a name="parameters"></a>パラメーター

*pFrame*<br/>
からミニフレームウィンドウへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

##  <a name="onsetpreviewmode"></a>  CMDIChildWndEx::OnSetPreviewMode

印刷プレビューモードを開始または終了するために、フレームワークによって呼び出されます。

```
virtual void OnSetPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>パラメーター

*bPreview*<br/>
からTRUE の場合は、「印刷プレビューモード」と入力します。 FALSE の場合は、印刷プレビューモードを終了します。

*pState*<br/>
から印刷プレビュー状態の構造体へのポインター。

##  <a name="onupdateframetitle"></a>  CMDIChildWndEx::OnUpdateFrameTitle

フレームタイトルを更新するためにフレームワークによって呼び出されます。

```
virtual void OnUpdateFrameTitle(BOOL bAddToTitle);
```

### <a name="parameters"></a>パラメーター

*bAddToTitle*<br/>
からTRUE の場合は、タイトルにドキュメント名を追加します。

##  <a name="panefrompoint"></a>CMDIChildWndEx::P aneFromPoint

指定されたポイントを含むペインを返します。

```
CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    bool bExactBar,
    CRuntimeClass* pRTCBarType) const;

CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    DWORD& dwAlignment,
    CRuntimeClass* pRTCBarType) const;
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
からチェックするポイントを画面座標で指定します。

*nSensitivity*<br/>
から検索領域をこの量だけ増やします。 指定されたポイントが増加した領域内にある場合、ペインは検索条件を満たします。

*bExactBar*<br/>
から*Nsensitivity*パラメーターを無視する場合は TRUE。それ以外の場合は FALSE。

*pRTCBarType*<br/>
からNULL でない場合、メソッドは、指定された型のペインだけを検索します。

*dwAlignment*<br/>
から指定したポイントにペインがある場合、このパラメーターには、指定したポイントに最も近いペインの辺が格納されます。 詳細については、「解説」を参照してください。

### <a name="return-value"></a>戻り値

指定された`CBasePane`ポイントを含むから派生したオブジェクトへのポインター。ペインが見つからなかった場合は NULL。

### <a name="remarks"></a>Remarks

このメソッドを呼び出して、指定したポイントが、ランタイムクラスや可視性などの指定した条件に従っているかどうかを確認します。

関数がを返し、ペインが見つかった場合、 *dwAlignment*には、指定した点のアラインメントが含まれます。 たとえば、ポイントがペインの一番上に最も近い場合、 *dwAlignment*は CBRS_ALIGN_TOP に設定されます。

##  <a name="recalclayout"></a>CMDIChildWndEx:: RecalcLayout

ウィンドウのレイアウトを再計算します。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>パラメーター

*bNotify*<br/>
からTRUE の場合、ウィンドウのアクティブなインプレース項目はレイアウト変更の通知を受け取ります。

##  <a name="removepanefromdockmanager"></a>CMDIChildWndEx:: RemovePaneFromDockManager

ドッキングマネージャーからペインを削除します。

```
void RemovePaneFromDockManager(
    CBasePane* pControlBar,
    BOOL bDestroy,
    BOOL bAdjustLayout,
    BOOL bAutoHide,
    CBasePane* pBarReplacement);
```

### <a name="parameters"></a>パラメーター

*pControlBar*<br/>
から削除するペインへのポインター。

*bDestroy*<br/>
からTRUE の場合、削除されたペインは破棄されます。

*bAdjustLayout*<br/>
からTRUE の場合は、ドッキングレイアウトをすぐに調整します。

*bAutoHide に隠す*<br/>
からTRUE の場合、ドッキングレイアウトは自動的に隠すバーの一覧に関連付けられます。 FALSE の場合、ドッキングレイアウトは通常のペインの一覧に関連付けられます。

*pBarReplacement*<br/>
から削除されたペインを置き換えるペインへのポインター。

##  <a name="setrelatedtabgroup"></a>CMDIChildWndEx:: Set Tabgroup

```
void SetRelatedTabGroup(CMFCTabCtrl* p);
```

### <a name="parameters"></a>パラメーター

から*p*<br/>

### <a name="remarks"></a>Remarks

##  <a name="showpane"></a>CMDIChildWndEx:: ShowPane

```
void ShowPane(
    CBasePane* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>パラメーター

から*Pbar*<br/>

から*bShow*<br/>

から*Bdelay*<br/>

から*Bactivate*<br/>

### <a name="remarks"></a>Remarks

##  <a name="updatetaskbartabicon"></a>CMDIChildWndEx:: UpdateTaskbarTabIcon

Windows 7 のタスクバータブのアイコンを更新します。

```
virtual void UpdateTaskbarTabIcon(HICON hIcon);
```

### <a name="parameters"></a>パラメーター

*hIcon*<br/>
Windows 7 のタスクバータブに表示されるアイコンへのハンドル。

### <a name="remarks"></a>Remarks

##  <a name="unregistertaskbartab"></a>CMDIChildWndEx:: UnregisterTaskbarTab

Windows 7 のタスクバーのタブから MDI 子を削除します。

```
void UnregisterTaskbarTab(BOOL bCheckRegisteredMDIChildCount = TRUE);
```

### <a name="parameters"></a>パラメーター

*bCheckRegisteredMDIChildCount*<br/>
この関数が MDI タブに登録されている MDI 子の数を確認する必要があるかどうかを指定します。 この数値が0の場合、この関数は、アプリケーションのタスクバーのサムネイルからクリッピング四角形を削除します。

### <a name="remarks"></a>Remarks

##  <a name="settaskbarthumbnailcliprect"></a>CMDIChildWndEx:: SetTaskbarThumbnailClipRect

ウィンドウのクライアント領域の一部を選択してウィンドウのサムネイルとしてタスクバーに表示するように、フレームワークによって呼び出されます。

```
virtual BOOL SetTaskbarThumbnailClipRect(CRect rect);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
新しいクリッピング四角形を指定します。 四角形が空または null の場合、クリッピングは削除されます。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="settaskbartabproperties"></a>CMDIChildWndEx:: SetTaskbarTabProperties

Windows 7 のタスクバー タブのプロパティを設定します。

```
void SetTaskbarTabProperties(DWORD dwFlags);
```

### <a name="parameters"></a>パラメーター

*dwFlags*<br/>
STPFLAG の値の組み合わせ。 詳細については、「 [ITaskbarList4:: SetTabProperties](/windows/win32/api/shobjidl_core/nf-shobjidl_core-itaskbarlist4-settabproperties)」を参照してください。

### <a name="remarks"></a>Remarks

##  <a name="settaskbartaborder"></a>CMDIChildWndEx:: SetTaskbarTabOrder

Windows 7 のタスクバータブで、指定したウィンドウの前に MDI 子を挿入します。

```
void SetTaskbarTabOrder(CMDIChildWndEx* pWndBefore = NULL);
```

### <a name="parameters"></a>パラメーター

*pWndBefore*<br/>
サムネイルが左側に挿入される MDI 子ウィンドウへのポインター。 このウィンドウは、によって`RegisterTaskbarTab`既に登録されている必要があります。 この値が NULL の場合、新しいサムネイルが一覧の末尾に追加されます。

### <a name="remarks"></a>Remarks

##  <a name="settaskbartabactive"></a>CMDIChildWndEx:: SetTaskbarTabActive

対応する Windows 7 タスクバータブをアクティブにします。

```
void SetTaskbarTabActive();
```

### <a name="remarks"></a>Remarks

##  <a name="registertaskbartab"></a>CMDIChildWndEx:: RegisterTaskbarTab

MDI 子を Windows 7 タスクバータブに登録します。

```
virtual void RegisterTaskbarTab(CMDIChildWndEx* pWndBefore = NULL);
```

### <a name="parameters"></a>パラメーター

*pWndBefore*<br/>
サムネイルが左側に挿入される MDI 子ウィンドウへのポインター。 このウィンドウは、によって`RegisterTaskbarTab`既に登録されている必要があります。 この値が NULL の場合、新しいサムネイルが一覧の末尾に追加されます。

### <a name="remarks"></a>Remarks

##  <a name="ontaskbartabthumbnailstretch"></a>  CMDIChildWndEx::OnTaskbarTabThumbnailStretch

MDI 子の Windows 7 タスクバーのタブサムネイルプレビューにビットマップを拡大する必要がある場合に、フレームワークによって呼び出されます。

```
virtual BOOL OnTaskbarTabThumbnailStretch(
    HBITMAP hBmpDst,
    const CRect& rectDst,
    HBITMAP hBmpSrc,
    const CRect& rectSrc);
```

### <a name="parameters"></a>パラメーター

*hBmpDst*<br/>
コピー先のビットマップを指定するハンドル。

*rectDst*<br/>
コピー先の四角形を指定します。

*hBmpSrc*<br/>
ソースビットマップを処理するハンドル。

*rectSrc*<br/>
ソースの四角形を指定します。

### <a name="remarks"></a>Remarks

要件: afxmdichildwndex

##  <a name="ontaskbartabthumbnailmouseactivate"></a>CMDIChildWndEx:: OnTaskbarTabThumbnailMouseActivate

タスクバーのタブサムネイルで WM_MOUSEACTIVATE メッセージを処理する必要があるときに、フレームワークによって呼び出されます。

```
virtual int OnTaskbarTabThumbnailMouseActivate(
    CWnd* pDesktopWnd,
    UINT nHitTest,
    UINT message);
```

### <a name="parameters"></a>パラメーター

*pDesktopWnd*<br/>
アクティブにするウィンドウのトップレベルの親ウィンドウへのポインターを指定します。 ポインターは一時的なものである可能性があるため、格納しないでください。

*nHitTest*<br/>
ヒットテスト領域コードを指定します。 ヒットテストは、カーソルの位置を決定するテストです。

*message*<br/>
マウスのメッセージ番号を指定します。

### <a name="remarks"></a>Remarks

既定の実装では、関連する MDI 子フレームがアクティブになります。

##  <a name="ontaskbartabthumbnailactivate"></a>CMDIChildWndEx:: OnTaskbarTabThumbnailActivate

タスクバーのタブサムネイルで WM_ACTIVATE メッセージを処理する必要があるときに、フレームワークによって呼び出されます。

```
virtual void OnTaskbarTabThumbnailActivate(
    UINT nState,
    CWnd* pWndOther,
    BOOL bMinimized);
```

### <a name="parameters"></a>パラメーター

*nState*<br/>
`CWnd`がアクティブ化または非アクティブ化されているかどうかを指定します。

*pWndOther*<br/>
アクティブまたは`CWnd`非アクティブ化されるへのポインター。 ポインターは NULL にすることができ、一時的なものでもかまいません。

*bMinimized*<br/>
アクティブまたは非アクティブ化`CWnd`するの最小化された状態を指定します。 値が TRUE の場合は、ウィンドウが最小化されていることを示します。

### <a name="remarks"></a>Remarks

既定の実装では、関連する MDI 子フレームがアクティブになります。

##  <a name="onpresstaskbarthmbnailclosebutton"></a>CMDIChildWndEx:: OnPressTaskbarThmbnailCloseButton

ユーザーがタスクバーのタブサムネイルの [閉じる] ボタンをクリックしたときに、フレームワークによって呼び出されます。

```
virtual void OnPressTaskbarThmbnailCloseButton();
```

### <a name="remarks"></a>Remarks

##  <a name="ongeticonicthumbnail"></a>CMDIChildWndEx:: Onge Onicthumbnail

MDI 子のアイコン化されたサムネイルのビットマップを取得する必要がある場合に、フレームワークによって呼び出されます。

```
virtual HBITMAP OnGetIconicThumbnail(
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>パラメーター

*nWidth*<br/>
必要なビットマップの幅を指定します。

*nHeight*<br/>
必要なビットマップの高さを指定します。

### <a name="remarks"></a>Remarks

##  <a name="ongeticoniclivepreviewbitmap"></a>  CMDIChildWndEx::OnGetIconicLivePreviewBitmap

MDI 子のライブプレビューのビットマップを取得する必要がある場合に、フレームワークによって呼び出されます。

```
virtual HBITMAP OnGetIconicLivePreviewBitmap(
    BOOL bIsMDIChildActive,
    CPoint& ptLocation);
```

### <a name="parameters"></a>パラメーター

*bIsMDIChildActive*<br/>
このパラメーターは、現在アクティブで、メインウィンドウが最小化されていない MDI 子にビットマップが要求されている場合に TRUE になります。 この場合の既定の処理では、メインウィンドウのスナップショットが取得されます。

*ptLocation*<br/>
メイン (最上位レベル) ウィンドウのクライアント座標におけるビットマップの位置を指定します。 このポイントは、呼び出し先によって提供される必要があります。

### <a name="return-value"></a>戻り値

処理された場合、有効な32bpp ビットマップへのハンドルを返します。それ以外の場合は NULL を返します。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドし、MDI 子のライブプレビューの有効な32bpp ビットマップを返します。 このメソッドは、MDI 子が Windows 7 のタスクバータブに表示される場合にのみ呼び出されます。 NULL を返す場合、MFC は、既定のハンドラーを呼び出し、 `PrintClient`また`PrintWindow`はを使用してビットマップを取得します。

##  <a name="m_dwdefaulttaskbartabpropertyflags"></a>CMDIChildWndEx:: m_dwDefaultTaskbarTabPropertyFlags

タブ (MDI 子) が Windows 7 のタスクバータブに`SetTaskbarTabProperties`登録されている場合に、フレームワークによってメソッドに渡されるフラグの組み合わせ。

```
AFX_IMPORT_DATA static DWORD m_dwDefaultTaskbarTabPropertyFlags;
```

### <a name="remarks"></a>Remarks

既定の組み合わせは STPF_USEAPPTHUMBNAILWHENACTIVE &#124; STPF_USEAPPPEEKWHENACTIVE です。

##  <a name="istaskbarthumbnailcliprectenabled"></a>CMDIChildWndEx:: IsTaskbarThumbnailClipRectEnabled

ウィンドウのクライアント領域の一部を自動的に選択して、タスクバーのウィンドウのサムネイルとして表示するかどうかを指定します。

```
BOOL IsTaskbarThumbnailClipRectEnabled() const;
```

### <a name="return-value"></a>戻り値

ウィンドウのクライアント領域の一部の自動選択が有効になっている場合に TRUE を返します。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="istaskbartabssupportenabled"></a>CMDIChildWndEx:: IsTaskbarTabsSupportEnabled

MDI 子要素が Windows 7 のタスクバータブに表示されるかどうかを示します。

```
BOOL IsTaskbarTabsSupportEnabled();
```

### <a name="return-value"></a>戻り値

MDI 子が Windows 7 のタスクバータブに表示される場合は TRUE。MDI 子が Windows 7 のタスクバータブに表示されない場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="isregisteredwithtaskbartabs"></a>CMDIChildWndEx:: IsRegisteredWithTaskbarTabs

MDI 子要素が Windows 7 のタスクバータブに正常に登録された場合に TRUE を返します。

```
BOOL IsRegisteredWithTaskbarTabs();
```

### <a name="return-value"></a>戻り値

MDI 子が Windows 7 のタスクバータブに登録されている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="invalidateiconicbitmaps"></a>CMDIChildWndEx:: InvalidateIconicBitmaps

MDI 子のアイコン化したビットマップ表現を無効にします。

```
BOOL InvalidateIconicBitmaps();
```

### <a name="return-value"></a>戻り値

Windows 7 のタスクバーのサポートが無効になっている場合、または MDI 子が Windows 7 のタスクバータブに登録されていない場合は FALSE を返します。それ以外の場合は TRUE を返します。

### <a name="remarks"></a>Remarks

MDI 子のライブコンテンツまたはサイズが変更された場合は、を呼び出す必要があります。

##  <a name="gettaskbarthumbnailcliprect"></a>CMDIChildWndEx:: GetTaskbarThumbnailClipRect

ウィンドウのクライアント領域の一部を選択して、そのウィンドウのサムネイルとしてタスクバーに表示する必要がある場合に、フレームワークによって呼び出されます。

```
virtual CRect GetTaskbarThumbnailClipRect() const;
```

### <a name="return-value"></a>戻り値

Windows 座標の四角形。 この四角形は、最上位レベルのフレームのクライアント領域にマップされます。 クリッピング四角形をクリアするには、四角形を空にする必要があります。

### <a name="remarks"></a>Remarks

##  <a name="gettaskbarpreviewwnd"></a>CMDIChildWndEx:: GetTaskbarPreviewWnd

Windows 7 のタスクバーのタブサムネイルに表示される子ウィンドウ (通常はビューまたは分割ウィンドウ) を取得する必要があるときにフレームワークによって呼び出されます。

```
virtual CWnd* GetTaskbarPreviewWnd();
```

### <a name="return-value"></a>戻り値

は、 `CWnd`オブジェクトへの有効なポインターを返す必要があります。このオブジェクトのプレビューは、この MDI 子に関連する Windows 7 タスクバータブに表示されます。 既定の実装は、AFX_IDW_PANE_FIRST コントロール ID (通常`CView`は派生クラス) を持つこの MDI 子の子ウィンドウを返します。

### <a name="remarks"></a>Remarks

##  <a name="gettabproxywnd"></a>CMDIChildWndEx:: GetTabProxyWnd

Windows 7 のタスクバータブに登録されているタブプロキシウィンドウを返します。

```
CMDITabProxyWnd* GetTabProxyWnd();
```

### <a name="return-value"></a>戻り値

Windows 7 のタスク`CMDITabProxyWnd`バータブに登録されているオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="enabletaskbarthumbnailcliprect"></a>CMDIChildWndEx:: EnableTaskbarThumbnailClipRect

ウィンドウのクライアント領域の一部の自動選択を有効または無効にして、そのウィンドウのサムネイルとしてタスクバーに表示します。

```
void EnableTaskbarThumbnailClipRect(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
ウィンドウのクライアント領域の一部を表示するかどうかを、有効 (TRUE) にするか、または無効 (FALSE) にするかを指定します。

### <a name="remarks"></a>Remarks

##  <a name="canshowontaskbartabs"></a>CMDIChildWndEx:: CanShowOnTaskBarTabs

この MDI 子が Windows 7 のタスクバータブに表示されるかどうかをフレームワークに指示します。

```
virtual BOOL CanShowOnTaskBarTabs();
```

### <a name="return-value"></a>戻り値

MDI 子要素のコンテンツを Windows 7 のタスクバーのサムネイルに表示できる場合は TRUE。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドし、FALSE を返して、Windows 7 のタスクバータブでこの MDI 子の表示を無効にします。

##  <a name="activatetoplevelframe"></a>CMDIChildWndEx:: ActivateTopLevelFrame

アプリケーションがタスクバータブからアクティブになったときに最上位レベルのフレームをアクティブ化するために、フレームワークによって呼び出されます。

```
virtual void ActivateTopLevelFrame();
```

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMDIChildWnd クラス](../../mfc/reference/cmdichildwnd-class.md)<br/>
[CMFCWindowsManagerDialog クラス](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)<br/>
[CMDIFrameWndEx クラス](../../mfc/reference/cmdiframewndex-class.md)
