---
title: CTokenPrivileges クラス
ms.date: 11/04/2016
f1_keywords:
- CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::CTokenPrivileges
- ATLSECURITY/ATL::CTokenPrivileges::Add
- ATLSECURITY/ATL::CTokenPrivileges::Delete
- ATLSECURITY/ATL::CTokenPrivileges::DeleteAll
- ATLSECURITY/ATL::CTokenPrivileges::GetCount
- ATLSECURITY/ATL::CTokenPrivileges::GetDisplayNames
- ATLSECURITY/ATL::CTokenPrivileges::GetLength
- ATLSECURITY/ATL::CTokenPrivileges::GetLuidsAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetNamesAndAttributes
- ATLSECURITY/ATL::CTokenPrivileges::GetPTOKEN_PRIVILEGES
- ATLSECURITY/ATL::CTokenPrivileges::LookupPrivilege
helpviewer_keywords:
- CTokenPrivileges class
ms.assetid: 89590105-f001-4014-870d-142926091231
ms.openlocfilehash: f4ecc96ee53d6c688d17afa9957ccbf5060ca3fd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496284"
---
# <a name="ctokenprivileges-class"></a>CTokenPrivileges クラス

このクラスは、 `TOKEN_PRIVILEGES`構造体のラッパーです。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CTokenPrivileges
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CTokenPrivileges::CTokenPrivileges](#ctokenprivileges)|コンストラクターです。|
|[CTokenPrivileges:: ~ CTokenPrivileges](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CTokenPrivileges::Add](#add)|オブジェクトに1つ以上の`CTokenPrivileges`特権を追加します。|
|[CTokenPrivileges::Delete](#delete)|`CTokenPrivileges`オブジェクトから特権を削除します。|
|[CTokenPrivileges::DeleteAll](#deleteall)|`CTokenPrivileges`オブジェクトからすべての特権を削除します。|
|[CTokenPrivileges::GetCount](#getcount)|`CTokenPrivileges`オブジェクト内の特権エントリの数を返します。|
|[CTokenPrivileges::GetDisplayNames](#getdisplaynames)|`CTokenPrivileges`オブジェクトに格納されている特権の表示名を取得します。|
|[CTokenPrivileges::GetLength](#getlength)|オブジェクトによって表される`TOKEN_PRIVILEGES`構造体を保持するために必要なバイト単位のバッファーサイズを返します。 `CTokenPrivileges`|
|[CTokenPrivileges::GetLuidsAndAttributes](#getluidsandattributes)|`CTokenPrivileges`オブジェクトからローカル一意識別子 (luid) と属性フラグを取得します。|
|[CTokenPrivileges::GetNamesAndAttributes](#getnamesandattributes)|`CTokenPrivileges`オブジェクトから特権名と属性フラグを取得します。|
|[CTokenPrivileges::GetPTOKEN_PRIVILEGES](#getptoken_privileges)|構造体への`TOKEN_PRIVILEGES`ポインターを返します。|
|[CTokenPrivileges::LookupPrivilege](#lookupprivilege)|指定された特権名に関連付けられている属性を取得します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CTokenPrivileges:: operator const TOKEN_PRIVILEGES *](#operator_const_token_privileges__star)|`TOKEN_PRIVILEGES`構造体へのポインターに値をキャストします。|
|[CTokenPrivileges:: operator =](#operator_eq)|代入演算子。|

## <a name="remarks"></a>Remarks

[アクセストークン](/windows/win32/SecAuthZ/access-tokens)は、プロセスまたはスレッドのセキュリティコンテキストを記述するオブジェクトで、Windows システムにログオンした各ユーザーに割り当てられます。

アクセストークンは、各ユーザーに付与されるさまざまなセキュリティ特権を記述するために使用されます。 特権は、ローカル一意識別子 ( [LUID](/windows/win32/api/winnt/ns-winnt-luid)) と記述子文字列と呼ばれる64ビット番号で構成されます。

`CTokenPrivileges` クラスは、[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges) 構造体のラッパーであり、0以上の特権を含みます。 特権は、指定されたクラスメソッドを使用して追加、削除、または照会できます。

Windows のアクセス制御モデルの概要については、Windows SDK の「 [Access Control](/windows/win32/SecAuthZ/access-control) 」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsecurity .h

##  <a name="add"></a>  CTokenPrivileges::Add

`CTokenPrivileges`アクセストークンオブジェクトに1つ以上の特権を追加します。

```
bool Add(LPCTSTR pszPrivilege, bool bEnable) throw(...);
void Add(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>パラメーター

*pszPrivilege*<br/>
権限の名前を指定する null で終わる文字列へのポインター (WINNT で定義)。H ヘッダーファイル。

*bEnable*<br/>
True の場合、特権が有効になります。 False の場合、特権は無効になります。

*rPrivileges*<br/>
[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)構造体への参照。 特権および属性は、この構造からコピーされ、 `CTokenPrivileges`オブジェクトに追加されます。

### <a name="return-value"></a>戻り値

このメソッドの最初の形式は、特権が正常に追加された場合は true、それ以外の場合は false を返します。

##  <a name="ctokenprivileges"></a>CTokenPrivileges::CTokenPrivileges

コンストラクターです。

```
CTokenPrivileges() throw();
CTokenPrivileges(const CTokenPrivileges& rhs) throw(... );
CTokenPrivileges(const TOKEN_PRIVILEGES& rPrivileges) throw(...);
```

### <a name="parameters"></a>パラメーター

*rhs*<br/>
新しいオブジェクトに割り当てるオブジェクト。`CTokenPrivileges`

*rPrivileges*<br/>
新しい`CTokenPrivileges`オブジェクトに割り当てる[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)構造体。

### <a name="remarks"></a>Remarks

オブジェクト`CTokenPrivileges`は、必要に応じ`TOKEN_PRIVILEGES`て、構造体または以前`CTokenPrivileges`に定義したオブジェクトを使用して作成できます。

##  <a name="dtor"></a>CTokenPrivileges:: ~ CTokenPrivileges

デストラクターです。

```
virtual ~CTokenPrivileges() throw();
```

### <a name="remarks"></a>Remarks

デストラクターは、割り当てられたすべてのリソースを解放します。

##  <a name="delete"></a>  CTokenPrivileges::Delete

`CTokenPrivileges`アクセストークンオブジェクトから特権を削除します。

```
bool Delete(LPCTSTR pszPrivilege) throw();
```

### <a name="parameters"></a>パラメーター

*pszPrivilege*<br/>
権限の名前を指定する null で終わる文字列へのポインター (WINNT で定義)。H ヘッダーファイル。 たとえば、このパラメーターでは、定数 SE_SECURITY_NAME、またはそれに対応する文字列 "SeSecurityPrivilege" を指定できます。

### <a name="return-value"></a>戻り値

特権が正常に削除された場合は true、それ以外の場合は false を返します。

### <a name="remarks"></a>Remarks

このメソッドは、制限付きトークンを作成するためのツールとして役立ちます。

##  <a name="deleteall"></a>  CTokenPrivileges::DeleteAll

`CTokenPrivileges`アクセストークンオブジェクトからすべての特権を削除します。

```
void DeleteAll() throw();
```

### <a name="remarks"></a>Remarks

アクセストークンオブジェクトに格納さ`CTokenPrivileges`れているすべての特権を削除します。

##  <a name="getdisplaynames"></a>  CTokenPrivileges::GetDisplayNames

`CTokenPrivileges`アクセストークンオブジェクトに格納されている特権の表示名を取得します。

```
void GetDisplayNames(CNames* pDisplayNames) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pDisplayNames*<br/>
`CString` オブジェクトの配列へのポインター。 `CNames`は typedef `CTokenPrivileges::CAtlArray<CString>`として定義されます。

### <a name="remarks"></a>Remarks

パラメーター `pDisplayNames`は、 `CTokenPrivileges`オブジェクトに格納されて`CString`いる特権に対応する表示名を受け取るオブジェクトの配列へのポインターです。 このメソッドは、WINNT の [定義された特権] セクションで指定された特権の表示名のみを取得します。始め.

このメソッドは、使用可能な名前を取得します。たとえば、属性名が SE_REMOTE_SHUTDOWN_NAME の場合、"リモートシステムからの強制シャットダウン" という名前の名前が付いています。 システム名を取得するには、 [CTokenPrivileges:: GetNamesAndAttributes](#getnamesandattributes)を使用します。

##  <a name="getcount"></a>  CTokenPrivileges::GetCount

`CTokenPrivileges`オブジェクト内の特権エントリの数を返します。

```
UINT GetCount() const throw();
```

### <a name="return-value"></a>戻り値

`CTokenPrivileges`オブジェクトに格納されている特権の数を返します。

##  <a name="getlength"></a>  CTokenPrivileges::GetLength

`CTokenPrivileges`オブジェクトの長さを返します。

```
UINT GetLength() const throw();
```

### <a name="return-value"></a>戻り値

オブジェクトによって表される構造体を`TOKEN_PRIVILEGES`保持するために必要なバイト数を返します。格納されているすべての特権エントリを含みます。 `CTokenPrivileges`

##  <a name="getluidsandattributes"></a>  CTokenPrivileges::GetLuidsAndAttributes

`CTokenPrivileges`オブジェクトからローカル一意識別子 (luid) と属性フラグを取得します。

```
void GetLuidsAndAttributes(
    CLUIDArray* pPrivileges,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pPrivileges*<br/>
[LUID](/windows/win32/api/winnt/ns-winnt-luid)オブジェクトの配列へのポインター。 `CLUIDArray`は、と`CAtlArray<LUID> CLUIDArray`して定義される typedef です。

*pAttributes*<br/>
DWORD オブジェクトの配列へのポインター。 このパラメーターを省略した場合、または NULL の場合、属性は取得されません。 `CAttributes`は、と`CAtlArray <DWORD> CAttributes`して定義される typedef です。

### <a name="remarks"></a>Remarks

このメソッドは、 `CTokenPrivileges`アクセストークンオブジェクトに含まれているすべての特権を列挙し、個々の luid と (必要に応じて) 属性フラグを配列オブジェクトに配置します。

##  <a name="getnamesandattributes"></a>  CTokenPrivileges::GetNamesAndAttributes

`CTokenPrivileges`オブジェクトから名前と属性フラグを取得します。

```
void GetNamesAndAttributes(
    CNames* pNames,
    CAttributes* pAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pNames*<br/>
オブジェクトの配列への`CString`ポインター。 `CNames`は、と`CAtlArray <CString> CNames`して定義される typedef です。

*pAttributes*<br/>
DWORD オブジェクトの配列へのポインター。 このパラメーターを省略した場合、または NULL の場合、属性は取得されません。 `CAttributes`は、と`CAtlArray <DWORD> CAttributes`して定義される typedef です。

### <a name="remarks"></a>Remarks

このメソッドは、 `CTokenPrivileges`オブジェクトに含まれているすべての特権を列挙し、名前と (オプションで) 属性フラグを配列オブジェクトに格納します。

このメソッドは、名前付きの名前ではなく、属性名を取得します。たとえば、属性名が SE_REMOTE_SHUTDOWN_NAME の場合、システム名は "Seremotes" になります。 名前を確認できる名前を取得するには、 [CTokenPrivileges:: GetDisplayNames](#getdisplaynames)メソッドを使用します。

##  <a name="getptoken_privileges"></a>  CTokenPrivileges::GetPTOKEN_PRIVILEGES

構造体への`TOKEN_PRIVILEGES`ポインターを返します。

```
const TOKEN_PRIVILEGES* GetPTOKEN_PRIVILEGES() const throw(...);
```

### <a name="return-value"></a>戻り値

[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)構造体へのポインターを返します。

##  <a name="lookupprivilege"></a>  CTokenPrivileges::LookupPrivilege

指定された特権名に関連付けられている属性を取得します。

```
bool LookupPrivilege(
    LPCTSTR pszPrivilege,
    DWORD* pdwAttributes = NULL) const throw(...);
```

### <a name="parameters"></a>パラメーター

*pszPrivilege*<br/>
権限の名前を指定する null で終わる文字列へのポインター (WINNT で定義)。H ヘッダーファイル。 たとえば、このパラメーターでは、定数 SE_SECURITY_NAME、またはそれに対応する文字列 "SeSecurityPrivilege" を指定できます。

*pdwAttributes*<br/>
属性を受け取る変数へのポインター。

### <a name="return-value"></a>戻り値

属性が正常に取得された場合は true、それ以外の場合は false を返します。

##  <a name="operator_eq"></a>CTokenPrivileges:: operator =

代入演算子。

```
CTokenPrivileges& operator= (const TOKEN_PRIVILEGES& rPrivileges) throw(...);
CTokenPrivileges& operator= (const CTokenPrivileges& rhs) throw(...);
```

### <a name="parameters"></a>パラメーター

*rPrivileges*<br/>
`CTokenPrivileges`オブジェクトに割り当てる[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)構造体。

*rhs*<br/>
オブジェクトに割り当てるオブジェクト。 `CTokenPrivileges`

### <a name="return-value"></a>戻り値

更新さ`CTokenPrivileges`れたオブジェクトを返します。

##  <a name="operator_const_token_privileges__star"></a>CTokenPrivileges:: operator const TOKEN_PRIVILEGES\*

`TOKEN_PRIVILEGES`構造体へのポインターに値をキャストします。

```
operator const TOKEN_PRIVILEGES *() const throw(...);
```

### <a name="remarks"></a>Remarks

値を[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)構造体へのポインターにキャストします。

## <a name="see-also"></a>関連項目

[セキュリティのサンプル](../../overview/visual-cpp-samples.md)<br/>
[TOKEN_PRIVILEGES](/windows/win32/api/winnt/ns-winnt-token_privileges)<br/>
[LUID](/windows/win32/api/winnt/ns-winnt-luid)<br/>
[LUID_AND_ATTRIBUTES](/windows/win32/api/winnt/ns-winnt-luid_and_attributes)<br/>
[クラスの概要](../../atl/atl-class-overview.md)<br/>
[セキュリティに関するグローバル関数](../../atl/reference/security-global-functions.md)
