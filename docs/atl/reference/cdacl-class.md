---
title: CDacl クラス
ms.date: 11/04/2016
f1_keywords:
- CDacl
- ATLSECURITY/ATL::CDacl
- ATLSECURITY/ATL::CDacl::CDacl
- ATLSECURITY/ATL::CDacl::AddAllowedAce
- ATLSECURITY/ATL::CDacl::AddDeniedAce
- ATLSECURITY/ATL::CDacl::GetAceCount
- ATLSECURITY/ATL::CDacl::RemoveAce
- ATLSECURITY/ATL::CDacl::RemoveAllAces
helpviewer_keywords:
- CDacl class
ms.assetid: 2dc76616-6362-4967-b6cf-e2d39ca37ddd
ms.openlocfilehash: a37ef47a4ea89d9ec24fac417e5b715bd2602fd7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496930"
---
# <a name="cdacl-class"></a>CDacl クラス

このクラスは、DACL (随意アクセス制御リスト) 構造のラッパーです。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CDacl : public CAcl
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDacl::CDacl](#cdacl)|コンストラクターです。|
|[CDacl:: ~ CDacl](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDacl::AddAllowedAce](#addallowedace)|許可された ACE (アクセス制御エントリ) を`CDacl`オブジェクトに追加します。|
|[CDacl::AddDeniedAce](#adddeniedace)|拒否された ACE を`CDacl`オブジェクトに追加します。|
|[CDacl::GetAceCount](#getacecount)|`CDacl`オブジェクト内の ace (アクセス制御エントリ) の数を返します。|
|[CDacl::RemoveAce](#removeace)|`CDacl`オブジェクトから特定の ACE (アクセス制御エントリ) を削除します。|
|[CDacl::RemoveAllAces](#removeallaces)|`CDacl`オブジェクトに格納されているすべての ace を削除します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CDacl:: operator =](#operator_eq)|代入演算子。|

## <a name="remarks"></a>Remarks

オブジェクトのセキュリティ記述子には、DACL を含めることができます。 DACL には、オブジェクトにアクセスできるユーザーおよびグループを識別する、0個以上の Ace (アクセス制御エントリ) が含まれています。 DACL が空の場合 (つまり、Ace がゼロの場合)、アクセスは明示的に付与されないため、アクセスは暗黙的に拒否されます。 ただし、オブジェクトのセキュリティ記述子に DACL がない場合、オブジェクトは保護されず、すべてのユーザーが完全なアクセス権を持ちます。

オブジェクトの DACL を取得するには、オブジェクトの所有者であるか、オブジェクトへの READ_CONTROL アクセス権を持っている必要があります。 オブジェクトの DACL を変更するには、オブジェクトへの WRITE_DAC アクセス権が必要です。

提供されているクラスメソッドを使用して、オブジェクトの`CDacl` ace を作成、追加、削除、および削除します。 [Atlgetdacl](security-global-functions.md#atlgetdacl)および[atlgetdacl](security-global-functions.md#atlsetdacl)も参照してください。

Windows のアクセス制御モデルの概要については、Windows SDK の「 [Access Control](/windows/win32/SecAuthZ/access-control) 」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CAcl](../../atl/reference/cacl-class.md)

`CDacl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsecurity .h

##  <a name="addallowedace"></a>  CDacl::AddAllowedAce

許可された ACE (アクセス制御エントリ) を`CDacl`オブジェクトに追加します。

```
bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddAllowedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>パラメーター

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)オブジェクト。

*AccessMask*<br/>
指定した`CSid`オブジェクトに許可するアクセス権のマスクを指定します。

*AceFlags*<br/>
ACE の継承を制御するビットフラグのセット。

*pObjectType*<br/>
オブジェクトの型。

*pInheritedObjectType*<br/>
継承されたオブジェクト型。

### <a name="return-value"></a>戻り値

ACE が`CDacl`オブジェクトに追加された場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

オブジェクト`CDacl`には、オブジェクトにアクセスできるユーザーおよびグループを識別する、0個以上の ace (アクセス制御エントリ) が含まれています。 このメソッドは、オブジェクトへの`CDacl`アクセスを許可する ACE を追加します。

`AceFlags`パラメーターで設定できるさまざまなフラグの詳細については、「 [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) 」を参照してください。

##  <a name="adddeniedace"></a>  CDacl::AddDeniedAce

拒否された ACE (アクセス制御エントリ) を`CDacl`オブジェクトに追加します。

```
bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags = 0) throw(...);

bool AddDeniedAce(
    const CSid& rSid,
    ACCESS_MASK AccessMask,
    BYTE AceFlags,
    const GUID* pObjectType,
    const GUID* pInheritedObjectType) throw(...);
```

### <a name="parameters"></a>パラメーター

*rSid*<br/>
`CSid` オブジェクト。

*AccessMask*<br/>
指定した`CSid`オブジェクトに対して拒否するアクセス権のマスクを指定します。

*AceFlags*<br/>
ACE の継承を制御するビットフラグのセット。 メソッドの最初の形式では、既定値は0です。

*pObjectType*<br/>
オブジェクトの型。

*pInheritedObjectType*<br/>
継承されたオブジェクト型。

### <a name="return-value"></a>戻り値

ACE が`CDacl`オブジェクトに追加された場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

オブジェクト`CDacl`には、オブジェクトにアクセスできるユーザーおよびグループを識別する、0個以上の ace (アクセス制御エントリ) が含まれています。 このメソッドは、オブジェクトへの`CDacl`アクセスを拒否する ACE を追加します。

`AceFlags`パラメーターで設定できるさまざまなフラグの詳細については、「 [ACE_HEADER](/windows/win32/api/winnt/ns-winnt-ace_header) 」を参照してください。

##  <a name="cdacl"></a>CDacl::CDacl

コンストラクターです。

```
CDacl (const ACL& rhs) throw(...);
CDacl () throw();
```

### <a name="parameters"></a>パラメーター

*rhs*<br/>
既存`ACL`の (アクセス制御リスト) 構造体。

### <a name="remarks"></a>Remarks

オブジェクト`CDacl`は、必要に応じて、既存`ACL`の構造を使用して作成できます。 このパラメーターとして渡す必要があるのは、SACL (システムアクセス制御リスト) ではなく DACL (随意アクセス制御リスト) のみであることに注意してください。 デバッグビルドでは、SACL を渡すとアサートが発生します。 リリースビルドでは、SACL を渡すと、ACL 内の Ace (アクセス制御エントリ) が無視され、エラーは発生しません。

##  <a name="dtor"></a>CDacl:: ~ CDacl

デストラクターです。

```
~CDacl () throw();
```

### <a name="remarks"></a>Remarks

デストラクターは、 [CDacl:: RemoveAllAces](#removeallaces)を使用して、すべての ace (アクセス制御エントリ) を含む、オブジェクトによって取得されたすべてのリソースを解放します。

##  <a name="getacecount"></a>  CDacl::GetAceCount

`CDacl`オブジェクト内の ace (アクセス制御エントリ) の数を返します。

```
UINT GetAceCount() const throw();
```

### <a name="return-value"></a>戻り値

`CDacl`オブジェクトに格納されている ace の数を返します。

##  <a name="operator_eq"></a>  CDacl::operator =

代入演算子。

```
CDacl& operator= (const ACL& rhs) throw(...);
```

### <a name="parameters"></a>パラメーター

*rhs*<br/>
既存のオブジェクトに割り当てる ACL (アクセス制御リスト)。

### <a name="return-value"></a>戻り値

更新さ`CDacl`れたオブジェクトへの参照を返します。

### <a name="remarks"></a>Remarks

DACL (随意アクセス制御リスト) のみをこの関数に渡すようにしてください。 この関数に SACL (システムアクセス制御リスト) を渡すと、デバッグビルドでアサートが発生しますが、リリースビルドではエラーは発生しません。

##  <a name="removeace"></a>  CDacl::RemoveAce

`CDacl`オブジェクトから特定の ACE (アクセス制御エントリ) を削除します。

```
void RemoveAce(UINT nIndex) throw();
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
削除する ACE エントリのインデックス。

### <a name="remarks"></a>Remarks

このメソッドは、 [CAtlArray:: RemoveAt](../../atl/reference/catlarray-class.md#removeat)から派生しています。

##  <a name="removeallaces"></a>  CDacl::RemoveAllAces

`CDacl`オブジェクトに格納されているすべての ace (アクセス制御エントリ) を削除します。

```
void RemoveAllAces() throw();
```

### <a name="remarks"></a>Remarks

オブジェクト内`ACE`のすべての (アクセス制御エントリ) 構造体 (存在する`CDacl`場合) を削除します。

## <a name="see-also"></a>関連項目

[セキュリティのサンプル](../../overview/visual-cpp-samples.md)<br/>
[CAcl クラス](../../atl/reference/cacl-class.md)<br/>
[Acl](/windows/win32/SecAuthZ/access-control-lists)<br/>
[Ace](/windows/win32/SecAuthZ/access-control-entries)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[セキュリティに関するグローバル関数](../../atl/reference/security-global-functions.md)
