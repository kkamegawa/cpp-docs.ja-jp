---
title: CMFCShellTreeCtrl クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::EnableShellContextMenu
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetItemPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::GetRelatedList
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnChildNotify
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemIcon
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::OnGetItemText
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::Refresh
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SelectPath
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetFlags
- AFXSHELLTREECTRL/CMFCShellTreeCtrl::SetRelatedList
helpviewer_keywords:
- CMFCShellTreeCtrl [MFC], EnableShellContextMenu
- CMFCShellTreeCtrl [MFC], GetFlags
- CMFCShellTreeCtrl [MFC], GetItemPath
- CMFCShellTreeCtrl [MFC], GetRelatedList
- CMFCShellTreeCtrl [MFC], OnChildNotify
- CMFCShellTreeCtrl [MFC], OnGetItemIcon
- CMFCShellTreeCtrl [MFC], OnGetItemText
- CMFCShellTreeCtrl [MFC], Refresh
- CMFCShellTreeCtrl [MFC], SelectPath
- CMFCShellTreeCtrl [MFC], SetFlags
- CMFCShellTreeCtrl [MFC], SetRelatedList
ms.assetid: 3d1da715-9554-4ed7-968c-055c48146267
ms.openlocfilehash: 97136342049a54d45af893962025f01eda4366d4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504907"
---
# <a name="cmfcshelltreectrl-class"></a>CMFCShellTreeCtrl クラス

クラス`CMFCShellTreeCtrl`は、シェル項目の階層を表示することによって、 [CTreeCtrl クラス](../../mfc/reference/ctreectrl-class.md)の機能を拡張します。

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。
## <a name="syntax"></a>構文

```
class CMFCShellTreeCtrl : public CTreeCtrl
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCShellTreeCtrl::EnableShellContextMenu](#enableshellcontextmenu)|ショートカットメニューを有効または無効にします。|
|[CMFCShellTreeCtrl:: GetFlags](#getflags)|[Ishellfolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)に渡されるフラグの組み合わせを返します。|
|[CMFCShellTreeCtrl:: GetItemPath](#getitempath)|項目へのパスを取得します。|
|[CMFCShellTreeCtrl:: Get List](#getrelatedlist)|この`CMFCShellTreeCtrl`オブジェクトと共に使用して、エクスプローラーのようなウィンドウを作成するために使用される[cmfcshelllistctrl クラス](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトへのポインターを返します。|
|[CMFCShellTreeCtrl::OnChildNotify](#onchildnotify)|このメンバー関数は、このウィンドウに適用される通知メッセージを受信すると、このウィンドウの親ウィンドウによって呼び出されます。 ( [CWnd:: OnChildNotify](../../mfc/reference/cwnd-class.md#onchildnotify)をオーバーライドします)。|
|[CMFCShellTreeCtrl:: OnGetItemIcon](#ongetitemicon)||
|[CMFCShellTreeCtrl::OnGetItemText](#ongetitemtext)||
|[CMFCShellTreeCtrl::Refresh](#refresh)|現在`CMFCShellTreeCtrl`のオブジェクトを更新し、再描画します。|
|[CMFCShellTreeCtrl:: SelectPath](#selectpath)|指定された PIDL または文字列パスに基づいて、適切なツリーコントロール項目を選択します。|
|[CMFCShellTreeCtrl:: SetFlags](#setflags)|ツリーコンテキストをフィルター処理するためのフラグを設定します ( `IShellFolder::EnumObjects`で使用されるフラグに似ています)。|
|[CMFCShellTreeCtrl:: Set List](#setrelatedlist)|現在`CMFCShellTreeCtrl`のオブジェクト`CMFCShellListCtrl`とオブジェクトの間のリレーションシップを設定します。|

## <a name="remarks"></a>Remarks

このクラスは、 `CTreeCtrl`プログラムがツリーに Windows シェル項目を含めることができるようにすることでクラスを拡張します。 このクラスは、すべてのエクスプローラー `CMFCShellListCtrl`ウィンドウを作成するために、オブジェクトに関連付けることができます。 次に、ツリー内の項目を選択すると、関連付けられている一覧に Windows シェル項目の一覧が表示されます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CTreeCtrl](../../mfc/reference/ctreectrl-class.md)

`CMFCShellTreeCtrl`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxshelltreeCtrl

## <a name="example"></a>例

次の例では、`CMFCShellTreeCtrl` クラスのオブジェクトを作成する方法を示します。 このコードスニペットは、エクスプローラーの[サンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_Explorer#4](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_1.h)]
[!code-cpp[NVC_MFC_Explorer#5](../../mfc/reference/codesnippet/cpp/cmfcshelltreectrl-class_2.cpp)]

##  <a name="enableshellcontextmenu"></a>  CMFCShellTreeCtrl::EnableShellContextMenu

ショートカットメニューを有効にします。

```
void EnableShellContextMenu(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
からショートカットメニューを有効にするかどうかを指定するブール値。

##  <a name="getflags"></a>CMFCShellTreeCtrl:: GetFlags

[CMFCShellTreeCtrl クラス](../../mfc/reference/cmfcshelltreectrl-class.md)オブジェクトに設定されたフラグを返します。

```
DWORD GetFlags() const;
```

### <a name="return-value"></a>戻り値

現在設定されているフラグの組み合わせを指定する DWORD 値。

### <a name="remarks"></a>Remarks

で`CMFCShellTreeCtrl`設定されたフラグは、オブジェクトが更新されるたびに[ishellfolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)メソッドに送信されます。 フラグは、 [CMFCShellTreeCtrl:: SetFlags](#setflags)メソッドを使用して変更できます。

##  <a name="getitempath"></a>  CMFCShellTreeCtrl::GetItemPath

[CMFCShellTreeCtrl Class](../../mfc/reference/cmfcshelltreectrl-class.md)オブジェクト内の項目のパスを取得します。

```
BOOL GetItemPath(
    CString& strPath,
    HTREEITEM htreeItem = NULL) const;
```

### <a name="parameters"></a>パラメーター

*strPath*<br/>
入出力文字列パラメーターへの参照。 メソッドは、このパラメーターに項目のパスを書き込みます。

*htreeItem*<br/>
からメソッドは、このツリーコントロール項目のパスを取得します。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。それ以外の場合は0。

### <a name="remarks"></a>Remarks

このメソッドが失敗した場合、 *strPath*には空の文字列が含まれます。

*HTreeItem*を指定しない場合、このメソッドは現在選択されている項目の文字列を取得しようとします。 項目が選択されておらず、 *hTreeItem*が NULL の場合、このメソッドは失敗します。

##  <a name="getrelatedlist"></a>CMFCShellTreeCtrl:: Get List

この[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)オブジェクトに関連付けられている[Cmfcshelllistctrl クラス](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトへのポインターを返します。

```
CMFCShellListCtrl* GetRelatedList() const;
```

### <a name="return-value"></a>戻り値

このツリーコントロールオブジェクト`CMFCShellListCtrl`に関連付けられているオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

オブジェクトを`CMFCShellTreeCtrl`オブジェクト`CMFCShellListCtrl`と共に使用すると、エクスプローラーのようなウィンドウを作成できます。 2つのクラスを関連付けるには、 [CMFCShellTreeCtrl:: Set関連付けリスト](#setrelatedlist)メソッドを使用します。 これらが関連付けられると、の選択範囲`CMFCShellListCtrl` `CMFCShellTreeCtrl`が変更されると、フレームワークによってが自動的に更新されます。

##  <a name="onchildnotify"></a>  CMFCShellTreeCtrl::OnChildNotify

```
virtual BOOL OnChildNotify(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* pLResult);
```

### <a name="parameters"></a>パラメーター

から*メッセージ*<br/>
から*wParam*<br/>
から*lParam*<br/>
から*Plresult*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="ongetitemicon"></a>  CMFCShellTreeCtrl::OnGetItemIcon

```
virtual int OnGetItemIcon(
    LPAFX_SHELLITEMINFO pItem,
    BOOL bSelected);
```

### <a name="parameters"></a>パラメーター

から*pItem*<br/>
から*選択された bselected*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="ongetitemtext"></a>  CMFCShellTreeCtrl::OnGetItemText

```
virtual CString OnGetItemText(LPAFX_SHELLITEMINFO pItem);
```

### <a name="parameters"></a>パラメーター

から*pItem*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="refresh"></a>  CMFCShellTreeCtrl::Refresh

[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)を更新し、再描画します。

```
void Refresh();
```

### <a name="remarks"></a>Remarks

に表示される`CMFCShellTreeCtrl`項目の階層を更新するには、このメソッドを呼び出します。

##  <a name="selectpath"></a>  CMFCShellTreeCtrl::SelectPath

指定されたパスに基づいて、 [CMFCShellTreeCtrl クラス](../../mfc/reference/cmfcshelltreectrl-class.md)の項目を選択します。

```
BOOL SelectPath(LPCTSTR lpszPath);
BOOL SelectPath(LPCITEMIDLIST lpidl);
```

### <a name="parameters"></a>パラメーター

*lpszPath*<br/>
から項目のパスを指定する文字列。

*lpidl*<br/>
から項目を指定する PIDL

### <a name="return-value"></a>戻り値

成功した場合は S_OK。それ以外の場合は E_FAIL です。

##  <a name="setflags"></a>CMFCShellTreeCtrl:: SetFlags

ツリーコンテキストをフィルター処理するためのフラグを設定します。

```
void SetFlags(
    DWORD dwFlags,
    BOOL bRefresh = TRUE);
```

### <a name="parameters"></a>パラメーター

*dwFlags*<br/>
から設定するフラグ。

*bRefresh*<br/>
からを`CMFCShellTreeCtrl`すぐに更新するかどうかを指定するブール値。

### <a name="remarks"></a>Remarks

は`CMFCShellTreeCtrl` 、すべての set フラグを[ishellfolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)に渡します。 異なるフラグの値の詳細については、「 [Ishellfolder:: EnumObjects](/windows/win32/api/shobjidl_core/nf-shobjidl_core-ishellfolder-enumobjects)」を参照してください。

##  <a name="setrelatedlist"></a>CMFCShellTreeCtrl:: Set List

[Cmfcshelllistctrl](../../mfc/reference/cmfcshelllistctrl-class.md)オブジェクトを[CMFCShellTreeCtrl](../../mfc/reference/cmfcshelltreectrl-class.md)オブジェクトに関連付けます。

```
void SetRelatedList(CMFCShellListCtrl* pShellList);
```

### <a name="parameters"></a>パラメーター

*pShellList*<br/>
から`CMFCShellListCtrl`オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、 `CMFCShellListCtrl` `CMFCShellTreeCtrl`をに関連付けます。 これらのオブジェクトは、エクスプローラーのようなウィンドウとして表示される場合があります`CMFCShellTreeCtrl`。ユーザーがでオブジェクトを`CMFCShellListCtrl`選択すると、内の関連する項目が自動的に更新されます。

メソッド[CMFCShellTreeCtrl:: get関連付けリスト](#getrelatedlist)を使用して、 `CMFCShellListCtrl`に`CMFCShellTreeCtrl`関連付けられているを取得します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CTreeCtrl クラス](../../mfc/reference/ctreectrl-class.md)<br/>
[CMFCShellListCtrl クラス](../../mfc/reference/cmfcshelllistctrl-class.md)
