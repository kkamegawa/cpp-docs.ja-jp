---
title: CMFCPropertySheet プロパティクラス
ms.date: 11/19/2018
f1_keywords:
- CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::CMFCPropertySheet
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPage
- AFXPROPERTYSHEET/CMFCPropertySheet::AddPageToTree
- AFXPROPERTYSHEET/CMFCPropertySheet::AddTreeCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::EnablePageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::GetHeaderHeight
- AFXPROPERTYSHEET/CMFCPropertySheet::GetLook
- AFXPROPERTYSHEET/CMFCPropertySheet::GetNavBarWidth
- AFXPROPERTYSHEET/CMFCPropertySheet::GetTab
- AFXPROPERTYSHEET/CMFCPropertySheet::InitNavigationControl
- AFXPROPERTYSHEET/CMFCPropertySheet::OnActivatePage
- AFXPROPERTYSHEET/CMFCPropertySheet::OnDrawPageHeader
- AFXPROPERTYSHEET/CMFCPropertySheet::OnRemoveTreePage
- AFXPROPERTYSHEET/CMFCPropertySheet::RemoveCategory
- AFXPROPERTYSHEET/CMFCPropertySheet::RemovePage
- AFXPROPERTYSHEET/CMFCPropertySheet::SetIconsList
- AFXPROPERTYSHEET/CMFCPropertySheet::SetLook
helpviewer_keywords:
- CMFCPropertySheet [MFC], CMFCPropertySheet
- CMFCPropertySheet [MFC], AddPage
- CMFCPropertySheet [MFC], AddPageToTree
- CMFCPropertySheet [MFC], AddTreeCategory
- CMFCPropertySheet [MFC], EnablePageHeader
- CMFCPropertySheet [MFC], GetHeaderHeight
- CMFCPropertySheet [MFC], GetLook
- CMFCPropertySheet [MFC], GetNavBarWidth
- CMFCPropertySheet [MFC], GetTab
- CMFCPropertySheet [MFC], InitNavigationControl
- CMFCPropertySheet [MFC], OnActivatePage
- CMFCPropertySheet [MFC], OnDrawPageHeader
- CMFCPropertySheet [MFC], OnRemoveTreePage
- CMFCPropertySheet [MFC], RemoveCategory
- CMFCPropertySheet [MFC], RemovePage
- CMFCPropertySheet [MFC], SetIconsList
- CMFCPropertySheet [MFC], SetLook
ms.assetid: 01d93573-9698-440f-a6a4-5bebbee879dc
ms.openlocfilehash: f7c9d2b472a443d8bf556d0b12dfe202ea8607a1
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "69505051"
---
# <a name="cmfcpropertysheet-class"></a>CMFCPropertySheet プロパティクラス

`CMFCPropertySheet` クラスは、各プロパティ ページがページ タブ、ツール バー ボタン、ツリー コントロールのノード、またはリスト項目で示されるプロパティ シートをサポートします。

## <a name="syntax"></a>構文

```
class CMFCPropertySheet : public CPropertySheet
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCPropertySheet プロパティ:: CMFCPropertySheet プロパティ](#cmfcpropertysheet)|`CMFCPropertySheet` オブジェクトを構築します。|
|`CMFCPropertySheet::~CMFCPropertySheet`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCPropertySheet プロパティ:: AddPage](#addpage)|プロパティ シートにページを追加します。|
|[CMFCPropertySheet:: AddPageToTree](#addpagetotree)|ツリー コントロールに新しいプロパティ ページを追加します。|
|[CMFCPropertySheet プロパティ:: AddTreeCategory](#addtreecategory)|ツリー コントロールに新しいノードを追加します。|
|[CMFCPropertySheet:: EnablePageHeader](#enablepageheader)|カスタム ヘッダーを描画する領域を各ページの上部に確保します。|
|[CMFCPropertySheet プロパティ:: GetHeaderHeight](#getheaderheight)|現在のヘッダーの高さを取得します。|
|[CMFCPropertySheet プロパティ:: GetLook](#getlook)|現在のプロパティ シートの外観を指定する列挙値を取得します。|
|[CMFCPropertySheet プロパティ:: Getナビゲーションバーの幅](#getnavbarwidth)|ナビゲーション バーの幅をピクセル単位で取得します。|
|[CMFCPropertySheet プロパティ:: GetTab](#gettab)|現在のプロパティ シート コントロールをサポートする内部タブ コントロール オブジェクトを取得します。|
|`CMFCPropertySheet::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|[CMFCPropertySheet:: InitNavigationControl](#initnavigationcontrol)|現在のプロパティ シート コントロールの外観を初期化します。|
|[CMFCPropertySheet プロパティ:: On[アクティブ] ページ](#onactivatepage)|プロパティ ページが有効になったときにフレームワークによって呼び出されます。|
|[CMFCPropertySheet プロパティ:: OnDrawPageHeader](#ondrawpageheader)|カスタム プロパティ ページのヘッダーを描画するためにフレームワークによって呼び出されます。|
|`CMFCPropertySheet::OnInitDialog`|[WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog)メッセージを処理します。 ( [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)をオーバーライドします。)|
|[CMFCPropertySheet プロパティ:: OnRemoveTreePage](#onremovetreepage)|ツリー コントロールからプロパティ ページを削除するためにフレームワークによって呼び出されます。|
|`CMFCPropertySheet::PreTranslateMessage`|[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)および[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)の Windows 関数にディスパッチされる前に、ウィンドウメッセージを変換します。 ( `CPropertySheet::PreTranslateMessage`をオーバーライドします)。|
|[CMFCPropertySheet プロパティ:: RemoveCategory](#removecategory)|ツリー コントロールからノードを削除します。|
|[CMFCPropertySheet プロパティ:: RemovePage](#removepage)|プロパティ シートからプロパティ ページを削除します。|
|[CMFCPropertySheet:: SetIconsList](#seticonslist)|Outlook ウィンドウのナビゲーション コントロールで使用されるイメージの一覧を指定します。|
|[CMFCPropertySheet プロパティ:: SetLook](#setlook)|プロパティ シートの外観を指定します。|

## <a name="remarks"></a>コメント

`CMFCPropertySheet` クラスは、プロパティ シート (タブ ダイアログ ボックスとも呼ばれます) を表します。 `CMFCPropertySheet` クラスは、さまざまな方法でプロパティ ページを表示できます。

アプリケーションで `CMFCPropertySheet` クラスを使用するには、次の手順を実行します。

1. `CMFCPropertySheet` クラスから派生クラスを作成し、名前 (CMyPropertySheet など) を付けます。

1. プロパティページごとに[Cmfcpropertypage](../../mfc/reference/cmfcpropertypage-class.md)オブジェクトを構築します。

1. CMyPropertySheet コンストラクターで[Cmfcpropertysheet:: SetLook](#setlook)メソッドを呼び出します。 このメソッドのパラメーターで、プロパティ ページの表示方法として、プロパティ シートの上部または左側のタブ、Microsoft OneNote プロパティ シート スタイルのタブ、Microsoft Outlook ツール バー コントロールのボタン、ツリー コントロールのノード、プロパティ シートの左側の項目リストのいずれかを指定します。

1. Microsoft Outlook ツールバーのスタイルでプロパティシートを作成する場合は、 [cmfcpropertysheet](#seticonslist)プロパティページを使用して、イメージリストをプロパティページと関連付けることができます。

1. 各プロパティページに対して[Cmfcpropertysheet::](#addpage)メソッドを呼び出します。

1. `CMFCPropertySheet` コントロールを作成し、その `DoModal` メソッドを呼び出します。

## <a name="illustrations"></a>図

次の図は、埋め込みの Microsoft Outlook ツール バー スタイルのプロパティ シートを示しています。 プロパティ シートの左側に Outlook ツール バーが表示されます。

![Cmfcpropertysheet の色コントロール](../../mfc/reference/media/cmfcpropertysheet_color.png "Cmfcpropertysheet の色コントロール")

次の図は、 [Cmfcpropertygridctrl クラス](../../mfc/reference/cmfcpropertygridctrl-class.md)オブジェクトを含むプロパティシートを示しています。 このオブジェクトは、標準のコモン コントロール スタイルのプロパティ シートです。

![Cmfcpropertysheet のリストとプロパティコントロール](../../mfc/reference/media/cmfcpropertysheet_list.png "Cmfcpropertysheet のリストとプロパティコントロール")

次の図は、ツリー コントロール スタイルのプロパティ シートを示しています。

![プロパティツリー](../../mfc/reference/media/proptree.png "プロパティツリー")

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

## <a name="requirements"></a>要件

**ヘッダー:** afxpropertysheet

##  <a name="addpage"></a>CMFCPropertySheet プロパティ:: AddPage

プロパティ シートにページを追加します。

```
void AddPage(CPropertyPage* pPage);
```

### <a name="parameters"></a>パラメーター

*pPage*<br/>
からページオブジェクトへのポインター。 このパラメーターを NULL にすることはできません。

### <a name="remarks"></a>コメント

このメソッドは、プロパティシートの右端のタブとして、指定されたプロパティページを追加します。 したがって、このメソッドを使用して、ページを左から右へ順に追加します。

プロパティシートが Microsoft Outlook のスタイルになっている場合、フレームワークは、プロパティシートの左側にナビゲーションボタンの一覧を表示します。 このメソッドによってプロパティページが追加されると、対応するボタンが一覧に追加されます。 プロパティページを表示するには、対応するボタンをクリックします。 プロパティシートのスタイルの詳細については、「 [cmfcpropertysheet:: SetLook](#setlook)」を参照してください。

##  <a name="addpagetotree"></a>CMFCPropertySheet:: AddPageToTree

ツリー コントロールに新しいプロパティ ページを追加します。

```
void AddPageToTree(
    CMFCPropertySheetCategoryInfo* pCategory,
    CMFCPropertyPage* pPage,
    int nIconNum=-1,
    int nSelIconNum=-1);
```

### <a name="parameters"></a>パラメーター

*pCategory*<br/>
から親ツリーノードへのポインター。指定したページをトップレベルノードに関連付ける場合は NULL。 このポインターを取得するには、 [Cmfcpropertysheet::](#addtreecategory)メソッドを呼び出します。

*pPage*<br/>
からプロパティページオブジェクトへのポインター。

*nIconNum*<br/>
からアイコンの0から始まるインデックス番号。アイコンが使用されていない場合は-1。 ページが選択されていない場合、ツリーコントロールのプロパティページの横にアイコンが表示されます。 既定値は -1 です。

*nSelIconNum*<br/>
からアイコンの0から始まるインデックス番号。アイコンが使用されていない場合は-1。 ページが選択されると、ツリーコントロールのプロパティページの横にアイコンが表示されます。 既定値は -1 です。

### <a name="remarks"></a>コメント

このメソッドは、プロパティページをツリーコントロールのリーフとして追加します。 プロパティページを追加するには、 `CMFCPropertySheet`オブジェクトを作成し、 *look*パラメーターをに`CMFCPropertySheet::PropSheetLook_Tree`設定して[cmfcpropertysheet: setlook](#setlook)メソッドを呼び出した後、このメソッドを使用してプロパティページを追加します。

##  <a name="addtreecategory"></a>CMFCPropertySheet プロパティ:: AddTreeCategory

ツリー コントロールに新しいノードを追加します。

```
CMFCPropertySheetCategoryInfo* AddTreeCategory(
    LPCTSTR lpszLabel,
    int nIconNum=-1,
    int nSelectedIconNum=-1,
    const CMFCPropertySheetCategoryInfo* pParentCategory=NULL);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
からノードの名前。

*nIconNum*<br/>
からアイコンの0から始まるインデックス番号。アイコンが使用されていない場合は-1。 ページが選択されていない場合、ツリーコントロールのプロパティページの横にアイコンが表示されます。 既定値は -1 です。

*nSelectedIconNum*<br/>
からアイコンの0から始まるインデックス番号。アイコンが使用されていない場合は-1。 ページが選択されると、ツリーコントロールのプロパティページの横にアイコンが表示されます。 既定値は -1 です。

*pParentCategory*<br/>
から親ツリーノードへのポインター。指定したページをトップレベルノードに関連付ける場合は NULL。 このパラメーターは、 [Cmfcpropertysheet::](#addtreecategory)メソッドで設定します。

### <a name="return-value"></a>戻り値

ツリーコントロール内の新しいノードへのポインター。

### <a name="remarks"></a>コメント

このメソッドを使用して、ツリーコントロールに新しいノード (カテゴリとも呼ばれます) を追加します。 ノードを追加するには、 `CMFCPropertySheet`オブジェクトを作成し、 *look*パラメーターをに`CMFCPropertySheet::PropSheetLook_Tree`設定して[cmfcpropertysheet: setlook](#setlook)メソッドを呼び出した後、このメソッドを使用してノードを追加します。

このメソッドの戻り値は、次に[cmfcpropertysheet:: AddPageToTree](#addpagetotree)および[Cmfcpropertysheet::](#addtreecategory)を呼び出すときに使用します。

##  <a name="cmfcpropertysheet"></a>CMFCPropertySheet プロパティ:: CMFCPropertySheet プロパティ

`CMFCPropertySheet` オブジェクトを構築します。

```
CMFCPropertySheet(
    UINT nIDCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);

CMFCPropertySheet(
    LPCTSTR pszCaption,
    CWnd* pParentWnd=NULL,
    UINT iSelectPage=0);
```

### <a name="parameters"></a>パラメーター

*pszCaption*<br/>
からプロパティシートのキャプションを格納している文字列。 Nll は指定できません。

*nIDCaption*<br/>
からプロパティシートのキャプションを格納しているリソース ID。

*pParentWnd*<br/>
からプロパティシートの親ウィンドウへのポインター。親ウィンドウがアプリケーションのメインウィンドウである場合は NULL。 既定値は NULL です。

*iSelectPage*<br/>
から最上位のプロパティページの0から始まるインデックス。 既定値は 0 です。

### <a name="remarks"></a>コメント

詳細については、 [CPropertySheet:: CPropertySheet](../../mfc/reference/cpropertysheet-class.md#cpropertysheet)コンストラクターのパラメーターを参照してください。

##  <a name="enablepageheader"></a>CMFCPropertySheet:: EnablePageHeader

カスタム ヘッダーを描画する領域を各ページの上部に確保します。

```
void EnablePageHeader(int nHeaderHeight);
```

### <a name="parameters"></a>パラメーター

*nHeaderHeight*<br/>
からヘッダーの高さ (ピクセル単位)。

### <a name="remarks"></a>コメント

*Nheaderheight*パラメーターの値を使用してカスタムヘッダーを描画するには、 [Cmfcpropertysheet::](#ondrawpageheader)メソッドをオーバーライドします。

##  <a name="getheaderheight"></a>CMFCPropertySheet プロパティ:: GetHeaderHeight

現在のヘッダーの高さを取得します。

```
int GetHeaderHeight() const;
```

### <a name="return-value"></a>戻り値

ヘッダーの高さ (ピクセル単位)。

### <a name="remarks"></a>コメント

このメソッドを呼び出す前に、 [Cmfcpropertysheet:: enablepageheader](#enablepageheader)呼び出してください。

##  <a name="getlook"></a>CMFCPropertySheet プロパティ:: GetLook

現在のプロパティ シートの外観を指定する列挙値を取得します。

```
PropSheetLook GetLook() const;
```

### <a name="return-value"></a>戻り値

プロパティシートの外観を指定する列挙値の1つ。 使用可能な値の一覧については、「 [Cmfcpropertysheet プロパティ:: SetLook](#setlook)」の「解説」の列挙テーブルを参照してください。

##  <a name="getnavbarwidth"></a>CMFCPropertySheet プロパティ:: Getナビゲーションバーの幅

ナビゲーション バーの幅を取得します。

```
int GetNavBarWidth() const;
```

### <a name="return-value"></a>戻り値

軸スクロール バーの幅 (ピクセル単位)。

##  <a name="gettab"></a>CMFCPropertySheet プロパティ:: GetTab

現在のプロパティ シート コントロールをサポートする内部タブ コントロール オブジェクトを取得します。

```
CMFCTabCtrl& GetTab() const;
```

### <a name="return-value"></a>戻り値

内部タブコントロールオブジェクト。

### <a name="remarks"></a>コメント

プロパティシートは、ツリーコントロール、ナビゲーションボタンの一覧、タブ付きページのセットなど、さまざまなスタイルで表示されるように設定できます。

このメソッドを呼び出す前に、 [cmfcpropertysheet: SetLook](#setlook)メソッドを呼び出して、プロパティシートコントロールの外観を設定します。 次に、 [Cmfcpropertysheet:: InitNavigationControl](#initnavigationcontrol)メソッドを呼び出して、内部タブコントロールオブジェクトを初期化します。 このメソッドを使用して、タブコントロールオブジェクトを取得し、そのオブジェクトを使用してプロパティシートのタブを操作します。

このメソッドは、プロパティシートコントロールが Microsoft OneNote のスタイルで表示されるように設定されていない場合に、デバッグモードでアサートします。

##  <a name="initnavigationcontrol"></a>CMFCPropertySheet:: InitNavigationControl

現在のプロパティ シート コントロールの外観を初期化します。

```
virtual CWnd* InitNavigationControl();
```

### <a name="return-value"></a>戻り値

プロパティシートコントロールのウィンドウへのポインター。

### <a name="remarks"></a>コメント

プロパティシートコントロールは、一連のタブ付きページ、ツリーコントロール、またはナビゲーションボタンの一覧など、さまざまな形式で表示できます。 プロパティシートコントロールの外観を指定するには、 [cmfcpropertysheet:: SetLook](#setlook)メソッドを使用します。

##  <a name="onactivatepage"></a>CMFCPropertySheet プロパティ:: On[アクティブ] ページ

プロパティ ページが有効になったときにフレームワークによって呼び出されます。

```
virtual void OnActivatePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>パラメーター

*pPage*<br/>
からEnabled プロパティページを表すプロパティページオブジェクトへのポインター。

### <a name="remarks"></a>コメント

既定では、このメソッドによって、有効なプロパティページが表示されるようになります。 現在のプロパティシートのスタイルに Microsoft Outlook のウィンドウが含まれている場合、このメソッドは対応する Outlook ボタンをチェックされた状態に設定します。

##  <a name="ondrawpageheader"></a>CMFCPropertySheet プロパティ:: OnDrawPageHeader

カスタムプロパティページのヘッダーを描画するためにフレームワークによって呼び出されます。

```
virtual void OnDrawPageHeader(
    CDC* pDC,
    int nPage,
    CRect rectHeader);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からデバイスコンテキストへのポインター。

*nPage*<br/>
から0から始まるプロパティページ番号。

*rectHeader*<br/>
からヘッダーの描画位置を指定する外接する四角形。

### <a name="remarks"></a>コメント

既定では、このメソッドは何も行いません。 このメソッドをオーバーライドする場合は、フレームワークがこのメソッドを呼び出す前に、 [Cmfcpropertysheet プロパティ:: enablepageheader](#enablepageheader)呼び出します。

##  <a name="onremovetreepage"></a>CMFCPropertySheet プロパティ:: OnRemoveTreePage

ツリー コントロールからプロパティ ページを削除するためにフレームワークによって呼び出されます。

```
virtual BOOL OnRemoveTreePage(CPropertyPage* pPage);
```

### <a name="parameters"></a>パラメーター

*pPage*<br/>
から削除するプロパティページを表すプロパティページオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

##  <a name="removecategory"></a>CMFCPropertySheet プロパティ:: RemoveCategory

ツリー コントロールからノードを削除します。

```
void RemoveCategory(CMFCPropertySheetCategoryInfo* pCategory);
```

### <a name="parameters"></a>パラメーター

*pCategory*<br/>
から削除するカテゴリ (ノード) へのポインター。

### <a name="remarks"></a>コメント

このメソッドを使用して、ツリーコントロールからノード (カテゴリとも呼ばれます) を削除します。 [Cmfcpropertysheet::](#addtreecategory)メソッドを使用して、ノードをツリーコントロールに追加します。

##  <a name="removepage"></a>CMFCPropertySheet プロパティ:: RemovePage

プロパティ シートからプロパティ ページを削除します。

```
void RemovePage(CPropertyPage* pPage);
void RemovePage(int nPage);
```

### <a name="parameters"></a>パラメーター

*pPage*<br/>
から削除するプロパティページを表すプロパティページオブジェクトへのポインター。 Nll は指定できません。

*nPage*<br/>
から削除するページの0から始まるインデックス。

### <a name="remarks"></a>コメント

このメソッドは、指定されたプロパティページを削除し、関連付けられているウィンドウを破棄します。 *PPage*パラメーターで指定されるプロパティページオブジェクトは、 [cmfcpropertysheet](../../mfc/reference/cmfcpropertysheet-class.md)ウィンドウが閉じられるまで破棄されません。

##  <a name="seticonslist"></a>CMFCPropertySheet:: SetIconsList

Outlook ウィンドウのナビゲーション コントロールで使用されるイメージの一覧を指定します。

```
BOOL SetIconsList(
    UINT uiImageListResID,
    int cx,
    COLORREF clrTransparent=RGB(255, 0, 255));
void SetIconsList(HIMAGELIST hIcons);
```

### <a name="parameters"></a>パラメーター

*Uiimagの登録 Stresid*<br/>
からイメージリストのリソース ID。

*cx*<br/>
からイメージリストのアイコンの幅 (ピクセル単位)。

*clrTransparent*<br/>
から透明な画像の色。 この色の画像の部分は透明になります。 既定値は、色マゼンタ、RGB (255、0255) です。

*hIcons*<br/>
から既存のイメージリストを処理するハンドル。

### <a name="return-value"></a>戻り値

最初のメソッドオーバーロード構文では、このメソッドが成功した場合は TRUE になります。それ以外の場合は FALSE。

### <a name="remarks"></a>コメント

プロパティシートが Microsoft Outlook のスタイルになっている場合、プロパティシートの左側に、Outlook ペインコントロールと呼ばれるナビゲーションボタンの一覧が表示されます。 このメソッドを使用して、Outlook ウィンドウコントロールによって使用されるイメージリストを設定します。

このメソッドをサポートするメソッドの詳細については、「 [cimagelist:: Create](../../mfc/reference/cimagelist-class.md#create) 」と「 [Cimagelist:: Add](../../mfc/reference/cimagelist-class.md#add)」を参照してください。 プロパティシートのスタイルを設定する方法の詳細については、「 [cmfcpropertysheet:: SetLook](#setlook)」を参照してください。

##  <a name="setlook"></a>CMFCPropertySheet プロパティ:: SetLook

プロパティ シートの外観を指定します。

```
void SetLook(
    PropSheetLook look,
    int nNavControlWidth=100);
```

### <a name="parameters"></a>パラメーター

*ほら*<br/>
からプロパティシートの外観を指定する列挙値の1つ。 プロパティシートの既定のスタイルは`CMFCPropertySheet::PropSheetLook_Tabs`です。 詳細については、このトピックの「解説」の表を参照してください。

*nNavControlWidth*<br/>
からナビゲーションコントロールの幅 (ピクセル単位)。 既定値は 100 です。

### <a name="remarks"></a>コメント

既定以外のスタイルでプロパティシートを表示するには、プロパティシートウィンドウを作成する前にこのメソッドを呼び出します。

次の表に、 *look*パラメーターで指定できる列挙値の一覧を示します。

|[値]|説明|
|-----------|-----------------|
|`CMFCPropertySheet::PropSheetLook_Tabs`|標準各プロパティページのタブを表示します。 タブは、プロパティシートの上部に表示され、1つの行に収まりきらないタブがある場合は積み重ねられます。|
|`CMFCPropertySheet::PropSheetLook_OutlookBar`|プロパティシートの左側にある、Microsoft Outlook バーのスタイルで、ナビゲーションボタンの一覧を表示します。 リスト内の各ボタンは、プロパティページに対応しています。 リストに表示されている領域に収まりきらないボタンが他にある場合、フレームワークはスクロール矢印を表示します。|
|`CMFCPropertySheet::PropSheetLook_Tree`|プロパティシートの左側にツリーコントロールを表示します。 ツリーコントロールの各親ノードまたは子ノードは、プロパティページに対応しています。 ツリーコントロールの表示領域に収まりきらないノードがある場合、フレームワークはスクロール矢印を表示します。|
|`CMFCPropertySheet::PropSheetLook_OneNoteTabs`|各プロパティページについて、Microsoft OneNote のスタイルでタブを表示します。 フレームワークでは、プロパティシートの上部にタブが表示され、1行に収まりきらないタブがある場合はスクロール矢印が表示されます。|
|`CMFCPropertySheet::PropSheetLook_List`|プロパティシートの左側に一覧が表示されます。 各リスト項目は、プロパティページに対応しています。 リストの表示領域に表示される項目よりも多くのリスト項目がある場合、フレームワークはスクロール矢印を表示します。|

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyPage クラス](../../mfc/reference/cmfcpropertypage-class.md)<br/>
[CMFCOutlookBar クラス](../../mfc/reference/cmfcoutlookbar-class.md)
