---
title: CHtmlEditView クラス
ms.date: 11/04/2016
f1_keywords:
- CHtmlEditView
- AFXHTML/CHtmlEditView
- AFXHTML/CHtmlEditView::CHtmlEditView
- AFXHTML/CHtmlEditView::Create
- AFXHTML/CHtmlEditView::GetDHtmlDocument
- AFXHTML/CHtmlEditView::GetStartDocument
helpviewer_keywords:
- CHtmlEditView [MFC], CHtmlEditView
- CHtmlEditView [MFC], Create
- CHtmlEditView [MFC], GetDHtmlDocument
- CHtmlEditView [MFC], GetStartDocument
ms.assetid: 166c8ba8-3fb5-4dd7-a9ea-5bca662d00f6
ms.openlocfilehash: 8267a5272d2d542c4679bf30aa9d3ad8b933d81d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389568"
---
# <a name="chtmleditview-class"></a>CHtmlEditView クラス

MFC のドキュメント/ビュー アーキテクチャのコンテキストで WebBrowser 編集プラットフォームの機能を提供します。

## <a name="syntax"></a>構文

```
class CHtmlEditView : public CHtmlView, public CHtmlEditCtrlBase<CHtmlEditView>
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CHtmlEditView::CHtmlEditView](#chtmleditview)|`CHtmlEditView` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CHtmlEditView::Create](#create)|新しいウィンドウ オブジェクトを作成します。|
|[CHtmlEditView::GetDHtmlDocument](#getdhtmldocument)|返します、`IHTMLDocument2`現在のドキュメントのインターフェイス。|
|[CHtmlEditView::GetStartDocument](#getstartdocument)|このビューの既定のドキュメントの名前を取得します。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CScrollView](../../mfc/reference/cscrollview-class.md)

[CFormView](../../mfc/reference/cformview-class.md)

[CHtmlEditCtrlBase](../../mfc/reference/chtmleditctrlbase-class.md)

[CHtmlView](../../mfc/reference/chtmlview-class.md)

`CHtmlEditView`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxhtml.h

##  <a name="chtmleditview"></a>  CHtmlEditView::CHtmlEditView

`CHtmlEditView` オブジェクトを構築します。

```
CHtmlEditView();
```

##  <a name="create"></a>  CHtmlEditView::Create

新しいウィンドウ オブジェクトを作成します。

```
virtual BOOL Create(
    LPCTSTR lpszClassName,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID,
    CCreateContext* pContext = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszClassName*<br/>
Windows クラスの名前を示す文字の null で終わる文字列を指します。 クラス名が登録されている任意の名前を指定できます、 [AfxRegisterWndClass](application-information-and-management.md#afxregisterwndclass)グローバル関数または`RegisterClass`Windows 関数。 NULL の場合は、定義済みの既定値を使用して[CFrameWnd](../../mfc/reference/cframewnd-class.md)属性。

*lpszWindowName*<br/>
ウィンドウの名前を表す null で終わる文字列へのポインター。

*dwStyle*<br/>
ウィンドウのスタイル属性を指定します。 既定では、WS_VISIBLE と WS_CHILD Windows スタイルが設定されます。

*rect*<br/>
参照を[RECT](/previous-versions/dd162897\(v=vs.85\))ウィンドウの位置とサイズを指定する構造体。 *RectDefault*値により、Windows を新しいウィンドウの位置とサイズを指定します。

*pParentWnd*<br/>
コントロールの親ウィンドウへのポインター。

*nID*<br/>
ビューの ID 番号。 既定では、AFX_IDW_PANE_FIRST に設定します。

*pContext*<br/>
ポインターを[CCreateContext](../../mfc/reference/ccreatecontext-structure.md)します。 既定では NULL です。

### <a name="remarks"></a>Remarks

このメソッドが含まれている web ブラウザーを呼び出すことも`Navigate`を既定のドキュメントを読み込むメソッド (を参照してください[CHtmlEditView::GetStartDocument](#getstartdocument))。

##  <a name="getdhtmldocument"></a>  CHtmlEditView::GetDHtmlDocument

返します、`IHTMLDocument2`現在のドキュメントのインターフェイス。

```
BOOL GetDHtmlDocument(IHTMLDocument2** ppDocument) const;
```

### <a name="parameters"></a>パラメーター

*ppDocument*<br/>
[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))インターフェイス。

##  <a name="getstartdocument"></a>  CHtmlEditView::GetStartDocument

このビューの既定のドキュメントの名前を取得します。

```
virtual LPCTSTR GetStartDocument();
```

## <a name="see-also"></a>関連項目

[HTMLEdit サンプル](../../overview/visual-cpp-samples.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
