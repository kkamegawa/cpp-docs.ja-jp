---
title: CMFCToolTipCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetIconSize
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetParams
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawBorder
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawLabel
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnFillBackground
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetFixedWidth
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetHotRibbonButton
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetLocation
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetParams
helpviewer_keywords:
- CMFCToolTipCtrl [MFC], GetIconSize
- CMFCToolTipCtrl [MFC], GetParams
- CMFCToolTipCtrl [MFC], OnDrawBorder
- CMFCToolTipCtrl [MFC], OnDrawDescription
- CMFCToolTipCtrl [MFC], OnDrawIcon
- CMFCToolTipCtrl [MFC], OnDrawLabel
- CMFCToolTipCtrl [MFC], OnDrawSeparator
- CMFCToolTipCtrl [MFC], OnFillBackground
- CMFCToolTipCtrl [MFC], SetDescription
- CMFCToolTipCtrl [MFC], SetFixedWidth
- CMFCToolTipCtrl [MFC], SetHotRibbonButton
- CMFCToolTipCtrl [MFC], SetLocation
- CMFCToolTipCtrl [MFC], SetParams
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
ms.openlocfilehash: 5376fd21f84411c86ade564d7c76d073ccb909a6
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273687"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl クラス

[CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)に基づいた拡張ツールヒントの実装です。 `CMFCToolTipCtrl` クラスに基づいたツールヒントは、アイコン、ラベル、および説明を表示できます。 グラデーション塗りつぶし、カスタム テキストと境界線の色、太字、角を丸く表示、またはバルーン形式を使用して、外観をカスタマイズできます。

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

## <a name="syntax"></a>構文

```
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|既定のコンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCToolTipCtrl:: GetIconSize](#geticonsize)|ツールヒント内のアイコンのサイズを返します。|
|[CMFCToolTipCtrl:: GetParams](#getparams)|ツールヒントの表示設定を返します。|
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|ツールヒントの枠線を描画します。|
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||
|[CMFCToolTipCtrl:: OnDrawIcon](#ondrawicon)|ツールヒント内にアイコンを表示します。|
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|ツールヒントのラベルを描画するか、ラベルのサイズを計算します。|
|[CMFCToolTipCtrl:: OnDrawSeparator](#ondrawseparator)|ツールヒント内のラベルと説明の間の区分線を描画します。|
|[CMFCToolTipCtrl:: OnFillBackground](#onfillbackground)|ツールヒントの背景を塗りつぶします。|
|[CMFCToolTipCtrl:: SetDescription](#setdescription)|ツールヒントに表示される説明を設定します。|
|[CMFCToolTipCtrl:: SetFixedWidth](#setfixedwidth)||
|[CMFCToolTipCtrl:: SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl:: SetLocation](#setlocation)||
|[CMFCToolTipCtrl:: SetParams](#setparams)|`CMFCToolTipInfo` オブジェクトを使用して、ツールヒントの外観を指定します。|

## <a name="remarks"></a>Remarks

、 `CMFCToolTipCtrl`、 `CMFCToolTipInfo`および[CTooltipManager クラス](../../mfc/reference/ctooltipmanager-class.md)オブジェクトを一緒に使用して、カスタマイズされたツールヒントをアプリケーションに実装します。

たとえば、バルーン形式のツールヒントを使用するには、次の手順に従います。

1. [CWinAppEx Class](../../mfc/reference/cwinappex-class.md)メソッドを使用して、アプリケーションでツールヒントマネージャーを初期化します。

2. `CMFCToolTipInfo` 構造体を作成し、必要な表示スタイルを指定します。

```
CMFCToolTipInfo params;
params.m_bBoldLabel = FALSE;
params.m_bDrawDescription = FALSE;
params.m_bDrawIcon = FALSE;
params.m_bRoundedCorners = TRUE;
params.m_bDrawSeparator = FALSE;
if (m_bCustomColors)
{
    params.m_clrFill = RGB (255, 255, 255);
    params.m_clrFillGradient = RGB (228, 228, 240);
    params.m_clrText = RGB (61, 83, 80);
    params.m_clrBorder = RGB (144, 149, 168);

}
```
3. [CTooltipManager:: SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams)メソッドを使用して、 `CMFCToolTipInfo`オブジェクトで定義されているスタイルを使用して、アプリケーションのすべてのツールヒントの visual スタイルを設定します。

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```
`CMFCToolTipCtrl` から新しいクラスを派生させて、ツールヒントの動作や描画を制御することもできます。 新しいツールヒント コントロール クラスを指定するには、`CTooltipManager::SetTooltipParams` メソッドを使用します。

```
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```
既定のツールヒント コントロール クラスを復元し、ツールヒントの外観を既定の状態にリセットするには、`SetTooltipParams` のランタイム クラスとツールヒント情報パラメーターに NULL を指定します。

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>例

次の例では、`CMFCToolTipCtrl` オブジェクトを作成し、ツールヒントに表示される説明とツールヒント コントロールの幅を設定する方法を示します。

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtooltipctrl

##  <a name="cmfctooltipctrl"></a>CMFCToolTipCtrl:: CMFCToolTipCtrl

```
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>パラメーター

から*Pparams*<br/>

### <a name="remarks"></a>Remarks

##  <a name="geticonsize"></a>CMFCToolTipCtrl:: GetIconSize

ツールヒント内のアイコンのサイズを返します。

```
virtual CSize GetIconSize();
```

### <a name="return-value"></a>戻り値

アイコンのサイズ (ピクセル単位)。

##  <a name="getparams"></a>CMFCToolTipCtrl:: GetParams

ツールヒントの表示設定を返します。

```
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>戻り値

[CMFCToolTipInfo クラス](../../mfc/reference/cmfctooltipinfo-class.md)オブジェクトに格納されている、現在のツールヒントの表示設定。

##  <a name="ondrawborder"></a>  CMFCToolTipCtrl::OnDrawBorder

ツールヒントの枠線を描画します。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

*rect*<br/>
からツールヒントの外接する四角形。

*clrLine*<br/>
から罫線の色。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドして、ツールヒントの境界線の外観をカスタマイズします。

##  <a name="ondrawdescription"></a>  CMFCToolTipCtrl::OnDrawDescription

```
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>パラメーター

から*pDC*<br/>
から*rect*<br/>
から*Bcalconly*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="ondrawicon"></a>CMFCToolTipCtrl:: OnDrawIcon

ツールヒント内にアイコンを表示します。

```
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

*rectImage*<br/>
からアイコンの座標。

### <a name="return-value"></a>戻り値

アイコンが描画された場合は TRUE。 それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

カスタムアイコンを表示するには、派生クラスでこのメソッドをオーバーライドします。 また、 [CMFCToolTipCtrl:: GetIconSize](#geticonsize)をオーバーライドして、ツールヒントがテキストと説明のレイアウトを正しく計算できるようにする必要があります。

##  <a name="ondrawlabel"></a>  CMFCToolTipCtrl::OnDrawLabel

ツールヒントのラベルを描画するか、ラベルのサイズを計算します。

```
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

*rect*<br/>
からラベル領域の外接する四角形。

*bCalcOnly*<br/>
からTRUE の場合、ラベルは描画されません。

### <a name="return-value"></a>戻り値

ラベルのサイズ (ピクセル単位)。

### <a name="remarks"></a>Remarks

ツールヒントラベルの外観をカスタマイズする場合は、派生クラスでこのメソッドをオーバーライドします。

##  <a name="ondrawseparator"></a>CMFCToolTipCtrl:: OnDrawSeparator

ツールヒント内のラベルと説明の間の区分線を描画します。

```
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

*x1*<br/>
から区切り記号の左端の水平方向の座標。

*×*<br/>
から区切り記号の右端の水平方向の座標。

*Y*<br/>
から区切り記号の垂直座標。

### <a name="remarks"></a>Remarks

既定の実装では、点 (x1, y) から点 (x2, y) までの線を描画します。

派生クラスでこのメソッドをオーバーライドして、区切り記号の外観をカスタマイズします。

##  <a name="onfillbackground"></a>CMFCToolTipCtrl:: OnFillBackground

ツールヒントの背景を塗りつぶします。

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

*rect*<br/>
から塗りつぶす領域の外接する四角形を指定します。

*clrText*<br/>
からツールヒントの前景色。

*clrLine*<br/>
から罫線の色、およびラベルと説明の間の区切り記号の線。

### <a name="remarks"></a>Remarks

既定の実装では、 *rect*によって指定された四角形が、 [CMFCToolTipCtrl:: setparams](#setparams)の最新の呼び出しで指定された色またはパターンで塗りつぶされます。

ツールヒントの外観をカスタマイズする場合は、派生クラスでこのメソッドをオーバーライドします。

##  <a name="setdescription"></a>CMFCToolTipCtrl:: SetDescription

ツールヒントに表示される説明を設定します。

```
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>パラメーター

*strdesrci*<br/>
から説明のテキスト。

### <a name="remarks"></a>Remarks

説明のテキストは、ツールヒントの区切り記号の下に表示されます。

##  <a name="setfixedwidth"></a>CMFCToolTipCtrl:: SetFixedWidth

```
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>パラメーター

から*N幅標準*<br/>
から*nWidthLargeImage*<br/>

### <a name="remarks"></a>Remarks

##  <a name="sethotribbonbutton"></a>CMFCToolTipCtrl:: SetHotRibbonButton

```
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>パラメーター

から準備中*Bbonbutton*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setlocation"></a>  CMFCToolTipCtrl::SetLocation

```
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>パラメーター

から*pt*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setparams"></a>CMFCToolTipCtrl:: SetParams

[CMFCToolTipInfo クラス](../../mfc/reference/cmfctooltipinfo-class.md)オブジェクトを使用して、ツールヒントの外観を指定します。

```
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>パラメーター

*pParams*<br/>
から表示パラメーターを格納している[CMFCToolTipInfo クラス](../../mfc/reference/cmfctooltipinfo-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

ツールヒントが表示されるたびに、 *Pparams*によって指定された色と視覚スタイルを使用して描画されます。 *Pparams*の値はプロテクトメンバーに格納され`m_Params`ます。このメンバーには、 [CMFCToolTipCtrl:: OnDrawBorder](#ondrawborder)、 [CMFCToolTipCtrl:: OnDrawIcon](#ondrawicon)、 [CMFCToolTipCtrl:: OnDrawLabel をオーバーライドする派生クラスからアクセスできます。](#ondrawlabel)、 [CMFCToolTipCtrl:: OnDrawSeparator](#ondrawseparator)、または[CMFCToolTipCtrl:: onfillbackground](#onfillbackground)を指定すると、指定した外観が維持されます。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CToolTipCtrl クラス](../../mfc/reference/ctooltipctrl-class.md)<br/>
[CTooltipManager クラス](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipInfo クラス](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)
