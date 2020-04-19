---
title: CMFCColorDialog クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::CMFCColorDialog
- AFXCOLORDIALOG/CMFCColorDialog::GetColor
- AFXCOLORDIALOG/CMFCColorDialog::GetPalette
- AFXCOLORDIALOG/CMFCColorDialog::RebuildPalette
- AFXCOLORDIALOG/CMFCColorDialog::SetCurrentColor
- AFXCOLORDIALOG/CMFCColorDialog::SetNewColor
- AFXCOLORDIALOG/CMFCColorDialog::SetPageOne
- AFXCOLORDIALOG/CMFCColorDialog::SetPageTwo
helpviewer_keywords:
- CMFCColorDialog [MFC], CMFCColorDialog
- CMFCColorDialog [MFC], GetColor
- CMFCColorDialog [MFC], GetPalette
- CMFCColorDialog [MFC], RebuildPalette
- CMFCColorDialog [MFC], SetCurrentColor
- CMFCColorDialog [MFC], SetNewColor
- CMFCColorDialog [MFC], SetPageOne
- CMFCColorDialog [MFC], SetPageTwo
ms.assetid: 235bbbbc-a3b1-46e0-801b-fb55093ec579
ms.openlocfilehash: 9e018c122cded09e5366c3b349525fa7cc004897
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505335"
---
# <a name="cmfccolordialog-class"></a>CMFCColorDialog クラス

クラス`CMFCColorDialog`は、色の選択ダイアログボックスを表します。

## <a name="syntax"></a>構文

```
class CMFCColorDialog : public CDialogEx
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCColorDialog::CMFCColorDialog](#cmfccolordialog)|`CMFCColorDialog` オブジェクトを構築します。|
|`CMFCColorDialog::~CMFCColorDialog`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCColorDialog::GetColor](#getcolor)|現在選択されている色を返します。|
|[CMFCColorDialog:: GetPalette](#getpalette)|色のパレットを返します。|
|`CMFCColorDialog::PreTranslateMessage`|[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)および[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)の Windows 関数にディスパッチされる前に、ウィンドウメッセージを変換します。 構文と詳細については、「 [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)」を参照してください。 ( `CDialogEx::PreTranslateMessage`をオーバーライドします)。|
|[CMFCColorDialog::RebuildPalette](#rebuildpalette)|システムパレットからパレットを派生します。|
|[CMFCColorDialog::SetCurrentColor](#setcurrentcolor)|現在選択されている色を設定します。|
|[CMFCColorDialog:: SetNewColor](#setnewcolor)|指定した RGB 値に最も等しい色を設定します。|
|[CMFCColorDialog::SetPageOne](#setpageone)|最初のプロパティページの RGB 値を選択します。|
|[CMFCColorDialog::SetPageTwo](#setpagetwo)|2番目のプロパティページの RGB 値を選択します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|`m_bIsMyPalette`|色の選択ダイアログボックスで独自の色パレットを使用する場合は TRUE、 `CMFCColorDialog`コンストラクターで指定されているパレットをダイアログボックスで使用する場合は FALSE。|
|`m_bPickerMode`|ユーザーが [選択] ダイアログボックスから色を選択している場合は TRUE。それ以外の場合は FALSE。|
|`m_btnColorSelect`|ユーザーが選択したカラーボタン。|
|`m_CurrentColor`|現在選択されている色。|
|`m_hcurPicker`|色の選択に使用されるカーソル。|
|`m_NewColor`|選択された見込み色。完全に選択するか、元の色に戻すことができます。|
|`m_pColourSheetOne`|色の選択プロパティシートの最初のプロパティページへのポインター。|
|`m_pColourSheetTwo`|色の選択プロパティシートの2番目のプロパティページへのポインター。|
|`m_pPalette`|現在の論理パレット。|
|`m_pPropSheet`|色の選択ダイアログボックスのプロパティシートへのポインター。|
|`m_wndColors`|カラーピッカーコントロールオブジェクト。|
|`m_wndStaticPlaceHolder`|カラーピッカープロパティシートのプレースホルダーである静的コントロール。|

## <a name="remarks"></a>Remarks

[色の選択] ダイアログボックスは、2ページのプロパティシートとして表示されます。 最初のページで、システムパレットから標準の色を選択します。2番目のページでは、ユーザー設定の色を選択します。

オブジェクトを`CMFCColorDialog`スタックに構築し、を呼び出し`DoModal`て、初期色をパラメーター `CMFCColorDialog`としてコンストラクターに渡すことができます。 次に、[色の選択] ダイアログボックスで、各カラーパレットを処理する複数の[CMFCColorPickerCtrl クラス](../../mfc/reference/cmfccolorpickerctrl-class.md)オブジェクトを作成します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md)

## <a name="example"></a>例

`CMFCColorDialog`クラスのさまざまなメソッドを使用してカラーダイアログを構成する方法を次の例に示します。 この例では、ダイアログの現在の色と新しい色を設定する方法、および色のダイアログボックスの2つのプロパティページで選択した色の赤、緑、および青のコンポーネントを設定する方法を示します。 この例は、「[新しいコントロールのサンプル](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_NewControls#3](../../mfc/reference/codesnippet/cpp/cmfccolordialog-class_1.cpp)]

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcolordialog

##  <a name="cmfccolordialog"></a>  CMFCColorDialog::CMFCColorDialog

`CMFCColorDialog` オブジェクトを構築します。

```
CMFCColorDialog(
    COLORREF clrInit=0,
    DWORD dwFlags=0,
    CWnd* pParentWnd=NULL,
    HPALETTE hPal=NULL);
```

### <a name="parameters"></a>パラメーター

*clrInit*<br/>
から既定の色の選択。 値が指定されていない場合、既定値は RGB (0, 0, 0) (黒) です。

*dwFlags*<br/>
[in] 予約されています。

*pParentWnd*<br/>
からダイアログボックスの親またはオーナーウィンドウへのポインター。

*hPal*<br/>
からカラーパレットを処理するハンドル。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getcolor"></a>  CMFCColorDialog::GetColor

色のダイアログからユーザーが選択した色を取得します。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>戻り値

[色] ダイアログボックスで選択した色の RGB 情報を含む[COLORREF](/windows/win32/gdi/colorref)値。

### <a name="remarks"></a>Remarks

メソッドを呼び出した後に、 `DoModal`この関数を呼び出します。

##  <a name="getpalette"></a>  CMFCColorDialog::GetPalette

現在の色のダイアログで使用できるカラーパレットを取得します。

```
CPalette* GetPalette() const;
```

### <a name="return-value"></a>戻り値

コンストラクターで指定さ`CPalette`れたオブジェクトへのポインター。 `CMFCColorDialog`

### <a name="remarks"></a>Remarks

カラーパレットでは、ユーザーが選択できる色を指定します。

##  <a name="rebuildpalette"></a>  CMFCColorDialog::RebuildPalette

システムパレットからパレットを派生します。

```
void RebuildPalette();
```

##  <a name="setcurrentcolor"></a>  CMFCColorDialog::SetCurrentColor

ダイアログボックスの現在の色を設定します。

```
void SetCurrentColor(COLORREF rgb);
```

### <a name="parameters"></a>パラメーター

*rgb*<br/>
からRGB カラー値

### <a name="remarks"></a>Remarks

##  <a name="setnewcolor"></a>  CMFCColorDialog::SetNewColor

現在の色を、最もよく似た現在のパレットの色に設定します。

```
void SetNewColor(COLORREF rgb);
```

### <a name="parameters"></a>パラメーター

*rgb*<br/>
からRGB 色を指定する[COLORREF](/windows/win32/gdi/colorref) 。

### <a name="remarks"></a>Remarks

##  <a name="setpageone"></a>  CMFCColorDialog::SetPageOne

色のダイアログの最初のプロパティページで、選択した色の赤、緑、および青のコンポーネントを明示的に指定します。

```
void SetPageOne(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>パラメーター

*R*<br/>
からRGB 値の赤の要素を指定します。

*G*<br/>
からRGB 値の緑の要素を指定します。

*B*<br/>
からRGB 値の青の要素を指定します。

### <a name="remarks"></a>Remarks

##  <a name="setpagetwo"></a>  CMFCColorDialog::SetPageTwo

色のダイアログボックスの2番目のプロパティページで、選択した色の赤、緑、および青のコンポーネントを明示的に指定します。

```
void SetPageTwo(
    BYTE R,
    BYTE G,
    BYTE B);
```

### <a name="parameters"></a>パラメーター

*R*<br/>
からRGB 値の赤の要素を指定します。

*G*<br/>
からRGB 値の緑の要素を指定します。

*B*<br/>
からRGB 値の青の要素を指定します。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorPickerCtrl クラス](../../mfc/reference/cmfccolorpickerctrl-class.md)
