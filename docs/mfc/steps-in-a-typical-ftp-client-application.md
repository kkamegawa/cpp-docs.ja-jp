---
title: 典型的な FTP クライアント アプリケーションの作成手順
ms.date: 11/04/2016
helpviewer_keywords:
- Internet client applications [MFC], FTP table
- FTP (File Transfer Protocol)
- WinInet classes [MFC], FTP
- FTP (File Transfer Protocol) [MFC], client applications
- Internet applications [MFC], FTP client applications
ms.assetid: 70bed7b5-6040-40d1-bc77-702e63a698f2
ms.openlocfilehash: d08edf704e748767f3b566252ad328baf40b55ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307018"
---
# <a name="steps-in-a-typical-ftp-client-application"></a>典型的な FTP クライアント アプリケーションの作成手順

典型的な FTP クライアント アプリケーションを作成、 [CInternetSession](../mfc/reference/cinternetsession-class.md)と[CFtpConnection](../mfc/reference/cftpconnection-class.md)オブジェクト。 これらの MFC WinInet クラスは制御しない点実際には、プロキシ型の設定に注意してください。IIS では。

次の表に、典型的な FTP クライアント アプリケーションでの手順を示します。

|目標|操作を実行します。|効果|
|---------------|----------------------|-------------|
|FTP セッションを開始します。|作成、 [CInternetSession](../mfc/reference/cinternetsession-class.md)オブジェクト。|WinInet を初期化し、サーバーに接続します。|
|FTP サーバーに接続します。|使用[CInternetSession::GetFtpConnection](../mfc/reference/cinternetsession-class.md#getftpconnection)します。|返します、 [CFtpConnection](../mfc/reference/cftpconnection-class.md)オブジェクト。|
|サーバー上に新しい FTP ディレクトリに変更します。|使用[CFtpConnection::SetCurrentDirectory](../mfc/reference/cftpconnection-class.md#setcurrentdirectory)します。|現在、サーバーに接続しているディレクトリを変更します。|
|FTP ディレクトリの最初のファイルを検索します。|使用[CFtpFileFind::FindFile](../mfc/reference/cftpfilefind-class.md#findfile)します。|最初のファイルを検索します。 ファイルが見つからない場合は FALSE を返します。|
|FTP ディレクトリの次のファイルを検索します。|使用[CFtpFileFind::FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile)します。|次のファイルを検索します。 ファイルが見つからない場合は FALSE を返します。|
|によって検出されたファイルを開く`FindFile`または`FindNextFile`の読み取りまたは書き込み。|使用[CFtpConnection::OpenFile](../mfc/reference/cftpconnection-class.md#openfile)、によって返されるファイル名を使用して[FindFile](../mfc/reference/cftpfilefind-class.md#findfile)または[FindNextFile](../mfc/reference/cftpfilefind-class.md#findnextfile)します。|サーバー上の読み取りまたは書き込みのファイルを開きます。 返します、 [CInternetFile](../mfc/reference/cinternetfile-class.md)オブジェクト。|
|読み取りまたはファイルに書き込みます。|使用[細かい](../mfc/reference/cinternetfile-class.md#read)または[CInternetFile::Write](../mfc/reference/cinternetfile-class.md#write)します。|読み取るか、指定した数の指定したバッファーを使用してバイトを書き込みます。|
|例外を処理する|使用して、 [CInternetException](../mfc/reference/cinternetexception-class.md)クラス。|すべての一般的なインターネット例外タイプを処理します。|
|FTP セッションを終了します。|破棄、 [CInternetSession](../mfc/reference/cinternetsession-class.md)オブジェクト。|開いているファイル ハンドルと接続を自動的にクリーンアップします。|

## <a name="see-also"></a>関連項目

[Win32 インターネット拡張機能 (WinInet)](../mfc/win32-internet-extensions-wininet.md)<br/>
[インターネット クライアント クラスの必要条件](../mfc/prerequisites-for-internet-client-classes.md)<br/>
[MFC WinInet クラスを使ってインターネット クライアント アプリケーションを作成する方法](../mfc/writing-an-internet-client-application-using-mfc-wininet-classes.md)
