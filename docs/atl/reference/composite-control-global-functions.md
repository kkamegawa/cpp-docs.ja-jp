---
title: 複合コントロールのグローバル関数
ms.date: 11/04/2016
f1_keywords:
- atlhost/ATL::AtlAxDialogBox
- atlhost/ATL::AtlAxCreateDialog
- atlhost/ATL::AtlAxCreateControl
- atlhost/ATL::AtlAxCreateControlEx
- atlhost/ATL::AtlAxCreateControlLic
- atlhost/ATL::AtlAxCreateControlLicEx
- atlhost/ATL::AtlAxAttachControl
- atlhost/ATL::AtlAxGetHost
- atlhost/ATL::AtlAxGetControl
- atlhost/ATL::AtlSetChildSite
- atlhost/ATL::AtlAxWinInit
- atlhost/ATL::AtlAxWinTerm
- atlhost/ATL::AtlGetObjectSourceInterface
helpviewer_keywords:
- composite controls, global functions
ms.assetid: 536884cd-e863-4c7a-ab0a-604dc60a0bbe
ms.openlocfilehash: 525fc01247053a1e2bc993398978cb332262a1a5
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927769"
---
# <a name="composite-control-global-functions"></a>複合コントロールのグローバル関数

これらの関数は、ダイアログボックスを作成し、ActiveX コントロールを作成、ホスト、およびライセンスするためのサポートを提供します。

> [!IMPORTANT]
>  次の表に示す関数は、Windows ランタイムで実行するアプリケーションでは使用できません。

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|ユーザーが用意するダイアログ テンプレートからモーダル ダイアログ ボックスを作成します。 表示されるダイアログボックスには、ActiveX コントロールを含めることができます。|
|[AtlAxCreateDialog](#atlaxcreatedialog)|ユーザーが用意するダイアログ テンプレートからモードレス ダイアログ ボックスを作成します。 表示されるダイアログボックスには、ActiveX コントロールを含めることができます。|
|[AtlAxCreateControl](#atlaxcreatecontrol)|ActiveX コントロールを作成して初期化し、指定されたウィンドウでホストします。|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|ActiveX コントロールを作成して初期化し、指定されたウィンドウでホストし、インターフェイスポインター (またはポインター) をコントロールから取得します。|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|ライセンスされた ActiveX コントロールを作成して初期化し、指定されたウィンドウでホストします。|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|ライセンスされた ActiveX コントロールを作成して初期化し、指定したウィンドウでホストし、インターフェイスポインター (またはポインター) をコントロールから取得します。|
|[AtlAxAttachControl](#atlaxattachcontrol)|事前に作成されたコントロールを指定されたウィンドウにアタッチします。|
|[AtlAxGetHost](#atlaxgethost)|ハンドルを指定して、指定したウィンドウ (存在する場合) のコンテナーへの直接インターフェイスポインターを取得するために使用します。|
|[AtlAxGetControl](#atlaxgetcontrol)|ハンドルを指定して、指定したウィンドウ内に格納されているコントロールへの直接インターフェイスポインター (存在する場合) を取得するために使用します。|
|[AtlSetChildSite](#atlsetchildsite)|子サイト`IUnknown`のを初期化します。|
|[AtlAxWinInit](#atlaxwininit)|AxWin オブジェクトのホストコードを初期化します。|
|[AtlAxWinTerm](#atlaxwinterm)|AxWin オブジェクトのホストコードを初期化前します。|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|オブジェクトの既定のソースインターフェイスに関する情報を返します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlhost. h

##  <a name="atlaxdialogbox"></a>  AtlAxDialogBox

ユーザーが用意するダイアログ テンプレートからモーダル ダイアログ ボックスを作成します。

```
ATLAPI_(int) AtlAxDialogBox(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>パラメーター

*hInstance*<br/>
からダイアログボックステンプレートを含む実行可能ファイルを持つモジュールのインスタンスを識別します。

*lpTemplateName*<br/>
からダイアログボックステンプレートを識別します。 このパラメーターは、ダイアログボックステンプレートの名前を指定する null で終わる文字列へのポインターか、ダイアログボックステンプレートのリソース識別子を指定する整数値です。 パラメーターがリソース識別子を指定する場合、その上位ワードはゼロにする必要があり、その下位ワードには識別子が含まれている必要があります。 [Makeintresource](/windows/win32/api/winuser/nf-winuser-makeintresourcew)マクロを使用して、この値を作成できます。

*hWndParent*<br/>
からダイアログボックスを所有するウィンドウを識別します。

*Lpの Proc*<br/>
からダイアログボックスのプロシージャを指します。 ダイアログボックスの手順の詳細については[、「プロパティ](/windows/win32/api/winuser/nc-winuser-dlgproc)」を参照してください。

*dwInitParam*<br/>
からWM_INITDIALOG メッセージの*lParam*パラメーターのダイアログボックスに渡す値を指定します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

ActiveX コントロール`AtlAxDialogBox`を含むダイアログテンプレートと共にを使用するには、ダイアログリソースの**コントロール**セクションの*テキスト*フィールドとして有効な CLSID、APPID、または URL 文字列を*クラス名*フィールドとして指定します。同じセクションにあります。 有効な**コントロール**セクションは次のようになります。

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

リソーススクリプトの編集の詳細について[は、「方法:リソーススクリプトファイルをテキスト形式](../../windows/how-to-open-a-resource-script-file-in-text-format.md)で開きます。 コントロールのリソース定義ステートメントの詳細については、「Windows SDK の下の[コモンコントロールパラメーター](/windows/win32/menurc/common-control-parameters) 」を参照してください。SDK Tools。

一般的なダイアログボックスの詳細については、Windows SDK の「ダイアログボックスと[Createdialogparam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) 」を[参照して](/windows/win32/api/winuser/nf-winuser-dialogboxw)ください。

##  <a name="atlaxcreatedialog"></a>  AtlAxCreateDialog

ユーザーが用意するダイアログ テンプレートからモードレス ダイアログ ボックスを作成します。

```
ATLAPI_(HWND) AtlAxCreateDialog(
    HINSTANCE hInstance,
    LPCWSTR lpTemplateName,
    HWND hWndParent,
    DLGPROC lpDialogProc,
    LPARAM dwInitParam);
```

### <a name="parameters"></a>パラメーター

*hInstance*<br/>
からダイアログボックステンプレートを含む実行可能ファイルを持つモジュールのインスタンスを識別します。

*lpTemplateName*<br/>
からダイアログボックステンプレートを識別します。 このパラメーターは、ダイアログボックステンプレートの名前を指定する null で終わる文字列へのポインターか、ダイアログボックステンプレートのリソース識別子を指定する整数値です。 パラメーターがリソース識別子を指定する場合、その上位ワードはゼロにする必要があり、その下位ワードには識別子が含まれている必要があります。 [Makeintresource](/windows/win32/api/winuser/nf-winuser-makeintresourcew)マクロを使用して、この値を作成できます。

*hWndParent*<br/>
からダイアログボックスを所有するウィンドウを識別します。

*Lpの Proc*<br/>
からダイアログボックスのプロシージャを指します。 ダイアログボックスの手順の詳細については[、「プロパティ](/windows/win32/api/winuser/nc-winuser-dlgproc)」を参照してください。

*dwInitParam*<br/>
からWM_INITDIALOG メッセージの*lParam*パラメーターのダイアログボックスに渡す値を指定します。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

表示されるダイアログボックスには、ActiveX コントロールを含めることができます。

Windows SDK の「 [Createdialog](/windows/win32/api/winuser/nf-winuser-createdialogw) And [Createdialogparam](/windows/win32/api/winuser/nf-winuser-createdialogparamw) 」を参照してください。

##  <a name="atlaxcreatecontrol"></a>  AtlAxCreateControl

ActiveX コントロールを作成して初期化し、指定されたウィンドウでホストします。

```
ATLAPI AtlAxCreateControl(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
コントロールに渡される文字列へのポインター。 次のいずれかの方法で書式設定する必要があります。

- などの ProgID。`"MSCAL.Calendar.7"`

- などの CLSID`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- のような URL`"<https://www.microsoft.com>"`

- などのアクティブなドキュメントへの参照`"file://\\\Documents\MyDoc.doc"`

- HTML のフラグメント (など)`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`は、MSHTML ストリームとして指定されるように、HTML フラグメントの前に配置する必要があります。

*hWnd*<br/>
からコントロールがアタッチされるウィンドウへのハンドル。

*pStream*<br/>
からコントロールのプロパティを初期化するために使用されるストリームへのポインター。 NULL を指定できます。

*ppUnkContainer*<br/>
入出力コンテナーのを`IUnknown`受け取るポインターのアドレス。 NULL を指定できます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

このグローバル関数は、 [AtlAxCreateControlEx](#atlaxcreatecontrolex)(*lpszname*、 *hWnd*、 *PSTREAM*、null、null、null、null) を呼び出した場合と同じ結果を得ます。

ライセンスされた ActiveX コントロールを作成するには、「 [AtlAxCreateControlLic](#atlaxcreatecontrollic)」を参照してください。

##  <a name="atlaxcreatecontrolex"></a>  AtlAxCreateControlEx

ActiveX コントロールを作成して初期化し、指定されたウィンドウでホストします。 新しいコントロールのインターフェイス ポインターとイベント シンクも作成されます。

```
ATLAPI AtlAxCreateControlEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
コントロールに渡される文字列へのポインター。 次のいずれかの方法で書式設定する必要があります。

- などの ProgID。`"MSCAL.Calendar.7"`

- などの CLSID`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- のような URL`"<https://www.microsoft.com>"`

- などのアクティブなドキュメントへの参照`"file://\\\Documents\MyDoc.doc"`

- HTML のフラグメント (など)`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`は、MSHTML ストリームとして指定されるように、HTML フラグメントの前に配置する必要があります。

*hWnd*<br/>
からコントロールがアタッチされるウィンドウへのハンドル。

*pStream*<br/>
からコントロールのプロパティを初期化するために使用されるストリームへのポインター。 NULL を指定できます。

*ppUnkContainer*<br/>
入出力コンテナーのを`IUnknown`受け取るポインターのアドレス。 NULL を指定できます。

*ppUnkControl*<br/>
入出力作成されたコントロールのを`IUnknown`受け取るポインターのアドレス。 NULL を指定できます。

*iidSink*<br/>
含まれているオブジェクトの送信インターフェイスのインターフェイス識別子。

*punkSink*<br/>
含まれている`IUnknown`オブジェクトが正常に作成された後に、含まれているオブジェクトの*iidsink*によって指定されたコネクションポイントに接続されるシンクオブジェクトのインターフェイスへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

`AtlAxCreateControlEx`は[AtlAxCreateControl](#atlaxcreatecontrol)に似ていますが、新しく作成されたコントロールへのインターフェイスポインターを受け取り、コントロールによって発生するイベントを受け取るようにイベントシンクを設定することもできます。

ライセンスされた ActiveX コントロールを作成するには、「 [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)」を参照してください。

##  <a name="atlaxcreatecontrollic"></a>  AtlAxCreateControlLic

ライセンスされた ActiveX コントロールを作成して初期化し、指定されたウィンドウでホストします。

```
ATLAPI AtlAxCreateControlLic(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
コントロールに渡される文字列へのポインター。 次のいずれかの方法で書式設定する必要があります。

- などの ProgID。`"MSCAL.Calendar.7"`

- などの CLSID`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- のような URL`"<https://www.microsoft.com>"`

- などのアクティブなドキュメントへの参照`"file://\\\Documents\MyDoc.doc"`

- HTML のフラグメント (など)`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`は、MSHTML ストリームとして指定されるように、HTML フラグメントの前に配置する必要があります。

*hWnd*<br/>
コントロールがアタッチされるウィンドウへのハンドル。

*pStream*<br/>
コントロールのプロパティを初期化するために使用されるストリームへのポインター。 NULL を指定できます。

*ppUnkContainer*<br/>
コンテナーのを`IUnknown`受け取るポインターのアドレス。 NULL を指定できます。

*bstrLic*<br/>
コントロールのライセンスを格納している BSTR。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="example"></a>例

の使用`AtlAxCreateControlLic`例については、「 [ATL AXHost を使用した ActiveX コントロールのホスト](../../atl/hosting-activex-controls-using-atl-axhost.md)」を参照してください。

##  <a name="atlaxcreatecontrollicex"></a>  AtlAxCreateControlLicEx

ライセンスされた ActiveX コントロールを作成して初期化し、指定されたウィンドウでホストします。 新しいコントロールのインターフェイス ポインターとイベント シンクも作成されます。

```
ATLAPI AtlAxCreateControlLicEx(
    LPCOLESTR lpszName,
    HWND hWnd,
    IStream* pStream,
    IUnknown** ppUnkContainer,
    IUnknown** ppUnkControl,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLic = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
コントロールに渡される文字列へのポインター。 次のいずれかの方法で書式設定する必要があります。

- などの ProgID。`"MSCAL.Calendar.7"`

- などの CLSID`"{8E27C92B-1264-101C-8A2F-040224009C02}"`

- のような URL`"<https://www.microsoft.com>"`

- などのアクティブなドキュメントへの参照`"file://\\\Documents\MyDoc.doc"`

- HTML のフラグメント (など)`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"`

   > [!NOTE]
   > `"MSHTML:"`は、MSHTML ストリームとして指定されるように、HTML フラグメントの前に配置する必要があります。

*hWnd*<br/>
コントロールがアタッチされるウィンドウへのハンドル。

*pStream*<br/>
コントロールのプロパティを初期化するために使用されるストリームへのポインター。 NULL を指定できます。

*ppUnkContainer*<br/>
コンテナーのを`IUnknown`受け取るポインターのアドレス。 NULL を指定できます。

*ppUnkControl*<br/>
入出力作成されたコントロールのを`IUnknown`受け取るポインターのアドレス。 NULL を指定できます。

*iidSink*<br/>
含まれているオブジェクトの送信インターフェイスのインターフェイス識別子。

*punkSink*<br/>
含まれている`IUnknown`オブジェクトが正常に作成された後に、含まれているオブジェクトの*iidsink*によって指定されたコネクションポイントに接続されるシンクオブジェクトのインターフェイスへのポインター。

*bstrLic*<br/>
コントロールのライセンスを格納している BSTR。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

`AtlAxCreateControlLicEx`は[AtlAxCreateControlLic](#atlaxcreatecontrollic)に似ていますが、新しく作成されたコントロールへのインターフェイスポインターを受け取り、コントロールによって発生するイベントを受け取るようにイベントシンクを設定することもできます。

### <a name="example"></a>例

の使用`AtlAxCreateControlLicEx`例については、「 [ATL AXHost を使用した ActiveX コントロールのホスト](../../atl/hosting-activex-controls-using-atl-axhost.md)」を参照してください。

##  <a name="atlaxattachcontrol"></a>  AtlAxAttachControl

事前に作成されたコントロールを指定されたウィンドウにアタッチします。

```
ATLAPI AtlAxAttachControl(
    IUnknown* pControl,
    HWND hWnd,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>パラメーター

*pControl*<br/>
からコントロール`IUnknown`のへのポインター。

*hWnd*<br/>
からコントロールをホストするウィンドウへのハンドル。

*ppUnkContainer*<br/>
入出力コンテナーオブジェクト`IUnknown`のへのポインターへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

コントロールを同時に作成してアタッチするには、 [AtlAxCreateControlEx](#atlaxcreatecontrolex)と[AtlAxCreateControl](#atlaxcreatecontrol)を使用します。

> [!NOTE]
>  を呼び出す`AtlAxAttachControl`前に、アタッチされるコントロールオブジェクトが正しく初期化されている必要があります。

##  <a name="atlaxgethost"></a>  AtlAxGetHost

ハンドルが与えられた指定のウィンドウに対するコンテナーへのダイレクト インターフェイス ポインターを取得します。

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
からコントロールをホストしているウィンドウへのハンドル。

*ページ*<br/>
入出力コントロールのコンテナーの。 `IUnknown`

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="atlaxgetcontrol"></a>  AtlAxGetControl

ハンドルが与えられた指定のウィンドウ内に含まれるコントロールへのダイレクト インターフェイス ポインターを取得します。

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
からコントロールをホストしているウィンドウへのハンドル。

*ページ*<br/>
入出力ホストされているコントロールの。`IUnknown`

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

##  <a name="atlsetchildsite"></a>  AtlSetChildSite

この関数を呼び出して、子オブジェクトのサイトを親オブジェクト`IUnknown`のに設定します。

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>パラメーター

*punkChild*<br/>
から子の`IUnknown`インターフェイスへのポインター。

*punkParent*<br/>
から親の`IUnknown`インターフェイスへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="atlaxwininit"></a>  AtlAxWinInit

この関数は、 **"AtlAxWin80"** と **"AtlAxWinLic80"** の各ウィンドウクラスといくつかのカスタムウィンドウメッセージを登録することによって、ATL のコントロールホスティングコードを初期化します。

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>戻り値

コントロールをホストしているコードが正常に初期化された場合は0以外の場合は。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ATL コントロールをホストする API を使用する前に、この関数を呼び出す必要があります。 この関数を呼び出すと、「Windows SDK」で説明されているように、 **"AtlAxWin"** ウィンドウクラスを[CreateWindow](/windows/win32/api/winuser/nf-winuser-createwindoww)または[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)の呼び出しで使用できます。

##  <a name="atlaxwinterm"></a>  AtlAxWinTerm

この関数は、 **"AtlAxWin80"** および **"AtlAxWinLic80"** ウィンドウクラスの登録を解除することによって、ATL のコントロールホスティングコードを初期化前します。

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>戻り値

常に TRUE を返します。

### <a name="remarks"></a>Remarks

この関数は、Windows SDK で説明されているように、単に[UnregisterClass](/windows/win32/api/winuser/nf-winuser-unregisterclassw)を呼び出します。

[AtlAxWinInit](#atlaxwininit)を呼び出した後、ホストウィンドウを作成する必要がなくなった場合に、既存のすべてのホストウィンドウが破棄された後に、この関数を呼び出してクリーンアップします。 この関数を呼び出さない場合、プロセスの終了時にウィンドウクラスが自動的に登録解除されます。

##  <a name="atlgetobjectsourceinterface"></a>  AtlGetObjectSourceInterface

オブジェクトの既定のソース インターフェイスに関する情報を取得します。

```
ATLAPI AtlGetObjectSourceInterface(
    IUnknown* punkObj,
    GUID* plibid,
    IID* piid,
    unsigned short* pdwMajor,
    unsigned short* pdwMinor);
```

### <a name="parameters"></a>パラメーター

*punkObj*<br/>
から情報が返されるオブジェクトへのポインター。

*plibid*<br/>
入出力ソースインターフェイスの定義を格納しているタイプライブラリの LIBID へのポインター。

*piid*<br/>
入出力オブジェクトの既定のソースインターフェイスのインターフェイス ID へのポインター。

*pdwMajor*<br/>
入出力ソースインターフェイスの定義を格納しているタイプライブラリのメジャーバージョン番号へのポインター。

*pdwMinor*<br/>
入出力ソースインターフェイスの定義を格納しているタイプライブラリのマイナーバージョン番号へのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

`AtlGetObjectSourceInterface`では、既定のソースインターフェイスのインターフェイス ID と共に、そのインターフェイスを記述するタイプライブラリの LIBID とメジャーバージョン番号とマイナーバージョン番号を提供できます。

> [!NOTE]
>  この関数が要求された情報を正常に取得するには、punkObj `IDispatch`によって表されるオブジェクト`IDispatch::GetTypeInfo`がを実装する必要があり`IProvideClassInfo2` 、さらにとの両方を実装する必要があります。`IPersist`. ソースインターフェイスの型情報は、の`IDispatch`型情報と同じタイプライブラリに存在する必要があります。

### <a name="example"></a>例

次の例は、イベントシンククラス`CEasySink`を定義する方法を示しています。これにより、に`IDispEventImpl`渡すことができるテンプレート引数の数を最小限に抑えることができます。 `EasyAdvise`および`EasyUnadvise`を`AtlGetObjectSourceInterface`使用して、 [dispeventadvise](idispeventsimpleimpl-class.md#dispeventadvise)または[dispeventadvise](idispeventsimpleimpl-class.md#dispeventunadvise)を呼び出す前に、 [IDispEventImpl](../../atl/reference/idispeventimpl-class.md)メンバーを初期化します。

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>関連項目

[関数](../../atl/reference/atl-functions.md)<br/>
[複合コントロールに関するマクロ](../../atl/reference/composite-control-macros.md)
