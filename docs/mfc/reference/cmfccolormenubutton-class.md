---
title: CMFCColorMenuButton クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CMFCColorMenuButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableAutomaticButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableDocumentColors
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableOtherButton
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::EnableTearOff
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetAutomaticColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::GetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnChangeParentWnd
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OpenColorDialog
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColor
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorByCmdID
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColorName
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::SetColumnsNumber
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CopyFrom
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::CreatePopupMenu
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::IsEmptyMenuAllowed
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDraw
- AFXCOLORMENUBUTTON/CMFCColorMenuButton::OnDrawOnCustomizeList
helpviewer_keywords:
- CMFCColorMenuButton [MFC], CMFCColorMenuButton
- CMFCColorMenuButton [MFC], EnableAutomaticButton
- CMFCColorMenuButton [MFC], EnableDocumentColors
- CMFCColorMenuButton [MFC], EnableOtherButton
- CMFCColorMenuButton [MFC], EnableTearOff
- CMFCColorMenuButton [MFC], GetAutomaticColor
- CMFCColorMenuButton [MFC], GetColor
- CMFCColorMenuButton [MFC], GetColorByCmdID
- CMFCColorMenuButton [MFC], OnChangeParentWnd
- CMFCColorMenuButton [MFC], OpenColorDialog
- CMFCColorMenuButton [MFC], SetColor
- CMFCColorMenuButton [MFC], SetColorByCmdID
- CMFCColorMenuButton [MFC], SetColorName
- CMFCColorMenuButton [MFC], SetColumnsNumber
- CMFCColorMenuButton [MFC], CopyFrom
- CMFCColorMenuButton [MFC], CreatePopupMenu
- CMFCColorMenuButton [MFC], IsEmptyMenuAllowed
- CMFCColorMenuButton [MFC], OnDraw
- CMFCColorMenuButton [MFC], OnDrawOnCustomizeList
ms.assetid: 42685704-e994-4f7b-9553-62283c27b754
ms.openlocfilehash: 5fccfbca9fe8c31070f3eb9f208c09cb3722b9b9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403725"
---
# <a name="cmfccolormenubutton-class"></a>CMFCColorMenuButton クラス

`CMFCColorMenuButton`メニュー コマンドまたはツール バー ボタンの色の選択 ダイアログ ボックスを起動するクラスをサポートしています。

## <a name="syntax"></a>構文

```
class CMFCColorMenuButton : public CMFCToolBarMenuButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCColorMenuButton::CMFCColorMenuButton](#cmfccolormenubutton)|`CMFCColorMenuButton` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)|有効にし、通常の色のボタンの上に配置された「自動」のボタンを無効にします。 (標準のシステムの自動ボタンのラベルは**自動**)。|
|[CMFCColorMenuButton::EnableDocumentColors](#enabledocumentcolors)|システム カラーではなくドキュメント固有の色の表示を有効にします。|
|[CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)|有効にし、標準のカラー ボタンの下にある、「その他」ボタンを無効にします。 ("Other"ボタンのラベルは、標準的なシステム**その他の色**)。|
|[CMFCColorMenuButton::EnableTearOff](#enabletearoff)|色ウィンドウをオフに除去する機能を有効にします。|
|[CMFCColorMenuButton::GetAutomaticColor](#getautomaticcolor)|現在の自動の色を取得します。|
|[CMFCColorMenuButton::GetColor](#getcolor)|現在のボタンの色を取得します。|
|[CMFCColorMenuButton::GetColorByCmdID](#getcolorbycmdid)|指定したコマンド ID に対応する色を取得します。|
|[CMFCColorMenuButton::OnChangeParentWnd](#onchangeparentwnd)|親ウィンドウが変更されたときに、フレームワークによって呼び出されます。|
|[CMFCColorMenuButton::OpenColorDialog](#opencolordialog)|色の選択 ダイアログ ボックスが開きます。|
|[CMFCColorMenuButton::SetColor](#setcolor)|現在のカラー ボタンの色を設定します。|
|[CMFCColorMenuButton::SetColorByCmdID](#setcolorbycmdid)|指定したカラー メニュー ボタンの色を設定します。|
|[CMFCColorMenuButton::SetColorName](#setcolorname)|指定した色の新しい名前を設定します。|
|[CMFCColorMenuButton::SetColumnsNumber](#setcolumnsnumber)|によって表示される列の数を設定、`CMFCColorBar`オブジェクト。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCColorMenuButton::CopyFrom](#copyfrom)|現在のボタンには、別のツール バー ボタンをコピーします。|
|[CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)|カラー ピッカー ダイアログ ボックスを作成します。|
|[CMFCColorMenuButton::IsEmptyMenuAllowed](#isemptymenuallowed)|空のメニューがサポートされているかどうかを示します。|
|[CMFCColorMenuButton::OnDraw](#ondraw)|ボタンにイメージを表示するためにフレームワークによって呼び出されます。|
|[CMFCColorMenuButton::OnDrawOnCustomizeList](#ondrawoncustomizelist)|前にフレームワークによって呼び出されます、`CMFCColorMenuButton`オブジェクトが、ツールバーのカスタマイズ ダイアログ ボックスの一覧に表示されます。|

## <a name="remarks"></a>Remarks

元のメニュー コマンドまたはツール バー ボタンを置換する、`CMFCColorMenuButton`オブジェクトを作成、`CMFCColorMenuButton`オブジェクト、設定、適切な[CMFCColorBar クラス](../../mfc/reference/cmfccolorbar-class.md)スタイル、および、呼び出し、`ReplaceButton`メソッド、の[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md)クラス。 ツールバーをカスタマイズする場合、 [CMFCToolBarsCustomizeDialog::ReplaceButton](../../mfc/reference/cmfctoolbarscustomizedialog-class.md#replacebutton)メソッド。

カラー ピッカー ダイアログ ボックスが処理中に作成された、 [CMFCColorMenuButton::CreatePopupMenu](#createpopupmenu)イベント ハンドラー。 WM_COMMAND メッセージと親フレームのイベント ハンドラーに通知します。 `CMFCColorMenuButton`オブジェクトが元のメニュー コマンドやツールバーのボタンに割り当てられているコントロール ID を送信します。

## <a name="example"></a>例

次の例では、作成して、さまざまなメソッドを使用してカラー メニュー ボタンを構成する方法、`CMFCColorMenuButton`クラス。 例を`CPalette`オブジェクトが最初に作成しのオブジェクトを構築するために使用し、`CMFCColorMenuButton`クラス。 `CMFCColorMenuButton`オブジェクトが、自動と他のボタンを有効にして、色と列の数を設定し、構成されています。 このコードは、 [Word パッド サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_WordPad#5](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_1.h)]
[!code-cpp[NVC_MFC_WordPad#6](../../mfc/reference/codesnippet/cpp/cmfccolormenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarMenuButton](../../mfc/reference/cmfctoolbarmenubutton-class.md)

[CMFCColorMenuButton](../../mfc/reference/cmfccolormenubutton-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcolormenubutton.h

##  <a name="cmfccolormenubutton"></a>  CMFCColorMenuButton::CMFCColorMenuButton

`CMFCColorMenuButton` オブジェクトを構築します。

```
CMFCColorMenuButton();

CMFCColorMenuButton(
    UINT uiCmdID,
    LPCTSTR lpszText,
    CPalette* pPalette=NULL);
```

### <a name="parameters"></a>パラメーター

*uiCmdID*<br/>
[in]ボタンのコマンド id。

*lpszText*<br/>
[in]ボタンのテキスト。

*pPalette*<br/>
[in]ボタンの色パレットへのポインター。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

最初のコンス トラクターは、既定のコンス トラクターです。 オブジェクトの現在の色と自動の色は、黒 (RGB (0, 0, 0)) に初期化されます。

2 番目のコンス トラクターを指定したコマンド ID に対応する色のボタンを初期化します

##  <a name="copyfrom"></a>  CMFCColorMenuButton::CopyFrom

1 つコピー [CMFCToolBarMenuButton クラス](../../mfc/reference/cmfctoolbarmenubutton-class.md)-別の派生オブジェクト。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
[in]コピー元のボタン。

### <a name="remarks"></a>Remarks

派生したオブジェクトをコピーするには、このメソッドをオーバーライド、`CMFCColorMenuButton`オブジェクト。

##  <a name="createpopupmenu"></a>  CMFCColorMenuButton::CreatePopupMenu

カラー ピッカー ダイアログ ボックスを作成します。

```
virtual CMFCPopupMenu* CreatePopupMenu();
```

### <a name="return-value"></a>戻り値

カラー ピッカー ダイアログ ボックスを表すオブジェクト。

### <a name="remarks"></a>Remarks

カラー メニュー ボタンを押すと、このメソッドは、フレームワークによって呼び出されます。

##  <a name="enableautomaticbutton"></a>  CMFCColorMenuButton::EnableAutomaticButton

有効にし、通常の色のボタンの上に配置された「自動」のボタンを無効にします。 (標準のシステムの自動ボタンのラベルは**自動**)。

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
[in]ときに、自動ボタンに表示されるボタンのテキストを指定します。

*colorAutomatic*<br/>
[in]新しい自動の色を指定します。

*bEnable*<br/>
[in]ボタンが自動であるかどうかどうかを指定します。

### <a name="remarks"></a>Remarks

自動ボタンには、現在の既定の色が適用されます。

##  <a name="enabledocumentcolors"></a>  CMFCColorMenuButton::EnableDocumentColors

システム カラーではなくドキュメント固有の色の表示を有効にします。

```
void EnableDocumentColors(
    LPCTSTR lpszLabel,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
[in]ボタンのテキストを指定します。

*bEnable*<br/>
[in]ドキュメントに固有の色または色のシステム カラーを表示する場合は FALSE を表示する場合は TRUE。

### <a name="remarks"></a>Remarks

カラー メニュー ボタンをクリックすると、現在のドキュメントの色またはシステム パレットの色を表示するのにには、このメソッドを使用します。

##  <a name="enableotherbutton"></a>  CMFCColorMenuButton::EnableOtherButton

有効にし、標準のカラー ボタンの下にある、「その他」ボタンを無効にします。 ("Other"ボタンのラベルは、標準的なシステム**その他の色**)。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
[in]ボタンのテキストを指定します。

*bAltColorDlg*<br/>
[in]表示するを指定する場合は TRUE、`CMFCColorDialog`ダイアログ ボックスで、または標準のシステム カラーのダイアログ ボックスを表示する場合は FALSE。

*bEnable*<br/>
[in]「その他」ボタンを表示する場合は TRUE を指定します。それ以外の場合、FALSE です。 既定では TRUE です。

### <a name="remarks"></a>Remarks

##  <a name="enabletearoff"></a>  CMFCColorMenuButton::EnableTearOff

色ウィンドウをオフに除去する機能を有効にします。

```
void EnableTearOff(
    UINT uiID,
    int nVertDockColumns=-1,
    int nHorzDockRows=-1);
```

### <a name="parameters"></a>パラメーター

*uiID*<br/>
[in]ティアオフ ペインの ID を指定します。

*nVertDockColumns*<br/>
[in]ティアオフ状態の間に垂直方向にドッキングされている色ウィンドウの列の数を指定します。

*nHorzDockRows*<br/>
[in]ティアオフ状態のときに、水平方向にドッキングされている色ウィンドウの行の数を指定します。

### <a name="remarks"></a>Remarks

ときにポップアップ表示される色ウィンドウの「ティアオフ」機能を有効にするには、このメソッドを呼び出して、`CMFCColorMenuButton`ボタンが押されました。

##  <a name="getautomaticcolor"></a>  CMFCColorMenuButton::GetAutomaticColor

現在の自動の色を取得します。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>戻り値

現在の自動の色を表す RGB カラー値。

### <a name="remarks"></a>Remarks

によって設定される自動の色を取得するには、このメソッドを呼び出す[CMFCColorMenuButton::EnableAutomaticButton](#enableautomaticbutton)します。

##  <a name="getcolor"></a>  CMFCColorMenuButton::GetColor

現在のボタンの色を取得します。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>戻り値

ボタンの色。

### <a name="remarks"></a>Remarks

##  <a name="getcolorbycmdid"></a>  CMFCColorMenuButton::GetColorByCmdID

指定したコマンド ID に対応する色を取得します。

```
static COLORREF GetColorByCmdID(UINT uiCmdID);
```

### <a name="parameters"></a>パラメーター

*uiCmdID*<br/>
[in]コマンド id。

### <a name="return-value"></a>戻り値

指定したコマンド ID に対応する色

### <a name="remarks"></a>Remarks

アプリケーションでいくつかの色のボタンがある場合は、このメソッドを使用します。 ユーザーは、色のボタンをクリックすると、ボタンは、その親に WM_COMMAND メッセージでそのコマンド ID を送信します。 `GetColorByCmdID`メソッドでは、コマンド ID を使用して、対応する色を取得します。

##  <a name="isemptymenuallowed"></a>  CMFCColorMenuButton::IsEmptyMenuAllowed

空のメニューがサポートされているかどうかを示します。

```
virtual BOOL IsEmptyMenuAllowed() const;
```

### <a name="return-value"></a>戻り値

空の場合は 0 以外のメニューは使用できません。それ以外の場合、0 を返します。

### <a name="remarks"></a>Remarks

既定では、空のメニューがサポートされています。 派生クラスでは、この動作を変更するには、このメソッドをオーバーライドします。

##  <a name="onchangeparentwnd"></a>  CMFCColorMenuButton::OnChangeParentWnd

親ウィンドウが変更されたときに、フレームワークによって呼び出されます。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
[in]新しい親ウィンドウへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="ondraw"></a>  CMFCColorMenuButton::OnDraw

ボタンにイメージを表示するためにフレームワークによって呼び出されます。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz=TRUE,
    BOOL bCustomizeMode=FALSE,
    BOOL bHighlight=FALSE,
    BOOL bDrawBorder=TRUE,
    BOOL bGrayDisabledButtons=TRUE);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

*rect*<br/>
[in]再描画する領域に外接する四角形。

*pImages*<br/>
[in]ツール バー イメージの一覧を指します。

*bHorz*<br/>
[in]水平のドッキング状態で、ツールバーを指定する場合は TRUEそれ以外の場合、FALSE です。 既定では TRUE です。

*bCustomizeMode*<br/>
[in]カスタマイズ モードでアプリケーションを指定する場合は TRUEそれ以外の場合、FALSE です。 既定では FALSE です。

*bHighlight*<br/>
[in]ボタンがハイライトされているかを指定する場合は TRUEそれ以外の場合、FALSE です。 既定では FALSE です。

*bDrawBorder*<br/>
[in]ボタンの境界線が表示されることを指定する場合は TRUEそれ以外の場合、FALSE です。 既定では TRUE です。

*bGrayDisabledButtons*<br/>
[in]Out; 無効なボタンが淡色表示 (淡色表示されます) ことを指定する場合は TRUEそれ以外の場合、FALSE です。 既定では TRUE です。

### <a name="remarks"></a>Remarks

##  <a name="ondrawoncustomizelist"></a>  CMFCColorMenuButton::OnDrawOnCustomizeList

前にフレームワークによって呼び出されます、`CMFCColorMenuButton`オブジェクトが、ツールバーのカスタマイズ ダイアログ ボックスの一覧に表示されます。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

*rect*<br/>
[in]描画するボタンの外接する四角形にします。

*bSelected*<br/>
[in]TRUE は、ボタンが選択されていることを指定しますそれ以外の場合、FALSE です。

### <a name="return-value"></a>戻り値

ボタンの幅。

### <a name="remarks"></a>Remarks

このメソッドは、フレームワークによって呼び出さときに、`CMFCColorMenuButton`ツールバーのカスタマイズ プロセス中にオブジェクトがリスト ボックスに表示されます。

##  <a name="opencolordialog"></a>  CMFCColorMenuButton::OpenColorDialog

色の選択 ダイアログ ボックスが開きます。

```
virtual BOOL OpenColorDialog(
    const COLORREF colorDefault,
    COLORREF& colorRes);
```

### <a name="parameters"></a>パラメーター

*colorDefault*<br/>
[in]色のダイアログ ボックスで選択されている既定の色。

*colorRes*<br/>
[out]ユーザーが色ダイアログ ボックスから選択した色を返します。

### <a name="return-value"></a>戻り値

ユーザーが新しい色を選択した場合、0 以外の場合それ以外の場合、0 を返します。

### <a name="remarks"></a>Remarks

メニュー ボタンがクリックされたときに、色のダイアログ ボックスを開くには、このメソッドを呼び出します。 ユーザーが選択した色が格納されている戻り値が 0 以外の場合、 *colorRes*パラメーター。 使用して、 [CMFCColorMenuButton::EnableOtherButton](#enableotherbutton)メソッドを標準の色 ダイアログ ボックスを切り替えると、 [CMFCColorDialog クラス](../../mfc/reference/cmfccolordialog-class.md) ダイアログ ボックス。

##  <a name="setcolor"></a>  CMFCColorMenuButton::SetColor

現在のカラー ボタンの色を設定します。

```
virtual void SetColor(
    COLORREF clr,
    BOOL bNotify=TRUE);
```

### <a name="parameters"></a>パラメーター

*clr*<br/>
[in]RGB 色の値。

*bNotify*<br/>
[in]適用する場合は TRUE、 *clr*パラメーターの色関連メニュー ボタンまたはツール バー ボタンには、それ以外の場合。

### <a name="remarks"></a>Remarks

現在の色のボタンの色を変更するには、このメソッドを呼び出します。 場合、 *bNotify*パラメーターが 0 以外の場合、関連付けられたポップアップ メニューまたはツールバーで、対応するボタンの色がで指定された色に変更された、 *clr*パラメーター。

##  <a name="setcolorbycmdid"></a>  CMFCColorMenuButton::SetColorByCmdID

指定したカラー メニュー ボタンの色を設定します。

```
static void SetColorByCmdID(
    UINT uiCmdID,
    COLORREF color);
```

### <a name="parameters"></a>パラメーター

*uiCmdID*<br/>
[in]カラー メニュー ボタンのリソース ID。

*色*<br/>
[in]RGB 色の値。

##  <a name="setcolorname"></a>  CMFCColorMenuButton::SetColorName

指定した色の新しい名前を設定します。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
[in]名前を変更、色の RGB 値。

*strName*<br/>
[in]色の新しい名前。

### <a name="remarks"></a>Remarks

##  <a name="setcolumnsnumber"></a>  CMFCColorMenuButton::SetColumnsNumber

色の選択コントロールに表示する列の数を設定します ( [CMFCColorBar](../../mfc/reference/cmfccolorbar-class.md)オブジェクト)。

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>パラメーター

*nColumns*<br/>
[in]表示する列の数。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorBar クラス](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarsCustomizeDialog クラス](../../mfc/reference/cmfctoolbarscustomizedialog-class.md)<br/>
[CMFCColorButton クラス](../../mfc/reference/cmfccolorbutton-class.md)
