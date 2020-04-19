---
title: CRenderTarget クラス
ms.date: 03/27/2019
f1_keywords:
- CRenderTarget
- AFXRENDERTARGET/CRenderTarget
- AFXRENDERTARGET/CRenderTarget::CRenderTarget
- AFXRENDERTARGET/CRenderTarget::Attach
- AFXRENDERTARGET/CRenderTarget::BeginDraw
- AFXRENDERTARGET/CRenderTarget::Clear
- AFXRENDERTARGET/CRenderTarget::COLORREF_TO_D2DCOLOR
- AFXRENDERTARGET/CRenderTarget::CreateCompatibleRenderTarget
- AFXRENDERTARGET/CRenderTarget::Destroy
- AFXRENDERTARGET/CRenderTarget::Detach
- AFXRENDERTARGET/CRenderTarget::DrawBitmap
- AFXRENDERTARGET/CRenderTarget::DrawEllipse
- AFXRENDERTARGET/CRenderTarget::DrawGeometry
- AFXRENDERTARGET/CRenderTarget::DrawGlyphRun
- AFXRENDERTARGET/CRenderTarget::DrawLine
- AFXRENDERTARGET/CRenderTarget::DrawRectangle
- AFXRENDERTARGET/CRenderTarget::DrawRoundedRectangle
- AFXRENDERTARGET/CRenderTarget::DrawText
- AFXRENDERTARGET/CRenderTarget::DrawTextLayout
- AFXRENDERTARGET/CRenderTarget::EndDraw
- AFXRENDERTARGET/CRenderTarget::FillEllipse
- AFXRENDERTARGET/CRenderTarget::FillGeometry
- AFXRENDERTARGET/CRenderTarget::FillMesh
- AFXRENDERTARGET/CRenderTarget::FillOpacityMask
- AFXRENDERTARGET/CRenderTarget::FillRectangle
- AFXRENDERTARGET/CRenderTarget::FillRoundedRectangle
- AFXRENDERTARGET/CRenderTarget::Flush
- AFXRENDERTARGET/CRenderTarget::GetAntialiasMode
- AFXRENDERTARGET/CRenderTarget::GetDpi
- AFXRENDERTARGET/CRenderTarget::GetMaximumBitmapSize
- AFXRENDERTARGET/CRenderTarget::GetPixelFormat
- AFXRENDERTARGET/CRenderTarget::GetPixelSize
- AFXRENDERTARGET/CRenderTarget::GetRenderTarget
- AFXRENDERTARGET/CRenderTarget::GetSize
- AFXRENDERTARGET/CRenderTarget::GetTags
- AFXRENDERTARGET/CRenderTarget::GetTextAntialiasMode
- AFXRENDERTARGET/CRenderTarget::GetTextRenderingParams
- AFXRENDERTARGET/CRenderTarget::GetTransform
- AFXRENDERTARGET/CRenderTarget::IsSupported
- AFXRENDERTARGET/CRenderTarget::IsValid
- AFXRENDERTARGET/CRenderTarget::PopAxisAlignedClip
- AFXRENDERTARGET/CRenderTarget::PopLayer
- AFXRENDERTARGET/CRenderTarget::PushAxisAlignedClip
- AFXRENDERTARGET/CRenderTarget::PushLayer
- AFXRENDERTARGET/CRenderTarget::RestoreDrawingState
- AFXRENDERTARGET/CRenderTarget::SaveDrawingState
- AFXRENDERTARGET/CRenderTarget::SetAntialiasMode
- AFXRENDERTARGET/CRenderTarget::SetDpi
- AFXRENDERTARGET/CRenderTarget::SetTags
- AFXRENDERTARGET/CRenderTarget::SetTextAntialiasMode
- AFXRENDERTARGET/CRenderTarget::SetTextRenderingParams
- AFXRENDERTARGET/CRenderTarget::SetTransform
- AFXRENDERTARGET/CRenderTarget::VerifyResource
- AFXRENDERTARGET/CRenderTarget::m_lstResources
- AFXRENDERTARGET/CRenderTarget::m_pRenderTarget
- AFXRENDERTARGET/CRenderTarget::m_pTextFormatDefault
helpviewer_keywords:
- CRenderTarget [MFC], CRenderTarget
- CRenderTarget [MFC], Attach
- CRenderTarget [MFC], BeginDraw
- CRenderTarget [MFC], Clear
- CRenderTarget [MFC], COLORREF_TO_D2DCOLOR
- CRenderTarget [MFC], CreateCompatibleRenderTarget
- CRenderTarget [MFC], Destroy
- CRenderTarget [MFC], Detach
- CRenderTarget [MFC], DrawBitmap
- CRenderTarget [MFC], DrawEllipse
- CRenderTarget [MFC], DrawGeometry
- CRenderTarget [MFC], DrawGlyphRun
- CRenderTarget [MFC], DrawLine
- CRenderTarget [MFC], DrawRectangle
- CRenderTarget [MFC], DrawRoundedRectangle
- CRenderTarget [MFC], DrawText
- CRenderTarget [MFC], DrawTextLayout
- CRenderTarget [MFC], EndDraw
- CRenderTarget [MFC], FillEllipse
- CRenderTarget [MFC], FillGeometry
- CRenderTarget [MFC], FillMesh
- CRenderTarget [MFC], FillOpacityMask
- CRenderTarget [MFC], FillRectangle
- CRenderTarget [MFC], FillRoundedRectangle
- CRenderTarget [MFC], Flush
- CRenderTarget [MFC], GetAntialiasMode
- CRenderTarget [MFC], GetDpi
- CRenderTarget [MFC], GetMaximumBitmapSize
- CRenderTarget [MFC], GetPixelFormat
- CRenderTarget [MFC], GetPixelSize
- CRenderTarget [MFC], GetRenderTarget
- CRenderTarget [MFC], GetSize
- CRenderTarget [MFC], GetTags
- CRenderTarget [MFC], GetTextAntialiasMode
- CRenderTarget [MFC], GetTextRenderingParams
- CRenderTarget [MFC], GetTransform
- CRenderTarget [MFC], IsSupported
- CRenderTarget [MFC], IsValid
- CRenderTarget [MFC], PopAxisAlignedClip
- CRenderTarget [MFC], PopLayer
- CRenderTarget [MFC], PushAxisAlignedClip
- CRenderTarget [MFC], PushLayer
- CRenderTarget [MFC], RestoreDrawingState
- CRenderTarget [MFC], SaveDrawingState
- CRenderTarget [MFC], SetAntialiasMode
- CRenderTarget [MFC], SetDpi
- CRenderTarget [MFC], SetTags
- CRenderTarget [MFC], SetTextAntialiasMode
- CRenderTarget [MFC], SetTextRenderingParams
- CRenderTarget [MFC], SetTransform
- CRenderTarget [MFC], VerifyResource
- CRenderTarget [MFC], m_lstResources
- CRenderTarget [MFC], m_pRenderTarget
- CRenderTarget [MFC], m_pTextFormatDefault
ms.assetid: 30d1607d-68d3-4d14-ac36-fdbd0ef903a1
ms.openlocfilehash: 08d01132927ca0a5f452703b14d0eb5fae2f58ba
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518452"
---
# <a name="crendertarget-class"></a>CRenderTarget クラス

ID2D1RenderTarget のラッパー。

## <a name="syntax"></a>構文

```
class CRenderTarget : public CObject;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|[名前]|説明|
|----------|-----------------|
|[CRenderTarget:: CRenderTarget](#crendertarget)|CRenderTarget オブジェクトを構築します。|
|[CRenderTarget:: ~ CRenderTarget](#_dtorcrendertarget)|デストラクターです。 レンダーターゲットオブジェクトが破棄されているときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|[名前]|説明|
|----------|-----------------|
|[CRenderTarget:: Attach](#attach)|既存のレンダーターゲットインターフェイスをオブジェクトにアタッチします。|
|[CRenderTarget:: BeginDraw](#begindraw)|このレンダーターゲットで描画を開始します。|
|[CRenderTarget:: Clear](#clear)|描画領域を指定した色にクリアします。|
|[CRenderTarget:: COLORREF_TO_D2DCOLOR](#colorref_to_d2dcolor)|GDI の色とアルファの値を D2D1_COLOR_F オブジェクトに変換します。|
|[CRenderTarget:: CreateCompatibleRenderTarget](#createcompatiblerendertarget)|現在のレンダーターゲットと互換性のある中間のオフスクリーン描画中に使用する、新しいビットマップレンダーターゲットを作成します。|
|[CRenderTarget::D estroy](#destroy)|1つ以上のリソースを削除します|
|[CRenderTarget::D etach。](#detach)|オブジェクトからレンダーターゲットインターフェイスをデタッチします|
|[CRenderTarget::D rawBitmap](#drawbitmap)|指定した IDWriteTextLayout オブジェクトによって記述された書式設定されたテキストを描画します。|
|[CRenderTarget::D rawEllipse](#drawellipse)|指定したストロークスタイルを使用して、指定した楕円の輪郭を描画します。|
|[CRenderTarget::D rawGeometry](#drawgeometry)|指定したストロークスタイルを使用して、指定したジオメトリの輪郭を描画します。|
|[CRenderTarget::D rawGlyphRun](#drawglyphrun)|指定したグリフを描画します。|
|[CRenderTarget::D rawLine](#drawline)|指定したストロークスタイルを使用して、指定した点の間に線を描画します。|
|[CRenderTarget::D rawRectangle](#drawrectangle)|指定した寸法とストロークスタイルを持つ四角形の輪郭を描画します。|
|[CRenderTarget::D rawRoundedRectangle](#drawroundedrectangle)|指定したストロークスタイルを使用して、指定した丸みのある四角形の輪郭を描画します。|
|[CRenderTarget::D rawText](#drawtext)|IDWriteTextFormat オブジェクトによって提供される書式情報を使用して、指定されたテキストを描画します。|
|[CRenderTarget::D rawTextLayout](#drawtextlayout)|指定した IDWriteTextLayout オブジェクトによって記述された書式設定されたテキストを描画します。|
|[CRenderTarget:: EndDraw](#enddraw)|レンダーターゲットで描画操作を終了し、現在のエラー状態と関連付けられているタグを示します。|
|[CRenderTarget:: FillEllipse](#fillellipse)|指定した楕円の内部を描画します。|
|[CRenderTarget:: FillGeometry](#fillgeometry)|指定したジオメトリの内部を描画します。|
|[CRenderTarget:: FillMesh](#fillmesh)|指定したメッシュの内部を描画します。|
|[CRenderTarget:: FillOpacityMask](#fillopacitymask)|指定したビットマップによって表される不透明度マスクをブラシに適用し、そのブラシを使用してレンダーターゲットの領域を描画します。|
|[CRenderTarget:: FillRectangle](#fillrectangle)|指定した四角形の内部を描画します。|
|[CRenderTarget:: Fill丸め Dedrectangle](#fillroundedrectangle)|指定した角丸四角形の内部を描画します。|
|[CRenderTarget:: Flush](#flush)|すべての保留中の描画コマンドを実行します。|
|[CRenderTarget:: Getアンチエイリアスモード](#getantialiasmode)|以外の描画操作の現在のアンチエイリアシングモードを取得します。|
|[CRenderTarget:: GetDpi](#getdpi)|レンダーターゲットのドット/インチ (DPI) を返します。|
|[CRenderTarget:: GetMaximumBitmapSize](#getmaximumbitmapsize)|レンダーターゲットでサポートされている1つのビットマップディメンションの最大サイズ (デバイスに依存する単位 (ピクセル単位)) を取得します。|
|[CRenderTarget:: Getピクセル形式](#getpixelformat)|レンダーターゲットのピクセル形式とアルファモードを取得します。|
|[CRenderTarget:: Getピクセルサイズ](#getpixelsize)|レンダーターゲットのサイズをデバイスピクセルで返します|
|[CRenderTarget::GetRenderTarget](#getrendertarget)|ID2D1RenderTarget インターフェイスを返します。|
|[CRenderTarget:: GetSize](#getsize)|レンダリングターゲットのサイズをデバイスに依存しないピクセル単位で返します|
|[CRenderTarget:: GetTags](#gettags)|後続の描画操作のラベルを取得します。|
|[CRenderTarget:: GetTextAntialiasMode](#gettextantialiasmode)|テキストおよびグリフ描画操作の現在のアンチエイリアシングモードを取得します。|
|[CRenderTarget:: GetTextRenderingParams](#gettextrenderingparams)|レンダーターゲットの現在のテキスト表示オプションを取得します。|
|[CRenderTarget:: GetTransform](#gettransform)|指定された変換をレンダーターゲットに適用し、既存の変換を置き換えます。 それ以降のすべての描画操作は、変換された領域で発生します。|
|[CRenderTarget:: IsSupported](#issupported)|レンダーターゲットが指定されたプロパティをサポートするかどうかを示します。|
|[CRenderTarget:: IsValid](#isvalid)|リソースの有効性を確認します|
|[CRenderTarget::P opAxisAlignedClip](#popaxisalignedclip)|レンダーターゲットから、軸に平行移動された最後のクリップを削除します。 このメソッドを呼び出すと、その後の描画操作にクリップが適用されなくなります。|
|[CRenderTarget::PopLayer](#poplayer)|最後の PushLayer 呼び出しで指定されたレイヤーへの描画操作のリダイレクトを停止します。|
|[CRenderTarget::P ushAxisAlignedClip](#pushaxisalignedclip)|レンダーターゲットから、軸に平行移動された最後のクリップを削除します。 このメソッドを呼び出すと、その後の描画操作にクリップが適用されなくなります。|
|[CRenderTarget::PushLayer](#pushlayer)|指定されたレイヤーをレンダーターゲットに追加します。これにより、PopLayer が呼び出されるまで、後続のすべての描画操作を受信できるようになります。|
|[CRenderTarget:: Restoreドローイング状態](#restoredrawingstate)|レンダーターゲットの描画状態を、指定した ID2D1DrawingStateBlock の描画状態に設定します。|
|[CRenderTarget:: Saveドローイング状態](#savedrawingstate)|現在の描画状態を、指定した ID2D1DrawingStateBlock に保存します。|
|[CRenderTarget:: Setアンチエイリアスモード](#setantialiasmode)|レンダーターゲットのアンチエイリアシングモードを設定します。 アンチエイリアシングモードは、テキスト描画操作とグリフ描画操作を除く、後続のすべての描画操作に適用されます。|
|[CRenderTarget:: SetDpi](#setdpi)|レンダーターゲットのドット/インチ (DPI) を設定します。|
|[CRenderTarget:: SetTags](#settags)|後続の描画操作のラベルを指定します。|
|[CRenderTarget:: Settextアンチエイリアスモード](#settextantialiasmode)|後続のテキストおよびグリフ描画操作に使用するアンチエイリアシングモードを指定します。|
|[CRenderTarget:: SetTextRenderingParams](#settextrenderingparams)|後続のすべてのテキストおよびグリフ描画操作に適用されるテキスト表示オプションを指定します。|
|[CRenderTarget:: SetTransform](#settransform)|オーバーロードされます。 指定された変換をレンダーターゲットに適用し、既存の変換を置き換えます。 それ以降のすべての描画操作は、変換された領域で発生します。|

### <a name="protected-methods"></a>プロテクト メソッド

|[名前]|説明|
|----------|-----------------|
|[CRenderTarget:: VerifyResource](#verifyresource)|CD2DResource オブジェクトの有効性を検証します。オブジェクトがまだ存在しない場合は、作成します。|

### <a name="public-operators"></a>パブリック演算子

|[名前]|説明|
|----------|-----------------|
|[CRenderTarget:: operator ID2D1RenderTarget *](#operator_id2d1rendertarget_star)|ID2D1RenderTarget インターフェイスを返します。|

### <a name="protected-data-members"></a>保護されるデータ メンバー

|[名前]|説明|
|----------|-----------------|
|[CRenderTarget:: m_lstResources](#m_lstresources)|CD2DResource オブジェクトへのポインターのリスト。|
|[CRenderTarget:: m_pRenderTarget](#m_prendertarget)|ID2D1RenderTarget オブジェクトへのポインター。|
|[CRenderTarget:: m_pTextFormatDefault](#m_ptextformatdefault)|既定のテキスト形式を格納している CD2DTextFormat オブジェクトへのポインター。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

## <a name="requirements"></a>要件

**ヘッダー:** afxrendertarget

##  <a name="_dtorcrendertarget"></a>CRenderTarget:: ~ CRenderTarget

デストラクターです。 レンダーターゲットオブジェクトが破棄されているときに呼び出されます。

```
virtual ~CRenderTarget();
```

##  <a name="attach"></a>CRenderTarget:: Attach

既存のレンダーターゲットインターフェイスをオブジェクトにアタッチします。

```
void Attach(ID2D1RenderTarget* pRenderTarget);
```

### <a name="parameters"></a>パラメーター

*pRenderTarget*<br/>
既存のレンダーターゲットインターフェイス。 NULL にすることはできません

##  <a name="begindraw"></a>CRenderTarget:: BeginDraw

このレンダーターゲットで描画を開始します。

```
void BeginDraw();
```

##  <a name="clear"></a>CRenderTarget:: Clear

描画領域を指定した色にクリアします。

```
void Clear(D2D1_COLOR_F color);
```

### <a name="parameters"></a>パラメーター

*color*<br/>
描画領域をクリアする色。

##  <a name="colorref_to_d2dcolor"></a>CRenderTarget:: COLORREF_TO_D2DCOLOR

GDI の色とアルファの値を D2D1_COLOR_F オブジェクトに変換します。

```
static D2D1_COLOR_F COLORREF_TO_D2DCOLOR(
    COLORREF color,
    int nAlpha = 255);
```

### <a name="parameters"></a>パラメーター

*color*<br/>
RGB 値。

*nAlpha*

### <a name="return-value"></a>戻り値

D2D1_COLOR_F 値。

##  <a name="createcompatiblerendertarget"></a>CRenderTarget:: CreateCompatibleRenderTarget

現在のレンダーターゲットと互換性のある中間のオフスクリーン描画中に使用する、新しいビットマップレンダーターゲットを作成します。

```
BOOL CreateCompatibleRenderTarget(
    CBitmapRenderTarget& bitmapTarget,
    CD2DSizeF sizeDesired = CD2DSizeF(0., 0.),
    CD2DSizeU sizePixelDesired = CD2DSizeU(0, 0),
    D2D1_PIXEL_FORMAT* desiredFormat = NULL,
    D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS options = D2D1_COMPATIBLE_RENDER_TARGET_OPTIONS_NONE);
```

### <a name="parameters"></a>パラメーター

*bitmapTarget*<br/>
このメソッドから制御が戻るときに、新しいビットマップレンダーターゲットへのポインターのアドレスを格納します。 このパラメーターは初期化せずに渡されます。

*sizeDesired*<br/>
新しいレンダーターゲットのサイズ (元のレンダーターゲットと異なる場合はデバイスに依存しないピクセル)、または NULL。 詳細については、「解説」を参照してください。

*Sizeピクセルが必要です*<br/>
元のレンダーターゲットと異なる必要がある場合は新しいレンダーターゲットのサイズ (ピクセル単位)。 NULL の場合は。 詳細については、「解説」を参照してください。

*desiredFormat*<br/>
新しいレンダーターゲットの必要なピクセル形式とアルファモード、または NULL。 ピクセル形式が DXGI_FORMAT_UNKNOWN に設定されている場合、またはこのパラメーターが null の場合、新しいレンダーターゲットは元のレンダーターゲットと同じピクセル形式を使用します。 アルファモードが D2D1_ALPHA_MODE_UNKNOWN か、またはこのパラメーターが NULL の場合、新しいレンダーターゲットのアルファモードは既定で D2D1_ALPHA_MODE_PREMULTIPLIED になります。 サポートされているピクセル形式の詳細については、「サポートされているピクセル形式とアルファモード」を参照してください。

*options*<br/>
新しいレンダーターゲットが GDI と互換性がある必要があるかどうかを指定する値。

### <a name="return-value"></a>戻り値

メソッドが成功した場合、TRUE を返します。 それ以外の場合は FALSE を返します。

##  <a name="crendertarget"></a>CRenderTarget:: CRenderTarget

CRenderTarget オブジェクトを構築します。

```
CRenderTarget();
```

##  <a name="destroy"></a>CRenderTarget::D estroy

1つ以上のリソースを削除します

```
BOOL Destroy(BOOL bDeleteResources = TRUE);
```

### <a name="parameters"></a>パラメーター

*bDeleteResources*<br/>
BDeleteResources が TRUE の場合、m_lstResources にあるすべてのリソースが自動的に破棄されます。

### <a name="return-value"></a>戻り値

メソッドが成功した場合、TRUE を返します。 それ以外の場合は FALSE を返します。

##  <a name="detach"></a>CRenderTarget::D etach。

オブジェクトからレンダーターゲットインターフェイスをデタッチします

```
ID2D1RenderTarget* Detach ();
```

### <a name="return-value"></a>戻り値

デタッチされたレンダーターゲットインターフェイスへのポインター。

##  <a name="drawbitmap"></a>CRenderTarget::D rawBitmap

指定した IDWriteTextLayout オブジェクトによって記述された書式設定されたテキストを描画します。

```
void DrawBitmap(
    CD2DBitmap* pBitmap,
    const CD2DRectF& rectDest,
    float fOpacity = 1.0,
    D2D1_BITMAP_INTERPOLATION_MODE interpolationMode = D2D1_BITMAP_INTERPOLATION_MODE_LINEAR,
    const CD2DRectF* pRectSrc = NULL);
```

### <a name="parameters"></a>パラメーター

*pBitmap*<br/>
レンダリングするビットマップ。

*rectDest*<br/>
ビットマップが描画される領域のサイズと位置 (レンダリングターゲットの座標空間内のデバイスに依存しないピクセル単位)。 四角形が適切に並べられていない場合は、何も描画されませんが、レンダーターゲットはエラー状態になりません。

*fOpacity*<br/>
ビットマップに適用する不透明度の値を指定する 0.0 f ~ 1.0 f の範囲の値。この値は、ビットマップのコンテンツのアルファ値に対して乗算されます。

*interpolationMode*<br/>
描画操作によってビットマップを拡大縮小または回転する場合に使用する補間モード。

*pRectSrc*<br/>
描画するビットマップ内の領域のサイズと位置 (ビットマップの座標空間内のデバイスに依存しないピクセル単位)。

##  <a name="drawellipse"></a>CRenderTarget::D rawEllipse

指定したストロークスタイルを使用して、指定した楕円の輪郭を描画します。

```
void DrawEllipse(
    const CD2DEllipse& ellipse,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>パラメーター

*楕円*<br/>
描画する楕円の位置と半径 (デバイスに依存しないピクセル単位)。

*pBrush*<br/>
楕円の輪郭の描画に使用するブラシ。

*fStrokeWidth*<br/>
楕円のストロークの太さ。 ストロークは、楕円の輪郭の中央に配置されます。

*strokeStyle*<br/>
楕円の輪郭に適用するストロークのスタイル。または、実線のストロークを描画する場合は NULL。

##  <a name="drawgeometry"></a>CRenderTarget::D rawGeometry

指定したストロークスタイルを使用して、指定したジオメトリの輪郭を描画します。

```
void DrawGeometry(
    CD2DGeometry* pGeometry,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>パラメーター

*pGeometry*<br/>
描画するジオメトリ。

*pBrush*<br/>
ジオメトリのストロークの描画に使用するブラシ。

*fStrokeWidth*<br/>
ジオメトリのストロークの太さ。 ストロークは、ジオメトリのアウトラインの中央に配置されます。

*strokeStyle*<br/>
ジオメトリの輪郭に適用するストロークのスタイル。または、実線のストロークを描画する場合は NULL。

##  <a name="drawglyphrun"></a>CRenderTarget::D rawGlyphRun

指定したグリフを描画します。

```
void DrawGlyphRun(
    const CD2DPointF& ptBaseLineOrigin,
    const DWRITE_GLYPH_RUN& glyphRun,
    CD2DBrush* pForegroundBrush,
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```

### <a name="parameters"></a>パラメーター

*ptBaseLineOrigin*<br/>
グリフのベースラインの原点 (デバイスに依存しないピクセル単位)。

*glyphRun*<br/>
描画するグリフ。

*pForegroundBrush*<br/>
指定したグリフの描画に使用するブラシ。

*measuringMode*<br/>
グリフのメトリックを使用してテキストの書式設定時にテキストを測定する方法を示す値。 既定値は DWRITE_MEASURING_MODE_NATURAL です。

##  <a name="drawline"></a>CRenderTarget::D rawLine

指定したストロークスタイルを使用して、指定した点の間に線を描画します。

```
void DrawLine(
    const CD2DPointF& ptFrom,
    const CD2DPointF& ptTo,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>パラメーター

*ptFrom*<br/>
線の始点 (デバイスに依存しないピクセル単位)。

*ptTo*<br/>
線の終点 (デバイスに依存しないピクセル単位)。

*pBrush*<br/>
線のストロークを描画するために使用するブラシ。

*fStrokeWidth*<br/>
ストロークの幅を指定する 0.0 f 以上の値。 このパラメーターが指定されていない場合、既定値は 1.0 f です。 ストロークは、線の中央に配置されます。

*strokeStyle*<br/>
描画するストロークのスタイル。純線を描画する場合は NULL。

##  <a name="drawrectangle"></a>CRenderTarget::D rawRectangle

指定した寸法とストロークスタイルを持つ四角形の輪郭を描画します。

```
void DrawRectangle(
    const CD2DRectF& rectangle,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>パラメーター

*四角形*<br/>
描画する四角形の大きさ (デバイスに依存しないピクセル単位)

*pBrush*<br/>
四角形のストロークを描画するために使用するブラシ。

*fStrokeWidth*<br/>
四角形のストロークの幅を指定する 0.0 f 以上の値。 ストロークは、四角形のアウトラインの中央に配置されます。

*strokeStyle*<br/>
描画するストロークのスタイル。または、純色のストロークを描画する場合は NULL。

##  <a name="drawroundedrectangle"></a>CRenderTarget::D rawRoundedRectangle

指定したストロークスタイルを使用して、指定した丸みのある四角形の輪郭を描画します。

```
void DrawRoundedRectangle(
    const CD2DRoundedRect& rectRounded,
    CD2DBrush* pBrush,
    FLOAT fStrokeWidth = 1.0,
    ID2D1StrokeStyle* strokeStyle = NULL);
```

### <a name="parameters"></a>パラメーター

*rectRounded*<br/>
描画する角丸四角形の大きさ (デバイスに依存しないピクセル単位)。

*pBrush*<br/>
角丸四角形の輪郭の描画に使用するブラシ。

*fStrokeWidth*<br/>
角丸四角形のストロークの幅。 ストロークは、角丸四角形のアウトラインの中央に配置されます。 既定値は 1.0 f です。

*strokeStyle*<br/>
角丸四角形のストロークのスタイル。または、実線を描画する場合は NULL。 既定値は NULL です。

##  <a name="drawtext"></a>CRenderTarget::D rawText

IDWriteTextFormat オブジェクトによって提供される書式情報を使用して、指定されたテキストを描画します。

```
void DrawText(
    const CString& strText,
    const CD2DRectF& rectangle,
    CD2DBrush* pForegroundBrush,
    CD2DTextFormat* textFormat = NULL,
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE,
    DWRITE_MEASURING_MODE measuringMode = DWRITE_MEASURING_MODE_NATURAL);
```

### <a name="parameters"></a>パラメーター

*strText*<br/>
描画する Unicode 文字の配列へのポインター。

*四角形*<br/>
テキストが描画される領域のサイズと位置。

*pForegroundBrush*<br/>
テキストの塗りつぶしに使用するブラシ。

*textFormat*<br/>
描画するテキストの書式設定の詳細 (フォント、フォントサイズ、フロー方向など) を記述するオブジェクト。

*options*<br/>
テキストをピクセル境界にスナップする必要があるかどうか、およびテキストをレイアウト四角形にクリップする必要があるかどうかを示す値。 既定値は D2D1_DRAW_TEXT_OPTIONS_NONE です。これは、テキストがピクセル境界にスナップされる必要があり、レイアウトの四角形にはクリップされないことを示します。

*measuringMode*<br/>
グリフのメトリックを使用してテキストの書式設定時にテキストを測定する方法を示す値。 既定値は DWRITE_MEASURING_MODE_NATURAL です。

##  <a name="drawtextlayout"></a>CRenderTarget::D rawTextLayout

指定した IDWriteTextLayout オブジェクトによって記述された書式設定されたテキストを描画します。

```
void DrawTextLayout(
    const CD2DPointF& ptOrigin,
    CD2DTextLayout* textLayout,
    CD2DBrush* pBrushForeground,
    D2D1_DRAW_TEXT_OPTIONS options = D2D1_DRAW_TEXT_OPTIONS_NONE);
```

### <a name="parameters"></a>パラメーター

*ptOrigin*<br/>
TextLayout によって記述されるテキストの左上隅が描画される、デバイスに依存しないピクセルで記述されたポイント。

*textLayout*<br/>
描画する書式設定されたテキスト。 ID2D1Resource から継承しない描画効果は無視されます。 ブラシではない ID2D1Resource から継承する描画効果がある場合、このメソッドは失敗し、レンダーターゲットはエラー状態になります。

*pBrushForeground*<br/>
描画効果 (IDWriteTextLayout:: SetDrawingEffect メソッドによって指定されます) として関連付けられたブラシがまだない textLayout のテキストを描画するために使用されるブラシ。

*options*<br/>
テキストをピクセル境界にスナップする必要があるかどうか、およびテキストをレイアウト四角形にクリップする必要があるかどうかを示す値。 既定値は D2D1_DRAW_TEXT_OPTIONS_NONE です。これは、テキストがピクセル境界にスナップされる必要があり、レイアウトの四角形にはクリップされないことを示します。

##  <a name="enddraw"></a>CRenderTarget:: EndDraw

レンダーターゲットで描画操作を終了し、現在のエラー状態と関連付けられているタグを示します。

```
HRESULT EndDraw();
```

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、S_OK を返します。 それ以外の場合は、HRESULT エラーコードを返します。

##  <a name="fillellipse"></a>  CRenderTarget::FillEllipse

指定した楕円の内部を描画します。

```
void FillEllipse(
    const CD2DEllipse& ellipse,
    CD2DBrush* pBrush);
```

### <a name="parameters"></a>パラメーター

*楕円*<br/>
描画する楕円の位置と半径 (デバイスに依存しないピクセル単位)。

*pBrush*<br/>
楕円の内部を描画するために使用するブラシ。

##  <a name="fillgeometry"></a>CRenderTarget:: FillGeometry

指定したジオメトリの内部を描画します。

```
void FillGeometry(
    CD2DGeometry* pGeometry,
    CD2DBrush* pBrush,
    CD2DBrush* pOpacityBrush = NULL);
```

### <a name="parameters"></a>パラメーター

*pGeometry*<br/>
描画するジオメトリ。

*pBrush*<br/>
ジオメトリの内部を描画するために使用するブラシ。

*pOpacityBrush*<br/>
ジオメトリに適用する不透明度マスク。不透明度マスクの場合は NULL です。 不透明度マスク (opacityBrush パラメーター) が指定されている場合、ブラシは、ID2D1BitmapBrush モードが D2D1_EXTEND_MODE_CLAMP に設定されたである必要があります。 詳細については、「解説」を参照してください。

##  <a name="fillmesh"></a>CRenderTarget:: FillMesh

指定したメッシュの内部を描画します。

```
void FillMesh(
    CD2DMesh* pMesh,
    CD2DBrush* pBrush);
```

### <a name="parameters"></a>パラメーター

*pMesh*<br/>
描画するメッシュ。

*pBrush*<br/>
メッシュの描画に使用するブラシ。

##  <a name="fillopacitymask"></a>CRenderTarget:: FillOpacityMask

指定したビットマップによって表される不透明度マスクをブラシに適用し、そのブラシを使用してレンダーターゲットの領域を描画します。

```
void FillOpacityMask(
    CD2DBitmap* pOpacityMask,
    CD2DBrush* pBrush,
    D2D1_OPACITY_MASK_CONTENT content,
    const CD2DRectF& rectDest,
    const CD2DRectF& rectSrc);
```

### <a name="parameters"></a>パラメーター

*pOpacityMask*<br/>
描画する楕円の位置と半径 (デバイスに依存しないピクセル単位)。

*pBrush*<br/>
DestinationRectangle によって指定されたレンダーターゲットの領域を描画するために使用されるブラシ。

*content*<br/>
不透明度マスクに含まれるコンテンツの種類。 値は、不透明度マスクがブレンドされる色空間を決定するために使用されます。

*rectDest*<br/>
描画するレンダーターゲットの領域 (デバイスに依存しないピクセル単位)。

*rectSrc*<br/>
不透明度マスクとして使用するビットマップの領域 (デバイスに依存しないピクセル単位)。

##  <a name="fillrectangle"></a>CRenderTarget:: FillRectangle

指定した四角形の内部を描画します。

```
void FillRectangle(
    const CD2DRectF& rectangle,
    CD2DBrush* pBrush);
```

### <a name="parameters"></a>パラメーター

*四角形*<br/>
描画する四角形の次元 (デバイスに依存しないピクセル単位)。

*pBrush*<br/>
四角形の内部を描画するために使用するブラシ。

##  <a name="fillroundedrectangle"></a>CRenderTarget:: Fill丸め Dedrectangle

指定した角丸四角形の内部を描画します。

```
void FillRoundedRectangle(
    const CD2DRoundedRect& rectRounded,
    CD2DBrush* pBrush);
```

### <a name="parameters"></a>パラメーター

*rectRounded*<br/>
描画する角丸四角形の大きさ (デバイス非依存のピクセル単位)。

*pBrush*<br/>
角丸四角形の内部を描画するために使用するブラシ。

##  <a name="flush"></a>CRenderTarget:: Flush

すべての保留中の描画コマンドを実行します。

```
void Flush(
    D2D1_TAG* tag1 = NULL,
    D2D1_TAG* tag2 = NULL);
```

### <a name="parameters"></a>パラメーター

*tag1*<br/>
エラーが発生した描画操作のタグを格納します。エラーがない場合は0を格納します。 このパラメーターは初期化せずに渡されます。

*tag2*<br/>
エラーが発生した描画操作のタグを格納します。エラーがない場合は0を格納します。 このパラメーターは初期化せずに渡されます。

##  <a name="getantialiasmode"></a>CRenderTarget:: Getアンチエイリアスモード

以外の描画操作の現在のアンチエイリアシングモードを取得します。

```
D2D1_ANTIALIAS_MODE GetAntialiasMode() const;
```

### <a name="return-value"></a>戻り値

以外の描画操作の現在のアンチエイリアシングモード。

##  <a name="getdpi"></a>CRenderTarget:: GetDpi

レンダーターゲットのドット/インチ (DPI) を返します。

```
CD2DSizeF GetDpi() const;
```

### <a name="return-value"></a>戻り値

レンダーターゲットのドット/インチ (DPI)。

##  <a name="getmaximumbitmapsize"></a>CRenderTarget:: GetMaximumBitmapSize

レンダーターゲットでサポートされている1つのビットマップディメンションの最大サイズ (デバイスに依存する単位 (ピクセル単位)) を取得します。

```
UINT32 GetMaximumBitmapSize() const;
```

### <a name="return-value"></a>戻り値

レンダーターゲットでサポートされている1つのビットマップディメンションの最大サイズ (ピクセル単位)

##  <a name="getpixelformat"></a>CRenderTarget:: Getピクセル形式

レンダーターゲットのピクセル形式とアルファモードを取得します。

```
D2D1_PIXEL_FORMAT GetPixelFormat() const;
```

### <a name="return-value"></a>戻り値

レンダーターゲットのピクセル形式とアルファモード

##  <a name="getpixelsize"></a>CRenderTarget:: Getピクセルサイズ

レンダーターゲットのサイズをデバイスピクセルで返します

```
CD2DSizeU GetPixelSize() const;
```

### <a name="return-value"></a>戻り値

レンダーターゲットのサイズ (デバイスピクセル単位)

##  <a name="getrendertarget"></a>  CRenderTarget::GetRenderTarget

ID2D1RenderTarget インターフェイスを返します。

```
ID2D1RenderTarget* GetRenderTarget();
```

### <a name="return-value"></a>戻り値

ID2D1RenderTarget インターフェイスへのポインター。オブジェクトがまだ初期化されていない場合は NULL。

##  <a name="getsize"></a>CRenderTarget:: GetSize

レンダリングターゲットのサイズをデバイスに依存しないピクセル単位で返します

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>戻り値

レンダリングターゲットの現在のサイズ (デバイスに依存しないピクセル単位)

##  <a name="gettags"></a>CRenderTarget:: GetTags

後続の描画操作のラベルを取得します。

```
void GetTags(
    D2D1_TAG* tag1 = NULL,
    D2D1_TAG* tag2 = NULL) const;
```

### <a name="parameters"></a>パラメーター

*tag1*<br/>
後続の描画操作の最初のラベルが含まれています。 このパラメーターは初期化せずに渡されます。 NULL が指定されている場合、このパラメーターの値は取得されません。

*tag2*<br/>
後続の描画操作の2番目のラベルを格納します。 このパラメーターは初期化せずに渡されます。 NULL が指定されている場合、このパラメーターの値は取得されません。

##  <a name="gettextantialiasmode"></a>  CRenderTarget::GetTextAntialiasMode

テキストおよびグリフ描画操作の現在のアンチエイリアシングモードを取得します。

```
D2D1_TEXT_ANTIALIAS_MODE GetTextAntialiasMode() const;
```

### <a name="return-value"></a>戻り値

テキスト描画操作とグリフ描画操作の現在のアンチエイリアシングモード。

##  <a name="gettextrenderingparams"></a>  CRenderTarget::GetTextRenderingParams

レンダーターゲットの現在のテキスト表示オプションを取得します。

```
void GetTextRenderingParams(IDWriteRenderingParams** textRenderingParams);
```

### <a name="parameters"></a>パラメーター

*textRenderingParams*<br/>
このメソッドから制御が戻るときに、レンダーターゲットの現在のテキスト表示オプションへのポインターのアドレスを textRenderingParamscontains します。

##  <a name="gettransform"></a>CRenderTarget:: GetTransform

レンダーターゲットの現在の変換を取得します。

```
void GetTransform(D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>パラメーター

*transform*<br/>
このが返されるときに、レンダーターゲットの現在の変換を格納します。 このパラメーターは初期化せずに渡されます。

##  <a name="issupported"></a>  CRenderTarget::IsSupported

レンダーターゲットが指定されたプロパティをサポートするかどうかを示します。

```
BOOL IsSupported(const D2D1_RENDER_TARGET_PROPERTIES& renderTargetProperties) const;
```

### <a name="parameters"></a>パラメーター

*renderTargetProperties*<br/>
テストするレンダーターゲットプロパティ

### <a name="return-value"></a>戻り値

指定したレンダーターゲットプロパティがこのレンダーターゲットでサポートされている場合は TRUE。それ以外の場合は FALSE

##  <a name="isvalid"></a>  CRenderTarget::IsValid

リソースの有効性を確認します

```
BOOL IsValid() const;
```

### <a name="return-value"></a>戻り値

リソースが有効な場合は TRUE。それ以外の場合は FALSE。

##  <a name="m_lstresources"></a>CRenderTarget:: m_lstResources

CD2DResource オブジェクトへのポインターのリスト。

```
CObList m_lstResources;
```

##  <a name="m_prendertarget"></a>  CRenderTarget::m_pRenderTarget

ID2D1RenderTarget オブジェクトへのポインター。

```
ID2D1RenderTarget* m_pRenderTarget;
```

##  <a name="m_ptextformatdefault"></a>  CRenderTarget::m_pTextFormatDefault

既定のテキスト形式を格納している CD2DTextFormat オブジェクトへのポインター。

```
CD2DTextFormat* m_pTextFormatDefault;
```

##  <a name="operator_id2d1rendertarget_star"></a>CRenderTarget:: operator ID2D1RenderTarget *

ID2D1RenderTarget インターフェイスを返します。

```
operator ID2D1RenderTarget*();
```

### <a name="return-value"></a>戻り値

ID2D1RenderTarget インターフェイスへのポインター。オブジェクトがまだ初期化されていない場合は NULL。

##  <a name="popaxisalignedclip"></a>  CRenderTarget::PopAxisAlignedClip

レンダーターゲットから、軸に平行移動された最後のクリップを削除します。 このメソッドを呼び出すと、その後の描画操作にクリップが適用されなくなります。

```
void PopAxisAlignedClip();
```

##  <a name="poplayer"></a>  CRenderTarget::PopLayer

最後の PushLayer 呼び出しで指定されたレイヤーへの描画操作のリダイレクトを停止します。

```
void PopLayer();
```

##  <a name="pushaxisalignedclip"></a>  CRenderTarget::PushAxisAlignedClip

レンダーターゲットから、軸に平行移動された最後のクリップを削除します。 このメソッドを呼び出すと、その後の描画操作にクリップが適用されなくなります。

```
void PushAxisAlignedClip(
    const CD2DRectF& rectClip,
    D2D1_ANTIALIAS_MODE mode = D2D1_ANTIALIAS_MODE_PER_PRIMITIVE);
```

### <a name="parameters"></a>パラメーター

*rectClip*<br/>
クリッピング領域のサイズと位置 (デバイスに依存しないピクセル単位)。

*モード*<br/>
サブピクセル境界を持つクリップ四角形の端を描画するために使用されるアンチエイリアシングモード。また、クリップをシーンコンテンツとブレンドするために使用されます。 ブレンドは、PopAxisAlignedClip メソッドが呼び出されたときに1回実行され、レイヤー内の各プリミティブには適用されません。

##  <a name="pushlayer"></a>  CRenderTarget::PushLayer

指定されたレイヤーをレンダーターゲットに追加します。これにより、PopLayer が呼び出されるまで、後続のすべての描画操作を受信できるようになります。

```
void PushLayer(
    const D2D1_LAYER_PARAMETERS& layerParameters,
    CD2DLayer& layer);
```

### <a name="parameters"></a>パラメーター

*レイヤーパラメーター*<br/>
レイヤーのコンテンツの境界、幾何マスク、不透明度、不透明度マスク、およびアンチエイリアシングオプション。

*レイヤー*<br/>
後続の描画操作を受け取るレイヤー。

##  <a name="restoredrawingstate"></a>CRenderTarget:: Restoreドローイング状態

レンダーターゲットの描画状態を、指定した ID2D1DrawingStateBlock の描画状態に設定します。

```
void RestoreDrawingState(ID2D1DrawingStateBlock& drawingStateBlock);
```

### <a name="parameters"></a>パラメーター

*drawingStateBlock*<br/>
レンダーターゲットの新しい描画状態。

##  <a name="savedrawingstate"></a>CRenderTarget:: Saveドローイング状態

現在の描画状態を、指定した ID2D1DrawingStateBlock に保存します。

```
void SaveDrawingState(ID2D1DrawingStateBlock& drawingStateBlock) const;
```

### <a name="parameters"></a>パラメーター

*drawingStateBlock*<br/>
このメソッドから制御が戻るときに、レンダーターゲットの現在の描画状態を格納します。 このパラメーターは、メソッドに渡す前に初期化する必要があります。

##  <a name="setantialiasmode"></a>CRenderTarget:: Setアンチエイリアスモード

レンダーターゲットのアンチエイリアシングモードを設定します。 アンチエイリアシングモードは、テキスト描画操作とグリフ描画操作を除く、後続のすべての描画操作に適用されます。

```
void SetAntialiasMode(D2D1_ANTIALIAS_MODE antialiasMode);
```

### <a name="parameters"></a>パラメーター

*アンチエイリアスモード*<br/>
将来の描画操作のためのアンチエイリアシングモード。

##  <a name="setdpi"></a>CRenderTarget:: SetDpi

レンダーターゲットのドット/インチ (DPI) を設定します。

```
void SetDpi(const CD2DSizeF& sizeDPI);
```

### <a name="parameters"></a>パラメーター

*sizeDPI*<br/>
レンダーターゲットの水平/垂直 Dpi を指定する0以上の値。

##  <a name="settags"></a>CRenderTarget:: SetTags

後続の描画操作のラベルを指定します。

```
void SetTags(
    D2D1_TAG tag1,
    D2D1_TAG tag2);
```

### <a name="parameters"></a>パラメーター

*tag1*<br/>
後続の描画操作に適用するラベル。

*tag2*<br/>
後続の描画操作に適用するラベル。

##  <a name="settextantialiasmode"></a>CRenderTarget:: Settextアンチエイリアスモード

後続のテキストおよびグリフ描画操作に使用するアンチエイリアシングモードを指定します。

```
void SetTextAntialiasMode(D2D1_TEXT_ANTIALIAS_MODE textAntialiasMode);
```

### <a name="parameters"></a>パラメーター

*Textアンチエイリアスモード*<br/>
後続のテキストおよびグリフ描画操作に使用するアンチエイリアシングモード。

##  <a name="settextrenderingparams"></a>  CRenderTarget::SetTextRenderingParams

後続のすべてのテキストおよびグリフ描画操作に適用されるテキスト表示オプションを指定します。

```
void SetTextRenderingParams(IDWriteRenderingParams* textRenderingParams = NULL);
```

### <a name="parameters"></a>パラメーター

*textRenderingParams*<br/>
後続のすべてのテキストおよびグリフ描画操作に適用されるテキスト表示オプション。現在のテキスト表示オプションをクリアする場合は NULL。

##  <a name="settransform"></a>CRenderTarget:: SetTransform

指定された変換をレンダーターゲットに適用し、既存の変換を置き換えます。 それ以降のすべての描画操作は、変換された領域で発生します。

```
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
void SetTransform(const D2D1_MATRIX_3X2_F& transform);
```

### <a name="parameters"></a>パラメーター

*transform*<br/>
レンダーターゲットに適用する変換。

##  <a name="verifyresource"></a>  CRenderTarget::VerifyResource

CD2DResource オブジェクトの有効性を検証します。オブジェクトがまだ存在しない場合は、作成します。

```
BOOL VerifyResource(CD2DResource* pResource);
```

### <a name="parameters"></a>パラメーター

*pResource*<br/>
CD2DResource オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

TRUE の場合、オブジェクトは有効です。それ以外の場合は FALSE。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
