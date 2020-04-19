---
title: CSecurityDesc クラス
ms.date: 11/04/2016
f1_keywords:
- CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::CSecurityDesc
- ATLSECURITY/ATL::CSecurityDesc::FromString
- ATLSECURITY/ATL::CSecurityDesc::GetControl
- ATLSECURITY/ATL::CSecurityDesc::GetDacl
- ATLSECURITY/ATL::CSecurityDesc::GetGroup
- ATLSECURITY/ATL::CSecurityDesc::GetOwner
- ATLSECURITY/ATL::CSecurityDesc::GetPSECURITY_DESCRIPTOR
- ATLSECURITY/ATL::CSecurityDesc::GetSacl
- ATLSECURITY/ATL::CSecurityDesc::IsDaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsDaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsDaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsDaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsGroupDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsOwnerDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclAutoInherited
- ATLSECURITY/ATL::CSecurityDesc::IsSaclDefaulted
- ATLSECURITY/ATL::CSecurityDesc::IsSaclPresent
- ATLSECURITY/ATL::CSecurityDesc::IsSaclProtected
- ATLSECURITY/ATL::CSecurityDesc::IsSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::MakeAbsolute
- ATLSECURITY/ATL::CSecurityDesc::MakeSelfRelative
- ATLSECURITY/ATL::CSecurityDesc::SetControl
- ATLSECURITY/ATL::CSecurityDesc::SetDacl
- ATLSECURITY/ATL::CSecurityDesc::SetGroup
- ATLSECURITY/ATL::CSecurityDesc::SetOwner
- ATLSECURITY/ATL::CSecurityDesc::SetSacl
- ATLSECURITY/ATL::CSecurityDesc::ToString
helpviewer_keywords:
- CSecurityDesc class
ms.assetid: 3767a327-378f-4690-ba40-4d9f6a1f5ee4
ms.openlocfilehash: 90f8cfd66fbab88bfa29c39ff27189f02447a7c7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496486"
---
# <a name="csecuritydesc-class"></a>CSecurityDesc クラス

このクラスは、 `SECURITY_DESCRIPTOR`構造体のラッパーです。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CSecurityDesc
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSecurityDesc::CSecurityDesc](#csecuritydesc)|コンストラクターです。|
|[CSecurityDesc:: ~ CSecurityDesc](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSecurityDesc::FromString](#fromstring)|文字列形式のセキュリティ記述子を、有効な機能セキュリティ記述子に変換します。|
|[CSecurityDesc::GetControl](#getcontrol)|セキュリティ記述子からコントロール情報を取得します。|
|[CSecurityDesc::GetDacl](#getdacl)|セキュリティ記述子から随意アクセス制御リスト (DACL) 情報を取得します。|
|[CSecurityDesc::GetGroup](#getgroup)|セキュリティ記述子からプライマリグループ情報を取得します。|
|[CSecurityDesc::GetOwner](#getowner)|セキュリティ記述子から所有者についを取得します。|
|[CSecurityDesc::GetPSECURITY_DESCRIPTOR](#getpsecurity_descriptor)|構造体への`SECURITY_DESCRIPTOR`ポインターを返します。|
|[CSecurityDesc::GetSacl](#getsacl)|セキュリティ記述子からシステムアクセス制御リスト (SACL: system access control list) 情報を取得します。|
|[CSecurityDesc::IsDaclAutoInherited](#isdaclautoinherited)|DACL が自動伝達をサポートするように構成されているかどうかを判断します。|
|[CSecurityDesc::IsDaclDefaulted](#isdacldefaulted)|セキュリティ記述子が既定の DACL で構成されているかどうかを判断します。|
|[CSecurityDesc::IsDaclPresent](#isdaclpresent)|セキュリティ記述子に DACL が含まれているかどうかを判断します。|
|[CSecurityDesc::IsDaclProtected](#isdaclprotected)|DACL が変更を防止するように構成されているかどうかを判断します。|
|[CSecurityDesc::IsGroupDefaulted](#isgroupdefaulted)|セキュリティ記述子のグループセキュリティ識別子 (SID) が既定で設定されているかどうかを判断します。|
|[CSecurityDesc::IsOwnerDefaulted](#isownerdefaulted)|セキュリティ記述子の所有者 SID が既定で設定されているかどうかを判断します。|
|[CSecurityDesc::IsSaclAutoInherited](#issaclautoinherited)|SACL が自動伝達をサポートするように構成されているかどうかを判断します。|
|[CSecurityDesc::IsSaclDefaulted](#issacldefaulted)|セキュリティ記述子が既定の SACL で構成されているかどうかを判断します。|
|[CSecurityDesc::IsSaclPresent](#issaclpresent)|セキュリティ記述子に SACL が含まれているかどうかを判断します。|
|[CSecurityDesc::IsSaclProtected](#issaclprotected)|SACL が変更を防止するように構成されているかどうかを判断します。|
|[CSecurityDesc::IsSelfRelative](#isselfrelative)|セキュリティ記述子が自己相対形式であるかどうかを判断します。|
|[CSecurityDesc::MakeAbsolute](#makeabsolute)|セキュリティ記述子を絶対形式に変換するには、このメソッドを呼び出します。|
|[CSecurityDesc::MakeSelfRelative](#makeselfrelative)|セキュリティ記述子を自己相対形式に変換するには、このメソッドを呼び出します。|
|[CSecurityDesc::SetControl](#setcontrol)|セキュリティ記述子の制御ビットを設定します。|
|[CSecurityDesc::SetDacl](#setdacl)|DACL の情報を設定します。 セキュリティ記述子に DACL が既に存在する場合は、その DACL が置き換えられます。|
|[CSecurityDesc::SetGroup](#setgroup)|絶対形式のセキュリティ記述子のプライマリグループ情報を設定します。これは、既に存在しているプライマリグループ情報を置き換えたものです。|
|[CSecurityDesc::SetOwner](#setowner)|絶対形式のセキュリティ記述子の所有者情報を設定し、既に存在する所有者情報を置き換えます。|
|[CSecurityDesc::SetSacl](#setsacl)|SACL の情報を設定します。 SACL がセキュリティ記述子に既に存在する場合は、置き換えられます。|
|[CSecurityDesc::ToString](#tostring)|セキュリティ記述子を文字列形式に変換します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CSecurityDesc:: operator const SECURITY_DESCRIPTOR *](#operator_const_security_descriptor__star)|構造体への`SECURITY_DESCRIPTOR`ポインターを返します。|
|[CSecurityDesc::operator =](#operator_eq)|代入演算子。|

## <a name="remarks"></a>Remarks

構造`SECURITY_DESCRIPTOR`体には、オブジェクトに関連付けられているセキュリティ情報が含まれます。 アプリケーションは、この構造を使用して、オブジェクトのセキュリティステータスを設定および照会します。 「 [Atlgetsecuritydescriptor](security-global-functions.md#atlgetsecuritydescriptor)」も参照してください。

アプリケーションでは`SECURITY_DESCRIPTOR`構造を直接変更しないでください。代わりに、提供されているクラスメソッドを使用する必要があります。

Windows のアクセス制御モデルの概要については、Windows SDK の「 [Access Control](/windows/win32/SecAuthZ/access-control) 」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsecurity .h

##  <a name="csecuritydesc"></a>  CSecurityDesc::CSecurityDesc

コンストラクターです。

```
CSecurityDesc() throw();
CSecurityDesc(const CSecurityDesc& rhs) throw(... );
CSecurityDesc(const SECURITY_DESCRIPTOR& rhs) throw(...);
```

### <a name="parameters"></a>パラメーター

*rhs*<br/>
`SECURITY_DESCRIPTOR`新しい`CSecurityDesc` オブジェクトに`CSecurityDesc`割り当てるオブジェクトまたは構造体。

### <a name="remarks"></a>Remarks

オブジェクト`CSecurityDesc`は、必要に応じ`SECURITY_DESCRIPTOR`て、構造体または以前`CSecurityDesc`に定義したオブジェクトを使用して作成できます。

##  <a name="dtor"></a>CSecurityDesc:: ~ CSecurityDesc

デストラクターです。

```
virtual ~CSecurityDesc() throw();
```

### <a name="remarks"></a>Remarks

デストラクターは、割り当てられたすべてのリソースを解放します。

##  <a name="fromstring"></a>  CSecurityDesc::FromString

文字列形式のセキュリティ記述子を、有効な機能セキュリティ記述子に変換します。

```
bool FromString(LPCTSTR pstr) throw(...);
```

### <a name="parameters"></a>パラメーター

*pstr*<br/>
変換する[文字列形式のセキュリティ記述子](/windows/win32/SecAuthZ/security-descriptor-string-format)を含む、null で終わる文字列へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は true を返します。 エラー発生時に例外をスローします。

### <a name="remarks"></a>Remarks

この文字列は、 [Csecuritydesc:: ToString](#tostring)を使用して作成できます。 セキュリティ記述子を文字列に変換すると、格納と送信が容易になります。

このメソッドは、 [convertstringsecuritydescriptortosecuritydescriptor がエラー](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)を呼び出します。

##  <a name="getcontrol"></a>  CSecurityDesc::GetControl

セキュリティ記述子からコントロール情報を取得します。

```
bool GetControl(SECURITY_DESCRIPTOR_CONTROL* psdc) const throw();
```

### <a name="parameters"></a>パラメーター

*psdc*<br/>
セキュリティ記述子の`SECURITY_DESCRIPTOR_CONTROL`制御情報を受け取る構造体へのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は true、失敗した場合は false を返します。

### <a name="remarks"></a>Remarks

このメソッドは、 [Getsecurity記述子コントロール](/windows/win32/api/securitybaseapi/nf-securitybaseapi-getsecuritydescriptorcontrol)を呼び出します。

##  <a name="getdacl"></a>  CSecurityDesc::GetDacl

セキュリティ記述子から随意アクセス制御リスト (DACL) 情報を取得します。

```
bool GetDacl(
    CDacl* pDacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pDacl*<br/>
セキュリティ記述子の`CDacl` DACL のコピーを格納する構造体へのポインター。 随意 ACL が存在する場合、メソッドは、 *pdacl*をセキュリティ記述子の随意 acl のアドレスに設定します。 随意 ACL が存在しない場合、値は保存されません。

*pbPresent*<br/>
指定されたセキュリティ記述子に随意 ACL が存在するかどうかを示す値へのポインター。 セキュリティ記述子に随意 ACL が含まれている場合、このパラメーターは true に設定されます。 セキュリティ記述子に随意 ACL が含まれていない場合、このパラメーターは false に設定されます。

*pbDefaulted 既定値*<br/>
セキュリティ記述子に随意 ACL が存在する場合、 `SECURITY_DESCRIPTOR_CONTROL`構造体の SE_DACL_DEFAULTED フラグの値に設定されたフラグへのポインター。 このフラグが true の場合、随意 ACL は既定のメカニズムによって取得されます。false の場合、ユーザーによって随意 ACL が明示的に指定されています。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は true、失敗した場合は false を返します。

##  <a name="getgroup"></a>  CSecurityDesc::GetGroup

セキュリティ記述子からプライマリグループ情報を取得します。

```
bool GetGroup(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pSid*<br/>
CDacl に格納されているグループのコピーを受け取る[CSid](../../atl/reference/csid-class.md) (セキュリティ識別子) へのポインター。

*pbDefaulted 既定値*<br/>
メソッドから制御が戻ったときに、 `SECURITY_DESCRIPTOR_CONTROL`構造体の SE_GROUP_DEFAULTED フラグの値に設定されたフラグへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は true、失敗した場合は false を返します。

##  <a name="getowner"></a>  CSecurityDesc::GetOwner

セキュリティ記述子から所有者についを取得します。

```
bool GetOwner(
    CSid* pSid,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pSid*<br/>
CDacl に格納されているグループのコピーを受け取る[CSid](../../atl/reference/csid-class.md) (セキュリティ識別子) へのポインター。

*pbDefaulted 既定値*<br/>
メソッドから制御が戻ったときに、 `SECURITY_DESCRIPTOR_CONTROL`構造体の SE_OWNER_DEFAULTED フラグの値に設定されたフラグへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は true、失敗した場合は false を返します。

##  <a name="getpsecurity_descriptor"></a>  CSecurityDesc::GetPSECURITY_DESCRIPTOR

構造体への`SECURITY_DESCRIPTOR`ポインターを返します。

```
const SECURITY_DESCRIPTOR* GetPSECURITY_DESCRIPTOR() const throw();
```

### <a name="return-value"></a>戻り値

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)構造体へのポインターを返します。

##  <a name="getsacl"></a>  CSecurityDesc::GetSacl

セキュリティ記述子からシステムアクセス制御リスト (SACL: system access control list) 情報を取得します。

```
bool GetSacl(
    CSacl* pSacl,
    bool* pbPresent = NULL,
    bool* pbDefaulted = NULL) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pSacl*<br/>
セキュリティ記述子の`CSacl` SACL のコピーを格納する構造体へのポインター。 システム ACL が存在する場合、メソッドは*Psacl*をセキュリティ記述子のシステム acl のアドレスに設定します。 システム ACL が存在しない場合、値は保存されません。

*pbPresent*<br/>
指定したセキュリティ記述子にシステム ACL が存在することを示すために、メソッドによって設定されるフラグへのポインター。 セキュリティ記述子にシステム ACL が含まれている場合、このパラメーターは true に設定されます。 セキュリティ記述子にシステム ACL が含まれていない場合、このパラメーターは false に設定されます。

*pbDefaulted 既定値*<br/>
セキュリティ記述子にシステム ACL が存在する場合、 `SECURITY_DESCRIPTOR_CONTROL`構造体の SE_SACL_DEFAULTED フラグの値に設定されたフラグへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は true、失敗した場合は false を返します。

##  <a name="isdaclautoinherited"></a>  CSecurityDesc::IsDaclAutoInherited

随意アクセス制御リスト (DACL) が自動伝達をサポートするように構成されているかどうかを判断します。

```
bool IsDaclAutoInherited() const throw();
```

### <a name="return-value"></a>戻り値

既存の子オブジェクトに対して、継承可能なアクセス制御エントリ (Ace) の自動伝達をサポートするために設定されている DACL がセキュリティ記述子に含まれている場合に true を返します。 それ以外の場合は、false を返します。

### <a name="remarks"></a>Remarks

システムは、オブジェクトとその既存の子オブジェクトに対して自動継承アルゴリズムを実行するときに、このビットを設定します。

##  <a name="isdacldefaulted"></a>  CSecurityDesc::IsDaclDefaulted

セキュリティ記述子が既定の随意アクセス制御リスト (DACL) を使用して構成されているかどうかを判断します。

```
bool IsDaclDefaulted() const throw();
```

### <a name="return-value"></a>戻り値

セキュリティ記述子に既定の DACL が含まれている場合は true、それ以外の場合は false を返します。

### <a name="remarks"></a>Remarks

このフラグは、アクセス制御エントリ (ACE: access control entry) の継承に関して、システムが DACL をどのように扱うかに影響する可能性があります。 たとえば、オブジェクトの作成者が DACL を指定していない場合、オブジェクトは作成者のアクセストークンから既定の DACL を受け取ります。 SE_DACL_PRESENT フラグが設定されていない場合、システムはこのフラグを無視します。

このフラグは、オブジェクトの最終的な DACL がどのように計算されるかを決定するために使用され、セキュリティ保護可能なオブジェクトのセキュリティ記述子コントロールに物理的に格納されることはありません。

このフラグを設定するには、 [Csecuritydesc:: SetDacl](#setdacl)メソッドを使用します。

##  <a name="isdaclpresent"></a>  CSecurityDesc::IsDaclPresent

セキュリティ記述子に随意アクセス制御リスト (DACL) が格納されているかどうかを判断します。

```
bool IsDaclPresent() const throw();
```

### <a name="return-value"></a>戻り値

セキュリティ記述子に DACL が含まれている場合は true、それ以外の場合は false を返します。

### <a name="remarks"></a>Remarks

このフラグが設定されていない場合、またはこのフラグが設定され、DACL が NULL の場合、セキュリティ記述子はすべてのユーザーにフルアクセスを許可します。

このフラグは、セキュリティ記述子がセキュリティ保護可能なオブジェクトに関連付けられるまで、呼び出し元によって指定されたセキュリティ情報を保持するために使用されます。 セキュリティ記述子がセキュリティ保護可能なオブジェクトに関連付けられると、SE_DACL_PRESENT フラグは常にセキュリティ記述子コントロールで設定されます。

このフラグを設定するには、 [Csecuritydesc:: SetDacl](#setdacl)メソッドを使用します。

##  <a name="isdaclprotected"></a>  CSecurityDesc::IsDaclProtected

随意アクセス制御リスト (DACL) が変更を防止するように構成されているかどうかを判断します。

```
bool IsDaclProtected() const throw();
```

### <a name="return-value"></a>戻り値

DACL が、継承可能なアクセス制御エントリ (Ace) によってセキュリティ記述子が変更されないように構成されている場合、true を返します。 それ以外の場合は、false を返します。

### <a name="remarks"></a>Remarks

このフラグを設定するには、 [Csecuritydesc:: SetDacl](#setdacl)メソッドを使用します。

このメソッドは、継承可能な Ace の自動伝達をサポートします。

##  <a name="isgroupdefaulted"></a>  CSecurityDesc::IsGroupDefaulted

セキュリティ記述子のグループセキュリティ識別子 (SID) が既定で設定されているかどうかを判断します。

```
bool IsGroupDefaulted() const throw();
```

### <a name="return-value"></a>戻り値

セキュリティ記述子の元のプロバイダーではなく、既定の機構でセキュリティ記述子のグループ SID が指定されている場合、true を返します。 それ以外の場合は、false を返します。

### <a name="remarks"></a>Remarks

このフラグを設定するには、 [Csecuritydesc:: SetGroup](#setgroup)メソッドを使用します。

##  <a name="isownerdefaulted"></a>  CSecurityDesc::IsOwnerDefaulted

セキュリティ記述子の所有者セキュリティ識別子 (SID) が既定で設定されているかどうかを判断します。

```
bool IsOwnerDefaulted() const throw();
```

### <a name="return-value"></a>戻り値

セキュリティ記述子の元のプロバイダーではなく、既定の機構がセキュリティ記述子の所有者 SID を指定した場合に true を返します。 それ以外の場合は、false を返します。

### <a name="remarks"></a>Remarks

このフラグを設定するには、 [Csecuritydesc:: SetOwner](#setowner)メソッドを使用します。

##  <a name="issaclautoinherited"></a>  CSecurityDesc::IsSaclAutoInherited

システムアクセス制御リスト (SACL) が自動伝達をサポートするように構成されているかどうかを判断します。

```
bool IsSaclAutoInherited() const throw();
```

### <a name="return-value"></a>戻り値

既存の子オブジェクトに対して、継承可能なアクセス制御エントリ (Ace) の自動伝達をサポートするために設定されている SACL がセキュリティ記述子に含まれている場合に true を返します。 それ以外の場合は、false を返します。

### <a name="remarks"></a>Remarks

システムは、オブジェクトとその既存の子オブジェクトに対して自動継承アルゴリズムを実行するときに、このビットを設定します。

##  <a name="issacldefaulted"></a>  CSecurityDesc::IsSaclDefaulted

セキュリティ記述子が既定のシステムアクセス制御リスト (SACL) を使用して構成されているかどうかを判断します。

```
bool IsSaclDefaulted() const throw();
```

### <a name="return-value"></a>戻り値

セキュリティ記述子に既定の SACL が含まれている場合は true、それ以外の場合は false を返します。

### <a name="remarks"></a>Remarks

このフラグは、アクセス制御エントリ (ACE: access control entry) の継承に関して、システムが SACL をどのように処理するかに影響する可能性があります。 SE_SACL_PRESENT フラグが設定されていない場合、システムはこのフラグを無視します。

このフラグを設定するには、 [Csecuritydesc:: SetSacl](#setsacl)メソッドを使用します。

##  <a name="issaclpresent"></a>  CSecurityDesc::IsSaclPresent

セキュリティ記述子にシステムアクセス制御リスト (SACL) が含まれているかどうかを判断します。

```
bool IsSaclPresent() const throw();
```

### <a name="return-value"></a>戻り値

セキュリティ記述子に SACL が含まれている場合は true、それ以外の場合は false を返します。

### <a name="remarks"></a>Remarks

このフラグを設定するには、 [Csecuritydesc:: SetSacl](#setsacl)メソッドを使用します。

##  <a name="issaclprotected"></a>  CSecurityDesc::IsSaclProtected

システムアクセス制御リスト (SACL) が変更を防止するように構成されているかどうかを判断します。

```
bool IsSaclProtected() const throw();
```

### <a name="return-value"></a>戻り値

継承可能なアクセス制御エントリ (Ace) によってセキュリティ記述子が変更されないように SACL が構成されている場合、true を返します。 それ以外の場合は、false を返します。

### <a name="remarks"></a>Remarks

このフラグを設定するには、 [Csecuritydesc:: SetSacl](#setsacl)メソッドを使用します。

このメソッドは、継承可能な Ace の自動伝達をサポートします。

##  <a name="isselfrelative"></a>  CSecurityDesc::IsSelfRelative

セキュリティ記述子が自己相対形式であるかどうかを判断します。

```
bool IsSelfRelative() const throw();
```

### <a name="return-value"></a>戻り値

セキュリティ記述子が、連続するメモリブロック内のすべてのセキュリティ情報と共に自己相対形式である場合は true を返します。 セキュリティ記述子が絶対形式の場合は false を返します。 詳細については、「[絶対セキュリティ記述子と自己相対セキュリティ記述子](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)」を参照してください。

##  <a name="makeabsolute"></a>  CSecurityDesc::MakeAbsolute

セキュリティ記述子を絶対形式に変換するには、このメソッドを呼び出します。

```
bool MakeAbsolute() throw(...);
```

### <a name="return-value"></a>戻り値

メソッドが成功した場合は true、それ以外の場合は false を返します。

### <a name="remarks"></a>Remarks

絶対形式のセキュリティ記述子には、情報自体ではなく、含まれている情報へのポインターが含まれています。 自己相対形式のセキュリティ記述子には、連続したメモリブロック内の情報が含まれています。 自己相対セキュリティ記述子では、構造体`SECURITY_DESCRIPTOR`は常に情報を開始しますが、セキュリティ記述子のその他のコンポーネントは、任意の順序で構造に従うことができます。 メモリアドレスを使用する代わりに、自己相対セキュリティ記述子のコンポーネントは、セキュリティ記述子の先頭からのオフセットによって識別されます。 この形式は、セキュリティ記述子をディスクに保存するか、通信プロトコルを使用して送信する必要がある場合に便利です。 詳細については、「[絶対セキュリティ記述子と自己相対セキュリティ記述子](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)」を参照してください。

##  <a name="makeselfrelative"></a>  CSecurityDesc::MakeSelfRelative

セキュリティ記述子を自己相対形式に変換するには、このメソッドを呼び出します。

```
bool MakeSelfRelative() throw(...);
```

### <a name="return-value"></a>戻り値

メソッドが成功した場合は true、それ以外の場合は false を返します。

### <a name="remarks"></a>Remarks

絶対形式のセキュリティ記述子には、情報自体を格納するのではなく、それに含まれる情報へのポインターが含まれています。 自己相対形式のセキュリティ記述子には、連続したメモリブロック内の情報が含まれています。 自己相対セキュリティ記述子では、構造体`SECURITY_DESCRIPTOR`は常に情報を開始しますが、セキュリティ記述子のその他のコンポーネントは、任意の順序で構造に従うことができます。 メモリアドレスを使用する代わりに、セキュリティ記述子のコンポーネントは、セキュリティ記述子の先頭からのオフセットによって識別されます。 この形式は、セキュリティ記述子をディスクに保存するか、通信プロトコルを使用して送信する必要がある場合に便利です。 詳細については、「[絶対セキュリティ記述子と自己相対セキュリティ記述子](/windows/win32/SecAuthZ/absolute-and-self-relative-security-descriptors)」を参照してください。

##  <a name="operator_eq"></a>  CSecurityDesc::operator =

代入演算子。

```
CSecurityDesc& operator= (const SECURITY_DESCRIPTOR& rhs) throw(...);
CSecurityDesc& operator= (const CSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>パラメーター

*rhs*<br/>
`CSecurityDesc` `CSecurityDesc` `SECURITY_DESCRIPTOR`オブジェクトに割り当てる構造体またはオブジェクト。

### <a name="return-value"></a>戻り値

更新さ`CSecurityDesc`れたオブジェクトを返します。

##  <a name="operator_const_security_descriptor__star"></a>CSecurityDesc:: operator const SECURITY_DESCRIPTOR *

`SECURITY_DESCRIPTOR`構造体へのポインターに値をキャストします。

```
operator const SECURITY_DESCRIPTOR *() const throw();
```

##  <a name="setcontrol"></a>  CSecurityDesc::SetControl

セキュリティ記述子の制御ビットを設定します。

```
bool SetControl(
    SECURITY_DESCRIPTOR_CONTROL ControlBitsOfInterest,
    SECURITY_DESCRIPTOR_CONTROL ControlBitsToSet) throw();
```

### <a name="parameters"></a>パラメーター

*ControlBitsOfInterest*<br/>
設定する制御ビットを示す SECURITY_DESCRIPTOR_CONTROL mask。 設定できるフラグの一覧については、「 [Setsecurity記述子コントロール](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)」を参照してください。

*ControlBitsToSet*<br/>
*ControlBitsOfInterest* mask によって指定されたコントロールビットの新しい値を示す SECURITY_DESCRIPTOR_CONTROL mask。 このパラメーターには、 *ControlBitsOfInterest*パラメーターに指定されているフラグの組み合わせを使用できます。

### <a name="return-value"></a>戻り値

正常に終了した場合は true を返します。失敗した場合は false を返します。

### <a name="remarks"></a>Remarks

このメソッドは、 [Setsecurity記述子コントロール](/windows/win32/api/securitybaseapi/nf-securitybaseapi-setsecuritydescriptorcontrol)を呼び出します。

##  <a name="setdacl"></a>  CSecurityDesc::SetDacl

随意アクセス制御リスト (DACL) に情報を設定します。 セキュリティ記述子に DACL が既に存在する場合は、その DACL が置き換えられます。

```
inline void SetDacl(
    bool bPresent = true,
    bool bDefaulted = false) throw(...);

inline void SetDacl(
    const CDacl& Dacl,
    bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>パラメーター

*Dacl*<br/>
セキュリティ記述子の`CDacl` DACL を指定するオブジェクトへの参照。 このパラメーターを NULL にすることはできません。 セキュリティ記述子に NULL の DACL を設定するには、メソッドの最初の形式を*Bpresent*を false に設定して使用する必要があります。

*bPresent*<br/>
セキュリティ記述子に DACL が存在することを示すフラグを指定します。 このパラメーターが true の場合、メソッドは`SECURITY_DESCRIPTOR_CONTROL`構造体の SE_DACL_PRESENT フラグを設定し、 *DACL*と*bdefaulted*値のパラメーターの値を使用します。 False の場合、メソッドは SE_DACL_PRESENT フラグをクリアし、 *Bdefaulted 既定*値は無視されます。

*bDefaulted 値*<br/>
DACL のソースを示すフラグを指定します。 このフラグが true の場合、DACL は既定のメカニズムによって取得されています。 False の場合、DACL はユーザーによって明示的に指定されています。 メソッドは、 `SECURITY_DESCRIPTOR_CONTROL`構造体の SE_DACL_DEFAULTED フラグにこの値を格納します。 このパラメーターが指定されていない場合、SE_DACL_DEFAULTED フラグはクリアされます。

### <a name="return-value"></a>戻り値

正常に終了した場合は true を返します。失敗した場合は false を返します。

### <a name="remarks"></a>Remarks

空の DACL と存在しない DACL には、重要な違いがあります。 DACL が空の場合は、アクセス制御エントリが含まれておらず、明示的に付与されたアクセス権はありません。 その結果、オブジェクトへのアクセスは暗黙的に拒否されます。 一方、オブジェクトに DACL がない場合、オブジェクトには保護が割り当てられず、すべてのアクセス要求が許可されます。

##  <a name="setgroup"></a>  CSecurityDesc::SetGroup

絶対形式のセキュリティ記述子のプライマリグループ情報を設定します。これは、既に存在しているプライマリグループ情報を置き換えたものです。

```
bool SetGroup(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>パラメーター

*Sid*<br/>
セキュリティ記述子の新しいプライマリグループの[CSid](../../atl/reference/csid-class.md)オブジェクトへの参照。 このパラメーターを NULL にすることはできません。 セキュリティ記述子は、DACL または SACL を持たないようにマークすることができますが、グループと所有者を持つ必要があります。これは、これらが NULL SID (特別な意味を持つ組み込み SID) であっても同様です。

*bDefaulted 値*<br/>
プライマリグループの情報が既定のメカニズムから派生したものかどうかを示します。 この値が true の場合、これは既定の情報です。メソッドは、この値を`SECURITY_DESCRIPTOR_CONTROL`構造体の SE_GROUP_DEFAULTED フラグとして格納します。 このパラメーターが0の場合、SE_GROUP_DEFAULTED フラグはクリアされます。

### <a name="return-value"></a>戻り値

正常に終了した場合は true を返します。失敗した場合は false を返します。

##  <a name="setowner"></a>  CSecurityDesc::SetOwner

絶対形式のセキュリティ記述子の所有者情報を設定します。 これは、既に存在する所有者情報を置き換えます。

```
bool SetOwner(const CSid& Sid, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>パラメーター

*Sid*<br/>
セキュリティ記述子の新しいプライマリ所有者の[CSid](../../atl/reference/csid-class.md)オブジェクト。 このパラメーターを NULL にすることはできません。

*bDefaulted 値*<br/>
所有者情報が既定のメカニズムから派生したものかどうかを示します。 この値が true の場合は、既定の情報です。 メソッドは、この値を SE_OWNER_DEFAULTED フラグとして`SECURITY_DESCRIPTOR_CONTROL`構造体に格納します。 このパラメーターが0の場合、SE_OWNER_DEFAULTED フラグはクリアされます。

### <a name="return-value"></a>戻り値

正常に終了した場合は true を返します。失敗した場合は false を返します。

##  <a name="setsacl"></a>  CSecurityDesc::SetSacl

システムアクセス制御リスト (SACL: system access control list) の情報を設定します。 SACL がセキュリティ記述子に既に存在する場合は、置き換えられます。

```
bool SetSacl(const CSacl& Sacl, bool bDefaulted = false) throw(...);
```

### <a name="parameters"></a>パラメーター

*Sacl*<br/>
セキュリティ記述子の`CSacl` SACL を指定するオブジェクトへのポインター。 このパラメーターを NULL にすることはできません。 CSacl オブジェクトである必要があります。 Dacl とは異なり、SACL オブジェクトはアクセス権を指定せず、監査情報のみを指定するため、NULL と空の SACL に違いはありません。

*bDefaulted 値*<br/>
SACL のソースを示すフラグを指定します。 このフラグが true の場合、いくつかの既定の機構によって SACL が取得されています。 False の場合、SACL はユーザーによって明示的に指定されています。 メソッドは、 `SECURITY_DESCRIPTOR_CONTROL`構造体の SE_SACL_DEFAULTED フラグにこの値を格納します。 このパラメーターが指定されていない場合、SE_SACL_DEFAULTED フラグはクリアされます。

### <a name="return-value"></a>戻り値

正常に終了した場合は true を返します。失敗した場合は false を返します。

##  <a name="tostring"></a>  CSecurityDesc::ToString

セキュリティ記述子を文字列形式に変換します。

```
bool ToString(
    CString* pstr, SECURITY_INFORMATION si = OWNER_SECURITY_INFORMATION |
    GROUP_SECURITY_INFORMATION | DACL_SECURITY_INFORMATION |
    SACL_SECURITY_INFORMATION) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pstr*<br/>
[文字列形式のセキュリティ記述子](/windows/win32/SecAuthZ/security-descriptor-string-format)を受け取る null で終わる文字列へのポインター。

*si*<br/>
出力文字列に含めるセキュリティ記述子のコンポーネントを示す、SECURITY_INFORMATION ビットフラグの組み合わせを指定します。

### <a name="return-value"></a>戻り値

正常に終了した場合は true を返します。失敗した場合は false を返します。

### <a name="remarks"></a>Remarks

セキュリティ記述子を文字列形式にすると、より簡単に格納または転送できます。 文字列を`CSecurityDesc::FromString`セキュリティ記述子に変換するには、メソッドを使用します。

*Si*パラメーターには、次の SECURITY_INFORMATION フラグを含めることができます。

|[値]|説明|
|-----------|-------------|
|OWNER_SECURITY_INFORMATION|所有者を含めます。|
|GROUP_SECURITY_INFORMATION|プライマリグループを含めます。|
|DACL_SECURITY_INFORMATION|DACL を含めます。|
|SACL_SECURITY_INFORMATION|SACL を含めます。|

DACL が NULL で、入力セキュリティ記述子に SE_DACL_PRESENT 制御ビットが設定されている場合、メソッドは失敗します。

DACL が NULL で、入力セキュリティ記述子で SE_DACL_PRESENT 制御ビットが設定されていない場合、結果として得られるセキュリティ記述子の文字列には D: コンポーネントがありません。 詳細については、「[セキュリティ記述子文字列の形式](/windows/win32/SecAuthZ/security-descriptor-string-format)」を参照してください。

このメソッドは、 [convertstringsecuritydescriptortosecuritydescriptor がエラー](/windows/win32/api/sddl/nf-sddl-convertstringsecuritydescriptortosecuritydescriptorw)を呼び出します。

## <a name="see-also"></a>関連項目

[セキュリティのサンプル](../../overview/visual-cpp-samples.md)<br/>
[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[セキュリティに関するグローバル関数](../../atl/reference/security-global-functions.md)
