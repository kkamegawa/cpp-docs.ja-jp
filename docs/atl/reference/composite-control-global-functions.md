---
title: 複合コントロールに関するグローバル関数
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
ms.openlocfilehash: 26d8d004c933e48833047f85727ae6282c4b43d7
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893861"
---
# <a name="composite-control-global-functions"></a>複合コントロールに関するグローバル関数

これらの関数は、ダイアログ ボックスの作成と、作成、ホスト、および ActiveX コントロールのライセンスのサポートを提供します。

> [!IMPORTANT]
>  Windows ランタイムで実行するアプリケーションでは、次の表に示す関数を使用できません。

|||
|-|-|
|[AtlAxDialogBox](#atlaxdialogbox)|ユーザーが用意するダイアログ テンプレートからモーダル ダイアログ ボックスを作成します。 表示されたダイアログ ボックスは、ActiveX コントロールを含めることができます。|
|[AtlAxCreateDialog](#atlaxcreatedialog)|ユーザーが用意するダイアログ テンプレートからモードレス ダイアログ ボックスを作成します。 表示されたダイアログ ボックスは、ActiveX コントロールを含めることができます。|
|[AtlAxCreateControl](#atlaxcreatecontrol)|ActiveX コントロールを作成して初期化し、指定されたウィンドウでホストします。|
|[AtlAxCreateControlEx](#atlaxcreatecontrolex)|ActiveX コントロールを作成、初期化し、指定したウィンドウでホストおよびコントロールからインターフェイス ポインターを (またはポインター) を取得します。|
|[AtlAxCreateControlLic](#atlaxcreatecontrollic)|ライセンスされた ActiveX コントロールを作成して初期化し、指定されたウィンドウでホストします。|
|[AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)|ライセンスされた ActiveX コントロールを作成します、初期化し、指定したウィンドウでホストおよびコントロールからインターフェイス ポインターを (またはポインター) を取得します。|
|[AtlAxAttachControl](#atlaxattachcontrol)|事前に作成されたコントロールを指定されたウィンドウにアタッチします。|
|[AtlAxGetHost](#atlaxgethost)|(ある場合) は、指定したウィンドウのコンテナーへのダイレクト インターフェイス ポインターを取得するために使用のハンドルを指定します。|
|[AtlAxGetControl](#atlaxgetcontrol)|(ある場合) は、指定したウィンドウ、内に含まれるコントロールへのダイレクト インターフェイス ポインターを取得するために使用のハンドルを指定します。|
|[AtlSetChildSite](#atlsetchildsite)|初期化します、`IUnknown`子サイトの。|
|[AtlAxWinInit](#atlaxwininit)|AxWin オブジェクトのホスティング コードを初期化します。|
|[AtlAxWinTerm](#atlaxwinterm)|AxWin オブジェクトのホストのコードは初期化されません。|
|[AtlGetObjectSourceInterface](#atlgetobjectsourceinterface)|オブジェクトの既定のソース インターフェイスに関する情報を返します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlhost.h

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
[in]実行可能ファイルには、ダイアログ ボックスのテンプレートが含まれています。 モジュールのインスタンスを識別します。

*lpTemplateName*<br/>
[in]ダイアログ ボックスのテンプレートを識別します。 このパラメーターは、いずれかのダイアログ ボックスのテンプレートの名前を指定する null で終わる文字列へのポインターまたはダイアログ ボックスのテンプレートのリソース識別子を指定する整数値は。 パラメーターは、リソース識別子を指定する場合の上位ワードはゼロである必要があり、その下位ワードは、識別子を含める必要があります。 使用することができます、[されるときは](/windows/desktop/api/winuser/nf-winuser-makeintresourcea)マクロをこの値を作成します。

*hWndParent*<br/>
[in]ダイアログ ボックスを所有するウィンドウを識別します。

*lpDialogProc*<br/>
[in]ダイアログ ボックス プロシージャへのポインター。 ダイアログ ボックス プロシージャの詳細については、次を参照してください。 [DialogProc](/windows/desktop/api/winuser/nc-winuser-dlgproc)します。

*dwInitParam*<br/>
[in]ダイアログ ボックスに渡す値を指定します、 *lParam* WM_INITDIALOG メッセージのパラメーター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

使用する`AtlAxDialogBox`ActiveX コントロールを含むダイアログ テンプレートで指定として有効な CLSID、APPID、または URL 文字列、*テキスト*のフィールド、**コントロール**ダイアログ リソースの セクションと共に"AtlAxWin80"として、*クラス名*同じセクションの下のフィールド。 以下はどのような有効な**コントロール**セクションのようになります。

```
CONTROL    "{04FE35E9-ADBC-4f1d-83FE-8FA4D1F71C7F}", IDC_TEST,
    "AtlAxWin80", WS_GROUP | WS_TABSTOP, 0, 0, 100, 100
```

リソース スクリプトの編集の詳細については、次を参照してください。[方法。テキスト形式でリソース スクリプト ファイルを開く](../../windows/how-to-open-a-resource-script-file-in-text-format.md)します。 コントロールのリソース定義ステートメントの詳細については、次を参照してください。[共通管理パラメーター](/windows/desktop/menurc/common-control-parameters) Windows SDK の下。SDK Tools。

[全般] ダイアログ ボックスの詳細についてを参照してください[DialogBox](/windows/desktop/api/winuser/nf-winuser-dialogboxa)と[CreateDialogParam](/windows/desktop/api/winuser/nf-winuser-createdialogparama) Windows SDK にします。

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
[in]実行可能ファイルには、ダイアログ ボックスのテンプレートが含まれています。 モジュールのインスタンスを識別します。

*lpTemplateName*<br/>
[in]ダイアログ ボックスのテンプレートを識別します。 このパラメーターは、いずれかのダイアログ ボックスのテンプレートの名前を指定する null で終わる文字列へのポインターまたはダイアログ ボックスのテンプレートのリソース識別子を指定する整数値は。 パラメーターは、リソース識別子を指定する場合の上位ワードはゼロである必要があり、その下位ワードは、識別子を含める必要があります。 使用することができます、[されるときは](/windows/desktop/api/winuser/nf-winuser-makeintresourcea)マクロをこの値を作成します。

*hWndParent*<br/>
[in]ダイアログ ボックスを所有するウィンドウを識別します。

*lpDialogProc*<br/>
[in]ダイアログ ボックス プロシージャへのポインター。 ダイアログ ボックス プロシージャの詳細については、次を参照してください。 [DialogProc](/windows/desktop/api/winuser/nc-winuser-dlgproc)します。

*dwInitParam*<br/>
[in]ダイアログ ボックスに渡す値を指定します、 *lParam* WM_INITDIALOG メッセージのパラメーター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

表示されたダイアログ ボックスは、ActiveX コントロールを含めることができます。

参照してください[:createdialog](/windows/desktop/api/winuser/nf-winuser-createdialoga)と[CreateDialogParam](/windows/desktop/api/winuser/nf-winuser-createdialogparama) Windows SDK にします。

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
コントロールに渡される文字列へのポインター。 次の方法のいずれかで書式設定する必要があります。

- "MSCAL などを ProgID。Calendar.7"

- "{8E27C92B-1264-101C-8A2F-040224009C02}"などの CLSID

- などの URL"<http://www.microsoft.com>"

- A reference to an Active document such as "file://\\\Documents\MyDoc.doc"

- などの HTML のフラグメント"MSHTML:\<HTML >\<本文 > これは、行のテキスト\</BODY >\</HTML >"

   > [!NOTE]
   > "MSHTML:"、MSHTML ストリームとして指定されているように、HTML フラグメントを付ける必要があります。

*hWnd*<br/>
[in]コントロールが接続されているウィンドウへのハンドルします。

*pStream*<br/>
[in]コントロールのプロパティを初期化するために使用されるストリームへのポインター。 NULL にすることができます。

*ppUnkContainer*<br/>
[out]受信するポインターのアドレス、`IUnknown`のコンテナー。 NULL にすることができます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

このグローバル関数は、呼び出すことと同じ結果を[行うに](#atlaxcreatecontrolex)(*lpszName*、 *hWnd*、 *pStream*、NULL、null の場合、NULL, NULL);。

ライセンスされた ActiveX コントロールを作成するを参照してください。[して](#atlaxcreatecontrollic)します。

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
コントロールに渡される文字列へのポインター。 次の方法のいずれかで書式設定する必要があります。

- "MSCAL などを ProgID。Calendar.7"

- "{8E27C92B-1264-101C-8A2F-040224009C02}"などの CLSID

- などの URL"<http://www.microsoft.com>"

- A reference to an Active document such as "file://\\\Documents\MyDoc.doc"

- などの HTML のフラグメント"MSHTML:\<HTML >\<本文 > これは、行のテキスト\</BODY >\</HTML >"

   > [!NOTE]
   > "MSHTML:"、MSHTML ストリームとして指定されているように、HTML フラグメントを付ける必要があります。

*hWnd*<br/>
[in]コントロールが接続されているウィンドウへのハンドルします。

*pStream*<br/>
[in]コントロールのプロパティを初期化するために使用されるストリームへのポインター。 NULL にすることができます。

*ppUnkContainer*<br/>
[out]受信するポインターのアドレス、`IUnknown`のコンテナー。 NULL にすることができます。

*ppUnkControl*<br/>
[out]受け取るポインターのアドレス、`IUnknown`のコントロールを作成します。 NULL にすることができます。

*れて*<br/>
送信のインターフェイスに含まれるオブジェクトのインターフェイスの識別子です。

*punkSink*<br/>
ポインター、`IUnknown`で指定された接続ポイントに接続されているシンク オブジェクトのインターフェイス*れて*に含まれるオブジェクトに含まれるオブジェクトが正常に作成されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

`AtlAxCreateControlEx` ような[して](#atlaxcreatecontrol)が新しく作成されたコントロールへのインターフェイス ポインターを受け取るし、コントロールによって発生したイベントを受信するために、イベント シンクをセットアップすることもできます。

ライセンスされた ActiveX コントロールを作成するを参照してください。 [AtlAxCreateControlLicEx](#atlaxcreatecontrollicex)します。

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
コントロールに渡される文字列へのポインター。 次の方法のいずれかで書式設定する必要があります。

- "MSCAL などを ProgID。Calendar.7"

- "{8E27C92B-1264-101C-8A2F-040224009C02}"などの CLSID

- などの URL"<http://www.microsoft.com>"

- A reference to an Active document such as "file://\\\Documents\MyDoc.doc"

- などの HTML のフラグメント"MSHTML:\<HTML >\<本文 > これは、行のテキスト\</BODY >\</HTML >"

   > [!NOTE]
   > "MSHTML:"、MSHTML ストリームとして指定されているように、HTML フラグメントを付ける必要があります。

*hWnd*<br/>
コントロールが接続されているウィンドウへのハンドルします。

*pStream*<br/>
コントロールのプロパティを初期化するために使用されるストリームへのポインター。 NULL にすることができます。

*ppUnkContainer*<br/>
受信するポインターのアドレス、`IUnknown`のコンテナー。 NULL にすることができます。

*bstrLic*<br/>
コントロールのライセンスを含む BSTR。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="example"></a>例

参照してください[ActiveX コントロール ATL を使用しての AXHost をホストしている](../../atl/hosting-activex-controls-using-atl-axhost.md)を使用する方法の例については`AtlAxCreateControlLic`します。

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
コントロールに渡される文字列へのポインター。 次の方法のいずれかで書式設定する必要があります。

- "MSCAL などを ProgID。Calendar.7"

- "{8E27C92B-1264-101C-8A2F-040224009C02}"などの CLSID

- などの URL"<http://www.microsoft.com>"

- A reference to an Active document such as "file://\\\Documents\MyDoc.doc"

- などの HTML のフラグメント"MSHTML:\<HTML >\<本文 > これは、行のテキスト\</BODY >\</HTML >"

   > [!NOTE]
   > "MSHTML:"、MSHTML ストリームとして指定されているように、HTML フラグメントを付ける必要があります。

*hWnd*<br/>
コントロールが接続されているウィンドウへのハンドルします。

*pStream*<br/>
コントロールのプロパティを初期化するために使用されるストリームへのポインター。 NULL にすることができます。

*ppUnkContainer*<br/>
受信するポインターのアドレス、`IUnknown`のコンテナー。 NULL にすることができます。

*ppUnkControl*<br/>
[out]受け取るポインターのアドレス、`IUnknown`のコントロールを作成します。 NULL にすることができます。

*れて*<br/>
送信のインターフェイスに含まれるオブジェクトのインターフェイスの識別子です。

*punkSink*<br/>
ポインター、`IUnknown`で指定された接続ポイントに接続されているシンク オブジェクトのインターフェイス*れて*に含まれるオブジェクトに含まれるオブジェクトが正常に作成されます。

*bstrLic*<br/>
コントロールのライセンスを含む BSTR。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

`AtlAxCreateControlLicEx` ような[して](#atlaxcreatecontrollic)が新しく作成されたコントロールへのインターフェイス ポインターを受け取るし、コントロールによって発生したイベントを受信するために、イベント シンクをセットアップすることもできます。

### <a name="example"></a>例

参照してください[ActiveX コントロール ATL を使用しての AXHost をホストしている](../../atl/hosting-activex-controls-using-atl-axhost.md)を使用する方法の例については`AtlAxCreateControlLicEx`します。

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
[in]ポインター、`IUnknown`のコントロール。

*hWnd*<br/>
[in]コントロールをホストするウィンドウへのハンドルします。

*ppUnkContainer*<br/>
[out]ポインターへのポインター、`IUnknown`のコンテナー オブジェクト。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

### <a name="remarks"></a>Remarks

使用[行うに](#atlaxcreatecontrolex)と[して](#atlaxcreatecontrol)を同時に作成し、コントロールをアタッチします。

> [!NOTE]
>  アタッチされるコントロール オブジェクトを呼び出す前に正しく初期化する必要があります`AtlAxAttachControl`します。

##  <a name="atlaxgethost"></a>  AtlAxGetHost

ハンドルが与えられた指定のウィンドウに対するコンテナーへのダイレクト インターフェイス ポインターを取得します。

```
ATLAPI AtlAxGetHost(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
[in]コントロールをホストしているウィンドウへのハンドル。

*pp*<br/>
[out]`IUnknown`のコントロールのコンテナー。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="atlaxgetcontrol"></a>  AtlAxGetControl

ハンドルが与えられた指定のウィンドウ内に含まれるコントロールへのダイレクト インターフェイス ポインターを取得します。

```
ATLAPI AtlAxGetControl(HWND h, IUnknown** pp);
```

### <a name="parameters"></a>パラメーター

*h*<br/>
[in]コントロールをホストしているウィンドウへのハンドル。

*pp*<br/>
[out]`IUnknown`のホストされているコントロール。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の 1 つ。

##  <a name="atlsetchildsite"></a>  AtlSetChildSite

子オブジェクトのサイトを設定するには、この関数を呼び出す、`IUnknown`の親オブジェクト。

```
HRESULT AtlSetChildSite(IUnknown* punkChild, IUnknown* punkParent);
```

### <a name="parameters"></a>パラメーター

*punkChild*<br/>
[in]ポインター、`IUnknown`子のインターフェイス。

*punkParent*<br/>
[in]ポインター、`IUnknown`親のインターフェイス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="atlaxwininit"></a>  AtlAxWinInit

この関数は、ホスティング コードを登録することにより、ATL のコントロールを初期化、 **"AtlAxWin80**と **"AtlAxWinLic80"** に加えてカスタム ウィンドウ メッセージのいくつかのウィンドウ クラスします。

```
ATLAPI_(BOOL) AtlAxWinInit();
```

### <a name="return-value"></a>戻り値

コードをホストしているコントロールの初期化が成功した場合、0 以外の場合それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

ATL コントロール ホスト API を使用する前に、この関数を呼び出す必要があります。 この関数への呼び出しの後、 **"AtlAxWin"** への呼び出しでウィンドウ クラスを使用できます[CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa)または[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)」の説明に従って、Windows SDK。

##  <a name="atlaxwinterm"></a>  AtlAxWinTerm

この関数の登録を解除してコードをホストしている、ATL のコントロールの初期化を解除、 **"AtlAxWin80**と **"AtlAxWinLic80"** ウィンドウ クラス。

```
inline BOOL AtlAxWinTerm();
```

### <a name="return-value"></a>戻り値

常に TRUE を返します。

### <a name="remarks"></a>Remarks

この関数を呼び出すだけです[UnregisterClass](/windows/desktop/api/winuser/nf-winuser-unregisterclassa) Windows SDK で説明されているとします。

呼び出した場合に既存のすべてのホスト ウィンドウが破棄された後にクリーンアップするには、この関数を呼び出す[AtlAxWinInit](#atlaxwininit)不要になったホスト ウィンドウを作成する必要があります。 この関数を呼び出さない場合、ウィンドウ クラスは登録解除する自動的にプロセスが終了します。

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
[in]情報が返される対象のオブジェクトへのポインター。

*plibid*<br/>
[out]ソース インターフェイスの定義を含むタイプ ライブラリの LIBID へのポインター。

*piid*<br/>
[out]オブジェクトの既定のソース インターフェイスのインターフェイス ID へのポインター。

*pdwMajor*<br/>
[out]ソース インターフェイスの定義を含むタイプ ライブラリのメジャー バージョン番号へのポインター。

*pdwMinor*<br/>
[out]ソース インターフェイスの定義を含むタイプ ライブラリのマイナー バージョン番号へのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>Remarks

`AtlGetObjectSourceInterface` LIBID と共にと主要な既定ソース インターフェイスのインターフェイス ID およびそのインターフェイスを記述するタイプ ライブラリのマイナー バージョン番号を指定できます。

> [!NOTE]
>  要求された情報を正常に取得するには、この関数によって表されるオブジェクト*punkObj*実装する必要があります`IDispatch`(によって型情報を返すと`IDispatch::GetTypeInfo`) かを実装する必要がありますもplus`IProvideClassInfo2`または`IPersist`します。 ソース インターフェイスの型情報は、の型情報と同じタイプ ライブラリである必要があります`IDispatch`します。

### <a name="example"></a>例

次の例は、イベント シンクのクラスを定義する方法を示します`CEasySink`、テンプレート引数を渡すことのできる数を減らすことができます`IDispEventImpl`最低限にします。 `EasyAdvise` `EasyUnadvise`使用`AtlGetObjectSourceInterface`初期化するために、 [IDispEventImpl](../../atl/reference/idispeventimpl-class.md)メンバーを呼び出す前に[DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise)または[DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise)します。

[!code-cpp[NVC_ATL_Windowing#93](../../atl/codesnippet/cpp/composite-control-global-functions_1.h)]

## <a name="see-also"></a>関連項目

[関数](../../atl/reference/atl-functions.md)<br/>
[複合コントロールに関するマクロ](../../atl/reference/composite-control-macros.md)
