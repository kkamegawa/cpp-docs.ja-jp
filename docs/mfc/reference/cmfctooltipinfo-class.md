---
title: CMFCToolTipInfo クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBalloonTooltip
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBoldLabel
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bRoundedCorners
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bVislManagerTheme
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrBorder
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFill
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFillGradient
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrText
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nGradientAngle
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nMaxDescrWidth
helpviewer_keywords:
- CMFCToolTipInfo [MFC], m_bBalloonTooltip
- CMFCToolTipInfo [MFC], m_bBoldLabel
- CMFCToolTipInfo [MFC], m_bDrawDescription
- CMFCToolTipInfo [MFC], m_bDrawIcon
- CMFCToolTipInfo [MFC], m_bDrawSeparator
- CMFCToolTipInfo [MFC], m_bRoundedCorners
- CMFCToolTipInfo [MFC], m_bVislManagerTheme
- CMFCToolTipInfo [MFC], m_clrBorder
- CMFCToolTipInfo [MFC], m_clrFill
- CMFCToolTipInfo [MFC], m_clrFillGradient
- CMFCToolTipInfo [MFC], m_clrText
- CMFCToolTipInfo [MFC], m_nGradientAngle
- CMFCToolTipInfo [MFC], m_nMaxDescrWidth
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
ms.openlocfilehash: b38c3a62cca376ef7a19a111fe3a34c923983d1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338221"
---
# <a name="cmfctooltipinfo-class"></a>CMFCToolTipInfo クラス

ツールヒントの外観に関する情報を格納します。

## <a name="syntax"></a>構文

```
class CMFCToolTipInfo
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCToolTipInfo::operator=](#operator_eq)||

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CMFCToolTipInfo::m_bBalloonTooltip](#m_bballoontooltip)|ツールヒントの外観をバルーンにするかどうかを示すブール値変数。|
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|ツールヒントのラベルを太字のフォントで表示するかどうかを示すブール値変数。|
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|ツールヒントに説明を含めるかどうかを示すブール値変数。|
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|ツールヒントにアイコンを含めるかどうかを示すブール値変数。|
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|ツールヒントのラベルとツールヒントの説明の間に区切り記号を表示するかどうかを示すブール値変数。|
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|ツールヒントの角を丸くするかどうかを示すブール値変数。|
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|ビジュアル マネージャーで、ツールヒントの外観を制御する必要があるかどうかを示すブール値変数 (を参照してください[CMFCVisualManager クラス](../../mfc/reference/cmfcvisualmanager-class.md))。|
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|ツールヒントの境界線の色。|
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|ツールヒントの背景の色。|
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|ツールヒントのグラデーション塗りの色。|
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|ツールヒントのテキストの色。|
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|ツールヒントのグラデーション塗りの角度。|
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|ツールヒントの説明で可能な最大幅 (ピクセル)。|

## <a name="remarks"></a>Remarks

使用[CMFCToolTipCtrl クラス](../../mfc/reference/cmfctooltipctrl-class.md)、 `CMFCToolTipInfo`、および[CTooltipManager クラス](../../mfc/reference/ctooltipmanager-class.md)アプリケーションでカスタマイズされたツールヒントを実装するためにします。 これらのツールヒントのクラスを使用する方法の例は、次を参照してください。、 [CMFCToolTipCtrl クラス](../../mfc/reference/cmfctooltipctrl-class.md)トピック。

## <a name="example"></a>例

次の例では、`CMFCToolTipInfo` クラスのさまざまなメンバー変数の値を設定する方法を示します。

[!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtooltipctrl.h

##  <a name="m_bballoontooltip"></a>  CMFCToolTipInfo::m_bBalloonTooltip

すべてのツールヒントの表示スタイルを指定します。

```
BOOL m_bBalloonTooltip;
```

### <a name="remarks"></a>Remarks

ツールヒントがバルーン形式を使用することを示す TRUE、FALSE ツールヒントが四角形のスタイルを使用することを示します。

##  <a name="m_bboldlabel"></a>  CMFCToolTipInfo::m_bBoldLabel

ツールヒントのテキストのフォントが太字かどうかを指定します。

```
BOOL m_bBoldLabel;
```

### <a name="remarks"></a>Remarks

このメンバーを設定する表示のツールヒント テキストを太字のフォントまたは FALSE の場合は true フォントを太字でないとツールヒントのラベルを表示します。

##  <a name="m_bdrawdescription"></a>  CMFCToolTipInfo::m_bDrawDescription

各ヒントが説明テキストを表示するかどうかを指定します。

```
BOOL m_bDrawDescription;
```

### <a name="remarks"></a>Remarks

このメンバーは、表示、説明、または説明を非表示にする場合は FALSE の場合は true に設定します。 ツールヒントの説明を指定するには呼び出すことによって[CMFCToolTipCtrl::SetDescription](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)

##  <a name="m_bdrawicon"></a>  CMFCToolTipInfo::m_bDrawIcon

すべてのツールヒントにアイコンを表示するかどうかを指定します。

```
BOOL m_bDrawIcon;
```

### <a name="remarks"></a>Remarks

各のツールヒントにアイコンが表示する場合は TRUE または FALSE アイコンなしのツールヒントを表示するには、このメンバーを設定します。

##  <a name="m_bdrawseparator"></a>  CMFCToolTipInfo::m_bDrawSeparator

各ツールヒントのラベルとその説明の間の区切り記号があるかどうかを指定します。

```
BOOL m_bDrawSeparator;
```

### <a name="remarks"></a>Remarks

ツールヒントのラベルと説明、間の区切り記号を表示する場合は TRUE または FALSE 区切り記号なしでツールヒントを表示するには、このメンバーを設定します。

##  <a name="m_broundedcorners"></a>  CMFCToolTipInfo::m_bRoundedCorners

すべてのツールヒントの角が丸いかどうかを指定します。

```
BOOL m_bRoundedCorners;
```

### <a name="remarks"></a>Remarks

このメンバーを設定する丸め表示角ヒント、または FALSE の場合は true ツール ヒントの四角形の角を表示します。

##  <a name="m_clrborder"></a>  CMFCToolTipInfo::m_clrBorder

すべてのツールヒントの枠線の色を指定します。

```
COLORREF m_clrBorder;
```

##  <a name="m_clrfill"></a>  CMFCToolTipInfo::m_clrFill

ツールヒントの背景の色を指定します。

```
COLORREF m_clrFill;
```

### <a name="remarks"></a>Remarks

場合[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) -1 で、ツールヒントの背景色は`m_clrFill`します。 それ以外の場合、`m_clrFill`グラデーションの最初の色を指定し、`m_clrFillGradient`グラデーションの終了色を指定します。 [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)のグラデーションの方向を決定します。

##  <a name="m_clrfillgradient"></a>  CMFCToolTipInfo::m_clrFillGradient

ツールヒントの背景のグラデーションの終了色を指定します。

```
COLORREF m_clrFillGradient;
```

### <a name="remarks"></a>Remarks

場合`m_clrFillGradient`-1 で、グラデーションはありません。 それ以外の場合、初期のグラデーションの色がで指定された[CMFCToolTipInfo::m_clrFill](#m_clrfill)によりグラデーションの終了色を指定`m_clrFillGradient`します。 [CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)のグラデーションの方向を決定します。

##  <a name="m_clrtext"></a>  CMFCToolTipInfo::m_clrText

すべてのツールヒントのテキストの色を指定します。

```
COLORREF m_clrText;
```

##  <a name="m_ngradientangle"></a>  CMFCToolTipInfo::m_nGradientAngle

ツールヒントの背景に描画されるグラデーションの角度を指定します。

```
int m_nGradientAngle;
```

### <a name="remarks"></a>Remarks

`m_nGradientAngle` ツールヒントの背景のグラデーションを水平方向のオフセットを度単位の角度を指定します。 場合`m_nGradientAngle`が 0 のグラデーションは、左から右に描画されます場合、。 場合`m_nGradientAngle`は 1 ~ 360 の場合は、間、グラデーションが右回りに回転、その角度。 場合`m_nGradientAngle`-1 で、既定値は、グラデーションは、上から下に描画されます。 これは、設定と同じ`m_nGradientAngle`を 90 にします。

[CMFCToolTipInfo::m_clrFill](#m_clrfill) `clrFill`グラデーションの最初の色を指定し、 [CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient) `clrFillGradient`グラデーションの終了色を指定します。 場合`m_clrFillGradient`-1 で、グラデーションはありません。

##  <a name="m_nmaxdescrwidth"></a>  CMFCToolTipInfo::m_nMaxDescrWidth

各ヒントに表示される説明の最大の幅を指定します。 説明の幅は、指定した値を超えている場合は、テキストがラップされます。

```
int m_nMaxDescrWidth;
```

##  <a name="m_bvislmanagertheme"></a>  CMFCToolTipInfo::m_bVislManagerTheme

アプリケーションのビジュアル マネージャーがすべてのツールヒントの外観を制御するかどうかを指定します。

```
BOOL m_bVislManagerTheme;
```

### <a name="remarks"></a>Remarks

場合`m_bVislManagerTheme`が true の場合、すべてのツールヒントに、新しい要求[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)そのオブジェクトの外観を決定する値を使用して、画面に表示する前に、アプリケーションのビジュアル マネージャーから。 他のメンバー、 [CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)は無視されます。

##  <a name="operator_eq"></a>  CMFCToolTipInfo::operator=

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```

### <a name="parameters"></a>パラメーター

[in]*src*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CTooltipManager クラス](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipCtrl クラス](../../mfc/reference/cmfctooltipctrl-class.md)
