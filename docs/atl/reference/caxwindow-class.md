---
title: CAxWindow クラス
ms.date: 11/04/2016
f1_keywords:
- CAxWindow
- ATLWIN/ATL::CAxWindow
- ATLWIN/ATL::AttachControl
- ATLWIN/ATL::CreateControl
- ATLWIN/ATL::CreateControlEx
- ATLWIN/ATL::GetWndClassName
- ATLWIN/ATL::QueryControl
- ATLWIN/ATL::QueryHost
- ATLWIN/ATL::SetExternalDispatch
- ATLWIN/ATL::SetExternalUIHandler
helpviewer_keywords:
- CAxWindow class
- ATL, hosting ActiveX controls
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
ms.openlocfilehash: 6f5c178090a970906209e41da9298be61a61c639
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864744"
---
# <a name="caxwindow-class"></a>CAxWindow クラス

このクラスには、ActiveX コントロールをホストしているウィンドウを操作するためのメソッドが用意されています。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CAxWindow : public CWindow
```

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[AttachControl](#attachcontrol)|既存の ActiveX コントロールを `CAxWindow` オブジェクトにアタッチします。|
|[CAxWindow](#caxwindow)|`CAxWindow` オブジェクトを構築します。|
|[CreateControl](#createcontrol)|ActiveX コントロールを作成して初期化し、[`CAxWindow`] ウィンドウでホストします。|
|[CreateControlEx](#createcontrolex)|ActiveX コントロールを作成し、コントロールからインターフェイスポインター (またはポインター) を取得します。|
|[GetWndClassName](#getwndclassname)|雑音`CAxWindow` オブジェクトの定義済みのクラス名を取得します。|
|[QueryControl](#querycontrol)|ホストされている ActiveX コントロールの `IUnknown` を取得します。|
|[QueryHost](#queryhost)|`CAxWindow` オブジェクトの `IUnknown` ポインターを取得します。|
|[SetExternalDispatch](#setexternaldispatch)|`CAxWindow` オブジェクトによって使用される外部ディスパッチインターフェイスを設定します。|
|[SetExternalUIHandler](#setexternaluihandler)|`CAxWindow` オブジェクトによって使用される外部 `IDocHostUIHandler` インターフェイスを設定します。|

### <a name="operators"></a>オペレーター

|||
|-|-|
|[operator =](#operator_eq)|既存の `CAxWindow` オブジェクトに HWND を割り当てます。|

## <a name="remarks"></a>解説

このクラスには、ActiveX コントロールをホストするウィンドウを操作するためのメソッドが用意されています。 ホスティングは、`CAxWindow`によってラップされる " **AtlAxWin80"** によって提供されます。

クラス `CAxWindow` は、`CAxWindowT` クラスの特殊化として実装されます。 この特殊化は次のように宣言されます。

`typedef CAxWindowT<CWindow> CAxWindow;`

基底クラスを変更する必要がある場合は、`CAxWindowT` を使用し、テンプレート引数として新しい基底クラスを指定できます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin. h

##  <a name="attachcontrol"></a>CAxWindow:: AttachControl

新しいホストオブジェクトがまだ存在しない場合は作成し、指定したコントロールをホストにアタッチします。

```
HRESULT AttachControl(
    IUnknown* pControl,
    IUnknown** ppUnkContainer);
```

### <a name="parameters"></a>パラメーター

*pControl*<br/>
からコントロールの `IUnknown` へのポインター。

*ppUnkContainer*<br/>
入出力ホスト (`AxWin` オブジェクト) の `IUnknown` へのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>解説

`AttachControl`を呼び出す前に、アタッチされるコントロールオブジェクトが正しく初期化されている必要があります。

##  <a name="caxwindow"></a>CAxWindow::CAxWindow

既存のウィンドウオブジェクトハンドルを使用して `CAxWindow` オブジェクトを構築します。

```
CAxWindow(HWND hWnd = NULL);
```

### <a name="parameters"></a>パラメーター

*hWnd*<br/>
既存のウィンドウオブジェクトを表すハンドル。

##  <a name="createcontrol"></a>CAxWindow::CreateControl

ActiveX コントロールを作成して初期化し、指定されたウィンドウでホストします。

```
HRESULT CreateControl(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);

HRESULT CreateControl(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
コントロールを作成する文字列へのポインター。 次のいずれかの方法で書式設定する必要があります。

- `"MSCAL.Calendar.7"` などの ProgID

- `"{8E27C92B-1264-101C-8A2F-040224009C02}"` などの CLSID

- URL (`"<https://www.microsoft.com>"` など)

- `"file://\\\Documents\MyDoc.doc"` などのアクティブなドキュメントへの参照

- HTML のフラグメント (`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"` など)

   > [!NOTE]
   > `"MSHTML:"` は、MSHTML ストリームとして指定されるように、HTML フラグメントの前に記述する必要があります。 Windows Mobile プラットフォームでは、ProgID と CLSID のみがサポートされています。 CE IE がサポートされている Windows Mobile 以外の Windows CE embedded プラットフォームでは、ProgID、CLSID、URL、active ドキュメントへの参照、HTML のフラグメントを含むすべての型がサポートされます。

*pStream*<br/>
からコントロールのプロパティを初期化するために使用されるストリームへのポインター。 NULL にすることができます。

*ppUnkContainer*<br/>
入出力コンテナーの `IUnknown` を受け取るポインターのアドレス。 NULL にすることができます。

*dwResID*<br/>
HTML リソースのリソース ID。 指定したリソースを使用して、WebBrowser コントロールが作成され、読み込まれます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>解説

このメソッドの2番目のバージョンを使用すると、HTML コントロールが作成され、 *dwResID*によって識別されるリソースにバインドされます。

このメソッドでは、を呼び出した場合と同じ結果が得られます。

[!code-cpp[NVC_ATL_Windowing#42](../../atl/codesnippet/cpp/caxwindow-class_1.cpp)]

ライセンスされた ActiveX コントロールを作成、初期化、およびホストする方法については、「 [CAxWindow2T:: CreateControlLic](../../atl/reference/caxwindow2t-class.md#createcontrollic) 」を参照してください。

### <a name="example"></a>例

`CreateControl`を使用するサンプルについては、「 [ATL AXHost を使用した ActiveX コントロールのホスト](../../atl/hosting-activex-controls-using-atl-axhost.md)」を参照してください。

##  <a name="createcontrolex"></a>CAxWindow::CreateControlEx

ActiveX コントロールを作成して初期化し、指定されたウィンドウでホストします。

```
HRESULT CreateControlEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);

HRESULT CreateControlEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
コントロールを作成する文字列へのポインター。 次のいずれかの方法で書式設定する必要があります。

- `"MSCAL.Calendar.7"` などの ProgID

- `"{8E27C92B-1264-101C-8A2F-040224009C02}"` などの CLSID

- URL (`"<https://www.microsoft.com>"` など)

- `"file://\\\Documents\MyDoc.doc"` などのアクティブなドキュメントへの参照

- HTML のフラグメント (`"MSHTML:\<HTML>\<BODY>This is a line of text\</BODY>\</HTML>"` など)

   > [!NOTE]
   > `"MSHTML:"` は、MSHTML ストリームとして指定されるように、HTML フラグメントの前に記述する必要があります。 Windows Mobile プラットフォームでは、ProgID と CLSID のみがサポートされています。 CE IE がサポートされている Windows Mobile 以外の Windows CE embedded プラットフォームでは、ProgID、CLSID、URL、active ドキュメントへの参照、HTML のフラグメントを含むすべての型がサポートされます。

*pStream*<br/>
からコントロールのプロパティを初期化するために使用されるストリームへのポインター。 NULL にすることができます。

*ppUnkContainer*<br/>
入出力コンテナーの `IUnknown` を受け取るポインターのアドレス。 NULL にすることができます。

*ppUnkControl*<br/>
入出力コントロールの `IUnknown` を受け取るポインターのアドレス。 NULL にすることができます。

*iidSink*<br/>
から含まれているオブジェクトの送信インターフェイスのインターフェイス識別子。 IID_NULL できます。

*punkSink*<br/>
から*Iidsink*によって指定された、格納されているオブジェクトの接続ポイントに接続するシンクオブジェクトの `IUnknown` インターフェイスへのポインター。

*dwResID*<br/>
からHTML リソースのリソース ID。 指定したリソースを使用して、WebBrowser コントロールが作成され、読み込まれます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>解説

このメソッドは[CAxWindow:: CreateControl](#createcontrol)に似ていますが、そのメソッドとは異なり、`CreateControlEx` では、新しく作成されたコントロールへのインターフェイスポインターを受け取り、コントロールによって発生するイベントを受け取るようにイベントシンクを設定することもできます。

ライセンスされた ActiveX コントロールを作成、初期化、およびホストする方法については、「 [CAxWindow2T:: CreateControlLicEx](../../atl/reference/caxwindow2t-class.md#createcontrollicex) 」を参照してください。

### <a name="example"></a>例

`CreateControlEx`を使用するサンプルについては、「 [ATL AXHost を使用した ActiveX コントロールのホスト](../../atl/hosting-activex-controls-using-atl-axhost.md)」を参照してください。

##  <a name="getwndclassname"></a>CAxWindow::GetWndClassName

ウィンドウクラスの名前を取得します。

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>戻り値

Nonlicensed ActiveX コントロールをホストできるウィンドウクラスの名前を格納している文字列へのポインター。

##  <a name="operator_eq"></a>CAxWindow:: operator =

既存の `CAxWindow` オブジェクトに HWND を割り当てます。

```
CAxWindow<TBase>& operator=(HWND hWnd);
```

### <a name="parameters"></a>パラメーター

*hWnd*<br/>
既存のウィンドウを処理するハンドル。

### <a name="return-value"></a>戻り値

現在の `CAxWindow` オブジェクトへの参照を返します。

##  <a name="querycontrol"></a>CAxWindow:: QueryControl

ホストされているコントロールの指定したインターフェイスを取得します。

```
HRESULT QueryControl(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryControl(Q** ppUnk);
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
からコントロールのインターフェイスの IID を指定します。

*ppUnk*<br/>
入出力コントロールのインターフェイスへのポインター。 このメソッドのテンプレートバージョンでは、関連付けられている UUID を持つ型指定されたインターフェイスが渡される限り、参照 ID は必要ありません。

*Q*<br/>
から照会されているインターフェイス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="queryhost"></a>CAxWindow:: QueryHost

ホストの指定されたインターフェイスを返します。

```
HRESULT QueryHost(REFIID iid, void** ppUnk);
template <class  Q>
HRESULT QueryHost(Q** ppUnk);
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
からコントロールのインターフェイスの IID を指定します。

*ppUnk*<br/>
入出力ホスト上のインターフェイスへのポインター。 このメソッドのテンプレートバージョンでは、関連付けられている UUID を持つ型指定されたインターフェイスが渡される限り、参照 ID は必要ありません。

*Q*<br/>
から照会されているインターフェイス。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>解説

ホストのインターフェイスを使用すると、`AxWin`によって実装された、ウィンドウホストコードの基になる機能にアクセスできます。

##  <a name="setexternaldispatch"></a>CAxWindow:: SetExternalDispatch

`CAxWindow` オブジェクトの外部ディスパッチインターフェイスを設定します。

```
HRESULT SetExternalDispatch(IDispatch* pDisp);
```

### <a name="parameters"></a>パラメーター

*pDisp*<br/>
から`IDispatch` インターフェイスへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="setexternaluihandler"></a>CAxWindow:: SetExternalUIHandler

`CAxWindow` オブジェクトの外部[IDocHostUIHandlerDispatch](../../atl/reference/idochostuihandlerdispatch-interface.md)インターフェイスを設定します。

```
HRESULT SetExternalUIHandler(IDocHostUIHandlerDispatch* pUIHandler);
```

### <a name="parameters"></a>パラメーター

*pUIHandler*<br/>
から`IDocHostUIHandlerDispatch` インターフェイスへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>解説

外部 `IDocHostUIHandlerDispatch` インターフェイスは、ホストのサイトに対して `IDocHostUIHandlerDispatch` インターフェイスを照会するコントロールによって使用されます。 WebBrowser コントロールは、これを行う1つのコントロールです。

## <a name="see-also"></a>参照

[ATLCON サンプル](../../overview/visual-cpp-samples.md)<br/>
[CWindow クラス](../../atl/reference/cwindow-class.md)<br/>
[複合コントロールの基本](../../atl/atl-composite-control-fundamentals.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[コントロールコンテインメントに関する FAQ](../../atl/atl-control-containment-faq.md)
