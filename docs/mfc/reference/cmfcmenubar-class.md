---
title: CMFCMenuBar クラス
ms.date: 10/18/2018
f1_keywords:
- CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar
- AFXMENUBAR/CMFCMenuBar::AdjustLocations
- AFXMENUBAR/CMFCMenuBar::AllowChangeTextLabels
- AFXMENUBAR/CMFCMenuBar::AllowShowOnPaneMenu
- AFXMENUBAR/CMFCMenuBar::CalcFixedLayout
- AFXMENUBAR/CMFCMenuBar::CalcLayout
- AFXMENUBAR/CMFCMenuBar::CalcMaxButtonHeight
- AFXMENUBAR/CMFCMenuBar::CanBeClosed
- AFXMENUBAR/CMFCMenuBar::CanBeRestored
- AFXMENUBAR/CMFCMenuBar::Create
- AFXMENUBAR/CMFCMenuBar::CreateEx
- AFXMENUBAR/CMFCMenuBar::CreateFromMenu
- AFXMENUBAR/CMFCMenuBar::EnableHelpCombobox
- AFXMENUBAR/CMFCMenuBar::EnableMenuShadows
- AFXMENUBAR/CMFCMenuBar::GetAvailableExpandSize
- AFXMENUBAR/CMFCMenuBar::GetColumnWidth
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenu
- AFXMENUBAR/CMFCMenuBar::GetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::GetFloatPopupDirection
- AFXMENUBAR/CMFCMenuBar::GetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::GetHelpCombobox
- AFXMENUBAR/CMFCMenuBar::GetHMenu
- AFXMENUBAR/CMFCMenuBar::GetMenuFont
- AFXMENUBAR/CMFCMenuBar::GetMenuItem
- AFXMENUBAR/CMFCMenuBar::GetRowHeight
- AFXMENUBAR/CMFCMenuBar::GetSystemButton
- AFXMENUBAR/CMFCMenuBar::GetSystemButtonsCount
- AFXMENUBAR/CMFCMenuBar::GetSystemMenu
- AFXMENUBAR/CMFCMenuBar::HighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsButtonExtraSizeAvailable
- AFXMENUBAR/CMFCMenuBar::IsHighlightDisabledItems
- AFXMENUBAR/CMFCMenuBar::IsMenuShadows
- AFXMENUBAR/CMFCMenuBar::IsRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommands
- AFXMENUBAR/CMFCMenuBar::IsShowAllCommandsDelay
- AFXMENUBAR/CMFCMenuBar::LoadState
- AFXMENUBAR/CMFCMenuBar::OnChangeHot
- AFXMENUBAR/CMFCMenuBar::OnDefaultMenuLoaded
- AFXMENUBAR/CMFCMenuBar::OnSendCommand
- AFXMENUBAR/CMFCMenuBar::OnSetDefaultButtonText
- AFXMENUBAR/CMFCMenuBar::OnToolHitTest
- AFXMENUBAR/CMFCMenuBar::PreTranslateMessage
- AFXMENUBAR/CMFCMenuBar::RestoreOriginalstate
- AFXMENUBAR/CMFCMenuBar::SaveState
- AFXMENUBAR/CMFCMenuBar::SetDefaultMenuResId
- AFXMENUBAR/CMFCMenuBar::SetForceDownArrows
- AFXMENUBAR/CMFCMenuBar::SetMaximizeMode
- AFXMENUBAR/CMFCMenuBar::SetMenuButtonRTC
- AFXMENUBAR/CMFCMenuBar::SetMenuFont
- AFXMENUBAR/CMFCMenuBar::SetRecentlyUsedMenus
- AFXMENUBAR/CMFCMenuBar::SetShowAllCommands
helpviewer_keywords:
- CMFCMenuBar [MFC], AdjustLocations
- CMFCMenuBar [MFC], AllowChangeTextLabels
- CMFCMenuBar [MFC], AllowShowOnPaneMenu
- CMFCMenuBar [MFC], CalcFixedLayout
- CMFCMenuBar [MFC], CalcLayout
- CMFCMenuBar [MFC], CalcMaxButtonHeight
- CMFCMenuBar [MFC], CanBeClosed
- CMFCMenuBar [MFC], CanBeRestored
- CMFCMenuBar [MFC], Create
- CMFCMenuBar [MFC], CreateEx
- CMFCMenuBar [MFC], CreateFromMenu
- CMFCMenuBar [MFC], EnableHelpCombobox
- CMFCMenuBar [MFC], EnableMenuShadows
- CMFCMenuBar [MFC], GetAvailableExpandSize
- CMFCMenuBar [MFC], GetColumnWidth
- CMFCMenuBar [MFC], GetDefaultMenu
- CMFCMenuBar [MFC], GetDefaultMenuResId
- CMFCMenuBar [MFC], GetFloatPopupDirection
- CMFCMenuBar [MFC], GetForceDownArrows
- CMFCMenuBar [MFC], GetHelpCombobox
- CMFCMenuBar [MFC], GetHMenu
- CMFCMenuBar [MFC], GetMenuFont
- CMFCMenuBar [MFC], GetMenuItem
- CMFCMenuBar [MFC], GetRowHeight
- CMFCMenuBar [MFC], GetSystemButton
- CMFCMenuBar [MFC], GetSystemButtonsCount
- CMFCMenuBar [MFC], GetSystemMenu
- CMFCMenuBar [MFC], HighlightDisabledItems
- CMFCMenuBar [MFC], IsButtonExtraSizeAvailable
- CMFCMenuBar [MFC], IsHighlightDisabledItems
- CMFCMenuBar [MFC], IsMenuShadows
- CMFCMenuBar [MFC], IsRecentlyUsedMenus
- CMFCMenuBar [MFC], IsShowAllCommands
- CMFCMenuBar [MFC], IsShowAllCommandsDelay
- CMFCMenuBar [MFC], LoadState
- CMFCMenuBar [MFC], OnChangeHot
- CMFCMenuBar [MFC], OnDefaultMenuLoaded
- CMFCMenuBar [MFC], OnSendCommand
- CMFCMenuBar [MFC], OnSetDefaultButtonText
- CMFCMenuBar [MFC], OnToolHitTest
- CMFCMenuBar [MFC], PreTranslateMessage
- CMFCMenuBar [MFC], RestoreOriginalstate
- CMFCMenuBar [MFC], SaveState
- CMFCMenuBar [MFC], SetDefaultMenuResId
- CMFCMenuBar [MFC], SetForceDownArrows
- CMFCMenuBar [MFC], SetMaximizeMode
- CMFCMenuBar [MFC], SetMenuButtonRTC
- CMFCMenuBar [MFC], SetMenuFont
- CMFCMenuBar [MFC], SetRecentlyUsedMenus
- CMFCMenuBar [MFC], SetShowAllCommands
ms.assetid: 8a3ce4c7-b012-4dc0-b4f8-53c10b4b86b8
ms.openlocfilehash: 278feca6b64915d0cf789e8f68af3c3fdf9b3129
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78869939"
---
# <a name="cmfcmenubar-class"></a>CMFCMenuBar クラス

ドッキングを実装するメニュー バーです。
詳細については、Visual Studio インストールの**VC\\atlmfc\\src\\mfc**フォルダーにあるソースコードを参照してください。

## <a name="syntax"></a>構文

```
class CMFCMenuBar : public CMFCToolbar
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|Description|
|----------|-----------------|
|[CMFCMenuBar:: AdjustLocations](#adjustlocations)|(`CMFCToolBar::AdjustLocations` をオーバーライドします。)|
|[CMFCMenuBar:: AllowChangeTextLabels](#allowchangetextlabels)|ツールバーのボタンの [画像] の下にテキストラベルを表示するかどうかを指定します。 ( [Cmfctoolbar:: AllowChangeTextLabels](../../mfc/reference/cmfctoolbar-class.md#allowchangetextlabels)をオーバーライドします)。|
|[CMFCMenuBar:: AllowShowOnPaneMenu](#allowshowonpanemenu)|(`CPane::AllowShowOnPaneMenu` をオーバーライドします。)|
|[CMFCMenuBar:: CalcFixedLayout](#calcfixedlayout)|ツールバーの水平方向のサイズを計算します。 ( [Cmfctoolbar:: CalcFixedLayout](../../mfc/reference/cmfctoolbar-class.md#calcfixedlayout)をオーバーライドします)。|
|[CMFCMenuBar:: CalcLayout](#calclayout)|(`CMFCToolBar::CalcLayout` をオーバーライドします。)|
|[CMFCMenuBar:: CalcMaxButtonHeight](#calcmaxbuttonheight)|ツールバーのボタンの高さの最大値を計算します。 ( [Cmfctoolbar:: CalcMaxButtonHeight](../../mfc/reference/cmfctoolbar-class.md#calcmaxbuttonheight)をオーバーライドします)。|
|[CMFCMenuBar:: Can"Losed"](#canbeclosed)|ユーザーがツールバーを閉じることができるかどうかを指定します。 ( [Cmfctoolbar:: canを](../../mfc/reference/cmfctoolbar-class.md#canbeclosed)オーバーライドします)。|
|[CMFCMenuBar:: CanBeRestored](#canberestored)|カスタマイズ後にツールバーを元の状態に戻すことができるかどうかを決定します。 ( [Cmfctoolbar:: CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)をオーバーライドします)。|
|[CMFCMenuBar:: Create](#create)|メニューコントロールを作成し、`CMFCMenuBar` オブジェクトにアタッチします。|
|[CMFCMenuBar:: CreateEx](#createex)|追加のスタイルオプションを使用して `CMFCMenuBar` オブジェクトを作成します。|
|[CMFCMenuBar:: CreateFromMenu](#createfrommenu)|`CMFCMenuBar` オブジェクトを初期化します。 設定された `CMFCMenuBar`のテンプレートとして機能する HMENU パラメーターを受け入れます。|
|[CMFCMenuBar:: EnableHelpCombobox](#enablehelpcombobox)|メニューバーの右側にある**ヘルプ**コンボボックスを有効にします。|
|[CMFCMenuBar:: EnableMenuShadows](#enablemenushadows)|ポップアップメニューに影を表示するかどうかを指定します。|
|[CMFCMenuBar:: Get持つ Expandsize](#getavailableexpandsize)|( [CPane:: Get Expandsize](../../mfc/reference/cpane-class.md#getavailableexpandsize)をオーバーライドします)。|
|[CMFCMenuBar:: GetColumnWidth](#getcolumnwidth)|ツールバーボタンの幅を返します。 ( [Cmfctoolbar:: GetColumnWidth](../../mfc/reference/cmfctoolbar-class.md#getcolumnwidth)をオーバーライドします)。|
|[CMFCMenuBar:: GetDefaultMenu](#getdefaultmenu)|リソースファイル内の元のメニューへのハンドルを返します。|
|[CMFCMenuBar:: GetDefaultMenuResId](#getdefaultmenuresid)|リソースファイル内の元のメニューのリソース識別子を返します。|
|[CMFCMenuBar:: GetFloatPopupDirection](#getfloatpopupdirection)||
|[CMFCMenuBar:: GetForceDownArrows](#getforcedownarrows)||
|[CMFCMenuBar:: Ge後者 Pcombobox](#gethelpcombobox)|**ヘルプ**コンボボックスへのポインターを返します。|
|[CMFCMenuBar:: GetHMenu](#gethmenu)|`CMFCMenuBar` オブジェクトにアタッチされているメニューへのハンドルを返します。|
|[CMFCMenuBar:: GetMenuFont](#getmenufont)|メニューオブジェクトの現在のグローバルフォントを返します。|
|[CMFCMenuBar:: GetMenuItem](#getmenuitem)|指定された項目インデックスに関連付けられているツールバーボタンを返します。|
|[CMFCMenuBar:: GetRowHeight](#getrowheight)|ツールバーボタンの高さを返します。 ( [Cmfctoolbar:: GetRowHeight](../../mfc/reference/cmfctoolbar-class.md#getrowheight)をオーバーライドします)。|
|[CMFCMenuBar:: GetSystemButton](#getsystembutton)||
|[CMFCMenuBar:: GetSystemButtonsCount](#getsystembuttonscount)||
|[CMFCMenuBar:: GetSystemMenu](#getsystemmenu)||
|[CMFCMenuBar:: HighlightDisabledItems](#highlightdisableditems)|無効になっているメニュー項目を強調表示するかどうかを示します。|
|[CMFCMenuBar:: IsButtonExtraSizeAvailable](#isbuttonextrasizeavailable)|拡張された境界線を持つボタンをツールバーに表示できるかどうかを決定します。 ( [Cmfctoolbar:: IsButtonExtraSizeAvailable](../../mfc/reference/cmfctoolbar-class.md#isbuttonextrasizeavailable)をオーバーライドします)。|
|[CMFCMenuBar:: IsHighlightDisabledItems](#ishighlightdisableditems)|無効になっている項目を強調表示するかどうかを示します。|
|[CMFCMenuBar:: IsMenuShadows](#ismenushadows)|ポップアップメニューに影を描画するかどうかを示します。|
|[CMFCMenuBar:: IsRecentlyUsedMenus](#isrecentlyusedmenus)|最近使用したメニューコマンドがメニューバーに表示されるかどうかを示します。|
|[CMFCMenuBar:: IsShowAllCommands](#isshowallcommands)|ポップアップメニューですべてのコマンドを表示するかどうかを示します。|
|[CMFCMenuBar:: IsShowAllCommandsDelay](#isshowallcommandsdelay)|メニューが短い遅延の後にすべてのコマンドを表示するかどうかを示します。|
|[CMFCMenuBar:: LoadState](#loadstate)|レジストリから `CMFCMenuBar` オブジェクトの状態を読み込みます。|
|[CMFCMenuBar:: OnChangeHot](#onchangehot)|ユーザーがツールバーのボタンを選択すると、フレームワークによって呼び出されます。 ( [Cmfctoolbar:: OnChangeHot](../../mfc/reference/cmfctoolbar-class.md#onchangehot)をオーバーライドします)。|
|[CMFCMenuBar:: OnDefaultMenuLoaded](#ondefaultmenuloaded)|フレームウィンドウがリソースファイルから既定のメニューを読み込むときに、フレームワークによって呼び出されます。|
|[CMFCMenuBar:: OnSendCommand](#onsendcommand)|(`CMFCToolBar::OnSendCommand` をオーバーライドします。)|
|[CMFCMenuBar:: OnSetDefaultButtonText](#onsetdefaultbuttontext)|メニューがカスタマイズモードのときに、ユーザーがメニュー項目のテキストを変更すると、フレームワークによって呼び出されます。|
|[CMFCMenuBar:: OnToolHitTest](#ontoolhittest)|(`CMFCToolBar::OnToolHitTest` をオーバーライドします。)|
|[CMFCMenuBar::P reTranslateMessage](#pretranslatemessage)|(`CMFCToolBar::PreTranslateMessage` をオーバーライドします。)|
|[CMFCMenuBar:: RestoreOriginalstate](#restoreoriginalstate)|メニューがカスタマイズモードのときに、ユーザーがメニューバーの **[リセット]** を選択すると、フレームワークによって呼び出されます。|
|[CMFCMenuBar:: SaveState](#savestate)|`CMFCMenuBar` オブジェクトの状態をレジストリに保存します。|
|[CMFCMenuBar:: SetDefaultMenuResId](#setdefaultmenuresid)|リソースファイル内の元のメニューを設定します。|
|[CMFCMenuBar:: SetForceDownArrows](#setforcedownarrows)||
|[CMFCMenuBar:: Set最大化 Izemode](#setmaximizemode)|MDI 子ウィンドウが表示モードを変更したときにフレームワークによって呼び出されます。 MDI 子ウィンドウが新たに最大化された場合、または最大化されていない場合は、このメソッドによってメニューバーが更新されます。|
|[CMFCMenuBar:: SetMenuButtonRTC](#setmenubuttonrtc)|ユーザーがメニューボタンを動的に作成するときに生成されるランタイムクラスの情報を設定します。|
|[CMFCMenuBar:: SetMenuFont](#setmenufont)|アプリケーションのすべてのメニューのフォントを設定します。|
|[CMFCMenuBar:: SetRecentlyUsedMenus](#setrecentlyusedmenus)|メニューバーに最近使用したメニューコマンドを表示するかどうかを指定します。|
|[CMFCMenuBar:: SetShowAllCommands](#setshowallcommands)|メニューバーにすべてのコマンドを表示するかどうかを指定します。|

## <a name="remarks"></a>解説

`CMFCMenuBar` クラスは、ドッキング機能を実装するメニューバーです。 ツールバーに似ていますが、閉じることはできません。常に表示されます。

`CMFCMenuBar` では、最近使用したメニュー項目オブジェクトを表示するオプションがサポートされています。 このオプションが有効になっている場合、`CMFCMenuBar` には、最初の表示時に使用可能なコマンドのサブセットのみが表示されます。 その後、最近使用したコマンドは、元のコマンドのサブセットと共に表示されます。 さらに、ユーザーはいつでもメニューを展開して、使用可能なすべてのコマンドを表示できます。 このため、使用可能な各コマンドは、常に表示されるように構成されているか、最近選択された場合にのみ表示されます。

`CMFCMenuBar` オブジェクトを使用するには、メインウィンドウフレームオブジェクトに埋め込みます。 `WM_CREATE` メッセージを処理する場合は、`CMFCMenuBar::Create` または `CMFCMenuBar::CreateEx`を呼び出します。 使用する create 関数に関係なく、メインフレームウィンドウへのポインターを渡します。 次に、 [CFrameWndEx:: EnableDocking](../../mfc/reference/cframewndex-class.md#enabledocking)を呼び出して、ドッキングを有効にします。 [CFrameWndEx::D ockPane](../../mfc/reference/cframewndex-class.md#dockpane)を呼び出して、このメニューをドッキングします。

## <a name="example"></a>例

`CMFCMenuBar` クラスのさまざまなメソッドの使用方法を次の例に示します。 この例では、ペインのスタイルを設定する方法、[カスタマイズ] ボタンを有効にする方法、ヘルプボックスを有効にする方法、ポップアップメニューの影を有効にする方法、およびメニューバーを更新する方法を示します。 このコードスニペットは、 [IE デモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#3](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[から派生しているのではない](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

`CMFCMenuBar`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxmenubar

##  <a name="adjustlocations"></a>CMFCMenuBar:: AdjustLocations

メニューバー上のメニュー項目の位置を調整します。

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>解説

##  <a name="allowchangetextlabels"></a>CMFCMenuBar:: AllowChangeTextLabels

メニューバーの [画像] でテキストラベルを使用できるかどうかを決定します。

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>戻り値

ユーザーが画像の下にテキストラベルを表示することを選択できる場合に TRUE を返します。

### <a name="remarks"></a>解説

##  <a name="allowshowonpanemenu"></a>CMFCMenuBar:: AllowShowOnPaneMenu

```
virtual BOOL AllowShowOnPaneMenu() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="calcfixedlayout"></a>CMFCMenuBar:: CalcFixedLayout

```
virtual CSize CalcFixedLayout(
    BOOL bStretch,
    BOOL bHorz);
```

### <a name="parameters"></a>パラメーター

から*Bstretch*<br/>

から*bHorz*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="calclayout"></a>CMFCMenuBar:: CalcLayout

```
virtual CSize CalcLayout(
    DWORD dwMode,
    int nLength = -1);
```

### <a name="parameters"></a>パラメーター

から*Dwmode*<br/>

から*Nlength*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="calcmaxbuttonheight"></a>CMFCMenuBar:: CalcMaxButtonHeight

```
virtual int CalcMaxButtonHeight();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="canbeclosed"></a>CMFCMenuBar:: Can"Losed"

```
virtual BOOL CanBeClosed() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="canberestored"></a>CMFCMenuBar:: CanBeRestored

```
virtual BOOL CanBeRestored() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="create"></a>CMFCMenuBar:: Create

メニューコントロールを作成し、 [Cmfcmenubar](../../mfc/reference/cmfcmenubar-class.md)オブジェクトにアタッチします。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    UINT nID = AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
から新しい `CMFCMenuBar` オブジェクトの親ウィンドウへのポインター。

*dwStyle*<br/>
から新しいメニューバーのスタイル。

*nID*<br/>
からメニューバーの子ウィンドウの ID。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>解説

`CMFCMenuBar` オブジェクトを構築した後、`Create`を呼び出す必要があります。 このメソッドは、`CMFCMenuBar` コントロールを作成し、`CMFCMenuBar` オブジェクトにアタッチします。

ツールバーのスタイルの詳細については、「 [Cbasepane:: Setpane style](../../mfc/reference/cbasepane-class.md#setpanestyle)」を参照してください。

##  <a name="createex"></a>CMFCMenuBar:: CreateEx

指定された拡張スタイルを使用して[Cmfcmenubar](../../mfc/reference/cmfcmenubar-class.md)オブジェクトを作成します。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle = TBSTYLE_FLAT,
    DWORD dwStyle = AFX_DEFAULT_TOOLBAR_STYLE,
    CRect rcBorders = CRect(1,
    1,
    1,
    1),
    UINT nID =AFX_IDW_MENUBAR);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
から新しい `CMFCMenuBar` オブジェクトの親ウィンドウへのポインター。

*dwCtrlStyle*<br/>
から新しいメニューバーの追加のスタイル。

*dwStyle*<br/>
から新しいメニューバーのメインスタイル。

*rcBorders*<br/>
から`CMFCMenuBar` オブジェクトの境界線のサイズを指定する `CRect` パラメーター。

*nID*<br/>
からメニューバーの子ウィンドウの ID。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

ツールバースタイルに加えてスタイルを指定する場合は、 [Cmfcmenubar:: Create](#create)ではなく、この関数を使用する必要があります。 頻繁に使用される追加のスタイルには、TBSTYLE_TRANSPARENT と CBRS_TOP があります。

追加のスタイルの一覧については、「[ツールバーコントロールとボタンスタイル](/windows/win32/Controls/toolbar-control-and-button-styles)」、「[コモンコントロールスタイル](/windows/win32/Controls/common-control-styles)」、および「[一般的なウィンドウスタイル](/windows/win32/winmsg/window-styles)」を参照してください。

### <a name="example"></a>例

次の例は、`CMFCMenuBar` クラスの `CreateEx` メソッドを使用する方法を示しています。 このコードスニペットは、 [IE デモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_IEDemo#1](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_1.h)]
[!code-cpp[NVC_MFC_IEDemo#2](../../mfc/reference/codesnippet/cpp/cmfcmenubar-class_3.cpp)]

##  <a name="createfrommenu"></a>CMFCMenuBar:: CreateFromMenu

[Cmfcmenubar](../../mfc/reference/cmfcmenubar-class.md)オブジェクトを初期化します。 このメソッドは、HMENU パラメーターの後に `CMFCMenuBar` オブジェクトをモデル化します。

```
virtual void CreateFromMenu(
    HMENU hMenu,
    BOOL bDefaultMenu = FALSE,
    BOOL bForceUpdate = FALSE);
```

### <a name="parameters"></a>パラメーター

*hMenu*<br/>
からメニューリソースを処理するハンドル。 `CreateFromMenu` は、このリソースを `CMFCMenuBar`のテンプレートとして使用します。

*bDefaultMenu*<br/>
から新しいメニューが既定のメニューであるかどうかを示すブール値。

*bForceUpdate*<br/>
からこのメソッドがメニュー更新を強制的に実行するかどうかを示すブール値。

### <a name="remarks"></a>解説

メニューコントロールがメニューリソースと同じメニュー項目を持つようにする場合は、このメソッドを使用します。 このメソッドは、 [Cmfcmenubar:: Create](#create)または[Cmfcmenubar:: CreateEx](#createex)を呼び出した後に呼び出します。

##  <a name="enablehelpcombobox"></a>CMFCMenuBar:: EnableHelpCombobox

メニューバーの右側にある**ヘルプ**コンボボックスを有効にします。

```
void EnableHelpCombobox(
    UINT uiID,
    LPCTSTR lpszPrompt = NULL,
    int nComboBoxWidth = 150);
```

### <a name="parameters"></a>パラメーター

*uiID*<br/>
から **[ヘルプ]** コンボボックスのボタンのコマンド ID です。

*lpszPrompt*<br/>
からコンボボックスが空で、アクティブでない場合にフレームワークによって表示されるテキストを含む文字列。 たとえば、"ここにテキストを入力してください" と表示されます。

*nComboBoxWidth*<br/>
からコンボボックスのボタンの幅 (ピクセル単位)。

### <a name="remarks"></a>解説

**[ヘルプ]** コンボボックスは、Microsoft Word のメニューバーの **[ヘルプ]** コンボボックスに似ています。

*UiID*を0に設定してこのメソッドを呼び出すと、このメソッドはコンボボックスを非表示にします。 それ以外の場合、このメソッドは、コンボボックスをメニューバーの右側に自動的に表示します。 このメソッドを呼び出した後、 [Cmfcmenubar:: Geb Pcombobox](#gethelpcombobox)を呼び出して、挿入された[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)オブジェクトへのポインターを取得します。

##  <a name="enablemenushadows"></a>CMFCMenuBar:: EnableMenuShadows

ポップアップメニューの影を有効にします。

```
static void EnableMenuShadows(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
からポップアップメニューの影を有効にする必要があるかどうかを示すブール値パラメーター。

### <a name="remarks"></a>解説

この方法で使用されるアルゴリズムは複雑であり、低速なシステムではアプリケーションのパフォーマンスが低下する可能性があります。

##  <a name="getavailableexpandsize"></a>CMFCMenuBar:: Get持つ Expandsize

```
virtual int GetAvailableExpandSize() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="getcolumnwidth"></a>CMFCMenuBar:: GetColumnWidth

```
virtual int GetColumnWidth() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="getdefaultmenu"></a>CMFCMenuBar:: GetDefaultMenu

元のメニューへのハンドルを取得します。 フレームワークは、リソースファイルから元のメニューを読み込みます。

```
HMENU GetDefaultMenu() const;
```

### <a name="return-value"></a>戻り値

メニューリソースを処理するハンドル。

### <a name="remarks"></a>解説

アプリケーションでメニューをカスタマイズした場合は、このメソッドを使用して元のメニューへのハンドルを取得できます。

##  <a name="getdefaultmenuresid"></a>CMFCMenuBar:: GetDefaultMenuResId

既定のメニューのリソース識別子を取得します。

```
UINT GetDefaultMenuResId() const;
```

### <a name="return-value"></a>戻り値

メニューリソース識別子。

### <a name="remarks"></a>解説

フレームワークは、リソースファイルから `CMFCMenuBar` オブジェクトの既定のメニューを読み込みます。

##  <a name="getfloatpopupdirection"></a>CMFCMenuBar:: GetFloatPopupDirection

```
int GetFloatPopupDirection(CMFCToolBarMenuButton* pButton);
```

### <a name="parameters"></a>パラメーター

から*Pbutton*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="getforcedownarrows"></a>CMFCMenuBar:: GetForceDownArrows

```
BOOL GetForceDownArrows();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="gethelpcombobox"></a>CMFCMenuBar:: Ge後者 Pcombobox

**ヘルプ**コンボボックスへのポインターを返します。

```
CMFCToolBarComboBoxButton* GetHelpCombobox();
```

### <a name="return-value"></a>戻り値

**ヘルプ**コンボボックスへのポインター。 **[ヘルプ]** コンボボックスが非表示または無効になっている場合は NULL です。

### <a name="remarks"></a>解説

**ヘルプ**コンボボックスは、メニューバーの右側にあります。 このコンボボックスを有効にするには、メソッド[Cmfcmenubar:: EnableHelpCombobox](#enablehelpcombobox)を呼び出します。

##  <a name="gethmenu"></a>CMFCMenuBar:: GetHMenu

[Cmfcmenubar](../../mfc/reference/cmfcmenubar-class.md)オブジェクトにアタッチされたメニューへのハンドルを取得します。

```
HMENU GetHMenu() const;
```

##  <a name="getmenufont"></a>CMFCMenuBar:: GetMenuFont

現在のメニューフォントを取得します。

```
static const CFont& GetMenuFont(BOOL bHorz = TRUE);
```

### <a name="parameters"></a>パラメーター

*bHorz*<br/>
から水平または垂直のフォントを返すかどうかを指定するブール型パラメーター。 TRUE は、横方向のフォントを示します。

### <a name="return-value"></a>戻り値

現在のメニューバーのフォントを格納している[CFont](../../mfc/reference/cfont-class.md)パラメーターへのポインター。

### <a name="remarks"></a>解説

返されるフォントは、アプリケーションのグローバルパラメーターです。 すべての `CMFCMenuBar` オブジェクトに対して、2つのグローバルフォントが保持されます。 これらの個別のフォントは、水平および垂直のメニューバーに使用されます。

##  <a name="getmenuitem"></a>CMFCMenuBar:: GetMenuItem

項目のインデックスに基づいて、メニューバーの[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)オブジェクトを取得します。

```
CMFCToolBarButton* GetMenuItem(int iItem) const;
```

### <a name="parameters"></a>パラメーター

*iItem*<br/>
から返されるメニュー項目のインデックス。

### <a name="return-value"></a>戻り値

*IItem*によって指定されたインデックスに一致する `CMFCToolBarButton` オブジェクトへのポインター。 インデックスが無効な場合は NULL になります。

##  <a name="getrowheight"></a>CMFCMenuBar:: GetRowHeight

```
virtual int GetRowHeight() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="getsystembutton"></a>CMFCMenuBar:: GetSystemButton

```
CMFCToolBarMenuButtonsButton* GetSystemButton(
    UINT uiBtn,
    BOOL bByCommand = TRUE) const;
```

### <a name="parameters"></a>パラメーター

から*uiBtn*<br/>

から*Bbycommand*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="getsystembuttonscount"></a>CMFCMenuBar:: GetSystemButtonsCount

```
int GetSystemButtonsCount() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="getsystemmenu"></a>CMFCMenuBar:: GetSystemMenu

```
CMFCToolBarSystemMenuButton* GetSystemMenu() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="highlightdisableditems"></a>CMFCMenuBar:: HighlightDisabledItems

フレームワークが無効化されたメニュー項目を強調表示するかどうかを制御します。

```
static void HighlightDisabledItems(BOOL bHighlight = TRUE);
```

### <a name="parameters"></a>パラメーター

*bHighlight 表示*<br/>
からフレームワークが使用できないメニュー項目を強調表示するかどうかを示すブール型パラメーターです。

### <a name="remarks"></a>解説

既定では、ユーザーがマウスポインターを上に置いたときに、使用できないメニュー項目は強調表示されません。

##  <a name="isbuttonextrasizeavailable"></a>CMFCMenuBar:: IsButtonExtraSizeAvailable

```
virtual BOOL IsButtonExtraSizeAvailable() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="ishighlightdisableditems"></a>CMFCMenuBar:: IsHighlightDisabledItems

フレームワークが使用できないメニュー項目を強調表示するかどうかを示します。

```
static BOOL IsHighlightDisabledItems();
```

### <a name="return-value"></a>戻り値

利用できないメニュー項目が強調表示されている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

既定では、ユーザーがマウスポインターを上に置いたときに、使用できないメニュー項目は強調表示されません。 この機能を有効にするには、 [Cmfcmenubar:: HighlightDisabledItems](#highlightdisableditems)メソッドを使用します。

##  <a name="ismenushadows"></a>CMFCMenuBar:: IsMenuShadows

フレームワークがポップアップメニューに影を描画するかどうかを示します。

```
static BOOL IsMenuShadows();
```

### <a name="return-value"></a>戻り値

フレームワークがメニューの影を描画する場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

この機能を有効または無効にするには、 [Cmfcmenubar:: EnableMenuShadows](#enablemenushadows)メソッドを使用します。

##  <a name="isrecentlyusedmenus"></a>CMFCMenuBar:: IsRecentlyUsedMenus

最近使用したメニューコマンドがメニューバーに表示されるかどうかを示します。

```
static BOOL IsRecentlyUsedMenus();
```

### <a name="return-value"></a>戻り値

`CMFCMenuBar` オブジェクトが最近使用したメニューコマンドを表示する場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

メニューバーに最近使用したメニューコマンドを表示するかどうかを制御するには、関数[Cmfcmenubar:: SetRecentlyUsedMenus](#setrecentlyusedmenus)を使用します。

##  <a name="isshowallcommands"></a>CMFCMenuBar:: IsShowAllCommands

メニューですべてのコマンドを表示するかどうかを示します。

```
static BOOL IsShowAllCommands();
```

### <a name="return-value"></a>戻り値

`CMFCMenuBar` にすべてのコマンドが表示される場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

`CMFCMenuBar` オブジェクトは、すべてのコマンドを表示するか、コマンドのサブセットのみを表示するように構成できます。 この機能の詳細については、「 [Cmfcmenubar クラス](../../mfc/reference/cmfcmenubar-class.md)」を参照してください。

`IsShowAllCommands` では、`CMFCMenuBar` オブジェクトに対してこの機能がどのように構成されているかがわかります。 表示されるメニューコマンドを制御するには、メソッド[Cmfcmenubar:: SetShowAllCommands](#setshowallcommands)および[Cmfcmenubar:: SetRecentlyUsedMenus](#setrecentlyusedmenus)を使用します。

##  <a name="isshowallcommandsdelay"></a>CMFCMenuBar:: IsShowAllCommandsDelay

[Cmfcmenubar](../../mfc/reference/cmfcmenubar-class.md)オブジェクトが、短い遅延の後にすべてのコマンドを表示するかどうかを示します。

```
static BOOL IsShowAllCommandsDelay();
```

### <a name="return-value"></a>戻り値

短い遅延後にメニューバーに全メニューが表示される場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>解説

最近使用した項目を表示するようにメニューバーを構成すると、メニューバーには次の2つの方法のいずれかで全メニューが表示されます。

- ユーザーがメニューの下部にある矢印の上にカーソルを置いたときから、プログラムによる遅延の後に完全なメニューを表示します。

- ユーザーがメニューの下部にある矢印をクリックした後、すべてのメニューを表示します。

既定では、すべての `CMFCMenuBar` オブジェクトは、短い遅延後に全メニューを表示するオプションを使用します。 このオプションは、`CMFCMenuBar` クラスでプログラムで変更することはできません。 ただし、ユーザーは、 **[カスタマイズ]** ダイアログボックスを使用して、ツールバーのカスタマイズ中に動作を変更できます。

##  <a name="loadstate"></a>CMFCMenuBar:: LoadState

Windows レジストリからメニューバーの状態を読み込みます。

```
virtual BOOL LoadState(
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
からWindows レジストリキーのパスを含む文字列。

*nIndex*<br/>
からメニューバーのコントロール ID。

*uiID*<br/>
から予約済みの値。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

[Cmfcmenubar:: SaveState](#savestate)メソッドを使用して、メニューバーの状態をレジストリに保存します。 保存された情報には、メニュー項目、ドッキング状態、およびメニューバーの位置が含まれます。

ほとんどの場合、アプリケーションは `LoadState`を呼び出しません。 フレームワークは、ワークスペースを初期化するときにこのメソッドを呼び出します。

##  <a name="onchangehot"></a>CMFCMenuBar:: OnChangeHot

```
virtual void OnChangeHot(int iHot);
```

### <a name="parameters"></a>パラメーター

から*Ihot*<br/>

### <a name="remarks"></a>解説

##  <a name="ondefaultmenuloaded"></a>CMFCMenuBar:: OnDefaultMenuLoaded

フレームワークは、リソースファイルからメニューリソースを読み込むときに、このメソッドを呼び出します。

```
virtual void OnDefaultMenuLoaded(HMENU hMenu);
```

### <a name="parameters"></a>パラメーター

*hMenu*<br/>
から`CMFCMenuBar` オブジェクトに関連付けられているメニューのハンドル。

### <a name="remarks"></a>解説

この関数の既定の実装は、何も行いません。 フレームワークによってリソースファイルからメニューリソースが読み込まれた後に、カスタムコードを実行するには、この関数をオーバーライドします。

##  <a name="onsendcommand"></a>CMFCMenuBar:: OnSendCommand

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>パラメーター

から*Pbutton*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="onsetdefaultbuttontext"></a>CMFCMenuBar:: OnSetDefaultButtonText

フレームワークは、ユーザーがメニューバー上の項目のテキストを変更したときに、このメソッドを呼び出します。

```
virtual BOOL OnSetDefaultButtonText(CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>パラメーター

*pButton*<br/>
からユーザーがカスタマイズを希望する[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

フレームワークがユーザーの変更をメニューバーに適用する場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

このメソッドの既定の実装では、ボタンのテキストが、ユーザーが入力したテキストに変更されます。

##  <a name="ontoolhittest"></a>CMFCMenuBar:: OnToolHitTest

```
virtual INT_PTR OnToolHitTest(
    CPoint point,
    TOOLINFO* pTI) const;
```

### <a name="parameters"></a>パラメーター

から*ポイント*<br/>

から*pTI*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="pretranslatemessage"></a>CMFCMenuBar::P reTranslateMessage

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>パラメーター

から*pMsg*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>解説

##  <a name="restoreoriginalstate"></a>CMFCMenuBar:: RestoreOriginalstate

ユーザーが **[カスタマイズ]** ダイアログボックスから **[リセット]** を選択したときに、フレームワークによって呼び出されます。

```
virtual BOOL RestoreOriginalstate();
```

### <a name="return-value"></a>戻り値

メソッドが成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

このメソッドは、ユーザーがカスタマイズメニューから **[リセット]** を選択したときに呼び出されます。 このメソッドを手動で呼び出して、メニューバーの状態をプログラムによってリセットすることもできます。 このメソッドは、リソースファイルから元の状態を読み込みます。

ユーザーが**リセット**オプションを選択したときに処理を実行する場合は、このメソッドをオーバーライドします。

##  <a name="savestate"></a>CMFCMenuBar:: SaveState

[Cmfcmenubar](../../mfc/reference/cmfcmenubar-class.md)オブジェクトの状態を Windows レジストリに保存します。

```
virtual BOOL SaveState (
    LPCTSTR lpszProfileName = NULL,
    int nIndex = -1,
    UINT uiID = (UINT)-1);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
からWindows レジストリキーのパスを含む文字列。

*nIndex*<br/>
からメニューバーのコントロール ID。

*uiID*<br/>
から予約済みの値。

### <a name="return-value"></a>戻り値

成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

通常、アプリケーションは `SaveState`を呼び出しません。 フレームワークは、ワークスペースがシリアル化されるときにこのメソッドを呼び出します。 詳細については、「 [CWinAppEx:: SaveState](../../mfc/reference/cwinappex-class.md#savestate)」を参照してください。

保存された情報には、メニュー項目、ドッキング状態、およびメニューバーの位置が含まれます。

##  <a name="setdefaultmenuresid"></a>CMFCMenuBar:: SetDefaultMenuResId

リソース ID に基づいて[Cmfcmenubar](../../mfc/reference/cmfcmenubar-class.md)オブジェクトの既定のメニューを設定します。

```
void SetDefaultMenuResId(UINT uiResId);
```

### <a name="parameters"></a>パラメーター

*uiResId*<br/>
から新しい既定のメニューのリソース ID。

### <a name="remarks"></a>解説

[Cmfcmenubar:: RestoreOriginalstate](#restoreoriginalstate)メソッドは、リソースファイルから既定のメニューを復元します。

[Cmfcmenubar:: GetDefaultMenuResId](#getdefaultmenuresid)メソッドを使用して、復元せずに既定のメニューを取得します。

##  <a name="setforcedownarrows"></a>CMFCMenuBar:: SetForceDownArrows

```
void SetForceDownArrows(BOOL bValue);
```

### <a name="parameters"></a>パラメーター

から*Bvalue*<br/>

### <a name="remarks"></a>解説

##  <a name="setmaximizemode"></a>CMFCMenuBar:: Set最大化 Izemode

フレームワークは、MDI が表示モードを変更し、メニューバーを更新する必要がある場合に、このメソッドを呼び出します。

```
void SetMaximizeMode(
    BOOL bMax,
    CWnd* pWnd = NULL,
    BOOL bRecalcLayout = TRUE);
```

### <a name="parameters"></a>パラメーター

*bMax*<br/>
からモードを指定するブール値です。 詳細については、「解説」を参照してください。

*pWnd*<br/>
から変更中の MDI 子ウィンドウへのポインター。

*bRecalcLayout*<br/>
からメニューバーのレイアウトをすぐに再計算する必要があるかどうかを指定するブール値。

### <a name="remarks"></a>解説

MDI 子ウィンドウが最大化されている場合、MDI メインフレームウィンドウに関連付けられているメニューバーには、システム メニューと **最小化**、**最大化**、**閉じる** の各ボタンが表示されます。 *Bmax*が TRUE で、 *pWnd*が NULL でない場合は、MDI 子ウィンドウが最大化され、メニューバーに追加のコントロールが組み込まれている必要があります。 それ以外の場合、メニューバーは通常の状態に戻ります。

##  <a name="setmenubuttonrtc"></a>CMFCMenuBar:: SetMenuButtonRTC

ユーザーがメニューボタンを作成するときにフレームワークが使用するランタイムクラス情報を設定します。

```
void SetMenuButtonRTC(CRuntimeClass* pMenuButtonRTC);
```

### <a name="parameters"></a>パラメーター

*pMenuButtonRTC*<br/>
から[Cmfcmenubutton クラス](../../mfc/reference/cmfcmenubutton-class.md)から派生したクラスの[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)情報。

### <a name="remarks"></a>解説

ユーザーがメニューバーに新しいボタンを追加すると、フレームワークによってボタンが動的に作成されます。 既定では `CMFCMenuButton` オブジェクトが作成されます。 フレームワークによって作成されるボタンオブジェクトの種類を変更するには、このメソッドをオーバーライドします。

##  <a name="setmenufont"></a>CMFCMenuBar:: SetMenuFont

アプリケーションのすべてのメニューバーのフォントを設定します。

```
static BOOL SetMenuFont(
    LPLOGFONT lpLogFont,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>パラメーター

*lpLogFont*<br/>
から設定するフォントを定義する[LOGFONT](/windows/win32/api/dimm/ns-dimm-logfonta)構造体へのポインター。

*bHorz*<br/>
から*LpLogFont*パラメーターを縦書きフォントに使用する場合は TRUE、水平フォントに使用する場合は FALSE です。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>解説

2つのフォントは、すべての `CMFCMenuBar` オブジェクトに使用されます。 これらの個別のフォントは、水平および垂直のメニューバーに使用されます。

フォントの設定はグローバル変数であり、すべての `CMFCMenuBar` オブジェクトに影響します。

##  <a name="setrecentlyusedmenus"></a>CMFCMenuBar:: SetRecentlyUsedMenus

メニューバーに最近使用したメニューコマンドを表示するかどうかを制御します。

```
static void SetRecentlyUsedMenus (BOOL bOn = TRUE);
```

### <a name="parameters"></a>パラメーター

*楽しい*<br/>
から最近使用したメニューコマンドを表示するかどうかを制御するブール値。

##  <a name="setshowallcommands"></a>CMFCMenuBar:: SetShowAllCommands

使用可能なすべてのコマンドをメニューに表示するかどうかを制御します。

```
static void SetShowAllCommands(BOOL bShowAllCommands = TRUE);
```

### <a name="parameters"></a>パラメーター

*bShowAllCommands*<br/>
からポップアップメニューにすべてのメニューコマンドを表示するかどうかを指定するブール型パラメーターです。

### <a name="remarks"></a>解説

メニューにメニューコマンドがすべて表示されない場合は、あまり使用されていないコマンドが非表示になります。 メニューコマンドの表示の詳細については、「 [Cmfcmenubar クラス](../../mfc/reference/cmfcmenubar-class.md)」を参照してください。

## <a name="see-also"></a>参照

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md)
