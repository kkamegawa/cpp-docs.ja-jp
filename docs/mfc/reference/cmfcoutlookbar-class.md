---
title: CMFCOutlookBar クラス
ms.date: 06/25/2018
f1_keywords:
- CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar
- AFXOUTLOOKBAR/CMFCOutlookBar::AllowDestroyEmptyTabbedPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanAcceptPane
- AFXOUTLOOKBAR/CMFCOutlookBar::CanSetCaptionTextToTabName
- AFXOUTLOOKBAR/CMFCOutlookBar::Create
- AFXOUTLOOKBAR/CMFCOutlookBar::CreateCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::DoesAllowDynInsertBefore
- AFXOUTLOOKBAR/CMFCOutlookBar::FloatTab
- AFXOUTLOOKBAR/CMFCOutlookBar::GetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::GetTabArea
- AFXOUTLOOKBAR/CMFCOutlookBar::IsMode2003
- AFXOUTLOOKBAR/CMFCOutlookBar::OnAfterAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnBeforeAnimation
- AFXOUTLOOKBAR/CMFCOutlookBar::OnScroll
- AFXOUTLOOKBAR/CMFCOutlookBar::RemoveCustomPage
- AFXOUTLOOKBAR/CMFCOutlookBar::SetButtonsFont
- AFXOUTLOOKBAR/CMFCOutlookBar::SetMode2003
helpviewer_keywords:
- CMFCOutlookBar [MFC], AllowDestroyEmptyTabbedPane
- CMFCOutlookBar [MFC], CanAcceptPane
- CMFCOutlookBar [MFC], CanSetCaptionTextToTabName
- CMFCOutlookBar [MFC], Create
- CMFCOutlookBar [MFC], CreateCustomPage
- CMFCOutlookBar [MFC], DoesAllowDynInsertBefore
- CMFCOutlookBar [MFC], FloatTab
- CMFCOutlookBar [MFC], GetButtonsFont
- CMFCOutlookBar [MFC], GetTabArea
- CMFCOutlookBar [MFC], IsMode2003
- CMFCOutlookBar [MFC], OnAfterAnimation
- CMFCOutlookBar [MFC], OnBeforeAnimation
- CMFCOutlookBar [MFC], OnScroll
- CMFCOutlookBar [MFC], RemoveCustomPage
- CMFCOutlookBar [MFC], SetButtonsFont
- CMFCOutlookBar [MFC], SetMode2003
ms.assetid: 2b335f71-ce99-4efd-b103-e65ba43ffc36
ms.openlocfilehash: fc1281db0271393ec0538e26c2a2d2af09c99f7a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374143"
---
# <a name="cmfcoutlookbar-class"></a>CMFCOutlookBar クラス

Microsoft Outlook 2000 または Outlook 2003 の **ナビゲーション ウィンドウ** と同じ外観を持つタブ付きペインです。 `CMFCOutlookBar`オブジェクトが含まれています、 [CMFCOutlookBarTabCtrl クラス](../../mfc/reference/cmfcoutlookbartabctrl-class.md)オブジェクトと一連のタブ。 タブは、 [CMFCOutlookBarPane クラス](../../mfc/reference/cmfcoutlookbarpane-class.md)オブジェクトまたは`CWnd`の派生オブジェクト。 ユーザーに対しては、Outlook バーは一連のボタンおよび表示領域として表示されます。 ユーザーがボタンをクリックすると、対応するコントロールまたはボタン ペインが表示されます。

## <a name="syntax"></a>構文

```cpp
class CMFCOutlookBar : public CBaseTabbedPane
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCOutlookBar::CMFCOutlookBar`|既定のコンストラクターです。|
|`CMFCOutlookBar::~CMFCOutlookBar`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCOutlookBar::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|空のタブ付きペインを破棄するかどうかを指定します。 (上書き[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](../../mfc/reference/cbasetabbedpane-class.md#allowdestroyemptytabbedpane))。|
|[CMFCOutlookBar::CanAcceptPane](#canacceptpane)|Outlook バー ペインを別のペインをドッキングできるかどうかを判断します。 (CDockablePane::CanAcceptPane を上書きします)。|
|[CMFCOutlookBar::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|タブ付きペインのキャプションがアクティブなタブとして、同じテキストを表示するかどうかを判断します。(上書き[CBaseTabbedPane::CanSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#cansetcaptiontexttotabname))。|
|[CMFCOutlookBar::Create](#create)|Outlook バー コントロールを作成します。|
|[CMFCOutlookBar::CreateCustomPage](#createcustompage)|カスタムの Outlook バー タブを作成します。|
|`CMFCOutlookBar::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|[CMFCOutlookBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|ユーザーが Outlook バーの外側にあるコントロール バーをドッキングできるかどうかを判断します。|
|[CMFCOutlookBar::FloatTab](#floattab)|現在ペインが切り離し可能なタブに存在する場合のみ、そのペインを切り離して表示します。(上書き[cbasetabbedpane::floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab))。|
|[CMFCOutlookBar::GetButtonsFont](#getbuttonsfont)|Outlook バーのボタンのテキストのフォントを返します。|
|[CMFCOutlookBar::GetTabArea](#gettabarea)|Outlook バーのサイズとタブ領域の位置を返します。 (上書き[CBaseTabbedPane::GetTabArea](../../mfc/reference/cbasetabbedpane-class.md#gettabarea))。|
|`CMFCOutlookBar::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|
|[CMFCOutlookBar::IsMode2003](#ismode2003)|Outlook バーの動作を模倣する Microsoft Office Outlook 2003 (「解説」を参照してください) のどうかを判断します。|
|[CMFCOutlookBar::OnAfterAnimation](#onafteranimation)|によって呼び出される[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)アニメーションを使用してアクティブなタブが設定されています。|
|[CMFCOutlookBar::OnBeforeAnimation](#onbeforeanimation)|によって呼び出される[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)タブの前にページがアニメーションを使用してアクティブなタブとして設定します。|
|[CMFCOutlookBar::OnScroll](#onscroll)|Outlook バーを上または下にスクロールする場合に、フレームワークによって呼び出されます。|
|[CMFCOutlookBar::RemoveCustomPage](#removecustompage)|カスタムの Outlook バー タブを削除します。|
|[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)|Outlook バーのボタンのテキストのフォントを設定します。|
|[CMFCOutlookBar::SetMode2003](#setmode2003)|Outlook バーの動作を模倣する Outlook 2003 (「解説」を参照してください) のどうかを指定します。|

## <a name="remarks"></a>Remarks

Outlook バーの例は、次を参照してください。、 [OutlookDemo サンプル。MFC OutlookDemo アプリケーション](../../overview/visual-cpp-samples.md)します。

## <a name="implementing-the-outlook-bar"></a>Outlook バーを実装します。

アプリケーションで、`CMFCOutlookBar` コントロールを使用するには、次の手順に従います。

1. `CMFCOutlookBar` オブジェクトをメイン フレーム ウィンドウ クラスに埋め込みます。

    ```cpp
    class CMainFrame : public CMDIFrameWnd
    {
        // ...
        CMFCOutlookBar m_wndOutlookBar;
        CMFCOutlookBarPane m_wndOutlookPane;
        // ...
    };
    ```

1. メイン フレームで WM_CREATE メッセージを処理するときに呼び出す、 [CMFCOutlookBar::Create](#create) Outlook バーのタブ コントロールを作成します。

    ```cpp
    m_wndOutlookBar.Create (_T("Shortcuts"),
        this,
        CRect (0, 0, 100, 100),
        ID_VIEW_OUTLOOKBAR,
        WS_CHILD | WS_VISIBLE | CBRS_LEFT);
    ```

1. 基になるポインターを取得する`CMFCOutlookBarTabCtrl`を使用して[CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow)します。

    ```cpp
    CMFCOutlookBarTabCtrl* pOutlookBar = (CMFCOutlookBarTabCtrl*) m_wndOutlookBar.GetUnderlyingWindow ();
    ```

1. 作成、 [CMFCOutlookBarPane クラス](../../mfc/reference/cmfcoutlookbarpane-class.md)の各タブのボタンを含むオブジェクト。

    ```cpp
    m_wndOutlookPane.Create(&m_wndOutlookBar,
        AFX_DEFAULT_TOOLBAR_STYLE,
        ID_OUTLOOK_PANE_GENERAL,
        AFX_CBRS_FLOAT | AFX_CBRS_RESIZE);

    // make the Outlook pane detachable (enable docking)
    m_wndOutlookPane.EnableDocking(CBRS_ALIGN_ANY);

    // add buttons
    m_wndOutlookPane.AddButton(theApp.LoadIcon (IDR_MAINFRAME),
        "About",
        ID_APP_ABOUT);

    m_wndOutlookPane.AddButton (theApp.LoadIcon (IDR_CUSTOM_OPEN_ICON),
        "Open",
        ID_FILE_OPEN);
    ```

1. 呼び出す[CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab)各新しいタブを追加します。設定、 *bDetachable*パラメーターを FALSE に、切り離し不可能なページを作成します。 または、使用して[CMFCOutlookBarTabCtrl::AddControl](../../mfc/reference/cmfcoutlookbartabctrl-class.md#addcontrol)切り離し可能なページを追加します。

    ```cpp
    pOutlookBar->AddTab (&m_wndOutlookPane, "General", (UINT) -1, TRUE);
    ```

1. 追加する、 `CWnd`-派生コントロール (たとえば、 [CMFCShellTreeCtrl クラス](../../mfc/reference/cmfcshelltreectrl-class.md))、タブ コントロールを作成して呼び出し[CMFCOutlookBarTabCtrl::AddTab](../../mfc/reference/cmfcbasetabctrl-class.md#addtab) Outlook バーに追加します。

> [!NOTE]
>  それぞれに一意のコントロール Id を使用する必要があります[CMFCOutlookBarPane クラス](../../mfc/reference/cmfcoutlookbarpane-class.md)オブジェクトと各`CWnd`-派生オブジェクト。

使用して動的に追加または削除の実行時に新しいページ、 [CMFCOutlookBar::CreateCustomPage](#createcustompage)と[CMFCOutlookBar::RemoveCustomPage](#removecustompage)します。

## <a name="outlook-2003-mode"></a>Outlook 2003 モード

Outlook 2003 モードでは、タブ ボタンは、Outlook バー ペインの下部に配置されます。 ボタンを表示するための十分なスペースが足りない、ウィンドウの下部にツールバーのような領域にアイコンとして表示されます。

使用[CMFCOutlookBar::SetMode2003](#setmode2003) Outlook 2003 モードを有効にします。 使用[CMFCOutlookBarTabCtrl::SetToolbarImageList](../../mfc/reference/cmfcoutlookbartabctrl-class.md#settoolbarimagelist) Outlook バーの下部に表示されるアイコンを含むビットマップを設定します。 ビットマップのアイコンは、タブ インデックスを使用して注文する必要があります。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CBaseTabbedPane](../../mfc/reference/cbasetabbedpane-class.md)

[CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxoutlookbar.h

##  <a name="allowdestroyemptytabbedpane"></a>  CMFCOutlookBar::AllowDestroyEmptyTabbedPane

空のタブ付きペインを破棄するかどうかを指定します。

```cpp
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>戻り値

TRUE の場合、空のタブ付きペインを破棄することができます。それ以外の場合、FALSE です。 既定の実装を常に TRUE を返します。

### <a name="remarks"></a>Remarks

場合は空のタブ付きペインを破棄することはできません、フレームワークを非表示に、代わりにします。

##  <a name="canacceptpane"></a>  CMFCOutlookBar::CanAcceptPane

Outlook バー ペインを別のペインをドッキングできるかどうかを判断します。

```cpp
virtual BOOL CanAcceptPane(const CBasePane* pBar) const;
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
[in]このペインにドッキングされる別のウィンドウへのポインター。

### <a name="return-value"></a>戻り値

Outlook バー ペイン; に別のペインをドッキングできる場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

バーがドッキングの Outlook 2003 モードで Outlook がサポートされていない場合、戻り値の値は FALSE はためです。

場合、 *pBar*パラメーターが NULL で、このメソッドは FALSE を返します。

このメソッドが基本のメソッドとして動作するそれ以外の場合、 [cbasepane::canacceptpane](../../mfc/reference/cbasepane-class.md#canacceptpane)ドッキングが有効でない場合でも、Outlook バーも有効にできます別の Outlook バーを上にドッキングされる点を除き、します。

##  <a name="cansetcaptiontexttotabname"></a>  CMFCOutlookBar::CanSetCaptionTextToTabName

タブ付きペインのキャプションがアクティブなタブとして、同じテキストを表示するかどうかを判断します。

```cpp
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>戻り値

Outlook ウィンドウのキャプション バーが自動的にアクティブなタブのテキストに設定されている場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

使用[CBaseTabbedPane::EnableSetCaptionTextToTabName](../../mfc/reference/cbasetabbedpane-class.md#enablesetcaptiontexttotabname)有効またはこの機能を無効にします。

Outlook 2003 モードでは、この設定は常に有効にします。

##  <a name="create"></a>  CMFCOutlookBar::Create

Outlook バー コントロールを作成します。

```cpp
virtual BOOL Create(
    LPCTSTR lpszCaption,
    CWnd* pParentWnd,
    const RECT& rect,
    UINT nID,
    DWORD dwStyle,
    DWORD dwControlBarStyle=AFX_CBRS_RESIZE,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>パラメーター

*lpszCaption*<br/>
[in]ウィンドウのキャプションを指定します。

*pParentWnd*<br/>
[in]親ウィンドウへのポインターを指定します。 NULL は指定できません。

*rect*<br/>
[in]Outlook バーのサイズと位置 (ピクセル単位) を指定します。

*nID*<br/>
[in]コントロールの ID を指定します その他のコントロール、アプリケーションで使用される Id とは異なる名前にする必要があります。

*dwStyle*<br/>
[in]目的のコントロール バーのスタイルを指定します。 使用可能な値は、次を参照してください。[ウィンドウ スタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)します。

*dwControlBarStyle*<br/>
[in]特殊なライブラリで定義されたスタイルを指定します。

*pContext*<br/>
[in]コンテキストを作成します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

構築する、 `CMFCOutlookBar` 2 つのステップ内のオブジェクト。 まず、コンス トラクターを呼び出します`Create`、outlook バー コントロールを作成しにアタッチする`CMFCOutlookBar`オブジェクト。

参照してください[cbasepane::createex](../../mfc/reference/cbasepane-class.md#createex)によって指定される使用可能なライブラリで定義されたスタイルの一覧については*dwControlBarStyle*します。

### <a name="example"></a>例

次の例では、使用する方法、`Create`のメソッド、`CMFCOutlookBar`クラス。 このコード スニペットの一部、 [Outlook マルチ ビュー サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_OutlookMultiViews#1](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#2](../../mfc/reference/codesnippet/cpp/cmfcoutlookbar-class_2.cpp)]

##  <a name="createcustompage"></a>  CMFCOutlookBar::CreateCustomPage

カスタムの Outlook バー タブを作成します。

```cpp
CMFCOutlookBarPane* CreateCustomPage(
    LPCTSTR lpszPageName,
    BOOL bActivatePage=TRUE,
    DWORD dwEnabledDocking=CBRS_ALIGN_ANY,
    BOOL bEnableTextLabels=TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszPageName*<br/>
[in]ページのラベル。

*bActivatePage*<br/>
[in]TRUE の場合、ページは作成時にアクティブになります。

*dwEnabledDocking*<br/>
[in]ページがデタッチされると、有効なドッキング辺を指定する cbrs_align _ フラグの組み合わせ。

*bEnableTextLabels*<br/>
[in]TRUE の場合、ページ上に存在するボタンのテキスト ラベルは有効です。

### <a name="return-value"></a>戻り値

新しく作成されたページで、または作成が失敗した場合は NULL へのポインター。

### <a name="remarks"></a>Remarks

カスタムの Outlook バー ページを作成するのにユーザーを有効にするのにには、このメソッドを使用します。 アプリケーションごとに最大 100 のページを作成することができます。 ページのコントロール Id は、一部が 0xF000 から起動します。 カスタムの Outlook バー ページの合計数が 100 を超える場合、作成が失敗します。

使用[CMFCOutlookBar::RemoveCustomPage](#removecustompage)カスタム ページを削除します。

##  <a name="doesallowdyninsertbefore"></a>  CMFCOutlookBar::DoesAllowDynInsertBefore

ユーザーが Outlook バーの外側にあるペインをドッキングできるかどうかを指定します。

```
DECLARE_MESSAGE_MAP virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>戻り値

既定の実装では、FALSE を返します。

### <a name="remarks"></a>Remarks

フレームワークによって、`DoesAllowDynInsertBefore`メソッドの動的なペインをドッキングする場所を探すときにします。 関数は、FALSE を返しますの場合、フレームワークには、ウィンドウの外側のエッジの動的ペインのドッキングは許可されません。

通常、静的な非フローティング コントロールとして Outlook バーを作成します。 派生クラスでは、この関数をオーバーライドし、この動作を変更する場合は TRUE を返すことができます。

> [!NOTE]
>  動的ペインをドッキングするときに、ドッキングされた静的なペインの状態を確認、ために、可能であれば静的ペインの後動的ペインをドッキングする必要があります。

##  <a name="floattab"></a>  CMFCOutlookBar::FloatTab

ペインをフローティングします。

```cpp
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide);
```

### <a name="parameters"></a>パラメーター

*pBar*<br/>
[in]Float 型に、ウィンドウへのポインター。

*nTabID*<br/>
[in]Float 型に、タブの 0 から始まるインデックス。

*dockMethod*<br/>
[in]使用して、ペインをフローティングするメソッドを指定します。  詳細については、次を参照してください。 [cbasetabbedpane::floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab)します。

*bHide*<br/>
[in]フローティングする前に、ウィンドウを非表示にする場合は TRUEそれ以外の場合、FALSE です。 このメソッドの基底クラスのバージョンとは異なりこのパラメーターに既定値はありません。

### <a name="return-value"></a>戻り値

ウィンドウをフローティング状態の場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドはのように、 [cbasetabbedpane::floattab](../../mfc/reference/cbasetabbedpane-class.md#floattab)を浮動小数点の Outlook バー コントロールの最後の残りのタブが有効にしない点が異なります。

##  <a name="getbuttonsfont"></a>  CMFCOutlookBar::GetButtonsFont

Outlook バーのボタンのタブ ページのテキストのフォントを返します。

```cpp
CFont* GetButtonsFont() const;
```

### <a name="return-value"></a>戻り値

Outlook のページ ボタン タブ バーのテキストを表示するために使用するフォント オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

この関数を使用して、Outlook のページ ボタン タブのテキストを表示するために使用するフォントを取得します。 呼び出すことによって、フォントを設定する[CMFCOutlookBar::SetButtonsFont](#setbuttonsfont)します。

##  <a name="gettabarea"></a>  CMFCOutlookBar::GetTabArea

Outlook バー上のタブ領域の位置とサイズを決定します。

```cpp
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const;
```

### <a name="parameters"></a>パラメーター

*rectTabAreaTop*<br/>
[out]関数が返す場合は、上部のタブ領域の (クライアント座標) での位置とサイズを格納します。

*rectTabAreaBottom*<br/>
[out]関数が返す場合は、下のタブ領域の (クライアント座標) での位置とサイズを格納します。

### <a name="remarks"></a>Remarks

フレームワークは、[ターゲット] ウィンドウをドッキングの種類を決定するには、このメソッドを呼び出します。 フレームワークは、ユーザーが [ターゲット] ウィンドウのタブ領域にドッキングするウィンドウをドラッグすることを判断した場合、[ターゲット] ウィンドウの新しいタブとして最初のウィンドウを追加しようとします。 それ以外の場合、[ターゲット] ウィンドウの適切な側にある最初のペインをドッキングしようとします。 フレームワークは、追加のドッキング ウィンドウに対応するスライダーを新しいコンテナーを作成します。

既定の実装`GetTabArea`Outlook バーが静的; である場合は、Outlook のバーの全体のクライアント領域を返す場合、Outlook バーがフローティングことはできません。 それ以外の場合、上部と下部にある Outlook バー コントロールのページ ボタンが取る領域を返します。

このメソッドから派生したクラスでオーバーライド`CMFCOutlookBar`この動作を変更します。

##  <a name="ismode2003"></a>  CMFCOutlookBar::IsMode2003

Microsoft Office Outlook 2003 の Outlook バーの動作を模倣するかどうかを指定します。

```cpp
BOOL IsMode2003() const;
```

### <a name="return-value"></a>戻り値

Outlook バーが Microsoft Office 2003 モードで実行されている場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

使用してこのモードを有効にすることができます[CMFCOutlookBar::SetMode2003](#setmode2003)します。

##  <a name="onafteranimation"></a>  CMFCOutlookBar::OnAfterAnimation

によって呼び出される[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)アニメーションを使用してアクティブなタブが設定されています。

```cpp
virtual void OnAfterAnimation(int nPage);
```

### <a name="parameters"></a>パラメーター

*nPage*<br/>
[in]アクティブになっているタブ ページの 0 から始まるインデックス。

### <a name="remarks"></a>Remarks

アクティブなタブの設定の視覚効果は、アニメーションを有効にするかどうかによって異なります。 詳細については、次を参照してください。 [CMFCOutlookBarTabCtrl::EnableAnimation](../../mfc/reference/cmfcoutlookbartabctrl-class.md#enableanimation)します。

##  <a name="onbeforeanimation"></a>  CMFCOutlookBar::OnBeforeAnimation

によって呼び出される[CMFCOutlookBarTabCtrl::SetActiveTab](../../mfc/reference/cmfcoutlookbartabctrl-class.md#setactivetab)タブの前にページがアニメーションを使用してアクティブなタブとして設定します。

```cpp
virtual BOOL OnBeforeAnimation(int nPage);
```

### <a name="parameters"></a>パラメーター

*nPage*<br/>
[in]アクティブ設定しようとしているタブ ページの 0 から始まるインデックス。

### <a name="return-value"></a>戻り値

TRUE の場合、新しいアクティブなタブの設定でアニメーションを使用する必要がありますまたはアニメーションを無効にする場合は FALSE を返します。

### <a name="remarks"></a>Remarks

##  <a name="onscroll"></a>  CMFCOutlookBar::OnScroll

Outlook バーを上または下にスクロールする場合に、フレームワークによって呼び出されます。

```cpp
virtual void OnScroll(BOOL bDown);
```

### <a name="parameters"></a>パラメーター

*bDown*<br/>
[in]Outlook バーは、下へスクロールまたは FALSE の場合、これは、スクロールする場合は TRUE。

### <a name="remarks"></a>Remarks

##  <a name="removecustompage"></a>  CMFCOutlookBar::RemoveCustomPage

カスタム Outlook バーのタブ ページを削除します。

```cpp
BOOL RemoveCustomPage(
    UINT uiPage,
    CMFCOutlookBarTabCtrl* pTargetWnd);
```

### <a name="parameters"></a>パラメーター

*uiPage*<br/>
[in]親の Outlook のウィンドウで、ページの 0 から始まるインデックス。

*pTargetWnd*<br/>
[in]Outlook の親ウィンドウへのポインター。

### <a name="return-value"></a>戻り値

カスタムのページが正常に削除された場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

カスタム ページを削除するには、この関数を呼び出します。 ページが削除されたときにそのコントロールの ID が使用可能な Id のプールに返されます。

ポインターを提供する必要があります[CMFCOutlookBarTabCtrl クラス](../../mfc/reference/cmfcoutlookbartabctrl-class.md)現在削除するページが存在するオブジェクトします。 別の Outlook バーの間、ユーザーが切り離し可能なページを移動できますが、呼び出したを Outlook バーのオブジェクトにカスタム ページに関する情報が存在する[CMFCOutlookBar::CreateCustomPage](#createcustompage)します。

使用[CBaseTabbedPane::GetUnderlyingWindow](../../mfc/reference/cbasetabbedpane-class.md#getunderlyingwindow) Outlook ウィンドウへのポインターを取得します。

##  <a name="setbuttonsfont"></a>  CMFCOutlookBar::SetButtonsFont

Outlook バーのボタンのテキストのフォントを設定します。

```cpp
void SetButtonsFont(
    CFont* pFont,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>パラメーター

*pFont*<br/>
[in]新しいフォントを指定します。

*bRedraw*<br/>
[in]TRUE の場合は、Outlook バーが再描画されます。

### <a name="remarks"></a>Remarks

このメソッドを使用すると、outlook のタブ ページのボタンに表示されるテキストのフォントを設定できます。

##  <a name="setmode2003"></a>  CMFCOutlookBar::SetMode2003

Outlook 2003 の Outlook バーの動作を模倣するかどうかを指定します。

```cpp
void SetMode2003(BOOL bMode2003=TRUE);
```

### <a name="parameters"></a>パラメーター

*bMode2003*<br/>
[in]TRUE の場合は、Office 2003 のモードを有効にします。

### <a name="remarks"></a>Remarks

有効にするか、Office 2003 のモードを無効にするには、この関数を使用します。 このモードでは、Outlook バーは、追加のツールバーのカスタマイズ ボタンを持ちます。 Outlook バーの動作は、Microsoft Office 2003 Outlook のバーの動作に準拠しています。

既定では、このモードは無効です。

> [!NOTE]
>  前に、この関数を呼び出す必要があります[CMFCOutlookBar::Create](#create)します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CBaseTabbedPane クラス](../../mfc/reference/cbasetabbedpane-class.md)<br/>
[CMFCOutlookBarTabCtrl クラス](../../mfc/reference/cmfcoutlookbartabctrl-class.md)<br/>
[CMFCOutlookBarPane クラス](../../mfc/reference/cmfcoutlookbarpane-class.md)
