---
title: COlePropertyPage クラス
ms.date: 11/04/2016
f1_keywords:
- COlePropertyPage
- AFXCTL/COlePropertyPage
- AFXCTL/COlePropertyPage::COlePropertyPage
- AFXCTL/COlePropertyPage::GetControlStatus
- AFXCTL/COlePropertyPage::GetObjectArray
- AFXCTL/COlePropertyPage::GetPageSite
- AFXCTL/COlePropertyPage::OVERWRITEApply
- AFXCTL/COlePropertyPage::IsModified
- AFXCTL/COlePropertyPage::OnEditProperty
- AFXCTL/COlePropertyPage::OnHelp
- AFXCTL/COlePropertyPage::OnInitDialog
- AFXCTL/COlePropertyPage::OnObjectsChanged
- AFXCTL/COlePropertyPage::OnSetPageSite
- AFXCTL/COlePropertyPage::SetControlStatus
- AFXCTL/COlePropertyPage::SetDialogResource
- AFXCTL/COlePropertyPage::SetHelpInfo
- AFXCTL/COlePropertyPage::SetModifiedFlag
- AFXCTL/COlePropertyPage::SetPageName
helpviewer_keywords:
- COlePropertyPage [MFC], COlePropertyPage
- COlePropertyPage [MFC], GetControlStatus
- COlePropertyPage [MFC], GetObjectArray
- COlePropertyPage [MFC], GetPageSite
- COlePropertyPage [MFC], IgnoreApply
- COlePropertyPage [MFC], IsModified
- COlePropertyPage [MFC], OnEditProperty
- COlePropertyPage [MFC], OnHelp
- COlePropertyPage [MFC], OnInitDialog
- COlePropertyPage [MFC], OnObjectsChanged
- COlePropertyPage [MFC], OnSetPageSite
- COlePropertyPage [MFC], SetControlStatus
- COlePropertyPage [MFC], SetDialogResource
- COlePropertyPage [MFC], SetHelpInfo
- COlePropertyPage [MFC], SetModifiedFlag
- COlePropertyPage [MFC], SetPageName
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
ms.openlocfilehash: 8253b2c2fa6b93ec51c7ede983ef710eed039970
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224450"
---
# <a name="colepropertypage-class"></a>COlePropertyPage クラス

ダイアログ ボックスのようなグラフィカルなインターフェイスでカスタム コントロールのプロパティを表示します。

## <a name="syntax"></a>構文

```
class AFX_NOVTABLE COlePropertyPage : public CDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COlePropertyPage::COlePropertyPage](#colepropertypage)|`COlePropertyPage` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|ユーザーがコントロールの値を変更したかどうかを示します。|
|[COlePropertyPage::GetObjectArray](#getobjectarray)|プロパティ ページで編集対象のオブジェクトの配列を返します。|
|[COlePropertyPage::GetPageSite](#getpagesite)|プロパティ ページのポインターを返します`IPropertyPageSite`インターフェイス。|
|[COlePropertyPage::IgnoreApply](#ignoreapply)|どのコントロールに適用 ボタンが有効にしないことを決定します。|
|[COlePropertyPage::IsModified](#ismodified)|ユーザーがプロパティ ページを変更したかどうかを示します。|
|[COlePropertyPage::OnEditProperty](#oneditproperty)|ユーザーがプロパティを編集するときに、フレームワークによって呼び出されます。|
|[COlePropertyPage::OnHelp](#onhelp)|ユーザーがヘルプを呼び出したときに、フレームワークによって呼び出されます。|
|[COlePropertyPage::OnInitDialog](#oninitdialog)|プロパティ ページが初期化されるときに、フレームワークによって呼び出されます。|
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|新しいプロパティを持つ別の OLE コントロールがクリックされたときに、フレームワークによって呼び出されます。|
|[COlePropertyPage::OnSetPageSite](#onsetpagesite)|プロパティ フレームがページのサイトを提供するときに、フレームワークによって呼び出されます。|
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|ユーザーがコントロールの値を変更したかどうかを示すフラグを設定します。|
|[COlePropertyPage::SetDialogResource](#setdialogresource)|プロパティ ページのダイアログ リソースを設定します。|
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|プロパティ ページの簡単なヘルプ テキスト、そのヘルプ ファイルとそのヘルプ コンテキストの名前を設定します。|
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|ユーザーがプロパティ ページを変更したかどうかを示すフラグを設定します。|
|[COlePropertyPage::SetPageName](#setpagename)|プロパティ ページの名前 (キャプション) を設定します。|

## <a name="remarks"></a>Remarks

たとえば、プロパティ ページが表示およびコントロールのキャプションのプロパティを変更するユーザーをエディット コントロールを含めることができます。

各コントロールをカスタムまたはストック プロパティ ダイアログ コントロール、コントロールのユーザーが現在のプロパティ値を表示し、必要な場合は、その値を変更できるようにすることができます。

使用しての詳細については`COlePropertyPage`、記事をご覧ください[ActiveX コントロール。プロパティ ページ](../../mfc/mfc-activex-controls-property-pages.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

`COlePropertyPage`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxctl.h

##  <a name="colepropertypage"></a>  COlePropertyPage::COlePropertyPage

`COlePropertyPage` オブジェクトを構築します。

```
COlePropertyPage(
    UINT idDlg,
    UINT idCaption);
```

### <a name="parameters"></a>パラメーター

*idDlg*<br/>
ダイアログ テンプレートのリソース ID。

*idCaption*<br/>
プロパティ ページのキャプションのリソース ID。

### <a name="remarks"></a>Remarks

サブクラスを実装する場合`COlePropertyPage`、サブクラスのコンス トラクターを使用する必要があります、`COlePropertyPage`にダイアログ テンプレート リソースを識別するためにコンス トラクターとそのキャプションを格納している文字列リソースのプロパティ ページに基づいています。

##  <a name="getcontrolstatus"></a>  COlePropertyPage::GetControlStatus

ユーザーが指定されたリソース ID を持つプロパティ ページのコントロールの値を変更したかどうかを決定します。

```
BOOL GetControlStatus(UINT nID);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
プロパティ ページのコントロールのリソース ID。

### <a name="return-value"></a>戻り値

コントロールの値が変更された場合は TRUE。それ以外の場合は FALSE です。

##  <a name="getobjectarray"></a>  COlePropertyPage::GetObjectArray

プロパティ ページで編集対象のオブジェクトの配列を返します。

```
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```

### <a name="parameters"></a>パラメーター

*pnObjects*<br/>
ページが編集対象のオブジェクトの数を受信する、符号なし long 整数を指すポインター。

### <a name="return-value"></a>戻り値

配列を指すポインター`IDispatch`ポインターで、[プロパティ] ページには、各コントロールのプロパティにアクセスするために使用します。 呼び出し元は、これらのインターフェイス ポインターを解放する必要があります。

### <a name="remarks"></a>Remarks

各プロパティ ページのオブジェクトへのポインターの配列を保持する、`IDispatch`のページで編集されているオブジェクトのインターフェイス。 この関数は、設定、 *pnObjects*その配列内の要素の数の引数と配列の最初の要素へのポインターを返します。

##  <a name="getpagesite"></a>  COlePropertyPage::GetPageSite

プロパティのページにポインターを取得します。`IPropertyPageSite`インターフェイス。

```
LPPROPERTYPAGESITE GetPageSite();
```

### <a name="return-value"></a>戻り値

プロパティ ページへのポインター`IPropertyPageSite`インターフェイス。

### <a name="remarks"></a>Remarks

コントロールとコンテナーは、ユーザーが参照してコントロールのプロパティを編集できるように連携します。 コントロールは、それぞれが、関連する一連のプロパティを編集するユーザーをできるようにする OLE オブジェクトのプロパティ ページを提供します。 コンテナーは、プロパティ ページを表示するプロパティのフレームを提供します。 プロパティ フレームがサポートしているページのサイトを提供する、各ページで、`IPropertyPageSite`インターフェイス。

##  <a name="ignoreapply"></a>  COlePropertyPage::IgnoreApply

どのコントロールに適用 ボタンが有効にしないことを決定します。

```
void IgnoreApply(UINT nID);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
コントロールの ID と、無視されます。

### <a name="remarks"></a>Remarks

ページ コントロールのプロパティの値が変更された場合にのみ、プロパティ ページの [適用] ボタンが有効にします。 この関数を使用すると、その値を変更するときに有効にするのに [適用] ボタンが発生しないコントロールを指定できます。

##  <a name="ismodified"></a>  COlePropertyPage::IsModified

ユーザーのプロパティ ページの任意の値が変更されたかどうかを判断します。

```
BOOL IsModified();
```

### <a name="return-value"></a>戻り値

プロパティ ページが変更された場合は TRUE。

##  <a name="oneditproperty"></a>  COlePropertyPage::OnEditProperty

フレームワークは、特定のプロパティは、編集するときに、この関数を呼び出します。

```
virtual BOOL OnEditProperty(DISPID dispid);
```

### <a name="parameters"></a>パラメーター

*dispid*<br/>
編集されるプロパティのディスパッチ ID。

### <a name="return-value"></a>戻り値

既定の実装では、FALSE を返します。 この関数のオーバーライドでは、TRUE を返す必要があります。

### <a name="remarks"></a>Remarks

ページの適切なコントロールにフォーカスを設定する上書きすることができます。 既定の実装では、何も実行し、FALSE を返します。

##  <a name="onhelp"></a>  COlePropertyPage::OnHelp

フレームワークは、ユーザーは、オンライン ヘルプを要求すると、この関数を呼び出します。

```
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```

### <a name="parameters"></a>パラメーター

*lpszHelpDir*<br/>
プロパティ ページのヘルプ ファイルを含むディレクトリ。

### <a name="return-value"></a>戻り値

既定の実装では、FALSE を返します。

### <a name="remarks"></a>Remarks

ユーザーがヘルプにアクセスするときに、プロパティ ページが特別な操作を実行する必要がある場合は、これをオーバーライドします。 既定の実装では、何も実行し、WinHelp を呼び出すために、フレームワークに指示する、FALSE を返します。

##  <a name="oninitdialog"></a>  COlePropertyPage::OnInitDialog

フレームワークは、プロパティ ページのダイアログの初期化時に、この関数を呼び出します。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>戻り値

既定の実装では、FALSE を返します。

### <a name="remarks"></a>Remarks

ダイアログの初期化時に、特別な操作が必要な場合は、これをオーバーライドします。 既定の実装`CDialog::OnInitDialog`FALSE を返します。

##  <a name="onobjectschanged"></a>  COlePropertyPage::OnObjectsChanged

新しいプロパティを持つ別の OLE コントロールがクリックされたときに、フレームワークによって呼び出されます。

```
virtual void OnObjectsChanged();
```

### <a name="remarks"></a>Remarks

開発者の環境における OLE コントロールのプロパティを表示するときに、モードレス ダイアログ ボックスは、そのプロパティ ページを表示に使用されます。 別のコントロールが選択されている場合、新しい一連のプロパティの別の一連のプロパティ ページを表示する必要があります。 フレームワークは、変更のプロパティ ページに通知するには、この関数を呼び出します。

この操作の通知を受け取るし、特別な操作を実行するには、この関数をオーバーライドします。

##  <a name="onsetpagesite"></a>  COlePropertyPage::OnSetPageSite

フレームワークは、プロパティのフレームは、プロパティ ページのページのサイトを提供するときに、この関数を呼び出します。

```
virtual void OnSetPageSite();
```

### <a name="remarks"></a>Remarks

既定の実装では、ページのキャプションを読み込み、ダイアログ リソースから、ページのサイズを決定しようとします。 プロパティ ページには、その後の操作が必要な場合は、この関数をオーバーライドします。オーバーライドは基本クラスの実装を呼び出す必要があります。

##  <a name="setcontrolstatus"></a>  COlePropertyPage::SetControlStatus

プロパティ ページのコントロールの状態を変更します。

```
BOOL SetControlStatus(
    UINT nID,
    BOOL bDirty);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
プロパティ ページのコントロールの ID が含まれています。

*bDirty*<br/>
プロパティ ページのフィールドが変更されたかどうかを指定します。 フィールドが変更された場合、FALSE に変更されていない場合は TRUE に設定します。

### <a name="return-value"></a>戻り値

指定したコントロールが設定された場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

プロパティ ページが閉じているか、[適用] ボタンを選択したときにプロパティ ページのコントロールの状態がダーティな場合は、コントロールのプロパティを適切な値に更新されます。

##  <a name="setdialogresource"></a>  COlePropertyPage::SetDialogResource

プロパティ ページのダイアログ リソースを設定します。

```
void SetDialogResource(HGLOBAL hDialog);
```

### <a name="parameters"></a>パラメーター

*hDialog*<br/>
プロパティ ページのダイアログ リソースへのハンドルします。

##  <a name="sethelpinfo"></a>  COlePropertyPage::SetHelpInfo

ツールヒント情報やヘルプ ファイル名、プロパティ ページのヘルプ コンテキストを指定します。

```
void SetHelpInfo(
    LPCTSTR lpszDocString,
    LPCTSTR lpszHelpFile = NULL,
    DWORD dwHelpContext = 0);
```

### <a name="parameters"></a>パラメーター

*lpszDocString*<br/>
ステータス バーまたは他の場所に表示するための簡単なヘルプ情報を含む文字列。

*lpszHelpFile*<br/>
プロパティ ページのヘルプ ファイルの名前です。

*dwHelpContext*<br/>
プロパティ ページのヘルプ コンテキスト。

##  <a name="setmodifiedflag"></a>  COlePropertyPage::SetModifiedFlag

ユーザーがプロパティ ページを変更したかどうかを示します。

```
void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>パラメーター

*bModified*<br/>
プロパティ ページの変更されたフラグの新しい値を指定します。

##  <a name="setpagename"></a>  COlePropertyPage::SetPageName

プロパティ フレームがページのタブに表示される通常プロパティ ページの名前を設定します。

```
void SetPageName(LPCTSTR lpszPageName);
```

### <a name="parameters"></a>パラメーター

*lpszPageName*<br/>
プロパティ ページの名前を含む文字列へのポインター。

## <a name="see-also"></a>関連項目

[MFC のサンプル CIRC3](../../overview/visual-cpp-samples.md)<br/>
[MFC サンプル TESTHELP](../../overview/visual-cpp-samples.md)<br/>
[CDialog クラス](../../mfc/reference/cdialog-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDialog クラス](../../mfc/reference/cdialog-class.md)
