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
ms.openlocfilehash: 4e93f167b9cb28a83c42220fa58b17d5c4845a75
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894290"
---
# <a name="ccmdtarget-class"></a>CCmdTarget クラス

Microsoft Foundation Class ライブラリのメッセージ マップ アーキテクチャの基本クラスです。

## <a name="syntax"></a>構文

```
class CCmdTarget : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CCmdTarget::CCmdTarget](#ccmdtarget)|`CCmdTarget` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CCmdTarget::BeginWaitCursor](#beginwaitcursor)|砂時計カーソル、カーソルを表示します。|
|[CCmdTarget::DoOleVerb](#dooleverb)|実行する OLE 動詞が指定したアクションを発生します。|
|[CCmdTarget::EnableAutomation](#enableautomation)|用の OLE automation により、`CCmdTarget`オブジェクト。|
|[CCmdTarget::EnableConnections](#enableconnections)|コネクション ポイントでイベントの発生からを有効にします。|
|[CCmdTarget::EnableTypeLib](#enabletypelib)|オブジェクトのタイプ ライブラリを有効にします。|
|[CCmdTarget::EndWaitCursor](#endwaitcursor)|以前のカーソルを返します。|
|[CCmdTarget::EnumOleVerbs](#enumoleverbs)|オブジェクトの OLE 動詞を列挙します。|
|[CCmdTarget::FromIDispatch](#fromidispatch)|ポインターを返します、`CCmdTarget`オブジェクトに関連付けられている、`IDispatch`ポインター。|
|[CCmdTarget::GetDispatchIID](#getdispatchiid)|プライマリ ディスパッチ インターフェイス ID を取得します|
|[CCmdTarget::GetIDispatch](#getidispatch)|ポインターを返します、`IDispatch`オブジェクトに関連付けられている、`CCmdTarget`オブジェクト。|
|[CCmdTarget::GetTypeInfoCount](#gettypeinfocount)|オブジェクトを提供する型情報インターフェイスの数を取得します。|
|[CCmdTarget::GetTypeInfoOfGuid](#gettypeinfoofguid)|指定された GUID に対応する型の説明を取得します。|
|[CCmdTarget::GetTypeLib](#gettypelib)|タイプ ライブラリへのポインターを取得します。|
|[CCmdTarget::GetTypeLibCache](#gettypelibcache)|タイプ ライブラリのキャッシュを取得します。|
|[CCmdTarget::IsInvokeAllowed](#isinvokeallowed)|オートメーション メソッドの呼び出しを有効にします。|
|[CCmdTarget::IsResultExpected](#isresultexpected)|オートメーション関数の場合は 0 以外を返します。 には、値を返す必要があります。|
|[CCmdTarget::OnCmdMsg](#oncmdmsg)|ルーティングし、コマンド メッセージをディスパッチします。|
|[CCmdTarget::OnFinalRelease](#onfinalrelease)|最後の OLE 参照が解放された後にクリーンアップされます。|
|[CCmdTarget::RestoreWaitCursor](#restorewaitcursor)|砂時計カーソルを復元します。|

## <a name="remarks"></a>Remarks

メッセージ マップは、それらを処理するために、メンバー関数にコマンドまたはメッセージをルーティングします。 (コマンドは、アクセラレータ キー、コマンド ボタンまたはメニュー項目からのメッセージです)。

キー フレームワーク クラスから派生した`CCmdTarget`含める[CView](../../mfc/reference/cview-class.md)、 [CWinApp](../../mfc/reference/cwinapp-class.md)、 [CDocument](../../mfc/reference/cdocument-class.md)、 [CWnd](../../mfc/reference/cwnd-class.md)、および[CFrameWnd](../../mfc/reference/cframewnd-class.md)します。 メッセージを処理する新しいクラスの場合は、次のいずれかからクラスを派生`CCmdTarget`-クラスを派生します。 クラスを派生させることはほとんどありませんが`CCmdTarget`直接します。

コマンド ターゲットの概要については、`OnCmdMsg`ルーティングを参照してください[コマンド ターゲット](../../mfc/command-targets.md)、[コマンド ルーティング](../../mfc/command-routing.md)、および[のメッセージの割り当て](../../mfc/mapping-messages.md)します。

`CCmdTarget` 砂時計カーソルの表示を処理するメンバー関数が含まれています。 コマンドの実行にかなりの時間を要するときに、砂時計カーソルを表示します。

ディスパッチ マップ、メッセージ マップのような OLE オートメーションを公開するため`IDispatch`機能します。 このインターフェイスを公開すると、(Visual Basic) などの他のアプリケーションは、アプリケーションに呼び出すことができます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CCmdTarget`

## <a name="requirements"></a>要件

**ヘッダー:** afxwin.h

##  <a name="beginwaitcursor"></a>  CCmdTarget::BeginWaitCursor

コマンドの実行にかなりの時間を実行するときに、砂時計として、カーソルを表示するには、この関数を呼び出します。

```
void BeginWaitCursor();
```

### <a name="remarks"></a>Remarks

フレームワークがときなど、ビジー状態であるユーザーを表示するには、この関数を呼び出し、`CDocument`オブジェクトがファイルに保存したり読み込んだりします。

アクション`BeginWaitCursor`常に 1 つのメッセージ ハンドラーの外部で効果的な他のアクションとしてようない`OnSetCursor`カーソルに変更を処理する可能性があります。

呼び出す`EndWaitCursor`を以前のカーソルを復元します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="ccmdtarget"></a>  CCmdTarget::CCmdTarget

`CCmdTarget` オブジェクトを構築します。

```
CCmdTarget();
```

##  <a name="dooleverb"></a>  CCmdTarget::DoOleVerb

実行する OLE 動詞が指定したアクションを発生します。

```
BOOL DoOleVerb(
    LONG iVerb,
    LPMSG lpMsg,
    HWND hWndParent,
    LPCRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*iVerb*<br/>
動詞の数値識別子です。

*lpMsg*<br/>
ポインター、 [MSG](/windows/desktop/api/winuser/ns-winuser-msg) (ダブルクリック) などの動詞を呼び出したイベントを記述する構造体。

*hWndParent*<br/>
オブジェクトを保持しているドキュメント ウィンドウのハンドル。

*lpRect*<br/>
ポインター、 [RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897) 、座標 (ピクセル)、オブジェクト定義を含む構造体の外接する四角形*hwndParent*します。

### <a name="return-value"></a>戻り値

TRUE の場合は成功しましたが、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメンバー関数は、の実装では基本的に[IOleObject::DoVerb](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-doverb)します。 実行可能なアクションによって列挙[CCmdTarget::EnumOleVerbs](#enumoleverbs)します。

##  <a name="enableautomation"></a>  CCmdTarget::EnableAutomation

オブジェクトの OLE オートメーションを有効にするには、この関数を呼び出します。

```
void EnableAutomation();
```

### <a name="remarks"></a>Remarks

この関数は通常、オブジェクトのコンス トラクターから呼び出され、クラスのディスパッチ マップが宣言されている場合にのみ呼び出す必要があります。 Automation の詳細については、記事をご覧ください。[オートメーション クライアント](../../mfc/automation-clients.md)と[オートメーション サーバー](../../mfc/automation-servers.md)します。

##  <a name="enableconnections"></a>  CCmdTarget::EnableConnections

コネクション ポイントでイベントの発生からを有効にします。

```
void EnableConnections();
```

### <a name="remarks"></a>Remarks

接続ポイントを有効にするには、派生クラスのコンス トラクターでこのメンバー関数を呼び出します。

##  <a name="enabletypelib"></a>  CCmdTarget::EnableTypeLib

オブジェクトのタイプ ライブラリを有効にします。

```
void EnableTypeLib();
```

### <a name="remarks"></a>Remarks

このメンバー関数のコンス トラクターを呼び出して、 `CCmdTarget`-派生オブジェクトの種類の情報を提供する場合。

##  <a name="endwaitcursor"></a>  CCmdTarget::EndWaitCursor

呼び出した後、この関数を呼び出し、`BeginWaitCursor`砂時計カーソルから以前のカーソルを返すメンバー関数。

```
void EndWaitCursor();
```

### <a name="remarks"></a>Remarks

砂時計カーソルを呼び出した後、フレームワークはまた、このメンバー関数を呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

##  <a name="enumoleverbs"></a>  CCmdTarget::EnumOleVerbs

オブジェクトの OLE 動詞を列挙します。

```
BOOL EnumOleVerbs(LPENUMOLEVERB* ppenumOleVerb);
```

### <a name="parameters"></a>パラメーター

*ppenumOleVerb*<br/>
ポインターへのポインター、[返します](/windows/desktop/api/oleidl/nn-oleidl-ienumoleverb)インターフェイス。

### <a name="return-value"></a>戻り値

オブジェクトは、少なくとも 1 つの OLE 動詞をサポートしている場合は TRUE。 (この場合\* *ppenumOleVerb*を指す、`IEnumOLEVERB`列挙子インターフェイス)、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメンバー関数は、の実装では基本的に[:enumverbs](/windows/desktop/api/oleidl/nf-oleidl-ioleobject-enumverbs)します。

##  <a name="fromidispatch"></a>  CCmdTarget::FromIDispatch

マップするには、この関数を呼び出し、`IDispatch`ポインターの場合に、クラスのメンバー関数をオートメーションから受信した、`CCmdTarget`のインターフェイスを実装するオブジェクト、`IDispatch`オブジェクト。

```
static CCmdTarget* PASCAL FromIDispatch(LPDISPATCH lpDispatch);
```

### <a name="parameters"></a>パラメーター

*lpDispatch*<br/>
`IDispatch` オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

ポインター、`CCmdTarget`オブジェクトに関連付けられている*lpDispatch*します。 場合、この関数は NULL を返します、`IDispatch`オブジェクトは、Microsoft Foundation Class として認識されません`IDispatch`オブジェクト。

### <a name="remarks"></a>Remarks

この関数の結果は、メンバー関数の呼び出しの逆`GetIDispatch`します。

##  <a name="getdispatchiid"></a>  CCmdTarget::GetDispatchIID

プライマリ ディスパッチ インターフェイス ID を取得します

```
virtual BOOL GetDispatchIID(IID* pIID);
```

### <a name="parameters"></a>パラメーター

*pIID*<br/>
インターフェイス ID へのポインター (、 [GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931))。

### <a name="return-value"></a>戻り値

TRUE の場合は成功しましたが、それ以外の場合は FALSE。 成功した場合、 \* *pIID*プライマリ ディスパッチ インターフェイスの ID に設定されています。

### <a name="remarks"></a>Remarks

派生クラスは、このメンバー関数をオーバーライドする必要があります (上書きされない場合、 `GetDispatchIID` FALSE を返します)。 参照してください[COleControl](../../mfc/reference/colecontrol-class.md)します。

##  <a name="getidispatch"></a>  CCmdTarget::GetIDispatch

取得するには、このメンバー関数を呼び出す、`IDispatch`ポインター オートメーション メソッドからはどちらかが返されます、`IDispatch`ポインターまたは、`IDispatch`ポインターの参照。

```
LPDISPATCH GetIDispatch(BOOL bAddRef);
```

### <a name="parameters"></a>パラメーター

*bAddRef*<br/>
オブジェクトの参照カウントをインクリメントするかどうかを指定します。

### <a name="return-value"></a>戻り値

`IDispatch`オブジェクトに関連付けられたポインター。

### <a name="remarks"></a>Remarks

オブジェクトを呼び出す`EnableAutomation`オートメーションを有効にできるように、コンス トラクターでこの関数の基礎クラスの実装にポインターを返す`IDispatch`を経由して通信するクライアントによって使用される、`IDispatch`インターフェイス。 呼び出しを行う必要はありませんので、ポインターへの参照を追加します自動的にこの関数を呼び出す[iunknown::addref](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref)します。

##  <a name="gettypeinfocount"></a>  CCmdTarget::GetTypeInfoCount

オブジェクトを提供する型情報インターフェイスの数を取得します。

```
virtual UINT GetTypeInfoCount();
```

### <a name="return-value"></a>戻り値

型情報インターフェイスの数。

### <a name="remarks"></a>Remarks

このメンバー関数は基本的に、実装[IDispatch::GetTypeInfoCount](/windows/desktop/api/oaidl/nf-oaidl-idispatch-gettypeinfocount)します。

派生クラスでは、(0 または 1) を提供する型情報インターフェイスの数を返すには、この関数をオーバーライドする必要があります。 上書きされない場合、 `GetTypeInfoCount` 0 を返します。 オーバーライドするには、使用して、 [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)マクロで、実装も`GetTypeLib`と`GetTypeLibCache`。

##  <a name="gettypeinfoofguid"></a>  CCmdTarget::GetTypeInfoOfGuid

指定された GUID に対応する型の説明を取得します。

```
HRESULT GetTypeInfoOfGuid(
    LCID lcid,
    const GUID& guid,
    LPTYPEINFO* ppTypeInfo);
```

### <a name="parameters"></a>パラメーター

*lcid*<br/>
ロケール識別子 ( `LCID`)。

*guid*<br/>
[GUID](https://msdn.microsoft.com/library/windows/desktop/aa373931)の型の説明。

*ppTypeInfo*<br/>
ポインターへのポインター、`ITypeInfo`インターフェイス。

### <a name="return-value"></a>戻り値

成功した場合または呼び出しの失敗を示す HRESULT。 成功した場合、 \* *ppTypeInfo*型情報インターフェイスを指します。

##  <a name="gettypelib"></a>  CCmdTarget::GetTypeLib

タイプ ライブラリへのポインターを取得します。

```
virtual HRESULT GetTypeLib(
    LCID lcid,
    LPTYPELIB* ppTypeLib);
```

### <a name="parameters"></a>パラメーター

*lcid*<br/>
ロケール識別子 (LCID)。

*ppTypeLib*<br/>
ポインターへのポインター、`ITypeLib`インターフェイス。

### <a name="return-value"></a>戻り値

成功した場合または呼び出しの失敗を示す HRESULT。 成功した場合、 \* *ppTypeLib*タイプ ライブラリのインターフェイスを指します。

### <a name="remarks"></a>Remarks

派生クラスは、このメンバー関数をオーバーライドする必要があります (上書きされない場合、 `GetTypeLib` TYPE_E_CANTLOADLIBRARY を返します)。 使用して、 [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)マクロで、実装も`GetTypeInfoCount`と`GetTypeLibCache`します。

##  <a name="gettypelibcache"></a>  CCmdTarget::GetTypeLibCache

タイプ ライブラリのキャッシュを取得します。

```
virtual CTypeLibCache* GetTypeLibCache();
```

### <a name="return-value"></a>戻り値

`CTypeLibCache` オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

派生クラスは、このメンバー関数をオーバーライドする必要があります (上書きされない場合、 `GetTypeLibCache` NULL が返されます)。 使用して、 [IMPLEMENT_OLETYPELIB](../../mfc/reference/type-library-access.md#implement_oletypelib)マクロで、実装も`GetTypeInfoCount`と`GetTypeLib`します。

##  <a name="isinvokeallowed"></a>  CCmdTarget::IsInvokeAllowed

この関数は mfc の`IDispatch::Invoke`場合、指定された automation メソッドを判断する (で識別される*dispid*) 呼び出すことができます。

```
virtual BOOL IsInvokeAllowed(DISPID dispid);
```

### <a name="parameters"></a>パラメーター

*dispid*<br/>
ディスパッチ id。

### <a name="return-value"></a>戻り値

TRUE の場合、メソッドが呼び出された、それ以外の場合は FALSE を指定できます。

### <a name="remarks"></a>Remarks

場合`IsInvokeAllowed`TRUE を返します`Invoke`にメソッドを呼び出します。 それ以外の場合、`Invoke`は失敗すると、E_UNEXPECTED を返します。

派生クラスは、適切な値を返すには、この関数をオーバーライドできます (上書きされない場合、 `IsInvokeAllowed` TRUE を返します)。 具体的にを参照してください[COleControl::IsInvokeAllowed](../../mfc/reference/colecontrol-class.md#isinvokeallowed)します。

##  <a name="isresultexpected"></a>  CCmdTarget::IsResultExpected

使用`IsResultExpected`をクライアントがその automation 関数の呼び出しからの戻り値を求めているかどうかを確認します。

```
BOOL IsResultExpected();
```

### <a name="return-value"></a>戻り値

以外の場合は、automation 関数が値を返す必要があります。それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

OLE インターフェイスは、MFC とクライアントの使用方法や関数の呼び出しの結果を無視するかどうかについての情報を提供し、MFC を使用してこの情報への呼び出しの結果を判定`IsResultExpected`します。 戻り値の生産が時間またはリソースの負荷がの場合は、戻り値を計算する前にこの関数を呼び出すことによって効率を高めることができます。

この関数は、クライアントが呼び出されてから呼び出す場合に、automation 関数をその他のオートメーション機能から有効な戻り値を取得は 1 回だけ、0 を返します。

`IsResultExpected` automation の関数呼び出しが行われていないときに呼び出された場合は、0 以外の値を返します。

##  <a name="oncmdmsg"></a>  CCmdTarget::OnCmdMsg

コマンド メッセージをディスパッチするためのコマンドのユーザー インターフェイス オブジェクトの更新を処理するためにフレームワークによって呼び出されます。

```
virtual BOOL OnCmdMsg(
    UINT nID,
    int nCode,
    void* pExtra,
    AFX_CMDHANDLERINFO* pHandlerInfo);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
コマンド ID が含まれています

*nCode*<br/>
コマンド通知コードを識別します。 参照してください**解説**の値の詳細について*nCode*します。

*pExtra*<br/>
値に従って使用*nCode*します。 参照してください**解説**の詳細については*pExtra*します。

*pHandlerInfo*<br/>
NULL 以外の場合`OnCmdMsg`塗りつぶす、 *pTarget*と*pmf*のメンバー、 *pHandlerInfo*コマンドをディスパッチするのではなく構造体。 通常、このパラメーターは NULL を指定する必要があります。

### <a name="return-value"></a>戻り値

メッセージが処理された場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

これは、framework コマンドのアーキテクチャの実装のメイン ルーチンです。

実行時に、`OnCmdMsg`他のオブジェクトへのコマンドをディスパッチまたはルート クラスを呼び出すことによって、コマンド自体を処理`CCmdTarget::OnCmdMsg`これは実際のメッセージ マップ検索します。 既定のコマンド ルーティングの詳細については、次を参照してください。[メッセージの処理とマップ」](../../mfc/message-handling-and-mapping.md)します。

まれに、フレームワークを拡張するには、このメンバー関数を無効にすることがあります標準コマンド ルーティングします。 参照してください[テクニカル ノート 21](../../mfc/tn021-command-and-message-routing.md)コマンド ルーティングのアーキテクチャの詳細についてはします。

オーバーライドする場合`OnCmdMsg`、適切な値を指定する必要があります*nCode*、コマンドの通知コードと*pExtra*の値に依存する*nCode*. 次の表では、対応する値を示します。

|*nCode*値|*pExtra*値|
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

オブジェクトとの間の最後の OLE 参照がリリースされたときに、フレームワークによって呼び出されます。

```
virtual void OnFinalRelease();
```

### <a name="remarks"></a>Remarks

このような状況に特別な処理を提供するには、この関数をオーバーライドします。 既定の実装は、オブジェクトを削除します。

##  <a name="restorewaitcursor"></a>  CCmdTarget::RestoreWaitCursor

(たとえば、終了後、メッセージ ボックスが開き、時間のかかる操作の途中で終了し)、システムのカーソルが変更された後に適切な砂時計カーソルを復元するには、この関数を呼び出します。

```
void RestoreWaitCursor();
```

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#43](../../mfc/codesnippet/cpp/ccmdtarget-class_1.cpp)]

## <a name="see-also"></a>関連項目

[MFC サンプル ACDUAL](../../visual-cpp-samples.md)<br/>
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
