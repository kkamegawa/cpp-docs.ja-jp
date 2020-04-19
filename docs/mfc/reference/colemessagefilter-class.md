---
title: COleMessageFilter クラス
ms.date: 11/04/2016
f1_keywords:
- COleMessageFilter
- AFXOLE/COleMessageFilter
- AFXOLE/COleMessageFilter::COleMessageFilter
- AFXOLE/COleMessageFilter::BeginBusyState
- AFXOLE/COleMessageFilter::EnableBusyDialog
- AFXOLE/COleMessageFilter::EnableNotRespondingDialog
- AFXOLE/COleMessageFilter::EndBusyState
- AFXOLE/COleMessageFilter::OnMessagePending
- AFXOLE/COleMessageFilter::Register
- AFXOLE/COleMessageFilter::Revoke
- AFXOLE/COleMessageFilter::SetBusyReply
- AFXOLE/COleMessageFilter::SetMessagePendingDelay
- AFXOLE/COleMessageFilter::SetRetryReply
helpviewer_keywords:
- COleMessageFilter [MFC], COleMessageFilter
- COleMessageFilter [MFC], BeginBusyState
- COleMessageFilter [MFC], EnableBusyDialog
- COleMessageFilter [MFC], EnableNotRespondingDialog
- COleMessageFilter [MFC], EndBusyState
- COleMessageFilter [MFC], OnMessagePending
- COleMessageFilter [MFC], Register
- COleMessageFilter [MFC], Revoke
- COleMessageFilter [MFC], SetBusyReply
- COleMessageFilter [MFC], SetMessagePendingDelay
- COleMessageFilter [MFC], SetRetryReply
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
ms.openlocfilehash: a06891f9413979895175808e109cc4abb7d75e09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224366"
---
# <a name="colemessagefilter-class"></a>COleMessageFilter クラス

OLE アプリケーション間の相互に要求されるコンカレンシーを管理します。

## <a name="syntax"></a>構文

```
class COleMessageFilter : public CCmdTarget
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|`COleMessageFilter` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleMessageFilter::BeginBusyState](#beginbusystate)|ビジー状態で、アプリケーションを配置します。|
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|有効にし、呼び出し先のアプリケーションがビジー状態のときに表示されるダイアログ ボックスを無効にします。|
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|有効にし、呼び出し先のアプリケーションが応答していないときに表示されるダイアログ ボックスを無効にします。|
|[COleMessageFilter::EndBusyState](#endbusystate)|アプリケーションのビジー状態を終了します。|
|[COleMessageFilter::OnMessagePending](#onmessagepending)|OLE 呼び出しが進行中は、メッセージを処理するためにフレームワークによって呼び出されます。|
|[COleMessageFilter::Register](#register)|OLE システム Dll をメッセージ フィルターを登録します。|
|[COleMessageFilter::Revoke](#revoke)|OLE システム Dll へのメッセージ フィルターの登録を取り消します。|
|[COleMessageFilter::SetBusyReply](#setbusyreply)|OLE 呼び出しにビジー状態のアプリケーションの応答を決定します。|
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|アプリケーションが OLE 呼び出しへの応答を待機する時間を決定します。|
|[COleMessageFilter::SetRetryReply](#setretryreply)|ビジー状態のアプリケーションへの呼び出し元アプリケーションの応答を決定します。|

## <a name="remarks"></a>Remarks

`COleMessageFilter`クラスは、OLE オートメーション アプリケーションだけでなく、ビジュアル編集サーバーとコンテナー アプリケーションで役立ちます。 呼び出されるサーバー アプリケーションで他のコンテナー アプリケーションからの着信呼び出しがキャンセルされるか、後で再試行するようにアプリケーションを「ビジー」にするこのクラスを使用できます。 このクラスは、呼び出し先のアプリケーションがビジー状態のときに、呼び出し元アプリケーションによって実行されるアクションを決定するも使用できます。

一般的な使用方法は、サーバー アプリケーションを呼び出す[BeginBusyState](#beginbusystate)と[EndBusyState](#endbusystate)危険なため、ドキュメントまたはその他の OLE アクセス可能なオブジェクトを破棄するときになります。 これらの呼び出しが行われた[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)ユーザー インターフェイスの更新中にします。

既定で、`COleMessageFilter`アプリケーションが初期化されるとき、オブジェクトが割り当てられます。 取得できる[AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter)します。

これは、高度なクラスです。頻度の低い、直接使用する必要があります。

詳細については、この記事を参照してください。[サーバー。サーバーを実装する](../../mfc/servers-implementing-a-server.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxole.h

##  <a name="beginbusystate"></a>  COleMessageFilter::BeginBusyState

ビジー状態を開始するには、この関数を呼び出します。

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>Remarks

組み合わせて動作[EndBusyState](#endbusystate)アプリケーションのビジー状態を制御します。 関数は、 [SetBusyReply](#setbusyreply)ビジー状態のときに、アプリケーションを呼び出すことに、アプリケーションの応答を決定します。

`BeginBusyState`と`EndBusyState`呼び出しをインクリメントおよびデクリメント、それぞれ、アプリケーションがビジー状態かどうかを決定するカウンター。 たとえば、2 回の呼び出しに`BeginBusyState`とに 1 回の呼び出し`EndBusyState`ビジー状態の結果をまだします。 呼び出す必要があるビジー状態をキャンセルする`EndBusyState`同じ回数`BeginBusyState`が呼び出されました。

既定では、フレームワークが付属しています、アイドル状態の処理中にビジー状態を入力[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)します。 アプリケーションが ON_COMMANDUPDATEUI 通知を処理中に呼び出しが処理後で、アイドル状態の処理が完了した後。

##  <a name="colemessagefilter"></a>  COleMessageFilter::COleMessageFilter

`COleMessageFilter` オブジェクトを作成します。

```
COleMessageFilter();
```

##  <a name="enablebusydialog"></a>  COleMessageFilter::EnableBusyDialog

有効にし、保留中のメッセージの遅延時間の有効期限が切れるときに表示されるダイアログ ボックスを無効にします (を参照してください[ビジー](#setretryreply)) OLE 呼び出し中にします。

```
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnableBusy*<br/>
「ビジー」ダイアログ ボックスが有効になっているかどうかを指定します。

##  <a name="enablenotrespondingdialog"></a>  COleMessageFilter::EnableNotRespondingDialog

キーボードまたはマウス メッセージが保留中の場合に表示される「応答していない」のダイアログ ボックスを無効にでき、OLE 中の呼び出しと呼び出しがタイムアウトしました。

```
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnableNotResponding*<br/>
「応答していない」のダイアログ ボックスが有効になっているかどうかを指定します。

##  <a name="endbusystate"></a>  COleMessageFilter::EndBusyState

この関数では、ビジー状態を終了します。

```
virtual void EndBusyState();
```

### <a name="remarks"></a>Remarks

組み合わせて動作[BeginBusyState](#beginbusystate)アプリケーションのビジー状態を制御します。 関数は、 [SetBusyReply](#setbusyreply)ビジー状態のときに、アプリケーションを呼び出すことに、アプリケーションの応答を決定します。

`BeginBusyState`と`EndBusyState`呼び出しをインクリメントおよびデクリメント、それぞれ、アプリケーションがビジー状態かどうかを決定するカウンター。 たとえば、2 回の呼び出しに`BeginBusyState`とに 1 回の呼び出し`EndBusyState`ビジー状態の結果をまだします。 呼び出す必要があるビジー状態をキャンセルする`EndBusyState`同じ回数`BeginBusyState`が呼び出されました。

既定では、フレームワークが付属しています、アイドル状態の処理中にビジー状態を入力[CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle)します。 ON_UPDATE_COMMAND_UI 通知の処理には、アプリケーションがあるが、中に、受信呼び出しは、アイドル状態の処理が完了した後に処理されます。

##  <a name="onmessagepending"></a>  COleMessageFilter::OnMessagePending

OLE 呼び出しが進行中は、メッセージを処理するためにフレームワークによって呼び出されます。

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>パラメーター

*pMsg*<br/>
保留中のメッセージへのポインター。

### <a name="return-value"></a>戻り値

正常に完了した場合はゼロ以外、それ以外の場合は 0 です。

### <a name="remarks"></a>Remarks

呼び出し元のアプリケーションは、呼び出しの完了の待機中に、フレームワーク`OnMessagePending`保留中のメッセージへのポインター。 既定では、ウィンドウの更新は長い時間がかかっている呼び出し中に発生することができるように、フレームワークは、WM_PAINT メッセージをディスパッチします。

呼び出しを使用して、メッセージ フィルターを登録する必要があります[登録](#register)前に、アクティブになることができます。

##  <a name="register"></a>  COleMessageFilter::Register

OLE システム Dll をメッセージ フィルターを登録します。

```
BOOL Register();
```

### <a name="return-value"></a>戻り値

正常に完了した場合はゼロ以外、それ以外の場合は 0 です。

### <a name="remarks"></a>Remarks

システム Dll に登録されていないメッセージ フィルターの効果はありません。 通常、アプリケーションの初期化コードは、アプリケーションのメッセージ フィルターを登録します。 呼び出して、プログラムが終了する前に、他のメッセージ フィルターによって、アプリケーション登録を取り消す必要があります[取り消す](#revoke)します。

フレームワークの既定のメッセージ フィルターは自動的に初期化中に登録され、終了時に失効します。

##  <a name="revoke"></a>  COleMessageFilter::Revoke

呼び出しによって実行される前の登録を取り消します[登録](#register)します。

```
void Revoke();
```

### <a name="remarks"></a>Remarks

メッセージ フィルターは、プログラムが終了する前に取り消す必要があります。

作成され、フレームワークによって自動的に登録されている、既定のメッセージ フィルターが自動的に失効します。

##  <a name="setbusyreply"></a>  COleMessageFilter::SetBusyReply

この関数は、アプリケーションの"ビジー状態の応答です。"を設定します。

```
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>パラメーター

*nBusyReply*<br/>
値、 `SERVERCALL` COMPOBJ で定義されている列挙型。H. 次の値のいずれかのことができます。

- SERVERCALL_ISHANDLED アプリケーションでは、呼び出しを受け入れることができますが、特定の呼び出しの処理に失敗する可能性があります。

- SERVERCALL_REJECTED アプリケーションおそらくできなく、呼び出しを処理します。

- SERVERCALL_RETRYLATER アプリケーションは、呼び出しを処理できない状態では一時的にします。

### <a name="remarks"></a>Remarks

[BeginBusyState](#beginbusystate)と[EndBusyState](#endbusystate)関数は、アプリケーションのビジー状態を制御します。

アプリケーションを行ったときの呼び出しでビジー状態`BeginBusyState`の最後の設定によって決定される値で OLE システム Dll からの呼び出しに応答が`SetBusyReply`します。 呼び出し元のアプリケーションでは、このビジー状態の応答を使用して、実行するには、どのようなアクションを調べます。

既定では、ビジー状態の応答は SERVERCALL_RETRYLATER です。 この応答は、できるだけ早く、呼び出しを再試行する呼び出し元のアプリケーションです。

##  <a name="setmessagependingdelay"></a>  COleMessageFilter::SetMessagePendingDelay

呼び出し元のアプリケーションがこれ以上の操作を実行する前に呼び出し先のアプリケーションからの応答を待機する時間を決定します。

```
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>パラメーター

*nTimeout*<br/>
保留中のメッセージの遅延時間のミリ秒数。

### <a name="remarks"></a>Remarks

この関数の動作と連携して[ビジー](#setretryreply)します。

##  <a name="setretryreply"></a>  COleMessageFilter::SetRetryReply

呼び出し先のアプリケーションのビジー状態の応答を受信した場合、呼び出し元アプリケーションの動作を決定します。

```
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>パラメーター

*nRetryReply*<br/>
再試行の間のミリ秒数。

### <a name="remarks"></a>Remarks

呼び出し先のアプリケーションでは、ビジー状態であることを示します、ときに、サーバーがビジー状態で、すぐに再試行するか、指定した時間後に再試行するまで待機する、呼び出し元アプリケーションがあります。 呼び出しをキャンセルすることもできます。

呼び出し元の応答は、関数によって制御される`SetRetryReply`と[SetMessagePendingDelay](#setmessagependingdelay)します。 `SetRetryReply` 呼び出し元のアプリケーションが特定の呼び出しの再試行の間待機する時間を決定します。 `SetMessagePendingDelay` さらにアクションを実行する前に、サーバーからの応答の呼び出し元のアプリケーションでは、待機する時間を決定します。

通常、既定値が許容されると変更する必要はありません。 呼び出しを再試行するために、フレームワークすべて*nretryreply で指定した*呼び出しがまたは保留中のメッセージの遅延時間が経過するまでのミリ秒。 値 0 を*nretryreply で指定した*を指定します、通話のキャンセルの即時再試行、および 1 を指定します。

保留中のメッセージの遅延が有効期限が切れて、OLE「ビジー状態 ダイアログ ボックス」(を参照してください[COleBusyDialog](../../mfc/reference/colebusydialog-class.md)) が表示され、ユーザーをキャンセルするか、呼び出しを再試行できます。 呼び出す[EnableBusyDialog](#enablebusydialog)有効またはこのダイアログ ボックスを無効にします。

キーボードまたはマウス メッセージが保留中の場合、呼び出しと呼び出しの中にタイムアウトしました (保留中のメッセージの遅延時間を超えると)、「応答していない」のダイアログ ボックスが表示されます。 呼び出す[EnableNotRespondingDialog](#enablenotrespondingdialog)有効またはこのダイアログ ボックスを無効にします。 通常の問題」のこの状態は、問題の発生をユーザーを待たを示します。

ダイアログ ボックスを無効にすると、現在「再試行応答」がビジー状態のアプリケーションへの呼び出しに使用されます。

## <a name="see-also"></a>関連項目

[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)
