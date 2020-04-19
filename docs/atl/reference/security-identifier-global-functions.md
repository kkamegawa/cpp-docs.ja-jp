---
title: セキュリティ識別子に関するグローバル関数
ms.date: 11/04/2016
f1_keywords:
- atlsecurity/ATL::Sids::AccountOps
- atlsecurity/ATL::Sids::Admins
- atlsecurity/ATL::Sids::AnonymousLogon
- atlsecurity/ATL::Sids::AuthenticatedUser
- atlsecurity/ATL::Sids::BackupOps
- atlsecurity/ATL::Sids::Batch
- atlsecurity/ATL::Sids::CreatorGroup
- atlsecurity/ATL::Sids::CreatorGroupServer
- atlsecurity/ATL::Sids::CreatorOwner
- atlsecurity/ATL::Sids::CreatorOwnerServer
- atlsecurity/ATL::Sids::Dialup
- atlsecurity/ATL::Sids::Guests
- atlsecurity/ATL::Sids::Interactive
- atlsecurity/ATL::Sids::Local
- atlsecurity/ATL::Sids::Network
- atlsecurity/ATL::Sids::NetworkService
- atlsecurity/ATL::Sids::Null
- atlsecurity/ATL::Sids::PowerUsers
- atlsecurity/ATL::Sids::PrintOps
- atlsecurity/ATL::Sids::Proxy
- atlsecurity/ATL::Sids::RasServers
- atlsecurity/ATL::Sids::Replicator
- atlsecurity/ATL::Sids::RestrictedCode
- atlsecurity/ATL::Sids::Self
- atlsecurity/ATL::Sids::ServerLogon
- atlsecurity/ATL::Sids::Service
- atlsecurity/ATL::Sids::System
- atlsecurity/ATL::Sids::SystemOps
- atlsecurity/ATL::Sids::TerminalServer
- atlsecurity/ATL::Sids::Users
- atlsecurity/ATL::Sids::World
helpviewer_keywords:
- security IDs [C++]
- SIDs [C++], returning SID objects
ms.assetid: 85404dcb-c59b-4535-ab3d-66cfa37e87de
ms.openlocfilehash: ab5d743c7c6abf7ee3a849a28916ebd32788ef40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62274946"
---
# <a name="security-identifier-global-functions"></a>セキュリティ識別子に関するグローバル関数

これらの関数は、オブジェクトに共通の既知の SID を返します。

> [!IMPORTANT]
>  Windows ランタイムで実行するアプリケーションでは、次の表に示す関数を使用できません。

|||
|-|-|
|[Sids::AccountOps](#accountops)|DOMAIN_ALIAS_RID_ACCOUNT_OPS SID を返します。|
|[Sids::Admins](#admins)|DOMAIN_ALIAS_RID_ADMINS SID を返します。|
|[Sids::AnonymousLogon](#anonymouslogon)|SECURITY_ANONYMOUS_LOGON_RID SID を返します。|
|[Sids::AuthenticatedUser](#authenticateduser)|SECURITY_AUTHENTICATED_USER_RID SID を返します。|
|[Sids::BackupOps](#backupops)|DOMAIN_ALIAS_RID_BACKUP_OPS SID を返します。|
|[Sids::Batch](#batch)|SECURITY_BATCH_RID SID を返します。|
|[Sids::CreatorGroup](#creatorgroup)|SECURITY_CREATOR_GROUP_RID SID を返します。|
|[Sids::CreatorGroupServer](#creatorgroupserver)|SECURITY_CREATOR_GROUP_SERVER_RID SID を返します。|
|[Sids::CreatorOwner](#creatorowner)|SECURITY_CREATOR_OWNER_RID SID を返します。|
|[Sids::CreatorOwnerServer](#creatorownerserver)|SECURITY_CREATOR_OWNER_SERVER_RID SID を返します。|
|[Sids::Dialup](#dialup)|SECURITY_DIALUP_RID SID を返します。|
|[Sids::Guests](#guests)|DOMAIN_ALIAS_RID_GUESTS SID を返します。|
|[Sids::Interactive](#interactive)|SECURITY_INTERACTIVE_RID SID を返します。|
|[Sids::Local](#local)|SECURITY_LOCAL_RID SID を返します。|
|[Sids::Network](#network)|SECURITY_NETWORK_RID SID を返します。|
|[Sids::NetworkService](#networkservice)|SECURITY_NETWORK_SERVICE_RID SID を返します。|
|[Sids::Null](#null)|SECURITY_NULL_RID SID を返します。|
|[Sids::PreW2KAccess](#prew2kaccess)|DOMAIN_ALIAS_RID_PREW2KCOMPACCESS SID を返します。|
|[Sids::PowerUsers](#powerusers)|DOMAIN_ALIAS_RID_POWER_USERS SID を返します。|
|[Sids::PrintOps](#printops)|DOMAIN_ALIAS_RID_PRINT_OPS SID を返します。|
|[Sids::Proxy](#proxy)|SECURITY_PROXY_RID SID を返します。|
|[Sids::RasServers](#rasservers)|DOMAIN_ALIAS_RID_RAS_SERVERS SID を返します。|
|[Sids::Replicator](#replicator)|DOMAIN_ALIAS_RID_REPLICATOR SID を返します。|
|[Sids::RestrictedCode](#restrictedcode)|SECURITY_RESTRICTED_CODE_RID SID を返します。|
|[Sids::Self](#self)|SECURITY_PRINCIPAL_SELF_RID SID を返します。|
|[Sids::ServerLogon](#serverlogon)|SECURITY_SERVER_LOGON_RID SID を返します。|
|[Sids::Service](#service)|SECURITY_SERVICE_RID SID を返します。|
|[Sids::System](#system)|SECURITY_LOCAL_SYSTEM_RID SID を返します。|
|[Sids::SystemOps](#systemops)|DOMAIN_ALIAS_RID_SYSTEM_OPS SID を返します。|
|[Sids::TerminalServer](#terminalserver)|SECURITY_TERMINAL_SERVER_RID SID を返します。|
|[Sids::Users](#users)|DOMAIN_ALIAS_RID_USERS SID を返します。|
|[Sids::World](#world)|SECURITY_WORLD_RID SID を返します。|

### <a name="requirements"></a>必要条件

**ヘッダー:** atlsecurity.h

##  <a name="accountops"></a>  Sids::AccountOps

DOMAIN_ALIAS_RID_ACCOUNT_OPS SID を返します。

```
CSid AccountOps() throw(...);
```

##  <a name="admins"></a>  Sids::Admins

DOMAIN_ALIAS_RID_ADMINS SID を返します。

```
CSid Admins() throw(...);
```

##  <a name="anonymouslogon"></a>  Sids::AnonymousLogon

SECURITY_ANONYMOUS_LOGON_RID SID を返します。

```
CSid AnonymousLogon() throw(...);
```

##  <a name="authenticateduser"></a>  Sids::AuthenticatedUser

SECURITY_AUTHENTICATED_USER_RID SID を返します。

```
CSid AuthenticatedUser() throw(...);
```

##  <a name="backupops"></a>  Sids::BackupOps

DOMAIN_ALIAS_RID_BACKUP_OPS SID を返します。

```
CSid BackupOps() throw(...);
```

##  <a name="batch"></a>  Sids::Batch

SECURITY_BATCH_RID SID を返します。

```
CSid Batch() throw(...);
```

##  <a name="creatorgroup"></a>  Sids::CreatorGroup

SECURITY_CREATOR_GROUP_RID SID を返します。

```
CSid CreatorGroup() throw(...);
```

##  <a name="creatorgroupserver"></a>  Sids::CreatorGroupServer

SECURITY_CREATOR_GROUP_SERVER_RID SID を返します。

```
CSid CreatorGroupServer() throw(...);
```

##  <a name="creatorowner"></a>  Sids::CreatorOwner

SECURITY_CREATOR_OWNER_RID SID を返します。

```
CSid CreatorOwner() throw(...);
```

##  <a name="creatorownerserver"></a>  Sids::CreatorOwnerServer

SECURITY_CREATOR_OWNER_SERVER_RID SID を返します。

```
CSid CreatorOwnerServer() throw(...);
```

##  <a name="dialup"></a>  Sids::Dialup

SECURITY_DIALUP_RID SID を返します。

```
CSid Dialup() throw(...);
```

##  <a name="guests"></a>  Sids::Guests

DOMAIN_ALIAS_RID_GUESTS SID を返します。

```
CSid Guests() throw(...);
```

##  <a name="interactive"></a>  Sids::Interactive

SECURITY_INTERACTIVE_RID SID を返します。

```
CSid Interactive() throw(...);
```

##  <a name="local"></a>  Sids::Local

SECURITY_LOCAL_RID SID を返します。

```
CSid Local() throw(...);
```

##  <a name="network"></a>  Sids::Network

SECURITY_NETWORK_RID SID を返します。

```
CSid Network() throw(...);
```

##  <a name="networkservice"></a>  Sids::NetworkService

SECURITY_NETWORK_SERVICE_RID SID を返します。

```
CSid NetworkService() throw(...);
```

### <a name="remarks"></a>Remarks

CPerfMon のセキュリティ オブジェクトの読み取りに NT authority \networkservice ユーザーを有効にするのにには、NetworkService を使用します。 NetworkService は、DLL は Windows XP Home Edition、Windows XP Professional、Windows Server 2003、およびオペレーティング システムが大きいの NetworkService アカウントでログインできるように ATLServer コードに、SecurityAttribute を追加します。

カスタム ログのカウンターがパフォーマンス モニター mmc ATLServer CPerfMon クラスを使用して作成されると、リアルタイム ビューに正しく表示されますが、ログ ファイルを表示するときに、カウンターが表示されません。 CPerfMon カスタム パフォーマンス カウンターは、Windows XP Home Edition、Windows XP Professional、windows Server 2003 (またはそれ以上) のオペレーティング システム (smlogsvc.exe)「パフォーマンス ログと警告」のサービスで実行するために必要なアクセス許可を必要はありません。 このサービスは、"NT authority \networkservice"のアカウントで実行されます。

##  <a name="null"></a>  Sids::Null

SECURITY_NULL_RID SID を返します。

```
CSid Null() throw(...);
```

##  <a name="prew2kaccess"></a>  Sids::PreW2KAccess

DOMAIN_ALIAS_RID_PREW2KCOMPACCESS SID を返します。

```
CSid PreW2KAccess() throw(...);
```

##  <a name="powerusers"></a>  Sids::PowerUsers

DOMAIN_ALIAS_RID_POWER_USERS SID を返します。

```
CSid PowerUsers() throw(...);
```

##  <a name="printops"></a>  Sids::PrintOps

DOMAIN_ALIAS_RID_PRINT_OPS SID を返します。

```
CSid PrintOps() throw(...);
```

##  <a name="proxy"></a>  Sids::Proxy

SECURITY_PROXY_RID SID を返します。

```
CSid Proxy() throw(...);
```

##  <a name="rasservers"></a>  Sids::RasServers

DOMAIN_ALIAS_RID_RAS_SERVERS SID を返します。

```
CSid RasServers() throw(...);
```

##  <a name="replicator"></a>  Sids::Replicator

DOMAIN_ALIAS_RID_REPLICATOR SID を返します。

```
CSid Replicator() throw(...);
```

##  <a name="restrictedcode"></a>  Sids::RestrictedCode

SECURITY_RESTRICTED_CODE_RID SID を返します。

```
CSid RestrictedCode() throw(...);
```

##  <a name="self"></a>  Sids::Self

SECURITY_PRINCIPAL_SELF_RID SID を返します。

```
CSid Self() throw(...);
```

##  <a name="serverlogon"></a>  Sids::ServerLogon

SECURITY_SERVER_LOGON_RID SID を返します。

```
CSid ServerLogon() throw(...);
```

##  <a name="service"></a>  Sids::Service

SECURITY_SERVICE_RID SID を返します。

```
CSid Service() throw(...);
```

##  <a name="system"></a>  Sids::System

SECURITY_LOCAL_SYSTEM_RID SID を返します。

```
CSid System() throw(...);
```

##  <a name="systemops"></a>  Sids::SystemOps

DOMAIN_ALIAS_RID_SYSTEM_OPS SID を返します。

```
CSid SystemOps() throw(...);
```

##  <a name="terminalserver"></a>  Sids::TerminalServer

SECURITY_TERMINAL_SERVER_RID SID を返します。

```
CSid TerminalServer() throw(...);
```

##  <a name="users"></a>  Sids::Users

DOMAIN_ALIAS_RID_USERS SID を返します。

```
CSid Users() throw(...);
```

##  <a name="world"></a>  Sids::World

SECURITY_WORLD_RID SID を返します。

```
CSid World() throw(...);
```

## <a name="see-also"></a>関連項目

[関数](../../atl/reference/atl-functions.md)
