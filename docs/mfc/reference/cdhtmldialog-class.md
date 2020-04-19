---
title: CDHtmlDialog クラス
ms.date: 03/27/2019
f1_keywords:
- CDHtmlDialog
- AFXDHTML/CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CDHtmlDialog
- AFXDHTML/CDHtmlDialog::CanAccessExternal
- AFXDHTML/CDHtmlDialog::CreateControlSite
- AFXDHTML/CDHtmlDialog::DDX_DHtml_AxControl
- AFXDHTML/CDHtmlDialog::DDX_DHtml_CheckBox
- AFXDHTML/CDHtmlDialog::DDX_DHtml_ElementText
- AFXDHTML/CDHtmlDialog::DDX_DHtml_Radio
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectIndex
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectString
- AFXDHTML/CDHtmlDialog::DDX_DHtml_SelectValue
- AFXDHTML/CDHtmlDialog::DestroyModeless
- AFXDHTML/CDHtmlDialog::EnableModeless
- AFXDHTML/CDHtmlDialog::FilterDataObject
- AFXDHTML/CDHtmlDialog::GetControlDispatch
- AFXDHTML/CDHtmlDialog::GetControlProperty
- AFXDHTML/CDHtmlDialog::GetCurrentUrl
- AFXDHTML/CDHtmlDialog::GetDHtmlDocument
- AFXDHTML/CDHtmlDialog::GetDropTarget
- AFXDHTML/CDHtmlDialog::GetElement
- AFXDHTML/CDHtmlDialog::GetElementHtml
- AFXDHTML/CDHtmlDialog::GetElementInterface
- AFXDHTML/CDHtmlDialog::GetElementProperty
- AFXDHTML/CDHtmlDialog::GetElementText
- AFXDHTML/CDHtmlDialog::GetEvent
- AFXDHTML/CDHtmlDialog::GetExternal
- AFXDHTML/CDHtmlDialog::GetHostInfo
- AFXDHTML/CDHtmlDialog::GetOptionKeyPath
- AFXDHTML/CDHtmlDialog::HideUI
- AFXDHTML/CDHtmlDialog::IsExternalDispatchSafe
- AFXDHTML/CDHtmlDialog::LoadFromResource
- AFXDHTML/CDHtmlDialog::Navigate
- AFXDHTML/CDHtmlDialog::OnBeforeNavigate
- AFXDHTML/CDHtmlDialog::OnDocumentComplete
- AFXDHTML/CDHtmlDialog::OnDocWindowActivate
- AFXDHTML/CDHtmlDialog::OnFrameWindowActivate
- AFXDHTML/CDHtmlDialog::OnInitDialog
- AFXDHTML/CDHtmlDialog::OnNavigateComplete
- AFXDHTML/CDHtmlDialog::ResizeBorder
- AFXDHTML/CDHtmlDialog::SetControlProperty
- AFXDHTML/CDHtmlDialog::SetElementHtml
- AFXDHTML/CDHtmlDialog::SetElementProperty
- AFXDHTML/CDHtmlDialog::SetElementText
- AFXDHTML/CDHtmlDialog::SetExternalDispatch
- AFXDHTML/CDHtmlDialog::SetHostFlags
- AFXDHTML/CDHtmlDialog::ShowContextMenu
- AFXDHTML/CDHtmlDialog::ShowUI
- AFXDHTML/CDHtmlDialog::TranslateAccelerator
- AFXDHTML/CDHtmlDialog::TranslateUrl
- AFXDHTML/CDHtmlDialog::UpdateUI
- AFXDHTML/CDHtmlDialog::m_bUseHtmlTitle
- AFXDHTML/CDHtmlDialog::m_nHtmlResID
- AFXDHTML/CDHtmlDialog::m_pBrowserApp
- AFXDHTML/CDHtmlDialog::m_spHtmlDoc
- AFXDHTML/CDHtmlDialog::m_strCurrentUrl
- AFXDHTML/CDHtmlDialog::m_szHtmlResID
helpviewer_keywords:
- CDHtmlDialog [MFC], CDHtmlDialog
- CDHtmlDialog [MFC], CanAccessExternal
- CDHtmlDialog [MFC], CreateControlSite
- CDHtmlDialog [MFC], DDX_DHtml_AxControl
- CDHtmlDialog [MFC], DDX_DHtml_CheckBox
- CDHtmlDialog [MFC], DDX_DHtml_ElementText
- CDHtmlDialog [MFC], DDX_DHtml_Radio
- CDHtmlDialog [MFC], DDX_DHtml_SelectIndex
- CDHtmlDialog [MFC], DDX_DHtml_SelectString
- CDHtmlDialog [MFC], DDX_DHtml_SelectValue
- CDHtmlDialog [MFC], DestroyModeless
- CDHtmlDialog [MFC], EnableModeless
- CDHtmlDialog [MFC], FilterDataObject
- CDHtmlDialog [MFC], GetControlDispatch
- CDHtmlDialog [MFC], GetControlProperty
- CDHtmlDialog [MFC], GetCurrentUrl
- CDHtmlDialog [MFC], GetDHtmlDocument
- CDHtmlDialog [MFC], GetDropTarget
- CDHtmlDialog [MFC], GetElement
- CDHtmlDialog [MFC], GetElementHtml
- CDHtmlDialog [MFC], GetElementInterface
- CDHtmlDialog [MFC], GetElementProperty
- CDHtmlDialog [MFC], GetElementText
- CDHtmlDialog [MFC], GetEvent
- CDHtmlDialog [MFC], GetExternal
- CDHtmlDialog [MFC], GetHostInfo
- CDHtmlDialog [MFC], GetOptionKeyPath
- CDHtmlDialog [MFC], HideUI
- CDHtmlDialog [MFC], IsExternalDispatchSafe
- CDHtmlDialog [MFC], LoadFromResource
- CDHtmlDialog [MFC], Navigate
- CDHtmlDialog [MFC], OnBeforeNavigate
- CDHtmlDialog [MFC], OnDocumentComplete
- CDHtmlDialog [MFC], OnDocWindowActivate
- CDHtmlDialog [MFC], OnFrameWindowActivate
- CDHtmlDialog [MFC], OnInitDialog
- CDHtmlDialog [MFC], OnNavigateComplete
- CDHtmlDialog [MFC], ResizeBorder
- CDHtmlDialog [MFC], SetControlProperty
- CDHtmlDialog [MFC], SetElementHtml
- CDHtmlDialog [MFC], SetElementProperty
- CDHtmlDialog [MFC], SetElementText
- CDHtmlDialog [MFC], SetExternalDispatch
- CDHtmlDialog [MFC], SetHostFlags
- CDHtmlDialog [MFC], ShowContextMenu
- CDHtmlDialog [MFC], ShowUI
- CDHtmlDialog [MFC], TranslateAccelerator
- CDHtmlDialog [MFC], TranslateUrl
- CDHtmlDialog [MFC], UpdateUI
- CDHtmlDialog [MFC], m_bUseHtmlTitle
- CDHtmlDialog [MFC], m_nHtmlResID
- CDHtmlDialog [MFC], m_pBrowserApp
- CDHtmlDialog [MFC], m_spHtmlDoc
- CDHtmlDialog [MFC], m_strCurrentUrl
- CDHtmlDialog [MFC], m_szHtmlResID
ms.assetid: 3f941c85-87e1-4f0f-9cc5-ffee8498b312
ms.openlocfilehash: ec424e433dc84bf4188e349eb6450888aeeeb463
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506896"
---
# <a name="cdhtmldialog-class"></a>CDHtmlDialog クラス

は、ダイアログリソースではなく HTML を使用してユーザーインターフェイスを実装するダイアログボックスを作成するために使用されます。

## <a name="syntax"></a>構文

```
class CDHtmlDialog : public CDialog, public CDHtmlEventSink
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDHtmlDialog:: CDHtmlDialog](#cdhtmldialog)|CDHtmlDialog オブジェクトを構築します。|
|[CDHtmlDialog:: ~ CDHtmlDialog](#_dtorcdhtmldialog)|CDHtmlDialog オブジェクトを破棄します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDHtmlDialog:: CanAccessExternal](#canaccessexternal)|読み込まれたページ上のスクリプトオブジェクトが、コントロールサイトの外部ディスパッチにアクセスできるかどうかを確認するアクセスチェックとして呼び出されるオーバーライド可能な。 ディスパッチがスクリプトに対して安全であることを確認するか、現在のゾーンでスクリプトに対して安全ではないオブジェクトを許可します。|
|[CDHtmlDialog:: CreateControlSite](#createcontrolsite)|ダイアログで WebBrowser コントロールをホストするコントロールサイトのインスタンスを作成するために使用されるオーバーライド可能な。|
|[CDHtmlDialog::DDX_DHtml_AxControl](#ddx_dhtml_axcontrol)|HTML ページ上の ActiveX コントロールのメンバー変数とプロパティ値の間でデータを交換します。|
|[CDHtmlDialog::DDX_DHtml_CheckBox](#ddx_dhtml_checkbox)|HTML ページのメンバー変数とチェックボックスの間でデータを交換します。|
|[CDHtmlDialog::D DX_DHtml_ElementText](#ddx_dhtml_elementtext)|HTML ページのメンバー変数と HTML 要素のプロパティとの間でデータを交換します。|
|[CDHtmlDialog::DDX_DHtml_Radio](#ddx_dhtml_radio)|メンバー変数と、HTML ページのラジオボタンの間でデータを交換します。|
|[CDHtmlDialog::DDX_DHtml_SelectIndex](#ddx_dhtml_selectindex)|HTML ページ上のリストボックスのインデックスを取得または設定します。|
|[CDHtmlDialog::D DX_DHtml_SelectString](#ddx_dhtml_selectstring)|HTML ページのリストボックスエントリ (現在のインデックスに基づく) の表示テキストを取得または設定します。|
|[CDHtmlDialog::DDX_DHtml_SelectValue](#ddx_dhtml_selectvalue)|HTML ページのリストボックスエントリ (現在のインデックスに基づく) の値を取得または設定します。|
|[CDHtmlDialog::D estroyModeless](#destroymodeless)|モードレスダイアログボックスを破棄します。|
|[CDHtmlDialog::EnableModeless](#enablemodeless)|モードレスダイアログボックスを有効にします。|
|[CDHtmlDialog:: FilterDataObject](#filterdataobject)|ホストされたブラウザーによって作成されたクリップボードデータオブジェクトをダイアログがフィルター処理できるようにします。|
|[CDHtmlDialog:: GetControlDispatch](#getcontroldispatch)|HTML ドキュメントに埋め込まれている ActiveX コントロールのインターフェイスを取得します。`IDispatch`|
|[CDHtmlDialog:: GetControlProperty](#getcontrolproperty)|指定した ActiveX コントロールの要求されたプロパティを取得します。|
|[CDHtmlDialog:: GetCurrentUrl](#getcurrenturl)|現在のドキュメントに関連付けられている Uniform Resource Locator (URL) を取得します。|
|[CDHtmlDialog:: GetDHtmlDocument](#getdhtmldocument)|現在読み込まれている HTML ドキュメントの IHTMLDocument2 インターフェイスを取得します。|
|[CDHtmlDialog:: GetDropTarget](#getdroptarget)|ドロップターゲットとして使用されている場合に、そのコントロールによって呼び出され、別の[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)をダイアログで提供できるようにします。|
|[CDHtmlDialog:: GetElement](#getelement)|HTML 要素のインターフェイスを取得します。|
|[CDHtmlDialog:: GetElementHtml](#getelementhtml)|HTML 要素のプロパティを取得します。 `innerHTML`|
|[CDHtmlDialog:: GetElementInterface](#getelementinterface)|要求されたインターフェイスポインターを HTML 要素から取得します。|
|[CDHtmlDialog:: GetElementProperty](#getelementproperty)|HTML 要素のプロパティの値を取得します。|
|[CDHtmlDialog:: GetElementText](#getelementtext)|HTML 要素のプロパティを取得します。 `innerText`|
|[CDHtmlDialog:: GetEvent](#getevent)|現在のイベントオブジェクトへのポインターを取得します。`IHTMLEventObj`|
|[CDHtmlDialog:: GetExternal](#getexternal)|ホストの`IDispatch`インターフェイスを取得します。|
|[CDHtmlDialog:: GetHostInfo](#gethostinfo)|ホストの UI 機能を取得します。|
|[CDHtmlDialog:: GetOptionKeyPath](#getoptionkeypath)|ユーザー設定が格納されているレジストリキーを取得します。|
|[CDHtmlDialog:: HideUI](#hideui)|ホストの UI を非表示にします。|
|[CDHtmlDialog:: IsExternalDispatchSafe](#isexternaldispatchsafe)|ホストの`IDispatch`インターフェイスがスクリプトに対して安全であるかどうかを示します。|
|[CDHtmlDialog:: LoadFromResource](#loadfromresource)|指定されたリソースを WebBrowser コントロールに読み込みます。|
|[CDHtmlDialog:: Navigate](#navigate)|指定された URL に移動します。|
|[CDHtmlDialog::OnBeforeNavigate](#onbeforenavigate)|ナビゲーションイベントが発生する前にフレームワークによって呼び出されます。|
|[CDHtmlDialog::OnDocumentComplete](#ondocumentcomplete)|ドキュメントが READYSTATE_COMPLETE 状態に達したときにアプリケーションに通知するために、フレームワークによって呼び出されます。|
|[CDHtmlDialog::OnDocWindowActivate](#ondocwindowactivate)|ドキュメントウィンドウがアクティブ化または非アクティブ化されたときにフレームワークによって呼び出されます。|
|[CDHtmlDialog::OnFrameWindowActivate](#onframewindowactivate)|フレームウィンドウがアクティブ化または非アクティブ化されたときにフレームワークによって呼び出されます。|
|[CDHtmlDialog::OnInitDialog](#oninitdialog)|WM_INITDIALOG メッセージへの応答として呼び出されます。|
|[CDHtmlDialog:: OnNavigateComplete](#onnavigatecomplete)|ナビゲーションイベントの完了後にフレームワークによって呼び出されます。|
|[CDHtmlDialog::ResizeBorder](#resizeborder)|境界領域のサイズを変更する必要があることをオブジェクトに通知します。|
|[CDHtmlDialog:: SetControlProperty](#setcontrolproperty)|ActiveX コントロールのプロパティを新しい値に設定します。|
|[CDHtmlDialog:: SetElementHtml](#setelementhtml)|HTML 要素`innerHTML`のプロパティを設定します。|
|[CDHtmlDialog:: SetElementProperty](#setelementproperty)|HTML 要素のプロパティを設定します。|
|[CDHtmlDialog:: SetElementText](#setelementtext)|HTML 要素`innerText`のプロパティを設定します。|
|[CDHtmlDialog:: SetExternalDispatch](#setexternaldispatch)|ホストの`IDispatch`インターフェイスを設定します。|
|[CDHtmlDialog:: SetHostFlags](#sethostflags)|ホストの UI フラグを設定します。|
|[CDHtmlDialog:: ShowContextMenu](#showcontextmenu)|コンテキストメニューが表示されようとしているときに呼び出されます。|
|[CDHtmlDialog:: ShowUI](#showui)|ホストの UI を表示します。|
|[CDHtmlDialog:: TranslateAccelerator](#translateaccelerator)|メニューアクセラレータキーメッセージを処理するために呼び出されます。|
|[CDHtmlDialog::TranslateUrl](#translateurl)|読み込まれる URL を変更するために呼び出されます。|
|[CDHtmlDialog:: UpdateUI](#updateui)|コマンドの状態が変更されたことをホストに通知するために呼び出されます。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CDHtmlDialog:: m_bUseHtmlTitle](#m_busehtmltitle)|HTML ドキュメントのタイトルをダイアログキャプションとして使用するかどうかを示します。|
|[CDHtmlDialog:: m_nHtmlResID](#m_nhtmlresid)|表示する HTML リソースのリソース ID。|
|[CDHtmlDialog:: m_pBrowserApp](#m_pbrowserapp)|Web ブラウザーアプリケーションへのポインター。|
|[CDHtmlDialog:: m_spHtmlDoc](#m_sphtmldoc)|HTML ドキュメントへのポインター。|
|[CDHtmlDialog:: m_strCurrentUrl](#m_strcurrenturl)|現在の URL。|
|[CDHtmlDialog:: m_szHtmlResID](#m_szhtmlresid)|HTML リソース ID の文字列バージョン。|

## <a name="remarks"></a>Remarks

`CDHtmlDialog`HTML リソースまたは URL から表示される HTML を読み込むことができます。

`CDHtmlDialog`は、HTML コントロールを使用してデータ交換を行い、ボタンのクリックなどの HTML コントロールからのイベントを処理することもできます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDHtmlSinkHandlerBase2`

`CDHtmlSinkHandlerBase1`

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDHtmlSinkHandler`

[CWnd](../../mfc/reference/cwnd-class.md)

`CDHtmlEventSink`

[CDialog](../../mfc/reference/cdialog-class.md)

`CDHtmlDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdhtml

##  <a name="ddx_dhtml_helper_macros"></a>DDX_DHtml Helper マクロ

DDX_DHtml helper マクロを使用すると、HTML ページ上のコントロールの一般的に使用されるプロパティに簡単にアクセスできます。

### <a name="data-exchange-macros"></a>データ交換マクロ

|||
|-|-|
|[DDX_DHtml_ElementValue](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementvalue)|選択したコントロールの値プロパティを設定または取得します。|
|[DDX_DHtml_ElementInnerText](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnertext)|現在の要素の開始タグと終了タグの間のテキストを設定または取得します。|
|[DDX_DHtml_ElementInnerHtml](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_elementinnerhtml)|現在の要素の開始タグと終了タグの間にある HTML を設定または取得します。|
|[DDX_DHtml_Anchor_Href](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_href)|送信先 URL またはアンカーポイントを設定または取得します。|
|[DDX_DHtml_Anchor_Target](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_anchor_target)|対象のウィンドウまたはフレームを設定または取得します。|
|[DDX_DHtml_Img_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_img_src)|ドキュメント内のイメージまたはビデオクリップの名前を設定または取得します。|
|[DDX_DHtml_Frame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_frame_src)|関連付けられたフレームの URL を設定または取得します。|
|[DDX_DHtml_IFrame_Src](../../mfc/reference/ddx-dhtml-helper-macros.md#ddx_dhtml_iframe_src)|関連付けられたフレームの URL を設定または取得します。|

##  <a name="canaccessexternal"></a>  CDHtmlDialog::CanAccessExternal

読み込まれたページ上のスクリプトオブジェクトが、コントロールサイトの外部ディスパッチにアクセスできるかどうかを確認するアクセスチェックとして呼び出されるオーバーライド可能な。 ディスパッチがスクリプトに対して安全であることを確認するか、現在のゾーンでスクリプトに対して安全ではないオブジェクトを許可します。

```
virtual BOOL CanAccessExternal();
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="cdhtmldialog"></a>  CDHtmlDialog::CDHtmlDialog

リソースベースの動的 HTML ダイアログボックスを構築します。

```
CDHtmlDialog();

CDHtmlDialog(
    LPCTSTR lpszTemplateName,
    LPCTSTR szHtmlResID,
    CWnd *pParentWnd = NULL);

CDHtmlDialog(
    UINT nIDTemplate,
    UINT nHtmlResID = 0,
    CWnd *pParentWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszTemplateName*<br/>
ダイアログボックステンプレートリソースの名前である null で終わる文字列。

*szHtmlResID*<br/>
HTML リソースの名前を表す null で終わる文字列。

*pParentWnd*<br/>
ダイアログオブジェクトが属する親またはオーナーウィンドウオブジェクト ( [CWnd](../../mfc/reference/cwnd-class.md)型) へのポインター。 NULL の場合は、ダイアログオブジェクトの親ウィンドウがメインアプリケーションウィンドウに設定されます。

*nIDTemplate*<br/>
ダイアログボックステンプレートリソースの ID 番号を格納します。

*nHtmlResID*<br/>
HTML リソースの ID 番号を格納します。

### <a name="remarks"></a>Remarks

コンストラクターの2番目の形式は、テンプレート名を使用してダイアログリソースへのアクセスを提供します。 コンストラクターの3番目の形式は、リソーステンプレートの ID を通じてダイアログリソースへのアクセスを提供します。 通常、ID は**IDD_** プレフィックスで始まります。

##  <a name="_dtorcdhtmldialog"></a>CDHtmlDialog:: ~ CDHtmlDialog

CDHtmlDialog オブジェクトを破棄します。

```
virtual ~CDHtmlDialog();
```

### <a name="remarks"></a>Remarks

[CWnd: [: Create](../../mfc/reference/cdialog-class.md#create)] で作成されたモードレスダイアログボックスを破棄するには、 [CWnd::D estroywindow](../../mfc/reference/cwnd-class.md#destroywindow)メンバー関数を使用する必要があります。

##  <a name="createcontrolsite"></a>CDHtmlDialog:: CreateControlSite

ダイアログで WebBrowser コントロールをホストするコントロールサイトのインスタンスを作成するために使用されるオーバーライド可能な。

```
virtual BOOL CreateControlSite(
    COleControlContainer* pContainer,
    COleControlSite** ppSite,
    UINT /* nID */,
    REFCLSID /* clsid */);
```

### <a name="parameters"></a>パラメーター

*pContainer*<br/>
[COleControlContainer](../../mfc/reference/colecontrolcontainer-class.md)オブジェクトへのポインター

*ppSite*<br/>
[COleControlSite](../../mfc/reference/colecontrolsite-class.md)へのポインターへのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数をオーバーライドして、独自のコントロールサイトクラスのインスタンスを返すことができます。

##  <a name="ddx_dhtml_axcontrol"></a>  CDHtmlDialog::DDX_DHtml_AxControl

HTML ページ上の ActiveX コントロールのメンバー変数とプロパティ値の間でデータを交換します。

```
void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    VARIANT& var);

void DDX_DHtml_AxControl(
    CDataExchange* pDX,
    LPCTSTR szId,
    LPCTSTR szPropName,
    VARIANT& var);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。

*szId*<br/>
ActiveX コントロールの HTML ソースのオブジェクトタグの ID パラメーターの値。

*dispId*<br/>
データの交換に使用するプロパティのディスパッチ ID。

*szPropName*<br/>
プロパティの名前。

*var*<br/>
ActiveX コントロールプロパティと交換された値を保持する、VARIANT、 [COleVariant](../../mfc/reference/colevariant-class.md)、または[CComVariant](../../atl/reference/ccomvariant-class.md)型のデータメンバー。

### <a name="example"></a>例

[!code-cpp[NVC_MFCHtmlHttp#1](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_1.cpp)]

##  <a name="ddx_dhtml_checkbox"></a>  CDHtmlDialog::DDX_DHtml_CheckBox

HTML ページのメンバー変数とチェックボックスの間でデータを交換します。

```
void DDX_DHtml_CheckBox(
    CDataExchange* pDX,
    LPCTSTR szId,
    int& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。

*szId*<br/>
HTML コントロールの ID パラメーターに指定した値。

*value*<br/>
交換される値。

### <a name="example"></a>例

[!code-cpp[NVC_MFCHtmlHttp#2](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_2.cpp)]

##  <a name="ddx_dhtml_elementtext"></a>  CDHtmlDialog::DDX_DHtml_ElementText

HTML ページのメンバー変数と HTML 要素のプロパティとの間でデータを交換します。

```
void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    CString& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    short& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    int& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    long& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    DWORD& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    float& value);

void DDX_DHtml_ElementText(
    CDataExchange* pDX,
    LPCTSTR szId,
    DISPID dispId,
    double& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。

*szId*<br/>
HTML コントロールの ID パラメーターに指定した値。

*dispId*<br/>
データの交換に使用する HTML 要素のディスパッチ ID。

*value*<br/>
交換される値。

##  <a name="ddx_dhtml_radio"></a>  CDHtmlDialog::DDX_DHtml_Radio

メンバー変数と、HTML ページのラジオボタンの間でデータを交換します。

```
void DDX_DHtml_Radio(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。

*szId*<br/>
HTML コントロールの ID パラメーターに指定した値。

*value*<br/>
交換される値。

##  <a name="ddx_dhtml_selectindex"></a>  CDHtmlDialog::DDX_DHtml_SelectIndex

HTML ページ上のリストボックスのインデックスを取得または設定します。

```
void DDX_DHtml_SelectIndex(
    CDataExchange* pDX,
    LPCTSTR szId,
    long& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。

*szId*<br/>
HTML コントロールの`id`パラメーターに指定した値。

*value*<br/>
交換される値。

##  <a name="ddx_dhtml_selectstring"></a>  CDHtmlDialog::DDX_DHtml_SelectString

HTML ページのリストボックスエントリ (現在のインデックスに基づく) の表示テキストを取得または設定します。

```
void DDX_DHtml_SelectString(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。

*szId*<br/>
HTML コントロールの ID パラメーターに指定した値。

*value*<br/>
交換される値。

##  <a name="ddx_dhtml_selectvalue"></a>  CDHtmlDialog::DDX_DHtml_SelectValue

HTML ページのリストボックスエントリ (現在のインデックスに基づく) の値を取得または設定します。

```
void DDX_DHtml_SelectValue(
    CDataExchange* pDX,
    LPCTSTR szId,
    CString& value);
```

### <a name="parameters"></a>パラメーター

*pDX*<br/>
[CDataExchange](../../mfc/reference/cdataexchange-class.md)オブジェクトへのポインター。

*szId*<br/>
HTML コントロールの ID パラメーターに指定した値。

*value*<br/>
交換される値。

### <a name="example"></a>例

[!code-cpp[NVC_MFCHtmlHttp#3](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_3.cpp)]

##  <a name="destroymodeless"></a>  CDHtmlDialog::DestroyModeless

`CDHtmlDialog`オブジェクトからモードレスダイアログボックスをデタッチし、オブジェクトを破棄します。

```
void DestroyModeless();
```

##  <a name="enablemodeless"></a>  CDHtmlDialog::EnableModeless

モードレスダイアログボックスを有効にします。

```
STDMETHOD(EnableModeless)(BOOL fEnable);
```

### <a name="parameters"></a>パラメーター

*fEnable*<br/>
Windows SDK の「 *Fenable* in [IDocHostUIHandler:: EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\)) 」を参照してください。

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))の CDHtmlDialog の実装です。

##  <a name="filterdataobject"></a>  CDHtmlDialog::FilterDataObject

ホストされたブラウザーによって作成されたクリップボードデータオブジェクトをダイアログがフィルター処理できるようにします。

```
STDMETHOD(FilterDataObject)(
    IDataObject* pDO,
    IDataObject** ppDORet);
```

### <a name="parameters"></a>パラメーター

*pDO*<br/>
Windows SDK の「 [IDocHostUIHandler:: FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))の*pDO* 」を参照してください。

*ppDORet*<br/>
Windows SDKの「 `IDocHostUIHandler::FilterDataObject` ppDORet」を参照してください。

### <a name="return-value"></a>戻り値

S_FALSE を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))の CDHtmlDialog の実装です。

##  <a name="getcontroldispatch"></a>  CDHtmlDialog::GetControlDispatch

[GetDHtmlDocument](#getdhtmldocument) によって返される HTML ドキュメントに埋め込まれている ActiveX コントロールのインターフェイスを取得します。`IDispatch`

```
HRESULT GetControlDispatch(
    LPCTSTR szId,
    IDispatch** ppdisp);
```

### <a name="parameters"></a>パラメーター

*szId*<br/>
ActiveX コントロールの HTML ID。

*ppdisp*<br/>
コントロール`IDispatch`のインターフェイス (Web ページに存在する場合)。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="getcontrolproperty"></a>  CDHtmlDialog::GetControlProperty

指定した ActiveX コントロールの要求されたプロパティを取得します。

```
VARIANT GetControlProperty(
    LPCTSTR szId,
    LPCTSTR szPropName);

VARIANT GetControlProperty(
    LPCTSTR szId,
    DISPID dispId);

VARIANT GetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId);
```

### <a name="parameters"></a>パラメーター

*szId*<br/>
ActiveX コントロールの HTML ID。

*szPropName*<br/>
現在のユーザーの既定のロケールでのプロパティの名前。

*pdispControl*<br/>
ActiveX コントロールのポインター。 `IDispatch`

*dispId*<br/>
プロパティのディスパッチ ID。

### <a name="return-value"></a>戻り値

要求されたプロパティを格納している variant。コントロールまたはプロパティが見つからなかった場合は空のバリアント。

### <a name="remarks"></a>Remarks

オーバーロードは、一番下にある最も効率的なものから順に表示されます。

##  <a name="getcurrenturl"></a>  CDHtmlDialog::GetCurrentUrl

現在のドキュメントに関連付けられている Uniform Resource Locator (URL) を取得します。

```
void GetCurrentUrl(CString& szUrl);
```

### <a name="parameters"></a>パラメーター

*szUrl*<br/>
取得する URL を格納している[CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクト。

##  <a name="getdhtmldocument"></a>  CDHtmlDialog::GetDHtmlDocument

現在読み込まれている HTML ドキュメントの[IHTMLDocument2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752574\(v=vs.85\))インターフェイスを取得します。

```
HRESULT GetDHtmlDocument(IHTMLDocument2 **pphtmlDoc);
```

### <a name="parameters"></a>パラメーター

pphtmlDoc HTML ドキュメントへのポインターへのポインター。  *\* \**

### <a name="return-value"></a>戻り値

標準の HRESULT です。 成功した場合は S_OK を返します。

##  <a name="getdroptarget"></a>CDHtmlDialog:: GetDropTarget

ドロップターゲットとして使用されている場合に、そのコントロールによって呼び出され、別の[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)をダイアログで提供できるようにします。

```
STDMETHOD(GetDropTarget)(
    IDropTarget* pDropTarget,
    IDropTarget** ppDropTarget);
```

### <a name="parameters"></a>パラメーター

*pDropTarget*<br/>
Windows SDK の「 [IDocHostUIHandler:: GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))の*pdroptarget* 」を参照してください。

*ppDropTarget*<br/>
Windows SDK の「 *ppdroptarget* `IDocHostUIHandler::GetDropTarget` 」を参照してください。

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))の CDHtmlDialog の実装です。

##  <a name="getelement"></a>  CDHtmlDialog::GetElement

*Szelementid*によって指定された HTML 要素のインターフェイスを返します。

```
HRESULT GetElement(
    LPCTSTR szElementId,
    IDispatch** ppdisp,
    BOOL* pbCollection = NULL);

HRESULT GetElement(
    LPCTSTR szElementId,
    IHTMLElement** pphtmlElement);
```

### <a name="parameters"></a>パラメーター

*szElementId*<br/>
HTML 要素の ID。

*ppdisp*<br/>
要求された要素または要素のコレクションへのポインター。`IDispatch`

*pbCollection*<br/>
*Ppdisp*によって表されるオブジェクトが、1つの要素または要素のコレクションであるかどうかを示すブール値。

*pphtmlElement*<br/>
要求された要素へのポインター。`IHTMLElement`

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

指定した ID を持つ要素が複数存在する可能性がある条件を処理する必要がある場合は、最初のオーバーロードを使用します。 最後のパラメーターを使用して、返されたインターフェイスポインターがコレクションまたは単一の項目のどちらになっているかを調べることができます。 インターフェイスポインターがコレクションにある場合は、 `IHTMLElementCollection`を照会し、その`item`プロパティを使用して、序数位置によって要素を参照することができます。

ページに同じ ID を持つ要素が複数ある場合、2番目のオーバーロードは失敗します。

##  <a name="getelementhtml"></a>  CDHtmlDialog::GetElementHtml

*Szelementid*によって識別される HTML 要素のプロパティを取得します。`innerHTML`

```
BSTR GetElementHtml(LPCTSTR szElementId);
```

### <a name="parameters"></a>パラメーター

*szElementId*<br/>
HTML 要素の ID。

### <a name="return-value"></a>戻り値

`innerHTML` *Szelementid*によって識別される HTML 要素のプロパティ、または要素が見つからなかった場合は NULL。

##  <a name="getelementinterface"></a>CDHtmlDialog:: GetElementInterface

*Szelementid*によって識別される HTML 要素から、要求されたインターフェイスポインターを取得します。

```
template <class Q> HRESULT GetElementInterface(
    LPCTSTR szElementId,
    Q** ppvObj);

HRESULT GetElementInterface(
    LPCTSTR szElementId,
    REFIID refiid,
    void** ppvObj);
```

### <a name="parameters"></a>パラメーター

*szElementId*<br/>
HTML 要素の ID。

*ppvObj*<br/>
要求されたインターフェイスポインターを格納するポインターのアドレス (要素が見つかった場合は、クエリが成功した場合)。

*refiid*<br/>
要求されたインターフェイスのインターフェイス ID (IID)。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="example"></a>例

[!code-cpp[NVC_MFCHtmlHttp#4](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_4.cpp)]

##  <a name="getelementproperty"></a>  CDHtmlDialog::GetElementProperty

*Szelementid*によって識別される HTML 要素から*dispId*によって識別されるプロパティの値を取得します。

```
VARIANT GetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId);
```

### <a name="parameters"></a>パラメーター

*szElementId*<br/>
HTML 要素の ID。

*dispId*<br/>
プロパティのディスパッチ ID。

### <a name="return-value"></a>戻り値

プロパティの値、またはプロパティまたは要素が見つからなかった場合は空のバリアント。

##  <a name="getelementtext"></a>  CDHtmlDialog::GetElementText

*Szelementid*によって識別される HTML 要素のプロパティを取得します。`innerText`

```
BSTR GetElementText(LPCTSTR szElementId);
```

### <a name="parameters"></a>パラメーター

*szElementId*<br/>
HTML 要素の ID。

### <a name="return-value"></a>戻り値

`innerText` *Szelementid*によって識別される HTML 要素のプロパティ、またはプロパティまたは要素が見つからなかった場合は NULL。

##  <a name="getevent"></a>  CDHtmlDialog::GetEvent

現在のイベントオブジェクトへのポインターを返します。`IHTMLEventObj`

```
HRESULT GetEvent(IHTMLEventObj** ppEventObj);
```

### <a name="parameters"></a>パラメーター

*ppEventObj*<br/>
`IHTMLEventObj`インターフェイスポインターを格納するポインターのアドレス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

この関数は、DHTML イベントハンドラー内からのみ呼び出す必要があります。

##  <a name="getexternal"></a>  CDHtmlDialog::GetExternal

ホストの`IDispatch`インターフェイスを取得します。

```
STDMETHOD(GetExternal)(IDispatch** ppDispatch);
```

### <a name="parameters"></a>パラメーター

*ppDispatch*<br/>
Windows SDK の「 [IDocHostUIHandler:: GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))での*ppdispatch* 」を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合は E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))の CDHtmlDialog の実装です。

##  <a name="gethostinfo"></a>  CDHtmlDialog::GetHostInfo

ホストの UI 機能を取得します。

```
STDMETHOD(GetHostInfo)(DOCHOSTUIINFO* pInfo);
```

### <a name="parameters"></a>パラメーター

*pInfo*<br/>
Windows SDK の「 *pInfo* in [IDocHostUIHandler:: GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\)) 」を参照してください。

### <a name="return-value"></a>戻り値

S_OK を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))の CDHtmlDialog の実装です。

##  <a name="getoptionkeypath"></a>  CDHtmlDialog::GetOptionKeyPath

ユーザー設定が格納されているレジストリキーを取得します。

```
STDMETHOD(GetOptionKeyPath)(
    LPOLESTR* pchKey,
    DWORD dw);
```

### <a name="parameters"></a>パラメーター

*pchKey*<br/>
Windows SDK の「 [IDocHostUIHandler:: GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))の*pchkey* 」を参照してください。

*dw*<br/>
Windows SDKの「 `IDocHostUIHandler::GetOptionKeyPath` dw in」を参照してください。

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))の CDHtmlDialog の実装です。

##  <a name="hideui"></a>  CDHtmlDialog::HideUI

ホストの UI を非表示にします。

```
STDMETHOD(HideUI)(void);
```

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))の CDHtmlDialog の実装です。

##  <a name="isexternaldispatchsafe"></a>  CDHtmlDialog::IsExternalDispatchSafe

ホストの`IDispatch`インターフェイスがスクリプトに対して安全であるかどうかを示します。

```
virtual BOOL IsExternalDispatchSafe();
```

### <a name="return-value"></a>戻り値

FALSE を返します。

##  <a name="loadfromresource"></a>  CDHtmlDialog::LoadFromResource

DHTML ダイアログで、指定されたリソースを WebBrowser コントロールに読み込みます。

```
BOOL LoadFromResource(LPCTSTR lpszResource);
BOOL LoadFromResource(UINT nRes);
```

### <a name="parameters"></a>パラメーター

*lpszResource*<br/>
読み込むリソースの名前を格納している文字列へのポインター。

*nRes*<br/>
読み込むリソースの ID。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

##  <a name="m_busehtmltitle"></a>  CDHtmlDialog::m_bUseHtmlTitle

HTML ドキュメントのタイトルをダイアログキャプションとして使用するかどうかを示します。

```
BOOL m_bUseHtmlTitle;
```

### <a name="remarks"></a>Remarks

**M**_ **busehtmltitle**が TRUE の場合、ダイアログキャプションは HTML ドキュメントのタイトルと同じに設定されます。それ以外の場合は、ダイアログリソースのキャプションが使用されます。

##  <a name="m_nhtmlresid"></a>CDHtmlDialog:: m_nHtmlResID

表示する HTML リソースのリソース ID。

```
UINT m_nHtmlResID;
```

### <a name="example"></a>例

[!code-cpp[NVC_MFCHtmlHttp#5](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_5.cpp)]

##  <a name="m_pbrowserapp"></a>  CDHtmlDialog::m_pBrowserApp

Web ブラウザーアプリケーションへのポインター。

```
CComPtr <IWebBrowser2> m_pBrowserApp;
```

##  <a name="m_sphtmldoc"></a>  CDHtmlDialog::m_spHtmlDoc

HTML ドキュメントへのポインター。

```
CComPtr<IHTMLDocument2> m_spHtmlDoc;
```

##  <a name="m_strcurrenturl"></a>CDHtmlDialog:: m_strCurrentUrl

現在の URL。

```
CString m_strCurrentUrl;
```

##  <a name="m_szhtmlresid"></a>  CDHtmlDialog::m_szHtmlResID

HTML リソース ID の文字列バージョン。

```
LPTSTR m_szHtmlResID;
```

### <a name="example"></a>例

[!code-cpp[NVC_MFCHtmlHttp#6](../../mfc/reference/codesnippet/cpp/cdhtmldialog-class_6.cpp)]

##  <a name="navigate"></a>CDHtmlDialog:: Navigate

*Lpszurl*で指定された url で識別されるリソースに移動します。

```
void Navigate(
    LPCTSTR lpszURL,
    DWORD dwFlags = 0,
    LPCTSTR lpszTargetFrameName = NULL,
    LPCTSTR lpszHeaders = NULL,
    LPVOID lpvPostData = NULL,
    DWORD dwPostDataLen = 0);
```

### <a name="parameters"></a>パラメーター

*lpszURL*<br/>
対象となる URL を格納している文字列へのポインター。

*dwFlags*<br/>
リソースを履歴リストに追加するかどうか、キャッシュに読み取るかキャッシュから書き込むか、新しいウィンドウにリソースを表示するかどうかを指定する変数のフラグ。 変数は、 [Browserナビゲーション定数](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768360\(v=vs.85\))列挙体で定義された値の組み合わせにすることができます。

*lpszTargetFrameName*<br/>
リソースを表示するフレームの名前を格納している文字列へのポインター。

*lpszHeaders*<br/>
サーバーに送信する HTTP ヘッダーを指定する値へのポインター。 これらのヘッダーは、Internet Explorer の既定のヘッダーに追加されます。 ヘッダーでは、サーバーに必要な操作、サーバーに渡されるデータの種類、ステータスコードなどの情報を指定できます。 URL が HTTP URL でない場合、このパラメーターは無視されます。

*lpvPostData*<br/>
HTTP POST トランザクションと共に送信するデータへのポインター。 たとえば、POST トランザクションは、HTML フォームによって収集されたデータを送信するために使用されます。 このパラメーターでポストデータが指定されて`Navigate`いない場合、は HTTP GET トランザクションを発行します。 URL が HTTP URL でない場合、このパラメーターは無視されます。

*dwPostDataLen*<br/>
HTTP POST トランザクションと共に送信するデータ。 たとえば、POST トランザクションは、HTML フォームによって収集されたデータを送信するために使用されます。 このパラメーターでポストデータが指定されて`Navigate`いない場合、は HTTP GET トランザクションを発行します。 URL が HTTP URL ではない場合、このパラメーターは無視されます。

##  <a name="onbeforenavigate"></a>  CDHtmlDialog::OnBeforeNavigate

ナビゲーションが発生する前にイベントを発生させるために、フレームワークによって呼び出されます。

```
virtual void OnBeforeNavigate(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>パラメーター

*pDisp*<br/>
`IDispatch` オブジェクトへのポインター。

*szUrl*<br/>
移動先の URL を格納している文字列へのポインター。

##  <a name="ondocumentcomplete"></a>  CDHtmlDialog::OnDocumentComplete

ドキュメントが READYSTATE_COMPLETE 状態を達成したことをアプリケーションに通知するために、フレームワークによって呼び出されます。

```
virtual void OnDocumentComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>パラメーター

*pDisp*<br/>
`IDispatch` オブジェクトへのポインター。

*szUrl*<br/>
移動先の URL を格納している文字列へのポインター。

##  <a name="ondocwindowactivate"></a>  CDHtmlDialog::OnDocWindowActivate

ドキュメントウィンドウがアクティブ化または非アクティブ化されたときにフレームワークによって呼び出されます。

```
STDMETHOD(OnDocWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>パラメーター

*fActivate*<br/>
Windows SDK の「 *Factivate* in [IDocHostUIHandler:: OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\)) 」を参照してください。

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))の CDHtmlDialog の実装です。

##  <a name="onframewindowactivate"></a>  CDHtmlDialog::OnFrameWindowActivate

フレームウィンドウがアクティブ化または非アクティブ化されたときにフレームワークによって呼び出されます。

```
STDMETHOD(OnFrameWindowActivate)(BOOL fActivate);
```

### <a name="parameters"></a>パラメーター

*fActivate*<br/>
Windows SDK の「 *Factivate* in [IDocHostUIHandler:: Onフレーム windowactivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\)) 」を参照してください。

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: OnCDHtmlDialog Windowactivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))の実装です。

##  <a name="oninitdialog"></a>  CDHtmlDialog::OnInitDialog

WM_INITDIALOG メッセージへの応答として呼び出されます。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>戻り値

既定の実装では、TRUE が返されます。

### <a name="remarks"></a>Remarks

このメッセージは、、 `Create` `CreateIndirect`、または`DoModal`の呼び出し中にダイアログボックスに送信されます。このダイアログボックスは、ダイアログボックスが表示される直前に発生します。

ダイアログボックスが初期化されるときに特別な処理を実行する必要がある場合は、このメンバー関数をオーバーライドします。 オーバーライドされたバージョンでは、最初に`OnInitDialog`基本クラスを呼び出しますが、戻り値は無視します。 通常は、オーバーライドされたメンバー関数から TRUE を返します。

Windows では`OnInitDialog` 、メッセージマップを使用するのではなく、すべての Microsoft Foundation Class ライブラリダイアログボックスに共通する標準のグローバルダイアログボックスのプロシージャを使用して関数を呼び出します。このため、このメンバー関数のメッセージマップエントリは必要ありません。

##  <a name="onnavigatecomplete"></a>  CDHtmlDialog::OnNavigateComplete

指定された URL への移動が完了した後に、フレームワークによって呼び出されます。

```
virtual void OnNavigateComplete(
    LPDISPATCH pDisp,
    LPCTSTR szUrl);
```

### <a name="parameters"></a>パラメーター

*pDisp*<br/>
`IDispatch` オブジェクトへのポインター。

*szUrl*<br/>
移動先の URL を格納している文字列へのポインター。

##  <a name="resizeborder"></a>  CDHtmlDialog::ResizeBorder

境界領域のサイズを変更する必要があることをオブジェクトに通知します。

```
STDMETHOD(ResizeBorder)(
    LPCRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fRameWindow);
```

### <a name="parameters"></a>パラメーター

*prcBorder*<br/>
Windows SDK の「 [IDocHostUIHandler:: ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))の*prcborder* 」を参照してください。

*pUIWindow*<br/>
Windows SDK の「 *puiwindow* `IDocHostUIHandler::ResizeBorder` 」を参照してください。

*fFrameWindow*<br/>
Windows SDK の「」の*fframewindow*を`IDocHostUIHandler::ResizeBorder`参照してください。

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

##  <a name="setcontrolproperty"></a>CDHtmlDialog:: SetControlProperty

ActiveX コントロールのプロパティを新しい値に設定します。

```
void SetControlProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    IDispatch* pdispControl,
    DISPID dispId,
    VARIANT* pVar);

void SetControlProperty(
    LPCTSTR szElementId,
    LPCTSTR szPropName,
    VARIANT* pVar);
```

### <a name="parameters"></a>パラメーター

*szElementId*<br/>
ActiveX コントロールの HTML ID。

*dispId*<br/>
設定するプロパティのディスパッチ ID。

*pVar*<br/>
新しいプロパティ値を格納している VARIANT へのポインター。

*pdispControl*<br/>
ActiveX コントロールのインターフェイスへの`IDispatch`ポインター。

*szPropName*<br/>
設定するプロパティの名前を格納している文字列。

##  <a name="setelementhtml"></a>  CDHtmlDialog::SetElementHtml

HTML 要素`innerHTML`のプロパティを設定します。

```
void SetElementHtml(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementHtml(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>パラメーター

*szElementId*<br/>
HTML 要素の ID。

*bstrText*<br/>
`innerHTML` プロパティの新しい値。

*punkElem*<br/>
HTML 要素のポインター。 `IUnknown`

##  <a name="setelementproperty"></a>CDHtmlDialog:: SetElementProperty

HTML 要素のプロパティを設定します。

```
void SetElementProperty(
    LPCTSTR szElementId,
    DISPID dispId,
    VARIANT* pVar);
```

### <a name="parameters"></a>パラメーター

*szElementId*<br/>
HTML 要素の ID。

*dispId*<br/>
設定するプロパティのディスパッチ ID。

*pVar*<br/>
プロパティの新しい値。

##  <a name="setelementtext"></a>  CDHtmlDialog::SetElementText

HTML 要素`innerText`のプロパティを設定します。

```
void SetElementText(
    LPCTSTR szElementId,
    BSTR bstrText);

void SetElementText(
    IUnknown* punkElem,
    BSTR bstrText);
```

### <a name="parameters"></a>パラメーター

*szElementId*<br/>
HTML 要素の ID。

*bstrText*<br/>
`innerText` プロパティの新しい値。

*punkElem*<br/>
HTML 要素のポインター。 `IUnknown`

##  <a name="setexternaldispatch"></a>  CDHtmlDialog::SetExternalDispatch

ホストの`IDispatch`インターフェイスを設定します。

```
void SetExternalDispatch(IDispatch* pdispExternal);
```

### <a name="parameters"></a>パラメーター

*外部の pdisp*<br/>
新しい`IDispatch`インターフェイス。

##  <a name="sethostflags"></a>  CDHtmlDialog::SetHostFlags

ホストの UI フラグを設定します。

```
void SetHostFlags(DWORD dwFlags);
```

### <a name="parameters"></a>パラメーター

*dwFlags*<br/>
使用可能な値については、Windows SDK の「 [DOCHOSTUIFLAG](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753277\(v=vs.85\)) 」を参照してください。

##  <a name="showcontextmenu"></a>  CDHtmlDialog::ShowContextMenu

コンテキストメニューが表示されようとしているときに呼び出されます。

```
STDMETHOD(ShowContextMenu)(
    DWORD dwID,
    POINT* ppt,
    IUnknown* pcmdtReserved,
    IDispatch* pdispReserved);
```

### <a name="parameters"></a>パラメーター

*dwID*<br/>
Windows SDK の「 *Dwid* in [IDocHostUIHandler:: showcontextmenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\)) 」を参照してください。

*ppt*<br/>
Windows SDKの「 `IDocHostUIHandler::ShowContextMenu` ppt」を参照してください。

*pcmdtReserved*<br/>
Windows SDK の「 `IDocHostUIHandler::ShowContextMenu` *pcmdtreserved 提供*」を参照してください。

*予約済みの pdisp*<br/>
Windows SDK の「」に`IDocHostUIHandler::ShowContextMenu`予約されている*pdispreserved*参照してください。

### <a name="return-value"></a>戻り値

S_FALSE を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))の CDHtmlDialog の実装です。

##  <a name="showui"></a>  CDHtmlDialog::ShowUI

ホストの UI を表示します。

```
STDMETHOD(ShowUI)(
    DWORD dwID,
    IOleInPlaceActiveObject* pActiveObject,
    IOleCommandTarget* pCommandTarget,
    IOleInPlaceFrame* pFrame,
    IOleInPlaceUIWindow* pDoc);
```

### <a name="parameters"></a>パラメーター

*dwID*<br/>
Windows SDK の「 *Dwid* in [IDocHostUIHandler:: ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\)) 」を参照してください。

*pActiveObject*<br/>
Windows SDK の「」 `IDocHostUIHandler::ShowUI`の「 *d pactiveobject* 」を参照してください。

*pCommandTarget*<br/>
Windows SDK の「 *pcommandtarget* `IDocHostUIHandler::ShowUI` 」を参照してください。

*pFrame*<br/>
Windows SDK の「 *pframe* `IDocHostUIHandler::ShowUI` 」を参照してください。

*pDoc*<br/>
Windows SDK の「」 `IDocHostUIHandler::ShowUI`の「 *pdoc* 」を参照してください。

### <a name="return-value"></a>戻り値

S_FALSE を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))の CDHtmlDialog の実装です。

##  <a name="translateaccelerator"></a>  CDHtmlDialog::TranslateAccelerator

メニューアクセラレータキーメッセージを処理するために呼び出されます。

```
STDMETHOD(TranslateAccelerator)(
    LPMSG lpMsg,
    const GUID* pguidCmdGroup,
    DWORD nCmdID);
```

### <a name="parameters"></a>パラメーター

*lpMsg*<br/>
Windows SDK の「 [IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))の*lpmsg* 」を参照してください。

*pguidCmdGroup*<br/>
Windows SDK の「 *pguidcmdgroup* `IDocHostUIHandler::TranslateAccelerator` 」を参照してください。

*nCmdID*<br/>
Windows SDK の「 *ncmdid* in `IDocHostUIHandler::TranslateAccelerator` 」を参照してください。

### <a name="return-value"></a>戻り値

S_FALSE を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))の CDHtmlDialog の実装です。

##  <a name="translateurl"></a>  CDHtmlDialog::TranslateUrl

読み込まれる URL を変更するために呼び出されます。

```
STDMETHOD(TranslateUrl)(
    DWORD dwTranslate,
    OLECHAR* pchURLIn,
    OLECHAR** ppchURLOut);
```

### <a name="parameters"></a>パラメーター

*dwTranslate*<br/>
Windows SDK の「 *Dwtranslate* in [IDocHostUIHandler:: TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\)) 」を参照してください。

*pchURLIn*<br/>
Windows SDKの「 `IDocHostUIHandler::TranslateUrl` pchURLIn」を参照してください。

*ppchURLOut*<br/>
Windows SDK の「 *ppchurlout* `IDocHostUIHandler::TranslateUrl` 」を参照してください。

### <a name="return-value"></a>戻り値

S_FALSE を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))の CDHtmlDialog の実装です。

##  <a name="updateui"></a>  CDHtmlDialog::UpdateUI

コマンドの状態が変更されたことをホストに通知するために呼び出されます。

```
STDMETHOD(UpdateUI)(void);
```

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IDocHostUIHandler:: UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))の CDHtmlDialog の実装です。

## <a name="see-also"></a>関連項目

[MFC サンプル DHtmlExplore](../../overview/visual-cpp-samples.md)<br/>
[DDX_DHtml Helper マクロ](#ddx_dhtml_helper_macros)<br/>
[階層図](../../mfc/hierarchy-chart.md)
