---
title: CButton クラス
ms.date: 11/04/2016
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
ms.openlocfilehash: 669bdb18e378c4dc39bdc6d51ca1ebe7f93fa839
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507421"
---
# <a name="cbutton-class"></a>CButton クラス

Windows のボタン コントロールの機能が用意されています。

## <a name="syntax"></a>構文

```
class CButton : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CButton:: CButton](#cbutton)|`CButton` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CButton:: Create](#create)|Windows のボタンコントロールを作成し、 `CButton`オブジェクトにアタッチします。|
|[CButton::D rawItem](#drawitem)|オーナー描画`CButton`オブジェクトを描画するには、をオーバーライドします。|
|[CButton:: GetBitmap](#getbitmap)|以前に[SetBitmap](#setbitmap)で設定されたビットマップのハンドルを取得します。|
|[CButton:: GetButtonStyle](#getbuttonstyle)|ボタンコントロールスタイルに関する情報を取得します。|
|[CButton:: GetCheck](#getcheck)|ボタンコントロールのチェックの状態を取得します。|
|[CButton:: GetCursor](#getcursor)|以前に[SetCursor](#setcursor)で設定したカーソルイメージのハンドルを取得します。|
|[CButton:: GetIcon](#geticon)|以前に[SetIcon](#seticon)で設定したアイコンのハンドルを取得します。|
|[CButton::GetIdealSize](#getidealsize)|ボタンコントロールの理想的なサイズを取得します。|
|[CButton::GetImageList](#getimagelist)|ボタンコントロールのイメージリストを取得します。|
|[CButton::GetNote](#getnote)|現在のコマンドリンクコントロールのノートコンポーネントを取得します。|
|[CButton::GetNoteLength](#getnotelength)|現在のコマンドリンクコントロールのノートテキストの長さを取得します。|
|[CButton:: GetSplitGlyph](#getsplitglyph)|現在の分割ボタンコントロールに関連付けられているグリフを取得します。|
|[CButton::GetSplitImageList](#getsplitimagelist)|現在の分割ボタンコントロールのイメージリストを取得します。|
|[CButton::GetSplitInfo](#getsplitinfo)|現在の分割ボタンコントロールを定義する情報を取得します。|
|[CButton:: GetSplitSize](#getsplitsize)|現在の分割ボタンコントロールのドロップダウンコンポーネントの外接する四角形を取得します。|
|[CButton:: GetSplitStyle](#getsplitstyle)|現在の分割ボタンコントロールを定義する分割ボタンのスタイルを取得します。|
|[CButton::GetState](#getstate)|ボタンコントロールのチェック状態、強調表示状態、およびフォーカス状態を取得します。|
|[CButton:: GetTextMargin](#gettextmargin)|ボタンコントロールのテキストの余白を取得します。|
|[CButton:: SetBitmap](#setbitmap)|ボタンに表示されるビットマップを指定します。|
|[CButton:: SetButtonStyle](#setbuttonstyle)|ボタンのスタイルを変更します。|
|[CButton:: SetCheck](#setcheck)|ボタンコントロールのチェックの状態を設定します。|
|[CButton:: SetCursor](#setcursor)|ボタンに表示されるカーソルイメージを指定します。|
|[CButton:: SetDropDownState](#setdropdownstate)|現在の分割ボタンコントロールのドロップダウン状態を設定します。|
|[CButton:: SetIcon](#seticon)|ボタンに表示するアイコンを指定します。|
|[CButton::SetImageList](#setimagelist)|ボタンコントロールのイメージリストを設定します。|
|[CButton::SetNote](#setnote)|現在のコマンドリンクコントロールでメモを設定します。|
|[CButton:: SetSplitGlyph](#setsplitglyph)|指定したグリフを現在の分割ボタンコントロールに関連付けます。|
|[CButton::SetSplitImageList](#setsplitimagelist)|イメージリストを現在の分割ボタンコントロールに関連付けます。|
|[CButton:: SetSplitInfo](#setsplitinfo)|現在の分割ボタンコントロールを定義する情報を指定します。|
|[CButton:: SetSplitSize](#setsplitsize)|現在の分割ボタンコントロールのドロップダウンコンポーネントの外接する四角形を設定します。|
|[CButton:: SetSplitStyle](#setsplitstyle)|現在の分割ボタンコントロールのスタイルを設定します。|
|[CButton:: SetState](#setstate)|ボタンコントロールの強調表示の状態を設定します。|
|[CButton::SetTextMargin](#settextmargin)|ボタンコントロールのテキストの余白を設定します。|

## <a name="remarks"></a>Remarks

ボタンコントロールは、クリックまたはオフにできる小さな四角形の子ウィンドウです。 ボタンは単独またはグループで使用でき、テキストなしでラベル付けまたは表示できます。 ボタンは、通常、ユーザーがボタンをクリックしたときに外観を変更します。

一般的なボタンは、チェックボックス、オプションボタン、およびプッシュボタンです。 オブジェクト`CButton`は、 [Create](#create) member 関数による初期化時に指定された[ボタンスタイル](../../mfc/reference/styles-used-by-mfc.md#button-styles)に従って、これらのいずれかになります。

さらに、から`CButton`派生した[cbitmapbutton](../../mfc/reference/cbitmapbutton-class.md)クラスは、テキストではなくビットマップイメージでラベル付けされたボタンコントロールの作成をサポートしています。 で`CBitmapButton`は、ボタンの上下の状態に対して個別のビットマップを使用できます。

ボタンコントロールは、ダイアログテンプレートから作成することも、コード内で直接作成することもできます。 どちらの場合も、最初にコンストラクター `CButton`を呼び出して`CButton` `Create`オブジェクトを構築した後、メンバー関数を呼び出して`CButton` Windows ボタンコントロールを作成し、それをオブジェクトにアタッチします。

構築は、から`CButton`派生したクラスの1ステップのプロセスにすることができます。 派生クラスのコンストラクターを記述し、コンストラクター `Create`内からを呼び出します。

ボタンコントロールから親 (通常は、 [CDialog](../../mfc/reference/cdialog-class.md)から派生したクラス) に送信される Windows 通知メッセージを処理する場合は、各メッセージの親クラスにメッセージマップエントリとメッセージハンドラーメンバー関数を追加します。

各メッセージマップエントリには、次の形式があります。

**通知\_時** **(** _id_、 _memberFxn_ **)**

ここで、 *id*で通知を送信するコントロールの子ウィンドウ id を指定します。 *memberFxn*は、通知を処理するために記述した親メンバー関数の名前です。

親の関数プロトタイプは次のとおりです。

`afx_msg void memberFxn();`

考えられるメッセージマップエントリは次のとおりです。

|マップエントリ|親に送信されたとき|
|---------------|----------------------------|
|ON_BN_CLICKED|ユーザーがボタンをクリックします。|
|ON_BN_DOUBLECLICKED|ユーザーがボタンをダブルクリックします。|

ダイアログリソース`CButton` `CButton`からオブジェクトを作成すると、ユーザーがダイアログボックスを閉じたときにオブジェクトが自動的に破棄されます。

ウィンドウ内に`CButton`オブジェクトを作成する場合は、そのオブジェクトを破棄する必要がある場合があります。 新しい関数を使用`CButton`してヒープにオブジェクトを作成する場合、ユーザーが Windows ボタンコントロールを閉じたときに破棄するには、オブジェクトに対して**delete**を呼び出す必要があります。 `CButton`オブジェクトをスタックに作成した場合、または親ダイアログオブジェクトに埋め込んだ場合は、自動的に破棄されます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="cbutton"></a>CButton:: CButton

`CButton` オブジェクトを構築します。

```
CButton();
```

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

##  <a name="create"></a>CButton:: Create

Windows のボタンコントロールを作成し、 `CButton`オブジェクトにアタッチします。

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*lpszCaption*<br/>
ボタンコントロールのテキストを指定します。

*dwStyle*<br/>
ボタンコントロールのスタイルを指定します。 ボタン[スタイル](../../mfc/reference/styles-used-by-mfc.md#button-styles)の任意の組み合わせをボタンに適用します。

*rect*<br/>
ボタンコントロールのサイズと位置を指定します。 `CRect` オブジェクト`RECT`または構造体のいずれかを指定できます。

*pParentWnd*<br/>
ボタンコントロールの親ウィンドウ (通常は`CDialog`) を指定します。 NULL にすることはできません。

*nID*<br/>
ボタンコントロールの ID を指定します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

オブジェクトを構築`CButton`するには、2つの手順を実行します。 まず、コンストラクターを呼び出し、次に`Create`を呼び出します。これにより、Windows ボタンコントロールが`CButton`作成され、オブジェクトにアタッチされます。

WS_VISIBLE スタイルが指定されている場合、アクティブ化してボタンを表示するために必要なすべてのメッセージが button コントロールに送信されます。

次の[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)をボタンコントロールに適用します。

- 常に WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED はまれ

- グループコントロールに WS_GROUP

- WS_TABSTOP をクリックして、タブオーダーにボタンを追加します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

##  <a name="drawitem"></a>CButton::D rawItem

オーナー描画ボタンの外観が変更されたときにフレームワークによって呼び出されます。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>パラメーター

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)構造体への long ポインター。 構造体には、描画する項目と必要な描画の種類に関する情報が含まれます。

### <a name="remarks"></a>Remarks

オーナー描画のボタンには、BS_OWNERDRAW スタイルが設定されています。 オーナー描画`CButton`オブジェクトの描画を実装するには、このメンバー関数をオーバーライドします。 アプリケーションでは、メンバー関数が終了する前に、 *lpDrawItemStruct*で指定された表示コンテキスト用に選択されたすべてのグラフィックスデバイスインターフェイス (GDI) オブジェクトを復元する必要があります。

[BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles)スタイル値も参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

##  <a name="getbitmap"></a>  CButton::GetBitmap

このメンバー関数を呼び出して、ボタンに関連付けられている、以前に[SetBitmap](#setbitmap)で設定したビットマップのハンドルを取得します。

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>戻り値

ビットマップを処理するハンドル。 以前にビットマップが指定されていない場合は NULL です。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="getbuttonstyle"></a>CButton:: GetButtonStyle

ボタンコントロールスタイルに関する情報を取得します。

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>戻り値

この`CButton`オブジェクトのボタンスタイルを返します。 この関数は、他のウィンドウスタイルのいずれかではなく、 [BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles) style 値のみを返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="getcheck"></a>  CButton::GetCheck

オプションボタンまたはチェックボックスのチェックの状態を取得します。

```
int GetCheck() const;
```

### <a name="return-value"></a>戻り値

BS_AUTOCHECKBOX、BS_AUTORADIOBUTTON、BS_AUTO3STATE、BS_CHECKBOX、BS_RADIOBUTTON、または BS_3STATE style で作成されたボタンコントロールからの戻り値は、次のいずれかの値になります。

|[値]|説明|
|-----------|-------------|
|BST_UNCHECKED|ボタンの状態がオフになっています。|
|BST_CHECKED|ボタンの状態がチェックされます。|
|BST_INDETERMINATE|ボタンの状態は不確定です (ボタンのスタイルが BS_3STATE または BS_AUTO3STATE の場合にのみ適用されます)。|

ボタンに他のスタイルがある場合、戻り値は BST_UNCHECKED です。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="getcursor"></a>  CButton::GetCursor

このメンバー関数を呼び出して、ボタンに関連付けられているカーソルのハンドルを取得します。これは、 [SetCursor](#setcursor)で設定されています。

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>戻り値

カーソルイメージを処理するハンドル。 カーソルが前に指定されていない場合は NULL です。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="geticon"></a>CButton:: GetIcon

このメンバー関数を呼び出して、ボタンに関連付けられている[SetIcon](#seticon)で以前に設定したアイコンのハンドルを取得します。

```
HICON GetIcon() const;
```

### <a name="return-value"></a>戻り値

アイコンにへのハンドル。 以前にアイコンが指定されていない場合は NULL です。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="getidealsize"></a>  CButton::GetIdealSize

ボタンコントロールの理想的なサイズを取得します。

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>パラメーター

*psize*<br/>
ボタンの現在のサイズへのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK の [[ボタン](/windows/win32/controls/buttons)] セクションで説明されているように、BCM_GETIDEALSIZE メッセージの機能をエミュレートします。

##  <a name="getimagelist"></a>  CButton::GetImageList

ボタンコントロールからイメージリストを取得するには、このメソッドを呼び出します。

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>パラメーター

*pbuttonImagelist*<br/>
`CButton`オブジェクトのイメージリストへのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK の [[ボタン](/windows/win32/controls/buttons)] セクションで説明されているように、BCM_GETIMAGELIST メッセージの機能をエミュレートします。

##  <a name="getnote"></a>  CButton::GetNote

現在のコマンドリンクコントロールに関連付けられているノートテキストを取得します。

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*lpszNote*|入出力バッファーへのポインター。呼び出し元が割り当てと割り当て解除を行います。 戻り値が TRUE の場合、現在のコマンドリンクコントロールに関連付けられているノートテキストがバッファーに格納されます。それ以外の場合、バッファーは変更されません。|
|*cchNote*|[入力、出力]符号なし整数変数へのポインター。<br /><br /> このメソッドが呼び出されると、変数には、 *Lpsznote*パラメーターによって指定されたバッファーのサイズが格納されます。<br /><br /> このメソッドから制御が戻るときに、戻り値が TRUE の場合、現在のコマンドリンクコントロールに関連付けられているメモのサイズが変数に格納されます。 戻り値が FALSE の場合、変数には、メモを格納するために必要なバッファーサイズが格納されます。|

### <a name="return-value"></a>戻り値

最初のオーバーロードでは、現在のコマンドリンクコントロールに関連付けられているノートテキストを含む[CString](../../atl-mfc-shared/using-cstring.md)オブジェクト。

\- または -

2番目のオーバーロードでは、このメソッドが成功した場合は TRUE になります。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンスタイルが BS_COMMANDLINK または BS_DEFCOMMANDLINK のコントロールでのみ使用します。

このメソッドは、Windows SDK で説明されている[BCM_GETNOTE](/windows/win32/Controls/bcm-getnote)メッセージを送信します。

##  <a name="getnotelength"></a>  CButton::GetNoteLength

現在のコマンドリンクコントロールのノートテキストの長さを取得します。

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>戻り値

現在のコマンドリンクコントロールのノートテキストの長さ (16 ビット Unicode 文字)。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンスタイルが BS_COMMANDLINK または BS_DEFCOMMANDLINK のコントロールでのみ使用します。

このメソッドは、Windows SDK で説明されている[BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength)メッセージを送信します。

##  <a name="getsplitglyph"></a>  CButton::GetSplitGlyph

現在の分割ボタンコントロールに関連付けられているグリフを取得します。

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>戻り値

現在の分割ボタンコントロールに関連付けられているグリフ文字。

### <a name="remarks"></a>Remarks

グリフは、特定のフォントにおける文字の物理的な表現です。 たとえば、分割ボタンコントロールは、Unicode チェックマーク文字 (U + 2713) のグリフで装飾される場合があります。

このメソッドは、ボタンスタイルが BS_SPLITBUTTON または BS_DEFSPLITBUTTON のコントロールでのみ使用します。

このメソッドは、 `mask` BCSIF_GLYPH フラグを使用して[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体のメンバーを初期化し、Windows SDK で説明されている[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)メッセージにその構造体を送信します。 メッセージ関数がを返すと、このメソッドは構造体の`himlGlyph`メンバーからグリフを取得します。

##  <a name="getsplitimagelist"></a>  CButton::GetSplitImageList

現在の分割ボタンコントロールの[イメージリスト](../../mfc/reference/cimagelist-class.md)を取得します。

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>戻り値

[CImageList](../../mfc/reference/cimagelist-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンスタイルが BS_SPLITBUTTON または BS_DEFSPLITBUTTON のコントロールでのみ使用します。

このメソッドは、 `mask` BCSIF_IMAGE フラグを使用して[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体のメンバーを初期化し、Windows SDK で説明されている[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)メッセージにその構造体を送信します。 メッセージ関数がを返すと、このメソッドは構造体の`himlGlyph`メンバーからイメージリストを取得します。

##  <a name="getsplitinfo"></a>  CButton::GetSplitInfo

ウィンドウが現在の分割ボタンコントロールを描画する方法を決定するパラメーターを取得します。

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pInfo*|入出力現在の分割ボタンコントロールに関する情報を受け取る[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体へのポインター。 呼び出し元は、構造体の割り当てを行います。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンスタイルが BS_SPLITBUTTON または BS_DEFSPLITBUTTON のコントロールでのみ使用します。

このメソッドは、Windows SDK で説明されている[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)メッセージを送信します。

##  <a name="getsplitsize"></a>CButton:: GetSplitSize

現在の分割ボタンコントロールのドロップダウンコンポーネントの外接する四角形を取得します。

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pSize*|入出力四角形の説明を受け取る[サイズ](/windows/win32/api/windef/ns-windef-size)構造体へのポインター。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンスタイルが BS_SPLITBUTTON または BS_DEFSPLITBUTTON のコントロールでのみ使用します。

分割ボタンコントロールが展開されると、リストコントロールやページャーコントロールなどのドロップダウンコンポーネントが表示されます。 このメソッドは、ドロップダウンコンポーネントを含む外接する四角形を取得します。

このメソッドは、 `mask` BCSIF_SIZE フラグを使用して[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体のメンバーを初期化し、Windows SDK で説明されている[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)メッセージにその構造体を送信します。 メッセージ関数がを返すと、このメソッドは構造体の`size`メンバーから外接する四角形を取得します。

##  <a name="getsplitstyle"></a>CButton:: GetSplitStyle

現在の分割ボタンコントロールを定義する分割ボタンのスタイルを取得します。

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>戻り値

分割ボタンのスタイルのビットごとの組み合わせ。 詳細については、 `uSplitStyle` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体のメンバーを参照してください。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンスタイルが BS_SPLITBUTTON または BS_DEFSPLITBUTTON のコントロールでのみ使用します。

分割ボタンのスタイルでは、ウィンドウが分割ボタンアイコンを描画する配置、縦横比、およびグラフィカルな形式を指定します。

このメソッドは、 `mask` BCSIF_STYLE フラグを使用して[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体のメンバーを初期化し、Windows SDK で説明されている[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)メッセージにその構造体を送信します。 メッセージ関数がを返すと、このメソッドは構造体の`uSplitStyle`メンバーから分割ボタンのスタイルを取得します。

##  <a name="getstate"></a>  CButton::GetState

ボタンコントロールの状態を取得します。

```
UINT GetState() const;
```

### <a name="return-value"></a>戻り値

ボタンコントロールの現在の状態を示す値の組み合わせを格納するビットフィールド。 次の表に、使用可能な値を示します。

|ボタンの状態|[値]|説明|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|初期状態。|
|BST_CHECKED|0x0001|ボタンコントロールがチェックされます。|
|BST_INDETERMINATE|0x0002|状態は不確定です (ボタンコントロールに3つの状態がある場合にのみ可能です)。|
|BST_PUSHED|0x0004|ボタンコントロールが押されています。|
|BST_FOCUS|0x0008|ボタンコントロールにフォーカスがあります。|

### <a name="remarks"></a>Remarks

BS_3STATE または BS_AUTO3STATE ボタンスタイルを持つボタンコントロールは、中間状態という名前の3番目の状態を持つチェックボックスを作成します。 不確定状態は、チェックボックスがオンでもオフでもないことを示します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="gettextmargin"></a>  CButton::GetTextMargin

`CButton`オブジェクトのテキストの余白を取得するには、このメソッドを呼び出します。

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>パラメーター

*pmargin*<br/>
`CButton`オブジェクトのテキストの余白へのポインター。

### <a name="return-value"></a>戻り値

テキストの余白を返します。

### <a name="remarks"></a>Remarks

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK の [[ボタン](/windows/win32/controls/buttons)] セクションで説明されているように、BCM_GETTEXTMARGIN メッセージの機能をエミュレートします。

##  <a name="setbitmap"></a>  CButton::SetBitmap

このメンバー関数を呼び出して、新しいビットマップをボタンに関連付けます。

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>パラメーター

*hBitmap*<br/>
ビットマップのハンドル。

### <a name="return-value"></a>戻り値

以前にボタンに関連付けられていたビットマップのハンドル。

### <a name="remarks"></a>Remarks

ビットマップは、既定で中心となるボタンの表面に自動的に配置されます。 ビットマップがボタンに対して大きすぎる場合は、いずれかの側でクリップされます。 次のような他の配置オプションを選択できます。

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

ボタンごとに4つのビットマップを使用する[cbitmapbutton](../../mfc/reference/cbitmapbutton-class.md)とは異なり、で`SetBitmap`は、ボタンごとにビットマップが1つだけ使用されます。 このボタンが押されると、ビットマップが下と右にシフトされます。

操作が完了したら、ビットマップを解放する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

##  <a name="setbuttonstyle"></a>CButton:: SetButtonStyle

ボタンのスタイルを変更します。

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>パラメーター

*nStyle*<br/>
ボタンの[スタイル](../../mfc/reference/styles-used-by-mfc.md#button-styles)を指定します。

*より描画*<br/>
ボタンを再描画するかどうかを指定します。 0以外の値を指定すると、ボタンが再描画されます。 0の値を指定しても、ボタンは再描画されません。 既定では、ボタンが再描画されます。

### <a name="remarks"></a>Remarks

ボタンの`GetButtonStyle`スタイルを取得するには、メンバー関数を使用します。 完全なボタンスタイルの下位ワードは、ボタン固有のスタイルです。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

##  <a name="setcheck"></a>  CButton::SetCheck

オプションボタンまたはチェックボックスのチェック状態を設定またはリセットします。

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>パラメーター

*n*<br/>
チェックの状態を指定します。 このパラメーターには、次のいずれかを指定できます。

|[値]|説明|
|-----------|-------------|
|BST_UNCHECKED|ボタンの状態を [オフ] に設定します。|
|BST_CHECKED|ボタンの状態を [オン] に設定します。|
|BST_INDETERMINATE|ボタンの状態を [不確定] に設定します。 この値は、ボタンのスタイルが BS_3STATE または BS_AUTO3STATE の場合にのみ使用できます。|

### <a name="remarks"></a>Remarks

このメンバー関数は、プッシュボタンには影響しません。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

##  <a name="setcursor"></a>  CButton::SetCursor

このメンバー関数を呼び出して、新しいカーソルをボタンに関連付けます。

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>パラメーター

*hCursor*<br/>
カーソルのハンドル。

### <a name="return-value"></a>戻り値

以前にボタンに関連付けられたカーソルのハンドル。

### <a name="remarks"></a>Remarks

既定では、カーソルはボタンの表面に自動的に配置されます。 カーソルがボタンに対して大きすぎる場合は、いずれかの側でクリップされます。 次のような他の配置オプションを選択できます。

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

ボタンごとに4つのビットマップを使用する[cbitmapbutton](../../mfc/reference/cbitmapbutton-class.md)とは異なり、で`SetCursor`は、ボタンごとに1つのカーソルのみが使用されます。 このボタンが押されると、カーソルが下と右に移動したように見えます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

##  <a name="setdropdownstate"></a>  CButton::SetDropDownState

現在の分割ボタンコントロールのドロップダウン状態を設定します。

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*fDropDown*|からBST_DROPDOWNPUSHED の状態を設定する場合は TRUE。それ以外の場合は FALSE。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

分割ボタンコントロールには、BS_SPLITBUTTON または BS_DEFSPLITBUTTON というスタイルがあり、ボタンとその右側のドロップダウン矢印で構成されます。 詳細については、「[ボタンのスタイル](/windows/win32/Controls/button-styles)」を参照してください。 通常、ドロップダウンの状態は、ユーザーがドロップダウン矢印をクリックしたときに設定されます。 コントロールのドロップダウン状態をプログラムで設定するには、このメソッドを使用します。 ドロップダウン矢印は、状態を示すために影付きで描画されます。

このメソッドは、Windows SDK で説明されている[BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、分割ボタンコントロールにプログラムでアクセスするために使用される変数*m_splitButton*を定義しています。 この変数は、次の例で使用します。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>例

次のコード例では、分割ボタンコントロールの状態を設定して、ドロップダウン矢印がプッシュされたことを示しています。

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

##  <a name="setelevationrequired"></a>  CButton::SetElevationRequired

現在のボタンコントロールの状態をに`elevation required`設定します。これは、コントロールが管理者特権のセキュリティアイコンを表示するために必要です。

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*fElevationRequired*|から状態を設定`elevation required`する場合は TRUE、それ以外の場合は FALSE。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ボタンまたはコマンドリンクコントロールでアクションを実行するために管理者特権のセキュリティアクセス許可`elevation required`が必要な場合は、コントロールを状態に設定します。 その後、Windows によって、コントロールのユーザーアカウント制御 (UAC) シールドアイコンが表示されます。 詳細については、 [MSDN](https://go.microsoft.com/fwlink/p/?linkid=18507)の「ユーザーアカウント制御」を参照してください。

このメソッドは、Windows SDK で説明されている[BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield)メッセージを送信します。

##  <a name="seticon"></a>CButton:: SetIcon

このメンバー関数を呼び出して、新しいアイコンをボタンに関連付けます。

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>パラメーター

*hIcon*<br/>
アイコンのハンドル。

### <a name="return-value"></a>戻り値

以前にボタンに関連付けられていたアイコンのハンドル。

### <a name="remarks"></a>Remarks

既定では、アイコンがボタンの表面に自動的に配置されます。 アイコンがボタンに対して大きすぎる場合は、いずれかの側でクリップされます。 次のような他の配置オプションを選択できます。

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

ボタンごとに4つのビットマップを使用する[cbitmapbutton](../../mfc/reference/cbitmapbutton-class.md)とは異なり、で`SetIcon`は、ボタンごとに1つのアイコンのみが使用されます。 このボタンが押されると、アイコンが右にシフトされます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

##  <a name="setimagelist"></a>CButton:: SetImageList

`CButton`オブジェクトのイメージリストを設定するには、このメソッドを呼び出します。

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>パラメーター

*pbuttonImagelist*<br/>
新しいイメージリストへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK の [[ボタン](/windows/win32/controls/buttons)] セクションで説明されているように、BCM_SETIMAGELIST メッセージの機能をエミュレートします。

##  <a name="setnote"></a>  CButton::SetNote

現在のコマンドリンクコントロールのノートテキストを設定します。

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*lpszNote*|からコマンドリンクコントロールのノートテキストとして設定されている Unicode 文字列へのポインター。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンスタイルが BS_COMMANDLINK または BS_DEFCOMMANDLINK のコントロールでのみ使用します。

このメソッドは、Windows SDK で説明されている[BCM_SETNOTE](/windows/win32/Controls/bcm-setnote)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、コマンドリンクコントロールにプログラムでアクセスするために使用される変数*m_cmdLink*を定義します。 この変数は、次の例で使用します。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>例

次のコード例では、コマンドリンクコントロールのノートテキストを設定します。

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

##  <a name="setsplitglyph"></a>CButton:: SetSplitGlyph

指定したグリフを現在の分割ボタンコントロールに関連付けます。

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*chGlyph*|から分割ボタンのドロップダウン矢印として使用するグリフを指定する文字。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンスタイルが BS_SPLITBUTTON または BS_DEFSPLITBUTTON のコントロールでのみ使用してください。

グリフは、特定のフォントにおける文字の物理的な表現です。 *Chglyph*パラメーターはグリフとして使用されませんが、システム定義の一連のグリフからグリフを選択するために使用されます。 既定のドロップダウン矢印グリフは文字 "6" で指定され、Unicode 文字の黒い下向き三角形 (U + 25BC) に似ています。

このメソッドは、 `mask` `himlGlyph` BCSIF_GLYPH フラグと*chglyph*パラメーターを使用してメンバーを指定して[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体のメンバーを初期化し、その構造体を[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)メッセージに送信します。詳細については、Windows SDK を参照してください。

##  <a name="setsplitimagelist"></a>CButton:: SetSplitImageList

[イメージリスト](../../mfc/reference/cimagelist-class.md)を現在の分割ボタンコントロールに関連付けます。

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pSplitImageList*|から現在の分割ボタンコントロールに割り当てる[CImageList](../../mfc/reference/cimagelist-class.md)オブジェクトへのポインター。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンスタイルが BS_SPLITBUTTON または BS_DEFSPLITBUTTON のコントロールでのみ使用します。

このメソッドは、 `mask` `himlGlyph` BCSIF_IMAGE フラグと*pSplitImageList*パラメーターを使用してメンバーを指定して、 [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体のメンバーを初期化し、その構造体を[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)に送信します。Windows SDK で説明されているメッセージ。

##  <a name="setsplitinfo"></a>  CButton::SetSplitInfo

ウィンドウが現在の分割ボタンコントロールを描画する方法を決定するパラメーターを指定します。

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pInfo*|から現在の分割ボタンコントロールを定義する[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体へのポインター。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンスタイルが BS_SPLITBUTTON または BS_DEFSPLITBUTTON のコントロールでのみ使用します。

このメソッドは、Windows SDK で説明されている[BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、分割`m_splitButton`ボタンコントロールにプログラムでアクセスするために使用される変数を定義します。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>例

次のコード例では、分割ボタンのドロップダウン矢印に使用されるグリフを変更します。 この例では、上向き三角形のグリフを既定の下向き三角形のグリフに置き換えます。 表示されるグリフは、 `himlGlyph` `BUTTON_SPLITINFO`構造体のメンバーで指定した文字によって異なります。 下向き三角形のグリフは文字 ' 6 ' によって指定され、上向き三角形のグリフは文字 ' 5 ' によって指定されます。 比較については、「 [CButton:: SetSplitGlyph](#setsplitglyph)」の便利なメソッドを参照してください。

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

##  <a name="setsplitsize"></a>CButton:: SetSplitSize

現在の分割ボタンコントロールのドロップダウンコンポーネントの外接する四角形を設定します。

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*pSize*|から外接する四角形を記述する[サイズ](/windows/win32/api/windef/ns-windef-size)構造体へのポインター。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンスタイルが BS_SPLITBUTTON または BS_DEFSPLITBUTTON のコントロールでのみ使用します。

分割ボタンコントロールが展開されると、リストコントロールやページャーコントロールなどのドロップダウンコンポーネントが表示されます。 このメソッドは、ドロップダウンコンポーネントを含む外接する四角形のサイズを指定します。

このメソッドは、 `mask` `size` BCSIF_SIZE フラグと*pSize*パラメーターを持つメンバーを使用して[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体のメンバーを初期化し、 [BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)メッセージにその構造体を送信します。については、Windows SDK を参照してください。

### <a name="example"></a>例

次のコード例では、分割`m_splitButton`ボタンコントロールにプログラムでアクセスするために使用される変数を定義します。 この変数は、次の例で使用します。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>例

次のコード例では、分割ボタンのドロップダウン矢印のサイズを2倍にしています。

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

##  <a name="setsplitstyle"></a>CButton:: SetSplitStyle

現在の分割ボタンコントロールのスタイルを設定します。

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*uSplitStyle*|から分割ボタンのスタイルのビットごとの組み合わせ。 詳細については、 `uSplitStyle` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体のメンバーを参照してください。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ボタンスタイルが BS_SPLITBUTTON または BS_DEFSPLITBUTTON のコントロールでのみ使用します。

分割ボタンのスタイルでは、ウィンドウが分割ボタンアイコンを描画する配置、縦横比、およびグラフィカルな形式を指定します。 詳細については、 `uSplitStyle` [BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体のメンバーを参照してください。

このメソッドは、 `mask` `uSplitStyle` BCSIF_STYLE フラグと*usplitstyle*パラメーターを持つメンバーを使用して[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)構造体のメンバーを初期化し、その構造体を[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)に送信します。Windows SDK で説明されているメッセージ。

### <a name="example"></a>例

次のコード例では、分割`m_splitButton`ボタンコントロールにプログラムでアクセスするために使用される変数を定義します。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>例

次のコード例では、分割ボタンのドロップダウン矢印のスタイルを設定します。 BCSS_ALIGNLEFT スタイルでは、ボタンの左側に矢印が表示され、ボタンのサイズを変更すると、BCSS_STRETCH スタイルによってドロップダウンの矢印の比率が保持されます。

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

##  <a name="setstate"></a>  CButton::SetState

ボタンコントロールを強調表示するかどうかを設定します。

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>パラメーター

*bHighlight 表示*<br/>
ボタンを強調表示するかどうかを指定します。 0以外の値を指定すると、ボタンが強調表示されます。0の値を指定すると、強調表示が解除されます。

### <a name="remarks"></a>Remarks

強調表示は、ボタンコントロールの外部に影響します。 オプションボタンまたはチェックボックスのチェックの状態には影響しません。

ボタンコントロールは、ユーザーがマウスの左ボタンをクリックして保持すると、自動的に強調表示されます。 ユーザーがマウスボタンを放すと、強調表示が削除されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

##  <a name="settextmargin"></a>  CButton::SetTextMargin

`CButton`オブジェクトのテキストの余白を設定するには、このメソッドを呼び出します。

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>パラメーター

*pmargin*<br/>
新しいテキスト余白へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK の [[ボタン](/windows/win32/controls/buttons)] セクションで説明されているように、BCM_SETTEXTMARGIN メッセージの機能をエミュレートします。

## <a name="see-also"></a>関連項目

[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox クラス](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit クラス](../../mfc/reference/cedit-class.md)<br/>
[CListBox クラス](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar クラス](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic クラス](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton クラス](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog クラス](../../mfc/reference/cdialog-class.md)
