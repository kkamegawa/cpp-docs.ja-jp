---
title: CAutoRevertImpersonation クラス
ms.date: 11/04/2016
f1_keywords:
- CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::CAutoRevertImpersonation
- ATLSECURITY/ATL::CAutoRevertImpersonation::Attach
- ATLSECURITY/ATL::CAutoRevertImpersonation::Detach
- ATLSECURITY/ATL::CAutoRevertImpersonation::GetAccessToken
helpviewer_keywords:
- CAutoRevertImpersonation class
ms.assetid: 43732849-1940-4bd4-9d52-7a5698bb8838
ms.openlocfilehash: f1941bfcd7689ab9d22f5094af0eb833a84dab6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497686"
---
# <a name="cautorevertimpersonation-class"></a>CAutoRevertImpersonation クラス

このクラスは、スコープ外に出ると、 [CAccessToken](../../atl/reference/caccesstoken-class.md)オブジェクトを非偽装状態に戻します。

## <a name="syntax"></a>構文

```
class CAutoRevertImpersonation
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAutoRevertImpersonation::CAutoRevertImpersonation](#cautorevertimpersonation)|オブジェクトを`CAutoRevertImpersonation`構築します。|
|[CAutoRevertImpersonation:: ~ CAutoRevertImpersonation](#dtor)|オブジェクトを破棄し、アクセストークンの偽装を元に戻します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAutoRevertImpersonation:: Attach](#attach)|アクセストークンの偽装再設定を自動化します。|
|[CAutoRevertImpersonation::D etach](#detach)|自動偽装再設定をキャンセルします。|
|[CAutoRevertImpersonation:: GetAccessToken](#getaccesstoken)|このオブジェクトに関連付けられているアクセストークンを取得します。|

## <a name="remarks"></a>Remarks

[アクセストークン](/windows/win32/SecAuthZ/access-tokens)は、プロセスまたはスレッドのセキュリティコンテキストを記述するオブジェクトで、windows NT または windows 2000 システムにログオンした各ユーザーに割り当てられます。 これらのアクセストークンは、 `CAccessToken`クラスを使用して表すことができます。

アクセストークンの偽装が必要になる場合があります。 このクラスは便利な方法として提供されていますが、アクセストークンの偽装は実行されません。非偽装状態の自動再設定のみを実行します。 これは、トークンアクセスの偽装をいくつかの方法で実行できるためです。

Windows のアクセス制御モデルの概要については、Windows SDK の「 [Access Control](/windows/win32/SecAuthZ/access-control) 」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsecurity .h

##  <a name="attach"></a>CAutoRevertImpersonation:: Attach

アクセストークンの偽装再設定を自動化します。

```
void Attach(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>パラメーター

*pAT*<br/>
自動的に元に戻される[CAccessToken](../../atl/reference/caccesstoken-class.md)オブジェクトのアドレス

### <a name="remarks"></a>Remarks

このメソッドは、 [CAutoRevertImpersonation](../../atl/reference/cautorevertimpersonation-class.md)オブジェクトが NULL `CAccessToken`ポインターを使用して作成された場合、または[デタッチ](#detach)が以前に呼び出された場合にのみ使用してください。 単純なケースでは、このメソッドを使用する必要はありません。

##  <a name="cautorevertimpersonation"></a>CAutoRevertImpersonation::CAutoRevertImpersonation

`CAutoRevertImpersonation` オブジェクトを構築します。

```
CAutoRevertImpersonation(const CAccessToken* pAT) throw();
```

### <a name="parameters"></a>パラメーター

*pAT*<br/>
自動的に元に戻される[CAccessToken](../../atl/reference/caccesstoken-class.md)オブジェクトのアドレス。

### <a name="remarks"></a>Remarks

アクセストークンの実際の偽装は、 `CAutoRevertImpersonation`オブジェクトの作成前とは別に実行する必要があります。 オブジェクトがスコープ外に出ると、 `CAutoRevertImpersonation`この偽装は自動的に元に戻されます。

##  <a name="dtor"></a>CAutoRevertImpersonation:: ~ CAutoRevertImpersonation

オブジェクトを破棄し、アクセストークンの偽装を元に戻します。

```
~CAutoRevertImpersonation() throw();
```

### <a name="remarks"></a>Remarks

構築時または[Attach](#attach)メソッドを使用して提供された[CAccessToken](../../atl/reference/caccesstoken-class.md)オブジェクトに対して現在有効な偽装を元に戻します。 `CAccessToken`が関連付けられていない場合、デストラクターは無効になります。

##  <a name="detach"></a>CAutoRevertImpersonation::D etach

自動偽装再設定をキャンセルします。

```
const CAccessToken* Detach() throw();
```

### <a name="return-value"></a>戻り値

以前に関連付けられた[CAccessToken](../../atl/reference/caccesstoken-class.md)のアドレス。または、関連付けが存在しない場合は NULL。

### <a name="remarks"></a>Remarks

**Detach**を呼び出す`CAutoRevertImpersonation`と、オブジェクトは、このオブジェクトに関連付けられている[CAccessToken](../../atl/reference/caccesstoken-class.md)オブジェクトに対して現在有効な偽装を元に戻すことができなくなります。 `CAutoRevertImpersonation`その後、再関連付けを使用して、影響を与えずに`CAccessToken`破棄するか、または[Attach](#attach)を使用して同じオブジェクトまたは別のオブジェクトに対しては

##  <a name="getaccesstoken"></a>  CAutoRevertImpersonation::GetAccessToken

このオブジェクトに関連付けられているアクセストークンを取得します。

```
const CAccessToken* GetAccessToken() throw();
```

### <a name="return-value"></a>戻り値

以前に関連付けられた[CAccessToken](../../atl/reference/caccesstoken-class.md)のアドレス。または、関連付けが存在しない場合は NULL。

### <a name="remarks"></a>Remarks

`CAccessToken`オブジェクトの偽装の再設定を含む目的でこのメソッドが呼び出された場合は、代わりに[Detach](#detach)メソッドを使用する必要があります。

## <a name="see-also"></a>関連項目

[ATLSecurity サンプル](../../overview/visual-cpp-samples.md)<br/>
[アクセストークン](/windows/win32/SecAuthZ/access-tokens)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
