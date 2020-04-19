---
title: COleControlContainer クラス
ms.date: 11/04/2016
f1_keywords:
- COleControlContainer
- AFXOCC/COleControlContainer
- AFXOCC/COleControlContainer::COleControlContainer
- AFXOCC/COleControlContainer::AttachControlSite
- AFXOCC/COleControlContainer::BroadcastAmbientPropertyChange
- AFXOCC/COleControlContainer::CheckDlgButton
- AFXOCC/COleControlContainer::CheckRadioButton
- AFXOCC/COleControlContainer::CreateControl
- AFXOCC/COleControlContainer::CreateOleFont
- AFXOCC/COleControlContainer::FindItem
- AFXOCC/COleControlContainer::FreezeAllEvents
- AFXOCC/COleControlContainer::GetAmbientProp
- AFXOCC/COleControlContainer::GetDlgItem
- AFXOCC/COleControlContainer::GetDlgItemInt
- AFXOCC/COleControlContainer::GetDlgItemText
- AFXOCC/COleControlContainer::HandleSetFocus
- AFXOCC/COleControlContainer::HandleWindowlessMessage
- AFXOCC/COleControlContainer::IsDlgButtonChecked
- AFXOCC/COleControlContainer::OnPaint
- AFXOCC/COleControlContainer::OnUIActivate
- AFXOCC/COleControlContainer::OnUIDeactivate
- AFXOCC/COleControlContainer::ScrollChildren
- AFXOCC/COleControlContainer::SendDlgItemMessage
- AFXOCC/COleControlContainer::SetDlgItemInt
- AFXOCC/COleControlContainer::SetDlgItemText
- AFXOCC/COleControlContainer::m_crBack
- AFXOCC/COleControlContainer::m_crFore
- AFXOCC/COleControlContainer::m_listSitesOrWnds
- AFXOCC/COleControlContainer::m_nWindowlessControls
- AFXOCC/COleControlContainer::m_pOleFont
- AFXOCC/COleControlContainer::m_pSiteCapture
- AFXOCC/COleControlContainer::m_pSiteFocus
- AFXOCC/COleControlContainer::m_pSiteUIActive
- AFXOCC/COleControlContainer::m_pWnd
- AFXOCC/COleControlContainer::m_siteMap
helpviewer_keywords:
- COleControlContainer [MFC], COleControlContainer
- COleControlContainer [MFC], AttachControlSite
- COleControlContainer [MFC], BroadcastAmbientPropertyChange
- COleControlContainer [MFC], CheckDlgButton
- COleControlContainer [MFC], CheckRadioButton
- COleControlContainer [MFC], CreateControl
- COleControlContainer [MFC], CreateOleFont
- COleControlContainer [MFC], FindItem
- COleControlContainer [MFC], FreezeAllEvents
- COleControlContainer [MFC], GetAmbientProp
- COleControlContainer [MFC], GetDlgItem
- COleControlContainer [MFC], GetDlgItemInt
- COleControlContainer [MFC], GetDlgItemText
- COleControlContainer [MFC], HandleSetFocus
- COleControlContainer [MFC], HandleWindowlessMessage
- COleControlContainer [MFC], IsDlgButtonChecked
- COleControlContainer [MFC], OnPaint
- COleControlContainer [MFC], OnUIActivate
- COleControlContainer [MFC], OnUIDeactivate
- COleControlContainer [MFC], ScrollChildren
- COleControlContainer [MFC], SendDlgItemMessage
- COleControlContainer [MFC], SetDlgItemInt
- COleControlContainer [MFC], SetDlgItemText
- COleControlContainer [MFC], m_crBack
- COleControlContainer [MFC], m_crFore
- COleControlContainer [MFC], m_listSitesOrWnds
- COleControlContainer [MFC], m_nWindowlessControls
- COleControlContainer [MFC], m_pOleFont
- COleControlContainer [MFC], m_pSiteCapture
- COleControlContainer [MFC], m_pSiteFocus
- COleControlContainer [MFC], m_pSiteUIActive
- COleControlContainer [MFC], m_pWnd
- COleControlContainer [MFC], m_siteMap
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
ms.openlocfilehash: 3aa2515b1731eafcb5e3bcfa22a56ebbc1cdfdfb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504326"
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer クラス

ActiveX コントロールのコントロール コンテナーとして機能します。

## <a name="syntax"></a>構文

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|`COleControlContainer` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleControlContainer:: AttachControlSite](#attachcontrolsite)|コンテナーによってホストされるコントロールサイトを作成します。|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|アンビエントプロパティが変更されたことを、すべてのホストコントロールに通知します。|
|[COleControlContainer:: CheckDlgButton](#checkdlgbutton)|指定されたボタンコントロールを変更します。|
|[COleControlContainer:: CheckRadioButton](#checkradiobutton)|グループの指定したラジオボタンを選択します。|
|[COleControlContainer::CreateControl](#createcontrol)|ホストされている ActiveX コントロールを作成します。|
|[COleControlContainer:: CreateOleFont](#createolefont)|OLE フォントを作成します。|
|[COleControlContainer:: FindItem](#finditem)|指定したコントロールのカスタムサイトを返します。|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|コントロールサイトがイベントを受け入れるかどうかを判断します。|
|[COleControlContainer::GetAmbientProp](#getambientprop)|指定されたアンビエントプロパティを取得します。|
|[COleControlContainer:: GetDlgItem](#getdlgitem)|指定されたダイアログコントロールを取得します。|
|[COleControlContainer:: GetDlgItemInt](#getdlgitemint)|指定したダイアログコントロールの値を取得します。|
|[COleControlContainer:: GetDlgItemText](#getdlgitemtext)|指定したダイアログコントロールのキャプションを取得します。|
|[COleControlContainer:: HandleSetFocus](#handlesetfocus)|コンテナーが WM_SETFOCUS メッセージを処理するかどうかを決定します。|
|[COleControlContainer:: Handlewindow メッセージ](#handlewindowlessmessage)|ウィンドウなしのコントロールに送信されたメッセージを処理します。|
|[COleControlContainer:: IsDlgButtonChecked](#isdlgbuttonchecked)|指定したボタンの状態を確認します。|
|[COleControlContainer:: OnPaint](#onpaint)|コンテナーの一部を再描画するために呼び出されます。|
|[COleControlContainer:: OnUIActivate](#onuiactivate)|コントロールが埋め込み先でアクティブになるときに呼び出されます。|
|[COleControlContainer:: Onuide アクティブ化](#onuideactivate)|コントロールが非アクティブになるときに呼び出されます。|
|[COleControlContainer:: ScrollChildren](#scrollchildren)|スクロールメッセージが子ウィンドウから受信されたときにフレームワークによって呼び出されます。|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|指定されたコントロールにメッセージを送信します。|
|[COleControlContainer:: SetDlgItemInt](#setdlgitemint)|指定したコントロールの値を設定します。|
|[COleControlContainer:: SetDlgItemText](#setdlgitemtext)|指定したコントロールのテキストを設定します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|コンテナーの背景色。|
|[COleControlContainer::m_crFore](#m_crfore)|コンテナーの前景色。|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|サポートされているコントロールサイトの一覧。|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|ホストされているウィンドウなしコントロールの数。|
|[COleControlContainer::m_pOleFont](#m_polefont)|カスタムコントロールサイトの OLE フォントへのポインター。|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|キャプチャコントロールサイトへのポインター。|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|現在入力フォーカスがあるコントロールへのポインター。|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|現在埋め込み先としてアクティブ化されているコントロールへのポインター。|
|[COleControlContainer::m_pWnd](#m_pwnd)|コントロールコンテナーを実装しているウィンドウへのポインター。|
|[COleControlContainer::m_siteMap](#m_sitemap)|サイトマップ。|

## <a name="remarks"></a>Remarks

これを行うには、1つ以上の ActiveX コントロールサイト (によっ`COleControlSite`て実装される) をサポートします。 `COleControlContainer`[IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe)インターフェイスと[IOleContainer](/windows/win32/api/oleidl/nn-oleidl-iolecontainer)インターフェイスを完全に実装します。これにより、含まれている ActiveX コントロールは、インプレース項目としての条件を満たすことができます。

一般的に、このクラスはと共`COccManager`に使用し`COleControlSite`て、カスタム activex コントロールコンテナーと、1つ以上の activex コントロール用のカスタムサイトを実装します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxocc

##  <a name="attachcontrolsite"></a>COleControlContainer:: AttachControlSite

コントロールサイトを作成してアタッチするために、フレームワークによって呼び出されます。

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
`CWnd` オブジェクトへのポインター。

*nIDC*<br/>
アタッチするコントロールの ID。

### <a name="remarks"></a>Remarks

このプロセスをカスタマイズする場合は、この関数をオーバーライドします。

> [!NOTE]
>  MFC ライブラリに静的にリンクしている場合は、この関数の最初の形式を使用します。 MFC ライブラリに動的にリンクする場合は、2番目の形式を使用します。

##  <a name="broadcastambientpropertychange"></a>  COleControlContainer::BroadcastAmbientPropertyChange

アンビエントプロパティが変更されたことを、すべてのホストコントロールに通知します。

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>パラメーター

*dispid*<br/>
変更するアンビエントプロパティのディスパッチ ID。

### <a name="remarks"></a>Remarks

この関数は、アンビエントプロパティの値が変更されたときにフレームワークによって呼び出されます。 この動作をカスタマイズするには、この関数をオーバーライドします。

##  <a name="checkdlgbutton"></a>COleControlContainer:: CheckDlgButton

ボタンの現在の状態を変更します。

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>パラメーター

*nIDButton*<br/>
変更するボタンの ID。

*n*<br/>
ボタンの状態を指定します。 次のいずれかの値を指定します。

- BST_CHECKED は、ボタンの状態を CHECKED に設定します。

- BST_INDETERMINATE は、ボタンの状態をグレーに設定し、不確定な状態を示します。 この値は、ボタンのスタイルが BS_3STATE または BS_AUTO3STATE の場合にのみ使用します。

- BST_UNCHECKED は、ボタンの状態をオフに設定します。

##  <a name="checkradiobutton"></a>COleControlContainer:: CheckRadioButton

グループ内の指定したラジオボタンを選択し、グループ内の残りのボタンをクリアします。

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>パラメーター

*nIDFirstButton*<br/>
グループ内の最初のラジオボタンの識別子を指定します。

*nIDLastButton*<br/>
グループ内の最後のオプションボタンの識別子を指定します。

*nIDCheckButton*<br/>
チェックするオプションボタンの識別子を指定します。

##  <a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer

`COleControlContainer` オブジェクトを構築します。

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
コントロールコンテナーの親ウィンドウへのポインター。

### <a name="remarks"></a>Remarks

オブジェクトが正常に作成されたら、の呼び出し`AttachControlSite`を使用して、カスタムコントロールサイトを追加します。

##  <a name="createcontrol"></a>COleControlContainer::CreateControl

指定した`COleControlSite`オブジェクトによってホストされる ActiveX コントロールを作成します。

```
BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);

BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);
```

### <a name="parameters"></a>パラメーター

*pWndCtrl*<br/>
コントロールを表すウィンドウオブジェクトへのポインター。

*clsid*<br/>
コントロールの一意のクラス ID。

*lpszWindowName*<br/>
コントロールに表示されるテキストへのポインター。 コントロールのキャプションまたはテキストプロパティ (存在する場合) の値を設定します。 NULL の場合、コントロールのキャプションまたはテキストプロパティは変更されません。

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

*ppNewSite*<br/>
作成されているコントロールをホストする既存のコントロールサイトへのポインター。 既定値は NULL です。これは、新しいコントロールサイトが自動的に作成され、新しいコントロールにアタッチされることを示します。

*ppt*<br/>
コントロールの左上隅`POINT`を格納している構造体へのポインター。 コントロールのサイズは、 *psize*の値によって決まります。 *Ppt*と*psize*の値は、コントロールのサイズと位置を指定するオプションのメソッドです。

*psize*<br/>
コントロールのサイズを`SIZE`格納している構造体へのポインター。 左上隅は、 *ppt*の値によって決まります。 *Ppt*と*psize*の値は、コントロールのサイズと位置を指定するオプションのメソッドです。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

では、Windows *dwStyle*フラグのサブセットのみが`CreateControl`サポートされています。

- WS_VISIBLE 最初に表示されるウィンドウを作成します。 通常のウィンドウのように、コントロールをすぐに表示する場合に必要です。

- WS_DISABLED は、最初は無効になっているウィンドウを作成します。 無効なウィンドウは、ユーザーから入力を受け取ることができません。 コントロールに Enabled プロパティがある場合は、を設定できます。

- WS_BORDER 細い境界線を持つウィンドウを作成します。 コントロールに BorderStyle プロパティがある場合は、を設定できます。

- WS_GROUP は、コントロールのグループの最初のコントロールを指定します。 ユーザーは、方向キーを使用して、グループ内の1つのコントロールから次のコントロールにキーボードフォーカスを変更できます。 最初のコントロールの後に WS_GROUP スタイルを使用して定義されたすべてのコントロールが、同じグループに属しています。 WS_GROUP スタイルの次のコントロールは、グループを終了し、次のグループを開始します。

- WS_TABSTOP ユーザーが TAB キーを押したときにキーボードフォーカスを受け取ることができるコントロールを指定します。 TAB キーを押すと、キーボードフォーカスが WS_TABSTOP スタイルの次のコントロールに変わります。

2番目のオーバーロードを使用して、既定のサイズのコントロールを作成します。

##  <a name="createolefont"></a>COleControlContainer:: CreateOleFont

OLE フォントを作成します。

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>パラメーター

*pFont*<br/>
コントロールコンテナーによって使用されるフォントへのポインター。

##  <a name="finditem"></a>COleControlContainer:: FindItem

指定された項目をホストするカスタムサイトを検索します。

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
検索する項目の識別子。

### <a name="return-value"></a>戻り値

指定した項目のカスタムサイトへのポインター。

##  <a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents

コンテナーが、添付されたコントロールサイトからのイベントを無視するか、それとも受け入れるかを決定します。

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>パラメーター

*bFreeze*<br/>
イベントが処理される場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  コントロールは、コントロールコンテナーによって要求された場合に、イベントの発生を停止する必要はありません。 実行を継続できますが、それ以降のすべてのイベントはコントロールコンテナーによって無視されます。

##  <a name="getambientprop"></a>  COleControlContainer::GetAmbientProp

指定したアンビエントプロパティの値を取得します。

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>パラメーター

*pSite*<br/>
アンビエントプロパティの取得元となるコントロールサイトへのポインター。

*dispid*<br/>
必要なアンビエントプロパティのディスパッチ ID。

*pVarResult*<br/>
アンビエントプロパティの値へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="getdlgitem"></a>COleControlContainer:: GetDlgItem

ダイアログボックスまたはその他のウィンドウで、指定したコントロールまたは子ウィンドウへのポインターを取得します。

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
取得するダイアログ項目の識別子。

*phWnd*<br/>
指定したダイアログ項目のウィンドウオブジェクトのハンドルへのポインター。

### <a name="return-value"></a>戻り値

ダイアログ項目のウィンドウへのポインター。

##  <a name="getdlgitemint"></a>COleControlContainer:: GetDlgItemInt

指定したコントロールの翻訳されたテキストの値を取得します。

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
コントロールの識別子。

*lpTrans*<br/>
関数の成功/失敗の値を受け取るブール型の変数へのポインター (TRUE は成功を示し、FALSE は失敗を示します)。

*bSigned*<br/>
関数で、先頭にあるマイナス記号のテキストを調べ、符号付き整数値が見つかった場合はその値を返すかどうかを指定します。 *Bsigned*パラメーターが TRUE の場合、取得する値が符号付き整数値であることを指定すると、戻り値が**int**型にキャストされます。 エラーの詳細情報を取得するには、 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出します。

### <a name="return-value"></a>戻り値

成功した場合、 *lpTrans*が指す変数は TRUE に設定され、戻り値は制御テキストの変換された値になります。

関数が失敗した場合、 *lpTrans*が指す変数は FALSE に設定され、戻り値はゼロになります。 0は変換可能な値であるため、戻り値が0の場合は、それ自体が失敗を示すわけではないことに注意してください。

*LpTrans*が NULL の場合、関数は成功または失敗に関する情報を返しません。

### <a name="remarks"></a>Remarks

関数は、テキストの先頭にある余分なスペースを削除し、10進数字を変換することによって、取得したテキストを変換します。 関数は、テキストの末尾に到達したとき、または数値以外の文字を検出したときに、変換を停止します。

変換後の値が INT_MAX (符号付き数値の場合) または UINT_MAX (符号なし数値の場合) より大きい場合、この関数は0を返します。

##  <a name="getdlgitemtext"></a>COleControlContainer:: GetDlgItemText

指定されたコントロールのテキストを取得します。

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
コントロールの識別子。

*lpStr*<br/>
コントロールのテキストへのポインター。

*nMaxCount*<br/>
*LpStr*が指すバッファーにコピーする文字列の最大長を文字数で指定します。 文字列の長さが制限を超えた場合、文字列は切り捨てられます。

### <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は、バッファーにコピーされた文字数を指定します。終端の null 文字は含まれません。

関数が失敗した場合は、0 を返します。 エラーの詳細情報を取得するには、 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出します。

##  <a name="handlesetfocus"></a>COleControlContainer:: HandleSetFocus

コンテナーが WM_SETFOCUS メッセージを処理するかどうかを決定します。

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>戻り値

コンテナーが WM_SETFOCUS メッセージを処理する場合は0以外。それ以外の場合は0。

##  <a name="handlewindowlessmessage"></a>COleControlContainer:: Handlewindow メッセージ

ウィンドウなしのコントロールのウィンドウメッセージを処理します。

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>パラメーター

*message*<br/>
Windows によって提供されるウィンドウメッセージの識別子。

*wParam*<br/>
メッセージのパラメーター。Windows によって提供されます。 メッセージ固有の追加情報を指定します。 このパラメーターの内容は、*メッセージ*パラメーターの値によって異なります。

*lParam*<br/>
メッセージのパラメーター。Windows によって提供されます。 メッセージ固有の追加情報を指定します。 このパラメーターの内容は、*メッセージ*パラメーターの値によって異なります。

*plResult*<br/>
Windows の結果コード。 メッセージ処理の結果を指定します。送信されたメッセージによって異なります。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

ウィンドウなしのコントロールメッセージの処理をカスタマイズするには、この関数をオーバーライドします。

##  <a name="isdlgbuttonchecked"></a>COleControlContainer:: IsDlgButtonChecked

指定したボタンの状態を確認します。

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>パラメーター

*nIDButton*<br/>
ボタンコントロールの識別子。

### <a name="return-value"></a>戻り値

BS_AUTOCHECKBOX、BS_AUTORADIOBUTTON、BS_AUTO3STATE、BS_CHECKBOX、BS_RADIOBUTTON、または BS_3STATE style で作成されたボタンからの戻り値。 次のいずれかの値を指定します。

- [BST_CHECKED] ボタンがオンになっています。

- BST_INDETERMINATE ボタンは淡色表示になっており、不確定状態を示します (このボタンには、BS_3STATE または BS_AUTO3STATE スタイルがある場合にのみ適用されます)。

- [BST_UNCHECKED] ボタンがオフになっています。

### <a name="remarks"></a>Remarks

ボタンが3つの状態のコントロールである場合、メンバー関数は、そのボタンが淡色表示されるか、チェックされるか、またはそのどちらでもないかを判断します。

##  <a name="m_crback"></a>COleControlContainer::m_crBack

コンテナーの背景色。

```
COLORREF m_crBack;
```

##  <a name="m_crfore"></a>COleControlContainer::m_crFore

コンテナーの前景色。

```
COLORREF m_crFore;
```

##  <a name="m_listsitesorwnds"></a>COleControlContainer::m_listSitesOrWnds

コンテナーによってホストされているコントロールサイトの一覧。

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

##  <a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls

コントロールコンテナーによってホストされているウィンドウなしのコントロールの数。

```
int m_nWindowlessControls;
```

##  <a name="m_polefont"></a>COleControlContainer::m_pOleFont

カスタムコントロールサイトの OLE フォントへのポインター。

```
LPFONTDISP m_pOleFont;
```

##  <a name="m_psitecapture"></a>COleControlContainer::m_pSiteCapture

キャプチャコントロールサイトへのポインター。

```
COleControlSite* m_pSiteCapture;
```

##  <a name="m_psitefocus"></a>COleControlContainer::m_pSiteFocus

現在入力フォーカスがあるコントロールサイトへのポインター。

```
COleControlSite* m_pSiteFocus;
```

##  <a name="m_psiteuiactive"></a>COleControlContainer::m_pSiteUIActive

埋め込み先でアクティブ化されているコントロールサイトへのポインター。

```
COleControlSite* m_pSiteUIActive;
```

##  <a name="m_pwnd"></a>COleControlContainer::m_pWnd

コンテナーに関連付けられたウィンドウオブジェクトへのポインター。

```
CWnd* m_pWnd;
```

##  <a name="m_sitemap"></a>  COleControlContainer::m_siteMap

サイトマップ。

```
CMapPtrToPtr m_siteMap;
```

##  <a name="onpaint"></a>COleControlContainer:: OnPaint

WM_PAINT 要求を処理するためにフレームワークによって呼び出されます。

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
コンテナーによって使用されるデバイスコンテキストへのポインター。

### <a name="return-value"></a>戻り値

メッセージが処理された場合は0以外の。それ以外の場合は0。

### <a name="remarks"></a>Remarks

描画プロセスをカスタマイズするには、この関数をオーバーライドします。

##  <a name="onuiactivate"></a>COleControlContainer:: OnUIActivate

*Psite*によってポイントされているコントロールサイトがインプレースでアクティブになるときに、フレームワークによって呼び出されます。

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>パラメーター

*pSite*<br/>
埋め込み先としてアクティブにするコントロールサイトへのポインター。

### <a name="remarks"></a>Remarks

インプレースライセンス認証とは、コンテナーのメインメニューを埋め込み先の複合メニューに置き換えることを意味します。

##  <a name="onuideactivate"></a>COleControlContainer:: Onuide アクティブ化

*Psite*によってポイントされているコントロールサイトが非アクティブになるときに、フレームワークによって呼び出されます。

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>パラメーター

*pSite*<br/>
非アクティブ化するコントロールサイトへのポインター。

### <a name="remarks"></a>Remarks

この通知を受信すると、コンテナーはユーザーインターフェイスを再インストールしてフォーカスを取得します。

##  <a name="scrollchildren"></a>COleControlContainer:: ScrollChildren

スクロールメッセージが子ウィンドウから受信されたときにフレームワークによって呼び出されます。

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>パラメーター

*dx*<br/>
X 軸に沿ったスクロールの量 (ピクセル単位)。

*dy*<br/>
Y 軸に沿ったスクロールの量 (ピクセル単位)。

##  <a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage

指定されたコントロールにメッセージを送信します。

```
virtual LRESULT SendDlgItemMessage(
    int nID,
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
メッセージを受信するコントロールの識別子を指定します。

*message*<br/>
送信するメッセージを指定します。

*wParam*<br/>
メッセージ固有の追加情報を指定します。

*lParam*<br/>
メッセージ固有の追加情報を指定します。

##  <a name="setdlgitemint"></a>COleControlContainer:: SetDlgItemInt

ダイアログボックス内のコントロールのテキストを、指定した整数値の文字列形式に設定します。

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
コントロールの識別子。

*nValue*<br/>
表示される整数値。

*bSigned*<br/>
*N 値*パラメーターが符号付きか符号なしかを指定します。 このパラメーターが TRUE の場合、 *n 値*は署名されます。 このパラメーターが TRUE で、 *n 値*が0未満の場合は、文字列の最初の桁の前にマイナス記号が挿入されます。 このパラメーターが FALSE の場合、 *n 値*は unsigned です。

##  <a name="setdlgitemtext"></a>COleControlContainer:: SetDlgItemText

*Lpszstring*に含まれるテキストを使用して、指定したコントロールのテキストを設定します。

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
コントロールの識別子。

*lpszString*<br/>
コントロールのテキストへのポインター。

## <a name="see-also"></a>関連項目

[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite クラス](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager クラス](../../mfc/reference/coccmanager-class.md)
