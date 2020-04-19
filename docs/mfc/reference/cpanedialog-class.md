---
title: C区画ダイアログクラス
ms.date: 11/04/2016
f1_keywords:
- CPaneDialog
- AFXPANEDIALOG/CPaneDialog
- AFXPANEDIALOG/CPaneDialog::Create
- AFXPANEDIALOG/CPaneDialog::HandleInitDialog
- AFXPANEDIALOG/CPaneDialog::SetOccDialogInfo
helpviewer_keywords:
- CPaneDialog [MFC], Create
- CPaneDialog [MFC], HandleInitDialog
- CPaneDialog [MFC], SetOccDialogInfo
ms.assetid: 48a6bb91-4b92-40f5-8907-b3270b146cf6
ms.openlocfilehash: e7ff55e37194d0fa405925e4b3895428cfcaf9eb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502989"
---
# <a name="cpanedialog-class"></a>C区画ダイアログクラス

クラス`CPaneDialog`は、モードレスでドッキング可能なダイアログボックスをサポートしています。

## <a name="syntax"></a>構文

```
class CPaneDialog : public CDockablePane
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CPaneDialog::CPaneDialog`|既定のコンストラクターです。|
|`CPaneDialog::~CPaneDialog`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CPaneDialog::Create](#create)|ドッキング可能なダイアログボックスを作成し、 `CPaneDialog`オブジェクトにアタッチします。|
|`CPaneDialog::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|`CPaneDialog::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|[CPaneDialog::HandleInitDialog](#handleinitdialog)|[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)メッセージを処理します。 (再`CBasePane::HandleInitDialog`定義します)。|
|`CPaneDialog::OnEraseBkgnd`|[WM_ERASEBKGND](/windows/win32/winmsg/wm-erasebkgnd)メッセージを処理します。 ( [CWnd:: OnEraseBkgnd](../../mfc/reference/cwnd-class.md#onerasebkgnd)を再定義します)。|
|`CPaneDialog::OnLButtonDblClk`|[WM_LBUTTONDBLCLK](/windows/win32/inputdev/wm-lbuttondblclk)メッセージを処理します。 ( [CWnd:: OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)を再定義します)。|
|`CPaneDialog::OnLButtonDown`|[WM_LBUTTONDOWN](/windows/win32/inputdev/wm-lbuttondown)メッセージを処理します。 ( [CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)を再定義します)。|
|`CPaneDialog::OnUpdateCmdUI`|ダイアログボックスウィンドウを更新するためにフレームワークによって呼び出されます。 ( [CDockablePane:: OnUpdateCmdUI](cdockablepane-class.md)をオーバーライドします。)|
|`CPaneDialog::OnWindowPosChanging`|[WM_WINDOWPOSCHANGING](/windows/win32/winmsg/wm-windowposchanging)メッセージを処理します。 ( [CWnd:: OnWindowPosChanging](../../mfc/reference/cwnd-class.md#onwindowposchanging)を再定義します)。|
|[CPaneDialog::SetOccDialogInfo](#setoccdialoginfo)|OLE コントロールコンテナーであるダイアログボックスのテンプレートを指定します。|

## <a name="remarks"></a>Remarks

2つ`CPaneDialog`の手順でオブジェクトを構築します。 まず、コードでオブジェクトを構築します。 次に、 [Cて dialog:: Create](#create)を呼び出します。 有効なリソーステンプレート名またはテンプレート ID を指定し、親ウィンドウへのポインターを渡す必要があります。 それ以外の場合、作成プロセスは失敗します。 ダイアログボックスでは、WS_CHILD および WS_VISIBLE スタイルを指定する必要があります。 また、WS_CLIPCHILDREN スタイルと WS_CLIPSIBLINGS スタイルも指定することをお勧めします。 詳細については、「[ウィンドウスタイル](styles-used-by-mfc.md#window-styles)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

[CPaneDialog](../../mfc/reference/cpanedialog-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxpanedialog

##  <a name="create"></a>  CPaneDialog::Create

ドッキングダイアログボックスを作成し、 `CPaneDialog`オブジェクトにアタッチします。

```
BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID,
    DWORD dwTabbedStyle= AFX_CBRS_REGULAR_TABS,
    DWORD dwControlBarStyle=AFX_DEFAULT_DOCKING_PANE_STYLE);

BOOL Create(
    LPCTSTR lpszWindowName,
    CWnd* pParentWnd,
    BOOL bHasGripper,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    LPCTSTR lpszTemplateName,
    UINT nStyle,
    UINT nID);

BOOL Create(
    CWnd* pParentWnd,
    UINT nIDTemplate,
    UINT nStyle,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*lpszWindowName*<br/>
からドッキングダイアログボックスの名前。

*pParentWnd*<br/>
から親ウィンドウをポイントします。

*bHasGripper*<br/>
からキャプション (グリップ) を使用してドッキングダイアログボックスを作成する場合は TRUE。それ以外の場合は FALSE。

*lpszTemplateName*<br/>
からリソースダイアログテンプレートの名前。

*nStyle*<br/>
からWindows スタイル。

*nID*<br/>
からコントロール ID。

*nIDTemplate*<br/>
からダイアログテンプレートのリソース ID。

*dwTabbedStyle*<br/>
からユーザーが別のコントロールペインをこのコントロールペインのキャプションにドラッグしたときに生成される、タブ付きウィンドウのスタイル。 既定値は AFX_CBRS_REGULAR_TABS です。 詳細については、 [Cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)メソッドの「解説」を参照してください。

*dwControlBarStyle*<br/>
から追加のスタイル属性。 既定値は AFX_DEFAULT_DOCKING_PANE_STYLE です。 詳細については、 [Cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)メソッドの「解説」を参照してください。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

`CPaneDialog`クラスの`Create`メソッドを使用する方法を次の例に示します。 この例は、 [Set Pane Size サンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_SetPaneSize#2](../../mfc/reference/codesnippet/cpp/cpanedialog-class_1.h)]
[!code-cpp[NVC_MFC_SetPaneSize#3](../../mfc/reference/codesnippet/cpp/cpanedialog-class_2.cpp)]

##  <a name="handleinitdialog"></a>  CPaneDialog::HandleInitDialog

[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)メッセージを処理します。

```
afx_msg LRESULT HandleInitDialog(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>パラメーター

*wParam*<br/>
から既定のキーボードフォーカスを受け取るコントロールのハンドル。

*lParam*<br/>
から追加の初期化データを指定します。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。 さらに、TRUE は、 *wParam*パラメーターで指定されたコントロールにキーボードフォーカスを設定します。FALSE に設定すると、既定のキーボードフォーカスが設定されません。

### <a name="remarks"></a>Remarks

フレームワークは、このメソッドを使用して、コントロールを初期化し、ダイアログボックスの外観を設定します。 フレームワークは、ダイアログボックスを表示する前にこのメソッドを呼び出します。

##  <a name="setoccdialoginfo"></a>  CPaneDialog::SetOccDialogInfo

OLE コントロールコンテナーであるダイアログボックスのテンプレートを指定します。

```
virtual BOOL SetOccDialogInfo(_AFX_OCC_DIALOG_INFO* pOccDialogInfo);
```

### <a name="parameters"></a>パラメーター

*Poccの情報*<br/>
からダイアログボックスオブジェクトの作成に使用されるダイアログボックステンプレートへのポインター。 このパラメーターの値は、その後、 [COccManager:: CreateDlgControls](../../mfc/reference/coccmanager-class.md#createdlgcontrols)メソッドに渡されます。

### <a name="return-value"></a>戻り値

常に TRUE です。

### <a name="remarks"></a>Remarks

このメソッドは、OLE コントロールサイトと ActiveX コントロールを管理する[COccManager](../../mfc/reference/coccmanager-class.md)クラスをサポートしています。 _AFX_OCC_DIALOG_INFO 構造体は、afxocc ヘッダーファイルで定義されています。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane クラス](../../mfc/reference/cdockablepane-class.md)<br/>
[ウィンドウ スタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)
