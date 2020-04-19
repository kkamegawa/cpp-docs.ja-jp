---
title: インターネット クライアント クラスの必要条件
ms.date: 11/04/2016
helpviewer_keywords:
- Internet files [MFC], writing to
- Internet [MFC], connections
- FTP (File Transfer Protocol), MFC classes
- Gopher prerequisites [MFC]
- files [MFC], writing to
- classes [MFC], connections
- HTTP [MFC], prerequisites for Internet clients
- connections [MFC], classes for
- Internet client class prerequisites [MFC]
- files [MFC], reading
- URLs [MFC], Internet client applications
- prerequisites, Internet client classes [MFC]
- Gopher client applications [MFC]
ms.assetid: c51d1dfe-260c-4228-8100-e4efd90e9599
ms.openlocfilehash: 6246db7dfb2837f5d94fa51f8433b46722c43663
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218807"
---
# <a name="prerequisites-for-internet-client-classes"></a>インターネット クライアント クラスの必要条件

(たとえば、ファイルの読み取り)、インターネット クライアントによって行われたいくつかのアクション (この場合は、インターネット接続を確立する) の前提条件のアクションがあります。 次の表は、一部のクライアント操作の前提条件を一覧表示します。

### <a name="general-internet-url-ftp-gopher-or-http"></a>一般的なインターネット URL (FTP、Gopher、または HTTP)

|アクション|必須コンポーネント|
|------------|------------------|
|接続を確立します。|作成、 [CInternetSession](../mfc/reference/cinternetsession-class.md)をインターネット クライアント アプリケーションの基礎を確立します。|
|URL を開きます。|接続を確立します。 呼び出す[できます](../mfc/reference/cinternetsession-class.md#openurl)します。 `OpenURL`関数が読み取り専用のリソース オブジェクトを返します。|
|データの読み取りの URL。|URL を開きます。 呼び出す[細かい](../mfc/reference/cinternetfile-class.md#read)します。|
|インターネット オプションを設定します。|接続を確立します。 呼び出す[CInternetSession::SetOption](../mfc/reference/cinternetsession-class.md#setoption)します。|
|ステータス情報で呼び出される関数を設定します。|接続を確立します。 呼び出す[CInternetSession::EnableStatusCallback](../mfc/reference/cinternetsession-class.md#enablestatuscallback)します。 オーバーライド[対応](../mfc/reference/cinternetsession-class.md#onstatuscallback)呼び出しを処理します。|

### <a name="ftp"></a>FTP

|アクション|必須コンポーネント|
|------------|------------------|
|FTP 接続を確立します。|作成、 [CInternetSession](../mfc/reference/cinternetsession-class.md)このインターネット クライアント アプリケーションの基礎として。 呼び出す[CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection)を作成する、 [CFtpConnection](../mfc/reference/cftpconnection-class.md)オブジェクト。|
|最初のリソースを検索します。|FTP 接続を確立します。 作成、 [CFtpFileFind](../mfc/reference/cftpfilefind-class.md)オブジェクト。 呼び出す[CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile)します。|
|使用可能なすべてのリソースを列挙します。|最初のファイルを検索します。 呼び出す[CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile)まで、FALSE が返されます。|
|FTP ファイルを開きます。|FTP 接続を確立します。 呼び出す[CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile)を作成して開く、 [CInternetFile](../mfc/reference/cinternetfile-class.md)オブジェクト。|
|FTP ファイルを読み取る。|読み取りアクセス権を持つ FTP ファイルを開きます。 呼び出す[細かい](../mfc/reference/cinternetfile-class.md#read)します。|
|FTP ファイルに書き込みます。|書き込みアクセス権を持つ FTP ファイルを開きます。 呼び出す[CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write)します。|
|サーバー上のクライアントのディレクトリを変更します。|FTP 接続を確立します。 呼び出す[CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)します。|
|サーバー上のクライアントの現在のディレクトリを取得します。|FTP 接続を確立します。 呼び出す[CFtpConnection::GetCurrentDirectory](../mfc/reference/cftpconnection-class.md#getcurrentdirectory)します。|

### <a name="http"></a>HTTP

|アクション|必須コンポーネント|
|------------|------------------|
|HTTP 接続を確立します。|作成、 [CInternetSession](../mfc/reference/cinternetsession-class.md)このインターネット クライアント アプリケーションの基礎として。 呼び出す[代わりに](../mfc/reference/cinternetsession-class.md#gethttpconnection)を作成する、 [CHttpConnection](../mfc/reference/chttpconnection-class.md)オブジェクト。|
|HTTP ファイルを開きます。|HTTP 接続を確立します。 呼び出す[しないで](../mfc/reference/chttpconnection-class.md#openrequest)を作成する、 [CHttpFile](../mfc/reference/chttpfile-class.md)オブジェクト。 呼び出す[CHttpFile::AddRequestHeaders](../mfc/reference/chttpfile-class.md#addrequestheaders)します。 呼び出す[chttpfile::sendrequest](../mfc/reference/chttpfile-class.md#sendrequest)します。|
|HTTP ファイルを読み取る。|HTTP ファイルを開きます。 呼び出す[細かい](../mfc/reference/cinternetfile-class.md#read)します。|
|HTTP 要求に関する情報を取得します。|HTTP 接続を確立します。 呼び出す[しないで](../mfc/reference/chttpconnection-class.md#openrequest)を作成する、 [CHttpFile](../mfc/reference/chttpfile-class.md)オブジェクト。 呼び出す[CHttpFile::QueryInfo](../mfc/reference/chttpfile-class.md#queryinfo)します。|

### <a name="gopher"></a>gopher

|アクション|必須コンポーネント|
|------------|------------------|
|Gopher の接続を確立します。|作成、 [CInternetSession](../mfc/reference/cinternetsession-class.md)このインターネット クライアント アプリケーションの基礎として。 呼び出す[代わり](../mfc/reference/cinternetsession-class.md#getgopherconnection)を作成する、 [CGopherConnection](../mfc/reference/cgopherconnection-class.md)します。|
|現在のディレクトリ内の最初のファイルを検索します。|Gopher の接続を確立します。 作成、 [CGopherFileFind](../mfc/reference/cgopherfilefind-class.md)オブジェクト。 呼び出す[CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator)を作成する、 [CGopherLocator](../mfc/reference/cgopherlocator-class.md)オブジェクト。 ロケーターを[CGopherFileFind::FindFile](../mfc/reference/cgopherfilefind-class.md#findfile)します。 呼び出す[なった](../mfc/reference/cgopherfilefind-class.md#getlocator)を後で必要な場合、ファイルのロケーターを取得します。|
|使用可能なすべてのファイルを列挙します。|最初のファイルを検索します。 呼び出す[CGopherFileFind::FindNextFile](../mfc/reference/cgopherfilefind-class.md#findnextfile)まで、FALSE が返されます。|
|Gopher ファイルを開きます。|Gopher の接続を確立します。 Gopher ロケーターを作成[CGopherConnection::CreateLocator](../mfc/reference/cgopherconnection-class.md#createlocator)ロケーターを検索または[なった](../mfc/reference/cgopherfilefind-class.md#getlocator)します。 呼び出す[CGopherConnection::OpenFile](../mfc/reference/cgopherconnection-class.md#openfile)します。|
|Gopher ファイルを読み取ります。|Gopher ファイルを開きます。 使用[CGopherFile](../mfc/reference/cgopherfile-class.md)します。|

## <a name="see-also"></a>関連項目

[Win32 インターネット拡張機能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[インターネット クライアント アプリケーションの作成用の MFC クラス](../mfc/mfc-classes-for-creating-internet-client-applications.md)<br/>
[MFC WinInet クラスを使ってインターネット クライアント アプリケーションを作成する方法](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
