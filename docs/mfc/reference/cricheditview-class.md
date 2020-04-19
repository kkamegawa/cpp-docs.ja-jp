---
title: CRichEditView クラス
ms.date: 11/04/2016
f1_keywords:
- CRichEditView
- AFXRICH/CRichEditView
- AFXRICH/CRichEditView::CRichEditView
- AFXRICH/CRichEditView::AdjustDialogPosition
- AFXRICH/CRichEditView::CanPaste
- AFXRICH/CRichEditView::DoPaste
- AFXRICH/CRichEditView::FindText
- AFXRICH/CRichEditView::FindTextSimple
- AFXRICH/CRichEditView::GetCharFormatSelection
- AFXRICH/CRichEditView::GetDocument
- AFXRICH/CRichEditView::GetInPlaceActiveItem
- AFXRICH/CRichEditView::GetMargins
- AFXRICH/CRichEditView::GetPageRect
- AFXRICH/CRichEditView::GetPaperSize
- AFXRICH/CRichEditView::GetParaFormatSelection
- AFXRICH/CRichEditView::GetPrintRect
- AFXRICH/CRichEditView::GetPrintWidth
- AFXRICH/CRichEditView::GetRichEditCtrl
- AFXRICH/CRichEditView::GetSelectedItem
- AFXRICH/CRichEditView::GetTextLength
- AFXRICH/CRichEditView::GetTextLengthEx
- AFXRICH/CRichEditView::InsertFileAsObject
- AFXRICH/CRichEditView::InsertItem
- AFXRICH/CRichEditView::IsRichEditFormat
- AFXRICH/CRichEditView::OnCharEffect
- AFXRICH/CRichEditView::OnParaAlign
- AFXRICH/CRichEditView::OnUpdateCharEffect
- AFXRICH/CRichEditView::OnUpdateParaAlign
- AFXRICH/CRichEditView::PrintInsideRect
- AFXRICH/CRichEditView::PrintPage
- AFXRICH/CRichEditView::SetCharFormat
- AFXRICH/CRichEditView::SetMargins
- AFXRICH/CRichEditView::SetPaperSize
- AFXRICH/CRichEditView::SetParaFormat
- AFXRICH/CRichEditView::TextNotFound
- AFXRICH/CRichEditView::GetClipboardData
- AFXRICH/CRichEditView::GetContextMenu
- AFXRICH/CRichEditView::IsSelected
- AFXRICH/CRichEditView::OnFindNext
- AFXRICH/CRichEditView::OnInitialUpdate
- AFXRICH/CRichEditView::OnPasteNativeObject
- AFXRICH/CRichEditView::OnPrinterChanged
- AFXRICH/CRichEditView::OnReplaceAll
- AFXRICH/CRichEditView::OnReplaceSel
- AFXRICH/CRichEditView::OnTextNotFound
- AFXRICH/CRichEditView::QueryAcceptData
- AFXRICH/CRichEditView::WrapChanged
- AFXRICH/CRichEditView::m_nBulletIndent
- AFXRICH/CRichEditView::m_nWordWrap
helpviewer_keywords:
- CRichEditView [MFC], CRichEditView
- CRichEditView [MFC], AdjustDialogPosition
- CRichEditView [MFC], CanPaste
- CRichEditView [MFC], DoPaste
- CRichEditView [MFC], FindText
- CRichEditView [MFC], FindTextSimple
- CRichEditView [MFC], GetCharFormatSelection
- CRichEditView [MFC], GetDocument
- CRichEditView [MFC], GetInPlaceActiveItem
- CRichEditView [MFC], GetMargins
- CRichEditView [MFC], GetPageRect
- CRichEditView [MFC], GetPaperSize
- CRichEditView [MFC], GetParaFormatSelection
- CRichEditView [MFC], GetPrintRect
- CRichEditView [MFC], GetPrintWidth
- CRichEditView [MFC], GetRichEditCtrl
- CRichEditView [MFC], GetSelectedItem
- CRichEditView [MFC], GetTextLength
- CRichEditView [MFC], GetTextLengthEx
- CRichEditView [MFC], InsertFileAsObject
- CRichEditView [MFC], InsertItem
- CRichEditView [MFC], IsRichEditFormat
- CRichEditView [MFC], OnCharEffect
- CRichEditView [MFC], OnParaAlign
- CRichEditView [MFC], OnUpdateCharEffect
- CRichEditView [MFC], OnUpdateParaAlign
- CRichEditView [MFC], PrintInsideRect
- CRichEditView [MFC], PrintPage
- CRichEditView [MFC], SetCharFormat
- CRichEditView [MFC], SetMargins
- CRichEditView [MFC], SetPaperSize
- CRichEditView [MFC], SetParaFormat
- CRichEditView [MFC], TextNotFound
- CRichEditView [MFC], GetClipboardData
- CRichEditView [MFC], GetContextMenu
- CRichEditView [MFC], IsSelected
- CRichEditView [MFC], OnFindNext
- CRichEditView [MFC], OnInitialUpdate
- CRichEditView [MFC], OnPasteNativeObject
- CRichEditView [MFC], OnPrinterChanged
- CRichEditView [MFC], OnReplaceAll
- CRichEditView [MFC], OnReplaceSel
- CRichEditView [MFC], OnTextNotFound
- CRichEditView [MFC], QueryAcceptData
- CRichEditView [MFC], WrapChanged
- CRichEditView [MFC], m_nBulletIndent
- CRichEditView [MFC], m_nWordWrap
ms.assetid: bd576b10-4cc0-4050-8f76-e1a0548411e4
ms.openlocfilehash: b32578cc3c9ad4f7a89b8ee76449259c0fa0b43b
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741509"
---
# <a name="cricheditview-class"></a>CRichEditView クラス

[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)と[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)を使用すると、は、MFC のドキュメントビューアーキテクチャのコンテキスト内で、リッチエディットコントロールの機能を提供します。

## <a name="syntax"></a>構文

```
class CRichEditView : public CCtrlView
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CRichEditView:: CRichEditView](#cricheditview)|`CRichEditView` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CRichEditView:: AdjustDialogPosition](#adjustdialogposition)|ダイアログボックスを移動して、現在の選択範囲を隠すことができないようにします。|
|[CRichEditView:: CanPaste](#canpaste)|リッチエディットビューに貼り付けることができるデータがクリップボードに含まれているかどうかを示します。|
|[CRichEditView::D oPaste](#dopaste)|OLE 項目をこのリッチエディットビューに貼り付けます。|
|[CRichEditView:: FindText](#findtext)|待機カーソルを呼び出して、指定されたテキストを検索します。|
|[CRichEditView:: FindTextSimple](#findtextsimple)|指定されたテキストを検索します。|
|[CRichEditView:: GetCharFormatSelection](#getcharformatselection)|現在の選択範囲の文字書式属性を取得します。|
|[CRichEditView:: GetDocument](#getdocument)|関連する[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)へのポインターを取得します。|
|[CRichEditView:: Getinplace Activeitem](#getinplaceactiveitem)|リッチエディットビューで現在アクティブになっている OLE 項目を取得します。|
|[CRichEditView:: GetMargins](#getmargins)|このリッチエディットビューの余白を取得します。|
|[CRichEditView::GetPageRect](#getpagerect)|このリッチエディットビューのページ四角形を取得します。|
|[CRichEditView:: GetPaperSize](#getpapersize)|このリッチエディットビューの用紙サイズを取得します。|
|[CRichEditView:: GetParaFormatSelection](#getparaformatselection)|現在の選択範囲の段落書式属性を取得します。|
|[CRichEditView:: GetPrintRect](#getprintrect)|このリッチエディットビューの印刷四角形を取得します。|
|[CRichEditView::GetPrintWidth](#getprintwidth)|このリッチエディットビューの印刷幅を取得します。|
|[CRichEditView:: GetRichEditCtrl](#getricheditctrl)|リッチエディットコントロールを取得します。|
|[CRichEditView:: GetSelectedItem](#getselecteditem)|リッチエディットビューから選択された項目を取得します。|
|[CRichEditView:: GetTextLength](#gettextlength)|リッチエディットビューのテキストの長さを取得します。|
|[CRichEditView:: GetTextLengthEx](#gettextlengthex)|リッチエディットビューの文字数またはバイト数を取得します。 長さを決定する方法の展開されたフラグの一覧。|
|[CRichEditView:: InsertFileAsObject](#insertfileasobject)|OLE 項目としてファイルを挿入します。|
|[CRichEditView:: InsertItem](#insertitem)|新しい項目を OLE 項目として挿入します。|
|[CRichEditView:: IsRichEditFormat](#isricheditformat)|クリップボードにリッチな編集またはテキスト形式のデータが含まれているかどうかを示します。|
|[CRichEditView:: OnCharEffect](#onchareffect)|現在の選択範囲の文字書式を切り替えます。|
|[CRichEditView:: OnParaAlign](#onparaalign)|段落の配置を変更します。|
|[CRichEditView:: OnUpdateCharEffect](#onupdatechareffect)|文字のパブリックメンバー関数のコマンド UI を更新します。|
|[CRichEditView:: OnUpdateParaAlign](#onupdateparaalign)|段落のパブリックメンバー関数のコマンド UI を更新します。|
|[CRichEditView::P rintInsideRect](#printinsiderect)|指定した四角形内の指定したテキストの書式を設定します。|
|[CRichEditView::P rintPage](#printpage)|指定したページ内の指定したテキストの書式を設定します。|
|[CRichEditView:: SetCharFormat](#setcharformat)|現在の選択範囲の文字書式属性を設定します。|
|[CRichEditView:: SetMargins](#setmargins)|このリッチエディットビューの余白を設定します。|
|[CRichEditView:: SetPaperSize](#setpapersize)|このリッチエディットビューの用紙サイズを設定します。|
|[CRichEditView:: SetParaFormat](#setparaformat)|現在の選択範囲の段落書式属性を設定します。|
|[CRichEditView:: TextNotFound](#textnotfound)|コントロールの内部検索状態をリセットします。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CRichEditView:: GetClipboardData](#getclipboarddata)|リッチエディットビューの範囲のクリップボードオブジェクトを取得します。|
|[CRichEditView:: GetContextMenu](#getcontextmenu)|右マウスボタンを押したときに使用するコンテキストメニューを取得します。|
|[CRichEditView:: IsSelected](#isselected)|指定した OLE 項目が選択されているかどうかを示します。|
|[CRichEditView:: OnFindNext](#onfindnext)|次に出現する部分文字列を検索します。|
|[CRichEditView:: OnInitialUpdate](#oninitialupdate)|ビューがドキュメントに最初にアタッチされたときに、そのビューを更新します。|
|[CRichEditView:: OnPasteNativeObject](#onpastenativeobject)|OLE 項目からネイティブデータを取得します。|
|[CRichEditView:: Onプリンターが変更されました](#onprinterchanged)|指定されたデバイスに印刷特性を設定します。|
|[CRichEditView:: OnReplaceAll](#onreplaceall)|指定した文字列のすべての出現箇所を新しい文字列に置換します。|
|[CRichEditView:: OnReplaceSel](#onreplacesel)|現在の選択範囲を置き換えます。|
|[CRichEditView::OnTextNotFound](#ontextnotfound)|要求されたテキストが見つからなかったことを示すユーザー通知を処理します。|
|[CRichEditView:: QueryAcceptData](#queryacceptdata)|のデータについての`IDataObject`クエリを行います。|
|[CRichEditView:: WrapChanged](#wrapchanged)|の`m_nWordWrap`値に基づいて、このリッチエディットビューのターゲット出力デバイスを調整します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CRichEditView:: m_nBulletIndent](#m_nbulletindent)|箇条書きのインデントの量を示します。|
|[CRichEditView:: m_nWordWrap](#m_nwordwrap)|右端での折り返しの制約を示します。|

## <a name="remarks"></a>Remarks

"リッチエディットコントロール" は、ユーザーがテキストを入力して編集できるウィンドウです。 テキストには、文字や段落の書式を割り当てることができ、埋め込み OLE オブジェクトを含めることができます。 リッチエディットコントロールは、テキストを書式設定するためのプログラミングインターフェイスを提供します。 ただし、アプリケーションは、ユーザーが書式設定操作を使用できるようにするために必要なユーザーインターフェイスコンポーネントを実装する必要があります。

`CRichEditView`テキストのテキストと書式設定の特性を維持します。 `CRichEditDoc`ビュー内の OLE クライアントアイテムの一覧を保持します。 `CRichEditCntrItem`OLE クライアントアイテムへのコンテナー側のアクセスを提供します。

この Windows コモンコントロール (および[CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md)および関連クラス) は、windows 95/98 および windows NT バージョン3.51 以降で実行されているプログラムに対してのみ使用できます。

MFC アプリケーションでリッチエディットビューを使用する例については、「[ワードパッド](../../overview/visual-cpp-samples.md)サンプルアプリケーション」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CView](../../mfc/reference/cview-class.md)

[CCtrlView](../../mfc/reference/cctrlview-class.md)

`CRichEditView`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrich

##  <a name="adjustdialogposition"></a>CRichEditView:: AdjustDialogPosition

現在の選択内容が不明瞭にならないように、この関数を呼び出して、指定されたダイアログボックスを移動します。

```
void AdjustDialogPosition(CDialog* pDlg);
```

### <a name="parameters"></a>パラメーター

*pDlg*<br/>
オブジェクトへの`CDialog`ポインター。

##  <a name="canpaste"></a>CRichEditView:: CanPaste

このリッチエディットビューに貼り付けることができる情報がクリップボードに含まれているかどうかを判断するには、この関数を呼び出します。

```
BOOL CanPaste() const;
```

### <a name="return-value"></a>戻り値

リッチエディットビューが受け入れることができる形式のデータがクリップボードに含まれている場合は0以外の。それ以外の場合は0です。

##  <a name="cricheditview"></a>CRichEditView:: CRichEditView

オブジェクトを作成するには`CRichEditView` 、この関数を呼び出します。

```
CRichEditView();
```

##  <a name="dopaste"></a>CRichEditView::D oPaste

*Dataobj*の OLE 項目をこのリッチエディットドキュメント/ビューに貼り付けるには、この関数を呼び出します。

```
void DoPaste(
    COleDataObject& dataobj,
    CLIPFORMAT cf,
    HMETAFILEPICT hMetaPict);
```

### <a name="parameters"></a>パラメーター

*dataobj*<br/>
貼り付けるデータを格納している[COleDataObject](../../mfc/reference/coledataobject-class.md) 。

*cf*<br/>
目的のクリップボード形式。

*hMetaPict*<br/>
貼り付ける項目を表すメタファイル。

### <a name="remarks"></a>Remarks

フレームワークは、 [Queryacceptdata](#queryacceptdata)の既定の実装の一部としてこの関数を呼び出します。

この関数は、[特殊な貼り付け] のハンドラーの結果に基づいて、貼り付けの種類を決定します。 *Cf*が0の場合、新しい項目は現在のアイコン表示を使用します。 *Cf*が0以外で、 *hMetaPict*が NULL でない場合、新しい項目はその表現に*hMetaPict*を使用します。

##  <a name="findtext"></a>CRichEditView:: FindText

この関数を呼び出して、指定したテキストを検索し、現在の選択範囲として設定します。

```
BOOL FindText(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszFind*<br/>
検索対象の文字列が含まれています。

*bCase*<br/>
検索で大文字と小文字を区別するかどうかを示します。

*bWord*<br/>
検索が単語の一部ではなく単語全体に一致する必要があるかどうかを示します。

*bNext*<br/>
検索の方向を示します。 TRUE の場合、検索方向はバッファーの末尾に向かっています。 FALSE の場合、検索方向はバッファーの先頭に向かっています。

### <a name="return-value"></a>戻り値

*LpszFind*テキストが見つかった場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

この関数は、検索操作中に待機カーソルを表示します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#151](../../mfc/codesnippet/cpp/cricheditview-class_1.cpp)]

##  <a name="findtextsimple"></a>CRichEditView:: FindTextSimple

この関数を呼び出して、指定したテキストを検索し、現在の選択範囲として設定します。

```
BOOL FindTextSimple(
    LPCTSTR lpszFind,
    BOOL bCase = TRUE,
    BOOL bWord = TRUE,
    BOOL bNext = TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszFind*<br/>
検索対象の文字列が含まれています。

*bCase*<br/>
検索で大文字と小文字を区別するかどうかを示します。

*bWord*<br/>
検索が単語の一部ではなく単語全体に一致する必要があるかどうかを示します。

*bNext*<br/>
検索の方向を示します。 TRUE の場合、検索方向はバッファーの末尾に向かっています。 FALSE の場合、検索方向はバッファーの先頭に向かっています。

### <a name="return-value"></a>戻り値

*LpszFind*テキストが見つかった場合は0以外の。それ以外の場合は0です。

### <a name="example"></a>例

  [CRichEditView:: FindText](#findtext)の例を参照してください。

##  <a name="getcharformatselection"></a>CRichEditView:: GetCharFormatSelection

現在の選択範囲の文字書式属性を取得するには、この関数を呼び出します。

```
CHARFORMAT2& GetCharFormatSelection();
```

### <a name="return-value"></a>戻り値

現在の選択範囲の文字書式属性を格納している[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)構造体。

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の[EM_GETCHARFORMAT](/windows/win32/Controls/em-getcharformat)メッセージと[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)構造体を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="getclipboarddata"></a>CRichEditView:: GetClipboardData

フレームワークは、 [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)の処理の一部としてこの関数を呼び出します。

```
virtual HRESULT GetClipboardData(
    CHARRANGE* lpchrg,
    DWORD dwReco,
    LPDATAOBJECT lpRichDataObj,
    LPDATAOBJECT* lplpdataobj);
```

### <a name="parameters"></a>パラメーター

*lpchrg*<br/>
*Lplpdataobj*によって指定されたデータオブジェクトにコピーする文字の範囲 (および OLE 項目) を指定する[charrange](/windows/win32/api/richedit/ns-richedit-charrange)構造体へのポインター。

*dwReco*<br/>
クリップボード操作フラグ。 次のいずれかの値を指定できます。

- RECO_COPY をクリップボードにコピーします。

- RECO_CUT をクリップボードに貼り付けます。

- RECO_DRAG のドラッグ操作 (ドラッグアンドドロップ)。

- RECO_DROP Drop 操作 (ドラッグアンドドロップ)。

- RECO_PASTE クリップボードから貼り付けます。

*lpRichDataObj*<br/>
リッチエディットコントロールからのクリップボードデータを格納する[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)オブジェクトへのポインター ( [IRichEditOle:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata))。

*lplpdataobj*<br/>
*Lpchrg*パラメーターで指定された範囲を`IDataObject`表すオブジェクトのアドレスを受け取るポインター変数へのポインター。 エラーが返された場合、 *lplpdataobj*の値は無視されます。

### <a name="return-value"></a>戻り値

操作が成功したことを報告する HRESULT 値。 HRESULT の詳細については、「Windows SDK の[COM エラーコードの構造](/windows/win32/com/structure-of-com-error-codes)」を参照してください。

### <a name="remarks"></a>Remarks

戻り値が成功を示す場合`IRichEditOleCallback::GetClipboardData`は、 `IDataObject` *lplpdataobj*によってアクセスされたを返します。それ以外の場合は、 *lpRichDataObj*によってアクセスされたを返します。 独自のクリップボードデータを提供するには、この関数をオーバーライドします。 この関数の既定の実装では、E_NOTIMPL が返されます。

これは高度なオーバーライド可能です。

詳細については、Windows SDK の「 [IRichEditOle:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditole-getclipboarddata)、 [IRichEditOleCallback:: GetClipboardData](/windows/win32/api/richole/nf-richole-iricheditolecallback-getclipboarddata)、および[charrange](/windows/win32/api/richedit/ns-richedit-charrange) 」を参照してください。また、Windows SDK の[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)を参照してください。

##  <a name="getcontextmenu"></a>  CRichEditView::GetContextMenu

フレームワークは、 [IRichEditOleCallback:: GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu)の処理の一部としてこの関数を呼び出します。

```
virtual HMENU GetContextMenu(
    WORD seltyp,
    LPOLEOBJECT lpoleobj,
    CHARRANGE* lpchrg);
```

### <a name="parameters"></a>パラメーター

*seltyp*<br/>
選択の種類。 選択の種類の値については、「解説」を参照してください。

*lpoleobj*<br/>
選択範囲に`OLEOBJECT` 1 つ以上の ole 項目が含まれている場合に、最初に選択された ole オブジェクトを指定する構造体へのポインター。 選択範囲に項目が含まれていない場合、 *lpoleobj*は NULL になります。 構造`OLEOBJECT`体は、OLE オブジェクト v テーブルへのポインターを保持します。

*lpchrg*<br/>
現在の選択範囲を含む[Charrange](/windows/win32/api/richedit/ns-richedit-charrange)構造体へのポインター。

### <a name="return-value"></a>戻り値

コンテキストメニューへのハンドル。

### <a name="remarks"></a>Remarks

この関数は、マウスの右ボタンのダウン処理の一般的な部分です。

選択の種類は、次のフラグの任意の組み合わせにすることができます。

- SEL_EMPTY は、現在選択されていないことを示します。

- SEL_TEXT は、現在の選択範囲にテキストが含まれていることを示します。

- SEL_OBJECT は、現在の選択範囲に少なくとも1つの OLE 項目が含まれていることを示します。

- SEL_MULTICHAR は、現在の選択範囲に1文字以上のテキストが含まれていることを示します。

- SEL_MULTIOBJECT は、現在の選択範囲に複数の OLE オブジェクトが含まれていることを示します。

既定の実装では、NULL が返されます。 これは高度なオーバーライド可能です。

詳細については、Windows SDK の「 [IRichEditOleCallback:: GetContextMenu](/windows/win32/api/richole/nf-richole-iricheditolecallback-getcontextmenu) 」と「 [charrange](/windows/win32/api/richedit/ns-richedit-charrange) 」を参照してください。

##  <a name="getdocument"></a>CRichEditView:: GetDocument

このビューに関連付けられている`CRichEditDoc`へのポインターを取得するには、この関数を呼び出します。

```
CRichEditDoc* GetDocument() const;
```

### <a name="return-value"></a>戻り値

`CRichEditView`オブジェクトに関連付けられている[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)オブジェクトへのポインター。

##  <a name="getinplaceactiveitem"></a>CRichEditView:: Getinplace Activeitem

この`CRichEditView`オブジェクトで現在アクティブになっている OLE 項目を取得するには、この関数を呼び出します。

```
CRichEditCntrItem* GetInPlaceActiveItem() const;
```

### <a name="return-value"></a>戻り値

このリッチエディットビューのインプレースアクティブ[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)オブジェクトへのポインター。現在埋め込み先のアクティブな状態に OLE 項目がない場合は NULL です。

##  <a name="getmargins"></a>CRichEditView:: GetMargins

印刷で使用されている現在の余白を取得します。

```
CRect GetMargins() const;
```

### <a name="return-value"></a>戻り値

印刷で使用される余白 (MM_TWIPS で測定)。

##  <a name="getpagerect"></a>  CRichEditView::GetPageRect

印刷で使用されるページの寸法を取得します。

```
CRect GetPageRect() const;
```

### <a name="return-value"></a>戻り値

印刷で使用されるページの境界は、MM_TWIPS で計測されます。

### <a name="remarks"></a>Remarks

この値は、用紙サイズに基づいています。

##  <a name="getpapersize"></a>CRichEditView:: GetPaperSize

現在の用紙サイズを取得するには、この関数を呼び出します。

```
CSize GetPaperSize() const;
```

### <a name="return-value"></a>戻り値

印刷で使用される用紙のサイズ (MM_TWIPS で測定)。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#153](../../mfc/codesnippet/cpp/cricheditview-class_3.cpp)]

##  <a name="getparaformatselection"></a>CRichEditView:: GetParaFormatSelection

現在の選択範囲の段落書式属性を取得するには、この関数を呼び出します。

```
PARAFORMAT2& GetParaFormatSelection();
```

### <a name="return-value"></a>戻り値

現在の選択範囲の段落書式属性を格納している[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)構造体。

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [EM_GETPARAFORMAT](/windows/win32/Controls/em-getparaformat) Message and [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) structure」を参照してください。

##  <a name="getprintrect"></a>CRichEditView:: GetPrintRect

この関数を呼び出して、ページの四角形内の印刷領域の境界を取得します。

```
CRect GetPrintRect() const;
```

### <a name="return-value"></a>戻り値

印刷で使用されるイメージ領域の境界 (MM_TWIPS で測定)。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#154](../../mfc/codesnippet/cpp/cricheditview-class_4.cpp)]

##  <a name="getprintwidth"></a>CRichEditView:: GetPrintWidth

印刷領域の幅を決定するには、この関数を呼び出します。

```
int GetPrintWidth() const;
```

### <a name="return-value"></a>戻り値

印刷領域の幅。 MM_TWIPS で計測されます。

##  <a name="getricheditctrl"></a>  CRichEditView::GetRichEditCtrl

この関数を呼び出して、`CRichEditView` オブジェクトに関連付けられている [CRichEditCtrl](../../mfc/reference/cricheditctrl-class.md) オブジェクトを取得します。

```
CRichEditCtrl& GetRichEditCtrl() const;
```

### <a name="return-value"></a>戻り値

このビューのオブジェクト。 `CRichEditCtrl`

### <a name="example"></a>例

  [CRichEditView:: FindText](#findtext)の例を参照してください。

##  <a name="getselecteditem"></a>  CRichEditView::GetSelectedItem

この`CRichEditCntrItem` オブジェクト`CRichEditView`で現在選択されている OLE 項目 (オブジェクト) を取得するには、この関数を呼び出します。

```
CRichEditCntrItem* GetSelectedItem() const;
```

### <a name="return-value"></a>戻り値

`CRichEditView` オブジェクトで選択されている [CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md) オブジェクトへのポインター。このビューで項目が選択されていない場合は NULL です。

##  <a name="gettextlength"></a>  CRichEditView::GetTextLength

この`CRichEditView`オブジェクトのテキストの長さを取得するには、この関数を呼び出します。

```
long GetTextLength() const;
```

### <a name="return-value"></a>戻り値

この`CRichEditView`オブジェクト内のテキストの長さ。

##  <a name="gettextlengthex"></a>  CRichEditView::GetTextLengthEx

このメンバー関数を呼び出して、この`CRichEditView`オブジェクト内のテキストの長さを計算します。

```
long GetTextLengthEx(
    DWORD dwFlags,
    UINT uCodePage = -1) const;
```

### <a name="parameters"></a>パラメーター

*dwFlags*<br/>
テキストの長さを決定するために使用するメソッドを指定する値。 このメンバーは、Windows SDK で説明されている[GETTEXTLENGTHEX](/windows/win32/api/richedit/ns-richedit-gettextlengthex)の flags メンバーに示されている1つ以上の値にすることができます。

*uCodePage*<br/>
翻訳用のコードページ (ANSI コードページの場合は CP_ACP、Unicode の場合は 1200)。

### <a name="return-value"></a>戻り値

エディットコントロールの文字数またはバイト数。 互換性のないフラグが*dwFlags*で設定されている場合、このメンバー関数は E_INVALIDARG を返します。

### <a name="remarks"></a>Remarks

`GetTextLengthEx`テキストの長さを確認するための追加の方法を提供します。 リッチエディット2.0 機能がサポートされています。 詳細については、「Windows SDK の[リッチエディットコントロールについ](/windows/win32/Controls/about-rich-edit-controls)て」を参照してください。

##  <a name="insertfileasobject"></a>CRichEditView:: InsertFileAsObject

[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)オブジェクトとして指定されたファイルをリッチエディットビューに挿入するには、この関数を呼び出します。

```
void InsertFileAsObject(LPCTSTR lpszFileName);
```

### <a name="parameters"></a>パラメーター

*lpszFileName*<br/>
挿入するファイルの名前を格納している文字列。

##  <a name="insertitem"></a>CRichEditView:: InsertItem

リッチエディットビューに[CRichEditCntrItem](../../mfc/reference/cricheditcntritem-class.md)オブジェクトを挿入するには、この関数を呼び出します。

```
HRESULT InsertItem(CRichEditCntrItem* pItem);
```

### <a name="parameters"></a>パラメーター

*pItem*<br/>
挿入する項目へのポインター。

### <a name="return-value"></a>戻り値

挿入が成功したかどうかを示す HRESULT 値。

### <a name="remarks"></a>Remarks

HRESULT の詳細については、「Windows SDK の[COM エラーコードの構造](/windows/win32/com/structure-of-com-error-codes)」を参照してください。

##  <a name="isricheditformat"></a>CRichEditView:: IsRichEditFormat

この関数を呼び出して、 *cf*がクリップボード形式であるかどうかを確認します。これは、テキスト、リッチテキスト、または OLE 項目を含むリッチテキストです。

```
static BOOL AFX_CDECL IsRichEditFormat(CLIPFORMAT cf);
```

### <a name="parameters"></a>パラメーター

*cf*<br/>
目的のクリップボード形式。

### <a name="return-value"></a>戻り値

*Cf*がリッチエディットテキストクリップボード形式の場合は0以外の。

##  <a name="isselected"></a>CRichEditView:: IsSelected

この関数を呼び出して、指定した OLE 項目がこのビューで現在選択されているかどうかを確認します。

```
virtual BOOL IsSelected(const CObject* pDocItem) const;
```

### <a name="parameters"></a>パラメーター

*pDocItem*<br/>
ビュー内のオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

オブジェクトが選択されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

派生ビュークラスに OLE 項目の選択を処理する別のメソッドがある場合は、この関数をオーバーライドします。

##  <a name="m_nbulletindent"></a>CRichEditView:: m_nBulletIndent

リスト内の箇条書き項目のインデント。既定では、720単位は1/2 インチです。

```
int m_nBulletIndent;
```

##  <a name="m_nwordwrap"></a>CRichEditView:: m_nWordWrap

このリッチエディットビューの折り返しの種類を示します。

```
int m_nWordWrap;
```

### <a name="remarks"></a>Remarks

次のいずれかの値です。

- `WrapNone`単語の自動折り返しがないことを示します。

- `WrapToWindow`ウィンドウの幅に基づいて単語の折り返しを示します。

- `WrapToTargetDevice`ターゲットデバイスの特性に基づいて、単語の折り返しを示します。

### <a name="example"></a>例

  [CRichEditView:: WrapChanged](#wrapchanged)の例を参照してください。

##  <a name="onchareffect"></a>CRichEditView:: OnCharEffect

現在の選択範囲の文字書式設定効果を切り替えるには、この関数を呼び出します。

```
void OnCharEffect(
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>パラメーター

*dwMask*<br/>
現在の選択範囲で変更する文字書式設定効果。

*dwEffect*<br/>
切り替えの対象となる文字書式設定効果の一覧。

### <a name="remarks"></a>Remarks

この関数を呼び出すたびに、現在の選択範囲に対して指定された書式設定効果が切り替わります。

*DwMask*および*dwEffect*パラメーターとその可能性のある値の詳細については、Windows SDK の[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)の対応するデータメンバーを参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#155](../../mfc/codesnippet/cpp/cricheditview-class_5.cpp)]

##  <a name="onfindnext"></a>CRichEditView:: OnFindNext

[検索と置換] ダイアログボックスからコマンドを処理するときに、フレームワークによって呼び出されます。

```
virtual void OnFindNext(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>パラメーター

*lpszFind*<br/>
検索する文字列。

*bNext*<br/>
検索する方向:TRUE は停止していることを示します。FALSE、上。

*bCase*<br/>
検索で大文字と小文字を区別するかどうかを示します。

*bWord*<br/>
検索で単語全体を照合するかどうかを示します。

### <a name="remarks"></a>Remarks

内のテキストを検索するには`CRichEditView`、この関数を呼び出します。 派生ビュークラスの検索特性を変更するには、この関数をオーバーライドします。

##  <a name="oninitialupdate"></a>CRichEditView:: OnInitialUpdate

最初にビューがドキュメントにアタッチされた後、最初にビューが表示される前に、フレームワークによって呼び出されます。

```
virtual void OnInitialUpdate();
```

### <a name="remarks"></a>Remarks

この関数の既定の実装では、ヒント情報を指定せずに[CView:: OnUpdate](../../mfc/reference/cview-class.md#onupdate)メンバー関数を呼び出します (つまり、 *lhint*パラメーターには0、 *PHINT*パラメーターには NULL を使用します)。 ドキュメントに関する情報を必要とする1回限りの初期化を実行するには、この関数をオーバーライドします。 たとえば、アプリケーションに固定サイズのドキュメントがある場合、この関数を使用すると、ドキュメントのサイズに基づいて、ビューのスクロール制限を初期化できます。 アプリケーションで可変サイズのドキュメントがサポートされ`OnUpdate`ている場合は、を使用して、ドキュメントが変更されるたびにスクロール制限を更新します。

### <a name="example"></a>例

  [CRichEditView:: m_nWordWrap](#m_nwordwrap)の例を参照してください。

##  <a name="onpastenativeobject"></a>CRichEditView:: OnPasteNativeObject

埋め込みアイテムからネイティブデータを読み込むには、この関数を使用します。

```
virtual BOOL OnPasteNativeObject(LPSTORAGE lpStg);
```

### <a name="parameters"></a>パラメーター

*lpStg*<br/>
[IStorage](/windows/win32/api/objidl/nn-objidl-istorage)オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

通常、これを行うには、`IStorage` の周囲に [COleStreamFile](../../mfc/reference/colestreamfile-class.md) を作成します。 は`COleStreamFile`アーカイブにアタッチでき、 [CObject:: Serialize](../../mfc/reference/cobject-class.md#serialize)はデータを読み込むために呼び出されます。

これは高度なオーバーライド可能です。

詳細については、Windows SDK の「 [IStorage](/windows/win32/api/objidl/nn-objidl-istorage) 」を参照してください。

##  <a name="onparaalign"></a>CRichEditView:: OnParaAlign

選択した段落の段落の配置を変更するには、この関数を呼び出します。

```
void OnParaAlign(WORD wAlign);
```

### <a name="parameters"></a>パラメーター

*wAlign*<br/>
目的の段落の配置。 次のいずれかの値です。

- PFA_LEFT 段落を左余白に揃えます。

- PFA_RIGHT 段落を右余白に揃えます。

- PFA_CENTER は、余白の間に段落を中央揃えで配置します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#156](../../mfc/codesnippet/cpp/cricheditview-class_6.cpp)]

##  <a name="onprinterchanged"></a>CRichEditView:: Onプリンターが変更されました

プリンターが変更されたときに、このリッチエディットビューの特性を変更するには、この関数をオーバーライドします。

```
virtual void OnPrinterChanged(const CDC& dcPrinter);
```

### <a name="parameters"></a>パラメーター

*dcPrinter*<br/>
新しいプリンターの[CDC](../../mfc/reference/cdc-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

既定の実装では、用紙サイズが出力デバイス (プリンター) の物理的な高さと幅に設定されます。 *Dcprinter*に関連付けられているデバイスコンテキストが存在しない場合、既定の実装では用紙サイズが11インチで8.5 に設定されます。

##  <a name="onreplaceall"></a>CRichEditView:: OnReplaceAll

[置換] ダイアログボックスのすべてのコマンドを処理するときに、フレームワークによって呼び出されます。

```
virtual void OnReplaceAll(
    LPCTSTR lpszFind,
    LPCTSTR lpszReplace,
    BOOL bCase,
    BOOL bWord);
```

### <a name="parameters"></a>パラメーター

*lpszFind*<br/>
置換されるテキスト。

*lpszReplace*<br/>
置換後のテキスト。

*bCase*<br/>
検索で大文字と小文字を区別するかどうかを示します。

*bWord*<br/>
検索で単語全体を選択する必要があるかどうかを示します。

### <a name="remarks"></a>Remarks

特定のテキストの出現箇所をすべて別の文字列に置換するには、この関数を呼び出します。 このビューの検索特性を変更するには、この関数をオーバーライドします。

### <a name="example"></a>例

  [CRichEditView:: FindText](#findtext)の例を参照してください。

##  <a name="onreplacesel"></a>CRichEditView:: OnReplaceSel

[置換] ダイアログボックスから [置換] コマンドを処理するときに、フレームワークによって呼び出されます。

```
virtual void OnReplaceSel(
    LPCTSTR lpszFind,
    BOOL bNext,
    BOOL bCase,
    BOOL bWord,
    LPCTSTR lpszReplace);
```

### <a name="parameters"></a>パラメーター

*lpszFind*<br/>
置換されるテキスト。

*bNext*<br/>
検索の方向を示します。TRUE はダウンしています。FALSE、上。

*bCase*<br/>
検索で大文字と小文字を区別するかどうかを示します。

*bWord*<br/>
検索で単語全体を選択する必要があるかどうかを示します。

*lpszReplace*<br/>
置換後のテキスト。

### <a name="remarks"></a>Remarks

特定のテキストの出現箇所を別の文字列に置き換えるには、この関数を呼び出します。 このビューの検索特性を変更するには、この関数をオーバーライドします。

##  <a name="ontextnotfound"></a>  CRichEditView::OnTextNotFound

検索が失敗するたびにフレームワークによって呼び出されます。

```
virtual void OnTextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>パラメーター

*lpszFind*<br/>
見つからなかったテキスト。

### <a name="remarks"></a>Remarks

[Messagebeep](/windows/win32/api/winuser/nf-winuser-messagebeep)からの出力通知を変更するには、この関数をオーバーライドします。

詳細については、「Windows SDK の[Messagebeep](/windows/win32/api/winuser/nf-winuser-messagebeep) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#157](../../mfc/codesnippet/cpp/cricheditview-class_7.cpp)]

##  <a name="onupdatechareffect"></a>CRichEditView:: OnUpdateCharEffect

フレームワークは、この関数を呼び出して、文字効果コマンドのコマンド UI を更新します。

```
void OnUpdateCharEffect(
    CCmdUI* pCmdUI,
    DWORD dwMask,
    DWORD dwEffect);
```

### <a name="parameters"></a>パラメーター

*pCmdUI*<br/>
[CCmdUI](../../mfc/reference/ccmdui-class.md)オブジェクトへのポインター。

*dwMask*<br/>
文字書式マスクを示します。

*dwEffect*<br/>
文字の書式設定の効果を示します。

### <a name="remarks"></a>Remarks

マスク*dwMask*は、どの文字書式属性を確認するかを指定します。 Flags *dwEffect*は、設定/クリアする文字書式属性を一覧表示します。

*DwMask*および*dwEffect*パラメーターとその可能性のある値の詳細については、Windows SDK の[CHARFORMAT](/windows/win32/api/richedit/ns-richedit-charformata)の対応するデータメンバーを参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#158](../../mfc/codesnippet/cpp/cricheditview-class_8.cpp)]

##  <a name="onupdateparaalign"></a>CRichEditView:: OnUpdateParaAlign

フレームワークは、この関数を呼び出して、段落効果コマンドのコマンド UI を更新します。

```
void OnUpdateParaAlign(
    CCmdUI* pCmdUI,
    WORD wAlign);
```

### <a name="parameters"></a>パラメーター

*pCmdUI*<br/>
[CCmdUI](../../mfc/reference/ccmdui-class.md)オブジェクトへのポインター。

*wAlign*<br/>
確認する段落の配置。 次のいずれかの値です。

- PFA_LEFT 段落を左余白に揃えます。

- PFA_RIGHT 段落を右余白に揃えます。

- PFA_CENTER は、余白の間に段落を中央揃えで配置します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#159](../../mfc/codesnippet/cpp/cricheditview-class_9.cpp)]

##  <a name="printinsiderect"></a>CRichEditView::P rintInsideRect

この関数を呼び出して、リッチエディットコントロールのテキスト範囲を、 *pDC*で指定されたデバイスの*rectLayout*内に収まるように書式設定します。

```
long PrintInsideRect(
    CDC* pDC,
    RECT& rectLayout,
    long nIndexStart,
    long nIndexStop,
    BOOL bOutput);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
出力領域のデバイスコンテキストへのポインター。

*rectLayout*<br/>
出力領域を定義する[RECT](/windows/win32/api/windef/ns-windef-rect)または[CRect](../../atl-mfc-shared/reference/crect-class.md) 。

*nIndexStart*<br/>
書式設定する最初の文字の0から始まるインデックス。

*nIndexStop*<br/>
書式設定する最後の文字の0から始まるインデックス番号。

*bOutput*<br/>
テキストを表示するかどうかを示します。 FALSE の場合、テキストは測定されただけです。

### <a name="return-value"></a>戻り値

出力領域に1を加えた最後の文字のインデックス。

### <a name="remarks"></a>Remarks

通常、この呼び出しの後に[CRichEditCtrl::D isplayBand](../../mfc/reference/cricheditctrl-class.md#displayband)が呼び出され、出力が生成されます。

### <a name="example"></a>例

  [CRichEditView:: GetPaperSize](#getpapersize)の例を参照してください。

##  <a name="printpage"></a>CRichEditView::P rintPage

この関数を呼び出して、 *pDC*によって指定された出力デバイスのリッチエディットコントロールのテキスト範囲を書式設定します。

```
long PrintPage(
    CDC* pDC,
    long nIndexStart,
    long nIndexStop);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
ページ出力のデバイスコンテキストへのポインター。

*nIndexStart*<br/>
書式設定する最初の文字の0から始まるインデックス。

*nIndexStop*<br/>
書式設定する最後の文字の0から始まるインデックス番号。

### <a name="return-value"></a>戻り値

ページに収まる最後の文字のインデックスと1つのインデックス。

### <a name="remarks"></a>Remarks

各ページのレイアウトは、 [GetPageRect](#getpagerect)と[getprintrect](#getprintrect)によって制御されます。 通常、この呼び出しの後に[CRichEditCtrl::D isplayBand](../../mfc/reference/cricheditctrl-class.md#displayband)が呼び出され、出力が生成されます。

余白は、論理ページではなく、物理ページに対して相対的であることに注意してください。 そのため、多くのプリンターのページに印刷できない領域があるため、通常、余白が0の場合はテキストがクリップされます。 テキストのクリッピングを避けるには、印刷する前に[SetMargins](#setmargins)を呼び出し、適切な余白を設定する必要があります。

##  <a name="queryacceptdata"></a>  CRichEditView::QueryAcceptData

リッチエディットにオブジェクトを貼り付けるためにフレームワークによって呼び出されます。

```
virtual HRESULT QueryAcceptData(
    LPDATAOBJECT lpdataobj,
    CLIPFORMAT* lpcfFormat,
    DWORD dwReco,
    BOOL bReally,
    HGLOBAL hMetaFile);
```

### <a name="parameters"></a>パラメーター

*lpdataobj*<br/>
クエリを実行する[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)へのポインター。

*lpcfFormat*<br/>
許容されるデータ形式へのポインター。

*dwReco*<br/>
使用しません。

*同盟を締結*<br/>
貼り付け操作を続行するかどうかを示します。

*hMetaFile*<br/>
項目のアイコンを描画するために使用されるメタファイルへのハンドル。

### <a name="return-value"></a>戻り値

操作が成功したことを報告する HRESULT 値。

### <a name="remarks"></a>Remarks

この関数をオーバーライドして、派生ドキュメントクラスの COM 項目のさまざまな編成を処理します。 これは高度なオーバーライド可能です。

HRESULT と`IDataObject`の詳細については、Windows SDK の「 [COM エラーコード](/windows/win32/com/structure-of-com-error-codes)と[IDataObject](/windows/win32/api/objidl/nn-objidl-idataobject)の構造」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#160](../../mfc/codesnippet/cpp/cricheditview-class_10.cpp)]

##  <a name="setcharformat"></a>CRichEditView:: SetCharFormat

この`CRichEditView`オブジェクトの新しいテキストの文字書式属性を設定するには、この関数を呼び出します。

```
void SetCharFormat(CHARFORMAT2 cf);
```

### <a name="parameters"></a>パラメーター

*cf*<br/>
新しい既定の文字書式属性を含む[CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w)構造体。

### <a name="remarks"></a>Remarks

`dwMask` *Cf*のメンバーによって指定された属性のみが、この関数によって変更されます。

詳細については、Windows SDK の「 [EM_SETCHARFORMAT](/windows/win32/Controls/em-setcharformat) Message and [CHARFORMAT2](/windows/win32/api/richedit/ns-richedit-charformat2w) structure」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#152](../../mfc/codesnippet/cpp/cricheditview-class_2.cpp)]

##  <a name="setmargins"></a>CRichEditView:: SetMargins

このリッチエディットビューの印刷余白を設定するには、この関数を呼び出します。

```
void SetMargins(const CRect& rectMargin);
```

### <a name="parameters"></a>パラメーター

*rectMargin*<br/>
印刷用の新しい余白の値 (MM_TWIPS で測定)。

### <a name="remarks"></a>Remarks

[M_nWordWrap](#m_nwordwrap)が`WrapToTargetDevice`の場合、この関数を使用して印刷特性を調整した後、 [WrapChanged](#wrapchanged)を呼び出す必要があります。

[System.drawing.printing.printdocument.printpage>](#printpage)で使用される余白は、論理ページではなく、物理ページに対する相対パスであることに注意してください。 そのため、多くのプリンターのページに印刷できない領域があるため、通常、余白が0の場合はテキストがクリップされます。 テキストがクリッピングされないようにするに`SetMargins`は、印刷する前に [使用] を呼び出して、適切なプリンターの余白を設定する必要があります。

### <a name="example"></a>例

  [CRichEditView:: GetPaperSize](#getpapersize)の例を参照してください。

##  <a name="setpapersize"></a>CRichEditView:: SetPaperSize

このリッチエディットビューを印刷するための用紙サイズを設定するには、この関数を呼び出します。

```
void SetPaperSize(CSize sizePaper);
```

### <a name="parameters"></a>パラメーター

*sizePaper*<br/>
印刷用の新しい用紙サイズ値 (MM_TWIPS で測定)。

### <a name="remarks"></a>Remarks

[M_nWordWrap](#m_nwordwrap)が`WrapToTargetDevice`の場合、この関数を使用して印刷特性を調整した後、 [WrapChanged](#wrapchanged)を呼び出す必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#161](../../mfc/codesnippet/cpp/cricheditview-class_11.cpp)]

##  <a name="setparaformat"></a>CRichEditView:: SetParaFormat

この`CRichEditView`オブジェクトの現在の選択項目の段落書式属性を設定するには、この関数を呼び出します。

```
BOOL SetParaFormat(PARAFORMAT2& pf);
```

### <a name="parameters"></a>パラメーター

*/pf*<br/>
新しい既定の段落書式属性を含む[PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2)構造体。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

この関数によって、 `dwMask` *pf*のメンバーによって指定された属性のみが変更されます。

詳細については、Windows SDK の「 [EM_SETPARAFORMAT](/windows/win32/Controls/em-setparaformat) Message and [PARAFORMAT2](/windows/win32/api/richedit/ns-richedit-paraformat2) structure」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#162](../../mfc/codesnippet/cpp/cricheditview-class_12.cpp)]

##  <a name="textnotfound"></a>CRichEditView:: TextNotFound

[FindText](#findtext)への呼び出しが失敗した後に、 [CRichEditView](../../mfc/reference/cricheditview-class.md)コントロールの内部検索状態をリセットするには、この関数を呼び出します。

```
void TextNotFound(LPCTSTR lpszFind);
```

### <a name="parameters"></a>パラメーター

*lpszFind*<br/>
に見つからなかったテキスト文字列が含まれています。

### <a name="remarks"></a>Remarks

このメソッドは、 [FindText](#findtext)への呼び出しが失敗した直後に呼び出され、コントロールの内部検索状態が適切にリセットされるようにすることをお勧めします。

*LpszFind*パラメーターには、 [FindText](#findtext)に指定された文字列と同じ内容を含める必要があります。 内部検索状態をリセットした後、このメソッドは指定された検索文字列を使用して[OnTextNotFound](#ontextnotfound)メソッドを呼び出します。

### <a name="example"></a>例

  [CRichEditView:: FindText](#findtext)の例を参照してください。

##  <a name="wrapchanged"></a>CRichEditView:: WrapChanged

印刷特性が変更された場合 ( [SetMargins](#setmargins)または[setpapersize](#setpapersize))、この関数を呼び出します。

```
virtual void WrapChanged();
```

### <a name="remarks"></a>Remarks

この関数をオーバーライドして、リッチエディットビューが[m_nWordWrap](#m_nwordwrap)の変更または印刷の特性 ( [Onプリンターが変更さ](#onprinterchanged)れた場合) にどのように応答するかを変更します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#163](../../mfc/codesnippet/cpp/cricheditview-class_13.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプルワードパッド](../../overview/visual-cpp-samples.md)<br/>
[CCtrlView クラス](../../mfc/reference/cctrlview-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CRichEditDoc クラス](../../mfc/reference/cricheditdoc-class.md)<br/>
[CRichEditCntrItem クラス](../../mfc/reference/cricheditcntritem-class.md)
