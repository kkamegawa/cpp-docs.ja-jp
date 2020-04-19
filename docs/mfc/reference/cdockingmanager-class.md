---
title: CDockingManager クラス
ms.date: 11/04/2016
f1_keywords:
- CDockingManager
- AFXDOCKINGMANAGER/CDockingManager
- AFXDOCKINGMANAGER/CDockingManager::AddDockSite
- AFXDOCKINGMANAGER/CDockingManager::AddHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::AddMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::AddPane
- AFXDOCKINGMANAGER/CDockingManager::AdjustDockingLayout
- AFXDOCKINGMANAGER/CDockingManager::AdjustPaneFrames
- AFXDOCKINGMANAGER/CDockingManager::AdjustRectToClientArea
- AFXDOCKINGMANAGER/CDockingManager::AlignAutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::AutoHidePane
- AFXDOCKINGMANAGER/CDockingManager::BringBarsToTop
- AFXDOCKINGMANAGER/CDockingManager::BuildPanesMenu
- AFXDOCKINGMANAGER/CDockingManager::CalcExpectedDockedRect
- AFXDOCKINGMANAGER/CDockingManager::Create
- AFXDOCKINGMANAGER/CDockingManager::DeterminePaneAndStatus
- AFXDOCKINGMANAGER/CDockingManager::DisableRestoreDockState
- AFXDOCKINGMANAGER/CDockingManager::DockPane
- AFXDOCKINGMANAGER/CDockingManager::DockPaneLeftOf
- AFXDOCKINGMANAGER/CDockingManager::EnableAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::EnableDocking
- AFXDOCKINGMANAGER/CDockingManager::EnableDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::EnablePaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::FindDockSite
- AFXDOCKINGMANAGER/CDockingManager::FindDockSiteByPane
- AFXDOCKINGMANAGER/CDockingManager::FindPaneByID
- AFXDOCKINGMANAGER/CDockingManager::FixupVirtualRects
- AFXDOCKINGMANAGER/CDockingManager::FrameFromPoint
- AFXDOCKINGMANAGER/CDockingManager::GetClientAreaBounds
- AFXDOCKINGMANAGER/CDockingManager::GetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::GetDockSiteFrameWnd
- AFXDOCKINGMANAGER/CDockingManager::GetEnabledAutoHideAlignment
- AFXDOCKINGMANAGER/CDockingManager::GetMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::GetOuterEdgeBounds
- AFXDOCKINGMANAGER/CDockingManager::GetPaneList
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManager
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingManagerPermanent
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::GetSmartDockingTheme
- AFXDOCKINGMANAGER/CDockingManager::HideAutoHidePanes
- AFXDOCKINGMANAGER/CDockingManager::InsertDockSite
- AFXDOCKINGMANAGER/CDockingManager::InsertPane
- AFXDOCKINGMANAGER/CDockingManager::IsDockSiteMenu
- AFXDOCKINGMANAGER/CDockingManager::IsInAdjustLayout
- AFXDOCKINGMANAGER/CDockingManager::IsOLEContainerMode
- AFXDOCKINGMANAGER/CDockingManager::IsPointNearDockSite
- AFXDOCKINGMANAGER/CDockingManager::IsPrintPreviewValid
- AFXDOCKINGMANAGER/CDockingManager::LoadState
- AFXDOCKINGMANAGER/CDockingManager::LockUpdate
- AFXDOCKINGMANAGER/CDockingManager::OnActivateFrame
- AFXDOCKINGMANAGER/CDockingManager::OnClosePopupMenu
- AFXDOCKINGMANAGER/CDockingManager::OnMoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::OnPaneContextMenu
- AFXDOCKINGMANAGER/CDockingManager::PaneFromPoint
- AFXDOCKINGMANAGER/CDockingManager::ProcessPaneContextMenuCommand
- AFXDOCKINGMANAGER/CDockingManager::RecalcLayout
- AFXDOCKINGMANAGER/CDockingManager::ReleaseEmptyPaneContainers
- AFXDOCKINGMANAGER/CDockingManager::RemoveHiddenMDITabbedBar
- AFXDOCKINGMANAGER/CDockingManager::RemoveMiniFrame
- AFXDOCKINGMANAGER/CDockingManager::RemovePaneFromDockManager
- AFXDOCKINGMANAGER/CDockingManager::ReplacePane
- AFXDOCKINGMANAGER/CDockingManager::ResortMiniFramesForZOrder
- AFXDOCKINGMANAGER/CDockingManager::SaveState
- AFXDOCKINGMANAGER/CDockingManager::SendMessageToMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::Serialize
- AFXDOCKINGMANAGER/CDockingManager::SetAutohideZOrder
- AFXDOCKINGMANAGER/CDockingManager::SetDockingMode
- AFXDOCKINGMANAGER/CDockingManager::SetDockState
- AFXDOCKINGMANAGER/CDockingManager::SetPrintPreviewMode
- AFXDOCKINGMANAGER/CDockingManager::SetSmartDockingParams
- AFXDOCKINGMANAGER/CDockingManager::ShowDelayShowMiniFrames
- AFXDOCKINGMANAGER/CDockingManager::ShowPanes
- AFXDOCKINGMANAGER/CDockingManager::StartSDocking
- AFXDOCKINGMANAGER/CDockingManager::StopSDocking
- AFXDOCKINGMANAGER/CDockingManager::m_bHideDockingBarsInContainerMode
- AFXDOCKINGMANAGER/CDockingManager::m_dockModeGlobal
- AFXDOCKINGMANAGER/CDockingManager::m_nDockSensitivity
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeDockingBarDock
- AFXDOCKINGMANAGER/CDockingManager::m_nTimeOutBeforeToolBarDock
helpviewer_keywords:
- CDockingManager [MFC], AddDockSite
- CDockingManager [MFC], AddHiddenMDITabbedBar
- CDockingManager [MFC], AddMiniFrame
- CDockingManager [MFC], AddPane
- CDockingManager [MFC], AdjustDockingLayout
- CDockingManager [MFC], AdjustPaneFrames
- CDockingManager [MFC], AdjustRectToClientArea
- CDockingManager [MFC], AlignAutoHidePane
- CDockingManager [MFC], AutoHidePane
- CDockingManager [MFC], BringBarsToTop
- CDockingManager [MFC], BuildPanesMenu
- CDockingManager [MFC], CalcExpectedDockedRect
- CDockingManager [MFC], Create
- CDockingManager [MFC], DeterminePaneAndStatus
- CDockingManager [MFC], DisableRestoreDockState
- CDockingManager [MFC], DockPane
- CDockingManager [MFC], DockPaneLeftOf
- CDockingManager [MFC], EnableAutoHidePanes
- CDockingManager [MFC], EnableDocking
- CDockingManager [MFC], EnableDockSiteMenu
- CDockingManager [MFC], EnablePaneContextMenu
- CDockingManager [MFC], FindDockSite
- CDockingManager [MFC], FindDockSiteByPane
- CDockingManager [MFC], FindPaneByID
- CDockingManager [MFC], FixupVirtualRects
- CDockingManager [MFC], FrameFromPoint
- CDockingManager [MFC], GetClientAreaBounds
- CDockingManager [MFC], GetDockingMode
- CDockingManager [MFC], GetDockSiteFrameWnd
- CDockingManager [MFC], GetEnabledAutoHideAlignment
- CDockingManager [MFC], GetMiniFrames
- CDockingManager [MFC], GetOuterEdgeBounds
- CDockingManager [MFC], GetPaneList
- CDockingManager [MFC], GetSmartDockingManager
- CDockingManager [MFC], GetSmartDockingManagerPermanent
- CDockingManager [MFC], GetSmartDockingParams
- CDockingManager [MFC], GetSmartDockingTheme
- CDockingManager [MFC], HideAutoHidePanes
- CDockingManager [MFC], InsertDockSite
- CDockingManager [MFC], InsertPane
- CDockingManager [MFC], IsDockSiteMenu
- CDockingManager [MFC], IsInAdjustLayout
- CDockingManager [MFC], IsOLEContainerMode
- CDockingManager [MFC], IsPointNearDockSite
- CDockingManager [MFC], IsPrintPreviewValid
- CDockingManager [MFC], LoadState
- CDockingManager [MFC], LockUpdate
- CDockingManager [MFC], OnActivateFrame
- CDockingManager [MFC], OnClosePopupMenu
- CDockingManager [MFC], OnMoveMiniFrame
- CDockingManager [MFC], OnPaneContextMenu
- CDockingManager [MFC], PaneFromPoint
- CDockingManager [MFC], ProcessPaneContextMenuCommand
- CDockingManager [MFC], RecalcLayout
- CDockingManager [MFC], ReleaseEmptyPaneContainers
- CDockingManager [MFC], RemoveHiddenMDITabbedBar
- CDockingManager [MFC], RemoveMiniFrame
- CDockingManager [MFC], RemovePaneFromDockManager
- CDockingManager [MFC], ReplacePane
- CDockingManager [MFC], ResortMiniFramesForZOrder
- CDockingManager [MFC], SaveState
- CDockingManager [MFC], SendMessageToMiniFrames
- CDockingManager [MFC], Serialize
- CDockingManager [MFC], SetAutohideZOrder
- CDockingManager [MFC], SetDockingMode
- CDockingManager [MFC], SetDockState
- CDockingManager [MFC], SetPrintPreviewMode
- CDockingManager [MFC], SetSmartDockingParams
- CDockingManager [MFC], ShowDelayShowMiniFrames
- CDockingManager [MFC], ShowPanes
- CDockingManager [MFC], StartSDocking
- CDockingManager [MFC], StopSDocking
- CDockingManager [MFC], m_bHideDockingBarsInContainerMode
- CDockingManager [MFC], m_dockModeGlobal
- CDockingManager [MFC], m_nDockSensitivity
- CDockingManager [MFC], m_nTimeOutBeforeDockingBarDock
- CDockingManager [MFC], m_nTimeOutBeforeToolBarDock
ms.assetid: 98e69c43-55d8-4f43-b861-4fda80ec1e32
ms.openlocfilehash: 8709b3a4eb3f57a3d2700ad7aaed16df994245c5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506869"
---
# <a name="cdockingmanager-class"></a>CDockingManager クラス

メイン フレーム ウィンドウのドッキング レイアウトを制御するコア機能を実装します。

## <a name="syntax"></a>構文

```
class CDockingManager : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDockingManager::AddDockSite](#adddocksite)|ドッキングペインを作成し、コントロールバーのリストに追加します。|
|[CDockingManager::AddHiddenMDITabbedBar](#addhiddenmditabbedbar)|非表示の MDI タブ付きバーペインの一覧に、バーペインへのハンドルを追加します。|
|[CDockingManager:: AddMiniFrame フレーム](#addminiframe)|ミニフレームの一覧にフレームを追加します。|
|[CDockingManager:: AddPane](#addpane)|ペインをドッキングマネージャーに登録します。|
|[CDockingManager:: AdjustDockingLayout](#adjustdockinglayout)|フレームウィンドウ内のすべてのペインのレイアウトを再計算して調整します。|
|[CDockingManager::AdjustPaneFrames](#adjustpaneframes)|WM_NCCALCSIZE メッセージをすべてのペインと`CPaneFrameWnd`ウィンドウに送信します。|
|[CDockingManager::AdjustRectToClientArea](#adjustrecttoclientarea)|四角形の配置を調整します。|
|[CDockingManager::AlignAutoHidePane](#alignautohidepane)|ドッキングサイトで囲まれたフレームのクライアント領域の幅または高さを完全に取得できるように、非自動モードでドッキングペインのサイズを変更します。|
|[CDockingManager:: AutoHidePane](#autohidepane)|自動的に隠すツールバーを作成します。|
|[CDockingManager:: BringBarsToTop](#bringbarstotop)|指定した配置を持つドッキングされたバーを上に配置します。|
|[CDockingManager:: BuildPanesMenu](#buildpanesmenu)|ドッキングペインおよびツールバーの名前をメニューに追加します。|
|[CDockingManager::CalcExpectedDockedRect](#calcexpecteddockedrect)|ドッキングされたウィンドウの予期される四角形を計算します。|
|[CDockingManager:: Create](#create)|ドッキングマネージャーを作成します。|
|[CDockingManager::D Eて Eブランコ Andstatus](#determinepaneandstatus)|指定されたポイントとそのドッキングステータスを含むペインを決定します。|
|[CDockingManager::D isableRestoreDockState](#disablerestoredockstate)|レジストリからのドッキングレイアウトの読み込みを有効または無効にします。|
|[CDockingManager::D ockPane](#dockpane)|ペインを別のペインまたはフレームウィンドウにドッキングします。|
|[CDockingManager::D ockPaneLeftOf](#dockpaneleftof)|ペインを別のペインの左側にドッキングします。|
|[CDockingManager:: EnableAutoHidePanes](#enableautohidepanes)|ペインのメインフレームへのドッキングを有効にし、ドッキングペインを作成して、コントロールバーのリストに追加します。|
|[CDockingManager:: EnableDocking](#enabledocking)|ドッキングペインを作成し、ペインをメインフレームにドッキングできるようにします。|
|[CDockingManager::EnableDockSiteMenu](#enabledocksitemenu)|すべてのドッキングウィンドウのキャプションにポップアップメニューを表示する追加ボタンを表示します。|
|[CDockingManager::EnablePaneContextMenu](#enablepanecontextmenu)|ユーザーがマウスの右ボタンをクリックし、ライブラリが WM_CONTEXTMENU メッセージを処理しているときに、アプリケーションのツールバーとドッキングウィンドウの一覧を含む特別なコンテキストメニューを表示するようライブラリに指示します。|
|[CDockingManager::FindDockSite](#finddocksite)|指定した配置を持つ、指定した位置にあるバーペインを取得します。|
|[CDockingManager::FindDockSiteByPane](#finddocksitebypane)|ターゲットバーペインの id を持つバーペインを返します。|
|[CDockingManager::FindPaneByID](#findpanebyid)|指定されたコントロール ID でペインを検索します。|
|[CDockingManager::FixupVirtualRects](#fixupvirtualrects)|現在のすべてのツールバーの位置を仮想四角形にコミットします。|
|[CDockingManager::FrameFromPoint](#framefrompoint)|指定されたポイントを含むフレームを返します。|
|[CDockingManager::GetClientAreaBounds](#getclientareabounds)|クライアント領域の境界を含む四角形を取得します。|
|[CDockingManager:: Getdoc モード](#getdockingmode)|現在のドッキングモードを返します。|
|[CDockingManager::GetDockSiteFrameWnd](#getdocksiteframewnd)|親ウィンドウフレームへのポインターを取得します。|
|[CDockingManager:: GetEnabledAutoHideAlignment](#getenabledautohidealignment)|ペインの有効な配置を返します。|
|[CDockingManager:: GetMiniFrames](#getminiframes)|ミニフレームの一覧を取得します。|
|[CDockingManager::GetOuterEdgeBounds](#getouteredgebounds)|フレームの外縁を含む四角形を取得します。|
|[CDockingManager:: Get List](#getpanelist)|ドッキングマネージャーに属するペインの一覧を返します。 これには、すべてのフローティングペインが含まれます。|
|[CDockingManager:: Getsmartdoc王国マネージャー](#getsmartdockingmanager)|スマートドッキングマネージャーへのポインターを取得します。|
|[CDockingManager:: Getsmartdocの Managermanagerパーマネント](#getsmartdockingmanagerpermanent)|スマートドッキングマネージャーへのポインターを取得します。|
|[CDockingManager:: Getsmartdocのパラメーター](#getsmartdockingparams)|ドッキングマネージャーのスマートドッキングパラメーターを返します。|
|[CDockingManager:: Getsmartdocのテーマ](#getsmartdockingtheme)|スマートドッキングマーカーの表示に使用するテーマを返す静的メソッド。|
|[CDockingManager:: HideAutoHidePanes](#hideautohidepanes)|自動的に隠すモードのペインを非表示にします。|
|[CDockingManager::InsertDockSite](#insertdocksite)|ドッキングペインを作成し、コントロールバーのリストに挿入します。|
|[CDockingManager:: InsertPane](#insertpane)|コントロールバーのリストにコントロールペインを挿入します。|
|[CDockingManager::IsDockSiteMenu](#isdocksitemenu)|すべてのウィンドウのキャプションにポップアップメニューを表示するかどうかを指定します。|
|[CDockingManager::IsInAdjustLayout](#isinadjustlayout)|すべてのウィンドウのレイアウトを調整するかどうかを決定します。|
|[CDockingManager::IsOLEContainerMode](#isolecontainermode)|ドッキングマネージャーが OLE コンテナーモードであるかどうかを指定します。|
|[CDockingManager::IsPointNearDockSite](#ispointneardocksite)|指定したポイントがドッキングサイトの近くにあるかどうかを判断します。|
|[CDockingManager::IsPrintPreviewValid](#isprintpreviewvalid)|印刷プレビューモードを設定するかどうかを決定します。|
|[CDockingManager:: LoadState](#loadstate)|レジストリからドッキングマネージャーの状態を読み込みます。|
|[CDockingManager:: LockUpdate](#lockupdate)|指定されたウィンドウをロックします。|
|[CDockingManager:: On Frame](#onactivateframe)|フレームウィンドウがアクティブまたは非アクティブになったときにフレームワークによって呼び出されます。|
|[CDockingManager::OnClosePopupMenu](#onclosepopupmenu)|アクティブなポップアップ メニューが WM_DESTROY メッセージを処理するときに、フレームワークによって呼び出されます。|
|[CDockingManager::OnMoveMiniFrame](#onmoveminiframe)|ミニフレームウィンドウを移動するためにフレームワークによって呼び出されます。|
|[CDockingManager::OnPaneContextMenu](#onpanecontextmenu)|ペインのリストを持つメニューをビルドするときに、フレームワークによって呼び出されます。|
|[CDockingManager::P aneFromPoint](#panefrompoint)|指定されたポイントを含むペインを返します。|
|[CDockingManager::P rocessPaneContextMenuCommand](#processpanecontextmenucommand)|指定したコマンドのチェックボックスをオンまたはオフにし、表示されているペインのレイアウトを再計算するために、フレームワークによって呼び出されます。|
|[CDockingManager:: RecalcLayout](#recalclayout)|コントロールのリストに存在するコントロールの内部レイアウトを再計算します。|
|[CDockingManager::ReleaseEmptyPaneContainers](#releaseemptypanecontainers)|空のペインコンテナーを解放します。|
|[CDockingManager::RemoveHiddenMDITabbedBar](#removehiddenmditabbedbar)|指定した非表示バーペインを削除します。|
|[CDockingManager::RemoveMiniFrame](#removeminiframe)|指定したフレームをミニフレームの一覧から削除します。|
|[CDockingManager::RemovePaneFromDockManager](#removepanefromdockmanager)|ペインの登録を解除し、ドッキングマネージャーの一覧から削除します。|
|[CDockingManager:: ReplacePane](#replacepane)|ペインを別のペインに置き換えます。|
|[CDockingManager::ResortMiniFramesForZOrder](#resortminiframesforzorder)|ミニフレームの一覧のフレームを並べ替えます。|
|[CDockingManager:: SaveState](#savestate)|ドッキングマネージャーの状態をレジストリに保存します。|
|[CDockingManager:: SendMessageToMiniFrames](#sendmessagetominiframes)|指定されたメッセージをすべてのミニフレームに送信します。|
|[CDockingManager:: Serialize](#serialize)|ドッキングマネージャーをアーカイブに書き込みます。 ( [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)をオーバーライドします)。|
|[CDockingManager:: SetAutohideZOrder](#setautohidezorder)|コントロールバーと指定したペインのサイズ、幅、および高さを設定します。|
|[CDockingManager:: Setdoc モード](#setdockingmode)|ドッキングモードを設定します。|
|[CDockingManager::SetDockState](#setdockstate)|コントロールバー、ミニフレーム、および自動的に隠すバーのドッキング状態を設定します。|
|[CDockingManager:: Setprintプレビューモード](#setprintpreviewmode)|印刷プレビューに表示されるバーの印刷プレビューモードを設定します。|
|[CDockingManager:: Setsmartdocのパラメーター](#setsmartdockingparams)|スマートドッキングの動作を定義するパラメーターを設定します。|
|[CDockingManager:: ShowDelayShowMiniFrames](#showdelayshowminiframes)|ミニフレームのウィンドウの表示と非表示を切り替えます。|
|[CDockingManager:: ShowPanes](#showpanes)|コントロールのペインおよび自動非表示バーの表示と非表示を切り替えます。|
|[CDockingManager:: StartSDocking](#startsdocking)|スマートドッキングマネージャーの配置に従って、指定したウィンドウのスマートドッキングを開始します。|
|[CDockingManager:: StopSDocking](#stopsdocking)|スマートドッキングを停止します。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CDockingManager::m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)|ドッキングマネージャーが OLE コンテナーモードでペインを非表示にするかどうかを指定します。|
|[CDockingManager::m_dockModeGlobal](#m_dockmodeglobal)|グローバルドッキングモードを指定します。|
|[CDockingManager::m_nDockSensitivity](#m_ndocksensitivity)|ドッキング感度を指定します。|
|[CDockingManager::m_nTimeOutBeforeDockingBarDock](#m_ntimeoutbeforedockingbardock)|ドッキングペインが即時ドッキングモードでドッキングされるまでの時間をミリ秒単位で指定します。|
|[CDockingManager::m_nTimeOutBeforeToolBarDock](#m_ntimeoutbeforetoolbardock)|ツールバーがメインフレームウィンドウにドッキングされるまでの時間をミリ秒単位で指定します。|

## <a name="remarks"></a>Remarks

メインフレームウィンドウは、このクラスを自動的に作成して初期化します。

ドッキングマネージャーオブジェクトは、ドッキングレイアウト内のすべてのペインの一覧を保持します。また、メインフレームウィンドウに属するすべての[CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)ウィンドウの一覧も保持します。

クラス`CDockingManager`は、ペイン`CPaneFrameWnd`またはウィンドウを検索するために使用できるいくつかのサービスを実装します。 通常、これらのサービスはメインフレームウィンドウオブジェクトにラップされるため、直接呼び出さないでください。 詳細については、「 [CPaneFrameWnd クラス](../../mfc/reference/cpaneframewnd-class.md)」を参照してください。

## <a name="customization-tips"></a>カスタマイズのヒント

オブジェクトに`CDockingManager`は、次のヒントが適用されます。

- [CDockingManager クラス](../../mfc/reference/cdockingmanager-class.md)は、次のドッキングモードをサポートしています。

  - `AFX_DOCK_TYPE::DT_IMMEDIATE`

  - `AFX_DOCK_TYPE::DT_STANDARD`

  - `AFX_DOCK_TYPE::DT_SMART`

  これらのドッキングモードは[CDockingManager:: m_dockModeGlobal](#m_dockmodeglobal)によって定義され、 [CDockingManager:: SetDockingMode](#setdockingmode)を呼び出すことによって設定されます。

- サイズ変更できない非サイズのウィンドウを作成する場合は、 [CDockingManager:: AddPane](#addpane)メソッドを呼び出します。 このメソッドは、ペインをドッキングマネージャーに登録します。このペインは、ペインのレイアウトを担当します。

## <a name="example"></a>例

`CDockingManager`クラスのさまざまなメソッドを使用してオブジェクトを`CDockingManager`構成する方法を次の例に示します。 この例では、追加のボタンを表示して、すべてのドッキングウィンドウのキャプションにポップアップメニューを開き、オブジェクトのドッキングモードを設定する方法を示します。 このコードスニペットは、 [Visual Studio のデモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_VisualStudioDemo#24](../../mfc/codesnippet/cpp/cdockingmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CDockingManager](../../mfc/reference/cdockingmanager-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxDockingManager

##  <a name="adddocksite"></a>CDockingManager::AddDockSite

ドッキングペインを作成し、コントロールバーのリストに追加します。

```
BOOL AddDockSite(
    const AFX_DOCKSITE_INFO& info,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>パラメーター

*インフォメーション*<br/>
からドッキングペインの配置を格納している情報構造体への参照。

*ppDockBar*<br/>
入出力新しい dock ペインへのポインターへのポインター。

### <a name="return-value"></a>戻り値

Dock ペインが正常に作成された場合は TRUE。それ以外の場合は FALSE。

##  <a name="addhiddenmditabbedbar"></a>  CDockingManager::AddHiddenMDITabbedBar

非表示の MDI タブ付きバーペインの一覧に、バーペインへのハンドルを追加します。

```
void AddHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
から横棒ペインへのポインター

##  <a name="addpane"></a>CDockingManager:: AddPane

ペインをドッキングマネージャーに登録します。

```
BOOL AddPane(
    CBasePane* pWnd,
    BOOL bTail = TRUE,
    BOOL bAutoHide = FALSE,
    BOOL bInsertForOuterEdge = FALSE);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
[入力、出力]ドッキングマネージャーに追加するペインを指定します。

*bTail*<br/>
からドッキングマネージャーのペインの一覧の末尾にペインを追加する場合は TRUE。それ以外の場合は FALSE。

*bAutoHide に隠す*<br/>
から内部でのみ使用します。 常に既定値の FALSE を使用します。

*bInsertForOuterEdge*<br/>
から内部でのみ使用します。 常に既定値の FALSE を使用します。

### <a name="return-value"></a>戻り値

ペインがドッキングマネージャーに正常に登録された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドを呼び出して、非フローティングでサイズ変更できないペインをドッキングマネージャーに登録します。 ペインを登録しないと、ドッキングマネージャーがレイアウトされても正しく表示されません。

##  <a name="adjustdockinglayout"></a>CDockingManager:: AdjustDockingLayout

フレームウィンドウ内のすべてのペインのレイアウトを再計算して調整します。

```
virtual void AdjustDockingLayout(HDWP hdwp = NULL);
```

### <a name="parameters"></a>パラメーター

*hdwp*<br/>
から遅延ウィンドウ位置の構造を指定します。 詳細については、「 [Windows のデータ型](/windows/win32/WinProg/windows-data-types)」を参照してください。

### <a name="remarks"></a>Remarks

##  <a name="addminiframe"></a>CDockingManager:: AddMiniFrame フレーム

ミニフレームの一覧にフレームを追加します。

```
virtual BOOL AddMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
からフレームへのポインター。

### <a name="return-value"></a>戻り値

フレームがミニフレームのリストに含まれておらず、正常に追加された場合は TRUE。それ以外の場合は FALSE。

##  <a name="adjustpaneframes"></a>CDockingManager::AdjustPaneFrames

WM_NCCALCSIZE メッセージをすべてのペインと`CPaneFrameWnd`ウィンドウに送信します。

```
virtual void AdjustPaneFrames();
```

### <a name="remarks"></a>Remarks

##  <a name="adjustrecttoclientarea"></a>CDockingManager::AdjustRectToClientArea

四角形の配置を調整します。

```
virtual BOOL AdjustRectToClientArea(
    CRect& rectResult,
    DWORD dwAlignment);
```

### <a name="parameters"></a>パラメーター

*rectResult*<br/>
から`CRect`オブジェクトへの参照

*dwAlignment*<br/>
から`CRect`オブジェクトの配置

### <a name="return-value"></a>戻り値

`CRect`オブジェクトの配置が調整された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

*DwAlignment*パラメーターには、次のいずれかの値を指定できます。

- CBRS_ALIGN_TOP

- CBRS_ALIGN_BOTTOM

- CBRS_ALIGN_LEFT

- CBRS_ALIGN_RIGHT

##  <a name="alignautohidepane"></a>CDockingManager::AlignAutoHidePane

ドッキングサイトで囲まれたフレームのクライアント領域の幅または高さを完全に取得できるように、非自動モードでドッキングペインのサイズを変更します。

```
void AlignAutoHidePane(
    CPaneDivider* pDefaultSlider,
    BOOL bIsVisible = TRUE);
```

### <a name="parameters"></a>パラメーター

*pDefaultSlider*<br/>
からドッキングスライダーペイン。

*bIsVisible*<br/>
からドッキングペインが表示されている場合は TRUE。それ以外の場合は FALSE。

##  <a name="autohidepane"></a>  CDockingManager::AutoHidePane

自動的に隠すツールバーを作成します。

```
CMFCAutoHideToolBar* AutoHidePane(
    CDockablePane* pBar,
    CMFCAutoHideToolBar* pCurrAutoHideToolBar = NULL);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
からバーペインへのポインター。

*pCurrAutoHideToolBar*<br/>
から自動的に隠すツールバーへのポインター。

### <a name="return-value"></a>戻り値

[自動的に隠す] ツールバーが作成されなかった場合は NULL になります。それ以外の場合は、新しいツールバーへのポインター。

##  <a name="bringbarstotop"></a>  CDockingManager::BringBarsToTop

指定した配置を持つドッキングされたバーを上に配置します。

```
void BringBarsToTop(
    DWORD dwAlignment = 0,
    BOOL bExcludeDockedBars = TRUE);
```

### <a name="parameters"></a>パラメーター

*dwAlignment*<br/>
から他のウィンドウの上部に移動するドッキングバーの配置。

*bExcludeDockedBars*<br/>
からドッキングされたバーを上から外す場合は TRUE。それ以外の場合は FALSE。

##  <a name="buildpanesmenu"></a>CDockingManager:: BuildPanesMenu

ドッキングペインおよびツールバーの名前をメニューに追加します。

```
void BuildPanesMenu(
    CMenu& menu,
    BOOL bToolbarsOnly);
```

### <a name="parameters"></a>パラメーター

*メニュー*<br/>
からドッキングペインおよびツールバーの名前を追加するメニュー。

*bToolbarsOnly*<br/>
からメニューにツールバーの名前のみを追加する場合は TRUE。それ以外の場合は FALSE。

##  <a name="calcexpecteddockedrect"></a>CDockingManager::CalcExpectedDockedRect

ドッキングされたウィンドウの予期される四角形を計算します。

```
void CalcExpectedDockedRect(
    CWnd* pWnd,
    CPoint ptMouse,
    CRect& rectResult,
    BOOL& bDrawTab,
    CDockablePane** ppTargetBar);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
からドッキングするウィンドウへのポインター。

*ptMouse*<br/>
からマウスの位置。

*rectResult*<br/>
入出力計算された四角形。

*bDrawTab タブ*<br/>
からタブを描画する場合は TRUE。それ以外の場合は FALSE。

*ppTargetBar*<br/>
入出力ターゲットペインへのポインターへのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、ユーザーがウィンドウを*Ptmouse*によって指定されたポイントにドラッグし、そこにドッキングした場合に、ウィンドウが占める四角形を計算します。

##  <a name="create"></a>CDockingManager:: Create

ドッキングマネージャーを作成します。

```
BOOL Create(CFrameWnd* pParentWnd);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
からドッキングマネージャーの親フレームへのポインター。 この値を NULL にすることはできません。

### <a name="return-value"></a>戻り値

常に TRUE です。

##  <a name="determinepaneandstatus"></a>CDockingManager::D Eて Eブランコ Andstatus

指定されたポイントとそのドッキングステータスを含むペインを決定します。

```
virtual AFX_CS_STATUS DeterminePaneAndStatus(
    CPoint pt,
    int nSensitivity,
    DWORD dwEnabledAlignment,
    CBasePane** ppTargetBar,
    const CBasePane* pBarToIgnore,
    const CBasePane* pBarToDock);
```

### <a name="parameters"></a>パラメーター

*未満*<br/>
から確認するペインの位置。

*nSensitivity*<br/>
からオンになっている各ペインのウィンドウ四角形を増やす値。 特定のポイントがこの増加した領域にある場合、ペインは検索条件を満たします。

*dwEnabledAlignment*<br/>
からドッキングペインの配置。

*ppTargetBar*<br/>
入出力ターゲットペインへのポインターへのポインター。

*pBarToIgnore*<br/>
からメソッドが無視するペイン。

*pBarToDock*<br/>
からドッキングされるウィンドウ。

### <a name="return-value"></a>戻り値

ドッキングステータス。

### <a name="remarks"></a>Remarks

ドッキング状態には、次のいずれかの値を指定できます。

|AFX_CS_STATUS 値|説明|
|---------------------------|-------------|
|CS_NOTHING|ポインターがドッキングサイト上にありません。 そのため、ペインはフローティング状態のままにします。|
|CS_DOCK_IMMEDIATELY|ポインターは、イミディエイトモードの dock サイト上にあります (DT_IMMEDIATE style が有効になっているため)。そのため、ウィンドウをすぐにドッキングする必要があります。|
|CS_DELAY_DOCK|ポインターがドッキングサイト上にあり、別のドッキングウィンドウであるか、またはメインフレームの端になっています。|
|CS_DELAY_DOCK_TO_TAB|ポインターがドッキングサイト上にあり、その結果、ペインがタブ付きウィンドウにドッキングされます。 このエラーは、マウスが別のドッキングウィンドウのキャプションまたはタブ付きペインのタブ領域上にある場合に発生します。|

##  <a name="disablerestoredockstate"></a>CDockingManager::D isableRestoreDockState

レジストリからのドッキングレイアウトの読み込みを有効または無効にします。

```
void DisableRestoreDockState(BOOL bDisable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bDisable*<br/>
からレジストリからのドッキングレイアウトの読み込みを無効にする場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

アプリケーションの状態を読み込んでいるときに、ドッキングペインおよびツールバーの現在のレイアウトを保持する必要がある場合は、このメソッドを呼び出します。

##  <a name="dockpane"></a>CDockingManager::D ockPane

ペインを別のペインまたはフレームウィンドウにドッキングします。

```
void DockPane(
    CBasePane* pBar,
    UINT nDockBarID = 0,
    LPCRECT lpRect = NULL);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
からドッキング先のバーペインへのポインター。

*nDockBarID*<br/>
からドッキングするバーの id。

*lpRect*<br/>
からコピー先の四角形。

##  <a name="dockpaneleftof"></a>CDockingManager::D ockPaneLeftOf

ペインを別のペインの左側にドッキングします。

```
BOOL DockPaneLeftOf(
    CPane* pBarToDock,
    CPane* pTargetBar);
```

### <a name="parameters"></a>パラメーター

*pBarToDock*<br/>
から*Ptargetbar*の左側にドッキングするペインへのポインター。

*pTargetBar*<br/>
からターゲットペインへのポインター。

### <a name="return-value"></a>戻り値

ペインが正常にドッキングされた場合は TRUE。それ以外の場合は FALSE。

##  <a name="enableautohidepanes"></a>CDockingManager:: EnableAutoHidePanes

ペインのメインフレームへのドッキングを有効にし、ドッキングペインを作成して、コントロールバーのリストに追加します。

```
BOOL EnableAutoHidePanes(DWORD dwStyle);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
からドッキングの配置。

### <a name="return-value"></a>戻り値

Dock ペインが正常に作成された場合は TRUE。それ以外の場合は FALSE。

##  <a name="enabledocking"></a>CDockingManager:: EnableDocking

ドッキングペインを作成し、ペインをメインフレームにドッキングできるようにします。

```
BOOL EnableDocking(DWORD dwStyle);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
からドッキングの配置。

### <a name="return-value"></a>戻り値

Dock ペインが正常に作成された場合は TRUE。それ以外の場合は FALSE。

##  <a name="enabledocksitemenu"></a>CDockingManager::EnableDockSiteMenu

すべてのドッキングウィンドウのキャプションにポップアップメニューを表示する追加ボタンを表示します。

```
static void EnableDockSiteMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
からDock サイトメニューを有効にする場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

[ドックサイト] メニューには、ウィンドウのドッキング状態を変更するための次のオプションが表示されます。

- `Floating`-ペインをフローティングします

- `Docking`-ペインが最後にドッキングされた場所のメインフレームにペインをドッキングします。

- `AutoHide`-ウィンドウを自動非表示モードに切り替えます

- `Hide`-ペインを非表示にします

既定では、このメニューは表示されません。

##  <a name="enablepanecontextmenu"></a>CDockingManager::EnablePaneContextMenu

ユーザーがマウスの右ボタンをクリックし、ライブラリが WM_CONTEXTMENU メッセージを処理しているときに、アプリケーションのツールバーとドッキングウィンドウの一覧を含む特別なコンテキストメニューを表示するようライブラリに指示します。

```
void EnablePaneContextMenu(
    BOOL bEnable,
    UINT uiCustomizeCmd,
    const CString& strCustomizeText,
    BOOL bToolbarsOnly = FALSE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
からTRUE の場合、ライブラリは自動コンテキストメニューのサポートを有効にします。FALSE の場合、ライブラリは自動コンテキストメニューのサポートをオフにします。

*uiCustomizeCmd*<br/>
からメニューの**カスタマイズ**項目のコマンド id。

*strCustomizeText*<br/>
から**カスタマイズ**項目のテキスト。

*bToolbarsOnly*<br/>
からTRUE の場合、メニューにはアプリケーションのツールバーの一覧のみが表示されます。FALSE の場合、ライブラリはアプリケーションのドッキングペインをこの一覧に追加します。

##  <a name="finddocksite"></a>CDockingManager::FindDockSite

指定した配置を持つ、指定した位置にあるバーペインを取得します。

```
virtual CDockSite* FindDockSite(
    DWORD dwAlignment,
    BOOL bOuter);
```

### <a name="parameters"></a>パラメーター

*dwAlignment*<br/>
からバーペインの配置。

*bOuter*<br/>
からTRUE の場合は、コントロールバーのリストの先頭位置にあるバーを取得します。 それ以外の場合は、コントロールバーの一覧の末尾の位置にあるバーを取得します。

### <a name="return-value"></a>戻り値

指定した配置のドッキングペイン。それ以外の場合は NULL です。

##  <a name="findpanebyid"></a>CDockingManager::FindPaneByID

指定されたコントロール ID でペインを検索します。

```
virtual CBasePane* FindPaneByID(
    UINT uBarID,
    BOOL bSearchMiniFrames = FALSE);
```

### <a name="parameters"></a>パラメーター

*uBarID*<br/>
から検索するペインのコントロール ID を指定します。

*bSearchMiniFrames*<br/>
からすべてのフローティングペインを検索に含める場合は TRUE。 ドッキングされたペインだけを含める場合は FALSE。

### <a name="return-value"></a>戻り値

指定したコントロール ID を持つ[Cbasepane](../../mfc/reference/cbasepane-class.md)オブジェクト。指定したペインが見つからない場合は NULL。

### <a name="remarks"></a>Remarks

##  <a name="finddocksitebypane"></a>CDockingManager::FindDockSiteByPane

ターゲットバーペインの id を持つバーペインを返します。

```
virtual CDockSite* FindDockSiteByPane(CPane* pTargetBar);
```

### <a name="parameters"></a>パラメーター

*pTargetBar*<br/>
からターゲットバーペインへのポインター。

### <a name="return-value"></a>戻り値

ターゲットバーペインの id を持つバーペイン。このようなバーペインが存在しない場合は NULL です。

##  <a name="fixupvirtualrects"></a>CDockingManager::FixupVirtualRects

現在のすべてのツールバーの位置を仮想四角形にコミットします。

```
virtual void FixupVirtualRects();
```

### <a name="remarks"></a>Remarks

ユーザーがツールバーのドラッグを開始すると、アプリケーションは*仮想四角形*内の元の位置を記憶します。 ユーザーがドッキングサイトでツールバーを移動すると、ツールバーに他のツールバーが表示される場合があります。 他のツールバーの元の位置は、対応する仮想四角形に格納されます。

##  <a name="framefrompoint"></a>CDockingManager::FrameFromPoint

指定されたポイントを含むフレームを返します。

```
virtual CPaneFrameWnd* FrameFromPoint(
    CPoint pt,
    CPaneFrameWnd* pFrameToExclude,
    BOOL bFloatMultiOnly) const;
```

### <a name="parameters"></a>パラメーター

*未満*<br/>
からチェックするポイントを画面座標で指定します。

*Pフレームの除外*<br/>
から除外するフレームへのポインター。

*bFloatMultiOnly*<br/>
からの`CMultiPaneFrameWnd`インスタンスではないフレームを除外する場合は TRUE。それ以外の場合は FALSE。

### <a name="return-value"></a>戻り値

指定した点を含むフレーム。それ以外の場合は NULL です。

##  <a name="getclientareabounds"></a>CDockingManager::GetClientAreaBounds

クライアント領域の境界を含む四角形を取得します。

```
CRect GetClientAreaBounds() const;

void GetClientAreaBounds(CRect& rcClient);
```

### <a name="parameters"></a>パラメーター

*rcClient*<br/>
入出力クライアント領域の境界を格納する四角形への参照。

### <a name="return-value"></a>戻り値

クライアント領域の境界を格納している四角形。

##  <a name="getdockingmode"></a>CDockingManager:: Getdoc モード

現在のドッキングモードを返します。

```
static AFX_DOCK_TYPE GetDockingMode();
```

### <a name="return-value"></a>戻り値

現在のドッキングモードを表す列挙子の値。 次のいずれかの値を指定できます。

- DT_STANDARD

- DT_IMMEDIATE

- DT_SMART

### <a name="remarks"></a>Remarks

ドッキングモードを設定するには、 [CDockingManager:: Setdoc モード](#setdockingmode)を呼び出します。

##  <a name="getdocksiteframewnd"></a>CDockingManager::GetDockSiteFrameWnd

親ウィンドウフレームへのポインターを取得します。

```
CFrameWnd* GetDockSiteFrameWnd() const;
```

### <a name="return-value"></a>戻り値

親ウィンドウフレームへのポインター。

##  <a name="getenabledautohidealignment"></a>CDockingManager:: GetEnabledAutoHideAlignment

ペインの有効な配置を返します。

```
DWORD GetEnabledAutoHideAlignment() const;
```

### <a name="return-value"></a>戻り値

CBRS_ALIGN_ フラグのビットごとの組み合わせ。自動非自動化ペインが有効になっていない場合は0。 詳細については、「 [CFrameWnd:: EnableDocking](../../mfc/reference/cframewnd-class.md#enabledocking)」を参照してください。

### <a name="remarks"></a>Remarks

このメソッドは、コントロールバーを自動的に隠すために有効な配置を返します。 自動的に隠すバーを有効にするには、 [CFrameWndEx:: EnableAutoHidePanes](../../mfc/reference/cframewndex-class.md#enableautohidepanes)を呼び出します。

##  <a name="getminiframes"></a>CDockingManager:: GetMiniFrames

ミニフレームの一覧を取得します。

```
const CObList& GetMiniFrames() const;
```

### <a name="return-value"></a>戻り値

ドッキングマネージャーに属するコントロールバーを含む miniframes の一覧。

##  <a name="getouteredgebounds"></a>CDockingManager::GetOuterEdgeBounds

フレームの外縁を含む四角形を取得します。

```
CRect GetOuterEdgeBounds() const;
```

### <a name="return-value"></a>戻り値

フレームの外縁を含む四角形。

##  <a name="getpanelist"></a>CDockingManager:: Get List

ドッキングマネージャーに属するペインの一覧を返します。 これには、すべてのフローティングペインが含まれます。

```
void GetPaneList(
    CObList& lstBars,
    BOOL bIncludeAutohide = FALSE,
    CRuntimeClass* pRTCFilter = NULL,
    BOOL bIncludeTabs = FALSE);
```

### <a name="parameters"></a>パラメーター

*lstBars*<br/>
[入力、出力]現在のドッキングマネージャーのすべてのペインが含まれます。

*bIncludeAutohide*<br/>
から自動非自動モードのペインを含める場合は TRUE。それ以外の場合は FALSE。

*pRTCFilter*<br/>
からNULL 以外の場合、返される一覧には、指定されたランタイムクラスのペインだけが含まれます。

*bIncludeTabs*<br/>
からタブを含める場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ドッキングマネージャーにタブ付きペインがある場合、メソッドは[CBaseTabbedPane クラス](../../mfc/reference/cbasetabbedpane-class.md)オブジェクトへのポインターを返し、タブを明示的に列挙する必要があります。

*Prtcfilter*を使用して、特定のクラスのペインを取得します。 たとえば、この値を適切に設定することによってのみ、ツールバーを取得できます。

##  <a name="getsmartdockingmanager"></a>CDockingManager:: Getsmartdoc王国マネージャー

スマートドッキングマネージャーへのポインターを取得します。

```
CSmartDockingManager* GetSmartDockingManager();
```

### <a name="return-value"></a>戻り値

スマートドッキングマネージャーへのポインター。

##  <a name="getsmartdockingmanagerpermanent"></a>CDockingManager:: Getsmartdocの Managermanagerパーマネント

スマートドッキングマネージャーへのポインターを取得します。

```
CSmartDockingManager* GetSmartDockingManagerPermanent() const;
```

### <a name="return-value"></a>戻り値

スマートドッキングマネージャーへのポインター。

##  <a name="getsmartdockingparams"></a>CDockingManager:: Getsmartdocのパラメーター

ドッキングマネージャーのスマートドッキングパラメーターを返します。

```
static CSmartDockingInfo& GetSmartDockingParams();
```

### <a name="return-value"></a>戻り値

現在のドッキングマネージャーのスマートドッキングパラメーターを格納しているクラス。 詳細については、「 [Csmartdocの情報クラス](../../mfc/reference/csmartdockinginfo-class.md)」を参照してください。

### <a name="remarks"></a>Remarks

##  <a name="hideautohidepanes"></a>CDockingManager:: HideAutoHidePanes

自動的に隠すモードのペインを非表示にします。

```
void HideAutoHidePanes(
    CDockablePane* pBarToExclude = NULL,
    BOOL bImmediately = FALSE);
```

### <a name="parameters"></a>パラメーター

*pBarToExclude*<br/>
から非表示から除外するバーを指すポインター。

*bImmediately ちに*<br/>
からペインをすぐに非表示にする場合は TRUE。[自動非表示] 効果を使用してペインを非表示にする場合は FALSE。

##  <a name="insertdocksite"></a>CDockingManager::InsertDockSite

ドッキングペインを作成し、コントロールバーのリストに挿入します。

```
BOOL InsertDockSite(
    const AFX_DOCKSITE_INFO& info,
    DWORD dwAlignToInsertAfter,
    CDockSite** ppDockBar = NULL);
```

### <a name="parameters"></a>パラメーター

*インフォメーション*<br/>
からドッキングペインに関する配置情報を格納している構造体。

*dwAlignToInsertAfter*<br/>
からドッキングペインの配置。

*ppDockBar*<br/>
入出力ドッキングペインへのポインターへのポインター。

### <a name="return-value"></a>戻り値

Dock ペインが正常に作成された場合は TRUE。それ以外の場合は FALSE。

##  <a name="insertpane"></a>CDockingManager:: InsertPane

コントロールバーのリストにコントロールペインを挿入します。

```
BOOL InsertPane(
    CBasePane* pControlBar,
    CBasePane* pTarget,
    BOOL bAfter = TRUE);
```

### <a name="parameters"></a>パラメーター

*pControlBar*<br/>
からコントロールペインへのポインター。

*pTarget*<br/>
からターゲットペインへのポインター。

*bAfter*<br/>
からターゲットペインの位置の後にペインを挿入する場合は TRUE。それ以外の場合は FALSE。

### <a name="return-value"></a>戻り値

コントロールペインがコントロールバーのリストに正常に追加された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

コントロールペインがコントロールバーのリストに既に存在する場合、またはターゲットペインがコントロールバーの一覧に存在しない場合、このメソッドは false を返します。

##  <a name="isdocksitemenu"></a>CDockingManager::IsDockSiteMenu

すべてのウィンドウのキャプションにポップアップメニューを表示するかどうかを指定します。

```
static BOOL IsDockSiteMenu();
```

### <a name="return-value"></a>戻り値

すべてのドッキングウィンドウのキャプションにドッキングサイトメニューを表示する場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

[CDockingManager:: EnableDockSiteMenu](#enabledocksitemenu)を呼び出すことによって、dock サイトメニューを有効にすることができます。

##  <a name="isinadjustlayout"></a>CDockingManager::IsInAdjustLayout

すべてのウィンドウのレイアウトを調整するかどうかを決定します。

```
BOOL IsInAdjustLayout() const;
```

### <a name="return-value"></a>戻り値

すべてのペインのレイアウトが調整される場合は TRUE。それ以外の場合は FALSE。

##  <a name="isolecontainermode"></a>CDockingManager::IsOLEContainerMode

ドッキングマネージャーが OLE コンテナーモードであるかどうかを指定します。

```
BOOL IsOLEContainerMode() const;
```

### <a name="return-value"></a>戻り値

ドッキングマネージャーが OLE コンテナーモードの場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

OLE コンテナーモードでは、すべてのドッキングウィンドウとアプリケーションツールバーが非表示になります。 [CDockingManager:: m_bHideDockingBarsInContainerMode](#m_bhidedockingbarsincontainermode)を TRUE に設定している場合、このモードではペインも表示されません。

##  <a name="ispointneardocksite"></a>CDockingManager::IsPointNearDockSite

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
入出力ポイントが近づいている端を指定します。 指定できる値は、CBRS_ALIGN_LEFT、CBRS_ALIGN_RIGHT、CBRS_ALIGN_TOP、および CBRS_ALIGN_BOTTOM です。

*bOuterEdge*<br/>
入出力ポイントがドッキングサイトの外側の境界の近くにある場合は TRUE。それ以外の場合は FALSE。

### <a name="return-value"></a>戻り値

ポイントがドッキングサイトの近くにある場合は TRUE。それ以外の場合は FALSE。

##  <a name="isprintpreviewvalid"></a>CDockingManager::IsPrintPreviewValid

印刷プレビューモードを設定するかどうかを決定します。

```
BOOL IsPrintPreviewValid() const;
```

### <a name="return-value"></a>戻り値

印刷プレビューモードが設定されている場合は TRUE。それ以外の場合は FALSE。

##  <a name="loadstate"></a>CDockingManager:: LoadState

レジストリからドッキングマネージャーの状態を読み込みます。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
からプロファイル名。

*uiID*<br/>
からドッキングマネージャーの id。

### <a name="return-value"></a>戻り値

ドッキングマネージャーの状態が正常に読み込まれた場合は TRUE。それ以外の場合は FALSE。

##  <a name="lockupdate"></a>CDockingManager:: LockUpdate

指定されたウィンドウをロックします。

```
void LockUpdate(BOOL bLock);
```

### <a name="parameters"></a>パラメーター

*帯*<br/>
からウィンドウがロックされている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ウィンドウがロックされている場合は、移動することはできません。また、ウィンドウは再描画できません。

##  <a name="m_bhidedockingbarsincontainermode"></a>CDockingManager::m_bHideDockingBarsInContainerMode

ドッキングマネージャーが OLE コンテナーモードでペインを非表示にするかどうかを指定します。

```
AFX_IMPORT_DATA static BOOL m_bHideDockingBarsInContainerMode;
```

### <a name="remarks"></a>Remarks

アプリケーションが OLE コンテナーモードのときにメインフレームにドッキングされているすべてのペインを表示したままにする場合は、この値を FALSE に設定します。 既定では、この値は TRUE です。

##  <a name="m_dockmodeglobal"></a>CDockingManager::m_dockModeGlobal

グローバルドッキングモードを指定します。

```
AFX_IMPORT_DATA static AFX_DOCK_TYPE m_dockModeGlobal;
```

### <a name="remarks"></a>Remarks

既定では、各ドッキングウィンドウはこのドッキングモードを使用します。 このフィールドに設定できる値の詳細については、「 [Cbasepane:: Getdocによるモード](../../mfc/reference/cbasepane-class.md#getdockingmode)」を参照してください。

##  <a name="m_ndocksensitivity"></a>CDockingManager::m_nDockSensitivity

ドッキング感度を指定します。

```
AFX_IMPORT_DATA static int m_nDockSensitivity;
```

### <a name="remarks"></a>Remarks

ドッキング感度は、ドッキングペイン、ドッキングサイト、またはその他のペインに対してフローティングペインを閉じる方法を定義します。これにより、フレームワークの状態がドッキング済みに変更されます。

##  <a name="m_ntimeoutbeforedockingbardock"></a>CDockingManager::m_nTimeOutBeforeDockingBarDock

ドッキングペインが即時ドッキングモードでドッキングされるまでの時間をミリ秒単位で指定します。

```
static UINT m_nTimeOutBeforeDockingBarDock;
```

### <a name="remarks"></a>Remarks

ペインがドッキングされる前に、フレームワークは指定された期間待機します。 これにより、ユーザーがまだドラッグしているときに、ペインが誤って位置にドッキングされるのを防ぐことができます。

##  <a name="m_ntimeoutbeforetoolbardock"></a>CDockingManager::m_nTimeOutBeforeToolBarDock

ツールバーがメインフレームウィンドウにドッキングされるまでの時間をミリ秒単位で指定します。

```
static UINT m_nTimeOutBeforeToolBarDock;
```

### <a name="remarks"></a>Remarks

ツールバーがドッキングされる前に、フレームワークは指定された期間待機します。 これにより、ユーザーがまだドラッグしているときに、ツールバーが誤って位置にドッキングされるのを防ぐことができます。

##  <a name="onactivateframe"></a>CDockingManager:: On Frame

フレームウィンドウがアクティブまたは非アクティブになったときにフレームワークによって呼び出されます。

```
virtual void OnActivateFrame(BOOL bActivate);
```

### <a name="parameters"></a>パラメーター

*bActivate*<br/>
からTRUE の場合、フレームウィンドウはアクティブになります。FALSE の場合、フレームウィンドウは非アクティブになります。

##  <a name="onclosepopupmenu"></a>CDockingManager::OnClosePopupMenu

アクティブなポップアップ メニューが WM_DESTROY メッセージを処理するときに、フレームワークによって呼び出されます。

```
void OnClosePopupMenu();
```

### <a name="remarks"></a>Remarks

フレームワークは、現在のメインウィンドウを閉じようとしているときに WM_DESTROY メッセージを送信します。 オブジェクトが`CMFCPopupMenu` `CMFCPopupMenu` WM_DESTROY メッセージを処理するときに、フレームウィンドウに属するオブジェクトからの通知を処理するには、このメソッドをオーバーライドします。

##  <a name="onmoveminiframe"></a>CDockingManager::OnMoveMiniFrame

ミニフレームウィンドウを移動するためにフレームワークによって呼び出されます。

```
virtual BOOL OnMoveMiniFrame(CWnd* pFrame);
```

### <a name="parameters"></a>パラメーター

*pFrame*<br/>
からミニフレームウィンドウへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

##  <a name="onpanecontextmenu"></a>CDockingManager::OnPaneContextMenu

ペインのリストを持つメニューをビルドするときに、フレームワークによって呼び出されます。

```
void OnPaneContextMenu(CPoint point);
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
からメニューの場所を指定します。

##  <a name="panefrompoint"></a>CDockingManager::P aneFromPoint

指定されたポイントを含むペインを返します。

```
virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    bool bExactBar = false,
    CRuntimeClass* pRTCBarType = NULL,
    BOOL bCheckVisibility = FALSE,
    const CBasePane* pBarToIgnore = NULL) const;

virtual CBasePane* PaneFromPoint(
    CPoint point,
    int nSensitivity,
    DWORD& dwAlignment,
    CRuntimeClass* pRTCBarType = NULL,
    const CBasePane* pBarToIgnore = NULL) const;
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
からチェックするポイントを画面座標で指定します。

*nSensitivity*<br/>
からオンになっている各ペインのウィンドウ四角形を拡大する値。 特定のポイントがこの拡大された領域にある場合、ペインは検索条件を満たします。

*bExactBar*<br/>
から*Nsensitivity*パラメーターを無視する場合は TRUE。それ以外の場合は FALSE。

*pRTCBarType*<br/>
からNULL でない場合、メソッドは、指定された型のペインだけを検索します。

*bCheckVisibility*<br/>
から表示されているペインだけをチェックする場合は TRUE。それ以外の場合は FALSE。

*dwAlignment*<br/>
入出力指定したポイントにペインがある場合、このパラメーターには、指定したポイントに最も近いペインの辺が格納されます。 詳細については、「解説」を参照してください。

*pBarToIgnore*<br/>
からNULL でない場合、メソッドはこのパラメーターで指定されたペインを無視します。

### <a name="return-value"></a>戻り値

指定されたポイントを含む[Cbasepane](../../mfc/reference/cbasepane-class.md)派生オブジェクト。ペインが見つからなかった場合は NULL。

### <a name="remarks"></a>Remarks

関数がを返し、ペインが見つかった場合、 *dwAlignment*には、指定した点のアラインメントが含まれます。 たとえば、ポイントがペインの一番上に最も近い場合、 *dwAlignment*は CBRS_ALIGN_TOP に設定されます。

##  <a name="processpanecontextmenucommand"></a>CDockingManager::P rocessPaneContextMenuCommand

指定したコマンドのチェックボックスをオンまたはオフにし、表示されているペインのレイアウトを再計算するために、フレームワークによって呼び出されます。

```
BOOL ProcessPaneContextMenuCommand(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
からメニューのコントロールバーの id。

*nCode*<br/>
からコマンド通知コード。

*pExtra*<br/>
から`CCmdUI` *NCode*が CN_UPDATE_COMMAND_UI の場合は、へのポインターにキャストされている void へのポインター。

*pHandlerInfo*<br/>
から情報構造体へのポインター。 このパラメーターは使用されません。

### <a name="return-value"></a>戻り値

*Pextra*が NULL でなく*nCode*が CN_UPDATE_COMMAND_UI と等しい場合は TRUE、指定された*nID*を持つコントロールバーがある場合は。

##  <a name="recalclayout"></a>  CDockingManager::RecalcLayout

コントロールのリストに存在するコントロールの内部レイアウトを再計算します。

```
virtual void RecalcLayout(BOOL bNotify = TRUE);
```

### <a name="parameters"></a>パラメーター

*bNotify*<br/>
からこのパラメーターは使用されません。

##  <a name="releaseemptypanecontainers"></a>  CDockingManager::ReleaseEmptyPaneContainers

空のペインコンテナーを解放します。

```
void ReleaseEmptyPaneContainers();
```

##  <a name="removehiddenmditabbedbar"></a>  CDockingManager::RemoveHiddenMDITabbedBar

指定した非表示バーペインを削除します。

```
void RemoveHiddenMDITabbedBar(CDockablePane* pBar);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
から削除するバーペインへのポインター。

##  <a name="removeminiframe"></a>  CDockingManager::RemoveMiniFrame

指定したフレームをミニフレームの一覧から削除します。

```
virtual BOOL RemoveMiniFrame(CPaneFrameWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
から削除するフレームへのポインター。

### <a name="return-value"></a>戻り値

指定したフレームが削除された場合は TRUE。それ以外の場合は FALSE。

##  <a name="removepanefromdockmanager"></a>  CDockingManager::RemovePaneFromDockManager

ペインの登録を解除し、ドッキングマネージャーの一覧から削除します。

```
void RemovePaneFromDockManager(
    CBasePane* pWnd,
    BOOL bDestroy,
    BOOL bAdjustLayout,
    BOOL bAutoHide = FALSE,
    CBasePane* pBarReplacement = NULL);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
[in]削除するウィンドウへのポインター。

*bDestroy*<br/>
からTRUE の場合、削除されたペインは破棄されます。

*bAdjustLayout*<br/>
からTRUE の場合は、ドッキングレイアウトをすぐに調整します。

*bAutoHide に隠す*<br/>
からTRUE の場合、ウィンドウは自動的に隠すバーの一覧から削除されます。 FALSE の場合、ペインは通常のペインの一覧から削除されます。

*pBarReplacement*<br/>
から削除されたペインを置き換えるペインへのポインター。

##  <a name="replacepane"></a>CDockingManager:: ReplacePane

ペインを別のペインに置き換えます。

```
BOOL ReplacePane(
    CDockablePane* pOriginalBar,
    CDockablePane* pNewBar);
```

### <a name="parameters"></a>パラメーター

*Porbar*<br/>
から元のペインへのポインター。

*pNewBar*<br/>
から元のペインを置き換えるペインへのポインター。

### <a name="return-value"></a>戻り値

ペインが正常に置き換えられた場合は TRUE。それ以外の場合は FALSE。

##  <a name="resortminiframesforzorder"></a>  CDockingManager::ResortMiniFramesForZOrder

ミニフレームの一覧のフレームを並べ替えます。

```
void ResortMiniFramesForZOrder();
```

##  <a name="savestate"></a>CDockingManager:: SaveState

ドッキングマネージャーの状態をレジストリに保存します。

```
virtual BOOL SaveState(
    LPCTSTR lpszProfileName = NULL,
    UINT uiID = (UINT) -1);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
からレジストリキーへのパス。

*uiID*<br/>
からドッキングマネージャー ID。

### <a name="return-value"></a>戻り値

状態が正常に保存された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ドッキングマネージャーの状態をレジストリに保存するには、コントロールバーの状態、自動的に隠すバーの状態、およびドッキングマネージャーに存在するミニフレームの状態を保存する必要があります。

##  <a name="sendmessagetominiframes"></a>CDockingManager:: SendMessageToMiniFrames

指定されたメッセージをすべてのミニフレームに送信します。

```
BOOL SendMessageToMiniFrames(
    UINT uMessage,
    WPARAM wParam = 0,
    LPARAM lParam = 0);
```

### <a name="parameters"></a>パラメーター

*uMessage*<br/>
から送信されるメッセージ。

*wParam*<br/>
から追加のメッセージ依存情報。

*lParam*<br/>
から追加のメッセージ依存情報。

### <a name="return-value"></a>戻り値

常に TRUE です。

##  <a name="serialize"></a>CDockingManager:: Serialize

ドッキングマネージャーをアーカイブに書き込みます。

```
void Serialize(CArchive& ar);
```

### <a name="parameters"></a>パラメーター

*金*<br/>
からArchive オブジェクトへの参照です。

### <a name="remarks"></a>Remarks

ドッキングマネージャーをアーカイブに書き込むには、ドッキングコントロールバーとスライダーの数を決定し、コントロールバー、ミニフレーム、自動非表示バー、および MDI タブ付きバーをアーカイブに書き込みます。

##  <a name="setautohidezorder"></a>CDockingManager:: SetAutohideZOrder

コントロールバーと指定したペインのサイズ、幅、および高さを設定します。

```
void SetAutohideZOrder(CDockablePane* pAHDockingBar);
```

### <a name="parameters"></a>パラメーター

*pAHDockingBar*<br/>
からドッキング可能なペインへのポインター。

##  <a name="setdockingmode"></a>CDockingManager:: Setdoc モード

ドッキングモードを設定します。

```
static void SetDockingMode(
    AFX_DOCK_TYPE dockMode,
    AFX_SMARTDOCK_THEME theme = AFX_SDT_DEFAULT);
```

### <a name="parameters"></a>パラメーター

*dockMode*<br/>
新しいドッキングモードを指定します。 詳細については、「解説」を参照してください。

*デザイン*<br/>
スマートドッキングマーカーに使用するテーマを指定します。 次の列挙値のいずれかを指定できます。AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.

### <a name="remarks"></a>Remarks

ドッキングモードを設定するには、この静的メソッドを呼び出します。

*dockMode*には、次のいずれかの値を指定できます。

- DT_STANDARD-Visual Studio .NET 2003 で実装されている標準のドッキングモード。 ペインはドラッグコンテキストなしでドラッグされます。

- DT_IMMEDIATE-Microsoft Visio に実装されている即時ドッキングモード。 ペインはドラッグコンテキストでドラッグされますが、マーカーは表示されません。

- DT_SMART-Visual Studio 2005 で実装されているスマートドッキングモード。 ペインはドラッグコンテキストでドラッグされ、ウィンドウをドッキングできる場所を示すスマートマーカーが表示されます。

##  <a name="setdockstate"></a>CDockingManager::SetDockState

コントロールバー、ミニフレーム、および自動的に隠すバーのドッキング状態を設定します。

```
virtual void SetDockState();
```

##  <a name="setprintpreviewmode"></a>CDockingManager:: Setprintプレビューモード

印刷プレビューに表示されるバーの印刷プレビューモードを設定します。

```
void SetPrintPreviewMode(
    BOOL bPreview,
    CPrintPreviewState* pState);
```

### <a name="parameters"></a>パラメーター

*bPreview*<br/>
から印刷プレビューモードが設定されている場合は TRUE です。それ以外の場合は FALSE。

*pState*<br/>
からプレビュー状態へのポインター。 このパラメーターは使用されません。

##  <a name="setsmartdockingparams"></a>CDockingManager:: Setsmartdocのパラメーター

スマートドッキングの動作を定義するパラメーターを設定します。

```
static void SetSmartDockingParams(CSmartDockingInfo& params);
```

### <a name="parameters"></a>パラメーター

*params*<br/>
[入力、出力]スマートドッキングのパラメーターを定義します。

### <a name="remarks"></a>Remarks

スマートドッキングマーカーの外観、色、または形状をカスタマイズする場合は、このメソッドを呼び出します。

スマートドッキングマーカーの既定の検索を使用するには、初期化されていない[Csmartdocの [情報] クラス](../../mfc/reference/csmartdockinginfo-class.md)のインスタンスを*params*に渡します。

##  <a name="showdelayshowminiframes"></a>CDockingManager:: ShowDelayShowMiniFrames

ミニフレームのウィンドウの表示と非表示を切り替えます。

```
void ShowDelayShowMiniFrames(BOOL bshow);
```

### <a name="parameters"></a>パラメーター

*bShow*<br/>
から表示されているフレームのウィンドウをアクティブにする場合は TRUE。フレームのウィンドウを非表示にする場合は FALSE。

##  <a name="showpanes"></a>CDockingManager:: ShowPanes

コントロールのペインおよび自動非表示バーの表示と非表示を切り替えます。

```
virtual BOOL ShowPanes(BOOL bShow);
```

### <a name="parameters"></a>パラメーター

*bShow*<br/>
からペインを表示する場合は TRUE。ペインを非表示にする場合は FALSE。

### <a name="return-value"></a>戻り値

常に FALSE です。

##  <a name="startsdocking"></a>CDockingManager:: StartSDocking

スマートドッキングマネージャーの配置に従って、指定したウィンドウのスマートドッキングを開始します。

```
void StartSDocking(CWnd* pDockingWnd);
```

### <a name="parameters"></a>パラメーター

*pDockingWnd*<br/>
からドッキングするウィンドウへのポインター。

##  <a name="stopsdocking"></a>CDockingManager:: StopSDocking

スマートドッキングを停止します。

```
void StopSDocking();
```

##  <a name="getsmartdockingtheme"></a>CDockingManager:: Getsmartdocのテーマ

スマートドッキングマーカーの表示に使用するテーマを返す静的メソッド。

```
static AFX_SMARTDOCK_THEME __stdcall GetSmartDockingTheme();
```

### <a name="return-value"></a>戻り値

次の列挙値のいずれかを返します。AFX_SDT_DEFAULT, AFX_SDT_VS2005, AFX_SDT_VS2008.

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[CFrameWndEx クラス](../../mfc/reference/cframewndex-class.md)<br/>
[CDockablePane クラス](../../mfc/reference/cdockablepane-class.md)<br/>
[CPaneFrameWnd クラス](../../mfc/reference/cpaneframewnd-class.md)
