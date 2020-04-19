---
title: CMFCDropDownToolbarButton クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CMFCDropDownToolbarButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::CopyFrom
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::DropDownToolbar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::ExportToMenuButton
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::GetDropDownToolBar
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsDropDown
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::IsExtraSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCalculateSize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnChangeParentWnd
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClick
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnClickUp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnContextHelp
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnCustomizeMenu
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDraw
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::OnDrawOnCustomizeList
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::Serialize
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::SetDefaultCommand
- AFXDROPDOWNTOOLBAR/CMFCDropDownToolbarButton::m_uiShowBarDelay
helpviewer_keywords:
- CMFCDropDownToolbarButton [MFC], CMFCDropDownToolbarButton
- CMFCDropDownToolbarButton [MFC], CopyFrom
- CMFCDropDownToolbarButton [MFC], DropDownToolbar
- CMFCDropDownToolbarButton [MFC], ExportToMenuButton
- CMFCDropDownToolbarButton [MFC], GetDropDownToolBar
- CMFCDropDownToolbarButton [MFC], IsDropDown
- CMFCDropDownToolbarButton [MFC], IsExtraSize
- CMFCDropDownToolbarButton [MFC], OnCalculateSize
- CMFCDropDownToolbarButton [MFC], OnChangeParentWnd
- CMFCDropDownToolbarButton [MFC], OnClick
- CMFCDropDownToolbarButton [MFC], OnClickUp
- CMFCDropDownToolbarButton [MFC], OnContextHelp
- CMFCDropDownToolbarButton [MFC], OnCustomizeMenu
- CMFCDropDownToolbarButton [MFC], OnDraw
- CMFCDropDownToolbarButton [MFC], OnDrawOnCustomizeList
- CMFCDropDownToolbarButton [MFC], Serialize
- CMFCDropDownToolbarButton [MFC], SetDefaultCommand
- CMFCDropDownToolbarButton [MFC], m_uiShowBarDelay
ms.assetid: bc9d69e6-bd3e-4c15-9368-e80a504a0ba7
ms.openlocfilehash: fcfb521e309463da81d0064451297b3b73610d2f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505329"
---
# <a name="cmfcdropdowntoolbarbutton-class"></a>CMFCDropDownToolbarButton クラス

ツール バー ボタンの一種で、クリックされたときは標準ボタンと同じように動作します。 ただし、ユーザーがツールバーボタンを押したままにしている場合は、ドロップダウンツールバー ( [Cmfcdropdowntoolbar クラス](../../mfc/reference/cmfcdropdowntoolbar-class.md)) が開きます。

## <a name="syntax"></a>構文

```
class CMFCDropDownToolbarButton : public CMFCToolBarButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCDropDownToolbarButton::CMFCDropDownToolbarButton](#cmfcdropdowntoolbarbutton)|`CMFCDropDownToolbarButton` オブジェクトを構築します。|
|`CMFCDropDownToolbarButton::~CMFCDropDownToolbarButton`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCDropDownToolbarButton:: CopyFrom](#copyfrom)|別のツールバーボタンのプロパティを現在のボタンにコピーします。 ( [CMFCToolBarButton:: CopyFrom を](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)オーバーライドします)。|
|`CMFCDropDownToolbarButton::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|[CMFCDropDownToolbarButton::D ropDownToolbar](#dropdowntoolbar)|ドロップダウンツールバーを開きます。|
|[CMFCDropDownToolbarButton:: ExportToMenuButton](#exporttomenubutton)|ツールバーボタンのテキストをメニューにコピーします。 ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)をオーバーライドします)。|
|[CMFCDropDownToolbarButton:: GetDropDownToolBar](#getdropdowntoolbar)|ボタンに関連付けられているドロップダウンツールバーを取得します。|
|`CMFCDropDownToolbarButton::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|[CMFCDropDownToolbarButton::IsDropDown](#isdropdown)|ドロップダウンツールバーが現在開いているかどうかを判断します。|
|[CMFCDropDownToolbarButton::IsExtraSize](#isextrasize)|拡張された境界線でボタンを表示できるかどうかを決定します。 ( [CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)をオーバーライドします。)|
|[CMFCDropDownToolbarButton:: On電卓 Atesize](#oncalculatesize)|指定されたデバイスコンテキストとドッキング状態のボタンのサイズを計算するために、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: On電卓 Atesize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)をオーバーライドします)。|
|`CMFCDropDownToolbarButton::OnCancelMode`|[WM_CANCELMODE](/windows/win32/winmsg/wm-cancelmode)メッセージを処理するためにフレームワークによって呼び出されます。 ( `CMCToolBarButton::OnCancelMode`をオーバーライドします)。|
|[CMFCDropDownToolbarButton::OnChangeParentWnd](#onchangeparentwnd)|新しいツールバーにボタンが挿入されたときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)をオーバーライドします。)|
|[CMFCDropDownToolbarButton:: OnClick](#onclick)|ユーザーがマウスボタンをクリックしたときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)をオーバーライドします)。|
|[CMFCDropDownToolbarButton::OnClickUp](#onclickup)|ユーザーがマウスボタンを離したときにフレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)をオーバーライドします。)|
|[CMFCDropDownToolbarButton::OnContextHelp](#oncontexthelp)|親ツールバーが WM_HELPHITTEST メッセージを処理するときに、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)をオーバーライドします。)|
|[CMFCDropDownToolbarButton:: Onカスタマイズ Emenu](#oncustomizemenu)|アプリケーションが親ツールバーにショートカットメニューを表示するときに、指定されたメニューを変更します。 ( [CMFCToolBarButton:: Onカスタマイズ Emenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)をオーバーライドします)。|
|[CMFCDropDownToolbarButton:: OnDraw](#ondraw)|指定されたスタイルとオプションを使用してボタンを描画するために、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnDraw](../../mfc/reference/cmfctoolbarbutton-class.md#ondraw)をオーバーライドします)。|
|[CMFCDropDownToolbarButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|**[カスタマイズ]** ダイアログボックスの **[コマンド]** ウィンドウにボタンを描画するために、フレームワークによって呼び出されます。 ( [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)をオーバーライドします。)|
|[CMFCDropDownToolbarButton:: Serialize](#serialize)|アーカイブからこのオブジェクトを読み取るか、アーカイブに書き込みます。 ( [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)をオーバーライドします)。|
|[CMFCDropDownToolbarButton:: SetDefaultCommand](#setdefaultcommand)|ユーザーがボタンをクリックしたときにフレームワークが使用する既定のコマンドを設定します。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CMFCDropDownToolbarButton::m_uiShowBarDelay](#m_uishowbardelay)|ドロップダウンツールバーが表示される前に、ユーザーがマウスボタンを押したままにする必要がある時間の長さを指定します。|

## <a name="remarks"></a>Remarks

は`CMFCDropDownToolBarButton` 、ボタンの右下隅に小さな矢印があるという点で、通常のボタンとは異なります。 ユーザーがドロップダウンツールバーからボタンを選択すると、フレームワークは最上位レベルのツールバーボタン (右下隅に小さな矢印が付いたボタン) にアイコンを表示します。

ドロップダウンツールバーを実装する方法の詳細については、「 [Cmfcdropdowntoolbar クラス](../../mfc/reference/cmfcdropdowntoolbar-class.md)」を参照してください。

オブジェクトを[cmfctoolbarmenubutton クラス](../../mfc/reference/cmfctoolbarmenubutton-class.md)オブジェクトにエクスポートし、ポップアップメニューを含むメニューボタンとして表示できます。 `CMFCDropDownToolBarButton`

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCDropDownToolbarButton](../../mfc/reference/cmfcdropdowntoolbarbutton-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdropdowntoolbar.h

##  <a name="copyfrom"></a>CMFCDropDownToolbarButton:: CopyFrom

別のツールバーボタンのプロパティを現在のボタンにコピーします。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
[in]コピー元のソースボタンへの参照。

### <a name="remarks"></a>Remarks

このツールバーボタンに別のツールバーボタンをコピーするには、このメソッドを呼び出します。 *src*の型`CMFCDropDownToolbarButton`はである必要があります。

##  <a name="cmfcdropdowntoolbarbutton"></a>CMFCDropDownToolbarButton::CMFCDropDownToolbarButton

`CMFCDropDownToolbarButton` オブジェクトを構築します。

```
CMFCDropDownToolbarButton();

CMFCDropDownToolbarButton(
    LPCTSTR lpszName,
    CMFCDropDownToolBar* pToolBar);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
からボタンの既定のテキスト。

*pToolBar*<br/>
からユーザーがボタンを`CMFCDropDownToolBar`押したときに表示されるオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

コンストラクターの2番目のオーバーロードは、 *Ptoolbar*が指定したツールバーの最初のボタンをドロップダウンボタンにコピーします。

通常、ドロップダウンツールバーボタンは、 *Ptoolbar*によって指定されたツールバーの、最近使用したボタンのテキストを使用します。 このメソッドは、ボタンがメニューボタンに変換されるか、または **[カスタマイズ]** ダイアログボックスの **[コマンド]** タブに表示されるときに、 *lpszname*で指定されたテキストを使用します。 **[ユーザー設定]** ダイアログボックスの詳細については、「 [Cmfctoolbarscustomizedialog クラス](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)」を参照してください。

### <a name="example"></a>例

`CMFCDropDownToolbarButton`クラスのオブジェクトを構築する方法を次の例に示します。 このコードスニペットは、 [Visual Studio のデモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_VisualStudioDemo#31](../../mfc/codesnippet/cpp/cmfcdropdowntoolbarbutton-class_1.cpp)]

##  <a name="dropdowntoolbar"></a>CMFCDropDownToolbarButton::D ropDownToolbar

ドロップダウンツールバーを開きます。

```
BOOL DropDownToolbar(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
からドロップダウンボックスの親ウィンドウ。または、ドロップダウンツールバーボタンの親ウィンドウを使用する場合は NULL。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

[CMFCDropDownToolbarButton:: OnClick](#onclick)メソッドは、このメソッドを呼び出して、ユーザーがツールバーボタンを押したときにドロップダウンツールバーを開きます。

このメソッドは、 [Cmfcdropdownframe:: Create](../../mfc/reference/cmfcdropdownframe-class.md#create)メソッドを使用して、ドロップダウンツールバーを作成します。 親ツールバーが垂直方向にドッキングされている場合、このメソッドは、適合に応じて、親ツールバーの左側または右側にドロップダウンツールバーを配置します。 それ以外の場合、このメソッドは、親ツールバーの下にドロップダウンツールバーを配置します。

*PWnd*が NULL で、ドロップダウンツールバーボタンに親ウィンドウがない場合、このメソッドは失敗します。

##  <a name="exporttomenubutton"></a>  CMFCDropDownToolbarButton::ExportToMenuButton

ツールバーボタンのテキストをメニューにコピーします。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>パラメーター

*menuButton*<br/>
からターゲットメニューボタンへの参照。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は 0 以外。それ以外の場合は 0。

### <a name="remarks"></a>Remarks

このメソッドは、基本クラスの実装 ( [CMFCToolBarButton:: ExportToMenuButton](../../mfc/reference/cmfctoolbarbutton-class.md#exporttomenubutton)) を呼び出した後、このボタンの各ツールバーメニュー項目を含むポップアップメニューをターゲットメニューボタンに追加します。 このメソッドは、ポップアップメニューにサブメニューを追加しません。

親ツールバー、 `m_pToolBar`、が NULL の場合、または基底クラスの実装が FALSE を返す場合、このメソッドは失敗します。

##  <a name="getdropdowntoolbar"></a>CMFCDropDownToolbarButton:: GetDropDownToolBar

ボタンに関連付けられているドロップダウンツールバーを取得します。

```
CMFCToolBar* GetDropDownToolBar() const;
```

### <a name="return-value"></a>戻り値

ボタンに関連付けられているドロップダウンツールバー。

### <a name="remarks"></a>Remarks

このメソッドは、 `m_pToolBar`データメンバーを返します。

##  <a name="isdropdown"></a>  CMFCDropDownToolbarButton::IsDropDown

ドロップダウンツールバーが現在開いているかどうかを判断します。

```
BOOL IsDropDown() const;
```

### <a name="return-value"></a>戻り値

ドロップダウンツールバーが現在開いている場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

[CMFCDropDownToolbarButton::D ropdowntoolbar](#dropdowntoolbar)メソッドを使用して、フレームワークによってドロップダウンツールバーが開きます。 ドロップダウンツールバーの非クライアント領域でマウスの左ボタンを押すと、フレームワークによってドロップダウンツールバーが閉じます。

##  <a name="isextrasize"></a>CMFCDropDownToolbarButton::IsExtraSize

拡張された境界線でボタンを表示できるかどうかを決定します。

```
virtual BOOL IsExtraSize() const;
```

### <a name="return-value"></a>戻り値

拡張境界線を使用してツールバーボタンを表示できる場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

拡張境界線の詳細については、「 [CMFCToolBarButton:: IsExtraSize](../../mfc/reference/cmfctoolbarbutton-class.md#isextrasize)」を参照してください。

##  <a name="m_uishowbardelay"></a>CMFCDropDownToolbarButton::m_uiShowBarDelay

ドロップダウンツールバーが表示される前に、ユーザーがマウスボタンを押したままにする必要がある時間の長さを指定します。

```
static UINT m_uiShowBarDelay;
```

### <a name="remarks"></a>Remarks

遅延時間はミリ秒単位で計測されます。 既定値は 500 です。 この共有データメンバーの値を変更することで、別の遅延を設定できます。

##  <a name="oncalculatesize"></a>CMFCDropDownToolbarButton:: On電卓 Atesize

指定されたデバイスコンテキストとドッキング状態のボタンのサイズを計算するために、フレームワークによって呼び出されます。

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からボタンを表示するデバイスコンテキスト。

*既定値の設定*<br/>
からボタンの既定のサイズ。

*bHorz*<br/>
から親ツールバーのドッキング状態。 このパラメーターは、ツールバーが水平方向にドッキングされている場合、またはフローティング状態の場合は TRUE、ツールバーが垂直方向にドッキングされている場合は FALSE です。

### <a name="return-value"></a>戻り値

ボタンの大きさをピクセル単位で格納する構造体。`SIZE`

### <a name="remarks"></a>Remarks

このメソッドは、ボタンサイズの水平方向の寸法にドロップダウン矢印の幅を追加することによって、基本クラスの実装 ( [CMFCToolBarButton:: On電卓 Atesize](../../mfc/reference/cmfctoolbarbutton-class.md#oncalculatesize)) を拡張します。

##  <a name="onchangeparentwnd"></a>CMFCDropDownToolbarButton::OnChangeParentWnd

新しいツールバーにボタンが挿入されたときにフレームワークによって呼び出されます。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
から新しい親ウィンドウ。

### <a name="remarks"></a>Remarks

このメソッドは、テキストラベル ( [CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)) をクリアし、 [CMFCToolBarButton:: m_bText](../../mfc/reference/cmfctoolbarbutton-class.md#m_btext)および CMFCToolBarButton を設定することによって、基底クラスの実装 ( [CMFCToolBarButton:: OnChangeParentWnd](../../mfc/reference/cmfctoolbarbutton-class.md#onchangeparentwnd)) をオーバーライドします。 [:: m_bUserButton](../../mfc/reference/cmfctoolbarbutton-class.md#m_buserbutton)データメンバーを FALSE にします。

##  <a name="onclick"></a>CMFCDropDownToolbarButton:: OnClick

ユーザーがマウスボタンをクリックしたときにフレームワークによって呼び出されます。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
からツールバーボタンの親ウィンドウ。

*bDelay*<br/>
からメッセージを遅延で処理する必要がある場合は TRUE。

### <a name="return-value"></a>戻り値

ボタンがクリックメッセージを処理する場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメソッドは、ドロップダウンツールバーの状態を更新することによって、基底クラスの実装である[CMFCToolBarButton:: OnClick](../../mfc/reference/cmfctoolbarbutton-class.md#onclick)を拡張します。

ユーザーがツールバーボタンをクリックすると、このメソッドは、 [CMFCDropDownToolbarButton:: m_uiShowBarDelay](#m_uishowbardelay)データメンバーによって指定された時間を待機し、CMFCDropDownToolbarButton を使用してドロップダウンツールバーを開くタイマーを作成します。 [::D ropDownToolbar](#dropdowntoolbar)メソッド。 このメソッドは、ユーザーがツールバーボタンをクリックしたときに、ドロップダウンツールバーを閉じます。

##  <a name="onclickup"></a>CMFCDropDownToolbarButton::OnClickUp

ユーザーがマウスボタンを離したときにフレームワークによって呼び出されます。

```
virtual BOOL OnClickUp();
```

### <a name="return-value"></a>戻り値

ボタンがクリックメッセージを処理する場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメソッドは、ドロップダウンツールバーの状態を更新することによって、基底クラスの実装である[CMFCToolBarButton:: OnClickUp](../../mfc/reference/cmfctoolbarbutton-class.md#onclickup)を拡張します。

このメソッドは、アクティブな場合、ドロップダウンツールバータイマーを停止します。 ドロップダウンツールバーが開いている場合は閉じます。

ドロップダウンツールバーとドロップダウンツールバーのタイマーの詳細については、「 [CMFCDropDownToolbarButton:: OnClick](#onclick)」を参照してください。

##  <a name="oncontexthelp"></a>CMFCDropDownToolbarButton::OnContextHelp

親ツールバーが WM_HELPHITTEST メッセージを処理するときに、フレームワークによって呼び出されます。

```
virtual BOOL OnContextHelp(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
からツールバーボタンの親ウィンドウ。

### <a name="return-value"></a>戻り値

ボタンがヘルプメッセージを処理する場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメソッドは、 *Bdelay*を FALSE に設定して[CMFCDropDownToolbarButton:: OnClick](#onclick)メソッドを呼び出すことによって、基底クラスの実装 ( [CMFCToolBarButton:: OnContextHelp](../../mfc/reference/cmfctoolbarbutton-class.md#oncontexthelp)) を拡張します。 このメソッドは、 [CMFCDropDownToolbarButton:: OnClick](#onclick)によって返される値を返します。

WM_HELPHITTEST メッセージの詳細については、 [テクニカルノート28を参照してください。状況依存のヘルプの](../../mfc/tn028-context-sensitive-help-support.md)サポート。

##  <a name="oncustomizemenu"></a>CMFCDropDownToolbarButton:: Onカスタマイズ Emenu

アプリケーションが親ツールバーにショートカットメニューを表示するときに、指定されたメニューを変更します。

```
virtual BOOL OnCustomizeMenu(CMenu* pMenu);
```

### <a name="parameters"></a>パラメーター

*pMenu*<br/>
からカスタマイズするメニュー。

### <a name="return-value"></a>戻り値

このメソッドは TRUE を返します。

### <a name="remarks"></a>Remarks

このメソッドは、次のメニュー項目を無効にすることによって、基本クラスの実装 ( [CMFCToolBarButton:: Onカスタマイズ Emenu](../../mfc/reference/cmfctoolbarbutton-class.md#oncustomizemenu)) を拡張します。

- **ボタンイメージのコピー**

- **ボタンの外観**

- **イメージ**

- **Text**

- **画像とテキスト**

フレームワークがカスタマイズモードで表示するショートカットメニューを変更するには、このメソッドをオーバーライドします。

##  <a name="ondraw"></a>CMFCDropDownToolbarButton:: OnDraw

指定されたスタイルとオプションを使用してボタンを描画するために、フレームワークによって呼び出されます。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からボタンを表示するデバイスコンテキスト。

*rect*<br/>
からボタンの外接する四角形。

*pImages*<br/>
からボタンに関連付けられているツールバーイメージのコレクション。

*bHorz*<br/>
から親ツールバーのドッキング状態。 このパラメーターは、ボタンが水平方向にドッキングされている場合は TRUE、ボタンが垂直方向にドッキングされている場合は FALSE です。

*Bカスタマイズの Emode*<br/>
からツールバーがカスタマイズモードであるかどうかを指定します。 このパラメーターは、ツールバーがカスタマイズモードの場合は TRUE、ツールバーがカスタマイズモードでない場合は FALSE です。

*bHighlight 表示*<br/>
からボタンを強調表示するかどうかを指定します。 このパラメーターは、ボタンが強調表示されている場合は TRUE、ボタンが強調表示されていない場合は FALSE になります。

*bDrawBorder*<br/>
からボタンの境界線を表示するかどうかを指定します。 このパラメーターは、ボタンの境界線を表示する場合は TRUE、ボタンの境界線を表示しない場合は FALSE になります。

*bGrayDisabledButtons*<br/>
から無効なボタンを網掛けするか、無効になっているイメージのコレクションを使用するかどうかを指定します。 このパラメーターは、無効にしたボタンを網掛けする場合に TRUE になり、無効になったイメージのコレクションをこのメソッドで使用する必要がある場合は FALSE になります。

### <a name="remarks"></a>Remarks

ツールバーボタンの描画をカスタマイズするには、このメソッドをオーバーライドします。

##  <a name="ondrawoncustomizelist"></a>CMFCDropDownToolbarButton::OnDrawOnCustomizeList

**[カスタマイズ]** ダイアログボックスの **[コマンド]** ウィンドウにボタンを描画するために、フレームワークによって呼び出されます。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からボタンを表示するデバイスコンテキスト。

*rect*<br/>
からボタンの外接する四角形。

*選択された bSelected*<br/>
からボタンが選択されているかどうか。 このパラメーターが TRUE の場合、ボタンが選択されます。 このパラメーターが FALSE の場合、ボタンは選択されません。

### <a name="return-value"></a>戻り値

指定したデバイスコンテキストのボタンの幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンがオーナー描画リストボックスに表示される必要がある場合に、カスタマイズ ダイアログボックス (**コマンド** タブ) によって呼び出されます。

このメソッドは、ボタンのテキストラベルをボタンの名前 (つまり、コンストラクターに渡された*lpszname*パラメーターの値) に変更することによって、基本クラスの実装 ( [CMFCToolBarButton:: OnDrawOnCustomizeList](../../mfc/reference/cmfctoolbarbutton-class.md#ondrawoncustomizelist)) を拡張します。).

##  <a name="serialize"></a>CMFCDropDownToolbarButton:: Serialize

アーカイブからこのオブジェクトを読み取るか、アーカイブに書き込みます。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>パラメーター

*金*<br/>
からまたはのシリアル化元のオブジェクト。`CArchive`

### <a name="remarks"></a>Remarks

このメソッドは、親ツールバーのリソース ID をシリアル化することによって、基本クラスの実装 ( [CMFCToolBarButton:: Serialize](../../mfc/reference/cmfctoolbarbutton-class.md#serialize)) を拡張します。 アーカイブが読み込まれるとき ( [CArchive:: isloading](../../mfc/reference/carchive-class.md#isloading)は0以外の値を返します) `m_pToolBar` 、このメソッドは、シリアル化されたリソース ID を含むツールバーにデータメンバーを設定します。

##  <a name="setdefaultcommand"></a>CMFCDropDownToolbarButton:: SetDefaultCommand

ユーザーがボタンをクリックしたときにフレームワークが使用する既定のコマンドを設定します。

```
void SetDefaultCommand(UINT uiCmd);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
から既定のコマンドの ID。

### <a name="remarks"></a>Remarks

ユーザーがボタンをクリックしたときにフレームワークが実行する既定のコマンドを指定するには、このメソッドを呼び出します。 *UiCmd*によって指定されたコマンド ID を持つ項目は、親のドロップダウンツールバーに配置する必要があります。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDropDownToolBar クラス](../../mfc/reference/cmfcdropdowntoolbar-class.md)<br/>
[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarMenuButton クラス](../../mfc/reference/cmfctoolbarmenubutton-class.md)<br/>
[チュートリアル: ツール バーへのコントロールの追加](../../mfc/walkthrough-putting-controls-on-toolbars.md)
