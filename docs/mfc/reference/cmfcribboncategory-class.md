---
title: CMFCRibbonCategory クラス
ms.date: 11/19/2018
f1_keywords:
- CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory::CMFCRibbonCategory
- AFXRIBBONCATEGORY/CMFCRibbonCategory::AddHidden
- AFXRIBBONCATEGORY/CMFCRibbonCategory::AddPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::CopyFrom
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindByData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindByID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::FindPanelWithElem
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetContextID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetDroppedDown
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetElements
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetElementsByID
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetFirstVisibleElement
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetFocused
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetHighlighted
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetImageCount
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetImageSize
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetItemIDsList
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetLastVisibleElement
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetLargeImages
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetMaxHeight
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetName
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelCount
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelFromPoint
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetPanelIndex
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentButton
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentMenuBar
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetParentRibbonBar
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetRect
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetSmallImages
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTabColor
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTabRect
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetTextTopLine
- AFXRIBBONCATEGORY/CMFCRibbonCategory::GetVisibleElements
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HighlightPanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTest
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTestEx
- AFXRIBBONCATEGORY/CMFCRibbonCategory::HitTestScrollButtons
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsActive
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsVisible
- AFXRIBBONCATEGORY/CMFCRibbonCategory::IsWindows7Look
- AFXRIBBONCATEGORY/CMFCRibbonCategory::NotifyControlCommand
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnCancelMode
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDraw
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDrawImage
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnDrawMenuBorder
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnKey
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnLButtonDown
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnLButtonUp
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnMouseMove
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnRTLChanged
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnScrollHorz
- AFXRIBBONCATEGORY/CMFCRibbonCategory::OnUpdateCmdUI
- AFXRIBBONCATEGORY/CMFCRibbonCategory::RecalcLayout
- AFXRIBBONCATEGORY/CMFCRibbonCategory::RemovePanel
- AFXRIBBONCATEGORY/CMFCRibbonCategory::ReposPanels
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetCollapseOrder
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetData
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetKeys
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetName
- AFXRIBBONCATEGORY/CMFCRibbonCategory::SetTabColor
helpviewer_keywords:
- CMFCRibbonCategory [MFC], CMFCRibbonCategory
- CMFCRibbonCategory [MFC], AddHidden
- CMFCRibbonCategory [MFC], AddPanel
- CMFCRibbonCategory [MFC], CopyFrom
- CMFCRibbonCategory [MFC], FindByData
- CMFCRibbonCategory [MFC], FindByID
- CMFCRibbonCategory [MFC], FindPanelWithElem
- CMFCRibbonCategory [MFC], GetContextID
- CMFCRibbonCategory [MFC], GetData
- CMFCRibbonCategory [MFC], GetDroppedDown
- CMFCRibbonCategory [MFC], GetElements
- CMFCRibbonCategory [MFC], GetElementsByID
- CMFCRibbonCategory [MFC], GetFirstVisibleElement
- CMFCRibbonCategory [MFC], GetFocused
- CMFCRibbonCategory [MFC], GetHighlighted
- CMFCRibbonCategory [MFC], GetImageCount
- CMFCRibbonCategory [MFC], GetImageSize
- CMFCRibbonCategory [MFC], GetItemIDsList
- CMFCRibbonCategory [MFC], GetLastVisibleElement
- CMFCRibbonCategory [MFC], GetLargeImages
- CMFCRibbonCategory [MFC], GetMaxHeight
- CMFCRibbonCategory [MFC], GetName
- CMFCRibbonCategory [MFC], GetPanel
- CMFCRibbonCategory [MFC], GetPanelCount
- CMFCRibbonCategory [MFC], GetPanelFromPoint
- CMFCRibbonCategory [MFC], GetPanelIndex
- CMFCRibbonCategory [MFC], GetParentButton
- CMFCRibbonCategory [MFC], GetParentMenuBar
- CMFCRibbonCategory [MFC], GetParentRibbonBar
- CMFCRibbonCategory [MFC], GetRect
- CMFCRibbonCategory [MFC], GetSmallImages
- CMFCRibbonCategory [MFC], GetTabColor
- CMFCRibbonCategory [MFC], GetTabRect
- CMFCRibbonCategory [MFC], GetTextTopLine
- CMFCRibbonCategory [MFC], GetVisibleElements
- CMFCRibbonCategory [MFC], HighlightPanel
- CMFCRibbonCategory [MFC], HitTest
- CMFCRibbonCategory [MFC], HitTestEx
- CMFCRibbonCategory [MFC], HitTestScrollButtons
- CMFCRibbonCategory [MFC], IsActive
- CMFCRibbonCategory [MFC], IsVisible
- CMFCRibbonCategory [MFC], IsWindows7Look
- CMFCRibbonCategory [MFC], NotifyControlCommand
- CMFCRibbonCategory [MFC], OnCancelMode
- CMFCRibbonCategory [MFC], OnDraw
- CMFCRibbonCategory [MFC], OnDrawImage
- CMFCRibbonCategory [MFC], OnDrawMenuBorder
- CMFCRibbonCategory [MFC], OnKey
- CMFCRibbonCategory [MFC], OnLButtonDown
- CMFCRibbonCategory [MFC], OnLButtonUp
- CMFCRibbonCategory [MFC], OnMouseMove
- CMFCRibbonCategory [MFC], OnRTLChanged
- CMFCRibbonCategory [MFC], OnScrollHorz
- CMFCRibbonCategory [MFC], OnUpdateCmdUI
- CMFCRibbonCategory [MFC], RecalcLayout
- CMFCRibbonCategory [MFC], RemovePanel
- CMFCRibbonCategory [MFC], ReposPanels
- CMFCRibbonCategory [MFC], SetCollapseOrder
- CMFCRibbonCategory [MFC], SetData
- CMFCRibbonCategory [MFC], SetKeys
- CMFCRibbonCategory [MFC], SetName
- CMFCRibbonCategory [MFC], SetTabColor
ms.assetid: 99ba25b6-d060-4fdd-bfab-3c46c22981bb
ms.openlocfilehash: 14ce057c141f22c14361bafd55fce3ccd345d4dd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237415"
---
# <a name="cmfcribboncategory-class"></a>CMFCRibbonCategory クラス

`CMFCRibbonCategory`クラス実装のグループを含むリボン タブ[リボン パネル](../../mfc/reference/cmfcribbonpanel-class.md)します。

## <a name="syntax"></a>構文

```
class CMFCRibbonCategory : public CObject
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonCategory::CMFCRibbonCategory](#cmfcribboncategory)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonCategory::AddHidden](#addhidden)|リボン カテゴリを非表示の要素を追加します。|
|[CMFCRibbonCategory::AddPanel](#addpanel)|リボン カテゴリには、新しいパネルを追加します。|
|[CMFCRibbonCategory::CopyFrom](#copyfrom)||
|[CMFCRibbonCategory::FindByData](#findbydata)||
|[CMFCRibbonCategory::FindByID](#findbyid)||
|[CMFCRibbonCategory::FindPanelWithElem](#findpanelwithelem)||
|[CMFCRibbonCategory::GetContextID](#getcontextid)|リボン カテゴリのコンテキスト ID を返します。|
|[CMFCRibbonCategory::GetData](#getdata)|リボン カテゴリに関連付けられているユーザー定義データを返します。|
|[CMFCRibbonCategory::GetDroppedDown](#getdroppeddown)||
|[CMFCRibbonCategory::GetElements](#getelements)||
|[CMFCRibbonCategory::GetElementsByID](#getelementsbyid)||
|[CMFCRibbonCategory::GetFirstVisibleElement](#getfirstvisibleelement)|リボン カテゴリに属している最初の可視要素を取得します。|
|[CMFCRibbonCategory::GetFocused](#getfocused)|フォーカスされた要素を返します。|
|[CMFCRibbonCategory::GetHighlighted](#gethighlighted)|強調表示されている要素を返します。|
|[CMFCRibbonCategory::GetImageCount](#getimagecount)||
|[CMFCRibbonCategory::GetImageSize](#getimagesize)||
|[CMFCRibbonCategory::GetItemIDsList](#getitemidslist)||
|[CMFCRibbonCategory::GetLastVisibleElement](#getlastvisibleelement)|リボン カテゴリに属している最後の可視要素を取得します。|
|[CMFCRibbonCategory::GetLargeImages](#getlargeimages)|リボン カテゴリを使用する大きいイメージの一覧への参照を返します。|
|[CMFCRibbonCategory::GetMaxHeight](#getmaxheight)||
|[CMFCRibbonCategory::GetName](#getname)||
|[CMFCRibbonCategory::GetPanel](#getpanel)|指定したインデックス位置にあるリボン パネルへのポインターを返します。|
|[CMFCRibbonCategory::GetPanelCount](#getpanelcount)|リボン カテゴリには、リボン パネルの数を返します。|
|[CMFCRibbonCategory::GetPanelFromPoint](#getpanelfrompoint)||
|[CMFCRibbonCategory::GetPanelIndex](#getpanelindex)|指定されたリボン パネルのインデックスを返します。|
|[CMFCRibbonCategory::GetParentButton](#getparentbutton)||
|[CMFCRibbonCategory::GetParentMenuBar](#getparentmenubar)||
|[CMFCRibbonCategory::GetParentRibbonBar](#getparentribbonbar)||
|[CMFCRibbonCategory::GetRect](#getrect)||
|[CMFCRibbonCategory::GetSmallImages](#getsmallimages)|カテゴリで使用される小さいイメージの一覧への参照を返します。|
|[CMFCRibbonCategory::GetTabColor](#gettabcolor)|リボンの [カテゴリ] タブの現在の色を返します。|
|[CMFCRibbonCategory::GetTabRect](#gettabrect)||
|[CMFCRibbonCategory::GetTextTopLine](#gettexttopline)||
|[CMFCRibbonCategory::GetVisibleElements](#getvisibleelements)|リボン カテゴリに属するすべての可視要素を取得します。|
|[CMFCRibbonCategory::HighlightPanel](#highlightpanel)||
|[CMFCRibbonCategory::HitTest](#hittest)||
|[CMFCRibbonCategory::HitTestEx](#hittestex)||
|[CMFCRibbonCategory::HitTestScrollButtons](#hittestscrollbuttons)||
|[CMFCRibbonCategory::IsActive](#isactive)||
|[CMFCRibbonCategory::IsVisible](#isvisible)|リボンのカテゴリが表示されるかどうかを判断します。|
|[CMFCRibbonCategory::IsWindows7Look](#iswindows7look)|親のリボンに外観が Windows 7 スタイル (小さな四角形のアプリケーション ボタン) があるかどうかを示します|
|[CMFCRibbonCategory::NotifyControlCommand](#notifycontrolcommand)||
|[CMFCRibbonCategory::OnCancelMode](#oncancelmode)||
|[CMFCRibbonCategory::OnDraw](#ondraw)||
|[CMFCRibbonCategory::OnDrawImage](#ondrawimage)||
|[CMFCRibbonCategory::OnDrawMenuBorder](#ondrawmenuborder)||
|[CMFCRibbonCategory::OnKey](#onkey)|ユーザーがキーボード ボタンを押したときに、フレームワークによって呼び出されます。|
|[CMFCRibbonCategory::OnLButtonDown](#onlbuttondown)||
|[CMFCRibbonCategory::OnLButtonUp](#onlbuttonup)||
|[CMFCRibbonCategory::OnMouseMove](#onmousemove)||
|[CMFCRibbonCategory::OnRTLChanged](#onrtlchanged)||
|[CMFCRibbonCategory::OnScrollHorz](#onscrollhorz)||
|[CMFCRibbonCategory::OnUpdateCmdUI](#onupdatecmdui)||
|[CMFCRibbonCategory::RecalcLayout](#recalclayout)||
|[CMFCRibbonCategory::RemovePanel](#removepanel)||
|[CMFCRibbonCategory::ReposPanels](#repospanels)||
|[CMFCRibbonCategory::SetCollapseOrder](#setcollapseorder)|リボン カテゴリに存在するリボン パネルの折りたたみの順序を定義します。|
|[CMFCRibbonCategory::SetData](#setdata)|リボン カテゴリには、ユーザー定義データを格納します。|
|[CMFCRibbonCategory::SetKeys](#setkeys)|Keytip をリボン カテゴリに割り当てます。|
|[CMFCRibbonCategory::SetName](#setname)||
|[Cmfcribboncategory::settabcolor](#settabcolor)|リボン カテゴリの色を設定します。|

## <a name="remarks"></a>Remarks

通常、カテゴリを作成していないリボン直接呼び出すことによって[CMFCRibbonBar::AddCategory](../../mfc/reference/cmfcribbonbar-class.md#addcategory)、新しく作成されたリボン カテゴリへのポインターを返します。 呼び出すことによって、カテゴリにパネルを追加する[CMFCRibbonCategory::AddPanel](#addpanel)します。

`CMFCRibbonTab`クラスのリボン カテゴリを描画します。 派生される[CMFCRibbonBaseElement クラス](../../mfc/reference/cmfcribbonbaseelement-class.md)します。

次の例では、リボン カテゴリを作成し、これにパネルを追加する方法を示します。

```cpp
// Create a new ribbon category and get a pointer to it`
CMFCRibbonCategory* pCategory = m_wndRibbonBar.AddCategory
    (_T("&Write"),           // Category name
    IDB_WRITE,               // Category small images (16 x 16)
    IDB_WRITE_LARGE);        // Category large images (32 x 32)

// Add a panel to the new category
CMFCRibbonPanel* pPanel = pCategory->AddPanel (
    _T("Clipboard"),                // Panel name
    m_PanelIcons.ExtractIcon (0));  // Panel icon
```

次の図は、[Home] カテゴリ RibbonApp サンプル アプリケーションからの図を示します。

![RibbonApp サンプル アプリケーションからホーム カテゴリ](../../mfc/reference/media/cmfcribboncategory.png "RibbonApp サンプル アプリケーションから [Home] カテゴリ")

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMFCRibbonCategory`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxribboncategory.h

##  <a name="addhidden"></a>  CMFCRibbonCategory::AddHidden

[カスタマイズ] ダイアログ ボックスに表示されるリボン要素の配列に指定されたリボン要素を追加します。

```
void AddHidden(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>パラメーター

*pElem*<br/>
[in]リボン要素へのポインター。

### <a name="remarks"></a>Remarks

[カスタマイズ] ダイアログ ボックスのリボン要素は、クイック アクセス ツールバーに追加できるコマンドです。

##  <a name="addpanel"></a>  CMFCRibbonCategory::AddPanel

リボン カテゴリをリボン パネルを作成します。

```
CMFCRibbonPanel* AddPanel(
    LPCTSTR lpszPanelName,
    HICON hIcon = 0,
    CRuntimeClass* pRTI = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszPanelName*<br/>
[in]新しいリボン パネルの名前へのポインター。

*hIcon*<br/>
[in]新しいリボン パネルの既定のアイコンへのハンドルします。

*pRTI*<br/>
[in]カスタム リボン パネルのランタイム クラス情報へのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、新しいリボン パネルへのポインターそれ以外の場合、パネルが作成されていない場合は NULL です。

### <a name="remarks"></a>Remarks

カスタム リボン パネルを作成する場合のランタイム クラス情報を指定する必要があります*pRTI*します。 カスタム リボン パネル クラスから派生する必要があります、`CMFCRibbonPanel`クラス。

リボン要素を表示する十分な領域がある場合に、リボン パネルの既定のアイコンが表示されます。

### <a name="example"></a>例

次の例では、使用する方法、`AddPanel`メソッドで、`CMFCRibbonCategory`クラス。

[!code-cpp[NVC_MFC_RibbonApp#10](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_1.cpp)]

##  <a name="cmfcribboncategory"></a>  CMFCRibbonCategory::CMFCRibbonCategory

構築し、初期化、 [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)オブジェクト。

```
CMFCRibbonCategory(
    CMFCRibbonBar* pParenrRibbonBar,
    LPCTSTR lpszName,
    UINT uiSmallImagesResID,
    UINT uiLargeImagesResID,
    CSize sizeSmallImage = CSize(16,
    16),
    CSize sizeLargeImage = CSize(32,
    32));
```

### <a name="parameters"></a>パラメーター

*pParenrRibbonBar*<br/>
[in]リボン カテゴリの親のリボン バーへのポインター。

*lpszName*<br/>
[in]リボン カテゴリの名前。

*uiSmallImagesResID*<br/>
[in]リボン カテゴリ内のリボン要素で使用される小さいイメージのイメージ リストのリソース ID。

*uiLargeImagesResID*<br/>
[in]リボン カテゴリ内のリボン要素で使用される大きなイメージのイメージ リストのリソース ID。

*sizeSmallImage*<br/>
[in]既定のリボン カテゴリ内のリボン要素の小さいイメージのサイズ。

*sizeLargeImage*<br/>
[in]既定のリボン カテゴリ内のリボン要素の大きいイメージのサイズ。

##  <a name="copyfrom"></a>  CMFCRibbonCategory::CopyFrom

指定した状態をコピー [CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)現在[CMFCRibbonCategory](../../mfc/reference/cmfcribboncategory-class.md)オブジェクト。

```
virtual void CopyFrom(CMFCRibbonCategory& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
[in]ソース`CMFCRibbonCategory`オブジェクト。

### <a name="remarks"></a>Remarks

##  <a name="findbydata"></a>  CMFCRibbonCategory::FindByData

指定されたデータに関連付けられているリボン要素を取得します。

```
CMFCRibbonBaseElement* FindByData(
    DWORD_PTR dwData,
    BOOL bVisibleOnly = TRUE) const;
```

### <a name="parameters"></a>パラメーター

*dwData*<br/>
[in]リボン要素に関連付けられたデータ。

*bVisibleOnly*<br/>
[in]検索にすばやくアクセスできるリボン要素を含める場合は TRUE。検索にすばやくアクセスできるリボン要素を除外する場合は FALSE。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、リボン要素へのポインターそれ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

##  <a name="findbyid"></a>  CMFCRibbonCategory::FindByID

指定したコマンド ID に関連付けられているリボン要素を取得します。

```
CMFCRibbonBaseElement* FindByID(
    UINT uiCmdID,
    BOOL bVisibleOnly = TRUE) const;
```

### <a name="parameters"></a>パラメーター

*uiCmdID*<br/>
[in]リボン要素に関連付けられたコマンド ID。

*bVisibleOnly*<br/>
[in]検索にすばやくアクセスできるリボン要素を含める場合は TRUE。検索にすばやくアクセスできるリボン要素を除外する場合は FALSE。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、リボン要素へのポインターそれ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

##  <a name="findpanelwithelem"></a>  CMFCRibbonCategory::FindPanelWithElem

指定されたリボン要素を含むリボン パネルを取得します。

```
CMFCRibbonPanel* FindPanelWithElem(const CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>パラメーター

*pElement*<br/>
[in]リボン要素へのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、リボン パネルへのポインターそれ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

##  <a name="getcontextid"></a>  CMFCRibbonCategory::GetContextID

リボン カテゴリのコンテキスト ID を取得します。

```
UINT GetContextID() const;
```

### <a name="return-value"></a>戻り値

リボン カテゴリのコンテキスト ID。

### <a name="remarks"></a>Remarks

リボン カテゴリは、コンテキスト リボン カテゴリではない場合、コンテキスト ID は 0 です。

##  <a name="getdata"></a>  CMFCRibbonCategory::GetData

リボン カテゴリに関連付けられているユーザー定義データを取得します。

```
DWORD_PTR GetData() const;
```

### <a name="return-value"></a>戻り値

リボン カテゴリに関連付けられているユーザー定義データ。

##  <a name="getdroppeddown"></a>  CMFCRibbonCategory::GetDroppedDown

ポップアップ メニューが表示されているリボン要素へのポインターを取得します。

```
CMFCRibbonBaseElement* GetDroppedDown();
```

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、リボン要素へのポインターそれ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

##  <a name="getelements"></a>  CMFCRibbonCategory::GetElements

リボン カテゴリ内のすべてのリボン要素を取得します。

```
void GetElements(
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```

### <a name="parameters"></a>パラメーター

*arElements*<br/>
[入力、出力]参照を[CArray](../../mfc/reference/carray-class.md)のリボン要素。

### <a name="remarks"></a>Remarks

配列には、クイック アクセス ツールバーで使用できるように設計されたリボン要素が含まれます。

##  <a name="getelementsbyid"></a>  CMFCRibbonCategory::GetElementsByID

指定したコマンド ID に関連付けられているすべてのリボン要素を取得します

```
void GetElementsByID(
    UINT uiCmdID,
    CArray <CMFCRibbonBaseElement*, CMFCRibbonBaseElement*>& arElements);
```

### <a name="parameters"></a>パラメーター

*uiCmdID*<br/>
[in]リボン要素に関連付けられたコマンド ID。

*arElements*<br/>
[入力、出力]参照を[CArray](../../mfc/reference/carray-class.md)のリボン要素。

### <a name="remarks"></a>Remarks

配列には、クイック アクセス ツールバーで使用できるように設計されたリボン要素が含まれます。

##  <a name="getfirstvisibleelement"></a>  CMFCRibbonCategory::GetFirstVisibleElement

リボン カテゴリに属している最初の可視要素を取得します。

```
CMFCRibbonBaseElement* GetFirstVisibleElement() const;
```

### <a name="return-value"></a>戻り値

最初の可視要素へのポインターカテゴリが表示される要素を持たない場合、NULL にすることがあります。

### <a name="remarks"></a>Remarks

##  <a name="getfocused"></a>  CMFCRibbonCategory::GetFocused

フォーカスされた要素を返します。

```
CMFCRibbonBaseElement* GetFocused();
```

### <a name="return-value"></a>戻り値

フォーカスがある要素または NULL へのポインター。

### <a name="remarks"></a>Remarks

##  <a name="gethighlighted"></a>  CMFCRibbonCategory::GetHighlighted

強調表示されている要素を返します。

```
CMFCRibbonBaseElement* GetHighlighted();
```

### <a name="return-value"></a>戻り値

強調表示されている要素または要素が強調表示されていない場合は NULL へのポインター。

### <a name="remarks"></a>Remarks

##  <a name="getimagecount"></a>  CMFCRibbonCategory::GetImageCount

リボン カテゴリに含まれる指定したイメージ リスト内のイメージの数を取得します。

```
int GetImageCount(BOOL bIsLargeImage) const;
```

### <a name="parameters"></a>パラメーター

*bIsLargeImage*<br/>
[in]大きいイメージ リスト内のイメージの数の場合は TRUE。小さいイメージ リスト内のイメージの数の場合は FALSE。

### <a name="return-value"></a>戻り値

指定したイメージ リスト内のイメージの数。

### <a name="remarks"></a>Remarks

##  <a name="getimagesize"></a>  CMFCRibbonCategory::GetImageSize

リボン カテゴリに含まれている指定されたイメージ リスト内のイメージのサイズを取得します。

```
CSize GetImageSize(BOOL bIsLargeImage) const;
```

### <a name="parameters"></a>パラメーター

*bIsLargeImage*<br/>
[in]大きなイメージのサイズの場合は TRUE。小さいイメージのサイズの場合は FALSE。

### <a name="return-value"></a>戻り値

指定したイメージ リスト内のイメージのサイズ。

### <a name="remarks"></a>Remarks

取得したサイズには、グローバルのイメージ スケール係数が含まれます。

##  <a name="getitemidslist"></a>  CMFCRibbonCategory::GetItemIDsList

リボン カテゴリに含まれるリボン要素のコマンド Id を取得します。

```
void GetItemIDsList(
    CList<UINT, UINT>& lstItems,
    BOOL bHiddenOnly = FALSE) const;
```

### <a name="parameters"></a>パラメーター

*lstItems*<br/>
[out]リボン カテゴリ内のリボン要素のコマンド Id の一覧。

*bHiddenOnly*<br/>
[in]リボン カテゴリ内のリボン パネルに表示されるリボン要素を除外する場合は TRUEリボン カテゴリにすべてのリボン要素を含める場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="getlargeimages"></a>  CMFCRibbonCategory::GetLargeImages

リボン カテゴリに含まれている大きなイメージの一覧を取得します。

```
CMFCToolBarImages& GetLargeImages();
```

### <a name="return-value"></a>戻り値

リボン カテゴリに含まれている大きなイメージの一覧。

##  <a name="getlastvisibleelement"></a>  CMFCRibbonCategory::GetLastVisibleElement

リボン カテゴリに属している最後の可視要素を取得します。

```
CMFCRibbonBaseElement* GetLastVisibleElement() const;
```

### <a name="return-value"></a>戻り値

最後の可視要素へのポインターカテゴリが表示される要素を持たない場合、NULL にすることがあります。

### <a name="remarks"></a>Remarks

##  <a name="getmaxheight"></a>  CMFCRibbonCategory::GetMaxHeight

リボン カテゴリに含まれるリボン パネルの最大の高さを取得します。

```
int GetMaxHeight(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]リボン パネル用のデバイス コンテキストへのポインター。

### <a name="return-value"></a>戻り値

リボン カテゴリに含まれるリボン パネルの最大の高さ。

### <a name="remarks"></a>Remarks

取得した値には、リボン パネルの上部と下部の余白の高さが含まれています。

##  <a name="getname"></a>  CMFCRibbonCategory::GetName

リボン カテゴリの名前を取得します。

```
LPCTSTR GetName() const;
```

### <a name="return-value"></a>戻り値

リボン カテゴリの名前。

### <a name="remarks"></a>Remarks

##  <a name="getpanel"></a>  CMFCRibbonCategory::GetPanel

指定したインデックス位置にあるリボン パネルへのポインターを返します。

```
CMFCRibbonPanel* GetPanel(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]リボン パネルの 0 から始まるインデックス。

### <a name="return-value"></a>戻り値

指定したインデックス位置にあるリボン パネルへのポインター。

### <a name="remarks"></a>Remarks

場合、例外がスローされます*nIndex*が範囲外です。

##  <a name="getpanelcount"></a>  CMFCRibbonCategory::GetPanelCount

リボン カテゴリには、リボン パネルの数を返します。

```
int GetPanelCount() const;
```

### <a name="return-value"></a>戻り値

リボン カテゴリ内のリボン パネルの数。

##  <a name="getpanelfrompoint"></a>  CMFCRibbonCategory::GetPanelFromPoint

これで、指定した点がある場合は、リボン パネルへのポインターを取得します。

```
CMFCRibbonPanel* GetPanelFromPoint(CPoint point) const;
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
[in]ウィンドウの左上隅に対して相対的で、ポインターの x と y を調整します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、リボン パネルへのポインターそれ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

リボン カテゴリに含まれるリボン パネルのみがテストされます。

##  <a name="getpanelindex"></a>  CMFCRibbonCategory::GetPanelIndex

指定されたリボン パネルの 0 から始まるインデックスを取得します。

```
int GetPanelIndex(const CMFCRibbonPanel* pPanel) const;
```

### <a name="parameters"></a>パラメーター

*pPanel*<br/>
[in]リボン パネルへのポインター。

### <a name="return-value"></a>戻り値

指定されたリボン パネル、メソッドが成功した場合の 0 から始まるインデックスそれ以外の場合は-1。

### <a name="remarks"></a>Remarks

リボン カテゴリに含まれるリボン パネルのみが検索されます。

##  <a name="getparentbutton"></a>  CMFCRibbonCategory::GetParentButton

リボン カテゴリの親のリボン要素を取得します。

```
CMFCRibbonBaseElement* GetParentButton() const;
```

### <a name="return-value"></a>戻り値

親要素が存在しない場合は、親のリボン要素にポインターを返します。

### <a name="remarks"></a>Remarks

##  <a name="getparentmenubar"></a>  CMFCRibbonCategory::GetParentMenuBar

親メニュー バーへのポインターを返します、`CMFCRibbonCategory`オブジェクト。

```
CMFCRibbonPanelMenuBar* GetParentMenuBar() const;
```

### <a name="return-value"></a>戻り値

内容を返します、`m_pParentMenuBar`メンバーを保護します。

### <a name="remarks"></a>Remarks

##  <a name="getparentribbonbar"></a>  CMFCRibbonCategory::GetParentRibbonBar

リボン カテゴリの親のリボン バーを取得します。

```
CMFCRibbonBar* GetParentRibbonBar() const;
```

### <a name="return-value"></a>戻り値

リボン カテゴリの親のリボン バーへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="getrect"></a>  CMFCRibbonCategory::GetRect

リボン カテゴリを表示する四角形を取得します。

```
CRect GetRect() const;
```

### <a name="return-value"></a>戻り値

リボン カテゴリを表示する四角形。

### <a name="remarks"></a>Remarks

リボン カテゴリを表示する四角形では、[カテゴリ] タブは含まれません。

##  <a name="getsmallimages"></a>  CMFCRibbonCategory::GetSmallImages

リボン カテゴリに含まれている小さいイメージの一覧を取得します。

```
CMFCToolBarImages& GetSmallImages();
```

### <a name="return-value"></a>戻り値

リボン カテゴリに含まれている小さいイメージの一覧。

##  <a name="gettabcolor"></a>  CMFCRibbonCategory::GetTabColor

リボンの [カテゴリ] タブの現在の色を返します。

```
AFX_RibbonCategoryColor GetTabColor() const;
```

### <a name="return-value"></a>戻り値

リボンの [カテゴリ] タブの現在の色。

### <a name="remarks"></a>Remarks

返される値には、次の列挙値のいずれかを指定できます。

- AFX_CategoryColor_Red

- AFX_CategoryColor_Orange

- AFX_CategoryColor_Yellow

- AFX_CategoryColor_Green

- AFX_CategoryColor_Blue

- AFX_CategoryColor_Indigo

- AFX_CategoryColor_Violet

##  <a name="gettabrect"></a>  CMFCRibbonCategory::GetTabRect

リボンのカテゴリ タブを表示する四角形を取得します。

```
CRect GetTabRect() const;
```

### <a name="return-value"></a>戻り値

リボンのカテゴリ タブを表示する四角形。

### <a name="remarks"></a>Remarks

##  <a name="gettexttopline"></a>  CMFCRibbonCategory::GetTextTopLine

大きなイメージを表示するリボン カテゴリのリボン ボタンのテキストの垂直方向の位置を取得します。

```
int GetTextTopLine() const;
```

### <a name="return-value"></a>戻り値

大きなイメージを表示するリボン ボタンのピクセル単位でのテキストの垂直方向の位置。

### <a name="remarks"></a>Remarks

##  <a name="getvisibleelements"></a>  CMFCRibbonCategory::GetVisibleElements

リボン カテゴリに属するすべての可視要素を取得します。

```
void GetVisibleElements(
    CArray <CMFCRibbonBaseElement*,
    CMFCRibbonBaseElement*>& arElements);
```

### <a name="parameters"></a>パラメーター

*arElements*<br/>
すべての可視要素の配列。

### <a name="remarks"></a>Remarks

##  <a name="highlightpanel"></a>  CMFCRibbonCategory::HighlightPanel

指定されたリボン パネルを強調表示されます。

```
CMFCRibbonPanel* HighlightPanel(
    CMFCRibbonPanel* pHLPanel,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

*pHLPanel*<br/>
[in]強調表示するリボン パネルへのポインター。

*ポイント*<br/>
[in]ウィンドウの左上隅に対して相対的で、ポインターの x と y を調整します。

### <a name="return-value"></a>戻り値

強調表示されていたリボン パネルへのポインターこのメソッドが呼び出されたときにリボン パネルが強調表示しない場合は NULL それ以外の場合。

### <a name="remarks"></a>Remarks

リボン パネルを強調表示の詳細については、次を参照してください。 [CMFCRibbonPanel::Highlight](../../mfc/reference/cmfcribbonpanel-class.md#highlight)します。

##  <a name="hittest"></a>  CMFCRibbonCategory::HitTest

これで、指定した点がある場合は、リボン要素へのポインターを取得します。

```
CMFCRibbonBaseElement* HitTest(
    CPoint point,
    BOOL bCheckPanelCaption = FALSE) const;
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
[in]ウィンドウの左上隅に対して相対的で、マウス ポインターの x と y を調整します。

*bCheckPanelCaption*<br/>
[in]リボン パネルのキャプションをテストする場合は TRUEリボン パネルのキャプションを除外する場合は FALSE。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、リボン要素へのポインターそれ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

リボン カテゴリに含まれるリボン要素のみがテストされます。

##  <a name="hittestex"></a>  CMFCRibbonCategory::HitTestEx

これで、指定した点がある場合は、リボン要素の 0 から始まるインデックスを取得します。

```
int HitTestEx(CPoint point) const;
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
[in]ウィンドウの左上隅に対して相対的で、マウス ポインターの x と y を調整します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、リボン要素の 0 から始まるインデックスそれ以外の場合は-1。

### <a name="remarks"></a>Remarks

リボン カテゴリに含まれるリボン要素のみがテストされます。

##  <a name="hittestscrollbuttons"></a>  CMFCRibbonCategory::HitTestScrollButtons

ポイントがリボン カテゴリの左側または右側のスクロール ボタン内にある場合は、そのボタンにポインターを返します。

```
CMFCRibbonBaseElement* HitTestScrollButtons(CPoint point) const;
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
[in]テストする点です。

### <a name="return-value"></a>戻り値

場合*ポイント*外接する四角形の左のいずれかまたはリボン カテゴリの水平スクロール バーのボタン内にある、そのボタンにポインターを返しますまたは、それ以外の場合は NULL を返します。

### <a name="remarks"></a>Remarks

##  <a name="isactive"></a>  CMFCRibbonCategory::IsActive

リボンのカテゴリがリボン バーで、アクティブなカテゴリであるかどうかを示します。

```
BOOL IsActive() const;
```

### <a name="return-value"></a>戻り値

リボン カテゴリは、アクティブなカテゴリは、TRUE を返します。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

アクティブなリボン カテゴリには、リボン パネルが表示されます。

##  <a name="isvisible"></a>  CMFCRibbonCategory::IsVisible

リボン カテゴリを表示するかどうかを示します。

```
BOOL IsVisible() const;
```

### <a name="return-value"></a>戻り値

リボン カテゴリを表示する場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

表示されるリボン カテゴリは、カテゴリ タブを表示します。

##  <a name="iswindows7look"></a>  CMFCRibbonCategory::IsWindows7Look

親リボンが Windows 7 の検索 (小さな四角形のアプリケーション ボタン) を持つかどうかを示します。

```
BOOL IsWindows7Look() const;
```

### <a name="return-value"></a>戻り値

TRUE の場合、親のリボンになります。 Windows 7それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="notifycontrolcommand"></a>  CMFCRibbonCategory::NotifyControlCommand

すべてに WM_NOTIFY コマンド メッセージを配信`CMFCRibbonPanel`内の要素、`CMFCRibbonCategory`まで、メッセージを処理します。

```
virtual BOOL NotifyControlCommand(
    BOOL bAccelerator,
    int nNotifyCode,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>パラメーター

*bAccelerator*<br/>
[in]それ以外の場合、アクセラレータまたは FALSE から発生した場合は TRUE コマンド。

*nNotifyCode*<br/>
[in]通知コード。

*wParam*<br/>
[in]メッセージの WPARAM フィールドです。

*lParam*<br/>
[in]メッセージの LPARAM フィールドです。

### <a name="return-value"></a>戻り値

メッセージが処理された場合は TRUE またはしない場合は FALSE を返します。

### <a name="remarks"></a>Remarks

##  <a name="oncancelmode"></a>  CMFCRibbonCategory::OnCancelMode

すべてのモードを [キャンセル] を呼び出す、`CMFCRibbonPanel`の要素、`CMFCRibbonCategory`します。

```
virtual void OnCancelMode();
```

### <a name="remarks"></a>Remarks

##  <a name="ondraw"></a>  CMFCRibbonCategory::OnDraw

リボン カテゴリを描画するためにフレームワークによって呼び出されます。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]リボン カテゴリのデバイス コンテキストへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="ondrawimage"></a>  CMFCRibbonCategory::OnDrawImage

リボン カテゴリを指定したイメージを描画するためにフレームワークによって呼び出されます。

```
virtual BOOL OnDrawImage(
    CDC* pDC,
    CRect rect,
    CMFCRibbonBaseElement* pElement,
    BOOL bIsLargeImage,
    BOOL nImageIndex,
    BOOL bCenter);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]イメージのデバイス コンテキストへのポインター。

*rect*<br/>
[in]イメージの四角形を表示します。

*pElement*<br/>
[in]イメージを含むリボン要素へのポインター。

*bIsLargeImage*<br/>
[in]イメージが、大きなサイズの場合は TRUE。イメージはサイズが小さい場合は FALSE。

*nImageIndex*<br/>
[in]リボン カテゴリに含まれているイメージ配列内のイメージの 0 から始まるインデックス。

*bCenter*<br/>
[in]表示の四角形に画像を中央揃えする場合は TRUE表示する四角形の左上隅で、イメージを描画する場合は FALSE。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="ondrawmenuborder"></a>  CMFCRibbonCategory::OnDrawMenuBorder

ポップアップ メニューの境界線を描画するためにフレームワークによって呼び出されます。

```
virtual void OnDrawMenuBorder(
    CDC* pDC,
    CMFCRibbonPanelMenuBar* pMenuBar);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]このパラメーターは使用されません。

*pMenuBar*<br/>
[in]このパラメーターは使用されません。

### <a name="remarks"></a>Remarks

既定では、このメソッドは何もしません。 ポップアップ メニューの枠線を描画するには、このメソッドをオーバーライドします。

##  <a name="onkey"></a>  CMFCRibbonCategory::OnKey

ユーザーがキーボード ボタンを押したときに、フレームワークによって呼び出されます。

```
virtual BOOL OnKey(UINT nChar);
```

### <a name="parameters"></a>パラメーター

*NChar*<br/>
ユーザーが押されたキーの仮想キー コード。

### <a name="remarks"></a>Remarks

##  <a name="onlbuttondown"></a>  CMFCRibbonCategory::OnLButtonDown

ユーザーがマウスの左ボタンを押したときに、指定したポイントの下でリボン要素を取得するためにフレームワークによって呼び出されます。

```
virtual CMFCRibbonBaseElement* OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
[in]ウィンドウの左上隅に対して相対的で、マウス ポインターの x と y を調整します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、リボン要素へのポインターそれ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

##  <a name="onlbuttonup"></a>  CMFCRibbonCategory::OnLButtonUp

リボン カテゴリ上にポインターがマウスの左ボタンを離したときに、フレームワークによって呼び出されます。

```
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
[in]ウィンドウの左上隅に対して相対的で、ポインターの x と y を調整します。

### <a name="remarks"></a>Remarks

##  <a name="onmousemove"></a>  CMFCRibbonCategory::OnMouseMove

リボン カテゴリの表示を更新するにはリボン バーで、ポインターが移動したときに、フレームワークによって呼び出されます。

```
virtual void OnMouseMove(CPoint point);
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
[in]ウィンドウの左上隅に対して相対的で、ポインターの x と y を調整します。

### <a name="remarks"></a>Remarks

##  <a name="onrtlchanged"></a>  CMFCRibbonCategory::OnRTLChanged

レイアウトの方向を変更するときに、フレームワークによって呼び出されます。

```
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>パラメーター

*bIsRTL*<br/>
[in]レイアウトは右から左の場合は TRUE。レイアウトが左から右の場合は FALSE です。

### <a name="remarks"></a>Remarks

このメソッドは、すべてのリボン パネルとリボン カテゴリに含まれるリボン要素のレイアウトを調整します。

##  <a name="onscrollhorz"></a>  CMFCRibbonCategory::OnScrollHorz

リボン カテゴリを水平方向にスクロールします。

```
virtual BOOL OnScrollHorz(
    BOOL bScrollLeft,
    int nScrollOffset = 0);
```

### <a name="parameters"></a>パラメーター

*bScrollLeft*<br/>
[in]左にスクロールする場合は TRUE右にスクロールする場合は FALSE。

*nScrollOffset*<br/>
[in]スクロールの距離 (ピクセル単位)。

### <a name="return-value"></a>戻り値

リボン カテゴリは水平方向の方向に移動した場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="onupdatecmdui"></a>  CMFCRibbonCategory::OnUpdateCmdUI

呼び出し、`OnUpdateCmdUI`の各メンバー関数、`CMFCRibbonPanel`の要素、`CMFCRibbonCategory`有効またはそれらのユーザー インターフェイス要素を無効にします。

```
virtual void OnUpdateCmdUI(
    CMFCRibbonCmdUI* pCmdUI,
    CFrameWnd* pTarget,
    BOOL bDisableIfNoHndler);
```

### <a name="parameters"></a>パラメーター

*pCmdUI*<br/>
[in]ポインター、`CMFCRibbonCmdUI`を無効にするにはこれを有効にするユーザー インターフェイス要素であると指定するオブジェクト。

*pTarget*<br/>
[in]有効にするか、ユーザー インターフェイス要素の無効化を制御するウィンドウへのポインター。

*持たず*<br/>
[in]メッセージ マップでハンドラーが定義されていない場合は、ユーザー インターフェイス項目を無効にする場合は TRUEそれ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="recalclayout"></a>  CMFCRibbonCategory::RecalcLayout

リボン カテゴリのすべてのコントロールのレイアウトを調整します。

```
virtual void RecalcLayout(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]リボン カテゴリのデバイス コンテキストへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="removepanel"></a>  CMFCRibbonCategory::RemovePanel

リボン カテゴリから、リボン パネルを削除します。

```cpp
BOOL RemovePanel(
    int nIndex,
    BOOL bDelete = TRUE);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]削除するパネルのインデックス番号。 呼び出すことによって取得、 [CMFCRibbonCategory::GetPanelIndex](#getpanelindex)メソッド。

*bDelete*<br/>
[in]パネル オブジェクトをメモリから削除する場合は TRUEパネル オブジェクトを削除せずには FALSE です。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合、FALSE です。

##  <a name="repospanels"></a>  CMFCRibbonCategory::ReposPanels

リボン カテゴリに含まれるリボン パネルのすべてのコントロールのレイアウトを調整します。

```
virtual void ReposPanels(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]リボン カテゴリに含まれるリボン パネル用のデバイス コンテキストへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="setcollapseorder"></a>  CMFCRibbonCategory::SetCollapseOrder

リボン カテゴリのリボン パネルを折りたたむ順序を定義します。

```
void SetCollapseOrder(const CArray<int,int>& arCollapseOrder);
```

### <a name="parameters"></a>パラメーター

*arCollapseOrder*<br/>
[in]折りたたみの順序を指定します。 配列には、リボン パネルの 0 から始まるインデックスが含まれています。

### <a name="remarks"></a>Remarks

ライブラリは、折りたたみの順序を定義します。 ただし、折りたたみの順序を指定するインデックスの一覧で、カテゴリを提供することで、この動作をカスタマイズできます。

カテゴリをリボン パネルを折りたたむことが検出されると、指定されたリストの次の要素を検索します。 リストが空、または十分な要素が指定されていない、カテゴリは内部アルゴリズムを使用します。

たとえば、カテゴリは、3 つのリボン パネルが、すべてのパネルが完全に折りたたまれた状態になるまで何度もを折りたたむことができます。 次の折りたたみの順序を設定できます。0, 0, 2, 2. この場合は、カテゴリは 2 回に、[0] パネルに折りたたむ、パネル 2 の 2 倍です。 1 のインデックスを持つパネルは折りたたまれていない状態のままになります。

### <a name="example"></a>例

次の例では、使用する方法、`SetCollapseOrder`メソッドで、`CMFCRibbonCategory`クラス。 例では、折りたたみ注文の配列を構築する方法とリボン カテゴリを折りたたみの順序を設定する方法を示します。

[!code-cpp[NVC_MFC_RibbonApp#13](../../mfc/reference/codesnippet/cpp/cmfcribboncategory-class_2.cpp)]

##  <a name="setdata"></a>  CMFCRibbonCategory::SetData

リボン カテゴリに関連付けられたユーザー定義データを設定します。

```
void SetData(DWORD_PTR dwData);
```

### <a name="parameters"></a>パラメーター

*dwData*<br/>
[in]ユーザー定義データ。

##  <a name="setkeys"></a>  CMFCRibbonCategory::SetKeys

Keytip をリボン カテゴリに割り当てます。

```
void SetKeys(LPCTSTR lpszKeys);
```

### <a name="parameters"></a>パラメーター

*lpszKeys*<br/>
[in]Keytip のテキスト。

### <a name="remarks"></a>Remarks

ユーザーが Alt キーまたは F10 キーを押すと、キー ヒントが表示されます。

##  <a name="setname"></a>  CMFCRibbonCategory::SetName

リボン カテゴリには、名前と keytip を割り当てます。

```
void SetName(LPCTSTR lpszName);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
[in]名前とリボン カテゴリの keytip。

### <a name="remarks"></a>Remarks

リボン カテゴリの keytip を設定する追加の keytip の文字に続く改行エスケープ シーケンス*lpszName*します。

##  <a name="settabcolor"></a>  CMFCRibbonCategory::SetTabColor

リボン カテゴリの色を設定します。

```
void SetTabColor(AFX_RibbonCategoryColor color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
[in]新しいリボン カテゴリの色を指定します。

### <a name="remarks"></a>Remarks

色には、次の値のいずれかを指定できます。

- AFX_CategoryColor_None

- AFX_CategoryColor_Red

- AFX_CategoryColor_Orange

- AFX_CategoryColor_Yellow

- AFX_CategoryColor_Green

- AFX_CategoryColor_Blue

- AFX_CategoryColor_Indigo

- AFX_CategoryColor_Violet

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)
