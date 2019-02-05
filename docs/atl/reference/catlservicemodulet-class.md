---
title: CAtlServiceModuleT クラス
ms.date: 11/04/2016
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
ms.openlocfilehash: ad682980fbc885d79598b41a5dcc094bb65db8cf
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893536"
---
# <a name="catlservicemodulet-class"></a>CAtlServiceModuleT クラス

このクラスは、サービスを実装します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class T, UINT nServiceNameID>
class ATL_NO_VTABLE CAtlServiceModuleT : public CAtlExeModuleT<T>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
クラスから派生した`CAtlServiceModuleT`します。

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
|[CAtlServiceModuleT::Handler](#handler)|サービスのハンドラー ルーチン。|
|[CAtlServiceModuleT::InitializeSecurity](#initializesecurity)|既定のサービスのセキュリティ設定を提供します。|
|[CAtlServiceModuleT::Install](#install)|インストールし、サービスを作成します。|
|[CAtlServiceModuleT::IsInstalled](#isinstalled)|サービスがインストールされていることを確認します。|
|[CAtlServiceModuleT::LogEvent](#logevent)|イベント ログに書き込みます。|
|[CAtlServiceModuleT::OnContinue](#oncontinue)|サービスを続行するには、このメソッドをオーバーライドします。|
|[CAtlServiceModuleT::OnInterrogate](#oninterrogate)|サービスを調査するには、このメソッドをオーバーライドします。|
|[CAtlServiceModuleT::OnPause](#onpause)|サービスを一時停止するには、このメソッドをオーバーライドします。|
|[CAtlServiceModuleT::OnShutdown](#onshutdown)|サービスのシャット ダウンするには、このメソッドをオーバーライドします。|
|[CAtlServiceModuleT::OnStop](#onstop)|サービスを停止するには、このメソッドをオーバーライドします。|
|[CAtlServiceModuleT::OnUnknownRequest](#onunknownrequest)|サービスに不明な要求を処理するには、このメソッドをオーバーライドします。|
|[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)|コマンドラインを解析し、必要な場合は、登録を実行します。|
|[CAtlServiceModuleT::PreMessageLoop](#premessageloop)|このメソッドは、メッセージ ループを開始する直前に呼び出されます。|
|[CAtlServiceModuleT::RegisterAppId](#registerappid)|レジストリにサービスを登録します。|
|[CAtlServiceModuleT::Run](#run)|サービスを実行します。|
|[CAtlServiceModuleT::ServiceMain](#servicemain)|サービス コントロール マネージャーから呼び出されるメソッド。|
|[CAtlServiceModuleT::SetServiceStatus](#setservicestatus)|サービスの状態を更新します。|
|[CAtlServiceModuleT::Start](#start)|メソッドを呼び出して`CAtlServiceModuleT::WinMain`サービスの起動時にします。|
|[CAtlServiceModuleT::Uninstall](#uninstall)|停止し、サービスを削除します。|
|[CAtlServiceModuleT::Unlock](#unlock)|サービスのロック カウントをデクリメントします。|
|[CAtlServiceModuleT::UnregisterAppId](#unregisterappid)|レジストリからサービスを削除します。|
|[CAtlServiceModuleT::WinMain](#winmain)|このメソッドは、サービスの実行に必要なコードを実装します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAtlServiceModuleT::m_bService](#m_bservice)|サービスとして、プログラムが実行されていることを示すフラグです。|
|[CAtlServiceModuleT::m_dwThreadID](#m_dwthreadid)|スレッド識別子を格納するメンバー変数です。|
|[CAtlServiceModuleT::m_hServiceStatus](#m_hservicestatus)|現在のサービスの状態情報の構造体を識別するハンドルを格納するメンバー変数。|
|[CAtlServiceModuleT::m_status](#m_status)|現在のサービスの状態情報の構造体を格納するメンバー変数。|
|[CAtlServiceModuleT::m_szServiceName](#m_szservicename)|登録されているサービスの名前。|

## <a name="remarks"></a>Remarks

`CAtlServiceModuleT`、から派生した[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)、ATL サービス モジュールを実装します。 `CAtlServiceModuleT` コマンドライン処理、インストール、登録、および削除メソッドを提供します。 追加の機能が必要な場合は、これらおよびその他のメソッドをオーバーライドできます。

このクラスは廃止された置換[CComModule クラス](../../atl/reference/ccommodule-class.md)以前のバージョンの ATL の使用 参照してください[ATL モジュール クラス](../../atl/atl-module-classes.md)の詳細。

## <a name="inheritance-hierarchy"></a>継承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)

`CAtlServiceModuleT`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="catlservicemodulet"></a>  CAtlServiceModuleT::CAtlServiceModuleT

コンストラクターです。

```
CAtlServiceModuleT() throw();
```

### <a name="remarks"></a>Remarks

データ メンバーを初期化し、初期サービスの状態を設定します。

##  <a name="handler"></a>  CAtlServiceModuleT::Handler

サービスのハンドラー ルーチン。

```
void Handler(DWORD dwOpcode) throw();
```

### <a name="parameters"></a>パラメーター

*dwOpcode*<br/>
ハンドラーの操作を定義するスイッチ。 詳細については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

これは、停止などのサービスと問題の手順の状態を取得または一時停止するサービス コントロール マネージャー (SCM) を呼び出すコードです。 SCM には、次に示す、操作コードを渡します`Handler`を示す、サービスが行う必要があります。

|操作コード|説明|
|--------------------|-------------|
|SERVICE_CONTROL_STOP|サービスを停止します。 メソッドをオーバーライド[CAtlServiceModuleT::OnStop](#onstop) atlbase.h 動作を変更するのです。|
|SERVICE_CONTROL_PAUSE|ユーザーが実装されています。 空のメソッドをオーバーライドして[CAtlServiceModuleT::OnPause](#onpause) atlbase.h サービスを一時停止にします。|
|SERVICE_CONTROL_CONTINUE|ユーザーが実装されています。 空のメソッドをオーバーライドして[CAtlServiceModuleT::OnContinue](#oncontinue) atlbase.h、サービスを続行するのです。|
|SERVICE_CONTROL_INTERROGATE|ユーザーが実装されています。 空のメソッドをオーバーライドして[CAtlServiceModuleT::OnInterrogate](#oninterrogate) atlbase.h、サービスを調査するのです。|
|SERVICE_CONTROL_SHUTDOWN|ユーザーが実装されています。 空のメソッドをオーバーライドして[CAtlServiceModuleT::OnShutdown](#onshutdown) atlbase.h サービスをシャット ダウンするのです。|

操作コードが認識されない場合、メソッド[されない](#onunknownrequest)が呼び出されます。

既定の ATL によって生成されたサービスでは、stop 命令のみ処理します。 SCM には、stop 命令が成功した場合、サービスは、プログラムが停止しようとしていますが、SCM を指示します。 サービスを呼び出して`PostThreadMessage`自体に中止メッセージを投稿します。 メッセージ ループを終了このし、サービスが最終的に終了します。

##  <a name="initializesecurity"></a>  CAtlServiceModuleT::InitializeSecurity

既定のサービスのセキュリティ設定を提供します。

```
HRESULT InitializeSecurity() throw();
```

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

Visual Studio .NET 2003 では、このメソッドが基底クラスで実装されていません。 Visual Studio プロジェクト ウィザードには、このメソッドにはで生成されたコードが含まれていますが、ATL 7.1 を使用して、以前のバージョンの Visual C で作成されたプロジェクトがコンパイルされている場合、コンパイル エラーが発生します。 任意のクラスから派生した`CAtlServiceModuleT`派生クラスでこのメソッドを実装する必要があります。

呼び出しの PKT レベルの認証、RPC_C_IMP_LEVEL_IDENTIFY の偽装レベル、および適切な非 null セキュリティ記述子を使用して`CoInitializeSecurity`します。

属性なしのサービスのウィザードで生成されたプロジェクトでは、次のようになります。

[!code-cpp[NVC_ATL_Service#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_1.cpp)]

属性付きのサービス プロジェクトでは、次のようになります。

[!code-cpp[NVC_ATL_ServiceAttrib#1](../../atl/reference/codesnippet/cpp/catlservicemodulet-class_2.cpp)]

##  <a name="install"></a>  CAtlServiceModuleT::Install

インストールし、サービスを作成します。

```
BOOL Install() throw();
```

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

サービス コントロール マネージャー (SCM) データベースにサービスをインストールし、サービス オブジェクトが作成されます。 サービスを作成できませんだった場合、は、メッセージ ボックスが表示され、FALSE を返します。

##  <a name="isinstalled"></a>  CAtlServiceModuleT::IsInstalled

サービスがインストールされていることを確認します。

```
BOOL IsInstalled() throw();
```

### <a name="return-value"></a>戻り値

かどうか、サービスがインストールされているそれ以外の場合は TRUE を返します。

##  <a name="logevent"></a>  CAtlServiceModuleT::LogEvent

イベント ログに書き込みます。

```
void __cdecl LogEvent(LPCTSTR pszFormat, ...) throw();
```

### <a name="parameters"></a>パラメーター

*pszFormat*<br/>
イベント ログに書き込む文字列。

*...*<br/>
イベント ログに書き込まれる省略可能な余分な文字列。

### <a name="remarks"></a>Remarks

このメソッドは、の詳細を関数を使用して、イベント ログに書き込みます[ReportEvent](/windows/desktop/api/winbase/nf-winbase-reporteventa)します。 サービスが実行されていない場合は、文字列がコンソールに送信されます。

##  <a name="m_bservice"></a>  CAtlServiceModuleT::m_bService

サービスとして、プログラムが実行されていることを示すフラグです。

```
BOOL m_bService;
```

### <a name="remarks"></a>Remarks

アプリケーションの exe ファイルからサービス実行可能ファイルを区別するために使用されます。

##  <a name="m_dwthreadid"></a>  CAtlServiceModuleT::m_dwThreadID

サービスのスレッド識別子を格納するメンバー変数です。

```
DWORD m_dwThreadID;
```

### <a name="remarks"></a>Remarks

この変数は、現在のスレッドのスレッド識別子を格納します。

##  <a name="m_hservicestatus"></a>  CAtlServiceModuleT::m_hServiceStatus

現在のサービスの状態情報の構造体を識別するハンドルを格納するメンバー変数。

```
SERVICE_STATUS_HANDLE m_hServiceStatus;
```

### <a name="remarks"></a>Remarks

[SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status)構造体には、サービスに関する情報が含まれています。

##  <a name="m_status"></a>  CAtlServiceModuleT::m_status

現在のサービスの状態情報の構造体を格納するメンバー変数。

```
SERVICE_STATUS m_status;
```

### <a name="remarks"></a>Remarks

[SERVICE_STATUS](/windows/desktop/api/winsvc/ns-winsvc-_service_status)構造体には、サービスに関する情報が含まれています。

##  <a name="m_szservicename"></a>  CAtlServiceModuleT::m_szServiceName

登録されているサービスの名前。

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

サービスを調査するには、このメソッドをオーバーライドします。

```
void OnInterrogate() throw();
```

##  <a name="onpause"></a>  CAtlServiceModuleT::OnPause

サービスを一時停止するには、このメソッドをオーバーライドします。

```
void OnPause() throw();
```

##  <a name="onshutdown"></a>  CAtlServiceModuleT::OnShutdown

サービスのシャット ダウンするには、このメソッドをオーバーライドします。

```
void OnShutdown() throw();
```

##  <a name="onstop"></a>  CAtlServiceModuleT::OnStop

サービスを停止するには、このメソッドをオーバーライドします。

```
void OnStop() throw();
```

##  <a name="onunknownrequest"></a>  CAtlServiceModuleT::OnUnknownRequest

サービスに不明な要求を処理するには、このメソッドをオーバーライドします。

```
void OnUnknownRequest(DWORD /* dwOpcode*/) throw();
```

### <a name="parameters"></a>パラメーター

*dwOpcode*<br/>
予約済み。

##  <a name="parsecommandline"></a>  CAtlServiceModuleT::ParseCommandLine

コマンドラインを解析し、必要な場合は、登録を実行します。

```
bool ParseCommandLine(LPCTSTR lpCmdLine, HRESULT* pnRetCode) throw();
```

### <a name="parameters"></a>パラメーター

*lpCmdLine*<br/>
コマンド ライン。

*pnRetCode*<br/>
(これが、行われた) 場合は、登録に対応する HRESULT。

### <a name="return-value"></a>戻り値

成功した場合、またはコマンドラインで指定した RGS ファイルを登録されていない場合は false に true を返します。

### <a name="remarks"></a>Remarks

コマンドライン解析の登録または必要な場合は、指定された RGS ファイルの登録を解除します。 このメソッドを呼び出す[CAtlExeModuleT::ParseCommandLine](../../atl/reference/catlexemodulet-class.md#parsecommandline)をチェックする **/RegServer**と **/UnregServer**します。 引数を追加する **-/service**サービスに登録されます。

##  <a name="premessageloop"></a>  CAtlServiceModuleT::PreMessageLoop

このメソッドは、メッセージ ループを開始する直前に呼び出されます。

```
HRESULT PreMessageLoop(int nShowCmd) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
このパラメーターに渡される[CAtlExeModuleT::PreMessageLoop](../../atl/reference/catlexemodulet-class.md#premessageloop)します。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

サービスのカスタム初期化コードを追加するには、このメソッドをオーバーライドします。

##  <a name="registerappid"></a>  CAtlServiceModuleT::RegisterAppId

レジストリにサービスを登録します。

```
inline HRESULT RegisterAppId(bool bService = false) throw();
```

### <a name="parameters"></a>パラメーター

*bService*<br/>
サービスとして登録する場合は true である必要があります。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="run"></a>  CAtlServiceModuleT::Run

サービスを実行します。

```
HRESULT Run(int nShowCmd = SW_HIDE) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
ウィンドウの表示方法を指定します。 このパラメーターで説明されている値のいずれかを指定できます、 [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain)セクション。 既定値は、SW_HIDE です。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

呼び出された後に`Run`呼び出し[CAtlServiceModuleT::PreMessageLoop](#premessageloop)、 [CAtlExeModuleT::RunMessageLoop](../../atl/reference/catlexemodulet-class.md#runmessageloop)、および[CAtlExeModuleT::PostMessageLoop](../../atl/reference/catlexemodulet-class.md#postmessageloop).

##  <a name="servicemain"></a>  CAtlServiceModuleT::ServiceMain

このメソッドには、サービス コントロール マネージャーでは、呼び出されます。

```
void ServiceMain(DWORD dwArgc, LPTSTR* lpszArgv) throw();
```

### <a name="parameters"></a>パラメーター

*dwArgc*<br/>
Argc 引数。

*lpszArgv*<br/>
Argv 引数。

### <a name="remarks"></a>Remarks

サービス コントロール マネージャー (SCM) 呼び出し`ServiceMain`コントロール パネルの サービス アプリケーションを開くと、サービスを選択し、スタート をクリックします。

SCM の後に呼び出す`ServiceMain`サービスがハンドラー関数には、SCM の付ける必要があります。 この関数では、SCM はサービスの状態を取得して (一時停止、停止など) の具体的な手順を渡すことができます。 その後、 [catlservicemodulet::run](#run)サービスの主な作業を実行すると呼びます。 `Run` サービスが停止するまで実行を継続します。

##  <a name="setservicestatus"></a>  CAtlServiceModuleT::SetServiceStatus

このメソッドは、サービスの状態を更新します。

```
void SetServiceStatus(DWORD dwState) throw();
```

### <a name="parameters"></a>パラメーター

*dwState*<br/>
新しいステータス。 参照してください[SetServiceStatus](/windows/desktop/api/winsvc/nf-winsvc-setservicestatus)使用可能な値。

### <a name="remarks"></a>Remarks

サービスのサービス コントロール マネージャーの状態情報を更新します。 呼び出して[catlservicemodulet::run](#run)、 [catlservicemodulet::servicemain](#servicemain)およびその他のハンドラー メソッド。 状態は、メンバー変数にも格納[CAtlServiceModuleT::m_status](#m_status)します。

##  <a name="start"></a>  CAtlServiceModuleT::Start

メソッドを呼び出して`CAtlServiceModuleT::WinMain`サービスの起動時にします。

```
HRESULT Start(int nShowCmd) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
ウィンドウの表示方法を指定します。 このパラメーターで説明されている値のいずれかを指定できます、 [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain)セクション。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

[起動時](#winmain)メソッド登録とインストールの両方を処理するだけでなくタスクのレジストリ エントリを削除して、モジュールのアンインストールに関係します。 サービスが実行される`WinMain`呼び出し`Start`します。

##  <a name="uninstall"></a>  CAtlServiceModuleT::Uninstall

停止し、サービスを削除します。

```
BOOL Uninstall() throw();
```

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

実行中のサービスを停止し、サービス コントロール マネージャー データベースから削除されます。

##  <a name="unlock"></a>  CAtlServiceModuleT::Unlock

サービスのロック カウントをデクリメントします。

```
LONG Unlock() throw();
```

### <a name="return-value"></a>戻り値

診断に役立ちますし、デバッグ可能性のあるロック カウントを返します。

##  <a name="unregisterappid"></a>  CAtlServiceModuleT::UnregisterAppId

レジストリからサービスを削除します。

```
HRESULT UnregisterAppId() throw();
```

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

##  <a name="winmain"></a>  CAtlServiceModuleT::WinMain

このメソッドは、サービスを開始するために必要なコードを実装します。

```
int WinMain(int nShowCmd) throw();
```

### <a name="parameters"></a>パラメーター

*nShowCmd*<br/>
ウィンドウの表示方法を指定します。 このパラメーターで説明されている値のいずれかを指定できます、 [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain)セクション。

### <a name="return-value"></a>戻り値

サービスの戻り値を返します。

### <a name="remarks"></a>Remarks

このメソッドは、コマンドラインを処理 (で[CAtlServiceModuleT::ParseCommandLine](#parsecommandline)) と、サービスを開始し (を使用して[catlservicemodulet::start](#start))。

## <a name="see-also"></a>関連項目

[CAtlExeModuleT クラス](../../atl/reference/catlexemodulet-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
