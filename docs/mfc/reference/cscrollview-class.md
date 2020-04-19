---
title: CScrollView クラス
ms.date: 11/04/2016
f1_keywords:
- CScrollView
- AFXWIN/CScrollView
- AFXWIN/CScrollView::CScrollView
- AFXWIN/CScrollView::CheckScrollBars
- AFXWIN/CScrollView::FillOutsideRect
- AFXWIN/CScrollView::GetDeviceScrollPosition
- AFXWIN/CScrollView::GetDeviceScrollSizes
- AFXWIN/CScrollView::GetScrollPosition
- AFXWIN/CScrollView::GetTotalSize
- AFXWIN/CScrollView::ResizeParentToFit
- AFXWIN/CScrollView::ScrollToPosition
- AFXWIN/CScrollView::SetScaleToFitSize
- AFXWIN/CScrollView::SetScrollSizes
helpviewer_keywords:
- CScrollView [MFC], CScrollView
- CScrollView [MFC], CheckScrollBars
- CScrollView [MFC], FillOutsideRect
- CScrollView [MFC], GetDeviceScrollPosition
- CScrollView [MFC], GetDeviceScrollSizes
- CScrollView [MFC], GetScrollPosition
- CScrollView [MFC], GetTotalSize
- CScrollView [MFC], ResizeParentToFit
- CScrollView [MFC], ScrollToPosition
- CScrollView [MFC], SetScaleToFitSize
- CScrollView [MFC], SetScrollSizes
ms.assetid: 4ba16dac-1acb-4be0-bb55-5fb695b6948d
ms.openlocfilehash: b89daaae4bb578d328e1468cc29470825e19c670
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502590"
---
# <a name="cscrollview-class"></a>CScrollView クラス

スクロール機能を持つ[CView](../../mfc/reference/cview-class.md) 。

## <a name="syntax"></a>構文

```
class CScrollView : public CView
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CScrollView:: CScrollView](#cscrollview)|`CScrollView` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CScrollView:: CheckScrollBars](#checkscrollbars)|スクロールビューに水平スクロールバーと垂直スクロールバーがあるかどうかを示します。|
|[CScrollView:: FillOutsideRect](#filloutsiderect)|ビューの領域をスクロール領域の外側に塗りつぶします。|
|[CScrollView:: GetDeviceScrollPosition](#getdevicescrollposition)|デバイスユニット内の現在のスクロール位置を取得します。|
|[CScrollView:: GetDeviceScrollSizes](#getdevicescrollsizes)|スクロール可能なビューの現在のマッピングモード、合計サイズ、および行とページのサイズを取得します。 サイズはデバイス単位です。|
|[CScrollView:: GetScrollPosition](#getscrollposition)|現在のスクロール位置を論理単位で取得します。|
|[CScrollView:: GetTotalSize](#gettotalsize)|スクロールビューの論理単位の合計サイズを取得します。|
|[CScrollView:: ResizeParentToFit](#resizeparenttofit)|ビューのサイズによって、フレームのサイズが決まります。|
|[CScrollView:: ScrollToPosition](#scrolltoposition)|ビューを論理単位で指定された特定のポイントまでスクロールします。|
|[CScrollView:: SetScaleToFitSize](#setscaletofitsize)|スクロールビューをスケールインフィットモードにします。|
|[CScrollView:: SetScrollSizes](#setscrollsizes)|スクロールビューのマッピングモード、合計サイズ、および水平および垂直方向のスクロールの量を設定します。|

## <a name="remarks"></a>Remarks

から`CView`派生した任意のクラスで標準スクロールを処理できます。そのためには、メッセージマップされた[OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)および[onvscroll](../../mfc/reference/cwnd-class.md#onvscroll)メンバー関数をオーバーライドします。 ただし`CScrollView` 、 `CView`機能には次の機能が追加されています。

- ウィンドウおよびビューポートのサイズとマッピングモードを管理します。

- スクロールバーのメッセージに応じて自動的にスクロールします。

- キーボード、スクロール不可のマウス、または IntelliMouse ホイールからのメッセージに応じて自動的にスクロールされます。

キーボードからのメッセージに応じて自動的にスクロールするには、WM_KEYDOWN メッセージを追加し、VK_DOWN、VK_PREV、および[SetScrollPos](/windows/win32/api/winuser/nf-winuser-setscrollpos)を呼び出します。

[OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)および[OnRegisteredMouseWheel](../../mfc/reference/cwnd-class.md#onregisteredmousewheel)の各メンバー関数をオーバーライドすることにより、マウスホイールのスクロールを自分で処理できます。 これらのメンバー関数`CScrollView`は、の場合と同様に、ホイールローテーションメッセージの[WM_MOUSEWHEEL](/windows/win32/inputdev/wm-mousewheel)に対して推奨される動作をサポートしています。

自動スクロールを利用するには、から`CScrollView` `CView`ではなく、からビュークラスを派生させます。 ビューを最初に作成するときに、ドキュメントのサイズに基づいてスクロール可能なビューのサイズを計算する場合は、 `SetScrollSizes` [cview:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate)または[cview:: OnUpdate](../../mfc/reference/cview-class.md#onupdate)のいずれかのオーバーライドからメンバー関数を呼び出します。 (ドキュメントのサイズに対してクエリを実行するには、独自のコードを記述する必要があります。 例については、 [Scribble サンプル](../../overview/visual-cpp-samples.md)を参照してください)。

この`SetScrollSizes`メンバー関数を呼び出すと、ビューのマッピングモード、スクロールビューの合計サイズ、水平および垂直方向にスクロールする量が設定されます。 すべてのサイズは論理単位になります。 ビューの論理サイズは、通常、ドキュメントに格納されているデータから計算されますが、場合によっては、固定サイズを指定する必要があります。 両方の方法の例については、「 [CScrollView:: SetScrollSizes](#setscrollsizes)」を参照してください。

論理単位で水平方向および垂直方向にスクロールする量を指定します。 既定では、スクロールボックスの外側でスクロールバーのシャフトをクリックすると`CScrollView` 、"ページ" がスクロールされます。 スクロールバーのいずれかの端のスクロールバーの矢印ボタンをクリック`CScrollView`すると、"線" がスクロールされます。 既定では、ページはビューの合計サイズの1/10 です。行はページサイズの1/10 です。 メンバー関数でカスタムサイズを渡すことによっ`SetScrollSizes`て、これらの既定値をオーバーライドします。 たとえば、水平方向のサイズを、合計サイズの幅の一部に設定し、垂直方向のサイズを現在のフォントの行の高さに設定できます。

スクロールではなく`CScrollView` 、では、現在のウィンドウサイズに合わせてビューを自動的に拡大縮小できます。 このモードでは、ビューにスクロールバーは表示されず、ウィンドウのクライアント領域にぴったり合うように論理ビューが拡大または縮小されます。 このスケールインフィット機能を使用するには、 [CScrollView:: SetScaleToFitSize](#setscaletofitsize)を呼び出します。 (または`SetScaleToFitSize`の`SetScrollSizes`いずれかを呼び出しますが、両方は呼び出さないでください)。

派生ビュークラスの`CScrollView` `CPaintDC` `OnDraw`メンバー関数が呼び出される前に、によって渡されるデバイスコンテキストオブジェクトのビューポートの原点が自動的に調整されます。 `OnDraw`

スクロールウィンドウのビューポートの原点を調整する`CScrollView`には、は[CView:: OnPrepareDC](../../mfc/reference/cview-class.md#onpreparedc)をオーバーライドします。 この調整は、に`CPaintDC` `OnDraw`渡されるデバイスコンテキスト`CScrollView`に対して自動的に行うこと`CScrollView::OnPrepareDC`ができ`CClientDC`ますが、など、使用するその他のデバイスコンテキストに対しては、を呼び出す必要があります。 をオーバーライド`CScrollView::OnPrepareDC`すると、ペン、背景色、およびその他の描画属性を設定できますが、基本クラスを呼び出してスケーリングを行うことができます。

スクロールバーは、次の場合に示すように、ビューに対して相対的に3か所に表示されます。

- 標準ウィンドウスタイルのスクロールバーは、WS_HSCROLL および WS_VSCROLL[Windows スタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)を使用して、ビューに対して設定できます。

- また、スクロールバーコントロールをビューが含まれているフレームに追加することもできます。この場合、フレームワークは WM_HSCROLL と WM_VSCROLL のメッセージをフレームウィンドウから現在アクティブなビューに転送します。

- また、フレームワークは、 `CSplitterWnd`スプリッターコントロールから現在アクティブなスプリッターペイン (ビュー) にスクロールメッセージを転送します。 共有されたスクロールバーを使用して [CSplitterWnd](../../mfc/reference/csplitterwnd-class.md) `CScrollView`に配置すると、オブジェクトは独自のを作成するのではなく、共有されたものを使用します。

の使用方法`CScrollView`の詳細については、「 [MFC で使用できる](../../mfc/derived-view-classes-available-in-mfc.md)[ドキュメント/ビューアーキテクチャ](../../mfc/document-view-architecture.md)および派生ビュークラス」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CScrollView`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="checkscrollbars"></a>CScrollView:: CheckScrollBars

スクロールビューに水平と垂直のバーがあるかどうかを判断するには、このメンバー関数を呼び出します。

```
void CheckScrollBars(
    BOOL& bHasHorzBar,
    BOOL& bHasVertBar) const;
```

### <a name="parameters"></a>パラメーター

*bHasHorzBar*<br/>
アプリケーションに水平スクロールバーがあることを示します。

*bHasVertBar*<br/>
アプリケーションに垂直スクロールバーがあることを示します。

##  <a name="cscrollview"></a>CScrollView:: CScrollView

`CScrollView` オブジェクトを構築します。

```
CScrollView();
```

### <a name="remarks"></a>Remarks

スクロールビューが使用`SetScrollSizes`できる`SetScaleToFitSize`ようにするには、またはのいずれかを呼び出す必要があります。

##  <a name="filloutsiderect"></a>CScrollView:: FillOutsideRect

を`FillOutsideRect`呼び出して、スクロール領域の外側に表示されるビューの領域を塗りつぶします。

```
void FillOutsideRect(
    CDC* pDC,
    CBrush* pBrush);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
塗りつぶしを行うデバイスコンテキスト。

*pBrush*<br/>
領域の塗りつぶしに使用するブラシ。

### <a name="remarks"></a>Remarks

バックグラウンド`FillOutsideRect`で過度に再描画`OnEraseBkgnd`されるのを防ぐために、スクロールビューのハンドラー関数でを使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#164](../../mfc/codesnippet/cpp/cscrollview-class_1.cpp)]

##  <a name="getdevicescrollposition"></a>CScrollView:: GetDeviceScrollPosition

スクロール`GetDeviceScrollPosition`バーのスクロールボックスの現在の水平方向および垂直位置が必要な場合に、を呼び出します。

```
CPoint GetDeviceScrollPosition() const;
```

### <a name="return-value"></a>戻り値

`CPoint`オブジェクトとしてのスクロールボックスの水平方向および垂直方向の位置 (デバイス単位)。

### <a name="remarks"></a>Remarks

この座標ペアは、ビューの左上隅がスクロールされたドキュメント内の位置に対応します。 これは、マウスデバイスの位置をスクロールビューのデバイスの位置にずらす場合に便利です。

`GetDeviceScrollPosition`デバイス単位で値を返します。 論理ユニットが必要な場合は`GetScrollPosition` 、代わりにを使用します。

##  <a name="getdevicescrollsizes"></a>CScrollView:: GetDeviceScrollSizes

`GetDeviceScrollSizes`スクロール可能なビューの現在のマッピングモード、合計サイズ、および行とページのサイズを取得します。

```
void GetDeviceScrollSizes(
    int& nMapMode,
    SIZE& sizeTotal,
    SIZE& sizePage,
    SIZE& sizeLine) const;
```

### <a name="parameters"></a>パラメーター

*nMapMode*<br/>
このビューの現在のマッピングモードを返します。 使用可能な値の一覧につい`SetScrollSizes`ては、「」を参照してください。

*sizeTotal*<br/>
デバイス単位でのスクロールビューの現在の合計サイズを返します。

*sizePage*<br/>
スクロールバーのシャフトでのマウスクリックに応じて、各方向にスクロールする現在の水平および垂直の量を返します。 この`cx`メンバーには、水平方向の金額が含まれています。 この`cy`メンバーには、垂直方向の金額が含まれています。

*siz*<br/>
スクロールボタンのマウスクリックに応じて、各方向にスクロールする現在の水平および垂直の量を返します。 この`cx`メンバーには、水平方向の金額が含まれています。 この`cy`メンバーには、垂直方向の金額が含まれています。

### <a name="remarks"></a>Remarks

サイズはデバイス単位です。 このメンバー関数は、と呼ばれることはほとんどありません。

##  <a name="getscrollposition"></a>CScrollView:: GetScrollPosition

スクロール`GetScrollPosition`バーのスクロールボックスの現在の水平方向および垂直位置が必要な場合に、を呼び出します。

```
CPoint GetScrollPosition() const;
```

### <a name="return-value"></a>戻り値

`CPoint`オブジェクトとしてのスクロールボックスの水平方向と垂直位置 (論理単位)。

### <a name="remarks"></a>Remarks

この座標ペアは、ビューの左上隅がスクロールされたドキュメント内の位置に対応します。

`GetScrollPosition`論理単位で値を返します。 デバイスユニットが必要な場合は`GetDeviceScrollPosition` 、代わりにを使用します。

##  <a name="gettotalsize"></a>CScrollView:: GetTotalSize

を`GetTotalSize`呼び出して、スクロールビューの現在の水平方向と垂直方向のサイズを取得します。

```
CSize GetTotalSize() const;
```

### <a name="return-value"></a>戻り値

スクロールビューの論理単位の合計サイズ。 水平方向のサイズは、 `cx` `CSize`戻り値のメンバーに含まれています。 垂直方向のサイズは、 `cy`メンバーに含まれています。

##  <a name="resizeparenttofit"></a>CScrollView:: ResizeParentToFit

を`ResizeParentToFit`呼び出して、ビューのサイズによってフレームウィンドウのサイズを決定します。

```
void ResizeParentToFit(BOOL bShrinkOnly = TRUE);
```

### <a name="parameters"></a>パラメーター

*bShrinkOnly*<br/>
実行するサイズ変更の種類。 既定値は TRUE で、必要に応じてフレームウィンドウが縮小されます。 大きいビューや小さいフレームウィンドウでは、スクロールバーが表示されます。 FALSE の値を指定すると、ビューは常にフレームウィンドウのサイズを正確に変更します。 フレームウィンドウが大きすぎてマルチドキュメントインターフェイス (MDI) フレームウィンドウまたは画面に収まりきらない可能性があるため、これは多少危険になることがあります。

### <a name="remarks"></a>Remarks

これは、MDI 子フレームウィンドウのビューに対してのみ推奨されます。 `OnInitialUpdate`派生`ResizeParentToFit` クラスのハンドラー関数でを`CScrollView`使用します。 このメンバー関数の例については、「 [CScrollView:: SetScrollSizes](#setscrollsizes)」を参照してください。

`ResizeParentToFit`ビューウィンドウのサイズが設定されていることを前提としています。 が呼び出されたときに`ResizeParentToFit`ビューウィンドウのサイズが設定されていない場合は、アサーションが発生します。 これが行われないようにするには、を呼び出す`ResizeParentToFit`前に、次の呼び出しを行います。

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="scrolltoposition"></a>CScrollView:: ScrollToPosition

を`ScrollToPosition`呼び出して、ビュー内の特定のポイントまでスクロールします。

```
void ScrollToPosition(POINT pt);
```

### <a name="parameters"></a>パラメーター

*未満*<br/>
論理単位でスクロールするポイント。 メンバー `x`は、正の値 (0 以上、ビューの合計サイズまで) である必要があります。 マッピングモードが MM_TEXT の場合`y`も、メンバーに対して同じことが当てはまります。 MM_TEXT `y`以外のマッピングモードでは、メンバーは負の値です。

### <a name="remarks"></a>Remarks

このポイントがウィンドウの左上隅になるように、ビューがスクロールされます。 ビューが合わせて拡大縮小されている場合は、このメンバー関数を呼び出さないでください。

##  <a name="setscaletofitsize"></a>CScrollView:: SetScaleToFitSize

ビュー `SetScaleToFitSize`ポートのサイズを現在のウィンドウサイズに自動的にスケーリングする場合は、を呼び出します。

```
void SetScaleToFitSize(SIZE sizeTotal);
```

### <a name="parameters"></a>パラメーター

*sizeTotal*<br/>
ビューをスケーリングする水平方向および垂直方向のサイズ。 スクロールビューのサイズは、論理単位で測定されます。 水平方向のサイズは、 `cx`メンバーに含まれています。 垂直方向のサイズは、 `cy`メンバーに含まれています。 `cx` と`cy`はどちらも0以上である必要があります。

### <a name="remarks"></a>Remarks

スクロールバーでは、論理ビューの一部だけがいつでも表示される場合があります。 ただし、スケールツーフィット機能を使用すると、ビューにはスクロールバーがなく、ウィンドウのクライアント領域に合わせて論理ビューが拡大または縮小されます。 ウィンドウのサイズを変更すると、ウィンドウのサイズに基づいて新しいスケールでデータが描画されます。

通常、ビューの`SetScaleToFitSize` `OnInitialUpdate`メンバー関数のオーバーライドでは、への呼び出しを配置します。 自動スケーリングを使用しない場合は、代わりに`SetScrollSizes`メンバー関数を呼び出します。

`SetScaleToFitSize`"最適なサイズに拡大" 操作を実装するために使用できます。 スクロール`SetScrollSizes`を再初期化するために使用します。

`SetScaleToFitSize`ビューウィンドウのサイズが設定されていることを前提としています。 が呼び出されたときに`SetScaleToFitSize`ビューウィンドウのサイズが設定されていない場合は、アサーションが発生します。 これが行われないようにするには、を呼び出す`SetScaleToFitSize`前に、次の呼び出しを行います。

[!code-cpp[NVC_MFCDocView#165](../../mfc/codesnippet/cpp/cscrollview-class_2.cpp)]

##  <a name="setscrollsizes"></a>CScrollView:: SetScrollSizes

ビュー `SetScrollSizes`を更新しようとしているときに、を呼び出します。

```
void SetScrollSizes(
    int nMapMode,
    SIZE sizeTotal,
    const SIZE& sizePage = sizeDefault,
    const SIZE& sizeLine = sizeDefault);
```

### <a name="parameters"></a>パラメーター

*nMapMode*<br/>
このビューに設定するマッピングモード。 次のような値となる場合があります。

|マッピングモード|論理ユニット|正の y 軸の拡張...|
|------------------|------------------|---------------------------------|
|MM_TEXT|1ピクセル|下向き|
|MM_HIMETRIC|0.01 mm|上向き|
|MM_TWIPS|1/1440|上向き|
|MM_HIENGLISH|0.001|上向き|
|MM_LOMETRIC|0.1 mm|上向き|
|MM_LOENGLISH|0.01|上向き|

これらのモードはすべて、Windows で定義されています。 MM_ISOTROPIC と MM_ANISOTROPIC という2つの標準マッピングモードは、 `CScrollView`には使用されません。 クラスライブラリには、 `SetScaleToFitSize`ビューをウィンドウサイズにスケーリングするためのメンバー関数が用意されています。 上の表の3列目は、座標の向きを示しています。

*sizeTotal*<br/>
スクロールビューの合計サイズ。 メンバー `cx`には、水平方向のエクステントが含まれます。 この`cy`メンバーには、垂直方向のエクステントが含まれます。 サイズは論理単位です。 `cx` と`cy`はどちらも0以上である必要があります。

*sizePage*<br/>
スクロールバーのシャフトでのマウスクリックに応じて、各方向にスクロールする水平および垂直の量。 この`cx`メンバーには、水平方向の金額が含まれています。 この`cy`メンバーには、垂直方向の金額が含まれています。

*siz*<br/>
スクロールバーの矢印の中でマウスクリックに応答して、各方向にスクロールする水平および垂直の量。 この`cx`メンバーには、水平方向の金額が含まれています。 この`cy`メンバーには、垂直方向の金額が含まれています。

### <a name="remarks"></a>Remarks

たとえば、ドキュメントが最初に表示`OnUpdate`されたときや、サイズが変更されたときに、スクロールの特性を調整するために、メンバー関数のオーバーライドで呼び出します。

通常、派生したドキュメントクラスで提供するドキュメントメンバー関数 ( `GetMyDocSize`など) を呼び出すことによって、ビューに関連付けられたドキュメントからサイズ情報を取得します。 次のコードは、この方法を示しています。

[!code-cpp[NVC_MFCDocView#166](../../mfc/codesnippet/cpp/cscrollview-class_3.cpp)]

また、次のコードのように、固定サイズの設定が必要になる場合もあります。

[!code-cpp[NVC_MFCDocView#167](../../mfc/codesnippet/cpp/cscrollview-class_4.cpp)]

マッピングモードは、MM_ISOTROPIC または MM_ANISOTROPIC を除くすべての Windows マッピングモードに設定する必要があります。 制約の`SetScaleToFitSize` `SetScrollSizes`ないマッピングモードを使用する場合は、ではなくメンバー関数を呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#168](../../mfc/codesnippet/cpp/cscrollview-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#169](../../mfc/codesnippet/cpp/cscrollview-class_6.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプル DIBLOOK](../../overview/visual-cpp-samples.md)<br/>
[CView クラス](../../mfc/reference/cview-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CView クラス](../../mfc/reference/cview-class.md)<br/>
[CSplitterWnd クラス](../../mfc/reference/csplitterwnd-class.md)
