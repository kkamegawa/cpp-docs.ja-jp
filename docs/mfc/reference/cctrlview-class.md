---
title: CCtrlView クラス
ms.date: 11/04/2016
f1_keywords:
- CCtrlView
- AFXWIN/CCtrlView
- AFXWIN/CCtrlView::CCtrlView
- AFXWIN/CCtrlView::OnDraw
- AFXWIN/CCtrlView::PreCreateWindow
- AFXWIN/CCtrlView::m_dwDefaultStyle
- AFXWIN/CCtrlView::m_strClass
helpviewer_keywords:
- CCtrlView [MFC], CCtrlView
- CCtrlView [MFC], OnDraw
- CCtrlView [MFC], PreCreateWindow
- CCtrlView [MFC], m_dwDefaultStyle
- CCtrlView [MFC], m_strClass
ms.assetid: ff488596-1e71-451f-8fec-b0831a7b44e0
ms.openlocfilehash: 334f139b81afeb06d57cbd128abe9e413b1fd0e7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507148"
---
# <a name="cctrlview-class"></a>CCtrlView クラス

Windows 98 および Windows NT Version 3.51 以降がサポートするコモン コントロールにドキュメント/ビュー アーキテクチャを適合させます。

## <a name="syntax"></a>構文

```
class CCtrlView : public CView
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CCtrlView::CCtrlView](#cctrlview)|`CCtrlView` オブジェクトを構築します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CCtrlView:: OnDraw](#ondraw)|指定されたデバイスコンテキストを使用して描画するために、フレームワークによって呼び出されます。|
|[CCtrlView::P reCreateWindow](#precreatewindow)|`CCtrlView` オブジェクトに関連付けられている Windows のウィンドウが作成される前に呼び出されます。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CCtrlView::m_dwDefaultStyle](#m_dwdefaultstyle)|ビュークラスの既定のスタイルを格納します。|
|[CCtrlView::m_strClass](#m_strclass)|ビュークラスの Windows クラス名を格納します。|

## <a name="remarks"></a>Remarks

クラスと`CCtrlView`その派生クラスで[ある CEditView、CEditView](../../mfc/reference/ceditview-class.md)、 [CListView](../../mfc/reference/clistview-class.md)、 [CTreeView](../../mfc/reference/ctreeview-class.md)、および[CRichEditView](../../mfc/reference/cricheditview-class.md)は、ドキュメント/ビューアーキテクチャを、windows 95/98 および windows NT バージョン3.51 でサポートされる新しいコモンコントロールに適応させます。以降。 ドキュメント/ビューアーキテクチャの詳細については、「[ドキュメント/ビューアーキテクチャ](../../mfc/document-view-architecture.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

`CCtrlView`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="cctrlview"></a>CCtrlView::CCtrlView

`CCtrlView` オブジェクトを構築します。

```
CCtrlView(
    LPCTSTR lpszClass,
    DWORD dwStyle);
```

### <a name="parameters"></a>パラメーター

*lpszClass*<br/>
ビュークラスの Windows クラス名。

*dwStyle*<br/>
ビュークラスのスタイル。

### <a name="remarks"></a>Remarks

フレームワークは、新しいフレームウィンドウが作成されたとき、またはウィンドウが分割されたときにコンストラクターを呼び出します。 ドキュメントが添付された後にビューを初期化するには、 [CView:: OnInitialUpdate](../../mfc/reference/cview-class.md#oninitialupdate)をオーバーライドします。 [Cwnd:: create](../../mfc/reference/cwnd-class.md#create)または[Cwnd:: CreateEx](../../mfc/reference/cwnd-class.md#createex)を呼び出して、Windows オブジェクトを作成します。

##  <a name="m_strclass"></a>CCtrlView::m_strClass

ビュークラスの Windows クラス名を格納します。

```
CString m_strClass;
```

##  <a name="m_dwdefaultstyle"></a>CCtrlView::m_dwDefaultStyle

ビュークラスの既定のスタイルを格納します。

```
DWORD m_dwDefaultStyle;
```

### <a name="remarks"></a>Remarks

このスタイルは、ウィンドウの作成時に適用されます。

##  <a name="ondraw"></a>  CCtrlView::OnDraw

指定されたデバイスコンテキストを使用して`CCtrlView`オブジェクトのコンテンツを描画するために、フレームワークによって呼び出されます。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
描画が発生するデバイスコンテキストへのポインター。

### <a name="remarks"></a>Remarks

`OnDraw`は、通常、画面表示のために呼び出され、 *pDC*によって指定された画面デバイスコンテキストを渡します。

##  <a name="precreatewindow"></a>CCtrlView::P reCreateWindow

`CWnd` オブジェクトに関連付けられている Windows のウィンドウが作成される前に呼び出されます。

```
virtual BOOL PreCreateWindow(CREATESTRUCT& cs);
```

### <a name="parameters"></a>パラメーター

*cs*<br/>
[CREATESTRUCT](/windows/win32/api/winuser/ns-winuser-createstructw)構造体。

### <a name="return-value"></a>戻り値

ウィンドウの作成を続行する場合は0以外の。作成エラーを示す場合は0。

### <a name="remarks"></a>Remarks

この関数を直接呼び出さないでください。

この関数の既定の実装では、ウィンドウクラス名が NULL かどうかがチェックされ、適切な既定値に置き換えられます。 ウィンドウが作成される前に`CREATESTRUCT`構造を変更するには、このメンバー関数をオーバーライドします。

から`CCtrlView`派生した各クラスは、のオーバーライドに独自`PreCreateWindow`の機能を追加します。 仕様として、これら`PreCreateWindow`の派生は記載されていません。 各クラスに適したスタイルとスタイル間の相互依存関係を判断するには、アプリケーションの基本クラスの MFC ソースコードを確認します。 をオーバーライド`PreCreateWindow`することを選択した場合は、MFC ソースコードから収集された情報を使用して、アプリケーションの基本クラスで使用されるスタイルが必要な機能を提供するかどうかを判断できます。

ウィンドウスタイルの変更の詳細については、「 [MFC で作成されたウィンドウのスタイルを変更](../../mfc/changing-the-styles-of-a-window-created-by-mfc.md)する」を参照してください。

## <a name="see-also"></a>関連項目

[CView クラス](../../mfc/reference/cview-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CTreeView クラス](../../mfc/reference/ctreeview-class.md)<br/>
[CListView クラス](../../mfc/reference/clistview-class.md)<br/>
[CRichEditView クラス](../../mfc/reference/cricheditview-class.md)
