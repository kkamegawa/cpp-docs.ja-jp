---
title: CMFCOutlookBarPane クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::AddButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::CanBeAttached
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::ClearAll
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::Create
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnablePageScrollMode
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::GetRegularColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsBackgroundTexture
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::IsDrawShadedHighlight
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveButton
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetBackImage
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetDefaultState
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetExtraSpace
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTextColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::SetTransparentColor
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::EnableContextMenuItems
- AFXOUTLOOKBARPANE/CMFCOutlookBarPane::RemoveAllButtons
helpviewer_keywords:
- CMFCOutlookBarPane [MFC], AddButton
- CMFCOutlookBarPane [MFC], CanBeAttached
- CMFCOutlookBarPane [MFC], ClearAll
- CMFCOutlookBarPane [MFC], Create
- CMFCOutlookBarPane [MFC], EnablePageScrollMode
- CMFCOutlookBarPane [MFC], GetRegularColor
- CMFCOutlookBarPane [MFC], IsBackgroundTexture
- CMFCOutlookBarPane [MFC], IsDrawShadedHighlight
- CMFCOutlookBarPane [MFC], RemoveButton
- CMFCOutlookBarPane [MFC], SetBackColor
- CMFCOutlookBarPane [MFC], SetBackImage
- CMFCOutlookBarPane [MFC], SetDefaultState
- CMFCOutlookBarPane [MFC], SetExtraSpace
- CMFCOutlookBarPane [MFC], SetTextColor
- CMFCOutlookBarPane [MFC], SetTransparentColor
- CMFCOutlookBarPane [MFC], EnableContextMenuItems
- CMFCOutlookBarPane [MFC], RemoveAllButtons
ms.assetid: 094e2ef3-a118-487e-a4cc-27626108fe08
ms.openlocfilehash: 9ef6a06a4889119e39e72a9e495e5d4f9e17cf56
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505161"
---
# <a name="cmfcoutlookbarpane-class"></a>CMFCOutlookBarPane クラス

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

Outlook バー ( [Cmfcoutlookbar クラス](../../mfc/reference/cmfcoutlookbar-class.md)) に挿入できる、 [cmfctoolbar クラス](../../mfc/reference/cmfctoolbar-class.md)から派生したコントロール。 Outlook バー ペインには、大きいボタンの列があります。 ボタンのリストがペインより長い場合、ユーザーはリストを上下にスクロールできます。 ユーザーが Outlook バー ペインを Outlook バーから切り離すと、そのペインをフローティング状態にするかメイン フレーム ウィンドウにドッキングできます。

## <a name="syntax"></a>構文

```
class CMFCOutlookBarPane : public CMFCToolBar
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCOutlookBarPane::CMFCOutlookBarPane`|既定のコンストラクターです。|
|`CMFCOutlookBarPane::~CMFCOutlookBarPane`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCOutlookBarPane:: AddButton](#addbutton)|Outlook バーペインにボタンを追加します。|
|[CMFCOutlookBarPane:: CanBeAttached](#canbeattached)|ペインを別のペインまたはフレームウィンドウにドッキングできるかどうかを決定します。 ( [Cbasepane:: CanBeAttached](../../mfc/reference/cbasepane-class.md#canbeattached)をオーバーライドします)。|
|`CMFCOutlookBarPane::CanBeRestored`|カスタマイズ後にツールバーを元の状態に戻すことができるかどうかを決定します。 ( [Cmfctoolbar:: CanBeRestored](../../mfc/reference/cmfctoolbar-class.md#canberestored)をオーバーライドします)。|
|[CMFCOutlookBarPane:: ClearAll](#clearall)|Outlook バーウィンドウのイメージによって使用されているリソースを解放します。|
|[CMFCOutlookBarPane:: Create](#create)|Outlook バーペインを作成します。|
|`CMFCOutlookBarPane::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|`CMFCOutlookBarPane::Dock`|Outlook バーペインをドッキングするためにフレームワークによって呼び出されます。 ( `CPane::Dock`をオーバーライドします)。|
|[CMFCOutlookBarPane::EnablePageScrollMode](#enablepagescrollmode)|Outlook バーペインのスクロール矢印がボタンの一覧をページごとに、またはボタンごとに進めるかどうかを指定します。|
|[CMFCOutlookBarPane:: GetRegularColor](#getregularcolor)|Outlook バーペインの標準 (選択されていない) テキストの色を返します。|
|`CMFCOutlookBarPane::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|[CMFCOutlookBarPane::IsBackgroundTexture](#isbackgroundtexture)|Outlook バーペインに背景画像が読み込まれているかどうかを判断します。|
|`CMFCOutlookBarPane::IsChangeState`|フローティングペインがドッキング可能かどうかを決定します。 ( `CPane::IsChangeState`をオーバーライドします)。|
|[CMFCOutlookBarPane:: IsDrawShadedHighlight](#isdrawshadedhighlight)|ボタンが強調表示され、背景イメージが表示されたときにボタンの境界線を影付きにするかどうかを決定します。|
|`CMFCOutlookBarPane::OnBeforeFloat`|ペインがフローティングしようとしているときに、フレームワークによって呼び出されます。 ( [CPane:: OnBeforeFloat](../../mfc/reference/cpane-class.md#onbeforefloat)をオーバーライドします。)|
|[CMFCOutlookBarPane:: RemoveButton](#removebutton)|指定したコマンド ID を持つボタンを削除します。|
|`CMFCOutlookBarPane::RestoreOriginalstate`|ツール バーを元の状態に戻します。 ( [Cmfctoolbar:: RestoreOriginalState](../../mfc/reference/cmfctoolbar-class.md#restoreoriginalstate)をオーバーライドします)。|
|[CMFCOutlookBarPane:: SetBackColor](#setbackcolor)|背景色を設定します。|
|[CMFCOutlookBarPane:: SetBackImage](#setbackimage)|背景イメージを設定します。|
|[CMFCOutlookBarPane:: SetDefaultState](#setdefaultstate)|Outlook バーペインを元のボタンのセットにリセットします。|
|[CMFCOutlookBarPane:: SetExtraSpace](#setextraspace)|Outlook バーペインのボタンの周囲で使用される余白のピクセル数を設定します。|
|[CMFCOutlookBarPane:: SetTextColor](#settextcolor)|Outlook バーペインで、標準および強調表示されているテキストの色を設定します。|
|[CMFCOutlookBarPane:: SetTransparentColor](#settransparentcolor)|Outlook バーペインの透明色を設定します。|
|`CMFCOutlookBarPane::SmartUpdate`|Outlook バーを更新するために内部的に使用されます。 ( `CMFCToolBar::SmartUpdate`をオーバーライドします)。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCOutlookBarPane:: EnableContextMenuItems](#enablecontextmenuitems)|カスタマイズモードで表示するショートカットメニュー項目を指定します。|
|[CMFCOutlookBarPane::RemoveAllButtons](#removeallbuttons)|Outlook バーペインからすべてのボタンを削除します。 ( [Cmfctoolbar:: RemoveAllButtons](../../mfc/reference/cmfctoolbar-class.md#removeallbuttons)をオーバーライドします)。|

## <a name="remarks"></a>Remarks

Outlook バーを実装する方法の詳細については、「 [Cmfcoutlookbar クラス](../../mfc/reference/cmfcoutlookbar-class.md)」を参照してください。

Outlook バーの例については、OutlookDemo サンプルプロジェクトを参照してください。

## <a name="example"></a>例

`CMFCOutlookBarPane`クラスのさまざまなメソッドを使用する方法を次の例に示します。 この例では、Outlook バーペインを作成する方法、ページスクロールモードを有効にする方法、ドッキングを有効にする方法、および Outlook バーの背景色を設定する方法を示します。 このコードスニペットは、 [Outlook マルチビューサンプル](../../overview/visual-cpp-samples.md)の一部です。

[!code-cpp[NVC_MFC_OutlookMultiViews#3](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_1.h)]
[!code-cpp[NVC_MFC_OutlookMultiViews#4](../../mfc/reference/codesnippet/cpp/cmfcoutlookbarpane-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCBaseToolBar](../../mfc/reference/cmfcbasetoolbar-class.md)

[CMFCToolBar](../../mfc/reference/cmfctoolbar-class.md)

[CMFCOutlookBarPane](../../mfc/reference/cmfcoutlookbarpane-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxoutlookbarpane

##  <a name="addbutton"></a>CMFCOutlookBarPane:: AddButton

Outlook バーペインにボタンを追加します。

```
BOOL AddButton(
    UINT uiImage,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    UINT uiImage,
    UINT uiLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    LPCTSTR szBmpFileName,
    LPCTSTR szLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HBITMAP hBmp,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1);

BOOL AddButton(
    HICON hIcon,
    LPCTSTR lpszLabel,
    UINT iIdCommand,
    int iInsertAt=-1,
    BOOL bAlphaBlend=FALSE);
```

### <a name="parameters"></a>パラメーター

*uiImage*<br/>
からビットマップのリソース識別子を指定します。

*lpszLabel*<br/>
からボタンのテキストを指定します。

*iIdCommand*<br/>
からボタンコントロールの ID を指定します。

*iInsertAt*<br/>
からボタンを挿入する outlook バーのページの0から始まるインデックスを指定します。

*uiLabel*<br/>
から文字列リソース ID。

*szBmpFileName*<br/>
から読み込むディスクイメージファイルの名前を指定します。

*szLabel*<br/>
からボタンのテキストを指定します。

*hBmp*<br/>
からボタンのビットマップを処理するハンドル。

*hIcon*<br/>
からボタンのアイコンを示すハンドル。

### <a name="return-value"></a>戻り値

ボタンが正常に追加された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

Outlook バーのページに新しいボタンを挿入するには、このメソッドを使用します。 ボタンのイメージは、アプリケーションリソースから、またはディスクファイルから読み込むことができます。

*UiPageID*によって指定されたページ ID が-1 の場合、ボタンは最初のページに挿入されます。

*IInsertAt*によって指定されたインデックスが-1 の場合、ボタンはページの最後に追加されます。

##  <a name="canbeattached"></a>CMFCOutlookBarPane:: CanBeAttached

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

```
virtual BOOL CanBeAttached() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="clearall"></a>CMFCOutlookBarPane:: ClearAll

Outlook バーウィンドウのイメージによって使用されているリソースを解放します。

```
void ClearAll();
```

### <a name="remarks"></a>Remarks

このメソッドは、Outlook バーペインで使用されるイメージに対して呼び出される[Cmfctoolbarimages:: Clear](../../mfc/reference/cmfctoolbarimages-class.md#clear)を直接呼び出します。

##  <a name="create"></a>CMFCOutlookBarPane:: Create

Outlook バーペインを作成します。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=AFX_DEFAULT_TOOLBAR_STYLE,
    UINT uiID=(UINT)-1,
    DWORD dwControlBarStyle=0);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
からOutlook バーペインコントロールの親ウィンドウを指定します。 NULL にすることはできません。

*dwStyle*<br/>
からウィンドウスタイル。  ウィンドウスタイルの一覧については、「[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)」を参照してください。

*uiID*<br/>
からコントロール ID。 コントロールの状態を保存できるようにするには、一意である必要があります。

*dwControlBarStyle*<br/>
からOutlook バーから切断されたときの Outlook バーペインコントロールの動作を定義する特殊なスタイルを指定します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

`CMFCOutlookBarPane`オブジェクトを構築するには、まずコンストラクターを呼び出し、次`Create`にを呼び出します。これにより、Outlook バーペインコントロール`CMFCOutlookBarPane`が作成され、オブジェクトにアタッチされます。

詳細`dwControlBarStyle`については、「 [cbasepane:: CreateEx](../../mfc/reference/cbasepane-class.md#createex)」を参照してください。

##  <a name="enablecontextmenuitems"></a>CMFCOutlookBarPane:: EnableContextMenuItems

カスタマイズモードで表示するショートカットメニュー項目を指定します。

```
virtual BOOL EnableContextMenuItems(
    CMFCToolBarButton* pButton,
    CMenu* pPopup);
```

### <a name="parameters"></a>パラメーター

*pButton*<br/>
からユーザーがクリックしたツールバーボタンへのポインター。

*pPopup*<br/>
からショートカットメニューへのポインター。

### <a name="return-value"></a>戻り値

ショートカットメニューを表示する必要がある場合は TRUE を返します。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

フレームワークによってカスタマイズモードで表示されるフレームワークの標準のショートカットメニューを変更するには、このメソッドをオーバーライドします。

既定の実装はカスタマイズモード ( [Cmfctoolbar:: Iscustomization emode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)) を確認し、TRUE に設定されている場合は、 **[削除]** を除くすべてのショートカットメニュー項目を無効にします。 次に、入力パラメーターをに`CMFCToolBar::EnableContextMenuItems`渡します。

> [!NOTE]
> *コンテキストメニュー*は、ショートカットメニューのシノニムです。

##  <a name="enablepagescrollmode"></a>  CMFCOutlookBarPane::EnablePageScrollMode

Outlook バーペインのスクロールバーの矢印がページごとにボタンの一覧を表示するかボタンをクリックするかを指定します。

```
void EnablePageScrollMode(BOOL bPageScroll=TRUE);
```

### <a name="parameters"></a>パラメーター

*bPageScroll*<br/>
からTRUE の場合は、ページのスクロールモードを有効にします。 FALSE の場合は、ページのスクロールモードを無効にします。

##  <a name="getregularcolor"></a>CMFCOutlookBarPane:: GetRegularColor

Outlook バーペインの標準 (つまり、選択されていない) テキストの色を返します。

```
DECLARE_MESSAGE_MAPCOLORREF GetRegularColor() const;
```

### <a name="return-value"></a>戻り値

現在のテキストの色を RGB カラー値として指定します。

### <a name="remarks"></a>Remarks

[Cmfcoutlookbarpane:: SetTextColor](#settextcolor)を使用して、Outlook バーの現在の (標準および選択されている) テキストの色を設定します。 COLOR_WINDOW インデックスを使用して[Getsyscolor](/windows/win32/api/winuser/nf-winuser-getsyscolor)関数を呼び出すと、既定のテキストの色を取得できます。

##  <a name="isbackgroundtexture"></a>  CMFCOutlookBarPane::IsBackgroundTexture

Outlook バーペインに背景画像が読み込まれているかどうかを判断します。

```
BOOL IsBackgroundTexture() const;
```

### <a name="return-value"></a>戻り値

表示する背景イメージが存在する場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

[Cmfcoutlookbarpane:: SetBackImage](#setbackimage)関数を呼び出すことで、背景画像を追加できます。

背景画像がない場合は、 [Cmfcoutlookbarpane:: SetBackColor](#setbackcolor)を使用して指定された色で背景が描画されます。

##  <a name="isdrawshadedhighlight"></a>CMFCOutlookBarPane:: IsDrawShadedHighlight

ボタンが強調表示され、背景イメージが表示されたときにボタンの境界線を影付きにするかどうかを決定します。

```
BOOL IsDrawShadedHighlight() const;
```

### <a name="return-value"></a>戻り値

ボタンの境界線が網掛けされている場合は TRUE。それ以外の場合は FALSE。

##  <a name="removeallbuttons"></a>  CMFCOutlookBarPane::RemoveAllButtons

Outlook バーペインからすべてのボタンを削除します。

```
virtual void RemoveAllButtons();
```

##  <a name="removebutton"></a>  CMFCOutlookBarPane::RemoveButton

指定したコマンド ID を持つボタンを削除します。

```
BOOL RemoveButton(UINT iIdCommand);
```

### <a name="parameters"></a>パラメーター

*iIdCommand*<br/>
から削除するボタンのコマンド ID を指定します。

### <a name="return-value"></a>戻り値

ボタンが正常に削除された場合は TRUE。指定されたコマンド ID が有効でない場合は FALSE。

##  <a name="setbackcolor"></a>CMFCOutlookBarPane:: SetBackColor

Outlook バーの背景色を設定します。

```
void SetBackColor(COLORREF color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
から新しい背景色を指定します。

### <a name="remarks"></a>Remarks

Outlook バーの現在の背景色を設定するには、この関数を呼び出します。 背景色は、背景画像がない場合にのみ使用されます。

##  <a name="setbackimage"></a>CMFCOutlookBarPane:: SetBackImage

背景イメージを設定します。

```
void SetBackImage(UINT uiImageID);
```

### <a name="parameters"></a>パラメーター

*uiImageID*<br/>
からイメージリソース ID を指定します。

### <a name="remarks"></a>Remarks

Outlook バーの背景画像を設定するには、このメソッドを呼び出します。 背景イメージの一覧は、埋め込み[Cmfctoolbarimages クラス](../../mfc/reference/cmfctoolbarimages-class.md)オブジェクトによって管理されます。

##  <a name="setdefaultstate"></a>CMFCOutlookBarPane:: SetDefaultState

Outlook バーペインを元のボタンのセットにリセットします。

```
void SetDefaultState();
```

### <a name="remarks"></a>Remarks

このメソッドは、Outlook バーボタンを元のセットに復元します。 このメソッドはと`CMFCOutlookBarPane::RestoreOriginalstate`似ていますが、Outlook バーペインの再描画をトリガーしない点が異なります。

##  <a name="setextraspace"></a>CMFCOutlookBarPane:: SetExtraSpace

Outlook バーペインのボタンの周囲で使用される余白のピクセル数を設定します。

```
void SetExtraSpace()
```

##  <a name="settextcolor"></a>  CMFCOutlookBarPane::SetTextColor

Outlook バーペインで、標準および強調表示されているテキストの色を設定します。

```
void SetTextColor(
    COLORREF clrRegText,
    COLORREF clrSelText=0);
```

### <a name="parameters"></a>パラメーター

*clrRegText*<br/>
から選択されていないテキストの新しい色を指定します。

*clrSelText*<br/>
から選択したテキストの新しい色を指定します。

##  <a name="settransparentcolor"></a>  CMFCOutlookBarPane::SetTransparentColor

Outlook バーペインの透明色を設定します。

```
void SetTransparentColor(COLORREF color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
新しい透明色を指定します。

### <a name="remarks"></a>Remarks

透明な画像を表示するには、透明色が必要です。 画像内でこの色が発生した場合は、代わりに背景色で塗りつぶされます。  背景画像と前景イメージはブレンドされません。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCOutlookBar クラス](../../mfc/reference/cmfcoutlookbar-class.md)<br/>
[CMFCOutlookBarTabCtrl クラス](../../mfc/reference/cmfcoutlookbartabctrl-class.md)
