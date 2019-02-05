---
title: CHttpFile クラス
ms.date: 11/04/2016
f1_keywords:
- CHttpFile
- AFXINET/CHttpFile
- AFXINET/CHttpFile::CHttpFile
- AFXINET/CHttpFile::AddRequestHeaders
- AFXINET/CHttpFile::EndRequest
- AFXINET/CHttpFile::GetFileURL
- AFXINET/CHttpFile::GetObject
- AFXINET/CHttpFile::GetVerb
- AFXINET/CHttpFile::QueryInfo
- AFXINET/CHttpFile::QueryInfoStatusCode
- AFXINET/CHttpFile::SendRequest
- AFXINET/CHttpFile::SendRequestEx
helpviewer_keywords:
- CHttpFile [MFC], CHttpFile
- CHttpFile [MFC], AddRequestHeaders
- CHttpFile [MFC], EndRequest
- CHttpFile [MFC], GetFileURL
- CHttpFile [MFC], GetObject
- CHttpFile [MFC], GetVerb
- CHttpFile [MFC], QueryInfo
- CHttpFile [MFC], QueryInfoStatusCode
- CHttpFile [MFC], SendRequest
- CHttpFile [MFC], SendRequestEx
ms.assetid: 399e7c68-bbce-4374-8c55-206e9c7baac6
ms.openlocfilehash: 3ee92a6cb627cee701b9b98a8a32666a0877f62c
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893653"
---
# <a name="chttpfile-class"></a>CHttpFile クラス

HTTP サーバー上のファイルを要求し、読み込む機能が用意されています。

## <a name="syntax"></a>構文

```
class CHttpFile : public CInternetFile
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CHttpFile::CHttpFile](#chttpfile)|`CHttpFile` オブジェクトを作成します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CHttpFile::AddRequestHeaders](#addrequestheaders)|HTTP サーバーに送信される要求にヘッダーを追加します。|
|[CHttpFile::EndRequest](#endrequest)|使用して HTTP サーバーに送信される要求の終了、 [SendRequestEx](#sendrequestex)メンバー関数。|
|[CHttpFile::GetFileURL](#getfileurl)|指定したファイルの URL を取得します。|
|[CHttpFile::GetObject](#getobject)|HTTP サーバーへの要求の動詞のターゲット オブジェクトを取得します。|
|[CHttpFile::GetVerb](#getverb)|HTTP サーバーへの要求で使用されている動詞を取得します。|
|[CHttpFile::QueryInfo](#queryinfo)|HTTP サーバーからの応答または要求ヘッダーを返します。|
|[CHttpFile::QueryInfoStatusCode](#queryinfostatuscode)|HTTP 要求に関連付けられている状態コードを取得し、指定された`dwStatusCode`パラメーター。|
|[CHttpFile::SendRequest](#sendrequest)|HTTP サーバーへの要求を送信します。|
|[CHttpFile::SendRequestEx](#sendrequestex)|使用して HTTP サーバーに要求を送信、[書き込み](../../mfc/reference/cinternetfile-class.md#write)または[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)メソッドの`CInternetFile`します。|

## <a name="remarks"></a>Remarks

インスタンスを作成する必要がある場合は、インターネット セッションでは、HTTP サーバーからデータを読み取り、`CHttpFile`します。

方法の詳細については、`CHttpFile`クラスでは、その他の MFC インターネット機能は、記事をご覧ください。[インターネットが WinInet を使用したプログラミング](../../mfc/win32-internet-extensions-wininet.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

[CInternetFile](../../mfc/reference/cinternetfile-class.md)

`CHttpFile`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxinet.h

##  <a name="addrequestheaders"></a>  CHttpFile::AddRequestHeaders

1 つ追加するには、このメンバー関数を呼び出すか、HTTP 要求に複数の HTTP 要求ヘッダーを処理します。

```
BOOL AddRequestHeaders(
    LPCTSTR pstrHeaders,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW,
    int dwHeadersLen = -1);

BOOL AddRequestHeaders(
    CString& str,
    DWORD dwFlags = HTTP_ADDREQ_FLAG_ADD_IF_NEW);
```

### <a name="parameters"></a>パラメーター

*pstrHeaders*<br/>
ヘッダーまたは要求に追加するヘッダーを含む文字列へのポインター。 各ヘッダーは、CR/LF の組み合わせで終わる必要があります。

*dwFlags*<br/>
新しいヘッダーのセマンティクスを変更します。 次のいずれかの値を指定します。

- HTTP_ADDREQ_FLAG_COALESCE マージを後続のヘッダーが見つかりました。 最初のヘッダーを追加するフラグを使用して、同じ名前のヘッダー。 たとえば、"Accept: テキスト/\*"続けて"Accept: オーディオ/\*"1 つのヘッダーの形成に"Accept: テキスト/\*、オーディオ/\*"。 まとめられた、または別のヘッダーで送信された要求で受信したデータに対して結合方式の保証を呼び出し元のアプリケーションの責任です。

- HTTP_ADDREQ_FLAG_REPLACE は、削除を実行し、交換の現在のヘッダーに追加します。 ヘッダー名は現在のヘッダーの削除に使用して、新しいヘッダーを追加する、完全な値が使用されます。 ヘッダー値が空のヘッダーが見つかった場合は削除されます。 指定しない場合、空の場合、ヘッダー値が置き換えられます。

- HTTP_ADDREQ_FLAG_ADD_IF_NEW のみが既に存在しない場合は、ヘッダーを追加します。 1 つが存在する場合は、エラーが返されます。

- HTTP_ADDREQ_FLAG_ADD with REPLACE を使用します。 存在しない場合は、ヘッダーを追加します。

*dwHeadersLen*<br/>
長さを文字単位の*pstrHeaders*します。 場合は、-1 L では、これは*pstrHeaders*は 0 で終了すると見なされ、長さが計算されます。

*str*<br/>
参照を[CString](../../atl-mfc-shared/reference/cstringt-class.md)要求ヘッダーまたは追加するヘッダーを含むオブジェクト。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)エラーの原因を特定するということがあります。

### <a name="remarks"></a>Remarks

`AddRequestHeaders` HTTP 要求のハンドルに、追加の自由な形式のヘッダーを追加します。 HTTP サーバーに送信される正確な要求の詳細に制御を必要とする高度なクライアントで使用するものでは。

> [!NOTE]
>  アプリケーションで複数のヘッダーを渡すことができます*pstrHeaders*または*str*の`AddRequestHeaders`HTTP_ADDREQ_FLAG_ADD または HTTP_ADDREQ_FLAG_ADD_IF_NEW を使用して呼び出します。 1 つだけのヘッダーを指定する、アプリケーションが削除または置換 HTTP_ADDREQ_FLAG_REMOVE または HTTP_ADDREQ_FLAG_REPLACE を使用してヘッダーを試みると、 *lpszHeaders*します。

##  <a name="chttpfile"></a>  CHttpFile::CHttpFile

このメンバー関数が構築すると呼ばれる、`CHttpFile`オブジェクト。

```
CHttpFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrObject,
    LPCTSTR pstrServer,
    LPCTSTR pstrVerb,
    DWORD_PTR dwContext);

CHttpFile(
    HINTERNET hFile,
    LPCTSTR pstrVerb,
    LPCTSTR pstrObject,
    CHttpConnection* pConnection);
```

### <a name="parameters"></a>パラメーター

*hFile*<br/>
インターネット ファイルへのハンドル。

*hSession*<br/>
インターネット セッションへのハンドル。

*pstrObject*<br/>
含んでいる文字列へのポインター、`CHttpFile`オブジェクト。

*pstrServer*<br/>
サーバーの名前を含む文字列へのポインター。

*pstrVerb*<br/>
要求を送信するときに使用されるメソッドを含む文字列へのポインター。 POST、HEAD、または取得します。

*dwContext*<br/>
コンテキスト識別子を`CHttpFile`オブジェクト。 参照してください**解説**このパラメーターの詳細についてはします。

*pConnection*<br/>
ポインターを[CHttpConnection](../../mfc/reference/chttpconnection-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

構築することはありません、`CHttpFile`オブジェクトに直接; 呼び出しではなく[できます](../../mfc/reference/cinternetsession-class.md#openurl)または[しないで](../../mfc/reference/chttpconnection-class.md#openrequest)代わりにします。

既定値`dwContext`に MFC によって送信される、`CHttpFile`オブジェクトから、 [CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトの作成、`CHttpFile`オブジェクト。 呼び出すと`CInternetSession::OpenURL`または`CHttpConnection`を構築する、`CHttpFile`オブジェクト コンテキスト識別子を独自の値に設定する既定値をオーバーライドすることができます。 コンテキスト識別子が返される[対応](../../mfc/reference/cinternetsession-class.md#onstatuscallback)が識別されるオブジェクトの状態を提供します。 記事をご覧ください[インターネットの最初の手順。WinInet](../../mfc/wininet-basics.md)コンテキスト識別子の詳細についてはします。

##  <a name="endrequest"></a>  CHttpFile::EndRequest

使用して HTTP サーバーに送信される要求を終了するには、このメンバー関数を呼び出す、 [SendRequestEx](#sendrequestex)メンバー関数。

```
BOOL EndRequest(
    DWORD dwFlags = 0,
    LPINTERNET_BUFFERS lpBuffIn = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>パラメーター

*dwFlags*<br/>
操作を記述するフラグ。 適切なフラグの一覧は、次を参照してください。 [HttpEndRequest](/windows/desktop/api/wininet/nf-wininet-httpendrequesta) Windows SDK に含まれています。

*lpBuffIn*<br/>
初期化されたへのポインター[記述](/windows/desktop/api/wininet/ns-wininet-_internet_buffersa)操作に使用される入力バッファーをについて説明します。

*dwContext*<br/>
`CHttpFile` 操作のコンテキスト識別子。 このパラメーターの詳細については、「解説」を参照してください。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しに失敗した場合は、スローされたエラーの原因を特定[CInternetException](../../mfc/reference/cinternetexception-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

既定値*独自*に MFC によって送信される、`CHttpFile`オブジェクトから、 [CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトの作成、`CHttpFile`オブジェクト。 呼び出すと[できます](../../mfc/reference/cinternetsession-class.md#openurl)または[CHttpConnection](../../mfc/reference/chttpconnection-class.md)を構築する、`CHttpFile`オブジェクト コンテキスト識別子を独自の値に設定する既定値をオーバーライドすることができます。 コンテキスト識別子が返される[対応](../../mfc/reference/cinternetsession-class.md#onstatuscallback)が識別されるオブジェクトの状態を提供します。 記事を参照して[インターネットの最初の手順。WinInet](../../mfc/wininet-basics.md)コンテキスト識別子の詳細についてはします。

##  <a name="getfileurl"></a>  CHttpFile::GetFileURL

URL として、HTTP ファイルの名前を取得するには、このメンバー関数を呼び出します。

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>戻り値

A [CString](../../atl-mfc-shared/reference/cstringt-class.md)このファイルに関連付けられたリソースを参照する URL を含むオブジェクト。

### <a name="remarks"></a>Remarks

このメンバー関数を使用して、呼び出しに成功した後のみ[SendRequest](#sendrequest)か、または、`CHttpFile`によって正常に作成されたオブジェクト[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)します。

##  <a name="getobject"></a>  CHttpFile::GetObject

これに関連付けられているオブジェクトの名前を取得するには、このメンバー関数を呼び出す`CHttpFile`します。

```
CString GetObject() const;
```

### <a name="return-value"></a>戻り値

A [CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクトの名前を表すオブジェクト。

### <a name="remarks"></a>Remarks

このメンバー関数を使用して、呼び出しに成功した後のみ[SendRequest](#sendrequest)か、または、`CHttpFile`によって正常に作成されたオブジェクト[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)します。

##  <a name="getverb"></a>  CHttpFile::GetVerb

これに関連付けられている HTTP 動詞 (またはメソッド) を取得するには、このメンバー関数を呼び出す`CHttpFile`します。

```
CString GetVerb() const;
```

### <a name="return-value"></a>戻り値

A [CString](../../atl-mfc-shared/reference/cstringt-class.md) HTTP 動詞 (またはメソッド) の名前を表すオブジェクト。

### <a name="remarks"></a>Remarks

このメンバー関数を使用して、呼び出しに成功した後のみ[SendRequest](#sendrequest)か、または、`CHttpFile`によって正常に作成されたオブジェクト[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)します。

##  <a name="queryinfo"></a>  CHttpFile::QueryInfo

応答を返すか、HTTP 要求からヘッダーを要求するには、このメンバー関数を呼び出します。

```
BOOL QueryInfo(
    DWORD dwInfoLevel,
    LPVOID lpvBuffer,
    LPDWORD lpdwBufferLength,
    LPDWORD lpdwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    CString& str,
    LPDWORD dwIndex = NULL) const;

BOOL QueryInfo(
    DWORD dwInfoLevel,
    SYSTEMTIME* pSysTime,
    LPDWORD dwIndex = NULL) const;
```

### <a name="parameters"></a>パラメーター

*dwInfoLevel*<br/>
クエリと、次のフラグを要求された情報の種類を指定する属性の組み合わせです。

- ヘッダーがヘッダーの名前を検索およびでは、この値を返します*lpvBuffer*に出力します。 ヘッダーがヘッダーが見つからない場合は、アサーションをスローします。

- HTTP_QUERY_FLAG_REQUEST_HEADERS 通常、アプリケーションが応答ヘッダーをクエリできますが、アプリケーションは、このフラグを使用して要求ヘッダーを照会もできます。

- これらのヘッダーの値は「最終更新時刻、」などの日付/時刻文字列の HTTP_QUERY_FLAG_SYSTEMTIME このフラグが標準の Win32 とヘッダー値を返します[SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)にアプリケーションを必要としない構造体データを解析します。 このフラグを使用する場合は、使用する可能性がある、`SYSTEMTIME`関数のオーバーライドします。

- これらのヘッダーの値を持つは、状態コードなどの番号を HTTP_QUERY_FLAG_NUMBER このフラグは、32 ビットの数値としてデータを返します。

参照してください、**解説**使用可能な値の一覧についてはセクション。

*lpvBuffer*<br/>
情報を受け取るバッファーへのポインター。

*lpdwBufferLength*<br/>
項目で、これは文字またはバイト数で、データ バッファーの長さを示す値を指します。 参照してください、**解説**セクションは、このパラメーターの詳細情報します。

*lpdwIndex*<br/>
ヘッダーの 0 から始まるインデックスへのポインター。 NULL にすることができます。 このフラグを使用して、同じ名前の複数のヘッダーの列挙します。 入力で*時*を返す指定したヘッダーのインデックスを示します。 出力では、*時*次のヘッダーのインデックスを示します。 次のインデックスが見つからない場合は、見つからないが返されます。

*str*<br/>
参照、 [CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクトが返される情報を受信します。

*dwIndex*<br/>
インデックス値。 参照してください*時*します。

*pSysTime*<br/>
Win32 へのポインター [SYSTEMTIME](/windows/desktop/api/minwinbase/ns-minwinbase-systemtime)構造体。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)エラーの原因を特定するということがあります。

### <a name="remarks"></a>Remarks

このメンバー関数を使用して、呼び出しに成功した後のみ[SendRequest](#sendrequest)か、または、`CHttpFile`によって正常に作成されたオブジェクト[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)します。

次の種類からのデータを取得する`QueryInfo`:

- 文字列 (既定値)

- `SYSTEMTIME` (の"データ:""Expires:"など、ヘッダー)

- (STATUS_CODE、CONTENT_LENGTH など) の DWORD

文字列が、バッファーに書き込まれ、メンバー関数が成功すると、 `lpdwBufferLength` -終端の NULL 文字の 1 文字の文字列の長さが含まれています。

使用可能な*dwInfoLevel*値が含まれます。

- HTTP_QUERY_MIME_VERSION

- HTTP_QUERY_CONTENT_TYPE

- HTTP_QUERY_CONTENT_TRANSFER_ENCODING

- HTTP_QUERY_CONTENT_ID

- HTTP_QUERY_CONTENT_DESCRIPTION

- HTTP_QUERY_CONTENT_LENGTH

- HTTP_QUERY_ALLOWED_METHODS

- HTTP_QUERY_PUBLIC_METHODS

- HTTP_QUERY_DATE

- HTTP_QUERY_EXPIRES

- HTTP_QUERY_LAST_MODIFIED

- HTTP_QUERY_MESSAGE_ID

- HTTP_QUERY_URI

- HTTP_QUERY_DERIVED_FROM

- HTTP_QUERY_LANGUAGE

- HTTP_QUERY_COST

- HTTP_QUERY_WWW_LINK

- HTTP_QUERY_PRAGMA

- HTTP_QUERY_VERSION

- HTTP_QUERY_STATUS_CODE

- HTTP_QUERY_STATUS_TEXT

- HTTP_QUERY_RAW_HEADERS

- HTTP_QUERY_RAW_HEADERS_CRLF

##  <a name="queryinfostatuscode"></a>  CHttpFile::QueryInfoStatusCode

HTTP 要求に関連付けられている状態コードを取得するには、このメンバー関数を呼び出すし、指定された配置*し*パラメーター。

```
BOOL QueryInfoStatusCode(DWORD& dwStatusCode) const;
```

### <a name="parameters"></a>パラメーター

*dwStatusCode*<br/>
状態コードへの参照。 状態コードは、要求されたイベントの成否を示します。 参照してください**解説**ステータス コードの説明のいくつか。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)エラーの原因を特定するということがあります。

### <a name="remarks"></a>Remarks

このメンバー関数を使用して、呼び出しに成功した後のみ[SendRequest](#sendrequest)か、または、`CHttpFile`によって正常に作成されたオブジェクト[OpenURL](../../mfc/reference/cinternetsession-class.md#openurl)します。

HTTP 状態コードは、成功または要求の失敗を示すグループに分類されます。 次の表は、ステータス コード グループと、最も一般的な HTTP ステータス コードを示しています。

|グループ化|説明|
|-----------|-------------|
|200-299|成功|
|300-399|情報|
|400-499|要求エラー|
|500-599|サーバー エラー|

一般的な HTTP ステータス コード:

|状態コード|説明|
|-----------------|-------------|
|200|URL にある、伝送次のとおりです。|
|400|解釈できない要求|
|404|要求 URL が見つかりません。|
|405|サーバーが要求されたメソッドをサポートしていません|
|500|不明なサーバー エラー|
|503|サーバーの容量に達しました|

##  <a name="sendrequest"></a>  CHttpFile::SendRequest

HTTP サーバーに要求を送信するには、このメンバー関数を呼び出します。

```
BOOL SendRequest(
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLen = 0,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);

BOOL SendRequest(
    CString& strHeaders,
    LPVOID lpOptional = NULL,
    DWORD dwOptionalLen = 0);
```

### <a name="parameters"></a>パラメーター

*pstrHeaders*<br/>
送信するヘッダーの名前を含む文字列へのポインター。

*dwHeadersLen*<br/>
識別されるヘッダーの長さ*pstrHeaders*します。

*lpOptional*<br/>
任意の省略可能な要求ヘッダーの直後に送信するデータ。 これは通常、POST と PUT 操作を使用します。 送信する省略可能なデータがない場合は、NULL にできます。

*dwOptionalLen*<br/>
長さ*lpOptional*します。

*strHeaders*<br/>
送信される要求のヘッダーの名前を含む文字列。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しに失敗した場合は、スローされたエラーの原因を特定[CInternetException](../../mfc/reference/cinternetexception-class.md)オブジェクト。

##  <a name="sendrequestex"></a>  CHttpFile::SendRequestEx

HTTP サーバーに要求を送信するには、このメンバー関数を呼び出します。

```
BOOL SendRequestEx(
    DWORD dwTotalLen,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);

BOOL SendRequestEx(
    LPINTERNET_BUFFERS lpBuffIn,
    LPINTERNET_BUFFERS lpBuffOut,
    DWORD dwFlags = HSR_INITIATE,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>パラメーター

*dwTotalLen*<br/>
要求で送信されるバイト数。

*dwFlags*<br/>
操作を記述するフラグ。 適切なフラグの一覧は、次を参照してください。 [HttpSendRequestEx](/windows/desktop/api/wininet/nf-wininet-httpsendrequestexa) Windows SDK に含まれています。

*dwContext*<br/>
`CHttpFile` 操作のコンテキスト識別子。 このパラメーターの詳細については、「解説」を参照してください。

*lpBuffIn*<br/>
初期化されたへのポインター[記述](/windows/desktop/api/wininet/ns-wininet-_internet_buffersa)操作に使用される入力バッファーをについて説明します。

*lpBuffOut*<br/>
操作に使用される出力バッファーを記述する初期化の記述へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外の値。 呼び出しに失敗した場合は、スローされたエラーの原因を特定[CInternetException](../../mfc/reference/cinternetexception-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

この関数により、アプリケーションを使用してデータを送信する、[書き込み](../../mfc/reference/cinternetfile-class.md#write)と[WriteString](../../mfc/reference/cinternetfile-class.md#writestring)メソッドの`CInternetFile`します。 この関数のいずれかのオーバーライドを呼び出す前に送信するデータの長さを知る必要があります。 最初のオーバーライドに送信するデータの長さを指定することができます。 2 番目のオーバーライドでは、詳しくバッファーを記述するために使用した構造体へのポインターを受け取ります。

コンテンツがファイルに書き込まれると、呼び出す[EndRequest](#endrequest)操作を終了します。

既定値*独自*に MFC によって送信される、`CHttpFile`オブジェクトから、 [CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトの作成、`CHttpFile`オブジェクト。 呼び出すと[できます](../../mfc/reference/cinternetsession-class.md#openurl)または[CHttpConnection](../../mfc/reference/chttpconnection-class.md)を構築する、`CHttpFile`オブジェクト コンテキスト識別子を独自の値に設定する既定値をオーバーライドすることができます。 コンテキスト識別子が返される[対応](../../mfc/reference/cinternetsession-class.md#onstatuscallback)が識別されるオブジェクトの状態を提供します。 記事をご覧ください[インターネットの最初の手順。WinInet](../../mfc/wininet-basics.md)コンテキスト識別子の詳細についてはします。

### <a name="example"></a>例

このコード フラグメントでは、MFCISAPI という名前の DLL を文字列の内容を送信します。ローカル ホスト サーバー上の DLL です。 この例で使用する 1 つだけの呼び出し中に`WriteString`、複数の呼び出しを使用するブロックでデータを送信可能です。

[!code-cpp[NVC_MFCWinInet#9](../../mfc/codesnippet/cpp/chttpfile-class_1.cpp)]

## <a name="see-also"></a>関連項目

[CInternetFile クラス](../../mfc/reference/cinternetfile-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CInternetFile クラス](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile クラス](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpConnection クラス](../../mfc/reference/chttpconnection-class.md)
