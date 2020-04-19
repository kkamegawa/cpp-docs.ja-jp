---
title: CInternetSession クラス
ms.date: 06/20/2018
f1_keywords:
- CInternetSession
- AFXINET/CInternetSession
- AFXINET/CInternetSession::CInternetSession
- AFXINET/CInternetSession::Close
- AFXINET/CInternetSession::EnableStatusCallback
- AFXINET/CInternetSession::GetContext
- AFXINET/CInternetSession::GetCookie
- AFXINET/CInternetSession::GetCookieLength
- AFXINET/CInternetSession::GetFtpConnection
- AFXINET/CInternetSession::GetGopherConnection
- AFXINET/CInternetSession::GetHttpConnection
- AFXINET/CInternetSession::OnStatusCallback
- AFXINET/CInternetSession::OpenURL
- AFXINET/CInternetSession::SetCookie
- AFXINET/CInternetSession::SetOption
helpviewer_keywords:
- CInternetSession [MFC], CInternetSession
- CInternetSession [MFC], Close
- CInternetSession [MFC], EnableStatusCallback
- CInternetSession [MFC], GetContext
- CInternetSession [MFC], GetCookie
- CInternetSession [MFC], GetCookieLength
- CInternetSession [MFC], GetFtpConnection
- CInternetSession [MFC], GetGopherConnection
- CInternetSession [MFC], GetHttpConnection
- CInternetSession [MFC], OnStatusCallback
- CInternetSession [MFC], OpenURL
- CInternetSession [MFC], SetCookie
- CInternetSession [MFC], SetOption
ms.assetid: ef54feb4-9d0f-4e65-a45d-7a4cf6c40e51
ms.openlocfilehash: c9b8eaf51820dfcd08c1390c8645978fa403931d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505843"
---
# <a name="cinternetsession-class"></a>CInternetSession クラス

単一のインターネット セッションまたは複数の同時インターネット セッションを作成し、初期化します。必要な場合は、プロキシ サーバーへの接続も記述します。

## <a name="syntax"></a>構文

```cpp
class CInternetSession : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CInternetSession:: CInternetSession](#cinternetsession)|`CInternetSession` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CInternetSession:: Close](#close)|インターネットセッションが終了したときに、インターネット接続を閉じます。|
|[CInternetSession::EnableStatusCallback](#enablestatuscallback)|ステータスコールバックルーチンを確立します。|
|[CInternetSession::GetContext](#getcontext)|インターネットセッションが終了したときに、インターネット接続を閉じます。|
|[CInternetSession::GetCookie](#getcookie)|指定された URL とそのすべての親 Url のクッキーを返します。|
|[CInternetSession::GetCookieLength](#getcookielength)|バッファーに格納されているクッキーの長さを指定する変数を取得します。|
|[CInternetSession:: GetFtpConnection](#getftpconnection)|サーバーとの FTP セッションを開きます。 ユーザーのログ。|
|[CInternetSession:: GetGopherConnection](#getgopherconnection)|接続を開こうとしているアプリケーションの gopher サーバーを開きます。|
|[CInternetSession:: GetHttpConnection](#gethttpconnection)|接続を開こうとしているアプリケーションの HTTP サーバーを開きます。|
|[CInternetSession:: OnStatusCallback](#onstatuscallback)|状態コールバックが有効になっている場合に、操作の状態を更新します。|
|[CInternetSession::OpenURL](#openurl)|URL を解析して開きます。|
|[CInternetSession:: SetCookie](#setcookie)|指定された URL のクッキーを設定します。|
|[CInternetSession:: SetOption](#setoption)|インターネットセッションのオプションを設定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CInternetSession:: operator HINTERNET](#operator_hinternet)|現在のインターネットセッションを対象としたハンドル。|

## <a name="remarks"></a>Remarks

アプリケーションの実行中にインターネット接続を維持する必要がある場合は、 [CWinApp](../../mfc/reference/cwinapp-class.md)クラス`CInternetSession`のメンバーを作成できます。

インターネットセッションを確立したら、 [OpenURL](#openurl)を呼び出すことができます。 `CInternetSession`次に、グローバル関数[AfxParseURL](internet-url-parsing-globals.md#afxparseurl)を呼び出して、URL を解析します。 プロトコルの種類に関係なく`CInternetSession` 、は URL を解釈し、管理します。 URL リソース "file://" で識別されるローカルファイルの要求を処理できます。 `OpenURL`渡された名前がローカルファイルの場合は、 [CStdioFile](../../mfc/reference/cstdiofile-class.md)オブジェクトへのポインターを返します。

を使用して`OpenURL`インターネットサーバーで URL を開くと、サイトから情報を読み取ることができます。 サーバー上のファイルに対してサービス固有の操作 (HTTP、FTP、gopher など) を実行する場合は、そのサーバーとの適切な接続を確立する必要があります。 特定のサービスに対して直接特定の種類の接続を開くには、次のいずれかのメンバー関数を使用します。

- [GetGopherConnection](#getgopherconnection)では、gopher サービスへの接続を開くことができます。

- [GetHttpConnection](#gethttpconnection)は、HTTP サービスへの接続を開きます。

- [Getftpconnection](#getftpconnection)を呼び出して、FTP サービスへの接続を開きます。

[SetOption](#setoption)を使用すると、タイムアウト値、再試行回数など、セッションのクエリオプションを設定できます。

`CInternetSession`メンバー関数[SetCookie](#setcookie)、 [getcookie](#getcookie)、および[GetCookieLength](#getcookielength)は、サーバーとスクリプトがクライアントワークステーションに関する状態情報を保持する、Win32 cookie データベースを管理するための手段を提供します。

基本的なインターネットプログラミングタスクの詳細については、 [インターネットの最初の手順に関する記事を参照してください。WinInet](../../mfc/wininet-basics.md)。 MFC WinInet クラスの使用に関する一般情報については、「 [wininet を使用したインターネットプログラミング](../../mfc/win32-internet-extensions-wininet.md)」を参照してください。

> [!NOTE]
> `CInternetSession`サポートされていないサービスの種類の[AfxThrowNotSupportedException](exception-processing.md#afxthrownotsupportedexception)をスローします。 現在サポートされているサービスの種類は次のとおりです。FTP、HTTP、gopher、およびファイル。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;`CInternetSession`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxinet.h

## <a name="cinternetsession"></a>CInternetSession:: CInternetSession

このメンバー関数は、 `CInternetSession`オブジェクトが作成されるときに呼び出されます。

```cpp
CInternetSession(
    LPCTSTR pstrAgent = NULL,
    DWORD_PTR dwContext = 1,
    DWORD dwAccessType = PRE_CONFIG_INTERNET_ACCESS,
    LPCTSTR pstrProxyName = NULL,
    LPCTSTR pstrProxyBypass = NULL,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>パラメーター

*pstrAgent*<br/>
インターネット機能を呼び出すアプリケーションまたはエンティティの名前 (たとえば、"Microsoft Internet Browser") を識別する文字列へのポインター。 *PstrAgent*が null (既定値) の場合、フレームワークはグローバル関数[AfxGetAppName](application-information-and-management.md#afxgetappname)を呼び出します。この関数は、アプリケーション名を含む null で終わる文字列を返します。 一部のプロトコルでは、この文字列を使用して、アプリケーションをサーバーに識別します。

*dwContext*<br/>
操作のコンテキスト識別子。 *dwContext*は、 [CInternetSession:: OnStatusCallback](#onstatuscallback)によって返される操作の状態情報を識別します。 既定値は1に設定されています。ただし、操作の特定のコンテキスト ID を明示的に割り当てることができます。 オブジェクトとそれが実行する作業は、そのコンテキスト ID に関連付けられます。

*dwAccessType*<br/>
必要なアクセスの種類。 有効な値を次に示します。そのうちの1つだけを指定できます。

- INTERNET_OPEN_TYPE_PRECONFIG は、レジストリの事前構成済みの設定を使用して接続します。 このアクセスの種類は、既定値として設定されます。 *DwAccessType*をプロキシ経由で接続するには、次の値に設定します。次に、レジストリを適切に設定します。

- INTERNET_OPEN_TYPE_DIRECT インターネットに直接接続します。

- INTERNET_OPEN_TYPE_PROXY は、CERN プロキシ経由で接続します。

さまざまな種類のプロキシで接続する方法については、[一般的な FTP クライアントアプリケーションの手順](../../mfc/steps-in-a-typical-ftp-client-application.md)に関する説明を参照してください。

*pstrProxyName*<br/>
*DwAccessType*が INTERNET_OPEN_TYPE_PROXY に設定されている場合は、優先する CERN プロキシの名前。 既定値は NULL です。

*pstrProxyBypass*<br/>
サーバーアドレスのオプションのリストを含む文字列へのポインター。 これらのアドレスは、プロキシアクセスを使用するときにバイパスされる可能性があります。 NULL 値を指定した場合は、バイパスリストがレジストリから読み込まれます。 このパラメーターは、 *dwAccessType*が INTERNET_OPEN_TYPE_PROXY に設定されている場合にのみ意味を持ちます。

*dwFlags*<br/>
さまざまなキャッシュオプションを示します。 既定値は0に設定されています。 指定できる値は次のとおりです。

- INTERNET_FLAG_DONT_CACHE は、ローカルまたは任意のゲートウェイサーバーにデータをキャッシュしません。

- INTERNET_FLAG_OFFLINE のダウンロード操作は、永続キャッシュのみで満たされます。 項目がキャッシュに存在しない場合は、適切なエラーコードが返されます。 このフラグは、ビットごとの**or** ( **&#124;** ) 演算子と組み合わせることができます。

### <a name="remarks"></a>Remarks

`CInternetSession`は、アプリケーションによって呼び出される最初のインターネット関数です。 内部データ構造を初期化し、アプリケーションからの今後の呼び出しのために準備します。

インターネット接続を開けない場合は、 `CInternetSession` [AfxThrowInternetException](internet-url-parsing-globals.md#afxthrowinternetexception)をスローします。

### <a name="example"></a>例

[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)の例を参照してください。

## <a name="close"></a>CInternetSession:: Close

このメンバー関数は、アプリケーションがオブジェクトの`CInternetSession`使用を終了したときに呼び出します。

```cpp
virtual void Close();
```

### <a name="example"></a>例

[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)の例を参照してください。

## <a name="enablestatuscallback"></a>  CInternetSession::EnableStatusCallback

ステータスコールバックを有効にするには、このメンバー関数を呼び出します。

```cpp
BOOL EnableStatusCallback(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
コールバックを有効にするか無効にするかを指定します。 既定値は TRUE です。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、スローされた[CInternetException](../../mfc/reference/cinternetexception-class.md)オブジェクトを調べて、エラーの原因を特定します。

### <a name="remarks"></a>Remarks

ステータスコールバックを処理するときは、アプリケーションのステータスバーで、操作の進行状況 (名前の解決、サーバーへの接続など) に関する状態を指定できます。 操作の状態の表示は、長期的な操作中に特に適しています。

コールバックは要求の処理中に発生するため、アプリケーションは、ネットワークへのデータスループットの低下を防ぐために、コールバックでできるだけ短い時間を費やす必要があります。 たとえば、コールバックにダイアログボックスを配置すると、サーバーが要求を終了する時間がかかることがあります。

コールバックが保留中である限り、ステータスコールバックを削除することはできません。

操作を非同期で処理するには、独自のスレッドを作成するか、MFC なしで WinInet 関数を使用する必要があります。

## <a name="getcontext"></a>  CInternetSession::GetContext

特定のアプリケーションセッションのコンテキスト値を取得するには、このメンバー関数を呼び出します。

```cpp
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>戻り値

アプリケーション定義のコンテキスト識別子。

### <a name="remarks"></a>Remarks

[OnStatusCallback](#onstatuscallback)は、によって返さ`GetContext`れるコンテキスト ID を使用して、特定のアプリケーションの状態を報告します。 たとえば、ユーザーがステータス情報を返すインターネット要求をアクティブにすると、状態コールバックはコンテキスト ID を使用してその特定の要求の状態を報告します。 両方がステータス情報を返すという2つの個別のインターネット要求`OnStatusCallback`をユーザーがアクティブにすると、はコンテキスト識別子を使用して、対応する要求に関する状態を返します。 その結果、コンテキスト識別子はすべてのステータスコールバック操作に使用され、セッションが終了するまでセッションに関連付けられます。

非同期操作の詳細については、インターネット[の最初の手順に関する記事を参照してください。WinInet](../../mfc/wininet-basics.md)。

## <a name="getcookie"></a>  CInternetSession::GetCookie

このメンバー関数は、Windows SDK で説明されているように、Win32 関数[Internetgetcookie](/windows/win32/api/wininet/nf-wininet-internetgetcookiew)の動作を実装します。

```cpp
static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPTSTR pstrCookieData,
    DWORD dwBufLen);

static BOOL GetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    CString& strCookieData);
```

### <a name="parameters"></a>パラメーター

*pstrUrl*<br/>
URL を格納している文字列へのポインター。

*pstrCookieName*<br/>
指定した URL に対して取得するクッキーの名前を格納している文字列へのポインター。

*pstrCookieData*<br/>
最初のオーバーロードでは、cookie データを受け取るバッファーのアドレスを格納している文字列へのポインター。 この値には NULL を指定できます。 2番目のオーバーロードでは、cookie データを受け取る[CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクトへの参照。

*dwBufLen*<br/>
*PstrCookieData*バッファーのサイズを指定する変数です。 関数が成功した場合、バッファーは*pstrCookieData*バッファーにコピーされたデータの量を受け取ります。 *PstrCookieData*が NULL の場合、このパラメーターは、すべての cookie データをコピーするために必要なバッファーのサイズを指定する値を受け取ります。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出して、エラーの原因を特定します。 次のエラー値が適用されます。

- ERROR_NO_MORE_ITEMS は、指定された URL とそのすべての親の cookie は存在しません。

- ERROR_INSUFFICIENT_BUFFER *Dwbuflen*で渡される値は、すべての cookie データをコピーするのに十分ではありません。 *Dwbuflen*で返される値は、すべてのデータを取得するために必要なバッファーのサイズです。

### <a name="remarks"></a>Remarks

2番目のオーバーロードでは、指定`CString`されたオブジェクトに cookie データが MFC によって取得されます。

## <a name="getcookielength"></a>  CInternetSession::GetCookieLength

バッファーに格納されているクッキーの長さを取得するには、このメンバー関数を呼び出します。

```cpp
static DWORD GetCookieLength(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName);
```

### <a name="parameters"></a>パラメーター

*pstrUrl*<br/>
URL を含む文字列へのポインター

*pstrCookieName*<br/>
クッキーの名前を格納している文字列へのポインター。

### <a name="return-value"></a>戻り値

バッファーに格納されている cookie の長さを示す DWORD 値。 *PstrCookieName*によって示された名前のクッキーが存在しない場合は0。

### <a name="remarks"></a>Remarks

この値は[Getcookie](#getcookie)によって使用されます。

## <a name="getftpconnection"></a>CInternetSession:: GetFtpConnection

このメンバー関数を呼び出して、FTP 接続を確立し、 `CFtpConnection`オブジェクトへのポインターを取得します。

```cpp
CFtpConnection* GetFtpConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>パラメーター

*pstrServer*<br/>
FTP サーバー名を含む文字列へのポインターです。

*pstrUserName*<br/>
ログインするユーザーの名前を指定する null で終わる文字列へのポインター。 NULL の場合、既定値は anonymous です。

*pstrPassword*<br/>
ログインに使用するパスワードを指定する null で終わる文字列へのポインター。 *PstrPassword*と*pstrUserName*の両方が NULL の場合、既定の匿名パスワードはユーザーの電子メール名になります。 *PstrPassword*が null (または空の文字列) であるにもかかわらず*pstrUserName*が null でない場合は、空白のパスワードが使用されます。 次の表では、 *pstrUserName*と*pstrPassword*の4つの設定の動作について説明します。

| *pstrUserName*  | *pstrPassword*  | FTP サーバーに送信されたユーザー名 | FTP サーバーに送信されるパスワード |
|-----------------|-----------------|-----------------------------|-----------------------------|
|   NULL または ""   |   NULL または ""   |         非同期         |      ユーザーの電子メール名      |
| NULL 以外の文字列 |   NULL または ""   |       *pstrUserName*        |             " "             |
|      NULL       | NULL 以外の文字列 |            ERROR            |            ERROR            |
| NULL 以外の文字列 | NULL 以外の文字列 |       *pstrUserName*        |       *pstrPassword*        |

*nPort*<br/>
サーバーで使用する TCP/IP ポートを識別する番号。

*bPassive*<br/>
この FTP セッションのパッシブモードまたはアクティブモードを指定します。 TRUE に設定すると、Win32 API `dwFlag`が INTERNET_FLAG_PASSIVE に設定されます。

### <a name="return-value"></a>戻り値

[CFtpConnection](../../mfc/reference/cftpconnection-class.md)オブジェクトへのポインター。 呼び出しが失敗した場合は、スローされた[CInternetException](../../mfc/reference/cinternetexception-class.md)オブジェクトを調べて、エラーの原因を特定します。

### <a name="remarks"></a>Remarks

`GetFtpConnection`FTP サーバーに接続し、 `CFTPConnection`オブジェクトへのポインターを作成して返します。 サーバーでは、特定の操作は実行されません。 たとえば、ファイルの読み取りまたは書き込みを行う場合は、これらの操作を別々の手順として実行する必要があります。 ファイルの検索、ファイルの開く、ファイルの読み取りまたは書き込みの詳細については、「 [CFtpConnection](../../mfc/reference/cftpconnection-class.md) and [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)クラス」を参照してください。 一般的な FTP 接続タスクの実行手順については、「 [WinInet を使用したインターネットプログラミング](../../mfc/win32-internet-extensions-wininet.md)」を参照してください。

### <a name="example"></a>例

[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)の例を参照してください。

## <a name="getgopherconnection"></a>  CInternetSession::GetGopherConnection

このメンバー関数を呼び出して、新しい gopher 接続を確立し、 `CGopherConnection`オブジェクトへのポインターを取得します。

```cpp
CGopherConnection* GetGopherConnection(
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>パラメーター

*pstrServer*<br/>
Gopher サーバー名を含む文字列へのポインターです。

*pstrUserName*<br/>
ユーザー名を含む文字列へのポインター。

*pstrPassword*<br/>
アクセスパスワードを格納している文字列へのポインター。

*nPort*<br/>
サーバーで使用する TCP/IP ポートを識別する番号。

### <a name="return-value"></a>戻り値

[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)オブジェクトへのポインター。 呼び出しが失敗した場合は、スローされた[CInternetException](../../mfc/reference/cinternetexception-class.md)オブジェクトを調べて、エラーの原因を特定します。

### <a name="remarks"></a>Remarks

`GetGopherConnection`gopher サーバーに接続し、 `CGopherConnection`オブジェクトへのポインターを作成して返します。 サーバーでは、特定の操作は実行されません。 たとえば、データの読み取りまたは書き込みを行う場合は、これらの操作を別々の手順として実行する必要があります。 ファイルの検索、ファイルの開く、ファイルの読み取りまたは書き込みの詳細については、 [CGopherConnection](../../mfc/reference/cgopherconnection-class.md)、 [CGopherFile](../../mfc/reference/cgopherfile-class.md)、および[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)クラスを参照してください。 FTP サイトの参照の詳細については、「メンバー関数[OpenURL](#openurl)」を参照してください。 一般的な gopher 接続タスクの実行手順については、「 [WinInet を使用したインターネットプログラミング](../../mfc/win32-internet-extensions-wininet.md)」を参照してください。

## <a name="gethttpconnection"></a>CInternetSession:: GetHttpConnection

このメンバー関数を呼び出して、HTTP 接続を確立し、 `CHttpConnection`オブジェクトへのポインターを取得します。

```cpp
CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);

CHttpConnection* GetHttpConnection(
    LPCTSTR pstrServer,
    DWORD dwFlags,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL);
```

### <a name="parameters"></a>パラメーター

*pstrServer*<br/>
HTTP サーバー名を格納している文字列へのポインター。

*nPort*<br/>
サーバーで使用する TCP/IP ポートを識別する番号。

*pstrUserName*<br/>
ユーザー名を含む文字列へのポインター。

*pstrPassword*<br/>
アクセスパスワードを格納している文字列へのポインター。

*dwflags*<br/>
`INTERNET_FLAG_*`フラグの任意の組み合わせ。 *DwFlags*値の説明については、「 [CHttpConnection:: openrequest](../../mfc/reference/chttpconnection-class.md#openrequest) 」の「**解説**」の表を参照してください。

### <a name="return-value"></a>戻り値

[CHttpConnection](../../mfc/reference/chttpconnection-class.md)オブジェクトへのポインター。 呼び出しが失敗した場合は、スローされた[CInternetException](../../mfc/reference/cinternetexception-class.md)オブジェクトを調べて、エラーの原因を特定します。

### <a name="remarks"></a>Remarks

`GetHttpConnection`HTTP サーバーに接続し、 `CHttpConnection`オブジェクトへのポインターを作成して返します。 サーバーでは、特定の操作は実行されません。 たとえば、HTTP ヘッダーを照会する場合は、この操作を別の手順として実行する必要があります。 HTTP サーバーへの接続を使用して実行できる操作の詳細については、「 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) and [CHttpFile](../../mfc/reference/chttpfile-class.md)クラス」を参照してください。 HTTP サイトの参照の詳細については、「メンバー関数[OpenURL](#openurl)」を参照してください。 一般的な HTTP 接続タスクの実行手順については、「 [WinInet を使用したインターネットプログラミング](../../mfc/win32-internet-extensions-wininet.md)」を参照してください。

## <a name="onstatuscallback"></a>CInternetSession:: OnStatusCallback

このメンバー関数は、ステータスコールバックが有効で操作が保留中の場合に状態を更新するために、フレームワークによって呼び出されます。

```cpp
virtual void OnStatusCallback(
    DWORD_PTR dwContext,
    DWORD dwInternetStatus,
    LPVOID lpvStatusInformation,
    DWORD dwStatusInformationLength);
```

### <a name="parameters"></a>パラメーター

*dwContext*<br/>
アプリケーションによって提供されるコンテキスト値。

*dwInternetStatus*<br/>
コールバックが行われた理由を示すステータスコード。 使用可能な値の一覧については、「**解説**」を参照してください。

*lpvStatusInformation*<br/>
このコールバックに関連する情報を格納しているバッファーへのポインター。

*dwStatusInformationLength*<br/>
*Lpvstatusinformation*のサイズ。

### <a name="remarks"></a>Remarks

ステータスコールバックを利用するには、最初に[EnableStatusCallback](#enablestatuscallback)を呼び出す必要があります。

*DwInternetStatus*パラメーターは、実行されている操作を示し、 *Lpvstatusinformation*の内容を決定します。 *Dwstatusinformationlength*は、 *lpvstatusinformation*に含まれるデータの長さを示します。 *DwInternetStatus*の次の状態値は、次のように定義されています。

|[値]|説明|
|-----------|-------------|
|INTERNET_STATUS_RESOLVING_NAME|*Lpvstatusinformation*に含まれる名前の IP アドレスを検索しています。|
|INTERNET_STATUS_NAME_RESOLVED|*Lpvstatusinformation*に含まれる名前の IP アドレスが正常に検出されました。|
|INTERNET_STATUS_CONNECTING_TO_SERVER|*Lpvstatusinformation*が指すソケットアドレス ([SOCKADDR](/windows/win32/winsock/sockaddr-2)) に接続しています。|
|INTERNET_STATUS_CONNECTED_TO_SERVER|*Lpvstatusinformation*が指すソケットアドレス (SOCKADDR) に正常に接続しました。|
|INTERNET_STATUS_SENDING_REQUEST|情報要求をサーバーに送信しています。 *Lpvstatusinformation*パラメーターが NULL です。|
|INTERNET_STATUS_ REQUEST_SENT|情報要求がサーバーに正常に送信されました。 *Lpvstatusinformation*パラメーターが NULL です。|
|INTERNET_STATUS_RECEIVING_RESPONSE|サーバーが要求に応答するのを待機しています。 *Lpvstatusinformation*パラメーターが NULL です。|
|INTERNET_STATUS_RESPONSE_RECEIVED|サーバーからの応答を正常に受信しました。 *Lpvstatusinformation*パラメーターが NULL です。|
|INTERNET_STATUS_CLOSING_CONNECTION|サーバーへの接続を閉じています。 *Lpvstatusinformation*パラメーターが NULL です。|
|INTERNET_STATUS_CONNECTION_CLOSED|サーバーへの接続が正常に切断されました。 *Lpvstatusinformation*パラメーターが NULL です。|
|INTERNET_STATUS_HANDLE_CREATED|新しいハンドルが作成されたことを示すために、Win32 API 関数[Internetconnect](/windows/win32/api/wininet/nf-wininet-internetconnectw)によって使用されます。 これにより、接続に時間がかかりすぎる場合、アプリケーションは別のスレッドから Win32 関数[Internetclosehandle](/windows/win32/api/wininet/nf-wininet-internetclosehandle)を呼び出すことができます。 これらの関数の詳細については、「Windows SDKfor」を参照してください。|
|INTERNET_STATUS_HANDLE_CLOSING|このハンドル値が正常に終了しました。|

ステータスコールバックルーチンが実行される前に何らかのアクションを要求するには、このメンバー関数をオーバーライドします。

> [!NOTE]
> 状態のコールバックには、スレッド状態の保護が必要です。 共有ライブラリで MFC を使用している場合は、オーバーライドの先頭に次の行を追加します。

[!code-cpp[NVC_MFCHtmlHttp#8](../../mfc/reference/codesnippet/cpp/cinternetsession-class_1.cpp)]

非同期操作の詳細については、インターネット[の最初の手順に関する記事を参照してください。WinInet](../../mfc/wininet-basics.md)。

## <a name="openurl"></a>  CInternetSession::OpenURL

このメンバー関数を呼び出して、指定された要求を HTTP サーバーに送信し、要求と共に送信する追加の RFC822、MIME、または HTTP ヘッダーをクライアントで指定できるようにします。

```cpp
CStdioFile* OpenURL(
    LPCTSTR pstrURL,
    DWORD_PTR dwContext = 1,
    DWORD dwFlags = INTERNET_FLAG_TRANSFER_ASCII,
    LPCTSTR pstrHeaders = NULL,
    DWORD dwHeadersLength = 0);
```

### <a name="parameters"></a>パラメーター

*pstrURL*<br/>
読み取りを開始する URL の名前へのポインター。 File:、ftp:、gopher:、または http: で始まる Url のみがサポートされています。 *PstrURL*が NULL の場合にアサートします。

*dwContext*<br/>
コールバックで返されたハンドルと共に渡されたアプリケーション定義の値。

*dwFlags*<br/>
この接続を処理する方法を説明するフラグ。 有効なフラグの詳細については、「**解説**」を参照してください。 有効なフラグは次のとおりです。

- 既定値は INTERNET_FLAG_TRANSFER_ASCII です。 ファイルを ASCII テキストとして転送します。

- INTERNET_FLAG_TRANSFER_BINARY ファイルをバイナリファイルとして転送します。

- INTERNET_FLAG_RELOAD は、ローカルにキャッシュされている場合でも、ネットワークからデータを取得します。

- INTERNET_FLAG_DONT_CACHE は、ローカルまたはどのゲートウェイにもデータをキャッシュしません。

- INTERNET_FLAG_SECURE このフラグは、HTTP 要求にのみ適用されます。 Secure Sockets Layer または PCT を使用して、セキュリティで保護されたトランザクションをネットワーク上で要求します。

- INTERNET_OPEN_FLAG_USE_EXISTING_CONNECT 可能であれば、接続要求ごとに新しいセッションを作成するの`OpenUrl`ではなく、によって生成された新しい要求に対して、サーバーへの既存の接続を再利用します。

- INTERNET_FLAG_PASSIVE FTP サイトで使用されます。 パッシブ FTP セマンティクスを使用します。 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)の`OpenURL`と共に使用します。

*pstrHeaders*<br/>
HTTP サーバーに送信されるヘッダーを格納している文字列へのポインター。

*dwHeadersLength*<br/>
追加ヘッダーの長さ (文字数)。 この値が-1L で、 *pstrHeaders*が NULL 以外の場合、 *pstrHeaders*はゼロで終了すると見なされ、長さが計算されます。

### <a name="return-value"></a>戻り値

FTP、GOPHER、HTTP、およびファイルタイプのインターネットサービスのみのファイルハンドルを返します。 解析が失敗した場合は NULL を返します。

が`OpenURL`返すポインターは、 *pstrURL*のサービスの種類によって異なります。 次の表は、ポインター `OpenURL`が返す可能性があることを示しています。

|URL の種類|戻り値|
|--------------|-------------|
|file://|`CStdioFile*`|
|http://|`CHttpFile*`|
|gopher://|`CGopherFile*`|
|ftp://|`CInternetFile*`|

### <a name="remarks"></a>Remarks

*DwFlags*パラメーターには、INTERNET_FLAG_TRANSFER_ASCII または INTERNET_FLAG_TRANSFER_BINARY のいずれかを含める必要がありますが、両方を含めることはできません。 残りのフラグは、ビットごとの**or**演算子 ( **&#124;** ) と組み合わせることができます。

`OpenURL`は、Win32 関数`InternetOpenURL`をラップし、インターネットサーバーからのデータのダウンロード、取得、および読み取りのみを許可します。 `OpenURL`リモートの場所でのファイルの操作を許可しないため、 [CInternetConnection](../../mfc/reference/cinternetconnection-class.md)オブジェクトを必要としません。

ファイルへの書き込みなど、接続固有の (プロトコル固有の) 関数を使用するには、セッションを開き、特定の種類の接続を開き、その接続を使用して目的のモードでファイルを開く必要があります。 接続`CInternetConnection`固有の関数の詳細については、「」を参照してください。

## <a name="operator_hinternet"></a>CInternetSession:: operator HINTERNET

現在のインターネットセッションの Windows ハンドルを取得するには、この演算子を使用します。

```cpp
operator HINTERNET() const;
```

## <a name="setcookie"></a>  CInternetSession::SetCookie

指定された URL のクッキーを設定します。

```cpp
static BOOL SetCookie(
    LPCTSTR pstrUrl,
    LPCTSTR pstrCookieName,
    LPCTSTR pstrCookieData);
```

### <a name="parameters"></a>パラメーター

*pstrUrl*<br/>
クッキーを設定する必要がある URL を指定する、null で終わる文字列へのポインター。

*pstrCookieName*<br/>
クッキーの名前を格納している文字列へのポインター。

*pstrCookieData*<br/>
URL に関連付ける実際の文字列データを格納している文字列へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE を返します。 特定のエラーコードを取得するには、を呼び出します。`GetLastError.`

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、Win32 message [InternetSetCookie](/windows/win32/api/wininet/nf-wininet-internetsetcookiew)の動作を実装します。

## <a name="setoption"></a>CInternetSession:: SetOption

このメンバー関数を呼び出して、インターネットセッションのオプションを設定します。

```cpp
BOOL SetOption(
    DWORD dwOption,
    LPVOID lpBuffer,
    DWORD dwBufferLength,
    DWORD dwFlags = 0);

BOOL SetOption(
    DWORD dwOption,
    DWORD dwValue,
    DWORD dwFlags = 0);
```

### <a name="parameters"></a>パラメーター

*dwOption*<br/>
設定するインターネットオプション。 使用可能なオプションの一覧については、「Windows SDKfor の[オプションフラグ](/windows/win32/WinInet/option-flags)」を参照してください。

*lpBuffer*<br/>
オプション設定を格納しているバッファー。

*dwBufferLength*<br/>
*Lpbuffer*の長さまたは*dwValue*のサイズ。

*dwValue*<br/>
オプション設定を含む DWORD です。

*dwFlags*<br/>
さまざまなキャッシュオプションを示します。 既定値は0に設定されています。 指定できる値は次のとおりです。

- INTERNET_FLAG_DONT_CACHE は、ローカルまたは任意のゲートウェイサーバーにデータをキャッシュしません。

- INTERNET_FLAG_OFFLINE のダウンロード操作は、永続キャッシュのみで満たされます。 項目がキャッシュに存在しない場合は、適切なエラーコードが返されます。 このフラグは、ビットごとの**or** ( **&#124;** ) 演算子と組み合わせることができます。

### <a name="return-value"></a>戻り値

操作が成功した場合、値 TRUE が返されます。 エラーが発生した場合は、値 FALSE が返されます。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection クラス](../../mfc/reference/cinternetconnection-class.md)<br/>
[CHttpConnection クラス](../../mfc/reference/chttpconnection-class.md)<br/>
[CFtpConnection クラス](../../mfc/reference/cftpconnection-class.md)<br/>
[CGopherConnection クラス](../../mfc/reference/cgopherconnection-class.md)
