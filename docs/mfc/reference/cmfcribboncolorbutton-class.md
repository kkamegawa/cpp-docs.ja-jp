---
title: CMFCRibbonColorButton クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::CMFCRibbonColorButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::AddColorsGroup
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableAutomaticButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::EnableOtherButton
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetAutomaticColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::GetHighlightedColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::RemoveAllColorGroups
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColor
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorBoxSize
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColorName
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetColumns
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetDocumentColors
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::SetPalette
- AFXRIBBONCOLORBUTTON/CMFCRibbonColorButton::UpdateColor
helpviewer_keywords:
- CMFCRibbonColorButton [MFC], CMFCRibbonColorButton
- CMFCRibbonColorButton [MFC], AddColorsGroup
- CMFCRibbonColorButton [MFC], EnableAutomaticButton
- CMFCRibbonColorButton [MFC], EnableOtherButton
- CMFCRibbonColorButton [MFC], GetAutomaticColor
- CMFCRibbonColorButton [MFC], GetColor
- CMFCRibbonColorButton [MFC], GetColorBoxSize
- CMFCRibbonColorButton [MFC], GetColumns
- CMFCRibbonColorButton [MFC], GetHighlightedColor
- CMFCRibbonColorButton [MFC], RemoveAllColorGroups
- CMFCRibbonColorButton [MFC], SetColor
- CMFCRibbonColorButton [MFC], SetColorBoxSize
- CMFCRibbonColorButton [MFC], SetColorName
- CMFCRibbonColorButton [MFC], SetColumns
- CMFCRibbonColorButton [MFC], SetDocumentColors
- CMFCRibbonColorButton [MFC], SetPalette
- CMFCRibbonColorButton [MFC], UpdateColor
ms.assetid: 6b4b4ee3-8cc0-41b4-a4eb-93e8847008e1
ms.openlocfilehash: ceb686a9aca4ac126c4d61dd45975c65a9376ce9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392519"
---
# <a name="cmfcribboncolorbutton-class"></a>CMFCRibbonColorButton クラス

`CMFCRibbonColorButton` クラスは、リボン バーに追加できるカラー ボタンを実装します。 リボンのカラー ボタンは、1 つまたは複数のカラー パレットを含むドロップダウン メニューを表示します。

## <a name="syntax"></a>構文

```
class CMFCRibbonColorButton : public CMFCRibbonGallery
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonColorButton::CMFCRibbonColorButton](#cmfcribboncolorbutton)||

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonColorButton::AddColorsGroup](#addcolorsgroup)|色のグループを通常の色領域に追加します。|
|[CMFCRibbonColorButton::EnableAutomaticButton](#enableautomaticbutton)|**[自動]** ボタンを有効にするかどうかを指定します。|
|[CMFCRibbonColorButton::EnableOtherButton](#enableotherbutton)|**[その他]** ボタンを有効にします。|
|[CMFCRibbonColorButton::GetAutomaticColor](#getautomaticcolor)||
|[CMFCRibbonColorButton::GetColor](#getcolor)|現在選ばれている色を返します。|
|[CMFCRibbonColorButton::GetColorBoxSize](#getcolorboxsize)|カラー バーに表示される色要素のサイズを返します。|
|[CMFCRibbonColorButton::GetColumns](#getcolumns)||
|[CMFCRibbonColorButton::GetHighlightedColor](#gethighlightedcolor)|ポップアップ カラー パレットで現在選ばれている要素の色を返します。|
|[CMFCRibbonColorButton::RemoveAllColorGroups](#removeallcolorgroups)|通常の色領域からすべての色グループを削除します。|
|[CMFCRibbonColorButton::SetColor](#setcolor)|通常の色領域から色を選びます。|
|[CMFCRibbonColorButton::SetColorBoxSize](#setcolorboxsize)|カラー バーに表示されるすべての色要素のサイズを設定します。|
|[CMFCRibbonColorButton::SetColorName](#setcolorname)||
|[CMFCRibbonColorButton::SetColumns](#setcolumns)||
|[CMFCRibbonColorButton::SetDocumentColors](#setdocumentcolors)|ドキュメントの色領域に表示する RGB 値の一覧を指定します。|
|[CMFCRibbonColorButton::SetPalette](#setpalette)||
|[CMFCRibbonColorButton::UpdateColor](#updatecolor)||

## <a name="remarks"></a>Remarks

ユーザーがリボンのカラー ボタンを押すと、カラー バーが表示されます。 既定では、このカラー バーには通常の色領域と呼ばれる色選択パレットが含まれます。 必要に応じて、カラー バーには **[自動]** ボタン (これを使用するとユーザーは既定の色を選択できます)、および **[その他]** ボタン (追加の色を含むポップアップ カラー パレットが表示されます) を表示できます。

## <a name="example"></a>例

`CMFCRibbonColorButton` クラスのさまざまなメソッドの使用方法を次の例に示します。 この例では、 `CMFCRibbonColorButton` オブジェクトの構築、大きいイメージの設定、 **[自動]** ボタンの有効化、 **[その他]** ボタンの有効化、列数の設定、カラー バーに表示されるすべての色要素のサイズの設定、通常の色領域への色グループの追加、ドキュメントの色領域に表示する RGB 値の一覧の指定方法を示します。 このコード スニペットは、「 [クライアント サンプルの描画](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_DrawClient#3](../../mfc/reference/codesnippet/cpp/cmfcribboncolorbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonGallery](../../mfc/reference/cmfcribbongallery-class.md)

[CMFCRibbonColorButton](../../mfc/reference/cmfcribboncolorbutton-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxribboncolorbutton.h

##  <a name="addcolorsgroup"></a>  CMFCRibbonColorButton::AddColorsGroup

色のグループを通常の色領域に追加します。

```
void AddColorsGroup(
    LPCTSTR lpszName,
    const CList<COLORREF,COLORREF>& lstColors,
    BOOL bContiguousColumns=FALSE);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
[in]グループの名前。

*lstColors*<br/>
[in]色の一覧。

*bContiguousColumns*<br/>
[in]グループ内の色のアイテムの表示方法を制御します。 TRUE の場合、上下の間隔なしの色の項目が描画されます。 FALSE の場合は、色のアイテムが上下の間隔で描画されます。

### <a name="remarks"></a>Remarks

この色にポップアップする関数を使用では、いくつかの色のグループを表示します。 グループ内の色の表示方法を制御できます。

##  <a name="cmfcribboncolorbutton"></a>  CMFCRibbonColorButton::CMFCRibbonColorButton

`CMFCRibbonColorButton` オブジェクトを構築します。

```
CMFCRibbonColorButton();

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    int nSmallImageIndex,
    COLORREF color = RGB(0, 0, 0));

CMFCRibbonColorButton(
    UINT nID,
    LPCTSTR lpszText,
    BOOL bSimpleButtonLook,
    int nSmallImageIndex,
    int nLargeImageIndex,
    COLORREF color = RGB(0, 0, 0));
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
[in]ユーザーがボタンをクリックしたときに実行するコマンドのコマンド ID を指定します。

*lpszText*<br/>
[in]ボタンに表示されるテキストを指定します。

*nSmallImageIndex*<br/>
[in]ボタンを表示する小さいイメージの 0 から始まるインデックス。

*色*<br/>
[in]\(既定値は黒) ボタンの色。

*bSimpleButtonLook*<br/>
[in]TRUE の場合は、単純な四角形として、ボタンが描画されます。

*nLargeImageIndex*<br/>
[in]ボタンを表示する大きいイメージの 0 から始まるインデックス。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="enableautomaticbutton"></a>  CMFCRibbonColorButton::EnableAutomaticButton

**[自動]** ボタンを有効にするかどうかを指定します。

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE,
    LPCTSTR lpszToolTip=NULL,
    BOOL bOnTop=TRUE,
    BOOL bDrawBorder=FALSE);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
[in]ラベル、**自動**ボタンをクリックします。

*colorAutomatic*<br/>
[in]RGB 値を指定する、**自動**ボタンの既定の色。

*bEnable*<br/>
[in]TRUE の場合、**自動**ボタンが有効になります。無効になっている場合は FALSE。

*lpszToolTip*<br/>
[in]ツールヒント、**自動**ボタンをクリックします。

*bOnTop*<br/>
[in]指定するかどうか、**自動**ボタンが上部のカラー パレットの前にします。

*bDrawBorder*<br/>
[in]TRUE の場合、アプリケーションがリボンのカラー ボタンのカラー バーの周りに罫線を描画します。 カラー バーには、現在選択されている色が表示されます。 アプリケーションは境界線を描画しない場合は FALSE

##  <a name="enableotherbutton"></a>  CMFCRibbonColorButton::EnableOtherButton

**[その他]** ボタンを有効にします。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    LPCTSTR lpszToolTip=NULL);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
ボタンのラベル。

*lpszToolTip*<br/>
ツールヒントのテキスト、**他**ボタンをクリックします。

### <a name="remarks"></a>Remarks

**他**ボタンは、色のグループの下に表示されるボタン。 ユーザーがクリックすると、**他**ボタン、カラー ダイアログが表示されます。

##  <a name="getautomaticcolor"></a>  CMFCRibbonColorButton::GetAutomaticColor

現在の自動ボタンの色を取得します。

```
COLORREF GetAutomaticColor() const;
```

### <a name="return-value"></a>戻り値

現在の自動ボタンの色を表す RGB カラー値。

### <a name="remarks"></a>Remarks

自動ボタンの色が設定されて、`colorAutomatic`に渡されるパラメーター、`CMFCRibbonColorButton::EnableAutomaticButton`メソッド。

##  <a name="getcolor"></a>  CMFCRibbonColorButton::GetColor

現在選ばれている色を返します。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>戻り値

ボタンをクリックして選択した色。

##  <a name="getcolorboxsize"></a>  CMFCRibbonColorButton::GetColorBoxSize

カラー バーに表示される色要素のサイズを返します。

```
CSize GetColorBoxSize() const;
```

### <a name="return-value"></a>戻り値

ドロップダウンのカラー パレットの色のボタンのサイズ。

##  <a name="getcolumns"></a>  CMFCRibbonColorButton::GetColumns

リボンのカラー ボタン ギャラリーの表示の行の項目の数を取得します。

```
int GetColumns() const;
```

### <a name="return-value"></a>戻り値

各行のアイコンの数を返します。

### <a name="remarks"></a>Remarks

##  <a name="gethighlightedcolor"></a>  CMFCRibbonColorButton::GetHighlightedColor

ポップアップ カラー パレットで現在選択されている要素の色を返します。

```
COLORREF GetHighlightedColor() const;
```

### <a name="return-value"></a>戻り値

ポップアップ カラー パレットで現在選択されている要素の色。

##  <a name="removeallcolorgroups"></a>  CMFCRibbonColorButton::RemoveAllColorGroups

通常の色領域からすべての色グループを削除します。

```
void RemoveAllColorGroups();
```

##  <a name="setcolor"></a>  CMFCRibbonColorButton::SetColor

通常の色領域から色を選びます。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
[in]設定する色。

##  <a name="setcolorboxsize"></a>  CMFCRibbonColorButton::SetColorBoxSize

カラー バーに表示されるすべての色要素のサイズを設定します。

```
void SetColorBoxSize(CSize sizeBox);
```

### <a name="parameters"></a>パラメーター

*sizeBox*<br/>
[in]カラー パレットの色のボタンの新しいサイズ。

##  <a name="setcolorname"></a>  CMFCRibbonColorButton::SetColorName

指定した色の新しい名前を設定します。

```
static void __stdcall SetColorName(
    COLORREF color,
    const CString& strName);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
[in]色の RGB 値。

*strName*<br/>
[in]指定した色の新しい名前。

### <a name="remarks"></a>Remarks

呼び出すので、 `CMFCColorBar::SetColorName`、このメソッドは、すべての指定した色の名前を変更`CMFCColorBar`アプリケーション内のオブジェクト。

##  <a name="setcolumns"></a>  CMFCRibbonColorButton::SetColumns

ユーザーの色の選択プロセス中に、ユーザーに表示される色の一覧に表示される列の数を設定します。

```
void SetColumns(int nColumns);
```

### <a name="parameters"></a>パラメーター

*nColumns*<br/>
[in]行ごとに表示するカラー アイコンの数。

### <a name="remarks"></a>Remarks

##  <a name="setdocumentcolors"></a>  CMFCRibbonColorButton::SetDocumentColors

ドキュメントの色領域に表示する RGB 値の一覧を指定します。

```
void SetDocumentColors(
    LPCTSTR lpszLabel,
    CList<COLORREF,COLORREF>& lstColors);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
[in]ドキュメントの色で表示されるテキスト。

*lstColors*<br/>
[in]RGB 値の一覧への参照。

##  <a name="setpalette"></a>  CMFCRibbonColorButton::SetPalette

色のボタンを表示するカラー テーブルに表示する標準の色を指定します。

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>パラメーター

*pPalette*<br/>
[in]色パレットへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="updatecolor"></a>  CMFCRibbonColorButton::UpdateColor

ユーザーが色のボタンをクリックしたときに表示されるカラー テーブルから色を選択すると、フレームワークによって呼び出されます。

```
void UpdateColor(COLORREF color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
[in]ユーザーが選択した色。

### <a name="remarks"></a>Remarks

`CMFCRibbonColorButton::UpdateColor`メソッドは、現在選択されているボタンの色を変更し、BN_CLICKED 標準通知 WM_COMMAND メッセージを送信することによって、親に通知します。 使用して、 [CMFCRibbonColorButton::GetColor](#getcolor)選択した色を取得します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonGallery クラス](../../mfc/reference/cmfcribbongallery-class.md)
