---
title: CMFCColorBar クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCColorBar
- AFXCOLORBAR/CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::CMFCColorBar
- AFXCOLORBAR/CMFCColorBar::ContextToSize
- AFXCOLORBAR/CMFCColorBar::CreateControl
- AFXCOLORBAR/CMFCColorBar::Create
- AFXCOLORBAR/CMFCColorBar::EnableAutomaticButton
- AFXCOLORBAR/CMFCColorBar::EnableOtherButton
- AFXCOLORBAR/CMFCColorBar::GetColor
- AFXCOLORBAR/CMFCColorBar::GetCommandID
- AFXCOLORBAR/CMFCColorBar::GetHighlightedColor
- AFXCOLORBAR/CMFCColorBar::GetHorzMargin
- AFXCOLORBAR/CMFCColorBar::GetVertMargin
- AFXCOLORBAR/CMFCColorBar::IsTearOff
- AFXCOLORBAR/CMFCColorBar::SetColor
- AFXCOLORBAR/CMFCColorBar::SetColorName
- AFXCOLORBAR/CMFCColorBar::SetCommandID
- AFXCOLORBAR/CMFCColorBar::SetDocumentColors
- AFXCOLORBAR/CMFCColorBar::SetHorzMargin
- AFXCOLORBAR/CMFCColorBar::SetVertMargin
- AFXCOLORBAR/CMFCColorBar::AdjustLocations
- AFXCOLORBAR/CMFCColorBar::AllowChangeTextLabels
- AFXCOLORBAR/CMFCColorBar::AllowShowOnList
- AFXCOLORBAR/CMFCColorBar::CalcSize
- AFXCOLORBAR/CMFCColorBar::CreatePalette
- AFXCOLORBAR/CMFCColorBar::GetColorGridSize
- AFXCOLORBAR/CMFCColorBar::GetExtraHeight
- AFXCOLORBAR/CMFCColorBar::InitColors
- AFXCOLORBAR/CMFCColorBar::OnKey
- AFXCOLORBAR/CMFCColorBar::OnSendCommand
- AFXCOLORBAR/CMFCColorBar::OnUpdateCmdUI
- AFXCOLORBAR/CMFCColorBar::OpenColorDialog
- AFXCOLORBAR/CMFCColorBar::Rebuild
- AFXCOLORBAR/CMFCColorBar::SelectPalette
- AFXCOLORBAR/CMFCColorBar::SetPropList
- AFXCOLORBAR/CMFCColorBar::ShowCommandMessageString
helpviewer_keywords:
- CMFCColorBar [MFC], CMFCColorBar
- CMFCColorBar [MFC], ContextToSize
- CMFCColorBar [MFC], CreateControl
- CMFCColorBar [MFC], Create
- CMFCColorBar [MFC], EnableAutomaticButton
- CMFCColorBar [MFC], EnableOtherButton
- CMFCColorBar [MFC], GetColor
- CMFCColorBar [MFC], GetCommandID
- CMFCColorBar [MFC], GetHighlightedColor
- CMFCColorBar [MFC], GetHorzMargin
- CMFCColorBar [MFC], GetVertMargin
- CMFCColorBar [MFC], IsTearOff
- CMFCColorBar [MFC], SetColor
- CMFCColorBar [MFC], SetColorName
- CMFCColorBar [MFC], SetCommandID
- CMFCColorBar [MFC], SetDocumentColors
- CMFCColorBar [MFC], SetHorzMargin
- CMFCColorBar [MFC], SetVertMargin
- CMFCColorBar [MFC], AdjustLocations
- CMFCColorBar [MFC], AllowChangeTextLabels
- CMFCColorBar [MFC], AllowShowOnList
- CMFCColorBar [MFC], CalcSize
- CMFCColorBar [MFC], CreatePalette
- CMFCColorBar [MFC], GetColorGridSize
- CMFCColorBar [MFC], GetExtraHeight
- CMFCColorBar [MFC], InitColors
- CMFCColorBar [MFC], OnKey
- CMFCColorBar [MFC], OnSendCommand
- CMFCColorBar [MFC], OnUpdateCmdUI
- CMFCColorBar [MFC], OpenColorDialog
- CMFCColorBar [MFC], Rebuild
- CMFCColorBar [MFC], SelectPalette
- CMFCColorBar [MFC], SetPropList
- CMFCColorBar [MFC], ShowCommandMessageString
ms.assetid: 4756ee40-25a5-4cee-af7f-acab7993d1c7
ms.openlocfilehash: 25bfe3ef67fcca7708179d1a316af05b3ba49dda
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505428"
---
# <a name="cmfccolorbar-class"></a>CMFCColorBar クラス

クラス`CMFCColorBar`は、ドキュメントまたはアプリケーションで色を選択できるドッキングコントロールバーを表します。

## <a name="syntax"></a>構文

```
class CMFCColorBar : public CMFCPopupMenuBar
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCColorBar:: CMFCColorBar](#cmfccolorbar)|`CMFCColorBar` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCColorBar:: ContextToSize](#contexttosize)|カラーバーコントロールにボタンを格納するために必要な垂直方向と水平方向の余白を計算し、そのボタンの位置を調整します。|
|[CMFCColorBar:: CreateControl](#createcontrol)|カラーバーコントロールウィンドウを作成し、 `CMFCColorBar`オブジェクトにアタッチして、指定した色のパレットを格納するようにコントロールのサイズを変更します。|
|[CMFCColorBar:: 作成](#create)|カラーバーコントロールウィンドウを作成し、 `CMFCColorBar`オブジェクトにアタッチします。|
|[CMFCColorBar:: Enable自動ボタン](#enableautomaticbutton)|自動ボタンの表示と非表示を切り替えます。|
|[CMFCColorBar:: EnableOtherButton](#enableotherbutton)|ユーザーがより多くの色を選択できるダイアログボックスの表示を有効または無効にします。|
|[CMFCColorBar:: GetColor](#getcolor)|現在選択されている色を取得します。|
|[CMFCColorBar:: GetCommandID](#getcommandid)|現在のカラーバーコントロールのコマンド ID を取得します。|
|[CMFCColorBar:: GetHighlightedColor](#gethighlightedcolor)|カラーボタンにフォーカスがあることを示す色を取得します。つまり、ボタンが*ホット*になります。|
|[CMFCColorBar:: GetHorzMargin](#gethorzmargin)|水平方向の余白を取得します。これは、左または右の色のセルとクライアント領域の境界の間のスペースです。|
|[CMFCColorBar:: GetVertMargin](#getvertmargin)|垂直方向の余白を取得します。これは、上または下の色のセルとクライアント領域の境界の間のスペースです。|
|[CMFCColorBar:: IsTearOff](#istearoff)|現在のカラーバーがドッキング可能かどうかを示します。|
|[CMFCColorBar:: SetColor](#setcolor)|現在選択されている色を設定します。|
|[CMFCColorBar::SetColorName](#setcolorname)|指定した色の新しい名前を設定します。|
|[CMFCColorBar::SetCommandID](#setcommandid)|カラーバーコントロールの新しいコマンド ID を設定します。|
|[CMFCColorBar:: SetDocumentColors](#setdocumentcolors)|現在のドキュメントで使用されている色の一覧を設定します。|
|[CMFCColorBar:: SetHorzMargin](#sethorzmargin)|左右の余白を設定します。これは、左または右の色のセルとクライアント領域の境界の間のスペースです。|
|[CMFCColorBar:: SetVertMargin](#setvertmargin)|垂直方向の余白を設定します。これは、上または下の色のセルとクライアント領域の境界の間のスペースです。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCColorBar:: AdjustLocations](#adjustlocations)|カラーバーコントロールのカラーボタンの位置を調整します。|
|[CMFCColorBar::AllowChangeTextLabels](#allowchangetextlabels)|カラーボタンのテキストラベルを変更できるかどうかを示します。|
|[CMFCColorBar::AllowShowOnList](#allowshowonlist)|カスタマイズプロセス中に、カラーバーコントロールオブジェクトをツールバーの一覧に表示できるかどうかを示します。|
|[CMFCColorBar:: CalcSize](#calcsize)|レイアウトの計算プロセスの一部として、フレームワークによって呼び出されます。|
|[CMFCColorBar::CreatePalette](#createpalette)|指定した色の配列の色でパレットを初期化します。|
|[CMFCColorBar:: GetColorGridSize](#getcolorgridsize)|カラーバーコントロールのグリッド内の行と列の数を計算します。|
|[CMFCColorBar:: GetExtraHeight](#getextraheight)|**他の**ボタン、ドキュメントの色など、その他のユーザーインターフェイス要素を表示するために現在のカラーバーが必要とする追加の高さを計算します。|
|[CMFCColorBar::InitColors](#initcolors)|指定したパレットまたはシステムの既定のパレットの色を使用して、色の配列を初期化します。|
|[CMFCColorBar:: OnKey](#onkey)|ユーザーがキーボードボタンを押したときにフレームワークによって呼び出されます。|
|[CMFCColorBar:: OnSendCommand](#onsendcommand)|Popup コントロールの階層を閉じるために、フレームワークによって呼び出されます。|
|[CMFCColorBar:: OnUpdateCmdUI](#onupdatecmdui)|項目が表示される前に、カラーバーコントロールのユーザーインターフェイス項目を有効または無効にするために、フレームワークによって呼び出されます。|
|[CMFCColorBar::OpenColorDialog](#opencolordialog)|色のダイアログボックスを開きます。|
|[CMFCColorBar:: Rebuild](#rebuild)|カラーバーコントロールを完全に再描画します。|
|[CMFCColorBar:: SelectPalette](#selectpalette)|指定したデバイスコンテキストの論理パレットを、現在のカラーバーコントロールの親ボタンのパレットに設定します。|
|[CMFCColorBar:: SetPropList](#setproplist)|`m_pWndPropList`保護されたデータメンバーを、プロパティグリッドコントロールへの指定したポインターに設定します。|
|[CMFCColorBar:: ShowCommandMessageString](#showcommandmessagestring)|カラーバーコントロールを所有するフレームウィンドウに対して、ステータスバーのメッセージ行を更新するように要求します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|`m_bInternal`|マウスイベントを処理するかどうかを決定するブール値フィールド。 通常、このフィールドが TRUE でカスタマイズモードが FALSE の場合、マウスイベントが処理されます。|
|`m_bIsEnabled`|コントロールが有効かどうかを示すブール値。|
|`m_bIsTearOff`|カラーバーコントロールがドッキングをサポートするかどうかを示すブール値。|
|`m_BoxSize`|カラーバーグリッド内のセルのサイズを指定する[CSize](../../atl-mfc-shared/reference/csize-class.md)オブジェクト。|
|`m_bShowDocColorsWhenDocked`|カラーバーがドッキングされている場合にドキュメントの色を表示するかどうかを示すブール値。 詳細については、「 [Cmfccolorbar:: SetDocumentColors](#setdocumentcolors)」を参照してください。|
|`m_bStdColorDlg`|標準システムカラーダイアログボックスと [ [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ] ダイアログボックスのどちらを表示するかを示すブール値です。 詳細については、「 [Cmfccolorbar:: EnableOtherButton](#enableotherbutton)」を参照してください。|
|`m_ColorAutomatic`|現在の自動カラーを格納する[COLORREF](/windows/win32/gdi/colorref) 。 詳細については、「 [Cmfccolorbar:: EnableOtherButton](#enableotherbutton)」を参照してください。|
|`m_ColorNames`|RGB 色のセットをその名前に関連付ける[CMap](../../mfc/reference/cmap-class.md)オブジェクト。|
|`m_colors`|カラーバーコントロールに表示される色を含む[CArray](../../mfc/reference/carray-class.md) [の値です](/windows/win32/gdi/colorref)。|
|`m_ColorSelected`|ユーザーがカラーバーコントロールから現在選択している色である[COLORREF](/windows/win32/gdi/colorref)値。|
|`m_lstDocColors`|ドキュメントで現在使用されている色を含む[COLORREF](/windows/win32/gdi/colorref)値の[CList](../../mfc/reference/clist-class.md) 。|
|`m_nCommandID`|色のボタンのコマンド ID を表す符号なし整数。|
|`m_nHorzMargin`|色のグリッド内のカラーボタンの水平方向の余白を表す整数。|
|`m_nHorzOffset`|カラーボタンの中央の水平方向のオフセットを表す整数。 この値は、ボタンに色以外のテキストまたはイメージが表示される場合に重要です。|
|`m_nNumColumns`|色のカラーバーコントロールグリッド内の列数を表す整数。|
|`m_nNumColumnsVert`|色の垂直方向のグリッド内の列数を表す整数。|
|`m_nNumRowsHorz`|水平方向の色のグリッド内の列数を表す整数。|
|`m_nRowHeight`|色のグリッドにあるカラーボタンの行の高さを表す整数。|
|`m_nVertMargin`|色のグリッド内のカラーボタン間の垂直方向の余白を表す整数。|
|`m_nVertOffset`|カラーボタンの中央の垂直方向のオフセットを表す整数。 この値は、ボタンに色以外のテキストまたはイメージが表示される場合に重要です。|
|`m_Palette`|カラーバーコントロールで使用される色の[CPalette](../../mfc/reference/cpalette-class.md) 。|
|`m_pParentBtn`|現在のボタンの親である[Cmfccolorbutton](../../mfc/reference/cmfccolorbutton-class.md)オブジェクトへのポインター。 この値は、カラーボタンがツールバーコントロールの階層内にある場合、またはカラープロパティグリッドコントロールにある場合に重要です。|
|`m_pParentRibbonBtn`|リボン上にあり、現在のボタンの親ボタンである[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)オブジェクトへのポインター。 この値は、カラーボタンがツールバーコントロールの階層内にある場合、またはカラープロパティグリッドコントロールにある場合に重要です。|
|`m_pWndPropList`|[Cmfcpropertygridctrl](../../mfc/reference/cmfcpropertygridctrl-class.md)オブジェクトへのポインター。|
|`m_strAutoColor`|**自動**ボタンに表示されるテキストである[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。 詳細については、「 [Cmfccolorbar:: Enable自動ボタン](#enableautomaticbutton)」を参照してください。|
|`m_strDocColors`|[ドキュメントの色] ボタンに表示されるテキストである[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。 詳細については、「 [Cmfccolorbar:: SetDocumentColors](#setdocumentcolors)」を参照してください。|
|`m_strOtherColor`|*他の*ボタンに表示されるテキストである[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。 詳細については、「 [Cmfccolorbar:: EnableOtherButton](#enableotherbutton)」を参照してください。|

## <a name="remarks"></a>Remarks

通常、オブジェクトを`CMFCColorBar`直接作成することはありません。 代わりに、 [cmfccolormenubutton クラス](../../mfc/reference/cmfccolormenubutton-class.md)(メニューやツールバーで使用されます) または[cmfccolorbutton クラス](../../mfc/reference/cmfccolorbutton-class.md)によってオブジェクトが`CMFCColorBar`作成されます。

クラス`CMFCColorBar`には、次の機能が用意されています。

- ドキュメントの色の一覧を自動的に調整します。

- 状態をドキュメントの状態と共に保存して復元します。

- [自動] ボタンを管理します。

- [CMFCColorPickerCtrl クラス](../../mfc/reference/cmfccolorpickerctrl-class.md)コントロールを使用して、カスタム色を選択します。

- "ティアオフ" 状態をサポートします ( [Cmfccolormenubutton クラス](../../mfc/reference/cmfccolormenubutton-class.md)を使用して作成されている場合)。

機能をアプリケーション`CMFCColorBar`に組み込むには、次のようにします。

1. 通常のメニューボタンを作成し、ID_CHAR_COLOR などの ID を割り当てます。

1. フレームウィンドウクラスで、 [CFrameWndEx:: OnShowPopupMenu](../../mfc/reference/cframewndex-class.md#onshowpopupmenu)メソッドをオーバーライドし、通常のメニューボタンを[cmfccolormenubutton クラス](../../mfc/reference/cmfccolormenubutton-class.md)オブジェクトに置き換えます ( [Cmfctoolbar:: replacebutton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)を呼び出します)。

1. [Cmfccolormenubutton クラス](../../mfc/reference/cmfccolormenubutton-class.md)の作成中に、すべての`CMFCColorBar`スタイルを設定し、オブジェクトの機能を有効または無効にします。 オブジェクトは、フレームワークが`CMFCColorBar`メソッドを`CreatePopupMenu`呼び出した後にオブジェクトを動的に作成します。 `CMFCColorMenuButton`

ユーザーがカラーバーコントロールボタンをクリックすると、フレームワークは`ON_COMMAND`マクロを使用して、カラーバーコントロールの親を通知します。 マクロでは、コマンド ID パラメーターは、手順1でカラーバーコントロールボタンに割り当てた値 (この例では ID_CHAR_COLOR) です。 詳細については、「 [Cmfccolormenubutton](../../mfc/reference/cmfccolormenubutton-class.md)クラス」、「 [cmfccolorbutton](../../mfc/reference/cmfccolorbutton-class.md)クラス」、「 [CMFCColorPickerCtrl クラス](../../mfc/reference/cmfccolorpickerctrl-class.md)」、「 [CFrameWndEx クラス](../../mfc/reference/cframewndex-class.md)」、および「 [cmfctoolbar クラス](../../mfc/reference/cmfctoolbar-class.md)クラス」を参照してください。

## <a name="example"></a>例

次の例は、 `CMFCColorBar`クラスのさまざまなメソッドを使用してカラーバーを構成する方法を示しています。 これらのメソッドは、水平方向と垂直方向の余白を設定し、[その他] ボタンを有効にし、カラーバーコントロールウィンドウを作成し、現在選択されている色を設定します。 この例は、「[新しいコントロールのサンプル](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_NewControls#1](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#2](../../mfc/reference/codesnippet/cpp/cmfccolorbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCPopupMenuBar](../../mfc/reference/cmfcpopupmenubar-class.md)

[CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcolorbar

##  <a name="adjustlocations"></a>  CMFCColorBar::AdjustLocations

カラーバーコントロールのカラーボタンの位置を調整します。

```
virtual void AdjustLocations();
```

### <a name="remarks"></a>Remarks

このメソッドは、WM_SIZE メッセージ処理中にフレームワークによって呼び出されます。

##  <a name="allowchangetextlabels"></a>  CMFCColorBar::AllowChangeTextLabels

カラーボタンのテキストラベルを変更できるかどうかを示します。

```
virtual BOOL AllowChangeTextLabels() const;
```

### <a name="return-value"></a>戻り値

常に FALSE です。

### <a name="remarks"></a>Remarks

既定では、このメソッドは常に FALSE を返します。これは、テキストラベルを変更できないことを意味します。 テキストラベルを変更できるようにするには、このメソッドをオーバーライドします。

##  <a name="allowshowonlist"></a>  CMFCColorBar::AllowShowOnList

カスタマイズプロセス中に、カラーバーコントロールオブジェクトをツールバーの一覧に表示できるかどうかを示します。

```
virtual BOOL AllowShowOnList() const;
```

### <a name="return-value"></a>戻り値

常に TRUE です。

### <a name="remarks"></a>Remarks

既定では、このメソッドは常に TRUE を返します。これは、フレームワークがカスタマイズプロセス中にカラーバーコントロールを表示できることを意味します。 別の動作を実装するには、このメソッドをオーバーライドします。

##  <a name="calcsize"></a>CMFCColorBar:: CalcSize

レイアウトの計算プロセスの一部として、フレームワークによって呼び出されます。

```
virtual CSize CalcSize(BOOL bVertDock);
```

### <a name="parameters"></a>パラメーター

*bVertDock*<br/>
からカラーバーコントロールを垂直方向にドッキングするように指定する場合は TRUE。カラーバーコントロールを水平方向にドッキングするように指定する場合は FALSE。

### <a name="return-value"></a>戻り値

カラーバーコントロールのカラーボタンの配列のサイズ。

##  <a name="cmfccolorbar"></a>CMFCColorBar:: CMFCColorBar

`CMFCColorBar` オブジェクトを構築します。

```
CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    int nRowsDockHorz,
    int nColDockVert,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCColorButton* pParentBtn);

CMFCColorBar(
    const CArray<COLORREF,COLORREF>& colors,
    COLORREF color,
    LPCTSTR lpszAutoColor,
    LPCTSTR lpszOtherColor,
    LPCTSTR lpszDocColors,
    CList<COLORREF,COLORREF>& lstDocColors,
    int nColumns,
    COLORREF colorAutomatic,
    UINT nCommandID,
    CMFCRibbonColorButton* pParentRibbonBtn);

CMFCColorBar(
    CMFCColorBar& src,
    UINT uiCommandID);
```

### <a name="parameters"></a>パラメーター

*色数*<br/>
からフレームワークによってカラーバーコントロールに表示される色の配列。

*色*<br/>
から最初に選択された色。

*lpszAutoColor*<br/>
から*自動*(既定) カラーボタンのテキストラベル、または NULL。

自動 ボタンの標準ラベルは **自動** です。

*lpszOtherColor*<br/>
から*他*のボタンのテキストラベル。より多くの色の選択肢を表示するか、NULL を表示します。

その他のボタンの標準のラベルは**他の色**。

*lpszDocColors*<br/>
から[ドキュメントの色] ボタンのテキストラベル。 ドキュメントの色パレットには、ドキュメントが現在使用しているすべての色が表示されます。

*lstDocColors*<br/>
からドキュメントが現在使用している色の一覧。

*nColumns*<br/>
から色の配列に含まれる列の数。

*nRowsDockHorz*<br/>
から水平方向にドッキングしたときにカラーバーが持つ行の数。

*nColDockVert*<br/>
からカラーバーが垂直方向にドッキングされるときの列の数。

*colorAutomatic*<br/>
から[自動] ボタンをクリックしたときにフレームワークによって適用される既定の色です。

*nCommandID*<br/>
からカラーバーコントロールのコマンド ID。

*pParentBtn*<br/>
から親ボタンへのポインター。

*src*<br/>
から`CMFCColorBar` 新しい`CMFCColorBar`オブジェクトにコピーされる既存のオブジェクト。

*uiCommandID*<br/>
からコマンド ID。

##  <a name="contexttosize"></a>  CMFCColorBar::ContextToSize

カラーバーコントロールにボタンを含めるために必要な垂直方向と水平方向の余白を計算し、それらのボタンの位置を調整します。

```
void ContextToSize(
    BOOL bSquareButtons = TRUE,
    BOOL bCenterButtons = TRUE);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*bSquareButtons*|からカラーバーコントロールのボタンの形状が四角形であることを指定する場合は TRUE。それ以外の場合は FALSE。 既定値は TRUE です。|
|*B中央ボタン*|からカラーバーコントロールボタンの表面上のコンテンツを中央揃えにするように指定する場合は TRUE。それ以外の場合は FALSE。 既定値は TRUE です。|

### <a name="remarks"></a>Remarks

##  <a name="create"></a>  CMFCColorBar::Create

カラーバーコントロールウィンドウを作成し、 `CMFCColorBar`オブジェクトにアタッチします。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle,
    UINT nID,
    CPalette* pPalette=NULL,
    int nColumns=0,
    int nRowsDockHorz=0,
    int nColDockVert=0);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
から親ウィンドウへのポインター。

*dwStyle*<br/>
から[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)のビットごとの組み合わせ (または)。

*nID*<br/>
からコマンド ID。

*pPalette*<br/>
から色のパレットへのポインター。 既定値は NULL です。

*nColumns*<br/>
からカラーバーコントロール内の列の数。 既定値は 0 です。

*nRowsDockHorz*<br/>
から水平方向にドッキングしたときのカラーバーコントロール内の行の数。 既定値は 0 です。

*nColDockVert*<br/>
からカラーバーコントロールが垂直方向にドッキングされるときの列数。 既定値は 0 です。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

`CMFCColorBar`オブジェクトを構築するには、このメソッドでクラスコンストラクターを呼び出します。 メソッド`Create`は、Windows コントロールを作成し、色のリストを初期化します。

##  <a name="createcontrol"></a>  CMFCColorBar::CreateControl

カラーバーコントロールウィンドウを作成し、 `CMFCColorBar`オブジェクトにアタッチし、指定した色のパレットを含むようにコントロールウィンドウのサイズを変更します。

```
virtual BOOL CreateControl(
    CWnd* pParentWnd,
    const CRect& rect,
    UINT nID,
    int nColumns=-1,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
から親ウィンドウへのポインター。 Nll は指定できません。

*rect*<br/>
からカラーバーコントロールの描画位置を指定する外接する四角形。

*nID*<br/>
からコントロール ID。

*nColumns*<br/>
からカラーバーコントロールの列の理想的な数。 このメソッドは、指定した色のパレットに応じてその数値を変更します。 既定値は-1 です。これは、このパラメーターが指定されていないことを意味します。

*pPalette*<br/>
から色のパレットへのポインター、または NULL。 このパラメーターが NULL の場合、このメソッドは、20色が指定されているかのようにカラーバーコントロールのサイズを計算します。 既定値は NULL です。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、 *rect*、 *ncolumns*、および*pPalette*パラメーターを使用して、カラーバーコントロール内の適切な数、行、および列を計算し、 [cmfccolorbar:: Create](#create)メソッドを呼び出します。

##  <a name="createpalette"></a>  CMFCColorBar::CreatePalette

指定した色の配列の色でパレットを初期化します。

```
static BOOL CreatePalette(
    const CArray<COLORREF, COLORREF>& arColors,
    CPalette& palette);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*arColors*|から色の配列。|
|*スロープ*|から色のパレット。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

##  <a name="enableautomaticbutton"></a>  CMFCColorBar::EnableAutomaticButton

自動ボタンの表示と非表示を切り替えます。

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
から*自動*(既定) カラーボタンのテキストラベル、または NULL。

自動 ボタンの標準ラベルは **自動** です。

*colorAutomatic*<br/>
から[自動] ボタンをクリックしたときにフレームワークによって適用される既定の色です。

*bEnable*<br/>
から[自動] ボタンを有効にする場合は TRUE。[自動] ボタンを無効にする場合は FALSE。 既定値は TRUE です。

### <a name="remarks"></a>Remarks

*Lpszlabel*パラメーターが NULL の場合、または*BENABLE*パラメーターが FALSE の場合、[自動] ボタンのテキストラベルは削除されます。

##  <a name="enableotherbutton"></a>CMFCColorBar:: EnableOtherButton

ユーザーがより多くの色を選択できるダイアログボックスの表示を有効または無効にします。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
から*他*のボタンのテキストラベル。より多くの色の選択肢を表示するか、NULL を表示します。

このボタンの標準的なラベルは**他の色**。

*Tcolordlg*<br/>
から[ [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ] ダイアログボックスを表示する場合は TRUE。FALSE を選択すると、標準の[CColorDialog](../../mfc/reference/ccolordialog-class.md)ダイアログボックスが表示されます。 既定値は TRUE です。

*bEnable*<br/>
からボタンを有効にする場合は TRUE。このボタンを無効にする場合は FALSE。 既定値は TRUE です。

##  <a name="getcolor"></a>  CMFCColorBar::GetColor

現在選択されている色を取得します。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>戻り値

現在選択されている色。

##  <a name="getcolorgridsize"></a>CMFCColorBar:: GetColorGridSize

カラーバーコントロールのグリッド内の行と列の数を計算します。

```
CSize GetColorGridSize(BOOL bVertDock) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*bVertDock*|から垂直方向にドッキングされたカラーバーコントロールの計算を実行する場合は TRUE。それ以外の場合は、水平方向にドッキングされたコントロールに対して計算を実行します。|

### <a name="return-value"></a>戻り値

列 `cx`の数を格納し、そのコンポーネントに行の数を格納している、[CSize](../../atl-mfc-shared/reference/csize-class.md) オブジェクト。`cy`

##  <a name="getcommandid"></a>  CMFCColorBar::GetCommandID

現在のカラーバーコントロールのコマンド ID を取得します。

```
UINT GetCommandID() const;
```

### <a name="return-value"></a>戻り値

コマンド ID。

### <a name="remarks"></a>Remarks

ユーザーが新しい色を選択すると、フレームワークは、 `CMFCColorBar`オブジェクトの親を通知するために、WM_COMMAND メッセージにコマンド ID を送信します。

##  <a name="getextraheight"></a>CMFCColorBar:: GetExtraHeight

**他の**ボタンやドキュメントの色など、その他のユーザーインターフェイス要素を表示するために現在のカラーバーが必要とする追加の高さを計算します。

```
int GetExtraHeight(int nNumColumns) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*nNumColumns*|からカラーバーコントロールにドキュメントの色が含まれている場合は、ドキュメントの色のグリッドに表示する列の数を指定します。 それ以外の場合、この値は使用されません。|

### <a name="return-value"></a>戻り値

必要な、計算された追加の高さ。

##  <a name="gethighlightedcolor"></a>CMFCColorBar:: GetHighlightedColor

カラーボタンにフォーカスがあることを示す色を取得します。つまり、ボタンが*ホット*になります。

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>戻り値

RGB 値。

### <a name="remarks"></a>Remarks

##  <a name="gethorzmargin"></a>  CMFCColorBar::GetHorzMargin

水平方向の余白を取得します。これは、左または右の色のセルとクライアント領域の境界の間のスペースです。

```
int GetHorzMargin();
```

### <a name="return-value"></a>戻り値

水平方向の余白。

##  <a name="getvertmargin"></a>  CMFCColorBar::GetVertMargin

垂直方向の余白を取得します。これは、上または下の色のセルとクライアント領域の境界の間のスペースです。

```
int GetVertMargin() const;
```

### <a name="return-value"></a>戻り値

垂直方向の余白。

##  <a name="initcolors"></a>  CMFCColorBar::InitColors

指定したパレットの色またはシステムの既定のパレットを使用して、色の配列を初期化します。

```
static int InitColors(
    CPalette* pPalette,
    CArray<COLORREF, COLORREF>& arColors);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pPalette*|からパレットオブジェクトへのポインター、または NULL。 このパラメーターが NULL の場合、このメソッドはオペレーティングシステムの既定のパレットを使用します。|
|*arColors*|から色の配列。|

### <a name="return-value"></a>戻り値

色の配列内の要素の数。

##  <a name="istearoff"></a>CMFCColorBar:: IsTearOff

現在のカラーバーがドッキング可能かどうかを示します。

```
BOOL IsTearOff() const;
```

### <a name="return-value"></a>戻り値

現在のカラーバーコントロールがドッキング可能な場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

カラーバーコントロールがドッキング可能な場合は、コントロールバーから切り離して別の場所にドッキングすることができます。

##  <a name="onkey"></a>  CMFCColorBar::OnKey

ユーザーがキーボードボタンを押したときにフレームワークによって呼び出されます。

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>パラメーター

*nChar*<br/>
からユーザーが押したキーの仮想キーコード。

### <a name="return-value"></a>戻り値

指定したキーをこのメソッドが処理する場合は TRUE。それ以外の場合は FALSE。

##  <a name="onsendcommand"></a>CMFCColorBar:: OnSendCommand

ポップアップコントロールの階層を閉じるために、フレームワークによって呼び出されます。

```
virtual BOOL OnSendCommand(const CMFCToolBarButton* pButton);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pButton*|からツールバー上に存在するコントロールへのポインター。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

##  <a name="onupdatecmdui"></a>CMFCColorBar:: OnUpdateCmdUI

項目が表示される前に、カラーバーコントロールのユーザーインターフェイス項目を有効または無効にするために、フレームワークによって呼び出されます。

```
virtual void OnUpdateCmdUI(
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>パラメーター

*pTarget*<br/>
から更新するユーザーインターフェイス項目を格納しているウィンドウへのポインター。

*bDisableIfNoHndler*<br/>
からメッセージマップでハンドラーが定義されていない場合にユーザーインターフェイス項目を無効にする場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

アプリケーションのユーザーがユーザーインターフェイスの項目をクリックすると、その項目が [有効] または [無効] と表示されているかどうかを確認する必要があります。 コマンドメッセージのターゲットは、ON_UPDATE_COMMAND_UI コマンドハンドラーを実装することによってこの情報を提供します。 このメソッドを使用すると、コマンドを処理できます。 詳細については、「 [CCmdUI クラス](../../mfc/reference/ccmdui-class.md)」を参照してください。

##  <a name="opencolordialog"></a>  CMFCColorBar::OpenColorDialog

色のダイアログボックスを開きます。

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>パラメーター

*colorDefault*<br/>
から色のダイアログボックスが開いたときに既定で選択される色。

*colorRes*<br/>
入出力ユーザーが選択した色。

### <a name="return-value"></a>戻り値

ユーザーが色を選択した場合は TRUE。ユーザーが色のダイアログボックスをキャンセルした場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="rebuild"></a>  CMFCColorBar::Rebuild

カラーバーコントロールを完全に再描画します。

```
virtual void Rebuild();
```

##  <a name="selectpalette"></a>  CMFCColorBar::SelectPalette

指定したデバイスコンテキストの論理パレットを、現在のカラーバーコントロールの親ボタンのパレットに設定します。

```
CPalette* SelectPalette(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pDC*|から現在のカラーバーコントロールの親ボタンのデバイスコンテキストへのポインター。|

### <a name="return-value"></a>戻り値

現在のカラーバーコントロールの親ボタンのパレットで置き換えられたパレットへのポインター。

##  <a name="setcolor"></a>  CMFCColorBar::SetColor

現在選択されている色を設定します。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
からRGB カラー値。

##  <a name="setcolorname"></a>  CMFCColorBar::SetColorName

指定した色の新しい名前を設定します。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
から色の RGB 値。

*strName*<br/>
から指定した色の新しい名前。

### <a name="remarks"></a>Remarks

このメソッドは、アプリケーション内のすべて`CMFCColorBar`のオブジェクトで、指定した色の名前を変更します。

##  <a name="setcommandid"></a>  CMFCColorBar::SetCommandID

カラーバーコントロールの新しいコマンド ID を設定します。

```
void SetCommandID(UINT nCommandID);
```

### <a name="parameters"></a>パラメーター

*nCommandID*<br/>
からコマンド ID。

### <a name="remarks"></a>Remarks

カラーバーコントロールのコマンド ID を変更し、ID が変更されたことをコントロールの親ウィンドウに通知するには、このメソッドを呼び出します。

##  <a name="setdocumentcolors"></a>CMFCColorBar:: SetDocumentColors

現在のドキュメントで使用されている色の一覧を設定します。

```
void SetDocumentColors(
    LPCTSTR lpszCaption,
    CList<COLORREF,COLORREF>& lstDocColors,
    BOOL bShowWhenDocked=FALSE);
```

### <a name="parameters"></a>パラメーター

*lpszCaption*<br/>
からカラーバーコントロールがドッキングされていない場合に表示されるキャプション。

*lstDocColors*<br/>
から現在のドキュメントの色を置き換える色の一覧。

*bShowWhenDocked*<br/>
からカラーバーコントロールがドッキングされているときにドキュメントの色を表示する場合は TRUE。それ以外の場合は FALSE。 既定値は FALSE です。

### <a name="remarks"></a>Remarks

*ドキュメントの色*は、ドキュメントで現在使用されている色です。 フレームワークはドキュメントの色の一覧を自動的に保持しますが、この方法を使用して一覧を変更できます。

##  <a name="sethorzmargin"></a>  CMFCColorBar::SetHorzMargin

水平方向の余白を設定します。これは、左または右の色のセルとクライアント領域の境界の間のスペースです。

```
void SetHorzMargin(int nHorzMargin);
```

### <a name="parameters"></a>パラメーター

*nHorzMargin*<br/>
から水平方向の余白 (ピクセル単位)。

### <a name="remarks"></a>Remarks

既定では、 [Cmfccolorbar:: cmfccolorbar](#cmfccolorbar)コンストラクターは、水平方向の余白を4ピクセルに設定します。

##  <a name="setproplist"></a>CMFCColorBar:: SetPropList

`m_pWndPropList`保護されたデータメンバーを、プロパティグリッドコントロールへの指定したポインターに設定します。

```
void SetPropList(CMFCPropertyGridCtrl* pWndList);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pWndList*|からプロパティグリッドコントロールオブジェクトへのポインター。|

##  <a name="setvertmargin"></a>  CMFCColorBar::SetVertMargin

垂直方向の余白を設定します。これは、上または下の色のセルとクライアント領域の境界の間のスペースです。

```
void SetVertMargin(int nVertMargin);
```

### <a name="parameters"></a>パラメーター

*nVertMargin*<br/>
から垂直方向の余白 (ピクセル単位)。

### <a name="remarks"></a>Remarks

既定では、 [Cmfccolorbar:: cmfccolorbar](#cmfccolorbar)コンストラクターは、垂直方向の余白を4ピクセルに設定します。

##  <a name="showcommandmessagestring"></a>  CMFCColorBar::ShowCommandMessageString

カラーバーコントロールを所有するフレームウィンドウに対して、ステータスバーのメッセージ行を更新するように要求します。

```
virtual void ShowCommandMessageString(UINT uiCmdId);
```

### <a name="parameters"></a>パラメーター

*uiCmdId*<br/>
からコマンド ID。 (このパラメーターは無視されます)。

### <a name="remarks"></a>Remarks

このメソッドは、カラーバーコントロールの所有者に WM_SETMESSAGESTRING メッセージを送信します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
