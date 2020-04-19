---
title: CAtlServiceModuleT クラス
ms.date: 05/06/2019
f1_keywords:
- CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::CAtlServiceModuleT
- ATLBASE/ATL::CAtlServiceModuleT::Handler
- ATLBASE/ATL::CAtlServiceModuleT::InitializeSecurity
- ATLBASE/ATL::CAtlServiceModuleT::Install
- ATLBASE/ATL::CAtlServiceModuleT::IsInstalled
- ATLBASE/ATL::CAtlServiceModuleT::LogEvent
- ATLBASE/ATL::CAtlServiceModuleT::OnContinue
- ATLBASE/ATL::CAtlServiceModuleT::OnInterrogate
- ATLBASE/ATL::CAtlServiceModuleT::OnPause
- ATLBASE/ATL::CAtlServiceModuleT::OnShutdown
- ATLBASE/ATL::CAtlServiceModuleT::OnStop
- ATLBASE/ATL::CAtlServiceModuleT::OnUnknownRequest
- ATLBASE/ATL::CAtlServiceModuleT::ParseCommandLine
- ATLBASE/ATL::CAtlServiceModuleT::PreMessageLoop
- ATLBASE/ATL::CAtlServiceModuleT::RegisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::Run
- ATLBASE/ATL::CAtlServiceModuleT::ServiceMain
- ATLBASE/ATL::CAtlServiceModuleT::SetServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::Start
- ATLBASE/ATL::CAtlServiceModuleT::Uninstall
- ATLBASE/ATL::CAtlServiceModuleT::Unlock
- ATLBASE/ATL::CAtlServiceModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlServiceModuleT::WinMain
- ATLBASE/ATL::CAtlServiceModuleT::m_bService
- ATLBASE/ATL::CAtlServiceModuleT::m_dwThreadID
- ATLBASE/ATL::CAtlServiceModuleT::m_hServiceStatus
- ATLBASE/ATL::CAtlServiceModuleT::m_status
- ATLBASE/ATL::CAtlServiceModuleT::m_szServiceName
helpviewer_keywords:
- CAtlServiceModuleT class
ms.assetid: 8fc753ce-4a50-402b-9b4a-0a4ce5dd496c
ms.openlocfilehash: 2854d0902700b268383eca094bed35843ea73272
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497738"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT クラス

このクラスは、サービスを実装します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
から`CAtlServiceModuleT`派生したクラス。

*nServiceNameID*<br/>
サービスのリソース識別子。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAtlServiceModuleT::CAtlServiceModuleT](#catlservicemodulet)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAtlServiceModuleT:: Handler](#handler)|サービスのハンドラールーチン。|
|[CAtlServiceModuleT:: InitializeSecurity](#initializesecurity)|サービスの既定のセキュリティ設定を提供します。|
|[CAtlServiceModuleT:: Install](#install)|サービスをインストールして作成します。|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|サービスがインストールされていることを確認します。|
|[CAtlServiceModuleT::LogEvent](#logevent)|イベントログに書き込みます。|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|サービスを続行するには、このメソッドをオーバーライドします。|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|サービスを照会するには、このメソッドをオーバーライドします。|
|[CAtlServiceModuleT::OnPause](#onpause)|サービスを一時停止するには、このメソッドをオーバーライドします。|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|サービスをシャットダウンするには、このメソッドをオーバーライドします|
|[CAtlServiceModuleT::OnStop](#onstop)|サービスを停止するには、このメソッドをオーバーライドします|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|サービスに対する不明な要求を処理するには、このメソッドをオーバーライドします|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|コマンドラインを解析し、必要に応じて登録を実行します。|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|このメソッドは、メッセージループを開始する直前に呼び出されます。|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|レジストリにサービスを登録します。|
|[CAtlServiceModuleT::Run](#run)|サービスを実行します。|
|[CAtlServiceModuleT:: ServiceMain](#servicemain)|サービスコントロールマネージャーによって呼び出されるメソッド。|
|[CAtlServiceModuleT:: SetServiceStatus](#setservicestatus)|サービスの状態を更新します。|
|[CAtlServiceModuleT:: Start](#start)|サービスの`CAtlServiceModuleT::WinMain`開始時にによって呼び出されます。|
|[CAtlServiceModuleT:: Uninstall](#uninstall)|サービスを停止して削除します。|
|[CAtlServiceModuleT:: Unlock](#unlock)|サービスのロックカウントをデクリメントします。|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|レジストリからサービスを削除します。|
|[CAtlServiceModuleT:: WinMain](#winmain)|このメソッドは、サービスを実行するために必要なコードを実装します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAtlServiceModuleT:: m_bService](#m_bservice)|プログラムがサービスとして実行されていることを示すフラグ。|
|[CAtlServiceModuleT:: m_dwThreadID](#m_dwthreadid)|スレッド識別子を格納しているメンバー変数。|
|[CAtlServiceModuleT:: m_hServiceStatus](#m_hservicestatus)|現在のサービスの状態情報構造体へのハンドルを格納しているメンバー変数。|
|[CAtlServiceModuleT:: m_status](#m_status)|現在のサービスの状態情報構造を格納しているメンバー変数。|
|[CAtlServiceModuleT:: m_szServiceName](#m_szservicename)|登録するサービスの名前。|

## <a name="remarks"></a>Remarks

`CAtlServiceModuleT`[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)から派生したは、ATL サービスモジュールを実装します。 `CAtlServiceModuleT`コマンドラインの処理、インストール、登録、および削除のためのメソッドを提供します。 追加の機能が必要な場合は、これらのメソッドとその他のメソッドをオーバーライドできます。

このクラスは、以前のバージョンの ATL で使用されていた古い[CComModule クラス](../../atl/reference/ccommodule-class.md)に代わるものです。 詳細については、「 [ATL モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="catlservicemodulet"></a>  CAtlServiceModuleT::CAtlServiceModuleT

コンストラクターです。

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Remarks

データメンバーを初期化し、初期サービスの状態を設定します。

##  <a name="handler"></a>  CAtlServiceModuleT::Handler

サービスのハンドラールーチン。

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>パラメーター

*dwOpcode*<br/>
ハンドラー操作を定義するスイッチ。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

これは、サービスコントロールマネージャー (SCM) がサービスの状態を取得して、停止や一時停止などの命令を発行するために呼び出すコードです。 SCM は、次に示す操作コードをに`Handler`渡して、サービスの動作を示します。

|操作コード|説明|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|サービスを停止します。 Atlbase. h のメソッド[CAtlServiceModuleT:: OnStop](#onstop)をオーバーライドして動作を変更します。|
|SERVICE_CONTROL_PAUSE|ユーザー実装済み。 Atlbase. h で空のメソッド[CAtlServiceModuleT:: OnPause](#onpause)をオーバーライドして、サービスを一時停止します。|
|SERVICE_CONTROL_CONTINUE|ユーザー実装済み。 Atlbase. h で空のメソッド[CAtlServiceModuleT:: OnContinue](#oncontinue)をオーバーライドしてサービスを続行します。|
|SERVICE_CONTROL_INTERROGATE|ユーザー実装済み。 Atlbase. h で空のメソッド[CAtlServiceModuleT:: Oninterrogate](#oninterrogate)をオーバーライドして、サービスを問い合わせます。|
|SERVICE_CONTROL_SHUTDOWN|ユーザー実装済み。 Atlbase. h で空のメソッド[CAtlServiceModuleT:: OnShutdown](#onshutdown)をオーバーライドして、サービスをシャットダウンします。|

操作コードが認識されない場合は、 [CAtlServiceModuleT:: OnUnknownRequest](#onunknownrequest)メソッドが呼び出されます。

既定の ATL によって生成されるサービスは、stop 命令のみを処理します。 SCM が stop 命令を渡した場合、サービスはプログラムが停止しようとしていることを SCM に通知します。 次に、サービス`PostThreadMessage`はを呼び出して、終了メッセージをそれ自体にポストします。 これにより、メッセージループが終了し、サービスは最終的に終了します。

##  <a name="initializesecurity"></a>  CAtlServiceModuleT::InitializeSecurity

サービスの既定のセキュリティ設定を提供します。

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

から`CAtlServiceModuleT`派生するすべてのクラスは、派生クラスでこのメソッドを実装する必要があります。

の呼び出し`CoInitializeSecurity`で、RPC_C_IMP_LEVEL_IDENTIFY の PKT レベルの認証、偽装レベル、および null 以外の適切なセキュリティ記述子を使用します。

ウィザードで生成された属性なしサービスプロジェクトの場合、次のようになります。

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

属性付きサービスプロジェクトの場合、次のようになります。

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

##  <a name="install"></a>  CAtlServiceModuleT::Install

サービスをインストールして作成します。

```
BOOL Install() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

サービスをサービスコントロールマネージャー (SCM) データベースにインストールし、サービスオブジェクトを作成します。 サービスを作成できなかった場合は、メッセージボックスが表示され、メソッドは FALSE を返します。

##  <a name="isinstalled"></a>CAtlServiceModuleT:: IsInstalled

サービスがインストールされていることを確認します。

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>戻り値

サービスがインストールされている場合は TRUE、それ以外の場合は FALSE を返します。

##  <a name="logevent"></a>  CAtlServiceModuleT::LogEvent

イベントログに書き込みます。

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>パラメーター

*pszFormat*<br/>
イベント ログに書き込む文字列。

*...*<br/>
イベントログに書き込まれる追加文字列 (省略可能)。

### <a name="remarks"></a>Remarks

このメソッドは、関数[Reportevent](/windows/win32/api/winbase/nf-winbase-reporteventw)を使用して、詳細情報をイベントログに書き込みます。 サービスが実行されていない場合は、文字列がコンソールに送信されます。

##  <a name="m_bservice"></a>  CAtlServiceModuleT::m_bService

プログラムがサービスとして実行されていることを示すフラグ。

```
BOOL m_bService;
```

### <a name="remarks"></a>Remarks

サービス EXE をアプリケーション EXE と区別するために使用されます。

##  <a name="m_dwthreadid"></a>CAtlServiceModuleT:: m_dwThreadID

サービスのスレッド識別子を格納しているメンバー変数。

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Remarks

この変数には、現在のスレッドのスレッド識別子が格納されます。

##  <a name="m_hservicestatus"></a>  CAtlServiceModuleT::m_hServiceStatus

現在のサービスの状態情報構造体へのハンドルを格納しているメンバー変数。

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Remarks

[SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status)構造体には、サービスに関する情報が含まれています。

##  <a name="m_status"></a>CAtlServiceModuleT:: m_status

現在のサービスの状態情報構造を格納しているメンバー変数。

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Remarks

[SERVICE_STATUS](/windows/win32/api/winsvc/ns-winsvc-service_status)構造体には、サービスに関する情報が含まれています。

##  <a name="m_szservicename"></a>  CAtlServiceModuleT::m_szServiceName

登録するサービスの名前。

```
TCHAR [256] m_szServiceName;
```

### <a name="remarks"></a>Remarks

サービスの名前を格納する、null で終わる文字列。

##  <a name="oncontinue"></a>  CAtlServiceModuleT::OnContinue

サービスを続行するには、このメソッドをオーバーライドします。

```
void OnContinue() throw();
```

##  <a name="oninterrogate"></a>  CAtlServiceModuleT::OnInterrogate

サービスを照会するには、このメソッドをオーバーライドします。

```
void OnInterrogate() throw();
```

##  <a name="onpause"></a>  CAtlServiceModuleT::OnPause

サービスを一時停止するには、このメソッドをオーバーライドします。

```
void OnPause() throw();
```

##  <a name="onshutdown"></a>  CAtlServiceModuleT::OnShutdown

サービスをシャットダウンするには、このメソッドをオーバーライドします。

```
void OnShutdown() throw();
```

##  <a name="onstop"></a>  CAtlServiceModuleT::OnStop

サービスを停止するには、このメソッドをオーバーライドします。

```
void OnStop() throw();
```

##  <a name="onunknownrequest"></a>  CAtlServiceModuleT::OnUnknownRequest

サービスに対する不明な要求を処理するには、このメソッドをオーバーライドします。

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>パラメーター

*dwOpcode*<br/>
予約済み。

##  <a name="parsecommandline"></a>  CAtlServiceModuleT::ParseCommandLine

コマンドラインを解析し、必要に応じて登録を実行します。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>パラメーター

*lpCmdLine*<br/>
コマンド ライン。

*pnRetCode*<br/>
登録に対応する HRESULT (行われた場合)。

### <a name="return-value"></a>戻り値

成功した場合は true、コマンドラインで指定された RGS ファイルを登録できなかった場合は false を返します。

### <a name="remarks"></a>Remarks

必要に応じて、コマンドラインを解析し、指定された RGS ファイルを登録または登録解除します。 このメソッドは、 [CAtlExeModuleT::P arsecommandline](../../atl/reference/catlexemodulet-class.md#parsecommandline)を呼び出して、と **/UnregServer**を確認します。 引数/**サービス**を追加すると、サービスが登録されます。

##  <a name="premessageloop"></a>  CAtlServiceModuleT::PreMessageLoop

このメソッドは、メッセージループを開始する直前に呼び出されます。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
このパラメーターは、 [CAtlExeModuleT::P](../../atl/reference/catlexemodulet-class.md#premessageloop)に渡されます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

サービスのカスタム初期化コードを追加するには、このメソッドをオーバーライドします。

##  <a name="registerappid"></a>  CAtlServiceModuleT::RegisterAppId

レジストリにサービスを登録します。

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>パラメーター

*bService*<br/>
をサービスとして登録するには、true である必要があります。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="run"></a>  CAtlServiceModuleT::Run

サービスを実行します。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
ウィンドウの表示方法を指定します。 このパラメーターには、 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)セクションで説明されている値のいずれかを指定できます。 既定値は SW_HIDE です。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

が呼び出されると`Run` 、は[CAtlServiceModuleT::P remessagCAtlExeModuleT](#premessageloop) [::: runmessag](../../atl/reference/catlexemodulet-class.md#runmessageloop)op を呼び出し、 [CAtlExeModuleT:P:](../../atl/reference/catlexemodulet-class.md#postmessageloop)を呼び出します。

##  <a name="servicemain"></a>CAtlServiceModuleT:: ServiceMain

このメソッドは、サービスコントロールマネージャーによって呼び出されます。

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>パラメーター

*dwArgc*<br/>
Argc 引数。

*lpszArgv*<br/>
Argv 引数。

### <a name="remarks"></a>Remarks

サービスコントロールマネージャー (SCM) は、 `ServiceMain`コントロールパネルでサービスアプリケーションを開いたときにを呼び出し、サービスを選択して、[開始] をクリックします。

Scm がを呼び出し`ServiceMain`た後、サービスは scm にハンドラー関数を与える必要があります。 この関数を使用すると、SCM はサービスの状態を取得し、特定の命令 (一時停止や停止など) を渡すことができます。 その後、 [CAtlServiceModuleT:: Run](#run)が呼び出され、サービスの主要な作業が実行されます。 `Run`は、サービスが停止するまで実行を続けます。

##  <a name="setservicestatus"></a>CAtlServiceModuleT:: SetServiceStatus

このメソッドは、サービスの状態を更新します。

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>パラメーター

*dwState*<br/>
新しい状態。 使用可能な値については、 [SetServiceStatus](/windows/win32/api/winsvc/nf-winsvc-setservicestatus)を参照してください。

### <a name="remarks"></a>Remarks

サービスのサービスコントロールマネージャーのステータス情報を更新します。 [CAtlServiceModuleT:: Run](#run)、 [CAtlServiceModuleT:: ServiceMain](#servicemain) 、およびその他のハンドラーメソッドによって呼び出されます。 状態は、メンバー変数[CAtlServiceModuleT:: m_status](#m_status)にも格納されます。

##  <a name="start"></a>CAtlServiceModuleT:: Start

サービスの`CAtlServiceModuleT::WinMain`開始時にによって呼び出されます。

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
ウィンドウの表示方法を指定します。 このパラメーターには、 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)セクションで説明されている値のいずれかを指定できます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>Remarks

[CAtlServiceModuleT:: WinMain](#winmain)メソッドは、登録とインストールの両方を処理します。また、レジストリエントリの削除やモジュールのアンインストールに関連するタスクも行います。 サービスが実行されると`WinMain` 、 `Start`はを呼び出します。

##  <a name="uninstall"></a>CAtlServiceModuleT:: Uninstall

サービスを停止して削除します。

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

サービスの実行を停止し、サービスコントロールマネージャーデータベースから削除します。

##  <a name="unlock"></a>CAtlServiceModuleT:: Unlock

サービスのロックカウントをデクリメントします。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>戻り値

ロックカウントを返します。これは、診断およびデバッグに便利な場合があります。

##  <a name="unregisterappid"></a>  CAtlServiceModuleT::UnregisterAppId

レジストリからサービスを削除します。

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合はエラー HRESULT を返します。

##  <a name="winmain"></a>  CAtlServiceModuleT::WinMain

このメソッドは、サービスを開始するために必要なコードを実装します。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
ウィンドウの表示方法を指定します。 このパラメーターには、 [WinMain](/windows/win32/api/winbase/nf-winbase-winmain)セクションで説明されている値のいずれかを指定できます。

### <a name="return-value"></a>戻り値

サービスの戻り値を返します。

### <a name="remarks"></a>Remarks

このメソッドは、( [CAtlServiceModuleT::P arsecommandline](#parsecommandline)を使用して) コマンドラインを処理した後、( [CAtlServiceModuleT:: Start](#start)を使用して) サービスを開始します。

## <a name="see-also"></a>関連項目

[CAtlExeModuleT クラス](../../atl/reference/catlexemodulet-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
