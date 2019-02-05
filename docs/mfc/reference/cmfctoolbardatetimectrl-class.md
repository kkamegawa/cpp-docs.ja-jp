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
ms.openlocfilehash: 1252f97a93e67348a00c9809e3f216d4ed63c4d8
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893680"
---
# <a name="cmfctoolbardatetimectrl-class"></a>CMFCToolBarDateTimeCtrl クラス

日付と時刻の選択コントロールを含むツール バー ボタン。

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
|[CMFCToolBarDateTimeCtrl::CanBeStretched](#canbestretched)|ユーザーがボタンをカスタマイズするときに拡張できるかどうかを指定します。 (上書き[CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched))。|
|[CMFCToolBarDateTimeCtrl::CopyFrom](#copyfrom)|現在のボタンには、別のツール バー ボタンのプロパティをコピーします。 (上書き[CMFCToolBarButton::CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom))。|
|`CMFCToolBarDateTimeCtrl::DuplicateData`|将来使用するために予約されています。|
|[CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)|ツール バー ボタンからメニューにテキストをコピーします。|
|`CMFCToolBarDateTimeCtrl::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|[CMFCToolBarDateTimeCtrl::GetByCmd](#getbycmd)|最初に取得`CMFCToolBarDateTimeCtrl`を指定したコマンド ID を持つアプリケーションでのオブジェクト|
|[CMFCToolBarDateTimeCtrl::GetDateTimeCtrl](#getdatetimectrl)|日付と時刻の選択コントロールへのポインターを返します。|
|[CMFCToolBarDateTimeCtrl::GetHwnd](#gethwnd)|ツール バー ボタンに関連付けられているウィンドウ ハンドルを取得します。 (上書き[CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd))。|
|`CMFCToolBarDateTimeCtrl::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|
|[CMFCToolBarDateTimeCtrl::GetTime](#gettime)|日付と時刻の選択コントロールから選択した時間を取得し、指定した[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)構造体。|
|[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)|指定したコマンド ID を持つ日時指定コントロールのボタンから選択した時間を返します。|
|[CMFCToolBarDateTimeCtrl::HaveHotBorder](#havehotborder)|ユーザーがボタンを選択したときに、ボタンの境界線を表示するかどうかを判断します。 (上書き[CMFCToolBarButton::HaveHotBorder](../../mfc/reference/cmfctoolbarbutton-class.md#havehotborder))。|
|[CMFCToolBarDateTimeCtrl::NotifyCommand](#notifycommand)|ボタンを処理するかどうかを指定します、 [WM_COMMAND](/windows/desktop/menurc/wm-command)メッセージ。 (上書き[CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand))。|
|[CMFCToolBarDateTimeCtrl::OnAddToCustomizePage](#onaddtocustomizepage)|ボタンが追加されたときに、フレームワークによって呼び出されます、**カスタマイズ** ダイアログ ボックス。 (上書き[CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage))。|
|`CMFCToolBarDateTimeCtrl::OnCalculateSize`|指定したデバイス コンテキストおよびドッキング状態のボタンのサイズを計算するためにフレームワークによって呼び出されます。 (上書き[CMFCToolBarButton::OnCalculateSize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize))。|
|[CMFCToolBarDateTimeCtrl::OnChangeParentWnd](#onchangeparentwnd)|新しいツールバーにボタンが挿入されたときに、フレームワークによって呼び出されます。 (上書き[CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd))。|
|[CMFCToolBarDateTimeCtrl::OnClick](#onclick)|ユーザー コントロールをクリックしたときに、フレームワークによって呼び出されます。 (上書き[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick))。|
|[CMFCToolBarDateTimeCtrl::OnCtlColor](#onctlcolor)|親ツールバー WM_CTLCOLOR メッセージを処理するときに、フレームワークによって呼び出されます。 (上書き[CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor))。|
|`CMFCToolBarDateTimeCtrl::OnDraw`|指定したスタイルとオプションを使用して、ボタンを描画するためにフレームワークによって呼び出されます。 (上書き[CMFCToolBarButton::OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw))。|
|`CMFCToolBarDateTimeCtrl::OnDrawOnCustomizeList`|ボタンを描画するためにフレームワークによって呼び出されます、**コマンド**のウィンドウ、**カスタマイズ** ダイアログ ボックス。 (上書き[CMFCToolBarButton::OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist))。|
|[CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged](#onglobalfontschanged)|グローバルのフォントが変更されたときに、フレームワークによって呼び出されます。 (上書き[CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged))。|
|[CMFCToolBarDateTimeCtrl::OnMove](#onmove)|親ツールバーを移動すると、フレームワークによって呼び出されます。 (上書き[CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove))。|
|[CMFCToolBarDateTimeCtrl::OnShow](#onshow)|フレームワークによって呼び出されます、ボタンが表示または非表示します。 (上書き[CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow))。|
|`CMFCToolBarDateTimeCtrl::OnSize`|親ツールバーのサイズが変更またはとサイズを変更するボタンの位置が変更されときに、フレームワークによって呼び出されます。 (上書き[CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize))。|
|[CMFCToolBarDateTimeCtrl::OnUpdateToolTip](#onupdatetooltip)|親ツールバーは、そのツールヒント テキストを更新するときに、フレームワークによって呼び出されます。 (上書き[CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip))。|
|`CMFCToolBarDateTimeCtrl::Serialize`|アーカイブからこのオブジェクトを読み取るか、アーカイブに書き込みます (オーバーライド[CMFCToolBarButton::Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize))。|
|`CMFCToolBarDateTimeCtrl::SetStyle`|ツール バー ボタンのスタイルを設定します。 (上書き[CMFCToolBarButton::SetStyle](../../mfc/reference/cmfctoolbarbutton-class.md#setstyle))。|
|[CMFCToolBarDateTimeCtrl::SetTime](#settime)|日時指定コントロールの日付と時刻を設定します。|
|[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)|日時指定コントロールの指定したコマンド ID を持つすべてのインスタンスでの日付と時刻を設定します。|

## <a name="remarks"></a>Remarks

日付と時刻の選択コントロールを使用する方法の例は、ToolbarDateTimePicker サンプル プロジェクトを参照してください。 ツールバーにコントロール ボタンを追加する方法については、次を参照してください。[チュートリアル。コントロールのツールバーに追加](../../mfc/walkthrough-putting-controls-on-toolbars.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtoolbardatetimectrl.h

##  <a name="canbestretched"></a>  CMFCToolBarDateTimeCtrl::CanBeStretched

ユーザーがボタンをカスタマイズするときに拡張できるかどうかを指定します。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>戻り値

このメソッドは、TRUE を返します。

### <a name="remarks"></a>Remarks

既定では、フレームワークにツール バー ボタンをカスタマイズするときに拡張するユーザーはできません。 このメソッドが基底クラスの実装を拡張 ( [CMFCToolBarButton::CanBeStretched](../../mfc/reference/cmfctoolbarbutton-class.md#canbestretched)) によって、ユーザーが日付と時刻のツール バー ボタンをカスタマイズするときに拡張できるようにします。

##  <a name="cmfctoolbardatetimectrl"></a>  CMFCToolBarDateTimeCtrl::CMFCToolBarDateTimeCtrl

作成し、初期化、 [CMFCToolBarDateTimeCtrl](../../mfc/reference/cmfctoolbardatetimectrl-class.md)オブジェクト。

```
CMFCToolBarDateTimeCtrl(
    UINT uiID,
    int iImage,
    DWORD dwStyle=0,
    int iWidth=0);
```

### <a name="parameters"></a>パラメーター

*uiID*<br/>
[in]コントロールの id。

*画像を*<br/>
[in]ツールバーのイメージのインデックス`CMFCToolBarImages`オブジェクト。

*dwStyle*<br/>
[in]スタイル、`CMFCToolBarDateTimeCtrlImpl`ユーザーがボタンをクリックして作成されたウィンドウ。

*iWidth*<br/>
[in]ピクセル単位で、コントロールの幅。

### <a name="remarks"></a>Remarks

このオブジェクトは、システムの日付と時刻に初期化されます。 内部のウィンドウ スタイル`CMFCToolBarDateTimeCtrlImpl`オブジェクトが含まれています、 *dwStyle*パラメーターと WS_CHILD と WS_VISIBLE スタイル。 使用してこれらのスタイルを変更することはできません`CMFCToolBarDateTimeCtrl::SetStyle`します。 使用`SetStyle`のスタイルを変更する、`CMFCToolBarDateTimeCtrl`コントロール。

### <a name="example"></a>例

次の例のオブジェクトを構築する方法、`CMFCToolBarDateTimeCtrl`クラス。 このコード スニペットの一部、[ツールバー日時指定サンプル](../../visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_ToolbarDateTimePicker#1](../../mfc/reference/codesnippet/cpp/cmfctoolbardatetimectrl-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCToolBarDateTimeCtrl::CopyFrom

現在のボタンには、別のツール バー ボタンのプロパティをコピーします。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
[in]コピー元のソースボタンへの参照。

### <a name="remarks"></a>Remarks

このツール バー ボタンに別のツール バー ボタンをコピーするには、このメソッドを呼び出します。 *src*型でなければなりません`CMFCToolBarDateTimeCtrl`します。

##  <a name="exporttomenubutton"></a>  CMFCToolBarDateTimeCtrl::ExportToMenuButton

ツール バー ボタンからメニューにテキストをコピーします。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>パラメーター

*メニュー ボタン*<br/>
[in]ターゲットのメニュー ボタンへの参照。

### <a name="return-value"></a>戻り値

このメソッドは、TRUE を返します。

### <a name="remarks"></a>Remarks

このメソッドは、基本クラスの実装 ( [CMFCToolBarButton::ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) をコントロールのコマンド ID に関連付けられている文字列リソースを読み込んでいます。 文字列リソースの詳細については、次を参照してください。 [CStringT::LoadString](../../atl-mfc-shared/reference/cstringt-class.md#loadstring)します。

##  <a name="getbycmd"></a>  CMFCToolBarDateTimeCtrl::GetByCmd

最初に取得`CMFCToolBarDateTimeCtrl`を指定したコマンド ID を持つアプリケーションでのオブジェクト

```
static CMFCToolBarDateTimeCtrl* __stdcall GetByCmd(UINT uiCmd);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
[in]取得するボタンのコマンド ID。

### <a name="return-value"></a>戻り値

最初の`CMFCToolBarDateTimeCtrl`をしない場合に、指定したコマンド ID、または NULL を持つアプリケーションでオブジェクト`CMFCToolBarDateTimeCtrl`オブジェクトは、指定したコマンド ID を持つ

### <a name="remarks"></a>Remarks

この共有ユーティリティ メソッドがなどのメソッドによって使用されます[CMFCToolBarDateTimeCtrl::SetTimeAll](#settimeall)と[CMFCToolBarDateTimeCtrl::GetTimeAll](#gettimeall)設定または時間のすべてのインスタンスの日付と時刻を取得するには指定したコマンド ID を持つピッカー コントロール

##  <a name="getdatetimectrl"></a>  CMFCToolBarDateTimeCtrl::GetDateTimeCtrl

日付と時刻の選択コントロールへのポインターを返します。

```
CDateTimeCtrl* GetDateTimeCtrl() const;
```

### <a name="return-value"></a>戻り値

日付と時刻の選択コントロールへのポインターまたは、コントロールが存在しない場合は NULL。

### <a name="remarks"></a>Remarks

`CMFCToolBarDateTimeCtrl`クラスを初期化します、`m_pWndDateTime`データ メンバーを挿入すると、`CMFCToolBarDateTimeCtrl`ツールバーにオブジェクト。

##  <a name="gethwnd"></a>  CMFCToolBarDateTimeCtrl::GetHwnd

ツール バー ボタンに関連付けられているウィンドウ ハンドルを取得します。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>戻り値

日付と時刻のツール バー ボタンに関連付けられているウィンドウ ハンドル。

### <a name="remarks"></a>Remarks

このメソッドは、 [CMFCToolBarButton::GetHwnd](../../mfc/reference/cmfctoolbarbutton-class.md#gethwnd)メソッド。

##  <a name="gettime"></a>  CMFCToolBarDateTimeCtrl::GetTime

関連付けられている日付と時刻の選択コントロールから選択した時間を取得し、指定した[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)構造体

```
BOOL GetTime(COleDateTime& timeDest) const;
DWORD GetTime(CTime& timeDest) const;
DWORD GetTime(LPSYSTEMTIME pTimeDest) const;
```

### <a name="parameters"></a>パラメーター

*timeDest*<br/>
[out]最初のオーバー ロードで、 [COleDateTime クラス](../../atl-mfc-shared/reference/coledatetime-class.md)システム時刻の情報を受け取るオブジェクト。 2 番目のオーバー ロードでは、 [CTime](../../atl-mfc-shared/reference/ctime-class.md)システム時刻の情報を受け取るオブジェクト。

*pTimeDest*<br/>
[out]ポインター、 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)システム時刻の情報を受け取る構造体。 NULL は指定できません。

### <a name="return-value"></a>戻り値

最初のオーバー ロードで、時間が正常に書き込む場合は 0 以外、 [COleDateTime クラス](../../atl-mfc-shared/reference/coledatetime-class.md)オブジェクト。 それ以外の場合、0。 2 番目と 3 番目のオーバー ロードで戻り値は DWORD で設定された dwFlag メンバーに等しい、[戻り](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange)構造体。

### <a name="remarks"></a>Remarks

メソッドのセット、[戻り](/windows/desktop/api/commctrl/ns-commctrl-tagnmdatetimechange)形式を日付と時刻の選択が、日付と時刻に設定されているかどうかを示します。 GDT_NONE の値が、コントロールに設定されます`no date`状態、DTS_SHOWNONE スタイルを使用するとします。 返される値には、戻りが達すると、システム時刻が正常に変換先の場所に格納されます。

##  <a name="gettimeall"></a>  CMFCToolBarDateTimeCtrl::GetTimeAll

指定したコマンド ID を持つ日時指定コントロールのボタンからユーザーが選択した時刻を返します

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
[in]ツール バー ボタンのコマンド ID を指定します

*timeDest*<br/>
[out]最初のオーバー ロードで、 [COleDateTime クラス](../../atl-mfc-shared/reference/coledatetime-class.md)システム時刻の情報を受け取るオブジェクト。 2 番目のオーバー ロードでは、 [CTime](../../atl-mfc-shared/reference/ctime-class.md)システム時刻の情報を受け取るオブジェクト。

*pTimeDest*<br/>
[out]ポインター、 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)システム時刻の情報を受け取る構造体。 NULL は指定できません。

### <a name="return-value"></a>戻り値

コマンド ID と一致するツールバー ボタンをフレームワークが見つからないかどうか*uiCmd*、戻り値には、最初のオーバー ロードで 0 と他のオーバー ロードで GDT_NONE します。 ツール バー ボタンが見つかった場合、戻り値への呼び出しからの戻り値と同じ[CMFCToolBarDateTimeCtrl::GetTime](#gettime)その ボタンをクリックします。 戻り値 0 または GDT_NONE は、ボタンが見つかったことを示す場合に発生する可能性が呼び出し`GetTime`何らかの理由で有効な日付が返されませんでした。

### <a name="remarks"></a>Remarks

このメソッドを呼び出し、指定したコマンド ID を持つツール バー ボタンを探します[CMFCToolBarDateTimeCtrl::GetTime](#gettime)ボタン メソッド。

##  <a name="havehotborder"></a>  CMFCToolBarDateTimeCtrl::HaveHotBorder

ユーザーがボタンを選択したときに、ボタンの境界線を表示するかどうかを判断します。

```
virtual BOOL HaveHotBorder() const;
```

### <a name="return-value"></a>戻り値

ボタン 0 以外の場合は、選択されたときの境界線を表示します。それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

このメソッドは、コントロールを表示する場合に 0 以外の値を返します。

##  <a name="notifycommand"></a>  CMFCToolBarDateTimeCtrl::NotifyCommand

ボタンを処理するかどうかを指定します、 [WM_COMMAND](/windows/desktop/menurc/wm-command)メッセージ。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>パラメーター

*iNotifyCode*<br/>
[in]コマンドに関連付けられている通知メッセージ。

### <a name="return-value"></a>戻り値

TRUE の場合、ボタンの処理、WM_COMMAND メッセージ、または FALSE を示す親ツールバーで、メッセージを処理する必要があります。

### <a name="remarks"></a>Remarks

送信しようとしてある場合に、フレームワークはこのメソッドを呼び出して、 [WM_COMMAND](/windows/desktop/menurc/wm-command)メッセージを親ウィンドウ。

このメソッドが基底クラスの実装を拡張 ( [CMFCToolBarButton::NotifyCommand](../../mfc/reference/cmfctoolbarbutton-class.md#notifycommand)) 処理することによって、 [DTN_DATETIMECHANGE](/windows/desktop/Controls/dtn-datetimechange)通知します。 内部の時間のステータスを更新し、時間のすべてのプロパティを更新`CMFCToolBarDateTimeCtrl`オブジェクトを同じコマンド ID

##  <a name="onaddtocustomizepage"></a>  CMFCToolBarDateTimeCtrl::OnAddToCustomizePage

ボタンが追加されたときに、フレームワークによって呼び出されます、**カスタマイズ** ダイアログ ボックス。

```
virtual void OnAddToCustomizePage();
```

### <a name="remarks"></a>Remarks

このメソッドが基底クラスの実装によって拡張[CMFCToolBarButton::OnAddToCustomizePage](../../mfc/reference/cmfctoolbarbutton-class.md#onaddtocustomizepage)での最初の日付からプロパティのコピーとコントロールをこのオブジェクトと同じコマンド ID を持つ任意のツールバーでの時刻します。 日付と時刻のコントロールで、このオブジェクトと同じコマンド ID を持つツールバーがない場合、このメソッドは何もはしません。

詳細については、**カスタマイズ**ダイアログ ボックスを参照してください[CMFCToolBarsCustomizeDialog クラス](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)します。

##  <a name="onchangeparentwnd"></a>  CMFCToolBarDateTimeCtrl::OnChangeParentWnd

新しいツールバーにボタンが挿入されたときに、フレームワークによって呼び出されます。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
[in]新しい親ウィンドウです。

### <a name="remarks"></a>Remarks

このメソッドは、基本クラスの実装 ( [CMFCToolBarButton::OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) 内部の再作成して`CMFCToolBarDateTimeCtrlImpl`オブジェクト。

##  <a name="onclick"></a>  CMFCToolBarDateTimeCtrl::OnClick

ユーザー コントロールをクリックしたときに、フレームワークによって呼び出されます。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>パラメーター

*我が物*<br/>
[in]使用されていません。

*bDelay*<br/>
[in]使用されていません。

### <a name="return-value"></a>戻り値

ボタンをクリックしてメッセージを処理する場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

このメソッドは基底クラスの実装をオーバーライド[CMFCToolBarButton::OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)場合に、0 以外の値を返すことによって、内部`CMFCToolBarDateTimeCtrlImpl`オブジェクトが表示されます。

##  <a name="onctlcolor"></a>  CMFCToolBarDateTimeCtrl::OnCtlColor

親ツールバー WM_CTLCOLOR メッセージを処理するときに、フレームワークによって呼び出されます。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]ボタンを表示するデバイス コンテキスト。

*nCtlColor*<br/>
[in]使用されていません。

### <a name="return-value"></a>戻り値

ボタンの背景を描画するために、フレームワークを使用するグローバル ブラシへのハンドル。

### <a name="remarks"></a>Remarks

このメソッドは基底クラスの実装をオーバーライド[CMFCToolBarButton::OnCtlColor](../../mfc/reference/cmfctoolbarbutton-class.md#onctlcolor)テキストを設定およびグローバルのテキストに指定されたデバイス コンテキストの色と背景の色をそれぞれバック グラウンドします。

アプリケーションに使用できるグローバル オプションの詳細については、次を参照してください。 [AFX_GLOBAL_DATA 構造体](../../mfc/reference/afx-global-data-structure.md)します。

##  <a name="onglobalfontschanged"></a>  CMFCToolBarDateTimeCtrl::OnGlobalFontsChanged

グローバルのフォントが変更されたときに、フレームワークによって呼び出されます。

```
virtual void OnGlobalFontsChanged();
```

### <a name="remarks"></a>Remarks

このメソッドが基底クラスの実装を拡張 ( [CMFCToolBarButton::OnGlobalFontsChanged](../../mfc/reference/cmfctoolbarbutton-class.md#onglobalfontschanged)) のグローバルのフォントのコントロールのフォントを変更することで。

アプリケーションに使用できるグローバル オプションの詳細については、次を参照してください。 [AFX_GLOBAL_DATA 構造体](../../mfc/reference/afx-global-data-structure.md)します。

##  <a name="onmove"></a>  CMFCToolBarDateTimeCtrl::OnMove

親ツールバーを移動すると、フレームワークによって呼び出されます。

```
virtual void OnMove();
```

### <a name="remarks"></a>Remarks

このメソッドは、既定のクラスの実装 ( [CMFCToolBarButton::OnMove](../../mfc/reference/cmfctoolbarbutton-class.md#onmove)) 内部の位置を更新して`CMFCToolBarDateTimeCtrlImpl`オブジェクト。

##  <a name="onshow"></a>  CMFCToolBarDateTimeCtrl::OnShow

フレームワークによって呼び出されます、ボタンが表示または非表示します。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>パラメーター

*bShow*<br/>
[in]ボタンが表示されているかどうかを指定します。 このパラメーターが TRUE の場合、ボタンが表示されます。 それ以外の場合、ボタンは表示されません。

### <a name="remarks"></a>Remarks

このメソッドが基底クラスの実装を拡張 ( [CMFCToolBarButton::OnShow](../../mfc/reference/cmfctoolbarbutton-class.md#onshow)) 場合、ボタンを表示することによって*bShow*は TRUE です。 それ以外の場合、このメソッドは、ボタンを非表示にします。

##  <a name="onsize"></a>  CMFCToolBarDateTimeCtrl::OnSize

親ツールバーのサイズが変更またはとサイズを変更するボタンの位置が変更されときに、フレームワークによって呼び出されます。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>パラメーター

*iSize*<br/>
[in]ピクセル単位で、ボタンの新しい幅。

### <a name="remarks"></a>Remarks

このメソッドは、既定のクラスの実装 ( [CMFCToolBarButton::OnSize](../../mfc/reference/cmfctoolbarbutton-class.md#onsize)) 内部の位置とサイズを更新して`CMFCToolBarDateTimeCtrlImpl`オブジェクト。

##  <a name="onupdatetooltip"></a>  CMFCToolBarDateTimeCtrl::OnUpdateToolTip

親ツールバーは、そのツールヒント テキストを更新するときに、フレームワークによって呼び出されます。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
[in]親ウィンドウ。

*iButtonIndex*<br/>
[in]親のボタン コレクション内のボタンの 0 から始まるインデックス。

*wndToolTip*<br/>
[in]ツールヒント テキストを表示するコントロール。

*str*<br/>
[out]A`CString`更新されたツールヒント テキストを受け取るオブジェクト。

### <a name="return-value"></a>戻り値

メソッドは、ツールヒントのテキストを更新する場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

このメソッドが基底クラスの実装を拡張 ( [CMFCToolBarButton::OnUpdateToolTip](../../mfc/reference/cmfctoolbarbutton-class.md#onupdatetooltip))、ボタンに関連付けられているツールヒント テキストを表示することで。 ボタンが水平方向にドッキングされていない場合、このメソッドは何も実行し、FALSE を返します。

##  <a name="settime"></a>  CMFCToolBarDateTimeCtrl::SetTime

日時指定コントロールの日付と時刻を設定します。

```
BOOL SetTime(const COleDateTime& timeNew);
BOOL SetTime(const CTime* timeNew);
BOOL SetTime(LPSYSTEMTIME pTimeNew=NULL);
```

### <a name="parameters"></a>パラメーター

*timeNew*<br/>
[in]最初のバージョンへの参照を[COleDateTime クラス](../../atl-mfc-shared/reference/coledatetime-class.md)コントロールを設定する時刻を表すオブジェクト。 2 番目のバージョンへのポインターで、 [CTime](../../atl-mfc-shared/reference/ctime-class.md)コントロールを設定する時刻を表すオブジェクト。

*pTimeNew*<br/>
[in]ポインター、 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)コントロールを設定する時刻を含む構造体。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

日付と時刻の選択コントロールで呼び出すことによって、時間を設定[CDateTimeCtrl::SetTime](../../mfc/reference/cdatetimectrl-class.md#settime)します。

##  <a name="settimeall"></a>  CMFCToolBarDateTimeCtrl::SetTimeAll

日時指定コントロールの指定したコマンド ID を持つすべてのインスタンスでの日付と時刻を設定します。

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
[in]ツール バー ボタンのコマンド ID を指定します

*timeNew*<br/>
[in]最初のバージョンで、 [COleDateTime クラス](../../atl-mfc-shared/reference/coledatetime-class.md)コントロールを設定する時刻を表すオブジェクト。 2 番目のバージョンへのポインターで、 [CTime](../../atl-mfc-shared/reference/ctime-class.md)コントロールを設定する時刻を表すオブジェクト。

*pTimeNew*<br/>
[in]ポインター、 [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)コントロールを設定する時刻を含む構造体。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

指定したコマンド ID を持つツール バー ボタンの外観し、時間を日付と時刻の選択コントロールで呼び出すことによって設定[CMFCToolBarDateTimeCtrl::SetTime](#settime)します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton クラス](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[チュートリアル: ツールバーのコントロールの追加](../../mfc/walkthrough-putting-controls-on-toolbars.md)

