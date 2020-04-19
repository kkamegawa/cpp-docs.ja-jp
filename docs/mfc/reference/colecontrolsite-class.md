---
title: COleControlSite クラス
ms.date: 11/04/2016
f1_keywords:
- COleControlSite
- AFXOCC/COleControlSite
- AFXOCC/COleControlSite::COleControlSite
- AFXOCC/COleControlSite::BindDefaultProperty
- AFXOCC/COleControlSite::BindProperty
- AFXOCC/COleControlSite::CreateControl
- AFXOCC/COleControlSite::DestroyControl
- AFXOCC/COleControlSite::DoVerb
- AFXOCC/COleControlSite::EnableDSC
- AFXOCC/COleControlSite::EnableWindow
- AFXOCC/COleControlSite::FreezeEvents
- AFXOCC/COleControlSite::GetDefBtnCode
- AFXOCC/COleControlSite::GetDlgCtrlID
- AFXOCC/COleControlSite::GetEventIID
- AFXOCC/COleControlSite::GetExStyle
- AFXOCC/COleControlSite::GetProperty
- AFXOCC/COleControlSite::GetStyle
- AFXOCC/COleControlSite::GetWindowText
- AFXOCC/COleControlSite::InvokeHelper
- AFXOCC/COleControlSite::InvokeHelperV
- AFXOCC/COleControlSite::IsDefaultButton
- AFXOCC/COleControlSite::IsWindowEnabled
- AFXOCC/COleControlSite::ModifyStyle
- AFXOCC/COleControlSite::ModifyStyleEx
- AFXOCC/COleControlSite::MoveWindow
- AFXOCC/COleControlSite::QuickActivate
- AFXOCC/COleControlSite::SafeSetProperty
- AFXOCC/COleControlSite::SetDefaultButton
- AFXOCC/COleControlSite::SetDlgCtrlID
- AFXOCC/COleControlSite::SetFocus
- AFXOCC/COleControlSite::SetProperty
- AFXOCC/COleControlSite::SetPropertyV
- AFXOCC/COleControlSite::SetWindowPos
- AFXOCC/COleControlSite::SetWindowText
- AFXOCC/COleControlSite::ShowWindow
- AFXOCC/COleControlSite::GetControlInfo
- AFXOCC/COleControlSite::m_bIsWindowless
- AFXOCC/COleControlSite::m_ctlInfo
- AFXOCC/COleControlSite::m_dwEventSink
- AFXOCC/COleControlSite::m_dwMiscStatus
- AFXOCC/COleControlSite::m_dwPropNotifySink
- AFXOCC/COleControlSite::m_dwStyle
- AFXOCC/COleControlSite::m_hWnd
- AFXOCC/COleControlSite::m_iidEvents
- AFXOCC/COleControlSite::m_nID
- AFXOCC/COleControlSite::m_pActiveObject
- AFXOCC/COleControlSite::m_pCtrlCont
- AFXOCC/COleControlSite::m_pInPlaceObject
- AFXOCC/COleControlSite::m_pObject
- AFXOCC/COleControlSite::m_pWindowlessObject
- AFXOCC/COleControlSite::m_pWndCtrl
- AFXOCC/COleControlSite::m_rect
helpviewer_keywords:
- COleControlSite [MFC], COleControlSite
- COleControlSite [MFC], BindDefaultProperty
- COleControlSite [MFC], BindProperty
- COleControlSite [MFC], CreateControl
- COleControlSite [MFC], DestroyControl
- COleControlSite [MFC], DoVerb
- COleControlSite [MFC], EnableDSC
- COleControlSite [MFC], EnableWindow
- COleControlSite [MFC], FreezeEvents
- COleControlSite [MFC], GetDefBtnCode
- COleControlSite [MFC], GetDlgCtrlID
- COleControlSite [MFC], GetEventIID
- COleControlSite [MFC], GetExStyle
- COleControlSite [MFC], GetProperty
- COleControlSite [MFC], GetStyle
- COleControlSite [MFC], GetWindowText
- COleControlSite [MFC], InvokeHelper
- COleControlSite [MFC], InvokeHelperV
- COleControlSite [MFC], IsDefaultButton
- COleControlSite [MFC], IsWindowEnabled
- COleControlSite [MFC], ModifyStyle
- COleControlSite [MFC], ModifyStyleEx
- COleControlSite [MFC], MoveWindow
- COleControlSite [MFC], QuickActivate
- COleControlSite [MFC], SafeSetProperty
- COleControlSite [MFC], SetDefaultButton
- COleControlSite [MFC], SetDlgCtrlID
- COleControlSite [MFC], SetFocus
- COleControlSite [MFC], SetProperty
- COleControlSite [MFC], SetPropertyV
- COleControlSite [MFC], SetWindowPos
- COleControlSite [MFC], SetWindowText
- COleControlSite [MFC], ShowWindow
- COleControlSite [MFC], GetControlInfo
- COleControlSite [MFC], m_bIsWindowless
- COleControlSite [MFC], m_ctlInfo
- COleControlSite [MFC], m_dwEventSink
- COleControlSite [MFC], m_dwMiscStatus
- COleControlSite [MFC], m_dwPropNotifySink
- COleControlSite [MFC], m_dwStyle
- COleControlSite [MFC], m_hWnd
- COleControlSite [MFC], m_iidEvents
- COleControlSite [MFC], m_nID
- COleControlSite [MFC], m_pActiveObject
- COleControlSite [MFC], m_pCtrlCont
- COleControlSite [MFC], m_pInPlaceObject
- COleControlSite [MFC], m_pObject
- COleControlSite [MFC], m_pWindowlessObject
- COleControlSite [MFC], m_pWndCtrl
- COleControlSite [MFC], m_rect
ms.assetid: 43970644-5eab-434a-8ba6-56d144ff1e3f
ms.openlocfilehash: 9b9b68a001acdf4b08d9cfc01cc67c43217d9a57
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504316"
---
# <a name="colecontrolsite-class"></a>COleControlSite クラス

クライアント側のカスタム コントロール インターフェイスをサポートします。

## <a name="syntax"></a>構文

```
class COleControlSite : public CCmdTarget
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleControlSite::COleControlSite](#colecontrolsite)|`COleControlSite` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleControlSite:: BindDefaultProperty](#binddefaultproperty)|ホストされるコントロールの既定のプロパティをデータソースにバインドします。|
|[COleControlSite:: BindProperty](#bindproperty)|ホストされるコントロールのプロパティをデータソースにバインドします。|
|[COleControlSite::CreateControl](#createcontrol)|ホストされている ActiveX コントロールを作成します。|
|[COleControlSite::DestroyControl](#destroycontrol)|ホストされているコントロールを破棄します。|
|[COleControlSite::DoVerb](#doverb)|ホストされているコントロールの特定の動詞を実行します。|
|[COleControlSite::EnableDSC](#enabledsc)|コントロールサイトのデータソースを有効にします。|
|[COleControlSite::EnableWindow](#enablewindow)|コントロールサイトを有効にします。|
|[COleControlSite::FreezeEvents](#freezeevents)|コントロールサイトがイベントを受け入れるかどうかを指定します。|
|[COleControlSite::GetDefBtnCode](#getdefbtncode)|ホストされるコントロールの既定のボタンコードを取得します。|
|[COleControlSite::GetDlgCtrlID](#getdlgctrlid)|コントロールの識別子を取得します。|
|[COleControlSite::GetEventIID](#geteventiid)|ホストされるコントロールのイベントインターフェイスの ID を取得します。|
|[COleControlSite::GetExStyle](#getexstyle)|コントロールサイトの拡張スタイルを取得します。|
|[COleControlSite::GetProperty](#getproperty)|ホストされているコントロールの特定のプロパティを取得します。|
|[COleControlSite::GetStyle](#getstyle)|コントロールサイトのスタイルを取得します。|
|[COleControlSite::GetWindowText](#getwindowtext)|ホストされているコントロールのテキストを取得します。|
|[COleControlSite::InvokeHelper](#invokehelper)|ホストされているコントロールの特定のメソッドを呼び出します。|
|[COleControlSite::InvokeHelperV](#invokehelperv)|引数の変数リストを使用して、ホストされるコントロールの特定のメソッドを呼び出します。|
|[COleControlSite::IsDefaultButton](#isdefaultbutton)|コントロールがウィンドウの既定のボタンかどうかを判断します。|
|[COleControlSite::IsWindowEnabled](#iswindowenabled)|コントロールサイトの表示状態を確認します。|
|[COleControlSite::ModifyStyle](#modifystyle)|コントロールサイトの現在の拡張スタイルを変更します。|
|[COleControlSite::ModifyStyleEx](#modifystyleex)|コントロールサイトの現在のスタイルを変更します。|
|[COleControlSite::MoveWindow](#movewindow)|コントロールサイトの位置を変更します。|
|[COleControlSite::QuickActivate](#quickactivate)|ホストされているコントロールをクイックアクティブ化します。|
|[COleControlSite::SafeSetProperty](#safesetproperty)|例外をスローすることなく、コントロールのプロパティまたはメソッドを設定します。|
|[COleControlSite::SetDefaultButton](#setdefaultbutton)|ウィンドウの既定のボタンを設定します。|
|[COleControlSite::SetDlgCtrlID](#setdlgctrlid)|コントロールの識別子を取得します。|
|[COleControlSite::SetFocus](#setfocus)|コントロールサイトにフォーカスを設定します。|
|[COleControlSite::SetProperty](#setproperty)|ホストされるコントロールの特定のプロパティを設定します。|
|[COleControlSite::SetPropertyV](#setpropertyv)|引数の変数リストを使用して、ホストされるコントロールの特定のプロパティを設定します。|
|[COleControlSite::SetWindowPos](#setwindowpos)|コントロールサイトの位置を設定します。|
|[COleControlSite::SetWindowText](#setwindowtext)|ホストされるコントロールのテキストを設定します。|
|[COleControlSite::ShowWindow](#showwindow)|コントロールサイトの表示と非表示を切り替えます。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[COleControlSite::GetControlInfo](#getcontrolinfo)|ホストされるコントロールのキーボード情報とニーモニックを取得します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COleControlSite::m_bIsWindowless](#m_biswindowless)|ホストされるコントロールがウィンドウなしのコントロールであるかどうかを判断します。|
|[COleControlSite::m_ctlInfo](#m_ctlinfo)|コントロールのキーボード処理に関する情報を格納します。|
|[COleControlSite::m_dwEventSink](#m_dweventsink)|コントロールのコネクションポイントのクッキー。|
|[COleControlSite::m_dwMiscStatus](#m_dwmiscstatus)|ホストされるコントロールのその他の状態。|
|[COleControlSite::m_dwPropNotifySink](#m_dwpropnotifysink)|コントロール`IPropertyNotifySink`のクッキー。|
|[COleControlSite::m_dwStyle](#m_dwstyle)|ホストされているコントロールのスタイル。|
|[COleControlSite::m_hWnd](#m_hwnd)|コントロールサイトのハンドル。|
|[COleControlSite::m_iidEvents](#m_iidevents)|ホストされるコントロールのイベントインターフェイスの ID。|
|[COleControlSite::m_nID](#m_nid)|ホストされるコントロールの ID。|
|[COleControlSite::m_pActiveObject](#m_pactiveobject)|ホストされるコントロール`IOleInPlaceActiveObject`のオブジェクトへのポインター。|
|[COleControlSite::m_pCtrlCont](#m_pctrlcont)|ホストされているコントロールのコンテナー。|
|[COleControlSite::m_pInPlaceObject](#m_pinplaceobject)|ホストされるコントロール`IOleInPlaceObject`のオブジェクトへのポインター。|
|[COleControlSite::m_pObject](#m_pobject)|コントロールの`IOleObjectInterface`インターフェイスへのポインター。|
|[COleControlSite::m_pWindowlessObject](#m_pwindowlessobject)|コントロールの`IOleInPlaceObjectWindowless`インターフェイスへのポインター。|
|[COleControlSite::m_pWndCtrl](#m_pwndctrl)|ホストされるコントロールのウィンドウオブジェクトへのポインター。|
|[COleControlSite::m_rect](#m_rect)|コントロールサイトの大きさ。|

## <a name="remarks"></a>Remarks

このサポートは、埋め込み ActiveX コントロールが、表示サイトの場所と範囲、モニカー、そのユーザーインターフェイス、アンビエントプロパティ、およびコンテナーによって提供されるその他のリソースに関する情報を取得する主な手段です。 `COleControlSite`は、 [IOleControlSite](/windows/win32/api/ocidl/nn-ocidl-iolecontrolsite)、 [IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)、 [IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite)、 [IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) `IBoundObjectSite`、、 `INotifyDBEvents`、 [IRowSetNotify](../../data/oledb/irowsetnotifyimpl-class.md)の各インターフェイスを完全に実装します。 また、IDispatch インターフェイス (アンビエントプロパティとイベントシンクのサポートを提供する) も実装されています。

を使用して`COleControlSite`ActiveX コントロールサイトを作成するには、から`COleControlSite`クラスを派生させます。 コンテナーの派生クラス (たとえば、ダイアログボックス) では、関数が`CWnd::CreateControlSite`オーバーライドされます。 `CWnd`

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlSite`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxocc

##  <a name="binddefaultproperty"></a>COleControlSite:: BindDefaultProperty

タイプライブラリに示されているように、呼び出し元オブジェクトの既定の単純バインドプロパティを、データソースコントロールの DataSource、UserName、Password、および SQL の各プロパティによって定義される基になるカーソルにバインドします。

```
virtual void BindDefaultProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    LPCTSTR szFieldName,
    CWnd* pDSCWnd);
```

### <a name="parameters"></a>パラメーター

*dwDispID*<br/>
データソースコントロールにバインドされるデータバインドコントロールのプロパティの DISPID を指定します。

*vtProp*<br/>
バインドするプロパティの型 (たとえば、VT_BSTR、VT_VARIANT など) を指定します。

*szFieldName*<br/>
プロパティがバインドされるデータソースコントロールによって提供されるカーソル内の列の名前を指定します。

*pDSCWnd*<br/>
プロパティがバインドさ`CWnd`れるデータソースコントロールをホストする、派生オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

この関数を呼び出すオブジェクトは、データバインドコントロールである必要があります。`CWnd`

##  <a name="bindproperty"></a>COleControlSite:: BindProperty

タイプライブラリでマークされている呼び出し元オブジェクトの単純バインドプロパティを、データソースコントロールの DataSource、UserName、Password、および SQL の各プロパティによって定義される基になるカーソルにバインドします。

```
virtual void BindProperty(
    DISPID dwDispId,
    CWnd* pWndDSC);
```

### <a name="parameters"></a>パラメーター

*dwDispId*<br/>
データソースコントロールにバインドされるデータバインドコントロールのプロパティの DISPID を指定します。

*pWndDSC*<br/>
プロパティがバインドさ`CWnd`れるデータソースコントロールをホストする、派生オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

この関数を呼び出すオブジェクトは、データバインドコントロールである必要があります。`CWnd`

##  <a name="colecontrolsite"></a>COleControlSite::COleControlSite

新しい `COleControlSite` オブジェクトを構築します。

```
explicit COleControlSite(COleControlContainer* pCtrlCont);
```

### <a name="parameters"></a>パラメーター

*pCtrlCont*<br/>
コントロールのコンテナー (AtiveX コントロールをホストするウィンドウを表す) へのポインター。

### <a name="remarks"></a>Remarks

この関数は、 [COccManager:: CreateContainer](../../mfc/reference/coccmanager-class.md#createcontainer)関数によって呼び出されます。 コンテナーの作成をカスタマイズする方法の詳細については、「 [COccManager:: CreateSite](../../mfc/reference/coccmanager-class.md#createsite)」を参照してください。

##  <a name="createcontrol"></a>  COleControlSite::CreateControl

オブジェクトによってホストされる`COleControlSite` ActiveX コントロールを作成します。

```
virtual HRESULT CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist = NULL,
    BOOL bStorage = FALSE,
    BSTR bstrLicKey = NULL);

virtual HRESULT CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist = NULL,
    BOOL bStorage = FALSE,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>パラメーター

*pWndCtrl*<br/>
コントロールを表すウィンドウオブジェクトへのポインター。

*clsid*<br/>
コントロールの一意のクラス ID。

*lpszWindowName*<br/>
コントロールに表示されるテキストへのポインター。 Winodw のキャプションまたはテキストプロパティ (存在する場合) の値を設定します。

*dwStyle*<br/>
Windows スタイル。 使用可能なスタイルは、「**解説**」の下に一覧表示されます。

*rect*<br/>
コントロールのサイズと位置を指定します。 `CRect` オブジェクト`RECT`または構造体のいずれかを指定できます。

*nID*<br/>
コントロールの子ウィンドウ ID を指定します。

*pPersist*<br/>
コントロールの永続的な`CFile`状態を格納しているへのポインター。 既定値は NULL です。これは、コントロールが永続的なストレージから状態を復元せずに自身を初期化することを示します。 NULL でない場合は、ストリームまたはストレージの`CFile`形式で、コントロールの永続データを含むから派生したオブジェクトへのポインターである必要があります。 このデータは、クライアントの以前のアクティブ化で保存されている可能性があります。 `CFile` に`CreateControl`は他のデータを含めることができますが、の呼び出し時には、読み取り/書き込みポインターを永続データの最初のバイトに設定する必要があります。

*bStorage*<br/>
*Ppersist*内のデータをまたは`IStorage` `IStream`データとして解釈するかどうかを示します。 *Ppersist*のデータがストレージの場合、 *BSTORAGE*は TRUE である必要があります。 *Ppersist*のデータがストリームの場合、 *BSTORAGE*は FALSE である必要があります。 既定値は FALSE です。

*Bstrのキー*<br/>
オプションのライセンスキーデータ。 このデータは、実行時ライセンスキーを必要とするコントロールを作成する場合にのみ必要です。 コントロールがライセンスをサポートしている場合は、コントロールの作成を成功させるためのライセンスキーを指定する必要があります。 既定値は NULL です。

*ppt*<br/>
コントロールの左上隅`POINT`を格納している構造体へのポインター。 コントロールのサイズは、 *psize*の値によって決まります。 *Ppt*と*psize*の値は、コントロールのサイズと位置を指定するオプションのメソッドです。

*psize*<br/>
コントロールのサイズを`SIZE`格納している構造体へのポインター。 左上隅は、 *ppt*の値によって決まります。 *Ppt*と*psize*の値は、コントロールのサイズと位置を指定するオプションのメソッドです。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

では、Windows *dwStyle*フラグのサブセットのみが`CreateControl`サポートされています。

- WS_VISIBLE 最初に表示されるウィンドウを作成します。 通常のウィンドウのように、コントロールをすぐに表示する場合に必要です。

- WS_DISABLED は、最初は無効になっているウィンドウを作成します。 無効なウィンドウは、ユーザーから入力を受け取ることができません。 コントロールに Enabled プロパティがある場合は、を設定できます。

- WS_BORDER 細い境界線を持つウィンドウを作成します。 コントロールに BorderStyle プロパティがある場合は、を設定できます。

- WS_GROUP は、コントロールのグループの最初のコントロールを指定します。 ユーザーは、方向キーを使用して、グループ内の1つのコントロールから次のコントロールにキーボードフォーカスを変更できます。 最初のコントロールの後に WS_GROUP スタイルを使用して定義されたすべてのコントロールが、同じグループに属しています。 WS_GROUP スタイルの次のコントロールは、グループを終了し、次のグループを開始します。

- WS_TABSTOP ユーザーが TAB キーを押したときにキーボードフォーカスを受け取ることができるコントロールを指定します。 TAB キーを押すと、キーボードフォーカスが WS_TABSTOP スタイルの次のコントロールに変わります。

2番目のオーバーロードを使用して、既定のサイズのコントロールを作成します。

##  <a name="destroycontrol"></a>  COleControlSite::DestroyControl

`COleControlSite` オブジェクトを破棄します。

```
virtual BOOL DestroyControl();
```

### <a name="return-value"></a>戻り値

成功した場合は0以外の。それ以外の場合は0。

### <a name="remarks"></a>Remarks

完了すると、オブジェクトがメモリから解放され、オブジェクトへのポインターが無効になります。

##  <a name="doverb"></a>  COleControlSite::DoVerb

指定された動詞を実行します。

```
virtual HRESULT DoVerb(
    LONG nVerb,
    LPMSG lpMsg = NULL);
```

### <a name="parameters"></a>パラメーター

*nVerb*<br/>
実行する動詞を指定します。 次のいずれかを含めることができます。

|[値]|説明|シンボル|
|-----------|-------------|------------|
|0|主動詞|OLEIVERB_PRIMARY|
|-1|2番目の動詞|(なし)|
|1|編集するオブジェクトを表示します。|OLEIVERB_SHOW|
|-2|項目を別のウィンドウで編集します。|OLEIVERB_OPEN|
|-3|オブジェクトを非表示にします。|OLEIVERB_HIDE|
|-4|コントロールを埋め込み先としてアクティブにします。|OLEIVERB_UIACTIVATE|
|-5|追加のユーザーインターフェイス要素を使用せずに、コントロールを埋め込み先でアクティブにします。|OLEIVERB_INPLACEACTIVATE|
|-7|コントロールのプロパティを表示します。|OLEIVERB_PROPERTIES|

*lpMsg*<br/>
項目がアクティブ化される原因となったメッセージへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

この関数は、コントロールの`IOleObject`インターフェイスを直接呼び出して、指定された動詞を実行します。 この関数呼び出しの結果として例外がスローされた場合は、HRESULT エラーコードが返されます。

詳細については、Windows SDK の「 [IOleObject::D oVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 」を参照してください。

##  <a name="enabledsc"></a>  COleControlSite::EnableDSC

コントロールサイトのデータソースを有効にします。

```
virtual void EnableDSC();
```

### <a name="remarks"></a>Remarks

コントロールサイトのデータソースを有効にし、初期化するために、フレームワークによって呼び出されます。 この関数をオーバーライドして、カスタマイズされた動作を提供します。

##  <a name="enablewindow"></a>  COleControlSite::EnableWindow

コントロールサイトへのマウスおよびキーボード入力を有効または無効にします。

```
virtual BOOL EnableWindow(BOOL bEnable);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
ウィンドウを有効にするか無効にするかを指定します。ウィンドウ入力が有効になっている場合は TRUE、それ以外の場合は FALSE。

### <a name="return-value"></a>戻り値

ウィンドウが既に無効になっている場合は0以外。それ以外の場合は0。

##  <a name="freezeevents"></a>  COleControlSite::FreezeEvents

コントロールサイトが、コントロールから発生したイベントを処理するか無視するかを指定します。

```
void FreezeEvents(BOOL bFreeze);
```

### <a name="parameters"></a>パラメーター

*bFreeze*<br/>
コントロール サイトにおけるイベントの受け取りを中止するかどうかを指定します。 コントロールがイベントを受け入れていない場合は0以外の。それ以外の場合は0。

### <a name="remarks"></a>Remarks

*Bfreeze*が TRUE の場合、コントロールサイトはコントロールに対してイベントの停止を要求します。 *Bfreeze*が FALSE の場合、コントロールサイトはコントロールに対して、イベントの発生を継続するように要求します。

> [!NOTE]
>  コントロールは、コントロールサイトによって要求された場合に、イベントの発生を停止する必要はありません。 実行を継続できますが、それ以降のすべてのイベントはコントロールサイトによって無視されます。

##  <a name="getcontrolinfo"></a>  COleControlSite::GetControlInfo

コントロールのキーボードニーモニックとキーボード動作に関する情報を取得します。

```
void GetControlInfo();
```

### <a name="remarks"></a>Remarks

情報は[COleControlSite:: m_ctlInfo](#m_ctlinfo)に格納されます。

##  <a name="getdefbtncode"></a>  COleControlSite::GetDefBtnCode

コントロールが既定のプッシュボタンであるかどうかを判断します。

```
DWORD GetDefBtnCode();
```

### <a name="return-value"></a>戻り値

次のいずれかの値になります。

- DLGC_DEFPUSHBUTTON コントロールは、ダイアログの既定のボタンです。

- DLGC_UNDEFPUSHBUTTON コントロールは、ダイアログの既定のボタンではありません。

- **0**コントロールはボタンではありません。

##  <a name="getdlgctrlid"></a>  COleControlSite::GetDlgCtrlID

コントロールの識別子を取得します。

```
virtual int GetDlgCtrlID() const;
```

### <a name="return-value"></a>戻り値

コントロールのダイアログ項目識別子。

##  <a name="geteventiid"></a>  COleControlSite::GetEventIID

コントロールの既定のイベントインターフェイスへのポインターを取得します。

```
BOOL GetEventIID(IID* piid);
```

### <a name="parameters"></a>パラメーター

*piid*<br/>
インターフェイス ID へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。それ以外の場合は0。 成功した場合、 *piid*には、コントロールの既定のイベントインターフェイスのインターフェイス ID が格納されます。

##  <a name="getexstyle"></a>  COleControlSite::GetExStyle

ウィンドウの拡張スタイルを取得します。

```
virtual DWORD GetExStyle() const;
```

### <a name="return-value"></a>戻り値

コントロールウィンドウの拡張スタイル。

### <a name="remarks"></a>Remarks

標準スタイルを取得するには、 [COleControlSite:: GetStyle](#getstyle)を呼び出します。

##  <a name="getproperty"></a>  COleControlSite::GetProperty

*Dwdispid*によって指定されたコントロールプロパティを取得します。

```
virtual void GetProperty(
    DISPID dwDispID,
    VARTYPE vtProp,
    void* pvProp) const;
```

### <a name="parameters"></a>パラメーター

*dwDispID*<br/>
取得するコントロールの既定`IDispatch`のインターフェイスで検出されたプロパティのディスパッチ ID を識別します。

*vtProp*<br/>
取得するプロパティの型を指定します。 使用できる値については、 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)の「解説」をご覧ください。

*pvProp*<br/>
プロパティ値を受け取る変数のアドレス。 *VtProp*によって指定された型と一致している必要があります。

### <a name="remarks"></a>Remarks

値は、 *Pvprop*を通じて返されます。

##  <a name="getstyle"></a>  COleControlSite::GetStyle

コントロールサイトのスタイルを取得します。

```
virtual DWORD GetStyle() const;
```

### <a name="return-value"></a>戻り値

ウィンドウのスタイル。

### <a name="remarks"></a>Remarks

使用可能な値の一覧については、「 [Windows スタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)」を参照してください。 コントロールサイトの拡張スタイルを取得するには、 [COleControlSite:: GetExStyle](#getexstyle)を呼び出します。

##  <a name="getwindowtext"></a>  COleControlSite::GetWindowText

コントロールの現在のテキストを取得します。

```
virtual void GetWindowText(CString& str) const;
```

### <a name="parameters"></a>パラメーター

*str*<br/>
コントロールの現在の`CString`テキストを格納しているオブジェクトへの参照。

### <a name="remarks"></a>Remarks

コントロールが Caption ストックプロパティをサポートしている場合は、この値が返されます。 Caption ストックプロパティがサポートされていない場合は、Text プロパティの値が返されます。

##  <a name="invokehelper"></a>  COleControlSite::InvokeHelper

*Wflags*によって指定されたコンテキストで、 *dwdispid*によって指定されたメソッドまたはプロパティを呼び出します。

```
virtual void AFX_CDECL InvokeHelper(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo, ...);
```

### <a name="parameters"></a>パラメーター

*dwDispID*<br/>
呼び出される、コントロールの`IDispatch`インターフェイスで見つかったプロパティまたはメソッドのディスパッチ ID を識別します。

*wFlags*<br/>
IDispatch:: Invoke への呼び出しのコンテキストを記述するフラグ。 使用可能な*wflags*値に`IDispatch::Invoke`ついては、Windows SDK の「」を参照してください。

*vtRet*<br/>
戻り値の型を指定します。 使用できる値については、 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)の「解説」をご覧ください。

*pvRet*<br/>
プロパティ値または戻り値を受け取る変数のアドレス。 これは、 *Vtret*によって指定された型と一致している必要があります。

*pbParamInfo*<br/>
*Pbparaminfo*に続くパラメーターの型を指定する、null で終わる文字列のバイトを指すポインター。 使用できる値については、 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)の「解説」をご覧ください。

*...*<br/>
*Pbparaminfo*で指定された型のパラメーターの変数リスト。

### <a name="remarks"></a>Remarks

*Pbparaminfo*パラメーターは、メソッドまたはプロパティに渡されるパラメーターの型を指定します。 引数の変数リストは...構文宣言で。

この関数は、パラメーターを VARIANTARG 値に変換して`IDispatch::Invoke`から、コントロールのメソッドを呼び出します。 `IDispatch::Invoke` の呼び出しに失敗すると、この関数は、例外をスローします。 によっ`IDispatch::Invoke`て返されたステータス`DISP_E_EXCEPTION`コードがの場合`COleDispatchException` 、この関数はオブジェクトをスロー `COleException`します。それ以外の場合は、をスローします。

##  <a name="invokehelperv"></a>  COleControlSite::InvokeHelperV

*Wflags*によって指定されたコンテキストで、 *dwdispid*によって指定されたメソッドまたはプロパティを呼び出します。

```
virtual void InvokeHelperV(
    DISPID dwDispID,
    WORD wFlags,
    VARTYPE vtRet,
    void* pvRet,
    const BYTE* pbParamInfo,
    va_list argList);
```

### <a name="parameters"></a>パラメーター

*dwDispID*<br/>
呼び出される、コントロールの`IDispatch`インターフェイスで見つかったプロパティまたはメソッドのディスパッチ ID を識別します。

*wFlags*<br/>
IDispatch:: Invoke への呼び出しのコンテキストを記述するフラグ。

*vtRet*<br/>
戻り値の型を指定します。 使用できる値については、 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)の「解説」をご覧ください。

*pvRet*<br/>
プロパティ値または戻り値を受け取る変数のアドレス。 これは、 *Vtret*によって指定された型と一致している必要があります。

*pbParamInfo*<br/>
*Pbparaminfo*に続くパラメーターの型を指定する、null で終わる文字列のバイトを指すポインター。 使用できる値については、 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)の「解説」をご覧ください。

*argList*<br/>
変数の引数リストへのポインター。

### <a name="remarks"></a>Remarks

*Pbparaminfo*パラメーターは、メソッドまたはプロパティに渡されるパラメーターの型を指定します。 呼び出されるメソッドまたはプロパティの追加パラメーターは、 *va_list*パラメーターを使用して渡すことができます。

通常、この関数はによっ`COleControlSite::InvokeHelper`て呼び出されます。

##  <a name="isdefaultbutton"></a>  COleControlSite::IsDefaultButton

コントロールが既定のボタンであるかどうかを判断します。

```
BOOL IsDefaultButton();
```

### <a name="return-value"></a>戻り値

コントロールがウィンドウの既定のボタンである場合は0以外の値。それ以外の場合は0。

##  <a name="iswindowenabled"></a>  COleControlSite::IsWindowEnabled

コントロールサイトが有効かどうかを判断します。

```
virtual BOOL IsWindowEnabled() const;
```

### <a name="return-value"></a>戻り値

コントロールが有効な場合は0以外の値。それ以外の場合は0。

### <a name="remarks"></a>Remarks

値は、コントロールの有効なストックプロパティから取得されます。

##  <a name="m_biswindowless"></a>  COleControlSite::m_bIsWindowless

オブジェクトがウィンドウなしのコントロールであるかどうかを判断します。

```
BOOL m_bIsWindowless;
```

### <a name="remarks"></a>Remarks

コントロールにウィンドウがない場合は0以外の値。それ以外の場合は0。

##  <a name="m_ctlinfo"></a>  COleControlSite::m_ctlInfo

コントロールがキーボード入力を処理する方法に関する情報。

```
CONTROLINFO m_ctlInfo;
```

### <a name="remarks"></a>Remarks

この情報は、制御[Linfo](/windows/win32/api/ocidl/ns-ocidl-controlinfo)構造体に格納されます。

##  <a name="m_dweventsink"></a>  COleControlSite::m_dwEventSink

コントロールのイベントシンクからの接続ポイントのクッキーを格納します。

```
DWORD m_dwEventSink;
```

##  <a name="m_dwmiscstatus"></a>COleControlSite::m_dwMiscStatus

コントロールに関するその他の情報を格納します。

```
DWORD m_dwMiscStatus;
```

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc)」を参照してください。

##  <a name="m_dwpropnotifysink"></a>  COleControlSite::m_dwPropNotifySink

[IPropertyNotifySink](/windows/win32/api/ocidl/nn-ocidl-ipropertynotifysink) cookie を格納します。

```
DWORD m_dwPropNotifySink;
```

##  <a name="m_dwstyle"></a>  COleControlSite::m_dwStyle

コントロールのウィンドウスタイルを格納します。

```
DWORD m_dwStyle;
```

##  <a name="m_hwnd"></a>  COleControlSite::m_hWnd

コントロールの HWND を格納します。コントロールがウィンドウなしの場合は NULL を格納します。

```
HWND m_hWnd;
```

##  <a name="m_iidevents"></a>  COleControlSite::m_iidEvents

コントロールの既定のイベントシンクインターフェイスのインターフェイス ID を格納します。

```
IID m_iidEvents;
```

##  <a name="m_nid"></a>  COleControlSite::m_nID

コントロールのダイアログ項目 ID を格納します。

```
UINT m_nID;
```

##  <a name="m_pactiveobject"></a>  COleControlSite::m_pActiveObject

コントロールの[IOleInPlaceActiveObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceactiveobject)インターフェイスを格納します。

```
LPOLEINPLACEACTIVEOBJECT m_pActiveObject;
```

##  <a name="m_pctrlcont"></a>  COleControlSite::m_pCtrlCont

コントロールのコンテナー (フォームを表す) が含まれています。

```
COleControlContainer* m_pCtrlCont;
```

##  <a name="m_pinplaceobject"></a>  COleControlSite::m_pInPlaceObject

コントロールの`IOleInPlaceObject` [IOleInPlaceObject](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceobject)インターフェイスを格納します。

```
LPOLEINPLACEOBJECT m_pInPlaceObject;
```

##  <a name="m_pobject"></a>  COleControlSite::m_pObject

コントロールの`IOleObjectInterface`インターフェイスが含まれています。

```
LPOLEOBJECT m_pObject;
```

##  <a name="m_pwindowlessobject"></a>  COleControlSite::m_pWindowlessObject

コントロールの`IOleInPlaceObjectWindowless` [IOleInPlaceObjectWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplaceobjectwindowless)インターフェイスを格納します。

```
IOleInPlaceObjectWindowless* m_pWindowlessObject;
```

##  <a name="m_pwndctrl"></a>  COleControlSite::m_pWndCtrl

コントロール自体を表す`CWnd`オブジェクトへのポインターを格納します。

```
CWnd* m_pWndCtrl;
```

##  <a name="m_rect"></a>  COleControlSite::m_rect

コンテナーのウィンドウを基準とした、コントロールの境界を格納します。

```
CRect m_rect;
```

##  <a name="modifystyle"></a>  COleControlSite::ModifyStyle

コントロールのスタイルを変更します。

```
virtual BOOL ModifyStyle(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>パラメーター

*dwRemove*<br/>
現在のウィンドウスタイルから削除するスタイル。

*dwAdd*<br/>
現在のウィンドウスタイルから追加するスタイル。

*nFlags*<br/>
ウィンドウの配置フラグ。 使用可能な値の一覧については、Windows SDK の「 [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)関数」を参照してください。

### <a name="return-value"></a>戻り値

スタイルが変更された場合は0以外の値。それ以外の場合は0。

### <a name="remarks"></a>Remarks

コントロールの stock Enabled プロパティは、WS_DISABLED の設定と一致するように変更されます。 コントロールのストック境界線のスタイルプロパティは、WS_BORDER の要求された設定と一致するように変更されます。 他のすべてのスタイルは、コントロールのウィンドウハンドル (存在する場合) に直接適用されます。

コントロールのウィンドウスタイルを変更します。 追加または削除するスタイルは、ビットごとの OR ( &#124; ) 演算子を使用して組み合わせることができます。 使用可能なウィンドウスタイルの詳細については、Windows SDK の「 [CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww)関数」を参照してください。

*Nflags*が0以外の`ModifyStyle`場合、は Win32 `SetWindowPos`関数を呼び出し、 *nflags*を次の4つのフラグと組み合わせてウィンドウを再描画します。

- SWP_NOSIZE は現在のサイズを保持します。

- SWP_NOMOVE は現在の位置を保持します。

- SWP_NOZORDER は、現在の Z オーダーを保持します。

- SWP_NOACTIVATE では、ウィンドウはアクティブになりません。

ウィンドウの拡張スタイルを変更するには、 [modifystyles ex](#modifystyleex)を呼び出します。

##  <a name="modifystyleex"></a>  COleControlSite::ModifyStyleEx

コントロールの拡張スタイルを変更します。

```
virtual BOOL ModifyStyleEx(
    DWORD dwRemove,
    DWORD dwAdd,
    UINT nFlags);
```

### <a name="parameters"></a>パラメーター

*dwRemove*<br/>
現在のウィンドウスタイルから削除する拡張スタイル。

*dwAdd*<br/>
現在のウィンドウスタイルから追加する拡張スタイル。

*nFlags*<br/>
ウィンドウの配置フラグ。 使用可能な値の一覧については、Windows SDK の「 [SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)関数」を参照してください。

### <a name="return-value"></a>戻り値

スタイルが変更された場合は0以外の値。それ以外の場合は0。

### <a name="remarks"></a>Remarks

コントロールの stock 外観プロパティは、WS_EX_CLIENTEDGE の設定と一致するように変更されます。 その他のすべての拡張ウィンドウスタイルは、コントロールのウィンドウハンドル (存在する場合) に直接適用されます。

コントロールサイトオブジェクトのウィンドウの拡張スタイルを変更します。 追加または削除するスタイルは、ビットごとの OR ( &#124; ) 演算子を使用して組み合わせることができます。 使用可能なウィンドウスタイルの詳細については、Windows SDK の「 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)関数」を参照してください。

*Nflags*が0以外の`ModifyStyleEx`場合、は Win32 `SetWindowPos`関数を呼び出し、 *nflags*を次の4つのフラグと組み合わせてウィンドウを再描画します。

- SWP_NOSIZE は現在のサイズを保持します。

- SWP_NOMOVE は現在の位置を保持します。

- SWP_NOZORDER は、現在の Z オーダーを保持します。

- SWP_NOACTIVATE では、ウィンドウはアクティブになりません。

ウィンドウの拡張スタイルを変更するには、 [Modifystyle](#modifystyle)を呼び出します。

##  <a name="movewindow"></a>  COleControlSite::MoveWindow

コントロールの位置を変更します。

```
virtual void MoveWindow(
    int x,
    int y,
    int nWidth,
    int nHeight);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
ウィンドウの左側の新しい位置。

*y*<br/>
ウィンドウの上部の新しい位置。

*nWidth*<br/>
ウィンドウの新しい幅

*nHeight*<br/>
ウィンドウの新しい高さ。

##  <a name="quickactivate"></a>  COleControlSite::QuickActivate

含まれているコントロールをクイックアクティブ化します。

```
virtual BOOL QuickActivate();
```

### <a name="return-value"></a>戻り値

コントロールサイトがアクティブになった場合は0以外の値。それ以外の場合は0。

### <a name="remarks"></a>Remarks

この関数は、ユーザーがコントロールの作成プロセスをオーバーライドしている場合にのみ呼び出す必要があります。

クイック`IPersist*::Load`アクティブ`IPersist*::InitNew`化が発生した後に、メソッドとメソッドを呼び出す必要があります。 コントロールは、クイックアクティブ化中にコンテナーのシンクへの接続を確立する必要があります。 ただし、これらの接続は、また`IPersist*::Load`は`IPersist*::InitNew`が呼び出されるまではライブではありません。

##  <a name="safesetproperty"></a>  COleControlSite::SafeSetProperty

*Dwdispid*によって指定されたコントロールプロパティを設定します。

```
virtual BOOL AFX_CDECL SafeSetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>パラメーター

*dwDispID*<br/>
設定するコントロールの`IDispatch`インターフェイスで検出されたプロパティまたはメソッドのディスパッチ ID を識別します。

*vtProp*<br/>
設定するプロパティの種類を指定します。 使用できる値については、 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)の「解説」をご覧ください。

*...*<br/>
*VtProp*によって指定された型の1つのパラメーター。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  `SetProperty` および`SetPropertyV`とは異なり、エラーが発生した場合 (存在しないプロパティを設定しようとした場合など)、例外はスローされません。

##  <a name="setdefaultbutton"></a>COleControlSite:: SetDefaultButton

コントロールを既定のボタンとして設定します。

```
void SetDefaultButton(BOOL bDefault);
```

### <a name="parameters"></a>パラメーター

*bDefault*<br/>
コントロールが既定のボタンになる場合は0以外の値。それ以外の場合は0。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールには、OLEMISC_ACTSLIKEBUTTON ステータスビットが設定されている必要があります。

##  <a name="setdlgctrlid"></a>  COleControlSite::SetDlgCtrlID

コントロールのダイアログ項目識別子の値を変更します。

```
virtual int SetDlgCtrlID(int nID);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
新しい識別子の値。

### <a name="return-value"></a>戻り値

成功した場合は、ウィンドウの前のダイアログ項目識別子。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

##  <a name="setfocus"></a>  COleControlSite::SetFocus

フォーカスをコントロールに設定します。

```
virtual CWnd* SetFocus();
virtual CWnd* SetFocus(LPMSG lpmsg);
```

### <a name="parameters"></a>パラメーター

*lpmsg*<br/>
[MSG 構造体](/windows/win32/api/winuser/ns-winuser-msg)へのポインター。 この構造体には、現在の`SetFocus`コントロールサイトに格納されているコントロールの要求をトリガーする Windows メッセージが含まれています。

### <a name="return-value"></a>戻り値

以前フォーカスがあったウィンドウへのポインター。

##  <a name="setproperty"></a>  COleControlSite::SetProperty

*Dwdispid*によって指定されたコントロールプロパティを設定します。

```
virtual void AFX_CDECL SetProperty(
    DISPID dwDispID,
    VARTYPE vtProp, ...);
```

### <a name="parameters"></a>パラメーター

*dwDispID*<br/>
設定するコントロールの`IDispatch`インターフェイスで検出されたプロパティまたはメソッドのディスパッチ ID を識別します。

*vtProp*<br/>
設定するプロパティの種類を指定します。 使用できる値については、 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)の「解説」をご覧ください。

*...*<br/>
*VtProp*によって指定された型の1つのパラメーター。

### <a name="remarks"></a>Remarks

`SetProperty`でエラーが発生すると、例外がスローされます。

例外の種類は、プロパティまたはメソッドを設定しようとしたときの戻り値によって決まります。 戻り値が`DISP_E_EXCEPTION` `COleDispatchExcpetion`の場合は、がスローされます`COleException`。それ以外の場合は。

##  <a name="setpropertyv"></a>  COleControlSite::SetPropertyV

*Dwdispid*によって指定されたコントロールプロパティを設定します。

```
virtual void SetPropertyV(
    DISPID dwDispID,
    VARTYPE vtProp,
    va_list argList);
```

### <a name="parameters"></a>パラメーター

*dwDispID*<br/>
設定するコントロールの`IDispatch`インターフェイスで検出されたプロパティまたはメソッドのディスパッチ ID を識別します。

*vtProp*<br/>
設定するプロパティの種類を指定します。 使用できる値については、 [COleDispatchDriver::InvokeHelper](../../mfc/reference/coledispatchdriver-class.md#invokehelper)の「解説」をご覧ください。

*argList*<br/>
引数リストへのポインター。

### <a name="remarks"></a>Remarks

呼び出されるメソッドまたはプロパティの追加パラメーターは、 *arg_list*パラメーターを使用して、パスワードを指定することができます。 `SetProperty`でエラーが発生すると、例外がスローされます。

例外の種類は、プロパティまたはメソッドを設定しようとしたときの戻り値によって決まります。 戻り値が`DISP_E_EXCEPTION` `COleDispatchExcpetion`の場合は、がスローされます`COleException`。それ以外の場合は。

##  <a name="setwindowpos"></a>  COleControlSite::SetWindowPos

コントロールサイトのサイズ、位置、および Z の順序を設定します。

```
virtual BOOL SetWindowPos(
    const CWnd* pWndInsertAfter,
    int x,
    int y,
    int cx,
    int cy,
    UINT nFlags);
```

### <a name="parameters"></a>パラメーター

*pWndInsertAfter*<br/>
ウィンドウへのポインター。

*x*<br/>
ウィンドウの左側の新しい位置。

*y*<br/>
ウィンドウの上部の新しい位置。

*cx*<br/>
ウィンドウの新しい幅

*暦年*<br/>
ウィンドウの新しい高さ。

*nFlags*<br/>
ウィンドウのサイズ変更フラグと配置フラグを指定します。 使用可能な値については、Windows SDK の[SetWindowPos](/windows/win32/api/winuser/nf-winuser-setwindowpos)の「解説」を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は0以外の値。それ以外の場合は0。

##  <a name="setwindowtext"></a>  COleControlSite::SetWindowText

コントロールサイトのテキストを設定します。

```
virtual void SetWindowText(LPCTSTR lpszString);
```

### <a name="parameters"></a>パラメーター

*lpszString*<br/>
新しいタイトルまたはコントロールテキストとして使用される、null で終わる文字列へのポインター。

### <a name="remarks"></a>Remarks

この関数は、最初にキャプションのストックプロパティを設定しようとします。 Caption ストックプロパティがサポートされていない場合は、代わりに Text プロパティが設定されます。

##  <a name="showwindow"></a>COleControlSite:: ShowWindow

ウィンドウの表示状態を設定します。

```
virtual BOOL ShowWindow(int nCmdShow);
```

### <a name="parameters"></a>パラメーター

*nCmdShow*<br/>
コントロールサイトを表示する方法を指定します。 次のいずれかの値を指定する必要があります。

- SW_HIDE は、このウィンドウを非表示にして、アクティブ化を別のウィンドウに渡します。

- SW_MINIMIZE によってウィンドウが最小化され、システムの一覧のトップレベルウィンドウがアクティブになります。

- SW_RESTORE がアクティブになり、ウィンドウが表示されます。 ウィンドウが最小化または最大化されている場合、Windows は元のサイズと位置にウィンドウを復元します。

- SW_SHOW ウィンドウをアクティブにし、現在のサイズと位置に表示します。

- SW_SHOWMAXIMIZED ウィンドウがアクティブになり、最大化ウィンドウとして表示されます。

- SW_SHOWMINIMIZED ウィンドウをアクティブにし、アイコンとして表示します。

- SW_SHOWMINNOACTIVE ウィンドウをアイコンとして表示します。 現在アクティブなウィンドウはアクティブのままになります。

- SW_SHOWNA ウィンドウが現在の状態で表示されます。 現在アクティブなウィンドウはアクティブのままになります。

- SW_SHOWNOACTIVATE により、ウィンドウが最新のサイズと位置で表示されます。 現在アクティブなウィンドウはアクティブのままになります。

- SW_SHOWNORMAL がアクティブになり、ウィンドウが表示されます。 ウィンドウが最小化または最大化されている場合、Windows は元のサイズと位置にウィンドウを復元します。

### <a name="return-value"></a>戻り値

ウィンドウが以前に表示されていた場合は0以外の。ウィンドウが以前は非表示になっていた場合は0。

## <a name="see-also"></a>関連項目

[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleControlContainer クラス](../../mfc/reference/colecontrolcontainer-class.md)
