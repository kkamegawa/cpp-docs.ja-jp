---
title: CUrl クラス
ms.date: 05/06/2019
f1_keywords:
- CUrl
- ATLUTIL/ATL::CUrl
- ATLUTIL/ATL::CUrl::CUrl
- ATLUTIL/ATL::CUrl::Canonicalize
- ATLUTIL/ATL::CUrl::Clear
- ATLUTIL/ATL::CUrl::CrackUrl
- ATLUTIL/ATL::CUrl::CreateUrl
- ATLUTIL/ATL::CUrl::GetExtraInfo
- ATLUTIL/ATL::CUrl::GetExtraInfoLength
- ATLUTIL/ATL::CUrl::GetHostName
- ATLUTIL/ATL::CUrl::GetHostNameLength
- ATLUTIL/ATL::CUrl::GetPassword
- ATLUTIL/ATL::CUrl::GetPasswordLength
- ATLUTIL/ATL::CUrl::GetPortNumber
- ATLUTIL/ATL::CUrl::GetScheme
- ATLUTIL/ATL::CUrl::GetSchemeName
- ATLUTIL/ATL::CUrl::GetSchemeNameLength
- ATLUTIL/ATL::CUrl::GetUrlLength
- ATLUTIL/ATL::CUrl::GetUrlPath
- ATLUTIL/ATL::CUrl::GetUrlPathLength
- ATLUTIL/ATL::CUrl::GetUserName
- ATLUTIL/ATL::CUrl::GetUserNameLength
- ATLUTIL/ATL::CUrl::SetExtraInfo
- ATLUTIL/ATL::CUrl::SetHostName
- ATLUTIL/ATL::CUrl::SetPassword
- ATLUTIL/ATL::CUrl::SetPortNumber
- ATLUTIL/ATL::CUrl::SetScheme
- ATLUTIL/ATL::CUrl::SetSchemeName
- ATLUTIL/ATL::CUrl::SetUrlPath
- ATLUTIL/ATL::CUrl::SetUserName
helpviewer_keywords:
- CUrl class
ms.assetid: b3894d34-47b9-4961-9719-4197153793da
ms.openlocfilehash: fe91a01fbe67580bf82ae57c0317d06057fc9098
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221493"
---
# <a name="curl-class"></a>CUrl クラス

このクラスは、URL を表します。 既存の URL を解析するかどうか、他のユーザーとは無関係に、URL の各要素を操作できる文字列またはゼロからの文字列を作成します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CUrl
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CUrl::CUrl](#curl)|コンストラクターです。|
|[CUrl:: ~ CUrl](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CUrl::Canonicalize](#canonicalize)|URL 文字列を正規の形式に変換するためには、このメソッドを呼び出します。|
|[CUrl::Clear](#clear)|すべての URL フィールドをクリアするには、このメソッドを呼び出します。|
|[CUrl::CrackUrl](#crackurl)|デコードし、URL を解析するには、このメソッドを呼び出します。|
|[CUrl::CreateUrl](#createurl)|URL を作成するには、このメソッドを呼び出します。|
|[CUrl::GetExtraInfo](#getextrainfo)|余分な情報を取得するには、このメソッドを呼び出す (など*テキスト*または #*テキスト*)、URL から。|
|[CUrl::GetExtraInfoLength](#getextrainfolength)|追加情報の長さを取得するには、このメソッドを呼び出す (など*テキスト*または #*テキスト*) URL からを取得します。|
|[CUrl::GetHostName](#gethostname)|URL からホスト名を取得するには、このメソッドを呼び出します。|
|[CUrl::GetHostNameLength](#gethostnamelength)|ホスト名の長さを取得するには、このメソッドを呼び出します。|
|[CUrl::GetPassword](#getpassword)|URL から、パスワードを取得するには、このメソッドを呼び出します。|
|[CUrl::GetPasswordLength](#getpasswordlength)|パスワードの長さを取得するには、このメソッドを呼び出します。|
|[CUrl::GetPortNumber](#getportnumber)|ATL_URL_PORT の観点から、ポート番号を取得するには、このメソッドを呼び出します。|
|[CUrl::GetScheme](#getscheme)|URL スキームを取得するには、このメソッドを呼び出します。|
|[CUrl::GetSchemeName](#getschemename)|URL スキームの名前を取得するには、このメソッドを呼び出します。|
|[CUrl::GetSchemeNameLength](#getschemenamelength)|URL のスキーム名の長さを取得するには、このメソッドを呼び出します。|
|[CUrl::GetUrlLength](#geturllength)|URL の長さを取得するには、このメソッドを呼び出します。|
|[CUrl::GetUrlPath](#geturlpath)|URL パスを取得するには、このメソッドを呼び出します。|
|[CUrl::GetUrlPathLength](#geturlpathlength)|URL パスの長さを取得するには、このメソッドを呼び出します。|
|[CUrl::GetUserName](#getusername)|URL からユーザー名を取得するには、このメソッドを呼び出します。|
|[CUrl::GetUserNameLength](#getusernamelength)|ユーザー名の長さを取得するには、このメソッドを呼び出します。|
|[CUrl::SetExtraInfo](#setextrainfo)|余分な情報を設定するには、このメソッドを呼び出す (など*テキスト*または #*テキスト*) の URL。|
|[CUrl::SetHostName](#sethostname)|ホスト名を設定するには、このメソッドを呼び出します。|
|[CUrl::SetPassword](#setpassword)|パスワードを設定するには、このメソッドを呼び出します。|
|[CUrl::SetPortNumber](#setportnumber)|ATL_URL_PORT の観点から、ポート番号を設定するには、このメソッドを呼び出します。|
|[CUrl::SetScheme](#setscheme)|URL スキームを設定するには、このメソッドを呼び出します。|
|[CUrl::SetSchemeName](#setschemename)|URL のスキーム名を設定するには、このメソッドを呼び出します。|
|[CUrl::SetUrlPath](#seturlpath)|URL パスを設定するには、このメソッドを呼び出します。|
|[CUrl::SetUserName](#setusername)|ユーザー名を設定するには、このメソッドを呼び出します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CUrl::operator =](#operator_eq)|指定した割り当て`CUrl`現在オブジェクト`CUrl`オブジェクト。|

## <a name="remarks"></a>Remarks

`CUrl` パスまたはポート番号など、URL のフィールドを操作することができます。 `CUrl` 次の形式の Url を認識します。

\<スキーム >://\<ユーザー名 >:\<パスワード >\@\<ホスト名 >:\<PortNumber >/\<UrlPath >\<ExtraInfo >

(一部のフィールドは、省略可能)。たとえば、この URL があるとします。

`http://someone:secret@www.microsoft.com:80/visualc/stuff.htm#contents`

[CUrl::CrackUrl](#crackurl)次のように解析します。

- スキーム:"http"または[ATL_URL_SCHEME_HTTP](atl-url-scheme-enum.md)

- ユーザー名:"someone"

- パスワード:「シークレット」

- ホスト名:"`www.microsoft.com`"

- ポート番号:80

- UrlPath: "visualc/stuff.htm"

- ExtraInfo:"#contents"

UrlPath フィールドを (たとえば) を操作するには、使用[GetUrlPath](#geturlpath)、 [GetUrlPathLength](#geturlpathlength)、および[SetUrlPath](#seturlpath)します。 使用する[CreateUrl](#createurl)完全な URL 文字列を作成します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlutil.h

##  <a name="canonicalize"></a>  CUrl::Canonicalize

URL 文字列を正規の形式に変換するためには、このメソッドを呼び出します。

```
inline BOOL Canonicalize(DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>パラメーター

*dwFlags*<br/>
正規化を制御するフラグ。 フラグが指定されていない場合 (*dwFlags* = 0)、メソッドは、すべての安全でない文字およびメタ シーケンスに変換します。 (など\\。、\..、と\\...) をエスケープするシーケンス。 *dwFlags*値は次のいずれかを指定できます。

- ATL_URL_BROWSER_MODE:「#」の後に文字をデコードまたはエンコードしませんまたは""、末尾の空白文字の後に削除されません""です。 この値が指定されていない場合は、URL 全体はエンコードされ、後続の空白が削除されます。

- ATL_URL _DECODE:URL が解析される前に、エスケープ シーケンスを含む文字すべて %XX シーケンスに変換します。

- ATL_URL _ENCODE_PERCENT:発生した任意のパーセント記号をエンコードします。 既定では、パーセント記号はエンコードされません。

- ATL_URL _ENCODE_SPACES_ONLY:Spaces only. をエンコードします。

- ATL_URL _NO_ENCODE:安全でない文字をエスケープ シーケンスは変換されません。

- ATL_URL _NO_META:メタ シーケンスは削除されません (など".「と」..")、URL から。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

正規の形式に変換するには、安全でない文字とスペースをエスケープ シーケンスに変換する必要があります。

##  <a name="clear"></a>  CUrl::Clear

すべての URL フィールドをクリアするには、このメソッドを呼び出します。

```
inline void Clear() throw();
```

##  <a name="crackurl"></a>  CUrl::CrackUrl

デコードし、URL を解析するには、このメソッドを呼び出します。

```
BOOL CrackUrl(LPCTSTR lpszUrl, DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>パラメーター

*lpszUrl*<br/>
URL。

*dwFlags*<br/>
内のすべてのエスケープ文字を変換するには、ATL_URL_DECODE または ATL_URL_ESCAPE 指定*lpszUrl*に解析後に実際の値。 (Visual の前にC++2005 では、解析する前に変換されたすべてのエスケープ文字を ATL_URL_DECODE)。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="createurl"></a>  CUrl::CreateUrl

このメソッドは、CUrl オブジェクトのコンポーネントのフィールドから URL 文字列を構築します。

```
inline BOOL CreateUrl(
    LPTSTR lpszUrl,
    DWORD* pdwMaxLength,
    DWORD dwFlags = 0) const throw();
```

### <a name="parameters"></a>パラメーター

*lpszUrl*<br/>
完全な URL 文字列を保持する文字列バッファー。

*pdwMaxLength*<br/>
最大長、 *lpszUrl*文字列バッファー。

*dwFlags*<br/>
内のすべてのエスケープ文字に変換する ATL_URL_ESCAPE 指定*lpszUrl*に実際の値。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

このメソッドは、次の形式を使用して、完全な URL 文字列を構築するために個別のフィールドを追加します。

**\<scheme>://\<user>:\<pass>\@\<domain>:\<port>\<path>\<extra>**

このメソッドを呼び出すときに、 *pdwMaxLength*パラメーターは、によって参照される文字列バッファーの最大長を含める必要があります最初に、 *lpszUrl*パラメーター。 値、 *pdwMaxLength*パラメーターは、URL 文字列の実際の長さで更新されます。

### <a name="example"></a>例

このサンプルでは CUrl オブジェクトとその URL 文字列の取得の作成

[!code-cpp[NVC_ATL_Utilities#133](../../atl/codesnippet/cpp/curl-class_1.cpp)]

##  <a name="curl"></a>  CUrl::CUrl

コンストラクターです。

```
CUrl() throw();
CUrl(const CUrl& urlThat) throw();
```

### <a name="parameters"></a>パラメーター

*いる Url*<br/>
`CUrl`オブジェクトにコピーする URL を作成します。

##  <a name="dtor"></a>  CUrl:: ~ CUrl

デストラクターです。

```
~CUrl() throw();
```

##  <a name="getextrainfo"></a>  CUrl::GetExtraInfo

余分な情報を取得するには、このメソッドを呼び出す (など*テキスト*または #*テキスト*)、URL から。

```
inline LPCTSTR GetExtraInfo() const throw();
```

### <a name="return-value"></a>戻り値

追加情報を含む文字列を返します。

##  <a name="getextrainfolength"></a>  CUrl::GetExtraInfoLength

追加情報の長さを取得するには、このメソッドを呼び出す (など*テキスト*または #*テキスト*) URL からを取得します。

```
inline DWORD GetExtraInfoLength() const throw();
```

### <a name="return-value"></a>戻り値

追加情報を含む文字列の長さを返します。

##  <a name="gethostname"></a>  CUrl::GetHostName

URL からホスト名を取得するには、このメソッドを呼び出します。

```
inline LPCTSTR GetHostName() const throw();
```

### <a name="return-value"></a>戻り値

ホスト名を返します。

##  <a name="gethostnamelength"></a>  CUrl::GetHostNameLength

ホスト名の長さを取得するには、このメソッドを呼び出します。

```
inline DWORD GetHostNameLength() const throw();
```

### <a name="return-value"></a>戻り値

ホスト名の長さを返します。

##  <a name="getpassword"></a>  CUrl::GetPassword

URL から、パスワードを取得するには、このメソッドを呼び出します。

```
inline LPCTSTR GetPassword() const throw();
```

### <a name="return-value"></a>戻り値

パスワードを返します。

##  <a name="getpasswordlength"></a>  CUrl::GetPasswordLength

パスワードの長さを取得するには、このメソッドを呼び出します。

```
inline DWORD GetPasswordLength() const throw();
```

### <a name="return-value"></a>戻り値

パスワードの長さを返します。

##  <a name="getportnumber"></a>  CUrl::GetPortNumber

ポート番号を取得するには、このメソッドを呼び出します。

```
inline ATL_URL_PORT GetPortNumber() const throw();
```

### <a name="return-value"></a>戻り値

ポート番号を返します。

##  <a name="getscheme"></a>  CUrl::GetScheme

URL スキームを取得するには、このメソッドを呼び出します。

```
inline ATL_URL_SCHEME GetScheme() const throw();
```

### <a name="return-value"></a>戻り値

返します、 [ATL_URL_SCHEME](atl-url-scheme-enum.md) URL のスキームを記述する値。

##  <a name="getschemename"></a>  CUrl::GetSchemeName

URL スキームの名前を取得するには、このメソッドを呼び出します。

```
inline LPCTSTR GetSchemeName() const throw();
```

### <a name="return-value"></a>戻り値

URL のスキーム名 ("http"、"ftp"など) を返します。

##  <a name="getschemenamelength"></a>  CUrl::GetSchemeNameLength

URL のスキーム名の長さを取得するには、このメソッドを呼び出します。

```
inline DWORD GetSchemeNameLength() const throw();
```

### <a name="return-value"></a>戻り値

URL のスキーム名の長さを返します。

##  <a name="geturllength"></a>  CUrl::GetUrlLength

URL の長さを取得するには、このメソッドを呼び出します。

```
inline DWORD GetUrlLength() const throw();
```

### <a name="return-value"></a>戻り値

URL の長さを返します。

##  <a name="geturlpath"></a>  CUrl::GetUrlPath

URL パスを取得するには、このメソッドを呼び出します。

```
inline LPCTSTR GetUrlPath() const throw();
```

### <a name="return-value"></a>戻り値

URL パスを返します。

##  <a name="geturlpathlength"></a>  CUrl::GetUrlPathLength

URL パスの長さを取得するには、このメソッドを呼び出します。

```
inline DWORD GetUrlPathLength() const throw();
```

### <a name="return-value"></a>戻り値

URL パスの長さを返します。

##  <a name="getusername"></a>  CUrl::GetUserName

URL からユーザー名を取得するには、このメソッドを呼び出します。

```
inline LPCTSTR GetUserName() const throw();
```

### <a name="return-value"></a>戻り値

ユーザー名を返します。

##  <a name="getusernamelength"></a>  CUrl::GetUserNameLength

ユーザー名の長さを取得するには、このメソッドを呼び出します。

```
inline DWORD GetUserNameLength() const throw();
```

### <a name="return-value"></a>戻り値

ユーザー名の長さを返します。

##  <a name="operator_eq"></a>  CUrl::operator =

指定した割り当て`CUrl`現在オブジェクト`CUrl`オブジェクト。

```
CUrl& operator= (const CUrl& urlThat) throw();
```

### <a name="parameters"></a>パラメーター

*いる Url*<br/>
`CUrl`現在のオブジェクトにコピーするオブジェクト。

### <a name="return-value"></a>戻り値

現在のオブジェクトへの参照を返します。

##  <a name="setextrainfo"></a>  CUrl::SetExtraInfo

余分な情報を設定するには、このメソッドを呼び出す (など*テキスト*または #*テキスト*) の URL。

```
inline BOOL SetExtraInfo(LPCTSTR lpszInfo) throw();
```

### <a name="parameters"></a>パラメーター

*lpszInfo*<br/>
URL に含める追加の情報を含む文字列。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="sethostname"></a>  CUrl::SetHostName

ホスト名を設定するには、このメソッドを呼び出します。

```
inline BOOL SetHostName(LPCTSTR lpszHost) throw();
```

### <a name="parameters"></a>パラメーター

*lpszHost*<br/>
ホスト名です。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="setpassword"></a>  CUrl::SetPassword

パスワードを設定するには、このメソッドを呼び出します。

```
inline BOOL SetPassword(LPCTSTR lpszPass) throw();
```

### <a name="parameters"></a>パラメーター

*lpszPass*<br/>
パスワード。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="setportnumber"></a>  CUrl::SetPortNumber

ポート番号を設定するには、このメソッドを呼び出します。

```
inline BOOL SetPortNumber(ATL_URL_PORT nPrt) throw();
```

### <a name="parameters"></a>パラメーター

*nPrt*<br/>
ポート番号。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="setscheme"></a>  CUrl::SetScheme

URL スキームを設定するには、このメソッドを呼び出します。

```
inline BOOL SetScheme(ATL_URL_SCHEME nScheme) throw();
```

### <a name="parameters"></a>パラメーター

*nScheme*<br/>
1 つ、 [ATL_URL_SCHEME](atl-url-scheme-enum.md)スキームの値。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

名前で、スキームを設定することもできます (を参照してください[スキーム](#setschemename))。

##  <a name="setschemename"></a>  CUrl::SetSchemeName

URL のスキーム名を設定するには、このメソッドを呼び出します。

```
inline BOOL SetSchemeName(LPCTSTR lpszSchm) throw();
```

### <a name="parameters"></a>パラメーター

*lpszSchm*<br/>
URL のスキーム名。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

### <a name="remarks"></a>Remarks

使用して、スキームを設定することも、 [ATL_URL_SCHEME](atl-url-scheme-enum.md)定数 (を参照してください[CUrl::SetScheme](#setscheme))。

##  <a name="seturlpath"></a>  CUrl::SetUrlPath

URL パスを設定するには、このメソッドを呼び出します。

```
inline BOOL SetUrlPath(LPCTSTR lpszPath) throw();
```

### <a name="parameters"></a>パラメーター

*lpszPath*<br/>
URL パス。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

##  <a name="setusername"></a>  CUrl::SetUserName

ユーザー名を設定するには、このメソッドを呼び出します。

```
inline BOOL SetUserName(LPCTSTR lpszUser) throw();
```

### <a name="parameters"></a>パラメーター

*lpszUser*<br/>
ユーザー名。

### <a name="return-value"></a>戻り値

成功した場合、true を返します。

## <a name="see-also"></a>関連項目

[クラス](../../atl/reference/atl-classes.md)
