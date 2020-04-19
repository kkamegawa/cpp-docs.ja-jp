---
title: CHeaderCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CHeaderCtrl
- AFXCMN/CHeaderCtrl
- AFXCMN/CHeaderCtrl::CHeaderCtrl
- AFXCMN/CHeaderCtrl::ClearAllFilters
- AFXCMN/CHeaderCtrl::ClearFilter
- AFXCMN/CHeaderCtrl::Create
- AFXCMN/CHeaderCtrl::CreateDragImage
- AFXCMN/CHeaderCtrl::CreateEx
- AFXCMN/CHeaderCtrl::DeleteItem
- AFXCMN/CHeaderCtrl::DrawItem
- AFXCMN/CHeaderCtrl::EditFilter
- AFXCMN/CHeaderCtrl::GetBitmapMargin
- AFXCMN/CHeaderCtrl::GetFocusedItem
- AFXCMN/CHeaderCtrl::GetImageList
- AFXCMN/CHeaderCtrl::GetItem
- AFXCMN/CHeaderCtrl::GetItemCount
- AFXCMN/CHeaderCtrl::GetItemDropDownRect
- AFXCMN/CHeaderCtrl::GetItemRect
- AFXCMN/CHeaderCtrl::GetOrderArray
- AFXCMN/CHeaderCtrl::GetOverflowRect
- AFXCMN/CHeaderCtrl::HitTest
- AFXCMN/CHeaderCtrl::InsertItem
- AFXCMN/CHeaderCtrl::Layout
- AFXCMN/CHeaderCtrl::OrderToIndex
- AFXCMN/CHeaderCtrl::SetBitmapMargin
- AFXCMN/CHeaderCtrl::SetFilterChangeTimeout
- AFXCMN/CHeaderCtrl::SetFocusedItem
- AFXCMN/CHeaderCtrl::SetHotDivider
- AFXCMN/CHeaderCtrl::SetImageList
- AFXCMN/CHeaderCtrl::SetItem
- AFXCMN/CHeaderCtrl::SetOrderArray
helpviewer_keywords:
- CHeaderCtrl [MFC], CHeaderCtrl
- CHeaderCtrl [MFC], ClearAllFilters
- CHeaderCtrl [MFC], ClearFilter
- CHeaderCtrl [MFC], Create
- CHeaderCtrl [MFC], CreateDragImage
- CHeaderCtrl [MFC], CreateEx
- CHeaderCtrl [MFC], DeleteItem
- CHeaderCtrl [MFC], DrawItem
- CHeaderCtrl [MFC], EditFilter
- CHeaderCtrl [MFC], GetBitmapMargin
- CHeaderCtrl [MFC], GetFocusedItem
- CHeaderCtrl [MFC], GetImageList
- CHeaderCtrl [MFC], GetItem
- CHeaderCtrl [MFC], GetItemCount
- CHeaderCtrl [MFC], GetItemDropDownRect
- CHeaderCtrl [MFC], GetItemRect
- CHeaderCtrl [MFC], GetOrderArray
- CHeaderCtrl [MFC], GetOverflowRect
- CHeaderCtrl [MFC], HitTest
- CHeaderCtrl [MFC], InsertItem
- CHeaderCtrl [MFC], Layout
- CHeaderCtrl [MFC], OrderToIndex
- CHeaderCtrl [MFC], SetBitmapMargin
- CHeaderCtrl [MFC], SetFilterChangeTimeout
- CHeaderCtrl [MFC], SetFocusedItem
- CHeaderCtrl [MFC], SetHotDivider
- CHeaderCtrl [MFC], SetImageList
- CHeaderCtrl [MFC], SetItem
- CHeaderCtrl [MFC], SetOrderArray
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
ms.openlocfilehash: 62915da703e1c938e65643ab389999b83c72d459
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741529"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl クラス

Windows コモン ヘッダー コントロールの機能が用意されています。

## <a name="syntax"></a>構文

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CHeaderCtrl:: CHeaderCtrl](#cheaderctrl)|`CHeaderCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CHeaderCtrl:: ClearAllFilters](#clearallfilters)|ヘッダーコントロールのすべてのフィルターをクリアします。|
|[CHeaderCtrl:: ClearFilter](#clearfilter)|ヘッダーコントロールのフィルターをクリアします。|
|[CHeaderCtrl:: Create](#create)|ヘッダーコントロールを作成し、 `CHeaderCtrl`オブジェクトにアタッチします。|
|[CHeaderCtrl:: CreateDragImage](#createdragimage)|ヘッダーコントロール内の項目のイメージの透明バージョンを作成します。|
|[CHeaderCtrl:: CreateEx](#createex)|指定した Windows 拡張スタイルを使用してヘッダーコントロールを作成し`CListCtrl` 、オブジェクトに添付します。|
|[CHeaderCtrl::DeleteItem](#deleteitem)|ヘッダーコントロールから項目を削除します。|
|[CHeaderCtrl::D rawItem](#drawitem)|ヘッダーコントロールの指定された項目を描画します。|
|[CHeaderCtrl:: EditFilter](#editfilter)|ヘッダーコントロールの指定したフィルターの編集を開始します。|
|[CHeaderCtrl:: GetBitmapMargin](#getbitmapmargin)|ヘッダーコントロールのビットマップの余白の幅を取得します。|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|フォーカスがある現在のヘッダーコントロール内の項目の識別子を取得します。|
|[CHeaderCtrl:: GetImageList](#getimagelist)|ヘッダーコントロールのヘッダー項目を描画するために使用されるイメージリストのハンドルを取得します。|
|[CHeaderCtrl:: GetItem](#getitem)|ヘッダーコントロールの項目に関する情報を取得します。|
|[CHeaderCtrl::GetItemCount](#getitemcount)|ヘッダーコントロール内の項目の数を取得します。|
|[CHeaderCtrl:: GetItemDropDownRect](#getitemdropdownrect)|ヘッダーコントロールの指定されたドロップダウンボタンの外接する四角形の情報を取得します。|
|[CHeaderCtrl::GetItemRect](#getitemrect)|ヘッダーコントロール内の指定された項目の外接する四角形を取得します。|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|ヘッダーコントロール内の項目の左から右の順序を取得します。|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|現在のヘッダーコントロールのオーバーフローボタンの外接する四角形を取得します。|
|[CHeaderCtrl::HitTest](#hittest)|指定したポイントに存在するヘッダー項目を判断します。|
|[CHeaderCtrl::InsertItem](#insertitem)|新しい項目をヘッダーコントロールに挿入します。|
|[CHeaderCtrl::Layout](#layout)|指定された四角形内のヘッダーコントロールのサイズと位置を取得します。|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|ヘッダーコントロールの順序に基づいて、項目のインデックス値を取得します。|
|[CHeaderCtrl:: SetBitmapMargin](#setbitmapmargin)|ヘッダーコントロールのビットマップの余白の幅を設定します。|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|フィルター属性および`HDN_FILTERCHANGE`通知の投稿で変更が行われるまでのタイムアウト間隔を設定します。|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|現在のヘッダーコントロール内の指定されたヘッダー項目にフォーカスを設定します。|
|[CHeaderCtrl:: SetHotDivider](#sethotdivider)|ヘッダー項目を手動でドラッグアンドドロップしたことを示すために、ヘッダー項目間の区分線を変更します。|
|[CHeaderCtrl:: SetImageList](#setimagelist)|イメージリストをヘッダーコントロールに割り当てます。|
|[CHeaderCtrl:: SetItem](#setitem)|ヘッダーコントロール内の指定された項目の属性を設定します。|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|ヘッダーコントロールの項目の左から右への順序を設定します。|

## <a name="remarks"></a>Remarks

ヘッダーコントロールは、通常、テキストまたは数値の列のセットの上に配置されるウィンドウです。 このファイルには、各列のタイトルが含まれており、それぞれの部分に分割できます。 ユーザーは、パーツを区切る分割線をドラッグして、各列の幅を設定できます。 ヘッダーコントロールの図解は、「[ヘッダーコントロール](/windows/win32/Controls/header-controls)」を参照してください。

このコントロール (および`CHeaderCtrl`クラス) は、windows 95/98 および windows NT バージョン3.51 以降で実行されるプログラムに対してのみ使用できます。

Windows 95/Internet Explorer 4.0 コモンコントロールに追加された機能には、次のものが含まれます。

- ヘッダー項目のカスタムの順序付け。

- ヘッダー項目を並べ替えるための、ヘッダー項目のドラッグアンドドロップ。 オブジェクトを`CHeaderCtrl`作成するときは、HDS_DRAGDROP スタイルを使用します。

- ヘッダー列のテキストは、列のサイズ変更中に常に表示できます。 オブジェクトを`CHeaderCtrl`作成するときは、HDS_FULLDRAG スタイルを使用します。

- ヘッダーホットトラッキング。ポインターがその上にポインターを置いたときに、ヘッダー項目を強調表示します。 オブジェクトを`CHeaderCtrl`作成するときは、HDS_HOTTRACK スタイルを使用します。

- イメージリストのサポート。 ヘッダー項目には、 `CImageList`オブジェクトまたはテキストに格納されているイメージを含めることができます。

の使用`CHeaderCtrl`方法の詳細については、「 [Controls](../../mfc/controls-mfc.md) and [using CHeaderCtrl](../../mfc/using-cheaderctrl.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmn.h

##  <a name="cheaderctrl"></a>  CHeaderCtrl::CHeaderCtrl

`CHeaderCtrl` オブジェクトを構築します。

```
CHeaderCtrl();
```

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

##  <a name="clearallfilters"></a>  CHeaderCtrl::ClearAllFilters

ヘッダーコントロールのすべてのフィルターをクリアします。

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されているように、列の値が-1 である Win32 message [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

##  <a name="clearfilter"></a>  CHeaderCtrl::ClearFilter

ヘッダーコントロールのフィルターをクリアします。

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>パラメーター

*n 列*<br/>
クリアするフィルターを示す列の値。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されているように、Win32 message [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

##  <a name="create"></a>  CHeaderCtrl::Create

ヘッダーコントロールを作成し、 `CHeaderCtrl`オブジェクトにアタッチします。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
ヘッダーコントロールのスタイルを指定します。 ヘッダーコントロールスタイルの説明については、「Windows SDK の[ヘッダーコントロールスタイル](/windows/win32/Controls/header-control-styles)」を参照してください。

*rect*<br/>
ヘッダーコントロールのサイズと位置を指定します。 これは、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトまたは[RECT](/previous-versions/dd162897\(v=vs.85\))構造体のいずれかになります。

*pParentWnd*<br/>
ヘッダーコントロールの親ウィンドウ (通常は`CDialog`) を指定します。 NULL にすることはできません。

*nID*<br/>
ヘッダーコントロールの ID を指定します。

### <a name="return-value"></a>戻り値

初期化が成功した場合は0以外の。それ以外の場合は0。

### <a name="remarks"></a>Remarks

オブジェクトを構築`CHeaderCtrl`するには、2つの手順を実行します。 まず、コンストラクターを呼び出し、次に`Create`を呼び出します。これにより、ヘッダーコントロールが`CHeaderCtrl`作成され、オブジェクトにアタッチされます。

ヘッダーコントロールスタイルに加えて、次のコモンコントロールスタイルを使用して、ヘッダーコントロールの位置とサイズの変更方法を決定できます (詳細については、「[コモンコントロールスタイル](/windows/win32/Controls/common-control-styles)」を参照してください)。

- CCS_BOTTOM を指定すると、コントロールが親ウィンドウのクライアント領域の下部に配置され、幅が親ウィンドウの幅と同じになるように設定されます。

- CCS_NODIVIDER は、コントロールの上部に2ピクセルの強調表示を描画しないようにします。

- CCS_NOMOVEY を指定すると、コントロールのサイズが変更され、そのコントロール自体は、WM_SIZE メッセージに応答して垂直方向ではなく、水平方向に移動します。 CCS_NORESIZE スタイルが使用されている場合、このスタイルは適用されません。 既定では、ヘッダーコントロールにこのスタイルが設定されています。

- CCS_NOPARENTALIGN は、コントロールが親ウィンドウの上部または下部に自動的に移動しないようにします。 代わりに、親ウィンドウのサイズが変更されても、コントロールの位置は親ウィンドウ内で保持されます。 CCS_TOP または CCS_BOTTOM スタイルも使用されている場合は、高さが既定値に調整されますが、位置と幅は変わりません。

- CCS_NORESIZE は、初期サイズまたは新しいサイズを設定するときに、コントロールが既定の幅と高さを使用しないようにします。 代わりに、コントロールは要求で指定された幅と高さを使用して作成またはサイズ変更を行います。

- CCS_TOP を指定すると、コントロールが親ウィンドウのクライアント領域の上端に配置され、幅が親ウィンドウの幅と同じになるように設定されます。

次のウィンドウスタイルをヘッダーコントロールに適用することもできます (詳細については、「[ウィンドウのスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)」を参照してください)。

- WS_CHILD 子ウィンドウを作成します。 WS_POPUP スタイルと共に使用することはできません。

- WS_VISIBLE 最初に表示されるウィンドウを作成します。

- WS_DISABLED は、最初は無効になっているウィンドウを作成します。

- WS_GROUP は、ユーザーが方向キーを使用して1つのコントロールから次のコントロールに移動できる、コントロールのグループの最初のコントロールを指定します。 最初のコントロールの後に WS_GROUP スタイルを使用して定義されたすべてのコントロールが、同じグループに属しています。 WS_GROUP スタイルを使用した次のコントロールは、スタイルグループを終了し、次のグループを開始します (つまり、次の開始位置にある1つのグループが終了します)。

- WS_TABSTOP は、TAB キーを使用してユーザーが移動できる任意の数のコントロールを指定します。 TAB キーを押すと、ユーザーが WS_TABSTOP スタイルで指定された次のコントロールに移動します。

拡張 windows スタイルをコントロールで使用する場合は、ではなく`Create` [CreateEx](#createex) を呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

##  <a name="createex"></a>CHeaderCtrl:: CreateEx

コントロール (子ウィンドウ) を作成し、 `CHeaderCtrl`オブジェクトに関連付けます。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwExStyle*<br/>
作成するコントロールの拡張スタイルを指定します。 拡張 Windows スタイルの一覧については、Windows SDK の[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)の*dwexstyle*パラメーターを参照してください。

*dwStyle*<br/>
ヘッダーコントロールのスタイル。 ヘッダーコントロールスタイルの説明については、「Windows SDK の[ヘッダーコントロールスタイル](/windows/win32/Controls/header-control-styles)」を参照してください。 追加のスタイルの一覧については、「[作成](#create)」を参照してください。

*rect*<br/>
*PParentWnd*のクライアント座標で、作成されるウィンドウのサイズと位置を記述する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。

*pParentWnd*<br/>
コントロールの親であるウィンドウへのポインター。

*nID*<br/>
コントロールの子ウィンドウ ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

Windows `CreateEx`拡張スタイル`Create`の先頭**WS_EX_** で指定されている拡張 Windows スタイルを適用するには、の代わりにを使用します。

##  <a name="createdragimage"></a>CHeaderCtrl:: CreateDragImage

ヘッダーコントロール内の項目のイメージの透明バージョンを作成します。

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
ヘッダーコントロール内の項目の0から始まるインデックス。 この項目に割り当てられたイメージは、透明なイメージの基礎となります。

### <a name="return-value"></a>戻り値

成功した場合は、 [CImageList](../../mfc/reference/cimagelist-class.md)オブジェクトへのポインター。それ以外の場合は NULL。 返される一覧には、イメージが1つだけ含まれます。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage)の動作を実装します。 ヘッダー項目のドラッグアンドドロップをサポートするために用意されています。

返されたポインターが指すオブジェクトは一時オブジェクトであり、次のアイドル時の処理で削除されます。`CImageList`

##  <a name="deleteitem"></a>  CHeaderCtrl::DeleteItem

ヘッダーコントロールから項目を削除します。

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
削除する項目の0から始まるインデックスを指定します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

##  <a name="drawitem"></a>CHeaderCtrl::D rawItem

オーナー描画ヘッダーコントロールの視覚的な側面が変更されたときに、フレームワークによって呼び出されます。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>パラメーター

*lpDrawItemStruct*<br/>
描画する項目を記述する[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)構造体へのポインター。

### <a name="remarks"></a>Remarks

構造`DRAWITEMSTRUCT`体のメンバーは`itemAction` 、実行する描画アクションを定義します。

既定では、このメンバー関数は何も行いません。 オーナー描画`CHeaderCtrl`オブジェクトの描画を実装するには、このメンバー関数をオーバーライドします。

このメンバー関数が終了する前に、アプリケーションでは、 *lpDrawItemStruct*で指定された表示コンテキスト用に選択されたすべてのグラフィックスデバイスインターフェイス (GDI) オブジェクトを復元する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

##  <a name="editfilter"></a>  CHeaderCtrl::EditFilter

ヘッダーコントロールの指定されたフィルターの編集を開始します。

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>パラメーター

*n 列*<br/>
編集する列。

*bDiscardChanges*<br/>
[HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)メッセージの送信時にユーザーがフィルターを編集している場合に、ユーザーの編集変更を処理する方法を指定する値。

ユーザーによって行われた変更を破棄する場合は TRUE を、ユーザーが行った変更を受け入れる場合は FALSE を指定します。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されているように、Win32 message [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

##  <a name="getbitmapmargin"></a>  CHeaderCtrl::GetBitmapMargin

ヘッダーコントロールのビットマップの余白の幅を取得します。

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>戻り値

ビットマップ余白の幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

##  <a name="getfocuseditem"></a>  CHeaderCtrl::GetFocusedItem

現在のヘッダーコントロールでフォーカスがある項目のインデックスを取得します。

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>戻り値

フォーカスがあるヘッダー項目の0から始まるインデックス。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[HDM_GETFOCUSEDITEM](/windows/win32/Controls/hdm-getfocuseditem)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、現在`m_headerCtrl`のヘッダーコントロールにアクセスするために使用される変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>例

次のコード例は、 `SetFocusedItem`メソッド`GetFocusedItem`とメソッドを示しています。 コードの前のセクションでは、5つの列を持つヘッダーコントロールを作成しました。 ただし、列が表示されないようにするには、列の区切り線をドラッグします。 次の例では、を設定し、最後の列ヘッダーをフォーカス項目として確認します。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="getimagelist"></a>  CHeaderCtrl::GetImageList

ヘッダーコントロールのヘッダー項目を描画するために使用されるイメージリストのハンドルを取得します。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>戻り値

[CImageList](../../mfc/reference/cimagelist-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist)の動作を実装します。 返されたポインターが指すオブジェクトは一時オブジェクトであり、次のアイドル時の処理で削除されます。`CImageList`

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

##  <a name="getitem"></a>  CHeaderCtrl::GetItem

ヘッダーコントロール項目に関する情報を取得します。

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
取得する項目の0から始まるインデックスを指定します。

*pHeaderItem*<br/>
新しい項目を受け取る[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)構造体へのポインター。 この構造体は、 `InsertItem`および`SetItem`メンバー関数と共に使用されます。 `mask`要素に設定されているフラグによって、返されるときに、対応する要素の値が正しく入力されます。 `mask`要素がゼロに設定されている場合、他の構造体要素の値は無意味になります。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

##  <a name="getitemcount"></a>  CHeaderCtrl::GetItemCount

ヘッダーコントロール内の項目の数を取得します。

```
int GetItemCount() const;
```

### <a name="return-value"></a>戻り値

成功した場合はヘッダーコントロール項目の数。それ以外の場合は-1。

### <a name="example"></a>例

  [CHeaderCtrl::D eleteitem](#deleteitem)の例を参照してください。

##  <a name="getitemdropdownrect"></a>CHeaderCtrl:: GetItemDropDownRect

現在のヘッダーコントロールのヘッダー項目のドロップダウンボタンの外接する四角形を取得します。

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*iItem*|からスタイルが HDF_SPLITBUTTON であるヘッダー項目の0から始まるインデックス。 詳細については、 `fmt` [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)構造体のメンバーを参照してください。|
|*lpRect*|入出力外接する四角形の情報を受け取る[RECT](/previous-versions/dd162897\(v=vs.85\))構造体へのポインター。|

### <a name="return-value"></a>戻り値

この関数が成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、現在`m_headerCtrl`のヘッダーコントロールにアクセスするために使用される変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>例

次のコード例は、 `GetItemDropDownRect`メソッドを示しています。 コードの前のセクションでは、5つの列を持つヘッダーコントロールを作成しました。 次のコード例では、ヘッダーのドロップダウンボタン用に予約されている最初の列の位置を囲む3D 四角形を描画します。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

##  <a name="getitemrect"></a>  CHeaderCtrl::GetItemRect

ヘッダーコントロール内の指定された項目の外接する四角形を取得します。

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
ヘッダーコントロール項目の0から始まるインデックス。

*lpRect*<br/>
外接する四角形の情報を受け取る[RECT](/previous-versions/dd162897\(v=vs.85\))構造体のアドレスへのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されているように、Win32 message [HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect)の動作を実装します。

##  <a name="getorderarray"></a>  CHeaderCtrl::GetOrderArray

ヘッダーコントロール内の項目の左から右の順序を取得します。

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>パラメーター

*piArray*<br/>
ヘッダーコントロール内の項目のインデックス値を、左から右へと表示される順序で受け取るバッファーのアドレスへのポインター。

*iCount*<br/>
ヘッダーコントロール項目の数。 負でない値である必要があります。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray)の動作を実装します。 ヘッダー項目の順序付けをサポートするために用意されています。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

##  <a name="getoverflowrect"></a>  CHeaderCtrl::GetOverflowRect

現在のヘッダーコントロールのオーバーフローボタンの外接する四角形を取得します。

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*lpRect*|入出力外接する四角形の情報を受け取る[RECT](/previous-versions/dd162897\(v=vs.85\))構造体へのポインター。|

### <a name="return-value"></a>戻り値

この関数が成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

同時に表示できない項目がヘッダーコントロールに含まれている場合、コントロールは、表示されていない項目にスクロールするオーバーフローボタンを表示できます。 オーバーフローボタンを表示するには、ヘッダーコントロールに HDS_OVERFLOW と HDF_SPLITBUTTON のスタイルが設定されている必要があります。 外接する四角形はオーバーフローボタンを囲み、オーバーフローボタンが表示されている場合にのみ存在します。 詳細については、「[ヘッダーコントロールのスタイル](/windows/win32/Controls/header-control-styles)」を参照してください。

このメソッドは、Windows SDK で説明されている[HDM_GETOVERFLOWRECT](/windows/win32/Controls/hdm-getoverflowrect)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、現在`m_headerCtrl`のヘッダーコントロールにアクセスするために使用される変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>例

次のコード例は、 `GetOverflowRect`メソッドを示しています。 コードの前のセクションでは、5つの列を持つヘッダーコントロールを作成しました。 ただし、列が表示されないようにするには、列の区切り線をドラッグします。 一部の列が表示されていない場合、ヘッダーコントロールはオーバーフローボタンを描画します。 次のコード例では、オーバーフローボタンの位置を囲む3D 四角形を描画します。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

##  <a name="hittest"></a>  CHeaderCtrl::HitTest

指定したポイントに存在するヘッダー項目を判断します。

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*phdhti*|[入力、出力]テストの結果をテストして受け取るポイントを指定する[Hdhittestinfo](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo)構造体へのポインター。|

### <a name="return-value"></a>戻り値

ヘッダー項目の0から始まるインデックス (存在する場合)。指定した位置にある場合は。それ以外の場合は-1。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[HDM_HITTEST](/windows/win32/Controls/hdm-hittest)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、現在`m_headerCtrl`のヘッダーコントロールにアクセスするために使用される変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>例

次のコード例は、 `HitTest`メソッドを示しています。 このコード例の前のセクションでは、5つの列を持つヘッダーコントロールを作成しました。 ただし、列が表示されないようにするには、列の区切り線をドラッグします。 この例では、列が表示されている場合はそのインデックスを報告し、列が表示されていない場合は-1 を報告します。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

##  <a name="insertitem"></a>  CHeaderCtrl::InsertItem

ヘッダーコントロール内の指定したインデックス位置に新しい項目を挿入します。

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
挿入する項目の 0 から始まるインデックス。 値が0の場合は、ヘッダーコントロールの先頭に項目が挿入されます。 値が最大値より大きい場合は、ヘッダーコントロールの末尾に項目が挿入されます。

*phdi*<br/>
挿入する項目に関する情報を格納している[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)構造体へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は、新しい項目のインデックス。それ以外の場合は-1。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

##  <a name="layout"></a>  CHeaderCtrl::Layout

指定された四角形内のヘッダーコントロールのサイズと位置を取得します。

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>パラメーター

*pHeaderLayout*<br/>
ヘッダーコントロールのサイズと位置を設定するために使用される情報を格納する、 [Hdlayout](/windows/win32/api/commctrl/ns-commctrl-hdlayout)構造体へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

この関数は、指定された四角形を占有する新しいヘッダーコントロールの適切な次元を決定するために使用されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

##  <a name="ordertoindex"></a>  CHeaderCtrl::OrderToIndex

ヘッダーコントロールの順序に基づいて、項目のインデックス値を取得します。

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>パラメーター

*nOrder*<br/>
ヘッダーコントロールの項目が左から右へと表示される、0から始まる順序。

### <a name="return-value"></a>戻り値

ヘッダーコントロールの順序に基づいた項目のインデックス。 インデックスは、0から順に左から右にカウントされます。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 マクロ[HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex)の動作を実装します。 ヘッダー項目の順序付けをサポートするために用意されています。

##  <a name="setbitmapmargin"></a>  CHeaderCtrl::SetBitmapMargin

ヘッダーコントロールのビットマップの余白の幅を設定します。

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>パラメーター

*nWidth*<br/>
既存のヘッダーコントロール内のビットマップを囲む余白の幅 (ピクセル単位)。

### <a name="return-value"></a>戻り値

ビットマップ余白の幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

##  <a name="setfilterchangetimeout"></a>  CHeaderCtrl::SetFilterChangeTimeout

フィルター属性で変更が行われるまでのタイムアウト間隔と、 [HDN_FILTERCHANGE](/windows/win32/Controls/hdn-filterchange)通知の投稿を設定します。

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>パラメーター

*dwTimeOut*<br/>
タイムアウト値 (ミリ秒単位)。

### <a name="return-value"></a>戻り値

変更されるフィルターコントロールのインデックス。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)の動作を実装します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

##  <a name="setfocuseditem"></a>  CHeaderCtrl::SetFocusedItem

現在のヘッダーコントロール内の指定されたヘッダー項目にフォーカスを設定します。

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*iItem*|からヘッダー項目の0から始まるインデックス。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、Windows SDK で説明されている[HDM_SETFOCUSEDITEM](/windows/win32/Controls/hdm-setfocuseditem)メッセージを送信します。

### <a name="example"></a>例

次のコード例では、現在`m_headerCtrl`のヘッダーコントロールにアクセスするために使用される変数を定義します。 この変数は次の例で使用されています。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>例

次のコード例は、 `SetFocusedItem`メソッド`GetFocusedItem`とメソッドを示しています。 コードの前のセクションでは、5つの列を持つヘッダーコントロールを作成しました。 ただし、列が表示されないようにするには、列の区切り線をドラッグします。 次の例では、を設定し、最後の列ヘッダーをフォーカス項目として確認します。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="sethotdivider"></a>  CHeaderCtrl::SetHotDivider

ヘッダー項目を手動でドラッグアンドドロップしたことを示すために、ヘッダー項目間の区分線を変更します。

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>パラメーター

*未満*<br/>
ポインターの位置。 ヘッダーコントロールは、ポインターの位置に基づいて適切な区分線を強調表示します。

*nIndex*<br/>
強調表示された区分線のインデックス。

### <a name="return-value"></a>戻り値

強調表示された区分線のインデックス。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider)の動作を実装します。 ヘッダー項目のドラッグアンドドロップをサポートするために用意されています。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

##  <a name="setimagelist"></a>  CHeaderCtrl::SetImageList

イメージリストをヘッダーコントロールに割り当てます。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>パラメーター

*pImageList*<br/>
ヘッダーコントロールに割り当て`CImageList`られるイメージリストを格納しているオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

以前にヘッダーコントロールに割り当てられた[CImageList](../../mfc/reference/cimagelist-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)の動作を実装します。 返されたポインターが指すオブジェクトは一時オブジェクトであり、次のアイドル時の処理で削除されます。`CImageList`

### <a name="example"></a>例

  [CHeaderCtrl:: GetImageList](#getimagelist)の例を参照してください。

##  <a name="setitem"></a>  CHeaderCtrl::SetItem

ヘッダーコントロール内の指定された項目の属性を設定します。

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
操作する項目の0から始まるインデックス。

*pHeaderItem*<br/>
新しい項目に関する情報を格納している[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)構造体へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

  [CHeaderCtrl:: GetItem](#getitem)の例を参照してください。

##  <a name="setorderarray"></a>  CHeaderCtrl::SetOrderArray

ヘッダーコントロールの項目の左から右への順序を設定します。

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>パラメーター

*iCount*<br/>
ヘッダーコントロール項目の数。

*piArray*<br/>
ヘッダーコントロール内の項目のインデックス値を、左から右へと表示される順序で受け取るバッファーのアドレスへのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 マクロ[HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray)の動作を実装します。 ヘッダー項目の順序付けをサポートするために用意されています。

### <a name="example"></a>例

  [CHeaderCtrl:: GetOrderArray](#getorderarray)の例を参照してください。

## <a name="see-also"></a>関連項目

[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl クラス](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl クラス](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList クラス](../../mfc/reference/cimagelist-class.md)
