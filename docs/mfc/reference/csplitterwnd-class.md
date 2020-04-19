---
title: CSplitterWnd クラス
ms.date: 11/04/2016
f1_keywords:
- CSplitterWnd
- AFXEXT/CSplitterWnd
- AFXEXT/CSplitterWnd::CSplitterWnd
- AFXEXT/CSplitterWnd::ActivateNext
- AFXEXT/CSplitterWnd::CanActivateNext
- AFXEXT/CSplitterWnd::Create
- AFXEXT/CSplitterWnd::CreateScrollBarCtrl
- AFXEXT/CSplitterWnd::CreateStatic
- AFXEXT/CSplitterWnd::CreateView
- AFXEXT/CSplitterWnd::DeleteColumn
- AFXEXT/CSplitterWnd::DeleteRow
- AFXEXT/CSplitterWnd::DeleteView
- AFXEXT/CSplitterWnd::DoKeyboardSplit
- AFXEXT/CSplitterWnd::DoScroll
- AFXEXT/CSplitterWnd::DoScrollBy
- AFXEXT/CSplitterWnd::GetActivePane
- AFXEXT/CSplitterWnd::GetColumnCount
- AFXEXT/CSplitterWnd::GetColumnInfo
- AFXEXT/CSplitterWnd::GetPane
- AFXEXT/CSplitterWnd::GetRowCount
- AFXEXT/CSplitterWnd::GetRowInfo
- AFXEXT/CSplitterWnd::GetScrollStyle
- AFXEXT/CSplitterWnd::IdFromRowCol
- AFXEXT/CSplitterWnd::IsChildPane
- AFXEXT/CSplitterWnd::IsTracking
- AFXEXT/CSplitterWnd::RecalcLayout
- AFXEXT/CSplitterWnd::SetActivePane
- AFXEXT/CSplitterWnd::SetColumnInfo
- AFXEXT/CSplitterWnd::SetRowInfo
- AFXEXT/CSplitterWnd::SetScrollStyle
- AFXEXT/CSplitterWnd::SplitColumn
- AFXEXT/CSplitterWnd::SplitRow
- AFXEXT/CSplitterWnd::OnDraw
- AFXEXT/CSplitterWnd::OnDrawSplitter
- AFXEXT/CSplitterWnd::OnInvertTracker
helpviewer_keywords:
- CSplitterWnd [MFC], CSplitterWnd
- CSplitterWnd [MFC], ActivateNext
- CSplitterWnd [MFC], CanActivateNext
- CSplitterWnd [MFC], Create
- CSplitterWnd [MFC], CreateScrollBarCtrl
- CSplitterWnd [MFC], CreateStatic
- CSplitterWnd [MFC], CreateView
- CSplitterWnd [MFC], DeleteColumn
- CSplitterWnd [MFC], DeleteRow
- CSplitterWnd [MFC], DeleteView
- CSplitterWnd [MFC], DoKeyboardSplit
- CSplitterWnd [MFC], DoScroll
- CSplitterWnd [MFC], DoScrollBy
- CSplitterWnd [MFC], GetActivePane
- CSplitterWnd [MFC], GetColumnCount
- CSplitterWnd [MFC], GetColumnInfo
- CSplitterWnd [MFC], GetPane
- CSplitterWnd [MFC], GetRowCount
- CSplitterWnd [MFC], GetRowInfo
- CSplitterWnd [MFC], GetScrollStyle
- CSplitterWnd [MFC], IdFromRowCol
- CSplitterWnd [MFC], IsChildPane
- CSplitterWnd [MFC], IsTracking
- CSplitterWnd [MFC], RecalcLayout
- CSplitterWnd [MFC], SetActivePane
- CSplitterWnd [MFC], SetColumnInfo
- CSplitterWnd [MFC], SetRowInfo
- CSplitterWnd [MFC], SetScrollStyle
- CSplitterWnd [MFC], SplitColumn
- CSplitterWnd [MFC], SplitRow
- CSplitterWnd [MFC], OnDraw
- CSplitterWnd [MFC], OnDrawSplitter
- CSplitterWnd [MFC], OnInvertTracker
ms.assetid: fd0de258-6dbe-4552-9e47-a39de0471d51
ms.openlocfilehash: 065735c13a3e763208142eb6bc989d3a496221f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323818"
---
# <a name="csplitterwnd-class"></a>CSplitterWnd クラス

分割ウィンドウの機能が用意されています。分割ウィンドウとは複数のペインを持つウィンドウです。

## <a name="syntax"></a>構文

```
class CSplitterWnd : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSplitterWnd::CSplitterWnd](#csplitterwnd)|構築への呼び出しを`CSplitterWnd`オブジェクト。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSplitterWnd::ActivateNext](#activatenext)|次のペインまたは前のペインのコマンドを実行します。|
|[CSplitterWnd::CanActivateNext](#canactivatenext)|次のペインまたは前のペイン コマンドが現在可能かどうかを確認します。|
|[CSplitterWnd::Create](#create)|動的分割ウィンドウを作成し、アタッチ先への呼び出し、`CSplitterWnd`オブジェクト。|
|[CSplitterWnd::CreateScrollBarCtrl](#createscrollbarctrl)|共有のスクロール バー コントロールを作成します。|
|[CSplitterWnd::CreateStatic](#createstatic)|静的分割ウィンドウを作成し、アタッチ先への呼び出し、`CSplitterWnd`オブジェクト。|
|[CSplitterWnd::CreateView](#createview)|分割ウィンドウのウィンドウの作成を呼び出します。|
|[CSplitterWnd::DeleteColumn](#deletecolumn)|スプリッター ウィンドウから列を削除します。|
|[CSplitterWnd::DeleteRow](#deleterow)|スプリッター ウィンドウから行を削除します。|
|[CSplitterWnd::DeleteView](#deleteview)|スプリッター ウィンドウからビューを削除します。|
|[あると](#dokeyboardsplit)|キーボード分割コマンドでは、通常は「ウィンドウの分割します。」を実行します。|
|[CSplitterWnd::DoScroll](#doscroll)|分割ウィンドウの同期スクロールを実行します。|
|[CSplitterWnd::DoScrollBy](#doscrollby)|指定されたピクセル数で、分割ウィンドウをスクロールします。|
|[CSplitterWnd::GetActivePane](#getactivepane)|フォーカスまたはアクティブなビュー、フレーム内のアクティブなペインを決定します。|
|[CSplitterWnd::GetColumnCount](#getcolumncount)|現在のウィンドウの列数を返します。|
|[CSplitterWnd::GetColumnInfo](#getcolumninfo)|指定した列に情報を返します。|
|[CSplitterWnd::GetPane](#getpane)|指定した行および列にあるペインを返します。|
|[CSplitterWnd::GetRowCount](#getrowcount)|現在のウィンドウの行の数を返します。|
|[CSplitterWnd::GetRowInfo](#getrowinfo)|指定された行情報を返します。|
|[CSplitterWnd::GetScrollStyle](#getscrollstyle)|共有のスクロール バー スタイルを返します。|
|[CSplitterWnd::IdFromRowCol](#idfromrowcol)|指定した行および列にあるウィンドウのウィンドウ ID の子を返します。|
|[CSplitterWnd::IsChildPane](#ischildpane)|ウィンドウが、現在このスプリッター ウィンドウの子ウィンドウかどうかを判断する呼び出しです。|
|[CSplitterWnd::IsTracking](#istracking)|分割バーは現在移動中かを決定します。|
|[CSplitterWnd::RecalcLayout](#recalclayout)|スプリッター ウィンドウを表示し、行または列のサイズを調整した後の呼び出しです。|
|[CSplitterWnd::SetActivePane](#setactivepane)|フレームのアクティブ状態であるペインを設定します。|
|[CSplitterWnd::SetColumnInfo](#setcolumninfo)|指定した列の情報を設定する呼び出し。|
|[CSplitterWnd::SetRowInfo](#setrowinfo)|指定した行の情報を設定する呼び出し。|
|[CSplitterWnd::SetScrollStyle](#setscrollstyle)|スクロール バーのサポートを共有の分割ウィンドウで、新しいスクロール バー スタイルを指定します。|
|[CSplitterWnd::SplitColumn](#splitcolumn)|フレーム ウィンドウが垂直方向に分割される場所を示します。|
|[CSplitterWnd::SplitRow](#splitrow)|フレーム ウィンドウを水平方向に分割する位置を示します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CSplitterWnd::OnDraw](#ondraw)|スプリッター ウィンドウを描画するためにフレームワークによって呼び出されます。|
|[CSplitterWnd::OnDrawSplitter](#ondrawsplitter)|分割ウィンドウのイメージをレンダリングします。|
|[CSplitterWnd::OnInvertTracker](#oninverttracker)|同じのサイズと形状、フレーム ウィンドウを分割ウィンドウのイメージをレンダリングします。|

## <a name="remarks"></a>Remarks

ペインは、通常、アプリケーション固有のオブジェクトから派生した[CView](../../mfc/reference/cview-class.md)、いずれかのことができますが、 [CWnd](../../mfc/reference/cwnd-class.md)適切な子ウィンドウ ID を持つオブジェクト

A`CSplitterWnd`オブジェクトが親に埋め込まれた通常[CFrameWnd](../../mfc/reference/cframewnd-class.md)または[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)オブジェクト。 作成、`CSplitterWnd`オブジェクト、次の手順を使用して。

1. 埋め込みを`CSplitterWnd`親フレーム内のメンバー変数。

2. 親フレームの[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)メンバー関数。

3. 内でオーバーライドされた`OnCreateClient`を呼び出し、[作成](#create)または[CreateStatic](#createstatic)のメンバー関数`CSplitterWnd`します。

呼び出す、`Create`動的分割ウィンドウを作成します。 動的分割ウィンドウは通常、多数の個別のウィンドウまたはビューは、同じドキュメントのスクロールを作成して使用されます。 フレームワークは、スプリッターの最初のウィンドウを自動的に作成されます。フレームワークは作成、サイズを変更して、分割ウィンドウのコントロールの操作とその他のウィンドウを破棄します。

呼び出すと`Create`ウィンドウが完全に表示するのには小さすぎる場合を決定する行の最小の高さと列幅を指定します。 呼び出した後`Create`、呼び出すことによって、最小値を調整することができます、[ため](#setcolumninfo)と[小さ](#setrowinfo)メンバー関数。

使用しても、`SetColumnInfo`と`SetRowInfo`「最適」列の幅と行の高さが「理想的な」を設定するメンバー関数。 フレームワークには、分割ウィンドウが表示されたら、親フレーム、分割ウィンドウでは、最初に表示されます。 スプリッター ウィンドウのクライアント領域の右下隅を左上隅から作業、その最適な大きさに基づいて列と行のペイン、フレームワークを配置します。

同じクラスの動的分割ウィンドウのすべてのペインがあります。 動的分割ウィンドウをサポートするよく知られたアプリケーションには、Microsoft Word および Microsoft Excel が含まれます。

使用して、`CreateStatic`メンバー関数は静的分割ウィンドウを作成します。 ユーザーは、静的分割ウィンドウ、しない、番号や注文のペインのサイズのみを変更できます。

静的分割ウィンドウを作成するときに具体的にはすべて、静的分割ウィンドウのウィンドウを作成する必要があります。 親フレームの前にすべてのウィンドウを作成するかどうかを確認`OnCreateClient`メンバー関数の戻り値、またはフレームワークは、ウィンドウを正しく表示されません。

`CreateStatic`メンバー関数は自動的に 0 の行の最小の高さと列幅で静的な分割を初期化します。 呼び出した後`Create`、呼び出すことによって、最小値を調整、[ため](#setcolumninfo)と[小さ](#setrowinfo)メンバー関数。 使用しても`SetColumnInfo`と`SetRowInfo`を呼び出した後`CreateStatic`を示すために最適なウィンドウ サイズを必要な。

静的分割ウィンドウの各ペインは、多くの場合、さまざまなクラスに属しています。 静的分割ウィンドウの例については、グラフィックス エディターと Windows ファイル マネージャーを参照してください。

分割ウィンドウは、(スクロール バー ペインが持っている) とは別の特殊なスクロール バーをサポートします。 これらのスクロール バーの子である、`CSplitterWnd`オブジェクトし、ウィンドウと共有されます。

スプリッター ウィンドウを作成するときに、これらの特殊なスクロール バーを作成します。 たとえば、`CSplitterWnd`を持つ 1 つの行、2 つの列と WS_VSCROLL スタイル、2 つのペインで共有される垂直スクロール バーが表示されます。 ユーザーがスクロール バーを移動すると、WM_VSCROLL メッセージは、両方のウィンドウに送信されます。 ペインには、スクロール バーの位置が設定されている場合は、共有のスクロール バーが設定されます。

分割ウィンドウについては、次を参照してください。[テクニカル ノート 29:](../../mfc/tn029-splitter-windows.md)します。

動的分割ウィンドウを作成する方法の詳細についてを参照してください。

- MFC サンプル[Scribble](../../overview/visual-cpp-samples.md)

- MFC サンプル[VIEWEX](../../overview/visual-cpp-samples.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CSplitterWnd`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxext.h

##  <a name="activatenext"></a>  CSplitterWnd::ActivateNext

次のペインまたは前のペインのコマンドを実行するためにフレームワークによって呼び出されます。

```
virtual void ActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>パラメーター

*bPrev*<br/>
どのウィンドウをアクティブ化することを示します。 **TRUE**の前。**FALSE** next でします。

### <a name="remarks"></a>Remarks

このメンバー関数は、高レベルのコマンドで使用される、 [CView](../../mfc/reference/cview-class.md)に委任するクラス、`CSplitterWnd`実装します。

##  <a name="canactivatenext"></a>  CSplitterWnd::CanActivateNext

次のペインまたは前のペイン コマンドが現在可能かどうかを確認するためにフレームワークによって呼び出されます。

```
virtual BOOL CanActivateNext(BOOL bPrev = FALSE);
```

### <a name="parameters"></a>パラメーター

*bPrev*<br/>
どのウィンドウをアクティブ化することを示します。 **TRUE**の前。**FALSE** next でします。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、高レベルのコマンドで使用される、 [CView](../../mfc/reference/cview-class.md)に委任するクラス、`CSplitterWnd`実装します。

##  <a name="create"></a>  CSplitterWnd::Create

動的分割ウィンドウを作成するには、`Create`メンバー関数。

```
virtual BOOL Create(
    CWnd* pParentWnd,
    int nMaxRows,
    int nMaxCols,
    SIZE sizeMin,
    CCreateContext* pContext,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE | WS_HSCROLL | WS_VSCROLL | SPLS_DYNAMIC_SPLIT,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
スプリッター ウィンドウの親フレーム ウィンドウ。

*nMaxRows*<br/>
スプリッター ウィンドウ内の行の最大数。 この値は、2 を超えることはできません。

*nMaxCols*<br/>
スプリッター ウィンドウ内の列の最大数。 この値は、2 を超えることはできません。

*sizeMin*<br/>
ペインが表示される最小サイズを指定します。

*pContext*<br/>
ポインターを[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)構造体。 ほとんどの場合、これはことができます、 *pContext*親フレーム ウィンドウに渡されます。

*dwStyle*<br/>
ウィンドウ スタイルを指定します。

*nID*<br/>
ウィンドウの子ウィンドウ ID。 ID は、分割ウィンドウがもう 1 つの分割ウィンドウ内に入れ子にしない限り、AFX_IDW_PANE_FIRST にすることができます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

埋め込むことができます、 `CSplitterWnd` 、親[CFrameWnd](../../mfc/reference/cframewnd-class.md)または[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)次の手順を実行してオブジェクト。

1. 埋め込みを`CSplitterWnd`親フレーム内のメンバー変数。

1. 親フレームの[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)メンバー関数。

1. 呼び出す、`Create`からのメンバー関数内でオーバーライドされた`OnCreateClient`します。

親フレーム内のスプリッター ウィンドウを作成するときに渡す親フレームの*pContext*スプリッター ウィンドウへのパラメーター。 それ以外の場合、このパラメーターは NULL にすることができます。

動的分割ウィンドウの最初の行の最小の高さと列の幅が定めた、 *sizeMin*パラメーター。 これらの最小値は、ウィンドウが小さすぎて全体を表示するかどうかを判断で変更できます、[小さ](#setrowinfo)と[ため](#setcolumninfo)メンバー関数。

動的分割ウィンドウについての記事では"分割 Windows"を参照してください。[複数のドキュメント タイプ、ビュー、およびフレーム Windows](../../mfc/multiple-document-types-views-and-frame-windows.md)、[テクニカル ノート 29:](../../mfc/tn029-splitter-windows.md)、および`CSplitterWnd`クラスの概要。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#125](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_1.cpp)]

##  <a name="createscrollbarctrl"></a>  CSplitterWnd::CreateScrollBarCtrl

共有のスクロール バー コントロールを作成するためにフレームワークによって呼び出されます。

```
virtual BOOL CreateScrollBarCtrl(
    DWORD dwStyle,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
ウィンドウ スタイルを指定します。

*nID*<br/>
ウィンドウの子ウィンドウ ID。 ID は、分割ウィンドウがもう 1 つの分割ウィンドウ内に入れ子にしない限り、AFX_IDW_PANE_FIRST にすることができます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

オーバーライド`CreateScrollBarCtrl`スクロール バーの横にある余分なコントロールを追加します。 既定の動作では、通常の Windows のスクロール バー コントロールを作成します。

##  <a name="createstatic"></a>  CSplitterWnd::CreateStatic

静的分割ウィンドウを作成するには、`CreateStatic`メンバー関数。

```
virtual BOOL CreateStatic(
    CWnd* pParentWnd,
    int nRows,
    int nCols,
    DWORD dwStyle = WS_CHILD | WS_VISIBLE,
    UINT nID = AFX_IDW_PANE_FIRST);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
スプリッター ウィンドウの親フレーム ウィンドウ。

*nRows*<br/>
行の番号。 この値は 16 を超えることはできません。

*nCols*<br/>
列の番号。 この値は 16 を超えることはできません。

*dwStyle*<br/>
ウィンドウ スタイルを指定します。

*nID*<br/>
ウィンドウの子ウィンドウ ID。 ID は、分割ウィンドウがもう 1 つの分割ウィンドウ内に入れ子にしない限り、AFX_IDW_PANE_FIRST にすることができます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

A`CSplitterWnd`は通常、親に埋め込まれて`CFrameWnd`または[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md)次の手順を実行してオブジェクト。

1. 埋め込みを`CSplitterWnd`親フレーム内のメンバー変数。

1. 親フレームの`OnCreateClient`メンバー関数。

1. 呼び出す、`CreateStatic`からのメンバー関数内でオーバーライドされた[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)します。

静的分割ウィンドウには、さまざまなクラスから多くの場合、ペインの固定の数が含まれています。

静的分割ウィンドウを作成するときに作成する必要がある同時にすべてのペインです。 [CreateView](#createview)メンバー関数は通常、この目的の使用も、他の nonview クラスを作成することができます。

静的分割ウィンドウの最初の行の最小の高さと列の幅は 0 です。 これらの最小値は、調べるには、ウィンドウが小さすぎて全体を表示するときで変更できます、[小さ](#setrowinfo)と[ため](#setcolumninfo)メンバー関数。

に静的分割ウィンドウをスクロール バーを追加する追加 WS_HSCROLL と WS_VSCROLL スタイル*dwStyle*します。

"分割 Windows"、情報の記事を参照してください[複数のドキュメント タイプ、ビュー、およびフレーム Windows](../../mfc/multiple-document-types-views-and-frame-windows.md)、[テクニカル ノート 29:](../../mfc/tn029-splitter-windows.md)、および`CSplitterWnd`の詳細については、静的分割ウィンドウ クラスの概要。

##  <a name="createview"></a>  CSplitterWnd::CreateView

静的分割ウィンドウのペインを作成します。

```
virtual BOOL CreateView(
    int row,
    int col,
    CRuntimeClass* pViewClass,
    SIZE sizeInit,
    CCreateContext* pContext);
```

### <a name="parameters"></a>パラメーター

*行*<br/>
新しいビューを配置するための分割ウィンドウの行を指定します。

*col*<br/>
新しいビューを配置するための分割ウィンドウの列を指定します。

*pViewClass*<br/>
指定します、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)の新しいビュー。

*sizeInit*<br/>
新しいビューの初期サイズを指定します。

*pContext*<br/>
ビューを作成するために使用作成コンテキストへのポインター (通常、 *pContext*オーバーライドされた親のフレームに渡される[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)スプリッター ウィンドウのメンバー関数作成されます)。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

フレームワークは、分割線を表示する前に、静的分割ウィンドウのすべてのウィンドウを作成する必要があります。

フレームワークでは、動的分割ウィンドウのユーザーがウィンドウで、行、または列を分割時に、新しいウィンドウを作成するには、このメンバー関数も呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#4](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_2.cpp)]

##  <a name="csplitterwnd"></a>  CSplitterWnd::CSplitterWnd

構築への呼び出しを`CSplitterWnd`オブジェクト。

```
CSplitterWnd();
```

### <a name="remarks"></a>Remarks

構築、 `CSplitterWnd` 2 つのステップ内のオブジェクト。 最初に、作成するコンス トラクターを呼び出し、`CSplitterWnd`オブジェクトを呼び出して、[作成](#create)メンバー関数は、分割ウィンドウを作成しにアタッチします、`CSplitterWnd`オブジェクト。

##  <a name="deletecolumn"></a>  CSplitterWnd::DeleteColumn

スプリッター ウィンドウから列を削除します。

```
virtual void DeleteColumn(int colDelete);
```

### <a name="parameters"></a>パラメーター

*colDelete*<br/>
削除する列を指定します。

### <a name="remarks"></a>Remarks

このメンバー関数は (つまり、分割ウィンドウでは、SPLS_DYNAMIC_SPLIT スタイルがある) 場合は、動的分割ウィンドウのロジックを実装するためにフレームワークによって呼び出されます。 これはカスタマイズ可能な仮想関数と共に[CreateView](#createview)より高度な動的分割ウィンドウを実装します。

##  <a name="deleterow"></a>  CSplitterWnd::DeleteRow

スプリッター ウィンドウから行を削除します。

```
virtual void DeleteRow(int rowDelete);
```

### <a name="parameters"></a>パラメーター

*rowDelete*<br/>
削除する行を指定します。

### <a name="remarks"></a>Remarks

このメンバー関数は (つまり、分割ウィンドウでは、SPLS_DYNAMIC_SPLIT スタイルがある) 場合は、動的分割ウィンドウのロジックを実装するためにフレームワークによって呼び出されます。 これはカスタマイズ可能な仮想関数と共に[CreateView](#createview)より高度な動的分割ウィンドウを実装します。

##  <a name="deleteview"></a>  CSplitterWnd::DeleteView

スプリッター ウィンドウからビューを削除します。

```
virtual void DeleteView(
    int row,
    int col);
```

### <a name="parameters"></a>パラメーター

*行*<br/>
分割ウィンドウの行ビューを削除する位置を指定します。

*col*<br/>
分割ウィンドウの列のビューを削除する位置を指定します。

### <a name="remarks"></a>Remarks

アクティブなビューが削除されている場合、次のビューがアクティブになります。 既定の実装は、ビューが自動的に前提としています。 削除[PostNcDestroy](../../mfc/reference/cwnd-class.md#postncdestroy)します。

このメンバー関数は (つまり、分割ウィンドウでは、SPLS_DYNAMIC_SPLIT スタイルがある) 場合は、動的分割ウィンドウのロジックを実装するためにフレームワークによって呼び出されます。 これはカスタマイズ可能な仮想関数と共に[CreateView](#createview)より高度な動的分割ウィンドウを実装します。

##  <a name="dokeyboardsplit"></a>  CSplitterWnd::DoKeyboardSplit

キーボード分割コマンドでは、通常は「ウィンドウの分割します。」を実行します。

```
virtual BOOL DoKeyboardSplit();
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、高レベルのコマンドで使用される、 [CView](../../mfc/reference/cview-class.md)に委任するクラス、`CSplitterWnd`実装します。

##  <a name="doscroll"></a>  CSplitterWnd::DoScroll

分割ウィンドウの同期スクロールを実行します。

```
virtual BOOL DoScroll(
    CView* pViewFrom,
    UINT nScrollCode,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>パラメーター

*pViewFrom*<br/>
スクロールのメッセージの発生元となるビューへのポインター。

*nScrollCode*<br/>
スクロール バーのコードをユーザーを示すには、要求のスクロールします。 このパラメーターは 2 つの部分で構成されます。 下位バイト、水平方向にスクロール発生の種類を決定すると、上位バイト、垂直方向にスクロール発生の種類を決定します。

    - SB_BOTTOM まで下にスクロールします。

    - 1 行下 SB_LINEDOWN までスクロールします。

    - 1 行上に SB_LINEUP までスクロールします。

    - 1 つ page down SB_PAGEDOWN までスクロールします。

    - 1 つ page up SB_PAGEUP までスクロールします。

    - ページのトップへ SB_TOP にスクロールします。

*bDoScroll*<br/>
指定したスクロール動作が発生したかどうかを判断します。 場合*bDoScroll*は場合は TRUE (子ウィンドウが存在する場合は、およびスクロールの範囲であれば、分割ウィンドウなど)、指定したスクロール アクションが実行できますその後*bDoScroll*場合は、FALSE (つまり、子ウィンドウ。存在する場合、または分割ビューでスクロールの範囲がない)、スクロールは発生しません。

### <a name="return-value"></a>戻り値

同期スクロールが発生した場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、ビューがスクロール メッセージを受信すると、分割ウィンドウの同期スクロールを実行するためにフレームワークによって呼び出されます。 同期スクロールを許可する前に、ユーザーが操作を要求するオーバーライドです。

##  <a name="doscrollby"></a>  CSplitterWnd::DoScrollBy

指定されたピクセル数で、分割ウィンドウをスクロールします。

```
virtual BOOL DoScrollBy(
    CView* pViewFrom,
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>パラメーター

*pViewFrom*<br/>
スクロールのメッセージの発生元となるビューへのポインター。

*sizeScroll*<br/>
水平および垂直にスクロールするピクセルの数。

*bDoScroll*<br/>
指定したスクロール動作が発生したかどうかを判断します。 場合*bDoScroll*は場合は TRUE (子ウィンドウが存在する場合は、およびスクロールの範囲であれば、分割ウィンドウなど)、指定したスクロール アクションが実行できますその後*bDoScroll*場合は、FALSE (つまり、子ウィンドウ。存在する場合、または分割ビューでスクロールの範囲がない)、スクロールは発生しません。

### <a name="return-value"></a>戻り値

同期スクロールが発生した場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

スクロール メッセージへの応答として、フレームワークによって呼び出されます、同期を実行するにはピクセル単位で示される量で、分割ウィンドウのスクロール*sizeScroll*します。 正の値が右にスクロール ダウンを示します負の値を示すを左へスクロールします。

スクロールを許可する前に、ユーザーが操作を要求するオーバーライドです。

##  <a name="getactivepane"></a>  CSplitterWnd::GetActivePane

フォーカスまたはアクティブなビュー、フレーム内のアクティブなペインを決定します。

```
virtual CWnd* GetActivePane(
    int* pRow = NULL,
    int* pCol = NULL);
```

### <a name="parameters"></a>パラメーター

*pRow*<br/>
ポインター、 **int**アクティブなペインの行番号を取得します。

*pCol*<br/>
ポインター、 **int**アクティブなペインの列番号を取得します。

### <a name="return-value"></a>戻り値

アクティブなペインへのポインター。 アクティブなペインが存在しない場合は NULL です。

### <a name="remarks"></a>Remarks

このメンバー関数は、分割ウィンドウのアクティブなペインを確認するためにフレームワークによって呼び出されます。 アクティブなペインを取得する前に、ユーザーが操作を要求するオーバーライドです。

##  <a name="getcolumncount"></a>  CSplitterWnd::GetColumnCount

現在のウィンドウの列数を返します。

```
int GetColumnCount() const;
```

### <a name="return-value"></a>戻り値

分割ウィンドウの現在の列数を返します。 静的分割ウィンドウで、これもは列の最大数です。

##  <a name="getcolumninfo"></a>  CSplitterWnd::GetColumnInfo

指定した列に情報を返します。

```
void GetColumnInfo(
    int col,
    int& cxCur,
    int& cxMin) const;
```

### <a name="parameters"></a>パラメーター

*col*<br/>
列を指定します。

*cxCur*<br/>
参照、 **int**列の現在の幅に設定されます。

*cxMin*<br/>
参照、 **int**列の現在の最小の幅に設定されます。

##  <a name="getpane"></a>  CSplitterWnd::GetPane

指定した行および列にあるペインを返します。

```
CWnd* GetPane(
    int row,
    int col) const;
```

### <a name="parameters"></a>パラメーター

*行*<br/>
行を指定します。

*col*<br/>
列を指定します。

### <a name="return-value"></a>戻り値

指定した行および列にあるペインを返します。 返されるペインは、通常、 [CView](../../mfc/reference/cview-class.md)-クラスを派生します。

##  <a name="getrowcount"></a>  CSplitterWnd::GetRowCount

現在のウィンドウの行の数を返します。

```
int GetRowCount() const;
```

### <a name="return-value"></a>戻り値

分割ウィンドウの行の現在の数を返します。 静的分割ウィンドウで、これもは行の最大数です。

##  <a name="getrowinfo"></a>  CSplitterWnd::GetRowInfo

指定された行情報を返します。

```
void GetRowInfo(
    int row,
    int& cyCur,
    int& cyMin) const;
```

### <a name="parameters"></a>パラメーター

*行*<br/>
行を指定します。

*cyCur*<br/>
参照**int**ピクセル単位で行の現在の高さに設定されます。

*cyMin*<br/>
参照**int**ピクセル単位で行の現在の最小の高さに設定されます。

### <a name="remarks"></a>Remarks

指定した行に関する情報を取得するには、このメンバー関数を呼び出します。 *CyCur*パラメーターが指定された行の現在の高さ入力と*cyMin*行の高さの最小値が格納されます。

##  <a name="getscrollstyle"></a>  CSplitterWnd::GetScrollStyle

分割ウィンドウで、共有のスクロール バー スタイルを返します。

```
DWORD GetScrollStyle() const;
```

### <a name="return-value"></a>戻り値

成功した場合は 1 つ以上の次の windows スタイルのフラグをします。

    - WS_HSCROLL スプリッターが現在が管理する場合は、水平スクロール バーを共有します。

    - WS_VSCROLL スプリッターが現在が管理する場合は、垂直スクロール バーを共有します。

0 の場合、分割ウィンドウは、共有のスクロール バーを現在管理しません。

##  <a name="idfromrowcol"></a>  CSplitterWnd::IdFromRowCol

指定した行および列にあるウィンドウのウィンドウ ID、子を取得します。

```
int IdFromRowCol(
    int row,
    int col) const;
```

### <a name="parameters"></a>パラメーター

*行*<br/>
分割ウィンドウの行を指定します。

*col*<br/>
分割ウィンドウの列を指定します。

### <a name="return-value"></a>戻り値

ウィンドウの子ウィンドウ ID。

### <a name="remarks"></a>Remarks

このメンバー関数は、ビューでないペインを作成するため使用され、ウィンドウが存在する前に呼び出すことができます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#5](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_3.cpp)]

##  <a name="ischildpane"></a>  CSplitterWnd::IsChildPane

決定かどうか*我が物*は現在、このスプリッター ウィンドウの子ウィンドウ。

```
BOOL IsChildPane(
    CWnd* pWnd,
    int* pRow,
    int* pCol);
```

### <a name="parameters"></a>パラメーター

*我が物*<br/>
ポインターを[CWnd](../../mfc/reference/cwnd-class.md)をテストするオブジェクト。

*pRow*<br/>
ポインター、 **int**行番号を格納します。

*pCol*<br/>
ポインター、 **int**列番号を格納します。

### <a name="return-value"></a>戻り値

ゼロ以外の場合、*我が物*このスプリッター ウィンドウの子ウィンドウは、現在と*pRow*と*pCol*分割ウィンドウのウィンドウの位置が入ります。 場合*我が物*が子ウィンドウ、分割ウィンドウの 0 が返されます。

### <a name="remarks"></a>Remarks

6.0 より前のバージョンを Visual C では、この関数として定義されました

`BOOL IsChildPane(CWnd* pWnd, int& row, int& col);`

このバージョンは廃止されておりは使用できません。

##  <a name="istracking"></a>  CSplitterWnd::IsTracking

ウィンドウのスプリッター バーは現在移動中かを判断するには、このメンバー関数を呼び出します。

```
BOOL IsTracking();
```

### <a name="return-value"></a>戻り値

以外の場合は、分割操作が進行中です。それ以外の場合 0 を返します。

##  <a name="ondrawsplitter"></a>  CSplitterWnd::OnDrawSplitter

分割ウィンドウのイメージをレンダリングします。

```
virtual void OnDrawSplitter(
    CDC* pDC,
    ESplitType nType,
    const CRect& rect);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
描画するためのデバイス コンテキストへのポインター。 場合*pDC*が null の場合、 [CWnd::RedrawWindow](../../mfc/reference/cwnd-class.md#redrawwindow)と呼びますフレームワークおよびありません分割によってウィンドウが描画されます。

*nType*<br/>
値、`enum ESplitType`次のいずれかを指定することができます。

    - `splitBox` 分割ドラッグ ボックス。

    - `splitBar` 2 つの分割ウィンドウ間に表示されるバー。

    - `splitIntersection` 分割ウィンドウの積集合。 Windows 95/98 で実行されているときに、この要素は呼び出されません。

    - `splitBorder` 分割ウィンドウの境界線。

*rect*<br/>
参照を[CRect](../../atl-mfc-shared/reference/crect-class.md)分割ウィンドウの形状とサイズを指定するオブジェクト。

### <a name="remarks"></a>Remarks

このメンバー関数は、描画し、正確な分割ウィンドウの特性を指定するためにフレームワークによって呼び出されます。 オーバーライド`OnDrawSplitter`スプリッター ウィンドウのさまざまなグラフィック要素の画像の高度にカスタマイズします。 既定の画像は、分割バーの交点のブレンドを Windows または Microsoft Windows 95/98 では、Microsoft は、スプリッターに似ています。

動的分割ウィンドウについての記事では"分割 Windows"を参照してください。[複数のドキュメント タイプ、ビュー、およびフレーム Windows](../../mfc/multiple-document-types-views-and-frame-windows.md)、[テクニカル ノート 29:](../../mfc/tn029-splitter-windows.md)、および`CSplitterWnd`クラスの概要。

##  <a name="oninverttracker"></a>  CSplitterWnd::OnInvertTracker

同じのサイズと形状、フレーム ウィンドウを分割ウィンドウのイメージをレンダリングします。

```
virtual void OnInvertTracker(const CRect& rect);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
参照を`CRect`追跡四角形を指定するオブジェクト。

### <a name="remarks"></a>Remarks

このメンバー関数は、分割ウィンドウのサイズ変更時に、フレームワークによって呼び出されます。 オーバーライド`OnInvertTracker`スプリッター ウィンドウの画像の高度にカスタマイズします。 既定の画像は、分割バーの交点のブレンドを Windows または Microsoft Windows 95/98 では、Microsoft は、スプリッターに似ています。

動的分割ウィンドウについての記事では"分割 Windows"を参照してください。[複数のドキュメント タイプ、ビュー、およびフレーム Windows](../../mfc/multiple-document-types-views-and-frame-windows.md)、[テクニカル ノート 29:](../../mfc/tn029-splitter-windows.md)、および`CSplitterWnd`クラスの概要。

##  <a name="recalclayout"></a>  CSplitterWnd::RecalcLayout

スプリッター ウィンドウを表示し、行または列のサイズを調整した後の呼び出しです。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Remarks

行および列のサイズを調整した後、正しくスプリッター ウィンドウを再表示するのには、このメンバー関数を呼び出す、[小さ](#setrowinfo)と[ため](#setcolumninfo)メンバー関数。 スプリッター ウィンドウが表示される前に、作成プロセスの一部として行と列のサイズを変更する場合、このメンバー関数を呼び出す必要はありません。

フレームワークは、ユーザーがスプリッター ウィンドウのサイズを変更または移動されるたびに、このメンバー関数を呼び出します。

### <a name="example"></a>例

  例をご覧ください[CSplitterWnd::SetColumnInfo](#setcolumninfo)します。

##  <a name="setactivepane"></a>  CSplitterWnd::SetActivePane

フレームのアクティブ状態であるペインを設定します。

```
virtual void SetActivePane(
    int row,
    int col,
    CWnd* pWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*行*<br/>
場合*我が物*が NULL でアクティブになるウィンドウで、行を指定します。

*col*<br/>
場合*我が物*が NULL でアクティブになるウィンドウで列を指定します。

*我が物*<br/>
`CWnd` オブジェクトへのポインター。 によって指定された NULL の場合、ウィンドウ*行*と*col*アクティブに設定されます。 NULL 以外の場合は、アクティブに設定されているウィンドウを指定します。

### <a name="remarks"></a>Remarks

このメンバー関数は、フレーム ウィンドウ内のペインにフォーカスが変更されると、ペインをアクティブとして設定するためにフレームワークによって呼び出されます。 明示的に呼び出すことができます`SetActivePane`を指定されたビューにフォーカスを変更します。

行と列のいずれかを提供することでウィンドウを指定**または**により*我が物*します。

##  <a name="setcolumninfo"></a>  CSplitterWnd::SetColumnInfo

指定した列の情報を設定する呼び出し。

```
void SetColumnInfo(
    int col,
    int cxIdeal,
    int cxMin);
```

### <a name="parameters"></a>パラメーター

*col*<br/>
分割ウィンドウの列を指定します。

*cxIdeal*<br/>
分割ウィンドウの列の最適の幅をピクセル単位で指定します。

*cxMin*<br/>
スプリッター ウィンドウの列の最小幅をピクセル単位で指定します。

### <a name="remarks"></a>Remarks

新しい最小の幅と列の適切な幅を設定するには、このメンバー関数を呼び出します。 列を完全に表示するのには小さすぎるするときに、列の最小値を決定します。

フレームワークは、分割ウィンドウを表示するときは、分割ウィンドウのクライアント領域の右下隅を左上隅から作業、その最適な大きさに基づいて列と行のペインをレイアウトします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#6](../../mfc/reference/codesnippet/cpp/csplitterwnd-class_4.cpp)]

##  <a name="setrowinfo"></a>  CSplitterWnd::SetRowInfo

指定した行の情報を設定する呼び出し。

```
void SetRowInfo(
    int row,
    int cyIdeal,
    int cyMin);
```

### <a name="parameters"></a>パラメーター

*行*<br/>
分割ウィンドウの行を指定します。

*cyIdeal*<br/>
最適な分割ウィンドウの行の高さをピクセル単位で指定します。

*cyMin*<br/>
スプリッター ウィンドウの行の最小の高さをピクセル単位で指定します。

### <a name="remarks"></a>Remarks

新しい高さの最小値と行の最適な高さを設定するには、このメンバー関数を呼び出します。 行が完全に表示するのには小さすぎるにするときに、行の最小値を決定します。

フレームワークは、分割ウィンドウを表示するときは、分割ウィンドウのクライアント領域の右下隅を左上隅から作業、その最適な大きさに基づいて列と行のペインをレイアウトします。

##  <a name="setscrollstyle"></a>  CSplitterWnd::SetScrollStyle

スクロール バーのサポートを共有の分割ウィンドウで、新しいスクロール スタイルを指定します。

```
void SetScrollStyle(DWORD dwStyle);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
スプリッター ウィンドウの新しいスクロール スタイルでは、スクロール バーのサポートは、次の値のいずれかを指定することができますを共有しました。

- WS_HSCROLL 作成/表示の共有の水平スクロール バー。

- 共有の垂直スクロール バーを作成/表示する言えることです。

### <a name="remarks"></a>Remarks

スクロール バーを作成した後は破棄されない場合でも`SetScrollStyle`せずそのスタイル; が呼び出されて代わりに、スクロール バーが非表示になります。 これにより、隠れている場合でも、その状態を保持するスクロール バーができます。 呼び出した後`SetScrollStyle`を呼び出す必要がある[RecalcLayout](#recalclayout)のすべての変更を有効にします。

##  <a name="splitcolumn"></a>  CSplitterWnd::SplitColumn

フレーム ウィンドウが垂直方向に分割される場所を示します。

```
virtual BOOL SplitColumn(int cxBefore);
```

### <a name="parameters"></a>パラメーター

*cxBefore*<br/>
ピクセル単位で分割が発生する前に位置します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、垂直方向の分割ウィンドウの作成時に呼び出されます。 `SplitColumn` 分割が発生する既定の場所を示します。

`SplitColumn` (つまり、分割ウィンドウでは、SPLS_DYNAMIC_SPLIT スタイルがある) 場合は、動的分割ウィンドウのロジックを実装するためにフレームワークによって呼び出されます。 これはカスタマイズ可能な仮想関数と共に[CreateView](#createview)より高度な動的分割ウィンドウを実装します。

##  <a name="splitrow"></a>  CSplitterWnd::SplitRow

フレーム ウィンドウを水平方向に分割する位置を示します。

```
virtual BOOL SplitRow(int cyBefore);
```

### <a name="parameters"></a>パラメーター

*cyBefore*<br/>
ピクセル単位で分割が発生する前に位置します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、水平方向の分割ウィンドウの作成時に呼び出されます。 `SplitRow` 分割が発生する既定の場所を示します。

`SplitRow` (つまり、分割ウィンドウでは、SPLS_DYNAMIC_SPLIT スタイルがある) 場合は、動的分割ウィンドウのロジックを実装するためにフレームワークによって呼び出されます。 これはカスタマイズ可能な仮想関数と共に[CreateView](#createview)より高度な動的分割ウィンドウを実装します。

##  <a name="ondraw"></a>  CSplitterWnd::OnDraw

スプリッター ウィンドウを描画するためにフレームワークによって呼び出されます。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
デバイス コンテキストへのポインター。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[MFC サンプル VIEWEX](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CView クラス](../../mfc/reference/cview-class.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)
