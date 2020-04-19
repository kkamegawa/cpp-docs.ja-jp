---
title: CEdit Class
ms.date: 09/12/2018
f1_keywords:
- CEdit
- AFXWIN/CEdit
- AFXWIN/CEdit::CEdit
- AFXWIN/CEdit::CanUndo
- AFXWIN/CEdit::CharFromPos
- AFXWIN/CEdit::Clear
- AFXWIN/CEdit::Copy
- AFXWIN/CEdit::Create
- AFXWIN/CEdit::Cut
- AFXWIN/CEdit::EmptyUndoBuffer
- AFXWIN/CEdit::FmtLines
- AFXWIN/CEdit::GetCueBanner
- AFXWIN/CEdit::GetFirstVisibleLine
- AFXWIN/CEdit::GetHandle
- AFXWIN/CEdit::GetHighlight
- AFXWIN/CEdit::GetLimitText
- AFXWIN/CEdit::GetLine
- AFXWIN/CEdit::GetLineCount
- AFXWIN/CEdit::GetMargins
- AFXWIN/CEdit::GetModify
- AFXWIN/CEdit::GetPasswordChar
- AFXWIN/CEdit::GetRect
- AFXWIN/CEdit::GetSel
- AFXWIN/CEdit::HideBalloonTip
- AFXWIN/CEdit::LimitText
- AFXWIN/CEdit::LineFromChar
- AFXWIN/CEdit::LineIndex
- AFXWIN/CEdit::LineLength
- AFXWIN/CEdit::LineScroll
- AFXWIN/CEdit::Paste
- AFXWIN/CEdit::PosFromChar
- AFXWIN/CEdit::ReplaceSel
- AFXWIN/CEdit::SetCueBanner
- AFXWIN/CEdit::SetHandle
- AFXWIN/CEdit::SetHighlight
- AFXWIN/CEdit::SetLimitText
- AFXWIN/CEdit::SetMargins
- AFXWIN/CEdit::SetModify
- AFXWIN/CEdit::SetPasswordChar
- AFXWIN/CEdit::SetReadOnly
- AFXWIN/CEdit::SetRect
- AFXWIN/CEdit::SetRectNP
- AFXWIN/CEdit::SetSel
- AFXWIN/CEdit::SetTabStops
- AFXWIN/CEdit::ShowBalloonTip
- AFXWIN/CEdit::Undo
helpviewer_keywords:
- CEdit [MFC], CEdit
- CEdit [MFC], CanUndo
- CEdit [MFC], CharFromPos
- CEdit [MFC], Clear
- CEdit [MFC], Copy
- CEdit [MFC], Create
- CEdit [MFC], Cut
- CEdit [MFC], EmptyUndoBuffer
- CEdit [MFC], FmtLines
- CEdit [MFC], GetCueBanner
- CEdit [MFC], GetFirstVisibleLine
- CEdit [MFC], GetHandle
- CEdit [MFC], GetHighlight
- CEdit [MFC], GetLimitText
- CEdit [MFC], GetLine
- CEdit [MFC], GetLineCount
- CEdit [MFC], GetMargins
- CEdit [MFC], GetModify
- CEdit [MFC], GetPasswordChar
- CEdit [MFC], GetRect
- CEdit [MFC], GetSel
- CEdit [MFC], HideBalloonTip
- CEdit [MFC], LimitText
- CEdit [MFC], LineFromChar
- CEdit [MFC], LineIndex
- CEdit [MFC], LineLength
- CEdit [MFC], LineScroll
- CEdit [MFC], Paste
- CEdit [MFC], PosFromChar
- CEdit [MFC], ReplaceSel
- CEdit [MFC], SetCueBanner
- CEdit [MFC], SetHandle
- CEdit [MFC], SetHighlight
- CEdit [MFC], SetLimitText
- CEdit [MFC], SetMargins
- CEdit [MFC], SetModify
- CEdit [MFC], SetPasswordChar
- CEdit [MFC], SetReadOnly
- CEdit [MFC], SetRect
- CEdit [MFC], SetRectNP
- CEdit [MFC], SetSel
- CEdit [MFC], SetTabStops
- CEdit [MFC], ShowBalloonTip
- CEdit [MFC], Undo
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
ms.openlocfilehash: 5ad8784f3bff999eec046aa91f52b1cd164764e5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506787"
---
# <a name="cedit-class"></a>CEdit Class

Windows のエディット コントロールの機能が用意されています。

## <a name="syntax"></a>構文

```
class CEdit : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CEdit::CEdit](#cedit)|コントロールオブジェクト`CEdit`を構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|エディットコントロール操作を元に戻すことができるかどうかを判断します。|
|[CEdit::CharFromPos](#charfrompos)|指定した位置に最も近い文字の行と文字のインデックスを取得します。|
|[CEdit::Clear](#clear)|エディットコントロール内の現在の選択項目 (存在する場合) を削除 (クリア) します。|
|[CEdit::Copy](#copy)|編集コントロール内の現在の選択項目 (存在する場合) を、CF_TEXT 形式でクリップボードにコピーします。|
|[CEdit::Create](#create)|Windows のエディットコントロールを作成し、 `CEdit`オブジェクトにアタッチします。|
|[CEdit::Cut](#cut)|エディットコントロール内の現在の選択項目 (存在する場合) を削除 (切り取り) し、削除されたテキストを CF_TEXT 形式でクリップボードにコピーします。|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|エディットコントロールの元に戻すフラグをリセット (クリア) します。|
|[CEdit::FmtLines](#fmtlines)|複数行のエディットコントロール内でソフト改行文字を含めるか無効にするかを設定します。|
|[CEdit::GetCueBanner](#getcuebanner)|コントロールが空でフォーカスがない場合に、エディットコントロールにテキストキュー (ヒント) として表示されるテキストを取得します。|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|エディットコントロールで最上位に表示される行を決定します。|
|[CEdit::GetHandle](#gethandle)|複数行のエディットコントロールに現在割り当てられているメモリのハンドルを取得します。|
|[CEdit::GetHighlight](#gethighlight)|現在の編集コントロールで強調表示されているテキスト範囲内の開始文字と終了文字のインデックスを取得します。|
|[CEdit::GetLimitText](#getlimittext)|この`CEdit`に格納できるテキストの最大量を取得します。|
|[CEdit::GetLine](#getline)|エディットコントロールからテキスト行を取得します。|
|[CEdit::GetLineCount](#getlinecount)|複数行のエディットコントロールの行数を取得します。|
|[CEdit::GetMargins](#getmargins)|この`CEdit`の左右の余白を取得します。|
|[CEdit::GetModify](#getmodify)|エディットコントロールの内容が変更されているかどうかを判断します。|
|[CEdit::GetPasswordChar](#getpasswordchar)|ユーザーがテキストを入力したときに編集コントロールに表示されるパスワード文字を取得します。|
|[CEdit::GetRect](#getrect)|エディットコントロールの書式指定用の四角形を取得します。|
|[CEdit::GetSel](#getsel)|エディットコントロール内の現在の選択範囲の最初と最後の文字位置を取得します。|
|[CEdit::HideBalloonTip](#hideballoontip)|現在の編集コントロールに関連付けられているバルーンヒントを非表示にします。|
|[CEdit::LimitText](#limittext)|ユーザーが編集コントロールに入力できるテキストの長さを制限します。|
|[CEdit::LineFromChar](#linefromchar)|指定した文字インデックスを含む行の行番号を取得します。|
|[CEdit::LineIndex](#lineindex)|複数行のエディットコントロール内の行の文字インデックスを取得します。|
|[CEdit::LineLength](#linelength)|エディットコントロールの行の長さを取得します。|
|[CEdit::LineScroll](#linescroll)|複数行のエディットコントロールのテキストをスクロールします。|
|[CEdit::Paste](#paste)|クリップボードのデータを現在のカーソル位置にあるエディットコントロールに挿入します。 データは、クリップボードに CF_TEXT 形式のデータが含まれている場合にのみ挿入されます。|
|[CEdit::PosFromChar](#posfromchar)|指定した文字インデックスの左上隅の座標を取得します。|
|[CEdit::ReplaceSel](#replacesel)|エディットコントロール内の現在の選択項目を指定したテキストに置き換えます。|
|[CEdit::SetCueBanner](#setcuebanner)|コントロールが空でフォーカスがない場合に、エディットコントロールにテキストキュー (ヒント) として表示されるテキストを設定します。|
|[CEdit::SetHandle](#sethandle)|複数行のエディットコントロールで使用されるローカルメモリのハンドルを設定します。|
|[CEdit::SetHighlight](#sethighlight)|現在の編集コントロールに表示されるテキストの範囲を強調表示します。|
|[CEdit::SetLimitText](#setlimittext)|この`CEdit`に含めることができるテキストの最大量を設定します。|
|[CEdit::SetMargins](#setmargins)|この`CEdit`の左右の余白を設定します。|
|[CEdit::SetModify](#setmodify)|エディットコントロールの変更フラグを設定または解除します。|
|[CEdit::SetPasswordChar](#setpasswordchar)|ユーザーがテキストを入力したときに編集コントロールに表示されるパスワード文字を設定または削除します。|
|[CEdit::SetReadOnly](#setreadonly)|エディットコントロールの読み取り専用の状態を設定します。|
|[CEdit::SetRect](#setrect)|複数行のエディットコントロールの書式指定用の四角形を設定し、コントロールを更新します。|
|[CEdit::SetRectNP](#setrectnp)|コントロールウィンドウを再描画せずに、複数行のエディットコントロールの書式指定用の四角形を設定します。|
|[CEdit::SetSel](#setsel)|エディットコントロール内の文字の範囲を選択します。|
|[CEdit::SetTabStops](#settabstops)|複数行のエディットコントロールでタブストップを設定します。|
|[CEdit::ShowBalloonTip](#showballoontip)|現在の編集コントロールに関連付けられているバルーンヒントを表示します。|
|[CEdit::Undo](#undo)|最後の編集コントロール操作を元に戻します。|

## <a name="remarks"></a>Remarks

エディットコントロールは、ユーザーがテキストを入力できる四角形の子ウィンドウです。

エディットコントロールは、ダイアログテンプレートから作成することも、コード内で直接作成することもできます。 どちらの場合も、最初にコンストラクター `CEdit`を呼び出して`CEdit`オブジェクトを構築し、次に[create](#create) member 関数を呼び出して Windows の`CEdit`エディットコントロールを作成し、それをオブジェクトにアタッチします。

構築は、から`CEdit`派生したクラスの1ステップのプロセスにすることができます。 派生クラスのコンストラクターを記述し、コンストラクター `Create`内からを呼び出します。

`CEdit`は、の重要`CWnd`な機能を継承します。 `CEdit`オブジェクトのテキストを設定および取得するには、 `CWnd`メンバー関数[SetWindowText](cwnd-class.md#setwindowtext)と[getwindowtext](cwnd-class.md#getwindowtext)を使用します。これにより、複数行のコントロールであっても、エディットコントロールの内容全体が設定または取得されます。 複数行コントロールのテキスト行は、"\r\n" 文字シーケンスで区切られます。 また、編集コントロールが複数行`CEdit`の場合は、 [getline](#getline)、 [SetSel](#setsel)、 [getline](#getsel)、および[replacesel](#replacesel)メンバー関数を呼び出すことによって、コントロールのテキストの一部を取得して設定します。

編集コントロールから親 (通常はから`CDialog`派生したクラス) に送信される Windows 通知メッセージを処理する場合は、各メッセージの親クラスにメッセージマップエントリとメッセージハンドラーメンバー関数を追加します。

各メッセージマップエントリには、次の形式があります。

  **ON_** _通知_ **(** _id_ **,** _memberFxn_ **)**

`memberFxn`は、通知を送信する編集コントロールの子ウィンドウ ID を指定します。は、通知を処理するために記述した親メンバー関数の名前です。`id`

親の関数プロトタイプは次のとおりです。

**afx_msg** void memberFxn **( );**

次に示すのは、潜在的なメッセージマップエントリの一覧と、親に送信される可能性のあるケースの説明です。

- ON_EN_CHANGE ユーザーがエディットコントロールでテキストを変更した可能性のあるアクションを実行しました。 EN_UPDATE 通知メッセージとは異なり、この通知メッセージは Windows がディスプレイを更新した後に送信されます。

- ON_EN_ERRSPACE 編集コントロールは、特定の要求を満たすのに十分なメモリを割り当てることができません。

- ON_EN_HSCROLL ユーザーがエディットコントロールの水平スクロールバーをクリックします。 親ウィンドウには、画面が更新される前に通知されます。

- ON_EN_KILLFOCUS エディットコントロールが入力フォーカスを失います。

- ON_EN_MAXTEXT エディットコントロールで、現在の挿入が指定された文字数を超えたため、切り捨てられました。 また、エディットコントロールに ES_AUTOHSCROLL スタイルが設定されておらず、挿入される文字数がエディットコントロールの幅を超える場合にも送信されます。 また、エディットコントロールに ES_AUTOVSCROLL スタイルが設定されておらず、テキストの挿入によって生成される行の合計数がエディットコントロールの高さを超える場合にも送信されます。

- ON_EN_SETFOCUS は、エディットコントロールが入力フォーカスを受け取ったときに送信されます。

- ON_EN_UPDATE エディットコントロールが変更されたテキストを表示しようとしています。 コントロールがテキストを書式設定した後、必要に応じてウィンドウサイズを変更できるように、テキストを表示する前に送信されます。

- ON_EN_VSCROLL は、ユーザーが編集コントロールの垂直スクロールバーをクリックしたときに発生します。 親ウィンドウには、画面が更新される前に通知されます。

ダイアログボックス`CEdit` `CEdit`内にオブジェクトを作成すると、ユーザーがダイアログボックスを閉じたときにオブジェクトが自動的に破棄されます。

ダイアログエディター `CEdit` `CEdit`を使用してダイアログリソースからオブジェクトを作成すると、ユーザーがダイアログボックスを閉じたときにオブジェクトが自動的に破棄されます。

ウィンドウ内に`CEdit`オブジェクトを作成する場合は、そのオブジェクトを破棄することも必要になることがあります。 スタックに`CEdit`オブジェクトを作成すると、そのオブジェクトは自動的に破棄されます。 新しい関数を使用`CEdit`してヒープにオブジェクトを作成する場合は、ユーザーが Windows のエディットコントロールを終了したときにオブジェクトを破棄するために、オブジェクトに対して**delete**を呼び出す必要があります。 `CEdit`オブジェクトにメモリを割り当てる場合は、 `CEdit`デストラクターをオーバーライドして割り当てを破棄します。

ES_READONLY などの編集コントロールで特定のスタイルを変更するには、 [Modifystyle](cwnd-class.md#modifystyle)を使用する代わりに、特定のメッセージをコントロールに送信する必要があります。 「Windows SDK での[コントロールスタイルの編集](/windows/win32/Controls/edit-control-styles)」を参照してください。

の`CEdit`詳細については、「[コントロール](../../mfc/controls-mfc.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="canundo"></a>  CEdit::CanUndo

最後の編集操作を元に戻すことができるかどうかを判断するには、この関数を呼び出します。

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>戻り値

メンバー関数の`Undo`呼び出しによって最後の編集操作を元に戻すことができる場合は0以外の場合は。元に戻すことができない場合は0。

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [EM_CANUNDO](/windows/win32/Controls/em-canundo) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: Undo](#undo)」の例を参照してください。

##  <a name="cedit"></a>CEdit:: CEdit

`CEdit` オブジェクトを構築します。

```
CEdit();
```

### <a name="remarks"></a>Remarks

[Create](#create)を使用して、Windows のエディットコントロールを構築します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

##  <a name="charfrompos"></a>  CEdit::CharFromPos

この`CEdit`コントロール内の指定された位置に最も近い文字の0から始まる行と文字のインデックスを取得するには、この関数を呼び出します。

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>パラメーター

*未満*<br/>
この`CEdit`オブジェクトのクライアント領域内の点の座標。

### <a name="return-value"></a>戻り値

下位ワードの文字インデックス、および上位ワード内の行のインデックスです。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  このメンバー関数は、Windows 95 および Windows NT 4.0 から使用できます。

詳細については、Windows SDK の「 [EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

##  <a name="clear"></a>  CEdit::Clear

エディットコントロール内の現在の選択項目 (存在する場合) を削除する場合は、この関数を呼び出します。

```
void Clear();
```

### <a name="remarks"></a>Remarks

によって`Clear`実行される削除は、 [Undo](#undo)メンバー関数を呼び出すことによって元に戻すことができます。

現在の選択範囲を削除し、削除された内容をクリップボードに配置するには、 [Cut](#cut)メンバー関数を呼び出します。

詳細については、Windows SDK の「 [WM_CLEAR](/windows/win32/dataxchg/wm-clear) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

##  <a name="copy"></a>  CEdit::Copy

この関数を呼び出して、エディットコントロール内の現在の選択項目 (存在する場合) を、CF_TEXT 形式でクリップボードにコピーします。

```
void Copy();
```

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [WM_COPY](/windows/win32/dataxchg/wm-copy) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

##  <a name="create"></a>  CEdit::Create

Windows のエディットコントロールを作成し、 `CEdit`オブジェクトにアタッチします。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
エディットコントロールのスタイルを指定します。 [編集スタイル](styles-used-by-mfc.md#edit-styles)の任意の組み合わせをコントロールに適用します。

*rect*<br/>
エディットコントロールのサイズと位置を指定します。 は、オブジェクト`CRect`または`RECT`構造体にすることができます。

*pParentWnd*<br/>
エディットコントロールの親ウィンドウ (通常は`CDialog`) を指定します。 NULL にすることはできません。

*nID*<br/>
エディットコントロールの ID を指定します。

### <a name="return-value"></a>戻り値

初期化が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

オブジェクトを構築`CEdit`するには、2つの手順を実行します。 まず、 `CEdit`コンストラクターを呼び出し、次に`Create`を呼び出します。これにより、Windows のエディットコントロール`CEdit`が作成され、オブジェクトにアタッチされます。

を`Create`実行すると、Windows は[WM_NCCREATE](/windows/win32/winmsg/wm-nccreate)、 [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize)、 [WM_CREATE](/windows/win32/winmsg/wm-create)、および[WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo)の各メッセージを編集コントロールに送信します。

これらのメッセージは、既定では`CWnd` 、基本クラスの[OnNcCreate](cwnd-class.md#onnccreate)、 [OnNcCalcSize](cwnd-class.md#onnccalcsize)、 [OnCreate](cwnd-class.md#oncreate)、および[OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo)の各メンバー関数によって処理されます。 既定のメッセージ処理を拡張するには、から`CEdit`クラスを派生させ、新しいクラスにメッセージマップを追加して、上記のメッセージハンドラーメンバー関数をオーバーライドします。 たとえば`OnCreate`、新しいクラスに必要な初期化を実行する場合は、をオーバーライドします。

次の[ウィンドウスタイル](styles-used-by-mfc.md#window-styles)を編集コントロールに適用します。

- 常に WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED はまれ

- グループコントロールに WS_GROUP

- WS_TABSTOP によって編集コントロールがタブ順に含まれるようになります。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

##  <a name="cut"></a>CEdit:: Cut

この関数を呼び出して、エディットコントロール内の現在の選択項目 (存在する場合) を削除 (切り取り) し、削除されたテキストを CF_TEXT 形式でクリップボードにコピーします。

```
void Cut();
```

### <a name="remarks"></a>Remarks

によって`Cut`実行される削除は、 [Undo](#undo)メンバー関数を呼び出すことによって元に戻すことができます。

削除されたテキストをクリップボードに配置せずに現在の選択項目を削除するには、 [Clear](#clear)メンバー関数を呼び出します。

詳細については、Windows SDK の「 [WM_CUT](/windows/win32/dataxchg/wm-cut) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

##  <a name="emptyundobuffer"></a>  CEdit::EmptyUndoBuffer

この関数を呼び出して、エディットコントロールの元に戻すフラグをリセット (クリア) します。

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>Remarks

エディットコントロールは、最後の操作を元に戻すことができなくなります。 元に戻すフラグは、エディットコントロール内の操作を元に戻すことができる場合に設定されます。

Undo フラグは、 [SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)または[SetHandle](#sethandle) `CWnd`メンバー関数が呼び出されるたびに自動的にクリアされます。

詳細については、Windows SDK の「 [EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

##  <a name="fmtlines"></a>  CEdit::FmtLines

この関数を呼び出して、複数行のエディットコントロール内でソフト改行文字を含めるか無効にするかを設定します。

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>パラメーター

*bAddEOL*<br/>
ソフト改行文字を挿入するかどうかを指定します。 値が TRUE の場合は、文字が挿入されます。値が FALSE の場合は、削除されます。

### <a name="return-value"></a>戻り値

書式設定が行われる場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

ソフトライン改行は、2つのキャリッジリターンと、単語の折り返しによって改行される行の末尾に挿入される改行で構成されます。 ハード改行は、1つのキャリッジリターンとラインフィードで構成されます。 ハード改行で終わる行は、による`FmtLines`影響を受けません。

ウィンドウは、 `CEdit`オブジェクトが複数行のエディットコントロールである場合にのみ応答します。

`FmtLines`は、 [GetHandle](#gethandle)によって返されるバッファーと[WM_GETTEXT](/windows/win32/winmsg/wm-gettext)によって返されるテキストにのみ影響します。 エディットコントロール内のテキストの表示には影響しません。

詳細については、Windows SDK の「 [EM_FMTLINES](/windows/win32/Controls/em-fmtlines) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

##  <a name="getcuebanner"></a>  CEdit::GetCueBanner

コントロールが空の場合に、エディットコントロールにテキストキュー (ヒント) として表示されるテキストを取得します。

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
入出力キューテキストを含む文字列へのポインター。

*cchText*<br/>
から受信できる文字数。 この数値には、終端の NULL 文字が含まれます。

### <a name="return-value"></a>戻り値

最初のオーバーロードの場合は、メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

2番目のオーバーロードでは、メソッドが成功した場合は、キューのテキストを含む[CString](../../atl-mfc-shared/using-cstring.md)です。それ以外の場合は、空の文字列 ("") です。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[EM_GETCUEBANNER](/windows/win32/Controls/em-getcuebanner)メッセージを送信します。 詳細については、「 [Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext)マクロ」を参照してください。

##  <a name="getfirstvisibleline"></a>  CEdit::GetFirstVisibleLine

この関数を呼び出して、エディットコントロールで最上位に表示される行を決定します。

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>戻り値

最上位の行の0から始まるインデックス。 単一行エディットコントロールの場合、戻り値は0です。

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

##  <a name="gethandle"></a>  CEdit::GetHandle

この関数を呼び出して、複数行のエディットコントロールに現在割り当てられているメモリのハンドルを取得します。

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>戻り値

エディットコントロールの内容を保持しているバッファーを識別するローカルメモリハンドル。 単一行のエディットコントロールにメッセージを送信するなどのエラーが発生した場合、戻り値は0です。

### <a name="remarks"></a>Remarks

ハンドルはローカルメモリハンドルであり、ローカルメモリハンドルをパラメーターとして受け取る**ローカル**の Windows メモリ関数のいずれかによって使用される場合があります。

`GetHandle`は、複数行のエディットコントロールによってのみ処理されます。

ダイアログ`GetHandle`ボックスが DS_LOCALEDIT style フラグが設定された状態で作成された場合にのみ、ダイアログボックスで複数行のエディットコントロールを呼び出します。 DS_LOCALEDIT スタイルが設定されていない場合でも、0以外の戻り値は取得されますが、返された値を使用することはできません。

> [!NOTE]
> `GetHandle`Windows 95/98 では機能しません。 Windows 95/98 で`GetHandle`を呼び出すと、NULL が返されます。 `GetHandle`は、「Windows NT バージョン3.51 以降」に記載されているとおりに動作します。

詳細については、Windows SDK の「 [EM_GETHANDLE](/windows/win32/Controls/em-gethandle) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

##  <a name="gethighlight"></a>  CEdit::GetHighlight

現在の編集コントロールで強調表示されているテキスト範囲内の最初と最後の文字のインデックスを取得します。

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*ピクチャの開始*|入出力強調表示されているテキスト範囲内の最初の文字の0から始まるインデックス番号。|
|*ピクチャの終了*|入出力強調表示されているテキスト範囲内の最後の文字の0から始まるインデックス番号。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[EM_GETHILITE](/windows/win32/Controls/em-gethilite)メッセージを送信します。 と`SetHighlight`は`GetHighlight`どちらも、現在 UNICODE ビルドでのみ有効です。

##  <a name="getlimittext"></a>  CEdit::GetLimitText

このメンバー関数を呼び出して、この`CEdit`オブジェクトのテキスト制限を取得します。

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>戻り値

この`CEdit`オブジェクトの現在のテキストの制限 (tchars)。

### <a name="remarks"></a>Remarks

テキストの上限は、エディットコントロールが受け入れることができるテキストの最大サイズ (TCHARs 単位) です。

> [!NOTE]
>  このメンバー関数は、Windows 95 および Windows NT 4.0 から使用できます。

詳細については、Windows SDK の「 [EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

##  <a name="getline"></a>  CEdit::GetLine

この関数を呼び出して、エディットコントロールからテキスト行を取得し、 *Lpszbuffer*に配置します。

```
int GetLine(
    int nIndex,
    LPTSTR lpszBuffer) const;

int GetLine(
    int nIndex,
    LPTSTR lpszBuffer,
    int nMaxLength) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
複数行のエディットコントロールから取得する行番号を指定します。 行番号は0から始まります。値0は最初の行を指定します。 このパラメーターは、単一行のエディットコントロールでは無視されます。

*lpszBuffer*<br/>
行のコピーを受け取るバッファーを指します。 バッファーの最初の単語では、バッファーにコピーできる TCHARs の最大数を指定する必要があります。

*nMaxLength*<br/>
バッファーにコピーできる TCHAR 文字の最大数を指定します。 `GetLine`Windows の呼び出しを行う前に、 *Lpszbuffer*の最初の単語にこの値を配置します。

### <a name="return-value"></a>戻り値

実際にコピーされた文字数。 *NIndex*によって指定された行番号がエディットコントロールの行数よりも大きい場合、戻り値は0です。

### <a name="remarks"></a>Remarks

コピーされた行に null 終端文字が含まれていません。

詳細については、Windows SDK の「 [EM_GETLINE](/windows/win32/Controls/em-getline) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: GetLineCount](#getlinecount)」の例を参照してください。

##  <a name="getlinecount"></a>  CEdit::GetLineCount

この関数を呼び出して、複数行のエディットコントロールの行数を取得します。

```
int GetLineCount() const;
```

### <a name="return-value"></a>戻り値

複数行のエディットコントロールの行数を格納している整数。 エディットコントロールにテキストが入力されていない場合、戻り値は1です。

### <a name="remarks"></a>Remarks

`GetLineCount`は、複数行のエディットコントロールによってのみ処理されます。

詳細については、Windows SDK の「 [EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

##  <a name="getmargins"></a>  CEdit::GetMargins

このメンバー関数を呼び出して、この編集コントロールの左右の余白を取得します。

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>戻り値

下位ワードの左余白の幅、および上位の単語の右余白の幅です ()。

### <a name="remarks"></a>Remarks

余白はピクセル単位で計測されます。

> [!NOTE]
>  このメンバー関数は、Windows 95 および Windows NT 4.0 から使用できます。

詳細については、Windows SDK の「 [EM_GETMARGINS](/windows/win32/Controls/em-getmargins) 」を参照してください。

### <a name="example"></a>例

  [CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl)の例を参照してください。

##  <a name="getmodify"></a>  CEdit::GetModify

この関数を呼び出して、エディットコントロールの内容が変更されているかどうかを確認します。

```
BOOL GetModify() const;
```

### <a name="return-value"></a>戻り値

編集コントロールの内容が変更されている場合は0以外の。変更されていない場合は0。

### <a name="remarks"></a>Remarks

Windows は、エディットコントロールの内容が変更されているかどうかを示す内部フラグを保持します。 このフラグは、エディットコントロールが最初に作成されたときにクリアされ、 [Setmodify](#setmodify)メンバー関数を呼び出すことによってクリアすることもできます。

詳細については、Windows SDK の「 [EM_GETMODIFY](/windows/win32/Controls/em-getmodify) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

##  <a name="getpasswordchar"></a>  CEdit::GetPasswordChar

ユーザーがテキストを入力したときに編集コントロールに表示されるパスワード文字を取得するには、この関数を呼び出します。

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>戻り値

ユーザーが入力した文字の代わりに表示される文字を指定します。 パスワード文字が存在しない場合、戻り値は NULL になります。

### <a name="remarks"></a>Remarks

ES_PASSWORD スタイルを使用して編集コントロールを作成した場合、コントロールをサポートする DLL によって既定のパスワード文字が決定されます。 マニフェストまたは[Initcommoncontrolsex](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex)メソッドは、どの DLL がエディットコントロールをサポートしているかを判断します。 User32.dll がエディットコントロールをサポートしている場合、既定のパスワード文字はアスタリスク (' * ', U + 002A) です。 Comctl32.dll バージョン6がエディットコントロールをサポートしている場合、既定の文字は黒の円 (' ● ', U + 25CF) です。 共通コントロールをサポートしている DLL とバージョンの詳細については、「 [Shell および Common Controls Versions](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\))」を参照してください。

このメソッドは、Windows SDK で説明されている[EM_GETPASSWORDCHAR](/windows/win32/Controls/em-getpasswordchar)メッセージを送信します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

##  <a name="getrect"></a>  CEdit::GetRect

エディットコントロールの書式指定用の四角形を取得します。

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
書式指定四角形`RECT`を受け取る構造体を指します。

### <a name="remarks"></a>Remarks

書式設定用の四角形は、エディットコントロールウィンドウのサイズに依存しない、テキストの限定された四角形です。

複数行のエディットコントロールの書式設定用の四角形は、 [SetRect](#setrect)および[SetRectNP](#setrectnp)メンバー関数によって変更できます。

詳細については、Windows SDK の「 [EM_GETRECT](/windows/win32/Controls/em-getrect) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: LimitText](#limittext)」の例を参照してください。

##  <a name="getsel"></a>  CEdit::GetSel

戻り値またはパラメーターを使用して、エディットコントロール内の現在の選択範囲の開始文字位置と終了文字位置を取得します。

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>パラメーター

*nStartChar*<br/>
現在の選択範囲の最初の文字の位置を受け取る整数への参照。

*nEndChar*<br/>
現在の選択範囲の末尾を越えて最初に選択解除された文字の位置を受け取る整数への参照。

### <a name="return-value"></a>戻り値

DWORD を返すバージョンでは、下位ワードの開始位置を含む値、および上位ワードの選択範囲の終了後の最初の項目の位置を返します。

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [EM_GETSEL](/windows/win32/Controls/em-getsel) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

##  <a name="hideballoontip"></a>  CEdit::HideBalloonTip

現在の編集コントロールに関連付けられているバルーンヒントを非表示にします。

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

この関数は、Windows SDK で説明されている[EM_HIDEBALLOONTIP](/windows/win32/Controls/em-hideballoontip)メッセージを送信します。

##  <a name="limittext"></a>  CEdit::LimitText

ユーザーがエディットコントロールに入力できるテキストの長さを制限するには、この関数を呼び出します。

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>パラメーター

*nChars*<br/>
ユーザーが入力できるテキストの長さ (TCHARs 単位) を指定します。 このパラメーターが0の場合、テキストの長さは UINT_MAX バイトに設定されます。 これが既定の動作です。

### <a name="remarks"></a>Remarks

テキストの制限を変更すると、ユーザーが入力できるテキストのみが制限されます。 エディットコントロールに既に存在するテキストには影響しません。また、の`CWnd` [SetWindowText](cwnd-class.md#setwindowtext)メンバー関数によってエディットコントロールにコピーされるテキストの長さにも影響しません。 アプリケーションで`SetWindowText`関数を使用して、の`LimitText`呼び出しで指定されたよりも多くのテキストを編集コントロールに配置する場合、ユーザーは編集コントロール内の任意のテキストを削除できます。 ただし、テキストの制限により、現在の選択範囲を削除してもテキストがテキストの上限を超えない限り、ユーザーは既存のテキストを新しいテキストに置き換えることができなくなります。

> [!NOTE]
>  Win32 (Windows NT および Windows 95/98) では、 [Setlimittext](#setlimittext)はこの関数を置き換えます。

詳細については、Windows SDK の「 [EM_LIMITTEXT](/windows/win32/Controls/em-limittext) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

##  <a name="linefromchar"></a>  CEdit::LineFromChar

この関数を呼び出して、指定した文字インデックスを含む行の行番号を取得します。

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
エディットコントロールのテキストに、目的の文字の0から始まるインデックス値を格納します。または、-1 を格納します。 *NIndex*が-1 の場合は、現在の行、つまり、カレットを含む行を指定します。

### <a name="return-value"></a>戻り値

*NIndex*によって指定された文字インデックスを含む行の0から始まる行番号。 *NIndex*が-1 の場合は、選択範囲の最初の文字を含む行の番号が返されます。 選択されていない場合は、現在の行番号が返されます。

### <a name="remarks"></a>Remarks

文字インデックスは、エディットコントロールの先頭からの文字数です。

このメンバー関数は、複数行のエディットコントロールによってのみ使用されます。

詳細については、Windows SDK の「 [EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

##  <a name="lineindex"></a>  CEdit::LineIndex

この関数を呼び出して、複数行のエディットコントロール内の行の文字インデックスを取得します。

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>パラメーター

*N 行*<br/>
エディットコントロールのテキスト内の目的の行のインデックス値を格納します。または、-1 を格納します。 *N 行*が-1 の場合は、現在の行、つまり、カレットを含む行を指定します。

### <a name="return-value"></a>戻り値

*N 行*で指定された行の文字インデックス。または、指定した行番号が編集コントロールの行数よりも大きい場合は-1。

### <a name="remarks"></a>Remarks

文字インデックスは、エディットコントロールの先頭から指定した行までの文字数です。

このメンバー関数は、複数行のエディットコントロールによってのみ処理されます。

詳細については、Windows SDK の「 [EM_LINEINDEX](/windows/win32/controls/em-lineindex) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

##  <a name="linelength"></a>  CEdit::LineLength

エディットコントロールの行の長さを取得します。

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>パラメーター

*N 行*<br/>
長さを取得する行内の文字の0から始まるインデックス。 既定値は -1 です。

### <a name="return-value"></a>戻り値

単一行エディットコントロールの場合、戻り値は、エディットコントロール内のテキストの長さ (TCHARs 単位) です。

複数行のエディットコントロールの場合、戻り値は*n 行*パラメーターで指定された行の tchars の長さです。 ANSI テキストの場合、長さは行のバイト数です。Unicode テキストの場合、長さは行の文字数です。 長さには、行末の復帰文字は含まれません。

*N 行*パラメーターがコントロール内の文字数よりも大きい場合、戻り値は0になります。

*N 行*パラメーターが-1 の場合、戻り値は、選択された文字を含む行で選択されていない文字の数になります。 たとえば、1つの行の4番目の文字から、次の行の末尾の8番目の文字までを選択した場合、戻り値は10になります。 つまり、1行目に3文字、次に7つの文字があります。

TCHAR 型の詳細については、「 [Windows データ型](/windows/win32/WinProg/windows-data-types)」の表にある tchar 行を参照してください。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[EM_LINELENGTH](/windows/win32/Controls/em-linelength)メッセージでサポートされています。

### <a name="example"></a>例

  「 [CEdit:: LineIndex](#lineindex)」の例を参照してください。

##  <a name="linescroll"></a>  CEdit::LineScroll

この関数を呼び出して、複数行のエディットコントロールのテキストをスクロールします。

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>パラメーター

*nLines*<br/>
垂直方向にスクロールする行数を指定します。

*nChars*<br/>
水平方向にスクロールする文字位置の数を指定します。 エディットコントロールに ES_RIGHT スタイルまたは ES_CENTER スタイルがある場合、この値は無視されます。

### <a name="remarks"></a>Remarks

このメンバー関数は、複数行のエディットコントロールによってのみ処理されます。

エディットコントロール内のテキストの最後の行を垂直方向にスクロールすることはできません。 現在の行と*nLines*で指定された行数が、エディットコントロールの行の合計数を超えた場合、エディットコントロールの最後の行が編集コントロールウィンドウの一番上にスクロールされるように値が調整されます。

`LineScroll`を使用すると、行の最後の文字を越えて水平方向にスクロールできます。

詳細については、Windows SDK の「 [EM_LINESCROLL](/windows/win32/Controls/em-linescroll) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: GetFirstVisibleLine](#getfirstvisibleline)」の例を参照してください。

##  <a name="paste"></a>  CEdit::Paste

クリップボード`CEdit`から挿入ポイントのにデータを挿入するには、この関数を呼び出します。

```
void Paste();
```

### <a name="remarks"></a>Remarks

データは、クリップボードに CF_TEXT 形式のデータが含まれている場合にのみ挿入されます。

詳細については、Windows SDK の「 [WM_PASTE](/windows/win32/dataxchg/wm-paste) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

##  <a name="posfromchar"></a>  CEdit::PosFromChar

この`CEdit`オブジェクト内の特定の文字の位置 (左上隅) を取得するには、この関数を呼び出します。

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>パラメーター

*nChar*<br/>
指定した文字の0から始まるインデックス。

### <a name="return-value"></a>戻り値

*NChar*によって指定された文字の左上隅の座標。

### <a name="remarks"></a>Remarks

文字は、0から始まるインデックス値を指定することによって指定されます。 *NChar*がこの`CEdit`オブジェクトの最後の文字のインデックスよりも大きい場合、戻り値は、この`CEdit`オブジェクトの最後の文字の直後にある文字位置の座標を指定します。

> [!NOTE]
>  このメンバー関数は、Windows 95 および Windows NT 4.0 から使用できます。

詳細については、Windows SDK の「 [EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: LineFromChar](#linefromchar)」の例を参照してください。

##  <a name="replacesel"></a>  CEdit::ReplaceSel

エディットコントロールの現在の選択項目を、 *lpszNewText*で指定したテキストに置き換えるには、この関数を呼び出します。

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>パラメーター

*lpszNewText*<br/>
置換テキストを含む null で終わる文字列を指します。

*bCanUndo*<br/>
この関数を元に戻すことができるように指定するには、このパラメーターの値を TRUE に設定します。 既定値は FALSE です。

### <a name="remarks"></a>Remarks

エディットコントロール内のテキストの一部だけを置換します。 すべてのテキストを置換する場合は、 [CWnd:: SetWindowText](cwnd-class.md#setwindowtext)メンバー関数を使用します。

現在選択されていない場合は、現在のカーソル位置に置換テキストが挿入されます。

詳細については、Windows SDK の「 [EM_REPLACESEL](/windows/win32/Controls/em-replacesel) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: LineIndex](#lineindex)」の例を参照してください。

##  <a name="setcuebanner"></a>  CEdit::SetCueBanner

コントロールが空の場合に、エディットコントロールにテキストキュー (ヒント) として表示されるテキストを設定します。

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
からエディットコントロールに表示するキューを含む文字列へのポインター。

*fDrawWhenFocused*<br/>
からFALSE の場合、ユーザーが編集コントロールをクリックしたときにキューバナーが描画されず、コントロールにフォーカスが移動します。

TRUE の場合、コントロールにフォーカスがあるときでも、キューバナーが描画されます。 ユーザーがコントロールの入力を開始すると、キューのバナーが表示されなくなります。

既定値は FALSE です。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[EM_SETCUEBANNER](/windows/win32/Controls/em-setcuebanner)メッセージを送信します。 詳細については、「 [Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused)マクロ」を参照してください。

### <a name="example"></a>例

次の例は、 [CEdit:: SetCueBanner](#setcuebanner)メソッドを示しています。

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

##  <a name="sethandle"></a>  CEdit::SetHandle

この関数を呼び出して、複数行のエディットコントロールによって使用されるローカルメモリのハンドルを設定します。

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>パラメーター

*hBuffer*<br/>
ローカルメモリへのハンドルを格納します。 このハンドルは、LMEM_MOVEABLE フラグを使用して、 [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) Windows 関数の前回の呼び出しによって作成されている必要があります。 メモリには、null で終わる文字列が含まれていると見なされます。 そうでない場合は、割り当てられたメモリの最初のバイトを0に設定する必要があります。

### <a name="remarks"></a>Remarks

エディットコントロールは、独自のバッファーを割り当てる代わりに、現在表示されているテキストを格納するために、このバッファーを使用します。

このメンバー関数は、複数行のエディットコントロールによってのみ処理されます。

アプリケーションで新しいメモリハンドルを設定する前に、 [GetHandle](#gethandle)メンバー関数を使用して、現在のメモリバッファーへのハンドルを取得し、Windows `LocalFree`の関数を使用してそのメモリを解放する必要があります。

`SetHandle`元に戻すバッファー ( [Canundo](#canundo)メンバー関数は0を返します) をクリアし、内部変更フラグ ( [getmodify](#getmodify)メンバー関数は0を返します) をクリアします。 編集コントロールウィンドウが再描画されます。

このメンバー関数は、ダイアログボックス内の複数行のエディットコントロールで、DS_LOCALEDIT style フラグが設定されたダイアログボックスを作成した場合にのみ使用できます。

> [!NOTE]
> `GetHandle`Windows 95/98 では機能しません。 Windows 95/98 で`GetHandle`を呼び出すと、NULL が返されます。 `GetHandle`は、「Windows NT バージョン3.51 以降」に記載されているとおりに動作します。

詳細については、Windows SDK の「 [EM_SETHANDLE](/windows/win32/Controls/em-sethandle)、 [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)、および[LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

##  <a name="sethighlight"></a>  CEdit::SetHighlight

現在の編集コントロールに表示されるテキストの範囲を強調表示します。

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*ichStart*|から強調表示するテキスト範囲内の最初の文字の0から始まるインデックス番号。|
|*ichEnd*|から強調表示するテキスト範囲内の最後の文字の0から始まるインデックス番号。|

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[EM_SETHILITE](/windows/win32/Controls/em-sethilite)メッセージを送信します。  このメソッドは、Windows SDK で説明されている[EM_SETHILITE](/windows/win32/Controls/em-sethilite)メッセージを送信します。 と`SetHighlight`は`GetHighlight`どちらも、UNICODE ビルドに対してのみ有効です。

##  <a name="setlimittext"></a>  CEdit::SetLimitText

この`CEdit`オブジェクトのテキスト制限を設定するには、このメンバー関数を呼び出します。

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>パラメーター

*N1 日*<br/>
新しいテキストの制限値 (文字数)。

### <a name="remarks"></a>Remarks

Text 制限は、エディットコントロールが受け入れることができるテキストの最大量 (文字数) です。

テキストの制限を変更すると、ユーザーが入力できるテキストのみが制限されます。 エディットコントロールに既に存在するテキストには影響しません。また、の`CWnd` [SetWindowText](cwnd-class.md#setwindowtext)メンバー関数によってエディットコントロールにコピーされるテキストの長さにも影響しません。 アプリケーションで`SetWindowText`関数を使用して、の`LimitText`呼び出しで指定されたよりも多くのテキストを編集コントロールに配置する場合、ユーザーは編集コントロール内の任意のテキストを削除できます。 ただし、テキストの制限により、現在の選択範囲を削除してもテキストがテキストの上限を超えない限り、ユーザーは既存のテキストを新しいテキストに置き換えることができなくなります。

この関数は、Win32 の[Limittext](#limittext)を置き換えます。

詳細については、Windows SDK の「 [EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) 」を参照してください。

### <a name="example"></a>例

  [CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl)の例を参照してください。

##  <a name="setmargins"></a>  CEdit::SetMargins

このエディットコントロールの左右の余白を設定するには、このメソッドを呼び出します。

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>パラメーター

*nLeft*<br/>
新しい左余白の幅 (ピクセル単位)。

*nRight*<br/>
新しい右余白の幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  このメンバー関数は、Windows 95 および Windows NT 4.0 から使用できます。

詳細については、Windows SDK の「 [EM_SETMARGINS](/windows/win32/Controls/em-setmargins) 」を参照してください。

### <a name="example"></a>例

  [CEditView:: GetEditCtrl](ceditview-class.md#geteditctrl)の例を参照してください。

##  <a name="setmodify"></a>  CEdit::SetModify

編集コントロールの変更されたフラグを設定またはクリアするには、この関数を呼び出します。

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>パラメーター

*bModified*<br/>
値が TRUE の場合は、テキストが変更されたことを示します。値が FALSE の場合は、変更されていないことを示します。 既定では、modified フラグが設定されています。

### <a name="remarks"></a>Remarks

Modified フラグは、エディットコントロール内のテキストが変更されたかどうかを示します。 ユーザーがテキストを変更するたびに自動的に設定されます。 値を取得するには、 [Getmodify](#getmodify)メンバー関数を使用します。

詳細については、Windows SDK の「 [EM_SETMODIFY](/windows/win32/Controls/em-setmodify) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: GetModify](#getmodify)」の例を参照してください。

##  <a name="setpasswordchar"></a>  CEdit::SetPasswordChar

ユーザーがテキストを入力したときに編集コントロールに表示されるパスワード文字を設定または削除するには、この関数を呼び出します。

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>パラメーター

*ch*<br/>
ユーザーが入力した文字の代わりに表示される文字を指定します。 *Ch*が0の場合は、ユーザーが入力した実際の文字が表示されます。

### <a name="remarks"></a>Remarks

パスワード文字を設定すると、ユーザーが入力した文字ごとにその文字が表示されます。

このメンバー関数は、複数行のエディットコントロールには影響しません。

メンバー関数が呼び出されると、 `CEdit`は、ch によって指定された文字を使用して、表示されるすべての文字を再描画します。 `SetPasswordChar`

エディットコントロールが[ES_PASSWORD](styles-used-by-mfc.md#edit-styles)スタイルで作成されている場合、既定のパスワード文字はアスタリスク ( <strong>\*</strong>) に設定されます。 Ch を0に設定`SetPasswordChar`してを呼び出すと、このスタイルは削除されます。

詳細については、Windows SDK の「 [EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

##  <a name="setreadonly"></a>  CEdit::SetReadOnly

エディットコントロールの読み取り専用の状態を設定するために、この関数を呼び出します。

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>パラメーター

*bReadOnly*<br/>
エディットコントロールの読み取り専用の状態を設定または削除するかどうかを指定します。 値が TRUE の場合は、状態が読み取り専用に設定されます。値が FALSE の場合、状態は読み取り/書き込みに設定されます。

### <a name="return-value"></a>戻り値

操作が成功した場合は0以外の場合は。エラーが発生した場合は0。

### <a name="remarks"></a>Remarks

現在の設定を見つけるには、 [CWnd:: GetStyle](cwnd-class.md#getstyle)の戻り値の[ES_READONLY](styles-used-by-mfc.md#edit-styles)フラグをテストします。

詳細については、Windows SDK の「 [EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

##  <a name="setrect"></a>  CEdit::SetRect

この関数を呼び出して、指定した座標を使用して四角形の寸法を設定します。

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
書式指定用`RECT`の四角形`CRect`の新しい次元を指定する構造体またはオブジェクトを指します。

### <a name="remarks"></a>Remarks

このメンバーは、複数行のエディットコントロールによってのみ処理されます。

複数`SetRect`行のエディットコントロールの書式指定用の四角形を設定するには、を使用します。 書式設定用の四角形は、エディットコントロールウィンドウのサイズに依存しない、テキストの限定された四角形です。 エディットコントロールが最初に作成されたとき、書式設定の四角形は編集コントロールウィンドウのクライアント領域と同じになります。 `SetRect`メンバー関数を使用すると、アプリケーションは、書式設定の四角形を編集コントロールウィンドウよりも大きくしたり小さくしたりすることができます。

エディットコントロールにスクロールバーがない場合、書式設定の四角形がウィンドウより大きい場合、テキストは切り取られずに切り取られます。 エディットコントロールに境界線が含まれている場合は、罫線のサイズによって書式設定の四角形が縮小されます。 `GetRect`メンバー関数によって返される四角形を調整する場合は、四角形をに`SetRect`渡す前に、境界線のサイズを削除する必要があります。

が`SetRect`呼び出されると、エディットコントロールのテキストも再フォーマットされ、再表示されます。

詳細については、Windows SDK の「 [EM_SETRECT](/windows/win32/Controls/em-setrect) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

##  <a name="setrectnp"></a>  CEdit::SetRectNP

複数行の編集コントロールの書式指定用の四角形を設定するには、この関数を呼び出します。

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
四角形の新しい`RECT`寸法を`CRect`指定する構造体またはオブジェクトを指します。

### <a name="remarks"></a>Remarks

書式設定用の四角形は、エディットコントロールウィンドウのサイズに依存しない、テキストの限定された四角形です。

`SetRectNP`は、編集コントロール`SetRect`ウィンドウが再描画されない点を除いて、メンバー関数と同じです。

エディットコントロールが最初に作成されたとき、書式設定の四角形は編集コントロールウィンドウのクライアント領域と同じになります。 アプリケーションでは`SetRectNP` 、メンバー関数を呼び出すことにより、書式設定の四角形を編集コントロールウィンドウよりも大きくしたり小さくしたりすることができます。

エディットコントロールにスクロールバーがない場合、書式設定の四角形がウィンドウより大きい場合、テキストは切り取られずに切り取られます。

このメンバーは、複数行のエディットコントロールによってのみ処理されます。

詳細については、Windows SDK の「 [EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: SetRect](#setrect)」の例を参照してください。

##  <a name="setsel"></a>  CEdit::SetSel

エディットコントロール内の文字の範囲を選択するには、この関数を呼び出します。

```
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>パラメーター

*dwSelection*<br/>
下位ワードの開始位置と上位ワードの終了位置を指定します。 下位ワードが0で、上位ワードが-1 の場合、エディットコントロール内のすべてのテキストが選択されます。 下位ワードが-1 の場合、現在の選択項目はすべて削除されます。

*bNoScroll*<br/>
キャレットをスクロールして表示するかどうかを示します。 FALSE の場合、キャレットはスクロールして表示されます。 TRUE の場合、キャレットはスクロールされずに表示されます。

*nStartChar*<br/>
開始位置を指定します。 *Nstartchar*が0で*nEndChar*が-1 の場合、エディットコントロール内のすべてのテキストが選択されます。 *Nstartchar*が-1 の場合、現在の選択はすべて削除されます。

*nEndChar*<br/>
終了位置を指定します。

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [EM_SETSEL](/windows/win32/Controls/em-setsel) 」を参照してください。

### <a name="example"></a>例

  「 [CEdit:: GetSel](#getsel)」の例を参照してください。

##  <a name="settabstops"></a>  CEdit::SetTabStops

この関数を呼び出して、複数行のエディットコントロールでタブストップを設定します。

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>パラメーター

*cxEachStop*<br/>
すべての*cxEachStop*ダイアログ単位でタブストップを設定することを指定します。

*nTabStops*<br/>
*RgTabStops*に含まれるタブストップの数を指定します。 この数値は1より大きい値である必要があります。

*rgTabStops*<br/>
ダイアログ単位のタブストップを指定する符号なし整数の配列を指します。 ダイアログ単位は、水平方向または垂直方向の距離です。 水平ダイアログ単位は、現在のダイアログベースの幅の単位の1番目と同じです。また、1つの垂直ダイアログ単位は、現在のダイアログベースの高さ単位の8分の1と等しくなります。 ダイアログの基本単位は、現在のシステムフォントの高さと幅に基づいて計算されます。 Windows `GetDialogBaseUnits`関数は、現在のダイアログベース単位をピクセル単位で返します。

### <a name="return-value"></a>戻り値

タブが設定されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

テキストが複数行の編集コントロールにコピーされると、テキスト内のタブ文字によって、次のタブストップまでの領域が生成されます。

タブストップを既定のサイズの32ダイアログ単位に設定するには、このメンバー関数のパラメーターなしのバージョンを呼び出します。 タブストップを32以外のサイズに設定するには、 *cxEachStop*パラメーターを使用してバージョンを呼び出します。 タブストップをサイズの配列に設定するには、2つのパラメーターを持つバージョンを使用します。

このメンバー関数は、複数行のエディットコントロールによってのみ処理されます。

`SetTabStops`編集ウィンドウは自動的に再描画されません。 エディットコントロールに既に存在するテキストのタブストップを変更する場合は、 [CWnd:: InvalidateRect](cwnd-class.md#invalidaterect)を呼び出して編集ウィンドウを再描画します。

詳細については、Windows SDK の「 [EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops)と[Get baseunits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) 」を参照してください。

### <a name="example"></a>例

  [CEditView:: SetTabStops](ceditview-class.md#settabstops)の例を参照してください。

##  <a name="showballoontip"></a>  CEdit::ShowBalloonTip

現在の編集コントロールに関連付けられているバルーンヒントを表示します。

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pEditBalloonTip*|からバルーンヒントを記述する[EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip)構造体へのポインター。|
|*lpszTitle*|からバルーンヒントのタイトルを含む Unicode 文字列へのポインター。|
|*lpszText*|からバルーンヒントテキストを含む Unicode 文字列へのポインター。|
|*ttiIcon*|からバルーンヒントに関連付けるアイコンの種類を指定する**INT** 。 既定値は TTI_NONE です。 詳細については、 `ttiIcon` [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip)構造体のメンバーを参照してください。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

この関数は、Windows SDK で説明されている[EM_SHOWBALLOONTIP](/windows/win32/Controls/em-showballoontip)メッセージを送信します。 詳細については、「 [Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip)マクロ」を参照してください。

### <a name="example"></a>例

現在の編集コントロールにアクセスするため`m_cedit`に使用される変数を定義するコード例を次に示します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>例

次のコード例では、エディットコントロールのバルーンヒントを表示します。 [CEdit:: ShowBalloonTip](#showballoontip)メソッドは、タイトルとバルーンヒントテキストを指定します。

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

##  <a name="undo"></a>  CEdit::Undo

最後の編集コントロール操作を元に戻すには、この関数を呼び出します。

```
BOOL Undo();
```

### <a name="return-value"></a>戻り値

単一行のエディットコントロールの場合、戻り値は常に0以外になります。 複数行のエディットコントロールでは、元に戻す操作が成功した場合、戻り値は0以外の値になります。また、元に戻す操作が失敗した場合は0になります。

### <a name="remarks"></a>Remarks

元に戻す操作は元に戻すこともできます。 たとえば、の最初の呼び出し`Undo`で、削除されたテキストを復元できます。 編集操作が介在しない限り、の2回目の呼び出し`Undo`でテキストを削除できます。

詳細については、Windows SDK の「 [EM_UNDO](/windows/win32/Controls/em-undo) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプル CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC のサンプル CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CWnd クラス](cwnd-class.md)<br/>
[CButton クラス](cbutton-class.md)<br/>
[CComboBox クラス](ccombobox-class.md)<br/>
[CListBox クラス](clistbox-class.md)<br/>
[CScrollBar クラス](cscrollbar-class.md)<br/>
[CStatic クラス](cstatic-class.md)<br/>
[CDialog クラス](cdialog-class.md)
