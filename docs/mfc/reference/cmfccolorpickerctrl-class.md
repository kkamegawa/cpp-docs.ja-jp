---
title: CMFCColorPickerCtrl クラス
ms.date: 11/19/2018
f1_keywords:
- CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::CMFCColorPickerCtrl
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::GetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SelectCellHexagon
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHLS
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetHue
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminance
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetLuminanceBarWidth
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetOriginalColor
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetPalette
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetSaturation
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::SetType
- AFXCOLORPICKERCTRL/CMFCColorPickerCtrl::DrawCursor
helpviewer_keywords:
- CMFCColorPickerCtrl [MFC], CMFCColorPickerCtrl
- CMFCColorPickerCtrl [MFC], GetColor
- CMFCColorPickerCtrl [MFC], GetHLS
- CMFCColorPickerCtrl [MFC], GetHue
- CMFCColorPickerCtrl [MFC], GetLuminance
- CMFCColorPickerCtrl [MFC], GetSaturation
- CMFCColorPickerCtrl [MFC], SelectCellHexagon
- CMFCColorPickerCtrl [MFC], SetColor
- CMFCColorPickerCtrl [MFC], SetHLS
- CMFCColorPickerCtrl [MFC], SetHue
- CMFCColorPickerCtrl [MFC], SetLuminance
- CMFCColorPickerCtrl [MFC], SetLuminanceBarWidth
- CMFCColorPickerCtrl [MFC], SetOriginalColor
- CMFCColorPickerCtrl [MFC], SetPalette
- CMFCColorPickerCtrl [MFC], SetSaturation
- CMFCColorPickerCtrl [MFC], SetType
- CMFCColorPickerCtrl [MFC], DrawCursor
ms.assetid: b9bbd03c-beb0-4b55-9765-9985fd05e5dc
ms.openlocfilehash: 1977717ee590acb63655ba21bfa5eb6bfe7c9bd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403795"
---
# <a name="cmfccolorpickerctrl-class"></a>CMFCColorPickerCtrl クラス

`CMFCColorPickerCtrl`クラスには、色の選択に使用するための機能が用意されています。

## <a name="syntax"></a>構文

```
class CMFCColorPickerCtrl : public CButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCColorPickerCtrl::CMFCColorPickerCtrl](#cmfccolorpickerctrl)|`CMFCColorPickerCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCColorPickerCtrl::GetColor](#getcolor)|ユーザーが選択した色を取得します。|
|[CMFCColorPickerCtrl::GetHLS](#gethls)|ユーザーが選択した色の色合い、明るさ、および鮮やかさの値を取得します。|
|[CMFCColorPickerCtrl::GetHue](#gethue)|ユーザーが選択した色の色合いを取得します。|
|[CMFCColorPickerCtrl::GetLuminance](#getluminance)|ユーザーが選択した色の輝度コンポーネントを取得します。|
|[CMFCColorPickerCtrl::GetSaturation](#getsaturation)|ユーザーが選択した色の彩度 コンポーネントを取得します。|
|[CMFCColorPickerCtrl::SelectCellHexagon](#selectcellhexagon)|現在の色を RGB 色の指定された要素または指定したセルの六角形で定義された色に設定します。|
|[CMFCColorPickerCtrl::SetColor](#setcolor)|RGB 色の値を指定するには、現在の色を設定します。|
|[CMFCColorPickerCtrl::SetHLS](#sethls)|現在の色を指定した HLS 色の値に設定します。|
|[CMFCColorPickerCtrl::SetHue](#sethue)|現在選択されている色の色合いを変更します。|
|[CMFCColorPickerCtrl::SetLuminance](#setluminance)|現在選択されている色の輝度コンポーネントを変更します。|
|[CMFCColorPickerCtrl::SetLuminanceBarWidth](#setluminancebarwidth)|カラー ピッカー コントロールでは、輝度バーの幅を設定します。|
|[CMFCColorPickerCtrl::SetOriginalColor](#setoriginalcolor)|選択した初期の色を設定します。|
|[CMFCColorPickerCtrl::SetPalette](#setpalette)|現在のカラー パレットを設定します。|
|[CMFCColorPickerCtrl::SetSaturation](#setsaturation)|現在選択されている色の彩度を変更します。|
|[CMFCColorPickerCtrl::SetType](#settype)|表示するカラー ピッカー コントロールの種類を設定します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCColorPickerCtrl::DrawCursor](#drawcursor)|選択した色をポイントするカーソルが表示される前に、フレームワークによって呼び出されます。|

## <a name="remarks"></a>Remarks

標準色が、六角形カラー パレットから選択されており、輝度バーからカスタムの色が選択されている色が赤/緑/青表記または色合い/satuaration/輝度表記を使用して指定された場所。

次の図はいくつか`CMFCColorPickerCtrl`オブジェクト。

![CMFCColorPickerCtrl ダイアログ ボックス](../../mfc/reference/media/colorpicker.png "CMFCColorPickerCtrl ダイアログ ボックス")

`CMFCColorPickerCtrl`スタイルの 2 つのペアをサポートします。 16 進数と HEX_GREYSCALE スタイルは、標準の色の選択に適しています。 ピッカーと輝度のスタイルは、カスタムの色の選択に適しています。

組み込むことは、次の手順を実行、`CMFCColorPickerCtrl`ダイアログ ボックスにコントロール。

1. 使用する場合、 **ClassWizard**、ダイアログ ボックスのテンプレートに新しいボタン コントロールを挿入 (ため、`CMFCColorPickerCtrl`クラスが継承、`CButton`クラス)。

1. ダイアログ ボックス クラスに新しいボタン コントロールに関連付けられているメンバー変数を挿入します。 変数の型を変更し、`CButton`に`CMFCColorPickerCtrl`します。

1. 挿入、 `WM_INITDIALOG`  ダイアログ ボックスのクラスのメッセージ ハンドラー。 ハンドラーで、種類、パレット、およびの初期の選択した色を設定、`CMFCColorPickerCtrl`コントロール。

## <a name="example"></a>例

次の例は、構成する方法を示します、`CMFCColorPickerCtrl`オブジェクトでさまざまなメソッドを使用して、`CMFCColorPickerCtrl`クラス。 例では、その色、色合い、明るさ、および彩度を設定する方法と、選択コントロールの種類を設定する方法を示します。 この例は、[新しいコントロール サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_NewControls#4](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#5](../../mfc/reference/codesnippet/cpp/cmfccolorpickerctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCColorPickerCtrl](../../mfc/reference/cmfccolorpickerctrl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcolorpickerctrl.h

##  <a name="cmfccolorpickerctrl"></a>  CMFCColorPickerCtrl::CMFCColorPickerCtrl

`CMFCColorPickerCtrl` オブジェクトを構築します。

```
CMFCColorPickerCtrl();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="drawcursor"></a>  CMFCColorPickerCtrl::DrawCursor

選択した色をポイントするカーソルが表示される前に、フレームワークによって呼び出されます。

```
virtual void DrawCursor(
    CDC* pDC,
    const CRect& rect);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

*rect*<br/>
[in]選択した色の周りの四角形の領域を指定します。

### <a name="remarks"></a>Remarks

選択した色をポイントするカーソルの形状を変更する必要がある場合は、このメソッドをオーバーライドします。

##  <a name="getcolor"></a>  CMFCColorPickerCtrl::GetColor

ユーザーが選択した色を取得します。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>戻り値

選択された色の RGB 値。

### <a name="remarks"></a>Remarks

##  <a name="gethls"></a>  CMFCColorPickerCtrl::GetHLS

ユーザーが選択した色の色合い、明るさ、および鮮やかさの値を取得します。

```
void GetHLS(
    double* hue,
    double* luminance,
    double* saturation);
```

### <a name="parameters"></a>パラメーター

*Hue*<br/>
[out]Hue の情報を受け取る double 型の変数へのポインター。

*輝度*<br/>
[out]輝度情報を受け取る double 型の変数へのポインター。

*saturation*<br/>
[out]鮮やかさの情報を受け取る double 型の変数へのポインター。

### <a name="remarks"></a>Remarks

##  <a name="gethue"></a>  CMFCColorPickerCtrl::GetHue

ユーザーが選択した色の色合いを取得します。

```
double GetHue() const;
```

### <a name="return-value"></a>戻り値

選択された色の色合いコンポーネント。

### <a name="remarks"></a>Remarks

##  <a name="getluminance"></a>  CMFCColorPickerCtrl::GetLuminance

ユーザーが選択した色の輝度コンポーネントを取得します。

```
double GetLuminance() const;
```

### <a name="return-value"></a>戻り値

選択された色の輝度コンポーネント。

### <a name="remarks"></a>Remarks

##  <a name="getsaturation"></a>  CMFCColorPickerCtrl::GetSaturation

ユーザーが選択した色の鮮やかさの値を取得します。

```
double GetSaturation() const;
```

### <a name="return-value"></a>戻り値

選択された色の彩度。

### <a name="remarks"></a>Remarks

##  <a name="selectcellhexagon"></a>  CMFCColorPickerCtrl::SelectCellHexagon

現在の色を RGB 色の指定された要素または指定したセルの六角形で定義された色に設定します。

```
void SelectCellHexagon(
    BYTE R,
    BYTE G,
    BYTE B);

BOOL SelectCellHexagon(
    int x,
    int y);
```

### <a name="parameters"></a>パラメーター

*R*<br/>
[in]赤のカラー コンポーネント。

*G*<br/>
[in]緑のカラー コンポーネント。

*B*<br/>
[in]青のコンポーネント。

*x*<br/>
[in]セルの六角形を指すと、カーソルの x 座標。

*y*<br/>
[in]セルの六角形を指すと、カーソルの y 座標。

### <a name="return-value"></a>戻り値

このメソッドの 2 番目のオーバー ロードは、常に FALSE を返します。

### <a name="remarks"></a>Remarks

現在の色を色の選択コントロールに対応する色にこのメソッドのセットの最初のオーバー ロードには、赤、緑、および青の色要素の指定しました。

このメソッドの 2 番目のオーバー ロードは、指定したカーソル位置によってポイントされているセルの六角形の色に、現在の色を設定します。

##  <a name="setcolor"></a>  CMFCColorPickerCtrl::SetColor

RGB 色の値を指定するには、現在の色を設定します。

```
void SetColor(COLORREF Color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
[in]RGB 色の値。

### <a name="remarks"></a>Remarks

##  <a name="sethls"></a>  CMFCColorPickerCtrl::SetHLS

現在の色を指定した HLS 色の値に設定します。

```
void SetHLS(
    double hue,
    double luminance,
    double saturation,
    BOOL bInvalidate=TRUE);
```

### <a name="parameters"></a>パラメーター

*Hue*<br/>
[in]色合いの値。

*輝度*<br/>
[in]輝度値。

*saturation*<br/>
[in]鮮やかさの値。

*bInvalidate*<br/>
[in]ウィンドウが強制的にすぐに新しい色を更新する場合は TRUEそれ以外の場合、FALSE です。 既定では TRUE です。

### <a name="remarks"></a>Remarks

##  <a name="sethue"></a>  CMFCColorPickerCtrl::SetHue

現在選択されている色の色合いを変更します。

```
void SetHue(double Hue);
```

### <a name="parameters"></a>パラメーター

*Hue*<br/>
[in]色合いの値。

### <a name="remarks"></a>Remarks

##  <a name="setluminance"></a>  CMFCColorPickerCtrl::SetLuminance

現在選択されている色の明るさを変更します。

```
void SetLuminance(double Luminance);
```

### <a name="parameters"></a>パラメーター

*輝度*<br/>
[in]輝度値。

### <a name="remarks"></a>Remarks

##  <a name="setluminancebarwidth"></a>  CMFCColorPickerCtrl::SetLuminanceBarWidth

カラー ピッカー コントロールでは、輝度バーの幅を設定します。

```
void SetLuminanceBarWidth(int w);
```

### <a name="parameters"></a>パラメーター

*w*<br/>
[in]輝度バーの幅はピクセル単位で測定されます。

### <a name="remarks"></a>Remarks

これには輝度バーのサイズを変更するには、このメソッドを使用して、**カスタム**カラー ピッカー コントロールのタブ。 *W*輝度バーの新しい幅を指定します。 幅の値には、クライアント領域の幅の 4 分の 3 を超えている場合は無視されます。

##  <a name="setoriginalcolor"></a>  CMFCColorPickerCtrl::SetOriginalColor

選択した初期の色を設定します。

```
void SetOriginalColor(COLORREF ref);
```

### <a name="parameters"></a>パラメーター

*ref*<br/>
[in]RGB 色の値。

### <a name="remarks"></a>Remarks

カラー ピッカー コントロールが初期化されるときに、このメソッドを呼び出します。

##  <a name="setpalette"></a>  CMFCColorPickerCtrl::SetPalette

現在のカラー パレットを設定します。

```
void SetPalette(CPalette* pPalette);
```

### <a name="parameters"></a>パラメーター

*pPalette*<br/>
[in]カラー パレットを指すポインター。

### <a name="remarks"></a>Remarks

色パレットは、カラー ピッカー コントロールで表示される色の配列を定義します。

##  <a name="setsaturation"></a>  CMFCColorPickerCtrl::SetSaturation

現在選択されている色の彩度を変更します。

```
void SetSaturation(double Saturation);
```

### <a name="parameters"></a>パラメーター

*彩度*<br/>
[in]鮮やかさの値。

### <a name="remarks"></a>Remarks

##  <a name="settype"></a>  CMFCColorPickerCtrl::SetType

表示するカラー ピッカー コントロールの種類を設定します。

```
void SetType(COLORTYPE colorType);
```

### <a name="parameters"></a>パラメーター

*colorType*<br/>
[in]カラー ピッカー コントロールの種類。

によって、型が定義されている、`CMFCColorPickerCtrl::COLORTYPE`列挙体。 輝度、ピッカー、16 進数および HEX_GREYSCALE のタイプがあります。 既定の種類は、選択します。

### <a name="remarks"></a>Remarks

カラー ピッカー コントロールの種類を指定するには、Windows コントロールを作成する前に、このメソッドを呼び出します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCColorDialog クラス](../../mfc/reference/cmfccolordialog-class.md)
