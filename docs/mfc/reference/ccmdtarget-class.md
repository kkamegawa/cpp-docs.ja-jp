---
title: CCmdTarget クラス
ms.date: 11/04/2016
f1_keywords:
- CCmdTarget
- AFXWIN/CCmdTarget
- AFXWIN/CCmdTarget::CCmdTarget
- AFXWIN/CCmdTarget::BeginWaitCursor
- AFXWIN/CCmdTarget::DoOleVerb
- AFXWIN/CCmdTarget::EnableAutomation
- AFXWIN/CCmdTarget::EnableConnections
- AFXWIN/CCmdTarget::EnableTypeLib
- AFXWIN/CCmdTarget::EndWaitCursor
- AFXWIN/CCmdTarget::EnumOleVerbs
- AFXWIN/CCmdTarget::FromIDispatch
- AFXWIN/CCmdTarget::GetDispatchIID
- AFXWIN/CCmdTarget::GetIDispatch
- AFXWIN/CCmdTarget::GetTypeInfoCount
- AFXWIN/CCmdTarget::GetTypeInfoOfGuid
- AFXWIN/CCmdTarget::GetTypeLib
- AFXWIN/CCmdTarget::GetTypeLibCache
- AFXWIN/CCmdTarget::IsInvokeAllowed
- AFXWIN/CCmdTarget::IsResultExpected
- AFXWIN/CCmdTarget::OnCmdMsg
- AFXWIN/CCmdTarget::OnFinalRelease
- AFXWIN/CCmdTarget::RestoreWaitCursor
helpviewer_keywords:
- CCmdTarget [MFC], CCmdTarget
- CCmdTarget [MFC], BeginWaitCursor
- CCmdTarget [MFC], DoOleVerb
- CCmdTarget [MFC], EnableAutomation
- CCmdTarget [MFC], EnableConnections
- CCmdTarget [MFC], EnableTypeLib
- CCmdTarget [MFC], EndWaitCursor
- CCmdTarget [MFC], EnumOleVerbs
- CCmdTarget [MFC], FromIDispatch
- CCmdTarget [MFC], GetDispatchIID
- CCmdTarget [MFC], GetIDispatch
- CCmdTarget [MFC], GetTypeInfoCount
- CCmdTarget [MFC], GetTypeInfoOfGuid
- CCmdTarget [MFC], GetTypeLib
- CCmdTarget [MFC], GetTypeLibCache
- CCmdTarget [MFC], IsInvokeAllowed
- CCmdTarget [MFC], IsResultExpected
- CCmdTarget [MFC], OnCmdMsg
- CCmdTarget [MFC], OnFinalRelease
- CCmdTarget [MFC], RestoreWaitCursor
ms.assetid: 8883b132-2057-4ce0-a5f2-88979f8f2b13
ms.openlocfilehash: 583b685295bf77910ef134776c1c4fa39baf93ad
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816336"
---
# <a name="ccmdtarget-class"></a>CCmdTarget クラス

Microsoft Foundation Class ライブラリメッセージマップアーキテクチャの基本クラスです。

## <a name="syntax"></a>構文

```
class CCmdTarget : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[CCmdTarget:: CCmdTarget](#ccmdtarget)|`CCmdTarget` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[CCmdTarget:: BeginWaitCursor](#beginwaitcursor)|カーソルを砂時計カーソルとして表示します。|
|[CCmdTarget::D oOleVerb](#dooleverb)|OLE 動詞によって指定されたアクションを実行します。|
|[CCmdTarget:: EnableAutomation](#enableautomation)|`CCmdTarget` オブジェクトの OLE オートメーションを許可します。|
|[CCmdTarget:: EnableConnections](#enableconnections)|コネクションポイントでのイベントの発生を有効にします。|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|オブジェクトのタイプライブラリを有効にします。|
|[CCmdTarget:: EndWaitCursor](#endwaitcursor)|前のカーソルに戻ります。|
|[CCmdTarget:: EnumOleVerbs](#enumoleverbs)|オブジェクトの OLE 動詞を列挙します。|
|[CCmdTarget:: FromIDispatch](#fromidispatch)|`IDispatch` ポインターに関連付けられている `CCmdTarget` オブジェクトへのポインターを返します。|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|プライマリディスパッチインターフェイス ID を取得します。|
|[CCmdTarget:: GetIDispatch](#getidispatch)|`CCmdTarget` オブジェクトに関連付けられている `IDispatch` オブジェクトへのポインターを返します。|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|オブジェクトが提供する型情報インターフェイスの数を取得します。|
|[CCmdTarget:: GetTypeInfoOfGuid](#gettypeinfoofguid)|指定した GUID に対応する型の説明を取得します。|
|[CCmdTarget::GetTypeLib](#gettypelib)|タイプライブラリへのポインターを取得します。|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|タイプライブラリキャッシュを取得します。|
|[CCmdTarget:: IsInvokeAllowed](#isinvokeallowed)|オートメーションメソッドの呼び出しを有効にします。|
|[CCmdTarget:: IsResultExpected 必要です。](#isresultexpected)|オートメーション関数が値を返す必要がある場合は、0以外の値を返します。|
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|コマンドメッセージをルーティングしてディスパッチします。|
|[CCmdTarget:: OnFinalRelease](#onfinalrelease)|最後の OLE 参照がリリースされた後にクリーンアップします。|
|[CCmdTarget:: RestoreWaitCursor](#restorewaitcursor)|砂時計カーソルを復元します。|

## <a name="remarks"></a>コメント

メッセージマップは、コマンドまたはメッセージを、それらを処理するために記述するメンバー関数にルーティングします。 (コマンドは、メニュー項目、コマンドボタン、またはアクセラレータキーからのメッセージです)。

`CCmdTarget` から派生した主なフレームワーククラスには、 [CView](../../mfc/reference/cview-class.md)、 [CWinApp](../../mfc/reference/cwinapp-class.md)、 [CDocument](../../mfc/reference/cdocument-class.md)、 [CWnd](../../mfc/reference/cwnd-class.md)、および[CFrameWnd](../../mfc/reference/cframewnd-class.md)があります。 新しいクラスを使用してメッセージを処理する場合は、これらの `CCmdTarget`派生クラスのいずれかからクラスを派生させます。 `CCmdTarget` から直接クラスを派生させることはめったにありません。

コマンドターゲットと `OnCmdMsg` ルーティングの概要については、「[コマンドターゲット](../../mfc/command-targets.md)」、「[コマンドルーティング](../../mfc/command-routing.md)」、および「[マッピングメッセージ](../../mfc/mapping-messages.md)」を参照してください。

`CCmdTarget` には、砂時計カーソルの表示を処理するメンバー関数が含まれています。 コマンドの実行に顕著な時間間隔がかかると予想される場合は、砂時計カーソルを表示します。

メッセージマップと同様のディスパッチマップは、OLE オートメーション `IDispatch` 機能を公開するために使用されます。 このインターフェイスを公開すると、他のアプリケーション (Visual Basic など) がアプリケーションを呼び出すことができます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>要件

**ヘッダー:** afxwin.h

##  <a name="beginwaitcursor"></a>CCmdTarget:: BeginWaitCursor

この関数を呼び出して、コマンドの実行に時間がかかることが予想されるときに、カーソルを砂時計として表示します。

```
void BeginWaitCursor();
```

### <a name="remarks"></a>コメント

フレームワークは、この関数を呼び出して、ビジー状態であることをユーザーに表示します。たとえば、`CDocument` オブジェクトがファイルに対して読み込みや保存を行う場合です。

`OnSetCursor` 処理などの他のアクションでカーソルが変更される可能性があるため、`BeginWaitCursor` のアクションは、1つのメッセージハンドラーの外部では常に有効とは限りません。

`EndWaitCursor` を呼び出して、前のカーソルを復元します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="ccmdtarget"></a>CCmdTarget:: CCmdTarget

`CCmdTarget` オブジェクトを構築します。

```
CCmdTarget();
```

##  <a name="dooleverb"></a>CCmdTarget::D oOleVerb

OLE 動詞によって指定されたアクションを実行します。

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*iVerb*<br/>
動詞の数値識別子。

*lpMsg*<br/>
動詞を呼び出したイベント (ダブルクリックなど) を記述する[MSG](/windows/win32/api/winuser/ns-winuser-msg)構造体へのポインター。

*hWndParent*<br/>
オブジェクトを保持しているドキュメント ウィンドウのハンドル。

*lpRect*<br/>
*HwndParent*のオブジェクトの外接する四角形を定義する座標 (ピクセル単位) を格納している[RECT](/previous-versions/dd162897\(v=vs.85\))構造体へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>コメント

このメンバー関数は、基本的に[IOleObject::D oVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb)の実装です。 使用可能なアクションは、 [CCmdTarget:: EnumOleVerbs](#enumoleverbs)によって列挙されます。

##  <a name="enableautomation"></a>CCmdTarget:: EnableAutomation

オブジェクトの OLE オートメーションを有効にするには、この関数を呼び出します。

```
void EnableAutomation();
```

### <a name="remarks"></a>コメント

この関数は、通常、オブジェクトのコンストラクターから呼び出されます。この関数は、クラスに対してディスパッチマップが宣言されている場合にのみ呼び出す必要があります。 オートメーションの詳細については、「[オートメーションクライアント](../../mfc/automation-clients.md)と[オートメーションサーバー](../../mfc/automation-servers.md)」を参照してください。

##  <a name="enableconnections"></a>CCmdTarget:: EnableConnections

コネクションポイントでのイベントの発生を有効にします。

```
void EnableConnections();
```

### <a name="remarks"></a>コメント

接続ポイントを有効にするには、派生クラスのコンストラクターでこのメンバー関数を呼び出します。

##  <a name="enabletypelib"></a>  CCmdTarget::EnableTypeLib

オブジェクトのタイプライブラリを有効にします。

```
void EnableTypeLib();
```

### <a name="remarks"></a>コメント

型情報を提供する場合は、`CCmdTarget`派生オブジェクトのコンストラクターでこのメンバー関数を呼び出します。

##  <a name="endwaitcursor"></a>CCmdTarget:: EndWaitCursor

砂時計カーソルから前のカーソルに戻るために `BeginWaitCursor` メンバー関数を呼び出した後に、この関数を呼び出します。

```
void EndWaitCursor();
```

### <a name="remarks"></a>コメント

また、このメンバー関数は、砂時計カーソルを呼び出した後に呼び出されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="enumoleverbs"></a>CCmdTarget:: EnumOleVerbs

オブジェクトの OLE 動詞を列挙します。

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>パラメーター

*ppenumOleVerb*<br/>
[IEnumOLEVERB](/windows/win32/api/oleidl/nn-oleidl-ienumoleverb)インターフェイスへのポインターへのポインター。

### <a name="return-value"></a>戻り値

オブジェクトが少なくとも1つの OLE 動詞 (この場合 \* *ppenumOleVerb*が `IEnumOLEVERB` 列挙子インターフェイスを指す) をサポートしている場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>コメント

このメンバー関数は、基本的に[IOleObject:: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs)の実装です。

##  <a name="fromidispatch"></a>CCmdTarget:: FromIDispatch

クラスのオートメーションメンバー関数から受け取った `IDispatch` ポインターを、`IDispatch` オブジェクトのインターフェイスを実装する `CCmdTarget` オブジェクトにマップするには、この関数を呼び出します。

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>パラメーター

*lpDispatch*<br/>
`IDispatch` オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

*Lpdispatch*に関連付けられている `CCmdTarget` オブジェクトへのポインター。 `IDispatch` オブジェクトが Microsoft Foundation Class `IDispatch` オブジェクトとして認識されない場合、この関数は NULL を返します。

### <a name="remarks"></a>コメント

この関数の結果は `GetIDispatch`メンバー関数の呼び出しの逆になります。

##  <a name="getdispatchiid"></a>  CCmdTarget::GetDispatchIID

プライマリディスパッチインターフェイス ID を取得します。

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>パラメーター

*pIID*<br/>
インターフェイス ID ( [GUID](/previous-versions/cc317743(v%3dmsdn.10))) へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。 成功した場合、\* *pIID*は、プライマリディスパッチインターフェイス ID に設定されます。

### <a name="remarks"></a>コメント

派生クラスは、このメンバー関数をオーバーライドする必要があります (オーバーライドされていない場合、`GetDispatchIID` は FALSE を返します)。 「 [COleControl](../../mfc/reference/colecontrol-class.md)」を参照してください。

##  <a name="getidispatch"></a>CCmdTarget:: GetIDispatch

このメンバー関数を呼び出して、`IDispatch` ポインターを返すか、参照によって `IDispatch` ポインターを取得するオートメーションメソッドから `IDispatch` ポインターを取得します。

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>パラメーター

*bAddRef*<br/>
オブジェクトの参照カウントをインクリメントするかどうかを指定します。

### <a name="return-value"></a>戻り値

オブジェクトに関連付けられている `IDispatch` ポインター。

### <a name="remarks"></a>コメント

コンストラクターで `EnableAutomation` を呼び出すオブジェクトのオートメーションを有効にすると、この関数は `IDispatch` インターフェイスを介して通信するクライアントによって使用される `IDispatch` の Foundation クラスの実装へのポインターを返します。 この関数を呼び出すと、ポインターへの参照が自動的に追加されるため、 [IUnknown:: AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref)を呼び出す必要はありません。

##  <a name="gettypeinfocount"></a>  CCmdTarget::GetTypeInfoCount

オブジェクトが提供する型情報インターフェイスの数を取得します。

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>戻り値

型情報インターフェイスの数。

### <a name="remarks"></a>コメント

このメンバー関数は、基本的に[IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)を実装します。

派生クラスは、指定された型情報インターフェイスの数 (0 または 1) を返すように、この関数をオーバーライドする必要があります。 オーバーライドされていない場合、`GetTypeInfoCount` は0を返します。 をオーバーライドするには、 [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)マクロを使用します。これは `GetTypeLib` と `GetTypeLibCache`も実装します。

##  <a name="gettypeinfoofguid"></a>CCmdTarget:: GetTypeInfoOfGuid

指定した GUID に対応する型の説明を取得します。

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>パラメーター

*lcid*<br/>
ロケール識別子 (`LCID`)。

*guid*<br/>
型の説明の[GUID](/previous-versions/cc317743(v%3dmsdn.10)) 。

*ppTypeInfo*<br/>
`ITypeInfo` インターフェイスへのポインターへのポインター。

### <a name="return-value"></a>戻り値

呼び出しの成功または失敗を示す HRESULT。 成功した場合、\* *ppTypeInfo*は型情報インターフェイスをポイントします。

##  <a name="gettypelib"></a>  CCmdTarget::GetTypeLib

タイプライブラリへのポインターを取得します。

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>パラメーター

*lcid*<br/>
ロケール識別子 (LCID)。

*ppTypeLib*<br/>
`ITypeLib` インターフェイスへのポインターへのポインター。

### <a name="return-value"></a>戻り値

呼び出しの成功または失敗を示す HRESULT。 成功した場合、\* *Pptypelib*はタイプライブラリインターフェイスをポイントします。

### <a name="remarks"></a>コメント

派生クラスは、このメンバー関数をオーバーライドする必要があります (オーバーライドされていない場合、`GetTypeLib` は TYPE_E_CANTLOADLIBRARY を返します)。 [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)マクロを使用します。これは `GetTypeInfoCount` と `GetTypeLibCache`も実装します。

##  <a name="gettypelibcache"></a>  CCmdTarget::GetTypeLibCache

タイプライブラリキャッシュを取得します。

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>戻り値

`CTypeLibCache` オブジェクトへのポインター。

### <a name="remarks"></a>コメント

派生クラスは、このメンバー関数をオーバーライドする必要があります (オーバーライドされていない場合、`GetTypeLibCache` は NULL を返します)。 [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)マクロを使用します。これは `GetTypeInfoCount` と `GetTypeLib`も実装します。

##  <a name="isinvokeallowed"></a>CCmdTarget:: IsInvokeAllowed

この関数は、特定のオートメーションメソッド ( *dispid*によって識別される) を呼び出すことができるかどうかを判断するために、MFC の `IDispatch::Invoke` の実装によって呼び出されます。

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>パラメーター

*dispid*<br/>
ディスパッチ ID。

### <a name="return-value"></a>戻り値

メソッドを呼び出すことができる場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>コメント

`IsInvokeAllowed` が TRUE を返す場合、`Invoke` はメソッドの呼び出しに進みます。それ以外の場合、`Invoke` は失敗し、E_UNEXPECTED が返されます。

派生クラスでは、この関数をオーバーライドして適切な値を返すことができます (オーバーライドされていない場合、`IsInvokeAllowed` は TRUE を返します)。 「特に[COleControl:: IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed)」を参照してください。

##  <a name="isresultexpected"></a>CCmdTarget:: IsResultExpected 必要です。

`IsResultExpected` を使用して、クライアントがオートメーション関数の呼び出しからの戻り値を受け取るかどうかを確認します。

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>戻り値

オートメーション関数が値を返す必要がある場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>コメント

OLE インターフェイスは、クライアントが関数呼び出しの結果を使用するか無視するかについての情報を MFC に提供します。また、MFC では、この情報を使用して `IsResultExpected`の呼び出しの結果を判断します。 戻り値の実稼働が時間やリソースを集中的に使用する場合は、戻り値を計算する前にこの関数を呼び出して効率を上げることができます。

この関数は、クライアントが呼び出したオートメーション関数から有効な戻り値を取得できるように、0を1回だけ返します。

オートメーション関数の呼び出しが進行中でない場合、`IsResultExpected` は0以外の値を返します。

##  <a name="oncmdmsg"></a>  CCmdTarget::OnCmdMsg

コマンドメッセージをルーティングおよびディスパッチし、コマンドユーザーインターフェイスオブジェクトの更新を処理するために、フレームワークによって呼び出されます。

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
コマンド ID を格納します。

*nCode*<br/>
コマンド通知コードを識別します。 *NCode*の値の詳細については、「**解説**」を参照してください。

*pExtra*<br/>
*NCode*の値に従って使用されます。 *Pextra*の詳細については、「**解説**」を参照してください。

*pHandlerInfo*<br/>
NULL でない場合、は、コマンドをディスパッチするのではなく `OnCmdMsg`、 *Ptarget*と*pmf*のメンバーに*pHandlerInfo*構造体の値を入力します。 通常、このパラメーターは NULL にする必要があります。

### <a name="return-value"></a>戻り値

メッセージが処理される場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>コメント

これは、フレームワークのコマンドアーキテクチャの主要な実装ルーチンです。

実行時に、`OnCmdMsg` は他のオブジェクトにコマンドをディスパッチするか、実際のメッセージマップの参照を行うルートクラス `CCmdTarget::OnCmdMsg`を呼び出すことによってコマンド自体を処理します。 既定のコマンドルーティングの詳細については、「[メッセージの処理とマッピングに関するトピック](../../mfc/message-handling-and-mapping.md)」を参照してください。

まれに、フレームワークの標準のコマンドルーティングを拡張するためにこのメンバー関数をオーバーライドすることが必要になる場合があります。 コマンドルーティングアーキテクチャの詳細については、「[テクニカルノート 21](../../mfc/tn021-command-and-message-routing.md) 」を参照してください。

`OnCmdMsg`をオーバーライドする場合は、 *nCode*の値に応じて、 *nCode*、コマンド通知コード、および*pextra*に適切な値を指定する必要があります。 次の表に、対応する値を示します。

|*nCode*値|*Pextra*値|
|-------------------|--------------------|
|CN_COMMAND|[CCmdUI](../../mfc/reference/ccmdui-class.md)\*|
|CN_EVENT|AFX_EVENT\*|
|CN_UPDATE_COMMAND_UI|CCmdUI\*|
|CN_OLECOMMAND|[COleCmdUI](../../mfc/reference/colecmdui-class.md)\*|
|CN_OLE_UNREGISTER|NULL|

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#44](../../mfc/codesnippet/cpp/ccmdtarget-class_2.cpp)]

[!code-cpp[NVC_MFCDocView#45](../../mfc/codesnippet/cpp/ccmdtarget-class_3.cpp)]

##  <a name="onfinalrelease"></a>  CCmdTarget::OnFinalRelease

オブジェクトへの最後の OLE 参照が解放されたときにフレームワークによって呼び出されます。

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>コメント

このような状況に対して特別な処理を行うには、この関数をオーバーライドします。 既定の実装では、オブジェクトが削除されます。

##  <a name="restorewaitcursor"></a>  CCmdTarget::RestoreWaitCursor

システムカーソルが変更された後、適切な砂時計カーソルを復元するには、この関数を呼び出します (たとえば、長い操作の途中でメッセージボックスを開いて閉じた後など)。

```
void RestoreWaitCursor();
```

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>参照

[MFC サンプル ACDUAL](../../overview/visual-cpp-samples.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CCmdUI クラス](../../mfc/reference/ccmdui-class.md)<br/>
[CDocument クラス](../../mfc/reference/cdocument-class.md)<br/>
[CDocTemplate クラス](../../mfc/reference/cdoctemplate-class.md)<br/>
[CWinApp クラス](../../mfc/reference/cwinapp-class.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[CView クラス](../../mfc/reference/cview-class.md)<br/>
[CFrameWnd クラス](../../mfc/reference/cframewnd-class.md)<br/>
[COleDispatchDriver クラス](../../mfc/reference/coledispatchdriver-class.md)
