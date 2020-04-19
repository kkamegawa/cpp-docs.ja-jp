---
title: CView クラス
ms.date: 11/04/2016
f1_keywords:
- CView
- AFXWIN/CView
- AFXWIN/CView::CView
- AFXWIN/CView::DoPreparePrinting
- AFXWIN/CView::GetDocument
- AFXWIN/CView::IsSelected
- AFXWIN/CView::OnDragEnter
- AFXWIN/CView::OnDragLeave
- AFXWIN/CView::OnDragOver
- AFXWIN/CView::OnDragScroll
- AFXWIN/CView::OnDrop
- AFXWIN/CView::OnDropEx
- AFXWIN/CView::OnInitialUpdate
- AFXWIN/CView::OnPrepareDC
- AFXWIN/CView::OnScroll
- AFXWIN/CView::OnScrollBy
- AFXWIN/CView::OnActivateFrame
- AFXWIN/CView::OnActivateView
- AFXWIN/CView::OnBeginPrinting
- AFXWIN/CView::OnDraw
- AFXWIN/CView::OnEndPrinting
- AFXWIN/CView::OnEndPrintPreview
- AFXWIN/CView::OnPreparePrinting
- AFXWIN/CView::OnPrint
- AFXWIN/CView::OnUpdate
helpviewer_keywords:
- CView [MFC], CView
- CView [MFC], DoPreparePrinting
- CView [MFC], GetDocument
- CView [MFC], IsSelected
- CView [MFC], OnDragEnter
- CView [MFC], OnDragLeave
- CView [MFC], OnDragOver
- CView [MFC], OnDragScroll
- CView [MFC], OnDrop
- CView [MFC], OnDropEx
- CView [MFC], OnInitialUpdate
- CView [MFC], OnPrepareDC
- CView [MFC], OnScroll
- CView [MFC], OnScrollBy
- CView [MFC], OnActivateFrame
- CView [MFC], OnActivateView
- CView [MFC], OnBeginPrinting
- CView [MFC], OnDraw
- CView [MFC], OnEndPrinting
- CView [MFC], OnEndPrintPreview
- CView [MFC], OnPreparePrinting
- CView [MFC], OnPrint
- CView [MFC], OnUpdate
ms.assetid: 9cff3c56-7564-416b-b9a4-71a9254ed755
ms.openlocfilehash: f6be846e80209ce94c84222d61c37a7964baad03
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127510"
---
# <a name="cview-class"></a>CView クラス

ユーザーが定義するビュークラスの基本機能が用意されています。

## <a name="syntax"></a>構文

```
class AFX_NOVTABLE CView : public CWnd
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|Name|説明|
|----------|-----------------|
|[CView:: CView](#cview)|`CView` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[CView::D oPreparePrinting](#doprepareprinting)|[印刷] ダイアログボックスを表示し、プリンターデバイスコンテキストを作成します。`OnPreparePrinting` メンバー関数をオーバーライドするときに、を呼び出します。|
|[CView:: GetDocument](#getdocument)|ビューに関連付けられているドキュメントを返します。|
|[CView:: IsSelected](#isselected)|ドキュメント項目が選択されているかどうかをテストします。 OLE のサポートに必要です。|
|[CView:: OnDragEnter](#ondragenter)|ビューのドラッグアンドドロップ領域に項目が最初にドラッグされたときに呼び出されます。|
|[CView:: OnDragLeave](#ondragleave)|ドラッグした項目がビューのドラッグアンドドロップ領域から離れると呼び出されます。|
|[CView:: OnDragOver](#ondragover)|ビューのドラッグアンドドロップ領域上に項目がドラッグされると呼び出されます。|
|[CView:: OnDragScroll](#ondragscroll)|カーソルがウィンドウのスクロール領域にドラッグされているかどうかを判断するために呼び出されます。|
|[CView:: OnDrop](#ondrop)|ビューのドラッグアンドドロップ領域に項目がドロップされたときに呼び出されます。既定のハンドラー。|
|[CView:: OnDropEx](#ondropex)|ビューのドラッグアンドドロップ領域に項目がドロップされたときに呼び出されます。プライマリハンドラー。|
|[CView:: OnInitialUpdate](#oninitialupdate)|ビューがドキュメントに最初にアタッチされた後に呼び出されます。|
|[CView:: OnPrepareDC](#onpreparedc)|`OnDraw` メンバー関数が画面に表示される前に呼び出されるか、または印刷または印刷プレビューのために `OnPrint` メンバー関数が呼び出される前に呼び出されます。|
|[CView:: OnScroll](#onscroll)|OLE 項目がビューの境界を越えてドラッグされると呼び出されます。|
|[CView:: OnScrollBy](#onscrollby)|アクティブなインプレース OLE 項目を含むビューがスクロールされたときに呼び出されます。|

### <a name="protected-methods"></a>プロテクト メソッド

|Name|説明|
|----------|-----------------|
|[CView:: Onアクティブフレーム](#onactivateframe)|ビューを含むフレームウィンドウがアクティブ化または非アクティブ化されたときに呼び出されます。|
|[CView:: Onアクティブビュー](#onactivateview)|ビューがアクティブになったときに呼び出されます。|
|[CView:: OnBeginPrinting](#onbeginprinting)|印刷ジョブの開始時に呼び出されます。をオーバーライドして、グラフィックスデバイスインターフェイス (GDI) リソースを割り当てます。|
|[CView:: OnDraw](#ondraw)|画面表示、印刷、または印刷プレビューのためにドキュメントのイメージをレンダリングするために呼び出されます。 実装が必要です。|
|[CView:: OnEndPrinting](#onendprinting)|印刷ジョブが終了したときに呼び出されます。GDI リソースの割り当てを解除するには、をオーバーライドします。|
|[CView:: OnEndPrintPreview](#onendprintpreview)|プレビューモードが終了したときに呼び出されます。|
|[CView:: OnPreparePrinting](#onprepareprinting)|ドキュメントが印刷またはプレビューされる前に呼び出されます。オーバーライドして [印刷] ダイアログボックスを初期化します。|
|[CView:: OnPrint](#onprint)|ドキュメントのページを印刷またはプレビューするために呼び出されます。|
|[CView:: OnUpdate](#onupdate)|ドキュメントが変更されたことをビューに通知するために呼び出されます。|

## <a name="remarks"></a>解説

ビューはドキュメントに添付され、ドキュメントとユーザーの間の仲介役として機能します。このビューでは、ドキュメントのイメージが画面またはプリンター上にレンダリングされ、ユーザーの入力がドキュメントに対する操作として解釈されます。

ビューは、フレームウィンドウの子です。 分割ウィンドウの場合と同じように、複数のビューでフレームウィンドウを共有できます。 ビュークラス、フレームウィンドウクラス、およびドキュメントクラス間のリレーションシップは、`CDocTemplate` オブジェクトによって確立されます。 ユーザーが新しいウィンドウを開いたり、既存のウィンドウを分割したりすると、フレームワークによって新しいビューが構築され、ドキュメントにアタッチされます。

1つのビューにアタッチできるドキュメントは1つだけですが、ドキュメントには複数のビューを一度にアタッチすることができます。たとえば、ドキュメントが分割ウィンドウまたはマルチドキュメントインターフェイス (MDI) アプリケーションの複数の子ウィンドウに表示されている場合などです。 アプリケーションでは、特定の種類のドキュメントに対してさまざまな種類のビューをサポートできます。たとえば、ワードプロセッシングプログラムでは、ドキュメントの完全なテキストビューと、セクションの見出しのみを表示するアウトラインビューの両方が提供される場合があります。 分割ウィンドウを使用する場合は、これらの異なる種類のビューを個別のフレームウィンドウまたは1つのフレームウィンドウの別のペインに配置できます。

ビューでは、キーボード入力、マウス入力、ドラッグアンドドロップによる入力、メニュー、ツールバー、またはスクロールバーのコマンドなど、さまざまな種類の入力を処理することができます。 ビューは、フレームウィンドウによって転送されたコマンドを受け取ります。 ビューが特定のコマンドを処理しない場合は、関連付けられているドキュメントにコマンドを転送します。 すべてのコマンドターゲットと同様、ビューはメッセージマップを介してメッセージを処理します。

ビューはドキュメントのデータを表示および変更する必要がありますが、保存するためのものではありません。 ドキュメントには、そのデータに関する必要な詳細情報が表示されます。 ビューがドキュメントのデータメンバーに直接アクセスできるようにすることも、を呼び出すビュークラスのドキュメントクラスにメンバー関数を指定することもできます。

ドキュメントのデータが変更されると、その変更を担当するビューは通常、ドキュメントの[CDocument:: UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)関数を呼び出します。これにより、それぞれの `OnUpdate` メンバー関数を呼び出すことによって、他のすべてのビューに通知します。 `OnUpdate` の既定の実装では、ビューのクライアント領域全体が無効になります。 これをオーバーライドして、ドキュメントの変更部分にマップされているクライアント領域の領域のみを無効にすることができます。

`CView`を使用するには、そこからクラスを派生させ、`OnDraw` メンバー関数を実装して画面表示を実行します。 `OnDraw` を使用して、印刷と印刷プレビューを実行することもできます。 フレームワークは、ドキュメントを印刷およびプレビューするための print ループを処理します。

ビューでは、 [cwnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)および[Cwnd:: onvscroll](../../mfc/reference/cwnd-class.md#onvscroll)メンバー関数を使用して、スクロールバーメッセージを処理します。 これらの関数では、スクロールバーのメッセージ処理を実装できます。また、`CView` 派生クラス[CScrollView](../../mfc/reference/cscrollview-class.md)を使用して、スクロールを処理することもできます。

Microsoft Foundation Class ライブラリには、`CScrollView`だけでなく、`CView`から派生した9つの他のクラスが用意されています。

- [CCtrlView](../../mfc/reference/cctrlview-class.md)は、ツリー、リスト、およびリッチエディットコントロールでドキュメントビューアーキテクチャを使用できるようにするビューです。

- [CDaoRecordView](../../mfc/reference/cdaorecordview-class.md)。ダイアログボックスコントロールにデータベースレコードを表示するビューです。

- 単一行テキストエディターを提供する[CEditView](../../mfc/reference/ceditview-class.md)ビュー。 `CEditView` オブジェクトは、ダイアログボックス内のコントロールとして使用することも、ドキュメント上のビューとして使用することもできます。

- [CFormView](../../mfc/reference/cformview-class.md): ダイアログボックスコントロールを含み、ダイアログテンプレートリソースに基づく、スクロール可能なビューです。

- [CListView](../../mfc/reference/clistview-class.md)。リストコントロールでドキュメントビューアーキテクチャを使用できるようにするビューです。

- [CRecordView](../../mfc/reference/crecordview-class.md): ダイアログボックスコントロールにデータベースレコードを表示するビューです。

- [CRichEditView](../../mfc/reference/cricheditview-class.md)は、リッチエディットコントロールによるドキュメントビューアーキテクチャの使用を可能にするビューです。

- [CScrollView](../../mfc/reference/cscrollview-class.md)は、スクロールサポートを自動的に提供するビューです。

- [CTreeView](../../mfc/reference/ctreeview-class.md)は、ツリーコントロールでドキュメントビューアーキテクチャを使用できるようにするビューです。

`CView` クラスには、`CPreviewView`という名前の派生実装クラスもあります。これは、印刷プレビューを実行するためにフレームワークによって使用されます。 このクラスは、印刷プレビューウィンドウに固有の機能をサポートしています。たとえば、ツールバー、単一ページまたは2ページのプレビュー、ズーム、つまり、プレビューされているイメージを拡大します。 印刷プレビュー用の独自のインターフェイスを実装する場合 (印刷プレビューモードでの編集をサポートする場合など) は、`CPreviewView`のメンバー関数を呼び出すこともオーバーライドする必要もありません。 `CView`の使用方法の詳細については、「[ドキュメント/ビューのアーキテクチャ](../../mfc/document-view-architecture.md)と[印刷](../../mfc/printing.md)」を参照してください。 また、印刷プレビューのカスタマイズの詳細については、「[テクニカルノート 30](../../mfc/tn030-customizing-printing-and-print-preview.md) 」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[から派生しているのではない](../../mfc/reference/cwnd-class.md)

`CView`

## <a name="requirements"></a>［要件］

**ヘッダー:** afxwin.h

##  <a name="cview"></a>CView:: CView

`CView` オブジェクトを構築します。

```
CView();
```

### <a name="remarks"></a>解説

フレームワークは、新しいフレームウィンドウが作成されたとき、またはウィンドウが分割されたときにコンストラクターを呼び出します。 [OnInitialUpdate](#oninitialupdate)メンバー関数をオーバーライドして、ドキュメントが添付された後にビューを初期化します。

##  <a name="doprepareprinting"></a>CView::D oPreparePrinting

[OnPreparePrinting](#onprepareprinting)のオーバーライドからこの関数を呼び出して、[印刷] ダイアログボックスを呼び出し、プリンターデバイスコンテキストを作成します。

```
BOOL DoPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>パラメーター

*pInfo*<br/>
現在の印刷ジョブを表す [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 構造体を指し示します。

### <a name="return-value"></a>戻り値

印刷または印刷プレビューを開始できる場合は0以外の。操作が取り消された場合は0。

### <a name="remarks"></a>解説

この関数の動作は、 *pInfo*パラメーターの `m_bPreview` メンバーによって指定された印刷または印刷プレビューに対して呼び出されているかどうかによって異なります。 ファイルが印刷されている場合、この関数は、 *pInfo*が指す[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)構造体の値を使用して、[印刷] ダイアログボックスを呼び出します。ユーザーがダイアログボックスを閉じた後、この関数は、ダイアログボックスで指定されたユーザー設定に基づいてプリンターデバイスコンテキストを作成し、 *pInfo*パラメーターを使用してこのデバイスコンテキストを返します。 このデバイスコンテキストは、ドキュメントを印刷するために使用されます。

ファイルがプレビューされている場合、この関数は現在のプリンター設定を使用してプリンターデバイスコンテキストを作成します。このデバイスコンテキストは、プレビュー期間中にプリンターをシミュレートするために使用されます。

##  <a name="getdocument"></a>CView:: GetDocument

ビューのドキュメントへのポインターを取得するには、この関数を呼び出します。

```
CDocument* GetDocument() const;
```

### <a name="return-value"></a>戻り値

ビューに関連付けられている[CDocument](../../mfc/reference/cdocument-class.md)オブジェクトへのポインター。 ビューがドキュメントにアタッチされていない場合は NULL です。

### <a name="remarks"></a>解説

これにより、ドキュメントのメンバー関数を呼び出すことができます。

##  <a name="isselected"></a>CView:: IsSelected

指定されたドキュメント項目が選択されているかどうかを確認するために、フレームワークによって呼び出されます。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>パラメーター

*pDocItem*<br/>
テスト対象のドキュメント項目をポイントします。

### <a name="return-value"></a>戻り値

指定されたドキュメント項目が選択されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

この関数の既定の実装では、FALSE が返されます。 [CDocItem](../../mfc/reference/cdocitem-class.md)オブジェクトを使用して選択を実装する場合は、この関数をオーバーライドします。 ビューに OLE 項目が含まれている場合は、この関数をオーバーライドする必要があります。

##  <a name="onactivateframe"></a>CView:: Onアクティブフレーム

ビューを含むフレームウィンドウがアクティブ化または非アクティブ化されたときにフレームワークによって呼び出されます。

```
virtual void OnActivateFrame(
    UINT nState,
    CFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>パラメーター

*nState*<br/>
フレームウィンドウをアクティブまたは非アクティブにするかどうかを指定します。 次のいずれかの値を指定できます。

- フレームウィンドウが非アクティブ化されて WA_INACTIVE。

- マウスクリック以外の何らかの方法 (たとえば、キーボードインターフェイスを使用してウィンドウを選択するなど) によってフレームウィンドウがアクティブ化されている WA_ACTIVE ます。

- フレームウィンドウがマウスクリックによってアクティブ化されている WA_CLICKACTIVE

*pFrameWnd*<br/>
アクティブにするフレームウィンドウへのポインター。

### <a name="remarks"></a>解説

ビューに関連付けられているフレームウィンドウがアクティブ化または非アクティブ化されたときに特殊な処理を実行する場合は、このメンバー関数をオーバーライドします。 たとえば、ctrl を使用すると、フォーカスがあるコントロールを保存および復元するときに、このオーバーライド[が実行さ](../../mfc/reference/cformview-class.md)れます。

##  <a name="onactivateview"></a>CView:: Onアクティブビュー

ビューがアクティブ化または非アクティブ化されたときにフレームワークによって呼び出されます。

```
virtual void OnActivateView(
    BOOL bActivate,
    CView* pActivateView,
    CView* pDeactiveView);
```

### <a name="parameters"></a>パラメーター

*bActivate*<br/>
ビューがアクティブ化または非アクティブ化されているかどうかを示します。

*Pアクティブビュー*<br/>
アクティブ化されているビューオブジェクトを指します。

*pDeactiveView*<br/>
非アクティブ化されているビューオブジェクトを指します。

### <a name="remarks"></a>解説

この関数の既定の実装では、アクティブになっているビューにフォーカスが設定されます。 ビューがアクティブ化または非アクティブ化されたときに特別な処理を実行する場合は、この関数をオーバーライドします。 たとえば、アクティブなビューを非アクティブなビューと区別する特別な視覚的な手掛かりを提供する場合は、 *Bactivate*パラメーターを調べ、それに応じてビューの外観を更新します。

アプリケーションのメインフレームウィンドウがアクティブビューで変更されずにアクティブになっている場合 (たとえば、フォーカスがアプリケーション内で別のアプリケーションから別のアプリケーションに移動されている場合や、MDI 子ウィンドウ間を切り替える場合など) は、 *Pactivateview*パラメーターと*pdeactiveview*パラメーターが同じビューを指します。 これにより、必要に応じてビューでパレットを再認識できます。

Cframewnd:: [getactiveview](../../mfc/reference/cframewnd-class.md#getactiveview)が返されるのとは異なるビューで[Cframewnd:: setactiveview](../../mfc/reference/cframewnd-class.md#setactiveview)が呼び出された場合、これらのパラメーターは異なります。 これは、ほとんどの場合、分割ウィンドウで発生します。

##  <a name="onbeginprinting"></a>CView:: OnBeginPrinting

`OnPreparePrinting` が呼び出された後で、印刷または印刷プレビュー ジョブの開始時にフレームワークによって呼び出されます。

```
virtual void OnBeginPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
プリンター デバイス コンテキストを指し示します。

*pInfo*<br/>
現在の印刷ジョブを表す [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 構造体を指し示します。

### <a name="remarks"></a>解説

この関数の既定の実装は、何も行いません。 この関数をオーバーライドして、特に印刷のために必要な GDI リソース (ペン、フォントなど) を割り当てます。 [OnPrint](#onprint) メンバー関数内から、デバイス コンテキストの GDI オブジェクトを、それらを使用する各ページ用に選択します。 同じビュー オブジェクトを使用して画面の表示と印刷の両方を実行している場合は、各表示に必要な GDI リソースに別個の変数を使用します。これにより、印刷時に画面を更新することができます。

さらに、この関数を使用して、プリンター デバイス コンテキストのプロパティに依存する初期化を実行することもできます。 たとえば、ドキュメントを印刷するために必要なページ数は、印刷ダイアログ ボックスでユーザーが指定した設定 (たとえば、ページの長さ) によって異なる可能性があります。 そのような場合は、通常行うように [OnPreparePrinting](#onprepareprinting) メンバー関数にドキュメントの長さを指定することはできません。ダイアログ ボックスの設定に基づいてプリンター デバイス コンテキストが作成されるまで待機する必要があります。 [OnBeginPrinting](#onbeginprinting) は、プリンター デバイス コンテキストを表す [CDC](../../mfc/reference/cdc-class.md) オブジェクトにアクセスできる初めてのオーバーライド可能な関数です。したがって、この関数からドキュメントの長さを設定することができます。 この時点でドキュメントの長さを指定しない場合、印刷プレビュー時にスクロール バーは表示されません。

##  <a name="ondragenter"></a>CView:: OnDragEnter

ドロップ先ウィンドウのスクロールしない領域にマウスが最初に入ったときにフレームワークによって呼び出されます。

```
virtual DROPEFFECT OnDragEnter(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

*pDataObject*<br/>
ビューのドロップ領域にドラッグされている[COleDataObject](../../mfc/reference/coledataobject-class.md)をポイントします。

*dwKeyState*<br/>
修飾子キーの状態を格納します。 これは、MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON、および MK_RBUTTON の任意の数を組み合わせたものです。

*視点*<br/>
ビューのクライアント領域を基準とする、現在のマウスの位置。

### <a name="return-value"></a>戻り値

DROPEFFECT 列挙型の値。ユーザーがこの位置でオブジェクトをドロップした場合に発生するドロップの種類を示します。 通常、ドロップの種類は、 *Dwkeystate*によって示される現在のキーの状態に依存します。 キーの状態と DROPEFFECT の値の標準マッピングは次のとおりです。

- このウィンドウでは、データオブジェクトを削除することはできません DROPEFFECT_NONE。

- MK_CONTROL &#124; MK_SHIFT を DROPEFFECT_LINK して、オブジェクトとそのサーバーとの間にリンケージを作成します。

- MK_CONTROL の DROPEFFECT_COPY は、削除されたオブジェクトのコピーを作成します。

- MK_ALT の DROPEFFECT_MOVE は、削除されたオブジェクトのコピーを作成し、元のオブジェクトを削除します。 これは、通常、ビューがこのデータオブジェクトを受け入れることができる場合の既定のドロップ効果です。

詳細については、MFC の高度な概念のサンプル[OCLIENT](../../overview/visual-cpp-samples.md)を参照してください。

### <a name="remarks"></a>解説

既定の実装では、何も行わずに DROPEFFECT_NONE を返します。

この関数をオーバーライドして、 [OnDragOver](#ondragover)メンバー関数の今後の呼び出しに備えるようにします。 この時点でデータオブジェクトから必要なデータを取得して、後で `OnDragOver` メンバー関数で使用できるようにする必要があります。 この時点でビューを更新して、ユーザーに視覚的なフィードバックを提供する必要もあります。 詳細については、「 [OLE ドラッグアンドドロップ: drop target を実装する](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)」を参照してください。

##  <a name="ondragleave"></a>CView:: OnDragLeave

マウスがそのウィンドウの有効なドロップ領域の外に移動したときに、ドラッグ操作中にフレームワークによって呼び出されます。

```
virtual void OnDragLeave();
```

### <a name="remarks"></a>解説

現在のビューが[Ondragenter](#ondragenter)または[OnDragOver](#ondragover)の呼び出し中に実行されるアクションをクリーンアップする必要がある場合 (オブジェクトをドラッグアンドドロップしたときにビジュアルユーザーフィードバックを削除する場合など) は、この関数をオーバーライドします。

##  <a name="ondragover"></a>CView:: OnDragOver

マウスをドロップ先のウィンドウ上に移動したときに、ドラッグ操作中にフレームワークによって呼び出されます。

```
virtual DROPEFFECT OnDragOver(
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

*pDataObject*<br/>
ドロップ先の上にドラッグされている[COleDataObject](../../mfc/reference/coledataobject-class.md)をポイントします。

*dwKeyState*<br/>
修飾子キーの状態を格納します。 これは、MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON、および MK_RBUTTON の任意の数を組み合わせたものです。

*視点*<br/>
ビュークライアント領域を基準とした、現在のマウス位置。

### <a name="return-value"></a>戻り値

DROPEFFECT 列挙型の値。ユーザーがこの位置でオブジェクトをドロップした場合に発生するドロップの種類を示します。 Drop の種類は、通常、 *Dwkeystate*によって示される現在のキーの状態によって異なります。 キーの状態と DROPEFFECT の値の標準マッピングは次のとおりです。

- このウィンドウでは、データオブジェクトを削除することはできません DROPEFFECT_NONE。

- MK_CONTROL &#124; MK_SHIFT を DROPEFFECT_LINK して、オブジェクトとそのサーバーとの間にリンケージを作成します。

- MK_CONTROL の DROPEFFECT_COPY は、削除されたオブジェクトのコピーを作成します。

- MK_ALT の DROPEFFECT_MOVE は、削除されたオブジェクトのコピーを作成し、元のオブジェクトを削除します。 これは、通常、ビューがデータオブジェクトを受け取ることができる場合の既定のドロップ効果です。

詳細については、MFC の高度な概念のサンプル[OCLIENT](../../overview/visual-cpp-samples.md)を参照してください。

### <a name="remarks"></a>解説

既定の実装では、何も行わずに DROPEFFECT_NONE が返されます。

この関数をオーバーライドして、ドラッグ操作中の視覚的なフィードバックをユーザーに提供します。 この関数は継続的に呼び出されるため、その中に含まれるコードはできるだけ最適化する必要があります。 詳細については、「 [OLE ドラッグアンドドロップ: drop target を実装する](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)」を参照してください。

##  <a name="ondragscroll"></a>CView:: OnDragScroll

[Ondragenter](#ondragenter)または[OnDragOver](#ondragover)を呼び出す前にフレームワークによって呼び出され、ポイントがスクロール領域にあるかどうかを判断します。

```
virtual DROPEFFECT OnDragScroll(
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

*dwKeyState*<br/>
修飾子キーの状態を格納します。 これは、MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON、および MK_RBUTTON の任意の数を組み合わせたものです。

*視点*<br/>
画面を基準とした、カーソルの位置 (ピクセル単位) を格納します。

### <a name="return-value"></a>戻り値

DROPEFFECT 列挙型の値。ユーザーがこの位置でオブジェクトをドロップした場合に発生するドロップの種類を示します。 通常、ドロップの種類は、 *Dwkeystate*によって示される現在のキーの状態に依存します。 キーの状態と DROPEFFECT の値の標準マッピングは次のとおりです。

- このウィンドウでは、データオブジェクトを削除することはできません DROPEFFECT_NONE。

- MK_CONTROL &#124; MK_SHIFT を DROPEFFECT_LINK して、オブジェクトとそのサーバーとの間にリンケージを作成します。

- MK_CONTROL の DROPEFFECT_COPY は、削除されたオブジェクトのコピーを作成します。

- MK_ALT の DROPEFFECT_MOVE は、削除されたオブジェクトのコピーを作成し、元のオブジェクトを削除します。

- DROPEFFECT_SCROLL は、ドラッグのスクロール操作が実行されるか、または対象のビューで発生することを示します。

詳細については、MFC の高度な概念のサンプル[OCLIENT](../../overview/visual-cpp-samples.md)を参照してください。

### <a name="remarks"></a>解説

このイベントに特別な動作を提供する場合は、この関数をオーバーライドします。 既定の実装では、カーソルが各ウィンドウの境界内の既定のスクロール領域にドラッグされると、ウィンドウが自動的にスクロールされます。 詳細については、「 [OLE ドラッグアンドドロップ: drop target を実装する](../../mfc/drag-and-drop-ole.md#implement-a-drop-target)」を参照してください。

##  <a name="ondraw"></a>CView:: OnDraw

ドキュメントのイメージをレンダリングするためにフレームワークによって呼び出されます。

```
virtual void OnDraw(CDC* pDC) = 0;
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
ドキュメントのイメージを描画するために使用されるデバイスコンテキストを指します。

### <a name="remarks"></a>解説

フレームワークは、画面の表示、印刷、および印刷プレビューを実行するためにこの関数を呼び出し、それぞれのケースで異なるデバイスコンテキストを渡します。 既定の実装はありません。

ドキュメントのビューを表示するには、この関数をオーバーライドする必要があります。 *PDC*パラメーターが指す[CDC](../../mfc/reference/cdc-class.md)オブジェクトを使用して、グラフィックデバイスインターフェイス (GDI) 呼び出しを行うことができます。 描画する前に、ペンやフォントなどの GDI リソースをデバイスコンテキストに選択し、後で選択を解除することができます。 多くの場合、描画コードはデバイスに依存しないことがあります。つまり、画像を表示しているデバイスの種類に関する情報は必要ありません。

描画を最適化するには、デバイスコンテキストの[RectVisible](../../mfc/reference/cdc-class.md#rectvisible)メンバー関数を呼び出して、特定の四角形が描画されるかどうかを確認します。 通常の画面表示と印刷を区別する必要がある場合は、デバイスコンテキストの[IsPrinting](../../mfc/reference/cdc-class.md#isprinting)メンバー関数を呼び出します。

##  <a name="ondrop"></a>CView:: OnDrop

ユーザーが有効なドロップターゲットを介してデータオブジェクトを解放したときに、フレームワークによって呼び出されます。

```
virtual BOOL OnDrop(
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

' pDataObject * は、ドロップ先にドロップされる[COleDataObject](../../mfc/reference/coledataobject-class.md)をポイントします。

*dropEffect*<br/>
ユーザーが要求したドロップ効果。

- DROPEFFECT_COPY によって、削除されるデータオブジェクトのコピーが作成されます。

- DROPEFFECT_MOVE は、データオブジェクトを現在のマウスの位置に移動します。

- DROPEFFECT_LINK は、データオブジェクトとそのサーバーとの間にリンクを作成します。

*視点*<br/>
ビュークライアント領域を基準とした、現在のマウス位置。

### <a name="return-value"></a>戻り値

削除に成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

既定の実装では、何も実行されず、FALSE が返されます。

この関数をオーバーライドすると、ビューのクライアント領域への OLE ドロップの効果が実装されます。 データオブジェクトは、指定されたポイントでクリップボードのデータ形式とデータが削除されるように*Pdataobject*を使用して調べることができます。

> [!NOTE]
>  このビュークラスで[OnDropEx](#ondropex)に対するオーバーライドがある場合、フレームワークはこの関数を呼び出しません。

##  <a name="ondropex"></a>CView:: OnDropEx

ユーザーが有効なドロップターゲットを介してデータオブジェクトを解放したときに、フレームワークによって呼び出されます。

```
virtual DROPEFFECT OnDropEx(
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

*pDataObject*<br/>
ドロップ先にドロップされる[COleDataObject](../../mfc/reference/coledataobject-class.md)をポイントします。

*dropDefault*<br/>
ユーザーが現在のキーの状態に基づいて既定のドロップ操作を選択した場合の効果。 DROPEFFECT_NONE の可能性があります。 ドロップ効果については、「解説」を参照してください。

*ドロップ*<br/>
ドロップソースがサポートするドロップ効果の一覧。 ドロップ効果の値は、ビットごとの OR ( **&#124;**) 演算を使用して組み合わせることができます。 ドロップ効果については、「解説」を参照してください。

*視点*<br/>
ビュークライアント領域を基準とした、現在のマウス位置。

### <a name="return-value"></a>戻り値

*ポイント*によって指定された位置での削除が試行された結果のドロップ効果。 これは、 *dropEffectList*によって示される値のいずれかである必要があります。 ドロップ効果については、「解説」を参照してください。

### <a name="remarks"></a>解説

既定の実装では、何も行わず、ダミーの値 (-1) を返して、フレームワークが[OnDrop](#ondrop)ハンドラーを呼び出す必要があることを示します。

マウスの右ボタンのドラッグアンドドロップの効果を実装するには、この関数をオーバーライドします。 マウスの右ボタンのドラッグアンドドロップでは、通常、マウスの右ボタンが離されたときに選択肢のメニューが表示されます。

`OnDropEx` のオーバーライドでは、マウスの右ボタンを照会する必要があります。 [Getkeystate](/windows/win32/api/winuser/nf-winuser-getkeystate)を呼び出すか、 [ondragenter](#ondragenter)ハンドラーからマウスの右ボタンの状態を格納することができます。

- マウスの右ボタンが押されていない場合は、ドロップソースによるドロップ効果のサポートを提供するポップアップメニューがオーバーライドによって表示されます。

   - ドロップ*ダウン*を調べて、ドロップソースでサポートされているドロップ効果を確認します。 ポップアップメニューでは、これらの操作のみを有効にします。

   - [Setmenudefaultitem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)を使用して、 *dropdefault*に基づいて既定のアクションを設定します。

   - 最後に、ポップアップメニューからユーザーが選択した操作を実行します。

- マウスの右ボタンが押されていない場合は、オーバーライドでこれを標準のドロップ要求として処理する必要があります。 *Dropdefault*に指定されているドロップ効果を使用します。 または、オーバーライドによってダミー値 (-1) を返すことで、`OnDrop` がこのドロップ操作を処理することを示すことができます。

*Pdataobject*を使用して、指定したポイントでクリップボードのデータ形式とデータが削除されたかどうかを `COleDataObject` を調べます。

ドロップ効果は、ドロップ操作に関連付けられているアクションを記述します。 次のドロップ効果の一覧を参照してください。

- DROPEFFECT_NONE 削除は許可されません。

- DROPEFFECT_COPY コピー操作が実行されます。

- 移動操作が実行さ DROPEFFECT_MOVE ます。

- DROPEFFECT_LINK、削除されたデータから元のデータへのリンクが確立されます。

- DROPEFFECT_SCROLL は、ドラッグのスクロール操作が実行されるか、またはターゲットで発生することを示します。

既定のメニューコマンドの設定の詳細については、このボリュームの Windows SDK および[CMenu:: GetSafeHmenu](../../mfc/reference/cmenu-class.md#getsafehmenu)の[Setmenudefaultitem](/windows/win32/api/winuser/nf-winuser-setmenudefaultitem)に関する説明を参照してください。

##  <a name="onendprinting"></a>CView:: OnEndPrinting

ドキュメントが印刷またはプレビューされた後に、フレームワークによって呼び出されます。

```
virtual void OnEndPrinting(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
プリンター デバイス コンテキストを指し示します。

*pInfo*<br/>
現在の印刷ジョブを表す [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 構造体を指し示します。

### <a name="remarks"></a>解説

この関数の既定の実装は、何も行いません。 この関数をオーバーライドすると、 [OnBeginPrinting](#onbeginprinting)メンバー関数で割り当てた GDI リソースがすべて解放されます。

##  <a name="onendprintpreview"></a>CView:: OnEndPrintPreview

ユーザーが印刷プレビューモードを終了したときにフレームワークによって呼び出されます。

```
virtual void OnEndPrintPreview(
    CDC* pDC,
    CPrintInfo* pInfo,
    POINT point,
    CPreviewView* pView);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
プリンター デバイス コンテキストを指し示します。

*pInfo*<br/>
現在の印刷ジョブを表す [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 構造体を指し示します。

*視点*<br/>
最後にプレビューモードで表示されたページ上のポイントを指定します。

*pView*<br/>
プレビューに使用されるビューオブジェクトを指します。

### <a name="remarks"></a>解説

この関数の既定の実装では、 [OnEndPrinting](#onendprinting)メンバー関数が呼び出され、メインフレームウィンドウが、印刷プレビューの開始前の状態に復元されます。 プレビューモードが終了したときに特別な処理を実行するには、この関数をオーバーライドします。 たとえば、プレビューモードから通常の表示モードに切り替えるときにドキュメント内のユーザーの位置を維持するには、*ポイント*パラメーターと、 *pInfo*パラメーターが指す `CPrintInfo` 構造体の `m_nCurPage` メンバーによって表される位置までスクロールします。

常に、関数の最後でオーバーライドから `OnEndPrintPreview` の基本クラスバージョンを呼び出します。

##  <a name="oninitialupdate"></a>CView:: OnInitialUpdate

最初にビューがドキュメントにアタッチされた後、最初にビューが表示される前に、フレームワークによって呼び出されます。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>解説

この関数の既定の実装では、ヒント情報を指定せずに[OnUpdate](#onupdate)メンバー関数を呼び出します (つまり、 *lhint*パラメーターには0、 *PHINT*パラメーターには NULL を使用します)。 ドキュメントに関する情報を必要とする1回限りの初期化を実行するには、この関数をオーバーライドします。 たとえば、アプリケーションに固定サイズのドキュメントがある場合、この関数を使用すると、ドキュメントのサイズに基づいて、ビューのスクロール制限を初期化できます。 アプリケーションで可変サイズのドキュメントがサポートされている場合、ドキュメントが変更されるたびにスクロール制限を更新するには、 [OnUpdate](#onupdate)を使用します。

##  <a name="onpreparedc"></a>CView:: OnPrepareDC

[OnDraw](#ondraw)メンバー関数が画面に表示される前にフレームワークによって呼び出されます。また、印刷中または印刷プレビュー中に、各ページに対して[OnPrint](#onprint)メンバー関数が呼び出される前に、フレームワークによって呼び出されます。

```
virtual void OnPrepareDC(
    CDC* pDC,
    CPrintInfo* pInfo = NULL);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
ドキュメントのイメージを描画するために使用されるデバイスコンテキストを指します。

*pInfo*<br/>
`OnPrepareDC` が印刷または印刷プレビューの対象として呼び出されている場合、現在の印刷ジョブを記述する[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)構造体をポイントします。`m_nCurPage` メンバーは、印刷するページを指定します。 画面表示のために `OnPrepareDC` が呼び出されている場合、このパラメーターは NULL になります。

### <a name="remarks"></a>解説

この関数の既定の実装では、画面表示のために関数が呼び出されても、何も実行されません。 ただし、この関数は、デバイスコンテキストの属性を調整するために、 [CScrollView](../../mfc/reference/cscrollview-class.md)などの派生クラスでオーバーライドされます。そのため、常にオーバーライドの先頭で基底クラスの実装を呼び出す必要があります。

印刷のために関数が呼び出された場合、既定の実装は、 *pInfo*パラメーターに格納されているページ情報を調べます。 ドキュメントの長さが指定されていない場合、`OnPrepareDC` はドキュメントを1ページの長さと想定し、1ページが印刷された後に印刷ループを停止します。 関数は、構造体の `m_bContinuePrinting` メンバーを FALSE に設定することによって、print ループを停止します。

次のいずれかの理由により、`OnPrepareDC` をオーバーライドします。

- 指定されたページで必要に応じて、デバイスコンテキストの属性を調整します。 たとえば、マッピングモードまたはデバイスコンテキストのその他の特性を設定する必要がある場合は、この関数で実行します。

- 印刷時の改ページ位置の自動修正を実行する場合。 通常、印刷を開始するときは、 [OnPreparePrinting](#onprepareprinting)メンバー関数を使用して、ドキュメントの長さを指定します。 ただし、ドキュメントがどれだけ長くなっているかがわかっていない場合 (たとえば、データベースから未確定数のレコードを印刷する場合など) は、`OnPrepareDC` をオーバーライドして、ドキュメントの印刷中にドキュメントの終わりをテストします。 印刷するドキュメントがそれ以上ない場合は、`CPrintInfo` 構造の `m_bContinuePrinting` メンバーを FALSE に設定します。

- ページ単位でプリンターにエスケープコードを送信すること。 `OnPrepareDC`からエスケープコードを送信するには、 *pDC*パラメーターの `Escape` メンバー関数を呼び出します。

オーバーライドの先頭にある `OnPrepareDC` の基本クラスバージョンを呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#183](../../mfc/codesnippet/cpp/cview-class_1.cpp)]

##  <a name="onprepareprinting"></a>CView:: OnPreparePrinting

ドキュメントが印刷またはプレビューされる前に、フレームワークによって呼び出されます。

```
virtual BOOL OnPreparePrinting(CPrintInfo* pInfo);
```

### <a name="parameters"></a>パラメーター

*pInfo*<br/>
現在の印刷ジョブを表す [CPrintInfo](../../mfc/reference/cprintinfo-structure.md) 構造体を指し示します。

### <a name="return-value"></a>戻り値

印刷を開始する場合は0以外。印刷ジョブが取り消された場合は0。

### <a name="remarks"></a>解説

既定の実装では、何も行われません。

印刷と印刷プレビューを有効にするには、この関数をオーバーライドする必要があります。 [DoPreparePrinting](#doprepareprinting)メンバー関数を呼び出し、 *pInfo*パラメーターを渡して、戻り値を返します。`DoPreparePrinting` によって [印刷] ダイアログボックスが表示され、プリンターデバイスコンテキストが作成されます。 既定値以外の値を使用して [印刷] ダイアログボックスを初期化する場合は、 *pInfo*のメンバーに値を割り当てます。 たとえば、ドキュメントの長さがわかっている場合は、`DoPreparePrinting`を呼び出す前に、 *pInfo*の[SetMaxPage](../../mfc/reference/cprintinfo-structure.md#setmaxpage)メンバー関数に値を渡します。 この値は、[印刷] ダイアログボックスの範囲の部分にある [To] ボックスに表示されます。

`DoPreparePrinting` では、プレビュージョブの [印刷] ダイアログボックスは表示されません。 印刷ジョブの [印刷] ダイアログボックスをバイパスする場合は、 *pInfo*の `m_bPreview` メンバーが FALSE であることを確認し、`DoPreparePrinting`に渡す前に TRUE に設定します。その後、それを FALSE にリセットします。

プリンターデバイスコンテキストを表す `CDC` オブジェクトへのアクセスを必要とする初期化を実行する必要がある場合は (たとえば、ドキュメントの長さを指定する前にページサイズを確認する必要がある場合)、`OnBeginPrinting` メンバー関数をオーバーライドします。

*PInfo*パラメーターの `m_nNumPreviewPages` または `m_strPageDesc` のメンバーの値を設定する場合は、`DoPreparePrinting`を呼び出した後に実行します。 `DoPreparePrinting` メンバー関数は、`m_nNumPreviewPages` をアプリケーションのの値に設定します。INI ファイルを `m_strPageDesc`、既定値に設定します。

### <a name="example"></a>例

  `OnPreparePrinting` をオーバーライドし、オーバーライドから `DoPreparePrinting` を呼び出して、フレームワークが [印刷] ダイアログボックスを表示し、プリンター DC を作成できるようにします。

[!code-cpp[NVC_MFCDocView#184](../../mfc/codesnippet/cpp/cview-class_2.cpp)]

ドキュメントに含まれるページ数がわかっている場合は、`DoPreparePrinting`を呼び出す前に `OnPreparePrinting` の [最大] ページを設定します。 フレームワークによって、[印刷] ダイアログボックスの [to] ボックスに最大ページ番号が表示されます。

[!code-cpp[NVC_MFCDocView#185](../../mfc/codesnippet/cpp/cview-class_3.cpp)]

##  <a name="onprint"></a>CView:: OnPrint

ドキュメントのページを印刷またはプレビューするために、フレームワークによって呼び出されます。

```
virtual void OnPrint(
    CDC* pDC,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
プリンター デバイス コンテキストを指し示します。

*pInfo*<br/>
現在の印刷ジョブを記述する `CPrintInfo` 構造体を指します。

### <a name="remarks"></a>解説

フレームワークは、印刷されるページごとに、 [OnPrepareDC](#onpreparedc)メンバー関数を呼び出した直後にこの関数を呼び出します。 印刷されるページは、 *pInfo*が指す[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)構造体の `m_nCurPage` メンバーによって指定されます。 既定の実装は、 [OnDraw](#ondraw)メンバー関数を呼び出し、それにプリンターデバイスコンテキストを渡します。

次のいずれかの理由で、この関数をオーバーライドします。

- マルチページドキュメントの印刷を許可する場合は。 現在印刷中のページに対応するドキュメントの部分のみを表示します。 レンダリングを実行するために `OnDraw` を使用している場合は、ドキュメントの適切な部分だけが印刷されるようにビューポートの原点を調整できます。

- 印刷されたイメージを画面イメージとは異なる外観にする場合は。アプリケーションが WYSIWYG でない場合は。 プリンターデバイスコンテキストを `OnDraw`に渡す代わりに、デバイスコンテキストを使用して、画面に表示されていない属性を使用してイメージをレンダリングします。

   画面表示に使用しない、印刷用の GDI リソースが必要な場合は、描画する前にデバイスコンテキストに選択し、後で選択を解除します。 これらの GDI リソースは[OnBeginPrinting](#onbeginprinting)に割り当てられ、 [OnEndPrinting](#onendprinting)でリリースされる必要があります。

- ヘッダーまたはフッターを実装します。 `OnDraw` を使用して、印刷できる領域を制限することで、レンダリングを行うことができます。

*PInfo*パラメーターの `m_rectDraw` メンバーは、ページの印刷可能領域を論理単位で記述することに注意してください。

`OnPrint`のオーバーライドで `OnPrepareDC` を呼び出さないでください。フレームワークは、`OnPrint`を呼び出す前に、`OnPrepareDC` を自動的に呼び出します。

### <a name="example"></a>例

オーバーライドされた `OnPrint` 関数のスケルトンを次に示します。

[!code-cpp[NVC_MFCDocView#186](../../mfc/codesnippet/cpp/cview-class_4.cpp)]

別の例については、「 [CRichEditView::P rintinsiderect](../../mfc/reference/cricheditview-class.md#printinsiderect)」を参照してください。

##  <a name="onscroll"></a>CView:: OnScroll

スクロールが可能かどうかを判断するために、フレームワークによって呼び出されます。

```
virtual BOOL OnScroll(
    UINT nScrollCode,
    UINT nPos,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>パラメーター

*nScrollCode*<br/>
ユーザーのスクロール要求を示すスクロールバーコード。 このパラメーターは2つの部分で構成されています。下位バイトは、水平方向に発生するスクロールの種類を決定し、上位バイトは垂直方向に発生するスクロールの種類を決定します。

- SB_BOTTOM が一番下までスクロールします。

- SB_LINEDOWN 1 行下にスクロールします。

- SB_LINEUP 1 行上へスクロールします。

- SB_PAGEDOWN 1 ページ下にスクロールします。

- SB_PAGEUP 1 ページ上にスクロールします。

- スクロールボックスを指定した位置にドラッグ SB_THUMBTRACK ます。 現在位置は*nPos*で指定されています。

- SB_TOP が一番上にスクロールします。

*nPos*<br/>
スクロールバーのコードが SB_THUMBTRACK 場合は、現在のスクロールボックスの位置を格納します。それ以外の場合は使用されません。 最初のスクロール範囲によっては、 *nPos*が負の値になる場合があり、必要に応じて**int**にキャストする必要があります。

*bDoScroll*<br/>
指定したスクロール操作を実際に実行する必要があるかどうかを判断します。 TRUE の場合、スクロールが行われます。FALSE の場合、スクロールは行われません。

### <a name="return-value"></a>戻り値

*BDoScroll*が TRUE で、ビューが実際にスクロールされた場合は、0以外の値を返します。それ以外の場合は0です。 *BDoScroll*が FALSE の場合は、実際にはスクロールを行っていなくても、 *bDoScroll*が TRUE の場合に返された値を返します。

### <a name="remarks"></a>解説

1つの場合、この関数はフレームワークによって呼び出され、ビューがスクロールバーメッセージを受信したときに*bDoScroll*が TRUE に設定されます。 この場合は、実際にビューをスクロールする必要があります。 それ以外の場合、この関数は*bDoScroll*を FALSE に設定して呼び出されます。これは、OLE 項目が最初にドロップ先の自動スクロール領域にドラッグされたときに、スクロールが行われる前に発生します。 この場合、実際にはビューをスクロールしないでください。

##  <a name="onscrollby"></a>CView:: OnScrollBy

OLE 項目をビューの現在の境界に対してドラッグするか、垂直方向または水平方向のスクロールバーを操作することによって、ユーザーがドキュメントの現在のビューの外にある領域を表示すると、フレームワークによって呼び出されます。

```
virtual BOOL OnScrollBy(
    CSize sizeScroll,
    BOOL bDoScroll = TRUE);
```

### <a name="parameters"></a>パラメーター

*sizeScroll*<br/>
水平方向および垂直方向にスクロールされたピクセル数。

*bDoScroll*<br/>
ビューのスクロールが発生するかどうかを決定します。 TRUE の場合、スクロールが行われます。FALSE の場合、スクロールは行われません。

### <a name="return-value"></a>戻り値

ビューをスクロールできた場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

派生クラスでは、このメソッドは、ユーザーが要求した方向にビューがスクロール可能かどうかを確認し、必要に応じて新しい領域を更新します。 この関数は、 [cwnd:: OnHScroll](../../mfc/reference/cwnd-class.md#onhscroll)と[Cwnd:: onvscroll](../../mfc/reference/cwnd-class.md#onvscroll)によって自動的に呼び出され、実際のスクロール要求を実行します。

このメソッドの既定の実装ではビューは変更されませんが、呼び出されていない場合、ビューは `CScrollView`派生クラスでスクロールされません。

ドキュメントの幅または高さが32767ピクセルを超えた場合、`OnScrollBy` は無効な*sizeScroll*引数を使用して呼び出されるため、32767を超えるスクロールは失敗します。

##  <a name="onupdate"></a>CView:: OnUpdate

ビューのドキュメントが変更された後にフレームワークによって呼び出されます。この関数は、 [CDocument:: UpdateAllViews](../../mfc/reference/cdocument-class.md#updateallviews)によって呼び出され、ビューがその変更を反映するように表示を更新できるようにします。

```
virtual void OnUpdate(
    CView* pSender,
    LPARAM lHint,
    CObject* pHint);
```

### <a name="parameters"></a>パラメーター

*pSender*<br/>
ドキュメントを変更したビューを指します。すべてのビューを更新する場合は NULL です。

*lHint*<br/>
変更に関する情報が含まれています。

*pHint*<br/>
変更に関する情報を格納しているオブジェクトを指します。

### <a name="remarks"></a>解説

また、 [OnInitialUpdate](#oninitialupdate)の既定の実装によって呼び出されます。 既定の実装は、クライアント領域全体を無効にし、次の WM_PAINT メッセージを受信したときに描画するようにマークします。 文書の変更部分にマップされている領域のみを更新する場合は、この関数をオーバーライドします。 これを行うには、ヒントパラメーターを使用して、変更に関する情報を渡す必要があります。

*Lhint*を使用するには、特殊なヒント値 (通常はビットマスクまたは列挙型) を定義し、ドキュメントがこれらの値のいずれかに合格するようにします。 *Phint*を使用するには、 [CObject](../../mfc/reference/cobject-class.md)からヒントクラスを派生させ、ドキュメントがヒントオブジェクトへのポインターを渡すようにします。`OnUpdate`をオーバーライドする場合は、 [CObject:: IsKindOf](../../mfc/reference/cobject-class.md#iskindof)メンバー関数を使用して、ヒントオブジェクトの実行時の型を決定します。

通常、`OnUpdate`から直接描画を実行することはできません。 代わりに、デバイス座標で、更新が必要な領域を示す四角形を特定します。この四角形を[CWnd:: InvalidateRect](../../mfc/reference/cwnd-class.md#invalidaterect)に渡します。 これにより、次に[WM_PAINT](/windows/win32/gdi/wm-paint)メッセージを受信したときに描画が行われます。

*Lhint*が0で*PHINT*が NULL の場合、ドキュメントは汎用更新通知を送信しています。 ビューが汎用更新通知を受信する場合、またはヒントをデコードできない場合は、クライアント領域全体を無効にする必要があります。

## <a name="see-also"></a>参照

[MFC のサンプル MDIDOCVW](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[CFrameWnd クラス](../../mfc/reference/cframewnd-class.md)<br/>
[CSplitterWnd クラス](../../mfc/reference/csplitterwnd-class.md)<br/>
[CDC クラス](../../mfc/reference/cdc-class.md)<br/>
[CDocTemplate クラス](../../mfc/reference/cdoctemplate-class.md)<br/>
[CDocument クラス](../../mfc/reference/cdocument-class.md)
