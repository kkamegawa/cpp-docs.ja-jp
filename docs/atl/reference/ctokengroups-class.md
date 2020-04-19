---
title: CTokenGroups クラス
ms.date: 11/04/2016
f1_keywords:
- CTokenGroups
- ATLSECURITY/ATL::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::CTokenGroups
- ATLSECURITY/ATL::CTokenGroups::Add
- ATLSECURITY/ATL::CTokenGroups::Delete
- ATLSECURITY/ATL::CTokenGroups::DeleteAll
- ATLSECURITY/ATL::CTokenGroups::GetCount
- ATLSECURITY/ATL::CTokenGroups::GetLength
- ATLSECURITY/ATL::CTokenGroups::GetPTOKEN_GROUPS
- ATLSECURITY/ATL::CTokenGroups::GetSidsAndAttributes
- ATLSECURITY/ATL::CTokenGroups::LookupSid
helpviewer_keywords:
- CTokenGroups class
ms.assetid: 2ab08076-4b08-4487-bc70-ec6dee304190
ms.openlocfilehash: 88096747f45d4a81c873837cdd4975da9d8c24e2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496293"
---
# <a name="ctokengroups-class"></a>CTokenGroups クラス

このクラスは、 `TOKEN_GROUPS`構造体のラッパーです。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CTokenGroups
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CTokenGroups::CTokenGroups](#ctokengroups)|コンストラクターです。|
|[CTokenGroups:: ~ CTokenGroups](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CTokenGroups::Add](#add)|または`CSid`既存`TOKEN_GROUPS` の`CTokenGroups`構造体をオブジェクトに追加します。|
|[CTokenGroups::Delete](#delete)|とそれ`CSid`に関連付けられて`CTokenGroups`いる属性をオブジェクトから削除します。|
|[CTokenGroups::DeleteAll](#deleteall)|`CSid` オブジェクト`CTokenGroups`からすべてのオブジェクトとそれに関連付けられている属性を削除します。|
|[CTokenGroups::GetCount](#getcount)|オブジェクトに格納さ`CSid`れているオブジェクトと関連する`CTokenGroups`属性の数を返します。|
|[CTokenGroups::GetLength](#getlength)|`CTokenGroups`オブジェクトのサイズを返します。|
|[CTokenGroups::GetPTOKEN_GROUPS](#getptoken_groups)|`TOKEN_GROUPS`構造体へのポインターを取得します。|
|[CTokenGroups::GetSidsAndAttributes](#getsidsandattributes)|オブジェクトに属する`CSid`オブジェクトと属性を取得`CTokenGroups`します。|
|[CTokenGroups::LookupSid](#lookupsid)|`CSid`オブジェクトに関連付けられている属性を取得します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CTokenGroups:: operator const TOKEN_GROUPS *](#operator_const_token_groups__star)|オブジェクトを`TOKEN_GROUPS`構造体へのポインターにキャストします。 `CTokenGroups`|
|[CTokenGroups:: operator =](#operator_eq)|代入演算子。|

## <a name="remarks"></a>Remarks

[アクセストークン](/windows/win32/SecAuthZ/access-tokens)は、プロセスまたはスレッドのセキュリティコンテキストを記述するオブジェクトで、Windows システムにログオンした各ユーザーに割り当てられます。

`CTokenGroups` クラスは、[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) 構造体のラッパーであり、アクセストークンのグループセキュリティ識別子 (sid) に関する情報が含まれています。

Windows のアクセス制御モデルの概要については、Windows SDK の「 [Access Control](/windows/win32/SecAuthZ/access-control) 」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsecurity .h

##  <a name="add"></a>  CTokenGroups::Add

または`CSid`既存`TOKEN_GROUPS` の`CTokenGroups`構造体をオブジェクトに追加します。

```
void Add(const CSid& rSid, DWORD dwAttributes) throw(... );
void Add(const TOKEN_GROUPS& rTokenGroups) throw(...);
```

### <a name="parameters"></a>パラメーター

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)オブジェクト。

*dwAttributes*<br/>
`CSid`オブジェクトに関連付ける属性。

*rTokenGroups*<br/>
[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)構造体。

### <a name="remarks"></a>Remarks

これらのメソッドは`CSid` 、 `CTokenGroups`オブジェクトに1つ以上のオブジェクトとそれに関連付けられている属性を追加します。

##  <a name="ctokengroups"></a>  CTokenGroups::CTokenGroups

コンストラクターです。

```
CTokenGroups() throw();
CTokenGroups(const CTokenGroups& rhs) throw(... );
CTokenGroups(const TOKEN_GROUPS& rhs) throw(...);
```

### <a name="parameters"></a>パラメーター

*rhs*<br/>
`CTokenGroups` オブジェクトの構築に使用する `CTokenGroups` オブジェクトまたは [TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups) 構造体。

### <a name="remarks"></a>Remarks

オブジェクト`CTokenGroups`は、必要に応じ`TOKEN_GROUPS`て、構造体または以前`CTokenGroups`に定義したオブジェクトを使用して作成できます。

##  <a name="dtor"></a>CTokenGroups:: ~ CTokenGroups

デストラクターです。

```
virtual ~CTokenGroups() throw();
```

### <a name="remarks"></a>Remarks

デストラクターは、割り当てられたすべてのリソースを解放します。

##  <a name="delete"></a>  CTokenGroups::Delete

とそれ`CSid`に関連付けられて`CTokenGroups`いる属性をオブジェクトから削除します。

```
bool Delete(const CSid& rSid) throw();
```

### <a name="parameters"></a>パラメーター

*rSid*<br/>
セキュリティ識別子 (SID) と属性を削除する必要がある[CSid](../../atl/reference/csid-class.md)オブジェクト。

### <a name="return-value"></a>戻り値

`CSid`が削除された場合は true、それ以外の場合は false を返します。

##  <a name="deleteall"></a>  CTokenGroups::DeleteAll

`CSid` オブジェクト`CTokenGroups`からすべてのオブジェクトとそれに関連付けられている属性を削除します。

```
void DeleteAll() throw();
```

##  <a name="getcount"></a>  CTokenGroups::GetCount

`CSid` に`CTokenGroups`格納されているオブジェクトの数を返します。

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>戻り値

オブジェクトに格納されている[CSid](../../atl/reference/csid-class.md)オブジェクトとそれに関連付けられている属性の数を返します。 `CTokenGroups`

##  <a name="getlength"></a>  CTokenGroups::GetLength

`CTokenGroup`オブジェクトのサイズを返します。

```
UINT GetLength() const throw();
```

### <a name="remarks"></a>Remarks

`CTokenGroup`オブジェクトの合計サイズをバイト単位で返します。

##  <a name="getptoken_groups"></a>  CTokenGroups::GetPTOKEN_GROUPS

`TOKEN_GROUPS`構造体へのポインターを取得します。

```
const TOKEN_GROUPS* GetPTOKEN_GROUPS() const throw(...);
```

### <a name="return-value"></a>戻り値

`CTokenGroups`アクセストークンオブジェクトに属する[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)構造体へのポインターを取得します。

##  <a name="getsidsandattributes"></a>  CTokenGroups::GetSidsAndAttributes

オブジェクト、`CTokenGroups`および (オプションで) オブジェクトに属する属性を取得します。 `CSid`

```
void GetSidsAndAttributes(
    CSid::CSidArray* pSids,
    CAtlArray<DWORD>* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pSids*<br/>
[CSid](../../atl/reference/csid-class.md)オブジェクトの配列へのポインター。

*pAttributes*<br/>
Dword の配列へのポインター。 このパラメーターを省略した場合、または NULL の場合、属性は取得されません。

### <a name="remarks"></a>Remarks

このメソッドは、 `CSid` `CTokenGroups`オブジェクトに格納されているすべてのオブジェクトを列挙し、それらのオブジェクトと (必要に応じて) 属性フラグを配列オブジェクトに格納します。

##  <a name="lookupsid"></a>  CTokenGroups::LookupSid

`CSid`オブジェクトに関連付けられている属性を取得します。

```
bool LookupSid(
    const CSid& rSid,
    DWORD* pdwAttributes = NULL) const throw();
```

### <a name="parameters"></a>パラメーター

*rSid*<br/>
[CSid](../../atl/reference/csid-class.md)オブジェクト。

*pdwAttributes*<br/>
`CSid`オブジェクトの属性を受け取る DWORD へのポインター。 省略した場合、または NULL の場合、属性は取得されません。

### <a name="return-value"></a>戻り値

`CSid`が見つかった場合は true、それ以外の場合は false を返します。

### <a name="remarks"></a>Remarks

*PdwAttributes*を NULL に設定すると、属性にアクセスせず`CSid`にの存在を確認することができます。 アクセス権を確認するためにこの方法を使用することはできないことに注意してください。 アプリケーションでは、代わりに[CAccessToken:: CheckTokenMembership](../../atl/reference/caccesstoken-class.md#checktokenmembership)メソッドを使用する必要があります。

##  <a name="operator_eq"></a>  CTokenGroups::operator =

代入演算子。

```
CTokenGroups& operator= (const TOKEN_GROUPS& rhs) throw(...);
CTokenGroups& operator= (const CTokenGroups& rhs) throw(...);
```

### <a name="parameters"></a>パラメーター

*rhs*<br/>
`CTokenGroups` オブジェクトに割り当てる `CTokenGroups` オブジェクトまたは [TOKEN_GROUPS ](/windows/win32/api/winnt/ns-winnt-token_groups)構造体。

### <a name="return-value"></a>戻り値

更新さ`CTokenGroups`れたオブジェクトを返します。

##  <a name="operator_const_token_groups__star"></a>CTokenGroups:: operator const TOKEN_GROUPS *

`TOKEN_GROUPS`構造体へのポインターに値をキャストします。

```
operator const TOKEN_GROUPS *() const throw(...);
```

### <a name="remarks"></a>Remarks

値を[TOKEN_GROUPS](/windows/win32/api/winnt/ns-winnt-token_groups)構造体へのポインターにキャストします。

## <a name="see-also"></a>関連項目

[セキュリティのサンプル](../../overview/visual-cpp-samples.md)<br/>
[CSid クラス](../../atl/reference/csid-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[セキュリティに関するグローバル関数](../../atl/reference/security-global-functions.md)
