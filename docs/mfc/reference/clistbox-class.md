---
title: CListBox クラス
description: MFC の CListBox クラスとそのメンバー関数の説明。
ms.date: 01/22/2020
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
helpviewer_keywords:
- CListBox [MFC], CListBox
- CListBox [MFC], AddString
- CListBox [MFC], CharToItem
- CListBox [MFC], CompareItem
- CListBox [MFC], Create
- CListBox [MFC], DeleteItem
- CListBox [MFC], DeleteString
- CListBox [MFC], Dir
- CListBox [MFC], DrawItem
- CListBox [MFC], FindString
- CListBox [MFC], FindStringExact
- CListBox [MFC], GetAnchorIndex
- CListBox [MFC], GetCaretIndex
- CListBox [MFC], GetCount
- CListBox [MFC], GetCurSel
- CListBox [MFC], GetHorizontalExtent
- CListBox [MFC], GetItemData
- CListBox [MFC], GetItemDataPtr
- CListBox [MFC], GetItemHeight
- CListBox [MFC], GetItemRect
- CListBox [MFC], GetListBoxInfo
- CListBox [MFC], GetLocale
- CListBox [MFC], GetSel
- CListBox [MFC], GetSelCount
- CListBox [MFC], GetSelItems
- CListBox [MFC], GetText
- CListBox [MFC], GetTextLen
- CListBox [MFC], GetTopIndex
- CListBox [MFC], InitStorage
- CListBox [MFC], InsertString
- CListBox [MFC], ItemFromPoint
- CListBox [MFC], MeasureItem
- CListBox [MFC], ResetContent
- CListBox [MFC], SelectString
- CListBox [MFC], SelItemRange
- CListBox [MFC], SetAnchorIndex
- CListBox [MFC], SetCaretIndex
- CListBox [MFC], SetColumnWidth
- CListBox [MFC], SetCurSel
- CListBox [MFC], SetHorizontalExtent
- CListBox [MFC], SetItemData
- CListBox [MFC], SetItemDataPtr
- CListBox [MFC], SetItemHeight
- CListBox [MFC], SetLocale
- CListBox [MFC], SetSel
- CListBox [MFC], SetTabStops
- CListBox [MFC], SetTopIndex
- CListBox [MFC], VKeyToItem
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
ms.openlocfilehash: 5c3337641dcfc720a5f9fbccf5bb0614e97c3b54
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518427"
---
# <a name="clistbox-class"></a>CListBox クラス

Windows のリスト ボックスの機能を提供します。

## <a name="syntax"></a>構文

```
class CListBox : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|[名前]|説明|
|----------|-----------------|
|[CListBox:: CListBox](#clistbox)|`CListBox` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|[名前]|説明|
|----------|-----------------|
|[CListBox::AddString](#addstring)|リストボックスに文字列を追加します。|
|[CListBox:: CharToItem](#chartoitem)|をオーバーライドして、文字列を持たないオーナー描画リストボックスにカスタム WM_CHAR 処理を提供します。|
|[CListBox:: CompareItem](#compareitem)|並べ替えられたオーナー描画リストボックス内の新しい項目の位置を確認するために、フレームワークによって呼び出されます。|
|[CListBox:: Create](#create)|Windows のリストボックスを作成し、`CListBox` オブジェクトにアタッチします。|
|[CListBox::D eleteItem](#deleteitem)|ユーザーがオーナー描画リストボックスから項目を削除したときに、フレームワークによって呼び出されます。|
|[CListBox::D eleteString](#deletestring)|リストボックスから文字列を削除します。|
|[CListBox::D ir](#dir)|ファイル名、ドライブ、またはその両方を現在のディレクトリからリストボックスに追加します。|
|[CListBox::D rawItem](#drawitem)|オーナー描画リストボックスの視覚的な側面が変化したときにフレームワークによって呼び出されます。|
|[CListBox:: FindString](#findstring)|リストボックス内の文字列を検索します。|
|[CListBox::FindStringExact](#findstringexact)|指定した文字列と一致する最初のリストボックス文字列を検索します。|
|[CListBox::GetAnchorIndex](#getanchorindex)|リストボックス内の現在のアンカー項目の0から始まるインデックスを取得します。|
|[CListBox::GetCaretIndex](#getcaretindex)|複数選択リストボックス内にフォーカスを持つ四角形を持つ項目のインデックスを確認します。|
|[CListBox::GetCount](#getcount)|リストボックス内の文字列の数を返します。|
|[CListBox::GetCurSel](#getcursel)|リストボックス内で現在選択されている文字列の0から始まるインデックスを返します。|
|[CListBox:: GetHorizontalExtent](#gethorizontalextent)|リストボックスを水平方向にスクロールできる幅 (ピクセル単位) を返します。|
|[CListBox:: GetItemData](#getitemdata)|リストボックス項目に関連付けられている値を返します。|
|[CListBox:: GetItemDataPtr](#getitemdataptr)|リストボックス項目へのポインターを返します。|
|[CListBox:: GetItemHeight](#getitemheight)|リストボックス内の項目の高さを決定します。|
|[CListBox::GetItemRect](#getitemrect)|現在表示されているリストボックス項目の外接する四角形を返します。|
|[CListBox::GetListBoxInfo](#getlistboxinfo)|列あたりの項目数を取得します。|
|[CListBox::GetLocale](#getlocale)|リストボックスのロケール識別子を取得します。|
|[CListBox:: GetSel](#getsel)|リストボックス項目の選択状態を返します。|
|[CListBox::GetSelCount](#getselcount)|複数選択のリストボックスで現在選択されている文字列の数を返します。|
|[CListBox:: GetSelItems](#getselitems)|リストボックスで現在選択されている文字列のインデックスを返します。|
|[CListBox:: GetText](#gettext)|リストボックス項目をバッファーにコピーします。|
|[CListBox::GetTextLen](#gettextlen)|リストボックス項目の長さをバイト単位で返します。|
|[CListBox::GetTopIndex](#gettopindex)|リストボックス内の最初に表示された文字列のインデックスを返します。|
|[CListBox:: InitStorage](#initstorage)|リストボックスの項目および文字列のメモリブロックを事前します。|
|[CListBox::InsertString](#insertstring)|リストボックス内の特定の位置に文字列を挿入します。|
|[CListBox::ItemFromPoint](#itemfrompoint)|ポイントに最も近いリストボックス項目のインデックスを返します。|
|[CListBox:: MeasureItem](#measureitem)|オーナー描画リストボックスが作成され、リストボックスのディメンションを決定するときに、フレームワークによって呼び出されます。|
|[CListBox::ResetContent](#resetcontent)|リストボックスからすべてのエントリを削除します。|
|[CListBox:: SelectString](#selectstring)|単一選択リストボックス内の文字列を検索して選択します。|
|[CListBox::SelItemRange](#selitemrange)|複数選択リストボックス内の文字列の範囲を選択または選択解除します。|
|[CListBox::SetAnchorIndex](#setanchorindex)|複数選択のリストボックスでアンカーを設定して、拡張選択を開始します。|
|[CListBox::SetCaretIndex](#setcaretindex)|複数選択リストボックス内の指定したインデックス位置にある項目にフォーカスを示す四角形を設定します。|
|[CListBox:: SetColumnWidth](#setcolumnwidth)|複数列のリストボックスの列幅を設定します。|
|[CListBox::SetCurSel](#setcursel)|リストボックスの文字列を選択します。|
|[CListBox:: SetHorizontalExtent](#sethorizontalextent)|リストボックスを水平方向にスクロールできる幅 (ピクセル単位) を設定します。|
|[CListBox:: SetItemData](#setitemdata)|リストボックス項目に関連付けられた値を設定します。|
|[CListBox:: SetItemDataPtr](#setitemdataptr)|リストボックス項目へのポインターを設定します。|
|[CListBox:: SetItemHeight](#setitemheight)|リストボックス内の項目の高さを設定します。|
|[CListBox::SetLocale](#setlocale)|リストボックスのロケール識別子を設定します。|
|[CListBox:: SetSel](#setsel)|複数選択リストボックス内のリストボックス項目を選択または選択解除します。|
|[CListBox:: SetTabStops](#settabstops)|リストボックス内のタブストップ位置を設定します。|
|[CListBox::SetTopIndex](#settopindex)|リストボックス内で最初に表示される文字列の0から始まるインデックスを設定します。|
|[CListBox::VKeyToItem](#vkeytoitem)|をオーバーライドして、LBS_WANTKEYBOARDINPUT スタイルセットを持つリストボックスにカスタムの WM_KEYDOWN 処理を提供します。|

## <a name="remarks"></a>Remarks

リストボックスには、ユーザーが表示および選択できる、ファイル名などの項目の一覧が表示されます。

1つの選択リストボックスでは、ユーザーが選択できる項目は1つだけです。 複数選択のリストボックスでは、項目の範囲を選択できます。 ユーザーが項目を選択すると、その項目が強調表示され、リストボックスが親ウィンドウに通知メッセージを送信します。

リストボックスを作成するには、ダイアログテンプレートを使用するか、コード内で直接作成します。 これを直接作成するには、`CListBox` オブジェクトを作成し、 [create](#create) member 関数を呼び出して、Windows のリストボックスコントロールを作成し、それを `CListBox` オブジェクトにアタッチします。 ダイアログテンプレートでリストボックスを使用するには、ダイアログボックスクラスでリストボックス変数を宣言し、ダイアログボックスクラスの `DoDataExchange` 関数で `DDX_Control` を使用して、メンバー変数をコントロールに接続します。 (これは、ダイアログボックスクラスにコントロール変数を追加すると自動的に行われます)。

構築は、`CListBox`から派生したクラスの1つの手順で構成されます。 派生クラスのコンストラクターを記述し、コンストラクター内から `Create` を呼び出します。

リストボックスから親 (通常は、 [CDialog](../../mfc/reference/cdialog-class.md)から派生したクラス) に送信される Windows 通知メッセージを処理する場合は、各メッセージの親クラスにメッセージマップエントリとメッセージハンドラーメンバー関数を追加します。

各メッセージマップエントリには、次の形式があります。

`ON_Notification( id, memberFxn )`

ここで `id` 通知を送信するリストボックスコントロールの子ウィンドウ ID を指定します。 `memberFxn` は、通知を処理するために記述した親メンバー関数の名前です。

親の関数プロトタイプは次のとおりです。

`afx_msg void memberFxn( );`

次に示すのは、潜在的なメッセージマップエントリの一覧と、親に送信される可能性のあるケースの説明です。

- ユーザーがリストボックス内の文字列をダブルクリックする ON_LBN_DBLCLK ます。 [LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルのリストボックスのみが、この通知メッセージを送信します。

- ON_LBN_ERRSPACE リストボックスは、要求を満たすのに十分なメモリを割り当てることができません。

- リストボックス ON_LBN_KILLFOCUS、入力フォーカスが失われています。

- ON_LBN_SELCANCEL 現在のリストボックスの選択はキャンセルされます。 このメッセージは、リストボックスに LBS_NOTIFY スタイルがある場合にのみ送信されます。

- リストボックスの選択範囲が変更された ON_LBN_SELCHANGE ます。 この通知は、選択が[CListBox:: SetCurSel](#setcursel)メンバー関数によって変更された場合には送信されません。 この通知は、LBS_NOTIFY スタイルを持つリストボックスにのみ適用されます。 選択が変更されない場合でも、ユーザーが方向キーを押すたびに、複数選択のリストボックスに対して LBN_SELCHANGE 通知メッセージが送信されます。

- リストボックスが入力フォーカスを受け取った ON_LBN_SETFOCUS ます。

- 文字列がない所有者描画リストボックス ON_WM_CHARTOITEM、WM_CHAR メッセージを受信します。

- LBS_WANTKEYBOARDINPUT スタイルのリストボックス ON_WM_VKEYTOITEM、WM_KEYDOWN メッセージを受信します。

ダイアログボックス内で (ダイアログリソースを使用して) `CListBox` オブジェクトを作成すると、ユーザーがダイアログボックスを閉じたときに `CListBox` オブジェクトが自動的に破棄されます。

ウィンドウ内に `CListBox` オブジェクトを作成する場合は、`CListBox` オブジェクトを破棄することが必要になる場合があります。 スタックに `CListBox` オブジェクトを作成すると、そのオブジェクトは自動的に破棄されます。 **新しい**関数を使用してヒープに `CListBox` オブジェクトを作成する場合、ユーザーが親ウィンドウを閉じたときに破棄するには、オブジェクトに対して**delete**を呼び出す必要があります。

`CListBox` オブジェクトにメモリを割り当てる場合は、`CListBox` デストラクターをオーバーライドして割り当てを破棄します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[から派生しているのではない](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>要件

**ヘッダー:** afxwin.h

##  <a name="addstring"></a>  CListBox::AddString

リストボックスに文字列を追加します。

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>パラメーター

*lpszItem*<br/>
は、追加する null で終わる文字列を指します。

### <a name="return-value"></a>戻り値

リストボックス内の文字列の0から始まるインデックス。 エラーが発生した場合、戻り値は LB_ERR ます。新しい文字列を格納するのに十分な領域がない場合、戻り値は LB_ERRSPACE ます。

### <a name="remarks"></a>Remarks

リストボックスが[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルで作成されなかった場合、文字列はリストの末尾に追加されます。 それ以外の場合は、文字列がリストに挿入され、リストが並べ替えられます。 リストボックスが LBS_SORT スタイルを使用して作成され、 [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルではない場合、フレームワークは `CompareItem` メンバー関数の1回以上の呼び出しによってリストを並べ替えます。

[Insertstring](#insertstring)を使用して、リストボックス内の特定の位置に文字列を挿入します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

##  <a name="chartoitem"></a>CListBox:: CharToItem

リストボックスの親ウィンドウがリストボックスから WM_CHARTOITEM メッセージを受信したときに、フレームワークによって呼び出されます。

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>パラメーター

*nKey*<br/>
ユーザーが入力した文字の ANSI コード。

*nIndex*<br/>
リストボックスカレットの現在位置。

### <a name="return-value"></a>戻り値

追加のアクションがない場合は-1 または-2、キーストロークの既定のアクションを実行するリストボックス項目のインデックスを指定する場合は負以外の数値を返します。 既定の実装では、-1 が返されます。

### <a name="remarks"></a>Remarks

WM_CHARTOITEM メッセージは WM_CHAR メッセージを受信したときにリストボックスによって送信されますが、リストボックスがこれらの条件をすべて満たしている場合に限ります。

- はオーナー描画リストボックスです。

- には[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルが設定されていません。

- 少なくとも1つの項目があります。

この関数を自分で呼び出すことは避けてください。 キーボードメッセージの独自のカスタム処理を提供するには、この関数をオーバーライドします。

オーバーライドでは、実行したアクションをフレームワークに通知するために値を返す必要があります。 戻り値-1 または-2 は、項目を選択するすべての要素を処理したことを示し、リストボックスによるそれ以上の操作は必要ありません。 -1 または-2 を返す前に、選択を設定するか、カレットまたはその両方を移動できます。 選択を設定するには、 [Setcursel](#setcursel)または[SetSel](#setsel)を使用します。 カレットを移動するには、 [SetCaretIndex](#setcaretindex)を使用します。

戻り値が0以上の場合は、リストボックス内の項目のインデックスを指定し、リストボックスが、指定された項目のキーストロークの既定の動作を実行することを示します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

##  <a name="clistbox"></a>CListBox:: CListBox

`CListBox` オブジェクトを構築します。

```
CListBox();
```

### <a name="remarks"></a>Remarks

`CListBox` オブジェクトを作成するには、2つの手順を実行します。 まず、コンストラクター `ClistBox` 呼び出し、次に `Create`を呼び出します。これにより、Windows のリストボックスが初期化され、`CListBox`にアタッチされます。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

##  <a name="compareitem"></a>CListBox:: CompareItem

並べ替えられたオーナー描画リストボックス内の新しい項目の相対位置を決定するために、フレームワークによって呼び出されます。

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>パラメーター

*lpCompareItemStruct*<br/>
`COMPAREITEMSTRUCT` 構造体への long ポインター。

### <a name="return-value"></a>戻り値

[COMPAREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-compareitemstruct)構造体に記述されている2つの項目の相対位置を示します。 次のいずれかの値を指定できます。

|Value|説明|
|-----------|-------------|
|-1|項目1は項目2の前に並べ替えられます。|
|0|項目1と項目2は同じように並べ替えられます。|
|1|項目1は項目2の後に並べ替えます。|

`COMPAREITEMSTRUCT` 構造の説明については、「 [CWnd:: OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) 」を参照してください。

### <a name="remarks"></a>Remarks

既定では、このメンバー関数は何も行いません。 LBS_SORT スタイルを使用してオーナー描画リストボックスを作成する場合は、このメンバー関数をオーバーライドして、リストボックスに追加された新しい項目の並べ替えのフレームワークをサポートする必要があります。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

##  <a name="create"></a>  CListBox::Create

Windows のリストボックスを作成し、`CListBox` オブジェクトにアタッチします。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
リストボックスのスタイルを指定します。 ボックスに、[リストボックススタイル](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)の任意の組み合わせを適用します。

*rect*<br/>
リストボックスのサイズと位置を指定します。 `CRect` オブジェクトまたは `RECT` 構造のいずれかになります。

*pParentWnd*<br/>
リストボックスの親ウィンドウ (通常は `CDialog` オブジェクト) を指定します。 NULL にすることはできません。

*nID*<br/>
リストボックスのコントロール ID を指定します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

`CListBox` オブジェクトを作成するには、2つの手順を実行します。 まず、コンストラクターを呼び出し、次に `Create`を呼び出します。これにより、Windows のリストボックスが初期化され、`CListBox` オブジェクトにアタッチされます。

`Create` 実行すると、Windows は、 [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)、 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)、 [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)、および[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)メッセージをリストボックスコントロールに送信します。

これらのメッセージは、既定では `CWnd` 基本クラスの[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)、 [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)、 [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)、および[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)メンバー関数によって処理されます。 既定のメッセージ処理を拡張するには、`CListBox`からクラスを派生させ、メッセージマップを新しいクラスに追加して、前のメッセージハンドラーメンバー関数をオーバーライドします。 たとえば、新しいクラスに必要な初期化を実行するために、`OnCreate`をオーバーライドします。

次の[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)をリストボックスコントロールに適用します。

- 常に WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED はまれ

- 垂直スクロールバーを追加する WS_VSCROLL

- 水平スクロールバーを追加する WS_HSCROLL

- グループコントロールに WS_GROUP

- このコントロールへのタブ移動を許可する WS_TABSTOP

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

##  <a name="deleteitem"></a>  CListBox::DeleteItem

ユーザーがオーナー描画 `CListBox` オブジェクトから項目を削除するか、リストボックスを破棄すると、フレームワークによって呼び出されます。

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>パラメーター

*lpDeleteItemStruct*<br/>
削除された項目に関する情報を格納している Windows [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)構造体への long ポインター。

### <a name="remarks"></a>Remarks

この関数の既定の実装は、何も行いません。 この関数をオーバーライドして、必要に応じてオーナー描画リストボックスを再描画します。

`DELETEITEMSTRUCT` 構造の説明については、「 [CWnd:: OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) 」を参照してください。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

##  <a name="deletestring"></a>  CListBox::DeleteString

リストボックスから、[位置] の*項目を削除*します。

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
削除する文字列の0から始まるインデックスを指定します。

### <a name="return-value"></a>戻り値

リストに残っている文字列の数。 *NIndex*がリスト内の項目数より大きいインデックスを指定している場合、戻り値は LB_ERR です。

### <a name="remarks"></a>Remarks

*これで*、すべての項目が1つ下に移動します。 たとえば、リストボックスに2つの項目が含まれている場合、最初の項目を削除すると、残りの項目が最初の位置になります。 1番目の位置の項目の場合は、[ *nIndex*] = 0 になります。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

##  <a name="dir"></a>CListBox::D ir

ファイル名、ドライブ、またはその両方のリストをリストボックスに追加します。

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>パラメーター

*attr*<br/>
`CFile::GetStatu`[s](../../mfc/reference/cfile-class.md#getstatus)に記述されている**列挙**値の任意の組み合わせ、または次の値の任意の組み合わせを指定できます。

|Value|説明|
|-----------|-------------|
|0x0000|ファイルの読み取りまたは書き込みを行うことができます。|
|0x0001|ファイルはから読み取ることができますが、に書き込むことはできません。|
|0x0002|ファイルは非表示であり、ディレクトリの一覧に表示されません。|
|0x0004|ファイルはシステムファイルです。|
|0x0010|*Lpszwildcard*によって指定された名前は、ディレクトリを指定します。|
|0x0020|ファイルはアーカイブされています。|
|0x4000|*Lpszwildcard*によって指定された名前に一致するすべてのドライブを含めます。|
|0x8000|排他フラグ。 排他フラグが設定されている場合は、指定された種類のファイルだけが表示されます。 それ以外の場合は、指定された種類のファイルが "normal" ファイルに加えて一覧表示されます。|

*lpszWildCard*<br/>
ファイル指定文字列を指します。 文字列には、ワイルドカード (たとえば、*.\*) を含めることができます。

### <a name="return-value"></a>戻り値

リストに追加された最後のファイル名の0から始まるインデックス。 エラーが発生した場合、戻り値は LB_ERR ます。新しい文字列を格納するのに十分な領域がない場合、戻り値は LB_ERRSPACE ます。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

##  <a name="drawitem"></a>CListBox::D rawItem

オーナー描画リストボックスの視覚的な側面が変化したときにフレームワークによって呼び出されます。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>パラメーター

*lpDrawItemStruct*<br/>
必要な描画の種類に関する情報を格納している[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)構造体への long ポインター。

### <a name="remarks"></a>Remarks

`DRAWITEMSTRUCT` 構造体の `itemAction` メンバーと `itemState` メンバーは、実行される描画アクションを定義します。

既定では、このメンバー関数は何も行いません。 オーナー描画 `CListBox` オブジェクトの描画を実装するには、このメンバー関数をオーバーライドします。 このメンバー関数が終了する前に、アプリケーションでは、 *lpDrawItemStruct*で指定された表示コンテキスト用に選択されたすべてのグラフィックスデバイスインターフェイス (GDI) オブジェクトを復元する必要があります。

`DRAWITEMSTRUCT` 構造の説明については、「 [CWnd:: OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) 」を参照してください。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

##  <a name="findstring"></a>CListBox:: FindString

リストボックスの選択を変更せずに、指定したプレフィックスを含むリストボックス内の最初の文字列を検索します。

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>パラメーター

*nStartAfter*<br/>
最初に検索される項目の前にある項目の0から始まるインデックスを格納します。 検索がリストボックスの下部に到達すると、リストボックスの一番上から*Nstartafter*によって指定された項目に戻ります。 *Nstartafter*が-1 の場合、リストボックス全体が最初から検索されます。

*lpszItem*<br/>
検索するプレフィックスを含む、null で終わる文字列を指します。 検索は大文字と小文字が区別されないため、この文字列には大文字と小文字の任意の組み合わせを含めることができます。

### <a name="return-value"></a>戻り値

一致する項目の0から始まるインデックス番号。検索に失敗した場合は LB_ERR。

### <a name="remarks"></a>Remarks

文字列を検索して選択するには、 [Selectstring](#selectstring)メンバー関数を使用します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

##  <a name="findstringexact"></a>CListBox:: FindStringExact

*LpszFind*で指定した文字列に一致する最初のリストボックス文字列を検索します。

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>パラメーター

*nIndexStart*<br/>
最初に検索する項目の前にある項目の0から始まるインデックスを指定します。 検索がリストボックスの下部に到達すると、リストボックスの一番上から、 *Nindexstart*によって指定された項目に戻ります。 *Nindexstart*が-1 の場合、リストボックス全体が最初から検索されます。

*lpszFind*<br/>
Null で終わる検索対象の文字列を指します。 この文字列には、拡張子を含む完全なファイル名を含めることができます。 検索では大文字と小文字が区別されないので、文字列には大文字と小文字の任意の組み合わせを含めることができます。

### <a name="return-value"></a>戻り値

一致する項目のインデックス。検索に失敗した場合は LB_ERR。

### <a name="remarks"></a>Remarks

リストボックスがオーナー描画スタイルを使用して作成され、 [LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルが指定されていない場合、`FindStringExact` メンバー関数は、ダブルワード値と*lpszFind*の値を照合しようとします。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

##  <a name="getanchorindex"></a>  CListBox::GetAnchorIndex

リストボックス内の現在のアンカー項目の0から始まるインデックスを取得します。

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>戻り値

成功した場合は、現在のアンカー項目のインデックス。それ以外の場合は LB_ERR。

### <a name="remarks"></a>Remarks

複数選択のリストボックスでは、アンカー項目は、連続して選択された項目のブロックの最初または最後の項目です。

### <a name="example"></a>使用例

  「 [CListBox:: SetAnchorIndex](#setanchorindex)」の例を参照してください。

##  <a name="getcaretindex"></a>  CListBox::GetCaretIndex

複数選択リストボックス内にフォーカスを持つ四角形を持つ項目のインデックスを確認します。

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>戻り値

リストボックス内でフォーカスを示す四角形を持つ項目の0から始まるインデックス。 リストボックスが単一選択リストボックスの場合、戻り値は選択されている項目のインデックス (存在する場合) です。

### <a name="remarks"></a>Remarks

項目は選択できない場合もあります。

### <a name="example"></a>使用例

  「 [CListBox:: SetCaretIndex](#setcaretindex)」の例を参照してください。

##  <a name="getcount"></a>  CListBox::GetCount

リストボックス内の項目の数を取得します。

```
int GetCount() const;
```

### <a name="return-value"></a>戻り値

リストボックス内の項目の数。エラーが発生した場合は LB_ERR。

### <a name="remarks"></a>Remarks

返されるカウントは、最後の項目のインデックス値よりも1だけ大きくなります (インデックスは0から始まります)。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

##  <a name="getcursel"></a>  CListBox::GetCurSel

単一選択リストボックス内で現在選択されている項目 (存在する場合) の0から始まるインデックスを取得します。

```
int GetCurSel() const;
```

### <a name="return-value"></a>戻り値

単一選択リストボックスの場合、現在選択されている項目の0から始まるインデックス。 現在選択されている項目がない場合は LB_ERR です。

複数選択のリストボックスで、フォーカスのある項目のインデックス。

### <a name="remarks"></a>Remarks

複数選択のリストボックスに対して `GetCurSel` を呼び出さないでください。 代わりに、 [CListBox:: GetSelItems](#getselitems)を使用してください。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

##  <a name="gethorizontalextent"></a>CListBox:: GetHorizontalExtent

リストボックスから水平方向にスクロールできる幅 (ピクセル単位) を取得します。

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>戻り値

リストボックスのスクロール可能な幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

これは、リストボックスに水平スクロールバーがある場合にのみ適用されます。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

##  <a name="getitemdata"></a>  CListBox::GetItemData

指定されたリストボックス項目に関連付けられた、アプリケーションが提供したダブルワード値を取得します。

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
リストボックス内の項目の0から始まるインデックスを指定します。

### <a name="return-value"></a>戻り値

項目に関連付けられている値。エラーが発生した場合は LB_ERR。

### <a name="remarks"></a>Remarks

ダブルワード値は、 [SetItemData](#setitemdata)呼び出しの*dwItemData*パラメーターでした。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

##  <a name="getitemdataptr"></a>  CListBox::GetItemDataPtr

指定されたリストボックス項目に関連付けられた、アプリケーションが提供した32ビット値をポインターとして取得します (**void** <strong>\*</strong>)。

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
リストボックス内の項目の0から始まるインデックスを指定します。

### <a name="return-value"></a>戻り値

ポインターを取得します。エラーが発生した場合は-1 を取得します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

##  <a name="getitemheight"></a>CListBox:: GetItemHeight

リストボックス内の項目の高さを決定します。

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
リストボックス内の項目の0から始まるインデックスを指定します。 このパラメーターは、リストボックスに LBS_OWNERDRAWVARIABLE スタイルが指定されている場合にのみ使用されます。それ以外の場合は0に設定する必要があります。

### <a name="return-value"></a>戻り値

リストボックス内の項目の高さ (ピクセル単位)。 リストボックスに[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルがある場合、戻り値は、 *nIndex*によって指定された項目の高さになります。 エラーが発生した場合、戻り値は LB_ERR です。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

##  <a name="getitemrect"></a>  CListBox::GetItemRect

リストボックスウィンドウに現在表示されているリストボックス項目の境界となる四角形の寸法を取得します。

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
項目の0から始まるインデックスを指定します。

*lpRect*<br/>
項目のリストボックスクライアント座標を受け取る[RECT 構造体](/windows/win32/api/windef/ns-windef-rect)への long ポインターを指定します。

### <a name="return-value"></a>戻り値

エラーが発生した場合は LB_ERR します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

##  <a name="getlistboxinfo"></a>  CListBox::GetListBoxInfo

列あたりの項目数を取得します。

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>戻り値

`CListBox` オブジェクトの列あたりの項目数。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [LB_GETLISTBOXINFO](/windows/win32/Controls/lb-getlistboxinfo)メッセージの機能をエミュレートします。

##  <a name="getlocale"></a>  CListBox::GetLocale

リストボックスによって使用されるロケールを取得します。

```
LCID GetLocale() const;
```

### <a name="return-value"></a>戻り値

リストボックス内の文字列のロケール識別子 (LCID) 値。

### <a name="remarks"></a>Remarks

たとえば、ロケールは、並べ替えられたリストボックス内の文字列の並べ替え順序を決定するために使用されます。

### <a name="example"></a>使用例

  「 [CListBox:: SetLocale](#setlocale)」の例を参照してください。

##  <a name="getsel"></a>CListBox:: GetSel

項目の選択状態を取得します。

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
項目の0から始まるインデックスを指定します。

### <a name="return-value"></a>戻り値

指定した項目が選択されている場合は正の数値。それ以外の場合は0になります。 エラーが発生した場合、戻り値は LB_ERR です。

### <a name="remarks"></a>Remarks

このメンバー関数は、単一選択と複数選択のリストボックスの両方で動作します。

現在選択されているリストボックス項目のインデックスを取得するには、[ [CListBox:: GetCurSel](#getcursel)] を使用します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

##  <a name="getselcount"></a>  CListBox::GetSelCount

複数選択リストボックス内の選択された項目の合計数を取得します。

```
int GetSelCount() const;
```

### <a name="return-value"></a>戻り値

リストボックス内の選択された項目の数。 リストボックスが単一選択リストボックスの場合、戻り値は LB_ERR です。

### <a name="example"></a>使用例

  「 [CListBox:: GetSelItems](#getselitems)」の例を参照してください。

##  <a name="getselitems"></a>CListBox:: GetSelItems

複数選択リストボックス内の選択された項目の項目数を指定する整数の配列をバッファーに格納します。

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>パラメーター

*nMaxItems*<br/>
項目番号がバッファーに配置される、選択された項目の最大数を指定します。

*rgIndex*<br/>
*NMaxItems*で指定された整数の数に対して十分な大きさのバッファーへのポインターを指定します。

### <a name="return-value"></a>戻り値

バッファーに配置された実際の項目数。 リストボックスが単一選択リストボックスの場合、戻り値は `LB_ERR`です。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

##  <a name="gettext"></a>  CListBox::GetText

リストボックスから文字列を取得します。

```
int GetText(
    int nIndex,
    LPTSTR lpszBuffer) const;

void GetText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
取得する文字列の0から始まるインデックスを指定します。

*lpszBuffer*<br/>
は、文字列を受け取るバッファーを指します。 バッファーには、文字列と終端の null 文字に十分な領域が必要です。 文字列のサイズは、`GetTextLen` メンバー関数を呼び出すことによって事前に決定できます。

*rString*<br/>
`CString` オブジェクトへの参照。

### <a name="return-value"></a>戻り値

文字列の長さ (バイト単位)。終端の null 文字は除外されます。 *NIndex*で有効なインデックスが指定されていない場合、戻り値は LB_ERR になります。

### <a name="remarks"></a>Remarks

このメンバー関数の2番目の形式は、`CString` オブジェクトに文字列テキストを格納します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

##  <a name="gettextlen"></a>  CListBox::GetTextLen

リストボックス項目内の文字列の長さを取得します。

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
文字列の0から始まるインデックスを指定します。

### <a name="return-value"></a>戻り値

終端の null 文字を除く、文字列の長さ (文字数)。 *NIndex*で有効なインデックスが指定されていない場合、戻り値は LB_ERR になります。

### <a name="example"></a>使用例

  「 [CListBox:: GetText](#gettext)」の例を参照してください。

##  <a name="gettopindex"></a>  CListBox::GetTopIndex

リストボックス内の最初に表示される項目の0から始まるインデックスを取得します。

```
int GetTopIndex() const;
```

### <a name="return-value"></a>戻り値

成功した場合はリストボックス内の最初に表示された項目の0から始まるインデックス。それ以外の場合は LB_ERR。

### <a name="remarks"></a>Remarks

最初は、項目0がリストボックスの一番上にありますが、リストボックスがスクロールされている場合は、別の項目が一番上に表示されます。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

##  <a name="initstorage"></a>  CListBox::InitStorage

リストボックス項目を格納するためのメモリを割り当てます。

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>パラメーター

*n 項目*<br/>
追加する項目の数を指定します。

*nBytes*<br/>
項目文字列に割り当てるメモリの量をバイト単位で指定します。

### <a name="return-value"></a>戻り値

成功した場合は、メモリの再割り当てが必要になる前にリストボックスに格納できる項目の最大数を指定します。それ以外の場合は LB_ERRSPACE、十分なメモリが使用できないことを意味します。

### <a name="remarks"></a>Remarks

多数の項目を `CListBox`に追加する前に、この関数を呼び出します。

この関数は、多数の項目 (100 を超える) を持つリストボックスの初期化を高速化するのに役立ちます。 事前は、指定された量のメモリを使用して、後続の[Addstring](#addstring)、 [insertstring](#insertstring)、および[Dir](#dir)関数が可能な限り最短の時間を取るようにします。 パラメーターには、推定値を使用できます。 過大評価を使用すると、いくつかの追加メモリが割り当てられます。過小評価を行う場合、通常の割り当ては、事前に割り当てられた量を超える項目に使用されます。

Windows 95/98 のみ: *Nitems*パラメーターは16ビット値に制限されています。 これは、リストボックスに32767を超える項目を含めることができないことを意味します。 項目の数は制限されていますが、リストボックス内の項目の合計サイズは、使用可能なメモリによってのみ制限されます。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

##  <a name="insertstring"></a>  CListBox::InsertString

リストボックスに文字列を挿入します。

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
文字列を挿入する位置の、0から始まるインデックスを指定します。 このパラメーターが-1 の場合、文字列はリストの末尾に追加されます。

*lpszItem*<br/>
挿入される null で終わる文字列を指します。

### <a name="return-value"></a>戻り値

文字列が挿入された位置の 0 から始まるインデックス。 エラーが発生した場合、戻り値は LB_ERR ます。新しい文字列を格納するのに十分な領域がない場合、戻り値は LB_ERRSPACE ます。

### <a name="remarks"></a>Remarks

[Addstring](#addstring)メンバー関数とは異なり、`InsertString` では、 [LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルを持つリストが並べ替えられることはありません。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

##  <a name="itemfrompoint"></a>  CListBox::ItemFromPoint

*Pt*で指定されたポイントに最も近いリストボックス項目を決定します。

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>パラメーター

*pt*<br/>
リストボックスのクライアント領域の左上隅を基準として指定された、最も近い項目を検索するポイント。

*bOutside*<br/>
ブール変数への参照。 *pt*がリストボックスのクライアント領域の外側にある場合は TRUE に設定され、 *pt*がリストボックスのクライアント領域内にある場合は FALSE に設定されます。

### <a name="return-value"></a>戻り値

*Pt*で指定したポイントまでの最も近い項目のインデックス。

### <a name="remarks"></a>Remarks

この関数を使用すると、マウスカーソルを移動するリストボックス項目を特定できます。

### <a name="example"></a>使用例

  「 [CListBox:: SetAnchorIndex](#setanchorindex)」の例を参照してください。

##  <a name="measureitem"></a>CListBox:: MeasureItem

オーナー描画スタイルのリストボックスが作成されたときに、フレームワークによって呼び出されます。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>パラメーター

*lpMeasureItemStruct*<br/>
[MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct)構造体への long ポインター。

### <a name="remarks"></a>Remarks

既定では、このメンバー関数は何も行いません。 このメンバー関数をオーバーライドし、`MEASUREITEMSTRUCT` 構造体に入力して、ウィンドウにリストボックスの寸法を通知します。 リストボックスが[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルで作成されている場合、フレームワークはリストボックスの各項目に対してこのメンバー関数を呼び出します。 それ以外の場合、このメンバーは1回だけ呼び出されます。

の`SubclassDlgItem` メンバー`CWnd`関数で作成されたオーナー描画リストボックスで [LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles) スタイルを使用する方法の詳細については、[テクニカルノート 14](../../mfc/tn014-custom-controls.md)の説明を参照してください。

`MEASUREITEMSTRUCT` 構造の説明については、「 [CWnd:: OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) 」を参照してください。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

##  <a name="resetcontent"></a>  CListBox::ResetContent

リストボックスからすべての項目を削除します。

```
void ResetContent();
```

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

##  <a name="selectstring"></a>  CListBox::SelectString

指定した文字列と一致するリストボックス項目を検索し、一致する項目が見つかった場合は項目を選択します。

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>パラメーター

*nStartAfter*<br/>
最初に検索される項目の前にある項目の0から始まるインデックスを格納します。 検索がリストボックスの下部に到達すると、リストボックスの一番上から*Nstartafter*によって指定された項目に戻ります。 *Nstartafter*が-1 の場合、リストボックス全体が最初から検索されます。

*lpszItem*<br/>
検索するプレフィックスを含む、null で終わる文字列を指します。 検索は大文字と小文字が区別されないため、この文字列には大文字と小文字の任意の組み合わせを含めることができます。

### <a name="return-value"></a>戻り値

検索が成功した場合は、選択された項目のインデックス。 検索に失敗した場合、戻り値は LB_ERR、現在の選択内容は変更されません。

### <a name="remarks"></a>Remarks

必要に応じて、リストボックスがスクロールされ、選択した項目が表示されます。

このメンバー関数は、 [LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルを持つリストボックスと共に使用することはできません。

項目が選択されるのは、最初の文字 (開始点から) が、 *Lpszitem*によって指定された文字列内の文字と一致する場合のみです。

項目を選択せずに文字列を検索するには、`FindString` メンバー関数を使用します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

##  <a name="selitemrange"></a>  CListBox::SelItemRange

複数選択リストボックス内の複数の連続する項目を選択します。

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>パラメーター

*bSelect*<br/>
選択の設定方法を指定します。 *Bselect*が TRUE の場合は、文字列が選択され、強調表示されます。FALSE の場合、強調表示が削除され、文字列が選択されなくなります。

*nFirstItem*<br/>
設定する最初の項目の0から始まるインデックスを指定します。

*nLastItem*<br/>
設定する最後の項目の0から始まるインデックスを指定します。

### <a name="return-value"></a>戻り値

エラーが発生した場合は LB_ERR します。

### <a name="remarks"></a>Remarks

このメンバー関数は、複数選択のリストボックスでのみ使用してください。 複数選択のリストボックスで項目を1つだけ選択する必要がある場合 ( *Nfirstitem*が*nfirstitem*と等しい場合)、代わりに[SetSel](#setsel)メンバー関数を呼び出します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

##  <a name="setanchorindex"></a>  CListBox::SetAnchorIndex

複数選択のリストボックスでアンカーを設定して、拡張選択を開始します。

```
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
アンカーとなるリストボックス項目の0から始まるインデックスを指定します。

### <a name="remarks"></a>Remarks

複数選択のリストボックスでは、アンカー項目は、連続して選択された項目のブロックの最初または最後の項目です。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

##  <a name="setcaretindex"></a>  CListBox::SetCaretIndex

複数選択リストボックス内の指定したインデックス位置にある項目にフォーカスを示す四角形を設定します。

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
リストボックス内でフォーカスを示す四角形を受け取る項目の0から始まるインデックスを指定します。

*bScroll*<br/>
この値が0の場合、項目は完全に表示されるまでスクロールされます。 この値が0以外の場合、項目は部分的に表示されるまでスクロールされます。

### <a name="return-value"></a>戻り値

エラーが発生した場合は LB_ERR します。

### <a name="remarks"></a>Remarks

項目が表示されていない場合は、スクロールして表示されます。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

##  <a name="setcolumnwidth"></a>CListBox:: SetColumnWidth

複数列のリストボックスのすべての列の幅をピクセル単位で設定します ( [LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルを使用して作成されます)。

```
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>パラメーター

*cxWidth*<br/>
すべての列の幅をピクセル単位で指定します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

##  <a name="setcursel"></a>  CListBox::SetCurSel

必要に応じて、文字列を選択し、ビューにスクロールします。

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>パラメーター

*nSelect*<br/>
選択する文字列の0から始まるインデックスを指定します。 *N*が-1 の場合、リストボックスは選択されていないことを示します。

### <a name="return-value"></a>戻り値

エラーが発生した場合は LB_ERR します。

### <a name="remarks"></a>Remarks

新しい文字列を選択すると、リストボックスには、前に選択した文字列から強調表示が削除されます。

このメンバー関数は、単一選択のリストボックスでのみ使用してください。

複数選択のリストボックスで選択範囲を設定または削除するには、[ [CListBox:: SetSel](#setsel)] を使用します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

##  <a name="sethorizontalextent"></a>CListBox:: SetHorizontalExtent

リストボックスを水平方向にスクロールできる幅をピクセル単位で設定します。

```
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>パラメーター

*cxExtent*<br/>
リストボックスを水平方向にスクロールできるピクセル数を指定します。

### <a name="remarks"></a>Remarks

リストボックスのサイズがこの値よりも小さい場合、水平スクロールバーはリストボックス内の項目を水平方向にスクロールします。 リストボックスがこの値より大きいか大きい場合、水平スクロールバーは非表示になります。

`SetHorizontalExtent`の呼び出しに応答するには、リストボックスが[WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles)スタイルを使用して定義されている必要があります。

このメンバー関数は、複数列のリストボックスには役立ちません。 複数列のリストボックスの場合は、`SetColumnWidth` メンバー関数を呼び出します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

##  <a name="setitemdata"></a>CListBox:: SetItemData

リストボックス内の指定した項目に関連付けられている値を設定します。

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
項目の0から始まるインデックスを指定します。

*dwItemData*<br/>
項目に関連付けられる値を指定します。

### <a name="return-value"></a>戻り値

エラーが発生した場合は LB_ERR します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

##  <a name="setitemdataptr"></a>CListBox:: SetItemDataPtr

リストボックス内の指定した項目に関連付けられている32ビット値を、指定したポインター ( **void** <strong>\*</strong>) に設定します。

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
項目の0から始まるインデックスを指定します。

*pData*<br/>
項目に関連付けられるポインターを指定します。

### <a name="return-value"></a>戻り値

エラーが発生した場合は LB_ERR します。

### <a name="remarks"></a>Remarks

項目が追加または削除されると、リストボックス内の項目の相対位置が変化する場合でも、このポインターはリストボックスの有効期間中は有効なままです。 そのため、ボックス内の項目のインデックスは変更される可能性がありますが、ポインターは信頼できる状態のままです。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

##  <a name="setitemheight"></a>CListBox:: SetItemHeight

リストボックス内の項目の高さを設定します。

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
リストボックス内の項目の0から始まるインデックスを指定します。 このパラメーターは、リストボックスに LBS_OWNERDRAWVARIABLE スタイルが指定されている場合にのみ使用されます。それ以外の場合は0に設定する必要があります。

*cyItemHeight*<br/>
項目の高さをピクセル単位で指定します。

### <a name="return-value"></a>戻り値

インデックスまたは高さが無効である場合に LB_ERR します。

### <a name="remarks"></a>Remarks

リストボックスに[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルが設定さ*れている*場合、この関数は、指定した項目の高さを返します。 それ以外の場合、この関数はリストボックス内のすべての項目の高さを設定します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

##  <a name="setlocale"></a>  CListBox::SetLocale

このリストボックスのロケール識別子を設定します。

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>パラメーター

*nNewLocale*<br/>
リストボックスに設定する新しいロケール識別子 (LCID) 値。

### <a name="return-value"></a>戻り値

このリストボックスの前のロケール識別子 (LCID) 値。

### <a name="remarks"></a>Remarks

`SetLocale` が呼び出されない場合は、既定のロケールがシステムから取得されます。 このシステムの既定のロケールは、コントロールパネルの地域 (または国際) アプリケーションを使用して変更できます。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

##  <a name="setsel"></a>CListBox:: SetSel

複数選択のリストボックスで文字列を選択します。

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
設定する文字列の0から始まるインデックスを格納します。 -1 の場合、選択範囲は、 *Bselect*の値に応じて、すべての文字列に対して追加または削除されます。

*bSelect*<br/>
選択の設定方法を指定します。 *Bselect*が TRUE の場合は、文字列が選択され、強調表示されます。FALSE の場合、強調表示が削除され、文字列が選択されなくなります。 指定した文字列が既定で選択され、強調表示されます。

### <a name="return-value"></a>戻り値

エラーが発生した場合は LB_ERR します。

### <a name="remarks"></a>Remarks

このメンバー関数は、複数選択のリストボックスでのみ使用してください。

1つの選択リストボックスから項目を選択するには、[ [CListBox:: SetCurSel](#setcursel)] を使用します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

##  <a name="settabstops"></a>CListBox:: SetTabStops

リストボックス内のタブストップ位置を設定します。

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>パラメーター

*cxEachStop*<br/>
タブストップは、すべての*cxEachStop*ダイアログ単位で設定されます。 ダイアログ単位の詳細については、「 *rgTabStops* 」を参照してください。

*nTabStops*<br/>
リストボックス内のタブストップの数を指定します。

*rgTabStops*<br/>
ダイアログ単位のタブストップ位置を格納している整数の配列の最初のメンバーを指します。 ダイアログ単位は、水平方向または垂直方向の距離です。 1つの水平ダイアログ単位は、現在のダイアログベースの幅の単位の1番目と同じです。また、1つの垂直ダイアログ単位は、現在のダイアログベースの高さ単位の8分の1と等しくなります。 ダイアログの基本単位は、現在のシステムフォントの高さと幅に基づいて計算されます。 `GetDialogBaseUnits` Windows 関数は、現在のダイアログベース単位をピクセル単位で返します。 タブストップは、昇順に並べ替える必要があります。戻るタブは使用できません。

### <a name="return-value"></a>戻り値

すべてのタブが設定されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

タブストップを既定サイズの2ダイアログ単位に設定するには、このメンバー関数のパラメーターなしのバージョンを呼び出します。 タブストップを2以外のサイズに設定するには、 *cxEachStop*引数を使用してバージョンを呼び出します。

タブストップをサイズの配列に設定するには、 *rgTabStops*引数と*ntabstops*引数を指定してバージョンを使用します。 *RgTabStops*の値ごとにタブストップが設定され、 *ntabstops*によって指定された数になります。

`SetTabStops` メンバー関数の呼び出しに応答するには、リストボックスが[LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルを使用して作成されている必要があります。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

##  <a name="settopindex"></a>  CListBox::SetTopIndex

特定のリストボックス項目が確実に表示されるようにします。

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
リストボックス項目の0から始まるインデックスを指定します。

### <a name="return-value"></a>戻り値

成功した場合は0。エラーが発生した場合は LB_ERR。

### <a name="remarks"></a>Remarks

システムは、[ *nIndex* ] で指定された項目がリストボックスの一番上に表示されるか、最大のスクロール範囲に達したときまで、リストボックスをスクロールします。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

##  <a name="vkeytoitem"></a>CListBox:: VKeyToItem

リストボックスの親ウィンドウがリストボックスから WM_VKEYTOITEM メッセージを受信したときに、フレームワークによって呼び出されます。

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>パラメーター

*nKey*<br/>
ユーザーが押したキーの仮想キーコード。 標準の仮想キーコードの一覧については、「Winuser. h」を参照してください。

*nIndex*<br/>
リストボックスカレットの現在位置。

### <a name="return-value"></a>戻り値

それ以外の操作を行う場合は-2、既定のアクションの場合は-1、キーストロークの既定のアクションを実行するリストボックスアイテムのインデックスを指定する場合は負でない数値を返します。

### <a name="remarks"></a>Remarks

WM_VKEYTOITEM メッセージは、WM_KEYDOWN メッセージを受信したときにリストボックスによって送信されますが、リストボックスが次の両方を満たしている場合に限ります。

- [LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルが設定されています。

- 少なくとも1つの項目があります。

この関数を自分で呼び出すことは避けてください。 キーボードメッセージの独自のカスタム処理を提供するには、この関数をオーバーライドします。

オーバーライドによって実行されたアクションをフレームワークに通知するには、値を返す必要があります。 戻り値-2 は、アプリケーションが項目の選択のすべての側面を処理し、リストボックスによるそれ以上の操作を必要としないことを示します。 -2 を返す前に、選択を設定するか、カレットまたはその両方を移動することができます。 選択を設定するには、 [Setcursel](#setcursel)または[SetSel](#setsel)を使用します。 カレットを移動するには、 [SetCaretIndex](#setcaretindex)を使用します。

戻り値-1 は、リストボックスがキーストロークに応答して既定のアクションを実行する必要があることを示します。既定の実装では、-1 が返されます。

戻り値が0以上の場合は、リストボックス内の項目のインデックスを指定し、リストボックスが、指定された項目のキーストロークの既定の動作を実行することを示します。

### <a name="example"></a>使用例

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプル CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[CButton クラス](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox クラス](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar クラス](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic クラス](../../mfc/reference/cstatic-class.md)
