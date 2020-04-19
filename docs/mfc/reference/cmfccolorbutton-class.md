---
title: CMFCColorButton クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::CMFCColorButton
- AFXCOLORBUTTON/CMFCColorButton::EnableAutomaticButton
- AFXCOLORBUTTON/CMFCColorButton::EnableOtherButton
- AFXCOLORBUTTON/CMFCColorButton::GetAutomaticColor
- AFXCOLORBUTTON/CMFCColorButton::GetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColor
- AFXCOLORBUTTON/CMFCColorButton::SetColorName
- AFXCOLORBUTTON/CMFCColorButton::SetColumnsNumber
- AFXCOLORBUTTON/CMFCColorButton::SetDocumentColors
- AFXCOLORBUTTON/CMFCColorButton::SetPalette
- AFXCOLORBUTTON/CMFCColorButton::SizeToContent
- AFXCOLORBUTTON/CMFCColorButton::IsDrawXPTheme
- AFXCOLORBUTTON/CMFCColorButton::OnDraw
- AFXCOLORBUTTON/CMFCColorButton::OnDrawBorder
- AFXCOLORBUTTON/CMFCColorButton::OnDrawFocusRect
- AFXCOLORBUTTON/CMFCColorButton::OnShowColorPopup
- AFXCOLORBUTTON/CMFCColorButton::RebuildPalette
- AFXCOLORBUTTON/CMFCColorButton::UpdateColor
- AFXCOLORBUTTON/CMFCColorButton::m_bEnabledInCustomizeMode
helpviewer_keywords:
- CMFCColorButton [MFC], CMFCColorButton
- CMFCColorButton [MFC], EnableAutomaticButton
- CMFCColorButton [MFC], EnableOtherButton
- CMFCColorButton [MFC], GetAutomaticColor
- CMFCColorButton [MFC], GetColor
- CMFCColorButton [MFC], SetColor
- CMFCColorButton [MFC], SetColorName
- CMFCColorButton [MFC], SetColumnsNumber
- CMFCColorButton [MFC], SetDocumentColors
- CMFCColorButton [MFC], SetPalette
- CMFCColorButton [MFC], SizeToContent
- CMFCColorButton [MFC], IsDrawXPTheme
- CMFCColorButton [MFC], OnDraw
- CMFCColorButton [MFC], OnDrawBorder
- CMFCColorButton [MFC], OnDrawFocusRect
- CMFCColorButton [MFC], OnShowColorPopup
- CMFCColorButton [MFC], RebuildPalette
- CMFCColorButton [MFC], UpdateColor
- CMFCColorButton [MFC], m_bEnabledInCustomizeMode
ms.assetid: 9fdf34ae-4cc5-4c5e-9d89-1c50e8a73699
ms.openlocfilehash: ac49957f075f8798607535286d6c4518c0eeeeae
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505361"
---
# <a name="cmfccolorbutton-class"></a>CMFCColorButton クラス

および`CMFCColorButton` [cmfccolorbar クラス](../../mfc/reference/cmfccolorbar-class.md)クラスは、カラーピッカーコントロールを実装するために一緒に使用されます。

## <a name="syntax"></a>構文

```
class CMFCColorButton : public CMFCButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCColorButton:: CMFCColorButton](#cmfccolorbutton)|新しい `CMFCColorButton` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCColorButton::EnableAutomaticButton](#enableautomaticbutton)|通常の色のボタンの上にある [自動] ボタンを有効または無効にします。 (標準システム 自動ボタンは **自動** というラベルが付いています)。|
|[CMFCColorButton:: EnableOtherButton](#enableotherbutton)|通常の色のボタンの下に配置される "その他" ボタンを有効または無効にします。 (標準システムの [その他] ボタンには、**より多くの色**が付けられています)。|
|[CMFCColorButton:: Get自動カラー](#getautomaticcolor)|現在の自動色を取得します。|
|[CMFCColorButton:: GetColor](#getcolor)|ボタンの色を取得します。|
|[CMFCColorButton:: SetColor](#setcolor)|ボタンの色を設定します。|
|[CMFCColorButton::SetColorName](#setcolorname)|色の名前を設定します。|
|[CMFCColorButton::SetColumnsNumber](#setcolumnsnumber)|[カラーピッカー] ダイアログボックスの列数を設定します。|
|[CMFCColorButton:: SetDocumentColors](#setdocumentcolors)|[カラーピッカー] ダイアログボックスに表示されるドキュメント固有の色の一覧を指定します。|
|[CMFCColorButton:: SetPalette](#setpalette)|標準表示色のパレットを指定します。|
|[CMFCColorButton:: SizeToContent](#sizetocontent)|テキストとイメージのサイズに応じて、ボタンコントロールのサイズを変更します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCColorButton:: Isdrawxp テーマ](#isdrawxptheme)|現在の色のボタンを Windows XP の視覚スタイルで表示するかどうかを示します。|
|[CMFCColorButton:: OnDraw](#ondraw)|ボタンのイメージを表示するためにフレームワークによって呼び出されます。|
|[CMFCColorButton::OnDrawBorder](#ondrawborder)|ボタンの境界線を表示するためにフレームワークによって呼び出されます。|
|[CMFCColorButton::OnDrawFocusRect](#ondrawfocusrect)|ボタンにフォーカスがあるときにフォーカスを示す四角形を表示するために、フレームワークによって呼び出されます。|
|[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)|カラーピッカーダイアログボックスを表示しようとしているときに、フレームワークによって呼び出されます。|
|[CMFCColorButton::RebuildPalette](#rebuildpalette)|指定したパレットまたは既定のシステムパレットに対して、保護されたデータメンバーを初期化します。`m_pPalette`|
|[CMFCColorButton:: UpdateColor](#updatecolor)|ユーザーがカラーピッカーダイアログボックスのパレットから色を選択すると、フレームワークによって呼び出されます。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|`m_bAltColorDlg`|ブール値。 TRUE の場合、[*その他*] ボタンがクリックされたときに [ [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) color] ダイアログボックスが表示されます。 FALSE の場合は、[システムカラー] ダイアログボックスが表示されます。 既定値は TRUE です。 詳細については、「 [Cmfccolorbutton:: EnableOtherButton](#enableotherbutton)」を参照してください。|
|`m_bAutoSetFocus`|ブール値。 TRUE の場合、フレームワークはメニューが表示されるときにカラーメニューにフォーカスを設定します。 FALSE の場合はフォーカスを変更しません。 既定値は TRUE です。|
|[CMFCColorButton:: m_bEnabledInCustomizeMode](#m_benabledincustomizemode)|色のボタンに対してカスタマイズモードが有効になっているかどうかを示します。|
|`m_Color`|[COLORREF](/windows/win32/gdi/colorref)値。 現在選択されている色が含まれます。|
|`m_ColorAutomatic`|[COLORREF](/windows/win32/gdi/colorref)値。 現在選択されている既定の色が含まれます。|
|`m_Colors`|[COLORREF](/windows/win32/gdi/colorref)値の[CArray](../../mfc/reference/carray-class.md) 。 現在使用可能な色が含まれています。|
|`m_lstDocColors`|[COLORREF](/windows/win32/gdi/colorref)値の[CList](../../mfc/reference/clist-class.md) 。 現在のドキュメントの色を格納します。|
|`m_nColumns`|整数。 色の選択メニューの色のグリッドに表示する列数を格納します。|
|`m_pPalette`|[CPalette](../../mfc/reference/cpalette-class.md)へのポインター。 現在の色の選択メニューで使用できる色が含まれています。|
|`m_pPopup`|[CMFCColorPopupMenu クラス](../../mfc/reference/cmfccolorpopupmenu-class.md)オブジェクトへのポインター。 色のボタンをクリックしたときに表示される色の選択メニュー。|
|`m_strAutoColorText`|文字列。 色選択メニューの [自動] ボタンのラベル。|
|`m_strDocColorsText`|文字列。 ドキュメントの色を表示する、カラー選択メニューのボタンのラベル。|
|`m_strOtherText`|文字列。 色選択メニューの [その他] ボタンのラベル。|

## <a name="remarks"></a>Remarks

既定では、 `CMFCColorButton`クラスは [カラーピッカー] ダイアログボックスを開くプッシュボタンとして動作します。 [カラーピッカー] ダイアログボックスには、小さいカラーボタンの配列と、カスタムカラーピッカーを表示する "その他" のボタンが含まれています。 (標準システムの [その他] ボタンには、**より多くの色**が付けられています)。ユーザーが新しい色を選択すると、 `CMFCColorButton`オブジェクトにはその変更が反映され、選択した色が表示されます。

色ボタンコントロールを作成するには、コード内で直接作成するか、 **ClassWizard**ツールとダイアログボックステンプレートを使用します。 カラーボタンコントロールを直接作成する場合は、アプリケーション`CMFCColorButton`に変数を追加し、 `CMFCColorButton`オブジェクトのコンストラクターと`Create`メソッドを呼び出します。 **ClassWizard**を使用する場合は、アプリケーション`CButton`に変数を追加し、変数の型をから`CButton`に`CMFCColorButton`変更します。

フレームワークがイベントハンドラーを`OnLButtonDown`呼び出すと、[カラーピッカー] ダイアログボックス ( [cmfccolorbar クラス](../../mfc/reference/cmfccolorbar-class.md)) が[cmfccolorbar:: onshowcolorpopup](#onshowcolorpopup)メソッドによって表示されます。 [Cmfccolorbutton:: OnShowColorPopup](#onshowcolorpopup)メソッドをオーバーライドして、独自の色の選択をサポートすることができます。

オブジェクト`CMFCColorButton`は、色が変更されていることを親に通知します。BN_CLICKED 通知。 親は、 [Cmfccolorbutton:: getcolor](#getcolor)メソッドを使用して現在の色を取得します。

## <a name="example"></a>例

次の例では、 `CMFCColorButton`クラスのさまざまなメソッドを使用して、色のボタンを構成する方法を示します。 これらのメソッドは、カラーボタンの色と列の数を設定し、自動およびその他のボタンを有効にします。 この例は、[ステータスバーのデモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_StatusBarDemo#10](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_1.h)]
[!code-cpp[NVC_MFC_StatusBarDemo#11](../../mfc/reference/codesnippet/cpp/cmfccolorbutton-class_2.cpp)]

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcolorbutton

##  <a name="cmfccolorbutton"></a>CMFCColorButton:: CMFCColorButton

新しい `CMFCColorButton` オブジェクトを構築します。

```
CMFCColorButton();
```

##  <a name="enableautomaticbutton"></a>  CMFCColorButton::EnableAutomaticButton

カラーピッカーコントロールの [自動] ボタンを有効または無効にし、自動 (既定) 色を設定します。

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
から自動ボタンのテキストを指定します。

*colorAutomatic*<br/>
から自動ボタンの既定の色を指定する RGB 値。

*bEnable*<br/>
から[自動] ボタンを有効または無効にするかどうかを指定します。

### <a name="remarks"></a>Remarks

##  <a name="enableotherbutton"></a>  CMFCColorButton::EnableOtherButton

[その他] ボタンを有効または無効にします。このボタンは、通常の色のボタンの下に表示されます。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg=TRUE,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
からボタンのテキストを指定します。

*Tcolordlg*<br/>
からユーザーがボタンをクリックしたときに、[ [CMFCColorDialog](../../mfc/reference/cmfccolordialog-class.md) ] ダイアログボックスまたは [システムカラー] ダイアログボックスを開くかどうかを指定します。

*bEnable*<br/>
から[その他] ボタンを有効または無効にするかどうかを指定します。

### <a name="remarks"></a>Remarks

[その他] ボタンをクリックして、色のダイアログボックスを表示します。 この場合 、 [CMFCColorDialog クラス](../../mfc/reference/cmfccolordialog-class.md)が表示されます。それ以外の場合は、[システムカラー] ダイアログボックスが表示されます。

##  <a name="getautomaticcolor"></a>  CMFCColorButton::GetAutomaticColor

現在の自動 (既定) 色を取得します。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>戻り値

現在の自動カラーを表す RGB 値。

### <a name="remarks"></a>Remarks

現在の自動色は、 [Cmfccolorbutton:: enable自動ボタン](#enableautomaticbutton)メソッドによって設定されます。

##  <a name="getcolor"></a>  CMFCColorButton::GetColor

現在選択されている色を取得します。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>戻り値

RGB 値。

### <a name="remarks"></a>Remarks

##  <a name="isdrawxptheme"></a>  CMFCColorButton::IsDrawXPTheme

現在の色のボタンを Windows XP の視覚スタイルで表示するかどうかを示します。

```
BOOL IsDrawXPTheme() const;
```

### <a name="return-value"></a>戻り値

Visual スタイルがサポートされていて、現在の色のボタンが Windows XP の視覚スタイルで表示されている場合は TRUE。それ以外の場合は FALSE。

##  <a name="m_benabledincustomizemode"></a>CMFCColorButton:: m_bEnabledInCustomizeMode

色のボタンをカスタマイズモードに設定します。

```
BOOL m_bEnabledInCustomizeMode;
```

### <a name="remarks"></a>Remarks

カスタマイズダイアログのページに色ボタンを追加する必要がある場合 (またはカスタマイズ中にユーザーが別の色を選択できるようにする場合) は`m_bEnabledInCustomizeMode` 、メンバーを TRUE に設定してボタンを有効にします。 既定では、このメンバーは FALSE に設定されています。

##  <a name="ondraw"></a>  CMFCColorButton::OnDraw

ボタンのイメージをレンダリングするためにフレームワークによって呼び出されます。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    UINT uiState);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からボタンのイメージのレンダリングに使用されるデバイスコンテキストを指します。

*rect*<br/>
からボタンの境界となる四角形。

*uiState*<br/>
からボタンの表示状態を指定します。

### <a name="remarks"></a>Remarks

レンダリングプロセスをカスタマイズするには、このメソッドをオーバーライドします。

##  <a name="ondrawborder"></a>  CMFCColorButton::OnDrawBorder

ボタンの境界線を表示するためにフレームワークによって呼び出されます。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect& rectClient,
    UINT uiState);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
から境界線の描画に使用されるデバイスコンテキストを指します。

*rectClient*<br/>
から*PDC*パラメーターによって指定される、描画されるボタンの境界を定義する、デバイスコンテキスト内の四角形。

*uiState*<br/>
からボタンの表示状態を指定します。

### <a name="remarks"></a>Remarks

色ボタンの境界線の外観をカスタマイズするには、この関数をオーバーライドします。

##  <a name="ondrawfocusrect"></a>  CMFCColorButton::OnDrawFocusRect

ボタンにフォーカスがあるときにフォーカスを示す四角形を表示するために、フレームワークによって呼び出されます。

```
virtual void OnDrawFocusRect(
    CDC* pDC,
    const CRect& rectClient);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からフォーカスを示す四角形を描画するために使用されるデバイスコンテキストを指します。

*rectClient*<br/>
から*PDC*パラメーターによって指定された、ボタンの境界を定義するデバイスコンテキスト内の四角形。

### <a name="remarks"></a>Remarks

フォーカスを示す四角形の外観をカスタマイズするには、このメソッドをオーバーライドします。

##  <a name="onshowcolorpopup"></a>  CMFCColorButton::OnShowColorPopup

ポップアップカラーバーが表示される前に呼び出されます。

```
virtual void OnShowColorPopup();
```

### <a name="remarks"></a>Remarks

##  <a name="rebuildpalette"></a>  CMFCColorButton::RebuildPalette

指定したパレットまたは既定のシステムパレットに対して、保護されたデータメンバーを初期化します。`m_pPalette`

```
void RebuildPalette(CPalette* pPal);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pPal*|から論理パレットまたは NULL へのポインター。 NULL の場合、既定のシステムパレットが使用されます。|

##  <a name="setcolor"></a>  CMFCColorButton::SetColor

ボタンの色を指定します。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
からRGB 値。

### <a name="remarks"></a>Remarks

##  <a name="setcolorname"></a>  CMFCColorButton::SetColorName

色の名前を指定します。

```
static void SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
から色の RGB 値。

*strName*<br/>
から色の名前。

### <a name="remarks"></a>Remarks

色の名前の一覧は、アプリケーションごとにグローバルです。 その結果、このメソッドはパラメーターを[Cmfccolorbar:: SetColorName](../../mfc/reference/cmfccolorbar-class.md#setcolorname)に転送します。

##  <a name="setcolumnsnumber"></a>  CMFCColorButton::SetColumnsNumber

ユーザーのカラー選択プロセス中にユーザーに表示される色の表に表示される列の数を定義します。

```
void SetColumnsNumber(int nColumns);
```

### <a name="parameters"></a>パラメーター

*nColumns*<br/>
から列の数を指定します。

### <a name="remarks"></a>Remarks

ユーザーは、事前に定義された色のテーブルを表示するポップアップカラーバーから色を選択できます。 このメソッドを使用して、テーブル内の列の数を定義します。

##  <a name="setdocumentcolors"></a>CMFCColorButton:: SetDocumentColors

一連の色とセット名を指定します。 色のセットは、 [Cmfccolorbar クラス](../../mfc/reference/cmfccolorbar-class.md)オブジェクトを使用して表示されます。

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
からドキュメントの色のセットと共に表示されるラベルを指定します。

*lstColors*<br/>
からRGB 値のリストへの参照。

### <a name="remarks"></a>Remarks

オブジェクト`CMFCColorButton`は、 [cmfccolorbar クラス](../../mfc/reference/cmfccolorbar-class.md)オブジェクトに転送される RGB 値の一覧を保持します。 カラーバーが表示されている場合、これらの色は、 *lpszlabel*パラメーターによってラベルが指定されている特殊なセクションに表示されます。

##  <a name="setpalette"></a>  CMFCColorButton::SetPalette

ポップアップカラーバーに表示する標準の色を指定します。

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>パラメーター

*pPalette*<br/>
からカラーパレットへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="sizetocontent"></a>CMFCColorButton:: SizeToContent

テキストとイメージに合わせてボタンコントロールのサイズを変更します。

```
virtual CSize SizeToContent(BOOL bCalcOnly=FALSE);
```

### <a name="parameters"></a>パラメーター

*bCalcOnly*<br/>
から0以外の場合は、ボタンコントロールの新しいサイズが計算されますが、実際のサイズは変更されません。

### <a name="return-value"></a>戻り値

新しいボタンコントロールのサイズを指定するオブジェクト。`CSize`

### <a name="remarks"></a>Remarks

##  <a name="updatecolor"></a>CMFCColorButton:: UpdateColor

ユーザーが色のボタンをクリックしたときに表示されるカラーバーから色を選択すると、フレームワークによって呼び出されます。

```
virtual void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
からユーザーが選択した色。

### <a name="remarks"></a>Remarks

関数`UpdateColor`は、現在選択されているボタンの色を変更し、BN_CLICKED 標準通知を使用して WM_COMMAND メッセージを送信することによってその親に通知します。 [Cmfccolorbutton:: getcolor](#getcolor)メソッドを使用して、選択した色を取得します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton クラス](../../mfc/reference/cmfcbutton-class.md)<br/>
[CMFCColorBar クラス](../../mfc/reference/cmfccolorbar-class.md)<br/>
[CMFCColorButton::OnShowColorPopup](#onshowcolorpopup)<br/>
[COLORREF](/windows/win32/gdi/colorref)<br/>
[CPalette クラス](../../mfc/reference/cpalette-class.md)<br/>
[CArray クラス](../../mfc/reference/carray-class.md)<br/>
[CList クラス](../../mfc/reference/clist-class.md)<br/>
[CString](../../atl-mfc-shared/reference/cstringt-class.md)
