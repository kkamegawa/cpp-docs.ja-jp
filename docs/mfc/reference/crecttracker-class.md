---
title: CRectTracker クラス
ms.date: 11/19/2018
f1_keywords:
- CRectTracker
- AFXEXT/CRectTracker
- AFXEXT/CRectTracker::CRectTracker
- AFXEXT/CRectTracker::AdjustRect
- AFXEXT/CRectTracker::Draw
- AFXEXT/CRectTracker::DrawTrackerRect
- AFXEXT/CRectTracker::GetHandleMask
- AFXEXT/CRectTracker::GetTrueRect
- AFXEXT/CRectTracker::HitTest
- AFXEXT/CRectTracker::NormalizeHit
- AFXEXT/CRectTracker::OnChangedRect
- AFXEXT/CRectTracker::SetCursor
- AFXEXT/CRectTracker::Track
- AFXEXT/CRectTracker::TrackRubberBand
- AFXEXT/CRectTracker::m_nHandleSize
- AFXEXT/CRectTracker::m_nStyle
- AFXEXT/CRectTracker::m_rect
- AFXEXT/CRectTracker::m_sizeMin
helpviewer_keywords:
- CRectTracker [MFC], CRectTracker
- CRectTracker [MFC], AdjustRect
- CRectTracker [MFC], Draw
- CRectTracker [MFC], DrawTrackerRect
- CRectTracker [MFC], GetHandleMask
- CRectTracker [MFC], GetTrueRect
- CRectTracker [MFC], HitTest
- CRectTracker [MFC], NormalizeHit
- CRectTracker [MFC], OnChangedRect
- CRectTracker [MFC], SetCursor
- CRectTracker [MFC], Track
- CRectTracker [MFC], TrackRubberBand
- CRectTracker [MFC], m_nHandleSize
- CRectTracker [MFC], m_nStyle
- CRectTracker [MFC], m_rect
- CRectTracker [MFC], m_sizeMin
ms.assetid: 99caa7f2-3c0d-4a42-bbee-e5d1d342d4ee
ms.openlocfilehash: 9c54cdfecfa6c4ff0eef7e16003ab2097553953d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372276"
---
# <a name="crecttracker-class"></a>CRectTracker クラス

項目を表示、移動、または異なる方法でサイズ変更を許可します。

## <a name="syntax"></a>構文

```
class CRectTracker
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[利用](#crecttracker)|`CRectTracker` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CRectTracker::AdjustRect](#adjustrect)|四角形のサイズが変更されたときに呼び出されます。|
|[CRectTracker::Draw](#draw)|四角形をレンダリングします。|
|[CRectTracker::DrawTrackerRect](#drawtrackerrect)|境界線を描画するときに呼び出されます、`CRectTracker`オブジェクト。|
|[CRectTracker::GetHandleMask](#gethandlemask)|マスクを取得するという、`CRectTracker`項目のサイズ変更ハンドル。|
|[CRectTracker::GetTrueRect](#gettruerect)|サイズ変更ハンドルを含む四角形の幅と高さを返します。|
|[CRectTracker::HitTest](#hittest)|関連するカーソルの現在位置を返します、`CRectTracker`オブジェクト。|
|[CRectTracker::NormalizeHit](#normalizehit)|ヒット テストのコードを正規化します。|
|[CRectTracker::OnChangedRect](#onchangedrect)|四角形のサイズを変更または移動したときに呼び出されます。|
|[CRectTracker::SetCursor](#setcursor)|四角形の上の位置によって、カーソルを設定します。|
|[反転](#track)|四角形を操作できます。|
|[CRectTracker::TrackRubberBand](#trackrubberband)|ユーザーが「ラバー バンド」を選択をできます。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CRectTracker::m_nHandleSize](#m_nhandlesize)|サイズ変更ハンドルのサイズを決定します。|
|[CRectTracker::m_nStyle](#m_nstyle)|トラッカーの現在のスタイル。|
|[裏返し](#m_rect)|四角形のピクセル単位で現在の位置。|
|[CRectTracker::m_sizeMin](#m_sizemin)|最小の四角形の幅と高さを決定します。|

## <a name="remarks"></a>Remarks

`CRectTracker` 基本クラスはありません。

ただし、`CRectTracker`クラスがグラフィカル インターフェイスを使用して OLE アイテムと対話するユーザーを許可するように設計、その使用は OLE 対応のアプリケーションに制限されません。 使用できる任意の場所、このようなユーザー インターフェイスが必要です。

`CRectTracker` 罫線は、solid または点線。 項目の破線の境界線または斜線パターンを項目のさまざまな状態を示すために重なって表示できます。 8 つのサイズ変更ハンドルを配置するには、外部または内部のいずれかのアイテムの罫線。 (サイズ変更ハンドルの詳細については、次を参照してください[GetHandleMask](#gethandlemask)。)。最後に、`CRectTracker`サイズ変更時に、項目の向きを変更することができます。

使用する`CRectTracker`、構築、`CRectTracker`オブジェクトし、どの表示状態が初期化されるかを指定します。 関連付けられている OLE 項目の現在の状態についてユーザーに視覚的フィードバックを提供するこのインターフェイスを使用することができますし、`CRectTracker`オブジェクト。

使用しての詳細については`CRectTracker`、記事をご覧ください[トラッカー](../../mfc/trackers.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`CRectTracker`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxext.h

##  <a name="adjustrect"></a>  CRectTracker::AdjustRect

サイズ変更ハンドルを使用して、追跡する四角形のサイズが変更されたときに、フレームワークによって呼び出されます。

```
virtual void AdjustRect(
    int nHandle,
    LPRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*nHandle*<br/>
使用されるハンドルのインデックス。

*lpRect*<br/>
現在の四角形のサイズへのポインター。 (四角形のサイズは、その高さと幅で指定されます)。

### <a name="remarks"></a>Remarks

この関数の既定の動作により、四角形の向きを変更する場合にのみを`Track`と`TrackRubberBand`許可と呼ばれます。

ドラッグ操作中に追跡する四角形の調整を制御するには、この関数をオーバーライドします。 1 つの方法は、によって指定された座標を調整する*lpRect*を返す前にします。

特殊な機能によって直接サポートされていない`CRectTracker`などグリッドにスナップまたは保持の縦横比は、この関数をオーバーライドすることで実装できます。

##  <a name="crecttracker"></a>  CRectTracker::CRectTracker

作成し、初期化、`CRectTracker`オブジェクト。

```
CRectTracker();

CRectTracker(
    LPCRECT lpSrcRect,
    UINT nStyle);
```

### <a name="parameters"></a>パラメーター

*lpSrcRect*<br/>
四角形オブジェクトの座標。

*nStyle*<br/>
スタイルを指定します、`CRectTracker`オブジェクト。 次のスタイルがサポートされています。

- `CRectTracker::solidLine` 四角形の枠線の実線を使用します。

- `CRectTracker::dottedLine` 四角形の境界線の点線を使用します。

- `CRectTracker::hatchedBorder` 四角形の境界線の斜線パターンを使用します。

- `CRectTracker::resizeInside` 四角形の内側にあるハンドルのサイズを変更します。

- `CRectTracker::resizeOutside` 四角形の外側にあるハンドルのサイズを変更します。

- `CRectTracker::hatchInside` パターンでは四角形全体をハッチします。

### <a name="remarks"></a>Remarks

既定のコンス トラクター、`CRectTracker`オブジェクトから値を持つ*lpSrcRect*し、システムの既定値を他のサイズを初期化します。 パラメーターなしで、オブジェクトが作成された場合、`m_rect`と`m_nStyle`データ メンバーは初期化されていません。

##  <a name="draw"></a>  CRectTracker::Draw

四角形の外枠と内部の領域を描画するには、この関数を呼び出します。

```
void Draw(CDC* pDC) const;
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
描画するデバイス コンテキストへのポインター。

### <a name="remarks"></a>Remarks

トラッカーのスタイルは、描画を行う方法を決定します。 コンス トラクターを参照してください。`CRectTracker`使用可能なスタイルの詳細についてはします。

##  <a name="drawtrackerrect"></a>  CRectTracker::DrawTrackerRect

トラッカーの位置が変わるたびにフレームワークによって呼び出さ内に、`Track`または`TrackRubberBand`メンバー関数。

```
virtual void DrawTrackerRect(
    LPCRECT lpRect,
    CWnd* pWndClipTo,
    CDC* pDC,
    CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
ポインター、`RECT`描画する四角形を格納しています。

*pWndClipTo*<br/>
クリッピング四角形で使用するウィンドウへのポインター。

*pDC*<br/>
描画するデバイス コンテキストへのポインター。

*我が物*<br/>
描画が発生するウィンドウへのポインター。

### <a name="remarks"></a>Remarks

既定の実装への呼び出しは、 `CDC::DrawFocusRect`、ピリオドで区切られた四角形を描画します。

追跡操作中にさまざまなフィードバックを提供するには、この関数をオーバーライドします。

##  <a name="gethandlemask"></a>  CRectTracker::GetHandleMask

フレームワークは、四角形のサイズ変更ハンドルのマスクを取得するには、このメンバー関数を呼び出します。

```
virtual UINT GetHandleMask() const;
```

### <a name="return-value"></a>戻り値

マスクを`CRectTracker`項目のサイズ変更ハンドル。

### <a name="remarks"></a>Remarks

サイズ変更ハンドルは、両側または四角形の角に表示され、四角形のサイズと形状を制御するユーザーを許可します。

四角形が 8 のサイズ変更ハンドルが 0 ~ 7 の番号です。 各サイズ変更ハンドルで表されるビット マスク内ビットの値は 2 ^ *n*ここで、 *n*はサイズ変更ハンドルの数です。 ビット 0 ~ 3 は、時計回りに移動の左上に開始角のサイズ変更ハンドルに対応します。 ビット 4 ~ 7 の側面に対応にサイズ変更ハンドルの時計回りの上部で開始を指定します。 次の図は、四角形のサイズ変更を処理し、それに対応するハンドル番号と値のサイズを変更します。

![ハンドル番号のサイズ変更](../../mfc/reference/media/vc35dp1.gif "サイズ変更ハンドルの番号")

既定の実装`GetHandleMask`サイズ変更ハンドルが表示されるように、次のビット マスクを返します。 1 つのビットがある場合は、対応するサイズ変更ハンドルが描画されます。

指定されたサイズ変更ハンドルを表示または非表示には、このメンバー関数をオーバーライドします。

##  <a name="gettruerect"></a>  CRectTracker::GetTrueRect

四角形の座標を取得するには、この関数を呼び出します。

```
void GetTrueRect(LPRECT lpTrueRect) const;
```

### <a name="parameters"></a>パラメーター

*lpTrueRect*<br/>
ポインター、`RECT`デバイスを含む構造体の各座標、`CRectTracker`オブジェクト。

### <a name="remarks"></a>Remarks

四角形の寸法には、外側の境界線上にある任意のサイズ変更ハンドルの幅と高さが含まれます。 *呼び出しから戻ると*デバイス座標で正規化された四角形は、常にします。

##  <a name="hittest"></a>  CRectTracker::HitTest

ユーザーがサイズ変更ハンドルを取得したかどうかを確認するには、この関数を呼び出します。

```
int HitTest(CPoint point) const;
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
テストする、デバイス座標でのポイント。

### <a name="return-value"></a>戻り値

返される値は列挙型に基づいて`CRectTracker::TrackerHit`値は次のいずれかを指定できます。

- `CRectTracker::hitNothing` -1

- `CRectTracker::hitTopLeft` 0

- `CRectTracker::hitTopRight` 1

- `CRectTracker::hitBottomRight` 2

- `CRectTracker::hitBottomLeft` 3

- `CRectTracker::hitTop` 4

- `CRectTracker::hitRight` 5

- `CRectTracker::hitBottom` 6

- `CRectTracker::hitLeft` 7

- `CRectTracker::hitMiddle` 8

##  <a name="m_nhandlesize"></a>  CRectTracker::m_nHandleSize

サイズをピクセル単位での`CRectTracker`ハンドルのサイズを変更します。

```
int m_nHandleSize;
```

### <a name="remarks"></a>Remarks

システムの既定値で初期化します。

##  <a name="m_rect"></a>  裏返し

四角形の現在の位置をクライアント座標 (ピクセル単位)。

```
CRect m_rect;
```

##  <a name="m_sizemin"></a>  CRectTracker::m_sizeMin

四角形の最小サイズ。

```
CSize m_sizeMin;
```

### <a name="remarks"></a>Remarks

両方の既定値`cx`と`cy`罫線の幅に関する既定のシステム値から計算されます。 このデータ メンバーがでのみ使用、`AdjustRect`メンバー関数。

##  <a name="m_nstyle"></a>  CRectTracker::m_nStyle

四角形の現在のスタイル。

```
UINT m_nStyle;
```

### <a name="remarks"></a>Remarks

参照してください[利用](#crecttracker)可能なスタイルの一覧についてはします。

##  <a name="normalizehit"></a>  CRectTracker::NormalizeHit

可能性のある下向きのハンドルを変換するには、この関数を呼び出します。

```
int NormalizeHit(int nHandle) const;
```

### <a name="parameters"></a>パラメーター

*nHandle*<br/>
ユーザーが選択されているハンドル。

### <a name="return-value"></a>戻り値

正規化されたハンドルのインデックス。

### <a name="remarks"></a>Remarks

ときに`CRectTracker::Track`または`CRectTracker::TrackRubberBand`と呼びますで許可されているを反転するには、四角形を x 軸、y 軸、またはその両方に反転させることはできます。 この場合、`HitTest`は四角形が反転されるハンドルを返します。 これはフィードバックが変更される四角形のデータ構造の部分ではなく、四角形の画面位置に依存するためには描画のカーソル フィードバック適していません。

##  <a name="onchangedrect"></a>  CRectTracker::OnChangedRect

トラッカー四角形の呼び出し中に変更されるたびにフレームワークによって呼び出さ`Track`します。

```
virtual void OnChangedRect(const CRect& rectOld);
```

### <a name="parameters"></a>パラメーター

*rectOld*<br/>
古いデバイス座標が含まれています、`CRectTracker`オブジェクト。

### <a name="remarks"></a>Remarks

時にこの関数が呼び出されると、すべてのフィードバックを使用して描画`DrawTrackerRect`が削除されました。 この関数の既定の実装は、何も行いません。

四角形のサイズが変更された後に何らかのアクションを実行する場合に、この関数をオーバーライドします。

##  <a name="setcursor"></a>  CRectTracker::SetCursor

スタイラスがカーソルの形状を変更するには、この関数を呼び出して、`CRectTracker`のオブジェクトの領域。

```
BOOL SetCursor(
    CWnd* pWnd,
    UINT nHitTest) const;
```

### <a name="parameters"></a>パラメーター

*我が物*<br/>
カーソルを現在含まれているウィンドウへのポインター。

*nHitTest*<br/>
WM_SETCURSOR メッセージから、前のヒット テストの結果。

### <a name="return-value"></a>戻り値

前のヒットがトラッカー四角形の; 経由の場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

WM_SETCURSOR メッセージを処理するウィンドウの関数内からこの関数を呼び出す (通常`OnSetCursor`)。

##  <a name="track"></a>  CRectTracker::Track

四角形のサイズを変更するユーザー インターフェイスを表示するには、この関数を呼び出します。

```
BOOL Track(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = FALSE,
    CWnd* pWndClipTo = NULL);
```

### <a name="parameters"></a>パラメーター

*我が物*<br/>
四角形を含むウィンドウ オブジェクト。

*ポイント*<br/>
デバイス座標のクライアント領域を基準と現在のマウスの位置。

*bAllowInvert*<br/>
TRUE の場合、x 軸または y 軸に沿った四角形を反転します。それ以外の場合は FALSE です。

*pWndClipTo*<br/>
描画操作にクリップされるウィンドウです。 NULL の場合、*我が物*クリッピング四角形として使用されます。

### <a name="return-value"></a>戻り値

ESC キーが押された場合は、追跡プロセスが停止したし、トラッカーに格納されている四角形は変更されません 0 が返されます。 変更がコミットされると、マウスを移動すると、マウスの左ボタンを解放する、新しい位置やサイズがトラッカーの四角形に記録され、0 以外の値が返されます。

### <a name="remarks"></a>Remarks

通常、処理するアプリケーションの関数の内部から呼び出されます、`WM_LBUTTONDOWN`メッセージ (通常`OnLButtonDown`)。

この関数は、ユーザーがマウスの左ボタンを離す、ESC キーを押すかマウスの右ボタンを押すまでマウスをキャプチャします。 呼び出すことによって、フィードバックを更新するように、ユーザーがマウス カーソルを移動`DrawTrackerRect`と`OnChangedRect`します。

場合*bAllowInvert*が true の場合、x 軸または y 軸のいずれかの追跡の四角形を反転することができます。

##  <a name="trackrubberband"></a>  CRectTracker::TrackRubberBand

ラバー バンド選択を行うには、この関数を呼び出します。

```
BOOL TrackRubberBand(
    CWnd* pWnd,
    CPoint point,
    BOOL bAllowInvert = TRUE);
```

### <a name="parameters"></a>パラメーター

*我が物*<br/>
四角形を含むウィンドウ オブジェクト。

*ポイント*<br/>
デバイス座標のクライアント領域を基準と現在のマウスの位置。

*bAllowInvert*<br/>
TRUE の場合、x 軸または y 軸に沿った四角形を反転します。それ以外の場合は FALSE です。

### <a name="return-value"></a>戻り値

0 以外の場合、マウスが移動したし、の四角形が空です。それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

通常、WM_LBUTTONDOWN メッセージを処理するアプリケーションの関数の内部から呼び出されます (通常`OnLButtonDown`)。

この関数は、ユーザーがマウスの左ボタンを離す、ESC キーを押すかマウスの右ボタンを押すまでマウスをキャプチャします。 呼び出すことによって、フィードバックを更新するように、ユーザーがマウス カーソルを移動`DrawTrackerRect`と`OnChangedRect`します。

追跡は、右下ハンドルからゴム、バンドの種類の選択で実行されます。 反転が許可されているいずれかを左またはダウンと右側にドラッグして四角形のサイズが設定できます。

## <a name="see-also"></a>関連項目

[MFC のサンプルの追跡ツール](../../overview/visual-cpp-samples.md)<br/>
[MFC サンプル DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleResizeBar クラス](../../mfc/reference/coleresizebar-class.md)<br/>
[CRect クラス](../../atl-mfc-shared/reference/crect-class.md)
