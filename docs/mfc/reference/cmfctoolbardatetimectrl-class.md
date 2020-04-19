---
title: CMFCToolBarDateTimeCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CanBeStretched
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::CopyFrom
- AFXTOOLBARDATETIMECTRL/CMFCToolBarButton::ExportToMenuButton
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetByCmd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetDateTimeCtrl
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetHwnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::GetTimeAll
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::HaveHotBorder
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::NotifyCommand
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnAddToCustomizePage
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnChangeParentWnd
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnClick
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnCtlColor
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnMove
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnShow
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::OnUpdateToolTip
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTime
- AFXTOOLBARDATETIMECTRL/CMFCToolBarDateTimeCtrl::SetTimeAll
helpviewer_keywords:
- CMFCToolBarDateTimeCtrl [MFC], CMFCToolBarDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], CanBeStretched
- CMFCToolBarDateTimeCtrl [MFC], CopyFrom
- CMFCToolBarButton [MFC], ExportToMenuButton
- CMFCToolBarDateTimeCtrl [MFC], GetByCmd
- CMFCToolBarDateTimeCtrl [MFC], GetDateTimeCtrl
- CMFCToolBarDateTimeCtrl [MFC], GetHwnd
- CMFCToolBarDateTimeCtrl [MFC], GetTime
- CMFCToolBarDateTimeCtrl [MFC], GetTimeAll
- CMFCToolBarDateTimeCtrl [MFC], HaveHotBorder
- CMFCToolBarDateTimeCtrl [MFC], NotifyCommand
- CMFCToolBarDateTimeCtrl [MFC], OnAddToCustomizePage
- CMFCToolBarDateTimeCtrl [MFC], OnChangeParentWnd
- CMFCToolBarDateTimeCtrl [MFC], OnClick
- CMFCToolBarDateTimeCtrl [MFC], OnCtlColor
- CMFCToolBarDateTimeCtrl [MFC], OnGlobalFontsChanged
- CMFCToolBarDateTimeCtrl [MFC], OnMove
- CMFCToolBarDateTimeCtrl [MFC], OnShow
- CMFCToolBarDateTimeCtrl [MFC], OnUpdateToolTip
- CMFCToolBarDateTimeCtrl [MFC], SetTime
- CMFCToolBarDateTimeCtrl [MFC], SetTimeAll
ms.assetid: a3853cb9-8ebc-444f-a1e4-9cf905e24c18
ms.openlocfilehash: 7ab6a240a403e70446ebc1860474f6cb9e1d71e3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504771"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl クラス

日付と時刻の選択コントロールを含むツールバーボタン。

## <a name="syntax"></a>構文

```
class CMFCToolBarDateTimeCtrl : public CMFCToolBarButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl](#cmfctoolbardatetimectrl)|`CMFCToolBarDateTimeCtrl` オブジェクトを構築します。|
|`CMFCToolBarDateTimeCtrl::~CMFCToolBarDateTimeCtrl`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCToolBarDateTimeCtrl:: CanBeStretched](#canbestretched)|カスタマイズ中にユーザーがボタンを引き伸ばすことができるかどうかを指定します。 ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)をオーバーライドします)。|
|[CMFCToolBarDateTimeCtrl:: CopyFrom](#copyfrom)|別のツールバーボタンのプロパティを現在のボタンにコピーします。 ( [CMFCToolBarButton:: CopyFrom を](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)オーバーライドします)。|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|将来使用するために予約されています。|
|[CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|ツールバーボタンのテキストをメニューにコピーします。|
|`CMFCToolBarDateTimeCtrl::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|[CMFCToolBarDateTimeCtrl:: GetByCmd](#getbycmd)|指定した`CMFCToolBarDateTimeCtrl`コマンド ID を持つ、アプリケーション内の最初のオブジェクトを取得します。|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|日付と時刻の選択コントロールへのポインターを返します。|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|ツールバーボタンに関連付けられているウィンドウハンドルを取得します。 ( [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)をオーバーライドします。)|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|[CMFCToolBarDateTimeCtrl:: GetTime](#gettime)|日付と時刻の選択コントロールから選択された時刻を取得し、指定した[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体に格納します。|
|[CMFCToolBarDateTimeCtrl:: GetTimeAll](#gettimeall)|指定されたコマンド ID を持つ選択された時刻を時間選択コントロールボタンから返します。|
|[CMFCToolBarDateTimeCtrl:: ホットボーダーを持つ](#havehotborder)|ユーザーがボタンを選択したときに、ボタンの境界線を表示するかどうかを決定します。 ( [CMFCToolBarButton:: は、ホットボーダー](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder)をオーバーライドします)。|
|[CMFCToolBarDateTimeCtrl:: NotifyCommand](#notifycommand)|ボタンが[WM_COMMAND](/windows/win32/menurc/wm-command)メッセージを処理するかどうかを指定します。 ( [CMFCToolBarButton:: NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)をオーバーライドします)。|
|[CMFCToolBarDateTimeCtrl:: OnAddToCustomizePage](#onaddtocustomizepage)|ボタンが **[カスタマイズ]** ダイアログボックスに追加されたときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)をオーバーライドします)。|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|指定されたデバイスコンテキストとドッキング状態のボタンのサイズを計算するために、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: On電卓 Atesize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)をオーバーライドします)。|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|新しいツールバーにボタンが挿入されたときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)をオーバーライドします。)|
|[CMFCToolBarDateTimeCtrl:: OnClick](#onclick)|ユーザーがコントロールをクリックすると、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)をオーバーライドします)。|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|親ツールバーが WM_CTLCOLOR メッセージを処理するときに、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)をオーバーライドします。)|
|`CMFCToolBarDateTimeCtrl::OnDraw`|指定されたスタイルとオプションを使用してボタンを描画するために、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)をオーバーライドします)。|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|**[カスタマイズ]** ダイアログボックスの **[コマンド]** ウィンドウにボタンを描画するために、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)をオーバーライドします。)|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|グローバルフォントが変更されたときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: Onglobalフォントの変更](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)をオーバーライドします)。|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|親ツールバーが移動したときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)をオーバーライドします。)|
|[CMFCToolBarDateTimeCtrl:: OnShow](#onshow)|ボタンが表示または非表示になったときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnShow を](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)オーバーライドします)。|
|`CMFCToolBarDateTimeCtrl::OnSize`|親ツールバーがサイズまたは位置を変更し、この変更によってボタンのサイズが変更されるときに、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)をオーバーライドします。)|
|[CMFCToolBarDateTimeCtrl:: OnUpdateToolTip](#onupdatetooltip)|親ツールバーがツールヒントテキストを更新するときに、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)をオーバーライドします)。|
|`CMFCToolBarDateTimeCtrl::Serialize`|このオブジェクトをアーカイブから読み取るか、アーカイブに書き込みます ( [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)をオーバーライドします)。|
|`CMFCToolBarDateTimeCtrl::SetStyle`|ツールバーボタンのスタイルを設定します。 ( [CMFCToolBarButton:: system.windows.forms.control.setstyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle)をオーバーライドします。)|
|[CMFCToolBarDateTimeCtrl:: SetTime](#settime)|タイムピッカーコントロールの日時を設定します。|
|[CMFCToolBarDateTimeCtrl:: SetTimeAll](#settimeall)|指定されたコマンド ID を持つ、時間選択コントロールのすべてのインスタンスの時刻と日付を設定します。|

## <a name="remarks"></a>Remarks

日付と時刻の選択コントロールを使用する方法の例については、ToolbarDateTimePicker サンプルプロジェクトを参照してください。 コントロールボタンをツールバーに追加する方法の詳細に[ついては、「チュートリアル:ツールバー](../../mfc/walkthrough-putting-controls-on-toolbars.md)にコントロールを配置する。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtoolbardatetimectrl

##  <a name="canbestretched"></a>CMFCToolBarDateTimeCtrl:: CanBeStretched

カスタマイズ中にユーザーがボタンを引き伸ばすことができるかどうかを指定します。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>戻り値

このメソッドは TRUE を返します。

### <a name="remarks"></a>Remarks

既定では、フレームワークでは、カスタマイズ時にツールバーボタンを拡張することをユーザーに許可しません。 このメソッドは、カスタマイズ中にユーザーが日付と時刻のツールバーボタンを拡張できるようにすることで、基本クラスの実装 ( [CMFCToolBarButton:: CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) を拡張します。

##  <a name="cmfctoolbardatetimectrl"></a>CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)オブジェクトを作成し、初期化します。

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>パラメーター

*uiID*<br/>
からコントロール ID。

*iImage*<br/>
からツールバーの`CMFCToolBarImages`オブジェクト内のイメージのインデックス。

*dwStyle*<br/>
からユーザーがボタンを`CMFCToolBarDateTimeCtrlImpl`クリックしたときに作成されるウィンドウのスタイル。

*iWidth*<br/>
からコントロールの幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

このオブジェクトは、システムの日付と時刻に初期化されます。 内部`CMFCToolBarDateTimeCtrlImpl`オブジェクトのウィンドウスタイルには、 *dwStyle*パラメーターと WS_CHILD スタイルおよび WS_VISIBLE スタイルが含まれています。 これらのスタイルは、を使用`CMFCToolBarDateTimeCtrl::SetStyle`して変更することはできません。 コントロールのスタイルを変更するには、を使用`SetStyle`します。 `CMFCToolBarDateTimeCtrl`

### <a name="example"></a>例

`CMFCToolBarDateTimeCtrl`クラスのオブジェクトを構築する方法を次の例に示します。 このコードスニペットは、[ツールバーの日付と時刻の選択のサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCToolBarDateTimeCtrl::CopyFrom

別のツールバーボタンのプロパティを現在のボタンにコピーします。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
[in]コピー元のソースボタンへの参照。

### <a name="remarks"></a>Remarks

このツールバーボタンに別のツールバーボタンをコピーするには、このメソッドを呼び出します。 *src*の型`CMFCToolBarDateTimeCtrl`はである必要があります。

##  <a name="exporttomenubutton"></a>CMFCToolBarDateTimeCtrl:: ExportToMenuButton

ツールバーボタンのテキストをメニューにコピーします。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>パラメーター

*menuButton*<br/>
からターゲットメニューボタンへの参照。

### <a name="return-value"></a>戻り値

このメソッドは TRUE を返します。

### <a name="remarks"></a>Remarks

このメソッドは、コントロールのコマンド ID に関連付けられている文字列リソースを読み込むことによって、基本クラスの実装 ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) をオーバーライドします。 文字列リソースの詳細については、「 [CStringT:: LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring)」を参照してください。

##  <a name="getbycmd"></a>CMFCToolBarDateTimeCtrl:: GetByCmd

指定した`CMFCToolBarDateTimeCtrl`コマンド ID を持つ、アプリケーション内の最初のオブジェクトを取得します。

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
から取得するボタンのコマンド ID。

### <a name="return-value"></a>戻り値

指定し`CMFCToolBarDateTimeCtrl`たコマンド id を持つアプリケーション内の最初のオブジェクト。指定した`CMFCToolBarDateTimeCtrl`コマンド id を持つオブジェクトがない場合は NULL。

### <a name="remarks"></a>Remarks

この共有ユーティリティメソッドは、 [CMFCToolBarDateTimeCtrl:: settimeall](#settimeall)や[CMFCToolBarDateTimeCtrl:: gettimeall](#gettimeall)などのメソッドによって使用され、指定されたコマンド ID を持つ、時間選択コントロールのすべてのインスタンスの日時を設定または取得します。

##  <a name="getdatetimectrl"></a>CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

日付と時刻の選択コントロールへのポインターを返します。

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>戻り値

日付と時刻の選択コントロールへのポインター。コントロールが存在しない場合は NULL。

### <a name="remarks"></a>Remarks

クラス`CMFCToolBarDateTimeCtrl`は、ツール`m_pWndDateTime`バーにオブジェクトを`CMFCToolBarDateTimeCtrl`挿入するときに、データメンバーを初期化します。

##  <a name="gethwnd"></a>CMFCToolBarDateTimeCtrl::GetHwnd

ツールバーボタンに関連付けられているウィンドウハンドルを取得します。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>戻り値

日付と時刻のツールバーボタンに関連付けられているウィンドウハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、 [CMFCToolBarButton:: GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)メソッドをオーバーライドします。

##  <a name="gettime"></a>CMFCToolBarDateTimeCtrl:: GetTime

関連付けられた日付と時刻の選択コントロールから選択された時刻を取得し、指定した[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体に格納します。

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>パラメーター

*timeDest*<br/>
入出力最初のオーバーロードでは、システム時刻情報を受け取る[COleDateTime クラス](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクト。 2番目のオーバーロードでは、システム時刻情報を受け取る[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクト。

*pTimeDest*<br/>
入出力システム時刻情報を受け取る[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。 NULL にすることはできません。

### <a name="return-value"></a>戻り値

最初のオーバーロードでは、時刻が[COleDateTime クラス](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトに正常に書き込まれた場合は0以外の。それ以外の場合は0です。 2番目と3番目のオーバーロードでは、戻り値は、 [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange)構造体で設定された dwflag メンバーと同じ DWORD です。

### <a name="remarks"></a>Remarks

メソッドは、日付と時刻の選択が日付と時刻に設定されているかどうかを示すために、 [NMDATETIMECHANGE](/windows/win32/api/commctrl/ns-commctrl-nmdatetimechange) structure メンバーの dwFlags を設定します。 値が GDT_NONE の場合、コントロールは status に`no date`設定され、DTS_SHOWNONE スタイルを使用します。 返される値が GDT_VALID の場合は、システム時刻がコピー先の場所に正常に格納されます。

##  <a name="gettimeall"></a>CMFCToolBarDateTimeCtrl:: GetTimeAll

指定されたコマンド ID を持つ、時間選択コントロールボタンからユーザーが選択した時間を返します。

```
static BOOL GetTimeAll(
    UINT uiCmd,
    COleDateTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    CTime& timeDest);

static DWORD GetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeDest);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からツールバーボタンのコマンド ID を指定します。

*timeDest*<br/>
入出力最初のオーバーロードでは、システム時刻情報を受け取る[COleDateTime クラス](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクト。 2番目のオーバーロードでは、システム時刻情報を受け取る[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクト。

*pTimeDest*<br/>
入出力システム時刻情報を受け取る[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。 NULL にすることはできません。

### <a name="return-value"></a>戻り値

フレームワークがコマンド ID *uiCmd*に一致するツールバーボタンを見つけることができない場合、最初のオーバーロードでは戻り値は0、他のオーバーロードでは GDT_NONE になります。 ツールバーのボタンが見つかった場合、戻り値はそのボタンの[CMFCToolBarDateTimeCtrl:: GetTime](#gettime)への呼び出しからの戻り値と同じになります。 戻り値の0または GDT_NONE は、ボタンが見つかったときに発生する可能性があります`GetTime` 。これは、の呼び出しが、他の何らかの理由で有効な日付を返さなかったことを示します。

### <a name="remarks"></a>Remarks

このメソッドは、指定されたコマンド ID を持つツールバーボタンを探し、そのボタンで[CMFCToolBarDateTimeCtrl:: GetTime](#gettime)メソッドを呼び出します。

##  <a name="havehotborder"></a>CMFCToolBarDateTimeCtrl:: ホットボーダーを持つ

ユーザーがボタンを選択したときに、ボタンの境界線を表示するかどうかを決定します。

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>戻り値

選択されたときにボタンの境界線が表示される場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメソッドは、コントロールが表示されている場合は0以外の値を返します。

##  <a name="notifycommand"></a>CMFCToolBarDateTimeCtrl:: NotifyCommand

ボタンが[WM_COMMAND](/windows/win32/menurc/wm-command)メッセージを処理するかどうかを指定します。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>パラメーター

*iNotifyCode*<br/>
からコマンドに関連付けられている通知メッセージ。

### <a name="return-value"></a>戻り値

ボタンが WM_COMMAND メッセージを処理する場合は TRUE。親ツールバーでメッセージを処理する必要があることを示す場合は FALSE。

### <a name="remarks"></a>Remarks

フレームワークは、親ウィンドウに[WM_COMMAND](/windows/win32/menurc/wm-command)メッセージを送信しようとしているときに、このメソッドを呼び出します。

このメソッドは、 [DTN_DATETIMECHANGE](/windows/win32/Controls/dtn-datetimechange)通知を処理することによって、基底クラスの実装 ( [CMFCToolBarButton:: notifycommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) を拡張します。 内部時間の状態を更新し、同じコマンド ID を持つ`CMFCToolBarDateTimeCtrl`すべてのオブジェクトの time プロパティを更新します。

##  <a name="onaddtocustomizepage"></a>CMFCToolBarDateTimeCtrl:: OnAddToCustomizePage

ボタンが **[カスタマイズ]** ダイアログボックスに追加されたときにフレームワークによって呼び出されます。

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Remarks

このメソッドは、このオブジェクトと同じコマンド ID を持つ任意のツールバーの最初の日付と時刻のコントロールからプロパティをコピーすることによって、基本クラスの実装である[CMFCToolBarButton:: OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)を拡張します。 このオブジェクトと同じコマンド ID を持つ日付と時刻のコントロールを持つツールバーがない場合、このメソッドは何も実行しません。

**[ユーザー設定]** ダイアログボックスの詳細については、「 [Cmfctoolbarscustomizedialog クラス](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)」を参照してください。

##  <a name="onchangeparentwnd"></a>CMFCToolBarDateTimeCtrl::OnChangeParentWnd

新しいツールバーにボタンが挿入されたときにフレームワークによって呼び出されます。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
から新しい親ウィンドウ。

### <a name="remarks"></a>Remarks

このメソッドは、内部`CMFCToolBarDateTimeCtrlImpl`オブジェクトを再作成することによって、基底クラスの実装 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) をオーバーライドします。

##  <a name="onclick"></a>CMFCToolBarDateTimeCtrl:: OnClick

ユーザーがコントロールをクリックすると、フレームワークによって呼び出されます。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
から未使用.

*bDelay*<br/>
から未使用.

### <a name="return-value"></a>戻り値

ボタンがクリックメッセージを処理する場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメソッドは、内部`CMFCToolBarDateTimeCtrlImpl`オブジェクトが表示されている場合に0以外の値を返すことによって、基底クラスの実装である[CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)をオーバーライドします。

##  <a name="onctlcolor"></a>  CMFCToolBarDateTimeCtrl::OnCtlColor

親ツールバーが WM_CTLCOLOR メッセージを処理するときに、フレームワークによって呼び出されます。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からボタンを表示するデバイスコンテキスト。

*nCtlColor*<br/>
から未使用.

### <a name="return-value"></a>戻り値

フレームワークがボタンの背景を描画するために使用するグローバルブラシへのハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、指定されたデバイスコンテキストのテキストと背景色をそれぞれグローバルテキストと背景色に設定することによって、基本クラスの実装である[CMFCToolBarButton:: OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)をオーバーライドします。

アプリケーションで使用できるグローバルオプションの詳細については、「 [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md)」を参照してください。

##  <a name="onglobalfontschanged"></a>  CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

グローバルフォントが変更されたときにフレームワークによって呼び出されます。

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Remarks

このメソッドは、コントロールのフォントをグローバルフォントのフォントに変更することによって、基本クラスの実装 ( [CMFCToolBarButton:: Onglobalfont-size changed](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) を拡張します。

アプリケーションで使用できるグローバルオプションの詳細については、「 [AFX_GLOBAL_DATA Structure](../../mfc/reference/afx-global-data-structure.md)」を参照してください。

##  <a name="onmove"></a>CMFCToolBarDateTimeCtrl::OnMove

親ツールバーが移動したときにフレームワークによって呼び出されます。

```
virtual void OnMove();
```

### <a name="remarks"></a>Remarks

このメソッドは、内部`CMFCToolBarDateTimeCtrlImpl`オブジェクトの位置を更新することによって、既定のクラス実装 ( [CMFCToolBarButton:: OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) をオーバーライドします。

##  <a name="onshow"></a>CMFCToolBarDateTimeCtrl:: OnShow

ボタンが表示または非表示になったときにフレームワークによって呼び出されます。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>パラメーター

*bShow*<br/>
からボタンを表示するかどうかを指定します。 このパラメーターが TRUE の場合は、ボタンが表示されます。 それ以外の場合、ボタンは表示されません。

### <a name="remarks"></a>Remarks

このメソッドは、 *bShow*が TRUE の場合にボタンを表示することによって、基底クラスの実装 ( [CMFCToolBarButton:: onshow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) を拡張します。 それ以外の場合、このメソッドはボタンを非表示にします。

##  <a name="onsize"></a>CMFCToolBarDateTimeCtrl:: OnSize

親ツールバーがサイズまたは位置を変更し、この変更によってボタンのサイズが変更されるときに、フレームワークによって呼び出されます。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>パラメーター

*iSize*<br/>
からボタンの新しい幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメソッドは、内部`CMFCToolBarDateTimeCtrlImpl`オブジェクトのサイズと位置を更新することによって、既定のクラス実装 ( [CMFCToolBarButton:: OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) をオーバーライドします。

##  <a name="onupdatetooltip"></a>CMFCToolBarDateTimeCtrl:: OnUpdateToolTip

親ツールバーがツールヒントテキストを更新するときに、フレームワークによって呼び出されます。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
から親ウィンドウ。

*iButtonIndex*<br/>
から親ボタンコレクション内のボタンの0から始まるインデックス。

*wndToolTip*<br/>
からツールヒントのテキストを表示するコントロール。

*str*<br/>
入出力更新されたツールヒントテキストを受け取るオブジェクト。`CString`

### <a name="return-value"></a>戻り値

メソッドがツールヒントテキストを更新する場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンに関連付けられているツールヒントテキストを表示することによって、基本クラスの実装 ( [CMFCToolBarButton:: OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip)) を拡張します。 ボタンが水平方向にドッキングされていない場合、このメソッドは何も実行せず、FALSE を返します。

##  <a name="settime"></a>  CMFCToolBarDateTimeCtrl::SetTime

タイムピッカーコントロールの日時を設定します。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>パラメーター

*timeNew*<br/>
から最初のバージョンでは、コントロールが設定される時刻を含む[COleDateTime クラス](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクトへの参照。 2番目のバージョンでは、コントロールが設定される時間を格納する[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへのポインター。

*pTimeNew*<br/>
からコントロールが設定される時刻を格納している[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

[Cdatetimectrl 使い方:: SetTime](../../mfc/reference/cdatetimectrl-class.md#settime)を呼び出すことによって、日時指定コントロールの時刻を設定します。

##  <a name="settimeall"></a>CMFCToolBarDateTimeCtrl:: SetTimeAll

指定されたコマンド ID を持つ、時間選択コントロールのすべてのインスタンスの時刻と日付を設定します。

```
static BOOL SetTimeAll(
    UINT uiCmd,
    const COleDateTime& timeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    const CTime* pTimeNew);

static BOOL SetTimeAll(
    UINT uiCmd,
    LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からツールバーボタンのコマンド ID を指定します。

*timeNew*<br/>
から最初のバージョンでは、コントロールが設定される時刻を含む[COleDateTime クラス](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクト。 2番目のバージョンでは、コントロールが設定される時間を格納する[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへのポインター。

*pTimeNew*<br/>
からコントロールが設定される時刻を格納している[SYSTEMTIME](/windows/win32/api/minwinbase/ns-minwinbase-systemtime)構造体へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

指定したコマンド ID のツールバーボタンを検索し、 [CMFCToolBarDateTimeCtrl:: SetTime](#settime)を呼び出すことにより、日付と時刻の選択コントロールに時刻を設定します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton クラス](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[チュートリアル: ツール バーへのコントロールの追加](../../mfc/walkthrough-putting-controls-on-toolbars.md)
