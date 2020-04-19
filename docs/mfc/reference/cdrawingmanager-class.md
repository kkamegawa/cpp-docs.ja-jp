---
title: Cドローイングマネージャークラス
ms.date: 11/04/2016
f1_keywords:
- CDrawingManager
- AFXDRAWMANAGER/CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CDrawingManager
- AFXDRAWMANAGER/CDrawingManager::CreateBitmap_32
- AFXDRAWMANAGER/CDrawingManager::DrawAlpha
- AFXDRAWMANAGER/CDrawingManager::DrawRotated
- AFXDRAWMANAGER/CDrawingManager::DrawEllipse
- AFXDRAWMANAGER/CDrawingManager::DrawGradientRing
- AFXDRAWMANAGER/CDrawingManager::DrawRect
- AFXDRAWMANAGER/CDrawingManager::DrawShadow
- AFXDRAWMANAGER/CDrawingManager::Fill4ColorsGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient
- AFXDRAWMANAGER/CDrawingManager::FillGradient2
- AFXDRAWMANAGER/CDrawingManager::GrayRect
- AFXDRAWMANAGER/CDrawingManager::HighlightRect
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_ONE
- AFXDRAWMANAGER/CDrawingManager::HLStoRGB_TWO
- AFXDRAWMANAGER/CDrawingManager::HSVtoRGB
- AFXDRAWMANAGER/CDrawingManager::HuetoRGB
- AFXDRAWMANAGER/CDrawingManager::MirrorRect
- AFXDRAWMANAGER/CDrawingManager::PixelAlpha
- AFXDRAWMANAGER/CDrawingManager::PrepareShadowMask
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSL
- AFXDRAWMANAGER/CDrawingManager::RGBtoHSV
- AFXDRAWMANAGER/CDrawingManager::SetAlphaPixel
- AFXDRAWMANAGER/CDrawingManager::SetPixel
- AFXDRAWMANAGER/CDrawingManager::SmartMixColors
helpviewer_keywords:
- CDrawingManager [MFC], CDrawingManager
- CDrawingManager [MFC], CreateBitmap_32
- CDrawingManager [MFC], DrawAlpha
- CDrawingManager [MFC], DrawRotated
- CDrawingManager [MFC], DrawEllipse
- CDrawingManager [MFC], DrawGradientRing
- CDrawingManager [MFC], DrawRect
- CDrawingManager [MFC], DrawShadow
- CDrawingManager [MFC], Fill4ColorsGradient
- CDrawingManager [MFC], FillGradient
- CDrawingManager [MFC], FillGradient2
- CDrawingManager [MFC], GrayRect
- CDrawingManager [MFC], HighlightRect
- CDrawingManager [MFC], HLStoRGB_ONE
- CDrawingManager [MFC], HLStoRGB_TWO
- CDrawingManager [MFC], HSVtoRGB
- CDrawingManager [MFC], HuetoRGB
- CDrawingManager [MFC], MirrorRect
- CDrawingManager [MFC], PixelAlpha
- CDrawingManager [MFC], PrepareShadowMask
- CDrawingManager [MFC], RGBtoHSL
- CDrawingManager [MFC], RGBtoHSV
- CDrawingManager [MFC], SetAlphaPixel
- CDrawingManager [MFC], SetPixel
- CDrawingManager [MFC], SmartMixColors
ms.assetid: 9e4775ca-101b-4aa9-a85a-4d047c701215
ms.openlocfilehash: 69365b66b12d5a9284c9b097b225ba041e07b6b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506808"
---
# <a name="cdrawingmanager-class"></a>Cドローイングマネージャークラス

クラス`CDrawingManager`は、複雑な描画アルゴリズムを実装します。

## <a name="syntax"></a>構文

```
class CDrawingManager : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[Cドローイングマネージャー:: Cドローイングマネージャー](#cdrawingmanager)|`CDrawingManager` オブジェクトを構築します。|
|`CDrawingManager::~CDrawingManager`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[Cドローイングマネージャー:: CreateBitmap_32](#createbitmap_32)|アプリケーションが直接書き込むことができる、32ビットのデバイスに依存しないビットマップ (DIB) を作成します。|
|[Cドローイングマネージャー::D rawAlpha](#drawalpha)|透明または半透明のピクセルを持つビットマップを表示します。|
|[Cドローイングマネージャー::D rawRotated](#drawrotated)|指定された四角形内のソース DC コンテンツを +/-90 度回転します|
|[Cドローイングマネージャー::D rawEllipse](#drawellipse)|指定した塗りつぶしと境界線の色を使用して、楕円を描画します。|
|[Cドローイングマネージャー::D rawGradientRing](#drawgradientring)|リングを描画し、色グラデーションで塗りつぶします。|
|[Cドローイングマネージャー::D rawLine、Cドローイングマネージャー::D rawLineA](#drawline_cdrawingmanager__drawlinea)|線を描画します。|
|[Cドローイングマネージャー::D rawRect](#drawrect)|塗りつぶしと境界線の色を指定して四角形を描画します。|
|[Cドローイングマネージャー::D rawShadow](#drawshadow)|四角形の領域の影を描画します。|
|[Cドローイングマネージャー:: Fill4ColorsGradient](#fill4colorsgradient)|四角形領域に2色のグラデーションを設定します。|
|[Cドローイングマネージャー:: FillGradient](#fillgradient)|指定した色のグラデーションで四角形の領域を塗りつぶします。|
|[Cドローイングマネージャー:: FillGradient2](#fillgradient2)|指定した色のグラデーションで四角形の領域を塗りつぶします。 グラデーションの色の変化の方向も指定されます。|
|[Cドローイングマネージャー:: グレーの四角形](#grayrect)|指定した灰色の色で四角形を塗りつぶします。|
|[Cドローイングマネージャー:: HighlightRect](#highlightrect)|四角形の領域を強調表示します。|
|[Cドローイングマネージャー:: HLStoRGB_ONE](#hlstorgb_one)|HLS 表現の色を RGB 表現に変換します。|
|[Cドローイングマネージャー:: HLStoRGB_TWO](#hlstorgb_two)|HLS 表現の色を RGB 表現に変換します。|
|[Cドローイングマネージャー:: HSVtoRGB](#hsvtorgb)|色を HSV 表現から RGB 表現に変換します。|
|[Cドローイングマネージャー:: の場合は、次のようになります。](#huetorgb)|色合いの値を赤、緑、または青のコンポーネントに変換するヘルパーメソッド。|
|[Cドローイングマネージャー:: MirrorRect](#mirrorrect)|四角形の領域を反転します。|
|[Cドローイングマネージャー::P ixelAlpha](#pixelalpha)|半透明ピクセルの最終的な色を決定するヘルパーメソッド。|
|[Cドローイングマネージャー::P repareShadowMask](#prepareshadowmask)|影として使用できるビットマップを作成します。|
|[Cドローイングマネージャー:: RGBtoHSL](#rgbtohsl)|色を RGB 表現から HSL 表現に変換します。|
|[Cドローイングマネージャー:: RGBtoHSV](#rgbtohsv)|色を RGB 表現から HSV 表現に変換します。|
|[Cドローイングマネージャー:: SetAlphaPixel](#setalphapixel)|ビットマップ内の部分的に透明なピクセルに色を色付けするヘルパーメソッド。|
|[Cドローイングマネージャー:: SetPixel](#setpixel)|ビットマップ内の1つのピクセルを指定された色に変更するヘルパーメソッド。|
|[Cドローイングマネージャー:: SmartMixColors](#smartmixcolors)|重み付け比率に基づいて2つの色を結合します。|

## <a name="remarks"></a>Remarks

クラス`CDrawingManager`には、影、色のグラデーション、および強調表示された四角形を描画するための関数が用意されています。 また、アルファブレンドも実行されます。 このクラスを使用して、アプリケーションの UI を直接変更することができます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)<br/>
`CDrawingManager`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdrawmanager

##  <a name="cdrawingmanager"></a>Cドローイングマネージャー:: Cドローイングマネージャー

[Cドローイングマネージャー](../../mfc/reference/cdrawingmanager-class.md)オブジェクトを構築します。

```
CDrawingManager(CDC& dc);
```

### <a name="parameters"></a>パラメーター

*dc*<br/>
からデバイスコンテキストへの参照。 は`CDrawingManager` 、描画にこのコンテキストを使用します。

##  <a name="createbitmap_32"></a>Cドローイングマネージャー:: CreateBitmap_32

アプリケーションが直接書き込むことができる、32ビットのデバイスに依存しないビットマップ (DIB) を作成します。

```
static HBITMAP __stdcall CreateBitmap_32(
    const CSize& size,
    void** pBits);

static HBITMAP __stdcall CreateBitmap_32(
    HBITMAP bitmap,
    COLORREF clrTransparent = -1);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*size*|からビットマップのサイズを示す[CSize](../../atl-mfc-shared/reference/csize-class.md)パラメーター。|
|*pBits*|入出力DIB のビット値の場所を受け取るデータポインターへのポインター。|
|*マップ*|元のビットマップへのハンドル|
|*clrTransparent*|元のビットマップの透明色を指定する RGB 値。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合に新しく作成された DIB ビットマップを処理するハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

DIB ビットマップを作成する方法の詳細については、「 [Createdibsection」](/windows/win32/api/wingdi/nf-wingdi-createdibitmap)を参照してください。

##  <a name="drawalpha"></a>Cドローイングマネージャー::D rawAlpha

透明または半透明のピクセルを持つビットマップを表示します。

```
void DrawAlpha(
    CDC* pDstDC,
    const CRect& rectDst,
    CDC* pSrcDC,
    const CRect& rectSrc);
```

### <a name="parameters"></a>パラメーター

*pDstDC*<br/>
から転送先のデバイスコンテキストを指すポインターです。

*rectDst*<br/>
からコピー先の四角形。

*pSrcDC*<br/>
からソースのデバイスコンテキストへのポインター。

*rectSrc*<br/>
からコピー元の四角形。

### <a name="remarks"></a>Remarks

このメソッドは、2つのビットマップのアルファブレンドを実行します。 アルファブレンドの詳細については、Windows SDK の「 [AlphaBlend](/windows/win32/api/wingdi/nf-wingdi-alphablend) 」を参照してください。

##  <a name="drawellipse"></a>Cドローイングマネージャー::D rawEllipse

指定した塗りつぶしと境界線の色を使用して、楕円を描画します。

```
void DrawEllipse(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
から楕円の外接する四角形。

*clrFill*<br/>
からこのメソッドが楕円の塗りつぶしに使用する色。

*clrLine*<br/>
からこのメソッドが楕円の境界として使用する色。

### <a name="remarks"></a>Remarks

このメソッドは、いずれかの色が-1 に設定されている場合、楕円を描画せずにを返します。 また、外接する四角形のいずれかの次元が0の場合、楕円を描画せずにを返します。

##  <a name="drawgradientring"></a>Cドローイングマネージャー::D rawGradientRing

リングを描画し、色グラデーションで塗りつぶします。

```
BOOL DrawGradientRing(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    COLORREF colorBorder,
    int nAngle,
    int nWidth,
    COLORREF clrFace = (COLORREF)-1);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
からグラデーションリングの境界を指定する[CRect](../../atl-mfc-shared/reference/crect-class.md)パラメーター。

*colorStart*<br/>
からグラデーションの最初の色。

*colorFinish*<br/>
からグラデーションの最後の色。

*colorBorder*<br/>
から境界線の色。

*nAngle*<br/>
から最初のグラデーションの描画角度を指定するパラメーター。 この値は 0 ~ 360 の範囲で指定する必要があります。

*nWidth*<br/>
からリングの境界線の幅。

*clrFace*<br/>
からリングの内部の色。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

*Rect*によって定義される四角形は、幅が5ピクセル、高さが5ピクセル以上である必要があります。

##  <a name="drawline_cdrawingmanager__drawlinea"></a>Cドローイングマネージャー::D rawLine、Cドローイングマネージャー::D rawLineA

線を描画します。

```
void DrawLine(
    int x1,
    int y1,
    int x2,
    int y2,
    COLORREF clrLine);

void DrawLineA(
    double x1,
    double y1,
    double x2,
    double y2,
    COLORREF clrLine);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*x1*|から直線の開始位置を指定する x 座標。|
|*y1*|から直線の開始位置を指定する y 座標。|
|*×*|から直線が終了する位置の x 座標。|
|*y2*|から直線が終了する位置の y 座標。|
|*clrLine*|から線の色。|

### <a name="remarks"></a>Remarks

*Clrline*が-1 の場合、このメソッドは失敗します。

##  <a name="drawrect"></a>Cドローイングマネージャー::D rawRect

塗りつぶしと境界線の色を指定して四角形を描画します。

```
void DrawRect(
    const CRect& rect,
    COLORREF clrFill,
    COLORREF clrLine);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
から四角形の境界。

*clrFill*<br/>
からこのメソッドが四角形の塗りつぶしに使用する色。

*clrLine*<br/>
からこのメソッドが四角形の境界線に使用する色。

### <a name="remarks"></a>Remarks

いずれかの色が-1 に設定されている場合、このメソッドは、四角形を描画せずにを返します。 また、四角形のいずれかの次元が0の場合にもを返します。

##  <a name="drawshadow"></a>Cドローイングマネージャー::D rawShadow

四角形の領域の影を描画します。

```
BOOL DrawShadow(
    CRect rect,
    int nDepth,
    int iMinBrightness = 100,
    int iMaxBrightness = 50,
    CBitmap* pBmpSaveBottom = NULL,
    CBitmap* pBmpSaveRight = NULL,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bRightShadow = TRUE);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
からアプリケーション内の四角形の領域。 描画マネージャーは、この領域の下に影を描画します。

*n 深さ*<br/>
から影の幅と高さ。

*iMinBrightness*<br/>
から影の最小明度。

*iMaxBrightness*<br/>
から影の最大輝度。

*pBmpSaveBottom*<br/>
から影の下部のイメージが格納されているビットマップへのポインター。

*pBmpSaveRight*<br/>
から四角形の右側に描画される影のイメージが格納されているビットマップへのポインター。

*clrBase*<br/>
から影の色。

*bRightShadow*<br/>
から影の描画方法を示すブール型パラメーター。 *BRightShadow*がの`TRUE`場合`DrawShadow`は、四角形の右側に影を描画します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

*Pbmpsavebottom*と*pBmpSaveRight*パラメーターを使用して、下と右の影に2つの有効なビットマップを提供できます。 これらの[CBitmap](../../mfc/reference/cbitmap-class.md)オブジェクトに GDI オブジェクトがアタッチさ`DrawShadow`れている場合、はそれらのビットマップをシャドウとして使用します。 パラメーターに GDI オブジェクトがアタッチされていない`DrawShadow`場合は、影を描画し、ビットマップをパラメーターにアタッチします。 `CBitmap` 今後のの呼び出し`DrawShadow`では、これらのビットマップを使用して描画プロセスを高速化できます。 クラスおよび GDI オブジェクトの`CBitmap`詳細については、「[グラフィックオブジェクト](../../mfc/graphic-objects.md)」を参照してください。

これらのパラメーターのいずれか`NULL`が`DrawShadow`の場合、は自動的に影を描画します。

*BRightShadow*を FALSE に設定すると、四角形領域の下と左側に影が描画されます。

### <a name="example"></a>例

クラスのメソッド`DrawShadow`を使用する方法を次の例に示します。 `CDrawingManager` このコードスニペットは、 [Prop シートのデモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_PropSheetDemo#1](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_1.cpp)]

##  <a name="fill4colorsgradient"></a>Cドローイングマネージャー:: Fill4ColorsGradient

四角形領域に2色のグラデーションを設定します。

```
void Fill4ColorsGradient(
    CRect rect,
    COLORREF colorStart1,
    COLORREF colorFinish1,
    COLORREF colorStart2,
    COLORREF colorFinish2,
    BOOL bHorz = TRUE,
    int nPercentage = 50);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
から塗りつぶす四角形。

*colorStart1*<br/>
から最初の色グラデーションの初期色。

*colorFinish1*<br/>
から最初の色グラデーションの最後の色。

*colorStart2*<br/>
から2番目の色グラデーションの初期色。

*colorFinish2*<br/>
から2番目の色グラデーションの最後の色。

*bHorz*<br/>
から水平方向または垂直方向`Fill4ColorsGradient`のグラデーションに色を指定するかどうかを示すブール値パラメーター。 TRUE は、水平方向のグラデーションを示します。

*nPercentage*<br/>
から0-100 からの整数。 この値は、最初の色グラデーションで塗りつぶす四角形の割合を示します。

### <a name="remarks"></a>Remarks

四角形が2つの色のグラデーションで塗りつぶされている場合、 *bHorz*の値に応じて、それぞれの上または横に位置しています。 各色のグラデーションは、 [Cドローイングマネージャー:: fillgradient](#fillgradient)メソッドとは別に計算されます。

このメソッドは、 *Npercentage*が0より小さいか、または100を超える場合にアサーションエラーを生成します。

##  <a name="fillgradient"></a>Cドローイングマネージャー:: FillGradient

指定した色のグラデーションで四角形の領域を塗りつぶします。

```
void FillGradient(
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    BOOL bHorz = TRUE,
    int nStartFlatPercentage = 0,
    int nEndFlatPercentage = 0);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
から塗りつぶす四角形の領域。

*colorStart*<br/>
からグラデーションの最初の色。

*colorFinish*<br/>
からグラデーションの最後の色。

*bHorz*<br/>
からが水平または垂直の`FillGradient`グラデーションを描画するかどうかを指定するブール型パラメーター。

*nStartFlatPercentage*<br/>
からグラデーションが開始される前`FillGradient`に*colorstart*で塗りつぶされる四角形の割合。

*nEndFlatPercentage*<br/>
からグラデーションが終了した後`FillGradient`に*colorfinish*で塗りつぶされる四角形の割合。

### <a name="example"></a>例

クラスのメソッド`FillGradient`を使用する方法を次の例に示します。 `CDrawingManager` このコードスニペットは、 [MS Office 2007 Demo サンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_MSOffice2007Demo#12](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_2.cpp)]

##  <a name="fillgradient2"></a>Cドローイングマネージャー:: FillGradient2

指定した色のグラデーションで四角形の領域を塗りつぶします。

```
void FillGradient2 (
    CRect rect,
    COLORREF colorStart,
    COLORREF colorFinish,
    int nAngle = 0);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
から塗りつぶす四角形の領域。

*colorStart*<br/>
からグラデーションの最初の色。

*colorFinish*<br/>
からグラデーションの最後の色。

*nAngle*<br/>
から0 ~ 360 の整数。 このパラメーターは、色グラデーションの方向を指定します。

### <a name="remarks"></a>Remarks

色のグラデーションの方向を指定するには、 *Nangle*を使用します。 色のグラデーションの方向を指定する場合は、色のグラデーションの開始位置も指定します。 *Nangle*に0を指定すると、四角形の上部からグラデーションが開始されます。 *Nangle*が増えると、グラデーションの開始位置は、角度に基づいて反時計回りの方向に移動します。

### <a name="example"></a>例

クラスのメソッド`FillGradient2`を使用する方法を次の例に示します。 `CDrawingManager` このコードスニペットは、[新しいコントロールのサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_NewControls#37](../../mfc/reference/codesnippet/cpp/cdrawingmanager-class_3.cpp)]

##  <a name="grayrect"></a>Cドローイングマネージャー:: グレーの四角形

指定した灰色の色で四角形を塗りつぶします。

```
BOOL GrayRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    COLORREF clrDisabled = (COLORREF)-1);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
から塗りつぶす四角形の領域。

*nPercentage*<br/>
から四角形に必要なグレーのパーセンテージ。

*clrTransparent*<br/>
から透明色。

*clrDisabled*<br/>
から*Npercentage*が-1 に設定されている場合に、このメソッドが鮮やかさの解除に使用する色。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

パラメーター *Npercentage*の場合、小さい値は濃い色を示します。

*Npercentage*の最大値は200です。 200より大きい値を指定しても、四角形の外観は変わりません。 値が-1 の場合、このメソッドは*Clrdisabled*を使用して四角形の鮮やかさを制限します。

##  <a name="highlightrect"></a>Cドローイングマネージャー:: HighlightRect

四角形の領域を強調表示します。

```
BOOL HighlightRect(
    CRect rect,
    int nPercentage = -1,
    COLORREF clrTransparent = (COLORREF)-1,
    int nTolerance = 0,
    COLORREF clrBlend = (COLORREF)-1);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
から強調表示する四角形の領域。

*nPercentage*<br/>
から強調表示の透明度を示すパーセント値。

*clrTransparent*<br/>
から透明色。

*nTolerance*<br/>
から色の許容範囲を示す 0 ~ 255 の整数。

*clrBlend*<br/>
からブレンドの基本色。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

*Npercentage*が 0 ~ 99 の場合、 `HighlightRect`ではアルファブレンドアルゴリズムが使用されます。 アルファブレンドの詳細については、「[アルファブレンドの直線と塗りつぶし](/dotnet/framework/winforms/advanced/alpha-blending-lines-and-fills)」を参照してください。 *N パーセント*が-1 の場合、このメソッドは既定の強調表示レベルを使用します。 *Npercentage*が100の場合、このメソッドは何も実行せず、TRUE を返します。

メソッドは、 *Ntolerance*パラメーターを使用して、四角形の領域を強調表示するかどうかを決定します。 四角形を強調表示するには、アプリケーションの背景色と*Clrtransparent*の差が、各色コンポーネント (赤、緑、および青) の*ntolerance*下回る必要があります。

##  <a name="hlstorgb_one"></a>Cドローイングマネージャー:: HLStoRGB_ONE

HLS 表現の色を RGB 表現に変換します。

```
static COLORREF __stdcall HLStoRGB_ONE(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>パラメーター

*H*<br/>
から色の色合いを表す 0 ~ 1 の数値。

*L*<br/>
から色の明度を示す 0 ~ 1 の範囲の数値。

*S*<br/>
から色の鮮やかさを示す 0 ~ 1 の範囲の数値。

### <a name="return-value"></a>戻り値

指定された HLS 色の RGB 表現。

### <a name="remarks"></a>Remarks

色は、HSV (色合い、鮮やかさ、および値)、HSL (色合い、鮮やかさ、および輝度)、または RGB (赤、緑、および青) として表すことができます。 色のさまざまな表現の詳細については、「 [color](/windows/win32/uxguide/vis-color)」を参照してください。

このメソッドとメソッド`CDrawingManager::HLStoRGB_TWO`は同じ操作を実行しますが、 *H*パラメーターには異なる値を指定する必要があります。 このメソッドでは、 *H*は円の割合です。 メソッドでは、H は 0 ~ 360 の間の角度の値です。どちらも赤を表します。 `CDrawingManager::HLStoRGB_TWO` たとえば`HLStoRGB_ONE`、を指定した場合、 *H*の値0.25 は、の値90と`HLStoRGB_TWO`等価です。

##  <a name="hlstorgb_two"></a>Cドローイングマネージャー:: HLStoRGB_TWO

HLS 表現の色を RGB 表現に変換します。

```
static COLORREF __stdcall HLStoRGB_TWO(
    double H,
    double L,
    double S);
```

### <a name="parameters"></a>パラメーター

*H*<br/>
から色の色合いを表す 0 ~ 360 の数値。

*L*<br/>
から色の明度を示す 0 ~ 1 の範囲の数値。

*S*<br/>
から色の鮮やかさを示す 0 ~ 1 の範囲の数値。

### <a name="return-value"></a>戻り値

指定された HLS 色の RGB 表現。

### <a name="remarks"></a>Remarks

色は、HSV (色合い、鮮やかさ、および値)、HSL (色合い、鮮やかさ、および輝度)、または RGB (赤、緑、および青) として表すことができます。 色のさまざまな表現の詳細については、「 [color](/windows/win32/uxguide/vis-color)」を参照してください。

このメソッドと[Cドローイングマネージャー:: HLStoRGB_ONE](#hlstorgb_one)メソッドは同じ操作を実行しますが、 *H*パラメーターには異なる値を指定する必要があります。 このメソッドでは、 *H*は 0 ~ 360 の角度の値であり、どちらも赤を表します。 [Cドローイングマネージャー:: HLStoRGB_ONE](#hlstorgb_one)メソッドでは、 *H*は円の割合です。 たとえば`HLStoRGB_ONE`、を指定した場合、 *H*の値0.25 は、の値90と`HLStoRGB_TWO`等価です。

##  <a name="hsvtorgb"></a>Cドローイングマネージャー:: HSVtoRGB

色を HSV 表現から RGB 表現に変換します。

```
static COLORREF __stdcall HSVtoRGB(
    double H,
    double S,
    double V);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*H*|から色の色合いを示す 0 ~ 360 の数値。|
|*S*|から色の鮮やかさを示す 0 ~ 1 の範囲の数値。|
|*V*|から色の値を示す 0 ~ 1 の範囲の数値。|

### <a name="return-value"></a>戻り値

指定された HSV 色の RGB 表現。

### <a name="remarks"></a>Remarks

色は、HSV (色合い、鮮やかさ、および値)、HSL (色合い、鮮やかさ、および輝度)、または RGB (赤、緑、および青) として表すことができます。 色のさまざまな表現の詳細については、「 [color](/windows/win32/uxguide/vis-color)」を参照してください。

##  <a name="huetorgb"></a>  CDrawingManager::HuetoRGB

色合いの値を赤、緑、または青のコンポーネントに変換します。

```
static double __stdcall HuetoRGB(
    double m1,
    double m2,
    double h);

static BYTE __stdcall HueToRGB(
    float rm1,
    float rm2,
    float rh);
```

### <a name="parameters"></a>パラメーター

*m1*<br/>
から「解説」を参照してください。

*m2*<br/>
から「解説」を参照してください。

*h*<br/>
から「解説」を参照してください。

*rm1*<br/>
から「解説」を参照してください。

*rm2*<br/>
から「解説」を参照してください。

*rh*<br/>
から「解説」を参照してください。

### <a name="return-value"></a>戻り値

指定された色合いの個々の赤、緑、または青のコンポーネント。

### <a name="remarks"></a>Remarks

このメソッドは、クラスが`CDrawingManager` HSV または HSL 表現で色の赤、緑、および青の各要素を計算するために使用するヘルパーメソッドです。 このメソッドは、プログラマが直接呼び出すようには設計されていません。 入力パラメーターは、変換アルゴリズムに依存する値です。

HSV または HSL の色を RGB 表現に変換するには、次のいずれかのメソッドを呼び出します。

- [Cドローイングマネージャー:: HSVtoRGB](#hsvtorgb)

- [Cドローイングマネージャー:: HLStoRGB_ONE](#hlstorgb_one)

- [Cドローイングマネージャー:: HLStoRGB_TWO](#hlstorgb_two)

##  <a name="mirrorrect"></a>Cドローイングマネージャー:: MirrorRect

四角形の領域を反転します。

```
void MirrorRect(
    CRect rect,
    BOOL bHorz = TRUE);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
から反転する領域の外接する四角形。

*bHorz*<br/>
から四角形を水平方向または垂直方向に反転するかどうかを示すブール型パラメーター。

### <a name="remarks"></a>Remarks

このメソッドは、 `CDrawingManager`クラスによって所有されているデバイスコンテキストのすべての領域を反転させることができます。 *BHorz*が TRUE に設定されている場合、このメソッドは領域を水平方向に反転します。 それ以外の場合は、領域を垂直方向に反転します。

##  <a name="pixelalpha"></a>Cドローイングマネージャー::P ixelAlpha

半透明ピクセルの最終的な色を計算します。

```
static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    int percent);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    double percentR,
    double percentG,
    double percentB);

static COLORREF __stdcall PixelAlpha(
    COLORREF srcPixel,
    COLORREF dstPixel,
    int percent);
```

### <a name="parameters"></a>パラメーター

*srcPixel*<br/>
からピクセルの初期色。

*~*<br/>
から透明度のパーセンテージを表す 0 ~ 100 の数値。 値100は、初期色が完全に透明であることを示します。

*percentR*<br/>
から赤のコンポーネントの透明度のパーセンテージを表す 0 ~ 100 の数値。

*percentG*<br/>
から緑のコンポーネントの透明度のパーセンテージを表す 0 ~ 100 の数値。

*percentB*<br/>
から青のコンポーネントの透明度のパーセンテージを表す 0 ~ 100 の数値。

*dstPixel*<br/>
からピクセルの基本色。

### <a name="return-value"></a>戻り値

半透明ピクセルの最終的な色。

### <a name="remarks"></a>Remarks

これは、半透明のビットマップを色分けするためのヘルパークラスであり、プログラマが直接呼び出すように設計されていません。

*Dstpixel*を含むバージョンのメソッドを使用する場合、最終的な色は、 *Dstpixel*と*srcpixel*の組み合わせになります。 *Srcpixel*の色は、 *dstpixel*の基本色に対して部分的に透明色になっています。

##  <a name="prepareshadowmask"></a>Cドローイングマネージャー::P repareShadowMask

影として使用できるビットマップを作成します。

```
static HBITMAP __stdcall PrepareShadowMask (
    int nDepth,
    COLORREF clrBase,
    int iMinBrightness = 0,
    int iMaxBrightness = 100);
```

### <a name="parameters"></a>パラメーター

*n 深さ*<br/>
から影の幅と高さ。

*clrBase*<br/>
から影の色。

*iMinBrightness*<br/>
から影の最小明度。

*iMaxBrightness*<br/>
から影の最大輝度。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合に作成されたビットマップを処理するハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

*Ndepth*が0に設定されている場合、このメソッドは終了し、NULL を返します。 *N depth*が3未満の場合、影の幅と高さは3ピクセルに設定されます。

##  <a name="rgbtohsl"></a>Cドローイングマネージャー:: RGBtoHSL

色を赤、緑、青 (RGB) に変換して、色合い、鮮やかさ、および明るさ (HSL) 表現に変換します。

```
static void __stdcall RGBtoHSL(
    COLORREF rgb,
    double* H,
    double* S,
    double* L);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*rgb*|からRGB 値の色。|
|*H*|入出力メソッドが色の色合いを格納する double へのポインター。|
|*S*|入出力色の鮮やかさをメソッドが格納する double へのポインター。|
|*L*|入出力メソッドが色の明度を格納する double へのポインター。|

### <a name="remarks"></a>Remarks

色は、HSV (色合い、鮮やかさ、および値)、HSL (色合い、鮮やかさ、および輝度)、または RGB (赤、緑、および青) として表すことができます。 色のさまざまな表現の詳細については、「 [color](/windows/win32/uxguide/vis-color)」を参照してください。

*H*に返される値は、0と1の間の分数として表されます。0と1の両方が赤を表します。 *S*と*L*の戻り値は、0から1までの数値です。

##  <a name="rgbtohsv"></a>Cドローイングマネージャー:: RGBtoHSV

色を RGB 表現から HSV 表現に変換します。

```
static void __stdcall RGBtoHSV(
    COLORREF rgb,
    double* H,
    double* S,
    double* V);
```

### <a name="parameters"></a>パラメーター

*rgb*<br/>
からRGB 表現で変換する色。

*H*<br/>
入出力このメソッドが色の結果の色合いを格納する double へのポインター。

*S*<br/>
入出力このメソッドが色の結果の鮮やかさを格納する double を指すポインター。

*V*<br/>
入出力結果として得られる色の値をこのメソッドが格納する double へのポインター。

### <a name="remarks"></a>Remarks

色は、HSV (色合い、鮮やかさ、および値)、HSL (色合い、鮮やかさ、および輝度)、または RGB (赤、緑、および青) として表すことができます。 色のさまざまな表現の詳細については、「 [color](/windows/win32/uxguide/vis-color)」を参照してください。

*H*に返される値は、0と360の間の数値で、0と360の両方が赤を示します。 *S*と*V*の戻り値は、0から1までの数値です。

##  <a name="setalphapixel"></a>Cドローイングマネージャー:: SetAlphaPixel

ビットマップ内の透明ピクセルを色をします。

```
static void __stdcall SetAlphaPixel(
    COLORREF* pBits,
    CRect rect,
    int x,
    int y,
    int percent,
    int iShadowSize,
    COLORREF clrBase = (COLORREF)-1,
    BOOL bIsRight = TRUE);
```

### <a name="parameters"></a>パラメーター

*pBits*<br/>
からビットマップのビット値へのポインター。

*rect*<br/>
からアプリケーション内の四角形の領域。 描画マネージャーは、この領域の下に影を描画します。

*x*<br/>
からピクセルの色の水平方向の座標。

*y*<br/>
からピクセルの色の垂直座標。

*~*<br/>
から透明度のパーセンテージ。

*iShadowSize*<br/>
から影の幅と高さ。

*clrBase*<br/>
から影の色。

*bIsRight*<br/>
から色のピクセルを示すブール型パラメーター。 詳細については、次の「解説」を参照してください。

### <a name="remarks"></a>Remarks

このメソッドは、 [Cドローイングマネージャー::D rawShadow](#drawshadow)メソッドによって使用されるヘルパーメソッドです。 影を描画する場合は、代わりにを呼び出す`CDrawingManager::DrawShadow`ことをお勧めします。

*BIsRight*が TRUE に設定されている場合、色のピクセルは、*四角形*の右端から*x*ピクセルを測定します。 FALSE の場合、色のピクセルは、*四角形*の左端から*x*ピクセルを測定します。

##  <a name="setpixel"></a>Cドローイングマネージャー:: SetPixel

ビットマップ内の1つのピクセルを、指定した色に変更します。

```
static void __stdcall SetPixel(
    COLORREF* pBits,
    int cx,
    int cy,
    int x,
    int y,
    COLORREF color);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pBits*|からビットマップのビット値へのポインター。|
|*cx*|からビットマップの合計幅。|
|*暦年*|からビットマップの高さの合計。|
|*x*|から変更するビットマップ内のピクセルの x 座標。|
|*y*|から変更するビットマップ内のピクセルの y 座標。|
|*色*|から指定された座標によって識別されるピクセルの新しい色。|

##  <a name="smartmixcolors"></a>Cドローイングマネージャー:: SmartMixColors

重み付け比率に基づいて2つの色を結合します。

```
static COLORREF __stdcall SmartMixColors(
    COLORREF color1,
    COLORREF color2,
    double dblLumRatio = 1.,
    int k1 = 1,
    int k2 = 1);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*color1*|から混合する最初の色。|
|*color2*|から混合する2番目の色。|
|*dblLumRatio*|から新しい色の明度の比率。 `SmartMixColors`最終的な色を決定する前に、混合色の明度をこの比率で乗算します。|
|*k1*|から最初の色の重み付け比率。|
|*k2*|から2番目の色の重み付け比率。|

### <a name="return-value"></a>戻り値

指定された色の重み付けされた色の組み合わせを表す色。

### <a name="remarks"></a>Remarks

*K1*または*k2*のいずれかが0未満の場合、このメソッドはエラーで失敗します。 これらのパラメーターの両方が0に設定されている`RGB(0, 0, 0)`場合、メソッドはを返します。

重み付け比率は、次の式を使用して計算\*されます\* : (color1 k1 + color2 k2)/(k1 + k2)。 重み付け比率が決定された後、メソッドは混合色の明度を計算します。 次に、 *dblLumRatio*によって明るさを乗算します。 値が1.0 より大きい場合、メソッドは混合色の明度を新しい値に設定します。 それ以外の場合、輝度は1.0 に設定されます。

##  <a name="drawrotated"></a>Cドローイングマネージャー::D rawRotated

指定された四角形内のソース DC コンテンツを90°回転します。

```
void DrawRotated(
    CRect rectDest,
    CDC& dcSrc,
    BOOL bClockWise);
```

### <a name="parameters"></a>パラメーター

*rectDest*<br/>
コピー先の四角形。

*dcSrc*<br/>
ソースデバイスコンテキスト。

*bClockWise*<br/>
TRUE は回転 + 90 度を示します。FALSE は回転-90 度を示します。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
