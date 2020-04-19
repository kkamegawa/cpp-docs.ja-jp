---
title: CMFCToolBarComboBoxButton クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::AddSortedItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::Compare
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::CreateEdit
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::DeleteItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::FindItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetByCmd
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetComboBox
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCount
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCountAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSel
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetCurSelAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetEditCtrl
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemData
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetItemDataPtrAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetText
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::GetTextAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::IsFlatMode
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::RemoveAllItems
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItem
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SelectItemAll
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetCenterVert
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetDropDownHeight
- AFXTOOLBARCOMBOBOXBUTTON/CMFCToolBarComboBoxButton::SetFlatMode
helpviewer_keywords:
- CMFCToolBarComboBoxButton [MFC], CMFCToolBarComboBoxButton
- CMFCToolBarComboBoxButton [MFC], AddItem
- CMFCToolBarComboBoxButton [MFC], AddSortedItem
- CMFCToolBarComboBoxButton [MFC], Compare
- CMFCToolBarComboBoxButton [MFC], CreateEdit
- CMFCToolBarComboBoxButton [MFC], DeleteItem
- CMFCToolBarComboBoxButton [MFC], FindItem
- CMFCToolBarComboBoxButton [MFC], GetByCmd
- CMFCToolBarComboBoxButton [MFC], GetComboBox
- CMFCToolBarComboBoxButton [MFC], GetCount
- CMFCToolBarComboBoxButton [MFC], GetCountAll
- CMFCToolBarComboBoxButton [MFC], GetCurSel
- CMFCToolBarComboBoxButton [MFC], GetCurSelAll
- CMFCToolBarComboBoxButton [MFC], GetEditCtrl
- CMFCToolBarComboBoxButton [MFC], GetItem
- CMFCToolBarComboBoxButton [MFC], GetItemAll
- CMFCToolBarComboBoxButton [MFC], GetItemData
- CMFCToolBarComboBoxButton [MFC], GetItemDataAll
- CMFCToolBarComboBoxButton [MFC], GetItemDataPtrAll
- CMFCToolBarComboBoxButton [MFC], GetText
- CMFCToolBarComboBoxButton [MFC], GetTextAll
- CMFCToolBarComboBoxButton [MFC], IsCenterVert
- CMFCToolBarComboBoxButton [MFC], IsFlatMode
- CMFCToolBarComboBoxButton [MFC], RemoveAllItems
- CMFCToolBarComboBoxButton [MFC], SelectItem
- CMFCToolBarComboBoxButton [MFC], SelectItemAll
- CMFCToolBarComboBoxButton [MFC], SetCenterVert
- CMFCToolBarComboBoxButton [MFC], SetDropDownHeight
- CMFCToolBarComboBoxButton [MFC], SetFlatMode
ms.assetid: 32fa39f7-8e4e-4f0a-a31d-7b540d969a6c
ms.openlocfilehash: 639a5f98ff4780bd26388796039e85b812621b36
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915969"
---
# <a name="cmfctoolbarcomboboxbutton-class"></a>CMFCToolBarComboBoxButton クラス

コンボボックスコントロール ( [CComboBox クラス](../../mfc/reference/ccombobox-class.md)) を含むツールバーボタン。

## <a name="syntax"></a>構文

```
class CMFCToolBarComboBoxButton : public CMFCToolBarButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton](#cmfctoolbarcomboboxbutton)|`CMFCToolBarComboBoxButton` を構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCToolBarComboBoxButton:: AddItem](#additem)|コンボボックスリストの末尾に項目を追加します。|
|[CMFCToolBarComboBoxButton::AddSortedItem](#addsorteditem)|コンボボックスの一覧に項目を追加します。 リスト内の項目の順序は、によっ`Compare`て指定されます。|
|[CMFCToolBarComboBoxButton:: Compare](#compare)|2つの項目を比較します。 をコンボボックスリストに`AddSortedItems`追加する項目を並べ替えるために呼び出されます。|
|[CMFCToolBarComboBoxButton:: CreateEdit](#createedit)|コンボボックスボタンの新しいエディットコントロールを作成します。|
|[CMFCToolBarComboBoxButton::D eleteItem](#deleteitem)|コンボボックスリストから項目を削除します。|
|[CMFCToolBarComboBoxButton:: FindItem](#finditem)|指定した文字列を含む項目のインデックスを返します。|
|[CMFCToolBarComboBoxButton:: GetByCmd](#getbycmd)|指定されたコマンド ID を持つコンボボックスボタンへのポインターを返します。|
|[CMFCToolBarComboBoxButton:: GetComboBox](#getcombobox)|コンボボックスボタンに埋め込まれているコンボボックスコントロールへのポインターを返します。|
|[CMFCToolBarComboBoxButton:: GetCount](#getcount)|コンボボックスリスト内の項目数を返します。|
|[CMFCToolBarComboBoxButton:: GetCountAll](#getcountall)|指定されたコマンド ID を持つコンボボックスボタンを検索します。 そのボタンのコンボボックスリスト内の項目数を返します。|
|[CMFCToolBarComboBoxButton:: GetCurSel](#getcursel)|コンボボックスリスト内の選択された項目のインデックスを返します。|
|[CMFCToolBarComboBoxButton:: GetCurSelAll](#getcurselall)|指定されたコマンド ID を持つコンボボックスボタンを検索し、そのボタンのコンボボックスリスト内で選択された項目のインデックスを返します。|
|[CMFCToolBarComboBoxButton::GetEditCtrl](#geteditctrl)|コンボボックスボタンに埋め込まれているエディットコントロールへのポインターを返します。|
|[CMFCToolBarComboBoxButton:: GetItem](#getitem)|コンボボックスリスト内の指定したインデックスに関連付けられている文字列を返します。|
|[CMFCToolBarComboBoxButton::GetItemAll](#getitemall)|指定されたコマンド ID を持つコンボボックスボタンを検索し、そのボタンのコンボボックスリスト内のインデックスに関連付けられている文字列を返します。|
|[CMFCToolBarComboBoxButton::GetItemData](#getitemdata)|コンボボックスリスト内の指定したインデックスに関連付けられている32ビット値を返します。|
|[CMFCToolBarComboBoxButton::GetItemDataAll](#getitemdataall)|指定されたコマンド ID を持つコンボボックスボタンを検索し、そのボタンのコンボボックスリスト内のインデックスに関連付けられている32ビット値を返します。|
|[CMFCToolBarComboBoxButton::GetItemDataPtrAll](#getitemdataptrall)|指定されたコマンド ID を持つコンボボックスボタンを検索します。 そのボタンのコンボボックスリスト内のインデックスに関連付けられている32ビット値を取得し、32ビット値をポインターとして返します。|
|[CMFCToolBarComboBoxButton:: GetText](#gettext)|コンボボックスの編集コントロールからテキストを返します。|
|[CMFCToolBarComboBoxButton::GetTextAll](#gettextall)|指定したコマンド ID を持つコンボボックスボタンを検索し、そのボタンの編集コントロールからテキストを返します。|
|[CMFCToolBarComboBoxButton::IsCenterVert](#iscentervert)|アプリケーションのコンボボックスボタンをツールバーの上部に配置するか、配置するかを決定します。|
|[CMFCToolBarComboBoxButton::IsFlatMode](#isflatmode)|アプリケーションのコンボボックスボタンの外観がフラットであるかどうかを決定します。|
|[CMFCToolBarComboBoxButton::RemoveAllItems](#removeallitems)|コンボボックスのリストボックスおよびエディットコントロールからすべての項目を削除します。|
|[CMFCToolBarComboBoxButton:: SelectItem](#selectitem)|インデックス、32ビット値、または文字列に基づいてコンボボックス内の項目を選択し、選択内容についてコンボボックスコントロールに通知します。|
|[CMFCToolBarComboBoxButton::SelectItemAll](#selectitemall)|指定されたコマンド ID を持つコンボボックスボタンを検索します。 文字列`SelectItem` 、インデックス、または32ビット値に従って、そのボタンのコンボボックス内の項目を選択するためにを呼び出します。|
|[CMFCToolBarComboBoxButton:: Set中央の垂直](#setcentervert)|アプリケーションのコンボボックスボタンを垂直方向に中央揃えにするか、またはツールバーの上部に配置するかを指定します。|
|[CMFCToolBarComboBoxButton:: SetDropDownHeight](#setdropdownheight)|ドロップダウンリストボックスの高さを設定します。|
|[CMFCToolBarComboBoxButton::SetFlatMode](#setflatmode)|アプリケーションのコンボボックスボタンの外観をフラットにするかどうかを指定します。|

## <a name="remarks"></a>Remarks

ツールバーにコンボボックスボタンを追加するには、次の手順を実行します。

1. 親ツール バー リソースでボタンのダミー リソース ID を予約します。

2.   `CMFCToolBarComboBoxButton` オブジェクトを構築します。

3. AFX_WM_RESETTOOLBAR メッセージを処理するメッセージハンドラーで、 [Cmfctoolbar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)を使用して、ダミーボタンを新しいコンボボックスボタンに置き換えます。

詳細については、「[チュートリアル:ツールバー](../../mfc/walkthrough-putting-controls-on-toolbars.md)にコントロールを配置する。 コンボボックスのツールバーボタンの例については、「プロジェクト VisualStudioDemo」の例を参照してください。

## <a name="example"></a>例

`CMFCToolBarComboBoxButton` クラスのさまざまなメソッドの使用方法を次の例に示します。 この例では、エディットボックスとコンボボックスを有効にし、アプリケーションでコンボボックスボタンの垂直位置を設定し、ドロップダウン時にリストボックスの高さを設定し、アプリケーションでコンボボックスボタンのフラットスタイルの外観を設定する方法を示します。 をクリックし、コンボボックスボタンのエディットボックスのテキストを設定します。 このコードスニペットは、 [Visual Studio のデモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_VisualStudioDemo#36](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_1.cpp)]
[!code-cpp[NVC_MFC_VisualStudioDemo#37](../../mfc/codesnippet/cpp/cmfctoolbarcomboboxbutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtoolbarcomboboxbutton

##  <a name="additem"></a>CMFCToolBarComboBoxButton:: AddItem

リストボックスに一意の項目を追加します。

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>パラメーター

*lpszItem*<br/>
からリストボックスに追加する項目のテキスト。

*dwData*<br/>
からリストボックスに追加する項目に関連付けられたデータ。

### <a name="return-value"></a>戻り値

リストボックス内の最後の項目のインデックス。

### <a name="remarks"></a>Remarks

リストボックスのスタイルが並べ替えられている場合は、このメソッドを使用しないでください。

項目のテキストが既にリストボックスにある場合、新しいデータは既存の項目と共に格納されます。 項目の検索では大文字と小文字が区別されます。

##  <a name="addsorteditem"></a>CMFCToolBarComboBoxButton::AddSortedItem

[Compare](#compare)メソッドによって定義された順序でリストボックスに項目を追加します。

```
virtual INT_PTR AddSortedItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>パラメーター

*lpszItem*<br/>
からリストボックスに追加する項目のテキスト。

*dwData*<br/>
からリストボックスに追加する項目に関連付けられたデータ。

### <a name="return-value"></a>戻り値

リストボックスに追加された項目のインデックス。

### <a name="remarks"></a>Remarks

この関数を使用すると、リストボックスに特定の順序で項目を追加できます。

##  <a name="canbestretched"></a>CMFCToolBarComboBoxButton:: CanBeStretched

コンボボックスボタンのサイズを変更できるかどうかを示します。

```
virtual BOOL CanBeStretched() const;
```

### <a name="return-value"></a>戻り値

TRUE を返します。

##  <a name="cmfctoolbarcomboboxbutton"></a>CMFCToolBarComboBoxButton::CMFCToolBarComboBoxButton

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)オブジェクトを構築します。

```
CMFCToolBarComboBoxButton(
    UINT uiID,
    int iImage,
    DWORD dwStyle=CBS_DROPDOWNLIST,
    int iWidth=0);
```

### <a name="parameters"></a>パラメーター

*uiID*<br/>
から新しいボタンのコマンド ID。

*iImage*<br/>
から[新規] ボタンに関連付けられているイメージのイメージインデックス。

*dwStyle*<br/>
から新しいボタンのスタイル。

*iWidth*<br/>
から新しいボタンの幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

既定の幅は150ピクセルです。

ツールバーボタンのスタイルの一覧については、「 [Toolbar コントロールスタイル](../../mfc/reference/toolbar-control-styles.md)」を参照してください。

##  <a name="cleardata"></a>CMFCToolBarComboBoxButton:: ClearData

ユーザー定義データを削除します。

```
virtual void ClearData();
```

### <a name="remarks"></a>Remarks

既定では、このメソッドは何も行いません。 ユーザー定義データを削除する場合は、派生クラスでこのメソッドをオーバーライドします。

##  <a name="compare"></a>CMFCToolBarComboBoxButton:: Compare

2 つの文字列を比較します。

```
virtual int Compare(
    LPCTSTR lpszItem1,
    LPCTSTR lpszItem2);
```

### <a name="parameters"></a>パラメーター

*lpszItem1*<br/>
から比較する最初の文字列。

*lpszItem2*<br/>
から比較する2番目の文字列。

### <a name="return-value"></a>戻り値

文字列間の、大文字と小文字を区別する辞書式の関係を示す値。 次の表に、使用可能な値を示します。

|[値]|説明|
|-----------|-----------------|
|\<0|最初の文字列が2番目の文字列未満です。|
|0|最初の文字列は2番目の文字列に相当します。|
|>0|最初の文字列が2番目の文字列を超えています。|

### <a name="remarks"></a>Remarks

リストボックス内の項目の並べ替え方法を変更するには、このメソッドをオーバーライドします。

比較では大文字と小文字が区別されます。

このメソッドは、 [AddSortedItem](#addsorteditem)メソッドからのみ呼び出されます。

##  <a name="copyfrom"></a>  CMFCToolBarComboBoxButton::CopyFrom

指定`CMFCToolBarComboBoxButton`したの状態を現在のオブジェクトにコピーします。

```
virtual void CopyFrom(const CMFCToolBarButton& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
からソース`CMFCToolBarComboBoxButton`オブジェクト。

##  <a name="createcombo"></a>CMFCToolBarComboBoxButton:: CreateCombo

コンボボックスボタンの新しいコンボボックスを作成します。

```
virtual CComboBox* CreateCombo(
    CWnd* pWndParent,
    const CRect& rect);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
からボタンの親ウィンドウへのポインター。

*rect*<br/>
からコンボボックスの外接する四角形。

### <a name="return-value"></a>戻り値

メソッドが正常に終了した場合は、新しいコンボボックスへのポインター。それ以外の場合は NULL。

##  <a name="createedit"></a>CMFCToolBarComboBoxButton:: CreateEdit

コンボボックスボタンの新しいエディットボックスを作成します。

```
virtual CMFCToolBarComboBoxEdit* CreateEdit(
    CWnd* pWndParent,
    const CRect& rect,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
からボタンの親ウィンドウへのポインター。

*rect*<br/>
から新しいエディットボックスの外接する四角形。

*dwEditStyle*<br/>
から新しいエディットボックスのコントロールスタイル。

### <a name="return-value"></a>戻り値

メソッドが正常に終了した場合は、新しいエディットボックスへのポインター。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

フレームワークは、コンボボックスボタンの新しいエディットボックスを作成するときに、このメソッドを呼び出します。 [CMFCToolBarComboBoxEdit](../../mfc/reference/cmfctoolbarcomboboxedit-class.md)の作成方法を変更するには、このメソッドをオーバーライドします。

##  <a name="deleteitem"></a>CMFCToolBarComboBoxButton::D eleteItem

指定した項目をリストボックスから削除します。

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);
BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
から削除する項目の0から始まるインデックス。

*dwData*<br/>
から削除する項目に関連付けられているデータ。

*lpszText*<br/>
から削除する項目のテキスト。 同じテキストを持つ複数の項目がある場合、最初の項目は削除されます。

### <a name="return-value"></a>戻り値

項目が見つかり、正常に削除された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="duplicatedata"></a>CMFCToolBarComboBoxButton::D uplicateData

ユーザー定義データを複製します。

```
virtual void DuplicateData();
```

### <a name="remarks"></a>Remarks

既定では、このメソッドは何も行いません。 ユーザー定義データをコピーする場合は、派生クラスでこのメソッドをオーバーライドします。

##  <a name="enablewindow"></a>  CMFCToolBarComboBoxButton::EnableWindow

エディットボックスとコンボボックスを有効または無効にします。

```
virtual void EnableWindow(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
からエディットボックスとコンボボックスを有効にする場合は TRUE。エディットボックスとコンボボックスを無効にする場合は FALSE。

### <a name="remarks"></a>Remarks

無効にした場合、コントロールはアクティブにならず、ユーザー入力を受け付けることができません。

##  <a name="exporttomenubutton"></a>CMFCToolBarComboBoxButton:: ExportToMenuButton

コンボボックスボタンのコマンド ID を使用して、アプリケーション文字列テーブルから指定されたメニューに文字列をコピーします。

```
virtual BOOL ExportToMenuButton(CMFCToolBarMenuButton& menuButton) const;
```

### <a name="parameters"></a>パラメーター

*menuButton*<br/>
入出力メニューボタンへの参照。

### <a name="return-value"></a>戻り値

常に TRUE です。

##  <a name="finditem"></a>CMFCToolBarComboBoxButton:: FindItem

リストボックス内で、指定した文字列が含まれている最初の項目のインデックスを返します。

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
からリストボックス内で検索するテキスト。

### <a name="return-value"></a>戻り値

項目のインデックス。項目が見つからない場合は CB_ERR。

### <a name="remarks"></a>Remarks

##  <a name="getbycmd"></a>CMFCToolBarComboBoxButton:: GetByCmd

指定されたコマンド ID を持つコンボボックスボタンへのポインターを取得します。

```
static CMFCToolBarComboBoxButton* GetByCmd(
    UINT uiCmd,
    BOOL bIsFocus=FALSE);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からコンボボックスボタンのコマンド ID。

*bIsFocus*<br/>
からフォーカスがあるボタンのみを検索する場合は TRUE。すべてのボタンを検索する場合は FALSE。

### <a name="return-value"></a>戻り値

コンボボックスボタンへのポインター。ボタンが見つからない場合は NULL。

### <a name="remarks"></a>Remarks

##  <a name="getcombobox"></a>  CMFCToolBarComboBoxButton::GetComboBox

コンボボックスボタンのコンボボックスへのポインターを返します。

```
CComboBox* GetComboBox() const;
```

### <a name="return-value"></a>戻り値

メソッドが正常に実行された場合は、 [CComboBox クラス](../../mfc/reference/ccombobox-class.md)オブジェクトへのポインター。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

##  <a name="getcontextmenuid"></a>CMFCToolBarComboBoxButton:: GetContextMenuID

コンボボックスボタンのショートカットメニューのリソース ID を取得します。

```
UINT GetContextMenuID();
```

### <a name="return-value"></a>戻り値

ショートカットメニューのリソース ID。

##  <a name="getcount"></a>CMFCToolBarComboBoxButton:: GetCount

リストボックス内の項目の数を返します。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>戻り値

リストボックス内の項目の数。

### <a name="remarks"></a>Remarks

##  <a name="getcountall"></a>CMFCToolBarComboBoxButton:: GetCountAll

指定されたコマンド ID を持つコンボボックスボタンのリストボックス内の項目の数を取得します。

```
static int GetCountAll(UINT uiCmd);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からコンボボックスボタンのコマンド ID。

### <a name="return-value"></a>戻り値

リストボックス内の項目の数。それ以外の場合は、コンボボックスボタンが見つからない場合は CB_ERR。

### <a name="remarks"></a>Remarks

##  <a name="getcursel"></a>CMFCToolBarComboBoxButton:: GetCurSel

リストボックス内で現在選択されている項目のインデックスを取得します。

```
int GetCurSel() const;
```

### <a name="return-value"></a>戻り値

リストボックス内で現在選択されている項目のインデックス。または、項目が選択されていない場合は CB_ERR。

### <a name="remarks"></a>Remarks

リストボックスのインデックスは0から始まります。

##  <a name="getcurselall"></a>CMFCToolBarComboBoxButton:: GetCurSelAll

指定されたコマンド ID を持つコンボボックスボタンのリストボックス内で現在選択されている項目のインデックスを返します。

```
static int GetCurSelAll(UINT uiCmd);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からコンボボックスボタンのコマンド ID。

### <a name="return-value"></a>戻り値

リストボックス内で現在選択されている項目のインデックス。それ以外の場合は、項目が選択されていない場合、またはコンボボックスボタンが見つからない場合は CB_ERR。

### <a name="remarks"></a>Remarks

リストボックスのインデックスは0から始まります。

##  <a name="geteditctrl"></a>CMFCToolBarComboBoxButton::GetEditCtrl

コンボボックスボタンのエディットボックスへのポインターを返します。

```
virtual CEdit* GetEditCtrl();
```

### <a name="return-value"></a>戻り値

メソッドが正常に終了した場合は、エディットボックスへのポインター。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

##  <a name="gethwnd"></a>CMFCToolBarComboBoxButton::GetHwnd

コンボボックスのウィンドウハンドルを返します。

```
virtual HWND GetHwnd();
```

### <a name="return-value"></a>戻り値

ウィンドウハンドル。コンボボックスがウィンドウオブジェクトに関連付けられていない場合は NULL。

##  <a name="getitem"></a>CMFCToolBarComboBoxButton:: GetItem

リストボックス内の指定したインデックス位置にある項目に関連付けられている文字列を返します。

```
LPCTSTR GetItem(int iIndex=-1) const;
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
からリストボックス内の項目の0から始まるインデックス。

### <a name="return-value"></a>戻り値

項目に関連付けられている文字列へのポインター。それ以外の場合は、index パラメーターが無効であるか、またはインデックスパラメーターが-1 で、コンボボックスに選択された項目がない場合は NULL になります。

### <a name="remarks"></a>Remarks

Index パラメーター-1 は、現在選択されている項目の文字列を返します。

##  <a name="getitemall"></a>CMFCToolBarComboBoxButton::GetItemAll

指定されたコマンド ID を持つコンボボックスボタンのリストボックス内の指定したインデックス位置にある項目に関連付けられている文字列を返します。

```
static LPCTSTR GetItemAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からコンボボックスボタンのコマンド ID。

*iIndex*<br/>
からリストボックス内の項目の0から始まるインデックス。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、項目の文字列へのポインター。それ以外の場合、インデックスが無効である場合、コンボボックスボタンが見つからない場合、または index が-1 で、コンボボックスに項目が選択されていない場合は、NULL になります。

### <a name="remarks"></a>Remarks

インデックス値-1 は、現在選択されている項目の文字列を返します。

##  <a name="getitemdata"></a>CMFCToolBarComboBoxButton::GetItemData

リストボックス内の特定のインデックス位置にある項目に関連付けられたデータを返します。

```
DWORD_PTR GetItemData(int iIndex=-1) const;
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
からリストボックス内の項目の0から始まるインデックス。

### <a name="return-value"></a>戻り値

項目に関連付けられているデータ。項目が存在しない場合は0。

### <a name="remarks"></a>Remarks

Index パラメーター-1 は、現在選択されている項目に関連付けられているデータを返します。

##  <a name="getitemdataall"></a>CMFCToolBarComboBoxButton::GetItemDataAll

特定のコマンド ID を持つコンボボックスボタンのリストボックス内の特定のインデックス位置にある項目に関連付けられたデータを返します。

```
static DWORD_PTR GetItemDataAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からコンボボックスボタンのコマンド ID。

*iIndex*<br/>
からリストボックス内の項目の0から始まるインデックス。

### <a name="return-value"></a>戻り値

メソッドが正常に実行された場合は、項目に関連付けられたデータ。それ以外の場合は、指定したインデックスが有効でない場合は0、コンボボックスボタンが見つからない場合は CB_ERR。

### <a name="remarks"></a>Remarks

Index パラメーター-1 は、現在選択されている項目に関連付けられているデータを返します。

##  <a name="getitemdataptrall"></a>CMFCToolBarComboBoxButton::GetItemDataPtrAll

特定のコマンド ID を持つコンボボックスボタンのリストボックス内の特定のインデックス位置にある項目に関連付けられたデータを返します。 このデータは、ポインターとして返されます。

```
static void* GetItemDataPtrAll(
    UINT uiCmd,
    int iIndex=-1);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からコンボボックスボタンのコマンド ID。

*iIndex*<br/>
からリストボックス内の項目の0から始まるインデックス。

### <a name="return-value"></a>戻り値

メソッドが正常に終了した場合は、項目に関連付けられているポインター。それ以外の場合は、エラーが発生した場合は-1、コンボボックスボタンが見つからない場合は NULL。

### <a name="remarks"></a>Remarks

##  <a name="getprompt"></a>CMFCToolBarComboBoxButton:: GetPrompt

コンボボックスボタンのプロンプト文字列を返します。

```
virtual CString GetPrompt() const;
```

### <a name="return-value"></a>戻り値

プロンプト文字列。

### <a name="remarks"></a>Remarks

このメソッドは現在実装されていません。

##  <a name="gettext"></a>CMFCToolBarComboBoxButton:: GetText

エディットボックス内のテキストを取得します。

```
LPCTSTR GetText() const;
```

### <a name="return-value"></a>戻り値

エディットボックス内のテキスト。

### <a name="remarks"></a>Remarks

##  <a name="gettextall"></a>CMFCToolBarComboBoxButton::GetTextAll

指定されたコマンド ID を持つコンボボックスボタンのエディットボックス内のテキストを取得します。

```
static LPCTSTR GetTextAll(UINT uiCmd);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
から特定のコンボボックスボタンのコマンド ID。

### <a name="return-value"></a>戻り値

メソッドが正常に実行された場合は、エディットボックス内のテキスト。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

##  <a name="hasfocus"></a>CMFCToolBarComboBoxButton:: HasFocus

コンボボックスに現在フォーカスがあるかどうかを示します。

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>戻り値

コンボボックスに現在フォーカスがある場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

また、このメソッドは、コンボボックスの子ウィンドウにフォーカスがある場合にも TRUE を返します。

##  <a name="iscentervert"></a>  CMFCToolBarComboBoxButton::IsCenterVert

アプリケーション内のコンボボックスボタンの垂直位置を返します。

```
static BOOL IsCenterVert();
```

### <a name="return-value"></a>戻り値

ボタンが中央揃えの場合は TRUE。ボタンが上部に固定されている場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="isflatmode"></a>CMFCToolBarComboBoxButton::IsFlatMode

アプリケーション内のコンボボックスボタンのフラットスタイルの外観を返します。

```
static BOOL IsFlatMode();
```

### <a name="return-value"></a>戻り値

ボタンにフラットスタイルが設定されている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

コンボボックスのボタンの既定のフラットスタイルは FALSE です。

##  <a name="isownerof"></a>CMFCToolBarComboBoxButton::IsOwnerOf

指定したハンドルがコンボボックスボタンまたはその子要素のいずれかに関連付けられているかどうかを示します。

```
virtual BOOL IsOwnerOf(HWND hwnd);
```

### <a name="parameters"></a>パラメーター

*hwnd*<br/>
からウィンドウハンドル。

### <a name="return-value"></a>戻り値

ハンドルがコンボボックスボタンまたはその子要素のいずれかで assocated されている場合は TRUE。それ以外の場合は FALSE。

##  <a name="isribbonbutton"></a>CMFCToolBarComboBoxButton:: IsRibbonButton

コンボボックスボタンがリボンパネルに存在するかどうかを示します。

```
BOOL IsRibbonButton() const;
```

### <a name="return-value"></a>戻り値

常に FALSE です。

### <a name="remarks"></a>Remarks

既定では、このメソッドは常に FALSE を返します。これは、コンボボックスボタンがリボンパネルに表示されないことを意味します。

##  <a name="iswindowvisible"></a>  CMFCToolBarComboBoxButton::IsWindowVisible

コンボボックスボタンの表示状態を返します。

```
virtual BOOL IsWindowVisible();
```

### <a name="return-value"></a>戻り値

コンボボックスボタンの表示状態。

##  <a name="notifycommand"></a>CMFCToolBarComboBoxButton:: NotifyCommand

コンボボックスボタンがメッセージを処理するかどうかを示します。

```
virtual BOOL NotifyCommand(int iNotifyCode);
```

### <a name="parameters"></a>パラメーター

*iNotifyCode*<br/>
からコマンドに関連付けられている通知メッセージ。

### <a name="return-value"></a>戻り値

コンボボックスボタンがメッセージを処理するかどうかを指定します。

##  <a name="onaddtocustomizepage"></a>CMFCToolBarComboBoxButton:: OnAddToCustomizePage

ボタンが **[カスタマイズ]** ダイアログボックスに追加されたときにフレームワークによって呼び出されます。

```
virtual void OnAddToCustomizePage();
```

##  <a name="oncalculatesize"></a>CMFCToolBarComboBoxButton:: On電卓 Atesize

ボタンのサイズを計算するためにフレームワークによって呼び出されます。

```
virtual SIZE OnCalculateSize(
    CDC* pDC,
    const CSize& sizeDefault,
    BOOL bHorz);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からコンボボックスボタンを表示するデバイスコンテキスト。

*既定値の設定*<br/>
からコンボボックスボタンの既定のサイズ。

*bHorz*<br/>
から親ツールバーのドッキング状態。 ツールバーが水平方向にドッキングされている場合は TRUE、ツールバーが垂直方向にドッキングされている場合は FALSE。

### <a name="return-value"></a>戻り値

コンボボックスボタンの大きさをピクセル単位で格納する構造体。`SIZE`

##  <a name="onchangeparentwnd"></a>CMFCToolBarComboBoxButton::OnChangeParentWnd

コンボボックスボタンが新しいツールバーに挿入されたときにフレームワークによって呼び出されます。

```
virtual void OnChangeParentWnd(CWnd* pWndParent);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
から新しい親ツールバーへのポインター。

##  <a name="onclick"></a>CMFCToolBarComboBoxButton:: OnClick

ユーザーがコンボボックスボタンをクリックしたときにフレームワークによって呼び出されます。

```
virtual BOOL OnClick(
    CWnd* pWnd,
    BOOL bDelay = TRUE);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
からコンボボックスボタンの親ウィンドウへのポインター。

*bDelay*<br/>
から派生クラスで使用するために予約されています。

### <a name="return-value"></a>戻り値

メソッドがイベントを処理する場合は TRUE。それ以外の場合は FALSE。

##  <a name="onctlcolor"></a>CMFCToolBarComboBoxButton::OnCtlColor

ユーザーが親のツールバーの色を変更してコンボボックスのボタンの色を設定したときに、フレームワークによって呼び出されます。

```
virtual HBRUSH OnCtlColor(
    CDC* pDC,
    UINT nCtlColor);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からコンボボックスボタンを表示するデバイスコンテキスト。

*nCtlColor*<br/>
から未使用.

### <a name="return-value"></a>戻り値

フレームワークがコンボボックスボタンの背景を描画するために使用するブラシをハンドルします。

### <a name="remarks"></a>Remarks

このメソッドは、コンボボックスボタンのテキストの色も設定します。

##  <a name="ondraw"></a>CMFCToolBarComboBoxButton:: OnDraw

指定されたスタイルとオプションを使用してコンボボックスボタンを描画するために、フレームワークによって呼び出されます。

```
virtual void OnDraw(
    CDC* pDC,
    const CRect& rect,
    CMFCToolBarImages* pImages,
    BOOL bHorz = TRUE,
    BOOL bCustomizeMode = FALSE,
    BOOL bHighlight = FALSE,
    BOOL bDrawBorder = TRUE,
    BOOL bGrayDisabledButtons = TRUE);
```

### <a name="parameters"></a>パラメーター

*Pdc*<br/>
からボタンを表示するデバイスコンテキスト。

*rect*<br/>
からボタンの外接する四角形。

*pImages*<br/>
からボタンに関連付けられているイメージのコレクション。

*bHorz*<br/>
から親ツールバーのドッキング状態。 ツールバーが水平方向にドッキングされている場合は TRUE、ツールバーが垂直方向にドッキングされている場合は FALSE。

*Bカスタマイズの Emode*<br/>
からアプリケーションがカスタマイズモードであるかどうか。

*bHighlight 表示*<br/>
からコンボボックスボタンを強調表示するかどうかを指定します。

*bDrawBorder*<br/>
から境界線付きでコンボボックスボタンを描画するかどうかを指定します。

*bGrayDisabledButtons*<br/>
から灰色の無効なボタンを描画する場合は TRUE。無効なイメージのコレクションを使用する場合は FALSE。

##  <a name="ondrawoncustomizelist"></a>CMFCToolBarComboBoxButton::OnDrawOnCustomizeList

**[カスタマイズ]** ダイアログボックスの **[コマンド]** ウィンドウにコンボボックスボタンを描画するために、フレームワークによって呼び出されます。

```
virtual int OnDrawOnCustomizeList(
    CDC* pDC,
    const CRect& rect,
    BOOL bSelected);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
からコンボボックスボタンを表示するデバイスコンテキスト。

*rect*<br/>
からコンボボックスボタンの外接する四角形。

*選択された bSelected*<br/>
からコンボボックスボタンが選択されている場合は TRUE。それ以外の場合は FALSE。

### <a name="return-value"></a>戻り値

コンボボックスボタンの幅 (ピクセル単位)。

##  <a name="onglobalfontschanged"></a>CMFCToolBarComboBoxButton:: Onglobalフォントの変更

アプリケーションフォントが変更されたときにコンボボックスボタンのフォントを設定するために、フレームワークによって呼び出されます。

```
virtual void OnGlobalFontsChanged();
```

##  <a name="onmove"></a>CMFCToolBarComboBoxButton::OnMove

親ツールバーが移動したときにコンボボックスボタンの位置を変更するために、フレームワークによって呼び出されます。

```
virtual void OnMove();
```

##  <a name="onshow"></a>CMFCToolBarComboBoxButton:: OnShow

コンボボックスボタンが非表示になっているか表示されているときに、フレームワークによって呼び出されます。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>パラメーター

*bShow*<br/>
からコンボボックスボタンを非表示にするか表示するかを指定します。

##  <a name="onsize"></a>CMFCToolBarComboBoxButton:: OnSize

親ツールバーのサイズが変更されたときに、コンボボックスボタンのサイズを変更するためにフレームワークによって呼び出されます。

```
virtual void OnSize(int iSize);
```

### <a name="parameters"></a>パラメーター

*iSize*<br/>
からコンボボックスボタンの新しい幅。

##  <a name="onupdatetooltip"></a>CMFCToolBarComboBoxButton:: OnUpdateToolTip

ユーザーがコンボボックスボタンのツールヒントを変更したときにフレームワークによって呼び出されます。

```
virtual BOOL OnUpdateToolTip(
    CWnd* pWndParent,
    int iButtonIndex,
    CToolTipCtrl& wndToolTip,
    CString& str);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
からコンボボックスボタンの親ウィンドウへのポインター。

*iButtonIndex*<br/>
からコンボボックスボタンの ID。

*wndToolTip*<br/>
からコンボボックスボタンに関連付けるツールヒント。

*str*<br/>
からツールヒントのテキスト。

### <a name="return-value"></a>戻り値

メソッドがイベントを処理する場合は TRUE。それ以外の場合は FALSE。

##  <a name="removeallitems"></a>  CMFCToolBarComboBoxButton::RemoveAllItems

リストボックスと編集ボックスからすべての項目を削除します。

```
void RemoveAllItems();
```

### <a name="remarks"></a>Remarks

リストボックスからすべての項目を削除し、コンボボックスのコントロールを編集します。

##  <a name="selectitem"></a>CMFCToolBarComboBoxButton:: SelectItem

リストボックス内の項目を選択します。

```
BOOL SelectItem(
    int iIndex,
    BOOL bNotify=TRUE);

BOOL SelectItem(DWORD_PTR dwData);
BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
からリストボックス内の項目の0から始まるインデックス。

*bNotify*<br/>
から選択範囲のコンボボックスボタンに通知する場合は TRUE。それ以外の場合は FALSE。

*dwData*<br/>
からリストボックス内の項目に関連付けられているデータ。

*lpszText*<br/>
からリストボックス内の項目のテキスト。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="selectitemall"></a>CMFCToolBarComboBoxButton::SelectItemAll

指定されたコマンド ID を持つコンボボックスボタンのリストボックス内の項目を選択します。

```
static BOOL SelectItemAll(
    UINT uiCmd,
    int iIndex);

static BOOL SelectItemAll(
    UINT uiCmd,
    DWORD_PTR dwData);

static BOOL SelectItemAll(
    UINT uiCmd,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
からリストボックスを含むコンボボックスボタンのコマンド ID。

*iIndex*<br/>
からリストボックス内の項目の0から始まるインデックス。 値を-1 に設定すると、リストボックス内の現在の選択範囲が削除され、エディットボックスがクリアされます。

*dwData*<br/>
からリストボックス内の項目のデータ。

*lpszText*<br/>
からリストボックス内の項目のテキスト。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="serialize"></a>CMFCToolBarComboBoxButton:: Serialize

アーカイブからこのオブジェクトを読み取るか、アーカイブに書き込みます。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>パラメーター

*金*<br/>
[入力、出力]シリアル化するオブジェクト。 `CArchive`

### <a name="remarks"></a>Remarks

`CArchive`オブジェクトの設定によって、このメソッドがアーカイブの読み取りまたは書き込みを行うかどうかが決まります。

##  <a name="setaccdata"></a>CMFCToolBarComboBoxButton:: Setのデータ

コンボボックスボタン`CAccessibilityData`のユーザー補助データを使用して、指定されたオブジェクトを設定します。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>パラメーター

*pParent*<br/>
からコンボボックスボタンの親ウィンドウ。

*data*<br/>
入出力コンボボックスボタンからユーザー補助データを受け取るオブジェクト。`CAccessibilityData`

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

##  <a name="setcentervert"></a>CMFCToolBarComboBoxButton:: Set中央の垂直

アプリケーション内のコンボボックスボタンの垂直位置を設定します。

```
static void SetCenterVert(BOOL bCenterVert=TRUE);
```

### <a name="parameters"></a>パラメーター

*B中央の垂直*<br/>
からツールバーのコンボボックスボタンを中央に配置する場合は TRUE。コンボボックスボタンをツールバーの上部に揃えて配置する場合は FALSE。

### <a name="remarks"></a>Remarks

既定では、コンボボックスのボタンは上部に並べられています。

##  <a name="setcontextmenuid"></a>CMFCToolBarComboBoxButton:: SetContextMenuID

コンボボックスボタンのショートカットメニューのリソース ID を設定します。

```
void SetContextMenuID(UINT uiResID);
```

### <a name="parameters"></a>パラメーター

*uiResID*<br/>
[in]ショートカット メニューのリソース id。

##  <a name="setdropdownheight"></a>CMFCToolBarComboBoxButton:: SetDropDownHeight

リストボックスがドロップダウンされたときの高さを設定します。

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>パラメーター

*nHeight*<br/>
からリストボックスの高さ (ピクセル単位)。

### <a name="remarks"></a>Remarks

既定の高さは150ピクセルです。

##  <a name="setflatmode"></a>CMFCToolBarComboBoxButton::SetFlatMode

アプリケーションのコンボボックスボタンのフラットスタイルの外観を設定します。

```
static void SetFlatMode(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>パラメーター

*bFlat*<br/>
からフラットスタイルの外観の場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

コンボボックスのボタンの既定のフラットスタイルは FALSE です。

##  <a name="setstyle"></a>CMFCToolBarComboBoxButton:: System.windows.forms.control.setstyle

コンボボックスボタンに指定されたスタイルを設定し、無効になっていない場合はコントロールを再描画します。

```
virtual void SetStyle(UINT nStyle);
```

### <a name="parameters"></a>パラメーター

*nStyle*<br/>
からツールバースタイルのビットごとの組み合わせ (または)。

### <a name="remarks"></a>Remarks

ツールバーボタンのスタイルの一覧については、「 [Toolbar コントロールスタイル](../../mfc/reference/toolbar-control-styles.md)」を参照してください。

##  <a name="settext"></a>CMFCToolBarComboBoxButton:: SetText

コンボボックスボタンのエディットボックスのテキストを設定します。

```
void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
からエディットボックスのテキストを含む文字列へのポインター。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarButton クラス](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CComboBox クラス](../../mfc/reference/ccombobox-class.md)<br/>
[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[チュートリアル: ツール バーへのコントロールの追加](../../mfc/walkthrough-putting-controls-on-toolbars.md)
