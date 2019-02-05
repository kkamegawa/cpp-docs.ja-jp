---
title: CAccessToken クラス
ms.date: 11/04/2016
f1_keywords:
- CAccessToken
- ATLSECURITY/ATL::CAccessToken
- ATLSECURITY/ATL::CAccessToken::Attach
- ATLSECURITY/ATL::CAccessToken::CheckTokenMembership
- ATLSECURITY/ATL::CAccessToken::CreateImpersonationToken
- ATLSECURITY/ATL::CAccessToken::CreatePrimaryToken
- ATLSECURITY/ATL::CAccessToken::CreateProcessAsUser
- ATLSECURITY/ATL::CAccessToken::CreateRestrictedToken
- ATLSECURITY/ATL::CAccessToken::Detach
- ATLSECURITY/ATL::CAccessToken::DisablePrivilege
- ATLSECURITY/ATL::CAccessToken::DisablePrivileges
- ATLSECURITY/ATL::CAccessToken::EnablePrivilege
- ATLSECURITY/ATL::CAccessToken::EnablePrivileges
- ATLSECURITY/ATL::CAccessToken::GetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::GetEffectiveToken
- ATLSECURITY/ATL::CAccessToken::GetGroups
- ATLSECURITY/ATL::CAccessToken::GetHandle
- ATLSECURITY/ATL::CAccessToken::GetImpersonationLevel
- ATLSECURITY/ATL::CAccessToken::GetLogonSessionId
- ATLSECURITY/ATL::CAccessToken::GetLogonSid
- ATLSECURITY/ATL::CAccessToken::GetOwner
- ATLSECURITY/ATL::CAccessToken::GetPrimaryGroup
- ATLSECURITY/ATL::CAccessToken::GetPrivileges
- ATLSECURITY/ATL::CAccessToken::GetProcessToken
- ATLSECURITY/ATL::CAccessToken::GetProfile
- ATLSECURITY/ATL::CAccessToken::GetSource
- ATLSECURITY/ATL::CAccessToken::GetStatistics
- ATLSECURITY/ATL::CAccessToken::GetTerminalServicesSessionId
- ATLSECURITY/ATL::CAccessToken::GetThreadToken
- ATLSECURITY/ATL::CAccessToken::GetTokenId
- ATLSECURITY/ATL::CAccessToken::GetType
- ATLSECURITY/ATL::CAccessToken::GetUser
- ATLSECURITY/ATL::CAccessToken::HKeyCurrentUser
- ATLSECURITY/ATL::CAccessToken::Impersonate
- ATLSECURITY/ATL::CAccessToken::ImpersonateLoggedOnUser
- ATLSECURITY/ATL::CAccessToken::IsTokenRestricted
- ATLSECURITY/ATL::CAccessToken::LoadUserProfile
- ATLSECURITY/ATL::CAccessToken::LogonUser
- ATLSECURITY/ATL::CAccessToken::OpenCOMClientToken
- ATLSECURITY/ATL::CAccessToken::OpenNamedPipeClientToken
- ATLSECURITY/ATL::CAccessToken::OpenRPCClientToken
- ATLSECURITY/ATL::CAccessToken::OpenThreadToken
- ATLSECURITY/ATL::CAccessToken::PrivilegeCheck
- ATLSECURITY/ATL::CAccessToken::Revert
- ATLSECURITY/ATL::CAccessToken::SetDefaultDacl
- ATLSECURITY/ATL::CAccessToken::SetOwner
- ATLSECURITY/ATL::CAccessToken::SetPrimaryGroup
helpviewer_keywords:
- CAccessToken class
ms.assetid: bb5c5945-56a5-4083-b442-76573cee83ab
ms.openlocfilehash: e53160860211ba09114f2d4d101a2eaaf7de941f
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894243"
---
# <a name="caccesstoken-class"></a>CAccessToken クラス

このクラスは、アクセス トークンのラッパーです。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CAccessToken
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAccessToken::~CAccessToken](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAccessToken::Attach](#attach)|指定したアクセス トークンのハンドルの所有権を取得するには、このメソッドを呼び出します。|
|[CAccessToken::CheckTokenMembership](#checktokenmembership)|指定された SID が有効になっているかどうかを判断するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::CreateImpersonationToken](#createimpersonationtoken)|新しい権限借用のアクセス トークンを作成するには、このメソッドを呼び出します。|
|[CAccessToken::CreatePrimaryToken](#createprimarytoken)|新しいプライマリ トークンを作成するには、このメソッドを呼び出します。|
|[CAccessToken::CreateProcessAsUser](#createprocessasuser)|によって表されるユーザーのセキュリティ コンテキストで実行されている新しいプロセスを作成するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::CreateRestrictedToken](#createrestrictedtoken)|新しく作成するには、このメソッドを呼び出す制限`CAccessToken`オブジェクト。|
|[CAccessToken::Detach](#detach)|アクセス トークンの所有権を取り消すには、このメソッドを呼び出します。|
|[CAccessToken::DisablePrivilege](#disableprivilege)|特権を無効にするには、このメソッドを呼び出す、`CAccessToken`オブジェクト。|
|[CAccessToken::DisablePrivileges](#disableprivileges)|1 つまたは複数の権限を無効にするには、このメソッドを呼び出す、`CAccessToken`オブジェクト。|
|[CAccessToken::EnablePrivilege](#enableprivilege)|特権を有効にするには、このメソッドを呼び出す、`CAccessToken`オブジェクト。|
|[CAccessToken::EnablePrivileges](#enableprivileges)|1 つまたは複数の権限を有効にするには、このメソッドを呼び出す、`CAccessToken`オブジェクト。|
|[CAccessToken::GetDefaultDacl](#getdefaultdacl)|返すには、このメソッドを呼び出して、`CAccessToken`オブジェクトの既定の DACL。|
|[CAccessToken::GetEffectiveToken](#geteffectivetoken)|取得するには、このメソッドを呼び出して、`CAccessToken`現在のスレッドに対して有効なアクセス トークンと等しいオブジェクト。|
|[CAccessToken::GetGroups](#getgroups)|返すには、このメソッドを呼び出して、`CAccessToken`トークンのオブジェクトのグループ。|
|[CAccessToken::GetHandle](#gethandle)|アクセス トークンを識別するハンドルを取得するには、このメソッドを呼び出します。|
|[CAccessToken::GetImpersonationLevel](#getimpersonationlevel)|アクセス トークンから偽装レベルを取得するには、このメソッドを呼び出します。|
|[CAccessToken::GetLogonSessionId](#getlogonsessionid)|関連付けられたログオン セッションの ID を取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::GetLogonSid](#getlogonsid)|関連付けられたログオン SID を取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::GetOwner](#getowner)|関連付けられている所有者を取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::GetPrimaryGroup](#getprimarygroup)|関連付けられているプライマリ グループを取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::GetPrivileges](#getprivileges)|関連付けられている特権を取得するには、このメソッドを呼び出し、`CAccessToken`オブジェクト。|
|[CAccessToken::GetProcessToken](#getprocesstoken)|指定されたプロセスからアクセス トークンを使用して `CAccessToken` を初期化するには、このメソッドを呼び出します。|
|[CAccessToken::GetProfile](#getprofile)|関連付けられているユーザーのプロファイルを指すハンドルを取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::GetSource](#getsource)|ソースを取得するには、このメソッドを呼び出し、`CAccessToken`オブジェクト。|
|[CAccessToken::GetStatistics](#getstatistics)|関連付けられている情報を取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::GetTerminalServicesSessionId](#getterminalservicessessionid)|関連付けられているターミナル サービス セッションの ID を取得するには、このメソッドを呼び出し、`CAccessToken`オブジェクト。|
|[CAccessToken::GetThreadToken](#getthreadtoken)|初期化するためには、このメソッドを呼び出して、`CAccessToken`特定のスレッドからトークンを使用します。|
|[CAccessToken::GetTokenId](#gettokenid)|関連付けられているトークンの ID を取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::GetType](#gettype)|トークンの種類を取得するには、このメソッドを呼び出し、`CAccessToken`オブジェクト。|
|[CAccessToken::GetUser](#getuser)|関連付けられているユーザーを識別するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::HKeyCurrentUser](#hkeycurrentuser)|関連付けられているユーザーのプロファイルを指すハンドルを取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::Impersonate](#impersonate)|権限の借用を割り当てるには、このメソッドを呼び出す`CAccessToken`スレッドにします。|
|[CAccessToken::ImpersonateLoggedOnUser](#impersonateloggedonuser)|ログオン ユーザーのセキュリティ コンテキストを偽装する呼び出し元のスレッドを許可するには、このメソッドを呼び出します。|
|[CAccessToken::IsTokenRestricted](#istokenrestricted)|場合をテストするには、このメソッドを呼び出す、`CAccessToken`オブジェクトには、制限付き Sid の一覧が含まれています。|
|[CAccessToken::LoadUserProfile](#loaduserprofile)|このメソッドに関連付けられているユーザー プロファイルの読み込みを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::LogonUser](#logonuser)|指定した資格情報に関連付けられているユーザーのログオン セッションを作成するには、このメソッドを呼び出します。|
|[CAccessToken::OpenCOMClientToken](#opencomclienttoken)|COM サーバーを初期化するには、クライアントから呼び出しの処理内からこのメソッドを呼び出し、 `CAccessToken` COM クライアントからアクセス トークンを使用します。|
|[CAccessToken::OpenNamedPipeClientToken](#opennamedpipeclienttoken)|初期化するために名前付きパイプ経由で取得要求をサーバーからこのメソッドを呼び出す、`CAccessToken`クライアントからアクセス トークンを使用します。|
|[CAccessToken::OpenRPCClientToken](#openrpcclienttoken)|初期化するために、RPC クライアントからの呼び出しを処理するサーバー内からこのメソッドを呼び出し、`CAccessToken`クライアントからアクセス トークンを使用します。|
|[CAccessToken::OpenThreadToken](#openthreadtoken)|権限借用レベルを設定し、初期化するには、このメソッドを呼び出す、`CAccessToken`特定のスレッドからトークンを使用します。|
|[CAccessToken::PrivilegeCheck](#privilegecheck)|指定された権限のセットが有効かどうかを確認するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::Revert](#revert)|偽装トークンを使用しているスレッドを停止するには、このメソッドを呼び出します。|
|[CAccessToken::SetDefaultDacl](#setdefaultdacl)|既定値を設定するには、このメソッドを呼び出すの DACL、`CAccessToken`オブジェクト。|
|[CAccessToken::SetOwner](#setowner)|所有者を設定するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|
|[CAccessToken::SetPrimaryGroup](#setprimarygroup)|プライマリ グループを設定するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。|

## <a name="remarks"></a>Remarks

[アクセス トークン](/windows/desktop/SecAuthZ/access-tokens)プロセスまたはスレッドのセキュリティ コンテキストを示し、Windows システムにログオンしている各ユーザーに割り当てられているオブジェクトです。

Windows でのアクセス制御モデルの概要については、次を参照してください。[アクセス制御](/windows/desktop/SecAuthZ/access-control)Windows SDK に含まれています。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsecurity.h

##  <a name="attach"></a>  CAccessToken::Attach

指定したアクセス トークンのハンドルの所有権を取得するには、このメソッドを呼び出します。

```
void Attach(HANDLE hToken) throw();
```

### <a name="parameters"></a>パラメーター

*hToken*<br/>
アクセス トークンへのハンドル。

### <a name="remarks"></a>Remarks

場合、デバッグ ビルドで、アサーション エラーが発生、`CAccessToken`オブジェクトには、アクセス トークンの所有権が既に存在します。

##  <a name="dtor"></a>  CAccessToken::~CAccessToken

デストラクターです。

```
virtual ~CAccessToken() throw();
```

### <a name="remarks"></a>Remarks

割り当てられているすべてのリソースを解放します。

##  <a name="checktokenmembership"></a>  CAccessToken::CheckTokenMembership

指定された SID が有効になっているかどうかを判断するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
bool CheckTokenMembership(
    const CSid& rSid,
    bool* pbIsMember) const throw(...);
```

### <a name="parameters"></a>パラメーター

*rSid*<br/>
参照を[CSid クラス](../../atl/reference/csid-class.md)オブジェクト。

*pbIsMember*<br/>
チェックの結果を受け取る変数へのポインター。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

`CheckTokenMembership`メソッドのユーザーとグループの Sid、アクセス トークンの SID の存在を確認します。 SID が存在し、SE_GROUP_ENABLED 属性を持つ*pbIsMember*にそれ以外の場合は TRUE を設定するには、FALSE に設定されています。

場合、デバッグ ビルドで、アサーション エラーが発生*pbIsMember*は有効なポインターではありません。

> [!NOTE]
>  `CAccessToken`偽装トークンと、プライマリのトークンではないオブジェクトがある必要があります。

##  <a name="createimpersonationtoken"></a>  CAccessToken::CreateImpersonationToken

偽装アクセス トークンを作成するには、このメソッドを呼び出します。

```
bool CreateImpersonationToken(
    CAccessToken* pImp,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pImp*<br/>
新しいポインター`CAccessToken`オブジェクト。

*sil*<br/>
指定します、 [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level)新しいトークンの偽装レベルを提供する型を列挙します。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

`CreateImpersonationToken` 呼び出し[DuplicateToken](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-duplicatetoken)新しい権限借用トークンを作成します。

##  <a name="createprimarytoken"></a>  CAccessToken::CreatePrimaryToken

新しいプライマリ トークンを作成するには、このメソッドを呼び出します。

```
bool CreatePrimaryToken(
    CAccessToken* pPri,
    DWORD dwDesiredAccess = MAXIMUM_ALLOWED,
    const CSecurityAttributes* pTokenAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pPri*<br/>
新しいポインター`CAccessToken`オブジェクト。

*dwDesiredAccess*<br/>
新しいトークンの要求されたアクセス権を指定します。 MAXIMUM_ALLOWED、既定では、呼び出し元が有効なすべてのアクセス権を要求します。 参照してください[アクセス権やアクセス マスク](/windows/desktop/SecAuthZ/access-rights-and-access-masks)詳細にアクセス権限。

*pTokenAttributes*<br/>
ポインターを[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)構造体を新しいトークンのセキュリティ記述子を指定し、子プロセスが、トークンを継承できるかどうかを決定します。 場合*pTokenAttributes* null、トークンは、既定のセキュリティ記述子を取得およびハンドルは継承できません。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

`CreatePrimaryToken` 呼び出し[DuplicateTokenEx](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-duplicatetokenex)新しいプライマリ トークンを作成します。

##  <a name="createprocessasuser"></a>  CAccessToken::CreateProcessAsUser

によって表されるユーザーのセキュリティ コンテキストで実行されている新しいプロセスを作成するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
bool CreateProcessAsUser(
    LPCTSTR pApplicationName,
    LPTSTR pCommandLine,
    LPPROCESS_INFORMATION pProcessInformation,
    LPSTARTUPINFO pStartupInfo,
    DWORD dwCreationFlags = NORMAL_PRIORITY_CLASS,
    bool bLoadProfile = false,
    const CSecurityAttributes* pProcessAttributes = NULL,
    const CSecurityAttributes* pThreadAttributes = NULL,
    bool bInherit = false,
    LPCTSTR pCurrentDirectory = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*pApplicationName*<br/>
実行するモジュールを指定する null で終わる文字列へのポインター。 このパラメーターを NULL にすることがありますはできません。

*pCommandLine*<br/>
実行するコマンドラインを指定する null で終わる文字列へのポインター。

*pProcessInformation*<br/>
ポインターを[ハンドル](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_process_information)を新しいプロセスの識別情報を受け取る構造体。

*pStartupInfo*<br/>
ポインターを[STARTUPINFO](/windows/desktop/api/processthreadsapi/ns-processthreadsapi-_startupinfoa)を新しいプロセスのメイン ウィンドウの表示方法を指定します。

*dwCreationFlags*<br/>
優先順位クラスとプロセスの作成を制御する追加のフラグを指定します。 Win32 関数を参照してください。 [CreateProcessAsUser](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessasusera)フラグの一覧についてはします。

*bLoadProfile*<br/>
ユーザーのプロファイルが読み込まれる TRUE の場合、 [LoadUserProfile](/windows/desktop/api/userenv/nf-userenv-loaduserprofilea)します。

*pProcessAttributes*<br/>
ポインターを[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)構造体を新しいプロセスのセキュリティ記述子を指定し、返されたハンドルを子プロセスが継承するかどうかを決定します。 場合*pProcessAttributes* null、プロセスは、既定のセキュリティ記述子を取得およびハンドルは継承できません。

*pThreadAttributes*<br/>
ポインターを[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560)構造体を新しいスレッドのセキュリティ記述子を指定し、返されたハンドルを子プロセスが継承するかどうかを決定します。 場合*pThreadAttributes* null、スレッドは、既定のセキュリティ記述子を取得およびハンドルは継承できません。

*bInherit*<br/>
新しいプロセスが呼び出し元のプロセスからハンドルを継承するかどうかを示します。 TRUE の場合、呼び出し元のプロセスで継承可能な各開いているハンドルは、新しいプロセスによって継承されます。 継承されたハンドルは、元のハンドルと同じ値とアクセス権限を持っています。

*pCurrentDirectory*<br/>
現在のドライブと、新しいプロセス用のディレクトリを指定する null で終わる文字列へのポインター。 文字列は、ドライブ文字を含む完全なパスである必要があります。 このパラメーターが NULL の場合、新しいプロセスは、呼び出し元プロセスとして同じの現在のドライブとディレクトリがあります。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

`CreateProcessAsUser` 使用して、`CreateProcessAsUser`によって表されるユーザーのセキュリティ コンテキストで実行されている新しいプロセスを作成する Win32 関数、`CAccessToken`オブジェクト。 説明を参照して、 [CreateProcessAsUser](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessasusera)関数に必要なパラメーターの詳細についてはします。

このメソッドが成功する、 `CAccessToken` (制限付きトークンである) 場合を除き、オブジェクトは AssignPrimaryToken を保持する必要がありますと IncreaseQuota 特権。

##  <a name="createrestrictedtoken"></a>  CAccessToken::CreateRestrictedToken

新しく作成するには、このメソッドを呼び出す制限`CAccessToken`オブジェクト。

```
bool CreateRestrictedToken(
    CAccessToken* pRestrictedToken,
    const CTokenGroups& SidsToDisable,
    const CTokenGroups& SidsToRestrict,
    const CTokenPrivileges& PrivilegesToDelete = CTokenPrivileges()) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pRestrictedToken*<br/>
新しい制限`CAccessToken`オブジェクト。

*SidsToDisable*<br/>
A`CTokenGroups`拒否専用 Sid を指定するオブジェクト。

*SidsToRestrict*<br/>
A`CTokenGroups`制限する Sid を指定するオブジェクト。

*PrivilegesToDelete*<br/>
A`CTokenPrivileges`制限付きトークンで削除する権限を指定するオブジェクト。 既定値は、空のオブジェクトを作成します。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

`CreateRestrictedToken` 使用して、 [CreateRestrictedToken](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-createrestrictedtoken) Win32 関数を新しく作成する`CAccessToken`オブジェクトは、制限があります。

> [!IMPORTANT]
>  使用する場合`CreateRestrictedToken`、以下を確認する: 既存のトークンが有効な (そして、ユーザーが入っていない) と*SidsToDisable*と*PrivilegesToDelete*が有効 (かつユーザーが入力されません)。 メソッドが FALSE を返した場合は、機能を拒否します。

##  <a name="detach"></a>  CAccessToken::Detach

アクセス トークンの所有権を取り消すには、このメソッドを呼び出します。

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>戻り値

識別するハンドルを返します、`CAccessToken`がデタッチされます。

### <a name="remarks"></a>Remarks

このメソッドでは失効、`CAccessToken`のアクセス トークンの所有者。

##  <a name="disableprivilege"></a>  CAccessToken::DisablePrivilege

特権を無効にするには、このメソッドを呼び出す、`CAccessToken`オブジェクト。

```
bool DisablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>パラメーター

*pszPrivilege*<br/>
無効にするための権限を含む文字列へのポインター、`CAccessToken`オブジェクト。

*pPreviousState*<br/>
ポインター、`CTokenPrivileges`特権の以前の状態を格納するオブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="disableprivileges"></a>  CAccessToken::DisablePrivileges

1 つまたは複数の権限を無効にするには、このメソッドを呼び出す、`CAccessToken`オブジェクト。

```
bool DisablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>パラメーター

*rPrivileges*<br/>
無効にする権限を含む文字列の配列へのポインター、`CAccessToken`オブジェクト。

*pPreviousState*<br/>
ポインター、`CTokenPrivileges`特権の以前の状態を格納するオブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="enableprivilege"></a>  CAccessToken::EnablePrivilege

特権を有効にするには、このメソッドを呼び出す、`CAccessToken`オブジェクト。

```
bool EnablePrivilege(
    LPCTSTR pszPrivilege,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>パラメーター

*pszPrivilege*<br/>
有効にするための権限を含む文字列へのポインター、`CAccessToken`オブジェクト。

*pPreviousState*<br/>
ポインター、`CTokenPrivileges`特権の以前の状態を格納するオブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="enableprivileges"></a>  CAccessToken::EnablePrivileges

1 つまたは複数の権限を有効にするには、このメソッドを呼び出す、`CAccessToken`オブジェクト。

```
bool EnablePrivileges(
    const CAtlArray<LPCTSTR>& rPrivileges,
    CTokenPrivileges* pPreviousState = NULL) throw(...);
```

### <a name="parameters"></a>パラメーター

*rPrivileges*<br/>
有効にする権限を含む文字列の配列へのポインター、`CAccessToken`オブジェクト。

*pPreviousState*<br/>
ポインター、`CTokenPrivileges`特権の以前の状態を格納するオブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="getdefaultdacl"></a>  CAccessToken::GetDefaultDacl

返すには、このメソッドを呼び出して、`CAccessToken`オブジェクトの既定の DACL。

```
bool GetDefaultDacl(CDacl* pDacl) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pDacl*<br/>
ポインター、 [CDacl クラス](../../atl/reference/cdacl-class.md)オブジェクトを受信する、`CAccessToken`オブジェクトの既定の DACL。

### <a name="return-value"></a>戻り値

既定の DACL が回復されたかどうかは TRUE を返します。

##  <a name="geteffectivetoken"></a>  CAccessToken::GetEffectiveToken

取得するには、このメソッドを呼び出して、`CAccessToken`現在のスレッドに対して有効なアクセス トークンと等しいオブジェクト。

```
bool GetEffectiveToken(DWORD dwDesiredAccess) throw();
```

### <a name="parameters"></a>パラメーター

*dwDesiredAccess*<br/>
アクセス トークンへの要求されたアクセス タイプを指定するアクセス マスクを指定します。 これらの要求されたアクセス タイプをトークンの DACL と比較することで、どのアクセスを許可するか、または拒否するかを判断します。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="getgroups"></a>  CAccessToken::GetGroups

返すには、このメソッドを呼び出して、`CAccessToken`トークンのオブジェクトのグループ。

```
bool GetGroups(CTokenGroups* pGroups) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pGroups*<br/>
ポインター、 [CTokenGroups クラス](../../atl/reference/ctokengroups-class.md)グループ情報を受信するオブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="gethandle"></a>  CAccessToken::GetHandle

アクセス トークンを識別するハンドルを取得するには、このメソッドを呼び出します。

```
HANDLE GetHandle() const throw();
```

### <a name="return-value"></a>戻り値

識別するハンドルを返します、`CAccessToken`オブジェクトのアクセス トークン。

##  <a name="getimpersonationlevel"></a>  CAccessToken::GetImpersonationLevel

アクセス トークンから偽装レベルを取得するには、このメソッドを呼び出します。

```
bool GetImpersonationLevel(
    SECURITY_IMPERSONATION_LEVEL* pImpersonationLevel) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pImpersonationLevel*<br/>
ポインターを[SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level)偽装レベルの情報を受信する列挙型。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="getlogonsessionid"></a>  CAccessToken::GetLogonSessionId

関連付けられたログオン セッションの ID を取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
bool GetLogonSessionId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pluid*<br/>
ポインターを[LUID](/windows/desktop/api/winnt/ns-winnt-_luid)ログオン セッションの id これが表示されます。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

場合、デバッグ ビルドで、アサーション エラーが発生*pluid*は無効な値です。

##  <a name="getlogonsid"></a>  CAccessToken::GetLogonSid

関連付けられたログオン SID を取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
bool GetLogonSid(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pSid*<br/>
ポインターを[CSid クラス](../../atl/reference/csid-class.md)オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

場合、デバッグ ビルドで、アサーション エラーが発生*pSid*は無効な値です。

##  <a name="getowner"></a>  CAccessToken::GetOwner

関連付けられている所有者を取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
bool GetOwner(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pSid*<br/>
ポインターを[CSid クラス](../../atl/reference/csid-class.md)オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

所有者は、既定ではこのアクセス トークンが有効なときに作成されたオブジェクトに設定されます。

##  <a name="getprimarygroup"></a>  CAccessToken::GetPrimaryGroup

関連付けられているプライマリ グループを取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
bool GetPrimaryGroup(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pSid*<br/>
ポインターを[CSid クラス](../../atl/reference/csid-class.md)オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

グループは、既定ではこのアクセス トークンが有効なときに作成されたオブジェクトに設定されます。

##  <a name="getprivileges"></a>  CAccessToken::GetPrivileges

関連付けられている特権を取得するには、このメソッドを呼び出し、`CAccessToken`オブジェクト。

```
bool GetPrivileges(CTokenPrivileges* pPrivileges) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pPrivileges*<br/>
ポインターを[CTokenPrivileges クラス](../../atl/reference/ctokenprivileges-class.md)特権を受け取るオブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="getprocesstoken"></a>  CAccessToken::GetProcessToken

指定されたプロセスからアクセス トークンを使用して `CAccessToken` を初期化するには、このメソッドを呼び出します。

```
bool GetProcessToken(DWORD dwDesiredAccess, HANDLE hProcess = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*dwDesiredAccess*<br/>
アクセス トークンへの要求されたアクセス タイプを指定するアクセス マスクを指定します。 これらの要求されたアクセス タイプをトークンの DACL と比較することで、どのアクセスを許可するか、または拒否するかを判断します。

*hProcess*<br/>
アクセス トークンが開いているプロセスへのハンドル。 既定値は NULL を使用する場合は、現在のプロセスが使用されます。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

呼び出し、 [OpenProcessToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-openprocesstoken) Win32 関数。

##  <a name="getprofile"></a>  CAccessToken::GetProfile

関連付けられているユーザーのプロファイルを指すハンドルを取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
HANDLE GetProfile() const throw();
```

### <a name="return-value"></a>戻り値

プロファイルが存在しない場合に、ユーザー プロファイル、または NULL を指すハンドルを返します。

##  <a name="getsource"></a>  CAccessToken::GetSource

ソースを取得するには、このメソッドを呼び出し、`CAccessToken`オブジェクト。

```
bool GetSource(TOKEN_SOURCE* pSource) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pSource*<br/>
ポインターを[TOKEN_SOURCE](/windows/desktop/api/winnt/ns-winnt-_token_source)構造体。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="getstatistics"></a>  CAccessToken::GetStatistics

関連付けられている情報を取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
bool GetStatistics(TOKEN_STATISTICS* pStatistics) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pStatistics*<br/>
ポインターを[TOKEN_STATISTICS](/windows/desktop/api/winnt/ns-winnt-_token_statistics)構造体。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="getterminalservicessessionid"></a>  CAccessToken::GetTerminalServicesSessionId

関連付けられているターミナル サービス セッションの ID を取得するには、このメソッドを呼び出し、`CAccessToken`オブジェクト。

```
bool GetTerminalServicesSessionId(DWORD* pdwSessionId) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pdwSessionId*<br/>
ターミナル サービス セッションの id。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="getthreadtoken"></a>  CAccessToken::GetThreadToken

初期化するためには、このメソッドを呼び出して、`CAccessToken`特定のスレッドからトークンを使用します。

```
bool GetThreadToken(
    DWORD dwDesiredAccess,
    HANDLE hThread = NULL,
    bool bOpenAsSelf = true) throw();
```

### <a name="parameters"></a>パラメーター

*dwDesiredAccess*<br/>
アクセス トークンへの要求されたアクセス タイプを指定するアクセス マスクを指定します。 これらの要求されたアクセス タイプをトークンの DACL と比較することで、どのアクセスを許可するか、または拒否するかを判断します。

*hThread*<br/>
アクセス トークンを開いたスレッドへのハンドルします。

*bOpenAsSelf*<br/>
アクセス チェックが、スレッドの呼び出し元のセキュリティ コンテキストに対して行われるかどうかを示す、`GetThreadToken`メソッドまたは呼び出し元のスレッドのプロセスのセキュリティ コンテキスト。

このパラメーターが FALSE の場合は、呼び出し元のスレッドのセキュリティ コンテキストを使用してアクセス チェックが実行されます。 スレッドは、クライアントを偽装する場合のクライアント プロセスをこのセキュリティ コンテキストにできます。 このパラメーターが TRUE の場合、呼び出し元のスレッドのプロセスのセキュリティ コンテキストを使用してアクセス チェックを実行します。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="gettokenid"></a>  CAccessToken::GetTokenId

関連付けられているトークンの ID を取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
bool GetTokenId(LUID* pluid) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pluid*<br/>
ポインターを[LUID](/windows/desktop/api/winnt/ns-winnt-_luid)トークンの ID が表示されます

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="gettype"></a>  CAccessToken::GetType

トークンの種類を取得するには、このメソッドを呼び出し、`CAccessToken`オブジェクト。

```
bool GetType(TOKEN_TYPE* pType) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pType*<br/>
アドレス、 [TOKEN_TYPE](/windows/desktop/api/winnt/ne-winnt-_token_type)成功した場合、トークンの種類を受け取る変数。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

TOKEN_TYPE 列挙型には、プライマリ トークンと権限借用トークンを区別する値が含まれています。

##  <a name="getuser"></a>  CAccessToken::GetUser

関連付けられているユーザーを識別するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
bool GetUser(CSid* pSid) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pSid*<br/>
ポインターを[CSid クラス](../../atl/reference/csid-class.md)オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="hkeycurrentuser"></a>  CAccessToken::HKeyCurrentUser

関連付けられているユーザーのプロファイルを指すハンドルを取得するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
HKEY HKeyCurrentUser() const throw();
```

### <a name="return-value"></a>戻り値

プロファイルが存在しない場合に、ユーザー プロファイル、または NULL を指すハンドルを返します。

##  <a name="impersonate"></a>  CAccessToken::Impersonate

権限の借用を割り当てるには、このメソッドを呼び出す`CAccessToken`スレッドにします。

```
bool Impersonate(HANDLE hThread = NULL) const throw(...);
```

### <a name="parameters"></a>パラメーター

*hThread*<br/>
スレッドの偽装トークンを割り当てるへのハンドルします。 TOKEN_IMPERSONATE アクセス権を持つこのハンドルが開かれているがある必要があります。 場合*hThread*が null の場合、このメソッドにより、スレッドの偽装トークンを使用して停止します。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

場合、デバッグ ビルドで、アサーション エラーが発生`CAccessToken`をトークンに有効なポインターはありません。

[CAutoRevertImpersonation クラス](../../atl/reference/cautorevertimpersonation-class.md)権限を借用したアクセス トークンを自動的に元に戻すために使用できます。

##  <a name="impersonateloggedonuser"></a>  CAccessToken::ImpersonateLoggedOnUser

ログオン ユーザーのセキュリティ コンテキストを偽装する呼び出し元のスレッドを許可するには、このメソッドを呼び出します。

```
bool ImpersonateLoggedOnUser() const throw(...);
```

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

> [!IMPORTANT]
>  偽装関数を呼び出すには、何らかの理由で失敗すると、クライアントを偽装はいないと、呼び出しが行われた処理のセキュリティ コンテキストで、クライアントの要求が行われます。 プロセスが、高い特権を持つアカウントとして実行されているか、管理グループのメンバーは、ユーザーがアクションを実行することがあります場合、かは許可されません。 そのため、この関数の戻り値常に確認する必要があります。

##  <a name="istokenrestricted"></a>  CAccessToken::IsTokenRestricted

場合をテストするには、このメソッドを呼び出す、`CAccessToken`オブジェクトには、制限付き Sid の一覧が含まれています。

```
bool IsTokenRestricted() const throw();
```

### <a name="return-value"></a>戻り値

オブジェクトには、FALSE、Sid を制限する Sid を制限することがない場合の一覧が含まれている場合、またはメソッドが失敗した場合、TRUE を返します。

##  <a name="loaduserprofile"></a>  CAccessToken::LoadUserProfile

このメソッドに関連付けられているユーザー プロファイルの読み込みを呼び出して、`CAccessToken`オブジェクト。

```
bool LoadUserProfile() throw(...);
```

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

場合、デバッグ ビルドで、アサーション エラーが発生、`CAccessToken`有効なトークンが含まれていないか、またはユーザーが既にプロファイルが。

##  <a name="logonuser"></a>  CAccessToken::LogonUser

指定した資格情報に関連付けられているユーザーのログオン セッションを作成するには、このメソッドを呼び出します。

```
bool LogonUser(
    LPCTSTR pszUserName,
    LPCTSTR pszDomain,
    LPCTSTR pszPassword,
    DWORD dwLogonType = LOGON32_LOGON_INTERACTIVE,
    DWORD dwLogonProvider = LOGON32_PROVIDER_DEFAULT) throw();
```

### <a name="parameters"></a>パラメーター

*pszUserName*<br/>
ユーザー名を指定する null で終わる文字列へのポインター。 これにログオンするユーザー アカウントの名前です。

*pszDomain*<br/>
ドメインまたはのアカウント データベースを含むサーバーの名前を指定する null で終わる文字列へのポインター、 *pszUserName*アカウント。

*pszPassword*<br/>
指定されたユーザー アカウントのクリア テキスト パスワードを指定する null で終わる文字列へのポインター *pszUserName*します。

*dwLogonType*<br/>
実行するログオン操作の種類を指定します。 参照してください[LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera)の詳細。

*dwLogonProvider*<br/>
ログオンのプロバイダーを指定します。 参照してください[LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera)の詳細。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

関連付けられる、ログオンによるトークンへのアクセス、`CAccessToken`します。 このメソッドが成功する、`CAccessToken`オブジェクトの基本の信頼されたコンピューターの一部として、所有者を識別する、SE_TCB_NAME 特権を保持する必要があります。 参照してください[LogonUser](/windows/desktop/api/winbase/nf-winbase-logonusera)必要な権限に関する詳細についてはします。

##  <a name="opencomclienttoken"></a>  CAccessToken::OpenCOMClientToken

COM サーバーを初期化するには、クライアントから呼び出しの処理内からこのメソッドを呼び出し、 `CAccessToken` COM クライアントからアクセス トークンを使用します。

```
bool OpenCOMClientToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>パラメーター

*dwDesiredAccess*<br/>
アクセス トークンへの要求されたアクセス タイプを指定するアクセス マスクを指定します。 これらの要求されたアクセス タイプをトークンの DACL と比較することで、どのアクセスを許可するか、または拒否するかを判断します。

*bImpersonate*<br/>
TRUE の場合、この呼び出しが正常に完了した場合、現在のスレッドは呼び出し元の COM クライアントを偽装します。 FALSE の場合は、アクセス トークンが開きますが、この呼び出しが完了すると、スレッドは、権限借用トークンを持ちません。

*bOpenAsSelf*<br/>
アクセス チェックが、スレッドの呼び出し元のセキュリティ コンテキストに対して行われるかどうかを示す、 [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)メソッドまたは呼び出し元のスレッドのプロセスのセキュリティ コンテキスト。

このパラメーターが FALSE の場合は、呼び出し元のスレッドのセキュリティ コンテキストを使用してアクセス チェックが実行されます。 スレッドは、クライアントを偽装する場合のクライアント プロセスをこのセキュリティ コンテキストにできます。 このパラメーターが TRUE の場合、呼び出し元のスレッドのプロセスのセキュリティ コンテキストを使用してアクセス チェックを実行します。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

[CAutoRevertImpersonation クラス](../../atl/reference/cautorevertimpersonation-class.md)できますを使用して自動的に設定して作成された権限を借用したアクセス トークンを戻す、 *bImpersonate*フラグを TRUE にします。

##  <a name="opennamedpipeclienttoken"></a>  CAccessToken::OpenNamedPipeClientToken

初期化するために名前付きパイプ経由で取得要求をサーバーからこのメソッドを呼び出す、`CAccessToken`クライアントからアクセス トークンを使用します。

```
bool OpenNamedPipeClientToken(
    HANDLE hPipe,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>パラメーター

*hPipe*<br/>
名前付きパイプへのハンドルします。

*dwDesiredAccess*<br/>
アクセス トークンへの要求されたアクセス タイプを指定するアクセス マスクを指定します。 これらの要求されたアクセス タイプをトークンの DACL と比較することで、どのアクセスを許可するか、または拒否するかを判断します。

*bImpersonate*<br/>
TRUE の場合、この呼び出しが正常に完了した場合、現在のスレッドは呼び出し元のパイプ クライアントを偽装します。 FALSE の場合は、アクセス トークンが開きますが、この呼び出しが完了すると、スレッドは、権限借用トークンを持ちません。

*bOpenAsSelf*<br/>
アクセス チェックが、スレッドの呼び出し元のセキュリティ コンテキストに対して行われるかどうかを示す、 [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)メソッドまたは呼び出し元のスレッドのプロセスのセキュリティ コンテキスト。

このパラメーターが FALSE の場合は、呼び出し元のスレッドのセキュリティ コンテキストを使用してアクセス チェックが実行されます。 スレッドは、クライアントを偽装する場合のクライアント プロセスをこのセキュリティ コンテキストにできます。 このパラメーターが TRUE の場合、呼び出し元のスレッドのプロセスのセキュリティ コンテキストを使用してアクセス チェックを実行します。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

[CAutoRevertImpersonation クラス](../../atl/reference/cautorevertimpersonation-class.md)できますを使用して自動的に設定して作成された権限を借用したアクセス トークンを戻す、 *bImpersonate*フラグを TRUE にします。

##  <a name="openrpcclienttoken"></a>  CAccessToken::OpenRPCClientToken

初期化するために、RPC クライアントからの呼び出しを処理するサーバー内からこのメソッドを呼び出し、`CAccessToken`クライアントからアクセス トークンを使用します。

```
bool OpenRPCClientToken(
    RPC_BINDING_HANDLE BindingHandle,
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true) throw(...);
```

### <a name="parameters"></a>パラメーター

*BindingHandle*<br/>
クライアントへのバインドを表す、サーバーにバインド ハンドル。

*dwDesiredAccess*<br/>
アクセス トークンへの要求されたアクセス タイプを指定するアクセス マスクを指定します。 これらの要求されたアクセス タイプをトークンの DACL と比較することで、どのアクセスを許可するか、または拒否するかを判断します。

*bImpersonate*<br/>
TRUE の場合、この呼び出しが正常に完了した場合、現在のスレッドは呼び出し元の RPC クライアントを偽装します。 FALSE の場合は、アクセス トークンが開きますが、この呼び出しが完了すると、スレッドは、権限借用トークンを持ちません。

*bOpenAsSelf*<br/>
アクセス チェックが、スレッドの呼び出し元のセキュリティ コンテキストに対して行われるかどうかを示す、 [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)メソッドまたは呼び出し元のスレッドのプロセスのセキュリティ コンテキスト。

このパラメーターが FALSE の場合は、呼び出し元のスレッドのセキュリティ コンテキストを使用してアクセス チェックが実行されます。 スレッドは、クライアントを偽装する場合のクライアント プロセスをこのセキュリティ コンテキストにできます。 このパラメーターが TRUE の場合、呼び出し元のスレッドのプロセスのセキュリティ コンテキストを使用してアクセス チェックを実行します。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

[CAutoRevertImpersonation クラス](../../atl/reference/cautorevertimpersonation-class.md)できますを使用して自動的に設定して作成された権限を借用したアクセス トークンを戻す、 *bImpersonate*フラグを TRUE にします。

##  <a name="openthreadtoken"></a>  CAccessToken::OpenThreadToken

権限借用レベルを設定し、初期化するには、このメソッドを呼び出す、`CAccessToken`特定のスレッドからトークンを使用します。

```
bool OpenThreadToken(
    DWORD dwDesiredAccess,
    bool bImpersonate = false,
    bool bOpenAsSelf = true,
    SECURITY_IMPERSONATION_LEVEL sil = SecurityImpersonation) throw(...);
```

### <a name="parameters"></a>パラメーター

*dwDesiredAccess*<br/>
アクセス トークンへの要求されたアクセス タイプを指定するアクセス マスクを指定します。 これらの要求されたアクセス タイプをトークンの DACL と比較することで、どのアクセスを許可するか、または拒否するかを判断します。

*bImpersonate*<br/>
TRUE の場合、メソッドの完了後、スレッドは、要求された権限借用レベルで左は。 FALSE の場合、スレッドは元の偽装レベルに戻ります。

*bOpenAsSelf*<br/>
アクセス チェックが、スレッドの呼び出し元のセキュリティ コンテキストに対して行われるかどうかを示す、 [GetThreadToken](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getcurrentthread)メソッドまたは呼び出し元のスレッドのプロセスのセキュリティ コンテキスト。

このパラメーターが FALSE の場合は、呼び出し元のスレッドのセキュリティ コンテキストを使用してアクセス チェックが実行されます。 スレッドは、クライアントを偽装する場合のクライアント プロセスをこのセキュリティ コンテキストにできます。 このパラメーターが TRUE の場合、呼び出し元のスレッドのプロセスのセキュリティ コンテキストを使用してアクセス チェックを実行します。

*sil*<br/>
指定します、 [SECURITY_IMPERSONATION_LEVEL](/windows/desktop/api/winnt/ne-winnt-_security_impersonation_level)トークンの偽装レベルを提供する型を列挙します。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

`OpenThreadToken` ような[CAccessToken::GetThreadToken](#getthreadtoken)、初期化する前に、偽装レベルを設定が、`CAccessToken`スレッドのアクセス トークンから。

[CAutoRevertImpersonation クラス](../../atl/reference/cautorevertimpersonation-class.md)できますを使用して自動的に設定して作成された権限を借用したアクセス トークンを戻す、 *bImpersonate*フラグを TRUE にします。

##  <a name="privilegecheck"></a>  CAccessToken::PrivilegeCheck

指定された権限のセットが有効かどうかを確認するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
bool PrivilegeCheck(
    PPRIVILEGE_SET RequiredPrivileges,
    bool* pbResult) const throw();
```

### <a name="parameters"></a>パラメーター

*RequiredPrivileges*<br/>
ポインターを[PRIVILEGE_SET](/windows/desktop/api/winnt/ns-winnt-_privilege_set)構造体。

*pbResult*<br/>
メソッドが設定を指定した権限の一部またはすべてがで有効かどうかを示す値へのポインター、`CAccessToken`オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

ときに`PrivilegeCheck`から制御が戻る、`Attributes`のそれぞれに所属[LUID_AND_ATTRIBUTES](/windows/desktop/api/winnt/ns-winnt-_luid_and_attributes)対応する特権が有効になっている場合は、構造体を SE_PRIVILEGE_USED_FOR_ACCESS に設定します。 このメソッドは、 [PrivilegeCheck](/windows/desktop/api/securitybaseapi/nf-securitybaseapi-privilegecheck) Win32 関数。

##  <a name="revert"></a>  CAccessToken::Revert

権限借用トークンを使用してからスレッドを停止するには、このメソッドを呼び出します。

```
bool Revert(HANDLE hThread = NULL) const throw();
```

### <a name="parameters"></a>パラメーター

*hThread*<br/>
スレッドの偽装を元に戻すへのハンドルします。 場合*hThread*が null の場合、現在のスレッドが使用されます。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

権限借用トークンの元に戻す処理を自動的に実行できる、 [CAutoRevertImpersonation クラス](../../atl/reference/cautorevertimpersonation-class.md)します。

##  <a name="setdefaultdacl"></a>  CAccessToken::SetDefaultDacl

既定値を設定するには、このメソッドを呼び出すの DACL、`CAccessToken`オブジェクト。

```
bool SetDefaultDacl(const CDacl& rDacl) throw(...);
```

### <a name="parameters"></a>パラメーター

*rDacl*<br/>
新しい既定[CDacl クラス](../../atl/reference/cdacl-class.md)情報。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

既定の DACL は、新しいオブジェクトがこのアクセス トークンが有効で作成されたときに、既定で使用される DACL です。

##  <a name="setowner"></a>  CAccessToken::SetOwner

所有者を設定するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
bool SetOwner(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>パラメーター

*rSid*<br/>
[CSid クラス](../../atl/reference/csid-class.md)所有者情報を含むオブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

所有者は、このアクセス トークンが有効なときに作成された新しいオブジェクトに使用される既定の所有者です。

##  <a name="setprimarygroup"></a>  CAccessToken::SetPrimaryGroup

プライマリ グループを設定するには、このメソッドを呼び出して、`CAccessToken`オブジェクト。

```
bool SetPrimaryGroup(const CSid& rSid) throw(...);
```

### <a name="parameters"></a>パラメーター

*rSid*<br/>
[CSid クラス](../../atl/reference/csid-class.md)プライマリ グループ情報を含むオブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

プライマリ グループは、このアクセス トークンが有効なときに作成された新しいオブジェクトの既定のグループです。

## <a name="see-also"></a>関連項目

[ATLSecurity サンプル](../../visual-cpp-samples.md)<br/>
[アクセス トークン](/windows/desktop/SecAuthZ/access-tokens)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
