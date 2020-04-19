---
title: CMFCShellListCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::DisplayParentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::EnableShellContextMenu
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentFolderName
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentItemIdList
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetCurrentShellFolder
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemPath
- AFXSHELLLISTCTRL/CMFCShellListCtrl::GetItemTypes
- AFXSHELLLISTCTRL/CMFCShellListCtrl::IsDesktop
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnCompareItems
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileDate
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnFormatFileSize
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemIcon
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnGetItemText
- AFXSHELLLISTCTRL/CMFCShellListCtrl::OnSetColumns
- AFXSHELLLISTCTRL/CMFCShellListCtrl::Refresh
- AFXSHELLLISTCTRL/CMFCShellListCtrl::SetItemTypes
helpviewer_keywords:
- CMFCShellListCtrl [MFC], DisplayFolder
- CMFCShellListCtrl [MFC], DisplayParentFolder
- CMFCShellListCtrl [MFC], EnableShellContextMenu
- CMFCShellListCtrl [MFC], GetCurrentFolder
- CMFCShellListCtrl [MFC], GetCurrentFolderName
- CMFCShellListCtrl [MFC], GetCurrentItemIdList
- CMFCShellListCtrl [MFC], GetCurrentShellFolder
- CMFCShellListCtrl [MFC], GetItemPath
- CMFCShellListCtrl [MFC], GetItemTypes
- CMFCShellListCtrl [MFC], IsDesktop
- CMFCShellListCtrl [MFC], OnCompareItems
- CMFCShellListCtrl [MFC], OnFormatFileDate
- CMFCShellListCtrl [MFC], OnFormatFileSize
- CMFCShellListCtrl [MFC], OnGetItemIcon
- CMFCShellListCtrl [MFC], OnGetItemText
- CMFCShellListCtrl [MFC], OnSetColumns
- CMFCShellListCtrl [MFC], Refresh
- CMFCShellListCtrl [MFC], SetItemTypes
ms.assetid: ad472958-5586-4c50-aadf-1844c30bf6e7
ms.openlocfilehash: 02d4883c6b5445515d891c5e76ccf10b6bb35bba
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504922"
---
# <a name="cmfcshelllistctrl-class"></a>CMFCShellListCtrl クラス

クラス`CMFCShellListCtrl`は、Windows リストコントロールの機能を提供し、シェル項目の一覧を表示する機能を追加することによって拡張します。

## <a name="syntax"></a>構文

```
class CMFCShellListCtrl : public CMFCListCtrl
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCShellListCtrl::D isplayFolder](#displayfolder)|指定されたフォルダーに格納されている項目の一覧を表示します。|
|[CMFCShellListCtrl::DisplayParentFolder](#displayparentfolder)|現在表示されているフォルダーの親であるフォルダーに格納されている項目の一覧を表示します。|
|[CMFCShellListCtrl::EnableShellContextMenu](#enableshellcontextmenu)|ショートカットメニューを有効または無効にします。|
|[CMFCShellListCtrl:: GetCurrentFolder](#getcurrentfolder)|現在のフォルダーのパスを取得します。|
|[CMFCShellListCtrl:: GetCurrentFolderName](#getcurrentfoldername)|現在のフォルダーの名前を取得します。|
|[CMFCShellListCtrl:: Getの一覧](#getcurrentitemidlist)|現在のリストコントロール項目の PIDL を返します。|
|[CMFCShellListCtrl:: GetCurrentShellFolder](#getcurrentshellfolder)|現在のシェルフォルダーへのポインターを返します。|
|[CMFCShellListCtrl:: GetItemPath](#getitempath)|項目のテキストパスを返します。|
|[CMFCShellListCtrl:: GetItemTypes](#getitemtypes)|リストコントロールによって表示されるシェル項目の種類を返します。|
|[CMFCShellListCtrl:: IsDesktop](#isdesktop)|現在選択されているフォルダーがデスクトップフォルダーであるかどうかを確認します。|
|[CMFCShellListCtrl::OnCompareItems](#oncompareitems)|フレームワークは、2つの項目を比較するときにこのメソッドを呼び出します。 ( [CMFCListCtrl:: OnCompareItems](../../mfc/reference/cmfclistctrl-class.md#oncompareitems)をオーバーライドします)。|
|[CMFCShellListCtrl::OnFormatFileDate](#onformatfiledate)|リストコントロールによって表示されるファイルの日付をフレームワークが取得するときに呼び出されます。|
|[CMFCShellListCtrl::OnFormatFileSize](#onformatfilesize)|フレームワークがリストコントロールのファイルサイズを変換するときに呼び出されます。|
|[CMFCShellListCtrl::OnGetItemIcon](#ongetitemicon)|フレームワークがリストコントロール項目のアイコンを取得するときに呼び出されます。|
|[CMFCShellListCtrl::OnGetItemText](#ongetitemtext)|フレームワークがリストコントロール項目のテキストを変換するときに呼び出されます。|
|[CMFCShellListCtrl::OnSetColumns](#onsetcolumns)|列の名前を設定するときに、フレームワークによって呼び出されます。|
|[CMFCShellListCtrl::Refresh](#refresh)|リストコントロールを更新し、再描画します。|
|[CMFCShellListCtrl:: SetItemTypes](#setitemtypes)|リストコントロールによって表示される項目の種類を設定します。|

## <a name="remarks"></a>Remarks

クラス`CMFCShellListCtrl`は、プログラムで Windows シェル項目を一覧表示できるようにすることで、 [CMFCListCtrl クラス](../../mfc/reference/cmfclistctrl-class.md)の機能を拡張します。 使用される表示形式は、エクスプローラーウィンドウのリストビューの形式に似ています。

[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)オブジェクトは、エクスプローラーウィンドウ全体を`CMFCShellListCtrl`作成するために、オブジェクトに関連付けることができます。 次に、で`CMFCShellTreeCtrl`項目を選択すると、選択した項目の内容が一覧表示され`CMFCShellListCtrl`ます。

## <a name="example"></a>例

次の例は、 `CMFCShellListCtrl`クラスのオブジェクトを作成する方法と、現在表示されているフォルダーの親フォルダーを表示する方法を示しています。 このコードスニペットは、エクスプローラーの[サンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_Explorer#1](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#2](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_2.cpp)]
[!code-cpp[NVC_MFC_Explorer#3](../../mfc/reference/codesnippet/cpp/cmfcshelllistctrl-class_3.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

`CMFCShellListCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxshelllistCtrl

##  <a name="displayfolder"></a>  CMFCShellListCtrl::DisplayFolder

指定されたフォルダーに格納されている項目の一覧を表示します。

```
virtual HRESULT DisplayFolder(LPCTSTR lpszPath);
virtual HRESULT DisplayFolder(LPAFX_SHELLITEMINFO lpItemInfo);
```

### <a name="parameters"></a>パラメーター

*lpszPath*<br/>
からフォルダーのパスを含む文字列。

*lpItemInfo*<br/>
から表示するフォルダーを`LPAFX_SHELLITEMINFO`記述する構造体へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK。それ以外の場合は E_FAIL です。

##  <a name="displayparentfolder"></a>  CMFCShellListCtrl::DisplayParentFolder

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトを更新して、現在表示されているフォルダーの親フォルダーを表示します。

```
virtual HRESULT DisplayParentFolder();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK。それ以外の場合は E_FAIL です。

##  <a name="enableshellcontextmenu"></a>  CMFCShellListCtrl::EnableShellContextMenu

ショートカットメニューを有効にします。

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
からフレームワークでショートカットメニューを有効にするかどうかを指定するブール値。

##  <a name="getcurrentfolder"></a>  CMFCShellListCtrl::GetCurrentFolder

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトで現在選択されているフォルダーのパスを取得します。

```
BOOL GetCurrentFolder(CString& strPath) const;
```

### <a name="parameters"></a>パラメーター

*strPath*<br/>
入出力メソッドがパスを書き込む文字列パラメーターへの参照。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。それ以外の場合は0。

### <a name="remarks"></a>Remarks

でフォルダーが選択されていない場合、 `CMFCShellListCtrl`このメソッドは失敗します。

##  <a name="getcurrentfoldername"></a>  CMFCShellListCtrl::GetCurrentFolderName

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトで現在選択されているフォルダーの名前を取得します。

```
BOOL GetCurrentFolderName(CString& strName) const;
```

### <a name="parameters"></a>パラメーター

*strName*<br/>
入出力メソッドが名前を書き込む文字列パラメーターへの参照。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。それ以外の場合は0。

### <a name="remarks"></a>Remarks

でフォルダーが選択されていない場合、 `CMFCShellListCtrl`このメソッドは失敗します。

##  <a name="getcurrentitemidlist"></a>  CMFCShellListCtrl::GetCurrentItemIdList

現在選択されている項目の PIDL を返します。

```
LPITEMIDLIST GetCurrentItemIdList() const;
```

### <a name="return-value"></a>戻り値

現在の項目の PIDL。

##  <a name="getcurrentshellfolder"></a>CMFCShellListCtrl:: GetCurrentShellFolder

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトで現在選択されている項目へのポインターを取得します。

```
const IShellFolder* GetCurrentShellFolder() const;
```

### <a name="return-value"></a>戻り値

選択されたオブジェクトの[Ishellfolder インターフェイス](/windows/win32/api/shobjidl_core/nn-shobjidl_core-ishellfolder)へのポインター。

### <a name="remarks"></a>Remarks

オブジェクトが現在選択されていない場合、このメソッドは NULL を返します。

##  <a name="getitempath"></a>CMFCShellListCtrl:: GetItemPath

項目のパスを取得します。

```
BOOL GetItemPath(
    CString& strPath,
    int iItem) const;
```

### <a name="parameters"></a>パラメーター

*strPath*<br/>
入出力パスを受け取る文字列への参照。

*iItem*<br/>
からリスト項目のインデックス。

### <a name="return-value"></a>戻り値

成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

*IItem*によって指定されたインデックスは、 [Cmfcshelllistctrl クラス](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトによって現在表示されている項目に基づいています。

##  <a name="getitemtypes"></a>CMFCShellListCtrl:: GetItemTypes

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトによって表示される項目の型を返します。

```
SHCONTF GetItemTypes() const;
```

### <a name="return-value"></a>戻り値

に`CMFCShellListCtrl`一覧表示されている項目の型を格納している[shf](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf)値。

### <a name="remarks"></a>Remarks

に`CMFCShellListCtrl`一覧表示されている項目の種類を設定するには、 [cmfcshelllistctrl:: SetItemTypes](#setitemtypes)を呼び出します。

##  <a name="isdesktop"></a>CMFCShellListCtrl:: IsDesktop

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトに表示されるフォルダーがデスクトップフォルダーであるかどうかを決定します。

```
BOOL IsDesktop() const;
```

### <a name="return-value"></a>戻り値

表示されているフォルダーがデスクトップフォルダーである場合は TRUE。それ以外の場合は FALSE。

##  <a name="oncompareitems"></a>  CMFCShellListCtrl::OnCompareItems

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>パラメーター

から*lParam1*<br/>
[in] *lParam2*<br/>
から*iColumn*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="onformatfiledate"></a>  CMFCShellListCtrl::OnFormatFileDate

フレームワークは、オブジェクトに関連付けられた日付を文字列に変換する必要がある場合に、このメソッドを呼び出します。

```
virtual void OnFormatFileDate(
    const CTime& tmFile,
    CString& str);
```

### <a name="parameters"></a>パラメーター

*tmFile*<br/>
からファイルに関連付けられた日付。

*str*<br/>
入出力書式設定されたファイルの日付を含む文字列。

### <a name="remarks"></a>Remarks

[Cmfcshelllistctrl Class](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトがファイルに関連付けられた日付を表示する場合、その日付を文字列形式に変換する必要があります。 は`CMFCShellListCtrl` 、このメソッドを使用して変換を行います。 既定では、このメソッドは現在のロケールを使用して、日付を文字列に書式設定します。

##  <a name="onformatfilesize"></a>  CMFCShellListCtrl::OnFormatFileSize

フレームワークは、オブジェクトのサイズを文字列に変換するときに、このメソッドを呼び出します。

```
virtual void OnFormatFileSize(
    long lFileSize,
    CString& str);
```

### <a name="parameters"></a>パラメーター

*lFileSize サイズ*<br/>
からフレームワークによって表示されるファイルのサイズ。

*str*<br/>
入出力書式設定されたファイルサイズを格納している文字列。

### <a name="remarks"></a>Remarks

[Cmfcshelllistctrl クラス](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトがファイルのサイズを表示する必要がある場合、ファイルサイズを文字列形式に変換する必要があります。 は`CMFCShellListCtrl` 、このメソッドを使用して変換を行います。 既定では、このメソッドはファイルサイズをバイトからキロバイトに変換し、現在のロケールを使用して、サイズを文字列に書式設定します。

##  <a name="ongetitemicon"></a>  CMFCShellListCtrl::OnGetItemIcon

フレームワークは、このメソッドを呼び出して、シェルリスト項目に関連付けられているアイコンを取得します。

```
virtual int OnGetItemIcon(
    int iItem,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>パラメーター

*iItem*<br/>
から項目のインデックス。

*pItem*<br/>
から項目を説明する LPAFX_SHELLITEMINFO パラメーター。

### <a name="return-value"></a>戻り値

成功した場合はアイコンイメージのインデックス。関数が失敗した場合は-1。

### <a name="remarks"></a>Remarks

アイコンイメージのインデックスは、システムイメージの一覧に基づいています。

既定では、このメソッドは*pItem*パラメーターに依存します。 *IItem*の値は、既定の実装では使用されません。 *IItem*を使用して、カスタム動作を実装できます。

##  <a name="ongetitemtext"></a>  CMFCShellListCtrl::OnGetItemText

フレームワークは、シェル項目のテキストを取得する必要がある場合に、このメソッドを呼び出します。

```
virtual CString OnGetItemText(
    int iItem,
    int iColumn,
    LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>パラメーター

*iItem*<br/>
から項目のインデックス。

*iColumn*<br/>
から対象の列。

*pItem*<br/>
から項目を説明する LPAFX_SHELLITEMINFO パラメーター。

### <a name="return-value"></a>戻り値

項目に関連付けられているテキストを格納している。`CString`

### <a name="remarks"></a>Remarks

オブジェクトの各項目`CMFCShellListCtrl`には、1つまたは複数の列にテキストを含めることができます。 フレームワークがこのメソッドを呼び出すと、目的の列が指定されます。 この関数を手動で呼び出す場合は、関心のある列も指定する必要があります。

既定では、このメソッドは、処理する項目を決定するために*pItem*パラメーターに依存します。 *IItem*の値は、既定の実装では使用されません。

##  <a name="onsetcolumns"></a>  CMFCShellListCtrl::OnSetColumns

フレームワークは、列の名前を設定するときにこのメソッドを呼び出します。

```
virtual void OnSetColumns();
```

### <a name="remarks"></a>Remarks

既定では、フレームワークによって`CMFCShellListCtrl`オブジェクトに4つの列が作成されます。 これらの列の名前は、**名前**、**サイズ**、**種類**、および**変更**されます。 このメソッドをオーバーライドして、列の数と列の名前をカスタマイズできます。

##  <a name="refresh"></a>  CMFCShellListCtrl::Refresh

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトを更新し、再描画します。

```
virtual HRESULT Refresh();
```

### <a name="return-value"></a>戻り値

`S_OK`成功した場合は。それ以外の場合は、エラー値。

### <a name="remarks"></a>Remarks

`CMFCShellListCtrl`オブジェクトによって表示される項目の一覧を更新するには、このメソッドを呼び出します。

##  <a name="setitemtypes"></a>CMFCShellListCtrl:: SetItemTypes

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトに一覧表示される項目の種類を設定します。

```
void SetItemTypes(SHCONTF nTypes);
```

### <a name="parameters"></a>パラメーター

*nTypes*<br/>
からオブジェクトが`CMFCShellListCtrl`サポートする項目の種類の一覧。

### <a name="remarks"></a>Remarks

項目の種類の一覧の詳細については、「 [Shsee f](/windows/win32/api/shobjidl_core/ne-shobjidl_core-_shcontf)」を参照してください。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl クラス](../../mfc/reference/cmfclistctrl-class.md)<br/>
[CMFCShellTreeCtrl クラス](../../mfc/reference/cmfcshelltreectrl-class.md)
