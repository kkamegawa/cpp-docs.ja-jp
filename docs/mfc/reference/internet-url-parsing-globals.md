---
title: インターネット URL 解析用グローバル関数とヘルパー
ms.date: 04/03/2017
helpviewer_keywords:
- parsing, URLs
- URLs, parsing
ms.assetid: 46c6384f-e4a6-4dbd-9196-219c19040ec5
ms.openlocfilehash: 310e4ffb3fc207d874e97ba1fac65f6f8cb41a31
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611033"
---
# <a name="internet-url-parsing-globals-and-helpers"></a>インターネット URL 解析用グローバル関数とヘルパー

クライアントはインターネット サーバーにクエリを送信するときは、クライアントに関する情報を抽出するのに URL 解析用グローバルのいずれかを使用できます。 ヘルパー関数は、その他のインターネット機能を提供します。

## <a name="internet-url-parsing-globals"></a>インターネット URL 解析用グローバル関数

|||
|-|-|
|[AfxParseURL](#afxparseurl)|URL 文字列を解析し、サービスとそのコンポーネントの型を返します。|
|[AfxParseURLEx](#afxparseurlex)|URL 文字列を解析し、サービスとそのコンポーネントでは、できるだけでなく、ユーザー名とパスワードの種類を返します。|

## <a name="other-internet-helpers"></a>その他のインターネット ヘルパー

|||
|-|-|
|[AfxThrowInternetException](#afxthrowinternetexception)|インターネット接続に関連する例外をスローします。|
|[AfxGetInternetHandleType](#afxgetinternethandletype)|インターネット ハンドルの種類を決定します。|

##  <a name="afxparseurl"></a>  AfxParseURL

このグローバル[できます](../../mfc/reference/cinternetsession-class.md#openurl)します。

```
BOOL AFXAPI AfxParseURL(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort);
```

### <a name="parameters"></a>パラメーター

*pstrURL*<br/>
解析する URL を含む文字列へのポインター。

*dwServiceType*<br/>
インターネット サービスの種類を示します。 次の値を指定できます。

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
サービスの種類を次の URL の最初のセグメント。

*strObject*<br/>
URL を参照するオブジェクト (空でもかまいません)。

*nPort*<br/>
いずれかが存在する場合に、URL のサーバーまたはオブジェクトのいずれかの部分から決定されます。

### <a name="return-value"></a>戻り値

以外の場合は、URL が正常に解析します。空であるか、既知のインターネット サービスの種類が含まれていない場合、それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

URL 文字列を解析し、サービスとそのコンポーネントの型を返します。

たとえば、`AfxParseURL`フォームの Url を解析*service://server/dir/dir/object.ext:port*し、次のように格納されているそのコンポーネントを返します。

*strServer* "server"= =

*strObject* = ="/dir/dir/object/object.ext"

*nPort* == #port

*dwServiceType* == #service

> [!NOTE]
>  この関数を呼び出すには、プロジェクトは AFXINET を含める必要があります。H.

### <a name="requirements"></a>必要条件

  **ヘッダー** afxinet.h

##  <a name="afxparseurlex"></a>  AfxParseURLEx

このグローバル関数は、拡張のバージョンの[AfxParseURL](#afxparseurl)で使用されます[できます](../../mfc/reference/cinternetsession-class.md#openurl)します。

```
BOOL AFXAPI AfxParseURLEx(
    LPCTSTR pstrURL,
    DWORD& dwServiceType,
    CString& strServer,
    CString& strObject,
    INTERNET_PORT& nPort,
    CString& strUsername,
    CString& strPassword,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>パラメーター

*pstrURL*<br/>
解析する URL を含む文字列へのポインター。

*dwServiceType*<br/>
インターネット サービスの種類を示します。 次の値を指定できます。

- AFX_INET_SERVICE_FTP

- AFX_INET_SERVICE_HTTP

- AFX_INET_SERVICE_HTTPS

- AFX_INET_SERVICE_GOPHER

- AFX_INET_SERVICE_FILE

- AFX_INET_SERVICE_MAILTO

- AFX_INET_SERVICE_NEWS

- AFX_INET_SERVICE_NNTP

- AFX_INET_SERVICE_TELNET

- AFX_INET_SERVICE_WAIS

- AFX_INET_SERVICE_MID

- AFX_INET_SERVICE_CID

- AFX_INET_SERVICE_PROSPERO

- AFX_INET_SERVICE_AFS

- AFX_INET_SERVICE_UNK

*strServer*<br/>
サービスの種類を次の URL の最初のセグメント。

*strObject*<br/>
URL を参照するオブジェクト (空でもかまいません)。

*nPort*<br/>
いずれかが存在する場合に、URL のサーバーまたはオブジェクトのいずれかの部分から決定されます。

*strUsername*<br/>
参照を`CString`ユーザーの名前を表すオブジェクト。

*strPassword*<br/>
参照を`CString`ユーザーのパスワードを格納しているオブジェクト。

*dwFlags*<br/>
URL を解析する方法を制御するフラグ。 次の値の組み合わせになります。

|値|説明|
|-----------|-------------|
|ICU_DECODE|%XX エスケープ シーケンスを文字に変換します。|
|ICU_NO_ENCODE|安全でない文字をエスケープ シーケンスに変換されません。|
|ICU_NO_META|(「\.」などのメタデータのシーケンスを削除しないでください。 および「\..」)URL。|
|ICU_ENCODE_SPACES_ONLY|Spaces only. をエンコードします。|
|ICU_BROWSER_MODE|エンコードまたは '#' の後に文字をデコードまたは '後の後続の空白を削除しない' です。 この値が指定されていない場合は、URL 全体はエンコードされ、後続の空白が削除されます。|

変換が安全でない文字や meta シーケンスのすべてのフラグがない、MFC の既定を使用する場合 (など\\.、\.. と\\...) をエスケープするシーケンスします。

### <a name="return-value"></a>戻り値

以外の場合は、URL が正常に解析します。空であるか、既知のインターネット サービスの種類が含まれていない場合、それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

これにより、URL 文字列を解析し、サービスとそのコンポーネントでは、できるだけでなく、ユーザーの名とパスワードの種類を返します。 どのように安全でない文字を指定するフラグは、処理されます。

> [!NOTE]
>  この関数を呼び出すには、プロジェクトは AFXINET を含める必要があります。H.

### <a name="requirements"></a>必要条件

  **ヘッダー** afxinet.h

## <a name="afxgetinternethandletype"></a>  AfxGetInternetHandleType

このグローバル関数を使用して、インターネット ハンドルの種類を決定します。

### <a name="syntax"></a>構文

  ```
DWORD AFXAPI AfxGetInternetHandleType(  HINTERNET hQuery );
```

### <a name="parameters"></a>パラメーター

*hQuery*<br/>
インターネット クエリへのハンドル。

### <a name="return-value"></a>戻り値

WININET で定義されているインターネット サービスの種類のいずれか。H. これらのインターネット サービスの一覧については、「解説」を参照してください。 ハンドルは、null または認識されない、AFX_INET_SERVICE_UNK を返します。

### <a name="remarks"></a>Remarks

次の一覧には、によって返される使用可能なインターネットの型が含まれています。`AfxGetInternetHandleType`します。

- INTERNET_HANDLE_TYPE_INTERNET

- INTERNET_HANDLE_TYPE_CONNECT_FTP

- INTERNET_HANDLE_TYPE_CONNECT_GOPHER

- INTERNET_HANDLE_TYPE_CONNECT_HTTP

- INTERNET_HANDLE_TYPE_FTP_FIND

- INTERNET_HANDLE_TYPE_FTP_FIND_HTML

- INTERNET_HANDLE_TYPE_FTP_FILE

- INTERNET_HANDLE_TYPE_FTP_FILE_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FIND

- INTERNET_HANDLE_TYPE_GOPHER_FIND_HTML

- INTERNET_HANDLE_TYPE_GOPHER_FILE

- INTERNET_HANDLE_TYPE_GOPHER_FILE_HTML

- INTERNET_HANDLE_TYPE_HTTP_REQUEST

> [!NOTE]
>  この関数を呼び出すために、プロジェクトは AFXINET を含める必要があります。H.

### <a name="requirements"></a>必要条件

**ヘッダー:** afxinet.h

## <a name="afxthrowinternetexception"></a>  AfxThrowInternetException

インターネットの例外をスローします。

### <a name="syntax"></a>構文

```
   void AFXAPI AfxThrowInternetException(  DWORD dwContext,  DWORD dwError = 0 );
```

### <a name="parameters"></a>パラメーター

*dwContext*<br/>
エラーの原因となった操作のコンテキスト id。 既定値*独自*で最初に指定された[CInternetSession](cinternetsession-class.md)に渡されると[CInternetConnection](cinternetconnection-class.md)- と[CInternetFile](cinternetfile-class.md)-クラスを派生します。 既定のオーバーライドは、通常、接続や、ファイルに対して実行される特定の操作、*独自*独自の。 この値に返されます、[対応](cinternetsession-class.md#onstatuscallback)特定の操作の状態を識別するためにします。

*dwError*<br/>
例外の原因となったエラー。

### <a name="remarks"></a>Remarks

オペレーティング システム エラー コードに基づいて、原因を判断するためにあります。

> [!NOTE]
>  この関数を呼び出すには、プロジェクトは AFXINET を含める必要があります。H.

### <a name="requirements"></a>必要条件

**ヘッダー:** afxinet.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](mfc-macros-and-globals.md)<br/>
[CInternetException クラス](cinternetexception-class.md)<br/>
[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)
