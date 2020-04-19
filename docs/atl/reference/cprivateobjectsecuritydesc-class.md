---
title: CPrivateObjectSecurityDesc クラス
ms.date: 11/04/2016
f1_keywords:
- CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::CPrivateObjectSecurityDesc
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::ConvertToAutoInherit
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Create
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Get
- ATLSECURITY/ATL::CPrivateObjectSecurityDesc::Set
helpviewer_keywords:
- CPrivateObjectSecurityDesc class
ms.assetid: 2c4bbb13-bf99-4833-912a-197f6815bb5d
ms.openlocfilehash: 97ea2b8411b404caf9f833ad85f226d18aea1e73
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496582"
---
# <a name="cprivateobjectsecuritydesc-class"></a>CPrivateObjectSecurityDesc クラス

このクラスは、プライベートオブジェクトのセキュリティ記述子オブジェクトを表します。

## <a name="syntax"></a>構文

```
class CPrivateObjectSecurityDesc : public CSecurityDesc
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CPrivateObjectSecurityDesc:: CPrivateObjectSecurityDesc](#cprivateobjectsecuritydesc)|コンストラクターです。|
|[CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CPrivateObjectSecurityDesc::ConvertToAutoInherit](#converttoautoinherit)|セキュリティ記述子とそのアクセス制御リスト (Acl) を、継承可能なアクセス制御エントリ (Ace) の自動伝達をサポートする形式に変換するには、このメソッドを呼び出します。|
|[CPrivateObjectSecurityDesc::Create](#create)|呼び出し元のリソースマネージャーによって作成されたプライベートオブジェクトの自己相対セキュリティ記述子を割り当てて初期化するには、このメソッドを呼び出します。|
|[CPrivateObjectSecurityDesc::Get](#get)|プライベートオブジェクトのセキュリティ記述子から情報を取得するには、このメソッドを呼び出します。|
|[CPrivateObjectSecurityDesc::Set](#set)|プライベートオブジェクトのセキュリティ記述子を変更するには、このメソッドを呼び出します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](#operator_eq)|代入演算子。|

## <a name="remarks"></a>Remarks

[Csecuritydesc](../../atl/reference/csecuritydesc-class.md)から派生したこのクラスは、プライベートオブジェクトのセキュリティ記述子を作成および管理するためのメソッドを提供します。

Windows のアクセス制御モデルの概要については、Windows SDK の「 [Access Control](/windows/win32/SecAuthZ/access-control) 」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CSecurityDesc](../../atl/reference/csecuritydesc-class.md)

`CPrivateObjectSecurityDesc`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsecurity .h

##  <a name="converttoautoinherit"></a>CPrivateObjectSecurityDesc:: ConvertToAutoInherit

セキュリティ記述子とそのアクセス制御リスト (Acl) を、継承可能なアクセス制御エントリ (Ace) の自動伝達をサポートする形式に変換するには、このメソッドを呼び出します。

```
bool ConvertToAutoInherit(
    const CSecurityDesc* pParent,
    GUID* ObjectType,
    bool bIsDirectoryObject,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>パラメーター

*pParent*<br/>
オブジェクトの親コンテナーを参照している[Csecuritydesc](../../atl/reference/csecuritydesc-class.md)オブジェクトへのポインター。 親コンテナーが存在しない場合、このパラメーターは NULL になります。

*ObjectType*<br/>
現在のオブジェクト`GUID`に関連付けられているオブジェクトの型を識別する構造体へのポインター。 オブジェクトに GUID がない場合は、 *ObjectType*を NULL に設定します。

*bIsDirectoryObject*<br/>
新しいオブジェクトに他のオブジェクトを含めることができるかどうかを指定します。 値が true の場合は、新しいオブジェクトがコンテナーであることを示します。 値が false の場合は、新しいオブジェクトがコンテナーではないことを示します。

*GenericMapping*<br/>
各汎用権限からオブジェクトの特定の権限へのマッピングを指定する[GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping)構造体へのポインター。

### <a name="return-value"></a>戻り値

正常に終了した場合は true を返します。失敗した場合は false を返します。

### <a name="remarks"></a>Remarks

このメソッドは、現在のセキュリティ記述子の随意アクセス制御リスト (DACL) とシステムアクセス制御リスト (SACL) の Ace が親セキュリティ記述子から継承されているかどうかを判断しようとします。 [Converttoautoinheritprivateobjectsecurity](/windows/win32/api/securitybaseapi/nf-securitybaseapi-converttoautoinheritprivateobjectsecurity)関数を呼び出します。

##  <a name="cprivateobjectsecuritydesc"></a>CPrivateObjectSecurityDesc:: CPrivateObjectSecurityDesc

コンストラクターです。

```
CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Remarks

`CPrivateObjectSecurityDesc` オブジェクトを初期化します。

##  <a name="dtor"></a>CPrivateObjectSecurityDesc:: ~ CPrivateObjectSecurityDesc

デストラクターです。

```
~CPrivateObjectSecurityDesc() throw();
```

### <a name="remarks"></a>Remarks

デストラクターは、割り当てられたすべてのリソースを解放し、プライベートオブジェクトのセキュリティ記述子を削除します。

##  <a name="create"></a>  CPrivateObjectSecurityDesc::Create

呼び出し元のリソースマネージャーによって作成されたプライベートオブジェクトの自己相対セキュリティ記述子を割り当てて初期化するには、このメソッドを呼び出します。

```
bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    bool bIsDirectoryObject,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();

bool Create(
    const CSecurityDesc* pParent,
    const CSecurityDesc* pCreator,
    GUID* ObjectType,
    bool bIsContainerObject,
    ULONG AutoInheritFlags,
    const CAccessToken& Token,
    PGENERIC_MAPPING GenericMapping) throw();
```

### <a name="parameters"></a>パラメーター

*pParent*<br/>
新しいオブジェクトが作成される親ディレクトリを参照する[Csecuritydesc](../../atl/reference/csecuritydesc-class.md)オブジェクトへのポインター。 親ディレクトリがない場合は、NULL に設定します。

*pCreator*<br/>
オブジェクトの作成者によって提供されたセキュリティ記述子へのポインター。 オブジェクトの作成者が新しいオブジェクトのセキュリティ情報を明示的に渡さない場合は、このパラメーターを NULL に設定します。

*bIsDirectoryObject*<br/>
新しいオブジェクトに他のオブジェクトを含めることができるかどうかを指定します。 値が true の場合は、新しいオブジェクトがコンテナーであることを示します。 値が false の場合は、新しいオブジェクトがコンテナーではないことを示します。

*Token*<br/>
オブジェクトの代理となるクライアントプロセスの[CAccessToken](../../atl/reference/caccesstoken-class.md)オブジェクトへの参照。

*GenericMapping*<br/>
各汎用権限からオブジェクトの特定の権限へのマッピングを指定する[GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping)構造体へのポインター。

*ObjectType*<br/>
現在のオブジェクト`GUID`に関連付けられているオブジェクトの型を識別する構造体へのポインター。 オブジェクトに GUID がない場合は、 *ObjectType*を NULL に設定します。

*bIsContainerObject*<br/>
新しいオブジェクトに他のオブジェクトを含めることができるかどうかを指定します。 値が true の場合は、新しいオブジェクトがコンテナーであることを示します。 値が false の場合は、新しいオブジェクトがコンテナーではないことを示します。

*AutoInheritFlags*<br/>
アクセス制御エントリ (Ace: access control entries) を*Pparent*から継承する方法を制御する一連のビットフラグ。 詳細については、「 [Createprivateobjectsecurityex](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) 」を参照してください。

### <a name="return-value"></a>戻り値

正常に終了した場合は true を返します。失敗した場合は false を返します。

### <a name="remarks"></a>Remarks

このメソッドは、 [Createprivateobjectsercursecurityex](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurity)または[Createprivateobjectsecurityex](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex)を呼び出します。

2番目の方法では、新しいオブジェクトのオブジェクトの種類の GUID を指定したり、Ace の継承方法を制御したりできます。

> [!NOTE]
>  自己相対セキュリティ記述子は、すべてのセキュリティ情報を連続したメモリブロックに格納するセキュリティ記述子です。

##  <a name="get"></a>  CPrivateObjectSecurityDesc::Get

プライベートオブジェクトのセキュリティ記述子から情報を取得するには、このメソッドを呼び出します。

```
bool Get(
    SECURITY_INFORMATION si,
    CSecurityDesc* pResult) const throw();
```

### <a name="parameters"></a>パラメーター

*si*<br/>
取得するセキュリティ記述子の部分を示すビットフラグのセット。 この値は、 [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)ビットフラグの組み合わせにすることができます。

*pResult*<br/>
指定されたセキュリティ記述子から要求された情報のコピーを受け取る[Csecuritydesc](../../atl/reference/csecuritydesc-class.md)オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

正常に終了した場合は true を返します。失敗した場合は false を返します。

### <a name="remarks"></a>Remarks

セキュリティ記述子は、セキュリティ保護可能なオブジェクトのセキュリティ情報を格納する構造体と関連付けられたデータです。

##  <a name="operator_eq"></a>  CPrivateObjectSecurityDesc::operator =

代入演算子。

```
CPrivateObjectSecurityDesc& operator= (const CPrivateObjectSecurityDesc& rhs) throw(...);
```

### <a name="parameters"></a>パラメーター

*rhs*<br/>
現在のオブジェクトに割り当てるオブジェクト。`CPrivateObjectSecurityDesc`

### <a name="return-value"></a>戻り値

更新さ`CPrivateObjectSecurityDesc`れたオブジェクトを返します。

##  <a name="set"></a>  CPrivateObjectSecurityDesc::Set

プライベートオブジェクトのセキュリティ記述子を変更するには、このメソッドを呼び出します。

```
bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();

bool Set(
    SECURITY_INFORMATION si,
    const CSecurityDesc& Modification,
    ULONG AutoInheritFlags,
    PGENERIC_MAPPING GenericMapping,
    const CAccessToken& Token) throw();
```

### <a name="parameters"></a>パラメーター

*si*<br/>
設定するセキュリティ記述子の部分を示すビットフラグのセット。 この値は、 [SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)ビットフラグの組み合わせにすることができます。

*変更*<br/>
[Csecuritydesc](../../atl/reference/csecuritydesc-class.md)オブジェクトへのポインター。 *Si*パラメーターによって示されるこのセキュリティ記述子の部分は、オブジェクトのセキュリティ記述子に適用されます。

*GenericMapping*<br/>
各汎用権限からオブジェクトの特定の権限へのマッピングを指定する[GENERIC_MAPPING](/windows/win32/api/winnt/ns-winnt-generic_mapping)構造体へのポインター。

*Token*<br/>
オブジェクトの代理となるクライアントプロセスの[CAccessToken](../../atl/reference/caccesstoken-class.md)オブジェクトへの参照。

*AutoInheritFlags*<br/>
アクセス制御エントリ (Ace: access control entries) を*Pparent*から継承する方法を制御する一連のビットフラグ。 詳細については、「 [Createprivateobjectsecurityex](/windows/win32/api/securitybaseapi/nf-securitybaseapi-createprivateobjectsecurityex) 」を参照してください。

### <a name="return-value"></a>戻り値

正常に終了した場合は true を返します。失敗した場合は false を返します。

### <a name="remarks"></a>Remarks

2番目の方法では、オブジェクトのオブジェクトの種類の GUID を指定したり、Ace の継承方法を制御したりできます。

## <a name="see-also"></a>関連項目

[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[セキュリティに関するグローバル関数](../../atl/reference/security-global-functions.md)<br/>
[CSecurityDesc クラス](../../atl/reference/csecuritydesc-class.md)
