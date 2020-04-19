---
title: CGopherConnection クラス
ms.date: 11/04/2016
f1_keywords:
- CGopherConnection
- AFXINET/CGopherConnection
- AFXINET/CGopherConnection::CGopherConnection
- AFXINET/CGopherConnection::CreateLocator
- AFXINET/CGopherConnection::GetAttribute
- AFXINET/CGopherConnection::OpenFile
helpviewer_keywords:
- CGopherConnection [MFC], CGopherConnection
- CGopherConnection [MFC], CreateLocator
- CGopherConnection [MFC], GetAttribute
- CGopherConnection [MFC], OpenFile
ms.assetid: b5b96aea-ac99-430e-bd84-d1372b43f78f
ms.openlocfilehash: f5d655aa7fd2eb9e41c15c60a71492c24ba43c43
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506192"
---
# <a name="cgopherconnection-class"></a>CGopherConnection クラス

gopher インターネット サーバーへの接続を管理します。

> [!NOTE]
>  クラス`CGopherConnection` 、`CGopherFile`、 、`CGopherLocator`およびそれらのメンバーは、Windows XP プラットフォームでは動作しないため、非推奨とされますが、以前のプラットフォームでも引き続き動作します。 `CGopherFileFind`

## <a name="syntax"></a>構文

```
class CGopherConnection : public CInternetConnection
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CGopherConnection::CGopherConnection](#cgopherconnection)|`CGopherConnection` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CGopherConnection::CreateLocator](#createlocator)|Gopher サーバー上のファイルを検索するための[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)オブジェクトを作成します。|
|[CGopherConnection::GetAttribute](#getattribute)|Gopher オブジェクトに関する属性情報を取得します。|
|[CGopherConnection::OpenFile](#openfile)|Gopher ファイルを開きます。|

## <a name="remarks"></a>Remarks

Gopher サービスは、MFC WinInet クラスによって認識される3つのインターネットサービスのうちの1つです。

クラス`CGopherConnection`には、gopher サービスを管理するコンストラクターと3つの追加メンバー関数が含まれています。[OpenFile](#openfile)、 [createlocator](#createlocator)、および[GetAttribute](#getattribute)。

Gopher インターネットサーバーと通信するには、まず[CInternetSession](../../mfc/reference/cinternetsession-class.md)のインスタンスを作成してから、 [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)を呼び出します。これ`CGopherConnection`により、オブジェクトが作成され、そのオブジェクトへのポインターが返されます。 オブジェクトを`CGopherConnection`直接作成することはありません。

が他の MFC インターネット`CGopherConnection`クラスと連携する方法の詳細については、「 [WinInet を使用したインターネットプログラミング](../../mfc/win32-internet-extensions-wininet.md)」を参照してください。 サポートされている2つのインターネットサービス (FTP と HTTP) の使用の詳細については、「 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) and [CFtpConnection](../../mfc/reference/cftpconnection-class.md)クラス」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CGopherConnection`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxinet.h

##  <a name="cgopherconnection"></a>  CGopherConnection::CGopherConnection

このメンバー関数は、オブジェクトを`CGopherConnection`構築するために呼び出されます。

```
CGopherConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CGopherConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>パラメーター

*pSession*<br/>
関連する[CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトへのポインター。

*hConnected*<br/>
現在のインターネットセッションの Windows ハンドル。

*pstrServer*<br/>
FTP サーバー名を含む文字列へのポインターです。

*dwContext*<br/>
操作のコンテキスト識別子。 *dwContext*は、 [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)によって返される操作の状態情報を識別します。 既定値は1に設定されています。ただし、操作の特定のコンテキスト ID を明示的に割り当てることができます。 オブジェクトとそれが実行する作業は、そのコンテキスト ID に関連付けられます。

*pstrUserName*<br/>
ログインするユーザーの名前を指定する null で終わる文字列へのポインター。 NULL の場合、既定値は anonymous です。

*pstrPassword*<br/>
ログインに使用するパスワードを指定する null で終わる文字列へのポインター。 *PstrPassword*と*pstrUserName*の両方が NULL の場合、既定の匿名パスワードはユーザーの電子メール名になります。 *PstrPassword*が null (または空の文字列) であるにもかかわらず*pstrUserName*が null でない場合は、空白のパスワードが使用されます。 次の表では、 *pstrUserName*と*pstrPassword*の4つの設定の動作について説明します。

|*pstrUserName*|*pstrPassword*|FTP サーバーに送信されたユーザー名|FTP サーバーに送信されるパスワード|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL または ""|NULL または ""|非同期|ユーザーの電子メール名|
|NULL 以外の文字列|NULL または ""|*pstrUserName*|" "|
|Null 以外の文字列|ERROR|ERROR||
|NULL 以外の文字列|NULL 以外の文字列|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
サーバーで使用する TCP/IP ポートを識別する番号。

### <a name="remarks"></a>Remarks

を`CGopherConnection`直接作成することはありません。 代わりに、 [CInternetSession:: GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)を呼び出して、 `CGopherConnection`オブジェクトを作成し、そのオブジェクトへのポインターを返します。

##  <a name="createlocator"></a>  CGopherConnection::CreateLocator

Gopher サーバー上のファイルを検索または特定するための gopher ロケーターを作成するには、このメンバー関数を呼び出します。

```
CGopherLocator CreateLocator(
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType);

static CGopherLocator CreateLocator(LPCTSTR pstrLocator);

static CGopherLocator CreateLocator(
    LPCTSTR pstrServerName,
    LPCTSTR pstrDisplayString,
    LPCTSTR pstrSelectorString,
    DWORD dwGopherType,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER);
```

### <a name="parameters"></a>パラメーター

*pstrDisplayString*<br/>
取得する gopher ドキュメントまたはディレクトリの名前を格納している文字列へのポインター。 *PstrDisplayString*パラメーターが NULL の場合、gopher サーバーの既定のディレクトリが返されます。

*pstrSelectorString*<br/>
項目を取得するために gopher サーバーに送信されるセレクター文字列へのポインター。 *pstrSelectorString*は NULL にすることができます。

*dwGopherType*<br/>
これは、 *pstrSelectorString*がディレクトリまたはドキュメントを参照するかどうか、および要求が gopher または gopher + であるかどうかを指定します。 Windows SDK[の構造体の属性を参照](/windows/win32/api/wininet/ns-wininet-gopher_find_dataw)してください。

*pstrLocator*<br/>
開くファイルを識別する文字列へのポインター。 通常、この文字列は[CGopherFileFind:: GetLocator](../../mfc/reference/cgopherfilefind-class.md#getlocator)の呼び出しから返されます。

*pstrServerName*<br/>
Gopher サーバー名を含む文字列へのポインターです。

*nPort*<br/>
この接続のインターネットポートを識別する番号。

### <a name="return-value"></a>戻り値

[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)オブジェクトです。

### <a name="remarks"></a>Remarks

静的バージョンのメンバー関数ではサーバーを指定する必要がありますが、非静的バージョンでは接続オブジェクトのサーバー名が使用されます。

Gopher サーバーから情報を取得するには、最初にアプリケーションで gopher ロケーターを取得する必要があります。 その後、アプリケーションでは、ロケーターを不透明なトークンとして処理する必要があります (つまり、アプリケーションはロケーターを使用できますが、直接操作や比較を行うことはできません)。 通常、アプリケーションは、 [CGopherFileFind:: FindFile](../../mfc/reference/cgopherfilefind-class.md#findfile)メンバー関数の呼び出しにロケーターを使用して、特定の情報を取得します。

##  <a name="getattribute"></a>  CGopherConnection::GetAttribute

このメンバー関数を呼び出して、gopher サーバーから項目に関する特定の属性情報を取得します。

```
BOOL GetAttribute(
    CGopherLocator& refLocator    CString strRequestedAttributes,
    CString& strResult,);
```

### <a name="parameters"></a>パラメーター

*refLocator*<br/>
[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)オブジェクトへの参照。

*strRequestedAttributes*<br/>
要求された属性の名前を指定するスペース区切りの文字列。

*strResult*<br/>
ロケーターの種類を受け取る[CString](../../atl-mfc-shared/reference/cstringt-class.md)への参照。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

##  <a name="openfile"></a>  CGopherConnection::OpenFile

このメンバー関数を呼び出して、gopher サーバー上のファイルを開きます。

```
CGopherFile* OpenFile(
    CGopherLocator& refLocator,
    DWORD dwFlags = 0,
    LPCTSTR pstrView = NULL,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>パラメーター

*refLocator*<br/>
[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)オブジェクトへの参照。

*dwFlags*<br/>
INTERNET_FLAG_ * フラグの任意の組み合わせ。 INTERNET_FLAG_\*フラグの詳細については、「 [CInternetSession:: OpenUrl](../../mfc/reference/cinternetsession-class.md#openurl) 」を参照してください。

*pstrView*<br/>
ファイルビュー文字列へのポインター。 ファイルの複数のビューがサーバーに存在する場合、このパラメーターは開くファイルビューを指定します。 *PstrView*が NULL の場合、既定のファイルビューが使用されます。

*dwContext*<br/>
開かれているファイルのコンテキスト ID。 *DwContext*の詳細については、「**解説**」を参照してください。

### <a name="return-value"></a>戻り値

開く[CGopherFile](../../mfc/reference/cgopherfile-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

*DwContext*の既定値をオーバーライドして、コンテキスト識別子を任意の値に設定します。 コンテキスト識別子は、その[CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトによって作成`CGopherConnection`されるオブジェクトのこの特定の操作に関連付けられます。 値は[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)に返され、識別された操作の状態が示されます。 インターネットの最初[の手順に関する記事を参照してください。WinInet](../../mfc/wininet-basics.md)の詳細については、「」を参照してください。

## <a name="see-also"></a>関連項目

[CInternetConnection クラス](../../mfc/reference/cinternetconnection-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CFtpConnection クラス](../../mfc/reference/cftpconnection-class.md)<br/>
[CHttpConnection クラス](../../mfc/reference/chttpconnection-class.md)<br/>
[CInternetConnection クラス](../../mfc/reference/cinternetconnection-class.md)<br/>
[CGopherLocator クラス](../../mfc/reference/cgopherlocator-class.md)<br/>
[CGopherFile クラス](../../mfc/reference/cgopherfile-class.md)<br/>
[CInternetSession クラス](../../mfc/reference/cinternetsession-class.md)
