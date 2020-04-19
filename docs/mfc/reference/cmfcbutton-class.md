---
title: CMFCButton クラス
ms.date: 08/28/2018
f1_keywords:
- CMFCButton
- AFXBUTTON/CMFCButton
- AFXBUTTON/CMFCButton::CleanUp
- AFXBUTTON/CMFCButton::EnableFullTextTooltip
- AFXBUTTON/CMFCButton::EnableMenuFont
- AFXBUTTON/CMFCButton::EnableWindowsTheming
- AFXBUTTON/CMFCButton::GetToolTipCtrl
- AFXBUTTON/CMFCButton::IsAutoCheck
- AFXBUTTON/CMFCButton::IsAutorepeatCommandMode
- AFXBUTTON/CMFCButton::IsCheckBox
- AFXBUTTON/CMFCButton::IsChecked
- AFXBUTTON/CMFCButton::IsHighlighted
- AFXBUTTON/CMFCButton::IsPressed
- AFXBUTTON/CMFCButton::IsPushed
- AFXBUTTON/CMFCButton::IsRadioButton
- AFXBUTTON/CMFCButton::IsWindowsThemingEnabled
- AFXBUTTON/CMFCButton::SetAutorepeatMode
- AFXBUTTON/CMFCButton::SetCheckedImage
- AFXBUTTON/CMFCButton::SetFaceColor
- AFXBUTTON/CMFCButton::SetImage
- AFXBUTTON/CMFCButton::SetMouseCursor
- AFXBUTTON/CMFCButton::SetMouseCursorHand
- AFXBUTTON/CMFCButton::SetStdImage
- AFXBUTTON/CMFCButton::SetTextColor
- AFXBUTTON/CMFCButton::SetTextHotColor
- AFXBUTTON/CMFCButton::SetTooltip
- AFXBUTTON/CMFCButton::SizeToContent
- AFXBUTTON/CMFCButton::OnDraw
- AFXBUTTON/CMFCButton::OnDrawBorder
- AFXBUTTON/CMFCButton::OnDrawFocusRect
- AFXBUTTON/CMFCButton::OnDrawText
- AFXBUTTON/CMFCButton::OnFillBackground
- AFXBUTTON/CMFCButton::SelectFont
- AFXBUTTON/CMFCButton::m_bDrawFocus
- AFXBUTTON/CMFCButton::m_bHighlightChecked
- AFXBUTTON/CMFCButton::m_bRightImage
- AFXBUTTON/CMFCButton::m_bTransparent
- AFXBUTTON/CMFCButton::m_nAlignStyle
- AFXBUTTON/CMFCButton::m_nFlatStyle
helpviewer_keywords:
- CMFCButton [MFC], CleanUp
- CMFCButton [MFC], EnableFullTextTooltip
- CMFCButton [MFC], EnableMenuFont
- CMFCButton [MFC], EnableWindowsTheming
- CMFCButton [MFC], GetToolTipCtrl
- CMFCButton [MFC], IsAutoCheck
- CMFCButton [MFC], IsAutorepeatCommandMode
- CMFCButton [MFC], IsCheckBox
- CMFCButton [MFC], IsChecked
- CMFCButton [MFC], IsHighlighted
- CMFCButton [MFC], IsPressed
- CMFCButton [MFC], IsPushed
- CMFCButton [MFC], IsRadioButton
- CMFCButton [MFC], IsWindowsThemingEnabled
- CMFCButton [MFC], SetAutorepeatMode
- CMFCButton [MFC], SetCheckedImage
- CMFCButton [MFC], SetFaceColor
- CMFCButton [MFC], SetImage
- CMFCButton [MFC], SetMouseCursor
- CMFCButton [MFC], SetMouseCursorHand
- CMFCButton [MFC], SetStdImage
- CMFCButton [MFC], SetTextColor
- CMFCButton [MFC], SetTextHotColor
- CMFCButton [MFC], SetTooltip
- CMFCButton [MFC], SizeToContent
- CMFCButton [MFC], OnDraw
- CMFCButton [MFC], OnDrawBorder
- CMFCButton [MFC], OnDrawFocusRect
- CMFCButton [MFC], OnDrawText
- CMFCButton [MFC], OnFillBackground
- CMFCButton [MFC], SelectFont
- CMFCButton [MFC], m_bDrawFocus
- CMFCButton [MFC], m_bHighlightChecked
- CMFCButton [MFC], m_bRightImage
- CMFCButton [MFC], m_bTransparent
- CMFCButton [MFC], m_nAlignStyle
- CMFCButton [MFC], m_nFlatStyle
ms.assetid: 4b32f57c-7a53-4734-afb9-d47e3359f62e
ms.openlocfilehash: 7628ac353d01c2a6853e35a35bd1f702d3bb041e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505862"
---
# <a name="cmfcbutton-class"></a>CMFCButton クラス

クラス`CMFCButton`は、ボタンテキストの配置、ボタンテキストとイメージの組み合わせ、カーソルの選択、ツールヒントの指定などの機能を、 [CButton](../../mfc/reference/cbutton-class.md)クラスに追加します。

## <a name="syntax"></a>構文

```
class CMFCButton : public CButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCButton::CMFCButton`|既定のコンストラクターです。|
|`CMFCButton::~CMFCButton`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCButton:: CleanUp](#cleanup)|内部変数をリセットし、イメージ、ビットマップ、アイコンなど、割り当てられたリソースを解放します。|
|`CMFCButton::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|`CMFCButton::DrawItem`|オーナー描画ボタンの外観が変更されたときにフレームワークによって呼び出されます。 ( [CButton::D rawItem](../../mfc/reference/cbutton-class.md#drawitem)をオーバーライドします)。|
|[CMFCButton::EnableFullTextTooltip](#enablefulltexttooltip)|ツールヒントのテキスト全体を大きなツールヒントウィンドウに表示するか、小さいツールヒントウィンドウ内のテキストの切り詰められたバージョンとして表示するかを指定します。|
|[CMFCButton:: EnableMenuFont](#enablemenufont)|ボタンテキストのフォントがアプリケーションのメニューフォントと同じかどうかを指定します。|
|[CMFCButton:: EnableWindowsTheming](#enablewindowstheming)|ボタンの境界線のスタイルが、現在の Windows テーマに対応するかどうかを指定します。|
|`CMFCButton::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|[CMFCButton:: GetToolTipCtrl](#gettooltipctrl)|基になるツールヒントコントロールへの参照を返します。|
|[CMFCButton::IsAutoCheck](#isautocheck)|チェックボックスまたはオプションボタンが自動ボタンかどうかを示します。|
|[CMFCButton::IsAutorepeatCommandMode](#isautorepeatcommandmode)|ボタンが自動繰り返しモードに設定されているかどうかを示します。|
|[CMFCButton:: IsCheckBox](#ischeckbox)|ボタンがチェックボックスボタンであるかどうかを示します。|
|[CMFCButton:: IsChecked](#ischecked)|現在のボタンがチェックされているかどうかを示します。|
|[CMFCButton:: IsHighlighted](#ishighlighted)|ボタンが強調表示されているかどうかを示します。|
|[CMFCButton:: IsPressed](#ispressed)|ボタンをプッシュして強調表示するかどうかを示します。|
|[CMFCButton:: Ispが Ed](#ispushed)|ボタンがプッシュされたかどうかを示します。|
|[CMFCButton:: IsRadioButton](#isradiobutton)|ボタンがオプションボタンかどうかを示します。|
|[CMFCButton::IsWindowsThemingEnabled](#iswindowsthemingenabled)|ボタンの境界線のスタイルが、現在の Windows テーマに対応するかどうかを示します。|
|`CMFCButton::OnDrawParentBackground`|指定した領域内のボタンの親の背景を描画します。 ( [AFX_GLOBAL_DATA::D rawParentBackground](../../mfc/reference/afx-global-data-structure.md)をオーバーライドします。|
|`CMFCButton::PreTranslateMessage`|[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)および[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)の Windows 関数にディスパッチされる前に、ウィンドウメッセージを変換します。 ( [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)をオーバーライドします)。|
|[CMFCButton:: SetAutorepeatMode](#setautorepeatmode)|ボタンを自動繰り返しモードに設定します。|
|[CMFCButton:: SetCheckedImage](#setcheckedimage)|チェックされたボタンのイメージを設定します。|
|[CMFCButton::SetFaceColor](#setfacecolor)|ボタンテキストの背景色を設定します。|
|[CMFCButton:: SetImage](#setimage)|ボタンのイメージを設定します。|
|[CMFCButton:: Setfromセキュリティー](#setmousecursor)|カーソルイメージを設定します。|
|[CMFCButton:: Setfromセキュリティー](#setmousecursorhand)|カーソルを手の形に設定します。|
|[CMFCButton:: SetStdImage](#setstdimage)|オブジェクトを`CMenuImages`使用して、ボタンイメージを設定します。|
|[CMFCButton:: SetTextColor](#settextcolor)|選択されていないボタンのボタンテキストの色を設定します。|
|[CMFCButton::SetTextHotColor](#settexthotcolor)|選択されているボタンのボタンテキストの色を設定します。|
|[CMFCButton:: SetTooltip](#settooltip)|ツールヒントをボタンに関連付けます。|
|[CMFCButton:: SizeToContent](#sizetocontent)|ボタンのテキストとイメージを含むようにボタンのサイズを変更します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCButton:: OnDraw](#ondraw)|ボタンを描画するためにフレームワークによって呼び出されます。|
|[CMFCButton::OnDrawBorder](#ondrawborder)|ボタンの境界線を描画するためにフレームワークによって呼び出されます。|
|[CMFCButton::OnDrawFocusRect](#ondrawfocusrect)|ボタンのフォーカスを示す四角形を描画するためにフレームワークによって呼び出されます。|
|[CMFCButton::OnDrawText](#ondrawtext)|ボタンのテキストを描画するためにフレームワークによって呼び出されます。|
|[CMFCButton:: OnFillBackground](#onfillbackground)|ボタンテキストの背景を描画するためにフレームワークによって呼び出されます。|
|[CMFCButton:: SelectFont](#selectfont)|指定したデバイスコンテキストに関連付けられているフォントを取得します。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CMFCButton:: m_nAlignStyle](#m_nalignstyle)|ボタンテキストの配置を指定します。|
|[CMFCButton:: m_bDontUseWinXPTheme](#m_bDontUseWinXPTheme)|Windows XP テーマを使用するかどうかを指定します。|
|[CMFCButton:: m_bDrawFocus](#m_bdrawfocus)|ボタンの周囲にフォーカスを示す四角形を描画するかどうかを示します。|
|[CMFCButton:: m_nFlatStyle](#m_nflatstyle)|ボタンのスタイルを指定します。たとえば、縁なし、フラット、半フラット、3D などです。|
|[CMFCButton:: m_bGrayDisabled](#m_bGrayDisabled)|TRUE の場合、無効になっているボタンを淡色表示で描画できます。|
|[CMFCButton:: m_bHighlightChecked](#m_bhighlightchecked)|カーソルがカーソルの上に置かれたときに、BS_CHECKBOX のボタンを強調表示するかどうかを示します。|
|[CMFCButton:: m_bResponseOnButtonDown](#m_bResponseOnButtonDown)|ボタンダウンイベントに応答するかどうかを示します。|
|[CMFCButton:: m_bRightImage](#m_brightimage)|ボタンの右側に画像を表示するかどうかを示します。|
|[CMFCButton:: m_bTopImage](#m_bTopImage)| 画像がボタンの上にあるかどうかを示します。|
|[CMFCButton:: m_bTransparent](#m_btransparent)|ボタンが透明であるかどうかを示します。|
|[CMFCButton::m_bWasDblClk](#m_bWasDblClk)| 最後のクリックイベントがダブルクリックであったかどうかを示します。|

## <a name="remarks"></a>Remarks

その他の種類のボタンは、 `CMFCButton` `CMFCColorButton`ハイパーリンクをサポートする[CMFCURLLinkButton](../../mfc/reference/cmfclinkctrl-class.md)クラスや、カラーピッカーダイアログボックスをサポートするクラスなどのクラスから派生します。

`CMFCButton`オブジェクトのスタイルには、 *3d*、*平面*、*半平面*、または*境界線なし*を使用できます。 ボタンのテキストは、ボタンの左側、上部、または中央に配置できます。 実行時に、ボタンがテキスト、画像、テキスト、画像のどれを表示するかを制御できます。 また、カーソルがボタンの上に置かれたときに、特定のカーソルイメージを表示するように指定することもできます。

ボタンコントロールを作成するには、コード内で直接作成するか、 **MFC クラスウィザード**ツールとダイアログボックステンプレートを使用します。 ボタンコントロールを直接作成する場合は、アプリケーション`CMFCButton`に変数を追加し、 `CMFCButton`オブジェクトのコンストラクターと`Create`メソッドを呼び出します。 **MFC クラスウィザード**を使用する場合は、アプリケーション`CButton`に変数を追加し、変数の型をから`CButton`に`CMFCButton`変更します。

ダイアログボックスアプリケーションで通知メッセージを処理するには、通知ごとにメッセージマップエントリとイベントハンドラーを追加します。 `CMFCButton`オブジェクトによって送信された通知は、 `CButton`オブジェクトによって送信された通知と同じです。

## <a name="example"></a>例

次の例では、 `CMFCButton`クラスのさまざまなメソッドを使用して、ボタンのプロパティを構成する方法を示します。 この例は、「[新しいコントロールのサンプル](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]
[!code-cpp[NVC_MFC_NewControls#32](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_3.cpp)]
[!code-cpp[NVC_MFC_NewControls#33](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_4.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxbutton

##  <a name="cleanup"></a>CMFCButton:: CleanUp

内部変数をリセットし、イメージ、ビットマップ、アイコンなど、割り当てられたリソースを解放します。

```
virtual void CleanUp();
```

##  <a name="enablefulltexttooltip"></a>  CMFCButton::EnableFullTextTooltip

ツールヒントのテキスト全体を大きなツールヒントウィンドウに表示するか、小さいツールヒントウィンドウ内のテキストの切り詰められたバージョンとして表示するかを指定します。

```
void EnableFullTextTooltip(BOOL bOn=TRUE);
```

### <a name="parameters"></a>パラメーター

*楽しい*<br/>
からすべてのテキストを表示する場合は TRUE。切り捨てられたテキストを表示する場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="enablemenufont"></a>  CMFCButton::EnableMenuFont

ボタンテキストのフォントがアプリケーションのメニューフォントと同じかどうかを指定します。

```
void EnableMenuFont(
    BOOL bOn=TRUE,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>パラメーター

*楽しい*<br/>
からアプリケーションのメニューフォントをボタンテキストのフォントとして使用する場合は TRUE。システムフォントを使用する場合は FALSE。 既定値は TRUE です。

*より描画*<br/>
から画面をすぐに再描画する場合は TRUE。それ以外の場合は FALSE。 既定値は TRUE です。

### <a name="remarks"></a>Remarks

このメソッドを使用してボタンテキストのフォントを指定しない場合は、 [CWnd:: SetFont](../../mfc/reference/cwnd-class.md#setfont)メソッドを使用してフォントを指定できます。 フォントをまったく指定しないと、フレームワークによって既定のフォントが設定されます。

##  <a name="enablewindowstheming"></a>  CMFCButton::EnableWindowsTheming

ボタンの境界線のスタイルが、現在の Windows テーマに対応するかどうかを指定します。

```
static void EnableWindowsTheming(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
から現在の Windows テーマを使用してボタンの境界線を描画する場合は TRUE。Windows のテーマを使用しない場合は FALSE。 既定値は TRUE です。

### <a name="remarks"></a>Remarks

このメソッドは、 `CMFCButton`クラスから派生したアプリケーションのすべてのボタンに影響します。

##  <a name="gettooltipctrl"></a>CMFCButton:: GetToolTipCtrl

基になるツールヒントコントロールへの参照を返します。

```
CToolTipCtrl& GetToolTipCtrl();
```

### <a name="return-value"></a>戻り値

基になるツールヒントコントロールへの参照。

### <a name="remarks"></a>Remarks

##  <a name="isautocheck"></a>  CMFCButton::IsAutoCheck

チェックボックスまたはオプションボタンが自動ボタンかどうかを示します。

```
BOOL IsAutoCheck() const;
```

### <a name="return-value"></a>戻り値

ボタンに style BS_AUTOCHECKBOX または BS_AUTORADIOBUTTON がある場合は TRUE を返します。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="isautorepeatcommandmode"></a>  CMFCButton::IsAutorepeatCommandMode

ボタンが自動繰り返しモードに設定されているかどうかを示します。

```
BOOL IsAutorepeatCommandMode() const;
```

### <a name="return-value"></a>戻り値

ボタンが自動繰り返しモードに設定されている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

[Cmfcbutton:: SetAutorepeatMode](#setautorepeatmode)メソッドを使用して、ボタンを自動繰り返しモードに設定します。

##  <a name="ischeckbox"></a>CMFCButton:: IsCheckBox

ボタンがチェックボックスボタンであるかどうかを示します。

```
BOOL IsCheckBox() const;
```

### <a name="return-value"></a>戻り値

ボタンが BS_CHECKBOX または BS_AUTOCHECKBOX style のいずれかである場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="ischecked"></a>  CMFCButton::IsChecked

現在のボタンがチェックされているかどうかを示します。

```
BOOL IsChecked() const;
```

### <a name="return-value"></a>戻り値

現在のボタンがオンになっている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

フレームワークでは、さまざまな種類のボタンがチェックされることを示すために、さまざまな方法を使用します。 たとえば、ドットが含まれている場合、ラジオボタンがチェックされます。**X**が含まれている場合、チェックボックスはオンになっています。

##  <a name="ishighlighted"></a>CMFCButton:: IsHighlighted

ボタンが強調表示されているかどうかを示します。

```
BOOL IsHighlighted() const;
```

### <a name="return-value"></a>戻り値

ボタンが強調表示されている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

マウスポインターをボタンの上に置くと、ボタンが強調表示されます。

##  <a name="ispressed"></a>CMFCButton:: IsPressed

ボタンをプッシュして強調表示するかどうかを示します。

```
BOOL IsPressed() const;
```

### <a name="return-value"></a>戻り値

ボタンが押された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="ispushed"></a>CMFCButton:: Ispが Ed

ボタンがプッシュされたかどうかを示します。

```
BOOL IsPushed() const;
```

### <a name="return-value"></a>戻り値

ボタンがプッシュされた場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="isradiobutton"></a>CMFCButton:: IsRadioButton

ボタンがオプションボタンかどうかを示します。

```
BOOL IsRadioButton() const;
```

### <a name="return-value"></a>戻り値

ボタンのスタイルが BS_RADIOBUTTON または BS_AUTORADIOBUTTON の場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="iswindowsthemingenabled"></a>  CMFCButton::IsWindowsThemingEnabled

ボタンの境界線のスタイルが、現在の Windows テーマに対応するかどうかを示します。

```
static BOOL IsWindowsThemingEnabled();
```

### <a name="return-value"></a>戻り値

ボタンの境界線のスタイルが現在の Windows テーマに対応する場合は TRUE。それ以外の場合は FALSE。

## <a name="a-namem_bdontusewinxptheme-cmfcbuttonm_bdontusewinxptheme"></a><a name="m_bDontUseWinXPTheme"/>CMFCButton:: m_bDontUseWinXPTheme

ボタンを描画するときに Windows XP のテーマを使用するかどうかを指定します。

```
BOOL m_bDontUseWinXPTheme;
```

##  <a name="m_bdrawfocus"></a>CMFCButton:: m_bDrawFocus

ボタンの周囲にフォーカスを示す四角形を描画するかどうかを示します。

```
BOOL m_bDrawFocus;
```

### <a name="remarks"></a>Remarks

ボタンが`m_bDrawFocus`フォーカスを受け取ると、フレームワークがボタンのテキストとイメージを囲むフォーカスを示す四角形を描画するように指定するには、メンバーを TRUE に設定します。

コンストラクター `CMFCButton`は、このメンバーを TRUE に初期化します。

##  <a name="m_bGrayDisabled"></a>CMFCButton:: m_bGrayDisabled

TRUE の場合、無効になっているボタンを淡色表示で描画できます。

```
BOOL m_bGrayDisabled;
```

##  <a name="m_bhighlightchecked"></a>CMFCButton:: m_bHighlightChecked

カーソルがカーソルの上に置かれたときに、BS_CHECKBOX のボタンを強調表示するかどうかを示します。

```
BOOL m_bHighlightChecked;
```

### <a name="remarks"></a>Remarks

`m_bHighlightChecked`メンバーを TRUE に設定すると、フレームワークは、マウスポインターを置いたときに BS_CHECKBOX のボタンを強調表示するように指定します。

##  <a name="m_bResponseOnButtonDown"></a>CMFCButton:: m_bResponseOnButtonDown

ボタンダウンイベントに応答するかどうかを示します。

```
BOOL m_bResponseOnButtonDown;
```

##  <a name="m_brightimage"></a>CMFCButton:: m_bRightImage

ボタンの右側に画像を表示するかどうかを示します。

```
BOOL m_bRightImage;
```

##  <a name="m_bTopImage"></a>CMFCButton:: m_bTopImage] (#m_bTopImage)

画像がボタンの上にあるかどうかを示します。

```
BOOL m_bTopImage;
```

### <a name="remarks"></a>Remarks

`m_bRightImage`メンバーを TRUE に設定すると、ボタンのテキストラベルの右側にボタンの画像が表示されるように指定できます。

##  <a name="m_btransparent"></a>CMFCButton:: m_bTransparent

ボタンが透明であるかどうかを示します。

```
BOOL m_bTransparent;
```

### <a name="remarks"></a>Remarks

フレームワークが`m_bTransparent`ボタンを透明にするように指定するには、メンバーを TRUE に設定します。 コンストラクター `CMFCButton`は、このメンバーを FALSE に初期化します。

##  <a name="m_nalignstyle"></a>CMFCButton:: m_nAlignStyle

ボタンテキストの配置を指定します。

```
AlignStyle m_nAlignStyle;
```

### <a name="remarks"></a>Remarks

次`CMFCButton::AlignStyle`の列挙値のいずれかを使用して、ボタンテキストの配置を指定します。

|[値]|説明|
|-----------|-----------------|
|ALIGN_CENTER|標準ボタンのテキストをボタンの中央に揃えます。|
|ALIGN_LEFT|ボタンのテキストをボタンの左側に揃えます。|
|ALIGN_RIGHT|ボタンのテキストをボタンの右側に揃えます。|

コンストラクター `CMFCButton`は、このメンバーを ALIGN_CENTER に初期化します。

##  <a name="m_bWasDblClk"></a>  CMFCButton::m_bWasDblClk](#m_bWasDblClk)|

最後のクリックイベントがダブルクリックであったかどうかを示します |。

```
BOOL m_bWasDblClk;
```

##  <a name="m_nflatstyle"></a>CMFCButton:: m_nFlatStyle

ボタンのスタイルを指定します。たとえば、縁なし、フラット、半フラット、3D などです。

```
FlatStyle  m_nFlatStyle;
```

### <a name="remarks"></a>Remarks

次の表に、 `CMFCButton::m_nFlatStyle`ボタンの外観を指定する列挙値の一覧を示します。

|[値]|説明|
|-----------|-----------------|
|BUTTONSTYLE_3D|標準このボタンには、高、3次元の辺が表示されます。 ボタンがクリックされると、ボタンがディープインデントに押されたように見えます。|
|BUTTONSTYLE_FLAT|マウスポインターをボタンの上に置いていない場合、ボタンは2次元で表示されます。 マウスポインターをボタンの上に置くと、ボタンの横が小さく、3次元で表示されます。 ボタンがクリックされると、ボタンが浅いインデントに押されたように見えます。|
|BUTTONSTYLE_SEMIFLAT|このボタンは、小さい3次元の辺を持つように見えます。 ボタンがクリックされると、ボタンがディープインデントに押されたように見えます。|
|BUTTONSTYLE_NOBORDERS|ボタンには、発生した辺はなく、常に2次元で表示されます。 ボタンがクリックされても、インデントに押されていないように見えます。|

コンストラクター `CMFCButton`は、このメンバーを BUTTONSTYLE_3D に初期化します。

### <a name="example"></a>例

`CMFCButton`クラスの`m_nFlatStyle`メンバー変数の値を設定する方法を次の例に示します。 この例は、「[新しいコントロールのサンプル](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#29](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_5.cpp)]

##  <a name="ondraw"></a>CMFCButton:: OnDraw

ボタンを描画するためにフレームワークによって呼び出されます。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

*rect*<br/>
からボタンの境界となる四角形への参照。

*uiState*<br/>
から現在のボタンの状態。 詳細については、 `itemState` [DRAWITEMSTRUCT 構造体](/windows/win32/api/winuser/ns-winuser-drawitemstruct)のメンバーに関するトピックを参照してください。

### <a name="remarks"></a>Remarks

独自のコードを使用してボタンを描画するには、このメソッドをオーバーライドします。

##  <a name="ondrawborder"></a>  CMFCButton::OnDrawBorder

ボタンの境界線を描画するためにフレームワークによって呼び出されます。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

*rectClient*<br/>
からボタンの境界となる四角形への参照。

*uiState*<br/>
から現在のボタンの状態。 詳細については、 `itemState` [DRAWITEMSTRUCT 構造体](/windows/win32/api/winuser/ns-winuser-drawitemstruct)のメンバーに関するトピックを参照してください。

### <a name="remarks"></a>Remarks

独自のコードを使用して境界線を描画するには、このメソッドをオーバーライドします。

##  <a name="ondrawfocusrect"></a>  CMFCButton::OnDrawFocusRect

ボタンのフォーカスを示す四角形を描画するためにフレームワークによって呼び出されます。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

*rectClient*<br/>
からボタンの境界となる四角形への参照。

### <a name="remarks"></a>Remarks

独自のコードを使用してフォーカスを示す四角形を描画するには、このメソッドをオーバーライドします。

##  <a name="ondrawtext"></a>CMFCButton:: OnDrawText

ボタンのテキストを描画するためにフレームワークによって呼び出されます。

```
virtual void OnDrawText(
    CDC* pDC,
    const CRect& rect,
    const CString& strText,
    UINT uiDTFlags,
    UINT uiState);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

*rect*<br/>
からボタンの境界となる四角形への参照。

*strText*<br/>
から描画するテキスト。

*uiDTFlags*<br/>
からテキストの書式設定方法を指定するフラグ。 詳細については、 [CDC::D rawText](../../mfc/reference/cdc-class.md#drawtext)メソッドの*nformat*パラメーターを参照してください。

*uiState*<br/>
[in] 予約されています。

### <a name="remarks"></a>Remarks

独自のコードを使用してボタンのテキストを描画するには、このメソッドをオーバーライドします。

##  <a name="onfillbackground"></a>CMFCButton:: OnFillBackground

ボタンテキストの背景を描画するためにフレームワークによって呼び出されます。

```
virtual void OnFillBackground(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

*rectClient*<br/>
からボタンの境界となる四角形への参照。

### <a name="remarks"></a>Remarks

独自のコードを使用してボタンの背景を描画するには、このメソッドをオーバーライドします。

##  <a name="selectfont"></a>  CMFCButton::SelectFont

指定したデバイスコンテキストに関連付けられているフォントを取得します。

```
virtual CFont* SelectFont(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

### <a name="return-value"></a>戻り値

独自のコードを使用してフォントを取得するには、このメソッドをオーバーライドします。

### <a name="remarks"></a>Remarks

##  <a name="setautorepeatmode"></a>CMFCButton:: SetAutorepeatMode

ボタンを自動繰り返しモードに設定します。

```
void SetAutorepeatMode(int nTimeDelay=500);
```

### <a name="parameters"></a>パラメーター

*nTimeDelay*<br/>
から親ウィンドウに送信されるメッセージの間隔を指定する負でない数値。 間隔はミリ秒単位で計測され、既定値は500ミリ秒です。 自動繰り返しメッセージモードを無効にするにはゼロを指定します。

### <a name="remarks"></a>Remarks

このメソッドを指定すると、ボタンが離されるか、 *Ntimedelay*パラメーターが0に設定されるまで、ボタンは常に WM_COMMAND メッセージを親ウィンドウに送信します。

##  <a name="setcheckedimage"></a>  CMFCButton::SetCheckedImage

チェックされたボタンのイメージを設定します。

```
void SetCheckedImage(
    HICON hIcon,
    BOOL bAutoDestroy=TRUE,
    HICON hIconHot=NULL,
    HICON hIconDisabled=NULL,
    BOOL bAlphaBlend=FALSE);

void SetCheckedImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy=TRUE,
    HBITMAP hBitmapHot=NULL,
    BOOL bMap3dColors=TRUE,
    HBITMAP hBitmapDisabled=NULL);

void SetCheckedImage(
    UINT uiBmpResId,
    UINT uiBmpHotResId=0,
    UINT uiBmpDsblResID=0);
```

### <a name="parameters"></a>パラメーター

*hIcon*<br/>
から新しいイメージのビットマップとマスクを含むアイコンへのハンドル。

*bAutoDestroy*<br/>
からビットマップリソースを自動的に破棄するように指定する場合は TRUE。それ以外の場合は FALSE。 既定値は TRUE です。

*hIconHot*<br/>
から選択された状態のイメージを含むアイコンへのハンドル。

*hBitmap*<br/>
から選択されていない状態のイメージを含むビットマップへのハンドル。

*hBitmapHot*<br/>
から選択された状態のイメージを含むビットマップへのハンドル。

*bMap3dColors*<br/>
からボタンの背景色を透明色として指定します。つまり、ボタンの表面です。 Color 値 RGB (192, 192, 192) を使用する場合は TRUE。によっ`AFX_GLOBAL_DATA::clrBtnFace`て定義された色の値を使用する場合は FALSE。

*uiBmpResId*<br/>
から選択されていないイメージのリソース ID。

*uiBmpHotResId*<br/>
から選択したイメージのリソース ID。

*hIconDisabled*<br/>
から無効なイメージのアイコンをハンドルします。

*hBitmapDisabled*<br/>
から無効なイメージを含むビットマップへのハンドル。

*uiBmpDsblResID*<br/>
から無効になっているビットマップのリソース ID。

*Phablend*<br/>
からアルファチャネルを使用する32ビットイメージのみを使用する場合は TRUE。アルファチャネルイメージのみを使用しない場合は FALSE。 既定値は FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="setfacecolor"></a>  CMFCButton::SetFaceColor

ボタンテキストの背景色を設定します。

```
void SetFaceColor(
    COLORREF crFace,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>パラメーター

*crFace*<br/>
からRGB カラー値。

*より描画*<br/>
から画面をすぐに再描画する場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドを使用して、ボタンの背景 (顔) の新しい塗りつぶしの色を定義します。 [Cmfcbutton:: m_bTransparent](#m_btransparent)メンバー変数が TRUE の場合、背景は塗りつぶされないことに注意してください。

##  <a name="setimage"></a>CMFCButton:: SetImage

ボタンのイメージを設定します。

```
void SetImage(
    HICON hIcon,
    BOOL bAutoDestroy=TRUE,
    HICON hIconHot=NULL,
    HICON hIconDisabled=NULL,
    BOOL bAlphaBlend=FALSE);

void SetImage(
    HBITMAP hBitmap,
    BOOL bAutoDestroy=TRUE,
    HBITMAP hBitmapHot=NULL,
    BOOL bMap3dColors=TRUE,
    HBITMAP hBitmapDisabled=NULL);

void SetImage(
    UINT uiBmpResId,
    UINT uiBmpHotResId=0,
    UINT uiBmpDsblResID=0);
```

### <a name="parameters"></a>パラメーター

*hIcon*<br/>
から新しいイメージのビットマップとマスクを含むアイコンへのハンドル。

*bAutoDestroy*<br/>
からビットマップリソースを自動的に破棄するように指定する場合は TRUE。それ以外の場合は FALSE。 既定値は TRUE です。

*hIconHot*<br/>
から選択された状態のイメージを含むアイコンへのハンドル。

*hBitmap*<br/>
から選択されていない状態のイメージを含むビットマップへのハンドル。

*hBitmapHot*<br/>
から選択された状態のイメージを含むビットマップへのハンドル。

*uiBmpResId*<br/>
から選択されていないイメージのリソース ID。

*uiBmpHotResId*<br/>
から選択したイメージのリソース ID。

*bMap3dColors*<br/>
からボタンの背景色を透明色として指定します。つまり、ボタンの表面です。 Color 値 RGB (192, 192, 192) を使用する場合は TRUE。によっ`AFX_GLOBAL_DATA::clrBtnFace`て定義された色の値を使用する場合は FALSE。

*hIconDisabled*<br/>
から無効なイメージのアイコンをハンドルします。

*hBitmapDisabled*<br/>
から無効なイメージを含むビットマップへのハンドル。

*uiBmpDsblResID*<br/>
から無効になっているビットマップのリソース ID。

*Phablend*<br/>
からアルファチャネルを使用する32ビットイメージのみを使用する場合は TRUE。アルファチャネルイメージのみを使用しない場合は FALSE。 既定値は FALSE です。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

`CMFCButton`クラスの`SetImage`メソッドのさまざまなバージョンを使用する方法を次の例に示します。 この例は、「[新しいコントロールのサンプル](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#31](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_2.cpp)]

##  <a name="setmousecursor"></a>CMFCButton:: Setfromセキュリティー

カーソルイメージを設定します。

```
void SetMouseCursor(HCURSOR hcursor);
```

### <a name="parameters"></a>パラメーター

*hcursor*<br/>
からカーソルのハンドル。

### <a name="remarks"></a>Remarks

このメソッドを使用して、カーソルイメージ (ハンドカーソルなど) をボタンに関連付けます。 カーソルはアプリケーションリソースから読み込まれます。

### <a name="example"></a>例

`CMFCButton`クラスの`SetMouseCursor`メソッドを使用する方法を次の例に示します。 この例は、「[新しいコントロールのサンプル](../../overview/visual-cpp-samples.md)」のコードの一部です。

[!code-cpp[NVC_MFC_NewControls#28](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#30](../../mfc/reference/codesnippet/cpp/cmfcbutton-class_6.cpp)]

##  <a name="setmousecursorhand"></a>CMFCButton:: Setfromセキュリティー

カーソルを手の形に設定します。

```
void SetMouseCursorHand();
```

### <a name="remarks"></a>Remarks

このメソッドを使用して、ハンドのカーソルイメージをボタンに関連付けます。 カーソルはアプリケーションリソースから読み込まれます。

##  <a name="setstdimage"></a>CMFCButton:: SetStdImage

オブジェクトを`CMenuImages`使用して、ボタンイメージを設定します。

```
void SetStdImage(
    CMenuImages::IMAGES_IDS id,
    CMenuImages::IMAGE_STATE state=CMenuImages::ImageBlack,
    CMenuImages::IMAGES_IDS idDisabled=(CMenuImages::IMAGES_IDS)0);
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
から`CMenuImage::IMAGES_IDS`列挙体で定義されているボタンイメージ識別子の1つ。 画像の値は、矢印、ピン、ラジオボタンなどの画像を指定します。

*state*<br/>
から`CMenuImages::IMAGE_STATE`列挙体で定義されているボタンイメージ状態識別子の1つ。 画像の状態では、黒、灰色、淡い灰色、白、濃い灰色などのボタンの色が指定されています。 既定値は `CMenuImages::ImageBlack` です。

*idDisabled*<br/>
から`CMenuImage::IMAGES_IDS`列挙体で定義されているボタンイメージ識別子の1つ。 この画像は、ボタンが無効になっていることを示しています。 既定値は、最初のボタンイメージ ( `CMenuImages::IdArrowDown`) です。

### <a name="remarks"></a>Remarks

##  <a name="settextcolor"></a>  CMFCButton::SetTextColor

選択されていないボタンのボタンテキストの色を設定します。

```
void SetTextColor(COLORREF clrText);
```

### <a name="parameters"></a>パラメーター

*clrText*<br/>
からRGB カラー値。

### <a name="remarks"></a>Remarks

##  <a name="settexthotcolor"></a>  CMFCButton::SetTextHotColor

選択されているボタンのボタンテキストの色を設定します。

```
void SetTextHotColor(COLORREF clrTextHot);
```

### <a name="parameters"></a>パラメーター

*clrTextHot*<br/>
からRGB カラー値。

### <a name="remarks"></a>Remarks

##  <a name="settooltip"></a>  CMFCButton::SetTooltip

ツールヒントをボタンに関連付けます。

```
void SetTooltip(LPCTSTR lpszToolTipText);
```

### <a name="parameters"></a>パラメーター

*lpszToolTipText*<br/>
からツールヒントのテキストへのポインター。 NULL を指定すると、ツールヒントが無効になります。

### <a name="remarks"></a>Remarks

##  <a name="sizetocontent"></a>CMFCButton:: SizeToContent

ボタンのテキストとイメージを含むようにボタンのサイズを変更します。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>パラメーター

*bCalcOnly*<br/>
からボタンの新しいサイズを計算しますが、変更しない場合は TRUE です。ボタンのサイズを変更する場合は FALSE。 既定値は FALSE です。

### <a name="return-value"></a>戻り値

ボタンの新しいサイズを格納しているオブジェクト。`CSize`

### <a name="remarks"></a>Remarks

既定では、このメソッドは、水平方向の余白が10ピクセル、垂直方向の余白が5ピクセルの新しいサイズを計算します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCLinkCtrl クラス](../../mfc/reference/cmfclinkctrl-class.md)<br/>
[CMFCColorButton クラス](../../mfc/reference/cmfccolorbutton-class.md)<br/>
[CMFCMenuButton クラス](../../mfc/reference/cmfcmenubutton-class.md)
